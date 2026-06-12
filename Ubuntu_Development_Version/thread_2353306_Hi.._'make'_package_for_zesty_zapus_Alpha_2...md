---
title: "Hi.. 'make' package for zesty zapus Alpha 2.."
date: 2017-02-20
forum: Ubuntu Development Version
---

### Post by Shiv_Das on 2017-02-20
Hi everyone..

I am testing out the alpha 2 lubuntu -- zesty-amd64-deskop.iso.. Installation all went fine..

Now when I try to compile my wifi drivers, I find 'make command not found'..

I downloaded these deb files from packages.ubuntu.com but lubuntu refuses to recognize them..

base-files_9.6ubuntu11_amd64.deb
base-files_9.6ubuntu5_amd64.deb
base-passwd_3.5.43_amd64.deb
build-essential_12.1ubuntu2_amd64.deb
coreutils_8.25-2ubuntu2_amd64.deb
debianutils_4.8.1_amd64.deb
essential-packages-list.txt
libc-bin_2.24-7ubuntu2_amd64.deb
module-init-tools_3.16-1ubuntu2_amd64.deb
ncurses-base_6.0+20160625-1ubuntu1_all.deb
ncurses-bin_6.0+20160625-1ubuntu1_amd64.deb

Where can I download make-tools for lubuntu 17 alpha2.. ??

Thanks in advance..

---

### Post by howefield on 2017-02-20
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by Shiv_Das on 2017-02-20
Thanks..

---

### Post by howefield on 2017-02-20
> **Shiv_Das said:**
> Thanks..

You're welcome.

Can you elaborate on what you mean by "*lubuntu refuses to recognize them*", how are you trying to install them, if that is what the issue is ?

---

### Post by Shiv_Das on 2017-02-20
Hi.. Thanks again..

Software updater says, "package not recognized" even though it is a valid zesty amd64 deb..

---

### Post by howefield on 2017-02-20
Have you tried installing from the terminal ?

Installing the downloaded deb package.. (assuming package is located in your ~/Downloads folder and the file name is as)
```
sudo apt install ~/Downloads/build-essential_12.1ubuntu2_amd64.deb
```

Installing from the apt repository
```
sudo apt install build-essential
```

ect, ect, ect.

---

### Post by Shiv_Das on 2017-02-20
currently, I am dual-booting bet'n lubuntu & win 7.. 

I'll try the terminal way and let u know.. :)

---

### Post by howefield on 2017-02-20
> **Shiv_Das said:**
> I'll try the terminal way and let u know.. :)

Do that. :)

Assuming that the packages are in the repository you should be able to install via the terminal straight from the repository without having to download them beforehand. Of course you have to have an idea of the package name..

The -s option with apt will simulate the install, so you will know that it is going to be ok before you do it for real, eg..

```
sudo apt install -s build-essential
```

---

### Post by Shiv_Das on 2017-02-20
Hi Howe..

Happy to report that debs are getting installed from the terminal but lots-n-lots of unmet dependencies..

It seems even the gcc required is a newer one.. after about re-booting, downloading and installation for scores of debs, I still have a lot of unmets..

I think the basic make should have been incorporated in the alpha 2.. Anyways will let you know tomorrow..

Thanks again...

---

### Post by cariboo on 2017-02-20
Apha 2 was released January 26th, there have been quite a few updates in the last 4 weeks. If you are running a testing release, you should be updating at least daily.

---

### Post by howefield on 2017-02-21
I guess that is all part of why it is in development :)

Just for info.. fresh daily spins of the current state of the release can be found here : [http://cdimage.ubuntu.com/daily-live/pending/](http://cdimage.ubuntu.com/daily-live/pending/)

That is the "pending" image, there is also a "current" image, pending being the most up to date, as I understand it. Can be useful to use zsync to update from the image you have to the latest without downloading the whole image again. Or of course simply keep the install updated.

---

