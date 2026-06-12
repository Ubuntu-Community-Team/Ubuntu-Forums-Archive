---
title: "[GUIDE] Installing Xubuntu 14.04 on Lenovo Thinkpad E540"
date: 2016-02-01
forum: Ubuntu, Linux and OS Chat
---

### Post by s-breedveld on 2016-02-01
I wrote this installation guide some years ago (6 Nov 2014), but had to move it. I think this is a good place to repost it for future references.

I decided to write this small guide as I figured out that more people  may want to install (X)ubuntu on their E540. The bottom line is: you  have a well running dual-boot Linux/Windows system out of the box, but  there are a few steps to be taken to fix some basic functionality.

[SIZE=4]  **Before you begin**[/SIZE]

 Before installing Linux next to Windows, take the usual steps. The  E540 is installed with Windows 8.1 by default, so setup and configure  your Windows, install and update drivers, optimise your SSD if any, etc.  When you are perfectly happy, download the Xubuntu image to an USB key.  I am not sure if a DVD would work well, as booting from the DVD drive  requires you to disable UEFI and Secure Boot, possibly complicating  dual-booting to Windows after the installation.

 
Of course it is possible to remove Windows altogether as well, but I  find it convenient to have a small Windows partition available.

[SIZE=4]  **Installing Xubuntu 14.04**[/SIZE]

As we will be shrinking partitions, make sure that Windows is shut  down fully before restarting (by default, Windows 8 goes into some  hibernate mode). You can do this by hitting the Windows key + X, and  then shut down.

Turn on the laptop again, and quickly hit F12 to open up the boot  menu. Boot from the USB key and select “Try Xubuntu without installing”.  Then open up a terminal and run

 ```

$ sudo gparted

```

 Then resize your Windows main partition, add a ext4 partition and a swap partition.
[I]
Important: remember your swap partition index (e.g. /dev/sda6) as  you need this later! Also make your swap a few MiB larger than your  memory.[/I]

Apply changes.

Now start the Xubuntu installer (either from the desktop or reboot  again), and manually assign the partitions you just created. Then  continue.

[SIZE=4]**Booting**[/SIZE]

 When the installer finishes, you should have a dual-booted  Xubuntu/Windows system, with UEFI and Secure Boot on! This is one of the  hard things that simply works out-of-the-box now. However, booting to  Windows can only be achieved using the UEFI boot manager (F12), and  changing the boot order should also be done in the BIOS.

 Using GRUB or the Windows boot manager will not allow you to boot to  the other system! This is due to the UEFI bootloader, and actually one  of the perks of it (although it may seem like a nuisance at first).

Now make sure both Xubuntu and Windows boot well. For Xubuntu, all  drivers should be working: WiFi, GPU (I only have the Intel HD), sound,  etc., and most super-buttons as well: screen brightness (a better fix is  below), audio, etc.

[SIZE=4]**Fixing**[/SIZE]

 So almost everything works, but swap, suspend, hibernate and better  screen brightness control does not. So far I have been unable to get  Hibernation to work reliably, but I will describe the steps below, which  basically fixes all loose ends I found.

All items can be found distributed over the internet, but it is convenient to put them all in one place.

[SIZE=3]**Swap**[/SIZE]

 If you enabled the encryption of your home directory, CryptoSwap is  also enabled by default, but the functionality is broken. This is  because the UUID identifier is overwritten due to the encryption. To fix  this, first reformat the swap partition. *(Note: make sure sda6 is your swap parition!!!)*

```

$ sudo mkswap /dev/sda6
Setting up swapspace version 1, size = 8491004 KiB

no label, UUID=b3cef7db-3bc8-4d72-baf7-9cd95ba9a188

```

Copy the UUID to your clipboard.

Now if you intend to use Hibernation, you can skip the next step, but  there is no harm in doing it anyway to correct your original  installation.

 Edit */etc/crypttab* to reflect the new UUID, and also add the *offset=36*  to the options. This prevents that the UUID is overwritten at each  reboot. In the end, crypttab should look something like this:

```

$ cat /dev/crypttab

cryptswap1 UUID=b3cef7db-3bc8z-4d72-baf7-9cd95ba9a188 /dev/urandom swap,offset=36,cipher=aes-cbc-essiv:sha256

```

Now that we are at it, also edit */etc/fstab* to update the UUID for the old swap partition.

[SIZE=3] **Hibernate**[/SIZE]

 For some reason, Hibernate is disabled by default. *I also cannot get it to work reliably: my session frequently returns frozen.* Anyway, it is a good idea to set things right in case you want to try it.
 To enable Hibernation, edit */etc/fstab*, disable the cryptswap line and enable the default swap partition, but now using the correct UUID:
```


# swap was on /dev/sda6 during installation
 
UUID=b3cef7db-3bc8-4d72-baf7-9cd95ba9a188 none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0

```

Now edit */etc/default/grub*, and update the GRUB_CMDLINE_LINUX_DEFAULT with the swap UUID to be able to resume the session.

```

GRUB_CMDLINE_LINUX_DEFAULT="resume=UUID=b3cef7db-3bc8-4d72-baf7-9cd95ba9a188 quiet splash"

```

Then update grub:
```

$ sudo update-grub

```

Now enable the Hibernate option in the Xfce menu. Edit:
 */etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla*
 with:


```

[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
 
[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate
ResultActive=yes

```

More information on Hibernate can be found [here]("http://www.jasom.net/how-to-enable-hibernation-in-lubuntu-14-04") and [here]("http://ubuntuhandbook.org/index.php/2014/04/enable-hibernate-ubuntu-14-04/").

[SIZE=3]**Suspend**[/SIZE]

 Suspend-to-ram works fine, but waking-up does not. This is a bug, but  can be circumvented by disabling USB3.0 and USB-Always-On options in  the BIOS.

After this, suspend from RAM works.

[SIZE=3]**Screensaver**[/SIZE]

 Another problem with Suspend and Hibernate is the default XFCE screen saver, Light Locker. This is a known [bug]("https://bugs.launchpad.net/ubuntu/+source/xubuntu-default-settings/+bug/1303736"), and despite being marked as fixed, I still have this problem. At one point I gave up, and decided to install the old *xscreensaver* application, as having an unlocked laptop is not an option.

```

apt-get remove --purge light-locker light-locker-settings

apt-get install xscreensaver

```

Then update the power-manager settings by enabling the screen saver  upon suspend/hibernate. Go to the Power Manager Settings -> Advanced  and tick “Lock screen when going for suspend/hibernate”.
 Also ensure that in the *xfce4-settings-manager* the following items are ticked:

```

lock-screen-suspend-hibernate = ticked

logind-handle-lid-swtich = ticked

```

[SIZE=3]**Display Brightness**[/SIZE]

 When you adapt the display [brightness]("https://wiki.ubuntu.com/Kernel/Debugging/Backlight"),  you will notice that you have ~7 steps, but only 3 different brightness  settings are active. Add this to the GRUB_CMDLINE_LINUX_DEFAULT in */etc/default/grub .*

```

acpi_backlight=vendor thinkpad-acpi.brightness_enable=1

```

Update grub again (*sudo update-grub*), reboot and you will notice that you have 7 steps now! Still not as much as normal, but acceptable.
  [B]
[SIZE=4]Other tips[/SIZE][/B]

[SIZE=3] **Swappiness**[/SIZE]

 If you have an SSD you might want to reduce your [swappiness]("https://sites.google.com/site/easylinuxtipsproject/ssd"), in order to reduce the amount of swap actions. Edit */etc/sysctl.conf* and add:

```

# Sharply reduce swap inclination
vm.swappiness=1

```

[SIZE=3]**No suspend when lid closes**[/SIZE]

 For some reason, the settings using the XFCE Power Manager were not  working directly. I do not want the laptop to suspend when I close my  lid. Hereto I edit */etc/systemd/logind.conf *and manually set:

```

HandleLidSwitch=ignore

```

[SIZE=4]**That’s it!**[/SIZE]

 Now you should have an operational Xubuntu installation with all  nuisances removed. If I ever get Hibernation to work properly, I will  update this post.

---

### Post by ajgreeny on 2016-02-01
Not a support request.
Moved to **Ubuntu, Linux & OS Chat**

---

### Post by mörgæs on 2016-02-01
Thanks for posting. Please post a short summary in the [list of compatible hardware]("http://ubuntuforums.org/showthread.php?t=1543006").

---

### Post by s-breedveld on 2016-02-03
Done! Thanks for moving.

---

### Post by oldgraf on 2016-02-18
"Suspend-to-ram works fine, but waking-up does not. This is a bug, but   can be circumvented by disabling USB3.0 and USB-Always-On options in   the BIOS."

There is a long time ago new BIOS from Lenovo. 
<2.18>
 - (New) Enabled Refresh rate 2x feature.
 - (Fix) Fixed an issue related to S3 resume failure on Ubuntu.

---

