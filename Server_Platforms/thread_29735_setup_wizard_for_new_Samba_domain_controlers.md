---
title: "setup wizard for new Samba domain controlers"
date: 2005-04-25
forum: Server Platforms
---

### Post by JGJones on 2005-04-25
I realise that in large enterprises they hire folks with uber Unix skills that deal with pure text only console (I have this picture of it being green text on black on anicent monitors!) however one feature that is sorely lacking in the Linux world is the easy method of installing a Linux server for simple domain network, with the scope to grow - ideal for the small/medium businesses that don't necessarily have any in-house IT team.

Thus we need some form of a setup wizard for creating new Samba controllers. My understanding of Samba running as a NT4 PDC is that it's not restricted by the limitations of the original NT4 domains? Especially when coupled with OpenLDAP as the backend?

After looking, this is the only one that I've found that will do setup wizard for creating domains:

IDEALX Management Console

[http://imc.sourceforge.net/dev/devplan.html](http://imc.sourceforge.net/dev/devplan.html)

It's now being worked on so not there yet.

However I'll love to hear your thoughts. I've been working on Linux faily recently have this week have started looking at setting up servers to replace Windows 2000 Active Directory on my test bed suite.

---

### Post by localzuk on 2005-04-26
It would be nice, however it does have a few problems in my mind.

First, if you are running a server, you should not need to have X running at all, as this is a security issue, and it uses up CPU, memory and hdd space.
Second, the issue of setting up a domain controller is so customisable, it would be difficult to create such scripts.

Personally, I think that if you want a reliable samba server as a pdc, it is best to not use x as a tool - in my experience, it leads to 'sloppy' work on the server (and eventually will lead to more reboots, upgrades and issues).

Spending a few hours setting up a samba server by command line is a lot better than spending a lot of time fixing issues with scripts.

PS. Have you looked at webmin/swat as a way of setting up?

---

### Post by JGJones on 2005-04-26
How about setting it up so that by default it won't start X, but if you wanted to do admin stuff, you can then run startx for the admin stuff?

I agree that security-wise it's better to have it off, but sometime GUI does make it easier, especially for file management (although you could do that remotely i suppose) or for the addition of user accounts and so on)

But having a look at webmin, that could do the above without needing X in the first place.

But for X using CPU - not really, when it's idle, it's using no CPU at all, and as for HDD's - they are so big these days that X take up a tiny portion of the pie, and likewise for memory (wouldn't it just get into swap if it's not being used much?)

Security however I can't argue with :)

But for small offices, they might appericate having a GUI to make their life easier. Windows Server use GUI for server setup etc and works well enough, and OSX Server use OpenLDAP but use GUI as well (although it's pricey!)

Linux can do that too surely - and when the admin's all done, you can then exit X and leave it in console mode?

Thanks for your comments though, I guess you are right. Meanwhile I came across SME Server which seem to set everything up using text console but use scripts to do it?

---

### Post by adeh on 2005-04-26
We just finished setting up a linux PDC for a small client (15-20 seats). We used debian testing net install (sarge). I like it because it is 1 disk, and it you are on a fast network you can do the install in 30 min.

The PDC part took a lot of time, but finally it works like a charm. All remotely through the command line. The one drawback is allowing the client to add new users on their own...

haven't figured out a good way to do it, but hey, at least it gives us a way to justify those support fees :)

this is the howto that worked best:
[http://mailman.lug.org.uk/pipermail/scarborough/2004-December/001795.html](http://mailman.lug.org.uk/pipermail/scarborough/2004-December/001795.html)


-Adeh

---

### Post by vvu on 2005-04-26
JGJones...I agree the need for a GUI base configuration tool.  I do NOT believe everything in Linux should be command line based.  I know that it is among its power; however, if we want the adoption of Linux in the Enterprise  or even SMB - we as a Linux community need to look or support these efforts - such as you pointed out with IDEALX (good one by the way).  

Windows may not be the best at everything, but they are the best when it comes to GUI Admin tools - bar none.  I am not a Linux zealot that will say Linux is the best for everything or CLI is the only way to go (which is a ridiculuous statement in itself).  I do work on Windows for a job but prefer Linux at other things.  I just hope that projects such as IDEALX flourishes.

As far as security and X/GUI - give me an example of how you can take over my machine or destroy it if I am using X.  I never had issues with Windows during my admin days at all - if there was - it was self-inflicted or stupidity - same thing can happen in Linux.

By the way, asides from commercial support of RedHat and Suse - those flourish because first time users/companies look for simplicity and low learning curve - and the Admin tools those companies provide are "good" enough for now.

Folks, you must realize that simplicity and GUI are the only way for Linux to gain more acceptance.

---

