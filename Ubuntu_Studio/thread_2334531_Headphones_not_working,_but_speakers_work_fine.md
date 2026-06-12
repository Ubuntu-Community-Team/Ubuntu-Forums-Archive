---
title: "Headphones not working, but speakers work fine"
date: 2016-08-20
forum: Ubuntu Studio
---

### Post by adm6l on 2016-08-20
[h=2]Headphones not working, but speakers work fine[/h] 		 				 					 					 				 				 					 				 		 			 				[INDENT] 					yesterday everything was great, but today after booting up headphones failed to work.
ubuntu 16.04LTS on asus icore7

alsamixer
[[IMG]https://ubuntuforums.org/attachment.php?attachmentid=270760&d=1471689821&thumb=1[/IMG]]("https://ubuntuforums.org/attachment.php?attachmentid=270760&d=1471689821")
 added this to/etc/modprobe.d/alsa-base.conf :
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
..
still not working
All the info here > [http://www.alsa-project.org/db/?f=57...918185efbd9370]("http://www.alsa-project.org/db/?f=5704fcac009e8de0bb3db23f7b918185efbd9370")
..  
[/INDENT]



please help me fix it

---

### Post by howefield on 2016-08-20
Duplicate thread closed.

---

