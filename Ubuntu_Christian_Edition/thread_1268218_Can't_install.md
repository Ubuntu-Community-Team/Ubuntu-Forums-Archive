---
title: "Can't install"
date: 2009-09-16
forum: Ubuntu Christian Edition
---

### Post by Tearaft on 2009-09-16
Hi everyone,

I hope I am posting this in the correct. I tried to install Submit CE several times and I was not able to. My computer is brand new and I have all of the updated software (9.04) but it will not let me install. This is terminal message, at least the end of it.

Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-ce: Depends: opensong but it is not installable
             Depends: usplash-theme-ubuntu-ce but it is not installable
E: Broken packages

Anyone have any clue as too what I need to do to get it installed?

PAX

Tom

---

### Post by Tearaft on 2009-09-16
Sorry about the typos. Submit should be Ubuntu. The submit came from spell check.

PAX

Tom

---

### Post by david_kt on 2009-09-16
> **Tearaft said:**
> 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-ce: Depends: opensong but it is not installable
             Depends: usplash-theme-ubuntu-ce but it is not installable
E: Broken packages

Tom

What is the out put of :

```
cat /etc/apt/sources.list.d/ubuntuce.list
```

DK

---

### Post by Tearaft on 2009-09-16
This is what I got.

thomas@thomas-laptop:~$ cat /etc/apt/sources.list.d/ubuntuce.list
deb [http://ubuntuce.com/repos/Ubuntu_CE/](http://ubuntuce.com/repos/Ubuntu_CE/) jaunty_amd/

# PPA for Crosswire Packaging Team
deb [http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu](http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu](http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu) jaunty main


deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
#deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"

PAX

Tom

---

### Post by david_kt on 2009-09-16
> **Tearaft said:**
> This is what I got.

thomas@thomas-laptop:~$ cat /etc/apt/sources.list.d/ubuntuce.list
deb [http://ubuntuce.com/repos/Ubuntu_CE/](http://ubuntuce.com/repos/Ubuntu_CE/) jaunty_amd/

# PPA for Crosswire Packaging Team
deb [http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu](http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu](http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu) jaunty main


deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
#deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"

PAX

Tom

You probably trying to install 64 bit version of CE to 32 (i386) version of ubuntu.

Try this:

```
sudo rm /etc/apt/sources.list.d/ubuntuce.list
sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_i386.list -O /etc/apt/sources.list.d/ubuntuce.list
sudo apt-get update && sudo apt-get install ubuntu-ce

```

---

### Post by Tearaft on 2009-09-16
I thought that maybe the problem but I thought my processors were64 bit (intel core duo2 ). I will give it another shot here soon.

Thanks

PAX

Tom

---

### Post by Tearaft on 2009-09-16
David_KT,

THANKS. It worked like a charm. I am up and running. I have one more question for you.

---

### Post by Tearaft on 2009-09-16
I noticed some different wallpapers from Ubuntu CE online (they were samples with watermarks at Google images), they must have been from a previous edition. Do you have any idea where I may get them?

Thanks

PAX

Tom

---

### Post by david_kt on 2009-09-16
Your computer support 64 bit, but you have installed 32 bit version of ubuntu. If you want 64 bit version, you have to reinstall ubuntu (or use ubuntu ce 64 bit version iso).

As for the wallpapers, I intend to upload additional wallpapers. But I would need to repack those wallpapers to avoid conflict with current one.

Or you could search christian wallpapers here:

[http://wallpaper4god.com/](http://wallpaper4god.com/)

There are many beautiful wallpapers there.

DK

---

### Post by Tearaft on 2009-09-16
Thanks David

PAX

Tom

---

