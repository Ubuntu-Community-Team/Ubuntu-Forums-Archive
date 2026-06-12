---
title: "[SOLVED] Converted Ubu7.04? to UbuCE Now Firefox Not Connecting??"
date: 2007-11-27
forum: Ubuntu Christian Edition
---

### Post by ChrisNZ on 2007-11-27
Hi Im new to Linux and very happy with it so far... :)
However with the lasted update or rather "convert" to CE My Firefox will not connect to the net via the Icon bar or menu bar start buttons. However checking a start/link from Dansgaurdian for example takes me to a "workable FF browser!
I've checked the network defaults and they 'seem' to be ok for NZ Kiwionline ISP- DansGrdn is 'FF Proxy locked' and enabled - but still will not connect:confused:

Have noted others have had the bookmarks gone but fixed this with backup copy and dont think this will affect anything?

Please can anyone help with this "simple problem":(

TIA and blessings

Chris

---

### Post by tak1150 on 2007-11-27
In firefox, when you go

Edit --> Preferences --> Advanced --> Network --> Settings,
What do you see there?

Do you have a router?
What do you get when you type "route -n" in the terminal?

---

### Post by ChrisNZ on 2007-11-27
Arrrgghh! This has just got worse!
In an effort to test Linux Systems I ran Ubu 7.04 Live disk.. and it worked OK.
However when I shut down and removed disk... boot up on dualboot screen select - UbuCe will not startup!

I get the splash screen then the Cursor Icon and a black background. It's taken me hours to figure a work around so I had to go into my Windows 98 and run FireFox from there and email etc...

I'm currently looking at the last fix I had for the Blk screen issue and try to fix again then see about FF and UbuCE!

Unknown when Ill be able to get email so may take some time.

The admin network is set to direct internet... as is was in Ubu 7.04

---

### Post by tak1150 on 2007-11-28
> **ChrisNZ said:**
> Arrrgghh! This has just got worse!
In an effort to test Linux Systems I ran Ubu 7.04 Live disk.. and it worked OK.
However when I shut down and removed disk... boot up on dualboot screen select - UbuCe will not startup!

I get the splash screen then the Cursor Icon and a black background. It's taken me hours to figure a work around so I had to go into my Windows 98 and run FireFox from there and email etc...

I'm currently looking at the last fix I had for the Blk screen issue and try to fix again then see about FF and UbuCE!

Unknown when Ill be able to get email so may take some time.

The admin network is set to direct internet... as is was in Ubu 7.04

I'm sorry to hear that. I noticed that I do get a black screen w/ Gutsy once in a while at some random time. But if I wait ~ 5min or so it just boots up on its own. The first time it happened it was scary. This never happened with Feisty. Strange...

---

### Post by ChrisNZ on 2007-11-28
Thanks...

I tried the commands sudo nano /etc/gdm/gdm.conf-custom but it comes back with not found or I can get a "Dos" type screen... then what!
I'm not so hot on Linux coding but make backup notes for referance how I fixed things :)

I still get the dual boot menu with the 'old' kernal Ubu 7.04 - but it it ends with a error15 code and backs up to dual Boot screen, so only access is to 'UbuCE' recovery mode. I see all the stuff fly by it just makes me 'fume' a bit :)

Blessings
Chris

---

### Post by tak1150 on 2007-11-28
> **ChrisNZ said:**
> Thanks...

I tried the commands sudo nano /etc/gdm/gdm.conf-custom but it comes back with not found or I can get a "Dos" type screen... then what!
I'm not so hot on Linux coding but make backup notes for referance how I fixed things :)

I still get the dual boot menu with the 'old' kernal Ubu 7.04 - but it it ends with a error15 code and backs up to dual Boot screen, so only access is to 'UbuCE' recovery mode. I see all the stuff fly by it just makes me 'fume' a bit :)

Blessings
Chris

The text editor nano may not be installed by default, I'd use vi or vim.
You may consider installing 7.10 then using the convert-me script that Jereme makes to turn it into CE. 7.10 comes with bullet-proof-X, meaning it should somehow get you to a GUI desktop even if there is something wrong with the video driver.

---

### Post by ChrisNZ on 2007-12-09
> **tak1150 said:**
> The text editor nano may not be installed by default, I'd use vi or vim.
You may consider installing 7.10 then using the convert-me script that Jereme makes to turn it into CE. 7.10 comes with bullet-proof-X, meaning it should somehow get you to a GUI desktop even if there is something wrong with the video driver.

Thanks to all who replied with possible fixes. In the end I took it to a linx IT guy and pleaded my case! :confused:
 As a result I'm now on to [COLOR="SeaGreen"]**Linux Mint**[/COLOR] I think its
based on 7.10 Gutsy.. ...And yes it came with Pidgin installed.

Blessings and Merry Christmas to you all.

---

