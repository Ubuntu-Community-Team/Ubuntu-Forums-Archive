---
title: "Restricting a Sudoer from Mounting (or from writing to a partition)"
date: 2010-06-05
forum: Security
---

### Post by jakswa on 2010-06-05
**Scenario being explored:**  We have a lab of computers wherein students need to use linux (CS students).  Currently, they just start up a VM whenever needed -- this is slow and we're exploring just having a linux partition they can boot into when needed (preferred by everyone involved).

**Question:**  We want students to have the ability to install programs and administer the system freely (this partition will be similar to a liveCD in that changes will not be saved on reboot), but we want to try and restrict their ability to mount/write to the windows partition on the drive.  Is there a way to limit access to mounting (or writing) to a partition on the system, **but still let the users sudo?**

I've been exploring creating a root-like user that is slightly limited, but cannot pinpoint the differences that would be required between it and root.

I fear we may just go with locking students out of sudo (setting 'rootpw' in the sudoers file), but if anyone has some ideas for me to pursue, I would **GREATLY** appreciate it!!

---

### Post by anomie on 2010-06-05
Quick context: The ideal scenario for configuring sudoers that you don't want to have full reign over a system is to explicitly allow *only* the needed commands. The reverse - allowing all commands and then trying to explicitly disable or prevent a few - is tricky. In your case, there are too many ways they could potentially access the Windows partition. 

What you might want to think about is setting up a virtualized environment for the students where you can prevent access to disks on the host system (Virtualbox? - not sure).

---

### Post by bodhi.zazen on 2010-06-05
You can restrict them either by :

1. see man sudoers and allow access to some commands but not others. Probably not as good as #2.

2. You can easily restrict them with apparmor.

ln /bin/bash /usr/local/jailbash

Change their log in shell to jailbash

Restrict jailbash with apparmor, restricting access to the partition or device in question.

You can modify this if you like:

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.local.bin.jailbash](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.local.bin.jailbash)

---

### Post by jakswa on 2010-06-05
Thanks Anomie!  I guess I didn't explain very clearly, but students do have access to a virtualized environment (I called it a VM above), and it works well.  But for repeated/long use it is slow so we're taking a stab at a live install.  I am gathering you are correct about the context I'm in, though... it looks like it will be very difficult to restrict write access to this partition.

At this point, I predict we'll be settling for having the live install be very restricted, with access to only a few commands (maybe just apt-get, who knows).

The last idea I'm trying at this moment is having the partition mounted on boot as read-only, and restricting sudo access to un-mounting anything.  Seems already like a fail, though, because even if the user cannot execute "/bin/umount", they can "cp /bin/umount ~" and execute it from their home directory...

If anyone following in my footsteps wants to see how (simple & weak) command restriction is performed, here are the corresponding lines in "/etc/sudoers" (edited with the command "sudo visudo"):

```
#alias for command(s) we want to restrict
Cmnd_Alias MOUNT = /bin/mount

#limit users in group 'test' from mounting
%test ALL=(ALL) ALL, !MOUNT
```

---

### Post by jakswa on 2010-06-05
> **bodhi.zazen said:**
> You can restrict them either by :

1. see man sudoers and allow access to some commands but not others. Probably not as good as #2.

2. You can easily restrict them with apparmor.

```
ln /bin/bash /usr/local/jailbash
```

Change their log in shell to jailbash

Restrict jailbash with apparmor, restricting access to the partition or device in question.

You can modify this if you like:

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.local.bin.jailbash](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.local.bin.jailbash)

This looks promising, I'm giving apparmor a spin, and will try to remember to post my results.

---

