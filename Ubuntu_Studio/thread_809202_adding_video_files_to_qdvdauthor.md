---
title: "adding video files to qdvdauthor"
date: 2008-05-27
forum: Ubuntu Studio
---

### Post by highrik on 2008-05-27
Hi guys

I'm trying to put my .mpg files on to a DVD using qdvdauthor and I'm following this tutorial:

[http://www.linuxforums.org/multimedia/how_to_make_dvds_with_menus_using_q_dvd_author.html](http://www.linuxforums.org/multimedia/how_to_make_dvds_with_menus_using_q_dvd_author.html)

I've got stuck on step 6 where I'm trying to add my .mpg files.  I click the 'Add/Organise Videos' button and then navigate to the directory where my .mpg files are.  The problem is all the files are coloured blue and have error written on them.  Does anyone know how I can solve this problem?

Thanks, Rick

---

### Post by fif on 2008-06-13
Hello Highrik

I add exactly the same problem (qdvdauthor version 1.0104 which is a 1.1.0.0-0.0ubuntu1 under synaptic).
I 'work-arounded' it the following way:
[LIST]
[*]
[/LIST] under tools->setup, select mplayer as the video player
- right click on the upper left blank window: a requester appears in which you can select your video. An error icon is displayed but still you can add your video even if it is in error.
I did not change the video player under tools->setup in the first place (it contained a default I did not remember). When adding the video via right-clicking, the thumbnail on the right showed a playing video but I had a freeze when pressing Ok.

If you still have the problem, try with another player. I also changed the Media engine to DummyWidget but I am not sure this has any influence.
Hth

---

### Post by cotcot on 2008-06-14
Open Qdvdauthor. Start a new project. Go to the upper left window with the All Video Audio tabs. Select the All tab. Double click in the white window. You will get a pop up window with your file browser. Go to the folder with your video files. Double click on the video file you want. This file will appear in the All tab window. The thumb nail is still an error icon. But do not care about it. It does not avoid you to author the dvd. Double click on the file in the All tab to adapt Pal Ntsc etc ... .

Good luck

This is copied from my answer (#7) in [[COLOR="Red"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=813412").

---

