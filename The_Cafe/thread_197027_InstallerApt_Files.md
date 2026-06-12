---
title: "Installer/Apt Files"
date: 2006-06-15
forum: The Cafe
---

### Post by DoctorMO on 2006-06-15
I just had this idea that perhaps we could fill in the missing gap between the way windows users expect things to be installed and also make adding repositories easyer:

We create two xml file definitions, the first will be a repository it defined a single repository and there would be a script installed into ubuntu by default which understands this file and when double opened (in gui) would ask for password and install that repository and run an update.

The second would be an application, it only need contain references to which repository it's contained within and what versions it's vailable to. same kind of functionality as above but it simply runs apt and installs that package+deps.

What do the rest of the ubuntu community think? would these be a useful thing to think about doing?

---

### Post by wmcbrine on 2006-06-15
I kinda like things the way they are... we have one standard set of repositories, where you know everything's been vetted. If you want to install random-source files, there's a built-in barrier -- either adding a new repository or compiling from source. Although this could be seen as a limitation on the user's freedom, it's the kind of limitation that helps keep us from being overrun with junkware, the way so many Windows systems are. Less experienced users benefit from the limitation; more experienced users can easily bypass it.

Besides, it doesn't get much easier than Applications -> Add/Remove.

---

### Post by bruce89 on 2006-06-15
[https://launchpad.net/distros/ubuntu/+spec/apt-third-party](https://launchpad.net/distros/ubuntu/+spec/apt-third-party)

---

### Post by DoctorMO on 2006-06-15
A couple of points:

1) ThirdPartyApt is about giving the tools required for installing applications other than those in the standard repositories, the proposal is not to have third party installs but to have small single use tools (one job only, one job well) to install programs and repositories which are known.
2) The proposal deals with creating two file types, one for installing programs from the main repositories the other with installing repositories using /etc/apt/sources.list.d as the directory where they would be stored instead of /etc/apt/sources.list file. app install would use the repo install if required.
3) none of this deals with deb files or other kinds of installation.

I have written some scripts which I will be finished tonight because they are very simple items to do, they have one single dependancy and thats the main perl package.

I'll post a link to them once compleat, although part of me does fear replication of work, I can't resist working on it anyway.

---

### Post by DoctorMO on 2006-06-15
Scratch that, after reading the security concerns there seems to be more thinking to be done.

---

### Post by The Cosmic Hobo on 2006-06-15
It was a well-intentioned thought, and I know when I first tried installing Linux (a boxed version of SuSE, about four or five years ago), I would've given my right arm to have it behave more like Windows because I just couldn't figure out how to install software.

---

### Post by DoctorMO on 2006-06-15
I've been using Linux since 1999 so it's not that I'm looking for it to handle more like windows.

Although I have messaged the programmers behind some of the other efforts as I believe something can be done which enables this kindof feature without compremising security.

---

### Post by bruce89 on 2006-06-15
[QUOTE=The Cosmic Hobo]It was a well-intentioned thought, and I know when I first tried installing Linux (a boxed version of SuSE, about four or five years ago), I would've given my right arm to have it behave more like Windows because I just couldn't figure out how to install software.[/QUOTE]
But then you realise it's not a good way of installing things, as they are from a untrusted source.

There is always [Autopackage]("http://autopackage.org/"), but I have forgotten about it after moving to AMD64.

---

### Post by DoctorMO on 2006-06-15
No wonder nothings been done, there are too many fears and the tools are already available. ok so they're not intergrated with apt or ubuntu but the security always stops up having them available on a standard install.

---

### Post by wmcbrine on 2006-06-16
This is kind of parallel to the "Should build-essential be included by default?" discussion. The difference is that, in the case of build-essential, I think the security risk is negligible; while here, I think it wins out. Reason being, that "easy install" systems are targetted at precisely the people who are least likely to be able to evaluate the safety of what they're installing.

I think, instead, that we should do more to educate new users about the repositories. Almost anything they're going to want is there, and Synaptic and even moreso Add/Remove are great, simple interfaces.

---

### Post by DoctorMO on 2006-06-16
I think you have confuised too much the ability to install third part debs and installs with a file which installs an available package in an aproved list.

---

### Post by wmcbrine on 2006-06-16
[QUOTE=DoctorMO]I think you have confuised too much the ability to install third part debs and installs with a file which installs an available package in an aproved list.[/QUOTE]If the package is in an "approved list", then presumably that means it's in the repositories. In that case, I see no reason to "fake out" the user with a pseudo-Windows installation. We should just teach them to use the repositories.

---

### Post by DoctorMO on 2006-06-16
You shouldn't confuse windowising (making it work like windows does) with making it intuitive to use; clicking a link in a browser or IRC channel and having an app installed through a mime type script is far more intuitive to the user regardless of prior operating system experience.

---

### Post by tzeentch on 2006-09-12
I think I get what you mean DoctorMO. You're basically thinking about creating a mime type for a 'installation shortcut' (well, maybe there'd be a better name for that :) ) and creating an association in the system so that when the 'shortcut' is run, it'll call the appropriate apt-get command for example. Is that correct?
Then this 'shortcut' could be an xml file which would contain package name and maybe the repository name (so that if someone has it disabled he'll be notified).
Well I must admit it seems like a good idea. Then say, in instructions we could, instead of posting '... and then go to your terminal and type apt-get isntall something ...' we could simply post '... and click this link ...' and the xml would be downloaded, parsed and appropriate command run.
I must say I really like the way linux does things and I'd probably still be using apt-get, etc but it may make things easier for new users.

=D> 

:D

---

### Post by maniacmusician on 2006-09-12
did you ever get around to finishing this project martin? sounds interesting, at least.

---

### Post by DoctorMO on 2006-09-13
It wasn't somthing I activly worked on, just an idea. I don't think it would take much perhaps a change in /usr/share/application-registry/gnome-vfs.applications or /usr/share/app-install/desktop/*

Anyone should, with enough messing about be able to come up with something simple to do it.

---

