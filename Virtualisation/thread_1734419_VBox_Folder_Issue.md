---
title: "VBox Folder Issue"
date: 2011-04-20
forum: Virtualisation
---

### Post by Warthaug on 2011-04-20
I installed vbox (current windows 32bit version, plus the extension to support USB) on my wifes vista laptop, for the purpose (if you can believe it) of playing some linux games.  I installed xubutu into vbox, without issue, and installed the guest additions.

At first glance, things appear to have worked properly - xubutu is installed and boots properly, the guest additions appear to function (mouse capture is working, screen size can go above 800X600, etc).  However, shared folders are not mounted, and when I click on the shared folders icon on the bottom of the vbox screen, or select it in the drop-down menus, I get an error stating that the guest additions have not been installed and thus the shared folders are not mounted.  Reinstalling guest additions did not fix the problem.

I've read through a lot of pages, but not been able to find anyone else with this exact issue.

Anyone know why this has happened, and how to fix it?

Thanx

Bryan

---

### Post by Warthaug on 2011-04-21
I have found a solution, sort of.  While it appears that issues with shared folders is common in xfce, you can mount them manually.  Simply create a directory in your home folder to mount to, then enter into the terminal:

```

sudo mount.vboxsf sharename ~/sharename 
```

where sharename is the name you gave to the folder on the host, sharename is the folder in your home folder.


B

---

