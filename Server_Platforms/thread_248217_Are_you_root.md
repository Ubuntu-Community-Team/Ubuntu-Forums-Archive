---
title: "Are you root??"
date: 2006-08-31
forum: Server Platforms
---

### Post by uncleclinto on 2006-08-31
Hey peeps,

I'm back.  I decided that instead of trying to migrate my moodle from WAMP to LAMP (no one could seem to help with moving my MySQL databases).  I decided to do an "aptitude install moodle" and start fresh.  Here's the message I got after several components installed successfully:

"E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"

Does anyone know what I need to do?  ](*,)

---

### Post by Anonii on 2006-08-31
Obviously you are not root ^_^ Root is the superuser. The mastah of everything in Linux. THE GOD!

To become root for a single command use this:

[U]
sudo aptitude install moodle[/U]

And now you will read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by IYY on 2006-08-31
Most likely you just have an instance of Ubuntu update, Synaptic or some other installer running.

---

### Post by robio376 on 2006-08-31
Wow, the question "Are you root?" should raise some flags!

---

### Post by uncleclinto on 2006-08-31
Okay, I just had my syntax all messed up.  I'm now root, and I have a whole host of new problems.  Contrary to the tutorial I read, "moodle" is not in the universal repositories.  Therefore, I now have the message "Couldn't find any package etc."   

Now, I've read countless guides including the moodle and ubuntu documentation.  Everything says download the package and run the command to install the package.  Everyone leaves out one crucial bit of info:
[LIST]
[*]Where does dapper look for packages aka where do I download to, or...
[*]How do I tell dapper (what do I put in the command line) where the package I want to install is?
[/LIST]

If I could get that down, it would solve my problem with mySQL admin *and[I]*[/I] moodle.

---

### Post by chrisfay on 2006-08-31
Moodle is in debian's repository (i just installed it):

> moodle (1.4.4.dfsg.1-3sarge1) [security] Course Management System for Online Learning

moodle-book (1.4.4-1) module for Moodle to add multi-page resources

make sure you're typing it correctly:

> sudo apt-get install moodle

You can see the list of software @ [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

---

### Post by uncleclinto on 2006-09-01
"E: couldn't find package moodle"

---

### Post by chrisfay on 2006-09-01
What do you have enabled in /etc/apt/sources.list?

---

### Post by Anonii on 2006-09-01
> **uncleclinto said:**
> "E: couldn't find package moodle"
_sudo gedit /etc/apt/sources.list_

and add the following lines inside:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse


Then: 
[U]sudo apt-get update
sudo apt-get install moodle[/U]

---

### Post by Klaidas on 2006-09-01
> **robio376 said:**
> Wow, the question "Are you root?" should raise some flags!

Hmm, got r00t? ;)

---

### Post by uncleclinto on 2006-09-01
> **Anonii said:**
> _sudo gedit /etc/apt/sources.list_

and add the following lines inside:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse


Then: 
[U]sudo apt-get update
sudo apt-get install moodle[/U]

Okay, I did that and got the following message.  Do I answer Y/N/q/?

"Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  moodle
The following NEW packages will be automatically installed:
  libgd2-xpm libt1-5 mimetex php5 php5-cli php5-gd
The following packages will be automatically REMOVED:
  libgd2-noxpm
The following packages have been kept back:
  libkrb53 libmagick9 xserver-xorg-core
The following NEW packages will be installed:
  libgd2-xpm libt1-5 mimetex php5 php5-cli php5-gd
The following packages will be REMOVED:
  libgd2-noxpm
0 packages upgraded, 7 newly installed, 1 to remove and 3 not upgraded.
Need to get 16.9MB of archives. After unpacking 93.3MB will be used.
The following packages have unmet dependencies:
  moodle: Depends: wwwconfig-common (>= 0.0.7) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
moodle [Not Installed]

Score is -1
Accept this solution? [Y/n/q/?]"

---

### Post by chrisfay on 2006-09-01
Looks like you're missing some dependencies. You may want to try using 
```
sudo aptitude install moodle
```
instead of
> sudo apt-get install moodle

that way if the extra dependencies break something you will have a database of those that can be easily removed.

> aptitude has an important feature that its command-line cousin apt-get and the graphical frontends Synaptic and Adept do not have--it remembers dependencies. If you update with aptitude, install with aptitude, and then uninstall with aptitude, all the dependencies you installed with a particular package will be removed when that package is removed (unless other packages also depend on those dependencies). 

---

### Post by uncleclinto on 2006-09-04
> **chrisfay said:**
> Looks like you're missing some dependencies. You may want to try using 
```
sudo aptitude install moodle
```
instead of


that way if the extra dependencies break something you will have a database of those that can be easily removed.

Okay, I already used aptitude install before I got that message (as opposed to apt-get).  I was told in an earlier discussion to NEVER use apt-get.  So, what do I do to fix my problem... "sudo aptitude uninstall"?  I'm sure it's way more complicated than that.

---

### Post by uncleclinto on 2006-09-04
Okay... I Chose "Y" and this is what I got.  Is it good or bad?

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  libgd2-xpm php5-cli
The following packages will be automatically REMOVED:
  libgd2-noxpm
The following packages have been kept back:
  libkrb53 libmagick9 xserver-xorg-core
The following NEW packages will be installed:
  libgd2-xpm php5-cli
The following packages will be REMOVED:
  libgd2-noxpm
0 packages upgraded, 2 newly installed, 1 to remove and 3 not upgraded.
Need to get 2439kB of archives. After unpacking 5087kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libgd2-xpm 2.0.33-2ubuntu5.1 [194kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main php5-cli 5.1.2-1ubuntu3.1 [2245kB]
Fetched 2439kB in 3s (628kB/s)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages)
dpkg: libgd2-noxpm: dependency problems, but removing anyway as you request:
 python2.4-gd depends on libgd2-noxpm (>= 2.0.33) | libgd2-xpm (>= 2.0.33); however:
  Package libgd2-noxpm is to be removed.
  Package libgd2-xpm is not installed.
(Reading database ... 73741 files and directories currently installed.)
Removing libgd2-noxpm ...
Selecting previously deselected package libgd2-xpm.
(Reading database ... 73734 files and directories currently installed.)
Unpacking libgd2-xpm (from .../libgd2-xpm_2.0.33-2ubuntu5.1_i386.deb) ...
Selecting previously deselected package php5-cli.
Unpacking php5-cli (from .../php5-cli_5.1.2-1ubuntu3.1_i386.deb) ...
Setting up libgd2-xpm (2.0.33-2ubuntu5.1) ...
Setting up php5-cli (5.1.2-1ubuntu3.1) ...

---

### Post by uncleclinto on 2006-09-04
Okay, I got this when I tried to install moodle from the package manager... what the heck does it mean??  what must I do?  I'm so close!!!!


"Depends: wwwconfig-common (>=0.0.7) but it is not installable"

---

