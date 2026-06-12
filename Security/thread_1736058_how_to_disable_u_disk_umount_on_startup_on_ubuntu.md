---
title: "how to disable u disk umount on startup on ubuntu"
date: 2011-04-22
forum: Security
---

### Post by allenxuyong on 2011-04-22
Dear all,
For security propose,we are disable u disk storage in our environment(Ubuntu10.04 LTS x64 ),do as follow:
1.delete u disk drives at /lib/modules/kernel/drivers/usb/storage/*.*
2.disable u disk storage modules be connect : blacklist usb-storage >> /etc/modprobe.d/blacklist.conf
3.dischoose  media_automount on& open in gconf-gedit
/apps/nautilus/preferences/media_automount 
/apps/nautilus/preferences/media_automount_open
and all client withdraw  root privilege,the problem seems solve.
but we find if u disk connect to PC before system start,after Ubuntu logon,the u disk willbe mount automatically.
i also edit /lib/udev/rules.d/ 80-udisks.rules and make change as follow:
# from here on, we only care about block devices
ACTION!="add|change", GOTO="udisks_end"
SUBSYSTEM!="block", GOTO="udisks_end"
KERNEL=="ram*", GOTO="udisks_end"
**GOTO="udisks_end"**

But it not take effect, any body help many tks... We only need disable u storage function,other communication needed for work.

---

### Post by cipherboy_loc on 2011-04-22
If the disk is in FSTAB, append the option **noauto**, but I don't fully understand what you are trying to do. 


Cipherboy

---

### Post by allenxuyong on 2011-04-24
Hi:
Yes ,i mean that we need disable the usb-storage function on all client,just usb-storage,
other function(such as usb communication) shuld be used for work.
1.delete usb-storage driver 
2.add usb-storage modules to black-list 
but,if i connect Usb disk to PC,and then start OS,the usb-storage willbe mount automatically,then i do form 1-2 activity.How to fix this problem??Many thks!

---

### Post by cipherboy_loc on 2011-04-24
You might try:

[http://www.cyberciti.biz/faq/disable-linux-unix-gnome-automounting/](http://www.cyberciti.biz/faq/disable-linux-unix-gnome-automounting/)
and
[http://ubuntuforums.org/showthread.php?t=1675343](http://ubuntuforums.org/showthread.php?t=1675343)

But if all else fails, try this:
[http://lmgtfy.com/?q=ubuntu+disable+usb+automount](http://lmgtfy.com/?q=ubuntu+disable+usb+automount)



Cipherboy

---

### Post by allenxuyong on 2011-04-27
Tks  for your reply.
1.I am already disable automount removiable devices in gconf-editor which the same as 
[http://www.cyberciti.biz/faq/disable...-automounting/]("http://www.cyberciti.biz/faq/disable-linux-unix-gnome-automounting/")
but the problems seems solve now as 
[http://ubuntuforums.org/showthread.php?t=1675343](http://ubuntuforums.org/showthread.php?t=1675343) said DVD disk automount
2.I have already solve this problem,our propose is disable usb storage function in Ubuntu.
i am uninstall usb storage module at system start. just add 
"rmmod -f usb_storage" to /etc/rc.local,or add this command to /etc/grub.d/00_header,at beginnig of content.

Best regards!):P

---

