---
title: "Windows 7 equivalent of vmstat -s?"
date: 2011-01-02
forum: Server Platforms
---

### Post by fatalGlory on 2011-01-02
Sorry if I shouldn't be asking this here, since it's not strictly an ubuntu question.  These forums just seem to be where the people who can actually help tend to hang out ;)

There is a linux utility called vmstat, which when called with "vmstat -s", displays a list of virtual memory statistics.  Particularly interesting is the different figures for memory that is "in use" versus memory which is "active".  Users familiar with the UNIX "top" command will also notice that it displays the figure for memory "in use" rather than "active".

After setting up a Windows 7 machine, I notice that its main resource monitoring GUI shows around 800-900MB of memory in use when idling at the desktop.  That seems incredibly high (considering I've set up openbox-based desktops that idle below 100MB and a full-blown Gnome+Compiz desktop at around 350MB).  I've been trying to figure out how much of this memory is actively used by processes, and how much (if any) is just sitting idle.

Can anyone tell me of a Windows 7 utility that can show me this information?  Or failing that, tell me where I might find a forum with people who know Windows well enough to help me?

**DISCLAIMER/EXPLANATION:**
I'm a long time Ubuntu user.  I've been doing UNIX administration (mostly with debian and centos systems) through 2010, but have now taken a job doing .NET development.  I'm just trying to re-learn my way around windows (having barely used it since XP SP2 was new).

---

### Post by CharlesA on 2011-01-02
Does task manager count? :-\" You might want to check out "Resource Monitor" which is accessible from task manager.

Depending on how much RAM you've got that should be fine. My netbook idles at around 700-800MB used, but it's got 2GB of RAM.

EDIT: [http://windows7forums.com/](http://windows7forums.com/)

---

### Post by fatalGlory on 2011-01-02
The resource monitor shows some statistics, but it only seems to list memory that is (by its own terminology) "in use".  What I'm wondering is whether this is equivalent to the "in use" statistic or the "active" statistic from vmstat/top.

Here's hoping its equivalent to "in use" because if not, then it would seem that Windows 7 literally uses around triple the memory of a Gnome/Compiz desktop when idling.

Thanks for the reply, might try windows7forums.  *sigh*, I am filled with sorrow, putting the windows business-suit back on after 7 years as a barefoot, unshaven linux/free-software hippie, lol.

---

### Post by CharlesA on 2011-01-02
Windows is Windows, I suppose.

The resource monitor lists cached memory as well, which is the same as what free -m shows.

Memory usage isn't really a huge deal unless you have a low spec system. Most everything today comes with 4GB of RAM or more.

The box I have running Ubuntu Desktop is running at 300MB of RAM used, but it's only got 512 RAM.

*shrugs*

---

