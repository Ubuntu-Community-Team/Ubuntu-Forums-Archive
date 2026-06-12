---
title: "Users mess-up."
date: 2010-10-30
forum: Security
---

### Post by cboxhero on 2010-10-30
I just got GIMP 2.6 and I wanted to put all these awesome new brushes on it, but the thing is, Ubuntu won't let me add files and/or extract files into there. It's saying I don't have permission. I'm the only account on this computer though. Any help? I'm so confused right now. :(

---

### Post by uRock on 2010-10-30
You need to be root to move files into the root directory. To open folders as root, open a terminal and enter ```
gksudo nautilus
``` but be very careful what you do in this mode as moving, altering and/or deleting files will be permanent.

Reading and understanding the content of [this link]("https://help.ubuntu.com/community/RootSudo") should aid in understanding how root level permissions are important and how they are used to protect your system.

---

### Post by cboxhero on 2010-10-30
Thank you, but how to I get it to where it stays that way?

---

### Post by uRock on 2010-10-30
You mean that you want the GUI to have root permissions at all times? The link I posted above explains how to do that. Scroll down the page to the Enable Root Account section. You can't miss it.

I advise against it, as Linux's way of setting up accounts is why there are very few problems with malware.

---

### Post by PhilGil on 2010-10-30
> **cboxhero said:**
> Thank you, but how to I get it to where it stays that way?
The nautilus window you open as root will remain root until you close it. You don't want nautilus to stay that way permanently. Privilege elevation is fundamental to the Linux security model - nothing can run as root unless you explicitly permit it. Entering your password on occasion is (IMHO) a small price to pay.

---

### Post by cboxhero on 2010-10-30
Alright then, thank you very much. I will be thinking about it.

---

### Post by sisco311 on 2010-10-30
User settings are stored in the user's home directory, so if you want to install brushes for your user add the files to ~/.gimp-2.6/brushes/ (.gimp-2.6 is a hidden directory in your user's home, you may have to press Ctrl+H to list hidden directories). 

If you want to make system wide changes you need root permission.

---

