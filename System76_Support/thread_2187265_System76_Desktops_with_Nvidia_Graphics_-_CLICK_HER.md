---
title: "System76 Desktops with Nvidia Graphics - CLICK HERE!"
date: 2013-11-11
forum: System76 Support
---

### Post by isantop on 2013-11-11
There is a bug in Ubuntu's OEM setup where if you ordered your system with Nvidia graphics, but plugged your monitor into the motherboard's video ports, it will irreversibly break the OEM setup and prevent you from creating an initial user account. 

To prevent this, make sure you always plug the monitor into the ports on the video card. They're horizontal, and located below the rest of the ports. 

If you have already plugged the monitor into the incorrect video ports (the vertical ones above), then you can fix the problem by reinstalling Ubuntu, or by using recovery mode:

[LIST=1]
[*]Turn your computer off.
[*]Ensure that the monitor is plugged into the correct video ports.
[*]Turn the machine on, and wait for the first purple screen to appear. Once it does, press the reset button on your computer immediately. (The reset button is the smaller button with the upside down triangle)
[*]When the machine starts back up, it should present you with a GRUB menu. Select "Advanced Options for Ubuntu", then choose the first item in the list labeled with "(Recovery Mode)" at the end.
[*]When you see the recovery menu, choose the "root" option.
[*]Enter the following commands:
```
mount -o remount,rw /
adduser user
```

Substitute in your desired user name in for "user". This can be anything with lowercase letters or numbers. Then enter the information the system asks for. You only need to enter a password and a Full Name.
[*]Next, run these commands:
```
adduser user sudo
adduser user adm
exit
```
Remember to use the same username for "user" that you used before. 
[*]From the recovery mode menu, choose the "Resume" option. 
[*]Log in to the computer using your new account, then set the time zone, language, and keyboard layout (if needed) from System Settings.
[/LIST]

If you have any questions, feel free to let us know by calling us or opening a support ticket on our website. You can open a support ticket from the link in my signature below.

---

### Post by RichardET on 2014-05-07
Was this "bug" ever fixed?  This thread is a few months old.

---

