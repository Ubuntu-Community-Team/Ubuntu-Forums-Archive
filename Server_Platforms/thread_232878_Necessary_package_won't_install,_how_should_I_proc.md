---
title: "Necessary package won't install, how should I proceed?"
date: 2006-08-09
forum: Server Platforms
---

### Post by heisters on 2006-08-09
Hi all,

I'm trying to install a webmail server on a bit of a deadline. I've got Horde3 and Imp4 installed, but when I try to install Turba2, dpkg complains that it requires horde3, which won't be installed. Horde3 is installed. I've filed a [bug report]("https://launchpad.net/distros/ubuntu/+source/turba2/+bug/55786") on launchpad, but I can't really wait for it to get fixed that way (some bugs I reported 6 months ago still haven't been addressed). Is there any way you can think of that I can force it to install (-f didn't work)? Any other thoughts on how I could keep moving?
[FONT="Courier New"]
# apt-get -f install turba2
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  turba2: Depends: horde3 but it is not going to be installed
E: Broken packages
# dpkg -l horde3
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                  Version               Description
+++-=====================-=====================-==========================================================
ii  horde3                3.1.1-1               horde web application framework
[/FONT]

---

