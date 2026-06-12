---
title: "Putting the CD image on the HDD?"
date: 2010-04-27
forum: Server Platforms
---

### Post by stray on 2010-04-27
Here's a trick I'd like to be able to do. You know how on Windows systems, you can copy the contents of the install disk to a folder, then point the system at it and when it would normally ask you to insert your Windows CD, it just reads that folder?

That's pretty much what I want to do. I want to put the contents of the Ubuntu CD-ROM on the HDD such that if I ever need to refer to the CD, it thinks it's already inserted and just reads from there.

This may sound like an odd request, but I'm asking because my Linux server is an old cheapo computer that doesn't have an internal CD-ROM drive. I have one that I can hook up, but it's a pain in the butt to open the case, set the jumpers, attach the drive, reboot, etc. 

This would be a lot simpler for me. This way, if I ever need to access something that was on the Ubuntu Server CD-ROM, I want to be able to just get it from right on the hard disk. (I've got the drive space, after all.)

---

### Post by hopstah on 2010-04-28
What you want to do is set up a symbolic link.  Do some reading about the command ```
ln -s
```  It's very powerful and almost "tricks" the computer into thinking that something is located someplace else than it really is.  Let me know if this works for you.

---

### Post by ChadMMc on 2010-04-28
You can also try using gmount-iso which will take an ISO file on your hard drive and mount it on the system as if it is a CD or DVD... then you can access it all you want.

---

