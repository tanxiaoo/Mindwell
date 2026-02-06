# MindWell

MindWell is a mobile app (Flutter-based) that provides a safe and empathetic space for users to share their feelings and receive supportive AI conversation. The goal is to offer emotional support, not clinical therapy.

## App Vision

MindWell is designed to provide 1-to-1 chat with an AI companion that behaves as if informed by:
- Top-level psychological knowledge
- Evidence-based techniques (CBT, ACT, mindfulness, humanistic psychology)

The AI validates feelings, listens empathetically, and offers gentle guidance, without diagnosing or giving medical advice.

## Core Features

- Conversational chat interface with an AI companion  
- Natural, empathetic, warm, and non-judgmental responses  
- Contextual memory: tracks mood and recurring themes for better support  
- Suggests small exercises to help users cope, such as:
  - Breathing techniques  
  - Grounding exercises  
  - Journaling prompts  
  - Cognitive reframing  

**Example Flow:**
- User: "I feel empty and worthless."
- AI:
    - Recognizes the emotional state
    - Validates feelings (without diagnosing)
    - Asks 1–2 gentle follow-up questions
    - Suggests a small exercise or reflection


## AI Behavior Guidelines

- Acts as an emotional support companion, not a therapist  
- Uses phrasing like:
  - "It might help to try…"
  - "Many people find it useful to…"
  - "I’m not a professional, but I can support you…"  
- Never:
  - Diagnose mental illnesses
  - Say "you have depression/anxiety"
  - Prescribe or suggest medication

## Tech Stack

- **Frontend:** Flutter (iOS & Android)  
- **Backend / Serverless:** Firebase Cloud Functions (handles AI calls and sensitive logic)  
- **Database:** Firebase Firestore (stores chat history and context)  
- **AI:** Gemini API (Free Tier)

## Standard Message Flow

User sends message in Flutter
          |
          v
Flutter writes message to Firestore
          |
          v
Firestore triggers Cloud Function: onUserMessageCreate
          |
          v
Cloud Function:
  1. Load chat history & last emotion
  2. detectUserEmotion (new emotion)
  3. buildAIRequestPrompt (System Prompt + history + new emotion)
  4. callGeminiAPI
  5. validateAIResponse
  6. Write AI reply & new emotion to Firestore
          |
          v
Flutter listens to Firestore updates → Display AI reply & updated emotion


## System Artecture




## Getting Started

1. Clone this repository  
2. Set up a Firebase project with Firestore  
3. Deploy Cloud Functions with your Gemini API key  
4. Run the Flutter app on iOS or Android  
5. Start chatting with your AI companion!  

## Disclaimer

MindWell is **not a medical app**. It does **not diagnose, prescribe, or provide medical advice**. It is intended solely for **emotional support and wellbeing**.
