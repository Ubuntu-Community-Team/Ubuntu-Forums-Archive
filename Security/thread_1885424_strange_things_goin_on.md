---
title: "strange things goin on"
date: 2011-11-23
forum: Security
---

### Post by robire on 2011-11-23
Got a few strange things at my ubuntu 11.04
1. while login in I sometimes got error message popping up 'couldn't copy to ./'
But this appeared before clicking on anything. 

2.Installed KNemo, it is not starting up while loggin in
that is how I configured, and I updated the system and NO traffic was displayed !?!

3. Plugged in a few days earlier my easydisk 16 GB usb
was empty from one second to the other.
Disk Utility told me there is no filesystem at usb and is unformatted.
Reformatted the disk with vfat, got 16 GB dsplayed when plugin and at
Disk Utility.
But at other computers ( Mandriva ) tells me know there are just 14.1 GB
The size was displayed at both systems the same before that incident.
hmmm
robire

---

### Post by crazy bird on 2011-11-23
What are the specs of your computer? Can you provide that info too?

---

### Post by robire on 2011-11-23
It is a DELL inspiron N5040

---

### Post by robire on 2011-11-24
I just did the new updates ( Firefox )
and this time KNemo did display the trafiic
during update properly. 
But KNemo still has to be started manual.
I consider to reinstall ubuntu, but want to get some information
about the strange size change of my easydisk.
Just a reminder, it changed for no reasons at other Linux
Computers from 16 GB to 14.1 GB in Mandriva.
If I attach the usb stick and click at properties in ubuntu
it tells me 14.9 GB and in diskutility it tells me 16 GB.
I am supposed there must something be wrong with that usb stick ?
some hidden directories or files.
The other option is that the developers are unable to calculate the size
of a usb stick !?!
I really think that is not the case.
So how to get the real size now, and how to find what is hidden at this stick.
Is there anybody out there with some suggestions ?
robire

---

### Post by cariboo on 2011-11-25
This really doesn't belong here, but I'll answer it anyway.

To view the hidden files on your usb drive, open nautilus, navigate to the drive and press Ctrl-h. 

To find the total amount of space the files are taking up, open an terminal, cd to the device, and type:

```
du -h
```

---

### Post by robire on 2011-12-12
thanks a million.
sorry for being at the wrong forum,
but I was concerned about security of my system.
And that made me selecting this forum.
thanks again
robire

---

