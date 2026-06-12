---
title: "New User warnings"
date: 2015-08-30
forum: Ubuntu, Linux and OS Chat
---

### Post by bob146 on 2015-08-30
Greetings to my fellow new users to Linux
 
 I really want to just warn my fellow new users of a couple of things here.
 
 Namely do not be afraid to experiment with Ubuntu desktop –
 I have been a user of Ubuntu for a long time now first time I tried it I lasted maybe 5 days and went back to windows.  Yeah I know.   I was in my 40's when I went to college for the first time for IT  Technology and then ended up opening my own business for computer repairs and designing and implementing home networks.  But I digress 

 I have always come back to Ubuntu again and again over the last few years a little bit here and a little bit longer there,   My point here is keep that cd or usb  nearby – YOU WILL need it again ..lol and if any of you EVER think about making a root log on thats okay   but DO NOT under any means do what I did and remove the passwords to my user account and the root.... remember I said you will need that installation cd/usb this will cause it to be one of those times, you can not unloc the user accounts if you dont have a password.  I.E.  no password no new user to fix what you have done and now access to your current users.   See I warned you!    We really need a Support group so we can compare the dumb things we try and do and succeed at, that goodness for this forum!!

 now my want to be  Linux user self must be off to make even more mistakes..:D

---

### Post by grahammechanical on 2015-08-30
So, this is not a request for support? Or even something for discussion? It is in the wrong section of the forum.

---

### Post by deadflowr on 2015-08-30
Not support.
Moved to [B][I]Ubuntu Linux and OS chat


[/I][/B]

---

### Post by bob146 on 2015-08-30
I knew i had to screw something else up today.....     Sorry about that

---

### Post by andrew257 on 2015-09-01
It's true.  I fudged the kernel earlier today while messing with display drivers.  I guess you don't learn until you break something.

---

### Post by QIII on 2015-09-01
Create a virtual machine.  Take snapshots. 

Destroy that system frequently just for kicks.  Restore the snapshot, see what you learned.  Repeat.

---

### Post by Irihapeti on 2015-09-02
I remember a couple of crazy things I did during the first few months of my Ubuntu journey.

One involved wanting to remove all backup files from the top two levels in I don't exactly recall where. Only, I ended up removing *every file* in said directories, which included some essential stuff for the system to run. :oops:

The second time, I thought I'd change the owner of /usr and subdirectories to root. Only, not everything in those directories is mean to belong to root. :oops: :oops:

Hey ho, time to reach for the BACKUP — which fortunately did what it was supposed to do. :D

---

### Post by Skaperen on 2015-09-02
*testing* your backups is a good thing.

---

### Post by Irihapeti on 2015-09-02
> **Skaperen said:**
> *testing* your backups is a good thing.

Agree. A backup that won't restore is no better than no backup at all.

Mine have been tested a fair few times now. :)

---

### Post by pauljw on 2015-09-02
> **QIII said:**
> Create a virtual machine.  Take snapshots. 

Destroy that system frequently just for kicks.  Restore the snapshot, see what you learned.  Repeat.

+1 on the vm suggestion.  I recommend that most users install the latest LTS version of Ubuntu, keep it updated and only install software from the repositories as they have been thoroughly tested for compatibility.  Then install virtualbox and put another instance of your os in vbox. Take a snapshot of the basic updated virtual machine.  Now you can play to your hearts content digging in as deeply as you dare with the knowledge that not only is your stable every day host system safe but your vm is easily returned to day 0 should you do something that breaks it.

---

### Post by v3.xx on 2015-09-02
I take it one step further and say VirtualBox for a VM.  It gets good support here and myself (and others) think it is the better choice for running desktop VMs.  There is a bit of a learning curve, but well worth it.  This all assumes your box can run it.

Ubuntu can also be ran as a minimal install.  This will give you the building blocks that a lot of linux is based on.

Enter the test box :D  An old piece of junk single core; half of gig of ram ( or 256) set up just to play with.  Buy a KVM switch and hook it up to your existing monitor/keyboard/mouse and switch between the two.

---

