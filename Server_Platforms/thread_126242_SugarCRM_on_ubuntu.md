---
title: "SugarCRM on ubuntu"
date: 2006-02-06
forum: Server Platforms
---

### Post by alamba on 2006-02-06
Hi,

I've finally been able to convince a friend of mine to try a open source enterprise tool rather than being a windoze only shop. As the first exercise I need to set him up with SugarCRM on a linux box for his office. I plan to do this on a server install of ubuntu.

Any advice, links, heads up, etc. would be appreciated.

Regards,
Akshay

---

### Post by alamba on 2006-02-06
bump...anyone? Need to sure that I don't mess this one up so being extra careful. Taken me ages to convince this friend and wanna make sure the first experience is good.

A

---

### Post by Bite_me_Bill on 2006-02-06
Should run without a problem.  Have you looked at the requirements? 

[http://www.sugarcrm.com/crm/products/faq.html#technical2](http://www.sugarcrm.com/crm/products/faq.html#technical2)

Just do a typical server install and then add the needed packages.  Mainly just a webserver.

---

### Post by alamba on 2006-02-06
Yep, have gone through the requirements. Am building a system that would more than confirm to the hardware requirements. I plan to apt-get apache, php and mysql before installing SugarCRM from source. Oh and ofcourse the header files for the latest kernel.

Akshay

---

### Post by snowjunkie on 2006-02-06
[QUOTE=alamba]Yep, have gone through the requirements. Am building a system that would more than confirm to the hardware requirements. I plan to apt-get apache, php and mysql before installing SugarCRM from source. Oh and ofcourse the header files for the latest kernel.

Akshay[/QUOTE]

Hi,
I'd really appreciate to hear how you get on with this... thanks.

---

### Post by alamba on 2006-02-06
Absolutely. Just drop me a line through my signature in a couple of days and will apt-get (update) you!! 

aaarrrgghhhh...that was a bad one even for me...now that's called too much of ubuntu/debian!!

---

### Post by alamba on 2006-02-11
Got it up and running. Clean install. Will post a howto in the next few days.

A

---

### Post by snowjunkie on 2006-02-12
[QUOTE=alamba]Got it up and running. Clean install. Will post a howto in the next few days.

A[/QUOTE]

Look forward to the HowTo!

Thanks!

---

### Post by dk_pa on 2006-02-12
Sugar is cake to setup but I couldn't get it to run worth a damn on the hosting I have.  It was just too power hungry for it I believe cause it was slower than what usuable is.  What machine did you install it on (specs) and how does it run on a LAN.  I would imagine really good.

---

### Post by wout.wepsait.com on 2006-02-15
SugarCRM is partnering with Microsoft. Next release will be under a Microsoft license. Just thought you should know..

[http://news.com.com/2100-7344_3-6038966.html?part=rss&tag=6038966&subj=news]("http://news.com.com/2100-7344_3-6038966.html?part=rss&tag=6038966&subj=news")

---

### Post by alamba on 2006-02-15
dk_pa: Running it on a 1.6 Ghz, 768 MB RAM, 250GB HDD box over the LAN. Response time is pretty good. However not as fast as one would expect over a 100 mbps network.

wout: Thanks for the link. Very informative, AFAIK the microsoft licence would be the "pro" version of the suite for just their server platform. This is unrelated to the OSS version available for linux. Am i reading that wrong?

A

---

### Post by alamba on 2006-02-15
Just a pointer to the howto incase someone drops in searching the forum:

[http://www.ubuntuforums.org/showthread.php?t=130059](http://www.ubuntuforums.org/showthread.php?t=130059)

A

---

### Post by dk_pa on 2006-02-15
> dk_pa: Running it on a 1.6 Ghz, 768 MB RAM, 250GB HDD box over the LAN. Response time is pretty good. However not as fast as one would expect over a 100 mbps network.

I was kinda leary that would be the response.  I guess I'll just look for something else.  Thanks for the info! =)

---

### Post by alamba on 2006-02-17
I'll be hosting it on the web for a client pretty soon. Will post how the response is online once I have it set up. I'll be using a VPS so hardware would be pretty minimalistic.

A

---

### Post by emut on 2006-02-17
I have just set up the open source version of SugarCRM 4.0.1 on a fresh server install of Ubuntu Breezy running on Xampp.  The installation is basically just copying over the source files to the root of your web directory and setting some permissions.

Everything seems to work fine and was up and running in under half and hour :) 

Only thing I can't figure out is how to get the inbound email working.  From what I figure I need to set up a cron job to process the cron.php in Sugar.  How is this done?

---

### Post by rjewelll on 2006-02-17
I recently installed SugarCRM and using xampp from apachefriends.org makes the whole process a lot easier (for other groupwares also).

The news about MS and Sugar sort of ruined my plans. I have been evaluating groupwares looking for a nice clean one for use in a friends law office. So far I've looked at Moregroupware, egroupware and Sugar. Sugar is obviously for a different purpose but it's so nice and clean. So... does anyone have suggestions for a comparable groupware package that isn't getting involved with Microsoft?

Thanks.
Ryan

---

### Post by snowjunkie on 2006-02-17
You have SSH listed in your steps... do you need to install SSH?  Is it required by SugarCRM?

---

### Post by emut on 2006-02-17
SSH isn't required by Sugar.  In Xampp SSL is compiled with Apache so accessing Sugar over https is supported.

---

### Post by alamba on 2006-02-18
snow: Nope ssh isn't really needed. I installed it cos I was going to remotely access the server during Sugar's install.

emut: I haven't gotten email integrated with Sugar yet. However my VPS is now ready so would probably end up loading sugar, postfix etc. in the next few days. Email integration is my first item on my to do before handling over the sugar implementation for production. Will let you know how it goes.

rjewell: I've been looking around for a good groupware too but have'nt really hit into anything that's rugged enough yet. There were some choices I came across but they were paid options only.

A

---

### Post by alamba on 2006-03-05
dk_pa: I recently put up sugarcrm on a VPS with pretty minimalistic configuration - 256 RAM, 5GB HDD - Been running pretty good. Atleast for an application hosted on the net. 

emut/rjewell: Thanks for the suggestion of XAMPP. It worked wonderfully after my original apache/php4 installation broke down. However, for a production environment I'd still prefer a "native" apache/php/mysql installation rather than XAMPP. 

Hence, I now have test beds on XAMPP and production systems on Debian. I wonder when they'll start to offer ubuntu server as VPS OS installation. Something to do with being compatible with the virtualization system.

Akshay

---

### Post by satimis on 2008-04-14
Hi folks,


I'm prepared testing SugarCRM community edition and don't know how/where to start.

OS - Ubuntu 7.10 server amd64 (64bits)


I found the thread;

HowTo: SugarCRM on Ubuntu Breezy
[http://ubuntuforums.org/showthread.php?t=130059](http://ubuntuforums.org/showthread.php?t=130059)


I hesitate whether it is right howto for me to follow.  

On SugarCRM --> Documentation --> Commumity Edition

[http://www.sugarcrm.com/crm/index.php?option=com_docs&edition=OS&Itemid=375](http://www.sugarcrm.com/crm/index.php?option=com_docs&edition=OS&Itemid=375)

There are many documents.  Which of them will be suitable for my use?  TIA


B.R.
satimis

---

