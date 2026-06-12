---
title: "Most successful DVD burning app"
date: 2007-05-27
forum: The Cafe
---

### Post by guitarmaniac on 2007-05-27
Whenever I wanted to backup a DVD in the past I used K9copy as it has the most intuitive interface from what I've seen.
However of late the majority of my DVDs fail to burn under K9copy.
What do you use to burn DVDs and how successful is it?

*disclaimer*
I only use DVD backup software to backup copies of DVDs I legally own. I use the burnt copy and leave the original in its case save it get scratched.

---

### Post by aidanr on 2007-05-27
i used to use xdvdshrink before changing to k9copy, k9copy has failed a few times so far, xdvdshrink has a lousy interface, is slower and a little bit harder to set up but never once failed

btw, if it's just the burning part that fails for you and not the ripping part, then you could rip to an iso first and then use gnomebaker or brasero or whatever to burn it

---

### Post by ramjet_1953 on 2007-05-28
I use K9 copy to shrink the DVD9 to DVD5, but had problems under GNOME with the auto-burn feature.

I just get k9Copy to make the iso and then burn it using k3b.

Works every time.

Regards,
Roger :cool:

---

### Post by guitarmaniac on 2007-05-28
this is what happens JUST as K9copy finishes making an ISO image of a DVD a crashes leaving me with nothing (and wasting a good half hour or more).

> (no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1241888112 (LWP 13143)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb77cf1a2 in k9DVDBackup::updatePgci_ut () from /usr/lib/libk9copy.so.0
#7  0xb77d1917 in k9DVDBackup::updateIfo () from /usr/lib/libk9copy.so.0
#8  0xb77d5ed0 in k9DVDBackup::execute () from /usr/lib/libk9copy.so.0
#9  0x0806425b in ?? ()
#10 0x0836f948 in ?? ()
#11 0xbfd61764 in ?? ()
#12 0x080a3d8c in ?? ()
#13 0xbfd6175c in ?? ()
#14 0xbfd61738 in ?? ()
#15 0x00000011 in ?? ()
#16 0xbfd61718 in ?? ()
#17 0x00000001 in ?? ()
#18 0x00003357 in ?? ()
#19 0x081a3d50 in ?? ()
#20 0x080b30c0 in ?? ()
#21 0x08316f80 in ?? ()
#22 0xbfd616d8 in ?? ()
#23 0xb6265bf0 in pthread_mutex_unlock ()
   from /lib/tls/i686/cmov/libpthread.so.0
#24 0x08080738 in ?? ()
#25 0x081a3b50 in ?? ()
#26 0x08225a78 in ?? ()
#27 0xbfd617c8 in ?? ()
#28 0xb6d13ab0 in ?? () from /usr/lib/libqt-mt.so.3
#29 0x080806e0 in ?? ()
#30 0x08225828 in ?? ()
#31 0xbfd61808 in ?? ()
#32 0xb684b88b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
Backtrace stopped: frame did not save the PC

any idea whats the go here?

---

### Post by orb9220 on 2007-05-28
Sorry but no ideas on that.

That is why I use DvDShrink and DVDecrypter thru wine.
[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)

It gives me the full ability to disable subs or max compress the extra's so I get the least amount of compression on main movie. Or I can reauthor and just rip main movie. Or I can rip a 2disc movie down to one using dvdshrink.

DVDecrypter allows me to rip movies with read error's that would make shrink choke. But then once it is on the HD then I use shrink to compress.

I find for me k3b sucks at burning 16x media on my 16x burner at only actual 4x and takes 15mins to burn. I can right click iso i made with shrink and nautilus burns it 8mins tops.

Also for me I find k9 takes 75-85 mins or so to rip when shrink will do it in 45-60 mins.  I find the burning programs still abit immature and missing features. I hope this changes for the good.


Go Figure.

---

### Post by guitarmaniac on 2007-05-28
WHOH, that guide is a tad out dated (I think it was using warty or something.
Dont wanna play around with config files in case things have changed in ubuntu since then.
Will look into using wine though as it seems the best option so far (sadly).
thanks for the info orb9220

---

### Post by guitarmaniac on 2007-05-28
OK, sorry its only a year old, but stuff has changed a lot since then.

---

### Post by orb9220 on 2007-05-28
Nope the guide is still valid today. Just used it a week ago.

---

### Post by mastergunner on 2007-06-30
Well I just tried using DVD Decrypter and Shrink and it doesnt work for me. I just keep getting errors and all sorts of issues. HELP HELP HELP!!!!

---

### Post by guitarmaniac on 2007-06-30
Yeah, I never did get it to work either. DVDShrink wouldnt install at all.

---

### Post by Polygon on 2007-06-30
> **guitarmaniac said:**
> Whenever I wanted to backup a DVD in the past I used K9copy as it has the most intuitive interface from what I've seen.
However of late the majority of my DVDs fail to burn under K9copy.
What do you use to burn DVDs and how successful is it?

*disclaimer*
I only use DVD backup software to backup copies of DVDs I legally own. I use the burnt copy and leave the original in its case save it get scratched.

i use gnomebaker and it has not failed on me yet.

I think part of the reason some dvd's fail is your cd/dvd drive, and if its on the verge of dying or the linux drivers for it are shaky

---

### Post by guitarmaniac on 2007-07-01
You can use Gnomebaker to backup movies now?

---

### Post by Polygon on 2007-07-01
what do you mean backup movies? as in ripping a DVD?

Gnomebaker can Copy DVD's, as well as burn data DVD's and DVD ISO's, but i dont think it can rip DVD's to like a certain format (like xvid or avi or w/e)

---

### Post by guitarmaniac on 2007-07-02
I need something that can shrink the DVD so it can fit on a regular 4.7GB DVD.

---

