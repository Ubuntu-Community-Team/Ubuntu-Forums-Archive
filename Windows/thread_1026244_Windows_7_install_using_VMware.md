---
title: "Windows 7 install using VMware?"
date: 2008-12-30
forum: Windows
---

### Post by djb6 on 2008-12-30
So i have a few questions.  I'm working on installing windows 7 on my computer with VMware.  Now I've gotten to the point where it sees the CD, reads it, and starts the program.  But my questions are this:

1) Using VMware, will this install wipe out my main operating system?

2) I have the blank VMware file in my partition where I want Windows 7 installed.  Does that mean that when I click the install now button, it will install in that partition?  I don't have the option of choosing the drive letter.

---

### Post by Sand &amp; Mercury on 2008-12-31
> **djb6 said:**
> So i have a few questions.  I'm working on installing windows 7 on my computer with VMware.  Now I've gotten to the point where it sees the CD, reads it, and starts the program.  But my questions are this:

1) Using VMware, will this install wipe out my main operating system?

2) I have the blank VMware file in my partition where I want Windows 7 installed.  Does that mean that when I click the install now button, it will install in that partition?  I don't have the option of choosing the drive letter.

1) Nope, VMware won't touch anything outside of the virtual hard drive you created for it

2) I'm not quite sure I follow, but when the W7 installer gives you a list of partitions to install to, you should only have one, and that will be the aforementioned virtual hard drive. Just go ahead with that and you should be fine.

---

### Post by rickyjones on 2008-12-31
Are you doing this within VMWare (as in you boot your virtual machine and it is booting off the CD) or are you booting your physical machine and trying to get it to install into the virtual hard drive?

Two very different things.

You should create your virtual machine in VMWare then either attach the ISO to the virtual machine or connect the virtual machine to your CD/DVD drive.

Thanks,
Richard

---

### Post by djb6 on 2008-12-31
Yeah I got it to work.  Thanks for the help!

---

### Post by rickyjones on 2008-12-31
> **djb6 said:**
> Yeah I got it to work.  Thanks for the help!

You're welcome :)

---

