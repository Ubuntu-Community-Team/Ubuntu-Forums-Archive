---
title: "PXE Boot results in &quot;Installation step failed&quot;"
date: 2010-09-03
forum: Server Platforms
---

### Post by sd_read on 2010-09-03
I have set up Ubuntu to install over the network. 

I did this by copying the directory contents of /install/netboot/ from the CD over to my tftp server in the correct directory.

It works and I can go through a good part of the install process. 

I get to the point where it tells me the kernel is installed and to check what applications I would like. I forget the exact wording.

So, I check Ubuntu desktop and it continues on and then pops up a red screen that says:

"Installation step failed
An installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is: Select and install software."

I have tried this on two different machines with the same result.

I am not able to figure out what I am doing wrong?

Thank you for your help.

---

### Post by uRock on 2010-09-03
Did you test the ISO before adding it to the PXE server?

---

### Post by sd_read on 2010-09-03
I discovered that it did not install because the drive was too small. I guess I expected it to tell me there wasn't enough space. 

So, I installed a larger drive and chose the Ubuntu desktop install and everything completed fine.

However, when I rebooted I was greeted with a command prompt and no GUI?

So, now my question is how do I do a PXE install so it behaves like installing from a CD with a GUI?

---

