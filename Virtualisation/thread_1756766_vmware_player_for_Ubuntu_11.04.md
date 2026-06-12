---
title: "vmware player for Ubuntu 11.04?"
date: 2011-05-12
forum: Virtualisation
---

### Post by ChaosChris2009 on 2011-05-12
Is there a download of vmware player for Ubuntu 11.04 or a way to install it in Natty?

---

### Post by 67GTA on 2011-05-12
[http://downloads.vmware.com/d/info/desktop_downloads/vmware_player/3_0](http://downloads.vmware.com/d/info/desktop_downloads/vmware_player/3_0)

You will have to create a free account to download it. They won't spam you. Download 32 or 64bit according to what you need. Once downloaded you can install it by running ```
sudo sh VMware-Player-3.1.4-385536.x86_64.bundle
``` or ```
sudo sh VMware-Player-3.1.4-385536.x86.bundle
``` in a terminal depending on which one you downloaded.

---

### Post by ChaosChris2009 on 2011-05-12
> **67GTA said:**
> [http://downloads.vmware.com/d/info/desktop_downloads/vmware_player/3_0](http://downloads.vmware.com/d/info/desktop_downloads/vmware_player/3_0)

You will have to create a free account to download it. They won't spam you. Download 32 or 64bit according to what you need. Once downloaded you can install it by running ```
sudo sh VMware-Player-3.1.4-385536.x86_64.bundle
``` or ```
sudo sh VMware-Player-3.1.4-385536.x86.bundle
``` in a terminal depending on which one you downloaded.

I signed up and download it, but when I run the commands in terminal gives me this...

```
sh: Can't open VMware-Player-3.1.4-385536.x86.bundle

```

Same for both commands

:confused:

---

### Post by 67GTA on 2011-05-12
It may not need the sh prefix. Right click the vmware package and make sure it is set to be executable under properties. Then open a terminal and type sudo, then drag and drop the vmware package onto the terminal window and hit enter.

---

### Post by ChaosChris2009 on 2011-05-12
> **67GTA said:**
> It may not need the sh prefix. Right click the vmware package and make sure it is set to be executable under properties. Then open a terminal and type sudo, then drag and drop the vmware package onto the terminal window and hit enter.

This is what happens

```
sudo  '/home/chrisv/Desktop/VMware-Player-3.1.4-385536.i386.bundle' 
/home/chrisv/Desktop/VMware-Player-3.1.4-385536.i386.bundle: 110: Syntax error: newline unexpected

```

---

### Post by 67GTA on 2011-05-12
Which link did you download from? Googling that error found this thread: [http://kubuntuforums.net/forums/index.php?topic=3113411.0](http://kubuntuforums.net/forums/index.php?topic=3113411.0)
This is a weird bug! Try the "Manually Download" link.

---

### Post by ChaosChris2009 on 2011-05-12
> **67GTA said:**
> Which link did you download from? Googling that error found this thread: [http://kubuntuforums.net/forums/index.php?topic=3113411.0](http://kubuntuforums.net/forums/index.php?topic=3113411.0)
This is a weird bug! Try the "Manually Download" link.

Yeah, figured that out just now

When I looked at my Chrome downloads it was showing it as cancelled 

Downloading manually now.

^^

---

### Post by ChaosChris2009 on 2011-05-12
Now it's asking me for root permissions or access, something like that.

I really don't want to login as my root just to perform this install.

---

### Post by ChaosChris2009 on 2011-05-12
Never mind, resolved by logging in as root and installing that way.

---

### Post by 67GTA on 2011-05-13
Prefixing a command with "sudo" gives you temporary root privileges. Running as root can be messy. Glad you got it going.

---

### Post by Hulmemanitarian on 2011-06-24
I managed to get the vmware player going with the following command: sudo sh /home/myusername/downloads/VMware-Player-3.1.4-3 85536.x86_64.bundle

---

### Post by jackdale on 2011-08-02
```
sudo sh VMware-Player-3.1.4-385536.x86_64.bundle
``` did not work for me, but the following did:

```
sudo sh ./VMware-Player-3.1.4-385536.x86_64.bundle
```

go figure.:D

---

### Post by KennethBlok on 2011-08-24
Use chmod +x on the bundle to make it executable.

---

### Post by C.Ganesh on 2011-09-15
how do you open a file using sudo that is in file system/etc/apt? i basically want to modify apt.cnf to modify the proxy settings but it can be modified only by root......and ideas to unlock root is also appreciated :) i am a newbie so please explain jargons :D

---

### Post by dcstar on 2011-09-15
> **C.Ganesh said:**
> how do you open a file using sudo that is in file system/etc/apt? i basically want to modify apt.cnf to modify the proxy settings but it can be modified only by root......and ideas to unlock root is also appreciated :) i am a newbie so please explain jargons :D

Do not hijack threads that have nothing whatsoever with your issue. Start a new thread.

---

### Post by vhin_d_2005 on 2012-03-28
> **ChaosChris2009 said:**
> I signed up and download it, but when I run the commands in terminal gives me this...

```
sh: Can't open VMware-Player-3.1.4-385536.x86.bundle

```Same for both commands

:confused:

Try to change directory, go to the directory where your files has been saved... 

:p

---

### Post by howefield on 2012-03-28
Thread moved to "*Virtualization*" forum.

---

