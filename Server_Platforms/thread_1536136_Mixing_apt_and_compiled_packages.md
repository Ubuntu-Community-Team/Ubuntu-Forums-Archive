---
title: "Mixing apt and compiled packages"
date: 2010-07-21
forum: Server Platforms
---

### Post by kerryhall on 2010-07-21
I don't want to screw up my system, but I need newer versions of packages then the ones in the apt repos. What is the community consensus on the best way to mix apt package management with building bleeding edge packages from source?

Should I build the source into a package and install it with apt? Should I avoid make install? 

I would also like to be able to use multiple versions of the same package, and have some sort of sym link or something to determine which version gets executed.

Thanks!

---

### Post by Telengard C64 on 2010-07-21
APT is one of the most powerful and effective package management systems available on any Linux distro. The last thing you want to do is fight against it by compiling from source.

Lately I've been adding PPAs from Launchpad to get the latest versions of some software. By doing so I am working with the package manager, not against it.

There are also third party repos for some programs, such as VirtualBox, which you can add to install the latest version of the software. This is also working with the package manager, not against it.

If you absolutely must compile from source then maybe you should consider using checkinstall. It will add the compiled program to your local package database, thus cooperating with the package manager. If you later choose to remove the software, you should be able to do so with the package manager.

---

### Post by kerryhall on 2010-07-28
I decided to go with checkinstall, but I am intrigued by the PPAs from Launchpad. How do I get those set up? I would like to get bleeding edge updates, but am using Hardy.

---

### Post by Telengard C64 on 2010-07-29
I also use Hardy.

There are instructions for installing on every PPA page on Launchpad, but just as an example here are instructions for the SANE PPA:

[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

The instructions for hardy are at the bottom.

---

### Post by kerryhall on 2010-08-04
I think I might just be a bit confused as to what a PPA is. So besides the standard package repos that Canonical provides, people will compile bleeding edge packages and put them into PPAs? So for example, if I want to upgrade to Eye of Gnome 2.30.2, I would need to find someone who has compiled that version into a package and posted it on there? 

Thanks!

---

### Post by Telengard C64 on 2010-08-04
Someone, typically a person on the team of a particular program, will prepare the source code of the program and upload the source code to Launchpad. Then Launchpad compiles the source code for both 32-bit and 64-bit architectures. Users who have added the public key and repository address for that PPA to their package manager may then download the binaries from the PPA.

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

If you want to search for a PPA to add to your package manager then search for it here:

[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

---

### Post by kerryhall on 2010-08-09
Awesome, thanks for that info, that is exactly what I wanted to know!

---

### Post by Vegan on 2010-08-09
I find outside of Webmin, ever thing is in the repository. So I have no issues as my Linux box is basically a web appliance.

---

