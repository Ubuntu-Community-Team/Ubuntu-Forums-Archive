---
title: "Delaying a NFS mount in /etc/fstab on system boot"
date: 2010-05-23
forum: Server Platforms
---

### Post by tr333 on 2010-05-23
I have a NFS mount defined in /etc/fstab that would normally mount on system boot.  The problem is that the network connection is over WiFi and that connection isn't active at the time the system tries to mount the NFS share.  Is there any option to delay mounting the NFS until the WiFi connection is up?

---

### Post by benderisgreat on 2010-05-23
You could remove it from fstab and create a sysv init style script to mount it after the wifi is up.

---

### Post by tr333 on 2010-05-23
> **benderisgreat said:**
> You could remove it from fstab and create a sysv init style script to mount it after the wifi is up.

Thanks for the idea.  I might look at an upstart task since Ubuntu uses upstart instead of init.
Alternatively, I think I might be able to just run the mount manually from @reboot in a root cronjob but I'm not sure when the cronjobs get executed.

---

### Post by K.Mandla on 2010-05-23
I generally flag all my nfs mounts as "noauto,users" in /etc/fstab, which makes it possible for a user to mount it whenever its ready.

---

### Post by tr333 on 2010-05-23
> **K.Mandla said:**
> I generally flag all my nfs mounts as "noauto,users" in /etc/fstab, which makes it possible for a user to mount it whenever its ready.

Do you know which method I could use to mount it on system boot which would be guaranteed to occur after the wlan connection is up?  I'm not quite sure when the user cronjob @reboot gets run.

---

### Post by K.Mandla on 2010-05-23
Not really. It does seem like you could fork off a bash script at startup though, that would sleep for a minute or two before mounting that location. That's probably a rather brutish way to do it though, since it would be more elegant to check and see if the location was available before arbitrarily mounting it.

---

### Post by tr333 on 2010-05-24
I just stumbled across [Autofs](https://help.ubuntu.com/community/Autofs), which appears to do what I want.  It will only mount the NFS share when it's accessed and unmount after a period of inactivity.

---

