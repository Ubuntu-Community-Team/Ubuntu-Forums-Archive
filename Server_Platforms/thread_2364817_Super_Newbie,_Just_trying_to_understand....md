---
title: "Super Newbie, Just trying to understand..."
date: 2017-06-28
forum: Server Platforms
---

### Post by mail4kiko on 2017-06-28
Hi, this is going to sound strange. But at my job we've had some unfortunate IT hires and now I'm just trying to look at what's left and make sense of it. 
What was left from first IT guy - was handed a host name, IP, ssh Login, Password and Root PW for our dedicated server. I am using Mac, so I was able to login with the regular login via Terminal, but not with Root Login so I can't make a new user. With login it said welcome to Ubuntu 14,04. And apparently I need an update and a restart, but that's another issue all together. Currently there is a template site and CMS (in the making) if I go to the host name xxx.xxxserver.com. First IT guy left. New IT guy, was given this information and gave me a new FTP Account, ID, and Password. I am able to use this to login to Filezilla. He left. Now I am left with a template site on xxx.xxxserver.com, and these various logins. What I want to do is to start over and upload wordpress onto the server and start making a new site. Is this possible without the root login working?? Do I need to make a new user? A new IP address? The old site can be completely deleted. I just want to know if what I want to do is possible with what I have, or if I'm wasting my time. Once I get wordpress installed, I can take it from there but starting to doubt if I can get that far... :( 

Any tips or basic knowledge spared would be greatly appreciated. Sorry if it's super basic 101 info... 

Kind regards, 

Kiko

---

### Post by howefield on 2017-06-28
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by TheFu on 2017-06-29
Welcome to the forums.

As you realize, you are in over your head.  Nothing you've asked is really that hard, but jumping into the deep end on day 1 really isn't the best idea for learning to tread water.

Please break up your future posts so they are easier to read. 1 long paragraph is hard to follow.

You don't need root to create new users.  Any useid in the either the sudoer or admin or wheel groups can elevate their permissions temporarily using sudo. This is how Ubuntu is designed to work. Root logins are not used.
**sudo apt update && sudo apt upgrade && sudo reboot** That should get the system patched and restarted, provided nothing fails earlier in the process.

Linux servers require weekly patching and daily attention to log files. That will never change. Admins have tools to help reduce the cruft we need to review, but the daily review of all server logs is still part of my day 25 yrs after I started learning.  

Here's what I do in the first 5 minutes on a new server: 
   [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)
Here's my recommendation for someone who wants to learn Linux:
   [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)
Here's my Linux Server Security thoughts: 
   [http://blog.jdpfu.com/2016/10/04/lamp-server-security](http://blog.jdpfu.com/2016/10/04/lamp-server-security)

Be aware that wordpress is the primary target for internet-based hacking:
   [https://www.wordfence.com/blog/2016/12/russia-malware-ip-hack/](https://www.wordfence.com/blog/2016/12/russia-malware-ip-hack/)  Take appropriate steps to protect your credentials and systems.

BTW, hacking into your own server is usually the 1st question for any Linux admin test.  There are multiple techniques, you should learn 3 or more.

And please [stop using plain FTP]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp"). It is a crackers favorite tool when people use unencrypted connections to servers.

If there were even a 10% chance that the prior admins weren't completely professional, I'd move all the services to a system that I had built and blow away the old box a few months later, after I was certain everything I needed as handled/moved.

---

### Post by Michael_McKenney on 2017-06-29
So you are playing fire fighter.   My suggestion is start a notebook for each server.   Write down everything about it.   Name, IP, subnet, gateway, OS version.   What you can and can't access.   What notes were left for that server will be important?   Maybe see if you boss will let you call the former two IT staff and invite them to lunch to get more information. Before you do anything.  Make sure you are getting clean backups.

---

### Post by mail4kiko on 2017-07-01
Hello! Thank you so much for your replies! 

Yes, it's frustrating because I know that what I am looking to do is probably quite simple, so simple that I'm having trouble finding the info on other threads :-|
The thing is, because what we wanted was so simple (and we are a small company) we just kept hiring 1 man IT guys that said they could do it. Literally all the information I have is what I've posted. We are currently trying to hunt down the last IT guy because after a month and a half of telling us he was working on it, he as pulled a runner...

I also understand, more and more, that though simple, to do everything right (as in all the links you have provided) I am in over my head. But because we are such a small company, and even now have the most IT capabilities in the company (I can make a WP site... ](*,)) . But because of this, and because of past hires, I feel like I need to step up and at least understand enough so that the IT guys don't just take us for fools... 

I have tried the **sudo apt update && sudo apt upgrade && sudo reboot **but it asks for the Sudo Password. 
I tried adding sudo with this command [COLOR=#111111][FONT=Consolas]sudo usermod -a -G sudo *myusername*[/FONT][/COLOR] but it also asks for the Sudo password... 

At the moment, since we are starting over, I don't mind wiping the server clean. All I want to do is set it up to make a new site with WP. (For my skill level, WP is really the only option at the moment). 

Thank you again for all your input. I feel like I still just need to wrap my head around the basic basics... 

Kind regards, 

Kiko

---

### Post by mail4kiko on 2017-07-01
Hello again, 

I've actually tried to add a new user with adduser but am told that only root may add user to the system. Is there a way around this?

Kind regards, 

Yukiko

---

### Post by TheFu on 2017-07-01
There isn't any "sudo password" - it is the password for anyone in any of these groups (usually).
* wheel
* sudo
* admin

'id' - that is a command - will show you what groups **your** userid is in.  If it isn't one of those, forgetaboutit.  You'll have to gain many, many, more skills before you should be allowed to sudo. IMHO.  I know that sounds harsh, but sudo is extremely powerful.  It is very common for people new to Linux to wipe the entire OS by misuse of sudo.

There are thousands of little details like sudo that an beginning admin should already know. Find a Linux Power User book in your native language and get started on pg1.  Do 20 pgs a day (that's probably 2 hrs) and in 2 weeks, you should be ready to begin doing admin stuff.  My "Learning Linux" link above has links, **in order**, for accomplishing this.  Random google answers aren't your friend at this point.  Organized learning that takes 2 weeks to begin will make you mostly safe to use sudo (well, nothing is absolutely safe).

If you don't like book learning and prefer exercise-based learning, EdX has free online courses in Linux.  Oh ... and forget the GUI or some webapp to manage your systems. That is a redherring. Best to do it the way admins have been doing it for 40 yrs - at least for the 1st 2 yrs.  After that point, you should have enough knowledge to properly secure the web-apps used about 5% of the time to admin Linux services.

Lastly, learn to read manpages on the system. Those will be the best information for what is actually running ON the system.  Sure, google will find a manpage for the command, but it won't be the same version as on your machine.  95% of the time, it is close enough, but once you've been burned by a slight difference, you'll always use the local manpage going forward.

---

### Post by TheFu on 2017-07-01
> **mail4kiko said:**
> I've actually tried to add a new user with adduser but am told that only root may add user to the system. Is there a way around this?
 

Yes. Hack into the system, add your account to the 'sudo' group.  Use sudo to add a new userid, but why bother adding a new userid? Really, you just want to add your userid to the sudo group.  Have you searched for how to do that?  I have - found 3 reputable websites with answers. My search "locked out add userid  sudo group ubuntu"

Adding a new userid is an administration function for every OS that I know. Modifying group membership is also an admin function.  Do you understand why that is?

---

### Post by mail4kiko on 2017-07-03
Thank you for your reply. Though not the answer I wanted, probably the best. In every question I ask Google I find myself with several more questions. 

Googled manpage and already confused again... 

I found that the only group my user was in was a group of the same name as the user... ](*,)

Thank you for your help anyway, will look into some other options. 

Kiko

---

### Post by mail4kiko on 2017-07-03
Hello, thank you for your reply. 

Yes I have googled it many times but it keep telling me to reboot and gives me what seems to be Ubuntu desktop options. I am trying to access this server using Terminal on my mac laptop, and can't seem to grasp what needs to be done :(

I would assume the admin function controls this for security measures. I'm wondering if I can do anything with this server without having those admin or sudo privileges on my user. But perhaps my line of questioning itself is incorrect...

---

### Post by ian-weisser on 2017-07-03
> **mail4kiko said:**
> I found that the only group my user was in was a group of the same name as the user...

Since your account lacks admin privileges, there's not much you can do...
...until you boot the server from a LiveUSB and add yourself to the admin group.

Since you are open to wiping the system clean and starting over, that may be a good way to undo whatever the previous admins have done.

Personally, I do not recommend self-hosted WordPress sites. I feel they have too many exploitable vulnerabilities, and simpler/safer options are readily available.

---

### Post by TheFu on 2017-07-04
> **mail4kiko said:**
> Thank you for your reply. Though not the answer I wanted, probably the best. In every question I ask Google I find myself with several more questions. 

That is normal. Being smart (as you are), it is easy to think that you (or I) can learn just enough to solve 1 problem.  I thought the same thing when I started with Unix.  It is 20+ yrs later and I can promise you that is the hard way.  My best advice is to start with my "Learning Linux" link provided above.  In about 4 hrs, you'll have a good basis to get started learning more details.

> **mail4kiko said:**
> Googled manpage and already confused again... 
man pages are the help system on Unix.  Type "man man" into a terminal to get an overview of how manpages work. They work the same on any Unix-like OS - OSX, Linux, AIX, HP-UX, Solaris, or the 20 others.  You can search manpages using the 'apropos' command.  To learn more about it, use "man apropos" - make sense?  "man chmod" does what?

> **mail4kiko said:**
> I found that the only group my user was in was a group of the same name as the user... ](*,)  Not good. That means your userid doesn't have any privileges.  There is no method, without literally hacking in, that you will gain access to the system to get higher privileges until you are physically on the machine. Once you are physically at the machine, there are many how-to guides for booting into single-user mode. From there, you have complete control over the system, but as someone really, really, new, I'm afraid you won't know what to do. 

> **mail4kiko said:**
> Thank you for your help anyway, will look into some other options. 

Kiko

There aren't really any other options - except starting over from scratch or paying someone to handle this stuff for you. That will also require physical access to the system.  There is no way to do anything from a remote Mac.

---

### Post by CatKiller on 2017-07-04
Just a quick chime in: man is short for manual. The manpages are pages from the manual.

---

