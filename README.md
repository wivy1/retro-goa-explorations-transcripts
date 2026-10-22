# DJ Solitare's Retro Goa Explorations Transcripts

This repository contains cleaned transcripts of every episode of [DJ Solitare's Retro Goa Explorations](https://www.youtube.com/playlist?list=PLI3nfsMvaXNhckzdkb0KJDu-nPeLlpw-0) video series.

## Motivation

This archive was created because DJ Solitare's direct involvement in the 1990s goa trance scene, along with his close personal connections from that time, gives him insider details about these tracks and their production that have not been documented elsewhere.

## Process

### Transcription

1. Download Episode audio with yt-dlp.
2. Convert the audio to 16kHz mono with FFmpeg.
3. Divide the audio into overlapping 30s sections with FFmpeg.
4. Perform local speech-recognition on each section using Qwen3-ASR 1.7B. If no speech is detected, that section is further processed with Whisper large-v3 through faster-whisper. *(These episodes consist of commentary spoken over a live playback of a track, which Qwen3 sometimes struggles with. I found that Whisper was more successful at extracting speech in those situations.)*
5. Join the individual sections and remove overlapping sections.
6. Format the transcribed text (punctuation, capitalization, sentence boundaries, and topic-based paragraphs) using Qwen3.6 27B (4-bit Q4_K_M quantization), running locally through Ollama.
7. Extract all YouTube comments with yt-dlp into JSON. 

### LLM-guided Cleanup

8. Provide GPT 6 Pro with the transcript, comments, and a specialist knowledge-base containing verified names, aliases, track titles, equipment names, terminology, and previous corrections.
9. Check names, titles, equipment, and terminology against the knowledge-base and surrounding discussion.
10. Research suspected phonetic errors and unresolved references using official artist/label catalogs, Bandcamp, Discogs, and specialist archives such as goatrance.xyz. *(Examples include “Roger Ram” → “Raja Ram” and “Spangle” → “Shpongle.”)*
11. Verify the specific release or mix before correcting titles, preserving intentional spelling variations.
12. Remove transcription-window duplication, preserving intentional repetition.
13. Correct punctuation, capitalization, and broken word boundaries.
14. Divide the transcript into the expected episode sections: introduction, track commentary, observations, and closing remarks.
15. Add a standardized episode header.
16. Review YouTube comments for relevant historical and musical details (e.g. artist recollections, corrections), placing them under the section "Notes from the Comments".
17. Update the specialist knowledge-base with newly verified names, aliases, spellings, terminology, corrections, and sources.
