---
title: "Password to mount a device."
date: 2009-12-07
forum: Security
---

### Post by cicos on 2009-12-07
Hello, i'm a new user, i've a problem.

I use the last version of ubuntu (9.10) and i've three partitions on my hard drive, two are for files, formatted using NTFS. When i open one of these partitions, ubuntu asks me the password to mount a device. When i'm not at home, my family in another accout needs to open them, but they don't have my passw. 

How can i delete the request of the password?

---

### Post by sisco311 on 2009-12-07
Hi! Welcome to the forums and Ubuntu.

You don't have to mount the partition manually. Mount the drive automatically every time you boot up Ubuntu.

[ntfs-config]("apt://ntfs-config") (click the link to install it) allows you to easily configure all of your NTFS devices to allow write support via a friendly gui. 

[http://psychocats.net/ubuntu/mountwindows#ntfsconfig]("http://psychocats.net/ubuntu/mountwindows#ntfsconfig")

---

### Post by teward on 2009-12-07
If I'm interpreting your problem correctly, you're trying to figure out how to stop the screen saying "System policy prevents the mounting of internal media" from showing up, right?


You can change the system policies to allow the mounting of internal media/devices by anyone.

On Jaunty (9.04), this can be done by going to System > Administration > Authorizations, then scroll down to the "hal" folder.  Under that folder is another folder called "storage".  Under that folder, is listed the options for "Mount file systems from internal drives".  By default, its set to Admin Authentication, and you can change that so that people can mount your devices (so that Active Console says "yes", and Anyone says "yes" and Console says "yes").  *_**This puts a hole in your system's security though, so that ANYONE can access your other partitions, which is why I don't recommend that you do this.  Because this will let guest sessions mount your NTFS partition as well**_*.

I'm not familiar as to whether this exists on Karmic (9.10), but I'm assuming it does.

---

### Post by bodhi.zazen on 2009-12-07
> **TrekCaptainUSA said:**
> If I'm interpreting your problem correctly, you're trying to figure out how to stop the screen saying "System policy prevents the mounting of internal media" from showing up, right?


You can change the system policies to allow the mounting of internal media/devices by anyone.

On Jaunty (9.04), this can be done by going to System > Administration > Authorizations, then scroll down to the "hal" folder.  Under that folder is another folder called "storage".  Under that folder, is listed the options for "Mount file systems from internal drives".  By default, its set to Admin Authentication, and you can change that so that people can mount your devices (so that Active Console says "yes", and Anyone says "yes" and Console says "yes").  *_**This puts a hole in your system's security though, so that ANYONE can access your other partitions, which is why I don't recommend that you do this.  Because this will let guest sessions mount your NTFS partition as well**_*.

I'm not familiar as to whether this exists on Karmic (9.10), but I'm assuming it does.

Well, it is a shared partition =)

And I restrict the guest account with apparmor, lol 

Anyways, as to how to change the behavior of your partitions, simply update /etc/fstab and in the options column add users.

For details see : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by cicos on 2009-12-07
thanks, i'll try to fix the problem soon, i'm not at home now.

Sorry if sometimes i make mistakes writing english, is because i'm italian and italian forums are not so good to fix problems.

---

### Post by cicos on 2009-12-09
> **sisco311 said:**
> Hi! Welcome to the forums and Ubuntu.

You don't have to mount the partition manually. Mount the drive automatically every time you boot up Ubuntu.

[ntfs-config]("apt://ntfs-config") (click the link to install it) allows you to easily configure all of your NTFS devices to allow write support via a friendly gui. 

[http://psychocats.net/ubuntu/mountwindows#ntfsconfig](http://psychocats.net/ubuntu/mountwindows#ntfsconfig)

Ok, it works, problem fixed.

> **TrekCaptainUSA said:**
> If I'm interpreting your problem correctly, you're trying to figure out how to stop the screen saying "System policy prevents the mounting of internal media" from showing up, right?


You can change the system policies to allow the mounting of internal media/devices by anyone.

On Jaunty (9.04), this can be done by going to System > Administration > Authorizations, then scroll down to the "hal" folder. Under that folder is another folder called "storage". Under that folder, is listed the options for "Mount file systems from internal drives". By default, its set to Admin Authentication, and you can change that so that people can mount your devices (so that Active Console says "yes", and Anyone says "yes" and Console says "yes"). *_**This puts a hole in your system's security though, so that ANYONE can access your other partitions, which is why I don't recommend that you do this. Because this will let guest sessions mount your NTFS partition as well**_*.

I'm not familiar as to whether this exists on Karmic (9.10), but I'm assuming it does.

It doesn't, there is not the folder System > Administration > Authorizations, maybe i've to install something

---

### Post by Agent ME on 2009-12-09
The System > Administration > Authorizations menu seems to have been deprecated in 9.10. It is now in the "policykit-gnome" package, but installing that is pretty useless now because it can't control much.
What is the replacement for it on 9.10? I don't understand why they would remove/cripple this tool.

---

### Post by cicos on 2009-12-10
i really don't know, this is the first time i use linux, and the 9.10 is my first version. Maybe they improved something about security, and now is better.

---

