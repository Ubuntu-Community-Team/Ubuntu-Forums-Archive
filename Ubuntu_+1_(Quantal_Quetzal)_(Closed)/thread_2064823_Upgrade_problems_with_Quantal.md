---
title: "Upgrade problems with Quantal"
date: 2012-09-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by thedoctor81877 on 2012-09-30
I suppose this is the right place for this new thread. I have recently upgraded from Lubuntu 12.04 to 12.10 beta 1, and now when I try to upgrade to beta 2, I get (both from the Software manager, and from the Terminal) the following messages:

```

W: Failed to fetch http://archive.canonical.com/dists/[distro]/partner/source/Sources  404  Not Found [IP: 91.189.92.150 80]

W: Failed to fetch http://archive.canonical.com/dists/[distro]/partner/binary-i386/Packages  404  Not Found [IP: 91.189.92.150 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

How can I resolve this and get upgraded to beta 2?

Thanks.

---

### Post by dino99 on 2012-09-30
Sometimes the servers are down for maintenace or else (weekend); retry later, if you only get error for this server that means the others are well checked, no worry.

---

### Post by thedoctor81877 on 2012-09-30
Upon purging, reintsalling, and then updating, I get the following:


```


enigmail.js: Registered components
caught error TypeError: Cc['@mozilla.org/mime/pgp-mime-decrypt;1'] is undefinedmimeDecrypt.jsm: MimeDecryptor registration done
** (thunderbird:16164): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/null.png,
borders don't fit within the image

** (thunderbird:16164): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/scrollbar_vertical.png,
borders don't fit within the image

(thunderbird:16164): GLib-GIO-ERROR **: Settings schema 'org.gnome.Evolution.DefaultSources' is not installed

Trace/breakpoint trap (core dumped)



```

---

