---
title: "guarddog"
date: 2008-03-20
forum: Security Discussions
---

### Post by spudratic on 2008-03-20
Error: "/tmp/ksocket-xxxxpzmM28" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-xxxxpzmM28" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-xxxx" is owned by uid 1000 instead of uid 0.
kbuildsycoca running...
Error: "/var/tmp/kdecache-xxxx" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-xxxx" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-xxxx" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-xxxx" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-xxxx" is owned by uid 1000 instead of uid 0.

The above error happens in terminal when I start guard dog by either command       

gksudo guarddog    or sudo guarddog I really don't know which one is correct no matter it starts and I can open ports and adjust it.

here is what happened all was fine no errors then the desktop kind of crashed      . the desk top went from the cube to just a 2 panel so I rebooted and when I started guard dog these errors came up.


I have no idea what they mean and wanted to see if I could fix it by uninstalling and then installing guarddog no luck with that route.

So I need some help or a page that deals with this or is it ok just to leave it alone.I would rather fix this if at all possible.I do not like errors for one and most definitely not in the firewall gui that interacts with the iptables

thanks for any help

edit p4 with 2 gigs of ram on a dual boot with xp

---

### Post by (((X))) on 2008-03-22
By reading errors you get, I suppose that you are using kubuntu or kde.
You shouldn't run kde app as root,
use kdesu instead of gksudo/sudo.

---

### Post by spudratic on 2008-03-22
thanks x I will give it a try. I'm running ubuntu 7.10 gusty


edit

 kdesu guarddog
kbuildsycoca running...
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Launched ok, pid = 6656


 gave it a try and got the above any idea whats going on.I'm a little lost

---

### Post by (((X))) on 2008-03-22
Hi, spudratic

I'd say..lieve it the way it is,
after all, it's just a GUI for iptables.
If you are not sure settings are sucessfully applied, 
iptables --list will give you current firewall state.

---

### Post by spudratic on 2008-03-22
It works fine just like it should X just those errors so I'm not worried about it if you say so there is nothing important on this box anyway.I just don,t want to have trouble while I,m learning this os I have enough trouble as it is lol.You wouldn't happen to know a good guide to find out what vlc shoutcast tv uses so I can get that to work.don,t bather if you don't know right off as I find a lot of info I need for other problems as I look for the solution for another.Read till your eyes bleed lol.Thanks again

---

