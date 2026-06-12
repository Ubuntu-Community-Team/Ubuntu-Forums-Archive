---
title: "Game Servers via Wine. Tickless required?"
date: 2010-03-04
forum: Server Platforms
---

### Post by oXYnary on 2010-03-04
*(Mods: If you feel this belongs more in the Games or Wine discussion area, please feel free to move.  This question does intersect many areas, so was unsure where to put)*

Hi I have a funky server Ubuntu 9.10 Enterprise setup where I have X on all the time (using Xfce4 - not Xbuntu) with latest wine so I can run Windows only based game server executables.

One of the applications is a simple dedicated racing game server made by the company I work for that works perfect in wine *(unfortunately, the full 3D game client does not, so its a windows only game)*.  The other is more just to test, runs Serious Sam HD dedicated with wine with a steam client active in background since SSHD Ded requires a steam client logged in (just create a dummy account).

Im getting some lag issues with the SSHD on the end-users client side.  Unsure if its related to it being a more complex game and using wine to translate slowing it down.  Things like tiny warps once in awhile, and the ping of clients kinda jumping around.

Im pretty sure my network settings are ok. Maybe not fully optimized for every bit via ipv4.  Still though.  This 1U Opteron server is in a ISP with a full 1000 up and down. Ports are locked out that aren't being used. I do have apache going, but its nothing strenuous.

The CPU isnt used overly so. Maybe peaks out around 60% under strain, but mostly 20-40%.  Memory use is about 550-700megs for SSHD itself.  Given, it only has 2 gigs total at this time, but I still usually have near a Gig of memory available at most times.

I admit newbness of linux servers in general. Was reading about other game servers like CS:S requiring a ticked kernel near 1000 to get the least amount of lag. Some even saying they dropped the tickless options of the newer 2.6 kernels on purpose because they produced lag.  Was checking on the history of newer Windows Server like 2008 and they still use a ticked OS, though a more optimized version.

So this boils down to should I be running a Ticked OS kernel to run a more complex Windows based dedicated server?  I haven't tried thus far, well because I am again a bit of a n00b to all this.  That and I'm not sure you have to tell wine or the SS:HD dedicated exe itself to run at a full ticked rate (no option I have seen for a command line function in the SS:HD itself).

Have any of you run windows based games servers on your systems?  Any important areas I should look into?

---

### Post by oXYnary on 2010-03-05
Wrong category?  Or too specialized?  Forum suggestions welcome that do then.  :)

---

### Post by oXYnary on 2010-03-23
I'll give this another try.

---

