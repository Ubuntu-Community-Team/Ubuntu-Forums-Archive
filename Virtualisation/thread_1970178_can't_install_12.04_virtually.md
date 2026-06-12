---
title: "can't install 12.04 virtually"
date: 2012-04-30
forum: Virtualisation
---

### Post by bdenckla on 2012-04-30
Update: this was due to a bad download of the iso. Ignore all the rest.

I am unable to install Ubuntu 12.04 i386 as a guest in the following virtual environments:

VirtualBox 4.1.14 for Mac (the latest)
VirtualBox 4.1.14 for Windows (the latest)
VMWare Fusion 4.1.2 (the latest)

In VirtualBox for Mac, the install appears to hang with a screen that is black except for "Ubuntu Desktop" written on a ribbon at the top of the screen. See attached window-grab.

In VMWare, the install appears to hang at the same point in the sequence, but the screen shows the default Ubuntu background, but no "Ubuntu Desktop" ribbon.

In VirtualBox for Windows, the install appears to hang at the same point in the sequence, but the screen shows the default Ubuntu background, plus the "Ubuntu Desktop" ribbon, plus the mouse pointer works.

I have tried the install with 3D graphics both on and off in both VirtualBox for Mac and VMWare. My theory being (and still is) that the installer is actually trying to use Unity but the virtualized graphics driver cannot support that. I have not yet tried 3D on Windows.

On VirtualBox for Mac, I also tried booting with "nomodeset xforcevesa", with no difference in behavior.

For comparison, Ubuntu 11.10 installs fine in VirtualBox for Mac and Windows. I have not tried it on VMWare Fusion.

I have entered the following Launchpad bug for this: [https://bugs.launchpad.net/ubuntu/+bug/996762](https://bugs.launchpad.net/ubuntu/+bug/996762)

---

### Post by dcstar on 2012-05-01
> **bdenckla said:**
> I am unable to install Ubuntu 12.04 i386 as a guest in the following virtual environments:

VirtualBox 4.1.14 for Mac (the latest)
VMWare Fusion 4.1.2 (the latest)


If you used any "Easy Install" option in VMware then you shouldn't have.

No VMware products will be fully compatible with a product released a couple of days ago.

---

### Post by bdenckla on 2012-05-01
> **dcstar said:**
> If you used any "Easy Install" option in VMware then you shouldn't have.

No VMware products will be fully compatible with a product released a couple of days ago.

Good point, I should have specified that I was not using Easy Install in VMWare Fusion.

---

### Post by dcstar on 2012-05-02
> **bdenckla said:**
> Good point, I should have specified that I was not using Easy Install in VMWare Fusion.

Try and install an earlier Ubuntu version, if that is successful then you may have to wait until VMware update Fusion to be 12.04 compatible.

---

### Post by ahouston on 2012-05-02
My ESXi 4.1.0 clients went beserk when I upgraded to Precise.

I followed the advice from this thread: [http://ubuntuforums.org/showthread.php?t=1674759](http://ubuntuforums.org/showthread.php?t=1674759)

The synopsis is that you need to enable "Paravirtualization" in the VM client settings on ESXi, I don't know if a similar setting is available to you, but it definitely sorted out my problems.

Hope it helps.

---

### Post by bdenckla on 2012-05-08
I have updated the original post to reflect that I have reproduced the problem on VirtualBox for Windows.

I have also updated the original post to reflect that Ubuntu 11.10 installs just fine on VirtualBox for Mac and Windows.

I have also updated the original post to include a link to the Lauchpad bug I have entered for this issue.

---

### Post by CharlesA on 2012-05-08
Precise works perfectly fine for me in VBox 4.1.14.

Verify the md5sum/sha1sum of the ISO and try again.

---

### Post by bdenckla on 2012-05-09
> **CharlesA said:**
> Verify the md5sum/sha1sum of the ISO and try again.

That was it! Sorry for wasting everyone's time.

---

### Post by CharlesA on 2012-05-09
> **bdenckla said:**
> That was it! Sorry for wasting everyone's time.
Glad you got it sorted out. :)

---

