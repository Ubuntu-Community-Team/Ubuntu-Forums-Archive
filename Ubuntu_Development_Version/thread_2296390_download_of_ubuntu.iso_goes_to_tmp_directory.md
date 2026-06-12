---
title: "download of ubuntu.iso goes to /tmp/ directory??"
date: 2015-09-25
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-09-25
I had just downloaded the daily-current ubuntu wily desktop .iso and it goes to some sort of /tmp/ file where there are all these systemd private files. I did this on a fully updated 15.10 ubuntu-desktop install.

---

### Post by VMC on 2015-09-25
How did you download it? If from your browser , then check download location.  Ex. Chrome is under advance settings: *[COLOR=#303942][FONT=Droid Sans]Download location:[/FONT][/COLOR][COLOR=#303942][FONT=Droid Sans] [/FONT][/COLOR]*

---

### Post by ventrical on 2015-09-25
> **VMC said:**
> How did you download it? If from your browser , then check download location.  Ex. Chrome is under advance settings: *[COLOR=#303942][FONT=Droid Sans]Download location:[/FONT][/COLOR]*

I use ff. It has always defaulted to /Downloads until now. I dragged it from /tmp/ to desktop and got a successful install to usb.

regards..

edit:

I'll check out your suggest  next time I swap out.

---

### Post by ventrical on 2015-09-25
> **VMC said:**
> How did you download it? If from your browser , then check download location.  Ex. Chrome is under advance settings: *[COLOR=#303942][FONT=Droid Sans]Download location:[/FONT][/COLOR]*

Something is busted somewhere ... but it does not appear to be ff.

---

### Post by VMC on 2015-09-25
Try and click on "**Always ask me where to save files**", and then when you download, select your "/home/download" folder and see if it works.
Also, is you "/home" and root "/" on the same partition. If not, how full is your "/home" partition?

---

### Post by mc4man on 2015-09-25
If one attempts to open a down-loadable file instead of saving a down-loadable file then it is downloaded to /tmp

---

### Post by ventrical on 2015-09-25
> **mc4man said:**
> If one attempts to open a down-loadable file instead of saving a down-loadable file then it is downloaded to /tmp

I just clicked on the download file/save.  I'll try again and see what happens. Also thought it could be a nautilus bug.

regards..

---

### Post by VMC on 2015-09-25
I'm unsure what you mean, but if you open link as the image shows, it downloads to Downloads folder:

[IMG]http://i.imgur.com/cY124Qd.png?1[/IMG]

---

### Post by ventrical on 2015-09-25
Found problem. I have no idea how this got configurated this way, but it did.

Thanks you guys for your help.

---

