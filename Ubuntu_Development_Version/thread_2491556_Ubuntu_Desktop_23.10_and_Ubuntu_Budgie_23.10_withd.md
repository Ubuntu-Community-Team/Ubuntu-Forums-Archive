---
title: "Ubuntu Desktop 23.10 and Ubuntu Budgie 23.10 withdrawn, then fixed and released"
date: 2023-10-13
forum: Ubuntu Development Version
---

### Post by sudodus on 2023-10-13
[SIZE=4]The iso files of Ubuntu Desktop 23.10 and Ubuntu Budgie 23.10 are getting withdrawn, then fixed and released[/SIZE]

Those iso files are being updated to resolve a malicious translation incident. If I understand correctly, it affects [only] the iso files with the new installer. It means that the corresponding 'legacy iso files' with the old Ubiquity installer are good and still available at

[cdimage.ubuntu.com/ubuntu/releases/23.10/release/](http://cdimage.ubuntu.com/ubuntu/releases/23.10/release/)

and

[cdimage.ubuntu.com/ubuntu-budgie/releases/mantic/release/](http://cdimage.ubuntu.com/ubuntu-budgie/releases/mantic/release//)

where you also find the sha256sums.

There are more details at [this link to Ubuntu Discourse](https://discourse.ubuntu.com/t/announcement-ubuntu-desktop-23-10-release-image-is-being-updated-to-resolve-a-malicious-translation-incident/39365).[SIZE=4][/SIZE]

[hr][/hr]
The other 23.10 iso files and image files are not affected and still available.

---

### Post by sudodus on 2023-10-14
A new version of the main Ubuntu Desktop 23.10 iso file is uploaded for iso testing, and it seems to work. 

Not only the malicious translation is removed, but also the bugs occurring in QEMU seem fixed. So I expect that we soon find it released as **[FONT=Courier New]ubuntu-23.10-desktop-amd64.iso[/FONT]** with the following **[FONT=Courier New]sha256sum[/FONT]**.

```

[s]cdb00cb2c46ec4681763384172ca317965a0844e629380fe72a6631216358fae *ubuntu-23.10-desktop-amd64.iso[/s]

```

**Edit 1:** A red bug is found, so there must [probably] be more debugging before the main Ubuntu Desktop 23.10 iso file is released.

**Edit 2:** Now (with the iso file dated 20231016.1) the iso file can be released.

My first test of this iso file (this morning) failed. But it works now (in the same computer where it failed), a Dell Latitude E7240 in UEFI mode (not secure boot), booted from cloned iso file. There was a previous Lubuntu system in the internal drive.

New since this morning: Early when started the installer, there is a popup window "**Update to version 0+git.1c719695**", I did that and restarted the installer.

Several error popups are shown. I sent reports ... but these errors were not stopping the installation.

Anyway, the installation finished and the installed system booted and reached the desktop environment correctly :-)

This iso file has the following **[FONT=Courier New]sha256sum[/FONT]**.

```

3b6c5275366d02160554fa5703add462da3b8ce9be1749f8806e8dbbffaa2b5a *ubuntu-23.10.1-desktop-amd64.iso

```

---

### Post by Irihapeti on 2023-10-16
It looks like the replacement ISOs are in the process of being officially released. The Budgie one is already on the website, and I imagine the Ubuntu one should follow shortly.

---

### Post by sudodus on 2023-10-16
@Irihapeti,

Thanks for the good news :-)

---

### Post by Bashing-om on 2023-10-16
23.10.1 is out:
[https://discourse.ubuntu.com/t/announcement-ubuntu-desktop-23-10-release-image-is-being-updated-to-resolve-a-malicious-translation-incident/39365](https://discourse.ubuntu.com/t/announcement-ubuntu-desktop-23-10-release-image-is-being-updated-to-resolve-a-malicious-translation-incident/39365)

---

### Post by #&amp;thj^% on 2023-10-16
> **Bashing-om said:**
> 20.10.1 is out:
[https://discourse.ubuntu.com/t/announcement-ubuntu-desktop-23-10-release-image-is-being-updated-to-resolve-a-malicious-translation-incident/39365](https://discourse.ubuntu.com/t/announcement-ubuntu-desktop-23-10-release-image-is-being-updated-to-resolve-a-malicious-translation-incident/39365)

he meant 23.10

---

### Post by MAFoElffen on 2023-10-16
I was testing 20231016's daily, compared to 20231013's image... 

guiverc told me it is just a respin, but things are different. 

The one on the 13th was crashing on me continually while I was busy working the the LIE. ubuntu-desktop-installer kept crashing, even though I was NOT working inside the installer. I was working in the desktop, in a terminal session. It was frustrating having to cancel apport dialogs many, many times, to try to continue what I was doing.

The one for the 16th has been stable and no problems at all... Even after working in the LIE for over 13 hours now! Even the bug's I filed on 20231013 were resolved in that image.

It looks like this one is a keeper and is ready now.

---

### Post by Claus7 on 2023-10-17
Hello,

I tried to install legacy first. It never asked me anything. Installation finished and I was greeted with the login screen. Then I tried the default option. It took much more time and more resources until ready for installation. I tried the hellenic (greek) keyboard to no avail. It is not corrected even in the final version. I tried to go backwards and select another keyboard, yet the previous button in "select your timezone" screen is grayed out.

Regards!

---

### Post by MAFoElffen on 2023-10-17
> **Claus7 said:**
> I tried the hellenic (greek) keyboard to no avail. It is not corrected even in the final version. I tried to go backwards and select another keyboard, yet the previous button in "select your timezone" screen is grayed out.

Dang. 

The way you wrote that implied it had a problem before this, in the beta, and still has the problem in the release. 

Or do I read that wrong. Was it working in the beta, and now in the release, since they removed things from the translation, it is now not working?

---

### Post by Claus7 on 2023-10-17
Hello,

I will write the steps followed today in order to try the new stable iso:
1) I went in that page: [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)
and for mantic there are two options to download:
i) download 23.10 inside a green button
ii) download 23.10 (legacy desktop installer)
2) First I tried the legacy iso using virtualbox. It never asked anything to fill, just started the installation and when it was over I was greeted with a virtualbox user (or something similar) and asking for a password in order to log in. Since I hadn't provided a password during installation, I powered off the virtual machine, removed it and tried the other iso.
3) For the other iso happened what I mentioned above. So what you say here:

> **MAFoElffen said:**
> ...
The way you wrote that implied it had a problem before this, in the beta, and still has the problem in the release. 


is what actually happened. I had been testing this since pre-beta releases. I provide also a relevant link in launchpad: [https://bugs.launchpad.net/ubuntu/+source/subiquity/+bug/2018943](https://bugs.launchpad.net/ubuntu/+source/subiquity/+bug/2018943)

As a result, it was not working during beta days and it is not working even now.

Regards!

---

