---
title: "Wine + Ableton Help"
date: 2012-01-28
forum: Ubuntu Studio
---

### Post by 0p7 0u7 on 2012-01-28
Hello, I've been trying to get Ableton Live working under Wine. There is a known bug and fix available for the rendering and exporting.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2113](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2113)

If you scroll down on the link it says.

"
**Exporting / Rendering Audio**
   Currently you need to build wine yourself and apply this [patch]("http://bugs2.winehq.org/attachment.cgi?id=33336"), as stated in [Bug 15695]("http://bugs.winehq.org/show_bug.cgi?id=15695").                    
Roughly:               

   $ git clone [git://source.winehq.org/git/wine.git]("http://source.winehq.org/git/wine.git") && cd wine               
$ patch -p1 < abletonexport.diff               
$ ./configure && make -j3
"


I have no idea what this is asking me to do. I typed the first command into the Terminal and it did something, the second command said file not found. The Wine Wiki appears to be down. I was wondering if someone might be able to help me out with this. I've been using Ubuntu for a while now but when it comes to stuff like this I'm still a total newb. Thanks.

---

### Post by sgx on 2012-01-28
Hi, here is a good page how to compile software in ubuntu.
Once you go through the steps, the things you tried can be tried
again.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[http://www.winehq.org/docs/wineusr-guide/installing-wine-source](http://www.winehq.org/docs/wineusr-guide/installing-wine-source)

If Live is starting and functioning, just failing to render and export,
learning the compile process and applying patches can help.

Placing these dll files in wines system32 folder, which are easily downloaded from the net, will likely help general compatibility.
Maybe your wine has some already.

gdiplus
mfc42
mfc71
msvcp60
msvcp71
msvcr71
msvcr80
mscvsc60
msvcp90
msvcr90

Cheers

---

### Post by 0p7 0u7 on 2012-01-29
Yes, the software loads and runs great until you try to do certain things like record, after a little research this appears to be normal and patchable. Thanks a bunch m8, I'll post back on how things go! :)

---

### Post by webdevel on 2012-02-03
Hey 0p7 0u7,

I'm trying to get ableton working on ubuntu right now too.  But I'm running into problems.

What versions of ableton, wine, ubuntu, winasio etc are you running? Did you follow a tutorial?

Thanks so much for any help!

---

### Post by 0p7 0u7 on 2012-02-03
I haven't got it working %100 just yet. Once I get it I'll be typing a brief tutorial.

---

### Post by sgx on 2012-02-05
This long thread to get FLStudio working starts with some
wine setup things, and in its 27 pages spanning 2 years :popcorn:

are some jewels of discovery,

which may apply to Ableton equally

there may be things worth pasting into a text file for future reference,
especially commands that display various hardware detections,
and software configs. Keeping an editor or light wordprocessor on the
taskbar is good luck.

gedit
abiword
kwrite
leafpad
etc

[http://ubuntuforums.org/showthread.php?t=1260057](http://ubuntuforums.org/showthread.php?t=1260057)

In the meantime, windows energy XT 2.5, cantabile 1.2lite, and
reaper, should all work without further ado, if you need to
record or jam :guitar:

---

