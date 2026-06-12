---
title: "Rock Xtreme X770 Ubuntu 9.10 64bit installation"
date: 2010-07-06
forum: Testimonials &amp; Experiences
---

### Post by dethorpe on 2010-07-06
Hi all, 
 
I've successfully installed Ubuntu 9.10 64bit on my Rock Xtreme X770 (1920x1200, Nvidia GTX7950 Go 512M, intel dual core 2, 4GB ram, DVD R/W, external Acer24" monitor)

I'd previously installed ubuntu desktop 9.04 on an old desktop to use as a house server. That went well, got mediatomb, funambol, teamspeak, mySQl, apache, samba all going & network access to my windows XP on the laptop set up as i wanted. Webmin was a very useful addition to help to setup the unfirmilier areas. So it was time to go the whole hog and go ubuntu on the laptop as well.

Got to say i was very impressed, all went fairly easily, just a  few bits that needed some extra work, which i was happy to do (although  as an experiences UNIX developer have a bit of an advantage there) and a couple of features (modem & fingerprint reader) not yet working but there things I don't use and could propably get working if I could spend the time on them.  Also slight proplum is that ACPI thinks its on battery all the time, but tweaks to power saving settings means that dosn't make any difference so can live with it until I can sort it out.

Thought I'd post the details of what I did in case its of help to any  others. basic rundown below, attached file for details of the install of  ubuntu and various applications and drivers. 
 
1) Backed up all my files to separate PC 
 
2) Used chkdsk, defrag and a bootable linux linix gParted cd to clean  up, prepare & partition the disk. I kept the existing windows  partition just cleaned it up as much as possible to free space. Then  setup a new linux partition and a new small windows partition in the  free space. 
  
3) used nLite to produce a striped down Win XP build and install that to  the small winXP partition, this is now my gaming partition used purely  for games so can keep it really clean and stripped down. The original  Win Xp partition I left untouched as a backup and so I could use  anything on there that I had trouble getting working in ubuntu 
 
4) The clean install of ubuntu was then done to the linux partition,  which is what is covered in the doc attached. 
 
Basically pretty much all worked OK, all the basics worked out the box,  GRUB was setup and worked so I could boot to ubuntu, original winXP  & new games winXP. Just a few bits and pieces needed some effort to  get working which is covered in the attached doc.  
 
Some Key points: ## use medibuntu ([http://medibuntu.org/](http://medibuntu.org/)) to install all  the media extras ##, without this had problems using media common file  types and playing dvds. I installed VLC as main media app is it pretty  much does everything. Installed Blueman Bluetooth app, which had much  better support for my N95 then the default, easily set up pairing and  Dial up 3G networking via bluetooth and USB using it. Used Nvidia propriety  drivers, they seem pretty good, supporting compiz for screen effects  and dual screen operation with my external 24" Acer monitor. 
 
At this point I still have the original winxp partition (although don't  use it as everything i need is now on ubuntu), next task is to wipe that  and make the space available to the linux install as an extra  partition. Will probably move things around to make a more sensible  partition layout, and then repair GRUB as expect this will cause it  problems.(full disk image back up first of course !!!) 
 
Only things not working are fingerprint reader, the internal modem  (which i don't use) & my medusa 5.1 USB headphones, they only  provide 2.0 at the moment. 
 
Hope this helps someone. 
 
Cheers 
  Craig

---

