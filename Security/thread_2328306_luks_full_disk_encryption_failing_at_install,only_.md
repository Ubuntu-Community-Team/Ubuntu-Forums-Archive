---
title: "luks full disk encryption failing at install,only me?"
date: 2016-06-19
forum: Security
---

### Post by a.dusty.trail on 2016-06-19
I've been trying to set up luks full disk encryption on two computers (hp pavilion acer vertaron) 
I was trying to set up luks on only part of the drive originally but now I've found that using luks on the entire drive is just failing to boot to grub. 
With the alternate lubuntu 16.04install disk I get no errors during install but it hangs with that dark blue screen and noting else.
With the desk top install 16.04 I get errors to turn swapoff to various partman errors and an outright failure to install grub with the dialog to change grubs location failing to respond to any action.

I've tried the two systems I readily have accessible to test on with various sata hard drives ranging in size from 80gb to 500th

All with the same end result. 
Not a bootable system.

Is any one else having issues installing with luks guided full disk encryption.
(No point even trying to find an up to date tutorial to setup luks sharing a hard drive with Any other partitions if the basic install is broken)

Or is it just me.

(We are taking I took both systems down to just motherboard and one hard drive. Booting from a sub stick. Checked my iso images with the md5 they are fine, the systems are offline systems)

---

### Post by cariboo on 2016-06-21
Make sure you aren't encrypting /boot.

---

### Post by sudodus on 2016-06-21
I think the problem with the ***alternate*** install is that you don't see the prompt for the passphrase. You can still type it (the passphrase) and press the Enter key to continue the boot process. If you remove the boot options 'quiet splash', you will see the prompt for the passphrase. (This is caused by a known bug.)

I think the problem with the ***desktop*** install is that the installer does not accept zram (when installing with 'encrypted disk'). So if you 'Try Lubuntu' and swapoff (and have enough RAM for the installer to work without zram) before you start the installer, the installation with 'encrypted disk' will succeed. You still won't see the prompt for the passphrase unless you remove the boot options 'quiet splash'.

-o-

These bugs were discovered during iso-testing before Lubuntu 16.04 LTS was released, but nobody had both time and knowledge to fix the bugs. (Actually the bug due to zram is very old and affects also previous versions of Lubuntu, but not the other flavours of Ubuntu. Only Lubuntu uses zram in the live session.) Let us hope that these bugs will be solved, when the first point version 16.04.1 LTS is released in July or early August.

---

### Post by a.dusty.trail on 2016-06-22
Strange I've never seen the lubuntu desktop issue before. But if it was not a priority to fix in the past I expect like many things it will be there for a long time.

Either way, those are some pretty serious issues to go to press with on a long term support distribution.
Very disappointing.

---

### Post by c0n7r4 on 2016-06-22
if it looks like its not booting, have you tried the 'esc' key trick? try tapping it several times...

---

### Post by xen3 on 2016-06-23
I have no clue because I don't use automated installs. If you feel free though to talk, if you want, and if you need that, if you have a Jabber/XMPP account (such as at kdetalk.net) you could try to message me if you need it :p (xennex83@kdetalk.net). (To get one at kdetalk.org, email [EMAIL="bcooksley@kde.org"]bcooksley@kde.org[/EMAIL]). (Client registration is broken).

Just for a little background:


[LIST]
[*]normally the automated install won't do an encryption of your boot partition, hardly anyone knows how to do that, and the automated install will just encrypt your root which is usually /dev/sda5, and place appropriate files in your /initrd. Successfully booting a LUKS container this way is only dependent on about 3-4 factors:
[/LIST]

[LIST]
[*]having the appropriate /etc/crypttab
[*]generating your initrd based on an appropriate /etc/crypttab (update-initramfs -u).
[*]your LUKS container is /dev/sda5 (for example) and contains an LVM setup which contains your root partition (and possibly swap and home)
[*]more is *not really needed*.
[/LIST]

To install Grub in /dev/sda, not much is required except the following:
[LIST]
[*]the first partition must start at sector 2048, and not at some smaller number such as 63 or something.
[/LIST]

You can verify this by running [COLOR=#0000ff]sudo parted /dev/sda unit s print[/COLOR] or just running [COLOR=#0000ff]for f in /dev/sd?; do sudo parted $f unit s print; done [/COLOR]to list all of them.

Press CTRL-C if needed there.

So the requirements for booting LUKS in its default configuration are very minimal. Using the proper /etc/crypttab your "boot image" (initrd) will be correctly created, I'm sure of that.

Setting up LUKS completely manually from the installer, normally comes down to:

[LIST]
[*]opening a TTY or a Konsole from the Live environment
[*]creating a partition table and 3 partitions (on msdos label) which are then boot at /dev/sda1, an extended partition for the rest of the drive, and then your LUKS at /dev/sda5. (First logical partition within the extended partition). So that is basically only 2 partitions.
[*]creating an ext2 filesystem (my preference) on /dev/sda1, which partition should be about 500M or a bit smaller depending on the size of your drive.
[*]creating an ext3 or ext4 filesystem on all the rest, but you don't have those volumes yet --- use ext4 if you have a SSD.
[/LIST]

[LIST]
[*]creating the LUKS container on /dev/sda5 is not more difficult than running [COLOR=#0000ff]cryptsetup luksFormat /dev/sda5[/COLOR] and entering your password (twice).
[*]to open it after creation, type [COLOR=#0000ff]cryptsetup open /dev/sda5 sda5_crypt[/COLOR].
[*]now create your LVM physical volume inside of that: [COLOR=#0000ff]pvcreate /dev/mapper/sda5_crypt[/COLOR].
[*]now create your volume group, you will have to choose a name for it, but "linux" or "ubuntu" would work fine: [COLOR=#0000ff]vgcreate ubuntu /dev/mapper/sda5_crypt[/COLOR].
[*]now create your root filesystem, and decide how big it must be. I recommend 20GB and dumping the rest in some home or data partition, but you will first want a proper root of sufficient size: [COLOR=#0000ff]lvcreate ubuntu -n root -L 20G[/COLOR] ([I]this will be 20 "real" gigabytes, so 20 x 1024 megabytes)
[/I]
[*]now create your swap partition. I usually recommend making it the same size as your RAM, but that might dwarf your root if you have a lot: [COLOR=#0000ff]lvcreate ubuntu -n swap -L 8G[/COLOR][COLOR=#000000].
[/COLOR]
[*]now create your home or data partition. Just give it all the rest, unless you need more specialized volumes first: [COLOR=#0000ff]lvcreate ubuntu -n home -l 100%free[/COLOR].
[*]unless it is important to you, do not format those partitions yourself, just let the installer do it later on.
[/LIST]

[LIST]
[*]if you had mounted any partitions (we have not done this) you must now first unmount them to proceed.
[*]start the installer, enlarge the window, move the column separator to the right, and start **manual** partitioning. You won't partition, you are just going to select mountpoints and formatting.
[*]select /dev/ubuntu/root as the / filesystem of either ext4 or ext3 preference
[*]select /dev/sda1 as the /boot filesystem, of ext2 preference
[*]select /dev/ubuntu/home as the /home filesystem, of probably ext4 or ext3 preference
[*]now let it format your partitions (including swap) and proceed with the installation.
[/LIST]

Now comes a bit of a hard part. You will let it install grub on /dev/sda (if that is your harddrive).
[LIST]
[*]notice that a fully fledged but modest root partition takes up about 12 gigabyte, but this normally also the place for temporary files, and some programs by default use it for creating e.g. DVD images. At this point you would have 8GB free. That is enough unless you install games or want to author blurays there ;-). You could always **link** those directories it wants to use to your home partition. You can even make /home a directory on your home partition (instead of the entire thing) and then **bind mount it **to your actual /home, but this is rather avanced (for now). But the **steam** program for example can be told to put its games in your home directory (and it normally does). For this reason it seems that your home as the **biggest** filesystem is not such a bad idea (for most people).
[/LIST]

Let it just complete the installation. It will have mounted your root filesystem on /target during installation, but it would normally unmount it after. We will remount it: [COLOR=#0000ff]mount /dev/ubuntu/root /target[/COLOR][COLOR=#000000]. We will mount boot on top of that: [/COLOR][COLOR=#0000ff]mount /dev/sda1 /target/boot[/COLOR][COLOR=#000000]. Unless you have done advanced stuff, there are no packages to install. First we will set up the crypttab now:
[/COLOR]

[LIST]
[*]use your favourite editor to edit /target/etc/crypttab. Add a line of <name> <device> none luks, which becomes [COLOR=#000080]sda5_crypt /dev/sda5 none luks[/COLOR][COLOR=#2f4f4f],[/COLOR] for us now. Now we will regenerate initrd. There is no need for encrypted swap, it is already in our vault (volume).
[*]We must enter the /target system as a "chroot":
[*][COLOR=#0000ff]mount --bind /dev /target/dev[/COLOR]; [COLOR=#0000ff]mount --bind /proc /target/proc[/COLOR]; [COLOR=#0000ff]mount --bind /sys /target/sys[/COLOR].
[*][COLOR=#0000ff]chroot /target[/COLOR][COLOR=#000000].[/COLOR]
[*](there are no "dots" after any of these commands, no . ).
[*][COLOR=#0000ff]update-initramfs -u[/COLOR]
[*][COLOR=#0000ff]update-grub[/COLOR]
[*][COLOR=#0000ff]grub-install /dev/sda[/COLOR]
[*][COLOR=#000000]We can verify the cryptsetup installation by running: [/COLOR][COLOR=#0000ff]lsinitramfs /initrd.img | grep cryptsetup[/COLOR] -- this verifies that your /etc/crypttab was correct, or at least good enough to get this done. The [COLOR=#000080]/sbin/cryptsetup[/COLOR] binary must be present in that output. Grub itself needs no special crypt parameters for our case. We might need a "resume=" kernel parameter for in case we want to hibernate our system using the encrypted swap (on our volume) but that might be taken care of already, I don't know. This system should now already be able to boot. If [COLOR=#0000ff]grub-install[/COLOR] fails, add the [COLOR=#0000ff]-s [/COLOR]flag and try again, it skips some checks.
[*]I can think of nothing else that can make it bootable if it doesn't already boot now. Check your /etc/fstab. Normally you wouldn't need to change anything, but you can change UUIDs to LVM paths if not used (/dev/ubuntu/root for /, /dev/ubuntu/swap for swap). The /dev/sda1 boot partition will be referenced by UUID. If you want, you can add a filesystem label to it and then change your fstab to that:
[*][COLOR=#0000ff]tune2fs /dev/sda1 -L boot[/COLOR][COLOR=#000000], and now mount it by referencing /dev/disk/by-label/boot instead of the UUID, this makes it more comprehensible.[/COLOR]
[*][COLOR=#000000]If you use an SSD as system partition (or anything) you may want to add [/COLOR][COLOR=#0000ff]discard[/COLOR][COLOR=#000000] and [/COLOR][COLOR=#0000ff]noatime[/COLOR][COLOR=#000000] options. You can also fix this in the filesystem itself or themselves:[/COLOR]
[*][COLOR=#000000](at least for discard: [/COLOR][COLOR=#0000ff]tune2fs /dev/ubuntu/root -o discard[/COLOR][COLOR=#000000] -- this will now be the default option for mounting it) -- and repeat for /home if necessary: [/COLOR][COLOR=#0000ff]tune2fs /dev/ubuntu/home -o discard[/COLOR][COLOR=#000000]. This implies having chosen the [/COLOR][COLOR=#a52a2a]ext4 [/COLOR][COLOR=#000000]filesystem because it is an option [/COLOR][COLOR=#a52a2a]ext3[/COLOR][COLOR=#000000] does not have.[/COLOR]
[/LIST]
[COLOR=#000000]
Exit the chroot by typing [/COLOR][COLOR=#0000ff]exit [/COLOR][COLOR=#000000]and if you are lucky, your system will now (automatically) boot into a functioning GRUB that loads the initrd.img from the unencrypted boot but the REST OF THE SYSTEM is encrypted and the initrd.img takes care of loading and unlocking that. Your GRUB needs to have no knowledge of any encryption because the parameter it passes to the kernel is just going to be /dev/ubuntu/root in the ideal case (not using UUID) or otherwise an incomprehensible string that points to the same. This is the parameter to the root filesystem that it will load (that the kernel will load) and your initrd will have ACCESS to it after unlocking it (using the password prompt on your screen). And all LVM volumes will also normally all be automatically loaded (and activated) once the LUKS container opens, and the initrd does that for you.

The installer will already have made your user inside the encrypted container. It has installed everything inside of the encrypted container (except the boot files on /dev/sda1). There is nothing but the fact that you are using encryption, present on any visible disk. There is a tiny bit of knowledge on the fact that you are using LVM, visible from the outside. It is not much and pretty standard and expected.

For me personally I use different setups but this is the easiest and closest to what the installer would normally do, if you chose the automatic setup, and it worked.
[/COLOR]

---

### Post by xen3 on 2016-06-23
To recap one thing to do take note of if nothing else, is that your first partition may not start at sector 63 but it needs to start at 2048 or above. Keep that in mind. For GPT disks you need a BIOS Boot partition at sector 2048 with a size of 2M (2048 begin, 6143 end, size 4096s or two megabytes). I am not sure about Lubuntu and its bugs of course. I just use Ubuntu and Kubuntu, in that sense. Regards.

---

