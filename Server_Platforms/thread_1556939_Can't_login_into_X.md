---
title: "Can't login into X"
date: 2010-08-20
forum: Server Platforms
---

### Post by xendistar on 2010-08-20
Yesterday I installed 10.04 LTS onto a new server, I then installed the xubuntu desktop. I installed a few other packages and rebooted a couple of times without a problem.

I started the server up this morning and I can't login, it boots to a X login screen (as it did yesterday) but when I enter the users password, it just says authentication failed. I did not have this problem when I rebooted yesterday and there is only the one user on the system. 

But if I select xterm from the session type I can login with the same username and password, so I guess this is a permission thing on starting X. One of the jobs I intended to do today was to set the boot up to boot to CLI, can somebody confirm it is a permissions problem and what I need to do to rectify and what I need to edit to make it boot to a CLI

Thanks in advance

Tim

---

### Post by xendistar on 2010-08-21
OK, I have resolved the booting to CLI, I can also confirm that the users can not startX from the CLI I have to sudo to startx. But as I want the option to be able as a normal user to boot to GUI and be able to login, can anybody confirm what permission the user needs to have to be able to login and startx???

For the record I altered the line in grub file by adding the word "text"

Tim

---

### Post by LightningCrash on 2010-08-21
check perms on X

ls -la /usr/bin/X

should be
-rwsr-sr-x

---

### Post by xendistar on 2010-08-22
It has those permissions, thanks

Tim

---

### Post by LightningCrash on 2010-08-22
try a login, then ls -ltr /var/log

look through the recent logs

Although if xterm is working it might be something else, like a home directory permissions problem.

---

### Post by xendistar on 2010-08-23
Thanks for the advice, although I can access the server in a round about way and do what I need to do I do need to resolve the issue and will add it to my to do list.

Tim

---

