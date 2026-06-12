---
title: "Install From Apt or Compile"
date: 2005-10-14
forum: Server Platforms
---

### Post by Lampshade on 2005-10-14
I'm looking for reccomendations from experienced Ubuntu-ers on whether it's better to use the Apache/PHP/Mysql applications from apt-get or it's better to grab the latest programs and compile and install them myself.  I'd also like an explanation as to why.  I really like Ubuntu as a desktop Linux and am thinking about rebuilding my server with it as well.  Time to upgrade from Red Hat 9.  Thanks for the info.

---

### Post by Lord Illidan on 2005-10-14
Depends...

Compiling a program, especially ones which require a lot of dependencies like the ones you mentioned, and Programming IDEs can be hell! This is because of the dependencies.. For example... Program X will need Program Y and Z..but Y needs  A and B and Z needs C and D.. and so on...
This is where apt comes in handy, because it handles dependencies automatically.. Upgrading is also a cinch...

However, compiling the latest source code will mean that you have the bleeding edge software installed, which apt does not guarantee, since most apps are actually 1 or 2 version numbers behind.. And the apps will be compiled and optimized for your pc...not some generic x86 processor...for example..

---

### Post by Lampshade on 2005-10-14
I understand the dependency issue, which would be a pain, but the benefit of installing it myself is that all the files (logs, confs, etc) are all in one place.  From looking at the Ubuntu guide it looks like my web folder will be /var/www and my confs in /etc/apache2.  But that's just a guess, I didn't see anywhere in the guide where it explains the directory structure.  

If someone with experience could fill me in, I'd appreciate it.  I wish I had an extra PC to install and see for myself, but I don't.  

Thanks again for the help.

---

### Post by jobezone on 2005-10-14
[QUOTE=Lord Illidan]Depends...

Compiling a program, especially ones which require a lot of dependencies like the ones you mentioned, and Programming IDEs can be hell! This is because of the dependencies.. For example... Program X will need Program Y and Z..but Y needs  A and B and Z needs C and D.. and so on...
This is where apt comes in handy, because it handles dependencies automatically.. Upgrading is also a cinch...[/QUOTE] And this is especially important for servers and the like, since you'll get automatic security updates from ubuntu.

---

### Post by brentoboy on 2005-10-14
Is there a way to tell apt (or synaptic) to automatically perfer source instead of binary, and after downloading the source (and dependancies) compile them and take the fresh binaries and install them as though they came in a deb package.

and when new versions of the source get posted... update/recompile, maintain etc - like it does with binaries today?

Of course, it would need to just use binaries if there was not easily available source.

You get the idea?

is this a dream, or is there something I dont know about that works already? If its a dream, are there any other people dreaming the same dream?

---

### Post by LordHunter317 on 2005-10-14
[QUOTE=Lampshade]I understand the dependency issue, which would be a pain, but the benefit of installing it myself is that all the files (logs, confs, etc) are all in one place.[/quote]That's not a benefit, as all that stuff is not supposed to be in the right place.

> From looking at the Ubuntu guide it looks like my web folder will be /var/www and my confs in /etc/apache2.That's correct.

> But that's just a guess, I didn't see anywhere in the guide where it explains the directory structure. It's covered at least in part in /usr/share/doc/apache2.

The Debian standards guide explain how the majority of packages are laid out, but it's really intended for programmers.  I'd love to say the layout is intuitive enough you'll just understand it, but I'm not sure that's really true.  Why don't you detail what you're having trouble with?

---

### Post by LordHunter317 on 2005-10-14
[QUOTE=brentoboy]Is there a way to tell apt (or synaptic) to automatically perfer source instead of binary,[/quote]Nope.

> and after downloading the source (and dependancies) compile them and take the fresh binaries and install them as though they came in a deb package.You can automatically compile for a single package, but that'll just yield the same thing you got online.

There are ways to do more automatic building, but they're intended for the package repositories.  I doubt the hassle of setting up a buildd is what you're interested in.

---

### Post by brentoboy on 2005-10-14
[QUOTE=LordHunter317]Nope.

You can automatically compile for a single package, but that'll just yield the same thing you got online.

There are ways to do more automatic building, but they're intended for the package repositories.  I doubt the hassle of setting up a buildd is what you're interested in.[/QUOTE]

I guess the correct syntax for apt-get'ing source for compilation goes something like this:
# emerge apache2

There are reasons that I went away from that command, so I'm not complaining too much.

---

### Post by LordHunter317 on 2005-10-14
No, you can download source.  But the automated procedure is just going to spit out the same .deb in the repository (i.e., download and build in one-step), so there's little point in downloading it unless you have changes to make.

---

### Post by jg123 on 2005-10-14
In the mysql docs they give commands for compiling mysql to use static modules and gain a ~10% performance improvement. I did it and had to keep apt-get installing like packages along the way.

---

