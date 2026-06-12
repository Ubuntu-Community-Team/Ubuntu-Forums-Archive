---
title: "Basic Security and Permissions"
date: 2008-05-23
forum: Security
---

### Post by Breetai on 2008-05-23
I'm constantly running into basic permissions issues that I haven't been able to figure out the logic too.  I've installed Ubuntu and I only have one account I open up the synaptec manager and enter my password and everything is good.  But when I try to edit the grub menu or the xorg.conf file I go to the file open it make my changes hit save and it says I don't have permission.  Sometimes I've seen the same problem in the terminal functions, It doesn't ask for a password it just says I don't have permission and I can't make whatever change it is I need to make.  

What am I doing wrong and how do I get around that stuff?

Thanks
Russ

---

### Post by sisco311 on 2008-05-23
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

To edit the xorg.conf:
```
gksu gedit /etc/X11/xorg.conf
```This command will run the text editor as root.

gksu and sudo will give you super user permissions.
Use gksu or gksudo for GUI applications and sudo for the text based ones.

---

### Post by whoop on 2008-05-23
If you want to edit a file like menu.lst or xorg.conf you need administrative rights. If you just open your editor you will have the rights of your current account. To open menu.lst with write access f.i. you need to open a terminal and type "sudu gedit" this gives your editor (gedit) super user permissions. You can launch basically any application like this. To start a command line editor you could type "sudo nano" for instance.

Hope this helps.

---

### Post by kamaji792 on 2008-05-25
> **whoop said:**
> "sudu gedit" this gives your editor (gedit) super user permissions.

I know you got it right later but just to confirm the command should be:

sudo gedit

You will then be asked for your password.

The nice thing about "sudo" is that if you do another sudo command shortly after it will not ask you for your password.

---

