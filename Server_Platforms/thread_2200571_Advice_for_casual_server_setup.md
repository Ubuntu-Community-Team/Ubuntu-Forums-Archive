---
title: "Advice for casual server setup"
date: 2014-01-20
forum: Server Platforms
---

### Post by darko19th on 2014-01-20
Couple of years ago I acquired 3 big server computers and one HP storage-works, all in good working order. At that time I installed Ubuntu 10.04 server on each of those, and did a lot of update/upgrade but didn't really know what to do with it. So, I switched them off and stored them.
Last year, at home, I installed the 12.04 server on one of my desktops and after a lot of reading successfully made it work as a DNS and WEB (locally only) servers , SSH, FTP, Samba, and (painfully) mail server. Proudly, I've configured the iptables to regulate the traffic. This week i will try installing a VPN to be able to administer my server when on holidays.

Now i would like to replicate all of this at work (even if it is not really needed) but i have 3 server-computers and another one (more recent) is coming. At work we have ADSL2 connection, 5 employees, 4 win7 desktops and my Debian laptop. No apparent business need for data center (for now).
Could somebody give me advice on how to divide all of the server software into 4 server machines. All machines have 2 NIC; should I use one of them as a dedicated firewall?

I'm doing all of this mostly for fun and pleasure (therapy as well), and a little bit for work (we are still heavily dependent on MS WIn). And why should only system administrators have all the fun?

---

### Post by CharlesA on 2014-01-20
If they already have the infrastructure in place, I would say not bother.
If a migration will not either A) Make them money B) Make it easier to do their jobs - they will not go for it. I would definitely talk to the IT manager first and get their OK on it before doing anything. If they do not agree with your assessment, leave it alone and just mess with it at home.

I fought tooth and nail with the IT manager at the place I work to get a wiki moved off a Windows 2K box and onto something newer so I could actually make sure everything was up-to-date. In my case, I did the project on my own after I made the argument that the wiki was slow because of the outdated hardware it was running on and the lack of any updates since it was installed made it vulnerable. Improved response time = less time waiting for information = improved productivity = $$$

---

### Post by koenn on 2014-01-20
I largely agree with charles, 
but you might have some added value yo offer, especially if you the equiment is already free 

stuff like a backup-to-disk solution, a wiki to collect all sorts of useful information,  a file server for the installers for the software the laptop runs so you can easily (re-)install it without having to remember where you left the CD's, ...  . Making this work for windows clients can be an interesting exercise

---

### Post by CharlesA on 2014-01-20
> **koenn said:**
> I largely agree with charles, 
but you might have some added value yo offer, especially if you the equiment is already free 

stuff like a backup-to-disk solution, a wiki to collect all sorts of useful information,  a file server for the installers for the software the laptop runs so you can easily (re-)install it without having to remember where you left the CD's, ...  . Making this work for windows clients can be an interesting exercise

Agreed. That would be something that might help the company increase productivity without costing them anything (other than time).

---

### Post by SeijiSensei on 2014-01-21
If the organization's mail is hosted by a third-party provider, you might consider whether to move it to one of those servers to improve the privacy and security of your mail traffic.

---

### Post by tgalati4 on 2014-01-21
An alternative is to set up one server as a development machine.  Load as many services as it will hold (some suggestions:  [http://bitnami.org/stacks](http://bitnami.org/stacks)) then put together a cut-sheet of services and allow any employees to use them.  Watch the activity and see which services are being used.  Over time a business case will develop and then one of the other servers could be used to host just the services that are needed/useful to the company.

---

### Post by darko19th on 2014-01-23
Thank you all. Now I will have small storage (server room) to fit the server rack. We will start with the system backups and see how it goes.
I will "Solved" this thread and certainly be back with technical questions in a couple of weeks.
Cheers.

---

