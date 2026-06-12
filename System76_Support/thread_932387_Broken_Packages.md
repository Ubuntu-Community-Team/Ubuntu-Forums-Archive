---
title: "Broken Packages"
date: 2008-09-28
forum: System76 Support
---

### Post by wireless_Phil on 2008-09-28
Need help figuring this out, don't know if it was the Firefox 3 update or the Ubuntu Hardy update that cause the problem?

This is what I get after trying to fix broken packages, I tried twice. Not sure what this means, but think its not good.

[B]Extracting templates from packages: 100%
Preconfigured packages...
dpkg: parse error, in file 'var/lib/dpkg/statuse' near line 12830 package 'xerver-xorg-input-synaptics':
file details field "Size" not allowed in status file

E: Sub-process /usr/bin/dpkg returned error code (2)
A package failed to install. Trying to recover:[/B]

I went into terminal and did "sudo apt-get update"

Everything looks good until the end.

[B]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]

So I am at a loss. I won't loose data, its all on flash.

Phil

---

### Post by perce on 2008-09-28
The second message looks like you were trying to open a second package manager, which is forbidden. Maybe you didn't close update manager before running apt-get?

---

### Post by wireless_Phil on 2008-09-28
Maybe? I'll try again, as you said and if I get the same results, I'll keep digging.

Thanks,

---

### Post by wireless_Phil on 2008-09-28
Ok Perce, that was part of it solved for the lower 2, I had the Terminal open and the Package Manager.

So now the Apt-get worked. I'll still have to figure out the rest of it.

Thanks,

Phil

---

### Post by jdb on 2008-09-28
> **wireless_Phil said:**
> Ok Perce, that was part of it solved for the lower 2, I had the Terminal open and the Package Manager.

So now the Apt-get worked. I'll still have to figure out the rest of it.

Thanks,

Phil

Google on:

dpkg: parse error, in file 'var/lib/dpkg/status

and you'll find a lot of things to try.

jdb

---

### Post by wireless_Phil on 2008-09-29
Thanks JDB, 

I started doing that yesterday and did find a few for various versions of Linux.

Some mention rebuilding the package which I really don't fell that at easy with. I'm new to Ubuntu, but did have some Unix experience 15 years ago, but not much.

All my data is saved on a flash drive so I won't loose anything and tried to start over with the live CD, but it ignored it and booted from the HD.

Starting over would be the easyest for me to do.

Phil

---

### Post by thomasaaron on 2008-09-29
Please run...

sudo apt-get install -f
sudo apt-get update
sudo apt-get --assume-yes dist-upgrade

Hopefully that will fix the problem and get your system up to date.

---

### Post by wireless_Phil on 2008-09-29
> **thomasaaron said:**
> Please run...

sudo apt-get install -f
sudo apt-get update
sudo apt-get --assume-yes dist-upgrade

Hopefully that will fix the problem and get your system up to date.

I'm using Ubuntu 8.4 with a Celeron CPU on a 2003 Toshiba Satellite. 30Gig HD.

---

### Post by thomasaaron on 2008-09-29
> I'm using Ubuntu 8.4 with a Celeron CPU on a 2003 Toshiba Satellite. 30Gig HD.

That's OK. It doesn't matter. Try running the commands.

---

### Post by wireless_Phil on 2008-09-29
> **wireless_Phil said:**
> I'm using Ubuntu 8.4 with a Celeron CPU on a 2003 Toshiba Satellite. 30Gig HD.

Commands ran in order and the end results as follows )Not all results, just the endings)

(1)
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 12830 package `xserver-xorg-input-synaptics':
 file details field `Size' not allowed in status file
E: Sub-process /usr/bin/dpkg returned an error code (2)


(2)
updates/restricted Sources
Reading package lists... Done

(3) Is a big list of Uninstalled maybe too big for me to place in this form?

led
                          Depends: xserver-xorg-video-rendition but it is not installed
                          Depends: xserver-xorg-video-sisusb but it is not installed
                          Depends: xserver-xorg-video-tdfx but it is not installed
                          Depends: xserver-xorg-video-vesa but it is not installed
  xterm: Depends: libncurses5 (>= 5.6+20071006-3) but it is not installed
  xulrunner-1.9: Depends: libpango1.0-0 (>= 1.20.1) but it is not installed
  xutils: Depends: x11-utils but it is not installed
  yelp: Depends: libpango1.0-0 (>= 1.20.1) but it is not installed
        Depends: librarian0 but it is not installed
  zenity: Depends: libpango1.0-0 (>= 1.20.0) but it is not installed
E: Unmet dependencies. Try using -f.

---

