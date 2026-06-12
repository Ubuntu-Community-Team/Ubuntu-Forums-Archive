---
title: "Power saving"
date: 2007-10-28
forum: Server Platforms
---

### Post by maxbear on 2007-10-28
I installed server edition to run my file server at home. This server won't use all the time. I would like to know how can I set power saving in server edition. Can I spin down the harddisk after certain period of time if there is no activities?

---

### Post by MJN on 2007-10-28
You can indeed spindown the hard disk, however if you've only got the one disk you will likely find it is relatively constant use insofar that something will require read/write access every few minutes.

You can use the hdparm command for this (the -S option in particular - see the man page) however, as mentioned, it will likely be futile.

Mathew

---

### Post by FEF on 2007-10-31
I'm in a similar situation, but a bit different.  I have the OS on one drive, and a RAID 1 for all my pics, videos, music, and such like that.

In my application, my server is in a closet and I use Webmin/PUTTY, with no GUI.  While it's not in any danger of over heating, it's clear that it's generating a lot of heat.  This means it's wasting energy (equal to a 100w bulb, I'm told).  This server gets used once or twice a week.  I really don't want to shut it down and restart it every time I want to use it.  I'd love to find some kind of ACPI solution.

If I read the last post right, the server R/Ws the HD, even when not being used...  In an idle state?  That sounds odd to me.  I can believe it would access the drive often, but I can't imagine why it would with no user input for long periods

Is there a way to make the server sleep, suspend, or hibernate, but then wake up when someone accesses the drives via SAMBA, Webmin, or PUTTY?

Thanks in advance

---

### Post by MJN on 2007-10-31
It's only the 'system' drive that risks being constantly used (by 'constant' I mean every few minutes) as servers tend to be serving and hence by definition are usually up to something. If your server sits idle for long periods doing nothing then you might be okay but there will inevitiably be background functions, such as daemons requiring logging (NTP, syslog etc) and other periodic function runs such the slocate database update, logwatch report generation, many of which may only run daily.
 
Your latter query is indeed possible - do some searching for wake-on-LAN. I've not got any experience of it myself but plenty others will have.
 
Try setting the spindown timers for your drives to, say, 10 minutes and see how you go - only you will know if your machine really sits silent enough for this to work.
 
Mathew

---

### Post by FEF on 2007-10-31
> **MJN said:**
> 
Your latter query is indeed possible - do some searching for wake-on-LAN. I've not got any experience of it myself but plenty others will have.
 
Try setting the spindown timers for your drives to, say, 10 minutes and see how you go - only you will know if your machine really sits silent enough for this to work.
 
Mathew
Wake-on-lan.  Thanks.   I'll dig around.

If I set the drives to spindown (which I was thinking of doing), will that mess up the data on the RAID? I wouldn't think so, becasue it won't do it if it's accessing data.

---

### Post by MJN on 2007-10-31
I don't use RAID and my knowledge of it is practically zero so I honestly don't know. I can't imagine any issues, particularly as the power saving is controlled by the drive itself (the host OS is merely setting the HDD's timer in this instance) and, as you say, it's only effective when the drive is not being accessed.

I may be way off the mark but given RAID strategies are often about data protection I do wonder if a sleeping drive may cause an issue if it can't be polled for health status or access is delayed whilst waiting for it to spin-up (I have a relatively unused drive in my machine which takes around 8-10 seconds from request to data delivery whilst sleeping).

I can't imagine you ever losing data, at worst you'll get moaned at.

Mathew

---

