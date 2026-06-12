---
title: "New Book on Ubuntu Server coming soon"
date: 2007-11-19
forum: Server Platforms
---

### Post by JulieM on 2007-11-19
Hi everyone,

Julie from Apress here. I wanted to let everyone know that we'll soon be publishing our newest Ubuntu-based book: *Beginning Ubuntu Server Administrator* by Sander van Vugt. We should have copies in early-mid December.

 More information about the book is available at the book page on our [website]("http://www.apress.com/book/view/1590599233").

Here's some information about the book:

*Beginning Ubuntu Server Administration* guides you through all of the key configuration and administration tasks you’ll need to know. Whether you’re interested in adopting Ubuntu within a Fortune 500 environment or just want to use Ubuntu to manage your home network, this book is your go–to guide to using the distribution securely for a wide variety of network services. Topics include file, print, web, and FTP management, command–line tips and tricks, automated installation, configuration and deployment processes, and kernel management.

What you’ll learn:

* Effectively and securely install, update, and deploy your Ubuntu server.
* Configure your server to operate most effectively for a wide variety of purposes, including as a web server, FTP server, and a file and printer manager.
* Rev up your command-line knowledge by taking advantage of little-known shell–related features, tips, and tricks.
* Remotely manage your server through a wide–variety of services.  

 * ISBN10: 1-59059-923-3 | ISBN13: 978-1-59059-923-5
  * 350 pp. | Will Publish in Dec 2007 |$39.99 US

I'm looking for a few folks that would be interested in reading the book, and writing reviews for this site, as well as other community and resale sites. If you're interested, please email julieATapressDOTcom. Cheers!

---

### Post by hkgonra on 2007-11-20
If you get any reviews please add the link to this thread. 
I will be watching. :-)

---

### Post by jmorrow on 2007-11-20
This is great news.  I have been looking for a book focused on Ubuntu server!

---

### Post by meatpan on 2007-11-20
> **JulieM said:**
> 
* Effectively and securely install, update, and deploy your Ubuntu server.
* Configure your server to operate most effectively for a wide variety of purposes, including as a web server, FTP server, and a file and printer manager.
* Rev up your command-line knowledge by taking advantage of little-known shell&#8211;related features, tips, and tricks.
* Remotely manage your server through a wide&#8211;variety of services.  


What makes these ubuntu-specific?  Don't get me wrong, all of the topics sound interesting.   With the exception of the first bullet, how does the content specifically relate to ubuntu, as opposed to any of the numerous flavors of linux servers?

---

### Post by DaveTurnbull on 2007-11-20
I'm new to server administration and Ubuntu in general, so I'll definitely pick up a copy. :)

---

### Post by JulieM on 2007-11-20
Hi Meatpan,

Sure, these topics could be covered in any SysAdmin book, the difference here is that the author focuses solely on using the Ubuntu server to get the job done.

The text that I included yesterday was a little generic, so here's the back cover author letter.
------------------------------
Dear Reader,

For the past few years, many have hailed Ubuntu Linux as the best chance to finally sway the computing masses toward the Linux desktop. And it’s easy to see why: it offers an amazingly user-friendly interface, intuitive installation and configuration process, and an enormous choice of applications. Indeed, it’s become so popular that system administrators are rapidly adopting Ubuntu Server Edition to configure, deploy, and manage network services more effectively than ever before.

Whether you’re interested in using Ubuntu within a Fortune 500 environment or just managing your home network, you hold in your hands the only book you need. While writing it, I kept your daily administration tasks constantly in mind, and I’ve included chapters on how to set up and run Ubuntu Server as a file and print server, a virtualization server, and a web server. I also show you how to perform many other tasks that you’ll frequently encounter as an Ubuntu Server administrator, such as automating installation, configuration, and deployment processes, and managing the kernel. 
Along the way, this book will help you become a more proficient administrator as you learn to take advantage of little-known shell-related features, tips, and tricks. Efficiency is a major theme of this book, and you’ll also learn how to optimize, troubleshoot, and remotely manage your server.

Reading this book will help you master every aspect of Ubuntu Server, from both the command line and the graphical interface. Whether you’re about to manage your first server or are interested in expanding your knowledge of Ubuntu Server, this is the book for you!

------------------------------
And the chapter level table of contents:

CHAPTER 1 Installing Ubuntu Server
CHAPTER 2 Getting the Most Out of the Command Line
CHAPTER 3 Performing Essential System Administration Tasks
CHAPTER 4 Performing File System Management Tasks
CHAPTER 5 Configuring Your Server for Security
CHAPTER 6 Setting the System to Your Hand
CHAPTER 7 Running It Anyway You Like
CHAPTER 8 Making Connection
CHAPTER 9 Configuring Network Infrastructure Services
CHAPTER 10 Using Ubuntu Server As a File and Print Server
CHAPTER 11 Setting Up Web Services
CHAPTER 12 Multiplying Your Server

------------------------------

Hope these help out. Please let me know if you have any more questions! And I'm still looking for reviewers, so please email me if you're interested.

---

### Post by meatpan on 2007-11-20
> **JulieM said:**
> 
Sure, these topics could be covered in any SysAdmin book, the difference here is that the author focuses solely on using the Ubuntu server to get the job done.

This isn't really what I was getting at (sorry if I was unclear).   I would like to know how you navigate ubuntu in a way that distinguishes it from the  masses of distro-specific server guides.  Put another way, is there content in this book that delves beyond the superficial uniqueness of a linux distribution?  An example of superficial uniqueness is the command used to manage a package, such as 'dpkg'  as opposed to 'rpm' or 'emerge'.

---

### Post by bmathis on 2007-11-21
Sign me up! I would love to review the book.

---

### Post by sanderv on 2007-11-21
> **meatpan said:**
> This isn't really what I was getting at (sorry if I was unclear).   I would like to know how you navigate ubuntu in a way that distinguishes it from the  masses of distro-specific server guides.  Put another way, is there content in this book that delves beyond the superficial uniqueness of a linux distribution?  An example of superficial uniqueness is the command used to manage a package, such as 'dpkg'  as opposed to 'rpm' or 'emerge'.

Hi, I wrote the book so let me comment on that. This book is on "Beginning Ubuntu Server administration". It is supposed to be an introduction to how to perform daily tasks on US for people that don't necissarily have experience with Linux in general or Ubuntu in specific. So let me answer your question with another question, what exactly is so Ubuntu specific about configuration of an Apache server, a Samba server and so on? Think we do agree that the differences are not that big here, so if you are looking for a specific Ubuntu Server angle into these subjects, sorry, the book doesn't offer that. Since it also is a generic book on server administration, that introduces things like package management, yes, I do cover Ubuntu Server specifics here. But I'm afraid we're talking about the superficial uniqueness here. In some other cases the "Ubuntuness" of the book goes deeper, for example when talking about startup procedures. Don't expect miracles here though.

Just out of curiosity: how would you see a book on US to go beyond that superficial uniqueness while still being a good introduction for people that don't have a lot of Linux experience?

---

### Post by meatpan on 2007-11-28
> **sanderv said:**
> 
Just out of curiosity: how would you see a book on US to go beyond that superficial uniqueness while still being a good introduction for people that don't have a lot of Linux experience?

Here are some ideas:
o You can teach fundamentals of processes, filesystems, and networking on a unix-based system
o How to plan an administer a distributed service, from software selection to downstream tasks of run-time debugging. and performance analysis.  
o Coverage and comparison of the major strategies and policies for server security.

These are a few simple, but critical, fundamentals that transcend linux distributions and will help the reader to become a better sys-admin.   Also, none of these topics are well covered in Ubuntu's own Server guide, or the numerous useful server how-to's that have been contributed by the community.

---

### Post by JulieM on 2007-12-27
Hi all,

Sorry for not popping in here sooner, but I wanted to let y'all know that that book is officially available! Your local bookstores should have it in stock, and I've seen it for sale at online retailers as well. And of course, the eBook is available at the [Apress eBookshop]("eBookshop.apress.com").

For those folks that contacted me re: reviews...I'll be getting your copies out next week.

Happy holidays to all, and a safe new year.

---

### Post by dpj23 on 2007-12-27
very interesting  - Thanks for the posting will be watching this one...

---

### Post by adamos on 2007-12-28
I want to review the book. I am working on Debian server administration now and i want to swtich to ubuntu for my web hosting from home.


Thanks

Adam

---

### Post by bmathis on 2008-04-03
For all of those waiting for a review on this book.... here it is!

> Beginning Ubuntu Server Administration, by Sander Van Vugt is a well written book coving a range of topics which includes examples. This book covers Ubuntu 7.04 Feisty Fawn. Although this release is a little behind, the information presented in the book is still relevant for completing the topics covered. I was impressed with the authors ability to show the reader how a task was completed while keeping it simple so new system administrators or others just starting to learn, will be able to understand what is going on.

While the book is geared towards Ubuntu, the majority of the topics can be associated with other GNU/Linux systems with very little or no changes at all. For instance; the command line section helps the user become more familiar with how commands are used with a Linux server system. It also demonstrates how to use the VI text editor which can be a daunt task for new admins. For advanced command line use, chapter 7 covers everything to get someone started in learning how to script which can be used to automate system tasks.

A great reference in this book, is the chapter about virtualization. Virtualization is becoming more and more dominate when it comes to budget and green computing needs. This chapter covers everything from what software you should use to setup and configuration of both the virtualization software and the guest Operating System. 

All in all, Beginning Ubuntu Server Administration: From Novice to Professional, is a well written book and can be used by either seasoned administrators, new techs entering the field, or someone just looking to expand their knowledge. I give this book a solid recommendation and will encourage everyone to pick up a copy.

This review can be found on [amazon.com]("http://www.amazon.com/Beginning-Ubuntu-Server-Administration-Professional/dp/1590599233/ref=sr_1_1?ie=UTF8&s=books&qid=1207244893&sr=1-1") and at my blog [brianmathis.net]("http://www.brianmathis.net/2008/03/31/review-beginning-ubuntu-server-administrator-from-novice-to-professional/"), enjoy :popcorn:

---

### Post by robertmf on 2008-05-25
[COLOR="DarkRed"]2 Ubuntu Server texts for 1/3-off pre-order from amazon.com[/COLOR]

***Beginning Ubuntu LTS Server Administration: From Novice to Professional, Second Edition***   (Paperback)
by Sander van Vugt (Author)
List Price: 	$39.99
Price: 	$26.39 & this item ships for FREE with Super Saver Shipping. Details
Publication target: October 20, 2008

You Save: 	$13.60 (34%)
	Special Offers Available
	Pre-order Price Guarantee. Details
This title has not yet been released.
You may pre-order it now and we will deliver it to you when it arrives. 

-----------------------------------------

[B][I]
Ubuntu Server Administration[/I][/B] (Paperback)
by Michael Jang (Author)
Publication target: November 29,2008
List Price: 	 $49.99
Pre-Order Price: $31.49 & this item ships for FREE with Super Saver Shipping. Details
You Save: 	$18.50 (37%)
	Special Offers Available
	Pre-order Price Guarantee. Details

This title has not yet been released.
You may pre-order it now and we will deliver it to you when it arrives.

---

