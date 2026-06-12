---
title: "Concern over update-manager on Ubuntu 14.04 64-bit"
date: 2014-08-06
forum: Security
---

### Post by slooksterpsv on 2014-08-06
I'm not sure if this is applicable in all Ubuntu versions or variants, but something seems off to me.

When ever I start my computer and update-manager finds updates, it asks if I'd like to install them. I say sure, install. Now for what it doesn't do, that concerns me. It doesn't prompt me to input my password.

This leaves me to believe that somewhere it's bypassing all security and allowing itself to become either sudo or su to install said updates - or, even worse, it's putting the updates in a separate location to install upon reboot (doubtful on that entirely). It seems like it could be hijacked to where any administrative actions could hijack off of the update-manager in order to execute malicious or damaging code. Does someone have an explanation or a proof of concept of how this works? It just seems odd. IIRC, which I probably don't, I thought Xubuntu prompted me for my password for updates.

My system is:
Ubuntu 14.04.1 64-bit

---

### Post by ian-weisser on 2014-08-06
If System Updater were using shell scripts to perform the updates, sure.

But it's not. It's using aptdaemon via dbus.

System updater runs as a user.
Aptdaemon runs as root.
dbus permits the two limited communication (preventing, for example, arbitrary code execution)

System Updater can ONLY update installed packages. And, if I recall correctly, it has an AppArmor profile to enforce that.

Updates using Update Manager used to require passwords. The change to System Updater removed the requirement. There was some debate in the developer community about it; the consensus was that:
- Sysadmins do have password protection when *installing* and *removing* packages.
- Sysadmins should prevent updates using apt-pinning instead of endlessly unchecking boxes in System Updater
- The password requirement was a legacy from when the same root CLI commands were used for install/remove and updates (like apt-get), and before the update-treadmill was too common.
- The application didn't have code to install or remove anything - only update
So there really wasn't much need anymore for password-protecting System Updater.

---

### Post by slooksterpsv on 2014-08-07
That makes sense but it still seems a bit unsettling. I trust Ubuntu and Canonical so I wont put more thought into it. Thank you for the information.

---

### Post by jimmy-frydkaer on 2014-08-07
@Ian Weisser

Thanks a million for the info

I have had the same wonders about System-Updater. Haven't come around to read up on it, but have noticed that the system-updater prompts for passw when the kernel gets updated. Same goes for any driver, like nVidia-driver, I have installed. Still, even small updates on occasion prompts for the code.

Having run Ubuntu since 6.10, and knowing the Linux-mind-set nothing gets into my box that doesn't come from Canonical, at least not through my system-updater. But thanks again for the clarification on the subject -

---

