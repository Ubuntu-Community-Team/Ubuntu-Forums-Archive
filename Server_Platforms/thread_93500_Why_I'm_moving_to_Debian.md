---
title: "Why I'm moving to Debian"
date: 2005-11-22
forum: Server Platforms
---

### Post by hagen00 on 2005-11-22
After reading numerous posts that criticize Debian for not having up to date packages, i find it very ironic that i will need to move to Debian since Ubuntu does not have the necessary up to date packages, while Debian does. 

I need to have the latest version of Asterisk (1.2) running on on our production server and this, as well as the numerous dependencies are all found in the Debian repository and not in the Ubuntu ones. 

And i'm not keen to install all the dependent packages like libc6 and libgcc etc on Ubuntu if they were made for Debian. 

hagen

---

### Post by dubz on 2005-11-22
I dont think thats a good enough reason.But thats just me.

You could always downoad the source from [http://www.asterisk.org/download]("http://www.asterisk.org/download") follow the instruction in the README file and install it thats way.

Why take the easy way out?
Linux is a challenge,embrace it.

---

### Post by 23meg on 2005-11-22
[QUOTE=hagen00]After reading numerous posts that criticize Debian for not having up to date packages, i find it very ironic that i will need to move to Debian since Ubuntu does not have the necessary up to date packages, while Debian does. 

I need to have the latest version of Asterisk (1.2) running on on our production server and this, as well as the numerous dependencies are all found in the Debian repository and not in the Ubuntu ones. 

And i'm not keen to install all the dependent packages like libc6 and libgcc etc on Ubuntu if they were made for Debian. 

hagen[/QUOTE]
In which Debian repository are those packages? Comparing Debian stable with Debian unstable is almost like comparing apples and oranges. Debian as a distro isn't criticized for old packages; Debian stable is. Ubuntu is based on Debian unstable and that's why it can provide more up to date packages than Debian stable.

Rather than move to Debian unstable you might as well add its repositories to your sources.list in Ubuntu, download Asterisk, and then remove them.

---

### Post by hagen00 on 2005-11-22
> You could always downoad the source from [http://www.asterisk.org/download](http://www.asterisk.org/download) follow the instruction in the README file and install it thats way.

Tried that, but like i said, there are a number of unmet dependencies, i.e. packages that have to be upgraded to a later version for Asterisk to work. These packages i could only find in Debian Unstable. 

> In which Debian repository are those packages? 
They're in Debian Unstable.

> Rather than move to Debian unstable you might as well add its repositories to your sources.list in Ubuntu, download Asterisk, and then remove them.
Ah, a light! So you reckon that this is safe enough to do? I will be upgrading quite a few vital packages, like libc6 etc. Can I just use the Debian Unstable packages without breaking my entire system? I might give this a go...but i've read it's a bad idea to use Debian packages on Ubuntu...

Thanks for the suggestion

h

---

### Post by earobinson on 2005-11-22
meh If debian suits you better go for it all the power to you, its all *nix to me. Without debian there would be no ubuntu, I think that while we all take our hats off to the ubuntu dev team we sometimes forget to do so in the case of the devian dev team.

---

### Post by 23meg on 2005-11-22
[QUOTE=hagen00]! So you reckon that this is safe enough to do? I will be upgrading quite a few vital packages, like libc6 etc. Can I just use the Debian Unstable packages without breaking my entire system? I might give this a go...but i've read it's a bad idea to use Debian packages on Ubuntu...
[/QUOTE]
Some apps that explicitly depend on lower versions of those libraries might malfunction. Don't take my word for it though; do proper research before doing this.

---

### Post by hagen00 on 2005-11-22
[QUOTE=23meg]Some apps that explicitly depend on lower version of those libraries might malfunction.[/QUOTE]

Yes. And if the intention is to build a production server then it's probably best to go for Debian...

---

### Post by 23meg on 2005-11-22
[QUOTE=hagen00]Yes. And if the intention is to build a production server then it's probably best to go for Debian...[/QUOTE]
Not really, as long as it's not Debian stable.

---

### Post by hagen00 on 2005-11-22
[QUOTE=23meg]Not really, as long as it's not Debian stable.[/QUOTE]
I'm a bit confused now, please excuse my ignorance of Debian. 

Is Debian Unstable not just like adding - for example - Backports to sources.list. Am i not just using normal Debian (Sarge) but adding a few packages found in the Unstable repository. 

Does one not just add the Unstable repository to sources.list, much like i'm used to when adding backports to Ubuntu?

---

### Post by 23meg on 2005-11-22
You'll find the answers here:

[http://www.debian.org/releases/](http://www.debian.org/releases/)

---

### Post by LordHunter317 on 2005-11-22
[QUOTE=dubz]Why take the easy way out?
Linux is a challenge,embrace it.[/QUOTE]Because production serving is no place for a challenge.

[quote=hagen00]Ah, a light! So you reckon that this is safe enough to do? I will be upgrading quite a few vital packages, like libc6 etc.[/quote]It's probably safe, but I wouldn't risk it myself.  Depending on the environment, I wouldn't even pin unstable to a Debian stable box.

[quote=23meg]Some apps that explicitly depend on lower versions of those libraries might malfunction. Don't take my word for it though; do proper research before doing this.[/quote]If they don't automatically uninstall themself, then you have a packaging bug or a serious, grave APT bug.

Anyway, if you're going to do this, don't just add the source, install the package, and delete it.  That's rather silly.  Instead, pin asterisk into place using the following pins in /etc/apt/preferences:```
Package: asterisk
Pin: release a=unstable 
Pin-Priority: 501

Package: *
Pin: release a=unstable
Pin-Priority: 499
```Which will give all of Debian Unstable a lower priority than Ubuntu packages, but given asterisk a higher priority.  THis way, you still get updates without any extra manual work.  You have to add pins for other asterisk packages you install as well, copying the first three lines.

---

### Post by hagen00 on 2005-11-22
After doing some googling i found the following, which is for installing Ruby on Debian, but i think applies exactly to my situation. 

> Ruby on Rails is not a part of the Debian stable distribution. It only exists on
the testing and unstable ones. There are two ways to work around this.

1. The complete debian way is adding debian testing apt sources to your system so Ruby on Rails debian packages can be installed. ( Note that your system won’t become unstable, only Ruby on Rails and its dependencies will be updated to testing packages ) 

And then further on...

> Add this line to your /etc/apt/apt.conf

APT:: Default-Release "stable";

Which will mean that future updates and upgrades will come from Debian Stable unless is specify apt-get -t unstable foobar

---

