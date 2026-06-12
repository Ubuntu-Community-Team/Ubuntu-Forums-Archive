---
title: "Is OpenSUSE Stable?"
date: 2011-01-08
forum: The Cafe
---

### Post by kevin11951 on 2011-01-08
Is OpenSUSE stable enough to be used as a desktop for business use, or is OpenSUSE the development version/testing grounds of SUSE Enterprise Linux?

---

### Post by jcolyn on 2011-01-08
I've been running Opensuse on a laptop for just over a month now with no problems..

However If you want a OS for business use I'd suggest Suse Enterprise since that is what it is made for.

---

### Post by ilovelinux33467 on 2011-01-08
I am running openSUSE 11.3 on my servers and I find it extremely stable. Also on my desktop, laptop, netbook etc it is very stable for that as well

---

### Post by Old_Grey_Wolf on 2011-01-08
> **kevin11951 said:**
> Is OpenSUSE stable enough to be used as a desktop for business use, or is OpenSUSE the development version/testing grounds of SUSE Enterprise Linux?

OpenSUSE is the development version of SUSE Enterprise Linux. Just like Fedora is the development version of Red Hat Enterprise Linux. 

You need to try it out for yourself in order to determine if it is stable enough for you and your clients. If you know what you are doing, you can probably find a workaround for the problems you may encounter. Of course, you need to test it before you deploy it on a client's machine or in their business environment. You should also have a transition plan for those that are already using Microsoft Windows and software that only runs on MS Windows.

After looking at your website, it looks like you are located in Austin, Texas. It also appears that you are just beginning to start up the business.

If you want to expand into the large city to your northeast at some point in the future, give me a PM. I also have an MBA.

---

### Post by ilovelinux33467 on 2011-01-08
If you do decide to use openSUSE and require help just ask on the helpful openSUSE forums:
[openSUSE Forums]("http://forums.opensuse.org/")

Here is the new user FAQ:
[New User FAQ]("http://forums.opensuse.org/english/get-technical-help-here/how-faq-forums/new-user-how-faq-read-only/")

---

### Post by Timmer1240 on 2011-01-08
try this lets you custome build your own version of suse! [http://susestudio.com/](http://susestudio.com/)

---

### Post by kaldor on 2011-01-08
> **Timmer1240 said:**
> try this lets you custome build your own version of suse! [http://susestudio.com/](http://susestudio.com/)

Indeed; might be useful if you have the time.

But, if I were you, I'd use RHEL or CentOS (6 when it comes out) for business.

---

### Post by wojox on 2011-01-08
I've never had a problem with it. Best KDE Distro around.

---

### Post by kevin11951 on 2011-01-08
Any way to get SUSE Linux Enterprise Desktop for free?  

This was one of the main reasons for the possible switch to Linux desktops...

---

### Post by kevin11951 on 2011-01-08
At this point, the only other real contender is Debian Stable 5...  Perhaps in an LTSP setup to save costs on hardware.

---

### Post by kaldor on 2011-01-09
> **kevin11951 said:**
> At this point, the only other real contender is Debian Stable 5...  Perhaps in an LTSP setup to save costs on hardware.

I disagree. CentOS is a debranded version of Red Hat Enterprise Linux. RHEL costs money and you get support with it. CentOS takes the RHEL source and removes all Red Hat logos and such. The problem with CentOS is that you get no vendor-level support. 

CentOS is one of the most popular Linux distros for servers. When CentOS 6 comes out, it'll essentially be a stable Fedora 12/13. Not only that, but you get free updates until 2017.

---

### Post by Verbeck on 2011-01-09
~edited out
unrelated comment

---

### Post by ilovelinux33467 on 2011-01-09
There is a new openSUSE project announced recently called Evergreen which aims to bring Long Term Support to openSUSE.

You can read more about Evergreen here. Just scroll down a bit and you will see it:
[http://news.opensuse.org/2011/01/03/opensuse-finished-2010-big/]("http://news.opensuse.org/2011/01/03/opensuse-finished-2010-big/")

---

### Post by ilovelinux33467 on 2011-01-09
> **wojox said:**
> Best KDE Distro around.

+1 openSUSE has a great KDE implementation

---

### Post by wojox on 2011-01-09
> **kevin11951 said:**
> At this point, the only other real contender is Debian Stable 5...  Perhaps in an LTSP setup to save costs on hardware.

That's what I use for my headless server

```
wojox@wojox-server:~$ uptime
 23:20:24 up 35 days, 14:47,  1 user,  load average: 0.00, 0.00, 0.00
```

---

### Post by kevin11951 on 2011-01-09
> **kaldor said:**
> I disagree. CentOS is a debranded version of Red Hat Enterprise Linux. RHEL costs money and you get support with it. CentOS takes the RHEL source and removes all Red Hat logos and such. The problem with CentOS is that you get no vendor-level support. 

CentOS is one of the most popular Linux distros for servers. When CentOS 6 comes out, it'll essentially be a stable Fedora 12/13. Not only that, but you get free updates until 2017.

No disrespect to Red Hat/CentOS, I just don't have any experience using it, and don't know if I can support it in a worst case scenario.

---

### Post by slooksterpsv on 2011-01-09
OpenSuSE is great! It really doesn't seem like a "development version" to me, but to each their own. I had problems with it on my laptop, it would cause my laptop to overheat, but it runs really well.

I've setup an LDAP server with it, web server etc. It is extremely stable, at least on the hardware I've used it with. I would look into it, it does feel like an enterprise class OS. Otherwise, Fedora may be what you should use, I don't really regard that one as a "development version" again, to each their own. Fedora is really good too

---

### Post by witeshark17 on 2011-01-09
I hear good about it for laptops... :popcorn:

---

### Post by LunaticHiatus on 2011-01-09
OpenSuse is stable, but I am not a huge fan of novell or opensuse for that matter. It uses the rpm package manager which is pretty fail. They have patent agreement with microsoft which is sorta fail. They recently were bought out by a company that split the operating system and patent holdings, then sold a bunch of patents to microsoft and miguel de icaza, who works at suse, is trying to develop mono and moonlight for linux (wat?) and is developing it in C# (double wat?) and asked linux users to literally beg microsoft to port their drm stack so we could watch netflix movies. 

Apparantly, despite all of the agreements he made with microsoft, they still wont port the drm stack.

Meh, screw'm.

---

### Post by ilovelinux33467 on 2011-01-09
> **LunaticHiatus said:**
> It uses the rpm package manager which is pretty fail.

How is using rpm pretty fail? IMO it is on par with deb

---

### Post by kaldor on 2011-01-09
> **ilovelinux33467 said:**
> How is using rpm pretty fail? IMO it is on par with deb

Obviously because DPKG is 10x better ;)

I don't understand the RPM hate at all.

---

### Post by LunaticHiatus on 2011-01-09
> **ilovelinux33467 said:**
> How is using rpm pretty fail? IMO it is on par with deb

package managers themselves are not very complex, but rpm causes more dll hell then deb does. More importantly, deb is becoming the dominant package manager and having a multitude of package managers just fragments things and makes it more a challenge for linux adoption since they will not have to support two (or more) package managers instead of one which they don't have to do with any other OS.

---

### Post by ilovelinux33467 on 2011-01-09
> **kaldor said:**
> I don't understand the RPM hate at all.

Nor do I. Nothing wrong with RPM

---

### Post by ilovelinux33467 on 2011-01-09
> **LunaticHiatus said:**
> package managers themselves are not very complex, but rpm causes more dll hell then deb does. More importantly, deb is becoming the dominant package manager and having a multitude of package managers just fragments things and makes it more a challenge for linux adoption since they will not have to support two (or more) package managers instead of one which they don't have to do with any other OS.

RPM hell doesn't really exist anymore after the creation of front ends for rpm such as Zypp (openSUSE, SLES), yum (Fedora, RHEL, CentOS etc...), urpmi (Mandriva) and apt-rpm. I didn't know that deb was becoming the dominant package manager.

---

### Post by Khakilang on 2011-01-09
I have install on 1 of my older computer and its been working fine. I am not a power user. So I can't really comment on its stability. But I heard its the best KDE Distros.

---

### Post by LunaticHiatus on 2011-01-09
> **ilovelinux33467 said:**
> Nor do I. Nothing wrong with RPM

thats the problem. Why have two package managers to begin with with deb works well enough. Its just reinventing the wheel twice and spiting development.

---

### Post by LunaticHiatus on 2011-01-09
> **ilovelinux33467 said:**
> RPM hell doesn't really exist anymore after the creation of front ends for rpm such as Zypp (openSUSE, SLES), yum (Fedora, RHEL, CentOS etc...), urpmi (Mandriva) and apt-rpm. I didn't know that deb was becoming the dominant package manager.

There was a speech given by some guy who did an analysis of package management usage and deb was ahead by quite a bit. There are more distributions using .deb (even when excluding debian/ubuntu spins)

---

### Post by 1clue on 2011-01-09
OpenSuse is not the "developer" release of Suse, it's just the traditional Linux distro set up for home and experimentation.  It's got the same software in it that the enterprise has in it, but enterprise has a longer development cycle (don't use software versions that are quite so green) and is already set up with the assumption that you are in an office environment.  They also do some more extensive testing based on office use.

Same thing with Fedora/RHEL, or any other distro that has an enterprise version.

There is nothing wrong with Suse.  Well, other than that it just doesn't turn my crank.  I use Ubuntu and Gentoo on my systems as I feel appropriate.

Not having looked at any site of that sort for several years, this is pretty much pure speculation based on things I saw years ago:  Last I heard, if you install the "open" version and need help, you can probably still call their tech support and get help.  It will just be a cost per unit time spent, or a cost per issue depending on how they do it.  Last I looked, Redhat claimed to support any distro with their tech support.

Frankly I find the forums of any distro to be as good a help as I need.

Good luck and have fun.

---

### Post by ilovelinux33467 on 2011-01-09
> **LunaticHiatus said:**
> thats the problem. Why have two package managers to begin with with deb works well enough. Its just reinventing the wheel twice and spiting development.

DEB and RPM both work well. Some prefer rpm and others prefer deb. It is a matter of opinion

---

### Post by ilovelinux33467 on 2011-01-09
That brings me to another good feature of openSUSE (Fedora has it as well) - Delta updates (Through delta rpm). This saves on bandwidth when doing updates because instead on downloading the whole new version of the package it just downloads the difference between the old and new package and applies that. It means for example instead of downloading 100MB package  you only need to download 3MB package.

---

### Post by LunaticHiatus on 2011-01-09
> **ilovelinux33467 said:**
> DEB and RPM both work well. Some prefer rpm and others prefer deb. It is a matter of opinion

yeah, they both work ok. They are package managers after all. Not exactly the most important thing in the world. 

My first objection is that you have to hire two sets of developers. One to develop .deb and another set to develop rpm. You could eliminate a lot of work by having one dominant package manager. I think that we should support deb since its more widely adopted.

My second objection is that it complicates things for users and developers. If you want to port your application to linux. You currently have two pretty dominant packages. Which means, as a developer you have two or more things to maintain and they sometimes end up choosing one or the other if at all.

To further complicate things, you have to explain to new users how you can "install deb on ubuntu, and KINDA install .rpm" and they look at you as if your speaking greek. 

I dunno, it just seems like needless fragmentation that actually causes more problems then it fixes.

---

### Post by lancest on 2011-01-09
Tried it and didn't like it because of a USB mount bug that was left unresolved in 11.3's Gnome. 
It felt a little rough on the edges, reminding me of my old Linux days.  
 I prefer Ubuntu.

---

### Post by ilovelinux33467 on 2011-01-09
> **LunaticHiatus said:**
> yeah, they both work ok. They are package managers after all. Not exactly the most important thing in the world. 

My first objection is that you have to hire two sets of developers. One to develop .deb and another set to develop rpm. You could eliminate a lot of work by having one dominant package manager. I think that we should support deb since its more widely adopted.

My second objection is that it complicates things for users and developers. If you want to port your application to linux. You currently have two pretty dominant packages. Which means, as a developer you have two or more things to maintain and they sometimes end up choosing one or the other if at all.

To further complicate things, you have to explain to new users how you can "install deb on ubuntu, and KINDA install .rpm" and they look at you as if your speaking greek. 

I dunno, it just seems like needless fragmentation that actually causes more problems then it fixes.

It would be nice to have one package manager I agree.

---

### Post by ilovelinux33467 on 2011-01-09
> **lancest said:**
> Tried it and didn't like it because of a USB mount bug that was left unresolved in 11.3's Gnome. 
It felt a little rough on the edges, reminding me of my old Linux days.  
 I prefer Ubuntu.

Its been a while (switched to openSUSE KDE back in August 2010) but I remember mounting USB devices fine on GNOME on openSUSE 11.3

---

### Post by inobe on 2011-01-09
as with any distribution, individual results may vary :P

everyone "will" experience different scenarios and most will be up and going in no time.

the best way is to install and configure, understand the workings, use it.

---

### Post by Spice Weasel on 2011-01-09
If you ask a question like this on Ubuntu Forums you'll get flaming and/or arguing. Best way to find out if it's stable: Download it and try it out yourself. ;)

---

### Post by halj32 on 2011-01-09
Ive been using SuSE on & off since 9.1 & it's a very good OS, but if you want to play multi-media files you must change to the packman repository's in yum  see here
 [http://packman.links2linux.org/](http://packman.links2linux.org/)

---

### Post by inobe on 2011-01-09
> **halj32 said:**
> Ive been using SuSE on & off since 9.1 & it's a very good OS, but if you want to play multi-media files you must change to the packman repository's in yum  see here
 [http://packman.links2linux.org/](http://packman.links2linux.org/)

[http://en.opensuse.org/Additional_package_repositories](http://en.opensuse.org/Additional_package_repositories)

add additional repos in yast

---

### Post by ilovelinux33467 on 2011-01-09
Here is a good guide for multimedia on the official forums which I follow. Just follow instructions for 11.3 (or whatever other version you are using):
openSUSE Multimedia and Restricted Formats Installation guide:
[http://forums.opensuse.org/english/get-technical-help-here/how-faq-forums/new-user-how-faq-read-only/407184-multi-media-restricted-format-installation-guide.html]("http://forums.opensuse.org/english/get-technical-help-here/how-faq-forums/new-user-how-faq-read-only/407184-multi-media-restricted-format-installation-guide.html")

Looking forward to the release of openSUSE 11.4 in March which will feature 2.6.37 Kernel with the 200 line per tty task groups patch :D

---

