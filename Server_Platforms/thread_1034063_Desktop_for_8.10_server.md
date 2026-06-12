---
title: "Desktop for 8.10 server??"
date: 2009-01-07
forum: Server Platforms
---

### Post by lightningrod66 on 2009-01-07
I just installed Ubuntu Server 8.10.  I thought it was supposed to use Gnome for the desktop, but apparently not.  When it boots up, I get to the login prompt, then I login and get just a command prompt.  How do I get to the desktop??  Is there no GUI for this version?  I wanted to run a LAMP server, but I don't know how to use it from a command line only :(  What should I do?  I want to use this as a web server, but I need my GUI :(

---

### Post by ibutho on 2009-01-07
Most server distributions do not install a GUI by default. If you want one, then you have to install it yourself. The server edition uses the same repos as the desktop edition, so you can just use apt-get to install the GUI of your choice.

---

### Post by blackened on 2009-01-07
```
sudo apt-get install ubuntu-desktop
```

I can't remember if this metapackage installs gdm as well, but if it doesn't send you to the graphical login, then you can use apt-get to install gdm or simply type startx after logging in at the cli.

That said, you would be amazed at how much you can learn by using only the command line to interact with the machine. 

Instead of installing a gui, might I suggest something like webmin instead? 

Forcing yourself to learn new things is never bad. Ever.

---

### Post by lightningrod66 on 2009-01-07
I tried the apt-get thing, but apparently my internet connection isn't setup correctly.  I don't know how to do anything from the command line only.  Also, I tried typing startx from the cli and got:
"The program startx is currently not installed.  You can install it by typing: sudo apt-get install xinit" :(

I have only had experience with Mandrake, SuSE, and Red Hat.  They were all desktop OS.  I have been running a WAMP server on Windows XP Pro, but decided to try a LAMP server using Ubuntu.

I didn't realize that there was no GUI.  I may try learning all about the command line in the future, but for now, I just need something that i can get everything up and running.

---

### Post by lightningrod66 on 2009-01-07
OK my next question is:  can I install the Desktop version and run LAMP server with it AND have GUI?  What would be the difference between Desktop version with server programs and server version (besides the GUI thing)?  I am always willing to try something new, and learning to run server from command line sounds intriguing, but right now i don't have the time to mess around fumbling through this from scratch.  I need to get my web server back up ASAP.

---

### Post by Titan8990 on 2009-01-07
Here is the place to start learning: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


You can install phpmyadmin very quickly once you have the server going. Apache and php don't even have GUIs in the first place...

---

### Post by lightningrod66 on 2009-01-07
what is webmin and how could I use it?

---

### Post by joshmuffin on 2009-01-07
It's using a web browser to control your server

---

### Post by Titan8990 on 2009-01-07
phpmyadmin is similar to webmin but phpmyadmin functions as a GUI for your mysql server.

---

### Post by joshmuffin on 2009-01-07
Also if you want to install ubuntu-desktop just plug in a Ethernet cable a.k.a blue cable (if your using a wireless router) or if not strait from the modem.[IMG]http://www.unconventionalbelts.com/files/standardcable.jpg[/IMG]

---

### Post by windependence on 2009-01-07
> **lightningrod66 said:**
> OK my next question is:  can I install the Desktop version and run LAMP server with it AND have GUI?  What would be the difference between Desktop version with server programs and server version (besides the GUI thing)?  I am always willing to try something new, and learning to run server from command line sounds intriguing, but right now i don't have the time to mess around fumbling through this from scratch.  I need to get my web server back up ASAP.

Let's be honest here. You don't intend on learning the CLI at all. It's hard. It takes too much time. I know, I said it all years ago just like you. Then one day I stopped being bullheaded and stupid and decided I was going to run a box with NO GUI tools at all. I forced myself to do it. It was painful, but at a certain point I started to "just get it" and now all my production boxes are headless and you know what? Some day your server is going to break. Your precious GUI is gonna fail. You're site will be down and you will have no alternative than to reload because you didn't back it up either. I'm sorry if I sound harsh but it's a shame to me how the Linux community has let this happen. You say you don't know anything about the CLI. Why are you even toying with the server version then? Like I said, I KNOW what you are thinking. I have been there and I fought it for years. Give up. Learn the CLI. Don't load the GUI. You'll be glad you did.

-Tim

---

### Post by lightningrod66 on 2009-01-08
Sorry for all these newbie questions.  I have been using Linux since about 1999 (Registered user #169136), but only Desktop variations,including several versions of Mandrake, SuSE, and Red Hat since version 5.  I have never gotten into completely running the thing from the command line.  I never used them for a web server.  I just started running a web server two years ago and was using Win XP Pro and IIS.  Recently, I have learned more things and switched to Win XP Pro and Apache-MySQL-PHP.  I wanted to see how well a LAMP server would work compared to WAMP server.  I am just used to the desktop and being able to visually move files, edit web pages, and used phpMyadmin for the database dealings.  I remember back when I used DOS and BASIC, but it has been too long...:(

---

### Post by blackened on 2009-01-08
> **lightningrod66 said:**
> OK my next question is:  can I install the Desktop version and run LAMP server with it AND have GUI?  What would be the difference between Desktop version with server programs and server version (besides the GUI thing)?  I am always willing to try something new, and learning to run server from command line sounds intriguing, but right now i don't have the time to mess around fumbling through this from scratch.  I need to get my web server back up ASAP.

Technically yes you can do this. Is it a good idea? Depends on the server load.

The server version uses different kernel options than the desktop version. If this server is only for personal use (low traffic) then using the desktop version will probably be ok, but if it is a higher traffic environment, then you should use the server version as it uses a better I/O scheduling method for decreased read time and lacks kernel task preemption allowing tasks to run to full completion without interruption.

Another benefit of the server install is that you can get most, if not all, of the necessary components for LAMP out of the box. From there all you would need to do is install your preferred GUI with apt-get.

Your networking problem is answered in many other threads on this forum. A quick search should yield some useful help.

**EDIT:**> **windependence said:**
> Let's be honest here. You don't intend on learning the CLI at all. It's hard. It takes too much time. I know, I said it all years ago just like you. Then one day I stopped being bullheaded and stupid and decided I was going to run a box with NO GUI tools at all. I forced myself to do it. It was painful, but at a certain point I started to "just get it" and now all my production boxes are headless and you know what? Some day your server is going to break. Your precious GUI is gonna fail. You're site will be down and you will have no alternative than to reload because you didn't back it up either. I'm sorry if I sound harsh but it's a shame to me how the Linux community has let this happen. You say you don't know anything about the CLI. Why are you even toying with the server version then? Like I said, I KNOW what you are thinking. I have been there and I fought it for years. Give up. Learn the CLI. Don't load the GUI. You'll be glad you did.

-Tim

A little harsh yeah, but good advice. Testament being the two headless boxes humming away next to my desk. It's definitely worth the effort to learn.

---

### Post by lightningrod66 on 2009-01-08
> **windependence said:**
> Let's be honest here. You don't intend on learning the CLI at all. It's hard. It takes too much time. I know, I said it all years ago just like you. Then one day I stopped being bullheaded and stupid and decided I was going to run a box with NO GUI tools at all. I forced myself to do it. It was painful, but at a certain point I started to "just get it" and now all my production boxes are headless and you know what? Some day your server is going to break. Your precious GUI is gonna fail. You're site will be down and you will have no alternative than to reload because you didn't back it up either. I'm sorry if I sound harsh but it's a shame to me how the Linux community has let this happen. You say you don't know anything about the CLI. Why are you even toying with the server version then? Like I said, I KNOW what you are thinking. I have been there and I fought it for years. Give up. Learn the CLI. Don't load the GUI. You'll be glad you did.

-Tim

It's not that I don't know ANYTHING about the command line, I have just never used it COMPLETELY.  I have ran things from command line like installing software tarballs, configuring my cd burner, moving/copying files and directories, etc.  How can you edit web pages from the command line?  I know how to use phpMyAdmin for databases, and I know apache doesn't have a gui.  I have just never been exposed to doing EVERYTHING from the command line (except for way back with BASIC and DOS).  I appreciate all the help, I just want you to understand what I am saying as I think I wasn't very clear.

---

### Post by blackened on 2009-01-08
> **lightningrod66 said:**
> It's not that I don't know ANYTHING about the command line, I have just never used it COMPLETELY.  I have ran things from command line like installing software tarballs, configuring my cd burner, moving/copying files and directories, etc.  How can you edit web pages from the command line?  I know how to use phpMyAdmin for databases, and I know apache doesn't have a gui.  I have just never been exposed to doing EVERYTHING from the command line (except for way back with BASIC and DOS).  I appreciate all the help, I just want you to understand what I am saying as I think I wasn't very clear.

There are many commandline text editors and they vary in power and usability (at least for new users). A short but incomplete list is here ->[http://en.wikipedia.org/wiki/List_of_text_editors#Text_user_interface]("http://en.wikipedia.org/wiki/List_of_text_editors#Text_user_interface").

---

### Post by windependence on 2009-01-08
> **lightningrod66 said:**
> It's not that I don't know ANYTHING about the command line, I have just never used it COMPLETELY.  I have ran things from command line like installing software tarballs, configuring my cd burner, moving/copying files and directories, etc.  How can you edit web pages from the command line?  I know how to use phpMyAdmin for databases, and I know apache doesn't have a gui.  I have just never been exposed to doing EVERYTHING from the command line (except for way back with BASIC and DOS).  I appreciate all the help, I just want you to understand what I am saying as I think I wasn't very clear.

Well, if I have to edit html or php at the command line I use nano. I actually do tweak my CSS stuff without the use of a WYSIWYG editor - I use notepad in Windows with a WinSCP connection if I am on a Windoze box, but my laptop is a Mac, so I can use the terminal or a simple text editor. There are also lots of editors with syntax highlighting that is nice for html or php. If you want a decent WYSIWYG tool I would suggest Nvu. It's free and pretty much full featured. Also cross platform, Windows, Mac, Linux.

-Tim

---

### Post by adlabens on 2009-01-08
Please excuse me if I'm seeming presumptious or preachy, or providing a solution that is not within the real of vision available.  However, I'm seeing a few things here that don't fit.

There seems to be a number of things going on here.  The most "contradictory" (maybe a bad choice of terms, but at this late hour, that's what comes to mind) is that it appears LighteningRid66 seems to want to do web page design (a desktop function) from a web server box.  If that's the case, then he definitely needs a GUI.  It also appears, per his statement about his current predicament, that he's under a lot of pressure to just get his web server back up & running.

Therefore, let me take those assumptions (correct me if they are wrong), and provide a course of action that might best suit his needs.

First, get the web server up & running in the quickest fashion possible.  For my money, that would mean getting it back to working exactly like it was working before it crashed.  If he was running it on a WinXP box, then his most painless solution will be to simply do it again.  There's no shame in going that route, especially when it's what he "knows."  While it's true that the only way to "walk on fire" is when the coals are blazing, it's not never a good idea to be learning how to walk when running is needed.  One can do neither a good nor effective job of either learning a new system or implementing a new system when the pressure is on to "perform."  If the pressure were to "learn," that would be a different story.  BUT, this is clearly a performance exercise and not an educational exercise.  Therefore, I would strongly suggest that the box that failed should be rebuilt exactly as it was built before, from the hardware to the operating system to the installed applications, so that the required performance be achieved as quickly as possible.

I know that was a mouthfull to say "go back down the path from which you came," but I'm not really saying that at all.  Let's continue the discussion with "Once you have achieved performance, then it's time to take a more relaxed attitude toward learning a new system and implementing your web services on it.  Once you have your performance at the needed level, its a lot easier to concentrate on the education part when you're not under the gun to "get it all done yesterday."

Once you are beyond the performance issue and working on the education issue, I would plan on doing three complete installations.  Yes, THREE!  The first one will be filled with mistakes, have added features that are not necessary, miss steps, and generally be terribly inefficient.  BUT, it will give you a taste of what you can accomplish.  

On the second attempt (use a different hard drive [they're cheap, about $35 for an 80gb SATA3 drive!], so that you're not destroying the first installation.  This will give you a point of reference, in case you have to disconnect the 2nd installation and reconnect the 1st installation, just to find some of the things that worked the first time but are giving you problems the 2nd time.  And, while you're at it, start a word processing document that will have your compilation of the full and complete instructions on how to build the server you're building.  The second go-around will be a lot cleaner and a lot more efficient, but you'll still make a few mistakes.  However, you'll also finish the 2nd installation with a nearly completed documentation that will serve to provide you with a very strong set of disaster recovery instructions.  

The third go-around will be done using the documentation you created on the 2nd go-around.  You can do it on the 1st disk because you'll have the 2nd disk fully functional and can plug that one in, if needed.  So, go back to the first disk and start from scratch following (and correcting) the instructions you created in the 2nd go-around.  When you get finished, you'll have a professional installation and professional documentation that a monkey could follow, so you'll have no problem making it work again, years from now, when that operating system drive fails.

That said, I've told you nothing more or less than exactly what I'm doing right now.  I'm building a file server for my home.  Granted, it's not doing web serving, but the concepts of development and learning are exactly as I've presented them to you.  

Finally, let me give you the best piece of advice I've ever gotten from a certified network administrator:  "Use the server as a server, not as a work station."  Oh, that and "Do your backups!" (but that's a different thing altogether).  If your server is only that, then you don't have to worry about having a keyboard connected, or a monitor draining energy from the grid.  It can do it's task as it's designed without taxing itself to do things that are "beneath" it.  What I'm saying is that the brain surgeon is a good brain surgeon because he never looks at anything but your brain.  Heck, he doesn't even do diagnosis, only coming in when the diagnosis is completed and it's time for him to cut, clean, cure, and close - and even he doesn't do much of the closing, either.  Let your workstation computer be the workhorse of what YOU are doing, let the server box be the workhorse of THAT task.  You can run the server much more efficiently, with less overhead, using much less RAM, if it's got no GUI.  But, your workstation will do a great job with a GUI and handling all the clicks and refreshes that should never be done on a server.

And, as I'm doing my own, I'm working hard to do everything from the CLI.  I've taken several weeks (I'm slow) to get the first round completed.  The second round has taken me a day (along with 9 hours of work for my employer - away from the computer), and I'm at about 85% of where I was when I finished the first go-around.  When I do the 3rd round, I expect it will take just a few hours one afternoon.  And, when I'm done, I'll have a document that will allow me to do it again, 5, 7, even 10 years from now, long after I've forgotten how to do any of it.  I'll be able to pick up the document and follow my own step-by-step instructions for disaster recovery that will have me back up & running with just a few hours work.  

Of course, by then, technology AND open-source will be so much more advanced, I may be able to hold up a hard drive and snap my fingers and have the server fully functional.  No, I don't really think so.  But, at least I'll have all my ducks lined in a row.  And, yes, I remember DOS - from the days when there weren't yet any HDDs, and the first one was 5MB, cost $500.00, and was this big (3"x4"x18" box that sat next to the IBM-PC (becasue there wasn't yet an IBM PC-XT).  

This CLI is different and the same, all at the same time.  And, I love the education I'm giving myself.  But, if I were under pressure to just get it back working, this would be a nightmare.  I hope you're doing better than that.

By the way, my file server is an AMD Athlon 64 6400 3.2ghz with 4gb RAM, an 80gb OS HDD and 4 250 gb RAID5'd HDDs with gigabit ethernet, and the whole thing cost about $460 (using a used monitor & keyboard & DVD ROM drive).  The price of technology has come WAY down from those $100/MB hard drives!

Good luck,
David
San Antonio, TX

---

### Post by windependence on 2009-01-08
> **adlabens said:**
> 
Finally, let me give you the best piece of advice I've ever gotten from a certified network administrator:  **"Use the server as a server, not as a work station."**  Oh, that and "Do your backups!" (but that's a different thing altogether).  If your server is only that, then you don't have to worry about having a keyboard connected, or a monitor draining energy from the grid.  It can do it's task as it's designed without taxing itself to do things that are "beneath" it.  What I'm saying is that the brain surgeon is a good brain surgeon because he never looks at anything but your brain.  Heck, he doesn't even do diagnosis, only coming in when the diagnosis is completed and it's time for him to cut, clean, cure, and close - and even he doesn't do much of the closing, either.  Let your workstation computer be the workhorse of what YOU are doing, let the server box be the workhorse of THAT task.  You can run the server much more efficiently, with less overhead, using much less RAM, if it's got no GUI.  But, your workstation will do a great job with a GUI and handling all the clicks and refreshes that should never be done on a server.


Good luck,
David
San Antonio, TX

This advice is golden. Clearly, the Ubuntu server product is targeted at commercial rather than home use. I am not saying you shouldn't use it that way, just that in probably 90% of the cases I see here on the server forum, people should be using a desktop product. Do your development on your desktop and when it's tested on the staging server and ready, upload it to the server and run it. Don't have a staging server or think you can't afford it? Virtualize. It's easy.

-Tim

---

### Post by lightningrod66 on 2009-01-08
I want to thank everyone for their advice and information.  When I decided to try the Ubuntu server, I didn't realize exactly what I would be getting.  I will continue with the Ubuntu server (I have a spare computer that I will use) and get my web server back into operation with the WAMP for now.  I will also be getting a feel for the ubuntu server at the same time. There is just one thing that I need to know about the ubuntu server (**using only CLI**) so I can be on my way and put this issue to rest:

Getting my server into my existing network so that I can get files onto it from another computer (where i will be doing all the editing and so forth).  You can point me to a tutorial, or a document, or whatever.  At this point, the server is NOT connected to my network and I am not sure how to get it that way.  Once it is in the network, I will be able to see it from another computer and access/transfer files.

I guess I wasn't thinking about it before but I really DON'T need the server to have a GUI, because with the web server I am currently using I don't actually do anything ON it once I get the server/database programs installed and configured.  I handle the databases using phpMyAdmin.  I write all the php/html/css etc with another software program on another computer.

I guess I was just EXPECTING a GUI, and when there wasn't one, I sort of *ahem* freaked!

The entire LAMP is installed because I can tell that when it boots.  I just have no network access yet.

Thanks for all of your help...EVERYONE

---

### Post by windependence on 2009-01-08
When you do the install, Ubuntu should config the network for you. If not, we can help you edit the files you need to to assign it an IP address. Then, once you get everything installed, you can go to your Windoze box, install WinSCP, log on and drag your files into the web root directory. Easy as pie and very secure as WinSCP uses ssh and SCP and it's free. That's how I do mine except I do it from my Mac using Fugu.

Just yell if you need help, some of us are always here. ;)

-Tim

---

### Post by lightningrod66 on 2009-01-09
> **windependence said:**
> When you do the install, Ubuntu should config the network for you. If not, we can help you edit the files you need to to assign it an IP address. Then, once you get everything installed, you can go to your Windoze box, install WinSCP, log on and drag your files into the web root directory. Easy as pie and very secure as WinSCP uses ssh and SCP and it's free. That's how I do mine except I do it from my Mac using Fugu.

Just yell if you need help, some of us are always here. ;)

-Tim

Yes, Ubuntu did configure the network - but after I supplied answers to the questions, such as which NIC, IP address, subnet mask, gateway, name server, domain, etc.  I know the answers to these questions, but I was stuck with the domain question.  I assumed (based on the hint it gives you) that it wanted my WEBSITE domain (it said "usually ends in com, net, org, etc").  My network is not on a domain - it is a workgroup. Should I have entered the Workgroup name instead (no com, net, org)? 

That may be the problem, but I have to figure out how to go about checking and reconfiguring the network parameters from CLI.

Anyway, this server will just be ON the network - not controlling the network, so I don't need the DHCP or anything like that.  I use a router and assign static IP addresses to each computer.  And this will just be a WEB server, but I need to be able to access it from a Windows computer to get files to it.  WinSCP sounds familiar, but I don't think I have ever done anything with it before.  As I stated earlier:  I have a lot of experience with Linux OS, just not from a server standpoint.

I would appreciate your help with reconfiguring my network info :)  Thanks.

---

