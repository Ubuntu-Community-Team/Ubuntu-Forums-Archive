---
title: "Set Ubuntu to work as a Desktop Grid"
date: 2008-12-20
forum: Server Platforms
---

### Post by Pyro.699 on 2008-12-20
Hello,

I placed this in the server section because it was to my understanding that my goals of this project were to resemble a server so if im wrong i appologize.

Im not sure if I'm using the term *Desktop Grid* correctly but it is to my understanding that it is a system of different computers that are set up in such a way that they are able to utilize unused processing power when one system is idle. In otherwords you turn 2 computers with medium processing power, into a single unit with a higher processing power.

Ive already taken an initiative to this project and looked into some software called [url=http://www.desktopgrid.hu/index.php?page=33]SZTAKI Desktop Grid[url] which, if my understanding of the term is correct, should be what im looking for. First i have a few questions before i go to all the work of installing this on aproximatly 6 systems.

First - In the instructions it uses the linux distrobution Debian and being a proud Ubuntu user i was wondering if there is anything special about Debian that would prevent the same software from working on Ubuntu.

Second - In the examples they use this software for is in industrial setttings, such as having hundreds of computers set up to this kind of network. Would there be any noticable differance in processing power with only 6 computers hooked up to this kind of system.

Third - If im not using the correct term, or im wrong about this project and its main goals then is there any other (free) software i could install on these systems. I was originally going to design a package that does this and would run as its own os (meaning there would be no human->machine interaction, the machine would be turned on and left alone. As the host required the power it could use the idle systems as required.

Fourth - This is kind of off topic from my main point, but after i have this set up on these systems i also want to use their disk space (why let it go to waist?). Would there be a sinple way to take all the non-used disk space and compile it into one large network disk?

Thank you all for your help
~Cody Woolaver

---

### Post by Ferret-Simpson on 2008-12-20
> **Pyro.699 said:**
> Hello,

Hey!

> **Pyro.699 said:**
> 
First - In the instructions it uses the linux distrobution Debian

Ubuntu is a fork of Debian-unstable. Chances are that things will be very similar, if not identical.

> **Pyro.699 said:**
> 
Would there be any noticable differance in processing power with only 6 computers hooked up to this kind of system.

Yes, but don't expect to crack WPA2 with it. :p

> **Pyro.699 said:**
> 
I was originally going to design a package that does this and would run as its own os.

Most distributed computing software is bespoke to your individual task - especially scientific software. There are a few standardised packages out there (Final cut server, djohn, to-an-extent blender.) but they're usually irrelevant.

UNIX servers one correctly configured can be switched on and left alone. If you're already writing your own software, I'd get a C (Or whatever compiled language you enjoy) book on distributed computing and build your code from scratch. If you can do it, and you can make the software scaleable - then when you have 40 machines all you'll need to do is install the latest tweaked version. If you think it's worth it, this is the path I would advise.

> **Pyro.699 said:**
> 
Would there be a sinple way to take all the non-used disk space and compile it into one large network disk?


There are several technologies, none of them simple. I would look into iSCSI and zfs. These are only things I've come across in passing.

Finally, as an alternative commercial solution for distributed computing, look into "Matlab" (And maybe it's open source clone Octave.)

G-man.

---

### Post by Pyro.699 on 2008-12-20
Thank you,

That was very informative (and don't worry, the main calculations i would be preforming would be personal ones (such as PI :P), there are not any wireless networks around me anyways). Do you know of any Desktop Grid software that is out there, aside from the one i mentioned (one supported by Ubuntu would be awesome)?

Thanks
~Cody Woolaver

---

