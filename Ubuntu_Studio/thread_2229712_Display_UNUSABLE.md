---
title: "Display UNUSABLE"
date: 2014-06-14
forum: Ubuntu Studio
---

### Post by Ben_Cunningham on 2014-06-14
Hi Ubuntu Geeks,

I have a serious problem. I have a new workstation grade server (It's the ASUS TS100-E8-PI4 Server). I have Ubuntu 13.04 Desktop installed on it (I enjoy using the GUI) but I have a big problem with it. The graphics are UNUSABLE. I attached a photo so you understand.I found some drivers for the Graphics in the server, but they make 0 sense to me and the drivers only go up to version 12.04 of Ubuntu. Please help me because the GUI is totally unusable (refer to attached pics)

Hope you can help,
Ben Cunningham [ATTACH=CONFIG]253957[/ATTACH]

---

### Post by sudodus on 2014-06-15
If the drivers only go up to version 12.04 of Ubuntu, you may succeed better with that version of Ubuntu. It is an LTS version with support until April 2017, and it is well debugged and polished now. I think it is a good alternative, unless you need some special feature, that is only available in newer versions. Anyway, Ubuntu 13.04 has passed end of life, so it is not a good option anyway.

So download a desktop iso file of Ubuntu 12.04.4 LTS. I guess you want the 64-bit version.

If still no go, please tell us about the graphics chip. It might be very simple and not really made for a graphical desktop because it is a server. If you still want to use it with graphics you might need a graphics card. But before speculating about that, please specify the graphics chip/card!

---

### Post by Ben_Cunningham on 2014-06-15
[SIZE=4][FONT=century gothic]According to ASUS's website it uses a Aspeed AST1300 with 64MB VRAM graphics card. I got the drivers from ASUS's website and just found out that they can be used on Ubuntu 13.04. The OS is just not listed in ASUS's 'Supported Operating System's' List. I uploaded the drivers I got to OneDrive and you can have a look at them here: [http://1drv.ms/U0rqak](http://1drv.ms/U0rqak) . I had a look at the README, but it makes 0 sense to me. Hope you can help![/FONT][/SIZE]

---

### Post by sudodus on 2014-06-16
You should be able to run the batch file ***auto-update.sh***. Probably you need superuser privileges (sudo).

So in a terminal window change directory to where you have these files, and run

```
sudo sh auto-update.sh
```

But I suggest that you ***backup your data before***, because things like these are risky.

I remind you that Ubuntu 13.04 has passed end of life and will receive no security updates.

---

### Post by Ben_Cunningham on 2014-06-16
Okay, I'll give that a try.

---

