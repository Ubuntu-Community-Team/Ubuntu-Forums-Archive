---
title: "use my celeron D, 3.33GHz, 512RAM as a server"
date: 2006-10-31
forum: Server Platforms
---

### Post by johnsincred on 2006-10-31
I am trying to figure out what version of Ubuntu Server so I need to use to get my web server online, I will be installing it on a compaq presario sr2006nx, celeron D processor 356, 3.33GHz, 512RAM and 80G HD.  I would also like to be able to use PHP and MySql as well.  I read somewhere that apache, PHP amd MySql is part of a LAMP distribution, what is this?  The last question is, do I need to install a operating system or does the Ubuntu server software the same as the Ubuntu operating system?:confused:

---

### Post by blind0wl on 2006-10-31
Server is pretty much the same as the normal Ubuntu, its just toned down with the apps.  When your running a server I guess the philosophy is, it should only run whats needed and not have a heap of stuff its never going to use.

You can install mysql, php and apache on any edition of Ubuntu.  Its the size of the install is what their giving you...choice...gotta love it

Cheers

Blindy

---

### Post by bache on 2006-10-31
LAMP stands for Linux, Apache, MySQL, PHP and when you get it you get all in one. Otherwise you have to install them one by one. LAMP is the easier way but by installing them one by one you can choose what versions to install and you have more flexibility.

I think the better solution for you is to install ubuntu desktop not the server because it will be easier for you to use the graphical environment than the console.

Ubuntu is operating system. You don't need to have another installed.

---

### Post by Chayak on 2006-10-31
You want a deadicated server as lean as possible running only the processes it needs to do it's job to cut down on security risks and resource usage.  By default Ubuntu server is command line only and honestly if you're asking this type of question you probably are not that familiar with linux command line.  I'd suggest doing a normal install of Ubuntu and then adding the server packages you need.  You also might want to check out [http://www.runyourownserver.org/]("http://www.runyourownserver.org/") a podcast I found by accident that has a lot of good tips for people wanting to run their own servers.

---

### Post by Gekitsuu on 2006-11-02
> **Chayak said:**
>  You also might want to check out [http://www.runyourownserver.org/]("http://www.runyourownserver.org/") a podcast I found by accident that has a lot of good tips for people wanting to run their own servers.

No don't listen to those guys, they're idiots ;) 


Gekitsuu
NoVaLoCo Team Leader
Co-Host - Run Your Own Server Podcast.

---

### Post by tturrisi on 2006-11-02
I have a compaq presario 333 celeron w/ 256mb ram that has been running Debian Woody lamp server for 4 yrs 24/7 rock solid.  It has been rebooted ONLY due to power brownouts & blackouts (bios is set to reboot if power cuts out). It has a gui using Fluxbox, nedit (txt editor), emelfm (file manager) & no display manager (xdm) so boots to shell. 

Your system would do well using Debian Etch.  I haven't upgraded it to Sarge or Etch because my php4-mysql3.x scripts will break.

---

