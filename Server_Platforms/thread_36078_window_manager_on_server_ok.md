---
title: "window manager on server ok?"
date: 2005-05-21
forum: Server Platforms
---

### Post by mccan on 2005-05-21
We are thinking of using a linux solution (possibly Ubuntu and Hula) to replace our exisiting email server.  During the discussion someone said that we should not have Gnome, KDE or other window manager on the server, that it was not only unnecessary but a security risk (more possible vulnerabilities).  

Is having Gnome installed a security risk?  Is there any value in having it installed on a server?  I am not sure if the statement reflects best practices or just the person's preferences and so would appreciate hearing what others think.

Thank you,

David

---

### Post by stilus on 2005-05-21
I'm no professional, so don't take my advise to seriously, but I would say running a desktop would not be a security problem perse... Though I think you would have to seriously investigate things like the remote access rights to gdm, ssh X forwarding etc. And then there is the simple "more packages = more possible bugs" equation. 

I personally prefer keeping to the command line and ssh (Protocol 2, ofcourse). 
If you do decide, after serious googling and manpaging (not to mention roaming forums like this one :) ) you want to have a desktop, you might want to look into something a little lighter than the default desktop (gnome) or KDE. Openbox, fluxbox, xfce, or some other light window manager, manually installed (no meta packages) so you have the minimum of packages, would work better, I think. Desktops can be as slim as you want them to be. 

Also, webmin might be a good alternative to a desktop. I must agree with [this thread](http://www.ubuntuforums.org/showthread.php?t=31071) though, that sticking to ssh (apt-get install ssh, cd /etc/ssh/ and reading the relevant manpages to the files there) gives a better understanding of what linux is about. It took me quite a while (and I learned some new nasty words along the way), but I can't imagine server administration without it. Good luck with your setup, and create yourself a testsytem first (after all, no per-user payment for the OS/applications ;) )

---

### Post by Beernut on 2005-05-21
I'm still on the fence about the desktop no desktop debate.  I guess it does add alot of packages that you really are not going to need or use if it is strictly going to be an email server.

I just installed a Hula server for email without a desktop and can tell you there was and is absolutley no reason for a desktop on this server.  All of your administration is done through a web interface with Webadmin.  So far I am very satisfied with Hula I can't wait for it to mature a bit more.  Use SSH to connect to the server and use apt-get to do updates and that's all you need to do.

---

### Post by mccan on 2005-05-22
Thanks for the feedback.  It sounds like running a windows manager is optional at best.

David

---

### Post by Stormy Eyes on 2005-05-22
[QUOTE=mccan]Is having Gnome installed a security risk?  Is there any value in having it installed on a server?  I am not sure if the statement reflects best practices or just the person's preferences and so would appreciate hearing what others think.[/QUOTE]

When configuring a server, it's generally good practice to refrain from installing things that aren't abolutely necessary. If it's easier to admin your server using X over SSH, then by all means install X, and either a window manager or a desktop environment (window managers are lighter, and don't come with the frills that desktop managers include). If you really want to be paranoid, or are concerned with performance, don't install X, but do everything from a commandline via SSH. It's up to you.

---

### Post by LordHunter317 on 2005-05-22
Seeing as every commerical UNIX include X and some sort of desktop environment, it's harmless to install it if you need it. X is pretty standard.

However, all of my servers run headless, and the only way to admin them is X forwarding or SSH, so it's good practice.

---

### Post by Burgundavia on 2005-05-22
Basically, what is boils down to is risk. EACH and every package you install adds risk. Thus, if you limit the number of packages you install, you reduce risk.

Corey

---

### Post by Jarl Nicolson on 2005-05-24
All of my servers run without a desktop environment running on the local terminal, but  some allow remote X sessions.  I find it easier to admin some stuff when I can have a bunch of terminals or config files open at once.  Opening multiple ssh sessions is annoying.

That said, I would never run Gnome or KDE, even like this.  XFCE or Blackbox is my choice.

---

### Post by mendicant on 2005-05-24
[QUOTE=Jarl Nicolson]I find it easier to admin some stuff when I can have a bunch of terminals or config files open at once.  Opening multiple ssh sessions is annoying.
[/QUOTE]

I like screen for doing this, in general.  The only problem is when you need to see one terminal while typing in another one.

---

### Post by LordHunter317 on 2005-05-24
You can make screen split... so you can see more than one terminal at once.

---

### Post by dataw0lf on 2005-05-24
apt-get install screen 
Great utility.

As for the 'debate' on a window manager on a server... why??  Unless it's a personal server (and even then I don't advocate it), they use up too many resources, add unneeded security issues, and don't add anything useful.  An email server, especially if you're planning on running ClamAV and SpamAssassin, or equivalents, will munch up the resources happily.  No need to add a windows manager.  Try explaining to your boss why you need a new server when you have Gnome / X running on your original one. 

If 'user friendliness' is an issue, then, and I don't mean to be rude, perhaps you shouldn't be running the server in the first place.  System administration can be quite hairy at sometimes, and you do _NEED_ the full control of the CLI at all times, without the added complexity and vagueness of trying to manage your services through a GUI.

---

### Post by mendicant on 2005-05-24
[QUOTE=LordHunter317]You can make screen split... so you can see more than one terminal at once.[/QUOTE]

Oh that's right--I usually have my terminals at 80x24 or so, and never think about splitting a screen--not enough data at once.

---

### Post by mendicant on 2005-05-24
Also note that you don't need to have X actually running on the server, but just have all the libraries and clients so you can use X remotely, once on the server.  Even then, you don't need the window manager unless you were planning on running a VNC session, for instance.

---

### Post by jannol on 2005-05-27
I use debian as my private server, ftp and web, serving about 10 users total. Since I had no speed issues due to the low trafic so I decided to have it as an extra surf computer for friends so I installed enlightenment with a browser. all shutdown and reboot options are forbidden, even for root, If X crashes it falls down to init 2 where all my services already started. Well there it still run all my necessary services and stays att terminal login for root only since I set user default level to init 3. The one user account is pretty much locked out from doing anything but surf the net.

I agree, I think it is always best to NOT use any extra at all that increase cpu loads but depending of knowledge, experience with servers and so on there might be an easier and perhaps more suitable configuration for you. Also I guess it is more actual work to set up a somewhat secure and workin server with X.

Next time when I build my new server I will not use anything extra nor X at all. I once read an article where they stated that the fastest and most reliable servers in the world had about 200 MB of installed software... well that was a few years ago but I don't think the server software need to be any bigger (of course, log files and backups not included).

And as mentioned before, all setup and config should be done in terminal, however, there is a bunch of really good gui tools but total control comes from terminal. You need to know how important the server is to be and how to preserve sensitive data if it crashes since the risk is of that increases for every extra stuff, also, every extra stuff need to be configured to not disturb or fall into any starnge behavior like respawn, loop or something else.

My point of view, yes you could install some windowmanager or just the X to be able to control via vnc, simply put it down to ex. init 2 when X is not needed, an email server might not be as disturbing to reboot as an ftp or web, I guess the users rather wait a few minutes for email server to start than web server.

btw, one day you will not wanna use X or wm with servers... I hope ;-)

---

### Post by LordHunter317 on 2005-05-27
[QUOTE=jannol]r. all shutdown and reboot options are forbidden, even for root,[/quote]So what are you going to do when you need to reboot the box?  Magic Sysreq Key?  Does Ubuntu even disable that? 

> Also I guess it is more actual work to set up a somewhat secure and workin server with X.Not really, believe it or not.  You have to careful so people can't abuse devices that the console user needs to be able to access, but Ubuntu does a good job of that.

> once read an article where they stated that the fastest and most reliable servers in the world had about 200 MB of installed software...That article was wrong.  Oracle for example is well over 200MB even if you strip out all the extra crap.  

Oracle's also bloatware, to be fair.  But I don't think I could setup a reasonable J2EE app-server in 200MB, for example.

>  well that was a few years ago but I don't think the server software need to be any bigger (of course, log files and backups not included).Yeah, it frequently does.

> And as mentioned before, all setup and config should be done in terminal, Tell that to Oracle.

>  You need to know how important the server is to be and how to preserve sensitive data if it crashes since the risk is of that increases for every extra stuff, Simply not true.

---

### Post by jannol on 2005-05-27
[QUOTE=LordHunter317]So what are you going to do when you need to reboot the box?  Magic Sysreq Key?  Does Ubuntu even disable that? [/QUOTE]
I guess you could disable all those in all *nix flavours, it just might be more difficault with some. However, my point was to minimize the risk of an accidental shutdown.

[QUOTE=jannol]Also I guess it is more actual work to set up a somewhat secure and workin server with X.[/quote]
[quote=LordHunter317]Not really, believe it or not.  You have to careful so people can't abuse devices that the console user needs to be able to access, but Ubuntu does a good job of that.[/quote]
Keylock ?

[quote=LordHunter317]That article was wrong.  Oracle for example is well over 200MB even if you strip out all the extra crap.[/quote]
I guess there might be a few other flavours of servers than oracle but this could be discussed for a loooooooong time so ok, I wont stand up for someones article.

[quote=LordHunter317]Oracle's also bloatware, to be fair.  But I don't think I could setup a reasonable J2EE app-server in 200MB, for example.[/quote]
I don't know very much about oracle but 'resonable' could be discussed, a stable ftp / web / mail server doesn't need to be very big, also maybe I missed something here but who mentioned J2EE app-server ?

[quote=jannol]well that was a few years ago but I don't think the server software need to be any bigger (of course, log files and backups not included).[/quote]
[quote=LordHunter317]Yeah, it frequently does.[/quote]
It depends much on your needs. By time it most likely will grow but as for today, I belive it is possible to set up a secure 200 mb server with ftp / web / mail.

[quote=jannol]And as mentioned before, all setup and config should be done in terminal,[/quote]
[Quote=LordHunter317]Tell that to Oracle.[/quote]
What response do you expect from that ?
Please tell us what you based your thoughts on.

[quote=jannol]You need to know how important the server is to be and how to preserve sensitive data if it crashes since the risk is of that increases for every extra stuff,[/quote]
[quote=LordHunter317]Simply not true.[/QUOTE]
I should have specified it a bit, as this discussion was about X and wm I ment that your system need to contain more libs, deamons and settings which can be hard to keep track of and therefor might run more daemons that could get stuck, interfere and hang your system or mess with your settings until you go crying a bit, have some coffee and then continue. ;-)

No offense

---

### Post by LordHunter317 on 2005-05-27
[QUOTE=jannol]I guess there might be a few other flavours of servers than oracle but this could be discussed for a loooooooong time so ok, I wont stand up for someones article.[/quote]Right, seeing as the article is crap.

>  also maybe I missed something here but who mentioned J2EE app-server ?Who mentioned just ftp/web/email?  The point is, a server install can take way more than 200MB quite easily.  It's completely task dependent.  Trying to say a good server shouldn't have less than XXX MB installed is roughly as smart as trying to judge code quality based on LOC.

>  I belive it is possible to set up a secure 200 mb server with ftp / web / mail.It'd be somewhat tight for a fully featured web-server.  Even a clean Debian or Ubuntu install is going to carry you past 50% of that goal, and you haven't even installed your actual server software yet.  Most of it's not a lot of code, but it depends on what you want to do.  

> What response do you expect from that ?
Please tell us what you based your thoughts on.Oracle 10g can't be installed without X.  There's currently no possible way on UNIX.  The idea of being able to do everything from the CLI is admirable at times, but simply not a reality in today's environment.  I'd have to install at least enough X to forward in order to install Oracle on any UNIX server.

> I should have specified it a bit, as this discussion was about X and wm I ment that your system need to contain more libs, deamons and settings which can be hard to keep track of and therefor might run more daemons that could get stuck, interfere and hang your system or mess with your settings until you go crying a bit, have some coffee and then continue. ;-)If you can't manage what you have installed, then you shouldn't be running a server.

Addmittedly, part of that is not installing more than you need.  But some servers need X11, end of story.  And one shouldn't be relcutant to install what one needs just because it makes configuration more difficult or because of the phantom belief that "more stuff == worse security, automatically."

---

### Post by usererror on 2005-06-01
I too, am not a professional, but, i have been running my webserver from my home, but it also was my desktop workstation with gnome installed.  i never had a problem, but again, it wasn't a traffic intense server.

---

### Post by mmealman on 2005-06-03
[QUOTE=mccan]We are thinking of using a linux solution (possibly Ubuntu and Hula) to replace our exisiting email server.  During the discussion someone said that we should not have Gnome, KDE or other window manager on the server, that it was not only unnecessary but a security risk (more possible vulnerabilities).  

Is having Gnome installed a security risk?  Is there any value in having it installed on a server?  I am not sure if the statement reflects best practices or just the person's preferences and so would appreciate hearing what others think.
[/QUOTE]

The anti-X server vibe is a holdback from the 90's when Linux boxes had 64 megs of ram and X would consume half of that. With today's systems there's really no reason not to have a GUI desktop on a server, unless you really know you're not going to use it.

---

