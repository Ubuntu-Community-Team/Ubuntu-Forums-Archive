---
title: "Rosegarden &amp; Timidity instrument recognition"
date: 2009-04-21
forum: Ubuntu Studio
---

### Post by haxeflashguy on 2009-04-21
This is a general post asking for anyone to please comment to contribute what they have been able to do to get past being able to just use basic midi on Rosegarden (piano thru gunshot and drums on instr#10)

The way I got Rosegarden to pump out basic midi with Timidy is as follows:

1) Download freepats or eawpats and set up Timidity. The best (most succinct, anyway) guide i have found for gettin that done is Hari's at [http://harishankar.org/blog/entry.php/three-steps-to-midi-on-linux](http://harishankar.org/blog/entry.php/three-steps-to-midi-on-linux)

2) Once you have changed your timidity.cfg file to reflect the location of your sound patches as per Hari's instructions, go ahead and start timidity by typing * timidity -iA -Os* and that starts timidity running.

3) Then you open up Rosegarden and you should have sound based on general midi patches.  Ignore the popup window that says "Failed to connect to Jack audio server". (At least i didn't and it works anyway). One way to check that you have sound is to select one of the midi sounds under the "instrument parameters" under "Program", then select the "draw" tool (red pen icon) and click on the first bar on the segment canvas (to the right of the area that looks like "1 o o <untitled>"). You should see the first bar filled in with a swatch labeled with the instrument you selected. Right click on that and choose "open in notation editor" and you can click out notes which should produce sound based on the instrument you selected under general midi.

The frustrating thing, and the part I am still struggling with is, how do I get Rosegarden to use the other sound patches that came with freepats or eawpats???
I mean, there are other cool looking sound effect patches and stuff that came with eawpats and I would like to be able to use them but so far, I have only figured out how to get the drum patches to produce sound..... 

In Rosegarden's "Track Parameters" section, select "Instrument #10[D]" under the general midi device, then when you draw on the segment canvas and open it in notiation editor, you will get various drum sounds depending on where you click on the staff.

If anyone can suggest how to get some of the other sounds that came with eawpats to play under Rosegarden, please respond. There are patches like "doggrowl" and "door" and "meow" that would be cool to be able to get Rosegarden to use.

Thanks in advance!!!

---

