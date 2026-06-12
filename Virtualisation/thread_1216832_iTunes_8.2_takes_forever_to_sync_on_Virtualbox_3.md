---
title: "iTunes 8.2 takes forever to sync on Virtualbox 3"
date: 2009-07-18
forum: Virtualisation
---

### Post by jepong on 2009-07-18
I created a windows xp guest os and allotted 512 RAM for it. Installation and running standard application is OK but when  try to sync my iPhone 3G and playlist it takes FOREVER to sync... i can't seem to find a virtualbox 3 workaround on google... is USB 2.0 already working in virtualbox 3?

pls help.

---

### Post by andrea000 on 2009-07-20
usb is if you installed the closed source and enabled guest additions.
You can download the closed source version on virtualbox's website.

---

### Post by jepong on 2009-07-20
i'm not using virtualbox-ose... i;m using virtualbox-3.0 from 'deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free'

---

### Post by andrea000 on 2009-07-21
usb is installed after you install guest additions but
you may also need to go to system administration
users and groups then unlock then manage groups and
then look for vboxusers dubble click it and make sure
you have a check by your user name.

---

### Post by jepong on 2009-07-21
made a successful sync last night but still slow. to make the process a little faster I disabled the iPhone backup and its much snappier right now.

I think the reason the music sync is slow is because of the shared folder from virtualbox to my \home directory. i notice that syncing downloaded application is much faster because the file is physically in the windows filesystem. 

I think my MSI Wind just can't support Win XP on virtualbox. Intel Atom and 1Gb memory is just not enough. :-)

---

### Post by jepong on 2009-08-09
looks like a possible fix...

[http://forums.virtualbox.org/viewtopic.php?f=7&t=18715&start=0]("http://forums.virtualbox.org/viewtopic.php?f=7&t=18715&start=0")

---

### Post by Reb on 2009-08-17
Is the cause of the problem poor USB speeds? That's mine, and the long sync times that go with them.

---

### Post by Reb on 2009-08-17
And furthermore, that workaround hasn't helped. I'll see if iTunes syncing all of the sudden got faster, but other USB activity (write to thumb drive) is still slow.

---

### Post by jepong on 2009-08-17
i think this is a virtualbox problem...:guitar:

---

### Post by m3alnemer on 2009-10-03
Try changing the resolution inside Windows to 800×600.

---

