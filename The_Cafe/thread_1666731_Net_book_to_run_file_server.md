---
title: "Net book to run file server?"
date: 2011-01-14
forum: The Cafe
---

### Post by PartisanEntity on 2011-01-14
Hi all,

I have been using my old Asus z9200 laptop to run a file server and time machine backup as described here:
[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

My setup is simple: a 1tb USB hdd attached to the Asus. Using netatalk and avahi I am advertising my shares on the network using afp protocol so I can access them from the MacBook and iMac. Been working perfectly for the past two years. 

The laptop however is very loud and I would like to replace it with a cheap net book, nothing fancy.

For example I was thinking of getting a cheap, older model Asus eee pc.

Would this work for my needs? I am guessing yes, but perhaps people here have concrete experiences?

Thanks.

---

### Post by Johnsie on 2011-01-14
It's fine... A decent netbook can run for years. THe only thing you need to worry about is keeping it cool and also the battery. Netbook batteries tend to wear out pretty quick. I've had a few EEPC's, they are quite rugged and easily able to do samba well enough to be a file server, even the 701. 

With the 701 there is an issue with drive space on the 4gb drive. Ubuntu takes more than 3gb of that , so it doesn't give you much room for cache and updating packages. If you compress /usr you can get a little more space.

---

### Post by nothingspecial on 2011-01-14
My aspire one (broken screen) has been in the garage making backups for over a year now.

Don`t buy something new, I picked up that netbook at a car boot sale for £15

---

### Post by WRDN on 2011-01-14
A netbook is more than powerful enough to run a file server.

I'm running a file server, web server and repository host on an old IBM Pentium 4 machine (P4,512MB RAM, 20Gb HDD). It has no trouble, so you would have no issues with a modern machine (other than heat, depending on the device).

---

### Post by ukripper on 2011-01-14
I use eeepc 2GB surf model 

Hardware:
[LIST]
[*]Internal 2GB SSD for running Ubuntu 9.10 server
[*]8GB SDHC class 6 card for data only
[*]512 DDR2
[*]576 Mhz underclocked celeron cpu
[*]Hooked 2 wireless cams to monitor premises
[/LIST]
Software & OS:
[LIST]
[*]Ubuntu 9.10 server 32 bit
[*]SSH (ofcourse)
[*]Zoneminder 
[*]Apache
[*]Dropbox command line only daemon to sync motion detected pictures from SDHC
[*]Logwatch to monitor logs.
[/LIST]

What I get from above is fully custom Advanced home security system at low cost.
I never had any problem running this setup more than a year now.

---

### Post by PartisanEntity on 2011-01-14
Perfect, thank you all for the feedback.

I shall be looking for a cheap used netbook.

I just want something that can do the job, and above all, is quieter than my old ageing laptop which is annoying the hell out of me in my work room.

---

### Post by PartisanEntity on 2011-01-15
Which netbook would you guys recommend? I'm hoping to buy that allows easy installation of Ubuntu.

---

### Post by nothingspecial on 2011-01-15
I`ve had good experiences with Samasung nc*

Acer aspire also work but I have run into (non insurmountable) problems in the past.

---

### Post by PartisanEntity on 2011-01-15
> **nothingspecial said:**
> I`ve had good experiences with Samasung nc*

Acer aspire also work but I have run into (non insurmountable) problems in the past.

I'd like to avoid Acer, I've had all kinds of problems with them.

I'm currently thinking of going with an Asus EEE PC model.

---

### Post by CharlesA on 2011-01-15
I haven't had any problems running Ubuntu on my eeePC (minus to finger scrolling)

---

### Post by nothingspecial on 2011-01-15
> **CharlesA said:**
> (minus to finger scrolling)

Don`t think that will be an issue with a file server :p

@PartisanEntity

I have 3 "broken" netbooks that I have picked up for a combined price of £55. One I use as a backup server (the one I already mentioned).

I have another with a foobared keyboard that I use as a digital photo frame. And another with a broken screen that I use (with an ext monitor), in my bedroom to watch films etc.

The point is, I wouldn`t worry about the make and model, just try to pick up something that the owner considers useless ie very cheap and make good use of it. If I was buying a fully working netbook, I`d want to use it as a netbook, not a file server.

I also have a media server which is an old computer that my work didn`t want. I took it off their hands and it runs 10.04 64 bit server like a dream.

Save your money for fun.

---

### Post by nothingspecial on 2011-01-15
Good advice from one of your colleagues

[http://kmandla.wordpress.com/2010/10/30/howto-find-an-old-computer/](http://kmandla.wordpress.com/2010/10/30/howto-find-an-old-computer/)

---

