---
title: "RAID 1 Issues - Ubuntu Server 9.04 Jaunty"
date: 2009-08-18
forum: Server Platforms
---

### Post by danooch13 on 2009-08-18
Hello everyone, 

I am fairly new to Linux (about 1 year or so).  I have a few linux servers in my house (DNS, DHCP, Samba, FTP, Web server, all running on 3 different computers).  I have been in the Windows administration area for about 10 years.  

Anyway onto my problem.  I started using ubuntu because I wanted to see what all the fuss was about with this Linux stuff and it has been great, up until I attempted to create a fileserver.

I have a fakeraid setup with a rosewill raid controller with two 500 gig drives in a raid 1 array.  When I first installed ubuntu, everything was ok.  It was working and the raid bios did not report any issues.  One day the machine froze up (not sure from what yet, still trying to figure out if it is a bad motherboard or psu), and after that for the past 2 weeks the bios still reports that the raid array is in the rebuild status.  If I have raid in here I want it to work correctly, but cant seem to get the raid bios to state that the raid array is ok.  Every dmraid command I try to rebuild it, it says that the array is not in the rebuild state.  

Any ideas as to why the bios states that it is always in the rebuild state?

---

### Post by danooch13 on 2009-08-18
Any ideas?

bump

---

### Post by ewook on 2009-08-18
Just pondering, but since you have a 'fakeraid', isn't there a rebuild in the bios for the fakeraid?

---

### Post by fjgaude on 2009-08-18
Could it be a bad drive? If the BIOS says it is rebuilding then it thinks something is wrong, having nothing to do with Linux. That's the way I see it now.

---

### Post by danooch13 on 2009-08-18
Maybe I am misunderstanding the term fakeraid.  I have two 500 gig sata drives connected to a rosewill pci sata raid controller.  In the bios of the controller, it has a rebuild option, but when I try to do it, it says that the array cannot be rebuilt, even though on the POST for the raid controller, it says that the array is in the rebuild state.

In other words, if I understand you right you are telling me to tell it to rebuild from the controllers bios, which it does not allow me to do.

---

### Post by danooch13 on 2009-08-18
fjgaude,

Funny you say that, I thought that too, so I bought a third 500 gig drive and mixed and matched the drives (this one with that one, that one with this one etc), and reinstalled ubuntu each time.  For a while it would work, then as soon as a crash happened, because I had a bad motherboard (possibly), the damn bios will always say it is in the rebuild state.

Although, when I type sudo dmraid -r, it says that both mirrors are ok, and sees both drives.  In other words, it always sees both drives and never gets read or write errors.

---

### Post by danooch13 on 2009-08-19
Just found out last night after some prodding around that the problem was a bad motherboard.  It seemed to be turning itself on and off.  I just ordered a new motherboard/processor combo from ebay.

Do you think that this could cause the issue?  The bios should not always say rebuilding, right?  How long do you think it should be rebuilding for a 500 gig mirror?

---

### Post by Registered2read on 2009-08-20
For a mirror of 500GiB I'd say around 3 hours. My mirror of 5 GiB takes around 2'. It's of course very dependent of the drives performance.

If I were you I'd not use the fake raid on the motherboard, it doesn't offer anything in term of increased performance. Using exclusively soft raid may make your boot experience more complex though - like when there is a bug in the raid boot code.

---

### Post by danooch13 on 2009-08-20
I am not sure I am understanding what you are saying, you are saying not to use the rosewill raid controller card (by the way they are terrible because they dont have there own processors, but thats another story, nor do I want to spend alot of money for one with a processor).

What do you recommend I do, my motherboard does not have any sata ports, which is why I use the card?  

I guess I could use ide drives...

What do you recommend, because this array has been in the rebuild status (according to the raid bios) for about 3 days now!

---

