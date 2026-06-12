---
title: "New web server: which hardware, how to config software?"
date: 2012-11-29
forum: Server Platforms
---

### Post by krainert on 2012-11-29
Hey people,

I'm currently looking into setting up a server for a student organization at my university. We have capital to spend on hardware, and the IT department has agreed to provide infrastructure so all we have to do is acquire the server hardware and configure it.

So, two questions:
1) Which hardware would be decent? We will probably run a virtual server with an info site and a wiki, nothing too fancy. Our budget is flexible, but as a rule of thumb, cheap is good, as long as the quality is justifiable.
2) Which software do we need for the virtual server, OS (thinking some server version of Ubuntu? I honestly know very little of Linux although I have worked a bit on Ubuntu and Red Hat), web server (Apache default choice?), anything else? Will configuration be difficult?

I have a bachelor's degree in computer science and have worked a bit with everything, but the depth of my experience is limited.

Many thanks!

---

### Post by chadk5utc on 2012-11-30
Hello
 All of the questions you've asked are really personal preference, any of the main stream Linux distro's will do well for this task. I do prefer Ubuntu LTS for simplicity as well as forum support. Installing the LAMP stack Linux-Apache-MySql-PHP and configuration are a breeze. AppArmour, UFW/iptables, fail2ban for security to name just a few. There are tons of "Howto's" for all subjects.

 About hardware again personal preference but I'd have a look at [www.geeks.com](www.geeks.com) if used/refurbished is an option or even [www.newegg.com](www.newegg.com) (not meant as an advertisement for either) both offer advantages, bang for the buck. Though hardware/memory will depend on your estimated load averages. If this is just a web server I believe something like this would work, [http://www.geeks.com/details.asp?invtid=R200-PDC240-PON&cat=SVR](http://www.geeks.com/details.asp?invtid=R200-PDC240-PON&cat=SVR)
again the link references are meant to point you in the right direction give you options, ideas.

---

### Post by SeijiSensei on 2012-11-30
I've run web servers on old i386 boxes.  Web service is not hardware-intensive at all.  Find some old PC lying around and stick a Linux distro on it with Apache, etc., connect it to the network, and you're off and running.  The most important thing is disk space.

On servers, I prefer CentOS, but I have long experience with RedHat-flavored systems.   

If you want a basis for comparison, I'd recommend something like [this low-end Dell](http://www.dell.com/us/business/p/poweredge-t110-2/fs).  Equip it with a SAS RAID card, which Linux supports,  configured for RAID 1 and two 1 TB hardrives for reliability.  The advantage of buying from someone like Dell is the warranty service.  Add the 3-yr 5/10 on-site contract.

You should ask your university if they have preferred hardware vendors and can buy a server for you.  They can probably get a better deal, and your machine would be covered by the institution-wide warranty.

---

### Post by krainert on 2012-12-04
Thanks for the help.
I'll bring this up at our next meeting and see which direction we're taking. If we could have the IT dept. help us buy hardware or use old stuff, that's probably preferable, but let's see :)

---

