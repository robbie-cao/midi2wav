# midi2wav

Convert midi to wav

## Introduction

MIDI files consist of instrument, note and timing information, and perhaps keypress information (pressure, sustain, fade, etc).   It is easy to parse a MIDI file and extract that information, as the file format is relatively simple and well documented. To create instruments and notes you need samples, and the timing and keypress information is then used to modify the samples to produce the audio output. You can create your samples from an audio waveform generator (hardware or software) or from recorded audio. You would then use the media encoder to create the output file from the samples as you modify them according to the MIDI data.

You should start with processing the MIDI file to build a table (or list) that defines the output. You will need to construct a class to use for each sample that needs to be output, and you will need digital audio manipulation tools to adjust the tone, speed, attack, sustain, fade and level characteristics of the sample. When you have prepared the list with the modified samples and the supporting data needed, then you will need to use the facilties of the encoder to output the modified samples, with correct timing information, to the WAV file.

> https://social.msdn.microsoft.com/Forums/en-US/d1703423-ba7b-49a8-bd92-9a3925170421/convert-midi-to-wav-or-wma?forum=vblanguage

Modern synthesizers with highly-realistic sounds may use the technique of sampled audio recordings of actual instruments digitally modified to allow MIDI instruction control, however, this is not the only way to create synthesized audio. You can create your samples from an audio waveform generator (hardware or software) or from recorded audio. If you want to start from scratch, then part of your application is going to include some implementation of an audio waveform generator.

Early digitial synthesizers created waveforms from scratch and then attempted to modify them into complex waveforms that replicated those of a given musical instrument. Since synthesizers are typically keyboards based on the piano, and the piano has one of the least complex harmonic structures, the most basic of these modified tones is the digital piano sound.

The base wave is a clean sin wave played through a sound buffer (the classic computer "tone generator"). However, after generating the base sin wave, it is passed through a number of "digital oscillators", algorithms that modify the sound wave such that the output is similar to the effect of a physical ocillator on an analog electrical signal (this is the digital implementation of the original analog synthesizers), before being played through the buffer and this changes the tone into something which more closely resembles the sound of the instrument.

So even without pre-existing samples of an instrument to work with, it is possible to generate a tone at a given frequency (note) and then modify it until it resembles the sound of a particular instrument. Just as the MIDI file does not contain any sound, only instructions on how to create sound, so too can a MIDI Insrument definition contain only instructions on how to modify a sin wave and no actual instrument sound samples.

The quality of the output is almost completely dependant on whether or not the MIDI playback is performed with pure synthesis or with source audio samples. Taking any given MIDI file, if I play it on the PC using the Microsoft MIDI Synth included with windows, it sounds like Atari video game music. If I play that exact same file on the PSR-900, you would think you are listening to a CD of live music being played.

So, you can certainly implement your own waveform generator, or attempt to access the built in MIDI synth in Windows and use this to generate sound data for the midi file. You can then encode the raw audio into whatever format you like. But the quality of the resulting wave file will depend completely on the processor and voice data used to generate the audioform.

If you want the voice quality of the Microsoft MIDI Synth, then yeah, just plug an audio cable from the speaker out to the mic in on your sound card, play the sound in media player and record it in sound recorder. If you want to get some high quality recording of the MIDI file, run it through someone's keyboard.

> https://social.msdn.microsoft.com/Forums/en-US/d1703423-ba7b-49a8-bd92-9a3925170421/convert-midi-to-wav-or-wma?forum=vblanguage

## Reference

- http://midi2wav.com/convert-midi-to-wav-mp3.html
- https://social.msdn.microsoft.com/Forums/en-US/d1703423-ba7b-49a8-bd92-9a3925170421/convert-midi-to-wav-or-wma?forum=vblanguage
- http://midi2wav.com
