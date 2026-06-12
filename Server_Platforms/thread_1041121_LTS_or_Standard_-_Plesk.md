---
title: "LTS or Standard - Plesk"
date: 2009-01-16
forum: Server Platforms
---

### Post by Gorlist on 2009-01-16
Hi, just posting to ask for some advice. Currently running a dedicated box with a few sites on FC4, Plesk 8.6.

Ive been looking to change OS to either CentOS, or preferably Ubuntu Server as we use Ubuntu Desktop in the office, ive been putting this off for aslong as possible, however im getting increasingly more concerned about the age of FC4.

Current hardware configuration is a AMD Athlon 64 3200+, 1 gig of ram, and using Raid 1 configuration.

I wasn't intending to change atleast until the new version of Plesk 9, as hopefully by then they may have fixed the migration manager and some of the bugs, however what im not sure on is whether I should use the standard Ubuntu release cycle or LTS. 

Personally im in favour of the standard 6 month updates, however what sort of effect would it have on a control panel such as Plesk? of course you expect to run into problems but would Plesk also be required to release new updates to support say Ubuntu 9.04?

Has anyone here have expediences with Ubuntu & Plesk? ive found a few old guides but nothing resent. 

Currently reading the Ubuntu Server Guide :)

Any infomation would be most appreciated. 

Best Regards,

---

### Post by str8rekt on 2009-01-16
I'd like to know too. We're currently running Plesk 8.6 on CentOS 5, but I'd like to try Ubuntu as well. I haven't taken the plunge to Plesk 9 yet either -- not until they at least get the migration manager working :)

---

### Post by windependence on 2009-01-16
9 is already out and it supports 8.04. If plesk is working on your old version, I would be hesitant just to do it for the sake of doing it. Plesk can be a nightmare with version changes, I have had the experience with commercial clients. Also, if you are even thinking about using your plesk machine for other things - don't. pleasj is very picky about the versions of php, perl, etc underneath it and if you change those or some other program changes those, you are hosed. I would make your Plesk box a dedicated box or run it in a VM.

[http://www.parallels.com/download/plesk9/#ubuntu](http://www.parallels.com/download/plesk9/#ubuntu)

-Tim

---

### Post by Gorlist on 2009-01-16
Thanks for the replies :)

Mine is just a dedicated webserver, so all I run is Plesk and a Teamspeak. Ive been using Plesk for about 2 years now, ive had no major problems with it, however ive never done a major revision update on the OS, or installed it myself.. 

FC4 is no longer supported, and YUM is no longer functioning properly, so ive got to decide somepoint :) 

My question was/is, if I managed to get Plesk installed on Ubuntu 8.11, whats the likely hood of having Plesk fail completely when 9.04 appears? (ive updated PHP, MySql through Yum and experienced no problems in newer revisions), but LTS might be a safer option somewhat.

> **str8rekt said:**
> I haven't taken the plunge to Plesk 9 yet either -- not until they at least get the migration manager working :) I may just install 8.6, and then update to 9x later on if I feel that way inclined - however 9 rv.2 is suppose to be allot more stable than their first release, and some people its been working fine! (the same happened when 8 came along)

---

