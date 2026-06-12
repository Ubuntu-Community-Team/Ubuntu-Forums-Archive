---
title: "Website Server confusion/ Issues"
date: 2015-02-15
forum: Server Platforms
---

### Post by ram19 on 2015-02-15
Hi 

I have recently purchased a server and wanted to install server software to run a website [http://www.directtraveller.com](http://www.directtraveller.com) from it.

Is there a recommended setup Ubuntu has specifically for such use? Can this actually be done or is the software environment just for internal servers and desktops and storage?

thanks

Ram :confused:

---

### Post by Doug S on 2015-02-15
Hi and welcome to Ubuntu forums,

Yes, you should be able to do what you want with [Ubuntu server edition]("http://www.ubuntu.com/server"). I would recommend using the [Ubuntu serverguide]("https://help.ubuntu.com/lts/serverguide/index.html") as your main reference. There is also a [PDF version]("https://help.ubuntu.com/lts/serverguide/serverguide.pdf"), which can be easier to print pages to make notes on.

---

### Post by TheFu on 2015-02-16
> **ram19 said:**
> Hi 

I have recently purchased a server and wanted to install server software to run a website [http://www.directtraveller.com](http://www.directtraveller.com) from it.

Is there a recommended setup Ubuntu has specifically for such use? Can this actually be done or is the software environment just for internal servers and desktops and storage?

thanks

Ram :confused:

There are hundreds of different configurations. Each is used based on the specific requirements for the server.  If you are looking for 1 answer - the *1 true way*, that just doesn't exist. There are different needs, so different configurations.  Flexibility is at the heart of Linux and it is extremely flexible.  All those choices **are** confusing initially but over the years, you'll come to appreciate the options.  I would caution that google will find "how-tos" claiming the 'best way for X" ... it probably is NOT the best way for your requirements, but it could work.

The Ubuntu Server Guide is a good reference. No single guide can prepare you for everything you need to know to securely run a server on the internet. That takes time, trials, errors. Hopefully, your box doesn't get hacked as you learn. If you don't want to commit to this quest for Linux server knowledge (like learning a new language), it is probably better to just pay someone else to do it for you - like I would hire a translator/guide on a trip to China.

---

### Post by ram19 on 2015-02-18
many thanks for your help.. i'm going to look through the guides you have supplied and see where i go from there

---

### Post by TheFu on 2015-02-18
> **ram19 said:**
> many thanks for your help.. i'm going to look through the guides you have supplied and see where i go from there

It is a steep learning curve - like learning a foreign language. Beginner level takes a month of daily effort.

Similarly, the best way to learn is total immersion. Just like total immersion, it can be hard, frustrating, brain-hurting.  I remember this both in my immersive Spanish studies (4 hrs daily in classes + daily living where nobody spoke my native language) and when I was first learning Unix.  

The "server" versions of Unix systems don't have any GUIs. This is painful for constant human interaction and less efficient since copy/paste doesn't work between terminals and other programs as you learn and try things out.  A simple desktop that can easily show many windows concurrently with multiple terminals open to your "server" will make your life much easier.  Since you've selected ubuntu server, it would make sense to use an ubuntu desktop .... I'd avoid unity since it doesn't force terminal use enough for a person needing to learn to be a sys admin. All the GUI tweaks really need to be manually managed by text/config files, so you get used to doing that. No point-n-click.   Oh - and limit your use of MS-Windows or OSX to less than 1 hr a day. Those OSes have a different underlying philosophy that harms "thinking the Unix way" - which is what you need now.

Also, if you need basic Linux knowledge before learning administrative skills, there are free courses online that will help - from linux.org, MIT, UT, Standford and Harvard.  Don't forget to hang out with Linux people at a nearby LUG.  You'll find like-minded people there who want to help by answering questions that forums and books don't cover well.

Don't forget to learn to RTFM too. Hope I don't get banned for suggesting that.  Directed learning is better in the early months than google-learning. After you have the basic Linux-user skills, get a few admin books and work through them, in order, to get the needed background from 2 different perspectives.  

Of course, these are just my recommendations and there are 500M different ways to get the knowledge you seek.

BTW, you didn't mention which web server or applications you planned to use.  There are many of each. Each with a different skillset required to install, configure and secure.  Don't get me started about Linux security - that is a specialized field completely different from being a system admin.  The **Ubuntu Basic Security Guide** is a good start, but every different web server and web app and DBMS will have slightly different security needs and techniques.

And don't forget that this stuff is fun! ;)

---

### Post by mastablasta on 2015-02-19
> **ram19 said:**
> 
Is there a recommended setup Ubuntu has specifically for such use? Can this actually be done or is the software environment just for internal servers and desktops and storage?


it can sure be done. I mean if Google & Facebook can do it...

however you will:
- need to administer server by yourself
- take care of backups and backup system by yourself
- secure the website by yourself (and if you plan to do business over that website you need to secure it really well)

---

