---
title: "Disk error"
date: 2017-05-12
forum: Windows
---

### Post by danielsender on 2017-05-12
I have a vintage Dell M50 laptop with two disks installed. I have on HD (sda) Windows 7 and on the bay drive (sdb) Ubuntu 16.04. Grub is installed on sdb and the BIOS is configured to sequence sdb first. So when I start the machine the grub window appears, if I select Ubuntu then there is no problem, but if I select windows it comes back with the message "Disk Error, press Alt-Ctl-Delete to restart" (or something like that). On the other hand, if I press F12 during the start up, and I select HD (sda) rather than the bay drive (sdb), then windows starts without problem. Is there anything that can be tweaked in grub to overcome this problem?

Thanks in advance.

Daniel

---

### Post by mdurham on 2017-05-12
Try booting into Ubuntu, open a terminal and entering:  sudo update-grub
then reboot and try to boot windows again.
Cheers, Mike

---

### Post by danielsender on 2017-05-13
I did that already three times but the problem persists. I also ran the Boot Repair Disk without success. It's strange, since sda boots perfectly when selected from the BIOS.

Thanks.

---

### Post by Yellow Pasque on 2017-05-13
See if disabling this in Windows helps: [https://www.tenforums.com/tutorials/4189-turn-off-fast-startup-windows-10-a.html](https://www.tenforums.com/tutorials/4189-turn-off-fast-startup-windows-10-a.html)

---

### Post by danielsender on 2017-05-14
That link pertains to windows10, I have windows7 - would that be equivalent process?

---

### Post by howefield on 2017-05-14
Thread moved to the "*Windows*" forum.

---

### Post by Yellow Pasque on 2017-05-14
No I don't think Windows 7 had fast shutdown.

---

### Post by danielsender on 2017-05-14
I forgot to mention one more piece of information. The sda disk (windows 7) is a SSD PATA (not SATA) if that would make any difference.

---

### Post by yancek on 2017-05-15
In post 3, you indicate that you have boot repair.  This software has an option to Create BootInfo Summary which you should use.  It should give you a link to post here so that members can view the output.  Someone will probably be able to point you in the right direction.

---

### Post by danielsender on 2017-05-16
Yes, I should have done that when I was able to run that tool. But now it doesn't even run, so I'm concluding that is very likely that one or both of the memory modules are bad. So I'm ordering a new set. I will post the results once I replace them.

Thanks.

---

