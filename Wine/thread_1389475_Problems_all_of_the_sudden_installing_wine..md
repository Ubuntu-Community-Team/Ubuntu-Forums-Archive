---
title: "Problems all of the sudden installing wine."
date: 2010-01-24
forum: Wine
---

### Post by Jguy on 2010-01-24
Running Ubuntu 9.10 64-bit. Installed from the alternate installer.

Took the following steps to try to install wine but with no luck. First, added the Thiurd Party source from wine's site to my repository, then jumped on a terminal and did the following:

```

jguy@jguy-desktop:~$ sudo apt-get install wine
[sudo] password for jguy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages
jguy@jguy-desktop:~$ apt-cache policy wine
wine:
  Installed: (none)
  Candidate: 1.1.37-0ubuntu1
  Version table:
     1.1.37-0ubuntu1 0
        500 http://ppa.launchpad.net karmic/main Packages
     1.0.1-0ubuntu8 0
        500 http://us.archive.ubuntu.com karmic/universe Packages
jguy@jguy-desktop:~$ apt-get install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jguy@jguy-desktop:~$ sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jguy@jguy-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jguy@jguy-desktop:~$ 
```

Installing from Add/Remove programs or Synaptic gives me a 'broken dependancies' error...I don't want wine 1.2, I want wine 1.1.37, the latest on the site. what now? :(

---

### Post by Settwi on 2010-01-24
Hmmm...
Have you tried installing it via the synaptic package manager?  it might work, if apt-get doesn't work for me, i usually do that..
:popcorn:
Cheers!

---

### Post by beastrace91 on 2010-01-24
> **Settwi said:**
> Hmmm...
Have you tried installing it via the synaptic package manager?

Synaptic is just a GUI front end for apt-get fyi - meaning if it doesn't work from the CLI it will not work from there either.

The issues you are experiencing is actually fairly common since Ubuntu chose to add their own "beta" Wine package (wine1.2) in Karmic - note that Wine 1.2 does not actually install Wine 1.1.2 but it installs one of the newer beta versions (which is still typically a few versions behind).

How did you add the third party Wine repos?

~Jeff

---

### Post by Jguy on 2010-01-25
Well, it worked by installing wine1.2 from synaptic, it just pretty much installed 1.1.37. 

I added them no differently from when I have in the past, popped open my software sources and copied the ppa etc code from wine's Ubuntu installation guide and then reloaded the package information both in the prompt that pops up after adding the third party source and via apt-get update/upgrade.

---

