---
title: "Kubuntu 9.10 - ext3 or ext4"
date: 2009-10-06
forum: Server Platforms
---

### Post by infinitezero on 2009-10-06
I finally have the opportunity to change our SVN server over from Debian to (K)ubuntu 9.10 and was wondering if ext4 is stable enough for production use? I have read through most of the ext4 reviews but they are a little dated, most of them referring to 9.04 and the 2.6.28 kernel. Any thoughts?

Thanks,
iz

---

### Post by fjgaude on 2009-10-06
I've been using ext4 since Alpha 5, 9.10, and have had no issues with it. So...

---

### Post by cdenley on 2009-10-06
> **infinitezero said:**
> I have read through most of the ext4 reviews but they are a little dated, most of them referring to 9.04 and the 2.6.28 kernel.

Ubuntu 9.04 and the 2.6.28 kernel are not dated. They are the most recent stable versions available. Ubuntu 9.10 hasn't been released yet, and I wouldn't use it in a production environment just yet. When stability is important, I stick with LTS releases.

---

### Post by infinitezero on 2009-10-06
I did not mean that Ubuntu 9.04 was dated. I have not seen any crash test info from 9.10 or any other distributions that have a newer kernel version with ext4.

Thanks,
iz

---

### Post by cdenley on 2009-10-06
> **infinitezero said:**
> I did not mean that Ubuntu 9.04 was dated. I have not seen any crash test info from 9.10 or any other distributions that have a newer kernel version with ext4.

Thanks,
iz

Well any crash test involving a beta release of Ubuntu wouldn't be too useful, but I guess testing with a more recent release of a different distribution might be more relevant to the upcoming ubuntu release.

---

### Post by infinitezero on 2009-10-06
I was thinking unless the kernel version is going to be changed or some patches are going to be add that directly effect the kernel interaction with ext4 that crash testing the beta would be a great baseline. I have been running 9.10 on laptop since alpha 4 and not had a single issue. But that is a fare cry from running it on a production level server. I guess what I am getting at is if it is the default for the desktop then where does it stand with server use?

Thanks,
iz

---

