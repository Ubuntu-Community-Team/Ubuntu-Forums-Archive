---
title: "Manual Installation Seems Not To Function Correctly"
date: 2024-10-12
forum: Ubuntu Development Version
---

### Post by Rubi1200 on 2024-10-12
Maybe I am missing something, but recent versions of Ubuntu seem to have made Manual Installation much less functional.

My test case with a VM and Oracular Oriole:

I formatted the vd drive to gpt and created 3 partitions, 16GB for root 6GB for home and 3GB as swap.

Started the installer, choosing Manual Installation, but even clicking Change and setting to reformat as ext4 and linux-swap did nothing.

The button for Next was greyed out, no options to force it through that I could see.

Has anyone else encountered this?

Do I need to create a larger vd at the outset? What would be recommended?

---

### Post by 1fallen on 2024-10-12
MAFoElffen and I talked about this a while back, all my and his install recipes went out the back door with the new installer.

Wish I had better news for you Rubi1200

---

### Post by tea for one on 2024-10-12
> **Rubi1200 said:**
> Maybe I am missing something, but recent versions of Ubuntu seem to have made Manual Installation much less functional
Certainly a slightly different procedure from the previous Ubiquity installer.
After you have chosen Manual Installation, then immediately choose "Device for boot loader installation"
This will automatically create an ESP size 1.13GB
Consequently, you can then add root, home and swap as required.

If you've booted the installer in Legacy mode, perhaps it's a similar procedure?
I haven't tested this mode.

---

### Post by Rubi1200 on 2024-10-13
> **tea for one said:**
> Certainly a slightly different procedure from the previous Ubiquity installer.
After you have chosen Manual Installation, then immediately choose "Device for boot loader installation"
This will automatically create an ESP size 1.13GB
Consequently, you can then add root, home and swap as required.

Is this documented somewhere or did you discover it by testing/experimenting?

Booted in UEFI mode and did as you said. The ESP partition is exactly the size you mention.

Added this time root and home partitions. Next button was not greyed out and was able to complete installation as normal.

I will also test what happens in Legacy mode and report back here.

Forgot to mention: I did not format the virtual disk before running Manual Installation. Will also test if that works with this method.

Thanks.

---

### Post by Rubi1200 on 2024-10-13
> **1fallen2 said:**
> MAFoElffen and I talked about this a while back, all my and his install recipes went out the back door with the new installer.

Wish I had better news for you Rubi1200

Appreciate the feedback :-)

---

### Post by Rubi1200 on 2024-10-13
Results:

Whether in Legacy or UEFI mode for booting, once you get to Manual Installation all you need to do is click + on the free space and choose to add a root partition (the simplest form).

In both cases, a boot partition was automatically added. For BIOS, it was 1.05MB and for ESP 1.13GB.

Installation can then proceed as normal.

In my test, there was no need to first select the device for the bootloader in either of these scenarios.

I still need to test whether partitioning with GParted before running the installer will have the same results.

Update: Yes, it is possible to use GParted first to create an ESP partition and then run the installer in Manual mode.

However, the options for formatting root or home partitions are limited to standard formats such as ext4, xfs, btrfs etc.

Also, as has been mentioned in other threads on the forums, there does not seem to be an option to encrypt in manual mode, whether the root or home partition.

---

### Post by tea for one on 2024-10-13
> **Rubi1200 said:**
> Is this documented somewhere or did you discover it by testing/experimenting?
Discovered by experimentation
> **Rubi1200 said:**
> Whether in Legacy or UEFI mode for booting, once you get to Manual Installation all you need to do is click + on the free space and choose to add a root partition (the simplest form).
In both cases, a boot partition was automatically added. For BIOS, it was 1.05MB and for ESP 1.13GB.
Installation can then proceed as normal.
In my test, there was no need to first select the device for the bootloader in either of these scenarios.
In this case the BIOS partition and the ESP are automatically created as partition 2

If you immediately choose "Device for boot loader installation", the ESP is partition 1 (In Legacy mode, the BIOS partition is also partition 1)
May be easier to manipulate partitions in the future if the ESP or BIOS were always first?

---

### Post by 1fallen on 2024-10-13
> **tea for one said:**
> 
May be easier to manipulate partitions in the future if the ESP or BIOS were always first?
+1

---

### Post by Rubi1200 on 2024-10-14
I agree.

This was just for testing purposes.

As an aside, I tested Kubuntu 24.10 in a VM and manual installation has way more options available, including adding LVM, LUKS, various filesystem types etc. etc.

I'm wondering what the logic is/was from the devs to, for lack of a better description, dumb down manual installs in vanilla Ubuntu?

---

