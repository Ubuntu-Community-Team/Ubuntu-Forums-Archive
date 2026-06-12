---
title: "Wine and apt-get dist-upgrade problem"
date: 2014-07-24
forum: Ubuntu Development Version
---

### Post by Ramesh_Jude_Fernando on 2014-07-24
Hi  I got this problem when running sudo apt-get dist-upgrade
ramesh@ramesh-Aspire-V3-771:~$ sudo apt-get dist-upgrade
[sudo] password for ramesh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Failed
The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed or
                 wine1.7 but it is not going to be installed
 wine1.6-amd64 : Depends: wine1.6:any (= 1:1.6.2-0ubuntu4)
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Internal error, Upgrade broke stuff

I looked in var/log/dpkg.log and there was nothing. Any other log files I should look under. Anyone know why this error. I did try apt-get install -f but it didn't seem to work. Appreciate any help on the matter. Thanks

Oh and running uname -a
ramesh@ramesh-Aspire-V3-771:~$ uname -a
Linux ramesh-Aspire-V3-771 3.16.0-4-generic #9-Ubuntu SMP Mon Jul 14 11:55:55 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
Ramesh

---

### Post by Bashing-om on 2014-07-24
Ramesh_Jude_Fernando; Hi !

Seems you have 2 versions of Wine installed:
> 
wine : Depends: wine1.6 but it is not going to be installed or
wine1.7 but it is not going to be installed
wine1.6-amd64 : Depends: wine1.6:any (= 1:1.6.2-0ubuntu4)

Remove the Wine(s) and then update.

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2014-07-25
Have you installed Wine through a PPA? Disable it. Do not run dist-upgrade it will bring in held back packages that are held back until packages they are dependant upon are put into the archive.  

Running dist-upgrade, especially on the development version, does carry this kind of risk. And the risk is especially great with packages like Wine which are available in Ubuntu but not part of the official Ubuntu distribution. Dist-upgrade will also remove packages it thinks are causing a problem with installing other packages. That can break things.

> [COLOR=#333333][FONT=Ubuntu]It tells APT to use "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary.[/FONT][/COLOR]

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Regards.

---

### Post by Ramesh_Jude_Fernando on 2014-07-25
Thanks for the advice. I will remove Wine, as I rarely run Windows programs/games other than a few programming editors like Freebasic IDE FBIDE.

---

### Post by Ramesh_Jude_Fernando on 2014-07-25
I had a conflict with both wine 1.6 and 1.7 installed, so I removed Wine 1.6 with "apt-get remove --purge wine1.6" and "apt-get remove --purvge wine"   and apt-get dist-upgrade worked. Since I am running Mathubuntu after the script i though (don't try it with Utopic 14.10 unless you are risk taker and back up which I do with Google Drive and USB stick)  I assumed it might have installed Wine ppa, but I don't see it when I check /etc/sources.list it or in the Unity GUI list in software update (having MS-DOS and Slackware background I prefer command line) doesn't show any Wine who knows.

---

### Post by Yellow Pasque on 2014-07-25
[https://bugs.launchpad.net/ubuntu/+source/openal-soft/+bug/1348393](https://bugs.launchpad.net/ubuntu/+source/openal-soft/+bug/1348393)

---

