---
title: "Ubuntu 10.04 File server and powerdown"
date: 2012-04-13
forum: Server Platforms
---

### Post by deepakdeshp on 2012-04-13
I am looking to build a file server with Ubuntu 10.04 server edition.


[LIST=1]
[*]I am looking for a compact box to house a P4 3 GHZ equivalent CPU , 2 GB ram and 250 GB IDE hdd. (SATA disks are costlier)
[*]It should have Samba, NFS, UPnP and DAAP and other useful software to have for a file server.
[*]The power switch when pressed briefly should power down the server in the proper sequence.
[/LIST]
Any suggestions for point 1,2 and 3 would be welcome.

---

### Post by 2F4U on 2012-04-13
3. I installed acpi on my 10.04 server and this automatically performs a shutdown when I press the power button.

---

### Post by Jonathan L on 2012-04-13
> **deepakdeshp said:**
> I am looking to build a file server with Ubuntu 10.04 server edition.


[LIST=1]
[*]I am looking for a compact box to house a P4 3 GHZ equivalent CPU , 2 GB ram and 250 GB IDE hdd. (SATA disks are costlier)
[*]It should have Samba, NFS, UPnP and DAAP and other useful software to have for a file server.
[*]The power switch when pressed briefly should power down the server in the proper sequence.
[/LIST]
Any suggestions for point 1,2 and 3 would be welcome.

Hi Deepakdeshp

For home purposes I have had very good mileage out of a little Acer nettop computer and 10.04 server, running Samba, NFS, Apache and so on; but not any audio.  The model is Acer Aspire Revo 3610.

It's 2 GByte RAM, 250 GByte disk, and the CPU scores 631 at [http://www.cpubenchmark.net/midlow_range_cpus.html](http://www.cpubenchmark.net/midlow_range_cpus.html)  (P4 at 3.46 GHz scores 610 ).  It's almost inaudible even with your ear next to it and is low power, so I leave it on continuously.  But the power switch does work.

Perhaps that helps.

Kind regards,
Jonathan.

---

### Post by deepakdeshp on 2012-04-14
> **Jonathan L said:**
> Hi Deepakdeshp

For home purposes I have had very good mileage out of a little Acer nettop computer and 10.04 server, running Samba, NFS, Apache and so on; but not any audio.  The model is Acer Aspire Revo 3610.


Perhaps that helps.

Kind regards,
Jonathan.

Thank you Jonathan. One more thing is that I do not need even the display. SO if I keep a desktop without a monitor the solution is much cheaper but the desktop box is bigger .

---

### Post by Jonathan L on 2012-04-14
Hi again Deepakdeshp

> I do not need even the displaySee attached long-serving Cisco wifi and router and on top the server.  Ruler is 30cm.  Authentic "never-gets-touched" dust.  I chose this particular computer for its size and in particular its power usage, which I remember measuring as something like 25 W.

For another project I used an Intel [SIZE=1]D945GSEJT [/SIZE]motherboard (inside industrial IP 66 housing) which I can recommend too.  Mini ITX which is only 170 mm square, passive cooling, 12V-only supply.  But only SATA: you might save more on the PSU than the SATA margin though.  If you're looking to build something, you might find this is a good place to start.
[http://www.silentpcreview.com/article987-page1.html](http://www.silentpcreview.com/article987-page1.html)
[http://www.homeserverhacks.com/2009/06/hands-on-whs-build-with-intel-d945gsejt.html](http://www.homeserverhacks.com/2009/06/hands-on-whs-build-with-intel-d945gsejt.html)
[http://www.intel.com/content/www/us/en/motherboards/desktop-motherboards/desktop-board-d945gsejt.html](http://www.intel.com/content/www/us/en/motherboards/desktop-motherboards/desktop-board-d945gsejt.html)

Kind regards,
Jonathan.

---

### Post by CharlesA on 2012-04-14
Can I give a +1 to the nettop? Those things sip energy and give you quite a bit of bang for the buck.

You might also want to consider how much total disk space you want to have for the file server, 250GB is not all that much.

---

### Post by oldwindows geek on 2012-04-14
Hi Deepakdeshd, I may get booted from here, but heres a little program that you should look at for your file sever!  it's FreeNas, a linux mix, with lots of options!):P

---

### Post by CharlesA on 2012-04-15
> **oldwindows geek said:**
> Hi Deepakdeshd, I may get booted from here, but heres a little program that you should look at for your file sever!  it's FreeNas, a linux mix, with lots of options!):P
FreeNAS is BSD based, so it's not exactly Linix (but it is UNIX-like). In any case you won't get booted for mentioning alternatives. ;)

---

### Post by Gyokuro on 2012-04-15
> **deepakdeshp said:**
> I am looking to build a file server with Ubuntu 10.04 server edition.


[LIST=1]
[*]I am looking for a compact box to house a P4 3 GHZ equivalent CPU , 2 GB ram and 250 GB IDE hdd. (SATA disks are costlier)
[*]It should have Samba, NFS, UPnP and DAAP and other useful software to have for a file server.
[*]The power switch when pressed briefly should power down the server in the proper sequence.
[/LIST]
Any suggestions for point 1,2 and 3 would be welcome.

Maybe a HP ProLiant N40L Micro server suite your needs. ([http://h10010.www1.hp.com/wwpc/us/en/sm/WF06b/15351-15351-4237916-4237918-4237917-4248009-5153252-5153253.html?dnr=1](http://h10010.www1.hp.com/wwpc/us/en/sm/WF06b/15351-15351-4237916-4237918-4237917-4248009-5153252-5153253.html?dnr=1))

and it has more power as an Atom box and do not take a lot juice.

---

### Post by rubylaser on 2012-04-15
The Microservers are awesome small file servers. A single drive isn't of much use to me as a fileserver, but the Microservers have 4 hot swap bays. And, if you want to go crazy, you can put alot more than just 4 drives in that case.

They are very power efficient and make great SOHO fileservers.

---

### Post by Jonathan L on 2012-04-15
[FONT=Arial][SIZE=1]Hi All

[/SIZE][/FONT]  [FONT=Arial][SIZE=1]> **rubylaser said:**
>  Microservers have 4 hot swap bays

These look very nice indeed, though are you quite sure they're hot swap bays?[/SIZE][/FONT][FONT=Arial][SIZE=1]
[/SIZE][/FONT] [FONT=Arial][SIZE=1]
[http://h18004.www1.hp.com/products/quickspecs/13716_na/13716_na.html](http://h18004.www1.hp.com/products/quickspecs/13716_na/13716_na.html) says:

[/SIZE][/FONT][FONT=Arial][SIZE=1]Maximum Internal Storage     [/SIZE][/FONT][FONT=Arial][SIZE=1]Non-Hot Plug SATA     [/SIZE][/FONT][FONT=Arial][SIZE=1]8TB (4 x 2TB) 3.5" SATA

Kind regards,
Jonathan.[/SIZE][/FONT]

---

### Post by rubylaser on 2012-04-15
> **Jonathan L said:**
> [FONT=Arial][SIZE=1]Hi All

[/SIZE][/FONT]  [FONT=Arial][SIZE=1]

These look very nice indeed, though are you quite sure they're hot swap bays?[/SIZE][/FONT][FONT=Arial][SIZE=1]
[/SIZE][/FONT] [FONT=Arial][SIZE=1]
[http://h18004.www1.hp.com/products/quickspecs/13716_na/13716_na.html](http://h18004.www1.hp.com/products/quickspecs/13716_na/13716_na.html) says:

[/SIZE][/FONT][FONT=Arial][SIZE=1]Maximum Internal Storage     [/SIZE][/FONT][FONT=Arial][SIZE=1]Non-Hot Plug SATA     [/SIZE][/FONT][FONT=Arial][SIZE=1]8TB (4 x 2TB) 3.5" SATA

Kind regards,
Jonathan.[/SIZE][/FONT]

Yup, you are correct, the bays are not hot swappable.  I was thinking about the 4 2.5" SATA bay adapters that are hot pluggable that many people use in their Microservers.  For most users that won't be a big deal at all, though, and doesn't detract from the HP's very useful specs.

---

