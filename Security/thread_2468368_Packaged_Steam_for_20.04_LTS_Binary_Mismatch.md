---
title: "Packaged Steam for 20.04 LTS Binary Mismatch"
date: 2021-10-26
forum: Security
---

### Post by corestarfish on 2021-10-26
Hello folks,

I was comparing the Steam installer file from Valve with the one available on Ubuntu.
I found the installer version is 1.0.0.61 so I located the equivalent package from Valves PPA.
After comparing the steam executables I realized that they are not the same file. You can find them in the links below:


[http://security.ubuntu.com/ubuntu/pool/multiverse/s/steam/steam_1.0.0.61-2ubuntu3_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/s/steam/steam_1.0.0.61-2ubuntu3_i386.deb)
or apt download steam
binary: steam_1.0.0.61-2ubuntu3_i386/data/usr/lib/games/steam/steam


[https://repo.steampowered.com/steam/archive/precise/steam-launcher_1.0.0.61_all.deb](https://repo.steampowered.com/steam/archive/precise/steam-launcher_1.0.0.61_all.deb)
binary: steam-launcher_1.0.0.61_all/data/usr/lib/steam/bootstraplinux_ubuntu12_32/ubuntu12_32/steam


I checked the source for that package from Ubuntu and it has a matching binary to the one from Valve. However the final packaged installer ended up with a different binary.


[http://security.ubuntu.com/ubuntu/pool/multiverse/s/steam/steam_1.0.0.61.orig.tar.xz](http://security.ubuntu.com/ubuntu/pool/multiverse/s/steam/steam_1.0.0.61.orig.tar.xz)
binary: steam_1.0.0.61-2ubuntu3_i386/data/usr/lib/games/steam


I thought they might have packaged a slightly updated version of that installer but I have no way of verifying that.


I was wondering if I'm missing something in my comparison?
Also how can we verify the integrity of provided binaries in this instance?

Your input would be greatly appreciated.

---

### Post by corestarfish on 2021-10-27
I got my answer in the launchpad. This is due to the use of [COLOR=#333333][FONT=Ubuntu]dwz and strip command to remove certain parts of the binary file.[/FONT][/COLOR]

---

### Post by DuckHook on 2021-10-28
Actually, you ask a good question and have commendable security savvy. It would never have occurred to me to compare binaries.

For the vast majority of Ubuntu users, the default practice is to just trust the binaries. As a non-programmer, that's the only real world option available to me. However, those more knowledgeable and/or more security conscious have the option of compiling from source—that being the whole point/advantage of FOSS.

---

### Post by corestarfish on 2021-10-30
Thank you.
I was not sure if I should go with the older installing method with a deb file, or the available package on Ubuntu which is always more convenient, and I decided to compare the installers.
The great thing is that there is transparency in place therefore build logs and source files are available, so people from the community were able to point me to the right direction and I was able to reproduce the same results with the provided steps in log files.
Also seeing how many knowledgeable and helpful people are involved in this community makes Ubuntu even more trustworthy for me.

---

