---
title: "Getting the latest security fixes...?"
date: 2006-07-16
forum: Server Platforms
---

### Post by Eidar on 2006-07-16
Hi,

I uninstalled my entire ubuntu-desktop and other packages that I do not currently need.

So I access my Ubuntu-server through SSH from my other workstations. I am only concerned about one thing; security updates and such.

How exactly can I get new security updates and updates for other packages - from a command line based environment?

I tried:

apt-get update && apt-get upgrade

But I never see any security, kernel updates being available. The MySQL package, I believe, had one update a couple of days ago - that's all.

Please advice.

/EIDAR

---

### Post by Jagot on 2006-07-16
There haven't been any updates for the last couple of days.  If that is exactly what you entered, remember to add sudo before commands.

---

### Post by aysiu on 2006-07-16
If you're that concerned, I would keep the *ubuntu-desktop* metapackage installed unless you're really hard-up for disk space. It ensures you get all the proper upgrades. And I would do ```
sudo aptitude update && sudo aptitude dist-upgrade
``` instead of just an upgrade--it's something I learned from [this thread](http://www.ubuntuforums.org/showthread.php?t=86198).

---

### Post by Eidar on 2006-07-16
Thanks, Jagot. When I login by SSH I usually "sudo -s" to become root permanently during the session.

"sudo"'ing all the time would make me ill :)

/EIDAR

---

### Post by Eidar on 2006-07-16
Thank you. I read about 5 pages.

Anyway, I'm running Breezy and was a bit concerned because the kernel seems old too:

Linux [DELETION] **2.6.12-10-386** #1 Mon Jun 12 22:04:42 UTC 2006 i686 GNU/Linux

Does that look alright?

/EIDAR

> **aysiu said:**
> If you're that concerned, I would keep the *ubuntu-desktop* metapackage installed unless you're really hard-up for disk space. It ensures you get all the proper upgrades. And I would do ```
sudo aptitude update && sudo aptitude dist-upgrade
``` instead of just an upgrade--it's something I learned from [this thread](http://www.ubuntuforums.org/showthread.php?t=86198).

---

### Post by aysiu on 2006-07-16
You're using Dapper, right? The latest I have is this: ```
linux-image-2.6.15-26-686
```

---

### Post by Jagot on 2006-07-16
> **aysiu said:**
> You're using Dapper, right?

He's using Breezy.  According to [http://packages.ubuntu.com/](http://packages.ubuntu.com/), the latest kernel for Breezy is 2.6.12.16.1, so yours appears to be out of date.

---

### Post by aysiu on 2006-07-16
Sorry, Jagot. Good catch.

---

### Post by Eidar on 2006-07-17
I see.

So to update to the latest kernel I would do this:

apt-get install linux-686

Does that look correct?

/EIDAR

---

### Post by az on 2006-07-17
Do you have Dapper-security and Dapper-updates repositories enabled?  You probably ony have the dapper repositores enabled.


For ever dapper main restricted universe.... 
you should have
dapper-security main restricted universe
and
dapper-updates main restricted universe...

---

### Post by Eidar on 2006-07-17
Oh really? Should I really enable those if I am running Breezy? I did not know.

/EIDAR

> **azz said:**
> Do you have Dapper-security and Dapper-updates repositories enabled?  You probably ony have the dapper repositores enabled.


For ever dapper main restricted universe.... 
you should have
dapper-security main restricted universe
and
dapper-updates main restricted universe...

---

### Post by az on 2006-07-17
Well, enable the breezy ones.

---

### Post by Eidar on 2006-07-17
Thank you. I had already added all these, it would seem. Anyway - I have also updated to the latest kernel available at packages.ubuntu.com, but is a reboot needed for the changes to actually take full effect, or can I leave it as it is? The reason why I don't really want to reboot is because its a server and its running a bunch of services, including http webserver with several domains.

/EIDAR

---

### Post by az on 2006-07-17
You need to reboot into your new kernel.  In the meantime, you are still using your old kernel.

---

### Post by Eidar on 2006-07-17
Hehe, OK. That is what I suspected too, but I was not entirely 100% sure of that.

I guess a reboot will have to be done soon.

/EIDAR

> **azz said:**
> You need to reboot into your new kernel.  In the meantime, you are still using your old kernel.

---

