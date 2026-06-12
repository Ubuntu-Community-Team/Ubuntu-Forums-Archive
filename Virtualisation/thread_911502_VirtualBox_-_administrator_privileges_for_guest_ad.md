---
title: "VirtualBox - administrator privileges for guest additions"
date: 2008-09-05
forum: Virtualisation
---

### Post by Lennerdie on 2008-09-05
Hello,

I'm new here, cause I'm looking for a solution for my problem.
I have already tried the solutions that were posted at this forum.

So, I have installed Ubuntu as a guest, but it's a very small screen. The solution is guest additions, but I can't install it!
Terminalwindow says: No administrator privileges to run this. Aborted

So, I have tried to typ the command in the terminalwindow, but that doesn't work either. A little bit frustrating, because I have all the administrator privileges.
If you have a solution, please reply to this post. 

Many, Many thanks.

---

### Post by Shazaam on 2008-09-05
Guest Additions gets installed inside the virtual machine. Start Virtualbox. Highlight Ubuntu in the main window, go to Settings>CD/DVD-ROM, check "Mount CD/DVD Drive", select "ISO Image File" and make sure the Guest Additions iso is there in the box.
Start the Ubuntu vm, open terminal in the vm. The terminal code for the Guest Additions install needs this first, then add the rest of the command to the same line...
```
sudo sh
```

---

### Post by Lennerdie on 2008-09-06
Thank You! Problem solved!

---

### Post by Tex786 on 2008-10-05
thanks

---

### Post by Tex786 on 2008-10-05
...

---

### Post by waleedakleh on 2009-02-19
> **Shazaam said:**
> Guest Additions gets installed inside the virtual machine. Start Virtualbox. Highlight Ubuntu in the main window, go to Settings>CD/DVD-ROM, check "Mount CD/DVD Drive", select "ISO Image File" and make sure the Guest Additions iso is there in the box.
Start the Ubuntu vm, open terminal in the vm. The terminal code for the Guest Additions install needs this first, then add the rest of the command to the same line...
```
sudo sh
```
hi i am knew in ubuntu can you specify more how to do that
after i open the terminal what should i type????
pleeeezzz help

---

### Post by konqueror7 on 2009-02-19
type it in the terminal and just drag the file into the terminal...

---

### Post by bodhi.zazen on 2009-02-19
In the guest , open a terminal

The additions should automatically mount at /media/cdrom

so ...

```
cd /media/cdrom
sudo ./VBoxAdditionsLinux-arch.sh
```

Sorry if I got the name of the script wrong , you can list the directory with ls if needed.

Then re-boot the guest.

---

