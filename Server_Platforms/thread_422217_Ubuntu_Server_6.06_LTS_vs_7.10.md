---
title: "Ubuntu Server 6.06 LTS vs 7.10"
date: 2007-04-24
forum: Server Platforms
---

### Post by fernando_lopes_jr on 2007-04-24
Hi guys;

I have a home server in Ubuntu 6.06 LTS that does file sharing, torrent download, ftp, runs VMware etc and It’s working like a charm. What I wanted to know is your opinion about if I should upgrade to the new version of Ubuntu of just stay still. It’s been a while since version 6.06 came out one year two be precise I really feel like it maybe the time to update the OS since new features must have came out meanwhile. I’ve read that this new version of Ubuntu was same optimizations for virtualization and I would very much appreciate the added performance since I play a lot around with SO when I have the free time to try things out. 
Above anything I need a SO that works 24/7 with few hassle and version 6.06 was gave me that.

Thanks for the help Fernando

---

### Post by strixy on 2007-04-25
I wouldn't upgrade just yet. Wait until July when some of the concerns and issues with the changes made in this new version are sorted out and people have had the chance to ask and respond to questions - especially on this forum (love it here!). Some of the things you did with 6.06 won't blindly accept the same config files you're using. You'll have to recreate them by hand and as I'm discovering, the changes in some software packages are substantial enough to warrant the caution above. What I thought would be a weekend project is turning into a two weekend project and I'm upgrading from 6.10, not 6.06. I usually jump on the new release with the last RC so I can mix it up in the forums - asking and answering questions, bug testing, etc... That's not for everyone, but it you want to mix it up a little your help and feedback would be appreciated.

I run a server for family and friends. They know the server goes down for a period every 6 months. Any of their sites that may need stable servers are hosted elsewhere. If you're fine with some down time, go for it! It's a pretty feisty release. he he... :)

---

### Post by Brazen on 2007-04-25
I wouldn't (and I won't) upgrade until the next LTS release.  The virtualization optimisations also only work if you have a processor that has the virtualization extensions (only certain new AMD and Intel processors).

---

### Post by glee on 2007-08-30
And what release will be the next LTS release? Where does one look to find out? Thanks.

---

### Post by dmizer on 2007-08-30
just posted today, hardy heron (gutsy +1) will be the next LTS release; due out next april.  [http://fridge.ubuntu.com/node/1099](http://fridge.ubuntu.com/node/1099) 

i strongly urge waiting as long as possible.  there's no reason to rush an upgrade to a perfectly functional, and securly patched server.  wait it out long enough for all the other ship jumpers to tell you what temperature the water is before you dive in yourself.

if you jump to gutsy now, it'll only be a few months and you'll have to upgrade to hardy anyway.  also, according to the LTS structure, you'll be able to upgrade directly from dapper to hardy.  but if you want gutsy, you'll have to fight the upgrade from dapper to edgy (often a very bumpy upgrade), then upgrade from edgy to feisty, and finally feisty to gutsy.  any single one of those upgrades could go horribly, irrecoverably sour on you.

---

### Post by geraner on 2007-08-31
> also, according to the LTS structure, you'll be able to upgrade directly from dapper to hardy.
This was new for me. Thanks for this information. I will wait until Ubuntu 8.04 with LTS comes out. :)

---

### Post by motang on 2007-08-31
Honestly I would stick with the LTS, that is same version I am using on my server that I used for my senior project and it worked like a charm.  The system was rock solid and everything I threw at the computer worked great.  I would suggest that you stick with LTS, and not upgrade to 7.10.  But if you planning updating your server I would suggest wait for 8.04 as it has been announced that release would be next LTS.  I believe (now this purely personal) if you are going to stick server stuff on your Ubuntu installation that LTS would be better than non-LTS releases.
Hope this was some what helpful to you. ;-)

---

### Post by geraner on 2007-08-31
Just read here:
[http://digg.com/linux_unix/Introducing_the_Hardy_Heron_Ubuntu_8_04](http://digg.com/linux_unix/Introducing_the_Hardy_Heron_Ubuntu_8_04)

---

