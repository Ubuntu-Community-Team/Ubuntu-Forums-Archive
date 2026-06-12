---
title: "How To Get Age Of Empires 2 Working in virtual xp?"
date: 2008-12-29
forum: Virtualisation
---

### Post by Dustin2128 on 2008-12-29
Uh, I'm having a problem whenever I try and run aoe 2, age of kings, and the conquerer's expansion. No luck running under wine, so I tried it with my virtual installation of xp (virtualbox). No problem trying to run Aoe original gold edition, but whenever I hit play on aoe 2, it says please insert the proper disk, hit ok to restart the app. Any help? Do I need to convert them to iso's? I run aoe original with iso's, but I installed it originally from the actual disk. Also for running aoe gold, does anyone know how to set vbox to automatically resize (resolution) because aoe has a pathetic maximum res of 1024x768, and I'd prefer full screen.

---

### Post by solwic on 2008-12-30
> **Dustin2128 said:**
> Uh, I'm having a problem whenever I try and run aoe 2, age of kings, and the conquerer's expansion. No luck running under wine, so I tried it with my virtual installation of xp (virtualbox). No problem trying to run Aoe original gold edition, but whenever I hit play on aoe 2, it says please insert the proper disk, hit ok to restart the app. Any help? Do I need to convert them to iso's? I run aoe original with iso's, but I installed it originally from the actual disk. Also for running aoe gold, does anyone know how to set vbox to automatically resize (resolution) because aoe has a pathetic maximum res of 1024x768, and I'd prefer full screen.

I wasn't aware that games worked in Windows installed in Virtual Box.  Or does this game not use DirectX or OpenGL?

Do you have the CDROM set up correctly in VirtualBox?  It should be set to passthrough, I believe.  

Good luck!

---

### Post by Dustin2128 on 2008-12-30
I don't really think that helps much... can anyone tell me how to get them working in wine?

---

### Post by solwic on 2008-12-30
> **Dustin2128 said:**
> I don't really think that helps much... can anyone tell me how to get them working in wine?

Forgive me for suggesting a verification of CDROM settings when trying to help with an issue of a CDROM not being read.

Next time, I won't bother.  

Good luck!

---

### Post by Dustin2128 on 2008-12-31
I have the cd properly configured, xp knows it's there

---

### Post by eldaria on 2008-12-31
I hardly think it is related to the CD, but more to the fact that Most games do not work in Virtual environments because no Direct3D is available.
But easiest way to get games in Linux, is with Cedega.
and AOE2 works.
[http://www.cedega.com/gamesdb/games/view.html?game_id=5164](http://www.cedega.com/gamesdb/games/view.html?game_id=5164)

Regards.
Brian Levinsen

---

### Post by solwic on 2008-12-31
> **eldaria said:**
> I hardly think it is related to the CD, but more to the fact that Most games do not work in Virtual environments because no Direct3D is available.


That's what I said :lolflag:.

---

### Post by andriy.kostyuk on 2009-01-01
> **Dustin2128 said:**
> Uh, I'm having a problem whenever I try and run aoe 2, age of kings, and the conquerer's expansion. No luck running under wine, so I tried it with my virtual installation of xp (virtualbox). No problem trying to run Aoe original gold edition, but whenever I hit play on aoe 2, it says please insert the proper disk, hit ok to restart the app. Any help? Do I need to convert them to iso's? I run aoe original with iso's, but I installed it originally from the actual disk. Also for running aoe gold, does anyone know how to set vbox to automatically resize (resolution) because aoe has a pathetic maximum res of 1024x768, and I'd prefer full screen.

I've got the same problem with SEGA Medieval II Total War.
The installation was OK. 
But when I try to run the game it says "Please insert the proper CR-ROM", despite that the CD-ROM is already inserted. The CD is mounted, Windows XP sees it.

---

### Post by andriy.kostyuk on 2009-01-01
> **eldaria said:**
> I hardly think it is related to the CD, but more to the fact that Most games do not work in Virtual environments because no Direct3D is available.
Why does it ask for CD, if it needs Direct3D?

---

### Post by Dustin2128 on 2009-01-06
In virtualbox on my (shudder) vista laptop, which had an ati integrated card, it has the option for 3D acceleration, or something like that. I have a Nvidia Geforce4 graphics card, which I know has those capabilities, yet on the linux version there is no option for 3d acceleration. can anyone explain?

---

### Post by Dustin2128 on 2009-01-06
Never mind, I just wasn't updated to 2.1.

---

### Post by Dedoimedo on 2009-01-06
So did you solve the issue?

BTW, copying / burning AOE 2 from iso might not always work, the disc may not be recognized as the original one.

VirtualBox works better with OpenGL, VMware with DirectX. So you may want to see this, if it's of any help:

3D on VMware:
[http://www.dedoimedo.com/computers/virtualization-3d-support-vmware.html](http://www.dedoimedo.com/computers/virtualization-3d-support-vmware.html)

3D on VirtualBox:
[http://www.dedoimedo.com/computers/virtualization-3d-support-virtualbox.html](http://www.dedoimedo.com/computers/virtualization-3d-support-virtualbox.html)

Dedoimedo

---

### Post by Dustin2128 on 2009-01-07
would there happen to be a freeware version of vmware?

---

### Post by Dedoimedo on 2009-01-07
Sure, VMware Server:
[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

Dedoimedo

---

### Post by TrashmanL on 2009-01-25
This has absolutely nothing to do with 3D drivers, whatsoever. I put in the CD, ran wine from the terminal and it installed fine. It appeared to run fine, but if I tried to run the Single Player or Map Editor, it gave me that same error, saying it needed the original CD (for copy protection, I would imagine). If I ran the tutorial, however, it ran just fine. Some initial lag after the tutorial levels loaded, but other than that no problems. If it was a 3D driver issue, the tutorial would not have ran.

It has to be something to do with how AOE2 looks for the CD vs how it appears in wine. That being said, there are people who have run it successfully so I wonder what the configuration difference is.

---

