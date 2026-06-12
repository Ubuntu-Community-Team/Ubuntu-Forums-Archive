---
title: "Disable root from logging in via GDM"
date: 2010-03-11
forum: Security
---

### Post by yeleek on 2010-03-11
Hi,

I've enabled the root account on Ubuntu 9.10, however I want to stop it from being used to login via GDM.  9.10 seems to have a different GDM version, how can I carry this out under 9.10 pls?

Thanks.

---

### Post by wojox on 2010-03-11
Did you try:

```
sudo usermod -p '!' root
```

---

### Post by lupinx on 2010-03-11
Check link: [http://ubuntuforums.org/showthread.php?t=168543](http://ubuntuforums.org/showthread.php?t=168543)
They explain as to enable, but they give you the key to disable ;)

---

### Post by yeleek on 2010-03-11
> **lupinx said:**
> Check link: [http://ubuntuforums.org/showthread.php?t=168543](http://ubuntuforums.org/showthread.php?t=168543)
They explain as to enable, but they give you the key to disable ;)

Hi,

Just go to System ->Adminstration->Login Screen Setup-> press Security Tab->Enable Root Login gdm.That's it


That doesn't exist under 9.10....  Believe a new version of GDM is in place for 9.10?

---

### Post by yeleek on 2010-03-11
> **wojox said:**
> Did you try:

```
sudo usermod -p '!' root
```

Hi,

-p = 'use encrypted password for the new password'

Can you explain pls how this would stop root from logging in via GDM?  I obviously still want to be able to use root...  just not let people login via GDM.  In the same way Debian does this by default...

Thanks

---

### Post by wojox on 2010-03-11
Then just lock it:

```
sudo passwd -l root
```

---

### Post by yeleek on 2010-03-11
> **wojox said:**
> Then just lock it:

```
sudo passwd -l root
```

That locks the account so that I cannot use SU.

I'm trying to allow the account to be used via SU, but not allow login via GDM.  By default Debian allows this....  How can I carry this out with Ubuntu pls.

---

### Post by cdenley on 2010-03-11
> **yeleek said:**
> That locks the account so that I cannot use SU.

I'm trying to allow the account to be used via SU, but not allow login via GDM.  By default Debian allows this....  How can I carry this out with Ubuntu pls.

Setting a root password is not recommended in ubuntu, and "sudo -i" should be used to get a root shell instead of "su". However, if you insist on allowing root authentications but disabling root logins for gdm, I think you can add "AllowRoot=0" to the "[security]" section of /etc/gdm/custom.conf.

---

### Post by yeleek on 2010-03-12
> **cdenley said:**
> Setting a root password is not recommended in ubuntu, and "sudo -i" should be used to get a root shell instead of "su". However, if you insist on allowing root authentications but disabling root logins for gdm, I think you can add "AllowRoot=0" to the "[security]" section of /etc/gdm/custom.conf.

Afraid that didn't work either...

I know that Ubuntu do not recommend it, but I've come from Lenny and would like to reproduce the root/GDM config Debian had....

Any other ideas pls?

---

### Post by cdenley on 2010-03-12
> **yeleek said:**
> Afraid that didn't work either...

I know that Ubuntu do not recommend it, but I've come from Lenny and would like to reproduce the root/GDM config Debian had....

Any other ideas pls?

Maybe adding this line to the top of /etc/pam.d/gdm.
```

auth required pam_succeed_if.so user != root quiet

```

---

### Post by yeleek on 2010-03-12
> **cdenley said:**
> Maybe adding this line to the top of /etc/pam.d/gdm.
```

auth required pam_succeed_if.so user != root quiet

```

Fantastic - thanks very much.  Works exactly as required.

---

