---
title: "Recover SSH Settings"
date: 2018-09-24
forum: Security
---

### Post by chunkydrew2 on 2018-09-24
When I installed a new file server, I used Ubuntu Server 16.04. Using a guide I found on YouTube, I created shares for my desktops and laptops. I also setup SSH, so that I could move files easily between the server and the desktops/laptops. This worked well for some time. Unfortunately, due to health reasons, I didn't do this for 6+ months. Now, I've forgotten all my keys, and can no longer use SSH.
Is there a way I can recover my SSH settings, short of starting over from scratch

---

### Post by TheFu on 2018-09-24
backups?

---

### Post by SeijiSensei on 2018-09-24
Are you using shared keys or passwords?  If you use keys, everything you need should be in /home/username/.ssh/.  Note the leading period; it "hides" the directory so it won't show up in normal directory listings.  You can use "ls -a" to list hidden files, or enable their listing in your file browser of choice.  In KDE's Dolphin, for instance, hitting "Alt + Period" will toggle the display of hidden files.  I'm sure Nautilus and other file browsers have an equivalent switch.

If you use passwords, and have forgotten your password on the server, you can log in from its console and use "recovery mode" as explained here:

[https://websiteforstudents.com/reset-forgotten-ubuntu-user-password-on-ubuntu-16-04-17-10-18-04/](https://websiteforstudents.com/reset-forgotten-ubuntu-user-password-on-ubuntu-16-04-17-10-18-04/)

---

