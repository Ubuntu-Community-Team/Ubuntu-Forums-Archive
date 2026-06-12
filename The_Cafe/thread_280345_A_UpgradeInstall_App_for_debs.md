---
title: "A Upgrade/Install App for debs"
date: 2006-10-19
forum: The Cafe
---

### Post by sbjaved on 2006-10-19
I'm a newbie that loves ubuntu...But one thing thats really problematic is installation of software. I've got a modem that doesn't work under ubuntu (Motorola SM56) and that means no internet access...also some people who do have workable modems have quite low download speeds (~5kbps) which is fine for surfing but NOT for downloading apps.

So for people like us we don't have any way to install (say amarok...or beagle) apps. What i did for Windows was that i used to go to a high-speed cafe and download all setups there and bring it back on a USB home but for Ubuntu there are no deb packages available for download DIRECTLY OFF THE INTERNET and i've seen people advise against installig software that way.

So what would i (and a lot of people) like is some utility that mimicks synaptic (or maybe even synaptic itself as a standalone utility) that we could use to download packages ON SOME OTHER PC WITH FASTER INTERNET ACCESS....plop it in our systems and update/install the packages offline. Such a utility should be available as a Windows application (bcz not many cafes run linux on workstations let alone Ubuntu) and it should SEAMLESSLY integrate with synaptic so that it recognizes it as a repository (albeit Offline) 

Has anyone made in-roads to such an approach?

Sorry for such a long post.

---

### Post by ATAQ on 2006-10-19
Well you can search for apps at [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)
and download them there. burn them, take them home.(make sure you download all dependancies aswell, they are listed on that site)

Then copy from cd to /home/usr/

then open terminal, type;  "sudo dpkg -i appname.deb"

Job sorted!

---

### Post by maniacmusician on 2006-10-19
i'm pretty sure there's a web interface for the ubuntu repositories as well; i once used them to download ndiswrapper from another computer, but i cant for the life of me remember where it was located...

---

### Post by Nonno Bassotto on 2006-10-19
You can download what you need from [here]("http://packages.ubuntu.com"), but be careful about dependencies. Apt-get should have some option to list the dependencies of a given package. Otherwise select the package you need in Synaptic and keep note of the other packages that are installed as dependencies. Then go to an internet cafe and download everything. It can be not so nice, in case you manually have to select dozens of dependencies...

---

### Post by chaosgeisterchen on 2006-10-19
Maybe someone could quickly create an app making this all possible.

---

### Post by argie on 2006-10-19
Wait, GDebi works fine for installing .debs and visiting the repositories with your browser means you can retrieve all the files there.

I think you can download the repositories themselves by doing a:
wget -r <repositoryaddress> , but I haven't ever tried that.

---

### Post by yman on 2006-10-19
I think all the people replying here are people who have high speed internet, because you don't seem so grasp just how hard it is to get around with Ubuntu without internet.

Without internet, you could in theory still do everything but in practice you could only install packages that have no unsatisfied dependancies. This is especially true for non-expert users.

There should be some sort of cross platform tool that creats portable repositories that include the app you want with its full dependancy tree. That way you can install offline and if the portable repository has something (a shell script?) that automatically installs it using synaptic it would be really portable and temporary and easy to use.

---

### Post by NoWhereMan on 2006-10-19
if there were a livecd with apt-zip he could use that... :/

---

### Post by maniacmusician on 2006-10-19
that is so true. I've never had to suffer that, but god it must be horrible. I remember having dial up once upon a time; it was torture. Not that I knew it at the time, having not tried any faster ways of access. i feel for all you dial up users out there...

---

### Post by UbuWu on 2006-10-20
> **yman said:**
> 
There should be some sort of cross platform tool that creats portable repositories that include the app you want with its full dependancy tree. That way you can install offline and if the portable repository has something (a shell script?) that automatically installs it using synaptic it would be really portable and temporary and easy to use.

There were some people working on something like that, but the project seems dead now: [http://hyper-get.sourceforge.net/](http://hyper-get.sourceforge.net/)

---

### Post by sbjaved on 2006-10-20
I totally agree with 'yman'...

And thanks to 'maniacmuscian' for his compassion...

As for 'ATAQ' i would like to say that I manually tried to install amarok that way...and it was HELL...i HIGHLY recommend nobody try that...especially not a newbie like me

---

### Post by sbjaved on 2006-10-20
> **Nonno Bassotto said:**
> You can download what you need from [here]("http://packages.ubuntu.com"), but be careful about dependencies. Apt-get should have some option to list the dependencies of a given package. Otherwise select the package you need in Synaptic and keep note of the other packages that are installed as dependencies. Then go to an internet cafe and download everything. It can be not so nice, in case you manually have to select dozens of dependencies...

Thats fine...I have a CD with all Amarok packages downloaded...How do i install them??

[http://ubuntuforums.org/showthread.php?t=244289&highlight=Amarok](http://ubuntuforums.org/showthread.php?t=244289&highlight=Amarok)

---

### Post by argie on 2006-10-20
use dpkg -i <nameofpackage> or just double click it. That should bring up GDebi.

Sometimes, a program won't install because of dependencies, then just type:
```
dpkg -i <nameofpackage> <dependency> <dependency2> 
``` and so on, as long as you have the dependencies too.

---

