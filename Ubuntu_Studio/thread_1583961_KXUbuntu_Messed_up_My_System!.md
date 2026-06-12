---
title: "KXUbuntu Messed up My System!"
date: 2010-09-28
forum: Ubuntu Studio
---

### Post by BanannaButt on 2010-09-28
I just installed KXStudio, and I can no longer run Kontakt 4.1 standalone via Wine 1.2.  I had to do a giant update after installing it, and I was successfully running 4.1 on my previous install of 10.04 UbuntuStudio.

Since the error report NI Kontakt gives out is in a foreign format, only openable by the NI team itself (or so I understand), the error report doesn't say much in notepad.

I have tried disabling/enabling some audio drivers to see if that helped.  Nothing.

Any ideas?  I'm really, really regretting installing the distro...

---

### Post by cchhrriiss121212 on 2010-09-28
Do you mean KXStudio? It isn't an official Ubuntu variant, and it still seems to be quite new so I expect it still has a few bugs. It does look promising though, and I think the guy who maintains it posts here occasionally.
KXUbuntu isn't an OS, there is Kubuntu and Xubuntu however.

If you really don't like it, you could just reinstall Ubuntu Studio. If you like testing out new distros, then look into creating a separate /home partition that can be shared by multiple root partitions.

---

### Post by BanannaButt on 2010-09-28
> **cchhrriiss121212 said:**
> Do you mean KXStudio? It isn't an official Ubuntu variant, and it still seems to be quite new so I expect it still has a few bugs. It does look promising though, and I think the guy who maintains it posts here occasionally.
KXUbuntu isn't an OS, there is Kubuntu and Xubuntu however.

If you really don't like it, you could just reinstall Ubuntu Studio. If you like testing out new distros, then look into creating a separate /home partition that can be shared by multiple root partitions.
Yep, sorry.  I definitely meant to say KXStudio.

The thing is, I am very happy with it... I just want to figure out what's wrong here... and moreover where I can look on this forum to find tweaks, advice, etc. on running standalone Kontakt + JACK in Linux.  All because I'm relatively new to the Linux DAW game!

Thanks.

---

### Post by sgx on 2010-09-29
Hi, since NI scatters install files like a cybertornado, do make a separate /home partition, and before each reinstall, rename the .wine
folder, then copy over your vst section. But Kontakt has maybe 5 separate
locations, in winecfg panel, some of those get mapped to E: 
your /home/banana folder. I have a dual boot with xp, and dragged all the
NI folders to their linux counterparts, after tracking them down, and the apps run fine.

Sometimes just a newer wine version is to blame, so saving your packages in the synaptic cache (a setting in its preferences) makes it easy to revert by uninstalling it in synaptic, move it out of the cache temporarily, then use the 

dpkg -i name-of-wine-package 

command, with the name of the older wine package. 

If you'll be streaming samples, now would be a good time to include a second hardisk to run them from.

Cheers

---

