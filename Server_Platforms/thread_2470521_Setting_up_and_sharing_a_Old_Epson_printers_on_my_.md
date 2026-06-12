---
title: "Setting up and sharing a Old Epson printers on my Home LAN"
date: 2022-01-02
forum: Server Platforms
---

### Post by johndid on 2022-01-02
Hi,

I'm a new Ubuntu Server user, and I'm trying to figure out how to set up and share my old Epson Stylus SX420W printer plugged via USB to my notebook with Ubuntu server 20.04 LTS installed on it (No GUI).

I have been looking up several articles on the internet but still confused about how to get the job done exactly. Some say that I need to install its linux driver, others say that I only need CUPS instead. Since I'm anything but a linux expert, I am still confused about what to do and I don't want to mess up with my system.
Could you please give me some hints about what would be the best way to do it?
For the record, I already installed Samba to share a few folders and it works fine
Thanks

---

### Post by Tadaen_Sylvermane on 2022-01-02
Cups is pretty easy. Just apt install it. Drivers may be the problem though. Personally I've always had difficulty with Epson. Just something to keep in mind. Cups is configured via web browser, not standard gui app.

---

### Post by johndid on 2022-01-03
I think that I found them here:
[https://download.ebz.epson.net/dsc/search/01/search/searchModule](https://download.ebz.epson.net/dsc/search/01/search/searchModule)

I don't think I got the difference between these ones:

[TABLE="class: searchResTbl"]
[TR]
[TD]Stylus SX420W
[/TD]
[TD]Printer Driver[/TD]
[TD]Linux
[/TD]
[TD]latest[/TD]
[TD]ESC/P Driver (full feature)[/TD]
[TD]
[/TD]
[TD][/TD]
[TD] 			
[/TD]
[/TR]
[TR]
 			[TD]Stylus SX420W
[/TD]
 			[TD]Printer Driver[/TD]
 			[TD]Linux
[/TD]
 			[TD]1.7.17[/TD]
 			[TD]ESC/P-R Driver  (generic driver)
[/TD]
[/TR]
[/TABLE]

---

### Post by johndid on 2022-01-03
I installed printer-driver-gutenprint via command line, then I launched the setup from CUPS in my Windows PC brower. 
The Epson printer was recognized at once and my Windows 10 PC can see it in my LAN and use it to print documents.

However, it seems that they are some issues with printing image (the text is ok) as you can see here:

[IMG][[IMG]https://images2.imgbox.com/9d/1d/0C4ZN6S8_o.jpg[/IMG]]("https://imgbox.com/0C4ZN6S8")[/IMG]

Text is ok, but there is something wrong with the images (I print another page in Words with a little image and some text. I got the same result).
Is it because I didn't install a proper driver? Can I fix the problem by changing something in CUPS?
Thanks

---

### Post by johndid on 2022-01-03
Ok. I did it.
I had to install the epson linux deb file driver. I deleted the old setup in CUPS, added my Epson printer again with the new driver and everything works fine now.
Thanks

---

