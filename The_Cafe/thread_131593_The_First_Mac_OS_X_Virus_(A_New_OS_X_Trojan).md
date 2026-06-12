---
title: "The First Mac OS X Virus? (A New OS X Trojan)"
date: 2006-02-16
forum: The Cafe
---

### Post by Derek Djons on 2006-02-16
I don't have to spend words on this. Check this post on MacRumors: [http://www.macrumors.com/pages/2006/02/20060216005401.shtml](http://www.macrumors.com/pages/2006/02/20060216005401.shtml)

We all know what this means for Unix / Linux.

**Update:** Check this link for further heads up: [http://www.ambrosiasw.com/forums/index.php?showtopic=102379](http://www.ambrosiasw.com/forums/index.php?showtopic=102379)

---

### Post by Bandit on 2006-02-16
Another great reason not to run as root.

---

### Post by endersshadow on 2006-02-16
*nix viruses are nothing new...and this is certainly not the first Mac virus.  For some reason, people think this is the case...

---

### Post by Sirin on 2006-02-16
> The resultant file decompresses into what appears to be a standard JPEG icon in Mac OS X but is actually a compiled Unix executable in disguise.

It's a UNIX executable, and native UNIX apps can run on UNIX-Based OSes, and Linux is based on UNIX, so that means that LINUX IS ALSO AT RISK. ;)

EDIT: This is for the people that think "OH, A MAC VIRUSE? HAHA! I WONT GET INFECKTED BCUZ I RUN LINUCKS!"

---

### Post by endersshadow on 2006-02-16
Note that it's only for PowerPC architectures, though, and calls *only* Mac programs.  While it's a Unix executable, it's functions are Mac and PowerPC based only.

[http://www.ambrosiasw.com/forums/index.php?showtopic=102379](http://www.ambrosiasw.com/forums/index.php?showtopic=102379)

---

### Post by Qrk on 2006-02-16
Wouldn't you need to give it executable permissions on linux? From the description it seems like Mac had already given it permission.

---

### Post by mstlyevil on 2006-02-16
I have had many debates with Mac fanboys that OSX is not completely immune from exploits. They spread this myth that some how Apple figured out a way to make a Unix based OS impenetrable like it was the gospel truth. In the near future this kind of attitude by most Mac users is going to lead to many of their PC's being infected with something pretty nasty. Many Linux users are no better considering the number of them that run as root and refuse to take basic security measures like a firewall and passwording the bios.

---

### Post by aysiu on 2006-02-16
[QUOTE=Qrk]Wouldn't you need to give it executable permissions on linux? From the description it seems like Mac had already given it permission.[/QUOTE] Mac, like Ubuntu, uses *sudo*. When you install software, you have to give your user password first.

I think Mac may allow you to modify more files, though, without *sudo* privileges. In Ubuntu, you get your /home directory, and that's about it.

---

### Post by BoyOfDestiny on 2006-02-16
It seriously depends on the user and habits. If you are logged in as root all the time, decide to download debs from mysterious websites (people do that with exe's now, that's why some folk get bittorrent packaged with ads), you'll have a wonderfully compromised machine. I will avoid a car metaphor, let's say a safe. A safe so fantastic that houdini would blush... Now if you have a user that's leaves it unlocked, or periodically puts dynamite in it...  Guess what happens?

For apps that I've been building from cvs or source, since checkinstall is broken in dapper, I haven't bothered running make install... just make... So I open the files associated with it by pointing straight there, and makes it easy when I update the software...(Anyway I trust these apps: zsnes, advmame, advmenu, uade, mednafen, etc... Gotta love the GPL).

Anyway, make backups, say your prayers, etc. A false sense of security is worse than no security.

---

### Post by BoyOfDestiny on 2006-02-16
[QUOTE=Sirin]It's a UNIX executable, and native UNIX apps can run on UNIX-Based OSes, and Linux is based on UNIX, so that means that LINUX IS ALSO AT RISK. ;)

EDIT: This is for the people that think "OH, A MAC VIRUSE? HAHA! I WONT GET INFECKTED BCUZ I RUN LINUCKS!"[/QUOTE]

Well, Linux isn't technically UNIX based... It tries to follow posix... So I guess it is unix-like. In ubuntu if I have a file of one extension that is actually another, Ubuntu warns me (something like "this file is of type mpeg, but it is really asf and may not be safe to execute") 

I don't want to test this "trojan", but does anyone know if Ubuntu would allow this to execute, especially if it's needs root? I've noticed unless something has gksudo (or whatever), double clicking on something that needs root to work... Does nothing, no prompt, nada. I guess it could just "harm" home...

Lastly, this is the second mac osx "trojan" I'd heard of.  [http://arstechnica.com/news/posts/1081455881.html](http://arstechnica.com/news/posts/1081455881.html)
It's from 2 years ago, so arstechnia didn't change their "rebel" color scheme yet. :)

---

### Post by Sirin on 2006-02-16
This crap can always be reduced by running as a normal user instead of root. As with Windows XP, you should always run as a Limited account, and leave the Administrator account type for doing administrative things (ex. Installins software, making system changes, etc.).

---

### Post by mstlyevil on 2006-02-16
[QUOTE=Sirin]This crap can always be reduced by running as a normal user instead of root. As with Windows XP, you should always run as a Limited account, and leave the Administrator account type for doing administrative things (ex. Installins software, making system changes, etc.).[/QUOTE]

Or better yet just run Linux as a normal user and use the XP cd as a drink coaster. :mrgreen:

---

### Post by Qrk on 2006-02-17
[QUOTE=mstlyevil]Or better yet just run Linux as a normal user and use the XP cd as a drink coaster. :mrgreen:[/QUOTE]

When I did that I got the flu!

---

### Post by Derek Djons on 2006-02-17
Some time ago I read an article about computer security in the year 2006. The article stated that virus / malware writers are going to use other methods than traditional in order to succeed in their goal.

I think with Mac OS X and maybe Linux in the future vunerability exploits will be used from freshly new developed software. This example is still a trojan / virus which has to be downloaded and executed before it goes harmful.

But I indeed agree with Ubuntu members stating that Mac OS X (and Linux) users can't sit and be ignorant now. The security meassures both groups have to take are infact very minimum and can be easily thought if Apple / Linux community spend some quality time on it.

---

### Post by 3rdalbum on 2006-02-17
> It doesn't actually do anything other than attempt to propagate itself via iChat

It's highly unlikely that anyone would send you a copy through e-mail, or that anyone would try to get you to download it. As the only way it reproduces is through iChat, Linux is pretty much safe from this one.

Don't be too hard on Mac users for thinking that OS X is invulnerable - Linux users think that all the time. Even me, sometimes.

---

