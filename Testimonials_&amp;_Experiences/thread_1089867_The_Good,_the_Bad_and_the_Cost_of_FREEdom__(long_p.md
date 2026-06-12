---
title: "The Good, the Bad and the Cost of FREEdom  (long post)"
date: 2009-03-07
forum: Testimonials &amp; Experiences
---

### Post by razzz on 2009-03-07
I was hesitant at first to make this post as I have seen many times on here that when someone says anything negative about Ubuntu they eventually get flamed and someone tells them to go back to M$. I posted this thread under “Testimonials and Experiences” and hope that everyone who reads it understands that I am merely sharing my own personal experience migrating to Ubuntu. Both the good and the bad. 

I am a small business owner with a network of 2 servers and 15 workstations. I have been able to maintain and manage my own machines and network since win 3.1. I am not totally computer illiterate.

Four months after our last hardware and OS upgrade, early 2007, major issues developed with one of the new servers running Win server 2003. A friend suggested I look into Ubuntu. I downloaded Ubuntu, installed it and was impressed. Ubuntu installed and configured very easily. It also appeared to serve files to our XP workstations faster than Win server 2003 ever did. Plus, as an added bonus, it was Free.

Since Ubuntu had been running on the servers flawlessly since 2007 (one server ran 24/7 for 266 days without a reboot or any maintenance), I decided to look into migrating our workstations away from M$  to Ubuntu early 2008. Not exactly the same experience. In fact it was difficult, frustrating and very costly.

Though Ubuntu is free of charge, I would have gladly paid for a license that came with technical support. I did visit Cononical's site and their rates seemed a bit high. I got the impression that they are focusing on selling support contracts to very large businesses, not the little guy.

I knew at the beginning that I would need to devote some time for learning. However, I never expected that I would need to spend countless hours, days and even months searching the forums and Google for suggestions on how to fix or configure things and then have to spend even more time experimenting with the suggestions until I found one that actually worked. And to be honest, I found more correct and useful information on other sites not related to Ubuntu. Every time I got frustrated, I reminded myself how extremely well Ubuntu had been running on the servers and that it will be worth it in the end.

Besides better on-screen help, warning and/or error messages could have greatly reduced my frustrations and improved my ability to learn and move forward faster. For instance, after a new install, I used the Add/Remove feature to install Samba. No warning of any issues or missing components during the Add process was indicated and all though a launcher for Samba appeared in the menu, it would not launch until after I did 200 updates. I found this out by accident.

As Ubuntu is based on Debian, I recently decided to download and install Debian out of curiosity to compare the two. For me, Debian took longer to load, required much more initial setup time and I noticed it was conservatively a few releases behind the current available version of many of the packages. However, it did not require any updates after the initial install and it had a very nice help feature that provided mouse-over pop-up messages in many of the GUI configuration interfaces, CUPS for instance. Why the Ubuntu developers decided to not include the mouse-rollover pop-up help messages baffles me. 

When I first began to look for solutions to migrate my workstations from M$ to Ubuntu, I contacted the folks at Codeweavers, the makers of Crossover and a major contributor to the WINE Project. I purchased their “Kick the Tires” service for $2,500.00 to attempt to get a few windows applications my business relies on to run in Crossover/Wine. At first they had some preliminary success so I cut them a second and even larger check to take the project further and hopefully succeed. In the end however, they were unable to get the applications to run in a usable condition. The charges for their services were non refundable and I knew this up front. I just spent several thousands dollars and wasn't one step closer to my goal.

After spending every free moment I had for several months, I realized that in order to find all the solutions my business required and to make the migration to Ubuntu within a reasonable time frame, it was time to seek out Linux professionals of which I hired on a per case basis. Yes, more financial investment in my quest to migrate to Ubuntu.

It took a better part of a year but I finally made the migration. All of my server's and workstation's are running faster and more reliably with Ubuntu being in control of the hardware then they ever did when M$ XP was the host OS.

In order to provide all the needs of the business, I ended up utilizing a combination of Linux software from the Ubuntu repository, two specialized windows based email programs running in Wine/Crossover and a few windows based business applications, such as Quick Books, Lotus Approach Database and UPS Worldship that are running in a virtual copy of M$ XP in Vmware. It's amazing, XP actually appears to run faster being a guest under Ubuntu then when it was the host and in control of everything.

Though Ubuntu's meat and potatoes seems as solid as a rock, I am disappointed with some of the annoying quarks the desktop presents on occasion. Workstations occasionally are missing some launchers from their panel after bootup, progress dialog boxes don't always paint in the progress bar, shortcuts sometimes become non-responsive, some of the “Help” buttons do nothing, and the clipboard's Copy/Paste function is very inconsistent. I understand that there are bugs and that they will eventually be addressed and fixed. I lost a little confidence in bugs being fixed in a timely manner as I have found posts reporting the Copy/Paste problem as far back as 2007.

We had very few problems with hardware. Ubuntu was able to address all of our peripherals except for one flatbed scanner and one OKI Data color laser printer. All the workstations and servers are less than two years old, all have multi core processors, SATA drives and a few are running a RAID1.

Now that I finally have most things configured and running, my only concern is that one day an update may break something and I may not have the knowledge to fix it FAST. I've already been through one kernel security update that caused  Vmware to stop working. It was easy to fix, however it did provide for a brief moment of panic as our order entry system only runs in XP.

I am currently running 8.04LTS, 32-bit on the workstations and 64-bit on the servers. I have decided to leave the security and recommended updates on for now. If I ever add anymore workstations they would initially install all available updates so I may as well keep the existing machines up to date and address an update issue if and when it would occur.

I realize than any good OS is a work in progress and that change is inevitable. However, I am counting on the current LTS version to continue to provide stable and reliable performance until the next LTS version s released. 

Ubuntu boots fasts, runs fast, is very flexible and customizable, rarely does anything crash, there are no M$ viruses to worry about, there are no more interruptions waiting for virus definitions to download and install, security is good, there is minimal maintenance and it actually shuts down when you tell it to.

Though it was more challenging than I had anticipated, I do not regret the amount of time and effort or the thousands of dollars I've spent on migrating all the machines at my pace of business to Ubuntu. I am very pleased with the end result and feel it was a very good investment for my business.

Bye Bill!

---

### Post by bapoumba on 2009-03-07
Well, nice reading :)
I understand the effort, the time and the cost for small businesses. Makes you experience even more important. Is this the only place you have reported it?

---

### Post by emshains on 2009-03-07
Don't take me wrong, the following is not to tell you that you are wrong. 


Firstly, about the updates. Ubuntu is based on debian, and some of the devs, who started ubuntu, were folks from debian. They were upset of the main devs from debian, because the liked to keep their repositories rock solid, with content which was thoroughly tested, but was a bit old. The ubuntu dudes didn't want that because they wanted to let people use the latest stuff. So they made ubuntu. And, since they are trying to keep up to the latest stuff, there are so much updates, but don't get me wrong, this ain't no rolling-release OS, like archlinux is. And ubuntu also has fixed release dates, which means, they may release an unfinished product, and later fix the impurities. That's why it is wise to stick with an LTS version, or just to wait a month or two before upgrading. 

Secondly, about the workstations. Since linux is most commonly used in servers than in pc's, it is supports server hardware better, and the server hardware components don't vary so much. Of course, times change, linux is starting to "storm" the desktop market, but it sill has issues. And just like any new product, there must be some time, before it is supported. You can't blame linux for not having support for your hardware, but you can('t) blame the hardware dev. The best supported hardware is the one that is used in home pc's, that have a separate GPU etc. The low spec'ed office computers you might have, are usually ran by windows, so the manufacturers didn't bother to make good drivers, whereas ati has opened up their drivers for the community. 

Well, since I am just a teenager "who knows computers", I actually hate the pop-up thingies. If I need help, I either type "man [program]", or hit F11, or google for it. I can't always rely on the forum, so I check the documentation. We must all agree, there are better documentated distribution's out there, but it is hard to just rewrite a tera-byte of data, but still, the devs are working on it. And, the how-to's and hints described in different sources, such as softopedia, are better written, because people get paid for the job. Here, well, it is all community built. 

I am glad, that you find ubuntu suited your needs, better yet, that you reported your experience, because any feedback from the users will actually help future development of the system.

---

### Post by razzz on 2009-03-07
Hi,
Thanks for your reply. Yes, this is the only place I posted my short story. I made this post to encourage other small business owners to consider migrating to Ubuntu and depending on their needs, it may take a little time and work however the end results are well worth it.

---

### Post by bapoumba on 2009-03-07
> **razzz said:**
> Hi,
Thanks for your reply. Yes, this is the only place I posted my short story. I made this post to encourage other small business owners to consider migrating to Ubuntu and depending on their needs, it may take a little time and work however the end results are well worth it.
If you do not mind, I'll try to see if this can be spread to some other Ubuntu channels :)

---

### Post by iheartubuntu on 2009-03-07
Razz.... With all the money you've spent, you deserve an award for helping with the linux technology. Maybe codeweavers didnt fix your problems, but down the line they may have learned something new they can apply elsewhere in the future.

I too am in a small family business and right now we have XP as the server, the accounting computer is also XP (for quick books pro) and all the other computers Ive switched to Ubuntu. They all work great! I do have one scanner that doesnt work... a Canon slide scanner. Cannon is known for not opening their source. I had bought it before I had got into linux a couple years ago. I'll have to find a high quality slide scanner that works well with Xane. Our entire network would be Ubuntu linux if I could get Quick Books to work or to find a decent native to linux business accounting program we would make the complete switch. I havent found anything yet. My wife is going to a university right now to get her masters in accounting and, I forget the name offhand, they are pushing a new Microsoft business accounting software on her that it is, i guess, becoming industry standard. While Im at it, my wife wont make the switch to linux becuase she NEEDS MS Money to work for her for our personal finances. None of the other free money management programs for linux appealed to her (ive tried them all and some look good to me, but what do i know). Ive also never been able to get MS Money to work in wine, although countless people report doing so. (I do have FIFA08 soccer working though ha!).

Yah, there are hurdles but every time a new release of Ubuntu comes out things get easier and easier. For us that like to tinker, we can accomplish a lot, save a few problems here and there. I personally have made the full switch to Ubuntu and Im getting a lot of friends and family on board, but nothings perfect.

Just want to say thanks for sticking with it. You may have indirectly helped me down the road when I need a wine program to work in ubuntu!

---

### Post by razzz on 2009-03-07
> **bapoumba said:**
> If you do not mind, I'll try to see if this can be spread to some other Ubuntu channels :)

Sure, feel free to copy my post and place it where ever you think it may help spread the word to other small businesses.

---

### Post by bapoumba on 2009-03-07
> **razzz said:**
> Sure, feel free to copy my post and place it where ever you think it may help spread the word to other small businesses.
Okay thanks. I was thinking about linking to the thread, no need to copy the post. I'll point it out to people taking care of spreading ubuntu news.

---

### Post by simtaalo on 2009-03-07
if your scared that an update will break your system don't do the update. maybe you can set it so you only do the security updates. if you have everything set the way you want it, and think its stable then you don't have to update.

---

### Post by mkvnmtr on 2009-03-07
This does seem to be the best most well presented experiences post I have read. No sugar coating, no rant about what didn't work just what you had to do to get the os working for you.

---

### Post by razzz on 2009-03-07
> **shirteesdotnet said:**
> Razz.... With all the money you've spent, you deserve an award for helping with the linux technology. Maybe codeweavers didnt fix your problems, but down the line they may have learned something new they can apply elsewhere in the future.

I too am in a small family business and right now we have XP as the server, the accounting computer is also XP (for quick books pro) and all the other computers Ive switched to Ubuntu. They all work great! I do have one scanner that doesnt work... a Canon slide scanner. Cannon is known for not opening their source. I had bought it before I had got into linux a couple years ago. I'll have to find a high quality slide scanner that works well with Xane. Our entire network would be Ubuntu linux if I could get Quick Books to work or to find a decent native to linux business accounting program we would make the complete switch. I havent found anything yet. My wife is going to a university right now to get her masters in accounting and, I forget the name offhand, they are pushing a new Microsoft business accounting software on her that it is, i guess, becoming industry standard. While Im at it, my wife wont make the switch to linux becuase she NEEDS MS Money to work for her for our personal finances. None of the other free money management programs for linux appealed to her (ive tried them all and some look good to me, but what do i know). Ive also never been able to get MS Money to work in wine, although countless people report doing so. (I do have FIFA08 soccer working though ha!).

Yah, there are hurdles but every time a new release of Ubuntu comes out things get easier and easier. For us that like to tinker, we can accomplish a lot, save a few problems here and there. I personally have made the full switch to Ubuntu and Im getting a lot of friends and family on board, but nothings perfect.

Just want to say thanks for sticking with it. You may have indirectly helped me down the road when I need a wine program to work in ubuntu!

Hi there,
I have experienced your scanner and quick book pro problem and have resolved them.

Scanner: Epson is selling refurbished discontinued models. I just purchased an Expression 1680 for $359.00. 60 day warranty and is fully supported by SANE. Shipping was included and they shipped it next day air.
Here is a link: [http://www.epson.com/cgi-bin/Store/consumer/consDetail.jsp?BV_UseBVCookie=yes&oid=36816257](http://www.epson.com/cgi-bin/Store/consumer/consDetail.jsp?BV_UseBVCookie=yes&oid=36816257)


Quick Books Pro: We are using QuickBooks Pro 2007 with 3 licenses. The QuickBooks company file is sitting in a directory on an Ubuntu Server. The workstations have a copy of XP running in VMware with Quick Books Server installed.

In order to get the files to reside on the Ubuntu server, make a Quick Books Backup then copy the backup file to a directory on the server.
Launch QuickBooks in XP running in VMware on an Ubuntu workstation (or an actual XP workstation) then choose "restore company file". It will ask what directory to restore the backup to, specify the directory on the server.  The only issue I had was that I needed to install the server version of QuickBooks on all 3 workstations. After that, all users can log in and use the files at the same time. I also had to call Intuit for a new key code to activate the software. I told them that I upgraded the OS and needed to reinstall QuickBooks and they gave me the new code over the phone.

As for the money I spent with Codeweavers, I don't see it as a loss. I agree that if the work they did trying to get my software to work helps them down the road to be able to support other windows software to run then it can potentially be a benefit down the road.

Hope this helps and thanks for your reply.

---

### Post by wolfen69 on 2009-03-07
i didn't read the story, but, welcome to open source!

---

### Post by Ms_Angel_D on 2009-03-07
Hi there Razzz! I'm not a business person, actually I'm just a stay at home Mom and Housewife who happens to really love learning about and using computers. I frequent this particular section of the Forums on a regular basis, and I just want to say that reading your story was quite refreshing, much better than the usual "rants" I see. It's nice to see someone who didn't give up and immediately and walk away at the first sign of trouble. Thank you so much posting and sharing your story, and I hope things continue to go well for you and your business.

---

### Post by armandh on 2009-03-07
As a user of QB for 2 real estate ventures, one active sub S and one winding down LLC, also another wind down C corp, and a very active member operated club organized as a not for profit; I would LOVE a Linux native QB but there is not yet a reason for me to go to the lengths you have. congratulations, but for now I'll dual boot XP.

---

### Post by betrunkenaffe on 2009-03-07
I do some system maintenance and management for my father's small business (he does much himself). He's using QB as well which is the only thing stopping him from looking at Linux as a viable alternative OS choice for his business. I'll share this with him as a potential solution since he'd like to lock down his machines alot more (and linux provides that control).

On the updates thing, I would highly recomend not introducing any update to all machines until it has been tested on your network, not even security updates. I'd disable updates on all the machines and then check updates on a non-critical machine at the selected time interval (daily, weekly, etc). Install the ones you deem necessary and then see if the user has any problems over the next few days. If they do, you'll need to fix it... Ideally you should backup the non-critical machine before you do the updates so you can restore it to pre-update form.

---

### Post by razzz on 2009-03-08
> **betrunkenaffe said:**
> I do some system maintenance and management for my father's small business (he does much himself). He's using QB as well which is the only thing stopping him from looking at Linux as a viable alternative OS choice for his business. I'll share this with him as a potential solution since he'd like to lock down his machines alot more (and linux provides that control).

On the updates thing, I would highly recomend not introducing any update to all machines until it has been tested on your network, not even security updates. I'd disable updates on all the machines and then check updates on a non-critical machine at the selected time interval (daily, weekly, etc). Install the ones you deem necessary and then see if the user has any problems over the next few days. If they do, you'll need to fix it... Ideally you should backup the non-critical machine before you do the updates so you can restore it to pre-update form.

QuickBooks is probably one of the biggest hurdles holding businesses back from totally migrating to Linux. I did find a few good Linux based accounting packages out there but I haven't found a single one that can import an existing QuickBooks file.

VMware has provided me a solution for QuickBooks and a few other wind-O's apps that I could not find a viable Linux solution for. If the virtual version of XP ever blows up or degrades, VMware can either restore it from a snapshot or you can make a tar.gz archive of the entire guest OS and simply replace it when needed. I have no real data living on any workstation running a virtual version of XP. All of our data, including our QuickBook files, reside on an Ubuntu server which is backed up daily.

As for the updates, I installed a virtual copy of Ubuntu in VMware on one of the workstations. I have all the Ubuntu machines set to only look for updates on a daily basis but not to install them. I install the unpdates once a week on the virtual version of Ubuntu first. If all goes well with the virtual copy of Ubuntu, I will then update all the other machines on the network. So far so go.

Thanks for the link. Good reading. I completely understand and totally agree with the article that Linux/Ubuntu is not a substitute for Windows, it is a totally different animal. What is the point of replacing an OS that you dislike with another OS that is trying to be like the one you are trying to get away from?

Linux being open source and providing the ability to customize just about every aspect of it was what really got my attention. Not to mention the stability once it is up and running. I also find that if you dig deep enough, you can find a solution for just about anything. 

Besides needing to run QuickBooks, most of our vendors prefer to have purchase orders submitted via fax. When we upgraded from 98 to XP we lost the ability to have a fax server and clients on each workstation. Linux provided me a solution, HylaFax server. Each Ubuntu and virtual XP system has a fax client installed that can send fax jobs to HylaFAX. The only fax server/client I was able to find that would run in XP was very expensive. Though it took a little effort to install and configure, Hylafax server and the fax clients were totally free, including the clients for the virtual XP systems.

---

### Post by razzz on 2009-03-08
> **emshains said:**
> Don't take me wrong, the following is not to tell you that you are wrong. 


Firstly, about the updates. Ubuntu is based on debian, and some of the devs, who started ubuntu, were folks from debian. They were upset of the main devs from debian, because the liked to keep their repositories rock solid, with content which was thoroughly tested, but was a bit old. The ubuntu dudes didn't want that because they wanted to let people use the latest stuff. So they made ubuntu. And, since they are trying to keep up to the latest stuff, there are so much updates, but don't get me wrong, this ain't no rolling-release OS, like archlinux is. And ubuntu also has fixed release dates, which means, they may release an unfinished product, and later fix the impurities. That's why it is wise to stick with an LTS version, or just to wait a month or two before upgrading. 

Secondly, about the workstations. Since linux is most commonly used in servers than in pc's, it is supports server hardware better, and the server hardware components don't vary so much. Of course, times change, linux is starting to "storm" the desktop market, but it sill has issues. And just like any new product, there must be some time, before it is supported. You can't blame linux for not having support for your hardware, but you can('t) blame the hardware dev. The best supported hardware is the one that is used in home pc's, that have a separate GPU etc. The low spec'ed office computers you might have, are usually ran by windows, so the manufacturers didn't bother to make good drivers, whereas ati has opened up their drivers for the community. 

Well, since I am just a teenager "who knows computers", I actually hate the pop-up thingies. If I need help, I either type "man [program]", or hit F11, or google for it. I can't always rely on the forum, so I check the documentation. We must all agree, there are better documentated distribution's out there, but it is hard to just rewrite a tera-byte of data, but still, the devs are working on it. And, the how-to's and hints described in different sources, such as softopedia, are better written, because people get paid for the job. Here, well, it is all community built. 

I am glad, that you find ubuntu suited your needs, better yet, that you reported your experience, because any feedback from the users will actually help future development of the system.

Thank you for your reply.

Yes, I understand that Ubuntu is more up to date with it's packages then Debian which is a bit conservative with their offerings. I also prefer to be using more current stuff myself as long is it reliable and very well tested before it is released. I am currently using 8.04LTS. 

I don't care for a lot of pop-up thingies either and usually turn them off once I understand what is going on. I suggested that this feature be included (but should be able to be turned off by the user is desired) with the desktop as many PC users are not computer experts and many have probably grown up with and only know wind-O's and IE. Placing a totally new and different desktop, or even a different browser, in front of them without these kinds of instant gratification help pop-ups that they are accustomed to seeing may cause many of them to loose interest and give up before ever giving Ubuntu a fair try. Though many of us would and do search the internet for answers, there are many that probably wouldn't take the time and each one that gives up is one less potential Ubuntu user and supporter. Several of my employees have become interested in Ubuntu since they started using it at work. These are people who use computers as tools on a daily basis at work and at home. They are not ones to tinker with their OS. Two have downloaded Ubuntu and tried to set things up on their home computers. Both got stuck and ended up coming to me for help. Their difficulties, along with my own experience learning how to configure certain things in Ubuntu, prompted my original comment concerning on screen help.

---

### Post by hyper_ch on 2009-03-08
> Now that I finally have most things configured and running, my only concern is that one day an update may break something and I may not have the knowledge to fix it FAST.
Then I would enable only security fixes and no other updats.

> I've already been through one kernel security update that caused Vmware to stop working. It was easy to fix,
Well, the kernel modules need to be recompiled. This happens when the kernel gets updated.

> However, I am counting on the current LTS version to continue to provide stable and reliable performance until the next LTS version s released.
LTS does not equal "stable". It's just long term support. At the end of its support time it will be very stable but not necessarily from the beginning :)

---

### Post by zerubbabel on 2009-03-08
I haven't tried it, but NolaPro offers a web-based accounting package for Linux, which is free but not open source, and has a (non-free, $29) QuickBooks converter:
[https://extras.nolapro.com/product_info.php/products_id/97](https://extras.nolapro.com/product_info.php/products_id/97)

I'd love to hear if someone has used this successfully.

---

### Post by Nastybuzz on 2011-03-29
Chase the Dream my lovely small buisness owner! im so glad the story didnt end with u pouring thousands of dollars into a free os without any success! when it comes to the patching i would definately set it all to manual; so u can at least plan a patch day or an all-nighter. whatever u do just be successful, 'cause i would hate to turn your long story of accomplishment into a long beat down of the shortcomings of ubuntu. Good Luck and High Five! Please give us an annual update or something, im interested.

Nastybuzz

---

### Post by rgb1701 on 2011-03-29
> **razzz said:**
> 

Though Ubuntu is free of charge, **I would have gladly paid for a license that came with technical support**. I did visit Cononical's site and their rates seemed a bit high. I got the impression that they are focusing on selling support contracts to very large businesses, not the little guy.


Bye Bill!

I hear this argument often.

I have never seen anyone who bought a PC with Windows in the US from typical outlets (Staples, Best Buy, Newegg, etc) ever get "free technical support" from the seller, the computer maker, or Microsoft.  AFAIK, true "technical support" is always an extra line item purchase, or extra cost if part of a support contract for a business buying many PC's with Windows.

In 20 years I have never heard of anyone who got real "free" technical support from Microsoft, even though the OS has been forced onto 90%+ of computers on the planet!?

So I don't see how the "technical support" issue is any different between Windows and using Linux/ubuntu

---

### Post by lancest on 2011-03-29
> **razzz said:**
> 
 I am disappointed with some of the annoying quarks the desktop presents on occasion. Workstations occasionally are missing some launchers from their panel after bootup
Bye Bill!

I hear you!
Seems to be solved in 11.04 since the Gnome system tray is gone - with Unity.

---

### Post by overdrank on 2011-03-29
Back to sleep thread. Thread closed :)

---

