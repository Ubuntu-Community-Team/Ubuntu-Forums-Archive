---
title: "my first thoughts on Breezy"
date: 2005-08-19
forum: The Cafe
---

### Post by benplaut on 2005-08-19
I had broken my hoary install o a point where it was almost unusable, so i decided to try out breezy, and see what all the fuss is about.

first of all, i decided that i was going to not have it as my primary OS, ans partition as follows:

15gb /home 
1.7gb swap
10gb / breezy
13gb / hoary

i decided to do my Breezy install first, since i know that the hoary installer is quite good at resizing partitions, but had no ieda on the breezy one.

after a bit of wrassling with the partitioner (my mistakes, not it's),  i got my free space, swap, /home, and / worked out. i made one last check to make sure my 3 backup locations were OK (i'm a bit paranoid), and let the installer do its thing.

the system rebooted, and i was impressed at the new progress bar for the phase 2 part of the install, but was a bit worried that the resolution had changed between phases... i expected xserver problems.

at 91%, the installer... stopped. in tty4 it was failing to unpack something to do with language packs. when i was sure ti was frozen (ctrl+c just made it try to repeat the task), i ctrl-alt-del rebooted it. when it came back up, it was stuck in the same place in tty4 and the progress bar in the same place at tty1, however i was presented with a gdm login screen!

i logged in, and proceeded to try and find the culprit, or at least stop its progress. ps -a revealed that aptitude was running in the installer, so i killall'd aptitude (what did i have to lose? i had just reformatted...). i went back to tty1 and saw that, to my delight, it had gone on the registering package documentation. this, too, froze  :roll: . i rebooted, hoped for the best, and, sure enough, everything worked! my tty1 and tty4 were also back open  :grin: 

who knows what i broke by doing that, but, it's a test install! it's there for breaking!  :grin: 

i really like some of the improvements to Gnome in 2.11. The fully transparent panel is godsend, and metacity seems considerably faster (might just be gcc4). still trying to figure out how to install mouse cursors... the drag-n-drop doesn't work; it's not a big deal, but should be dealt with.

i hate the new icon theme, and, lucky for me, a new version fo NuoveXT came out... looks very good!

sound worked- amazing. the only thing that didn't work out of the box that i expected to was the mouse scroll wheel. luckily, it was a simple fix of the ZaxisMapping, and it was good to go. 

wireless, i am pleased to announce, is FIXED... madwifi can now scan  :grin: 

i still can't use GTKwifi due to a DHCP timeout that is too short, but the scanning from the gnome applet worked splendiferously (tm)  :grin: .

3d acceleration worked after a quick edit of xorg.conf, but i can't tell how much- glxgears (not installed by default, weird) won't give me any info  :roll: 

3D screensavers work well, so i guess it's OK  :)

still some bugs to iron out, but i haven't found many...

i think i'm just going to add the extra 13gb to my Hoary / :D

---

### Post by mrtaber on 2005-08-19
Great report!  I've been playing just a little with Breezy.  The little foxes that spoil the grapes?: no 'New Terminal' option on a right-click on the desktop, and the scroll wheel doesn't work on anything.  But it's shaping up real nicely.  I can't wait.

Mark :)

---

### Post by benplaut on 2005-08-19
[QUOTE=mrtaber]Great report!  I've been playing just a little with Breezy.  The little foxes that spoil the grapes?: no 'New Terminal' option on a right-click on the desktop, and the scroll wheel doesn't work on anything.  But it's shaping up real nicely.  I can't wait.

Mark :)[/QUOTE]

yeah... i forgot to add about the missing terminal...

Crossover Office isn't working... this is gonna need some work  :?

---

### Post by drizek on 2005-08-19
the panel is not fully transparent. task buttons still have a background and beagle in the systray is also not transparent. ive never used gnome for an extended amount of time before though, so i dont know if it was even worse before.

anyway, the human icon theme is very nice (IMO). did you try that or the defualt?

@mrtaber, look in the thread i posted "breezy kicks ass" in this section for the mouse scroll wheel fix.

oh, and no glxgears here either with i810 drivers. flurry and planetpenguin racer are VERY smooth, so i want to know how good this thing is at glxgears. i honestly did not expect such good performance from integrated graphics, especially on linux.

---

### Post by poofyhairguy on 2005-08-19
I also tried out Breezy today. My Enlightened Gnome was broke to hell, and I was bored. So I tried to dist-upgrade. Didn't work for me. Apt-get breakkage followed. So I downloaded the Colony 3 and installed it on my home partition.....and that didn't work. I'm posting this from a Windows install I use for maybe 5 hours a year.

I guess I shouldn't have played with fire. Why does the Breezy install CD need to download things off the internet to install? Is it automatic updates?

---

### Post by sapo on 2005-08-19
[QUOTE=poofyhairguy]I guess I shouldn't have played with fire. Why does the Breezy install CD need to download things off the internet to install? Is it automatic updates?[/QUOTE]

I hope that they fix the dhcp stuff in the installation process.. i ALWAYS had problems with crashes when searching for a network that i dont have.. a button "Would you like to search for a dhcp server" yes or no? would be perfect cause i always get stuck in it :p

---

### Post by poofyhairguy on 2005-08-20
[QUOTE=poofyhairguy]I also tried out Breezy today. My Enlightened Gnome was broke to hell, and I was bored. So I tried to dist-upgrade. Didn't work for me. Apt-get breakkage followed. So I downloaded the Colony 3 and installed it on my home partition.....and that didn't work. I'm posting this from a Windows install I use for maybe 5 hours a year.

I guess I shouldn't have played with fire. Why does the Breezy install CD need to download things off the internet to install? Is it automatic updates?[/QUOTE]

Yeah! I got it to work!

---

### Post by christooss on 2005-08-20
My expirience with breezy is preaty good. I see new icons for stuff :)

I upgrade it last week. I found it not so different from hoary.

I only have problem with aMule. It doesn't put tray icon in tray icons playe it opens nev window as small as icon. Everything else is working perfectly. For now :)

I m looking forward to new futures of Breezy.
BTW: I had to instal ubuntu-desktop to gain access to all breezy futures.
P.S. I scream in to the sky When is new gaim coming to breezy

---

### Post by jobezone on 2005-08-20
[QUOTE=christooss]My expirience with breezy is preaty good. I see new icons for stuff :)

I upgrade it last week. I found it not so different from hoary.

I only have problem with aMule. It doesn't put tray icon in tray icons playe it opens nev window as small as icon. Everything else is working perfectly. For now :)

I m looking forward to new futures of Breezy.
BTW: I had to instal ubuntu-desktop to gain access to all breezy futures.
P.S. I scream in to the sky When is new gaim coming to breezy[/QUOTE]
 So, how is gnome-app-install ? How does it feel and behave? Also, could you get me a .DEB package of it for me to try ;) ?

---

### Post by poofyhairguy on 2005-08-20
[QUOTE=jobezone]How does it feel and behave? Also, could you get me a .DEB package of it for me to try ;) ?[/QUOTE]

here it is:

[http://ftp.cs.umn.edu/pub/ubuntu/pool/main/g/gnome-app-install/gnome-app-install_0+20050816_all.deb](http://ftp.cs.umn.edu/pub/ubuntu/pool/main/g/gnome-app-install/gnome-app-install_0+20050816_all.deb)

Might not work on Hoary.

---

### Post by jobezone on 2005-08-21
[QUOTE=poofyhairguy]here it is:

[http://ftp.cs.umn.edu/pub/ubuntu/pool/main/g/gnome-app-install/gnome-app-install_0+20050816_all.deb](http://ftp.cs.umn.edu/pub/ubuntu/pool/main/g/gnome-app-install/gnome-app-install_0+20050816_all.deb)

Might not work on Hoary.[/QUOTE]
  Well, it doesn't work in Debian Unstable, it asks for a newer version of  python-gnome2-extras than available.

But have you tried it out? Could you tell how was your experience with it? Is it cooler and easier to use than Synaptic? More helpful? Or nothing special?

---

