---
title: "Moving from windows to ubuntu - need advice and suggestion"
date: 2007-07-17
forum: Server Platforms
---

### Post by uforic on 2007-07-17
Hello all, I like some advice and suggestions on a complete move over to Ubuntu.

Here are the specs to my companies' Dell servers:
Dell PowerEdge 1850
2 x Intel Xeon 3.0GHz (EM64T)
2 x 1GB DDR2 400 SDRAM, ECC, registered
Integrated Single channel LSI53C1030 Ultra320 SCSI controller with 2 x 36GB 15k rpm Ultra320 SCSI Drives
Embedded ATI Radeon 7000-M with 16MB SDRAM video controller
Dual embedded Intel 82541EI Gigabit Ethernet NIC with PXE and WOL

In the process of ordering this for the 1850:
Optional embedded single channel Ultra320 SCSI integrated PERC 4e/Si with 256MB of battery-backed cache

Dell PowerEdge 2950
2 x Intel Dual Core Xeon 2.0GHz (5130-EM64T)
2 x 2GB DDR2 533 SDRAM, ECC, registered
Integrated PERC 5/i SAS 3.0 Gb/s RAID controller with 256MB of battery-backup cache with 4 x 73GB 15k rpm SAS Drives
Embedded ATI Radeon ES1000 with 16MB memory video controller
Dual embedded Broadcom NetXtreme IITM  5708 Gigabit Ethernet NIC with fail-over and load balancing.

Systems and platforms in these servers are as follows:
Dell 1850
-Apache
-php
-vsftp
-wordpress 2.2.1
-phpbb 2.0.22
-phpchat
-java irc
and looking at an opensource video and audio stream platform. Most probably with red5

Dell 2950
-Apache
-Mysql
-php
-vsftp
-postfix (for transport purposes only, low traffic)

What we have now are on windows 2003 server, obviously its become a headache for us and most importantly its become very unstable over the last year and half. Our setup is for a high traffic website with its focus on the phpbb forum and wordpress blog, all content of these 2 platforms are stored in mysql. And inside these 2 platforms, we provide live chat, java irc type chat and will start to provide streaming audio and video as well, also having these content stored in mysql. The postfix mail transport is mostly used in registration and newsletters to our members, therefore not a high traffic mail server.

Presently we are on only one PE1850 with all the services described minus the streaming part. So as you can see, its really taxing the server alot, so after researching and reading all the Dell server related post in Ubuntu forum, we decided to start preparing for a complete migration.

Here is our planning:
PE1850 - we will do a raid 0 on the present drives with a new PERC 4e/Si controller add-on. This will not only increase our drive space but also improve on the disk I/O. Its secondary gigabit ethernet port is use for database connection. 
PE2950 - We will do a raid 1+0 or raid 5 (but after doing all the research, for performance but with space sacrifices, we are leaning towards raid 1+0 but would like any advice from you guys, thanx)  this server main purpose is for Mysql and mail services. It will connect with our front end services like web, phpbb and wordpress via its secondary gigabit ethernet port. 

We are no experts by all means nor we are linux experience users, so any suggestions or advice to the above setup is much appreciated.

Here are my questions:
1. We are aiming for stabilities and readiness out of the box setup and really do not have the hacking expertise to make driver/hardware work properly, so I believe choosing Feisty Fawn 7.04 server edition is the best way to go, is this a correct move?

2. After reading all the posts in this forum, we have alot of worries regarding Dell's PERC raid controllers and Ubuntu driver supports. Since we need to do raid setup in both servers, are all these drivers ready out of the box, and getting everything to work like the we planned is going to work or we will face alot of issues?

3. I know the following are a bunch of old debates but my company is in China, 1. our techs/programmers are windows people, so gui environment is a must; 2. this is a world of kiddy hackers and virus infested environment, therefore all extra layer of protection and security are necessary. 3. our co-lo is quite a ways from our office, therefore a or a few remote management software are needed.
So here go my questions:
     1.	We will need a gui remote access, so we are going to install gnome in our servers and
         by using ssh and NoMachine’s NX servers, are there any security involved? There will be
         also all webmin that needs to be install as well, see any security issues in these?

     2.	Since we have all these remote access in the server, a firewall is a must; we looked at
         ubuntu-firewall and firestarter, which is better for our needs? Or are there any better
         ones?

     3.	I know this is much debated subject, is anti-virus needed in our setup? Our mail server is
         mostly outgoing mails, and very little incoming (at least we will ignore most of them) and
         we will not use pop, its all system emails.

4. We are a little confused about the support timeframe of each ubuntu distro, we read that LTS has longer support time, what does all these means to us? 

We really appreciate all advice and suggestion, and please excuse any dumb questions (as we are not familiar with linux) from here on, thank you in advance.

---

### Post by koenn on 2007-07-17
I wouldn't do it. 

Considering a number of facts in your post, 

- "Our setup is for a high traffic website "  ;  I assume this implies yuou don't want any serious downtime

-"apache .. mysql ... php ... "  ; on a public server, you want this secure. web servers are a prime target for skript kiddies and the likes, especially if the serve dynamic content

- ~"we need al sorts of remote access"  --> more security issues if you don't do it right

- "We are no experts by all means nor we are linux experience users"
- "We are aiming for stabilities and readiness out of the box setup and really do not have the hacking expertise to make driver/hardware work properly" ;
translates to "if anything doesn't work out of the box, we're fried",  "If anything goes wrong, we'll have no idea how to deal with it"

-"our techs/programmers are windows people, "

-"we need GUI"  => and if the GUI isn't avalaible, we're lost ? 

...
 
I'd say that this is a bad idea. 
If you're serious about migrating to Ubuntu (or any other Linux), I'd say you go talk to canonical and/or a local (Ubunto-oriented) Linux company to support you before, during and after the migration. 
Maintaining and supporting a professional Linux environment without any previous experience, no in-house expertise, and coming from a Windows-only context, while relying on a volunteer forum, ... no. 

[http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

-----------------------------------------------------------------------------------------------------------


> 4. We are a little confused about the support timeframe of each ubuntu distro, we read that LTS has longer support time, what does all these means to us?
refer to [http://www.ubuntu.com/products/whatisubuntu/releases](http://www.ubuntu.com/products/whatisubuntu/releases)
> 
We release Ubuntu every six months.  ... Each Ubuntu release is supported for 18 months with security patches, fixes for critical bugs that could cause data loss, and extra translations.

In addition to the regular six-monthly releases, the Ubuntu team may make an Enterprise Release (based on an existing time-based release), also known as a "Long Term Support (LTS)" release, that has received additional stabilization, polish and translation work. These Enterprise Releases will be supported for a longer period than the standard 18 month support of the time based releases. 

==> For servers, the support periode (security patches, critical bug fixes) is  5 years (I thjk) after release date

---

### Post by Mr. C. on 2007-07-17
It appears your primary reasons for considering a switch are to a) avoid headaches, and b) improve stability.

Any switch will increase headaches, not decrease them.  There is a large learning curve, so several bottles of aspirin will be suggested.

Improving stability is a good, worthy goal, but changing to an all new environment with essentially rookies will only decrease your stability and increase your problems.

Given just those two reasons for switching, I agree with the previous poster - switching will not meet your goals.

If you have other goals, or decide to move forward regardless, I'd advise that your staff make the transition in stages while they leap the learning curve and become comfortable with the new environment.  Start with new hardware, and bring the system up one step at a time, always evaluating performance along the way.  As you become confident, you can cut services over to the new platform.  Expect this to be a long term process, not an overnight cut.

Best of luck,
MrC

---

### Post by darkog on 2007-07-17
you may want to consider hiring a consultant or paying for support. thats actually how open source works. the "software" is  free -- but when you need expertise which you do not have in house, you pay for the "service".

running a linux env is very different than running a windows env. you might achieve the stability that you want in the long run  -- but you will pay for it in loss to your own time in having to learn everything new, a very strong possibility in down time and loss of service to your customers. 

thats when you got to seriously look at the numbers and decide if paying someone to get you up and running is worth it. 

[http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

best of luck.

---

### Post by gregor171 on 2007-07-19
I agree with others.
My experience on a much smaller proportions was that I bought 1 test box and 1 preproduction box and after something around 6 months, I published first test server that already serves some content, but not all. As I started I installed ubuntu 6.04 + KDE core, to be still able to login in to a "kind" environment. I did a lot of testing and studying... Nobody would fire me, so this pressure was OFF.

After a lot of load and other testing I moved to Ubuntu Server 7.04 that will go live in some 4-5 weeks.  After some time, SSH is all you need, since everything else is much greater security issue. GUI is something you might not need when you go publish.

In your case I'd make a good plan with stages as preparing, evaluating needed time, prepare few stages (publish services one by one on a third box)... in time you'll have one complete box published and another 50% solved. I suggest you to hire a consultant, to help you in prepare plan, first and hard steps, as well as fast solutions, after you go live! 
It might pay off. Good luck.

PS: for security issues look in [http://secunia.com]("http://secunia.com")

---

### Post by jflaker on 2007-12-10
bring in one good Linux guru who you can learn from.  You could probably do this on a contract basis so you are not committed to the "guru" after everything is running smoothly.  

Bringing in an infrastructure without expertise can be suicide and should be avoided.

The good thing about what you intend to do is that your return on investment (Executive love seeing ROI) will be realized very quickly as the cost of making the switch, after paying your guru, will be quick as your hardware requirements will be less than that for a similar Windows infrastructure.  The return comes in the form of NOT having to pay on licensing for all the software.  Another source of ROI is re-tasking old equipment under Linux.

Plan your move and get an expert!

---

