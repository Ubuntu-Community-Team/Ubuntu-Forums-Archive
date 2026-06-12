---
title: "Live USB displays grub boot menu even on non-uefi machines"
date: 2020-10-13
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2020-10-13
Maybe I'm missing something? As I said the live image (via USB) now seems to only boot using the grub menu, like had been the case for UEFI hardware only.

I also can't get a live USB to boot at all on either Latitude E6400 or E6510 laptops. Even using F12 to display the boot selections does NOT show any media in USB. Same hardware works fine with Focal (and older) aside from some needed touch pad tweaks (best to just use a mouse for installation). I'll maybe try a DVD soon.

I've tested mostly Ubuntu MATE but in this case I get the same with Ubuntu and Lubuntu.

---

### Post by oldfred on 2020-10-13
Groovy has changed to use grub for both BIOS & UEFI boot.

On my Gigabyte z170 system a flash drive created by Disk Image Writer in 20.04 booted in both BIOS & UEFI boot mode. 
Sudodus was looking for users who had issues, I do not.

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1886148](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1886148)
[https://ubuntuforums.org/showthread.php?t=2447379](https://ubuntuforums.org/showthread.php?t=2447379)

---

### Post by kansasnoob on 2020-10-14
> **oldfred said:**
> Groovy has changed to use grub for both BIOS & UEFI boot.

On my Gigabyte z170 system a flash drive created by Disk Image Writer in 20.04 booted in both BIOS & UEFI boot mode. 
Sudodus was looking for users who had issues, I do not.

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1886148](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1886148)
[https://ubuntuforums.org/showthread.php?t=2447379](https://ubuntuforums.org/showthread.php?t=2447379)

How can you tell now whether you've booted in UEFI or BIOS mode? I still have some old Intel boards that can be setup either way.

---

### Post by guiverc on 2020-10-14
> **kansasnoob said:**
> Maybe I'm missing something? As I said the live image (via USB) now seems to only boot using the grub menu, like had been the case for UEFI hardware only.

I also can't get a live USB to boot at all on either Latitude E6400 or E6510 laptops. Even using F12 to display the boot selections does NOT show any media in USB. Same hardware works fine with Focal (and older) aside from some needed touch pad tweaks (best to just use a mouse for installation). I'll maybe try a DVD soon.

I've tested mostly Ubuntu MATE but in this case I get the same with Ubuntu and Lubuntu.

@oldfred already answered the first point - refer [https://discourse.ubuntu.com/t/groovy-to-use-grub2-for-booting-installer-media-in-any-modes-on-all-architectures/16871](https://discourse.ubuntu.com/t/groovy-to-use-grub2-for-booting-installer-media-in-any-modes-on-all-architectures/16871)

but providing specifics as to the release you are trying to boot (and if *groovy*, the date of the *daily* may also be helpful).

As for the latitude laptops, there are a number of bugs related to failure to boot, but without specifics as to your release, you may mean something different to what I'm thinking of (given I'm thinking of *groovy* but you may mean a different release, let alone the *daily* in question)

If issues relate to cdimages/cd-boot-images-amd64 etc, all *flavors* and main Ubuntu are usually impacted.  Me, I test mostly in Lubuntu, but confirm issues using other *flavors* and main Ubuntu usually too.

---

### Post by kansasnoob on 2020-10-14
> **guiverc said:**
> @oldfred already answered the first point - refer [https://discourse.ubuntu.com/t/groovy-to-use-grub2-for-booting-installer-media-in-any-modes-on-all-architectures/16871](https://discourse.ubuntu.com/t/groovy-to-use-grub2-for-booting-installer-media-in-any-modes-on-all-architectures/16871)

but providing specifics as to the release you are trying to boot (and if *groovy*, the date of the *daily* may also be helpful).

As for the latitude laptops, there are a number of bugs related to failure to boot, but without specifics as to your release, you may mean something different to what I'm thinking of (given I'm thinking of *groovy* but you may mean a different release, let alone the *daily* in question)

If issues relate to cdimages/cd-boot-images-amd64 etc, all *flavors* and main Ubuntu are usually impacted.  Me, I test mostly in Lubuntu, but confirm issues using other *flavors* and main Ubuntu usually too.

It is the daily images I'm talking about. Prior releases all work fine.

---

### Post by sudodus on 2020-10-16
> **kansasnoob said:**
> How can you tell now whether you've booted in UEFI or BIOS mode? I still have some old Intel boards that can be setup either way.

```

test -d /sys/firmware/efi && echo efi || echo bios

```

See also [this link](https://help.ubuntu.com/community/Installation/FromUSBStick#Test_if_running_in_UEFI_mode)

---

### Post by ajgreeny on 2020-10-16
This may or may not be important  re this particular query, but I have now two versions of groovy running in KVM as virtual OSs, both of which booted automatically as UEFI without any input from me.
In both cases I just let the KVM system install by default and all was apparently good until grub failed to install as it should because there was no EFI partition.
Being new to KVM, I was not aware that there is a choice of BIOS or UEFI when configuring the virtual disk at the start of installing.

My surprise, however, was that UEFI  was the way it installed even if you took  no action to chose that mode. Now I know about this it is easy to overcome this problem but it took me several attempts.

---

### Post by kansasnoob on 2020-10-17
> **ajgreeny said:**
> This may or may not be important  re this particular query, but I have now two versions of groovy running in KVM as virtual OSs, both of which booted automatically as UEFI without any input from me.
In both cases I just let the KVM system install by default and all was apparently good until grub failed to install as it should because there was no EFI partition.
Being new to KVM, I was not aware that there is a choice of BIOS or UEFI when configuring the virtual disk at the start of installing.

My surprise, however, was that UEFI  was the way it installed even if you took  no action to chose that mode. Now I know about this it is easy to overcome this problem but it took me several attempts.

That's a bit worrisome to me. Some of these older Intel boards I'm using offer the UEFI boot option but it's such an early version of UEFI it's really just junk. Like DG43xx and DB43xx which are circa 2009 :redface:

---

