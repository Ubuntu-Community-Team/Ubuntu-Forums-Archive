---
title: "Ubuntu Cinnamon Remix failing to boot with luks encrypted drive on Yoga 9i"
date: 2021-07-13
forum: Ubuntu/Debian BASED
---

### Post by getut on 2021-07-13
I am having a bear of a time getting Ubuntu Cinnamon Remix 21.04 running on a Lenovo Yoga 9i. I cannot get it to boot fully when I use full disk encryption. I have gotten it to install and run without encryption in legacy mode. I would prefer UEFI over legacy, but I absolutely must have encryption as this is a business laptop. I'm a long time linux user, but this is the worst time I've ever had getting linux on one.

Here are some notes on what I've tried and the settings involved:

UEFI on, Secure Boot on, Intel SGX on = won't even boot USB installer (hangs with black screen just after boot selection for try ubuntu or safe mode, even with all the kernel options I have found)
UEFI on, Secure Boot off, Intel SGX on = won't even boot USB installer (hangs with black screen just after boot selection for try ubuntu or safe mode, even with all the kernel options I have found)
UEFI on, Secure Boot off, Intel SGX off, no drive encryption = boots USB media and installs, final installation boots and runs fine although useless for me without encryption
UEFI on, Secure Boot off, Intel SGX off, full disk encryption = boots USB media and installs, final installation prompts for password then pauses a long time and drops to busybox prompt with no errors displayed

Legacy mode on, Boot Legacy first, no drive encryption = boots USB media and installs, final installation boots and runs fine although useless for me without encryption
Legacy mode on, Boot Legacy first, no drive encryption = boots USB media and installs, final installation prompts for password then pauses a long time and drops to busybox prompt with an error about Volume Group "luks" not found.

The closest article I have found to try to manually fix the encrypted disk error is this: [https://askubuntu.com/questions/567730/gave-up-waiting-for-root-device-ubuntu-vg-root-doesnt-exist](https://askubuntu.com/questions/567730/gave-up-waiting-for-root-device-ubuntu-vg-root-doesnt-exist)

The post by lumbric about halfway down seemed to be the most relevant but the cryptab created by the install lists the drive by UUID in the format luks-<UUID> UUID=<UUID>. I can run the command below and it goes through with no errors but the vgscans don't seem to be working properly.

sudo crypsetup luksOpen /dev/nvme0n1p2  luks-<UUID>

All of the mounts work, but the DNS commands don't seem to get DNS working in chroot. In hopes that I actually was not missing the packages I went ahead and tried the update-initramfs command and it worked and it got me further. But it now drops me to a busybox prompt with the error Volume Group "luks" not found.

On the outside possibility that cryptab was not parsing the luks-<UUID> correctly, I just shortened it to luksmain with no dash and then went through the whole process a 2nd time also using luks main in the /dev/mapper command. On the next boot attempt, I got exactly the same error Volume Group "luks" not found.

I'm stuck. I can't get this thing to boot with full disk encryption on it and need some help... I have been installing and trying this thing with every option under the sun for 10+ hours today.

---

### Post by Frogs Hair on 2021-07-14
Moved to Ubuntu/Debian Based.

---

