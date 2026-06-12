---
title: "Hardy keeps dropping to shell"
date: 2008-05-01
forum: Server Platforms
---

### Post by DjQurt on 2008-05-01
i got it all installed and it will drop to shell shortly after displaying this

Check root= Bootarg cat /proc/cmdline or missing modules, devices:cat /proc/modules ls /dev

Alert! /dev/disk/by-uuid/48117696-6b22-4a1f-829e-fb660e056277 does not exist. dropping to shell!

and then im left with

(initramfs) _

---

### Post by cdenley on 2008-05-02
Boot to a livecd, mount your filesystem, then post the output for
```

ls -l /dev/disk/by-uuid
sudo fdisk -l
sudo cat /media/disk/etc/fstab

```
assuming your filesystem is mounted at /media/disk

---

### Post by DjQurt on 2008-05-03
same thing happens when i try to boot from live cd :(

---

### Post by andguent on 2008-05-03
Is this occuring during the install, or after you have installed completely and removed the CD? If the Live CD booted successfully before, but not again, then something has changed. The Live CD should boot even if the hard drive is completely missing.

Can you boot the cd, and then select "Test CD" and see how that goes?

The pessimistic side of me is speaking here, but keep an eye out for signs of a failing hard drive, or a bad cd download/burn.

---

### Post by DjQurt on 2008-05-03
ubuntu server installed all the way and it boots up without the cd. whne i stick the live cd in it starts doint the ping pong loading bar then just goes to the command line with shell :(

---

### Post by andguent on 2008-05-03
Just to clarify, when you say it boots up without the cd, I assume it still goes to the error you mentioned?

When you reboot with the CD in, do you ever get to the option to test the CD?

What is the history on the computer? Does it have any data you care about?

---

### Post by DjQurt on 2008-05-03
i just tested it and it does the same thing, starts the ping pong loading thing then drops to shell :( the system is an old server from a grocery store i got for free so theres nothing important on it.

---

### Post by andguent on 2008-05-03
If the CD test comes up clean, I would try installing again. If that fails, I may also try Dapper server or Debian, see if any distro will install correctly. Verify that Knoppix can read the drives as well. 

The more distributions and variants you try, the more you will get a feel for if it is hardware or the installer that is screwing you up. If the server you are referring to is in your signature, it may or may not be a heavily tested piece of hardware. 

Also, if that raid is hardware raid, some of those controller cards have their own special quirks. See what happens if you disconnect the raid drives, attach a boring ole IDE drive, and install to that.

---

### Post by DjQurt on 2008-05-03
well it wouldnt install at all when i had them raided i took raid out and just have 1 scsi drive in right now but i keep getting acpi errors also and errors about th raid card. server is very confusing but ill try to find a ide port in it somewhere

---

### Post by ghostknife on 2008-05-03
I don't know how the installer works, but it's probably trying to mount your drive when you boot, which is why this cd boot is giving problems.

What you can try is to see if there is some boot option that would prevent it from doing this.

Another option is to boot from Knoppix or some other live disc and drop the partitions on the disk. Then try to install it again.

Before you do this though, using the other distro's live disc, see if you can mount the partitions and read/write to the mount. Then do an "ls -l /dev/disk/*" and paste the output here. It's probably that the disk links weren't (all) created. Many things can cause this.

If it still doesn't work we can try and diagnose the problem, or hack around it.

---

### Post by DjQurt on 2008-05-04
so get another live disc say debian or suse or something and then do what? how do i read and write to the mount? you mean like save stuff on it and browse through it?

---

### Post by ghostknife on 2008-05-04
Boot the other live cd.

Then do the following (as root): fdisk -l

Find the path to the partitions you want to mount, and do: mount /dev/sda1 /mnt/disk1

Make sure /mnt/disk1 exists, and replace /dev/sda1 with the path to the partition you're trying to mount.

Then create a file on /mnt/disk1, say "test", put some data into it, close the editor, open it again and make sure the data is there. Then delete it.

If this all works you can write to the disk, then do the other instructions I mentioned.

---

