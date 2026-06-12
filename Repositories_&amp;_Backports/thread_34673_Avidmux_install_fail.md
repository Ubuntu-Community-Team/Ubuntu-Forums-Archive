---
title: "Avidmux install fail?"
date: 2005-05-15
forum: Repositories &amp; Backports
---

### Post by greenwom on 2005-05-15
Hope I've the right fourum!!!!

So I

sudo apt-get install avidmux

and I get 

[COLOR=Indigo]Reading package lists... Done
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
  avidemux: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
            Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
            Depends: libvorbisenc2 (>= 1.1.0) but 1.0.1-1 is to be installed
E: Broken packages[/COLOR]

I have these packages installed, I tried this
[COLOR=DarkGreen]mike1@mikesubuntu:~$ sudo apt-get install libc6 libvorbis0a libvorbisenc2 Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
libvorbis0a is already the newest version.
libvorbisenc2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
mike1@mikesubuntu:~$[/COLOR]

So what do I do now, the dependancy packages are installed.  I think there's some kind of mismatch with package versions or something (not that I could fix it without guidence)  

HELP  :-#

---

### Post by Ali_Baba on 2005-05-16
Have you updated your Files to Breezy? When i did that i got same kind of problems.
Have you checked Synaptic packet manager. Maybe theres some vorbis or libc6 packages you should install.Not sure cause im a kind of newbie myself :)

---

### Post by greenwom on 2005-05-16
Breezy, no way, I'm a true nuub.  I've only been playing Linux for a couple months now. Ubuntu is my first Distro and I have no dersire to venture off into a unstable system :)   

In synaptic, I have all the packages that are required.

One thing I'd like to know is what these packages each do. I'm almost positive that there's a simple probplem, like a version number mismatch.  I've already encountered that.

Still haven't figured it out


EDIT :  Is there anyone out here who can help?
EDIT #2: Still looking for an answer :(

---

