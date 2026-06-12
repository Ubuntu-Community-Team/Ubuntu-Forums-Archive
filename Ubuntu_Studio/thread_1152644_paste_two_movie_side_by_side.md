---
title: "paste two movie side by side"
date: 2009-05-08
forum: Ubuntu Studio
---

### Post by checcouniud on 2009-05-08
Does anybody know how to paste two movies side by side? which program can i use?
I have two movies of exactly the same length,dimension, and format and i want to paste them together side by side, such that i can see both of the at the same time. Can anybody tell me if there is a program that does that? and how to do that?
It should be an easy task but i am unexperienced in the field.

thank you very much for any help

---

### Post by Meelis on 2009-05-08
I did it so some tyme ago.
1. Convert to same fps
2. In VirtualDub delete some frames (both files have same amount of frames).
3. In VirtualDub: File - Export - image sequence (separate folders)
4. 1st folder batch rename in IrfanView starting index 1, increment 2
5. 2nt folder batch rename in IrfanView starting index 2, increment 2
6. Move all frames in 1 folder.
7. Open IrfanView Thumbnails, navigate to your folder, Ctrl + A, right Mouse click on some image - Create contact sheet from selected files. Make sure you use fast image format (fastest png or uncompressed) because it will take hours.
8. Rename all contact sheets if needed (00001, 00002...46321)
9. open 1st contact sheet with VirtualDub (Virtualdub opens all others to)
10. Set fps, compression, audio and save as video file.
------
You can to mutch of it with digikam / plugins. I havn't used Linux video editors.

Good luck :)

---

### Post by cotcot on 2009-05-08
Blender VSE. 
Put both videos above each other in the timeline with an empty track between them (for the effects). Apply on both (separately) a transform effect (green strips; more info see [[COLOR="Red"]here[/COLOR]]("http://wiki.blender.org/index.php/Doc:Manual/Sequencer/Effects")) to scale them down to the size you want and move one to the left and the other to the right so that they fit with the frame size of your rendering.
Apply an alpha over effect (brown strip) of the upper transform strip on the lower. Render.

I have put an example in a screenshot in attachment.(I made the example with 2 x the same clip)

---

### Post by checcouniud on 2009-05-08
Thank you,
both of you.
I think i will install blender VSE.
i will give a try tonight and see if i am able to make it work.
:)
You help me a lot.

I really appreciate.

---

### Post by kayosiii on 2009-05-08
Another method is to use xjadeo (if you merely want to view two videos at the same time and not necessarily combine them). you can getting by adding this repository to your [https://launchpad.net/~stochastic/+archive/ppa](https://launchpad.net/~stochastic/+archive/ppa) list of sources.

Basically just load the two videos from the command line 
xjadeo [Videos/name_of_video.avi] &
xjadeo [name_of_second_video.ogg] 

or something like that.
These will play simultaneously when you hit the play button on the jack transport. (you can do this from a lot of jack enabled audio applications eg rosegarden or ardour, or you can use the transport buttons in qjackctl.)

xjadeo is designed for writing music that syncs with visuals...

---

