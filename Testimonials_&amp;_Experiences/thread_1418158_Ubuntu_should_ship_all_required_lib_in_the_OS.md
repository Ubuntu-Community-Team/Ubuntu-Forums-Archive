---
title: "Ubuntu should ship all required lib in the OS"
date: 2010-02-28
forum: Testimonials &amp; Experiences
---

### Post by pushkarajthorat on 2010-02-28
Greetings,

I've come across linux from last 3 years, this question is about dependencies which are required to satisfy before installations.

Before I start, let me tell you, I've worked extensively on windows as a user and a developer form last 10 years, and I've never installed any lib. to satisfy dependency, except DirectX and few others. So here I assume MS ships all the required lib. with its OS, and so external dependencies are almost NOT required.

Now, when I came accross linux developement, I was pretty confused with the dependencies and their versions which are required to satisfied. I managed to solve the problem with apt, but, lame user for which, I suppose, ubuntu is targetted, will not understand these tricky things.

Here I wish if we could club all the MOST requied lib. and ship them with distributions, so that when user recieves a .deb file it won't give any dependency problem while installation.

Regards, Pushkaraj

Admins, I've wrongly started the thread in this forum, if possible, please move this thread to appropriate forum.

---

### Post by jrusso2 on 2010-02-28
I agree and my distro will have something similar so you can install packages from anywhere you find them.

---

### Post by Riffer on 2010-03-02
I'm trying to figure out your problem.  If I download a *.deb, the default is GDebi which automatically find any missing dependencies and downloads and installs them for you.

---

### Post by craig10x on 2010-03-02
Most websites that offer downloads for Linux usually do not offer deb files...usually only tar or jar which have to be compiled...

---

### Post by pushkarajthorat on 2010-03-02
> **Riffer said:**
> I'm trying to figure out your problem.  If I download a *.deb, the default is GDebi which automatically find any missing dependencies and downloads and installs them for you.


Riffer, I agree with you, GDebi sort out the dependency problem, BUT if the endpoint is not connected to internet and, no local apt repository is configured, then, .deb file will fail to install. If it requires any lib. dependency which is not satisfied.


> **craig10x said:**
> Most websites that offer downloads for Linux usually do not offer deb files...usually only tar or jar which have to be compiled...

I am new to Ubuntu, so not sure what most of the sites offer for installation, but, from last week, I used 2 .deb files, one for Google Chrome, and other for Yahoo Messenger and unfortunately both failed because of dependency error ;)

---

### Post by mastablasta on 2010-03-02
i wonder.... what about Ubuntu LiveDVD? does it have them? It definatelly has more stuff than the CD.

---

### Post by 3rdalbum on 2010-03-02
I've just tried to mark all "lib*" packages for installation, to demonstrate how much space all those libraries would take up. Synaptic is still calculating.

You've got the wrong end of the stick. Windows does not ship with "all the libraries you need". Windows ships with a slim set of libraries. If a programmer wants to use a different library in a program, the programmer must compile it in. This makes the binary bigger (2x-4x) and has several other disadvantages:

1. If five different programs use the same libraries, they all must contain the library. That's five different copies of the same library!

2. If a security flaw is found in a library, you have no way of knowing what programs of yours are affected. The developer of the program must release a new version of the program containing the fixed library. What if the program is no longer maintained? Even if it is, you've got five different programs that use the same library; you have to download five different programs again.

On Linux, you'd just install a new version of that library, and the fix would take effect in all programs that use the library.

Synaptic has finally finished calculating. It wants to mark most of the desktop for removal. I tried to click Apply, and it crashed. I guess I can't demonstrate how much room on the CD all those libraries would take up? You might fit Ubuntu on a DVD. Maybe.

Anyhow, I can't really believe that you've programmed anything much if you've never installed a development library for anything. Unless you work entirely in Visual Basic.

In short, with dependencies, this is the way the system is meant to work. Hey, if we wanted to, we could compile all the program's dependencies into the binary. We don't want to, because static linked libraries suck for users and developers. Just compare the sizes of the Debian package for Amarok, and the Windows installer for iTunes (which contains a full copy of Quicktime) and you'll see what I mean.

If you got "dependency problems" installing Google Chrome, then you don't have all the Ubuntu repositories enabled. Full-stop.

---

### Post by DexterLB on 2010-03-02
That's the second worst thing about windoze (the first is viruses) - No packages, no libraries. If you develop a software you have to include everything in it thus making it huge. It may happen that 15 programmes on one PC use the same libraries, but the developer can't know, so the libraries are included in all these softwares. So, a mean average set of let's say, 30 linux apps takes a lot less space (or at least the installation packages do) than a set of apps that do the same job on 'doze.

---

### Post by d3v1150m471c on 2010-03-02
If i'm not mistaken, several depencies and libraries conflict with one another depending on what they are therefore not all of them will be preinstalled. The deb installer recognizes missing dependencies, those of which, can be installed with synaptic or kpackage, depending on your ubuntu version. In cases of installing with synaptic, apt, etc, they will also fetch the dependencies you need.

---

### Post by juancarlospaco on 2010-03-02
You can include all dependency on a single deb, BTW you got a nice 100Mb deb for a 10k program.
*[See here for example.]("http://python-packager.com/")*
:)

---

### Post by pushkarajthorat on 2010-03-02
Here I am pointing out the problem that - user dont have internet on the machine and wanted to install .deb installer, then  its installation should not fail due to library dependency problem.

> **3rdalbum said:**
> 
I've just tried to mark all "lib*" packages for installation, to demonstrate how much space all those libraries would take up. Synaptic is still calculating.
Have you skipped all the lib*dev packages?


> **3rdalbum said:**
> 
Anyhow, I can't really believe that you've programmed anything much if you've never installed a development library for anything. Unless you work entirely in Visual Basic.

Yeah, you are correct, most of the time I have worked on ASM, DOS, VB and VC but my experience with packaging the dlls is less.


> **3rdalbum said:**
> 
Synaptic has finally finished calculating. It wants to mark most of the desktop for removal. I tried to click Apply, and it crashed. 
In my openion, this is because, many of the libraries provide same functionalities and conflicts each other.

We can create a set of libraries which required on MOST desktop machines, and standardize the set so that no duplicate implementations are present, and we can encourage application developers to use the libraries from the standardized set. 

This will solve problem with most softwares, but if the application developer wants to pick a non standard library, then he can have the library installer integrated with the software(.deb), so and installing the software will also install the library as a seperate software.(I am not sure about the possibility with apt framework.)


> **3rdalbum said:**
> 
If you got "dependency problems" installing Google Chrome, then you don't have all the Ubuntu repositories enabled. Full-stop.
I don't have Ubuntu repositories enabled and reason is no internet connection at my place. If this is the case with a naive user, s/he will be scared of using ubuntu.

---

### Post by Riffer on 2010-03-02
> **pushkarajthorat said:**
> Riffer, I agree with you, GDebi sort out the dependency problem, BUT if the endpoint is not connected to internet and, no local apt repository is configured, then, .deb file will fail to install. If it requires any lib. dependency which is not satisfied.

This is a separate issue.  Linux relies heavily on the net for installations.  While mostly this way of doing things works well, you have pointed out a drawback.  For the few times that may happen it does n't take away the power of GDebi.

> I am new to Ubuntu, so not sure what most of the sites offer for installation, but, from last week, I used 2 .deb files, one for Google Chrome, and other for Yahoo Messenger and unfortunately both failed because of dependency error ;)

Yeah that has happened a couple of times to me, I generally go into Synaptic and get the missing lib.  Having said that I would say that this isn't a Linux problem, rather its poor coding on Yahoo and Google.  If the majority of .deb's tell GDebi to find and get dependencies, then it stands to reason that all should be able to do that.

---

### Post by pricetech on 2010-03-02
Having supported winders boxen for several years I can tell from the way you're talking you've never been in "dll hell". (term recognized by ms themselves)

Granted, a lot of winders apps include the library necessary, leading to the aforementioned bloat, but when they don't, or when they use a "non contemporary" version, it creates havoc for the user and / or the technician.  Try finding a specific dll file assuming you can even identify which file you need, and putting it in the right place to make stuff work.

I will say I have run into dependency problems in the past when I used Red Hat, but with the streamlined installers that Ubuntu uses, the problem doesn't exist for me any more.

Not having an Internet connection is a problem, but one must be available or you wouldn't have the software to install and why would you want to install a web browser if you had no Internet connection to use it with ??

Not saying that to be a smart ***, just making the point that your problem is hardly insurmountable, more of an inconvenience.  You should be able to use whatever connection you used to download the software to also download any dependencies that need to be satisfied.

---

### Post by pushkarajthorat on 2010-03-02
Pricetech,

I agree with you.

---

