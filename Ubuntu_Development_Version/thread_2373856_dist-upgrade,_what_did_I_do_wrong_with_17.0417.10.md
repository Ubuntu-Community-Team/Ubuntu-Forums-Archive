---
title: "dist-upgrade, what did I do wrong with 17.04/17.10?"
date: 2017-10-10
forum: Ubuntu Development Version
---

### Post by Drone4four on 2017-10-10
I did something wrong with my 17.04 installation a few months ago.  Intending to only to update my kernel, I invoked sudo apt-get dist-upgrade, as I have done hundreds of times in the past.  However in July it transferred me over the experimental repos for the 17.10 development release.  I’m 100% I did not invoke do-release-upgrade.  So stuck with 17.10 development version, I didn’t wish to bother with the reinstallation process.  The development release really isn’t that bad.  I like Gnome 3.26 alot.  

One contributor on Stack Overflow [explains]("https://askubuntu.com/questions/215267/will-apt-get-dist-upgrade-upgrade-my-system-to-newer-version") dist-upgrade:
> sudo apt-get dist-upgrade will not upgrade to a new Ubuntu release. It will just install available updates for the Ubuntu release you already have installed.
Is this, like, no longer true?  If dist-upgrade now migrates Ubuntu to the next release, going forward, how do I upgrade my kernel while keeping the current version of Ubuntu (non +1). I do not want to continue my updates into the 18.04 development release.

---

### Post by dino99 on 2017-10-10
you should have 'linux-generic' installed to get automatically the kernel updates proposed.

---

### Post by Drone4four on 2017-10-14
**@dino99**: I just installed the linux-generic kernel.  So now all I have to do in order to update my system is, 'sudo apt-get upgrade' and don't ever have to use 'dist-upgrade'?

---

### Post by dino99 on 2017-10-14
With a genuine install you have all the metapackages installed (here linux-generic about managing kernel upgrade). Dist-upgrade does something else.
[https://askubuntu.com/questions/215267/will-apt-get-dist-upgrade-upgrade-my-system-to-newer-version](https://askubuntu.com/questions/215267/will-apt-get-dist-upgrade-upgrade-my-system-to-newer-version)

---

### Post by Drone4four on 2017-10-14
> **dino99 said:**
> With a genuine install you have all the metapackages installed (here linux-generic about managing kernel upgrade). Dist-upgrade does something else.
[https://askubuntu.com/questions/215267/will-apt-get-dist-upgrade-upgrade-my-system-to-newer-version](https://askubuntu.com/questions/215267/will-apt-get-dist-upgrade-upgrade-my-system-to-newer-version)
You referred to AskUbuntu.  The link you referred to is the same one that I referenced in my original post.  You must have missed that. Here it is again:
> **Drone4four said:**
> One contributor on Stack Overflow [explains]("https://askubuntu.com/questions/215267/will-apt-get-dist-upgrade-upgrade-my-system-to-newer-version") dist-upgrade:
> sudo apt-get dist-upgrade will not upgrade to a new Ubuntu release. It will just install available updates for the Ubuntu release you already have installed.

According to AskUbuntu/SO, dist-upgrade should not upgrade to a new Ubuntu release.  But it did in my case.  I’m 100% certain I didn’t invoke do-release-update.

---

### Post by ventrical on 2017-10-14
> **Drone4four said:**
> You referred to AskUbuntu.  The link you referred to is the same one that I referenced in my original post.  You must have missed that. Here it is again:

According to AskUbuntu/SO, dist-upgrade should not upgrade to a new Ubuntu release.  But it did in my case.  I’m 100% certain I didn’t invoke do-release-update.

You are correct. dist-upgrade only upgrades the packages of that particular cycle. I use it on all my testing installs. Update mangler does not always do a complete job.

Regards..

---

### Post by Bucky Ball on 2017-10-14
I use
```

sudo apt update
sudo apt full-upgrade
```

(I no longer use 'apt-get' for anything.) That second command upgrades everything, but not the release to the next one. Will it do the same if run in 17.04? Thoughts?

---

