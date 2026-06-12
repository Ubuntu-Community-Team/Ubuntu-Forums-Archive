---
title: "what to do if nautilus doesn't open when upgrading to 22.10 development"
date: 2022-08-23
forum: Ubuntu Development Version
---

### Post by Claus7 on 2022-08-23
Hello,

first of all, before the upgrade, if you have tilix installed, remove it. After the upgrade I had an error about tilix and python, where part of it was:
*nautilus requires version... raise value error namespace is loaded with version*
the versions reported were 3.0 and 4.0

after removing tilix, still nautilus refused to open without showing any error when trying to open it from terminal. So I had to remove the following packages from synaptic:
gnome-sushi
nautilus-admin
gir1.2-nautilus-4.0
python3-nautilus

I do not know which of these made the trick, yet I logged out and back in and nautilus started normally.

Regards!

---

### Post by jbicha on 2022-08-23
I am unable to reproduce that issue.

I do see that tilix ships a Nautilus extension that is incompatible with Nautilus 4.0 but it doesn't cause Nautilus to fail to start for me.

Now that Nautilus is working for you, could you see if there is anything you can install to make it stop working?

---

### Post by Claus7 on 2022-08-24
Hello,

> **jbicha said:**
> ...

Now that Nautilus is working for you, could you see if there is anything you can install to make it stop working?

I reinstalled gnome-sushi first, logging out and back in: pressing spacespace on pdf files is not working, yet nautilus opens fine.
Then I reinstalled nautilus-admin which required the packages gir1.2-nautilus-4.0 and python3-nautilus. Logged out and back in: nautilus doesn't open, so I removed them again.

Regards!

---

### Post by jbicha on 2022-08-24
nautilus-admin works here. Can you duplicate the problem from a clean install?

Do you see any errors when you try to run nautilus from the command line?

---

### Post by Claus7 on 2022-08-24
Hello,

> **jbicha said:**
> nautilus-admin works here. Can you duplicate the problem from a clean install?
With the latest updates I tried to install nautilus-admin. Initially it made a complaint about gedit, yet installation with upgrades finished normally. Then I restarted the system and nautilus is working fine. I do not see any option like open as admin though when right clicking on files.
edit: because I had to reinstall nautilus-admin, now with the same dependencies as mentioned above. Installation went fine and now I have also the option "Edit as Administrator".

> **jbicha said:**
> Do you see any errors when you try to run nautilus from the command line?
No errors at all.

I suppose that I have to reinstall.

Regards!

---

### Post by jbicha on 2022-08-24
What version of nautilus-admin , gvfs-backends and python3-nautilus do you have installed?

What desktop are you using?

What was the gedit complaint?

---

### Post by Claus7 on 2022-08-24
Hello,

> **jbicha said:**
> What version of nautilus-admin , gvfs-backends and python3-nautilus do you have installed?
nautilus-admin: 1.1.9-3.2~ubuntu1
gvfs-backends: 1.50.2-1
python3-nautilus: 4.0~alpha-2

> **jbicha said:**
> What desktop are you using?
upgrade: ubuntu wayland
fresh installation: ubuntu xorg

> **jbicha said:**
> What was the gedit complaint?
About some missing dependencies. Checking history from synaptic the upgrade of gedit-common is from 42.2-1 to the same version.

Regards!

---

### Post by jbicha on 2022-08-26
OK, it's good that it sounds like it works from a clean install.

Unless you're able to provide us a series of steps where you get from an old install (say new install of Ubuntu 22.04 LTS or older) which you upgrade to run into the bug, I don't think there's anything we can do here. Because the bug is currently unreproducible.

Depending on how old the install is, perhaps you installed some script or something that was interfering with Nautilus 43. For instance, if you managed to install nautilus-admin as a user-specific extension (I think that's possible), then it would badly conflict with a different version installed system-wide. And the user-specific extension wouldn't work either because it's not compatible with Nautilus 43.

---

### Post by Claus7 on 2022-08-26
Hello,

> **jbicha said:**
> OK, it's good that it sounds like it works from a clean install.

Unless you're able to provide us a series of steps where you get from an old install (say new install of Ubuntu 22.04 LTS or older) which you upgrade to run into the bug, I don't think there's anything we can do here. Because the bug is currently unreproducible.

Depending on how old the install is, perhaps you installed some script or something that was interfering with Nautilus 43. For instance, if you managed to install nautilus-admin as a user-specific extension (I think that's possible), then it would badly conflict with a different version installed system-wide. And the user-specific extension wouldn't work either because it's not compatible with Nautilus 43.

thank you for letting me know. Something in the process might have made it like that. I just posted it as a quick workaround in order for basic tasks to get accomplished.

Regards!

---

