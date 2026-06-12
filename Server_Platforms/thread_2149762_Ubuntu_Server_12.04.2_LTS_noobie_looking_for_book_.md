---
title: "Ubuntu Server 12.04.2 LTS noobie looking for book recommendations / help."
date: 2013-05-29
forum: Server Platforms
---

### Post by Rossithecat on 2013-05-29
Hi all.

I'm brand new to Ubuntu and Ubuntu server 12.04.2 LTS and I'm looking for a good current Ubuntu server 12.04.2 LTS book and other tutorial recommendations.

I need to learn EVERYTHING from the ground up. I've never used or configured an Ubuntu or Linux server before.


On Amazon there are a few Ubuntu server books:
[http://www.amazon.com/Beginning-Ubuntu-Server-Administration-Professional/dp/1590599233/ref=sr_1_7?s=books&ie=UTF8&qid=1369873255&sr=1-7&keywords=ubuntu+server+12](http://www.amazon.com/Beginning-Ubuntu-Server-Administration-Professional/dp/1590599233/ref=sr_1_7?s=books&ie=UTF8&qid=1369873255&sr=1-7&keywords=ubuntu+server+12)
By Sander van Vugt.

But this book was written with Ubuntu server 7.04 back in 2008.

Has a lot changed from Ubuntu server 7.04 to Ubuntu server 12.04?
Should I not buy this book because it's so old?

Here's another book by this guy 
[http://www.amazon.com/Ubuntu-Server-Administration-Experts-Voice/dp/1430216220/ref=sr_1_12?s=books&ie=UTF8&qid=1369873255&sr=1-12&keywords=ubuntu+server+12](http://www.amazon.com/Ubuntu-Server-Administration-Experts-Voice/dp/1430216220/ref=sr_1_12?s=books&ie=UTF8&qid=1369873255&sr=1-12&keywords=ubuntu+server+12)

That one seems to be aimed at 'Pros' and those already familiar with Ubuntu server.
It was also written a long time ago, 2009.



Then there are these books by two authors :
[Kyle Rankin]("http://www.amazon.com/Kyle-Rankin/e/B001ILKDJI/ref=ntt_athr_dp_pel_1"), and [Benjamin Mako Hill]("http://www.amazon.com/Benjamin-Mako-Hill/e/B001IQXODA/ref=ntt_athr_dp_pel_2")[COLOR=#666666]
[/COLOR]
This first book of theirs was written for Ubuntu server 10.0.4.
[http://www.amazon.com/Official-Ubuntu-Server-Book-2nd/dp/0137081332/ref=sr_1_2?s=books&ie=UTF8&qid=1369874658&sr=1-2&keywords=the+official+ubuntu+server](http://www.amazon.com/Official-Ubuntu-Server-Book-2nd/dp/0137081332/ref=sr_1_2?s=books&ie=UTF8&qid=1369874658&sr=1-2&keywords=the+official+ubuntu+server)
Written in 2010.

Here's another book by those authors on Ubuntu server that isn't out yet.
Would there be a big difference between the two books and versions of Ubuntu server?
[http://www.amazon.com/Official-Ubuntu-Server-Book-3rd/dp/0133017532/ref=sr_1_1?s=books&ie=UTF8&qid=1369874658&sr=1-1&keywords=the+official+ubuntu+server](http://www.amazon.com/Official-Ubuntu-Server-Book-3rd/dp/0133017532/ref=sr_1_1?s=books&ie=UTF8&qid=1369874658&sr=1-1&keywords=the+official+ubuntu+server)


Is it not worth buying an older Ubuntu server book because it will not have many things in the newer version of Ubuntu server or are the updates primarily bug fixes and security patches?



I doubt this below question is answered in any of those books but I am also needing to learn how to stop or limit the server's bandwidth usage when I need to. This will be to prevent excess bandwidth charges by exceeding my purchased bandwidth amount.


Thank you guys for your help.

---

### Post by CharlesA on 2013-05-29
I like this book:
[http://www.amazon.com/Ubuntu-Unleashed-2013-Edition-Covering/dp/0672336243](http://www.amazon.com/Ubuntu-Unleashed-2013-Edition-Covering/dp/0672336243)

You could also look at the official server guide, too.
[https://help.ubuntu.com/12.04/serverguide/](https://help.ubuntu.com/12.04/serverguide/)

---

### Post by Rossithecat on 2013-05-29
Hello.

That book looks to be mainly for desktop users. I need a server admin book.
I know that book has a small section on running a web server but I don't think it will cover server admin stuff.

I'll start to flip through the server manual.

Thanks.

---

### Post by CharlesA on 2013-05-29
He covers some of both - check out the table of contents. ;)

> You will learn:
GUI (Graphical User interface)
Terminal (Linux Commands)
Setting up Servers
Installing Software
Terminal Tricks
Troubleshooting Ubuntu.

---

### Post by tgalati4 on 2013-05-29
Write your own book.  Check out the pages in NewDocs in the link in my signature.  It's got 1,000 pages of linux documentation.  Use the search bar to find server-specific tutorials.

---

### Post by CharlesA on 2013-05-29
> **tgalati4 said:**
> Write your own book.  Check out the pages in NewDocs in the link in my signature.  It's got 1,000 pages of linux documentation.  Use the search bar to find server-specific tutorials.

Huge +1 to that. You tend to learn when you break things. ;)

---

### Post by SeijiSensei on 2013-05-30
I recommend browing the offerings from [O'Reilly]("http://www.oreilly.com/"), for years the definitive source on Unix administration.  When I started out, my "bible" was Craig Hunt's [TCP/IP Network Administration](http://shop.oreilly.com/product/9780596002978.do).  

For one-stop shopping, I also endorse the [Ubuntu Server Guide]("https://help.ubuntu.com/12.04/serverguide/").  Otherwise you should begin by identifying the services you wish to run on your server and focus just on those.  Remember that there is generally nothing unique about Ubuntu when it comes to mainstream server programs like Apache, Postfix, or dovecot.  For any service you might wish to offer there are a variety of alternative open-source programs available.  For SMTP mail exchange, for instance, there are sendmail, Postfix, exim, and qmail.  Each have their pros and cons, and you'll find advocates for each (and often bashers of the others).  For web services, Apache faces a new competitor in nginx.  In general, you are probably best off at the start to stick with the programs distributed by default with Ubuntu: [Postfix](http://www.postfix.org) for SMTP, [dovecot]("http://www.dovecot.org/") for POP3/IMAP, and [Apache](http://httpd.apache.org/) for HTTP/HTTPS.  The websites for these programs all have extensive documentation available as well.

As for bandwidth management, the usual method is to use iptables rules or "wrap" the programs in xinetd.  A Google search should lead you to some solutions.

---

### Post by LHammonds on 2013-05-30
You could learn a lot from trial-n-error.  I recommend heavy use of VirtualBox to install Ubuntu Server.  Once you are fairly confident and set on the initial installation and configuration, you can make snapshots and revert back to them when testing things out such as installing software packages.

Check my sig for links to what I have learned installing and running Ubuntu Server.

The initial main topics to learn are:
 * Partition Design (RAID/LVM/file systems)
 * User/Group/Other file permissions.
 * Bash Scripting + Crontab.
 * Use of "man" (manual) pages.
 * Firewall and AppArmor.
 * SSH, PuTTY, WinSCP.
 * Maintenance tasks (apt, df, etc.)
 * Monitoring (ram, cpu, disk, network, Nagios, etc.)
 * Backup and Restore (partition and file level, full and differential, archiving)
 * Advantages/Disadvantages regarding installing from source/repository/other

---

### Post by gordintoronto on 2013-05-30
Let me also note that you almost certainly would be better off running Ubuntu Desktop. Desktop can do everything that Server can do. It has a bit of processor and memory overhead, which is important if you are running a high-volume web site or a busy database server. On the other hand, you have all the GUI tools available, which cuts the learning curve dramatically.

---

