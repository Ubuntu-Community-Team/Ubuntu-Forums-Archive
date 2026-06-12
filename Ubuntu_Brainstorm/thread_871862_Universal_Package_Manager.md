---
title: "Universal Package Manager"
date: 2008-07-27
forum: Ubuntu Brainstorm
---

### Post by Slug71 on 2008-07-27
I think something like this may have arised already but not sure as a poll.
Would just like to see what other people think by means of a poll.
IMO there should be a universal package manager built into Ubuntu which would allow the installation of drivers/apps from all distros whether it be a .deb or rpm or whatever. I cant help but think that this would be a huge step forward for Linux and Ubuntu. This would simplify things so much for noobs like myself and also get a lot more people switching to Ubuntu. And even if other Distros followed suit then we may see just see a single type installation format used by all distros which would make drivers and apps be much more available since manufactures and developers would just have to create a single type installer for Linux.

---

### Post by rockin_goliath on 2008-07-27
+1
Check out [http://www.packagekit.org]("http://www.packagekit.org")

---

### Post by smartboyathome on 2008-07-27
Try searching, this has been suggested before. The reason it cannot work is because packages are named differently in different distros, and even in Ubuntu packages can change their names between versions. As far as unifying all types of packages, that won't happen due to Linux's "freedom of choice" philosophy. Take away freedom of choice even through this, and you will upset some Linux users.

---

### Post by Slug71 on 2008-07-27
Well it must be possible since Alien already does something like it. Im not sure to what extent regarding names between different verions of the same OS as ive never used it but im sure it will be possible in the future as it is upgraded. And if Distros were to start including this in future versions then i think a single installer type file could arise. As far as upsetting some people, it would only be a tiny part of linux that has changed and i think the benefits far outway the cons.

---

### Post by smartboyathome on 2008-07-27
What aliens does is a hack, it just unpacks the pre-compiled portion of a package and packs it again in the deb format. The package would have been compiled on a different machine so it isn't guarenteed that it would work or even run, since libraries can be located in different spots. Try reading through portions of [this thread]("http://ubuntuforums.org/showthread.php?t=658574"), it explains the situation quite well.

---

### Post by Slug71 on 2008-07-28
Thanks for that link man, was pretty interresting. It seemed like it was really getting somewhere with the talk about Autopackage and Packagekit working together. Do you think it is possible with LSB?

Now my linux knowledge is very limited as ive only had Ubuntu for 4 days and havent really messed much with other distros other than installing them on my Desktop which i managed to make multi-boot so i could mess with them all. Basically this might sound very stupid but would it be possible if hardware manufacturers and ISVs etc wrote drivers and software to a single installer xx format and then you have a app that comes in all distros which can read this format and convert it to the format supported by your distro and then install? The app of course will detect what distro youre running and its all setup by the distro team. If this is possible the only short fall i would see is that it would take longer to install than using a package for your distro as it has to convert then install. Also this xx format will have to be written much bigger than it has to so that it contains all the info required by the different distros and versions etc. The app to run this will probably be pretty difficult to compile too.

Do you know if LSB 3.? comes in Hardy or has it not been included yet?

---

### Post by smartboyathome on 2008-07-28
> **Slug71 said:**
> Thanks for that link man, was pretty interresting. It seemed like it was really getting somewhere with the talk about Autopackage and Packagekit working together. Do you think it is possible with LSB?

I don't think it is right now, since LSB isn't trying to force Autopackage on anyone, and different distros have already made their standards on where everything is placed, etc. Give a man complete freedom like Linux did for too long and they multiply so much that there is no way to reverse it.

> **Slug71 said:**
> Now my linux knowledge is very limited as ive only had Ubuntu for 4 days and havent really messed much with other distros other than installing them on my Desktop which i managed to make multi-boot so i could mess with them all. Basically this might sound very stupid but would it be possible if hardware manufacturers and ISVs etc wrote drivers and software to a single installer xx format and then you have a app that comes in all distros which can read this format and convert it to the format supported by your distro and then install? The app of course will detect what distro youre running and its all setup by the distro team. If this is possible the only short fall i would see is that it would take longer to install than using a package for your distro as it has to convert then install. Also this xx format will have to be written much bigger than it has to so that it contains all the info required by the different distros and versions etc. The app to run this will probably be pretty difficult to compile too.

It could be possible, but isn't at the moment. You are welcome to make it if you want. But besides that, we already have a sort of "package format" which distributers are using to distribute their packages which works on all distros, it is called .bin packages. From what I understand, they basically combine their targz package with a script which runs an ncurses installer (in order to avoid extra dependancies just to run that installer :p) and asks you a few questions on locations and such, and then installs it for you.

> **Slug71 said:**
> Do you know if LSB 3.? comes in Hardy or has it not been included yet?

LSB is a standard, not a program. So of course it does. See here: [http://www.linuxfoundation.org/en/LSB](http://www.linuxfoundation.org/en/LSB)

---

### Post by lukjad on 2008-07-28
I vote no because not all distros can function with the same package manager and how would we choose? Whatever we did choose would not be good for everyone. Let distros choose on their own.

---

### Post by Alasdair on 2008-07-28
Package management is not a completely solved problem, standardizing on a single package format would likely hurt new and innovative approaches to installing software such as the [nix package manager]("http://nixos.org/").

---

### Post by Slug71 on 2008-07-28
True that, what if say alsa and hplips and other software you manually install just has an auto updater no matter what version? Then each Distro can keep their own installer format and the writers of the the formats just build around the current version and send it through a server.

If that makes sense.

---

### Post by songshu on 2008-07-29
what happened to "make install"? that always seemed to work.

but still, even if the same package architecture is being used, then what happens with the custom configs??

---

### Post by TFrog on 2008-07-30
I voted yes.  However, I'm not voting for a Universal Package Manager between distro's.  What I'm implying is that all variants of Ubuntu (Ubuntu, Kubuntu, Xubuntu, and others) use the same package manager instead of using Synaptic in Ubuntu and Adept in Kubuntu (I'm familiar with both managers).  Synaptic though a cluttered interface is still superior in my opinion than Adept.  Adept gives you far to much information than the novice needs and even a seasoned guru of any variant of Ubuntu doesn't require all the information that Adept allows you to see.  I vote for a Universal Package Manager for all of Ubuntu variants.

---

### Post by sujoy on 2008-08-01
package management is almost perfect. instead working on an already working system, lets try and devote time in finding solutions to some real problems, like drivers and such. it would be nice to have a  hardware team, getting support from all distro, who could just write up drivers and manage a repo for that, in a nice  & easy to access zone

---

