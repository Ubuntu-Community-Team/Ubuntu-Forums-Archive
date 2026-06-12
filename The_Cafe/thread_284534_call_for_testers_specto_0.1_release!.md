---
title: "call for testers: specto 0.1 release!"
date: 2006-10-25
forum: The Cafe
---

### Post by kiddo on 2006-10-25
Want bleeding edge apps hot from the oven? :D

I am hereby providing a first release for edgy users who like to try out new stuff. Be aware that I *might* update the .deb package attached if emergency calls for it, but this is basically a first "stable" release. It is currently partially translated in French, German, Romanian. Any comments/patches/problem reports are appreciated!

[IMG]http://specto.sourceforge.net/i/screenshots/2006%2009%2016.png[/IMG]

> Specto is a desktop application that will **watch user-specified events** (website updates, emails, file and folder changes...). For example, this allows you to specify a website to watch, and Specto will automatically check for updates on the web page. It will then notify the user when there is activity. This will allow the user to *be informed of new updates/events instead of having to look out for them*. This *changes the way you work*, because Specto will only notify you when something happens, and stay out of the way otherwise.
We are a volunteer project, free “as in beer” and free “as in GNU GPL v2”, and contributions are very, very, very welcome. If you like this software and want to fix annoyances that itch you, we value all the help we can get. You don't need to be a hacking guru! [(full announcement and release notes)]("http://sourceforge.net/forum/forum.php?forum_id=627204")

I'm releasing this in hope to get feedback from ubuntu testing users. Have fun :) and please **give me your comments**!

---

### Post by kiddo on 2006-10-25
Hm. Actually I realize this thread should go in another forum, maybe Ubuntu Café, could someone move it?

---

### Post by William the Conquerer on 2006-10-25
woah!!  This is exactly something that I've wanted for a while now..  I've just been too lazy to actually write anything and this looks a whole lot better anyway ;).  I'll definitely have to check this out...

---

### Post by meng on 2006-10-25
Just to confirm, this is written in python, yes?

---

### Post by RAOF on 2006-10-26
And for those of you who like your software sitting in a repository, the [misc section]("http://raof.dyndns.org/falcon/dists/edgy/misc") of my repository has the 0.1 version packaged for your enjoyment.  You'll have better luck/speed with the mirrors, too: [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org) and [http://ubuntu.moshen.de](http://ubuntu.moshen.de)

---

### Post by H.E. Pennypacker on 2006-10-26
> **meng said:**
> Just to confirm, this is written in python, yes?

Yes, it is, by python beginners (not sure if that's relevant, that they're beginners).

This is definitely one of my favorite projects.  I am keeping up with updates, although I don't use Specto at the moment.  Couldn't figure out how to use it.  But I'll use it one day.

---

### Post by mssever on 2006-10-26
Since I don't yet use Edgy, I've been trying (unsuccessfully) to produce a .deb for Dapper. The biggest hangup seems to be the dependency python-central, which conflicts with Dapper's version of debhelper. And after resolving all the dependency issues with upgrading debhelper, I'd practically wind up with Edgy anyway. (I broke pbuilder in the process of trying to upgrade debhelper. Fortunately, that's not too difficult to recover from.)

Is python-central really required? The dependency list for the source tarball on sourceforge says nothing about python-central. What do I need to do to make a Dapper deb without all those upgrades? Since the tarball doesn't use the standard "./configure && make && sudo make install" I'm out of my element.

Or, could somebody post a Dapper .deb and save me the effort? ;) I refuse to install non-deb software on my system, unless I can make a deb before installing.

---

### Post by RAOF on 2006-10-26
> **mssever said:**
> Since I don't yet use Edgy, I've been trying (unsuccessfully) to produce a .deb for Dapper. The biggest hangup seems to be the dependency python-central, which conflicts with Dapper's version of debhelper. And after resolving all the dependency issues with upgrading debhelper, I'd practically wind up with Edgy anyway. (I broke pbuilder in the process of trying to upgrade debhelper. Fortunately, that's not too difficult to recover from.)

Is python-central really required? The dependency list for the source tarball on sourceforge says nothing about python-central. What do I need to do to make a Dapper deb without all those upgrades? Since the tarball doesn't use the standard "./configure && make && sudo make install" I'm out of my element.

Or, could somebody post a Dapper .deb and save me the effort? ;) I refuse to install non-deb software on my system, unless I can make a deb before installing.

Oooh, difficult.  The python-central dependency is there to support Debian's new python policy.  You could also build it with python-support instead, but you'd need to change a bit of the packaging stuff.  Specifically, change the debian/rules line which says "pycentral" to "pysupport".  I think that should be all you need to do to get a working deb.

---

### Post by Jingo on 2006-10-26
The idea is great.

But... I need SSL for my email accounts. Created a bug on this issue, but it might actually be a feature request.

---

### Post by tseliot on 2006-10-26
> **kiddo said:**
> Hm. Actually I realize this thread should go in another forum, maybe Ubuntu Café, could someone move it?

Done

---

### Post by Shin_Gouki2501 on 2006-10-26
Hm Not too bad, what resoruces Besides Websides or forum i can define?

---

### Post by G|N| on 2006-10-26
> **Jingo said:**
> The idea is great.

But... I need SSL for my email accounts. Created a bug on this issue, but it might actually be a feature request.

fixed this in cvs! :D

---

### Post by mssever on 2006-10-26
> **RAOF said:**
> Oooh, difficult.  The python-central dependency is there to support Debian's new python policy.  You could also build it with python-support instead, but you'd need to change a bit of the packaging stuff.  Specifically, change the debian/rules line which says "pycentral" to "pysupport".  I think that should be all you need to do to get a working deb.

OK, I give up. I've managed to get a Dapper package of specto, but specto depends on python-notify, which appears to be quite difficult to package for Dapper, especially since I'll be upgrading to edgy in a couple weeks. If anyone wants my dapper package, I'll be glad to post it.

---

### Post by kiddo on 2006-10-26
> **meng said:**
> Just to confirm, this is written in python, yes?

Yeah, it is indeed written in python :)

> **mssever said:**
> OK, I give up. I've managed to get a Dapper package of specto, but specto depends on python-notify, which appears to be quite difficult to package for Dapper, especially since I'll be upgrading to edgy in a couple weeks. If anyone wants my dapper package, I'll be glad to post it.

Well, I pretty much doubt you will easily be able to package it for dapper. Anyway, as it depends on stuff that is available only in edgy, and since edgy is out today, I think it's not such a big problem; it would be difficult to support older releases in this case...

---

### Post by Shin_Gouki2501 on 2006-10-27
was my question this difficult?

What resources am i able to add for watch?

---

### Post by G|N| on 2006-10-27
> **Shin_Gouki2501 said:**
> was my question this difficult?

What resources am i able to add for watch?

these are the watches that currently work:
websites (xml-feeds, static)
emails (pop3, pop3-ssl, imap, imap-ssl, gmail)
files (folders/files)

if you have any other ideas for watches, let us know!

---

### Post by maniacmusician on 2006-10-27
bookmarked. I'll check it out after i install edgy

---

### Post by William the Conquerer on 2006-10-30
sweet sassy mollassy, this program is EXACTLY what I've been looking for =)  I've been using it for a few days now and I'm trying to remember to depend on it so I don't obsessively check every open source project, band website, and blog I can think of...  it does it for me!!!! =)  Anyway, the only gripe I have with it is that the notification really only stays for like a second and than disappears...  not really a huge problem since it changes the icon in the system tray.

---

### Post by kiddo on 2006-10-31
> **William the Conquerer said:**
> sweet sassy mollassy, this program is EXACTLY what I've been looking for =)  I've been using it for a few days now and I'm trying to remember to depend on it so I don't obsessively check every open source project, band website, and blog I can think of...  it does it for me!!!! =)  Anyway, the only gripe I have with it is that the notification really only stays for like a second and than disappears...  not really a huge problem since it changes the icon in the system tray.

:) very happy to see you like it! The notification time thing should be possible to set, I think. I [filed a bug]("https://launchpad.net/products/specto/+bug/69492") on it to remember it.

Oh, and I think that Specto [can now be translated from Rosetta]("https://launchpad.net/products/specto/+translations"): fire up your dictionaries gentlemen (hint: the word "watch" could be interpreted as "observer")

(current translated languages [here]("https://launchpad.net/products/specto/0.2/+pots/specto"))

---

### Post by jasay on 2006-11-01
Jeepers man, this is useful.  Many thanks.=D>

---

