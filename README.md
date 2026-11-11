# Smart City - Civic OS & AI Tender Checker

AI-powered civic engagement and public works transparency platform for citizens, contractors, and municipal authorities.

## Core Features

### 1. AI-Powered Tender & Public Works Transparency
- **Authority / Contractor Work Order Publishing:** Officials and contractors upload official project documentation, budgets, contractor licenses, locations, and warranty terms.
- **Gemini AI Plain-Language Cost & Material Table:** Decodes complex 30-page engineering jargon into an itemized, transparent table showing where every single rupee is allocated (Materials, Base Foundation, Drainage, Machinery, Testing).
- **AI Integrity & Fair-Cost Score:** Rates tender fairness against standard municipal Schedule of Rates (SOR) and flags potential anomalies or missing maintenance clauses.
- **Contractor Warranty & Liability Tracking:** Explicitly details legally binding Defect Liability Period (DLP) obligations for free repairs.
- **Citizen Tender Dispute & Quality Flag System:** Citizens can report substandard materials, abandoned work, ghost projects, or warranty defects directly against any tender with photo evidence.
- **AI Vigilance & RTI Complaint Generator:** Automatically drafts a formal legal notice / Right to Information (RTI) application citing tender violation clauses for submission to anti-corruption authorities.

### 2. Hyperlocal Civic Issue Reporting
- **Multi-Modal Capture:** Image upload, video frame extraction, and live camera photo capture.
- **Gemini Vision AI Analysis:** Automatic issue categorization (Potholes, Water Leaks, Streetlights, Garbage, Flooding, Hazards), public risk assessment, priority scoring (1-10), and municipal department routing.
- **AI Formal Complaint Letter:** One-click generated 3-paragraph administrative letters ready to send to department officers.
- **Live City Map:** Leaflet.js interactive dark-themed map with severity pins and real-time tracking.
- **Crowdsourced Verification:** Upvoting and 3-peer verification protocol to prevent fake reports.
- **Area Health Score:** Algorithmic live city index (0-100) reflecting neighborhood safety and maintenance.

## Technologies Used
- **Google Gemini AI:** Gemini 2.5 Flash & 2.0 Flash (Vision, Natural Language, Table Generation & Legal Drafting)
- **Leaflet.js & CartoDB:** Real-time geospatial mapping
- **Firebase:** Firestore Database & Google OAuth Authentication
- **Vanilla Modern JS, HTML5, CSS3:** Ultra-clean, responsive, dark-mode civic dashboard

## How to Run

### Option A: Local HTTP Server (Recommended for full Google Auth)
Firebase Authentication requires an HTTP/HTTPS origin (not `file://`):
```bash
# Using Python
python -m http.server 8000

# OR using Node / npx
npx serve .
```
Then open `http://localhost:8000` (or the port shown) in your browser.

### Option B: Direct Browser Launch & Demo Mode
You can also open `index.html` directly in your browser. If you don't run a local server or haven't enabled Google Auth in Firebase yet, click **Demo Login** in the top navigation bar to test all features instantly (AI Vision analysis, Tender Decoder, RTI generator, and reporting).

## Firebase Console Configuration
To enable live Google Sign-In and Firestore for your Firebase project (`capstone26-7th`):
1. **Enable Google Sign-In**:
   - Go to [Firebase Console](https://console.firebase.google.com/) -> Select `capstone26-7th`
   - Go to **Build** -> **Authentication** -> **Sign-in method**
   - Click **Google**, toggle **Enable**, select a support email, and click **Save**.
2. **Authorized Domains**:
   - Under **Authentication** -> **Settings** -> **Authorized domains**, ensure `localhost` is listed.
3. **Firestore Database**:
   - Go to **Build** -> **Firestore Database** -> Click **Create database**.
   - In **Rules**, ensure read/write access is permitted for development:
     ```javascript
     rules_version = '2';
     service cloud.firestore {
       match /databases/{database}/documents {
         match /{document=**} {
           allow read, write: if true;
         }
       }
     }
     ```

## Multi-Page Architecture
The platform features an instant, client-side view router that provides distinct, isolated pages with full browser history support (`Back`/`Forward`) and deep linking:
- **`/#home`**: Clean landing page with centered title, description, interactive 4-step operation guide, and live city statistics.
- **`/#report`**: Dedicated issue reporting interface with camera, video, photo upload, and Gemini AI analysis panel.
- **`/#map`**: Dedicated geospatial intelligence view featuring the Leaflet dark map, area health score, AI city predictions, and crowdsourced community feed.
- **`/#tenders`**: Dedicated public works audit hub with contract registration, itemized AI cost tables, and citizen RTI dispute generator.
- **`/#admin`**: Administrative moderation feed for municipal officers.