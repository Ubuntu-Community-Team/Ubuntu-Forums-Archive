---
title: "Virtual Screen Size"
date: 2009-09-21
forum: Virtualisation
---

### Post by running_rabbit07 on 2009-09-21
Is there any way to make the virtual screen fill the screen or is this it? 

I am using the VirtualBox 3.0.6 on Jaunty 64 Bit.

Thanks for any and all help.

---

### Post by Joshua Lückers on 2009-09-21
Did you install the VirtualBox Guest Additions?

---

### Post by running_rabbit07 on 2009-09-21
> **Joshua Lückers said:**
> Did you install the VirtualBox Guest Additions?

Nope, Where do i find that?

---

### Post by running_rabbit07 on 2009-09-21
Ok, I found a tutorial on that. Thanks.

---

### Post by running_rabbit07 on 2009-09-21
If anyone finds themselves reading this because of the same need for a bigger screen.
This apparently does NOT work if you are running a 32 Bit client on a 64 Bit host.

Start VBox
Boot your client OS.
Click on Devices in the upper left corner.
Click Install Guest Additions.
This will place a disk on your virtual desktop.
Open a terminal.
Enter the following codes.
```
cd /media/cdrom
```If you are using 64Bit host.
```
sudo bash ./VBoxLinuxAdditions-amd64.run
``` If you are using 32Bit host.
```
sudo bash ./VBoxLinuxAdditions-x86.run
```Once the install is done you will have to restart the client and then you will have a much larger view.

---

### Post by littlemog on 2009-09-21
thanks it worked for me!

---

### Post by running_rabbit07 on 2010-01-06
Works every time.

---

