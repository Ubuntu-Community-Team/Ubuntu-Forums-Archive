---
title: "GoboLinux - Better system directories"
date: 2020-06-09
forum: Ubuntu, Linux and OS Chat
---

### Post by ericoporto2008 on 2020-06-09
[https://www.gobolinux.org/at_a_glance.html](https://www.gobolinux.org/at_a_glance.html)

GoboLinux offers system directories that are more intuitive to deal with than what we have on traditional Linux distributions including Ubuntu.

Is there any chance we could rearrange the directory structure in Ubuntu to something similar?

It's far more intuitive. It enables installing application basically creating a directory in a specific location, similar to how one can just move an application to the application directory in Mac.

---

### Post by VMC on 2020-06-09
That would take too much time and effort to accomplish. Its Linux after all. They have recently combined "/bin,/lib,/lib64,/sbin" into "/usr/bin". 
Its unlikely Linux structure will put everything into one basket. I would say never going to happen.

---

### Post by EuclideanCoffee on 2020-06-09
I don't see the benefit.

Perhaps new users will catch on a bit quicker, maybe? But older users it wouldn't be as much of a benefit, as I think we're all accustomized to figuring out where certain files are.

---

### Post by ericoporto2008 on 2020-06-09
It actually has a separate place for System things and Application things so not exactly.

Really recommend checking it out, it uses a Kernel module to help out, it's not as hard and has some benefits like being able to have multiple versions of the same application.

---

### Post by mastablasta on 2020-06-11
> **ericoporto2008 said:**
> 
... benefits like being able to have multiple versions of the same application.

you have snap and flatpack for that

---

### Post by ericoporto2008 on 2020-06-13
No, I don't get half the functionality this gives me. With GoboLinux you get the application clearly inside a dedicated directory for it. And with write access. Let's say I get a bug, if I know how to fix I can! This is the point of open source. Doing the same with snap would require a ton of hoops - a ton of Snapcraft.yaml files were designed to be run with a very specific version of snapcraft (which I can't run because the thing auto updates) and a very specific environment (no Multipass haven't fixed this - and why the hell is Multipass a snap??? Structural things should be kept debs). I won't comment on flatpak since I have neither used or built - the docs on those are reaaaaally bad.

Appimage is a cool format and maybe there could be a way to have the download appimage turned into a directory application when placed in the right place - I think dmg files allow this on MacOS.

The point is, there's a lot of good design on GoboLinux and on MacOS that could provide simpler and working ease of use when dealing with applications.

The thing I don't like about snaps is not being able to easily fix stuff on my computer - maybe would not be a problem if software wasn't something so broken (yes, all software, point me anything and I will give you a bug).

---

### Post by grahammechanical on 2020-06-13
Getting Linux developers to agree on any thing must be like herding cats! The GoboLinux way of doing things sounds a lot like the Microsoft method. And that would send Linux developers running to the barricades.

I was wondering about the package format of an application. Would an app developer have to re-package the app? I do not know but I think that an app developer would have to structure the code in a way that a package manager can use to install the app. So, for an app to run on GoboLinux would an app developer need to structure the code of the app in what way? Is there a need for an install script that would put all the files in the right directories?

People get fixed in their ways. They resist change. And with Linux no one is forced to go in any direction they do not want. GoboLinux would not exist if that was not true.

Regards.

---

### Post by ericoporto2008 on 2020-06-14
So, from what I can tell part of the magic is that no program needs to change. 

I know usually when you build a binary on Linux the file generates the binaries in a build directory (some have the build and install "phase" mixed together but allow passing a directory for the "install"). This makes the programs generate a minor unixy file structure with a bin directory for it's binaries, lib for the libraries built, etc for configs and some includes for it's header files.

So what GoboLinux does is just keep these programs unaltered from upstream but place them in individual directories. When they are run they can search their own paths but also each system library paths. This makes the programs not having to pack their own version of libraries unless they are done like that already.

The system libraries are built in their own directories. So there's a separation from what are system libraries and what are applications.
Forcing these different search paths to happen is done through a kernel module apparently.

I don't have more information just thought it was really neat file structure to navigate in the command line.

---

