---
title: "CBT nuggets in Ubuntu"
date: 2009-07-22
forum: Wine
---

### Post by Lallen on 2009-07-22
I had vista running on my system which was very crapy especially after running GNS3. So I decided to flatten my system and dual both xp & ubuntu. I am really loving the ubuntu. I installed wine, however i cannot run my cbt nuggets under wine or ubuntu. can someone help me to get this running.

Thanks Much

---

### Post by ajackson on 2009-07-22
[** Before asking for help with Wine << PLEASE READ BEFORE POSTING **]("http://ubuntuforums.org/showthread.php?t=885111")

---

### Post by khayward on 2013-01-14
I was having this issue as well, and after doing the runaround with different codecs, I finally stumbled upon this:

"I converted the file using a 32-bit Linux machine and Mencoder compiled with "all-20110131" codecs from here:- 
[http://www.mplayerhq.hu/MPlayer/releases/codecs](http://www.mplayerhq.hu/MPlayer/releases/codecs)

Using a command like this:-
Code:
mencoder ccent10.wmv -o ccent10.avi -ovc lavc -oac mp3lame 

(Thank you bat999 the videohelp forum)"

Not sure if this will help you. If you play it in mplayer, you can't skip to a certain part but if you play it in VLC, it works excellent. Got my GNS3 and packetswitcher running...now onto the CCNA!

p.s. I was trying to figure out a script to convert all the .wmv files to .avi files, but haven't taken the time to fully explore it.

---

