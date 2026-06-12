---
title: "Ubuntu, AppCenter and Packagekit."
date: 2009-09-16
forum: The Cafe
---

### Post by Slug71 on 2009-09-16
So.. I filed a bug requesting that Ubuntu Software Store(AppCenter) be based on/use Packagekit instead of what it is now.
Replace gnome-packagekit basically.

Bug #423718.

Received this reply from Michael Vogt:

> Thanks for your bugreport.
We would love to use packagekit, but it does not support debconf or conffile prompting. We attempted to contribute those missing features and unfortunately they were not accepted on the ground that a packagekit transaction can not be interrupted (for something like debconf or conffile handling). This is a important feature for us and without it, e.g. sun-java packages do not install.

I then went to the Packagekit Mailing List and asked if this feature is at all possible and may be available in a future release.

Got this response from Richard Hughes:

> That isn't true at all. Nobody from Ubuntu tried to contribute the missing functionality, but quite a few people insisted I wrote code to connect a VTE widget to the transaction which is very different to what actually needs to be done.
Transactions can already be stopped and re-started with different options (see [http://www.packagekit.org/gtk-doc/introduction-ideas-transactions.html#introduction-ideas-transactions-sig-install](http://www.packagekit.org/gtk-doc/introduction-ideas-transactions.html#introduction-ideas-transactions-sig-install) for how all this works) and questions can be put to the user. We already do that for EULAs, GPG keys and extended authentication prompts. We already use the EULA prompts in SUSE, and GPG prompts in Fedora. I'm just not letting a random script ask the user random non-localised questions. I am happy to add any number of abstract questions, as long as they are written in a nice way that other distributions can use.

Sure, it just needs someone from Ubuntu to contribute the code. I guess it's harder contributing to a shared project than just writing _yet_another_ frontend to apt, but I guess that's the Ubuntu way. I don't want to seem like I'm bashing Ubuntu, as I think it's a great product, just the transparency and upstream ethos still needs quite a lot of work. In a few years time I hope you guys will realize that trying to be the one upstream source for all of the Linux desktop is impossible, and then hopefully will start working with other distributions in public. For what it's worth, Sebastian Heinlein has been doing a great job supporting the apt backend for PackageKit, but the reception PackageKit is getting in Ubuntu (especially for the integration points) is distinctly lukewarm.
We need someone interested in this to actually write some code, rather than just decide it's "too hard" and run away and write more code that will be obsolete (in my opinion) in a few years anyway. If anyone actually wants to implement this, I've written quite a lot about it on the mailing lists, or I would happy to discuss things in person, on a conf call, or even on IRC.
Thanks,
Richard.

Ive been getting a lot of emails from the mailing list where this is in hot discussion now and things seem to be positive. 
Richard is willing to address these issues and those of Debian to make Packagekit more suitable.

Seems the ball is back in Canonicals court now.

---

### Post by Podex on 2009-09-17
On which mailing list is this discussion? I'm pretty interested in the results of it and generally love reading heated debates :)

---

### Post by keiichidono on 2009-09-17
Hughes is right, Ubuntu may "just work" but they (Canonical) snuff out upstream and make Ubuntu specific apps as if they ARE upstream. That's WAY uncool. Ubuntu Software Store anyone?

---

### Post by Slug71 on 2009-09-17
> **Podex said:**
> On which mailing list is this discussion? I'm pretty interested in the results of it and generally love reading heated debates :)

On the Packagekit mailing list.

[http://lists.freedesktop.org/mailman/listinfo/packagekit](http://lists.freedesktop.org/mailman/listinfo/packagekit)

---

### Post by Slug71 on 2009-09-17
> **CalvinB said:**
> Hughes is right, Ubuntu may "just work" but they (Canonical) snuff out upstream and make Ubuntu specific apps as if they ARE upstream. That's WAY uncool. Ubuntu Software Store anyone?


Seems this way more and more. :(

---

### Post by RiceMonster on 2009-09-17
> **CalvinB said:**
> Hughes is right, Ubuntu may "just work" but they (Canonical) snuff out upstream and make Ubuntu specific apps as if they ARE upstream. That's WAY uncool. Ubuntu Software Store anyone?

I agree. They should develop more upstream like Red Hat.

---

### Post by juancarlospaco on 2009-09-17
Read Ubuntu 10.10 RoadMap!, PackageKits have nothing to do with it.

Ubuntu Software Store in example is being able to SELL your gpl software directly from YOUR ppa.

:)

---

### Post by Bodsda on 2009-09-17
I love this. The community scream 'Ubuntu' when things are good, but when things are bad they scream 'Canonical'.

We have plenty of programmers in the community who are not part of Canonical. Why not ask the guys in Programming talk and get hold of the MOTU team and see if the 'Ubuntu Community' can help out? If Canonical see that the community is making a huge effort to make a constructive upstream change then they are much more likely to help out.

---

### Post by zekopeko on 2009-09-17
> **CalvinB said:**
> Hughes is right, Ubuntu may "just work" but they (Canonical) snuff out upstream and make Ubuntu specific apps as if they ARE upstream. That's WAY uncool. Ubuntu Software Store anyone?

OK dude let's do this properly.

[IMG]http://static.houseofnintendo.com/houseofnintendo.com/imgname--nintendo_fanboy_internets_misunderstand_sonys_kaz_hirai---50226711--picard-no-facepalm.jpg[/IMG]

After this read what upstream is here: [http://en.wikipedia.org/wiki/Upstream_(software_development](http://en.wikipedia.org/wiki/Upstream_(software_development))

After that ask yourself if developing a FLOSS application for your needs makes you the upstream.

---

### Post by keiichidono on 2009-09-17
> **Bodsda said:**
> I love this. The community scream 'Ubuntu' when things are good, but when things are bad they scream 'Canonical'.

We have plenty of programmers in the community who are not part of Canonical. Why not ask the guys in Programming talk and get hold of the MOTU team and see if the 'Ubuntu Community' can help out? If Canonical see that the community is making a huge effort to make a constructive upstream change then they are much more likely to help out.
You're absolutely right. Revision: Hughes is right, Ubuntu may "just work" but they (Ubuntu Developers) snuff out upstream and make Ubuntu specific apps as if they ARE upstream. That's WAY uncool. Ubuntu Software Store anyone?
> **zekopeko said:**
> OK dude let's do this properly.

[IMG]http://static.houseofnintendo.com/houseofnintendo.com/imgname--nintendo_fanboy_internets_misunderstand_sonys_kaz_hirai---50226711--picard-no-facepalm.jpg[/IMG]

After this read what upstream is here: [http://en.wikipedia.org/wiki/Upstream_(software_development](http://en.wikipedia.org/wiki/Upstream_(software_development))

After that ask yourself if developing a FLOSS application for your needs makes you the upstream.

I don't really get the point you're trying to make. Applications like Shutter (screenshot tool) are upstream, distributions like Arch Linux are downstream. How would Fedora or Linux Mint users like using "Ubuntu Software Store"?

---

### Post by Slug71 on 2009-09-17
We have a response from Michael Vogt to Richard Hughes.

> My understanding of your position has been that you will not support a mechanism like debconf. Debconf provides localized questions and a abstract UI based on a simple protocol. Its used to ask basic configuration question before (and sometimes during) install. It supports gnome and qt frontends. The Debian world (that includes Ubuntu) quite likes debconf.  

I still stand to what I wrote above. I would love to use PK as the backend for the software-store project. I think its great to have a single tool for all distros. But I also want to ensure that it works on all valid deb packages. That includes debconf questions and configuration file prompts (another area that seems to be problematic, but its less important as there is some work being done to map that do debconf). The reason why its useful to ask configuration file changes prompts during the install is that when a daemon restarts, it makes sense to restart them with the new config (if the users wants that). In the aptdaemon project (that was written by Sebastian and draws alot of inspiration from PK) deconf support is integrated. I'm absolutely willing to work on adding that to PK if there is a chance of this getting accepted. Even if its just a deb-systems-only option. 

This has been discussed in the past and you expressed that you do not want any sort of interaction during a transaction as a policy decision. Its documented:[http://www.packagekit.org/pk-faq.html#hughsies-law](http://www.packagekit.org/pk-faq.html#hughsies-law)  This does not map well to the deb package world. Of course your reasons are valid, in 99% of the cases it is not needed and the enduser does not care. But we do want to cover 100% of the packages, especially since the goal is to cover updates (that can be any packages and not just applications) and generic packages as well. Most users won't ever see a debconf dialog, but if the packages requiresit, then it should be there.

This is because of the points mentioned above. It can be debatted ifthe deb format should change and/or if debconf is a good idea or not. But if we want to provide a way to install every valid debpackage (including the packages that require debconf) now, then PK is not a option (and that is unfortunate).

I do not think the reason is "its too hard". Its about the PK policy being incompatible with the Debian/Ubuntu policy. 

If there is a chance that debconf support would be accepted I would certainly be interessted in working on this.  
Cheers,Michael

---

### Post by keiichidono on 2009-09-17
So what now? I'm confused. He didn't deny not contributing but he does seem to have a valid reason.

---

### Post by Slug71 on 2009-09-18
> **CalvinB said:**
> So what now? I'm confused. He didn't deny not contributing but he does seem to have a valid reason.


Yep, almost seems the ball is back in PK's court now. I really hope this comes to fruition.

---

### Post by mpt on 2009-09-18
> **CalvinB said:**
> I don't really get the point you're trying to make. Applications like Shutter (screenshot tool) are upstream, distributions like Arch Linux are downstream.

The point is that when you say “they (Canonical) snuff out upstream and make Ubuntu specific apps as if they ARE upstream”, it demonstrates that you are seriously, seriously mistaken about what “upstream” means.

If Ubuntu developers are developing software from scratch, then those Ubuntu developers are, by definition, the upstream developers for that software. Ubuntu developers are the upstream developers for Ubiquity, for Upstart, for Notify OSD, for xsplash, and for the Ubuntu Software Store.

In almost all these cases, by the way, it is Ubuntu developers in general doing the development, not Canonical developers in particular. For example, the Store has had many bug-fixes from contributors outside Canonical, the main developer of Aptdaemon does not work for Canonical, and [you’re welcome to help out yourself]("https://wiki.ubuntu.com/SoftwareStore#How%20you%20can%20help").

> *How would Fedora or Linux Mint users like using "Ubuntu Software Store"?*

Fedora could not use it, just like Windows or Mac OS X couldn’t, because it is for .deb-based operating systems. Mint could use it, though, because it is .deb-based. It would need a bit of work to abstract out the Ubuntu-specific elements (such as the special treatment of the ubuntu-desktop metapackage), but that shouldn’t be difficult.

> **RiceMonster said:**
> I agree. They should develop more upstream like Red Hat.

Be happy, then, because the Store is an example of Ubuntu developers doing upstream development. You can criticize us for not doing enough. You can criticize us for doing too much. But please, please, for the love of all that is holy, don’t criticize us for both at the same time.

---

### Post by Slug71 on 2009-09-18
Talks are proceding very well in the mailing list between Michael and Richard and as of right now i would say it is possible we may have PK as the backend to Ubuntu Software Store after Karmic. :)

---

### Post by Swarms on 2009-09-18
> **Slug71 said:**
> Talks are proceding very well in the mailing list between Michael and Richard and as of right now i would say it is possible we may have PK as the backend to Ubuntu Software Store after Karmic. :)

Oh that sounds very interesting!

---

### Post by keiichidono on 2009-09-18
> **mpt said:**
> The point is that when you say “they (Canonical) snuff out upstream and make Ubuntu specific apps as if they ARE upstream”, it demonstrates that you are seriously, seriously mistaken about what “upstream” means.

If Ubuntu developers are developing software from scratch, then those Ubuntu developers are, by definition, the upstream developers for that software. Ubuntu developers are the upstream developers for Ubiquity, for Upstart, for Notify OSD, for xsplash, and for the Ubuntu Software Store.

In almost all these cases, by the way, it is Ubuntu developers in general doing the development, not Canonical developers in particular. For example, the Store has had many bug-fixes from contributors outside Canonical, the main developer of Aptdaemon does not work for Canonical, and [you’re welcome to help out yourself]("https://wiki.ubuntu.com/SoftwareStore#How%20you%20can%20help").



Fedora could not use it, just like Windows or Mac OS X couldn’t, because it is for .deb-based operating systems. Mint could use it, though, because it is .deb-based. It would need a bit of work to abstract out the Ubuntu-specific elements (such as the special treatment of the ubuntu-desktop metapackage), but that shouldn’t be difficult.



Be happy, then, because the Store is an example of Ubuntu developers doing upstream development. You can criticize us for not doing enough. You can criticize us for doing too much. But please, please, for the love of all that is holy, don’t criticize us for both at the same time.

Well i can't argue with that. And even Linux Mint does it with mintools.

---

### Post by Slug71 on 2009-09-27
From Sebastian Heinlein:

> Hello,
 
I have made up this plan to integrate debconf and conf file conflicts
into PackageKit. These issues will be handled during a running
transaction which will paused while waiting for an answer from the
user - new transaction will be blocked so long. To avoid an endless 
block the caller-active property and a time out will be used.
 
Config file conflicts and debconf have to be dealt during the running
transaction, since we have to make sure that daemons start with the
correct configuration and maintainer scripts cannot be safely
suspended or killed.
 
Conflict file handling:
 
If the backend recognizes a conf file conflict, pauses the transaction
and reports this to the packagekit daemon. The daemon checks if the
caller is still active. If so it sends a ConfigFileConlift signal with
the old and new file as attributes. The user would call a
ResolveConfigFileConflict method with the new file or possible
predefined values like "keep" or "replace". The daemon sends the
answer to the backend.
If the caller is no longer available on the bus the daemon will report
this to the backend, which will choose a default action.
 
Debconf:
 
Would be basically the same as for config file conflicts. We could
use the proxy debconf frontend. This allows to communicate with
debconf using a socket. The backend would listen on the socket and
behave like a normal debconf frontend. A configuration question would
be send to the backend and from the daemon to the user using a signal.
The signal would need some further thinking since there are different
kind of possible questions e.g. yes/no, lists. See above for answer and 
caller-active handling.
 
A further issue is the communication with the backend. Currently we
cannot access the caller-active property from a spawned backend.
Should we send this information to the backend or limit this advanced
features to native backends?
 
Cheers,
 
Sebastian

---

### Post by Slug71 on 2009-09-27
Response from Richard Hughes:

> 2009/9/24 Sebastian Heinlein <sebi@glatzor.de>:
> I have made up this plan to integrate debconf and conf file conflicts
> into PackageKit. These issues will be handled during a running
> transaction which will paused while waiting for an answer from the
> user - new transaction will be blocked so long. To avoid an endless
> block the caller-active property and a time out will be used.
 
If that's what we have to do, that's what we have to do. I can't say I
like it, but if we can run things un-attended, ten it doesn't break
too many of the use cases.
 
> If the backend recognizes a conf file conflict, pauses the transaction
> and reports this to the packagekit daemon. The daemon checks if the
> caller is still active. If so it sends a ConfigFileConlift signal with
> the old and new file as attributes. The user would call a
> ResolveConfigFileConflict method with the new file or possible
> predefined values like "keep" or "replace". The daemon sends the
> answer to the backend.
 
Sounds sane.
 
> If the caller is no longer available on the bus the daemon will report
> this to the backend, which will choose a default action.
 
Doesn't the backend know if the caller is active or not?
 
> Would be basically the same as for config file conflicts. We could
> use the proxy debconf frontend. This allows to communicate with
> debconf using a socket. The backend would listen on the socket and
> behave like a normal debconf frontend. A configuration question would
> be send to the backend and from the daemon to the user using a signal.
> The signal would need some further thinking since there are different
> kind of possible questions e.g. yes/no, lists. See above for answer and
> caller-active handling.
 
Right.
 
> A further issue is the communication with the backend. Currently we
> cannot access the caller-active property from a spawned backend.
> Should we send this information to the backend or limit this advanced
> features to native backends?
 
There's no reason why we can't proxy this, the problem is that
typically we set the data as environment variables (NETWORK etc) which
don't change during the transaction. I'm not sure if you can change an
running process' environment. Other ways to contact the running
instance is just to dump more stuff to stdin, but if it's like the yum
backend it's blocking whilst it's running to command.
 
Either way, I think it's best if the backend itself knows if the
caller is active or not.
 
Richard.
 
p.s. Thanks for working on this.

---

### Post by NormanFLinux on 2009-09-27
I got rid of Packagekit after I upgraded Kubuntu Netbook Edition. I replaced it with Synaptic. Its my favorite package manager in two
distros.

---

### Post by Slug71 on 2009-10-22
[http://dantti.wordpress.com/2009/10/14/packagekit-and-the-road-to-debian/](http://dantti.wordpress.com/2009/10/14/packagekit-and-the-road-to-debian/)

---

### Post by Sand Lee on 2009-10-25
Hey Slug71, good work on starting a productive dialogue between the Pk-devs and the SoftwareCenter guys. Being a liaison between software projects is a great idea!

---

