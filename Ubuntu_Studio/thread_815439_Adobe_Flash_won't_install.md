---
title: "Adobe Flash won't install"
date: 2008-06-01
forum: Ubuntu Studio
---

### Post by cyclonedr on 2008-06-01
Hi all,
  So I've installed Ubuntu on a USB external hard drive with Grub installed on that drive.  I've fought with my WUSB54GS v2 wireless adapter getting that to work, which I've done successfully, but I can't for the life of me get flash to install.  I started by going to the command prompt and typing the following: sudo apt-get install flashplugin-nonfree, press enter and it would download, but then I'd get an error saying flash not installed.  Then I went through firefox, I think version 2.0.0.6, went to YouTube found a random video and clicked install missing plugins. Then got an error that said flash was already installed.  Back in the Synaptic package manager I removed flash and went back through firefox.  This time it seemed to install, but after restarting firefox I still got the missing plugins error.  I typed in about:plugins and there was no entry for flash.  What can I do?  Thanks for any suggestions

---

### Post by Hozza on 2008-06-01
make sure you are conected to the web, ubuntu says it is when its not (with wifi). - go to google and type in somethin

if it still wont install try locating all of the files that install with flash, delete them manually.

then reinstall flash - there is probably a better way to do it though 8)

---

### Post by cyclonedr on 2008-06-01
Well, I know my wifi works because I'm typing this in Ubuntu.  I'm not sure what file would be associated with flash after it's uninstalled

---

### Post by Hozza on 2008-06-29
go in to synaptic package manager

and find the program your looking for, right click it and click Full Removal

then re-install it

---

### Post by Tomatz on 2008-06-29
When you install flash check in the folder */home/**YOUR-USER-NAME**/.mozilla/plugins* for the file **libflashplayer.so**

---

