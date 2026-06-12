---
title: "Disable apt authentification check"
date: 2011-04-03
forum: Security
---

### Post by vmalep on 2011-04-03
Hi,

I have looked on Google for a while, but to no avail, except this thread:
[Any way to disable apt authentication?]("http://ubuntuforums.org/showthread.php?t=79333"), but left without proper answer.

In my case, having a slow internet connection, I bought the all maverick repository on DVDs, copied the files on a usb drive and modified the apt sources file to consider the local repository only:
```
# deb file:/var/www/ubuntu_local/ ./
deb file:/var/www/maverick/dvd1/ maverick main universe restricted multiverse
deb file:/var/www/maverick/dvd2/ maverick main universe restricted multiverse
deb file:/var/www/maverick/dvd3/ maverick main universe restricted multiverse
deb file:/var/www/maverick/dvd4/ maverick main universe restricted multiverse
deb file:/var/www/maverick/dvd5/ maverick main universe restricted multiverse
deb file:/var/www/maverick/dvd6/ maverick main universe restricted multiverse
deb file:/var/www/maverick/dvd7/ maverick main universe restricted multiverse
deb file:/var/www/maverick/dvd8/ maverick main universe restricted multiverse
deb file:/var/www/maverick/dvd9/ maverick main universe restricted multiverse
```

Even though I am reasonably sure it is safe, this local repository is not authenticated and I can only install package through the command line or synaptic, the Ubuntu Software Centre giving an error message "Requires installation of untrusted packages"...

I thus would like to disable the apt authentication check for this local repository. Any way to do that?

Thanks in advance,
Pierre

---

### Post by cjsteele on 2011-04-03
The keys should be in the repository disks... instead of disabling the authentication check, I'd opt for importing the keys from the repo disks.

The keys should be on the disks as '*.asc' files, so you can import them with:

```
sudo apt-key add /path/to/key-file.asc
```

cheers,
-C

---

### Post by vmalep on 2011-04-04
Hi,

Thanks for your reply.

Every repo. should come with a .asc file, but it does not.

Each DVD (9 in total) comes with 2 main folders "dists" and "pool", dists containing the Packages.gz files in subfolders: ../maverick/main/binary-i386/Packages.gz for example and pool containing the .deb files in subfolders /main/a/[package name]/[deb file]...

There may be a way to generate those asc files. I tried a few time ago and gave up, but I could try again if someone convince me it is easier than disabling this authentification check. However, in my situation, the authentification check has no added value.

BR
Pierre

---

