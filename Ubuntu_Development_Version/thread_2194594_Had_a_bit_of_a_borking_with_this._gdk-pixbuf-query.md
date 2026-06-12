---
title: "Had a bit of a borking with this. gdk-pixbuf-query-loaders"
date: 2013-12-19
forum: Ubuntu Development Version
---

### Post by philinux on 2013-12-19
Updated from a 13.10 chroot and saw this fix in an error message.   ```
gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
```

Rebooted into trusty and no top panel in login and no desktop. 

I copied the above command into a file on trusty's home from 13.10 so I could easily cat the file.

Rebooted again and got a terminal with ctrl alt t.


Installed that but had to sudi -i to get the pixbuf command to work. 

Rebooted and all ok. Question. Was this caused cos of chroot? Anyone else had it?

---

### Post by zika on 2013-12-19
> **philinux said:**
> Updated from a 13.10 chroot and saw this fix in an error message.   ```
gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
```

Rebooted into trusty and no top panel in login and no desktop. 

I copied the above command into a file on trusty's home from 13.10 so I could easily cat the file.

Rebooted again and got a terminal with ctrl alt t.


Installed that but had to sudi -i to get the pixbuf command to work. 

Rebooted and all ok. Question. Was this caused cos of chroot? Anyone else had it?Did You try to fix that from CLI(tty)? That should (as it did in almost all testings lately) (possibly) prevent from entering DM but tty(s) should work fine.

---

### Post by ventrical on 2013-12-19
> **philinux said:**
> Updated from a 13.10 chroot and saw this fix in an error message.   ```
gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
```

Rebooted into trusty and no top panel in login and no desktop. 

I copied the above command into a file on trusty's home from 13.10 so I could easily cat the file.

Rebooted again and got a terminal with ctrl alt t.


Installed that but had to sudi -i to get the pixbuf command to work. 

Rebooted and all ok. Question. Was this caused cos of chroot? Anyone else had it?

  I always get this during dev cycles but on a regular upgrade.

After todays updates:

```

Processing triggers for gnome-icon-theme ...

(gtk-update-icon-cache-3.0:11198): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.

```

---

### Post by ventrical on 2013-12-19
I did what zika suggested and it reported to me that:

'gdk-pixbuf-query-loaders' is currently not installed

 So then I,

```

apt-get install libgdk-pixbuf2.0-dev

```

and it installs,

```

libglib2.0-dev, libpcre3-dev and libpcrecpp0

```

and suggests installing,

```

libglib2.0-doc

```

which I find the last file very curious as we have been having big problems with gnome-session-flashback with one of the libglib2.0 files.

I'll reboot and report back in

 All went well with zika's suggestion so far.

---

### Post by philinux on 2013-12-19
> **ventrical said:**
> I always get this during dev cycles but on a regular upgrade.

After todays updates:

```

Processing triggers for gnome-icon-theme ...

(gtk-update-icon-cache-3.0:11198): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.

```

Yep that's the same I got in chroot from 13.10. Applying the fix prompted to install some dev package. But fix then worked.

---

### Post by ventrical on 2013-12-19
I now have  what @philinux described in his OP. Login screen, no top panel , no desktop, no terminal , report internal system error.

---

### Post by philinux on 2013-12-19
> **ventrical said:**
> I now have  what @philinux described in his OP. Login screen, no top panel , no desktop, no terminal , report internal system error.

You need to follow my instructions or similar to fix it.

---

### Post by zika on 2013-12-19
> **ventrical said:**
> I did what zika suggested and it reported to me that:
...
All went well with zika's suggestion so far.You give me too much credit. I did not suggest anything but to go to tty and do the fixing... Command to be used is Ubuntu's suggestion and it should be used, as I recall, with sudoer priviledges... As @philinux already pointed (twice)...

---

### Post by philinux on 2013-12-19
Question remains. Why have to install a dev package and do this fix anyway?

---

### Post by zika on 2013-12-20
> **philinux said:**
> Question remains. Why have to install a dev package and do this fix anyway?Because You are creating a new file that should have come (and will) through .deb...?

---

### Post by philinux on 2013-12-20
> **zika said:**
> Because You are creating a new file that should have come (and will) through .deb...?

This borked my install 2 weeks ago as well. I reinstalled then as other things were messed up.

---

### Post by zika on 2013-12-20
> **philinux said:**
> This borked my install 2 weeks ago as well. I reinstalled then as other things were messed up.As far as I remember, from previous testing periods, I was saved from re-install because I've had Gnome3 also so I was able to wait until mess cleared itself (it was a long wait as I recall)... Since I had Mir and other stuff my memory is a bit blured there due to many factors that contributed...
As I said already, it does not bork install but only makes life with DM harder... I've learned to live with such defficiencies in testing...

---

### Post by philinux on 2013-12-20
> **zika said:**
> As far as I remember, from previous testing periods, I was saved from re-install because I've had Gnome3 also so I was able to wait until mess cleared itself (it was a long wait as I recall)... Since I had Mir and other stuff my memory is a bit blured there due to many factors that contributed...
As I said already, it does not bork install but only makes life with DM harder... I've learned to live with such defficiencies in testing...

The 2 week ago episode was worse as I missed the fix in the chroot. And only booted into trusty a couple of days later.

---

### Post by ventrical on 2013-12-20
> **philinux said:**
> This borked my install 2 weeks ago as well. I reinstalled then as other things were messed up.

The new trusty .iso for Ubuntu (don't forget) will bring in old files and configs if we do not format our partitons or drives. I was able to fix the lock out this way but inherited some other stuff left over from previous. It's my own fault for not doing proper housekeeping but I 'm just testing on the fly.  I have 10 (real)machines, all with varying stages of installs .. so my installs can get a little dishevled.

---

