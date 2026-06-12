---
title: "Remove need for sudo for mount/umount"
date: 2010-02-17
forum: Security
---

### Post by narnie on 2010-02-17
Hello,

I'm trying to remove the need to use sudo to mount (in particular, binding).

Modifying /etc/sudoers using visudo, I have tried:
```

%admin ALL=NOPASSWD: /usr/bin/mount
%admin ALL=NOPASSWD: /usr/bin/umount
```
and
```

%admin ALL=(ALL) NOPASSWD: /usr/bin/mount
%admin ALL=(ALL) NOPASSWD: /usr/bin/umount
```

Both return 

```
$ mount --bind /home/woodnt/Dir1 /home/woodnt/Dir2
mount: only root can do that
```

I have logged out and in (and even rebooted) to no avail.

What am I missing here?

With thanks,
Narnie

---

### Post by sisco311 on 2010-02-17
You still have to use sudo to run the commands, but it will not prompt you for a password.

---

### Post by Zimmer on 2010-02-17
Have you thought of using pmount instead ?
[https://launchpad.net/pmount](https://launchpad.net/pmount)

or adding the disk mounter  to the Gnome panel??

---

### Post by bodhi.zazen on 2010-02-17
Or better, add an entry in fstab. use the user or users option ;)

```
/home/woodnt/Dir1 /home/woodnt/Dir2 none bind,user 0 0
```

Now you can simply

```
mount /home/woodnt/Dir2
```

No need to edit system files ;)

To answer you question, if you still need to enter a password with sudo, it would be because your user is listed twice in /etc/sudoers, this causes conflict

%admin ALL=(ALL) ALL[FONT=monospace]
[/FONT]%admin ALL=(ALL) NOPASSWD: /usr/bin/mount[FONT=monospace]
[/FONT]%admin ALL=(ALL) NOPASSWD: /usr/bin/umount

These three lines will conflict with each other ^^

So, first, add multiple commands on the same line
[FONT=monospace]
[/FONT]%admin ALL=(ALL) NOPASSWD: /usr/bin/mount[FONT=monospace],[/FONT]/usr/bin/umount

And second make sure there are no conflicts ;)

If your user matches more then one line, the LAST match is often what is applied (meaning you may have lost sudo access).

See man sudoers for details.

---

### Post by DawieS on 2010-02-18
After upgrading to 9.10, I have spent hours on testing different combinations of configurations in the **/etc/sudoers** and **/etc/fstab** files, all to no avail.

My set-up is as follows:

- 1 Internal drive (ext3 with 9.10 file system, /home for temp storage, mostly empty).
- 3 External drives (**ext3** and **ntfs** file systems, mostly switched off).

I wanted to be able to switch on a drive and mount/unmount on demand, without having to type a password. Testing different combinations of mount options resulted in:

- drives appearing doubled up in the file browser, with error messages if clicked on the wrong choice.
- drives correctly mounted, but unable to unmount and switch off.
- drives cross-mounted to the wrong drive in the file browser, even if using the more robust UUID identification in **/etc/fstab**.
- **ext3** drives mounting/unmounting correctly, but unable to mount **ntfs** drives.
- drives mounting/unmounting correctly only once, thereafter unable to mount/unmount, have to reboot to mount again.

In the end the solution was:

- Leave the** /etc/sudoers** file as per the original installation (no mention of mount/umount).
- Leave the **/etc/fstab** file as per the original installation, containing only lines for the CD/DVD drive and the installation/boot drive. Do not add any lines for other drives, as this will result in the problems described above.
- Edit the **/usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy** file by using the **sudo gedit** command in a terminal.
Look for this:
<action id="org.freedesktop.devicekit.disks.filesystem-mount-system-internal">
Find something like this:
<defaults>
    <allow_any>no</allow_any>
    <allow_inactive>no</allow_inactive>
    <allow_active>[COLOR=Red]auth_admin_keep[/COLOR]</allow_active>
</defaults>
Change the highlighted one to:
    <allow_active>[COLOR=Red]yes[/COLOR]</allow_active>
Save, exit, and reboot.

I have found this solution somewhere on a forum - I would like to give the person credit for it but I could not find it again rightaway.

Please note that this change may be overwritten with an update, and may need to be redone thereafter. Also please check whether you are enabled to **Mount user-space filesystems** in the **System - Administration - Users and Groups - Properties** tab.

I do not see the need for requiring a password in a normal home environment for mounting disks. Even in a business or office environment, the risk of damage to the operating system is increased if everyone now has the root password, just to be able to mount disks and save his work. I would rather go for restricting user permissions, if file access restrictions is required for some reason.
:grin:

---

### Post by bodhi.zazen on 2010-02-18
> **DawieS said:**
> I do not see the need for requiring a password in a normal home environment for mounting disks. Even in a business or office environment, the risk of damage to the operating system is increased if everyone now has the root password, just to be able to mount disks and save his work. I would rather go for restricting user permissions, if file access restrictions is required for some reason.
:grin:

I do not think you understand how sudo works.

This is why you should use sudo. Sudo uses the USERS password, not root, and you may edit /sec/sudoers to give fine grain control over what a user may do with sudo.

In addition, sudo allows superior logging.

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

su , as used by Fedora and other distros, uses the root password and is all or none.

==========

Second, although I do not use gnome, I have not seen the behavior you describe. 

Without your posting of your configuration efforts it is hard to advise you with any detail.

See: [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by DawieS on 2010-02-18
> I do not think you understand how sudo works.I do understand how sudo works. I may have misnamed it by calling it 'root'. Lets just say it is the only password on my machine. I have chosen to boot without a login screen during installation, since I am the only user on my machine.

> Second, although I do not use gnome, I have not seen the behavior you describe.With Ubuntu 9.04 a sudo password was not required to mount/unmount ntfs drives or partitions. This behaviour started with upgrading to Ubuntu 9.10.

I don't know whether this was intentional or a bug. However, by making the change as suggested in the solution results in gnome behaving exactly as it did in 9.04. Mounting/unmounting can be done with the click of a button.

I have noticed lots of other people complaining about it. However most of the advice given referred to adjustments in the /etc/sudoers and /etc/fstab files. This made matters even worse, and some people even returned back to 9.04, and are now living without important security updates.

> This is why you should use sudo. Sudo uses the USERS password, not root, and you may edit /sec/sudoers to give fine grain control over what a user may do with sudo.A drive cannot be fine tuned into mounting. It either mounts, or it doesn't, and I have tested all possible combinations in the book.

I am willing to take a side bet, that I will eat my hat, if you succeed in mounting/unmounting multiple ntfs drives with the click of a button from a default 9.10 installation without making the change as suggested.

---

### Post by bodhi.zazen on 2010-02-18
> **DawieS said:**
> I am willing to take a side bet, that I will eat my hat, if you succeed in mounting/unmounting multiple ntfs drives with the click of a button from a default 9.10 installation without making the change as suggested.

Well, thank you for the info on NTFS partitions.

If I find the time to test it I will, if nothing else out of interest. I may have a ntfs partition around somewhere ...

---

### Post by sisco311 on 2010-02-18
> **DawieS said:**
> 

I don't know whether this was intentional or a bug. However, by making the change as suggested in the solution results in gnome behaving exactly as it did in 9.04. Mounting/unmounting can be done with the click of a button.



It's not a BUG, I think it's a sane & safe default setting. Admin users may mount external disks without being prompted for a password, but mounting an internal disk requires password authentication. It's a default setting & as you pointed out it's relatively easy to change it by editing relevant the policykit *action* file.

---

### Post by bodhi.zazen on 2010-02-18
> **sisco311 said:**
> It's not a BUG, I think it's a sane & safe default setting. Admin users may mount external disks without being prompted for a password, but mounting an internal disk requires password authentication. It's a default setting & as you pointed out it's relatively easy to change it by editing relevant the policykit *action* file.

I believe the "bug" s/he is referring to is the fact that it could not be "fixed" by modifying /etc/sudoers or /etc/fstab

However, no offense, from the postings I am not sure s/he understands /etc/sudoers and/or sudo.

Although I am somewhat familiar with various fstab options, I have not tried an entry for a ntfs partition in some time now, so it is possible the syntax has changed.

---

### Post by sisco311 on 2010-02-18
> **bodhi.zazen said:**
> I believe the "bug" s/he is referring to is the fact that it could not be "fixed" by modifying /etc/sudoers or /etc/fstab


DawieS is talking about (un)mounting an NTFS/FAT partition via the GUI (nautilus/policykit). By default, in 9.04, PolicyKit allows admin users to (un)mount NTFS/FAT partition without password authentication, while 9.10 uses the new poicykit-1 (a complete rewrite of the old one) which comes with different, in my opinion better, safer & improved, default settings. i.e. (un)mounting internal disk partitions requires password authentication, but (un)mounting an external disk partition does not.

---

### Post by bodhi.zazen on 2010-02-18
Ah, thank you, that helps my understanding. As I said, I do not use gnome or NTFS enough, lol.

---

### Post by bodhi.zazen on 2010-02-19
OIC the problem now , I have to agree with DawieS, this is a can of worms.

I can edit sudoers so that the NTFS partition can be mounted from the command line, with sudo, without a password.

The fstab entry does not work 

[http://www.tuxera.com/community/ntfs-3g-faq/#useroption2](http://www.tuxera.com/community/ntfs-3g-faq/#useroption2)

When you set the SUID in Ubuntu, it still does not work.

The edit to /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy did not work on my system (still could not mount the partition from the gnome interface).

I would find that frustrating if I used a ntfs partition with the easiest solution (for me) simply to either auto mount the partition at boot (works) or use sudo.

I believe you should file a bug report on that, IMO it should not be *that* difficult and one can certainly mount and unmount Linux native partitions with ease (simple edit of fstab).

---

### Post by DawieS on 2010-02-19
Just to add to the subject, Ubuntu 9.10 does not know which drives are internal or external.
Edit:
> A second thought on this: All drives are seen as internal (except USB mounted drives). In my box, 3 of the 4 SATA ports on the motherboard are extended through plug-able backplates to the external drives, and 1 port is directly connected to the internal drive. I also have a skeleton copy of Ubuntu on one external drive, from which I sometimes boot, for backup, maintenance and checks on the internal drive.

Depending on which drives were switched on at boot-time, the drives may show up in the file browser (unmounted) in a different order for each boot.

 Mount points are only created once clicked on the drive. A drive may disappear from the file browser if switched off, and will re-appear again if switched on later. Obviously you have to be able to unmount it before you can switch off (Currently you have to reboot to be able to switch off drives safely, with the default installation but with auto-mounting).

---

### Post by DawieS on 2010-02-20
I had a long hard thought on this matter. My recommendation is:

- Keep the default **Server** Edition of Ubuntu with the option marked as 'auth_admin_keep'. This would provide an extra security layer to prevent unauthorized access. An administrator would have to be present to mount/unmount disks.
- Change the default **Desktop** Edition of Ubuntu with the option marked as 'yes'. This is intended for general home and office use, where the users themselves are responsible for the integrity and back-up of their data. Add a note to 'Instructions to Administrators' to change the option to 'auth_admin_keep', should there be a need to increase security requirements.

Motivation:

Currently we are forced to also use NTFS for compatibility reasons. We are still in the minority, and beggars can't be choosers, so to speak. However when I look around me, I can see a Linux community growing exponentially in numbers. It is unavoidable that in the not too distant future, Linux will become the dominant operating system worldwide. When this happens, the new minority will be forced into using our file systems of choice, in order to stay compatible.

In addition to being robust and secure, an important consideration is also the ease of use, especially for kids and new users, for an operating system to be a viable alternative to the others out there. It is not realistic to expect of a new user to go sudo hunting in the depths of an Ubuntu 9.10 installation, just to get a workable setup to compare with his previous operating system.

---

