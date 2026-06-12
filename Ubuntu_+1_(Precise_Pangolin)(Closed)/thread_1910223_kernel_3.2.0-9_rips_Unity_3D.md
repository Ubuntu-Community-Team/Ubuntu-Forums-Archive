---
title: "kernel 3.2.0-9 rips Unity 3D"
date: 2012-01-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2012-01-16
just reporting in that  the new 3.2.0-9 kernel had ripped Unity 3D including compiz settings but reverting back to 3.2.0-8 resotres all.

---

### Post by fjgaude on 2012-01-16
> **ventrical said:**
> just reporting in that  the new 3.2.0-9 kernel had ripped Unity 3D including compiz settings but reverting back to 3.2.0-8 resotres all.

Gosh, all is swell, i.e., cool. with 3.2.0-9 here. No issues with CCSM or compiz. Notice my signature.

---

### Post by lucazade on 2012-01-17
vertical.. a kernel cannot, directly, interfere with a desktop shell like Unity.

If Unity-3D is not working after a kernel update it is because your graphic driver is not working properly (i.e. the kernel module of the gfx driver has not been rebuilded for the new kernel).
Usually a disable/enable driver in the Restricted Hardware tool is enough to fix this situation.

---

### Post by ventrical on 2012-01-17
> **fjgaude said:**
> Gosh, all is swell, i.e., cool. with 3.2.0-9 here. No issues with CCSM or compiz. Notice my signature.


Yeah I did.

---

### Post by ventrical on 2012-01-17
> **lucazade said:**
> vertical.. a kernel cannot, directly, interfere with a desktop shell like Unity.

If Unity-3D is not working after a kernel update it is because your graphic driver is not working properly (i.e. the kernel module of the gfx driver has not been rebuilded for the new kernel).
Usually a disable/enable driver in the Restricted Hardware tool is enough to fix this situation.

Ok .. I'll check into that too.

---

### Post by shuttleworthwannabe on 2012-01-17
I noticed that too--I reinstalled unity from repo's and it did the trick; btw--I would have known as I use Gnome Shell, and if I did not see this thread.
Thanks

---

### Post by ventrical on 2012-01-17
> **shuttleworthwannabe said:**
> I noticed that too--I reinstalled unity from repo's and it did the trick; btw--I would have known as I use Gnome Shell, and if I did not see this thread.
Thanks


Actually it was the nVidia driver that got ripped (or not built in with kernel #-9)


But .. if that works too then thats great ! :)

---

### Post by iClouseau88 on 2012-01-17
Hi all,

I struggled with the same problem, same kernel version.  Installed nvidia-current, activated it, blacklisted nouveau and re-installed unity.  Still no go.

Re-installed compiz-configuration-settings-manager (ccsm) and made sure Unity Plugin box is checked.  Still no go!

Finally, the following steps work for me:

1. Re-install ccsm
2. Check Unity Plugin box in ccsm
3. Reset Unity:

```

$unity --reset

```

Ignore the warning messages in the terminal

4. Reboot and log into Unity (aka Unity 3D).

I believe ccsm has to be re-installed and unity reset in the _same_ session for this to work.  I trust this info is useful.

:D

---

### Post by ventrical on 2012-01-17
> **iClouseau88 said:**
> Hi all,

I struggled with the same problem, same kernel version.  Installed nvidia-current, activated it, blacklisted nouveau and re-installed unity.  Still no go.

Re-installed compiz-configuration-settings-manager (ccsm) and made sure Unity Plugin box is checked.  Still no go!

Finally, the following steps work for me:

1. Re-install ccsm
2. Check Unity Plugin box in ccsm
3. Reset Unity:

```

$unity --reset

```Ignore the warning messages in the terminal

4. Reboot and log into Unity (aka Unity 3D).

I believe ccsm has to be re-installed and unity reset in the _same_ session for this to work.  I trust this info is useful.

:D

Thanks for sharing this. This is unique in contradistinction to my original problem which I assumed was a Unity 3D prob- but was nVidia driver being ripped, but I bet it comes in handy during this cycle.

---

### Post by shuttleworthwannabe on 2012-01-17
That could be true--nVidia being ripped with the kernel update--the font rendering got disrupted as well; I discovered this when I installed "fonts-droid"; the fonts returned to normal after the fontconfig.

---

