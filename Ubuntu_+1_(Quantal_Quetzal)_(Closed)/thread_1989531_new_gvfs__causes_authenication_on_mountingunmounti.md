---
title: "new gvfs*  causes authenication on mounting/unmounting internal drives thru nautilus"
date: 2012-05-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-05-28
Could be something that other packages due to be upgraded will resolve or something needed to be fixed
Can't imagine it is now intentional
(doesn't affect external drives & seems to use the auth timeout of 15 min or whatever
[bug report]("https://bugs.launchpad.net/bugs/1005643")

---

### Post by scradock on 2012-05-28
Indeed. Internal volumes are now mounted under /run/media/$USER/ instead of /media/.

Most strange!

Data volumes are owned by $USER, but bootable volumes are owned by ROOT. I think that may have been the case before, though...

---

### Post by scradock on 2012-05-28
For me, the internal volumes AND volumes on a USB external disk are mounted on /run/media/$USER/; hot-plugging a USB stick also brings it up mounted on /run/media/$USER/. 

I agree that the external drive volumes seem to be mounting correctly, whereas the internal (dev/sda) volumes are asking for authentification before being mounted.

Nothing appears in /etc/fstab for any of them (after a fresh install of quantal). There is some information somewhere else that needs to be reset to default to mounting internal volumes...

---

### Post by scradock on 2012-05-28
Curiouser and curiouser! 

Clicking on a volume on /dev/sda (a true internal volume) brings up the authentification dialog. Then it mounts, once the password is given. But the other volumes on /dev/sda are still not mounted, and clicking on ANY of them causes the Nautilus window to vanish - probably a crash. Re-opening Nautilus shows the second internal volume not mounted, as before, but the first one is mounted. Clicking on the second one again mounts it and opens the contents in Nautilus. 

And this repeats - now click on another internal volume, Nautilus vanishes again. Open it up again and try again - no problem for the first try, crash again for the second one...

Opening Nautilus from a terminal I got the following errors - all too familiar these days, don't know if they mean anything...
> sc@scqq:~$ nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:2367): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(nautilus:2367): GLib-GObject-CRITICAL **: g_object_remove_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2367): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:2367): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:2367): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:2367): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:2367): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:2367): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:2367): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

---

### Post by mc4man on 2012-05-28
One thing that stands out - 
The policy in /usr/share/polkit-1/action/org.freedesktop.udisks2.policy
is a new name, udisks2,  that's not in in the default .pkla

So it used to be in udisks.policy
action id="org.freedesktop.udisks.filesystem-mount-system-internal"

That's not there anymore, intead there is 
action id="org.freedesktop.udisks2.filesystem-mount-system"
&
action id="org.freedesktop.udisks2.filesystem-mount-other-seat"

The current .pkla shows for this -
```
[Mounting, checking, etc. of internal drives]
Identity=unix-group:admin;unix-group:sudo
Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*
ResultActive=yes

```

So editing it to be udisks[COLOR="Red"]2[/COLOR] resolves here

```
sudo gedit /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```

---

### Post by mc4man on 2012-05-29
There is also this bug I've seen concerning mounting drives thru nautilus

For this you need at least 2 internal
If you try to mount more than one _from the same nautilus window_ then nautilus will crash
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1002506](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1002506)

---

### Post by scradock on 2012-05-29
> **mc4man said:**
> There is also this bug I've seen concerning mounting drives thru nautilus

For this you need at least 2 internal
If you try to mount more than one _from the same nautilus window_ then nautilus will crash
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1002506](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1002506)
OK - I've confirmed that bug report.

Also changed (both) the udisks to udisks2 in the .pkla you mentioned. I'll see if it work now..

---

### Post by Harry33 on 2012-05-29
The new gvfs does not use udisks any more.
Instead, it needs to have the package udisks2 installed.
However, gvfs is not marked to depend on it.

---

### Post by mc4man on 2012-05-29
> **Harry33 said:**
> The new gvfs does not use udisks any more.
Instead, it needs to have the package udisks2 installed.
However, gvfs is not marked to depend on it.

udisks2 was introduced/installed on 5/25 as a dep of gnome-disk-utility, gvfs now will use that policy (udisks2)
So in this case I believe it's  policykit-desktop-privileges that needs an update, report in 1st post

Edit: 
so the fix will be to add on to the action line using non wild card & leave the orig also,  as in - 
```
Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*;[COLOR="Blue"]org.freedesktop.udisks2.filesystem-mount-system;org.freedesktop.udisks2.filesystem-fstab;[/COLOR]

```
Whatever the new 'seat' one is will require auth
unity still may use udisk as does update-notifier so that may be one reason to leave the orig. udisks *

---

### Post by Harry33 on 2012-05-29
New update to policykit-desktop-privileges (0.11) is availabla for Quantal.

Here:
[https://launchpad.net/ubuntu/quantal/+source/policykit-desktop-privileges/0.11](https://launchpad.net/ubuntu/quantal/+source/policykit-desktop-privileges/0.11)

---

### Post by mc4man on 2012-05-30
> **scradock said:**
> For me, the internal volumes AND volumes on a USB external disk are mounted on /run/media/$USER/; hot-plugging a USB stick also brings it up mounted on /run/media/$USER/. 
.
Didn't notice yesterday, could of sworn a usb drive was mounted as before, at least as far as icon & options
Anyway now all removable media goes to /run/media/$USER/ with exception of audio cd's

I'm getting a new usb icon for a flash drive - looks like old one  + a yellow monitor overlayed

The only real change is usb drives can now only be unmounted, no more eject or safely remove options (sorta liked safely remove myself

---

### Post by jerrylamos on 2012-05-30
> **mc4man said:**
> udisks2 was introduced/installed on 5/25 as a dep of gnome-disk-utility, gvfs now will use that policy (udisks2)
So in this case I believe it's  policykit-desktop-privileges that needs an update, report in 1st post

Edit: 
so the fix will be to add on to the action line using non wild card & leave the orig also,  as in - 
```
Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*;[COLOR="Blue"]org.freedesktop.udisks2.filesystem-mount-system;org.freedesktop.udisks2.filesystem-fstab;[/COLOR]

```
Whatever the new 'seat' one is will require auth
unity still may use udisk as does update-notifier so that may be one reason to leave the orig. udisks *
I'd really like to get back to where it was before:

Disks mounted as /media instead of /run/media/$user

No password required to mount disks internal or external

Any hope?

Thanks, Jerry

---

### Post by mc4man on 2012-05-30
> **jerrylamos said:**
> I'd really like to get back to where it was before:

Disks mounted as /media instead of /run/media/$user

No password required to mount disks internal or external

Any hope?

Thanks, Jerry

You shouldn't need a password for this if you're updated.
The ability to unmount usb drives was something removed several releases back - now it's returned which is a good thing.
  Removing the 'safely remove' option, (power down), possibly will affrct some but not a big deal here 

Also the new 'disks' utility is a bit spartan, all the options are probably still there if you look hard enough.
 Either it's not yet complete or more likely falls under Gnome's idea that less is better

---

