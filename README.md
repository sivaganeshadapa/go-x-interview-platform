# Go-X Analytics Platform

A comprehensive SaaS analytics interface for AI-powered interviewing with physiological analytics, biometric verification, and real-time insights.

## Features

### Core Analytics
- **Audio Analytics**: Overall scores, lip sync, engagement, influence, truthfulness, bias, sentiment analysis
- **Health Metrics**: Real-time HR, HRV, blood pressure, SpO2, stress index, respiration monitoring
- **Biometric Verification**: Facial recognition, voice pattern matching, liveness detection
- **HR Insights**: AI-powered candidate analysis with technical scoring and recommendations

### Interface Components
- **Speaker Diarization**: Real-time timeline with color-coded speaker segments and percentages
- **Video Player**: 16:9 aspect ratio with draggable floating thumbnail
- **Interactive Analytics**: Tabbed interface with real-time data visualization
- **Responsive Design**: Optimized for desktop, tablet, and mobile devices

### AI Integration
- **Zai AI Assistant**: Emotionally intelligent recruiter with 130+ language support
- **Real-time Insights**: Live behavioral and physiological analysis
- **Automated Summaries**: AI-generated interview reports and recommendations

## Technology Stack

- **Frontend**: React 18, TypeScript, Tailwind CSS
- **Charts**: Recharts, Custom Gauge Components
- **Icons**: Lucide React
- **Database**: Supabase (PostgreSQL)
- **Authentication**: Supabase Auth
- **Real-time**: Supabase Realtime subscriptions

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd gox-analytics-platform
```

2. Install dependencies:
```bash
npm install
```

3. Set up environment variables:
```bash
# Create .env file
VITE_SUPABASE_URL=your-supabase-url
VITE_SUPABASE_ANON_KEY=your-supabase-anon-key
```

4. Start development server:
```bash
npm run dev
```

## Database Setup

The platform uses Supabase with the following schema:

- `user_profiles` - User information and preferences
- `meetings` - Interview sessions and metadata
- `participants` - Meeting participants (Zai, candidates)
- `speaker_segments` - Diarization data for timeline
- `audio_metrics` - Audio analysis results
- `health_metrics` - Physiological monitoring data
- `biometric_verification` - Identity verification results
- `hr_insights` - AI-generated candidate insights

## API Integration

### Supabase Operations

```typescript
import { supabaseOperations } from './lib/supabase';

// Fetch meetings
const meetings = await supabaseOperations.getMeetings(userId);

// Subscribe to real-time updates
const subscription = supabaseOperations.subscribeToMeetingUpdates(
  meetingId, 
  (payload) => {
    // Handle real-time analytics updates
  }
);

// Save biometric verification
await supabaseOperations.saveBiometricVerification(meetingId, verification);
```

## Component Architecture

### Main Components
- `InterviewDashboard` - Main application layout
- `Sidebar` - Navigation menu
- `Header` - Meeting information and controls
- `VideoPlayer` - Video display with floating thumbnail
- `SpeakerDiarization` - Timeline visualization
- `AnalyticsPanel` - Tabbed analytics interface

### Analytics Components
- `AudioAnalytics` - Audio metrics and visualizations
- `HealthMetrics` - Physiological monitoring cards
- `BiometricVerification` - Identity verification flow
- `HRInsights` - AI-generated candidate analysis

### Utility Components
- `GaugeChart` - Custom gauge visualization
- `Homepage` - Marketing and brand website

## Data Flow

1. **Meeting Creation**: Create meeting record in Supabase
2. **Real-time Analytics**: Stream audio/video data to AI processors
3. **Data Updates**: Push analytics to database via Supabase API
4. **UI Updates**: Real-time subscriptions update interface
5. **Report Generation**: AI summaries and insights saved to database

## Mock Data Structure

```typescript
interface Meeting {
  id: string;
  title: string;
  participants: Speaker[];
  speakerSegments: SpeakerSegment[];
  audioMetrics: AudioMetrics;
  healthMetrics: HealthMetrics;
  biometricVerification: BiometricVerification;
  hrInsights: HRInsights;
  // ... other fields
}
```

## Customization

### Theme Configuration
The platform uses a consistent color system:
- Primary: `#1B1F3B` (Navy)
- Secondary: `#7C4DFF` (Purple)
- Accent: `#00C2A0` (Teal)
- Success: `#10B981` (Green)
- Warning: `#F59E0B` (Amber)
- Error: `#EF4444` (Red)

### Analytics Customization
Each analytics component accepts props for real-time data:

```typescript
<AudioAnalytics metrics={meeting.audioMetrics} />
<HealthMetrics metrics={meeting.healthMetrics} />
<BiometricVerification data={meeting.biometricVerification} />
```

## Deployment

1. Build the project:
```bash
npm run build
```

2. Deploy to your preferred hosting platform (Vercel, Netlify, etc.)

3. Configure environment variables in your hosting platform

4. Set up Supabase database with the provided schema

## Security & Compliance

- **Data Encryption**: All data encrypted in transit and at rest
- **GDPR Compliance**: User consent and data deletion workflows
- **HIPAA Ready**: Healthcare-grade security for physiological data
- **SOC2 Compliance**: Enterprise security standards
- **Row Level Security**: Database-level access control

## Performance Optimization

- **Code Splitting**: Lazy loading of components
- **Image Optimization**: Optimized images from Pexels CDN
- **Real-time Efficiency**: Debounced updates and smart subscriptions
- **Caching**: Intelligent data caching strategies

## Browser Support

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

This project is proprietary software. All rights reserved.

## Support

For technical support or questions:
- Email: support@go-x.ai
- Documentation: https://docs.go-x.ai
- Status Page: https://status.go-x.ai