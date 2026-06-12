---
title: "Best Distro to Learn Linux Server Administration?"
date: 2009-01-09
forum: The Cafe
---

### Post by Mason Whitaker on 2009-01-09
Hey, whats the best Linux distro to learn Linux Server Adminitration on? Or what the best linux server is?

---

### Post by BGFG on 2009-01-09
Ubuntu has a server edition. Why not start with what some tout as the most user friendly, and as you learn, move on if you feel the need ?
Should be fun... :)

---

### Post by bsharp on 2009-01-09
Slackware would be my first choice, followed by anything Red Hat based.

EDIT: Lets not forget Linux From Scratch, either.

---

### Post by Mason Whitaker on 2009-01-09
> **BGFG said:**
> Ubuntu has a server edition. Why not start with what some tout as the most user friendly, and as you learn, move on if you feel the need ?
Should be fun... :)

I was thinking about going with that, but then I'd need someone to install the regular Ubuntu GUI to it. I think I'd get bored with just a regular text based screen.

---

### Post by Bachstelze on 2009-01-09
Why do you want to learn system administration? Do you plan to make it your job, or is it just for "fun"? If you want to make it your job, go with the most used ones in corporations: Debian, RH and maybe FreeBSD. If it's just for personal knowledge, just choose what you're most comfortable with. The server programs (Apache, PHP, MySQL, BIND, etc.) are the same in all distros anyway, so it's better to go with something that won't hold you back for weeks while you'll be trying to figure out how the distro works, so you can focus on what interests you right away.

> **Mason Whitaker said:**
> I was thinking about going with that, but then I'd need someone to install the regular Ubuntu GUI to it. I think I'd get bored with just a regular text based screen.

Why not just install the server stuff on your current Ubuntu system then?

---

### Post by Mason Whitaker on 2009-01-09
> **HymnToLife said:**
> Why not just install the server stuff on your current Ubuntu system then?

Maybe a little backstory on why I'm asking this question then, eh? My Uncle works for a company called Hobsons as an Oracle Database Manager. His company is throwing out some three year old servers that were purchased for somewhere around $100,000 US at the time, but now they were buying some newer, more efficient ones. But these are still in fine working condition. 

They were going to just throw them out, but my Uncle managed to get ahold of five of them. As I told him that I want to go to college to learn Linux Server Administration, he's willing to give me one of the ones he managed to grab to me. 

Now for the time being, I'll only be doing this for fun, just to learn how to do the stuff myself before I actually take college classes in it. Now, I'll probably take your advice and just install Ubuntu to them and then install the server stuff to it when its all said and done.

Tu es Francais? Je suis Americaine :P

---

### Post by tubezninja on 2009-01-09
> **Mason Whitaker said:**
> 
Now for the time being, I'll only be doing this for fun, just to learn how to do the stuff myself before I actually take college classes in it. Now, I'll probably take your advice and just install Ubuntu to them and then install the server stuff to it when its all said and done.


I think this is a good choice.  ubuntu *is* gaining some acceptance, both in corporate and institutional environments, and is close enough to Debian that you'll gain practical experience from it.  If and when you feel the need and are ready, you can move on to CentOS or Debian.

Just be aware that eventually, you *are* going to have to do away with the GUI to really immerse yourself in server administration. :)

---

### Post by Mason Whitaker on 2009-01-09
> **scaredpoet said:**
> I think this is a good choice.  ubuntu *is* gaining some acceptance, both in corporate and institutional environments, and is close enough to Debian that you'll gain practical experience from it.  If and when you feel the need and are ready, you can move on to CentOS or Debian.

Just be aware that eventually, you *are* going to have to do away with the GUI to really immerse yourself in server administration. :)

Yeah, but good thing I still have three computers besides the server :P

Thanks everyone, for the comments

---

### Post by Twitch6000 on 2009-01-09
Debain Server Or Cent OS Server is probably the best servers.

For a paid for server however, RedHat is great.

---

### Post by Mason Whitaker on 2009-01-09
> **Twitch6000 said:**
> For a paid for server however, RedHat is great.Not really doing anything large scale that would require Redhat :)
Just the four computers in my house that me and my family use. 

Still, I'm kinda leaning more towards either Debian or Fedora over Ubuntu.

---

### Post by bryonak on 2009-01-09
Debian is the best choice I'd think.

Ubuntu doesn't give you the "real deal" (sudo on a server!? sure, but then you won't learn how the vast majority of servers out there does it).

Fedora is a good testing/desktop distro, not really for servers.
RHEL (RedHat) is about advisable as Debian for learning purposes, but I strongly recommend APT over RPM based systems.

Suse.. well Suse isn't the favourite child of the community (the server system, not OpenSuse), so I won't comment much on that. I won't endorse it either.

The rest... offspring, all of them ;D (ok, LFS maybe not)

---

### Post by Bachstelze on 2009-01-09
> **bryonak said:**
> 
Ubuntu doesn't give you the "real deal" (sudo on a server!? sure, but then you won't learn how the vast majority of servers out there does it).

Indeed, using sudo instead of su makes a HUGE difference! :shock:

(And I shall add that sudo is maintained by an OpenBSD developer. Definitely not a server OS...)

---

### Post by bryonak on 2009-01-10
> **HymnToLife said:**
> Indeed, using sudo instead of su makes a HUGE difference!

This statement is correct (and skillfully taken out of context by myself ;P)

Not that much of a a difference, but it is nevertheless...
It's about habits, about the way you maintain the system (ok cron is the same for both) and think about interacting with the network or your partitioning scheme (boot and var each on a separate partition is trivial, and the like).
We're talking mission critical*** server/network administration here, not desktop use (where "sudo vs root" is just a formality).
With all these tasks, you are either used to running them as a normal user with a root abstraction (sudo) or as root. It often comes down to differences within your maintenance scripts (echo | tee...).

Many sysadmins (still) claim sudo to be a huge security risk, though that can be mitigated by not allowing shell accounts for sudoers and changing to a sudoer after SSH'ing into the machine.
And there's still good old *sudo -s*, but then sudo becomes superfluous.

Besides, sudo is just the most prominent example. (Though Ubuntu server does a good job of keeping the good bits and improving where it should... there aren't that many differences after all.)

Bottom line: nothing wrong with sudo (or Ubuntu server), but my personal recommendation is to start learning Debian.

Cheers



*** right now he's learning, but if he want's to study server administration, he'll probably want use his skills in a production environment later. It's advisable to choose what is used by most systems.

---

### Post by Frak on 2009-01-10
CentOS, Debian, FreeBSD, SLED, Ubuntu, or RedHat.

---

### Post by Bachstelze on 2009-01-10
> **bryonak said:**
> 
Many sysadmins (still) claim sudo to be a huge security risk,

Sources? And you have omitted the second part of my message: sudo is maintained by an OpenBSD developer. Those people don't exactly have a reputation for developing tools that are "huge security risks".

The only security risks sudo is vulnerable to are PEBKACs (i.e. a sysadmin using sudo without doing his homework). Of course, any sudoer account should be considered equivalent to root in terms of security, but it is not sudo's fault if some people using it have no common sense.

---

### Post by cardinals_fan on 2009-01-10
> **HymnToLife said:**
> Indeed, using sudo instead of su makes a HUGE difference! :shock:

(And I shall add that sudo is maintained by an OpenBSD developer. Definitely not a server OS...)
This is only a big deal if the timeout is left at a nonzero value.

@OP: It depends on what your goals are.  If you want to work in the field, I would strongly recommend CentOS (a free clone of RHEL), because Red Hat is a very common platform.  Otherwise, I would use NetBSD, FreeBSD, or Slackware.

---

### Post by Bachstelze on 2009-01-10
> **cardinals_fan said:**
> This is only a big deal if the timeout is left at a nonzero value.

This was ironical. ;) I consider both approaches to be perfectly equivalent in terms of security. Choosing one or the other is really just a matter of personal preference.

---

### Post by cardinals_fan on 2009-01-10
> **HymnToLife said:**
> This was ironical. ;) I consider both approaches to be perfectly equivalent in terms of security. Choosing one or the other is really just a matter of personal preference.
I know it was sarcastic.  However, I would argue that sudo with a nonzero timeout can be a fairly significant risk.

---

### Post by toupeiro on 2009-01-10
> **HymnToLife said:**
> Indeed, using sudo instead of su makes a HUGE difference! :shock:

(And I shall add that sudo is maintained by an OpenBSD developer. Definitely not a server OS...)

Not sure I am following your logic here.  I use sudo on many shared servers to delegate elevated rights to users or groups of users.  I use it in Redhat, Solaris, and SGI alike.


If you need a root prompt, ever thought to do "sudo su -" ?

The way I see it, this keeps the root account indefinitely encrypted or at least very tightly controlled. So, you create another local account for maintenance which you can grant access to sudo into root.  All you really need to do is get good with a sudoers file. Once you do, you will see how nice sudo is.  By default, ubuntu distros keep it pretty open.  Also, this does not prevent you from having single user mode root access. From a security standpoint, its really a hell of a lot better than su by itself.

---

### Post by bryonak on 2009-01-10
> **HymnToLife said:**
> > Originally Posted by bryonak
Many sysadmins (still) claim sudo to be a huge security risk,
Sources?
I thought the *(still)* in there is enough implication that I don't share this view, though maybe that was too subtle. Nevermind, I've read it quite a few times.
Where? Hey, where would we be if everyone had to back up their claims with actual facts instead of.. oh wait, this isn't Slashdot ;)
I can't reproduce the exact links from memory, but [Google helps out]("http://www.google.com/search?hl=en&q=sudo+security+risk").


> **HymnToLife said:**
> 
And you have omitted the second part of my message
I did that on purpose, for obvious argumentative reasons :P

The thing is that many of learners don't have the kind of common sense an experienced sysadmin would consider normal. I refer to those who have to do their homework yet, because lots of it isn't that intuitive...

My recommendation for Debian still stands, because of the reasons I've given (closer familiarity with the majority of systems, but let's not repeat).

Hmm, I haven't got much left to say on topic, so I guess we should write the opinions that don't contribute to the thread via PM.


> **toupeiro said:**
> 
If you need a root prompt, ever thought to do "sudo su -" ?

*sudo su* will get you lynched by purist zealots. To avoid this, use *sudo -s*.

---

### Post by Mason Whitaker on 2009-01-10
I'll probably switch distros over time to learn the differences in all of them, but from what I've seen I may go ahead and get RHEL, which seems to be the industry standard.

---

### Post by gnomeuser on 2009-01-10
If you want a solid server platform, RHEL. There's years of expertise, the best security trackrecord in the business, world class certification. Award winning support solutions. The platform also does virtulization very well through oVirt, they have a lot of very interesting server technology going.

If you want a home server to play with that does the same as RHEL, CentOS, it's a recompile of RHEL without the branding and naturally only community support. Fedora and RPMFusion provides additional packages for both to make it more full featured.

Novell's SLES platform is also very nice, but more geared towards complete management of every device in your business. I wouldn't hestitate to recommend them though for those needing that.

Now you could also slap a system on there you are comfortable with, managing things like samba is pretty much the same regardless of the platform so you can learn in an environment you know. This is what I would recommend for starters, however if the idea is to prepare for work in the field the way forward is learning the traits needed to become a RHCE. Here you definitely want to learn CentOS since paying for RHEL is cost prohibitive and the skills nearly directly translate over.

---

### Post by Simian Man on 2009-01-10
I would recommend CentOS.

Red Hat is *the* biggest server used in industry (at least in the US) and if you ever want to make money as a Linux sys admin, you should go for the Red Hat Certified Engineer certification.

Since you are just learning, I'd not recommend spending money on Red Hat, so CentOS is the best choice.

---

### Post by Bachstelze on 2009-01-10
> **bryonak said:**
> 
*sudo su* will get you lynched by purist zealots. To avoid this, use *sudo -s*.

[font="monospace"]sudo -s[/font] is even worse than [font="monospace"]sudo su[/font], and for a purely technical reason that has nothing to do with zealotry:

```
firas@iori ~ % sudo -s
iori ~ # echo $HOME
/home/firas
```

For a root shell, always use [font="monospace"]sudo -i[/font] or [font="monospace"]sudo su -[/font].

By the way, I do agree with you that Debian makes a better server than Ubuntu, it just has nothing to do with sudo.

---

### Post by t3tech on 2009-01-10
Personally, I'd say Slackware, but that's what I primarily use and have for several years. However, when I hosted my own domain I used Engarde. CentOS seems to be pretty popular for web servers and I understand has decent GUI tools, though I'm not all that familiar with it specifically and have only done anything on CentOS boxes the old fashioned way - ssh and a command line. 

On Slack, the base configuration files are not obscured by other config files. The one thing that always annoyed me about RedHat - config files in different places and if you edit one manually then make a change using one of the RedHat utilities your manual changes disappeared. It's been a while since I've been on a RedHat box so I don't know if that is still an issue.

I still think Slackware fits the bill for if the goal is lean, mean, stable, and simple. Plus an install process that can allow the admin to select just those packages that need to be there.

---

### Post by albinootje on 2009-01-10
> **Mason Whitaker said:**
> Hey, whats the best Linux distro to learn Linux Server Adminitration on? Or what the best linux server is?

From your posting and your comments is only clear that you want to learn Linux Server Administration (Or perhaps I missed something in your comments).
But what do you want with that in the future ?
Just for fun, and/or for a home network ? 
Or to get some Linux sysadmin job later ?

If it's about a job, then try both Debian and Ubuntu versus CentOS.

CentOS is the free of charge alternative for RedHat Linux Enterprise.
CentOS basically takes the source code from RHLE and replaces the word RedHat by CentOS, and the RH logos by CentOS logos.

If it's not for a job, then go for Debian and/or Ubuntu.

About your remark about the text mode possibly being boring.
If I were your manager I would make sure that you know your way around on the command line, at *least* for remote system administration, instead of being/becoming dependent on a GUI for server system administration.

---

### Post by Mason Whitaker on 2009-01-11
I'm pretty handy with the command line already, its just that for now, I'll need one.

---

### Post by binbash on 2009-01-11
debian and centos

---

### Post by jonabyte on 2009-01-11
to learn it...Slackware hands down.

best server distro...there are too many to decide.

---

