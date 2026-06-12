---
title: "Is there any Linux alternative for Hazel / Belvedere?"
date: 2008-03-29
forum: The Cafe
---

### Post by hazica on 2008-03-29
I just stumbled upon this [list]("http://blog.bachyaproductions.com/index.php/software/2008/03/19/5-coolest-unknown-freeware-for-windows-stage-1/") of Windows freeware and entry number 3 caught my eye.
It is a program called [Belvedere]("http://lifehacker.com/341950/belvedere-automates-your-self+cleaning-pc") which is apparently a rip-off of the Mac-only [Hazel]("http://www.noodlesoft.com/hazel.php").
Here's a quote from the page, describing the functionality of Hazel:

> Some time ago, I ran across an awesome program for the Mac called Hazel, a rule-based program designed to keep files on your computer in order. Want your downloads folder - where you dump everything you download in Firefox - cleaned every week? Hazel can do it.

I really like the idea of partially automating the file management on my computer, so I was wondering whether there are any Linux alternatives to the programmes mentioned above.

Cheers!

---

### Post by zobcat on 2008-04-01
I just "stumbled" on the same site. Looks like we're in the same boat. Your post is all I found.

---

### Post by madjr on 2008-04-01
am sure what you want can be automated as a cron job with a few simple scripts if some gui program is not available.

you can automate anything in linux.

---

### Post by sicofante on 2008-04-04
> **zobcat said:**
> I just "stumbled" on the same site. Looks like we're in the same boat. Your post is all I found.
Same here. This is the type of apps we need to make Linux useful for day to day home/office computing.

---

### Post by hazica on 2008-04-05
> **madjr said:**
> am sure what you want can be automated as a cron job with a few simple scripts if some gui program is not available.

you can automate anything in linux.

Quite! But playing with shell scripts isn't really everyone's cup of tea and it doesn't reach the broad public. GUI's are the way to go.

We'll see... maybe someone with some spare time on their hands might write this little piece of software for the Linux community. 

Any volunteers?:D

---

### Post by sicofante on 2008-04-07
> **madjr said:**
> am sure what you want can be automated as a cron job with a few simple scripts if some gui program is not available.

you can automate anything in linux.
A desktop is a desktop is a desktop. Not a server.

---

### Post by original_jamingrit on 2008-04-07
> **sicofante said:**
> A desktop is a desktop is a desktop. Not a server.

What's wrong with with running cron job scripts on a desktop?

Doing a little bit searching, I found a related app: GNOME crontab editor:
[http://nixbit.com/cat/desktop-environment/tools/gnome-crontab-editor/](http://nixbit.com/cat/desktop-environment/tools/gnome-crontab-editor/)
[http://gnome-apps.berlios.de/apps.php?action=view&id=22962](http://gnome-apps.berlios.de/apps.php?action=view&id=22962)

Although it seems to have been abandoned??? can someone using GNOME check it out?

---

### Post by banjobacon on 2008-04-07
Based on the description of Hazel, the Download Sort extension for Firefox might provide you with somewhat similar functionality.

[https://addons.mozilla.org/en-US/firefox/addon/25](https://addons.mozilla.org/en-US/firefox/addon/25)

---

### Post by sicofante on 2008-04-07
> **original_jamingrit said:**
> What's wrong with with running cron job scripts on a desktop?
Nothing, if you're a system administrator, in which case a server and a desktop look pretty much the same to you. Otherwise, suggesting scripts to people asking for an alternative to something so end-user oriented as Hazel/Belvedere is stupid (a very common stupidity in Linuxland, BTW). If people suggesting these things knew the  design difference between a desktop and a server, they would stop doing so.

---

### Post by bardophile on 2009-04-14
Just found gnome-schedule. Going to see if it can do the same job Hazel and Belvedere do. Will post back here with my conclusions, but someone else might want to futz around with it in the meantime.

---

### Post by Tibuda on 2009-04-14
> **bardophile said:**
> Just found gnome-schedule. Going to see if it can do the same job Hazel and Belvedere do. Will post back here with my conclusions, but someone else might want to futz around with it in the meantime.

Yes, it can. But you need to know bash. See the manual page for find and rm. (type "man find" and "man rm" in your terminal)

---

### Post by mkmcllln on 2010-07-27
Has anyone had any luck finding a linux equivalent for Hazel / Belvedere?  This would be really handy to help me sort all of my downloads.

---

### Post by kujhawk94 on 2010-11-09
FWIW, today after a bit of Google work, I located a package called *incron* which looks more or less to be the answer to this thread's question - except it is CLI <shrug>

Here's the package description:
> incron is an "inotify cron" system. It works like the regular cron but is driven by filesystem events instead of time events. This package provides two programs, a daemon called "incrond" (analogous to crond) and a table  manipulator "incrontab" (like "crontab").                                                                         

incron uses the Linux Kernel inotify syscalls. 

like cron, each user can edit its own incron tables.
 
incron can be used to : 
* notifying programs (e.g. server daemons) about changes in configuration  
* guarding changes in critical files (with their eventual recovery) 
* file usage monitoring, statistics  
* automatic on-crash cleanup 
* automatic on-change backup or versioning       
* new mail notification (for maildir) 
* server upload notification  
* installation management (outside packaging systems)
* ... and many others                                                  
Homepage: [http://inotify.aiken.cz/]("http://inotify.aiken.cz/") 

---

### Post by benjaminoakes on 2011-05-30
I'm working on an open source, Hazel-inspired project that I'm calling "Maid".  If you have RubyGems installed (typical if you have Ruby), it just takes a single command to install:

```

sudo gem install maid --pre
# And if you don't have RubyGems, this should set you straight:
# sudo apt-get install rubygems

```

Specifying --pre will install pre-release versions, the Maid beta version in this case.  Even though it's in beta at the time of this writing, I would love to have your input and opinions.

There's more info at [http://github.com/benjaminoakes/maid](http://github.com/benjaminoakes/maid) and [http://rubygems.org/gems/maid](http://rubygems.org/gems/maid).

Maid is based on some code I had written for myself.  Eventually, it turned into something I thought others might find useful, so I packaged it up.  I've been using Maid on a few Macs for a while now, but I use a few Ubuntu machines per day, so Linux support is important to me.  Right now, it's command-line and cron-based, and I'm certainly open to improvements.

Anyway, if anyone here is a programmer or eager beta-tester, please take a look and let me know what you think. Any and all contributions are welcome!

---

