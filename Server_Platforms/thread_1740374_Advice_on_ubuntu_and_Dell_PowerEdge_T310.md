---
title: "Advice on ubuntu and Dell PowerEdge T310"
date: 2011-04-26
forum: Server Platforms
---

### Post by Macgos on 2011-04-26
Hi all, I am new to this forum, and new to servers and ubuntu in general.

I am taking a leap and upgrading my small office computer to a server, and wanting to use ubuntu to operate it.

Can someone please confirm for me that ubuntu will work fine on this server: [http://configure.ap.dell.com/dellstore/config.aspx?oc=t420319nz&c=nz&l=en&s=bsd&cs=nzbsd1&model_id=poweredge-t310](http://configure.ap.dell.com/dellstore/config.aspx?oc=t420319nz&c=nz&l=en&s=bsd&cs=nzbsd1&model_id=poweredge-t310)

If it is possible, is it really as simple as purchasing the server with no operating system, then burning a disk from the server files on this site and installing it on the new server? Cos that would be great...:D

I am wanting to host my websites and email locally on the server and also for file access and remote access etc...

Five days ago, I was unsure even what a server could do for me, so this is a big learning curve - but very interesting.

You help would be much appreciated.

Thanks,

Mark
Newbie:P

---

### Post by Buntumatic on 2011-04-27
> I am wanting to host my websites and email locally on the server and also for file access and remote access etc...An old Pentium could do all this, running Linux ... May need Pentium III if your websites use databases.
But if you must spend $$$$ go ahead, Linux will run on this machine.
BTW, last time I checked Ubuntu server didn't have GUI (GUI is a waste of resources), can you manage your server using CLI?

---

### Post by Macgos on 2011-04-27
Re using CLI - am new to this, but if everything is detailed in the server install manual - ie: what to type etc......hopefully it would be ok....

I run several phpbb forums - plus I need more local processing power than what I currently have. All about future proofing really. 

It's a big jump up to learning about servers and ubuntu etc...might be best to pay canonical for help I guess...??

---

### Post by Buntumatic on 2011-04-27
Well, you can try Ubuntu server. You cannot lose trying it. Even if it proves too tough for you you will learn something regarding Linux and POSIX systems in general. That's not bad, is it? :)

You can try CentOS, which has a GUI and is a free version of RHEL. Or, you can get Red Hat, pay for support and they will help you.

---

### Post by spynappels on 2011-04-27
I'd say go for Ubuntu Server, and learn to use the CLI. There is also Webmin for tasks that you need a GUI for.

The most important thing I was told when I started doing this was to take the migration in stages.

Start with the websites, and get them running the way you want while leaving your email on the old server. Once you are happy with how to setup and configure Apache (or whatever webserver you choose to use), then look at adding the email functionality, or the FTP functionality or any other functionality, making sure that each one is running well before moving on to the next one.

Oh, and backup everything!

---

### Post by skrag on 2011-04-27
> **Macgos said:**
> if everything is detailed in the server install manual - ie: what to type etc......hopefully it would be ok....

HAHAH server install manual? That's hilarious. Dont buy this server and expect it to go smoothly with everything you need. You will have a LOT of reading to do, a LOT of forum searching and a LOT of IRC help. Ive been a server admin for years and I still spend ridiculous amounts of time researching stuff on the web. Ubuntu is by far the best documented distro, but its still cryptic.

---

### Post by spynappels on 2011-04-27
> **skrag said:**
> HAHAH server install manual? That's hilarious. Dont buy this server and expect it to go smoothly with everything you need. You will have a LOT of reading to do, a LOT of forum searching and a LOT of IRC help. Ive been a server admin for years and I still spend ridiculous amounts of time researching stuff on the web. Ubuntu is by far the best documented distro, but its still cryptic.

Way to go with the help! That is unnecessarily pessimistic, following one of the excellent how-tos available online, it will NOT be as painful as that. Server installation can be reasonably straight forward, especially if the OP takes it one task at a time like I suggested.

---

### Post by Macgos on 2011-04-28
Thanks for taking the time to comment all...I really appreciate it....

Spynappels - your advice is great. Thanks....taking one step at a time seems like the most sensible and safest thing to do.

Can you suggest a particular how-to online to get me started? 

Re setting things up in stages, I am therefore presuming with the OS install, that I can throw in the disk again and add these extra features in my own time - say three months down the track? I don't need to load everything all in one go?

Yes, I know my questions are very basic, but we all have to start somewhere in our quest for knowledge ;)

I also purchased a Linux for Dummies book today...learned a bunch already.... quite an exciting journey me thinks....

---

### Post by spynappels on 2011-04-28
The easiest thing is to install the base OS with LAMP and SSH server and then you can add modules directly from the repositories, without having to put the disk in again. This can be done anytime and just needs an internet connection.

I'll try and dig up some how-tos, although the instructions in the Ubuntu Wiki pages is very good. 

As you seem happy enough to buy books, always a good idea IMHO, take a look at "Beginning Ubuntu LTS Server" and "Pro Ubuntu Server Administration", both by Sander van Vugt and both published by Apress. I found these books to be a fantastic help when trying to do new things with my servers. I still refer to them from time to time myself.

And of course, ask here, we try our best to help!

---

### Post by Macgos on 2011-04-28
Hey thanks for those book titles - I will take a look. ;)

---

### Post by elico on 2011-04-29
if you do ask me the next linux OS afetr RH is ubuntu.
RH is an enterprise class OS and has a lot of industry support by hardware vendors.
ubuntu have major support from many vendors such as dell and some of ibm servers.

i worked on a big system for more then 20000 users that is using ubuntu as one of the major OS in the infrastructure.
basic install with ssh + LAMP + mail server is simple to do.

---

### Post by Macgos on 2011-04-29
Thanks elico - I am slowly getting some confidence in giving this a go....

I think I have settled on the Dell Power Edge T310...seems pretty grunty and should future proof my business for some years.

I will definitely use ubuntu server OS....for one, there seems to be a great bunch of friendly guys willing to help out :P...and that to me is brilliant.

So..(another silly question), If my servers OS is ubuntu, should my desktop machine also be migrated to ubuntu too? I believe I can also run MS and ubuntu on the same machine...?

Also, will LAMP provide me with everything I need to move my phpbb forums across from my existing web host?....on first glance (MySQL etc)...it seems it would....

---

