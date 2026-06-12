---
title: "installation of multiple OS."
date: 2011-10-23
forum: Server Platforms
---

### Post by buntu2020 on 2011-10-23
Is it possible to install UBUNTU SERVER along with two order OS. I have UBUNTU 11.10 AND WIN 7 ON my laptop and I also want to install UBUNTU SERVER? How do I install it.

---

### Post by darkod on 2011-10-23
Yes. I also have dual boot of Win7 and Ubuntu, with added later Ubuntu Server for testing purposes.

First make sure you have empty unpartitioned space, which is easier to be created in advance either from within your Ubuntu or Win7, whatever you prefer. Then just do the Server installation as you would if it was the only OS.

If you are using GRUB as bootloader, make a decision which one to use, from Ubuntu or Server. I preferred to use the one from Ubuntu. In that case towards the end of the installation of the Server tell it not to install a bootloder. Then boot Ubuntu and run "sudo update-grub" and the Server installation will be recognized.

If you want to use the bootloader from the Server just let it install it, and it should find and recognize your Win7 and Ubuntu.

If the question is about the exact step by step procedure, there are plenty of manuals on Google. I can't tell you all the steps right now, I'm not installing server that often.

---

### Post by Vegan on 2011-10-23
If you are using several operating systems, virtualization might be a route to consider

---

