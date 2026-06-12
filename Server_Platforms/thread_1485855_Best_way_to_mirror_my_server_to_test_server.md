---
title: "Best way to mirror my server to test server"
date: 2010-05-17
forum: Server Platforms
---

### Post by dacool25 on 2010-05-17
Hi there,

I'm running VMWare's ESXi to host my Ubuntu 9.10 server OS. I would like to create a new test OS that mirror's my current server however with a different hostname and ip address and was wondering what the best way of doing this was.

I know there's tons of ways to do this, whether it be rsync, tar'ing the drive, or just making a snapshot of the VM, but I was wondering what everyone's opinions are as to what the best way to do it is.

Thanks!

---

### Post by CharlesA on 2010-05-17
Can't you just export the VM, and import it but leave it disconnected from the network until you are able to change the hostname and whatnot?

---

### Post by dacool25 on 2010-05-17
Yes, that would be fine. But what I've forgot to mention is that I may want to put this on a different computer that isn't using VMWare products.

So for example, on my laptop I have Parallels running and can't really convert the image to make it work, so I may need to go inside the OS to create the backup of the OS.

---

### Post by CharlesA on 2010-05-17
> **dacool25 said:**
> Yes, that would be fine. But what I've forgot to mention is that I may want to put this on a different computer that isn't using VMWare products.

So for example, on my laptop I have Parallels running and can't really convert the image to make it work, so I may need to go inside the OS to create the backup of the OS.

In that case, I would suggest using clonezilla or dd to image the drive and then restore it to the other machine. If you use either of those, the drive on the machine that will receive the image must be at least as big as the one on the machine you are imaging.

---

