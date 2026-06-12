---
title: "Firefox 1.0.4 security fixes and Hoary"
date: 2005-07-24
forum: Server Platforms
---

### Post by jozjan on 2005-07-24
I wonder why official Hoary repositories still have just the 1.0.4 version of Firefox. 
Firefox 1.0.4 contains some bugs, and there are also exploit on the web for these bugs ([http://www.frsirt.com/exploits/20050712.mfsa2005-55exploit.php](http://www.frsirt.com/exploits/20050712.mfsa2005-55exploit.php) ,...)
Please upload the new version of Firefox (1.0.6) into official repositories. Or linux users could be hacked so easily as like Windows users can if they don't use Microsoft Updates.

root@jozjan:/home/jozjan # apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@jozjan:/home/jozjan # mozilla-firefox --version
Mozilla Firefox 1.0.4, Copyright (c) 1998 - 2005 mozilla.org

---

### Post by AgenT on 2005-07-24
[QUOTE=jozjan]I wonder why official Hoary repositories still have just the 1.0.4 version of Firefox. 
Firefox 1.0.4 contains some bugs, and there are also exploit on the web for these bugs ([http://www.frsirt.com/exploits/20050712.mfsa2005-55exploit.php]("http://www.frsirt.com/exploits/20050712.mfsa2005-55exploit.php") ,...)
Please upload the new version of Firefox (1.0.6) into official repositories. [/QUOTE]

This is because you do not understand how patching and upgrades work. The current official Firefox (1.0.2) in Ubuntu has all the patches and fixes that the newest Firefox has. The reason for not having it upgraded is simple and complex at the same time - the simple version is given: newer versions of software tend to break things and, because Ubuntu has a promise of not breaking things, they do not upgrade to newer version but instead only patch them with security fixes. This is how real security updates in operating systems work.

There is, however, the backports project (see this forum, it has a whole section). The backports project allows you to upgrade your programs to newer versions. Do note that 1.0.6 introduces a lot of problems with certain feature (this does not seem to be Ubuntu's fault, however).

Also, search before asking. Searching for "firefox 1.0.6" brings up a lot of threads that more than answer your question. Being too lazy to search and asking others to do the work for you is just rude.

> Or linux users could be hacked so easily as like Windows users can if they don't use Microsoft Updates Your claims are *way* over stated. But that is not relevent to your question about Firefox.

---

### Post by sprucio on 2005-07-24
Quick question: once the software is patched to fix the security issues, how can we keep track of this event taking place?

I suppose the next time you run apt-get update && apt-get dist-upgrade will show firefox updating but is there a web log of this?

---

### Post by brim4brim on 2005-07-24
I personally just install firefox from their website as the installer is very easy to use.  I install it in a directory where I know where it is if I need to delete it at a later time.  It uses a completely graphical installer so you don't need the comand line.

---

### Post by AgenT on 2005-07-24
[QUOTE=sprucio]Quick question: once the software is patched to fix the security issues, how can we keep track of this event taking place?

I suppose the next time you run apt-get update && apt-get dist-upgrade will show firefox updating but is there a web log of this?[/QUOTE]

Not sure what you mean by keeping track by events, but just so you know, apt-get dist-upgrade is probably not what you want. You probably want apt-get upgrade (two different things). Unless you are using other repositories like backports, you probably want to use apt-get upgrade. To quickly summerize: upgrade upgrades your current installation while dist-upgrade upgrades the whole distribution which can equal to adding or deleting packages/programs. See the man page for apt-get for more information. In fact, read it regardless as I could be wrong. ;-)

---

### Post by sprucio on 2005-07-24
My understanding was that dist-upgrade was the smarter way that apt-get processed it's database. This was what I read from Debian's documentation.

What I meant by keeping track is this. Debian has a security page devoted to issues like that. Debian can upgrade the version number at will and this is one way that the user will know a change has happened.

So without something like that, how will we know if the package was actually patched?

I managed to find this:
[http://www.ubuntulinux.org/support/documentation/usn/usn-124-1](http://www.ubuntulinux.org/support/documentation/usn/usn-124-1)

and while it does tell you a great deal of detail, it should be more structured like Debian's DSA. In fact, I think it's rather annoying that Ubuntu doens't have this more well structured.

---

### Post by AgenT on 2005-07-24
[QUOTE=sprucio]My understanding was that dist-upgrade was the smarter way that apt-get processed it's database. This was what I read from Debian's documentation.

What I meant by keeping track is this. Debian has a security page devoted to issues like that. Debian can upgrade the version number at will and this is one way that the user will know a change has happened.

So without something like that, how will we know if the package was actually patched?[/QUOTE]

You will know it is patched when you upgrade. The Ubuntu team does not (unless you use non-official repositories like backports) upgrade programs, they just patch them (fix security issues and so on). For example, Firefox will always be 1.0.2 in Hoary, but you will receive updates for it in the form of security fixes. Ubuntu Hoary will *not* upgrade your Firefox to any other version (like, for example, to 1.0.4 or 1.0.6). To upgrade, you need to use backports. This is a *good thing* (read on to find out why).

The same goes for Debian. The Debian team, as far as I know, does not upgrade any program, they just release security fixes. Not counting other repositories like unstable, testing, etc, but only stable. Think of each major Ubuntu release as a better frozen stable release of Debian stable. And think of other repositories, such as backports as Debian unstable.

You can see that an update has happened the same way you see that an upgrade occured: you look at the version numbers. For example, firefox version 1.0.2-0ubuntu5.4 is an update (one assumes the 4th) of 1.0.2-0ubuntu5. In terms of there being a website: this forum has a section that issues security updates via threads. "Official Security Announcements" under the forum "Official Ubuntu Announcements"

---

### Post by sprucio on 2005-07-24
Point taken on the version numbering. In Debian, that only applies to testing and unstable (I got too used to testing).

I must be going nuts, there is a date on those security patch announcements.

---

### Post by fishfork on 2005-07-25
Looks like [1.0.6 has been rolled out into Hoary](http://ubuntuforums.org/showthread.php?p=271702#post271702). Hasn't appeared on the mirrors yet for me so I haven't tested it. This is an unusual occurrence!

---

### Post by jdong on 2005-07-25
[QUOTE=fishfork]Looks like [1.0.6 has been rolled out into Hoary](http://ubuntuforums.org/showthread.php?p=271702#post271702). Hasn't appeared on the mirrors yet for me so I haven't tested it. This is an unusual occurrence![/QUOTE]

Yeah, and it broke a backport, too! LOL

---

### Post by AgenT on 2005-07-26
[QUOTE=jdong]Yeah, and it broke a backport, too! LOL[/QUOTE]

What do you mean it broke a backport and why?

---

### Post by jdong on 2005-07-26
[QUOTE=AgenT]What do you mean it broke a backport and why?[/QUOTE]

If you have the 1.0.4 from Backports and try to upgrade to the official 1.0.6, then the upgrade fails with attempt-to-overwrite errors from dpkg. The official backport doesn't  do the rename from mozilla-firefox to firefox, and the upstream Breezy packagers never expected this situation.

Anyway, promoting the 1.0.6 Backport fixed this mess.

---

### Post by AgenT on 2005-07-26
[QUOTE=jdong]If you have the 1.0.4 from Backports and try to upgrade to the official 1.0.6, then the upgrade fails with attempt-to-overwrite errors from dpkg. The official backport doesn't do the rename from mozilla-firefox to firefox, and the upstream Breezy packagers never expected this situation.

Anyway, promoting the 1.0.6 Backport fixed this mess.[/QUOTE]

Thanks for making that clear.

---

### Post by fishfork on 2005-07-26
Offtopic, but what does the script in your sig do? Reminds me of posters on Slashdot who'd put an obfuscated 'rm -rf /' after every post...

---

### Post by jdong on 2005-07-26
It uses 'sed' to remove comments and blank lines. I guess it might be useful for removing blank lines from various config files, but I usually like to see it there. The formatting is easier on the eyes, and sometimes there are worthwhile explanations in comments to various config files.

---

### Post by AgenT on 2005-07-26
The script removes worthless empty lines and commented lines from a config file. It does not change the config file itself, but spits out a clean version of it in the terminal. This is very helpful when someone posts their config file asking for help as it makes things easier to read because the post becomes much smaller. A great example is the xorg config file. No one needs to see the comments or excessive blank lines for it. If they do then they probably shouldn't be helping. ;-) Same for samba configs, apache configs, ssh configs, etc..

It comes from my days with Gentoo where config questions were much more rampant than on Ubuntu and it was very annoying to see huge config files with mostly worthless information (comments and empty lines) when trying to help people.

An etiquette for posting configs one may say.

---

### Post by fishfork on 2005-07-26
Ok, thanks for the explanation. I should learn about sed sometime.

---

