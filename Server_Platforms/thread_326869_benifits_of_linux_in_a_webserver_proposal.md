---
title: "benifits of linux in a webserver proposal"
date: 2006-12-28
forum: Server Platforms
---

### Post by at0mic on 2006-12-28
Hi,

I dont see one of these threads anywhere so i thought id start one for those of you doing the same thing which is proposing linux / ubuntu for servers and the benifits of doing so. if i miss anything feel free to add.

Benefits:

•	Security of Linux which includes immunity to common Microsoft Windows worms, viruses and the like. 
•	Free open source operating system. This will free up a Windows XP / Vista license as well as a Symantec Antivirus license. This lowers total cost of ownership.
•	Ability to install additional free software and services such as a secure internal access only FTP server which will vastly improve the speed and efficiency of common website updates. This maintenance time savings lowers total cost of ownership.
•	Assurance of security updates and operating system life for 5 years. The Linux distribution has long term support from its developers.
•	Vastly improved TCP/IP internet protocol and system resource management resulting in faster download speeds and page load times for all.
•	Increased uptime with improved stability. System updates generally do not require reboots either resulting in potential uptime of months to years.
•	Offers potential for designing a more dynamic webpage with PHP/Perl/Python and MySQL.
•	Highly secure default configurations and very fast to install. This reduces total cost of ownership.
•	Very low maintenance time with Debian based Linux distributions. One or two commands will update all software on the system.

---

### Post by MrHorus on 2006-12-28
> **at0mic said:**
> 
•	Free open source operating system. This will free up a Windows XP / Vista license as well as a Symantec Antivirus license. This lowers total cost of ownership.

That's debatable, as you may require additional support as many orginisations lack the nescesary UNIX/Linux expertise so the TCO gains you make may be swallowed up by ongoing support.
> 
•	Ability to install additional free software and services such as a secure internal access only FTP server which will vastly improve the speed and efficiency of common website updates. This maintenance time savings lowers total cost of ownership.

See above.
> 
•	Assurance of security updates and operating system life for 5 years. The Linux distribution has long term support from its developers.

5 years is quite some time but it's similar to the length of time that Microsoft have supported NT4 and Win2k.

> 
•	Vastly improved TCP/IP internet protocol and system resource management resulting in faster download speeds and page load times for all.

Can you post your benchmarks for this?

> 
•	Increased uptime with improved stability. System updates generally do not require reboots either resulting in potential uptime of months to years.

I would agree with this one.

> 
•	Offers potential for designing a more dynamic webpage with PHP/Perl/Python and MySQL.

This isn's a specific benefit to Linux - I can and have ran Apache, PHP and MySQL on Windows machines many times in the past.

> 
•	Highly secure default configurations and very fast to install. This reduces total cost of ownership.

Where is the connection between speed of install and Total Cost of Ownership?

> 
•	Very low maintenance time with Debian based Linux distributions. One or two commands will update all software on the system.

This is again something that I can agree with.

I am not trying to be intentionally nasty but most of your arguements are flawed and certainally not something that you would want to take to a boss as part of a project proposal for example.

---

### Post by at0mic on 2006-12-28
do share how u would propose / word . i dont think i did THAT bad of a job :)

the difference in xfer rates between a linux host server [doest matter the application] compared to a windows server is mind blowing. take 2 connections and speed test using any app to find out for urself. the higher the bandwidth available the more noticable the difference. And dont tell me windows xp does a better job with 256MB of RAM :)

 reduced time to install / configure and reduced risk of misconfiguration definately relate to your TCO

---

### Post by MrHorus on 2006-12-28
> **at0mic said:**
> 
the difference in xfer rates between a linux host server [doest matter the application] compared to a windows server is mind blowing. take 2 connections and speed test using any app to find out for urself. the higher the bandwidth available the more noticable the difference

Well show me the TCP/IP stack benchmarks then :)

> 
 And dont tell me windows xp does a better job with 256MB of RAM :)


It's no secret that Linux gets more out of less resources but I wouldn't run a production enterprise server with only 256MB of RAM.

>  reduced time to install / configure and reduced risk of misconfiguration definately relate to your TCO

In an enterprise environment there are likely to be large numbers of support staff who are competant enough to install and configure a Windows Server environment and relatively few that have Linux experience - this *is* likely to have an impact over the lifetime of the system but with all things being equal and there being suitable Linux-aware staff, I don't see how a quick install is going to impact the TCO in either the long or the short term.

---

### Post by Miademora on 2006-12-28
While these benchmarks are a bit dated its upto you what you read out of it

[http://www.kegel.com/nt-linux-benchmarks.html]("http://www.kegel.com/nt-linux-benchmarks.html")

Please read also this article

[Mark Russinovich on Linux Versus Windows NT and Benchmark Reliability]("http://www.linuxtoday.com/news_story.php3?ltsn=1999-04-30-015-05-PS")

---

### Post by SuperMike on 2006-12-28
•	Security of Linux which includes immunity to common Microsoft Windows worms, viruses and the like. 

What's one of the points why Apple bolted their OS onto BSD Unix? Many reasons, but one of the major ones was security. And this was from a company which already had a relatively very low problem with viruses and so on. Linux, a clean room re-interpretation of BSD Unix, is based on the same sound strategy of being tough with security deep in its design. It's also not about what's built into Linux that makes it more secure, but the common design principles and practices followed by the community, as well as the ability to read the source and see the weaknesses.

Also note ClamAV is fairly good as well as a custom iptables firewall script. On Windows the established practice is to have to pay for these two things.

•	Free open source operating system. This will free up a Windows XP / Vista license as well as a Symantec Antivirus license. This lowers total cost of ownership.

TCO goes down on product cost when using Linux, but can go back up on tech support. However, if done properly, even a novice Linux sysop with the ability to use online forums can work like a pro and save a company a lot of dollars in product support costs. Still, product support subscriptions are a good idea for mission critical systems.

•	Ability to install additional free software and services such as a secure internal access only FTP server which will vastly improve the speed and efficiency of common website updates. This maintenance time savings lowers total cost of ownership.

True.

•	Assurance of security updates and operating system life for 5 years. The Linux distribution has long term support from its developers.

Yep.

•	Vastly improved TCP/IP internet protocol and system resource management resulting in faster download speeds and page load times for all.

Yep.

•	Increased uptime with improved stability. System updates generally do not require reboots either resulting in potential uptime of months to years.

Oh yes, most definitely! I'm still having to do monthly reboots on even W2K3.

•	Offers potential for designing a more dynamic webpage with PHP/Perl/Python and MySQL.

I prefer PostgreSQL, but your call. You might want to see the stats on transactions per minute and how PostgreSQL can scale greater than MySQL after more than 20 simultaneous, heavy transactions.

•	Highly secure default configurations and very fast to install. This reduces total cost of ownership.

That's something I love about Linux. By default, most stuff is turned off and you have to opt-in in order to expose a potential service (and thus a potential weakness). On Windows, it's often the inverse.

•	Very low maintenance time with Debian based Linux distributions. One or two commands will update all software on the system.

Yep.



I have some more:

•	The Windows IIS server uses a database inside it that is proprietary and can potentially be corrupted with very little recourse for you to resolve it. Microsoft gives you a viewer/editor tool in the ResourceKit, but it can't help when the database is corrupt. With Linux, the Apache configuration is stored in text files.

•	The ability to change the settings on a web server in text console mode by editing some text files and bouncing web services at command line, rather than having to use a GUI.

•	The ability to host a server without a GUI, thereby giving more resources to the server and providing more uptime because the GUI bugs won't be there to potentially affect the rest of the OS.

•	Apache is the defacto/dejure standard on the web for almost all web hosting. There's more Apache out there than IIS hosts. Apache also has a longer history than IIS.

•	Microsoft only updates IIS with performance improvements every so many years. The Apache team is improving performance at least every 6 months. Microsoft may leapfrog the Apache team on an initial release of a product, but they can't hold those bragging rights for even more than two months.

---

### Post by at0mic on 2006-12-31
thnx for the comments. ill definately use pieces of it

---

