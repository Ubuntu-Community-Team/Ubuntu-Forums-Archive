---
title: "Last day of Monthly Broadband Billing Cycle, hope to download Ubuntu 14.04.3 today."
date: 2015-08-05
forum: Ubuntu, Linux and OS Chat
---

### Post by kagashe on 2015-08-05
I have monthly quota 10 GB 1 Mbps Broadband connection and today is last day of Monthly Billing Cycle and I hope Ubuntu 14.04.3 is launched on time at 12 hrs GMT (that will be 17:30 hrs my time) so that I can use the balance quota.

The alternative is to download the current image, is it going to be same?

Kamalakar

---

### Post by Bucky Ball on 2015-08-05
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Better here and bumped in the process. :)

---

### Post by jason_gibson2 on 2015-08-06
```
sudo apt-get update && sudo apt-get -y dist-upgrade
```

You can use your quota for something useful. There is zero reason to download an entire iso to upgrade an existing installation to a new point release.

---

### Post by vasa1 on 2015-08-06
> **jason_gibson2 said:**
>  ...
You can use your quota for something useful. There is zero reason to download an entire iso to upgrade an existing installation to a new point release.
+1. You'll get the updates in any case.

---

### Post by kagashe on 2015-08-06
> **jason_gibson2 said:**
> ```
sudo apt-get update && sudo apt-get -y dist-upgrade
```

You can use your quota for something useful. There is zero reason to download an entire iso to upgrade an existing installation to a new point release.It is not to upgrade any existing installation. I am using Ubuntu for last 10 years and know these things.

It is useful to keep an iso of the latest LTS vesrion to try on new hardware which does not have linux and it is my hobby to do this.

Kamalakar

---

### Post by coffeecat on 2015-08-06
> **kagashe said:**
> It is not to upgrade any existing installation. I am using Ubuntu for last 10 years and know these things.

It is useful to keep an iso of the latest LTS vesrion to try on new hardware which does not have linux and it is my hobby to do this.

I doubt that anyone here will be able to say whether the ISO will be released in the usual download sites on time, or late, but I do have one suggestion. The ISO that will be released will have been available as a daily live for 24 or more hours before release for final testing. You can get the latest daily live for 14.04.3 here:

[http://cdimage.ubuntu.com/trusty/daily-live/current/](http://cdimage.ubuntu.com/trusty/daily-live/current/)

At the moment the dates for trusty-desktop-amd64.iso and trusty-desktop-i386.iso are showing as 3rd August with an expected release date for the definitive ISO of 6th August, today. However, all the MD5SUMS and SHA1SUMS files are showing today's date, so I suspect that the 3rd August ISOs will turn out to be the release ones. I suggest you wait until as long as you can in your current billing cycle. If the release ISO has been made available, that's fine. If not, download whichever of the dailys - i386 or amd64 - you need, and hope that will become the one that is released. You can check when the ISO is released from the md5sum for it. Although the filename will be different, the md5sums will be the same if the daily you downloaded becomes the release ISO.

---

### Post by kagashe on 2015-08-07
While waiting for Ubuntu 14.04.3 I decided to boot Windows 8.1 and look for Windows 10 upgrade option. I rarely boot Windows 8.1 and there were huge pending updates. Then I checked for Windows 10 upgrade FAQ and came to know that I need to download and install all pending updates to get "Get Windows 10" icon in the tray.

I could use the Broadband Balance for updating Windows 8.1 and now I have "Get Windows 10" icon and reserved my copy of Windows 10 upgrade.
[ATTACH=CONFIG]263698[/ATTACH]

I also subscribed to Ubuntu-announce mailing list and came to know the launch of Ubuntu 14.04.3 which was past midnight (and next billing cycle) for me.

Kamalakar

---

### Post by Bucky Ball on 2015-08-07
> **kagashe said:**
> I could use the Broadband Balance for updating Windows 8.1 and now I have "Get Windows 10" icon and reserved my copy of Windows 10 upgrade.
[ATTACH=CONFIG]263698[/ATTACH]

The choice is entirely yours. :)

---

### Post by QIII on 2015-08-07
As stated, there is little to be gained by upgrading if things are working fine for you right now.  If you are using proprietary drivers that work, you don't need the Hardware Enablement Stack (HWE).  If the open source drivers are working, you can skip the HWE.

There's no need at all to download the entire .iso.

You could significantly reduce the amount of stuff you are downloading by doing 

```
sudo apt-get install --install-recommends linux-generic-lts-vivid
```

to just get the new kernel.

If you do want the HWE, you could always get it by doing as described [here]("https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes") in the section "LTS Hardware Enablement Stack".  If you decide to go for the HWE, be sure to uninstall any proprietary drivers and reboot before you begin the upgrade.  You can re-install them later.

I downloaded and installed everything as described in the link above just to be sure everything would work so I could be confident in suggesting that.

---

### Post by vasa1 on 2015-08-07
> **QIII said:**
> As stated, there is little to be gained by upgrading if things are working fine for you right now.  ...
OP clarified that > It is useful to keep an iso of the latest LTS vesrion to try on new hardware which does not have linux and it is my hobby to do this.
So it's not to upgrade an existing system.

---

### Post by night_sky2 on 2015-08-08
IMO, the Ubuntu 14.04.3 point release is only crucial *if *you have new hardware that were not previously supported by the LTS. Hence the Enablement Stack.

Otherwise, I would choose the 14.04.1 iso which has a full-blown 5 years support for kernel v.3.13. The most annoying bugs from the 14.04 iso have been fixed as well.

---

### Post by Irihapeti on 2015-08-09
In a situation like the OP was describing, **zsync** is very useful for updating ISO files. For example, if 2 packages and some config files have been updated since you last ran zsync, you download those items only, not the whole ISO.

---

