---
title: "[SOLVED] soundkonverter doesn't start"
date: 2008-09-29
forum: Ubuntu Studio
---

### Post by Blindekinder on 2008-09-29
Hi,
I'm new user of U-S, but old with ubuntu... It works great, I installed Ffado for my Edirol FA-101, etc...
But I just tried to install soundkonverter, but it refuses to start, nothing happends... I tried in a terminal also, and nothing, not error message...
Doe's anybody had the same problem?
I'm running U-S Hardy...

I forgot: it works great on ubuntu...

---

### Post by Stochastic on 2008-09-30
Strange, it opens successfully on my UbuntuStudio Hardy box.  How did you install it?  Maybe try going into Synaptec Package Manager (if you installed it from the repos) and finding it in the list, the right click it and choose 'mark for reinstallation' then click apply.  Do you see any messages when you run it from the command line or does it just hang?  Do you see it in your system monitor as a running process?

Would you be just as happy running SoundConverter?

---

### Post by Blindekinder on 2008-09-30
Thanks Stochastic,
Yes, I installed it with Synaptic, and I already tried to reinstall it... 
The terminal doesn't give any message... just the cursor on the next line... and no running process... I also tried to run it as Sudo, and directly from the binary, thinking it was a problem with the launcher...

I know sound_c_onverter doesn't support all soundcodecs... but im interested about XCFE: does it work great?

---

### Post by Stochastic on 2008-09-30
> **Blindekinder said:**
> Thanks Stochastic,
Yes, I installed it with Synaptic, and I already tried to reinstall it... 
The terminal doesn't give any message... just the cursor on the next line... and no running process... I also tried to run it as Sudo, and directly from the binary, thinking it was a problem with the launcher...

I know sound_c_onverter doesn't support all soundcodecs... but im interested about XCFE: does it work great?

Yes, sound**C**onverter doesn't support wma, but other than that it'll cover everything sound**K**onverter covers.  XFCE is an entire desktop environment, not just a sound conversion app, infact I'm not sure there is a dedicated sound conversion app for it...  if I'm bored later I'll go hunting...

One last idea before I tell you to file a launchpad bug report on this, can you post the output of ```
strace soundkonverter
``` if the output is too big, you may want to upload a text file of the output rather than post it all in 'code' tags.

---

### Post by Blindekinder on 2008-09-30
ok, 
I straced soundkonverter and I get a list of error telling that he doesn't have permission on /home/.../.kde/shared/config... I checked and owner was root... I changed, but it still doesn't work...
strace output is in attachment (tar.bz, because txt was too big)...
I don't understand everything, but it seems it tries to open lib's, but doesn't find them (no such file or directory)
I tried to find some of them in synaptic, but they are not in repositories... :(:(

---

### Post by Stochastic on 2008-10-01
Well all the "(No such file or directory)" errors look to be resolved on the subsequent line(s) (i.e. you have the libraries installed and they are found by the program eventually, but it's looking in the wrong place to start).  The only place that looks out of order to me (though I'm no strace expert or developer) is the very end looks to be suddenly cut off.  This suggests that either it's hanging or you've cut it off prematurely with a ctrl+c command; try leaving it run for 10min to see if it eventually loads (kde apps on a gnome system get pretty heavy).  If you're still having troubles after that all I can suggest is to file an official bug report on launchpad.net

edit: p.s. those libraries are all in the repos, try running "apt-file search libwhatever.so.2" and it will show you which package contains the given file/library etc...

---

### Post by Bungo Pony on 2008-10-02
The only problem I had with SoundKonverter was getting the codecs working. It started without any problems.

Sound**C**onverter is a piece of junk. It's not as customizable as the KDE version. BTW, there seems to be a bug where after I change the destination directory in SoundKonverter, I have to restart the app for it to take effect.

Another option you could try is using EAC with WINE which works quite well and has all the functionality of SoundKonverter. You will also have to install LAME.EXE to convert MP3s.

---

### Post by Blindekinder on 2008-10-21
sorry for answering so late, problem with subscription...
Well, tank you for answers:
> try leaving it run for 10min to see if it eventually loads 
tried for half an hour... nothing... I think I'll report the bug...
> SoundConverter is a piece of junk
I just remember I used to work with it and It was something I couldn't do... that was why I installed SK... It's a great soft...
I tell you soon the progress...

---

### Post by Blindekinder on 2008-10-26
Well, I posted a bugreport... but then I found the solution: I removed ~/.kde, and this was recreated on next SK launch... now everything is ok... If you want to check the bugreport: [https://bugs.launchpad.net/ubuntu/+source/soundkonverter/+bug/289529]("https://bugs.launchpad.net/ubuntu/+source/soundkonverter/+bug/289529")
Thank you for your help...

---

