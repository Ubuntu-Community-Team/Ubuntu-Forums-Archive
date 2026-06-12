---
title: "Install Ubuntu with root user"
date: 2010-11-20
forum: The Cafe
---

### Post by Oxwivi on 2010-11-20
Yes, I've done my homework about the risks, but I still need this account. Is there anyway to do it at Ubuntu installation?

---

### Post by cgroza on 2010-11-20
Whats wrong with SUDO?

---

### Post by Oxwivi on 2010-11-20
Like I said I still need that account, I sometimes face problems with GUI authentication. Anyway, I just need it.

---

### Post by Shining Arcanine on 2010-11-20
> **Oxwivi said:**
> Yes, I've done my homework about the risks, but I still need this account. Is there anyway to do it at Ubuntu installation?

Install screen. Then do sudo -i screen and you are logged into a terminal multiplexer as root.

Alternatives are available in Canonical's documentation:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Alternatively, you could use a distribution that does not try to hide the root account from you. Debian would probably be familiar to you.

---

### Post by cpmman on 2010-11-20
I may be very wrong here and I am sure someone will indicate where but have you considered installing the latest Lucid Puppy which installs as root but has access to Ubuntu repositories for say Ubuntu-desktop etc.?

---

### Post by Oxwivi on 2010-11-20
> **cpmman said:**
> I may be very wrong here and I am sure someone will indicate where but have you considered installing the latest Lucid Puppy which installs as root but has access to Ubuntu repositories for say Ubuntu-desktop etc.?
Is that Minimal?

Shining Arcanine, thanks, but where do I type that at installation? I remember entering a command line from Alternate CD, but do not know how I had arrived at that.

---

### Post by cpmman on 2010-11-20
_***[Lucid Puppy]("http://puppylinuxnews.org/home/lucid-puppy-511-release/")***_

---

### Post by cariboo on 2010-11-20
The only account you can setup during an Ubuntu installation is the user account, there is no option to set up any other accounts, until the installation is finished.

With that, this thread is closed.

---

