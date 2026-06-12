---
title: "Is there an extremely simple notation editor that will export MIDI?"
date: 2011-10-10
forum: Ubuntu Studio
---

### Post by boulezfan317 on 2011-10-10
Hello and thanks to anyone who can help me! 
I am trying to do something extremely simple. All of the software I have tried seems to be designed with a higher degree of functionality than I actually need for my purposes, and do not seem to be able to do this simple task: 

My goal is to create synthesized audio files in non-standard tunings to use in my violin practice. My ultimate goal would be to render 4 or 5 part music in a different tuning, and then have a set of files: all parts together, a file for each solo line, and a set of files each missing one part (like music minus one). I actually succeeded at this a few months ago using MuseScore, but I'm using a different machine now and that program crashes every 5 minutes for some reason. Every time I cut and paste for example, the program simply disappears. 
I used NoteEdit this time around, and succeeded in realizing a 5 part Gesualdo madrigal in a non-equal temperament, but it seems that I can't export individual parts with that program. Maybe I just can't find the right keyboard command or something, which is my hope, because is seems insane to write a music notation editing software without the ability to cut and paste or export out individual staffs. I have gained enough facility with lilypond to create a beautiful looking score, but I haven't come across any way to export a lilypond file as midi. I tried Rosegarden, but I think that program is designed to do far more sophisticated things, and while I can copy an individual track and save it as its own midi file, it won't play in timidity or anything else. 

All I want is 1: pitch, rhythm, and instrument data, 2: the ability to enter four or five staffs in one file and then export different combinations of those tracks as MIDI files. 

Any ideas? Am I just missing something? 

Thank you!

---

### Post by hreichgott on 2011-10-10
To export lilypond as midi:

Format your score block like this
```

\score {
<<
music goes here
>>
\layout {}
\midi {}
}

```

Whenever you compile the lilypond code (by running lilypond) it will now create both a .pdf score and a .mid file.

Here is how to specify the instrument for each staff: Put this inside each Staff block
```
  \set Staff.midiInstrument = #"cello"
```
There is probably a way to do that using MIDI channel numbers instead of text names, but can't remember what that is right now.

For more on Lilypond and MIDI look here
[http://lilypond.org/doc/v2.14/Documentation/notation/midi-output](http://lilypond.org/doc/v2.14/Documentation/notation/midi-output)

---

