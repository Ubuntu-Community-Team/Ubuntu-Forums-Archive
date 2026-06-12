---
title: "Warning: Trying to apply debian policy here!"
date: 2008-03-14
forum: The Cafe
---

### Post by ruibernardo on 2008-03-14
Hi everybody,

I like the super-uber-APT cow and all it does for the Debian/Ubuntu system management, like installing dependencies and having secure default configurations for the packages. Debian is beautiful in this aspect.

This leaves the administrator/user all the work of configuring the computer, editing numerous files in /etc/. The administrator/user is free to edit those files. When there is an upgrade of the package where that changed file is to be substituted, the system will ask:

```
  Configuration file `/etc/ssh/ssh_config'
   ==> Deleted (by you or by a script) since installation.
   ==> Package distributor has shipped an updated version.
     What would you like to do about it ?  Your options are:
      Y or I  : install the package maintainer's version
      N or O  : keep your currently-installed version
        D     : show the differences between the versions
        Z     : background this process to examine the situation
   The default action is to keep your current version.


```This is cool, for one computer.

This makes maintaining the system a bit complicated for several computers when upgrades comes and most non-geek users can find this questions a bit over-their-head. I would like to avoid them, leaving the user just with news and infos about new configuration features output (if any) of the new upgraded package.

I'd like to create a package that have my site/computer settings and when this "configuration package" is installed, it would dpkg-divert the original configuration file, just like what the debian policy apparently says to do (although the preferred debian policy is just to edit the file with a simple text editor.

Removing the "configuration package" before upgrading would re-install the default configuration file of the package and the upgrade would be made without that questions asked, just upgrading the package normally, without problems. Then, if there wasn't any changes on the upgraded package configuration (apt should list and warn you if something changed. Without user changes on the configuration file it only shows new features or security stuff about the configuration. If I think there is no problems with the new configuration (no changes), I install my "configuration package" back and my settings are back.

Of course this is complicated. Dealing with dpkg-divert, stoping and restarting daemons, creating dependencies... I'm trying to work this out.

I know of an example about something like this in: [http://www.eyrie.org/~eagle/notes/debian/server.html#package](http://www.eyrie.org/~eagle/notes/debian/server.html#package)

It's for entreprise deployments and I'm not going to do all that, but the way they've done it is interesting for my case.

What I would like to know is how you people have dealed with this issue? Anyone can point me some example  package that makes something like this?

The long-term high-level objective of all this would be to create that package and put it on a server, install another Ubuntu/Debian computer with preseed to install packages I want, and in the end install my configuration package, leaving me with a (hopefully) ready-to-use-computer.

What's your opinion about this? Does it respect Debian policy? Will this break? Would it be useful? Is it a good practice or not? Thanks.

---

### Post by ruibernardo on 2008-03-17
Maybe my post was too long and I didn't/couldn't express myself better, or this subject isn't much of a conversation subject, but here goes...

I search more things and found out that the new version of "equivs", a script to create "dummy" packages to fulfil dependencies problems, now can install files too.

[[SIZE=2]equivs: option to add additional files to a package[/SIZE]]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=449542")

This means that you can install files with it! 

Using this new version of equivs solved my problem. I made a "proof-of-concept" howto about it with two dummy packages, one of them a "configuration-package": 

**[Howto: create "configuration packages" with equivs]("http://ubuntuforums.org/showthread.php?t=726317")**                       
                                    
Uups, I need to learn to "squeeze" my posts...

---

