---
title: "Best encryption software for virtual encrypted folder on cloud service"
date: 2016-12-18
forum: Security
---

### Post by erotavlas on 2016-12-18
Hi,
I take care a lot about my privacy. I have some backup of my data offline. However, I would like to use a cloud service in order to have the data available everywhere and to have enhanced safety in case of a disaster of my physical copies.
I'm looking for free cloud service with encryption. The best one that I found is mega.nz, however even if is open source, I do not trust it at 100% since it is located in New Zeland a member of 5 eyes. I cannot use ownCloud since I need to pay a lot for hosting.
I read [here]("https://www.privacytools.io/#encrypt") about of various alternatives of encryption software.
I know that GnuPG does not allow to create a virtual folder in which I can copy all my data and I have to encrypt all single folders. So my last alternatives are [veracrypt]("https://veracrypt.codeplex.com/"), [cryptomator]("https://cryptomator.org/") or this new project [cryFS]("https://www.cryfs.org/") that seems strong and have a theoretic base, but it is still a beta and [only works with linux]("https://www.cryfs.org/comparison").
Do you have any suggestion?
Thank you

---

### Post by TheFu on 2016-12-18
Cloud and privacy do not mix.

Use something like owncloud/nextcloud/sovereign behind openVPN on HW that you host at home (or in some other location that has limited physical access) over a broadband connection.  A Raspberry Pi is sufficient for this. A $100 "server" will do wonders, however.

[https://cloudnimbus.org/](https://cloudnimbus.org/) &#8211; a Raspberry Pi personal Cloud project; free
[https://pimylifeup.com/raspberry-pi-owncloud/](https://pimylifeup.com/raspberry-pi-owncloud/) 

Be your own cloud, if you care about privacy.

---

### Post by erotavlas on 2016-12-18
> **TheFu said:**
> Cloud and privacy do not mix.

Use something like owncloud/nextcloud/sovereign behind openVPN on HW that you host at home (or in some other location that has limited physical access) over a broadband connection.  A Raspberry Pi is sufficient for this. A $100 "server" will do wonders, however.

[https://cloudnimbus.org/](https://cloudnimbus.org/) – a Raspberry Pi personal Cloud project; free
[https://pimylifeup.com/raspberry-pi-owncloud/](https://pimylifeup.com/raspberry-pi-owncloud/) 

Be your own cloud, if you care about privacy.

You are right.
I know that storing my data on encrypted cloud like mega.nz in which my data are previously encrypted with a secure encryption software is wore than having all my data at my home.
However, I have slow Internet connection especially on upload side 1 Mbps. Moreover, owning my personal cloud allows me to access everywhere to my data, but it does not protect me from disaster or robbery.
These are the reasons for which I asked my question.
Do you have any suggestion?
Thank you

---

### Post by TheFu on 2016-12-18
Sorry. No. Putting data on 
* someone else’s hard drive 
* attached to someone else’s server
* in someone else’s data center
* at the end of an Internet pipe controlled by someone else 
Just doesn't work for me.

1Mbps up is plenty for anything except video.

Let's consider this for a minute.  If you don't fully encrypt the data and only transfer that data while still encrypted, then it is out of the bag.  Mounting the data quickly on the remote server allows root (and probably others) to access the data.
Transferring it over HTTPS is also broken.  HTTPS requires 2 external providers to work together and not allow either of them, anywhere in the world, to be untrustworthy. We know that isn't the situation, so HTTPS is broken if you care at all about security.

I'd rather see people switch to I2P networks than use TOR.

Ok ... so you'll group the files into chunks that are unknown to anyone looking thanks to encryption.  Now the problem is usability.  Do all the platforms you need/want to use have access to the decryption method needed? Plus you'll have to download the entire "chunk" to access the files inside, assuming you care a privacy and don't want the size of the files known (which can be used to guesstimate the contents).

BTW, I've run IT businesses with 128Kbps connections, so 1Mbps is huge bandwidth.  Someone at my LUG mtg today pointed to [this link]("https://www.cyberciti.biz/cloud-computing/7-awesome-open-source-cloud-storage-software-for-your-privacy-and-security/") when I asked the question.

---

### Post by erotavlas on 2016-12-20
> **TheFu said:**
> Sorry. No. Putting data on 
* someone else&#8217;s hard drive 
* attached to someone else&#8217;s server
* in someone else&#8217;s data center
* at the end of an Internet pipe controlled by someone else 
Just doesn't work for me.

You are right if you want to be 100% sure it is better to do not put your data online. At the same time, storing the data in different storage (hard drives) and in different location (houses) is less secure with respect to a cloud in case of disaster (less redundancy).
For this reason I'm looking for a good encryption software with transparent virtual encrypted folder in order to have both benefits.

> **TheFu said:**
> 
1Mbps up is plenty for anything except video.


1Mbps is about 125 kBps in the best case, average about 0.7Mbps about 87.5 kBps. So if you want to transfer 10MB you need about 80 seconds in best case and about 115 seconds in the average case. If you want to transfer 100MB or 1 GB you need in the average case 1150 seconds (19 minutes) and 11500 (191 minutes i.e. more than 3 hours).
I do not think it is good enough in my case.

> **TheFu said:**
> 
Let's consider this for a minute.  If you don't fully encrypt the data and only transfer that data while still encrypted, then it is out of the bag.  Mounting the data quickly on the remote server allows root (and probably others) to access the data.
Transferring it over HTTPS is also broken.  HTTPS requires 2 external providers to work together and not allow either of them, anywhere in the world, to be untrustworthy. We know that isn't the situation, so HTTPS is broken if you care at all about security.

I did not understand your point. If I encrypted my data, assuming reliable software and algorithm for encryption, nobody can read my data even if he has access to them.

> **TheFu said:**
> 
Ok ... so you'll group the files into chunks that are unknown to anyone looking thanks to encryption.  Now the problem is usability.  Do all the platforms you need/want to use have access to the decryption method needed? Plus you'll have to download the entire "chunk" to access the files inside, assuming you care a privacy and don't want the size of the files known (which can be used to guesstimate the contents).

This is the point. I cannot use GnuGP or encrypted compressed file like .7z format since they are not very useful. If it was cheap, I would install owncloud on hosting server. Unfortunately, I cannot follow this option.

> **TheFu said:**
> 
BTW, I've run IT businesses with 128Kbps connections, so 1Mbps is huge bandwidth.  Someone at my LUG mtg today pointed to [this link]("https://www.cyberciti.biz/cloud-computing/7-awesome-open-source-cloud-storage-software-for-your-privacy-and-security/") when I asked the question.
Thank you, I read the link. Can you recommend a software for virtual encrypted folder?

---

### Post by TheFu on 2016-12-22
What do you define as "cheap"?  A $5/month VPS is pretty cheap to most people. You'll pay more than that for a reputable storage-only provider.  I'd suggest NextCloud with a VPN. HTTPS is not sufficient if you care about privacy.

As long as the locations are 500 miles apart and not in "bad" areas, it is unlikely that one disaster/theft would impact both locations. I did this (systems architecture and DR planning) for a living for almost a decade. If we remove volcanos and typhoons from the problem, even smaller distances can be supported, say 200 miles. It isn't like this removes the need for an offsite, offline, backup (which you already have). Sure, everything starts with physical security, but a tiny raspberry pi with an external 1TB laptop disk connected through a powered USB2 port doesn't exactly scream for a thief to take it when there is a laptop/desktop nearby.  Anyway - that horse has been beaten enough - probably for both of us. I'll drop it.

---

### Post by erotavlas on 2016-12-22
> **TheFu said:**
> What do you define as "cheap"?  A $5/month VPS is pretty cheap to most people. You'll pay more than that for a reputable storage-only provider.  I'd suggest NextCloud with a VPN. HTTPS is not sufficient if you care about privacy.


Thank you for your hint of nextcloud, I prefer it over owncloud since it is completely open source. [Here]("https://nextcloud.com/providers/") there are some free provider of nextcloud service. Do you have any recommendation?

What about VPS? Which VPN can I use?

Why do you think that https is not secure? Due the vulnerabilities described in [this article]("https://www.eff.org/deeplinks/2011/10/how-secure-https-today")? A due to old SSL bug? 

> **TheFu said:**
> 
As long as the locations are 500 miles apart and not in "bad" areas, it is unlikely that one disaster/theft would impact both locations. I did this (systems architecture and DR planning) for a living for almost a decade. If we remove volcanos and typhoons from the problem, even smaller distances can be supported, say 200 miles. It isn't like this removes the need for an offsite, offline, backup (which you already have). Sure, everything starts with physical security, but a tiny raspberry pi with an external 1TB laptop disk connected through a powered USB2 port doesn't exactly scream for a thief to take it when there is a laptop/desktop nearby.  Anyway - that horse has been beaten enough - probably for both of us. I'll drop it.

You are right about risk management, however in my case the two locations that I have available are very close in the same town. So I prefer a cloud service.

Thank you

---

### Post by TheFu on 2016-12-22
I can google these things as easily as you can, but in the interest of teaching you to fish ... 
If you don't pay for the service, then YOU (and your data) are the product.

"secure VPS providers" - I'm thinking digital ocean or chicago VPS.  Look for lists with those.

"secure VPN providers" - but if you run a VPS, then run the VPN off that too. I'd use openvpn or simple ssh.

https has a flawed design.  Any certificate provider in the world can create a cert for any other domain. That completely breaks the entire trust model.  It has happened a few times (that we know about) before.  Basically, only technologies that use private certs can be trusted. It isn't about the math, it is about overall systems architecture.

I've seen some really poorly designed data centers in my time.  Some in hurricane areas, prone to flooding, some at the end
major airport runways, above subway stations, etc.   Foolish.  Also saw one with water leaks after major storm came through.  The building wasn't rated for F3 tornadoes and they have tornadoes in that part of the world.  One had a power-kill button about 4ft off the floor.

One class-5 data center kept going on and on about their security - they used biometrics to control access to the main door and onto the data center floor.  Each cage was locked for the different vendors to get access only to a small number of systems, with each rack similarly locked just for those vendors. They tracked outbound as well. On the way out, saw a side-door propped open and 3 guys standing outside having a smoke break.  Plus the biometrics didn't work on the way out - seems they required the hand-print to be a certain temperature, but inside was so cold that our tour guide's hand was too cool to work.

Not all DCs are good.

I've seen some amazing DCs too - full RF shielded, gas turbines on anti-earthquake springs, battery replacement schedules that swapped out every battery, every 3 years. Redundant power from 2 different substations, 5 different network connections, multi-layer physical security. This location was #2 for refueling after a natural disaster, just behind the regional trauma center.  Sadly, this type of DC is the exception, not the rule.

I trust my house over all these. It isn't really secure at all, but it is uninteresting to thieves. Power here is extremely stable. Maybe (5) 20 min of outages the last 10 yrs. Once it was off for an hour when they swapped out the power meter.  Have a few UPSes that cover 45 min outages. For a raspberry pi and wifi router, it could handle 3+ hours, easy.  Did some power work in Nepal a few years ago where they have rotating power outages daily. They call it "load sharing" and it is equally inconvenient for everyone, but sufficient to maintain a fridge and charge batteries.

Internet connection is fairly stable here the last 15 yrs.  Oddly, as I type this it is down:
```
$ internet-up-summary.sh 
 Period 20161218-062611  - 20161222-142821
  Total Time: 6244 (min) 104.07 (hrs)
  Percent Up Time: 99.74 % 
  Percent Down Time: 0.26 % 
  Total Down Time: 16 min or 0.27 hrs
 Currently: DOWN

``` Because all my data is local, I didn't notice. Haven't noticed any issues at all in months. It is back up now.
```
$ internet-up-summary.sh 
 Period 20161218-062611  - 20161222-143011
  Total Time: 6246 (min) 104.10 (hrs)
  Percent Up Time: 99.74 % 
  Percent Down Time: 0.26 % 
  Total Down Time: 16 min or 0.27 hrs
 Currently: UP
```
Had some connectivity issues a few years ago and setup internet connection monitoring.  With that, the ISP handles any issues I have almost immediately just by offering to show the log files. Log files don't lie. Plus a 5 min phone call will get a $50 reduction off my bill for the outage. Proof matters. 

Anyway, good luck.

---

### Post by erotavlas on 2016-12-23
> **TheFu said:**
> I can google these things as easily as you can, but in the interest of teaching you to fish ... 
If you don't pay for the service, then YOU (and your data) are the product.

"secure VPS providers" - I'm thinking digital ocean or chicago VPS.  Look for lists with those.

"secure VPN providers" - but if you run a VPS, then run the VPN off that too. I'd use openvpn or simple ssh.

https has a flawed design.  Any certificate provider in the world can create a cert for any other domain. That completely breaks the entire trust model.  It has happened a few times (that we know about) before.  Basically, only technologies that use private certs can be trusted. It isn't about the math, it is about overall systems architecture.

I've seen some really poorly designed data centers in my time.  Some in hurricane areas, prone to flooding, some at the end
major airport runways, above subway stations, etc.   Foolish.  Also saw one with water leaks after major storm came through.  The building wasn't rated for F3 tornadoes and they have tornadoes in that part of the world.  One had a power-kill button about 4ft off the floor.

One class-5 data center kept going on and on about their security - they used biometrics to control access to the main door and onto the data center floor.  Each cage was locked for the different vendors to get access only to a small number of systems, with each rack similarly locked just for those vendors. They tracked outbound as well. On the way out, saw a side-door propped open and 3 guys standing outside having a smoke break.  Plus the biometrics didn't work on the way out - seems they required the hand-print to be a certain temperature, but inside was so cold that our tour guide's hand was too cool to work.

Not all DCs are good.

I've seen some amazing DCs too - full RF shielded, gas turbines on anti-earthquake springs, battery replacement schedules that swapped out every battery, every 3 years. Redundant power from 2 different substations, 5 different network connections, multi-layer physical security. This location was #2 for refueling after a natural disaster, just behind the regional trauma center.  Sadly, this type of DC is the exception, not the rule.

I trust my house over all these. It isn't really secure at all, but it is uninteresting to thieves. Power here is extremely stable. Maybe (5) 20 min of outages the last 10 yrs. Once it was off for an hour when they swapped out the power meter.  Have a few UPSes that cover 45 min outages. For a raspberry pi and wifi router, it could handle 3+ hours, easy.  Did some power work in Nepal a few years ago where they have rotating power outages daily. They call it "load sharing" and it is equally inconvenient for everyone, but sufficient to maintain a fridge and charge batteries.

Internet connection is fairly stable here the last 15 yrs.  Oddly, as I type this it is down:
```
$ internet-up-summary.sh 
 Period 20161218-062611  - 20161222-142821
  Total Time: 6244 (min) 104.07 (hrs)
  Percent Up Time: 99.74 % 
  Percent Down Time: 0.26 % 
  Total Down Time: 16 min or 0.27 hrs
 Currently: DOWN

``` Because all my data is local, I didn't notice. Haven't noticed any issues at all in months. It is back up now.
```
$ internet-up-summary.sh 
 Period 20161218-062611  - 20161222-143011
  Total Time: 6246 (min) 104.10 (hrs)
  Percent Up Time: 99.74 % 
  Percent Down Time: 0.26 % 
  Total Down Time: 16 min or 0.27 hrs
 Currently: UP
```
Had some connectivity issues a few years ago and setup internet connection monitoring.  With that, the ISP handles any issues I have almost immediately just by offering to show the log files. Log files don't lie. Plus a 5 min phone call will get a $50 reduction off my bill for the outage. Proof matters. 

Anyway, good luck.

Thank you for your useful information, I learnt many new stuff. 
My conclusions are:
[LIST]
[*]Free option: use [nextcloud]("https://nextcloud.com/") if it possible on your home even if there are several limitations (small upload bandwidth, disaster, variable IP address, etc.);
[*]Paid option: buy for online provider of nextcloud;
[*]Use [cryptomator]("https://cryptomator.org/") in conjunction with mega.nz for 50 GB and double encryption both with open source software. [Cryptomator security architecture]("https://cryptomator.org/architecture/") and [Mega.nz.]("http://mega:#blog_32")
[/LIST]

---

### Post by kevdog on 2016-12-26
In a different vain, I like the borg backup utility for remote encrypted backups.  Backups can of course just be a folder or directory so you can configure your backup however you want.  Only caveats with this solution -- the remote utility needs ssh and borg to be installed.  If these utilities are available, you could then mount the remote encrypted backup as a FUSE directory structure and browse the contents.  Borg offers backup diffs, is encrypted, and a versioned utility.  Rsync for example doesn't backup diffs, doesn't do native encryption, and really isn't a versioned or snapshot capable program as comparison.  Comparable products are for example obnam and duplicity.  I haven't found any of these programs however to be multiplatform.  I believe many can run on Win 10 if you've installed the basic ubuntu installation which is now offered natively in Win10.  All three will run on Mac, Linux and BSD.  If ever in need its also possible to run an installation on Windows for example within a VirtualBox which has Linux installed that can read and write to the Windows partition. Both OS's would need to be running simaltaneously for this to work -- I've found this a lot better and easier solution than a dual boot which requires logging back in and out.  Probably in the future you could run these within a container, however I'm not aware of current solutions for this. 

NextCloud is great to run personally however unless its off-site you don't protect from catostrophic loss such as a fire, hurricane, lightening strike, etc.  Other than that its really really good.

---

### Post by erotavlas on 2016-12-30
> **kevdog said:**
> In a different vain, I like the borg backup utility for remote encrypted backups.  Backups can of course just be a folder or directory so you can configure your backup however you want.  Only caveats with this solution -- the remote utility needs ssh and borg to be installed.  If these utilities are available, you could then mount the remote encrypted backup as a FUSE directory structure and browse the contents.  Borg offers backup diffs, is encrypted, and a versioned utility.  Rsync for example doesn't backup diffs, doesn't do native encryption, and really isn't a versioned or snapshot capable program as comparison.  Comparable products are for example obnam and duplicity.  I haven't found any of these programs however to be multiplatform.  I believe many can run on Win 10 if you've installed the basic ubuntu installation which is now offered natively in Win10.  All three will run on Mac, Linux and BSD.  If ever in need its also possible to run an installation on Windows for example within a VirtualBox which has Linux installed that can read and write to the Windows partition. Both OS's would need to be running simaltaneously for this to work -- I've found this a lot better and easier solution than a dual boot which requires logging back in and out.  Probably in the future you could run these within a container, however I'm not aware of current solutions for this. 

NextCloud is great to run personally however unless its off-site you don't protect from catostrophic loss such as a fire, hurricane, lightening strike, etc.  Other than that its really really good.

Thank you for your hints. I did not know Borg, it seems very good solution for encrypted versioning backup. Unfortunately, in the best case it requires a server with SSH and if I have access to it, I would go for nextCloud.
However, it could be the solution by encrypting the backup folder and uploading it to encrypted mega.nz cloud.
What about borg encryption security? Is it better than cryptomator?
Thank you

---

### Post by kevdog on 2016-12-31
I'm not very familiar with cryptomator.  Borg uses AES-256 encryption. I'm not trying to bust your bubble, but what is most important for you? I'd only recommend borg if you need versioned backups which happen to be encrypted.  If you just need encryption, you could use a wealth of other programs that might do this.  One of the reasons I wanted a versioning type system -- rsnapshot, duplicity, borg, is that I didn't want like 20 copies of each file within the backup.  rsync is great however it isn't versioned.  You basically keep one copy of everything, and it uploads changed files only.  It doesn't allow for rollback to a specific time point in case of failure.  If your working with a large data set you probably want a versioning type system since if all your doing is zipping a directory and encrypting it --- your going to have numerous copies of each file on your backup server.  This also is a bandwidth efficient process, however if you're working with a small dataset, this probably isn't the limiting factor.

---

### Post by erotavlas on 2017-01-01
> **kevdog said:**
> I'm not very familiar with cryptomator.  Borg uses AES-256 encryption. I'm not trying to bust your bubble, but what is most important for you? I'd only recommend borg if you need versioned backups which happen to be encrypted.  If you just need encryption, you could use a wealth of other programs that might do this.  One of the reasons I wanted a versioning type system -- rsnapshot, duplicity, borg, is that I didn't want like 20 copies of each file within the backup.  rsync is great however it isn't versioned.  You basically keep one copy of everything, and it uploads changed files only.  It doesn't allow for rollback to a specific time point in case of failure.  If your working with a large data set you probably want a versioning type system since if all your doing is zipping a directory and encrypting it --- your going to have numerous copies of each file on your backup server.  This also is a bandwidth efficient process, however if you're working with a small dataset, this probably isn't the limiting factor.
I want to have a virtual encrypted folder on cloud service. There are several options:

[LIST]
[*]Plain folder stored in encrypted cloud -> nextcloud (best available for all OS, but with some limitations described in a previous message)
[*]Encrypted folder plus cloud service -> GNUPG, 7z plus mega.nz (not very comfortable, some feature missing as versioning and duplicating file)
[*]Encrypted folder plus cloud service -> Borg plus mega.nz (best option for a single access from unix style)
[*]Encrypted folder plus cloud service -> Cryptomator plus mega.nz (new option under development)
[/LIST]
In my case, Borg seems to be very good solution for storing data that I use only from my PC with linux OS. For general sharing and standard cloud service accessible from different devices it is better to use nextcloud.
Thank you again I'm going to use Borg.

---

