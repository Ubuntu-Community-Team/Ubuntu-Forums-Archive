---
title: "Problems with nvidia drivers only in last couple of days?"
date: 2015-04-15
forum: Ubuntu Development Version
---

### Post by jones-home on 2015-04-15
Have other people found that nvidia drivers have started having problems rendering Libreoffice and some Gnome games on unity (e.g. Swell Foop)?
I have found that Swell Foop is transparent and without background, also LO writer, calc etc are unable to render properly with thick black edges and black background in dialogues etc. This has only happended to me in the last few days. It seems to be occurring with drivers versions 349, 346 etc where everything was fine 2 days ago. 

I have reverted to nouveau and all is well (but slow and tearing a lot on my 2 monitor system, but that is how Noveau has always been). 

I am running an Nvidia Gefore GT 630 PCI-E card on an Intel Motherboard. Just want to know if it is a stage in the progress of vivid, that might get fixed tomorrow, or whether I have broken my system. If the latter I will try a clean install of Vivid. 

Thanks

Chris

---

### Post by dino99 on 2015-04-15
cant tell with unity as i only use gnome-shell; but using nvidia 346 is ok with that DE. Maybe test your system with a gnome-shell session: hit the lightdm cog to select it.

---

### Post by jones-home on 2015-04-16
Problem persists after today's update (which I note included jre). Problem with Fell Swoop occurs in Gnome flashback with metacity as well as with compiz, but not with Gnomeshell initially. However, it does occur when the settings dialogue is put up. 

The problem with Libreoffice is persists in all three desktop environments with both the repo version of LO and installing 4.4.2 from the LO website debs (64 bit).

If no one else is having the problem, perhaps I should try a clean install. Might wait a couple of days for that though.

Any more thoughts?

---

### Post by grahammechanical on 2015-04-16
To eliminate nvidia drivers as the cause of the problem, install an older nvidia driver. If Additional Drivers is only offering variants of the 346 and the 349 drivers then you might find 340 and 304 in the Software Centre.

If this is a recent install of vivid then you will not have many older kernels to try out. I have noticed on my long standing install of vivid that there have been 14 Ubuntu revisions to the 3.19 kernel as the kernel team respond to problems.

Regards.

---

### Post by jones-home on 2015-04-16
Many thanks to 9D9 and Grahammechanical. Your helpfulness is greatly appreciated. 

Problem with LO solved by deleting the libreoffice sub-directory in  ~/.config. So it must have been a setting in LO that I screwed up somewhere along the line. 
The gnome games transparency problem still happens though but this is not so important. Perhaps I should kick my swell foop habit anyway. 

The settings dialogue is inaccessible in these gnome games when running unity anyway. 

Anyway, thanks again.

---

