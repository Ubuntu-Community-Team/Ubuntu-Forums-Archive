---
title: "Problem Administering Network Printers"
date: 2007-03-29
forum: Server Platforms
---

### Post by BirkBum on 2007-03-29
I am having a problem that I have not been able to solve. I have a media server with the Ubuntu-server installed on it. By using the forums I have been able to install my printer and can see it when I go to [http://localhost:631/printers](http://localhost:631/printers). I can even print a test page when I click the button on the page that pops up.

If I try to do any administration type tasks from the CUPS webpage...including clicking on the administration tab...it just jumps to a "403 Forbidden" message.

Also, I have accidentally installed the printer twice but when I try and delete one of the instances of the printer with the command:

```
sudo lpadmin -x Epson-R220
```

I get the message:

> lpadmin: Forbidden

I cannot view or install the printer in Vista. I have a file share set up on the same Ubuntu server the printer is attached to. I can write files to this from my Vista laptop and can use torrentflux etc. This leads me to believe that my samba settings should be ok...hopefully.

I have an Epson Stylus Photo R220 printer. I assume from these messages that there is a problem with the permission but between samba, cups, and Linux I have not been able to fix it myself. I am also struggling getting this part set up using only the command line.

If I need to post a file for anyone to be able to help I will do so. Thanks in advance. Once I finish this final step I will have the perfect media server.

---

### Post by elst on 2007-03-29
I don't know much about CUPS, but it sounds like something is broken in the configuration. I would have guessed that your account isn't a member of the relevent group, but the fact that it doesn't work with sudo suggests that it's not going to work at all with the current settings.

One simple trick - grab a copy of the "cupsys" package from your install CD or elsewhere, and open it with file-roller or any archiver. This will contain a pristine copy of all of the files, including all of the configuration files. The most important one is /etc/cups/cupsd.conf. You can then compare them with your current configuration, either by eye, or with a tool such as diff, and edit or replace. To replace configuration files: rename the existing file, copy the pristine version into place, and check that the permissions match.

---

