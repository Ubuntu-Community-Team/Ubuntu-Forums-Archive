---
title: "Ubuntu One for Windows always &quot;File Sync Starting...&quot; never starts"
date: 2011-09-30
forum: Ubuntu One (CLOSED)
---

### Post by Martin_sensei on 2011-09-30
Hello,

I have had some files sync on from my Ubuntu One client on my windows partition, however one day is failed to get past "File Sync Starting..."

I have uninstalled, reinstalled, upgraded to v2.0, but with no success. 

Now, when every I start Ubuntu One, my CPU hits a steady 50%, and the status is File Sync Starting...  I have left this for days but nothing changes.

Can I see a log anywhere?  Can I Force a reset or something? Is this normal?  I have just over 1GB to sync and it has done 755MB previously... Surely this should take an hour at the most!?

---

### Post by xl9g3e on 2011-10-03
I too am having this same problem today. Did you have any luck solving it?

Anyone have a solution?

---

### Post by Martin_sensei on 2011-10-04
Have not solved this, I resorted to manually copying the documents in the windows partition, to my home documents.

I also tried to uninstall Ubuntu One Windows, but the uninstall failed!  I tried to removed everything from the file system and registry but there are still some bits and pieces lying around I didn't want to touch.

So does this software actually work for people?

---

### Post by exsysprog on 2011-10-19
I too noticed tonight that the file sync "starts" but never does anything.  U1 seemed to work great when I first installed it a week or so ago.  All seems to have come to a halt. Windows7. U1 2.0.1

Hmmm hope we can get this worked out.  I really would like to use this stuff.  :(

---

### Post by penn919 on 2011-10-20
Guys, I'm having the exact same problem. Like the poster above, it was working about a week ago, but it stopped. It still works on my linux mint laptop, but I get "File Sync starting..." When I use the windows client. Please help! This is a real pain since I decided not too long ago to switch from Zumo to Ubuntu One since it didn't work well with linux, now it seems Ubuntu One doesn't work well with windows! :confused:

---

### Post by nigeldodd on 2011-10-23
File Sync starting... is the slogan for Ubuntu One on my desktop PC. Has been for months. It works on my laptop but not my desktop running 11.10. This problem is not confined to windows.

---

### Post by exsysprog on 2011-10-23
anybody know of a bug open in a tracking database or some other way we can track progress on this???  I'm having the same issue.

---

### Post by siucdude on 2011-10-24
Same here anyone get a fix, please post.. thank you

---

### Post by a$tr0_K1d on 2011-11-05
Please make sure ubuntu one is allowed through firewall and or make an exception for it.

this worked for me on win7

---

### Post by supernonu on 2011-11-05
i my pc it takes a lot of time
:(

---

### Post by penn919 on 2011-11-08
I've already checked my firewall. Ubuntu one isn't blocked. Has anyone had any luck yet? It's been forever.

---

### Post by siucdude on 2011-11-10
Yeah i read the firewall stuff and thats not it.. Still nothing.. I keep opening bugs.
Newest bug open is at
[https://bugs.launchpad.net/ubuntuone-windows-installer/+bug/888660](https://bugs.launchpad.net/ubuntuone-windows-installer/+bug/888660)
if you have that same issue please make comments and follow there as they may get this fixed sooner.
Thanks
TJ

---

### Post by Matti L on 2011-11-12
I've been thinking of using Ubuntu One instead of Dropbox, but maybe it's not time to switch yet.

---

### Post by hunterkasy on 2011-11-17
I am having the same problem with Ubuntu one on win 7 machine, I had to make changes in the firewall just to let it load, and now it loads and just sits on file sync starting (or something in that order)

my biggest question is why don't anyone seem to get any help in the Ubuntu one forum?  I have asked for help several times about Ubuntu one and I can't even get any help reply's

---

### Post by morph3x on 2011-11-23
I have same problem there, anyone figured out if its possible to fix it?

Also i already asked on askubuntu.com but didnt help at all.

---

### Post by penn919 on 2011-12-15
Hey guys, it looks like the problem has finally been fixed. I just checked and everything seems to be syncing just fine even on my Windows 7 PC. :D

---

### Post by Garland Fox on 2011-12-16
penn919;
See any indication that contact sync may be working yet?

---

### Post by penn919 on 2011-12-20
Garland Fox
I wouldn't know. I don't use that feature.

---

### Post by Garland Fox on 2011-12-22
> **penn919 said:**
> Garland Fox
I wouldn't know. I don't use that feature.
 Thanks for the reply

---

### Post by exsysprog on 2012-01-04
> **a$tr0_K1d said:**
> Please make sure ubuntu one is allowed through firewall and or make an exception for it.

this worked for me on win7

This also worked for me on W7 .. until it didn't :-(  Traffic had cleared the firewall on the W7 machine in question and from both my android phone and an ubuntu box on the same local network.  Did you have to do something special with your windows firewall to clear a path for U1?

---

### Post by exsysprog on 2012-01-05
for me this issue is resolved per:

[http://ubuntuforums.org/showthread.php?t=1865228](http://ubuntuforums.org/showthread.php?t=1865228)

I seem to be syncing again

---

