---
title: "Troubleshooting Hardware via Terminal"
date: 2017-11-16
forum: Virtualisation
---

### Post by cowboy.bebop on 2017-11-16
I work for a large computer manufacturing giant, and we handle mostly the business side of things (not consumer). The training we are provided with is strictly Windows and very little to no Linux troubleshooting at all. I am looking for material on how to better troubleshoot hardware like motherboard, memory, HDD, USB and Video to determine what it's defect is and why it failed to load during boot. Our scope is within Ubuntu strictly, but we have very little material on it. I feel like I am the only one in the center who has working knowledge in terminal and how to navigate it but not familiar with the troubleshooting portion. Any white papers or focus would greatly help. Thank you!

---

### Post by sgian on 2017-11-17
I don't know about white papers, but the logs are in /var/log so the first thing I check is usually the syslog with the command 
nano /var/log/syslog

Ubuntu usually has memtest installed to check the memory, although it might not come with server editions.  In that case you can just burn a live cd with memtest.  

For hard drives SeaTools used to be available on a live cd too, OS independent but I think that changed.  The legacy SeaTools or something similar might still be available to test hard drives with a live cd.

---

### Post by cowboy.bebop on 2017-11-17
> **sgian said:**
> I don't know about white papers, but the logs are in /var/log so the first thing I check is usually the syslog with the command 
nano /var/log/syslog

Ubuntu usually has memtest installed to check the memory, although it might not come with server editions.  In that case you can just burn a live cd with memtest.  

For hard drives SeaTools used to be available on a live cd too, OS independent but I think that changed.  The legacy SeaTools or something similar might still be available to test hard drives with a live cd.

Problem is, we have to work with the bare minimum. Lets say a CX comes in an says is not booting, but BIOS can detect the drive; the only tools we have to work with is terminal or a diagnostics test, but diags do not detect sensors or motherboard defects. I know linux has a variety of tools, other than dmesg and the grep to find strings in a log; to work with. But I am unfamiliar with these tools.

---

### Post by Bucky Ball on 2017-11-18
You possibly alreadly use it, but smartmontools will get you somewhere with hard drives. [Have a look here]("https://help.ubuntu.com/community/Smartmontools") if you don't use it.

---

### Post by cowboy.bebop on 2017-11-18
I have a VirtualBox set up with Ubuntu on it. Is there a way to tamper with the hardware commodity's within the virtual environment to create sort of a test lab to troubleshoot these hardware issues from terminal?

---

### Post by QIII on 2017-11-18
Moved to virtualization, as your questions can only be addressed within the context of the VM.

I'm sure someone will come along with some specific answers for tools, but be aware that the only hardware the VM will have access to will be contained in the hardware abstraction layer provided by VirtualBox.  That is, what you can work with will be limited and you will not be able to do much to "see" the physical hardware.

---

