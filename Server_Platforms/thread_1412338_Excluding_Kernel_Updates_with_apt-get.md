---
title: "Excluding Kernel Updates with apt-get"
date: 2010-02-21
forum: Server Platforms
---

### Post by holastickboy on 2010-02-21
Hey all.

I have a nice little server running Ubuntu, and I like to have it updated to the latest as frequently as possible.  I like to keep my uptime as high as possible too, but I find that I have problems because whenever I use...

```
apt-get upgrade
```... it downloads all updates and installs them, as well as new kernels, so I have to restart the system before I can do any more system updates (because if I don't, it wont let me install the new updates until I have restarted).  

My question is, is there a way I can do a software update without downloading and installing the kernels?

---

### Post by suseendran.rengabashyam on 2010-02-22
Hi,

Try the following steps in your Ubuntu Machine

a) Open the terminal and enter the following command

```
dpkg -l linux-generic
```

note down the 'Version' number of the latest installed kernel package.

b) Create a file called 'kernel_update_pinning' in /etc/apt/preferences.d directory with the following content

```
Package: linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic
Pin: version 2.6.31.14.27
Pin-Priority: 1001
```

make necessary changes to the line 'version 2.6.31.14.27'.

c) Run ```
sudo apt-get update
```

d) Run ```
sudo apt-cache policy
``` to check whether the latest installed kernel package has been pinned down.

You can refer [https://wiki.ubuntu.com/PinningHowto](https://wiki.ubuntu.com/PinningHowto) for more information.

Hope This Helps.

---

### Post by slakkie on 2010-02-22
I agree with the poster above me to use a preferences file, however, aptitude ignores it, so I would create /etc/apt/preferences in stead of /etc/apt/preferences.d/somefile.

On my blog there is a article on how to use the preferences file on Ubuntu/Debian.

---

### Post by holastickboy on 2010-02-28
thanks guys, will try this when I get home!

---

