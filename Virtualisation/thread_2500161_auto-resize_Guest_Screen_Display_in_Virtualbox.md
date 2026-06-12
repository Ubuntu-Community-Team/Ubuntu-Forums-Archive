---
title: "auto-resize Guest Screen Display in Virtualbox"
date: 2024-08-24
forum: Virtualisation
---

### Post by victorylap26748 on 2024-08-24
I have just installed Ubuntu VM on Virtualbox from Manjaro OS host machine.

It has properly installed BUT the auto-resize to full screen does not appear to be working properly. 

Forgive me I am a noob as far as Linux and virtual machines go.[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294125&stc=1[/IMG]

---

### Post by &amp;KyT$0P# on 2024-08-24
This requires VirtualBox Guest Additions installed in the Ubuntu guest (Devices > Insert Guest Additions CD Image).  Also, auto-resize doesn't always work at the login screen, you might need to login for the display to auto resize.

---

### Post by victorylap26748 on 2024-08-25
I seem to have the CD image up but I don't know what to do after this. I tried just clicking the 'run software' and it shown the terminal image you see and didn't resolve full screen issue.

---

### Post by &amp;KyT$0P# on 2024-08-25
Please post the output from running the following command in Terminal in the Ubuntu guest -
```
apt-cache policy bzip2 tar
```

---

### Post by victorylap26748 on 2024-08-27
I managed to complete the process from the terminal.

---

