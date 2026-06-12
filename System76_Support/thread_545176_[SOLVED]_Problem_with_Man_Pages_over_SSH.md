---
title: "[SOLVED] Problem with Man Pages over SSH"
date: 2007-09-07
forum: System76 Support
---

### Post by blackhole54 on 2007-09-07
Hi All,

I have an old computer running RH 7.0 that I frequently use to SSH into both a Ratel and a Pangolin, each running *edgy eft*.  I am posting this on this forum because there is a difference between the Ratel and the Pangolin that I don't understand.  When I view a man page from the Pagnolin (over SSH) the page always displays fine.  But man pages from the Ratel are usually screwed up --  anything from weird or foreign characters, to the page being practically unreadable, to sometimes locking up the terminal.  The difference baffles me as I thought the Ratel and the Pangolin were running identical software.

I presume this is a subset of a larger issue of other things not displaying right on the RH 7.0 system when originating from a remote system that is accessed via SSH.  But since these two similar Ubuntu systems are giving such divergent results, I thought this might be a good place to start analyzing this issue.

Does anybody have any thoughts where to start looking, or what might be different between the Ratel and Pangolin?

---

### Post by thomasaaron on 2007-09-07
As far as anything that would affect ssh, there is nothing that I can think of different in the Pangolin and Ratel.

You might want to completely remove ssh from the Ratel, purging all config files and then re-install it. Maybe there is some configuration/character encoding nuance that accidentally got messed up.

At any rate, this problem is one that would be very difficult for us to reproduce. If you want to email me (support...system76....com), I could try to ssh into your Ratel and see if I get the same problem.

Best,
Tom

---

### Post by blackhole54 on 2007-09-08
> **thomasaaron said:**
> I could try to ssh into your Ratel and see if I get the same problem.

Thanks for the offer Tom, but it probably wouldn't help.  (And it would be difficult to schedule as I am on dialup.) I think the problem is related (in part) to the old RH software.  I can ssh into the Ratel from the Pangolin and I don't have any  problems displaying the man pages, so you likely could not reproduce the problem.

WRT to your idea of ssh config files, off the top of my head I thought the only relevant file was *sshd_config*, but I may look at the package when I get the chance.  I'll post back if I get any new info.

BTW, I really like your "three sacred principles!" :p

---

### Post by blackhole54 on 2007-09-09
It always amazes me how sometimes, when you are having absolutely no luck solving a problem yourself, sometimes simply discussing it with somebody else can clear your vision some and lead to progress.  Such seems to be the case here.  Long before purchasing the Ubuntu systems, I had suspected a problem like this on yet a different system might be related to unicode, which I don't think RH7.0 handles.  But despite googling and tearing my hair out, I couldn't get my head around the problem. Now it appears the solution might be as simple as the LANG variable.

After pondering man's man page a bit more, I discovered using

```

LANG=en_US man man

```

led to a correct rendering of man's man page on the Ratel over ssh, which previously was problematic.  (*en_US* is what the RH7.0 system uses for LANG.)  A little checking showed that the Ratel always has LANG set to *en_US.UTF-8*.  The Pangolin, however, is different.  When queried locally, or when SSHing in from the Ratel, the Pangolin shows LANG set to *en_US.UTF-8*.  **But when SSHing in from the RH7.0 system, LANG on the Pangolin is unset!**.  I quick check showed that

```

LANG= man man

```

also worked when SSHing into the Ratel from the RH7.0 system.

But I can't find where LANG is either set or unset (although I have located */etc/default/locale*).

```

grep LANG /etc/profile /etc/bash.bashrc .bash_profile .bashrc
grep locale /etc/profile /etc/bash.bashrc .bash_profile .bashrc

```

both yield nothing.  Both the Ratel and Pangolin have the line

```

AcceptEnv LANG LC_*

```

in *sshd_config*, but the ssh client on the RH7.0 system is too old to have the SendEnv option.

Any ideas where LANG is getting set or unset in Ubuntu?


ADDITIONAL INFO:  I have a second installation of *edgy eft* (after shrinking original Ubuntu partition) on the Pangolin which I installed from CD.  I just installed openssh-server on it.  It exhibits the same behavior as the Ratel.  So it would seem it is the  original installation on the Pangolin that exhibits the exceptional (but useful) behavior.   I am unaware of having done anything to the Pangolin to alter this behavior.   :confused:

---

### Post by thomasaaron on 2007-09-10
It is kept in:
/etc/default/locale 

Hey, have a look at this article. Evidently, your problem is not so uncommon:
[http://jean-christophe.dubacq.fr/index.php?post/2007/05/09/Openssh-and-the-transmission-of-the-locale-setting](http://jean-christophe.dubacq.fr/index.php?post/2007/05/09/Openssh-and-the-transmission-of-the-locale-setting)

---

### Post by blackhole54 on 2007-09-11
The difference between the Ratel and the Pangolin was I had commented out the **UsePAM yes** line in *sshd_config* on the Pangolin.  It was your link that put me onto this.  (I *never* would have suspected PAM!)  Every time I've tried to figure out PAM my mind began spinning.  I probably should take anothe stab at it.

Thanks for your help.

---

