---
title: "[SOLVED] looking for an audio cd burning app with ability to split tracks and show wa"
date: 2008-11-20
forum: Ubuntu Studio
---

### Post by scarf on 2008-11-20
i have some recordings from my mp3 player that are just large wav files.  i have split them with audacity into ~80 minute chunks suitable for burning to a cd.

what i used to do, was use nero in windows xp, and add the wav file to a new audio cd compilation.  then, nero had this nice feature where it would load up the waveform of the audio and i could pick the exact spot to insert a split in the track.  i could zoom into the waveform to get very precise.

so, i'm looking for something like that.  i've checked out some apps like gnomebaker and k3d and they offer the ability to split the track, but it isn't precise enough.  seeing the waveform and being able to pick a spot down to the hundredth of a second (or is it a frame? either way...) is very important.

---

### Post by ryanhaigh on 2008-11-20
Why not just break them up again with Audacity?

---

### Post by scarf on 2008-11-23
thank you for the suggestion.

i have tried [_using audacity to split the track_](http://audacityteam.org/wiki/index.php?title=Splitting_recordings_into_separate_tracks) and then use "export multiple" to produce multiple wav files i can add to an audio cd project.

the problem i have run into, now, is that there are slight gaps that have been introduced between the tracks when i play back the burned cd.

i'm not sure if this is a problem with audacity or brasero.

i have loaded the separate wav files into totem, and the gaps can be heard as the playlist progresses between the tracks.  so, this could also be totem's fault for not playing the playlist continuously, or it could be a problem with the wav files audacity produced...

in brasero, i have made sure that the "pause length" on each track is 0

---

### Post by scarf on 2008-11-27
reading more through that link in my last post regarding splitting recordings into separate tracks, there is a section at the end regarding gapless burning which provides instructions on exporting a label list from audacity and then using a community-provided java applet to convert that file into a cue sheet.  the cue sheet can then be loaded into the burning app to produce the desired output.  brasero has a bug in which the cue sheet doesn't work unless edited to include the full path to the wav file.  another burning app, like gnomebacker, handles the cue sheet properly without editing.

so, i'll mark this solved...

however, a new issue has arisen that would be nice to address before finishing up.  i know the cd i have produced is gapless between the tracks (since i have played it in a stand-alone cd audio player), but no player i can find within ubuntu will properly play the disc: they all insert gaps between the tracks.  i even tried some commercially-produced electronic music and they don't play properly either.  i have tried rhythmbox, audacious, exaile, vlc, totem, banshee, amarok....

so, the final thing to accomplish now is find an app that will properly play the cd without gaps.  anyone have any clues?  it seems to be a problem from what i've found....

---

