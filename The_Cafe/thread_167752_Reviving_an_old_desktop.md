---
title: "Reviving an old desktop"
date: 2006-04-29
forum: The Cafe
---

### Post by anil_robo on 2006-04-29
I have an old desktop (more than 9 years old) and want to host websites on it using Ubuntu. But it's too slow for Ubuntu. So I'm using windows 98 with apache to do this. Here is the website:
[http://stooge.myftp.org](http://stooge.myftp.org)

Is it possible to run Ubuntu on that desktop somehow?

System specs are:
[INDENT]Make: Acer Aspire (1997)
Intel Pentium 166 MHz
72MB SIMM RAM
1GB Fujitsu Hard Drive
8x CDROM drive
Floppy Drive
Sound Card - Soundblaster 16 compatible
Ethernet Card - D-Link DFE 530TX+ (added)
Startech 2-port PCI USB card (added)
[/INDENT]
I'm asking this because I am familiar with Ubuntu and would like to keep the same on this old desktop.

Please advise.

---

### Post by ubuntu_demon on 2006-04-29
try a Dapper server install cd . Don't install a gui. Do everything in the terminal. Then it will probably be fast enough (unless it's a heavy website).

---

### Post by 3rdalbum on 2006-04-29
You could also try Damn Small Linux. It would give you a DE, run quite quickly, and it comes with Apache.

---

### Post by ubuntu_demon on 2006-04-29
[QUOTE=3rdalbum]You could also try Damn Small Linux. It would give you a DE, run quite quickly, and it comes with Apache.[/QUOTE]
it's not necessary to run a gui on a server at all. IMHO it's not a good idea to run a gui on this hardware if intended as a server because it would use most of the resources available.

---

### Post by anil_robo on 2006-04-29
[quote=ubuntu_demon]it's not necessary to run a gui on a server at all. IMHO it's not a good idea to run a gui on this hardware if intended as a server because it would use most of the resources available.[/quote]
But I'm not confident if I can work comfortably with command-line. I would still prefer a distro with GUI :(

Basic idea is: I'm getting the job done with windows98 for the time being. But I would like to replace windows98 with any linux distro as soon as possible.

I'll try to make the ethernet card work on puppy or Damn Small tonight, and let know if it works. ](*,)

---

### Post by Tedd on 2006-04-29
You could try Kubuntu, I've heard there's a version that's extremely small for computers that are older.

---

### Post by ubuntu_demon on 2006-04-29
[QUOTE=anil_robo]But I'm not confident if I can work comfortably with command-line. I would still prefer a distro with GUI :(

Basic idea is: I'm getting the job done with windows98 for the time being. But I would like to replace windows98 with any linux distro as soon as possible.

I'll try to make the ethernet card work on puppy or Damn Small tonight, and let know if it works. ](*,)[/QUOTE]
you can install icewm / fluxbox or something like that on Ubuntu too. You don't need Damn Small Linux for that. It's just that a gui on a slow machine like that would use almost all resources.

---

### Post by briancurtin on 2006-04-29
[QUOTE=anil_robo]But I'm not confident if I can work comfortably with command-line.[/QUOTE]
now is the time to learn.

---

### Post by htinn on 2006-04-29
I recently installed Xubuntu on a portable that had similar specs. It spent a lot of time in hard-drive thrashing (especially for programs like Firefox). XFCE is about 5 times faster than GNOME on that system.

---

### Post by nalmeth on 2006-04-29
[http://www.ubuntulite.org/dokuwiki/doku.php](http://www.ubuntulite.org/dokuwiki/doku.php)

or you can just install xubuntu, unless that is also too slow

---

### Post by Kernel Sanders on 2006-04-29
[QUOTE=nalmeth][http://www.ubuntulite.org/dokuwiki/doku.php](http://www.ubuntulite.org/dokuwiki/doku.php)

or you can just install xubuntu, unless that is also too slow[/QUOTE]

Tbh, i'd say stick with Windows 98 if its "doing the job" (As it appears to be)

My question though, is how'd you get your ISP to consider hosting your own website "fair use"??? :-k 

John :)

---

### Post by Compucore on 2006-04-29
Memory wise sound enough for even hoary hedghog 5.04 that you can install on that. Is the memory for that machine 72 pin or 168 pin variety. I know my old Pentium 120 had both version. So I could use either 72 or 168 pin for it. And it was a old Gigabyte motherboard. My old Aptiva that I have here is slightly faster. It is running a AMD K6-2 400 with about 192 megs of ram and a 20 hard drive. Try using ubuntu 5.4 if you have a version of it and install the server side like some of the others had mentioned. 

Compucore


[QUOTE=anil_robo]I have an old desktop (more than 9 years old) and want to host websites on it using Ubuntu. But it's too slow for Ubuntu. So I'm using windows 98 with apache to do this. Here is the website:
[http://stooge.myftp.org](http://stooge.myftp.org)

Is it possible to run Ubuntu on that desktop somehow?

System specs are:
[INDENT]Make: Acer Aspire (1997)
Intel Pentium 166 MHz
72MB SIMM RAM
1GB Fujitsu Hard Drive
8x CDROM drive
Floppy Drive
Sound Card - Soundblaster 16 compatible
Ethernet Card - D-Link DFE 530TX+ (added)
Startech 2-port PCI USB card (added)
[/INDENT]
I'm asking this because I am familiar with Ubuntu and would like to keep the same on this old desktop.

Please advise.[/QUOTE]

---

### Post by BoyOfDestiny on 2006-04-29
[QUOTE=*John*]Tbh, i'd say stick with Windows 98 if its "doing the job" (As it appears to be)

My question though, is how'd you get your ISP to consider hosting your own website "fair use"??? :-k 

John :)[/QUOTE]

I have to recommend not sticking with windows 98. Besides uptime issues (I averaged about 2 weeks, but there is a bug that prevents it going beyond 49.7 days...)
Dunno if they fixed it, but here is a link.
[http://news.com.com/2100-1040-222391.html?legacy=cnet](http://news.com.com/2100-1040-222391.html?legacy=cnet)

2nd, MS is dropping support for 98... I wouldn't want that machine exposed on the net without patches. 

As was said here a few times:
Try something like DSL, maybe look for a faq or copy your apache config files from ubuntu.

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

As for ISP's, mine blocks port 80 for hosting, but that wouldn't stop someone from using a different port... If you stay within your normal bandwidth limit the ISP shouldn't care...

Also, for practice, if you have an ok main desktop, launch the damn small linux iso in qemu. You can play around with it in the comfort of Ubuntu. :)

---

### Post by Kernel Sanders on 2006-04-29
[QUOTE=BoyOfDestiny]I have to recommend not sticking with windows 98. Besides uptime issues (I averaged about 2 weeks, but there is a bug that prevents it going beyond 49.7 days...)
Dunno if they fixed it, but here is a link.
[http://news.com.com/2100-1040-222391.html?legacy=cnet](http://news.com.com/2100-1040-222391.html?legacy=cnet)

2nd, MS is dropping support for 98... I wouldn't want that machine exposed on the net without patches. 

As was said here a few times:
Try something like DSL, maybe look for a faq or copy your apache config files from ubuntu.

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

As for ISP's, mine blocks port 80 for hosting, but that wouldn't stop someone from using a different port... If you stay within your normal bandwidth limit the ISP shouldn't care...

Also, for practice, if you have an ok main desktop, launch the damn small linux iso in qemu. You can play around with it in the comfort of Ubuntu. :)[/QUOTE]


I believe the flaw your describing was fixed for Windows 98 SE, so it should be ok providing that he's not using the first version of Windows 98 :D

The last figures I saw put Windows 98 usage at around 15%? Surely hackers arnt still targeting that group are they? :-k 

As far as internet traffic and bandwidth goes, i'm not sure I could personally host my own website..... (I have a 1mb/s DSL connection with a 1mb max download speed, and a 250k max upload speed) 

What connection do you lot have then to be able to host your own websites?

John :)

---

### Post by drizek on 2006-04-29
theres nubuntu which has fluxbox.

Personally i would just go with DSL. It is debian based so you can still use apt, but it is tons faster than ubuntu.

The flaws in windows xp are going to just be ones that werent patched for windows 98. Also, viruses are backwards compatible ;)

---

### Post by anil_robo on 2006-04-30
[quote=ubuntu_demon]you can install icewm / fluxbox or something like that on Ubuntu too. You don't need Damn Small Linux for that. It's just that a gui on a slow machine like that would use almost all resources.[/quote]

Would Ubuntu Server install fit on 1GB hard drive? And I will need some free space for my files as well.

---

### Post by anil_robo on 2006-04-30
[quote=*John*]Tbh, i'd say stick with Windows 98 if its "doing the job" (As it appears to be)[/quote]
Yeah, it works fine for me, but it's no fun! I would love to see linux on this machine! :)

> My question though, is how'd you get your ISP to consider hosting your own website "fair use"??? :-k 
I have an SBC DSL internet connection and the terms and conditions mention nothing about web hosting: [http://att.sbc.com/gen/general?pid=7688#hsi](http://att.sbc.com/gen/general?pid=7688#hsi)
:)

Anil

---

### Post by anil_robo on 2006-04-30
[quote=*John*]I believe the flaw your describing was fixed for Windows 98 SE, so it should be ok providing that he's not using the first version of Windows 98 :D

The last figures I saw put Windows 98 usage at around 15%? Surely hackers arnt still targeting that group are they? :-k[/quote]

M$ sucks! They wouldn't let me update my copy of windows98, which I have preserved with utmost care for all these years!!! Dudes, the support for win98 HAS ENDED (at least for me) despite whatever M$ may say!

> As far as internet traffic and bandwidth goes, i'm not sure I could personally host my own website..... (I have a 1mb/s DSL connection with a 1mb max download speed, and a 250k max upload speed) 

I have slower speeds than yours. My download is around 160kbps, and upload is about 60kbps. And I'm sharing the internet connection with three roommates (total four of us). Still, the [site]("http://stooge.myftp.org") is showing good response. :)

---

### Post by drizek on 2006-04-30
just go with DSL. 

It performs better than ubuntu and it has a much smaller install(about 128mb).

---

### Post by briancurtin on 2006-04-30
[QUOTE=anil_robo]Still, the [site]("http://stooge.myftp.org") is showing good response. :)[/QUOTE]
doesnt work at all

---

### Post by anil_robo on 2006-04-30
[quote=briancurtin]doesnt work at all[/quote]

Because I'm installing Ubuntu Server on that right now :)

Sorry for doing it so soon, but I am desperate to get rid of windows98 on that machine! :)

---

### Post by Kernel Sanders on 2006-04-30
[QUOTE=anil_robo]Because I'm installing Ubuntu Server on that right now :)

Sorry for doing it so soon, but I am desperate to get rid of windows98 on that machine! :)[/QUOTE]

Website still not working..... Windows 98 1-0 Ubuntu :(

*Joke*

John :)

---

### Post by Stew2 on 2006-04-30
I see that your website is back up. Did you get the server install working or go back to Windows 98? I think its great to see an old machine utilized vs going to a landfill! \\:D/ . Seems such a waste to throw out perfectly good machines.
Regards,
Stew

---

### Post by ice60 on 2006-04-30
i think it's still running Windows. what about these?
this has a web based setup
[http://www.engardelinux.org/modules/index/index.cgi](http://www.engardelinux.org/modules/index/index.cgi)

and there's the LAMP livecd which has the best hidden home page on the internet. i can't find it anyway. this is the closest i came to it. i know i've been there before. it's the LAMP livecd.
[http://www.linuxforum.com/lamp-manual.php](http://www.linuxforum.com/lamp-manual.php)

this is it. it seems perfect to practice with
[http://www.livelamp.org/](http://www.livelamp.org/)

---

### Post by anil_robo on 2006-04-30
[quote=Stew2]I see that your website is back up. Did you get the server install working or go back to Windows 98?[/quote]

Stew, I'm still using windows. I started Ubuntu server install. It was able to reach only 3% in six hours. So I gave up on that, and reinstalled windows 98. I still have puppy linux cd and Damn  Small Linux CD, so I'll try them after some time - hopefully I'll get D-Link 530TX PLUS card working!!!

> I think its great to see an old machine utilized vs going to a landfill! \\:D/ . Seems such a waste to throw out perfectly good machines.
Regards,
Stew

Thanks a bunch dude! :)

---

### Post by TrailerTrash on 2006-05-01
Try STX Linux. It works great. Its based off of Slackware. 

[http://www.stibs.cc/stx/](http://www.stibs.cc/stx/)

Check out the web site.

---

### Post by ubuntu_demon on 2006-05-01
[QUOTE=anil_robo]Stew, I'm still using windows. I started Ubuntu server install. It was able to reach only 3% in six hours. So I gave up on that, and reinstalled windows 98. I still have puppy linux cd and Damn  Small Linux CD, so I'll try them after some time - hopefully I'll get D-Link 530TX PLUS card working!!!
[/QUOTE]

You can check the cd for errors if you boot from the server cd (you'll see an option to check it).

---

### Post by anil_robo on 2006-05-01
[quote=ubuntu_demon]You can check the cd for errors if you boot from the server cd (you'll see an option to check it).[/quote]

Thanks for the tip. I checked the Ubuntu install CD for errors on my faster Dell laptop. The CD is fine. It's just the the desktop has very little processing power for the Ubuntu installer. I think I'm not going to fiddle around with this old desktop (a.k.a. "Stooge") anymore.

Thanks everyone! Now I need someone to critique [my website]("http://stooge.myftp.org")! :mrgreen:

---

### Post by drizek on 2006-05-01
[QUOTE=anil_robo]
Thanks everyone! Now I need someone to critique [my website]("http://stooge.myftp.org")! :mrgreen:[/QUOTE]

But its running on windows...

---

### Post by Kernel Sanders on 2006-05-01
[QUOTE=drizek]But its running on windows...[/QUOTE]

Whatever works tbh, and if thats windows 98, then thats fine......

P.S = I thought we were "pro choice" and "pro freedom" here? :neutral:

---

### Post by Stew2 on 2006-05-01
[QUOTE=anil_robo]Thanks for the tip. I checked the Ubuntu install CD for errors on my faster Dell laptop. The CD is fine. It's just the the desktop has very little processing power for the Ubuntu installer. I think I'm not going to fiddle around with this old desktop (a.k.a. "Stooge") anymore.

Thanks everyone! Now I need someone to critique [my website]("http://stooge.myftp.org")! :mrgreen:[/QUOTE]

I think it looks great, very professional! :D As for the OS, use whatever works best! ;) 

Regards,
Stew

---

### Post by htinn on 2006-05-01
Hate to nitpick but:

> For a simple website you made using your HTML editor, just place all your files (with index.html page) in the htdocs folder (\var\www directory for Ubuntu linux).

That should be "/var/www/" :p

---

### Post by drizek on 2006-05-01
[QUOTE=*John*]I thought we were "pro choice" and "pro freedom" here? :neutral:[/QUOTE]

Exactly, which means were anti-windows.:p 

Anyway glad your old puter is up and running, just kidding about the windows thing.

---

### Post by anil_robo on 2006-05-02
[quote=htinn]Hate to nitpick but:

That should be "/var/www/" :p[/quote]

Hey thanks for spotting this! I guess windows 98 is now getting on my nerves! As long as I was using Ubuntu only, I could use the slashes better. Now I have windows98, I frequently insert forward/backward slash in the wrong way! :D Stupidly cool! :rolleyes:

---

### Post by anil_robo on 2006-05-04
Now look what!

I have also subscribed to Google adsense, and made $10 already in three days! :) This is cool! The damn old computer is actually earning me money! Quite funny, interesting and inspiring! :D

---

