---
title: "Virtualbox doen't see USB devices"
date: 2010-05-16
forum: Virtualisation
---

### Post by eekfonky on 2010-05-16
Hello

I have installed Virtualbox 64 bit 3.1.8 in Ubuntu 10.04 and have checked the filter boxes in USB devices on the setup but still it doesn't see them?

What am I doing wrong?

---

### Post by thebigob on 2010-05-16
sound like exactly the same problem I had have a look here

[http://ubuntuforums.org/showthread.php?t=1484000](http://ubuntuforums.org/showthread.php?t=1484000)

---

### Post by eekfonky on 2010-05-16
I tried that and it rendered my system unbootable. It said 'there was a problem mounting USB' S to skip or M to manually mount.

How do I fix that?

---

### Post by Pengwyn44 on 2010-05-16
You must add User(s) to the "vboxusers" Group.

Go to System &#8594; Administration &#8594; Users & Groups. Click on Advanced Settings, 
then OK, wait 5 seconds, then click on “Manage Groups”

Scroll through the list of group names until you find “vboxusers” then 
click on it to highlight and click on the “Properties” button. You'll 
see a list of users on your system. Check off all the users who you will 
want to give access to VirtualBox. Do NOT check off “root”. After you've 
made your changes, click "OK" and then close groups settings and user's settings.

Then re-boot lucid lynx.

It worked for me!

Pengwyn44

---

### Post by eekfonky on 2010-05-16
After restart it worked, thank you

---

