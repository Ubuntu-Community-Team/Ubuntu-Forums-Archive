---
title: "SELinux or AppArmor for Ubuntu?"
date: 2010-08-07
forum: Security
---

### Post by r2rX on 2010-08-07
Hey guys,

I have been doing some research, and it seems that Ubuntu doesn't have any security software installed by default.

So, from other security-minded users out there, what would you recommend? SELinux or AppArmor? I know OpenSUSE is hailed as one of the most secure distro's of Linux out there; using AppArmor (and i'm sure other architectural infrastructures of OpenSUSE are responsible as well)...

How can one make Ubuntu more secure? If not SELinux or AppArmor, any other suggestions?

All the help is appreciated. ;)

r2rX  :D

---

### Post by rookcifer on 2010-08-07
> **r2rX said:**
> Hey guys,

I have been doing some research, and it seems that Ubuntu doesn't have any security software installed by default.

So, from other security-minded users out there, what would you recommend? SELinux or AppArmor? I know OpenSUSE is hailed as one of the most secure distro's of Linux out there; using AppArmor (and i'm sure other architectural infrastructures of OpenSUSE are responsible as well)...

How can one make Ubuntu more secure? If not SELinux or AppArmor, any other suggestions?

All the help is appreciated. ;)

r2rX  :D

As I answered in the other thread, you are wrong.  AppArmor is installed by default on Ubuntu.  You can even enable the pre-made Firefox profile by doing the following:

```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox*
```

The Ubuntu AppArmor documentation is [here.]("https://help.ubuntu.com/community/AppArmor")  Also there is a sticky at the top of this forum that covers AppArmor and how to create your own profiles.

---

### Post by r2rX on 2010-08-07
I stand corrected...seems my research was flawed. :) Between the two, which do you prefer? SELinux or AppArmor?

r2rX  :)

---

### Post by rookcifer on 2010-08-07
AppArmor because it is far easier to configure and understand.  However, it can't do as much as SELinux, so there's a trade-off.  For a desktop box, AppArmor is more than sufficient.

---

### Post by bodhi.zazen on 2010-08-08
IMO Selinux is fare more mature and the tools to manage selinux profiles have come a long ways.

Apparmor is easier to learn, but, IMO, there are insufficient profiles and the profiles end up being broad and permissive.

IMO the main point of apparmor is to limit access to file in $HOME (system files are already protected by linux permissions) and/or confine daemons (for example, apache or personally I confine privoxy with an apparmor profile).

If you want to try selinux I highly suggest you use Fedora. Honestly not many here are familiar with selinux and selinux is not easy to install or configure on ubuntu. You will get much better selinux support on the Fedora forums.

If you wish to stay with ubuntu, use apparmor.

---

