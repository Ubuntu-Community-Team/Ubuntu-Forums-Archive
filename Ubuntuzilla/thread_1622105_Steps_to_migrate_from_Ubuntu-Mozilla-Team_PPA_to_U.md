---
title: "Steps to migrate from Ubuntu-Mozilla-Team PPA to Ubuntuzilla PPA"
date: 2010-11-15
forum: Ubuntuzilla
---

### Post by sreevathsa on 2010-11-15
I am on 32 bit Lucid Lynx (10.04.1). 

I have been using the default Ubuntu-Mozilla-Team PPA ([https://launchpad.net/ubuntu/+source/thunderbird/](https://launchpad.net/ubuntu/+source/thunderbird/)) on Lucid Lynx that provides only 3.0 series of TB (TB 3.0.10 is what I currently have). I want to now upgrade to TB 3.1. Since the above PPA only supports, 3.0 series of thunderbird on Lucid, I want to change the PPA to Ubuntuzilla ([http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)) to upgrade to TB 3.1.

I would like to know the best practices and steps for migrating from "Ubuntu_Mozilla-Team PPA" (with TB 3.0.10 currently installed) to "Ubuntuzilla PPA" to get TB 3.1.

I want to know what to uninstall, install, backup (and the order) etc to have a smooth change over to Ubuntuzilla PPA to get latest TB.

Thanks,
Sreevathsa

---

### Post by winecurmudgeon on 2010-11-15
I have more or less the same question for Thunderbird. I'm running the 64-bit from the Ubuntu PPA, but it doesn't always play well with Lightning. Can I back up my profile, uninstall the 64-bit Thunderbird, and install the 32-bit Thunderbird from Ubuntuzilla?

---

### Post by nanotube on 2010-11-16
sreevathsa:
1. back up your data profile directory, 'just in case'. 
2. uninstall whatever packages you installed from the mozilla-team ppa
3. remove the mozilla-team ppa from your list of sources.
4. follow ubuntuzilla instructions for adding the repository and installing the mozilla build packages.

---

### Post by nanotube on 2010-11-16
> **winecurmudgeon said:**
> I have more or less the same question for Thunderbird. I'm running the 64-bit from the Ubuntu PPA, but it doesn't always play well with Lightning. Can I back up my profile, uninstall the 64-bit Thunderbird, and install the 32-bit Thunderbird from Ubuntuzilla?

ubuntuzilla repository only contains 32bit packages, so won't want to install on your 64bit machine. there's the old ubuntuzilla.py install script, but that's no longer maintained, so no guarantees. 

Your best bet on trying the 32bit thunderbird right now is, i think, to just grab the .tar.gz from mozilla, manually extract it and run the binary, and see how it works.

---

### Post by sreevathsa on 2010-11-17
> **nanotube said:**
> sreevathsa:
1. back up your data profile directory, 'just in case'. 
2. uninstall whatever packages you installed from the mozilla-team ppa
3. remove the mozilla-team ppa from your list of sources.
4. follow ubuntuzilla instructions for adding the repository and installing the mozilla build packages.
nanotube,

Thanks much for your detailed steps. I am a newbie w.r.t Ubuntu package management and hence a question about step #2 in your reply:

To get a list of packages I installed from Ubuntu-mozilla team PPA, I opened the Synaptic Manager, searched for "Maintainer = Ubuntu Mozilla Team". I got the following packages as "installed" from this PPA:

firefox
firefox-branding
firefox-gnome-support
libnspr4-0d
libnss3-1d
thunderbird
xulrunner-1.9.2

When I marked firefox for 'Removal', it automatically marked firefox-branding, firefox-gnome-support and sun-java6-plugin also for removal. And when I marked thunderbird for removal, it just marked that package alone.

Now the other installed packages from this PPA listed above - libnspr4-0d, libnss3-1d and xulrunner-1.9.2 are not marked for removal. Should I also include these 3 packages for removal? I am not sure if they are being used by any other programs on my system! Also, why is the sun-java6-plugin being removed? I am assuming that other programs could be using it on my system.

Sorry to bug you with this newbie question. Please advice.

TIA.

---

### Post by sreevathsa on 2010-11-17
>
> Sorry to bug you with this newbie question. Please advice.
>

This is my office desktop. So I am a little sceptical about daring to try  out some possibilities myself. Don't want to get the system into an inconsistent state by hurrying up.

Thanks.

---

### Post by nanotube on 2010-11-17
> **sreevathsa said:**
> >
> Sorry to bug you with this newbie question. Please advice.
>

This is my office desktop. So I am a little sceptical about daring to try  out some possibilities myself. Don't want to get the system into an inconsistent state by hurrying up.

Thanks.

Hi
I thought you were only talking about thunderbird... I'd recommend to leave all firefox-related stuff alone. Just uninstall thunderbird.

---

### Post by sreevathsa on 2010-11-18
> **nanotube said:**
> Hi
I thought you were only talking about thunderbird... I'd recommend to leave all firefox-related stuff alone. Just uninstall thunderbird.
OK. What if I want to get both latest FF and latest TB from Ubuntuzilla? How do I go about the package removal? The same question that I had in comment #5.

The 4 steps that you mentioned in comment #3 seems generic enough and a pretty good way to go about it (without introducing any inconsistency from multiple maintainers providing different versions of the same program). Its just that I am unsure about the situation explained in comment #5.

---

### Post by nanotube on 2010-11-18
> **sreevathsa said:**
> OK. What if I want to get both latest FF and latest TB from Ubuntuzilla? How do I go about the package removal? The same question that I had in comment #5.

The 4 steps that you mentioned in comment #3 seems generic enough and a pretty good way to go about it (without introducing any inconsistency from multiple maintainers providing different versions of the same program). Its just that I am unsure about the situation explained in comment #5.

ubuntuzilla packages divert the /usr/bin links to point to the mozilla build versions. so uninstalling previous packages is really optional. :)

---

### Post by sreevathsa on 2010-11-22
> **nanotube said:**
> ubuntuzilla packages divert the /usr/bin links to point to the mozilla build versions. so uninstalling previous packages is really optional. :)
OK, that sounds harmless then. I tried to install the repo following instructions on the wiki. While adding the repo itself succeeded and lists the tb-mozilla-build package as available in the repo, I am having problems with installing the key. Here is what I get:

$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


Ignored this and went ahead with installing thunderbird-mozilla-build package through 'Ubuntu Software Center', and I get this error message in a pop up:

"Requires installation of untrusted packages - The action would require the installation of packages from not authenticated sources. Details: thunderbitd-mozilla-build"

Appreciate any trouble shooting tips to get through this.

TIA.

---

### Post by sreevathsa on 2010-11-22
> **sreevathsa said:**
> OK, that sounds harmless then. I tried to install the repo following instructions on the wiki. While adding the repo itself succeeded and lists the tb-mozilla-build package as available in the repo, I am having problems with installing the key. Here is what I get:

$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


Ignored this and went ahead with installing thunderbird-mozilla-build package through 'Ubuntu Software Center', and I get this error message in a pop up:

"Requires installation of untrusted packages - The action would require the installation of packages from not authenticated sources. Details: thunderbitd-mozilla-build"

Appreciate any trouble shooting tips to get through this.

TIA.
Just to update, with the above state still in place, I was able to install thunderbird-mozilla-build package from command line:


$ sudo apt-get install thunderbird-mozilla-build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  thunderbird-mozilla-build
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.6MB of archives.
After this operation, 0B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  thunderbird-mozilla-build
Install these packages without verification [y/N]? y
Get:1 [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/) all/main thunderbird-mozilla-build 3.1.6-0ubuntu1 [12.6MB]
Fetched 12.6MB in 9min 46s (21.6kB/s)                                                                                                                                                                                                                                               
Selecting previously deselected package thunderbird-mozilla-build.
(Reading database ... 261085 files and directories currently installed.)
Unpacking thunderbird-mozilla-build (from .../thunderbird-mozilla-build_3.1.6-0ubuntu1_i386.deb) ...
Adding `diversion of /usr/bin/thunderbird to /usr/bin/thunderbird.ubuntu by thunderbird-mozilla-build'
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.cache...
Processing triggers for python-support ...
Setting up thunderbird-mozilla-build (3.1.6-0ubuntu1) ...

As mentioned in previous comment the install failed from Software Center and also the key install failed. Now that the command line install has succeeded, is this still a complete and safe install? If not, what steps should I take to rectify?

Thanks.

---

### Post by nanotube on 2010-11-23
hey
your problem getting the key seems to have been due to keyserver.ubuntu.com being down at the time. try it again now.

the key is only for assuring integrity of packages... if you installed without it, everything would still be working fine. so just try again getting the key, so that your apt stops complaining about missing keys for the future.

---

