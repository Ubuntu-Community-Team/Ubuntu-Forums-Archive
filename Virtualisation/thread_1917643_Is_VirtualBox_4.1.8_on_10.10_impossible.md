---
title: "Is VirtualBox 4.1.8 on 10.10 impossible?"
date: 2012-01-30
forum: Virtualisation
---

### Post by mnordal on 2012-01-30
I'm trying to install virtualbox 4.1.8 on Ubuntu 10.10. In synaptic package manager I only see 3.2.8 available. I have tried to tick off "pre-released packages" and "unsupported packages" but still I only see 3.2.8.

Then I tried with ```
sudo apt-get install virtualbox-4.1
```

From which I get: 
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 virtualbox-4.1 : Depends: libqt4-opengl (>= 4:4.7.2) but 4:4.7.0-0ubuntu4.4 is to be installed
                  Depends: libssl1.0.0 (>= 1.0.0) but it is not installable
                  Depends: libstdc++6 (>= 4.6) but 4.5.1-7ubuntu2 is to be installed
```


Then I tried downloading the Maverick Mercat deb from here: [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)
And when I run this file the Software center says "Conflicts with the installed package 'virtualbox-ose'". 

I have spent hours on this now and cannot find any with a similar problem. What's up with this? 

PS: I have tried installing the missing dependencies but trying that I get other missing dependencies. 

Any help is much appreciated!

---

### Post by haqking on 2012-01-30
remove current version.

Install latest version from the .deb

---

### Post by mnordal on 2012-01-31
> **haqking said:**
> remove current version.

Install latest version from the .deb

Thank you for the suggestion but I got the same message after removing 3.2.8 and running 

```
sudo apt-get install virtualbox-4.1
```

Any other ideas?

---

### Post by doobrie on 2012-01-31
Can you remove it all using apt-get and then install from the downloaded deb?

---

### Post by uRock on 2012-01-31
Moved to Virtualization.

You should be able to remove via Ubuntu Software Center or Synaptic Package Manager.

---

### Post by mnordal on 2012-01-31
Thanks folks, seems we're getting closer.
So instead of installing via 'sudo apt-get install virtualbox-4.1'
I downloaded the .deb as you guys suggested and it seems to have gone ok..somewhat. I noticed these "Unknown media type in type.." messages as you can see below, what's that? 
But also I seem to have 4.1 now and it opens ok. Not sure yet if it's 100% functional or these "Unknown media type in type.." messages will cause problems?


```
Setting up virtualbox-4.1 (4.1.8-75467~Ubuntu~maverick) ...
Adding group `vboxusers' (GID 128) ...
Done.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS           [ OK ] 
 * Starting VirtualBox kernel modules                                    [ OK ] 
Processing triggers for ureadahead ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'fonts/package'
Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_DK.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-central ...
Processing triggers for python-support ...

```

---

### Post by jim_deadlock on 2012-01-31
*EDIT* you beat me to it...


> **mnordal said:**
> 
```
sudo apt-get install virtualbox-4.1
```


No don't install from the repository, go to virtualbox.org and download the .deb file from there and install it (then install the extension pack).

[https://www.virtualbox.org/wiki/Downloads]("https://www.virtualbox.org/wiki/Downloads")

---

### Post by mnordal on 2012-01-31
Yes, that seems to have done it, but what about the warnings above?

Also, I should note that I went to Synaptic Package Manager to check it out and I see it's marked as "upgradeable" but when trying to upgrade I get this (familiar) message: 

```
virtualbox-4.1:
  Depends: libqt4-opengl (>=4:4.7.2) but 4:4.7.0-0ubuntu4.4 is to be installed
 Depends: libssl1.0.0 (>=1.0.0) but it is not installable
  Depends: libstdc++6 (>=4.6) but 4.5.1-7ubuntu2 is to be installed
 Recommends: libsdl-ttf2.0-0 but it is not going to be installed
```

What's funny to me here is that Synaptic Package Manager says the installed version is 4.1.8-75467 and as far as I can see that's the newest one. In the versions tab I have two possibilities:
4.1.8-75467 ~ Ubutu oneiric (download.virtualbox.org)
4.1.8-75467 ~ Ubutu maverick (now)

Has my Synaptic Package Manager gone nuts? Or maybe I have?

---

### Post by doobrie on 2012-01-31
It looks like the Unknown Media Types are arifacts of the packaging and not Virtual Box.

According to Virtual Box, these are warnings only and can probably be ignored.

[https://www.virtualbox.org/ticket/7991](https://www.virtualbox.org/ticket/7991)

---

### Post by mnordal on 2012-01-31
Ok thanks, that's good news! 

Any idea about the "upgradeability" which is not really the case when I try?

---

### Post by japzone on 2012-01-31
> **mnordal said:**
> Ok thanks, that's good news! 

Any idea about the "upgradeability" which is not really the case when I try?

I've run into similar before. It seems to happen when a Package has dependencies that need a latest version of something but the latest version is only compiled for/available in the "Latest OS Version's" Repository. One workaround is to open the Repository in a Web Browser and manually download the latest version of something and install it manually using dpkg.
[COLOR="Red"]**WARNING: Doing this can be dangerous if replacing system critical packages. Only attempt on non-critical packages or if you have a DEB backup of the currently installed version.**[/COLOR]
```

##to install
dpkg --force-depends -i filename.deb
##to remove
dpkg --force-depends -r packagename

```

---

### Post by uRock on 2012-01-31
> **mnordal said:**
> Ok thanks, that's good news! 

Any idea about the "upgradeability" which is not really the case when I try?

I use GDebi to install .deb packages. That said, VBox will inform you whenever a newer version is released. Once I get that notification I download the newest version and install it with just a few clicks of the mouse. I have never had any issues installing newer versions of VBox. I do not use the PPA, because I have had problems with the VBox PPA in the past.

---

### Post by mnordal on 2012-01-31
OK, I think I'll stick to what's there now. It seems to work fine. I'll keep your code tips there though, just in case.

Thanks again!

---

### Post by haqking on 2012-01-31
> **uRock said:**
> I use GDebi to install .deb packages. That said, VBox will inform you whenever a newer version is released. Once I get that notification I download the newest version and install it with just a few clicks of the mouse. I have never had any issues installing newer versions of VBox. I do not use the PPA, because I have had problems with the VBox PPA in the past.

+1

Glad i am not the only one with PPA issues from Vbox.  I always use the .deb.

I dont use Ubuntu as my main OS anymore but when i was i always had PPA issues, i still get the same in Debian now.

.deb works well along with Vbox telling me when there is an update available.

Cheers

---

### Post by japzone on 2012-01-31
> **uRock said:**
> I use GDebi to install .deb packages. That said, VBox will inform you whenever a newer version is released. Once I get that notification I download the newest version and install it with just a few clicks of the mouse. I have never had any issues installing newer versions of VBox. I do not use the PPA, because I have had problems with the VBox PPA in the past.

GDebi doesn't have a "force" option in the case that dependencies aren't met, which is the problem he's having.

---

### Post by uRock on 2012-01-31
> **japzone said:**
> GDebi doesn't have a "force" option in the case that dependencies aren't met, which is the problem he's having.

Please reread the thread. The OP installed without needing to force the install. The OP only had problems when trying to get 4.1 OSE to install/upgrade.

---

### Post by Rebelli0us on 2012-01-31
I'm running VirtualBox 4.1.8 on 10.10. 

Oracle has installation instructions online, 2 or 3 commands in terminal... **or** Update Manager > Software Sources > Other Software ... Works very well, and auto-updates after that.

---

