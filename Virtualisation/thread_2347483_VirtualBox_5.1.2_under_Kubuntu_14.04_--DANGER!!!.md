---
title: "VirtualBox 5.1.2 under Kubuntu 14.04 --DANGER!!!"
date: 2016-12-25
forum: Virtualisation
---

### Post by pwabrahams on 2016-12-25
I've manage to install VirtualBox 5.1.2 under Kubuntu 14.04, but not without a major disruption.  I retrieved it from the VirtualBox website and followed the defaults to use QApt Package Installer to install it.  When I rebooted Kubuntu, the system quit with a blank screen after displaying the initial Kubuntu legend.  Bad. bad, bad!

The reason for the disaster was that QApt Package Manager had helpfully removed virtually all of my video supporting software before doing the installation.  Fortunately I happened upon a not-so-obvious way to bring my system back to life.  I went into recovery mode, then selected Resume.  That got me to a login prompt.  I logged in, went into superuser mode, and entered the directory where I had stored the virtualbox package.  I then did "apt-get -f install vbox...", using autocomplete to select the package.  And all my supporting software came back. My system was alive again!  This time I used dpkg to install VirtualBox.  Rescued!!

---

### Post by Bucky Ball on 2016-12-25
Maybe you should have installed virtualbox from the official repos rather than try and install from elsewhere. You'll find it in Muon and it should install without issue.

---

### Post by SeijiSensei on 2016-12-26
No, I'm a strong believer in using the Oracle repos for VirtualBox, but I'd follow the method described here: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions) to add the repo to your apt sources list.

---

### Post by DuckHook on 2016-12-26
> **Bucky Ball said:**
> …virtualbox from the official repos…

> **SeijiSensei said:**
> …using the Oracle repos for VirtualBox, but I'd follow the method described here: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions) to add the repo to your apt sources list.FWIW, I find both methods to be quite valid strategies. I agree with SeijiSensei that if using Oracle repos, then use the method he describes. The one drawback that I find with the Oracle repo method is the constant updating that this imposes. Most users don't need the monthly upgrades and the obligatory cycle of constantly maintaining the extensions in the VM appliance. For ease of maintenance, the one-time install from the Ubuntu repo works best. For always having the latest and greatest with bug fixes and new features, but with corresponding bother of maintenance, the Oracle repo is the choice.

For lurkers out there:

This is a good example of how Linux allows for many different but equally valid approaches to the same issue.

---

### Post by SeijiSensei on 2016-12-26
One nice thing about adding the repo to the apt sources list is that VirtualBox will be updated automatically just like any other application.  Now that they have streamlined the installation method for the Extensions, it's pretty easy to keep up with the upgrades.  After an upgrade you are prompted to install the Extension Pack.  All it takes is a couple of clicks and entering your password when asked.

---

### Post by DuckHook on 2016-12-27
> **SeijiSensei said:**
> …it's pretty easy to keep up with the upgrades…All it takes is a couple of clicks and entering your password when asked.Yes, it's very easy to keep the extension pack itself updated, but I keep about two dozen VMs and every one of *them* have to be updated too. This involves booting up each machine, loading the virtual ISO into each OS, navigating to the mount directory, running the upgrade script, and&#8213;what is most time-consuming&#8213;using the workaround for each distro that the extension pack installer does not automatically recognize. That's when it becomes a bother. More often than not, these VMs would run perfectly well in the VBox version residing in the Ubuntu repos. As is often the case in things IT, stability means foregoing the latest and greatest.

---

### Post by SeijiSensei on 2016-12-27
Two dozen?  I can see why that would be a pain to manage.  I have four, of which I only run one or two on a regular basis.  Usually I'm just running a Kubuntu VM on Windows or a Windows VM on Kubuntu.

I suspect my situation is closer to the OP's than yours.

---

### Post by DuckHook on 2016-12-28
> **SeijiSensei said:**
> Two dozen?  I can see why that would be a pain to manage.  I have four, of which I only run one or two on a regular basis.  Usually I'm just running a Kubuntu VM on Windows or a Windows VM on Kubuntu.I realize it looks silly. I'm an odd duck that way. I find trying out obscure distros to be much easier using VMs, and I can't resist test-driving them any more than a kid can resist himself in a candy store. Like you, I only use three or four with any sort of frequency.> I suspect my situation is closer to the OP's than yours.I suspect you are right. :)

---

### Post by pwabrahams on 2016-12-28
At one time the version of VirtualBox in the repositories was missing some functionality that was available in the Oracle version.  Is that still the case?

---

### Post by DuckHook on 2016-12-28
> **pwabrahams said:**
> At one time the version of VirtualBox in the repositories was missing some functionality that was available in the Oracle version.  Is that still the case?Yes. These are the "extensions" in the "Extension Pack" that SeijiSensei and I have been discussing. These extensions add things like USB support, seamless mouse integration and other extras to the VM for more functionality and a more fluid user experience. Unlike the "base" VM package, Oracle has decided to not release these extensions as FOSS code. Since the code is proprietary, Ubuntu will not host the Extension Pack in their repos. If you want them, you will have to go to Oracle's site, download them, and install them one time. Thereafter, you will have the same functionality as VMs that make use of the Oracle repository, but without the need for the monthly upgrade/maintenance cycle because, since your base VM cames from the Ubuntu site, it doesn't change monthly.

BTW, even if you make use of the Oracle repos, you will still have to install the extension pack separately.

Actually, like SeijiSensei, I make use of the Oracle repos, using exactly the instructions that he has already posted. Despite my two dozen VMs, I just put up with the monthly chore of upgrading all of the guests. I'm less interested in new features than in having bugs fixed and security holes filled. But it's still drudge work, and there's a lot to be said for the fixed unchanging VM method that Bucky Ball espouses.

---

### Post by SeijiSensei on 2016-12-28
> **DuckHook said:**
> Yes. These are the "extensions" in the "Extension Pack" that SeijiSensei and I have been discussing. These extensions add things like USB support, seamless mouse integration and other extras to the VM for more functionality and a more fluid user experience. Unlike the "base" VM package, Oracle has decided to not release these extensions as FOSS code.
Some of these extensions are proprietary because they use technologies that are encumbered by patents or copyrights and thus cannot be released as open source.  USB support is a good example. Because VirtualBox provides the virtual equivalent of a USB connection in software, it likely has to meet [USB-IF compliance standards]("http://www.usb.org/developers/compliance/").

---

### Post by pwabrahams on 2016-12-28
Does the website virtualbox.org contain all the Oracle files relating to VirtualBox, and nothing else?

---

### Post by pwabrahams on 2016-12-29
Is virtualbox.org actually *Oracle's* website for VirtualBox?  In other words, is there any difference between what you can get by going to virtualbox.org versus what you can get by going to oracle.com?

---

### Post by howefield on 2016-12-29
> **pwabrahams said:**
> Is virtualbox.org actually *Oracle's* website for VirtualBox?  In other words, is there any difference between what you can get by going to virtualbox.org versus what you can get by going to oracle.com?

Yes, the packages are identical irrespective of whether they are downloaded from the oracle or virtualbox websites. You can always compare the SHA256SUMS for confirmation.

---

