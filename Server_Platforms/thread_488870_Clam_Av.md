---
title: "Clam Av"
date: 2007-06-30
forum: Server Platforms
---

### Post by borahshadow on 2007-06-30
Ok I Have a file server that serves several windows machines

I have dapper installed on that server. I want to install clamav (or some AV) to add an extra layer of protection to my family's windows machines

I want to have clamav run weekly or something from cron [Look here for more info on that]("http://ubuntuforums.org/showthread.php?t=488856").

But from what I've read dapper's clamav is so outdated that some of the new virus signatures don't even work with it

I'm not against compiling from source but I couldn't find and detailed guides for it. Some mentioned having to add clamav user and said you have to configure with --enable experimental or something I want an explanation (I don't want experimental I want stable?)

So here is my question does anybody know of any good guides for compiling clamav on ubuntu (or any distro really)

is it worth it to compile it and not just use the old one from the repos (I think yes)

and if someone wants to help me get it scanning with cron your welcome to but I think I can figure that our if I need to.

I know that AVG has a linux version but it is RPM I could try alien if I need to would you recommend that instead of clamav?

are there any other good Linux anti virus?

would it be worth it to run 2 AV?

Thanks

---

### Post by peterbrewer on 2007-06-30
If you add the backports repository you should get a more updated version.

---

### Post by keithweddell on 2007-07-01
See [this thread]("http://ubuntuforums.org/showthread.php?t=384190&page=5") for backporting the latest version.  You will need to search further back in the thread for dapper specific instructions.


Keith

---

### Post by lisati on 2007-07-01
Having 2 AV systems in place might slow things down a bit if they're both set to do their stuff at the same time

---

### Post by euler_fan on 2007-07-01
The ClamAV website has a main document that pretty much explains everything, including how to set it up from an install from source situation, using the daemon, etc. I've used it several times and it seems to work great.

---

### Post by borahshadow on 2007-07-03
Thanks for all the replies
I was just looking at the wki for clamav which was vague
the pdf doccumentation looks great I think I'll compile from source
now what I'm not sure about is how to actually do the scanning on my fileserver

I was going to run a cron job but clamav I read that it stopps when a virus is found how can I make it not and how can I email the results of the scan to my email?
I noticed something in the doccumentation about the clamav daemon whoud that be better than cron?
thanks

ps does anybody else have opinions about using 2 AV like having each run every other day staggered?eg. clam-mon-wed-fri-sun  AVG-tue-Thur-sat

EDIT I just noticed that AVG now has a deb for debian and ubuntu so mabey I'll Go that route any opinions?

---

### Post by euler_fan on 2007-07-03
> **borahshadow said:**
> Thanks for all the replies
I was just looking at the wki for clamav which was vague
the pdf doccumentation looks great I think I'll compile from source
now what I'm not sure about is how to actually do the scanning on my fileserver

I was going to run a cron job but clamav I read that it stopps when a virus is found how can I make it not and how can I email the results of the scan to my email?
I noticed something in the doccumentation about the clamav daemon whoud that be better than cron?
thanks

ps does anybody else have opinions about using 2 AV like having each run every other day staggered?eg. clam-mon-wed-fri-sun  AVG-tue-Thur-sat

EDIT I just noticed that AVG now has a deb for debian and ubuntu so mabey I'll Go that route any opinions?

cron is a good option, especially for updating your definition files. Not sure how to make the email thing work (but it would be nice!). The scanning part is easy. Open the terminal and enter:
```
clamscan -r -i /
```
which will scan everything on the root partition. I have heard that one must run it under sudo for it to scan absolutely everything, but I am not personally sure of this either way. Even with a cron job it is still a good idea to run a manual scan periodically in addition to looking at any log files.

Insofar as two AV systems are concerned, there is really no need for two on an Ubuntu machine. ClamAV should be enough. I would personally be more worried about a firewall, an IDS, and root kit hunters than a second AV system. Firestarter is a great simple firewall app for a personal machine or simple server (nothing too fancy but still very flexible) and you can look into installing OSSEC-HIDS and/or SNORT,  chkrootkit, and rkhunter too. I never have managed to get either OSSEC-HIDS or SNORT fully set up to the point where I knew what was going on and could monitor things, but it is worth a shot.

---

### Post by borahshadow on 2007-07-05
Thanks everything is working I think :)

---

