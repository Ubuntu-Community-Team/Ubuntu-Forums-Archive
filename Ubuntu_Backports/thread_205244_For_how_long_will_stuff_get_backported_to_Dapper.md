---
title: "For how long will stuff get backported to Dapper ?"
date: 2006-06-28
forum: Ubuntu Backports
---

### Post by ubuntu_demon on 2006-06-28
Hi,

For how long will stuff get backported to Dapper ? Will there be only backports from Edgy or also from Edgy+1 ? I am curious because Dapper is a LTS and Edgy might not be suitable for some people due to its "edginess".

I'm sorry if this has been asked before (then I've missed it).

---

### Post by Akoluth of Nandus on 2006-06-28
The farther the current Ubuntu release moves away from Dapper the harder it will be to make a proper backport, i suspect.
Maintaining more than one backport target release (the LTS release and the newest release) also affords more work/time that the backporters have to have. ;)

---

### Post by ubuntu_demon on 2006-06-28
[QUOTE=Akoluth of Nandus]The farther the current Ubuntu release moves away from Dapper the harder it will be to make a proper backport, i suspect.
Maintaining more than one backport target release (the LTS release and the newest release) also affords more work/time that the backporters have to have. ;)[/QUOTE]
true

In order to give users good advice on whether or not to run backports we need some idea of timeframes.

---

### Post by Snam on 2006-06-28
[QUOTE=ubuntu_demon]For how long will stuff get backported to Dapper?[/QUOTE]

Are there backports for Dapper? On [http://ubuntuforums.org/showthread.php?t=40291](http://ubuntuforums.org/showthread.php?t=40291) I only see /etc/apt/sources.list lines for Hoary and Breezy.

What is the /etc/apt/sources.list backport line for Dapper? Or where can I find a list with all the backport lines?

Thnx,

Snam

---

### Post by ubuntu_demon on 2006-06-28
[QUOTE=Snam]Are there backports for Dapper? On [http://ubuntuforums.org/showthread.php?t=40291](http://ubuntuforums.org/showthread.php?t=40291) I only see /etc/apt/sources.list lines for Hoary and Breezy.

What is the /etc/apt/sources.list backport line for Dapper? Or where can I find a list with all the backport lines?

Thnx,

Snam[/QUOTE]
AFAIK there are no backports for Dapper yet. As you can see here :
[http://packages.ubuntu.com](http://packages.ubuntu.com)
[http://packages.ubuntu.com/dapper-backports](http://packages.ubuntu.com/dapper-backports)

My recommended Dapper sources.list shows the backport lines :
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)
> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


---

### Post by caldevil on 2006-06-28
The backports of rhythmbox 0.9.5 and couple of others are in testing stage. We should expect the first backport pretty soon.

---

### Post by doclivingston on 2006-06-28
[QUOTE=ubuntu_demon]For how long will stuff get backported to Dapper ? Will there be only backports from Edgy or also from Edgy+1 ? I am curious because Dapper is a LTS and Edgy might not be suitable for some people due to its "edginess".[/QUOTE]

I imagine it will depend greatly on the dependencies of the application. If an application starts depending on newer versions of libraries, it starts getting a lot harder to backport - virtually impossible if they are "core" libraries that it isn't safe to upgrade.

---

### Post by paul cooke on 2006-07-11
> **doclivingston said:**
> I imagine it will depend greatly on the dependencies of the application. If an application starts depending on newer versions of libraries, it starts getting a lot harder to backport - virtually impossible if they are "core" libraries that it isn't safe to upgrade.
like the trouble you had with Firefox 1.5 and Breezy...

---

