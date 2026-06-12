---
title: "Backing up the server"
date: 2010-05-29
forum: Server Platforms
---

### Post by KunoNoOni on 2010-05-29
So after many years I've finally decided to upgrade my Ubuntu Server. Right now its running 6.06 LTS, I think. I know its the server version of 6 :)

Anyways, normally when I would change version of Linux I'd just format and reinstall. But I have many things on there that I don't want to lose. Like my Mysql database. So I guess my question is How would you go about backing up the information that you don't want to lose then add it back when you've upgraded to a newer version of the server.

I hope this makes sense. This is the first time I've ever done this on Linux. 

-KunoNoOni

---

### Post by craigp84 on 2010-05-29
Hey join the club! I've still got a 6.06 running in a client site too :P nowt wrong with it either.

First things last and all that, get the un-sexy work done first. Backups all in order? Tested bare metal restore (do the first try into a virtual machine) all a-ok?

For upgrading you;ve got 2 main paths if there's no new hardware being purchased: blow it all away and install fresh or read the release notes and upgrade through each LTS version in turn until you arrive at the one you want to stick on. Read the instructions and follow, it's pretty fool proof to be honest.

Remember software versions change, and that means their config files, data file formats and usability change too. In your MySQL case there's a few differences for upgraders, there's a nasty one (i forget exactly what it is, but it'll be in the release notes or changelog) to do with UTF character sets if i remember right. Just remember a client coming unstuck on an upgrade and me getting a middle of the night wakeup call :-(

p.s. you've also identified a hole in your documentation for this system i think...

p.p.s. you've got time on your side before 6.06 goes EOL, don't rush into anything if this is a production box.

---

### Post by KunoNoOni on 2010-05-29
Hmm, that does sound easy :) I just want to be sure that if I upgrade to the next LTS that the data I already have won't be removed. 

Thanks for the input though :)

-KunoNoOni

---

