---
title: "Viruses, windows apps, emulators, and WINE"
date: 2010-08-22
forum: Security
---

### Post by andrewcd on 2010-08-22
Hi All,

I am a non-specialist using ubuntu (10.x) as my primary machine, installed on a lenovo X200 laptop.

I'd like to know if windows viruses threaten an ubuntu machine, or the files saved on the ubuntu-formatted hard drive, if those windows viruses are introduced to the system through an emulated Windows XP machine running in VirtualBox.  I have guest additions set up, so the virtual machine can access, save, and delete files through what it "thinks" is a network (Z) drive.  

Intuitively, it seems like a risk.  But I don't really understand well what viruses do or how they work, so I would appreciate any advice.  I don't care if the virtual machine becomes corrupted, but I want my main machine (and the files saved on it) to be safe.  

I would also like to know if windows viruses threaten a system if they are accessed via WINE.  I was never able to get WINE working in 9.x, and I have not tried since upgrading to 10.x.   

Thanks

---

### Post by Sub101 on 2010-08-22
Heres an article about Viruses in Wine; [http://www.linux.com/archive/feed/42031](http://www.linux.com/archive/feed/42031)

---

### Post by andrewcd on 2010-08-23
***Apologies for cross-posting (in absolute beginner talk)***

 			 			 		   		 		 		Hi All,

I am a non-specialist using ubuntu (10.x) as my primary machine, installed on a lenovo X200 laptop.

I'd like to know if windows viruses threaten an ubuntu machine, or the  files saved on the ubuntu-formatted hard drive, if those windows viruses  are introduced to the system through an emulated Windows XP machine  running in VirtualBox.  I have guest additions set up, so the virtual  machine can access, save, and delete files through what it "thinks" is a  network (Z) drive.  

Intuitively, it seems like a risk.  But I don't really understand well  what viruses do or how they work, so I would appreciate any advice.  I  don't care if the virtual machine becomes corrupted, but I want my main  machine (and the files saved on it) to be safe.  

I would also like to know if windows viruses threaten a system if they  are accessed via WINE.  I was never able to get WINE working in 9.x, and  I have not tried since upgrading to 10.x.   

Thanks

---

### Post by cariboo on 2010-08-23
Windows viruses have no affect on a system running a Linux variant. If you are running wine, the only thing malware will affect is the wine partition.

Please don't cross post, I have merged your two threads.

---

### Post by uRock on 2010-08-23
> **andrewcd said:**
> Hi All,

I am a non-specialist using ubuntu (10.x) as my primary machine, installed on a lenovo X200 laptop.

I'd like to know if windows viruses threaten an ubuntu machine, or the files saved on the ubuntu-formatted hard drive, if those windows viruses are introduced to the system through an emulated Windows XP machine running in VirtualBox.  I have guest additions set up, so the virtual machine can access, save, and delete files through what it "thinks" is a network (Z) drive.  

Intuitively, it seems like a risk.  But I don't really understand well what viruses do or how they work, so I would appreciate any advice.  I don't care if the virtual machine becomes corrupted, but I want my main machine (and the files saved on it) to be safe.  

I would also like to know if windows viruses threaten a system if they are accessed via WINE.  I was never able to get WINE working in 9.x, and I have not tried since upgrading to 10.x.   

Thanks
If the Windows VM has permissions to alter files on the drive, then it can ruin them, but the Virus would not be able to harm any files that the VM doesn't have permissions to write to.

To say it simply, an infected Windows VM can only alter files in the "Z drive" and nothing else.

---

