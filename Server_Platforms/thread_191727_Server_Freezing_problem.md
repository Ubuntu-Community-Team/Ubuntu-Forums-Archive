---
title: "Server Freezing problem"
date: 2006-06-07
forum: Server Platforms
---

### Post by TriggerHappyChewie on 2006-06-07
Ok, so I had Dapper installed fine and was running a webserver using Apache, PHP5, and MySQL.  I was using it to run Ubuntu Center among other things.  I wanted to give Dapper Server a try.  It is on the exact same computer, same hardware.  I installed the server addition with the LAMP option.  It boots up fine and works great, including Apache/MySQL/PHP.  However, whenever I try to do ANYTHING with apt-get, including update or install, it locks up.  It completely freezes, I can't even switch using Ctrl+Alt+F2.  It's a complete hard lock.  I tried stopping some services like apache and mysql, but it still freezes.

Any ideas?  I need to get my music streaming soon!

Thanks :-)

[EDIT]: Well, it always freezes while using apt-get, but it also freezes intermittently.  It sometimes freezes at boot-up, and even freezes while I'm not even touching the keyboard or running any commands.  I am still trying to disable all the services I can.

---

### Post by TriggerHappyChewie on 2006-06-07
I tried disabling some more services, but no luck.  I am going to try to re-install the server without LAMP and see what that does.  I want to use lighttpd anyway.

Still help if you have any ideas though! :p

---

### Post by TriggerHappyChewie on 2006-06-08
Bump?

---

### Post by linuxone on 2006-06-08
Hi,

[QUOTE=TriggerHappyChewie]I tried disabling some more services, but no luck.  I am going to try to re-install the server without LAMP and see what that does.  I want to use lighttpd anyway.[/QUOTE]

did you check /var/log/*  (syslog, messages, daemon.log, kernel.log, ... ) for related error messages?

What kind of hardware has your server? For example: are you using more than one network card? Maybe using some kind of firewall rules?

I tried Dapper on 2 different machines yet and must remove it from both because it fails and won't run. First one was a hardware compatibility problem (Adaptec Raid Controller fails, possibly a basic Linux/Kernel problem). On the second PC several programs won't run, ie. my year's old firewall script doesn't work, DNS proxy won't work, samba doesn't run, cups won't accept any printer .... finally, Dappar was and still is a real nightmare for me. I'm really very disappointed about "LTS". Really. :mad:
Don't like to say this - I moved all my servers and desktop machines to Ubuntu-Server 5.10 a few month ago, after ~5 years using Mandrake.

Thomas

---

### Post by TriggerHappyChewie on 2006-06-08
It's a Pentium 4 1.7Ghz, ATI Radeon 9600 XT, 384 mb ram, 40 GB WD HDD, onboard LAN.

It works just fine with Dapper Desktop, I'll check the logs, thanks for the suggestion.

---

### Post by TriggerHappyChewie on 2006-06-08
I think it might be a problem with my hard drive, it's ide.  I saw some error that I didn't understand in the system log about it, but I also saw something about DMA.  It tried fiddling around with the DMA options but no luck.  When I do apt-get update, it always stops at 98% on updating package lists. (I think?)

---

### Post by TriggerHappyChewie on 2006-06-08
GAH!  I installed without the LAMP option and still no luck.  I can't figure this out, it seems completely random.  It sometimes freezes while switching directories!  I think I'm going back to Dapper Desktop. :-(

Maybe my harddrive is shot...

---

