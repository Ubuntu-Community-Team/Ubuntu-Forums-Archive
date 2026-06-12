---
title: "Shared Folders - network path not found"
date: 2008-04-11
forum: Virtualisation
---

### Post by gambrjl on 2008-04-11
Ok.  I've got virtualbox installed and working with a Windows XP installation as a guest and what I'd like to do is this..

share my /home/user/Music folder with the Guest so that I can use MediaMonkey to manage my music and sync it with my Creative Zen (I just like the way mediamonkey handles it).

First of all I'm having trouble getting sharing to work at all.  I tried first with an empty folder that I created just to test using the documentation [here](https://help.ubuntu.com/community/VirtualBox)

```

#mkdir ~/vboxshare
#VBoxManage sharedfolder add "Windows XP" -name "share" -hostpath ~/vboxshare

```

It then shows up under shared folders when I start virtualbox.  Then when XP is all booted up I fire up a dos prompt and do

```

net use x: \\vboxsvr\share

```

and get

*System Error 53 has occured.  The Network Path was not found*

What am I doing wrong?

---

### Post by gambrjl on 2008-04-11
Doh.. I thought since I had a shared folders option I already had guest additions installed..  so I'll update this for those that 

to add Guest Additions go to 

Devices -> Mount CDDVDROM -> CD/DVD-ROM Image

then navigate to

/usr/share/virtualbox

and you'll see VBoxGuestAdditions.iso

choose that and you're off to the races.  Sorry for the post

---

### Post by seijling on 2008-10-09
Well, this post helped me!  Thank you!

---

### Post by ruru on 2008-10-21
Thanks - this helped me too!

---

### Post by dnick on 2009-10-15
thanks again)

---

### Post by gbmaizol on 2013-03-26
Thanks dude!


> **gambrjl said:**
> Doh.. I thought since I had a shared folders option I already had guest additions installed..  so I'll update this for those that 

to add Guest Additions go to 

Devices -> Mount CDDVDROM -> CD/DVD-ROM Image

then navigate to

/usr/share/virtualbox

and you'll see VBoxGuestAdditions.iso

choose that and you're off to the races.  Sorry for the post

---

### Post by wildmanne39 on 2013-03-26
Thread closed. Please do not post in old threads.

---

