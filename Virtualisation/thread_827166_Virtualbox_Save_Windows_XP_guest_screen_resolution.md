---
title: "Virtualbox: Save Windows XP guest screen resolution"
date: 2008-06-12
forum: Virtualisation
---

### Post by CRMcMullen on 2008-06-12
I've got VirtualBox 1.6.2 installed on a Ubuntu 8.04 host.   Running Windows XP SP3 in VM.   I prefer to use a screen resolution of 1440x900x32 for my guest and can easily set this using:

VBoxManage controlvm [xpGuestName] setvideomodehint 1440 900 32

HOWEVER, I have to do this every time, as the default resolution of 1024x768 is how it starts at bootup.  Is there any way to save the 1440x900 screen resolution properties so that my VBox WinXP guest will start that way every time?

---

### Post by linux6994 on 2008-06-12
I have it running as well on Hardy. Under Machine on the top bar look at Install Guest addtions. These help with screen resolution.

---

### Post by CRMcMullen on 2008-06-12
Going to "Devices" and installing Guest Additions was the first thing I did.  I believe that's what allows me to change the resolution to 1440x900 with VBoxManage to begin with, but I'm not sure.   At any rate, additions are installed.

No problem changing the resolution from within Terminal, just want to be able to save them once they're changed so I don't have to manually resize every time.

---

### Post by Ubeaut on 2008-06-12
There's a new way to fix this, outlined in my posting #19 in this other thread:

[http://ubuntuforums.org/showthread.php?t=720709](http://ubuntuforums.org/showthread.php?t=720709)

---

### Post by CRMcMullen on 2008-06-13
Thanks for the setextradata info ... that fixed my problem and permanently assigned my screen resolution to my Windows XP guest.

---

