---
title: "General Installation Question"
date: 2009-10-14
forum: Server Platforms
---

### Post by Ewanuk on 2009-10-14
Hi there,

I am completely new to linux (raised on Microsoft/Mac) and am slowly getting used to the nuances of it.

Right now I'm installing Bugzilla on our Linux server and trying to follow the installation instructions.

At the moment, I'm at the stage where I have to install a set of perl modules. However, this system is very mission critical (read: not backed up with a lot of sensitive stuff on it) and I cannot risk changing any databases or changing configurations such that some of our services don't work.

If I run commands such as:

/user/bin/perl install-module.pl CGI
or 
/user/bin/perl install-module.pl DBD::mysql

this is generally the same as installing a plug-in or additional libraries on an existing application (using a windows-based platform as a comparison) right?

I know I come off as the paranoid computer user, so be forgiving  I just cant afford to **** up.

thanks!

---

### Post by kanikilu on 2009-10-14
> this is generally the same as installing a plug-in or additional libraries on an existing application (using a windows-based platform as a comparison) right? I think that's a fair comparison. There's no telling if it will conflict with anything else on the system, though, since we don't know what else is on there.

> However, this system is very mission critical (read: **not backed up** with a lot of sensitive stuff on it) ***What?*** Sorry to state the obvious, but BACK THAT UP ASAP! I just had a colleague lose about a year's worth of data because of *very* poor backup habits. If you are a system administrator, getting that backed up **is** your mission.

---

### Post by Ewanuk on 2009-10-14
Hehe, tell me about it. This is office flies blind when it comes to IT. I keep reporting to the higher-ups that you must bring in someone qualified/experienced to look after this, but they live in the world that nothing bad will happen if they ignore the problem.

I've been filling in on IT work Pro Bono just because, sad to say, I know the most of anyone here and actually have *some* time to deal with some of the problems.

Unfortunately, there just isn't enough hours in the day for me to sit down and integrate a backup system for free. I just don't know enough about what I'm doing.


Annnyway, back on topic:

We have a set of other MySQL databases (Trac, Games, Scrumworks, etc.) so I'm assuming by installing a "plug-in", I'm not going to destroy or alter any of that data. The system itself runs pretty barebones, there's not a lot on there besides a small host of server apps and their respective MySQL databases.

Thanks for the help

---

### Post by kanikilu on 2009-10-14
I hear ya. The people around here are the same way. I've been lobbying for a centralized backup solution for the better part of a decade with no success :-/ So, it's up to the individual user, and as I'm sure they are around the world, users want to get work done, not run updates, do backups, etc...

> We have a set of other MySQL databases (Trac, Games, Scrumworks, etc.) so I'm assuming by installing a "plug-in", I'm not going to destroy or alter any of that data. The system itself runs pretty barebones, there's not a lot on there besides a small host of server apps and their respective MySQL databases. I wouldn't think so, but I still have to keep the disclaimer, since I don't know 100% ;)

Is there no way you could at least do a "one time" backup so that if things go pear shaped, you can at least get things back to they way they were relatively painlessly?

---

### Post by Ewanuk on 2009-10-14
If I could just basically do a carbon copy of the hard drive to our network drive, I'd be happy enough for now and could probably score some points with the superiors, maybe then they would actually listen to me :P. I don't mind doing a manual backup solution like that once a week or so.

Do you know a good piece of linux-based software that will take care of that?

---

### Post by kanikilu on 2009-10-14
It's been a while since I've done full disk images (I just backup what I need with rsync), but I used partimage in the past.

[http://www.partimage.org](http://www.partimage.org)

I think it's in the repos, so you can install it with Synaptic/aptitude.

Maybe someone else has experience with other solutions? I see Bacula get mentioned here sometimes, but haven't used it myself...

[http://www.bacula.org/en/](http://www.bacula.org/en/)

---

### Post by Lars Noodén on 2009-10-14
1) as @ kanikilu  wrote: back everything up ASAP!

2) You can usually add perl modules using the package manager, it is much less risky that way.  Look for ones that match the pattern 'lib.*perl'

You can look for specific packages using apt-cache. e.g.

```
$ apt-cache search DBD::mysql
libdbd-mysql-perl - A Perl5 database interface to the MySQL database
libdbd-mock-perl - Mock database driver for testing
libdbix-fulltextsearch-perl - Indexing documents with MySQL as storage

```

If there are too many, then use egrep or less.

---

