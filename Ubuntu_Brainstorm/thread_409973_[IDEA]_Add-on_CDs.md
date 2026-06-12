---
title: "[IDEA]: Add-on CDs"
date: 2007-04-15
forum: Ubuntu Brainstorm
---

### Post by aysiu on 2007-04-15
**Summary:**
Make available ISOs for more software.

**Rationale:**
Not everyone has a broadband internet connection or any internet connection on Ubuntu. Sometimes they can download in Windows or get friends to burn CDs for them, but they don't have a direct connection to the repositories in Ubuntu. If Ubuntu is *Linux for Human Beings*, there should be a recognition of the lack of broadband internet in many places.

Yes, too many download options can confuse new users, but you don't have to advertise these add-on CDs. You just have to have them available somewhere. People will find them if they need them.

The DVDs contain Main and Restricted repositories, but not everyone has access to a DVD burner, and a lot of popular packages are in Universe. It's true a lot of popular packages are also in Multiverse, too, but I'm not sure if there are legal issues involved with distributing those on a CD.

**Scope and Use Cases:**
Pavel has a dual boot with Windows. His USB modem doesn't work in Ubuntu, but it works in Windows. He wants to install Inkscape, Blender, IceWM, and a bunch of other applications from Universe. He's told he has to go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and track down all the individual dependencies. Yuck. If the add-on CDs existed, he could just download them in Windows, burn them to CD, and then add them as repositories in Ubuntu.

Eiko has dial-up--it works in Windows and doesn't work at all in Ubuntu, but even when it works in Windows, it is slow. She has a friend who has broadband access but no Ubuntu installed. She, too, would like to install a lot of packages from Universe. Add-on CDs would really come in handy here...

**Implementation Plan:**
Create ISOs of the most popular programs in Universe, Main, and Restricted. If it doesn't create too many legal problems, create ISOs for the most popular codecs and programs in Multiverse, too. Make these available as part of the Other Download Options off the main download page on the Ubuntu website.

**Blueprint**:
[https://blueprints.launchpad.net/ubuntu/+spec/extra-cds](https://blueprints.launchpad.net/ubuntu/+spec/extra-cds)

---

### Post by .t. on 2007-04-15
How do we select the most popular packages? Does everyone use the "popularity-contest" utility? I would prefer a simple apt-mirror of the full Ubuntu repositories (which I have heard amounts to about 20GiB of data), and this kept in sync by a weekly cronjob on the server. This could then be mkisofs'd into DVD-size ISO, which could be downloaded via [jigdo](http://atterer.net/jigdo/) and kept updated with that same utility (which would decrease the amount of bandwidth used).

---

### Post by 23meg on 2007-04-15
A slightly crazy, but useful way to address this problem would be a Windows/OSX utility that would track dependencies and grab the required packages, similar to APTonCD. There's even a script that parses the packages.ubuntu.com pages to do this; IIRC it's a Python script so it should work anywhere.

---

### Post by PriceChild on 2007-04-15
I think aptoncd should be able to fill this niche. It's quite easy to use it to burn whole repositories to disc.

---

### Post by missmomo0911 on 2007-04-15
I agree that Ubuntu should have Official Add-on CD ,because some people don't have fast intertent or DVD driver,that could help people to install softwares offline.We could include some package like Mplayer,w32codecs...or else,depends on members vote.

---

### Post by .t. on 2007-04-15
PriceChild, it's not as much a niche as you might think; and APTonCD is kinda a one-time jobbie. A cron job in the datacentre would be better; but the possibility of that all depends on the server maintainers.

---

### Post by deathbyswiftwind on 2007-04-16
I agree a million times over Ive had to download the entire repos for my friend 3 times (breezy, dapper, edgy) since he doesnt have the net. First it went from 2 dvds and a 1 and now its 3 full dvds. We dont need all of that but the important stuff would be nice ex

build essnetial
kernal with all the goodies needed for build
um will port again when I figure out my usual installs

---

### Post by aysiu on 2007-04-16
FYI: *build-essential* is already on the standard CD--just not installed by default.

---

### Post by bwhite82 on 2007-04-17
Here here! This is a great idea, many other distros already do this, it's time for Ubuntu to step up to the plate in this arena.

---

### Post by kvonb on 2007-04-17
I believe that is exactly what the DVD version of Ubuntu is.

It contains the main/restricted/universe repos I think.

You just put the DVD back in once you've installed Ubuntu and it pops up a dialogue asking if you want to add it as a repo.

I did that with Edgy, I'm sure it will be the same in Feisty :).

---

### Post by 23meg on 2007-04-17
[QUOTE=kvonb]It contains the main/restricted/universe repos I think.[/QUOTE]

It only has main and restricted.

---

### Post by aysiu on 2007-04-17
The Ubuntu DVD does not contain the Universe repositories--only the Main and Restricted ones.

And a DVD is 4 GB. A second CD, however, would be only 700 MB. And a lot more people (especially those with only dial-up or no internet) have CD burners than DVD burners.

---

### Post by TheMono on 2007-04-17
Something to download the application deb file, and all its dependencies, EXCEPT FOR those already depended on by ubuntu-desktop (or ku or xu...)

---

### Post by aysiu on 2007-04-17
> **TheMono said:**
> Something to download the application deb file, and all its dependencies, EXCEPT FOR those already depended on by ubuntu-desktop (or ku or xu...)
Except, presumably, that would be a Windows application. If you had an internet connection in Ubuntu, you'd just use the package manager.

---

### Post by Bavo on 2007-04-17
> **aysiu said:**
> Except, presumably, that would be a Windows application. If you had an internet connection in Ubuntu, you'd just use the package manager.
Wouldn't it be possible to write some php (or whatever language)-script that checks the dab you want to download for dependencies and creates a tar.gz on the fly for you to download.


So lets say i want to install program A, but i don't have an internet connection on my computer.

I go to a friend and go to getsoftware.ubuntu.com or whatever. This site ask me which (K/X/U)buntu  I have installed. And witch software i'd like to install.
In a search field i enter program A, and the site checks the dependencies for program A, lists them, and offers me an option to download all the necessary deb's in one tar.gz or even better in an .iso so i can download it and burn it to a cd immediately.

Then i cant take the cd home and install my freshly downloaded program.

Of course verifying debs, creating .tar.gz and especially .iso might require to much resources from the webserver.

---

### Post by 23meg on 2007-04-17
There's a client-side script that does something close by parsing packages.ubuntu.com. It's hardly ideal, but can be expanded to become a possible solution. You should be able to find it with a forum search.

---

### Post by Bavo on 2007-04-17
A client-side script isn't really a solution, the great thing about doing it on the server side is that it doesn't matter which OS you are using to download the packages.

---

### Post by 23meg on 2007-04-17
See post #3. That would be an unofficial supplementary project, like Wubi.

Your idea sounds good to the ear, but I don't think packages.ubuntu.com can bear such a high load; it would certainly need reinforcement, and the coding to be done wouldn't be trivial either. I'll still consult the maintainer and some others about its feasibility.

---

### Post by ShirishAg75 on 2007-04-18
need to check here l8ter, is cool. my .2 cents

---

