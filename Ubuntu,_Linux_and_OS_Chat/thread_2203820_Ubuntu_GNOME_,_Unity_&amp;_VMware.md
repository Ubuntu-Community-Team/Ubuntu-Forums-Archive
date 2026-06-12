---
title: "Ubuntu GNOME , Unity &amp; VMware"
date: 2014-02-05
forum: Ubuntu, Linux and OS Chat
---

### Post by RichardET on 2014-02-05
For the past year I have been using Unity, but it seems to not play 100% well with VMware.  I have now switched to the GNOME version of Ubuntu 13.10
and it seems much better.  So for me, this is now my distribution of choice.  Before I made this decision, I did try some other distributions with GNOME, but 
they all lacked the ease of use that Ubuntu has, so back to Ubuntu, but with GNOME.  VMware is running flawlessly now.

---

### Post by TheFu on 2014-02-05
Which vmware? They make 6 different products for different uses.

There is no need to switch an entire distro just for a GUI.  You can install Gnome2, gnome3, XFCE, LXDE, Unity, Cinnamon, fvwm, openbox, enlightenment, twm, or 30 other GUIs on stock Ubuntu desktop. Usually the install takes 3 seconds to 3 minutes - tops.  Then just logout, choose the other environment (click the **gear** on the login page) and login.

Tuning the VM settings is an important aspect to getting the best performance under virtualization. I've used ESX, ESXi, Workstation, Server and Player from VMware over the years, but stopped a few years ago when the company sales/marketing people made some extremely large-impact decisions for clients. For us, it would triple the costs, which was unacceptable. Within 6 months, we'd stopped using anything from VMware as a decision from the CxO suites.

---

### Post by neu5eeCh on 2014-02-05
> **TheFu said:**
> There is no need to switch an entire distro just for a GUI.  You can install Gnome2, gnome3, XFCE, LXDE, Unity, Cinnamon, fvwm, openbox, enlightenment, twm, or 30 other GUIs on stock Ubuntu desktop. Usually the install takes 3 seconds to 3 minutes - tops....

Not true. Installing different DEs can wreak havoc on a system -- much depends on which version of Ubuntu one is using, which version of Unity, Gnome, KDE, Cinnamon etc... Installing multiple DEs is a much dicier proposition than it used to be.

---

### Post by TheFu on 2014-02-05
The installation of multple window managers has never been an issue. If the DEs break that, then that is a **MAJOR BUG and needs to be fixed**. 
In the meantime, use a different userid, if that sort of issue is discovered, to keep the settings separate. 
Hardly worth installing a new OS just to try out a different GUI.
Creating a new userid is ... about 10 seconds?

---

### Post by coffeecat on 2014-02-05
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by RichardET on 2014-02-06
> **TheFu said:**
> Which vmware? They make 6 different products for different uses.

There is no need to switch an entire distro just for a GUI.  You can install Gnome2, gnome3, XFCE, LXDE, Unity, Cinnamon, fvwm, openbox, enlightenment, twm, or 30 other GUIs on stock Ubuntu desktop. Usually the install takes 3 seconds to 3 minutes - tops.  Then just logout, choose the other environment (click the **gear** on the login page) and login.

Tuning the VM settings is an important aspect to getting the best performance under virtualization. I've used ESX, ESXi, Workstation, Server and Player from VMware over the years, but stopped a few years ago when the company sales/marketing people made some extremely large-impact decisions for clients. For us, it would triple the costs, which was unacceptable. Within 6 months, we'd stopped using anything from VMware as a decision from the CxO suites.

Thanks for the tip;  I see that there are many DE choices;  I am not as experienced with Ubuntu as other brands of GNU/Linux.

---

### Post by TheFu on 2014-02-06
> **RichardET said:**
> Thanks for the tip;  I see that there are many DE choices;  I am not as experienced with Ubuntu as other brands of GNU/Linux.

The other Linux flavors can do the same things, just the way you select with DE or WM at login would be different.
Like others have said, some of the newer DEs might corrupt settings used by other DEs, so it would be best to have a different userid for each DE used until you decide to make it permanent.  I consider it a bug, but that doesn't change reality.

---

### Post by RichardET on 2014-02-06
How do you get rid of the gnome/openbox DE choice?  it does not seem to do anything.

---

### Post by TheFu on 2014-02-07
The normal way would be to remove those packages, but gnome and openbox are general purpose, so removing those packages might (most likely) be bad.  There could be a metapackage for the gnome desktop - removing it probably removes the option form the login.

Is it a big deal to leave them?  Whichever choice was last picked will be used the next login, so you need not see the choices at login.

There is probably a text file somewhere that controls the list. It would depend on which login manager is being used. Look under /etc/ and be certain to have an alternate method of getting back into the machine to fix it.

---

### Post by RichardET on 2014-02-07
Because I keep very good backups, I decided to go back to a plain vanilla Ubuntu with Unity;  Less hassle;  I noticed that GNOME sometimes has hiccups like not allowing me to unlock.  That's bad, Unity never did that.

---

