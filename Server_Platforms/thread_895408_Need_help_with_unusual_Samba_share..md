---
title: "Need help with unusual Samba share."
date: 2008-08-20
forum: Server Platforms
---

### Post by Lutrova on 2008-08-20
I have an Ubuntu webserver set up in VirtuaBox on my local Windows machine, so *nevermind* any security issues whatsoever as this is only meant for rapid web development on my part. My issue is this.... I'm operating under Windows XP obviously. I finally got a lot of the security fluff removed or fixed so I can FTP directly to /var/www and load PHP files without errors. However I'd prefer to use a Samba share so I can just open/edit/create/drag-drop files directly from Windows to the Linux share as I work. I have followed every single direction for creating shares, enabling guest access and so forth, but no matter what I do the directory (/var/www) can be viewed but I cannot write, create, or delete files or directories.

My question is...how do I share this directory so I can read/write to it without any problems? Again I'd like to reiterate this is NOT a public server and is running under VirtualBox. It is perfectly OK to forgo any security in favor of functionality here.

---

### Post by Ximbiot on 2008-08-20
> **Lutrova said:**
> I have followed every single direction for creating shares, enabling guest access and so forth, but no matter what I do the directory (/var/www) can be viewed but I cannot write, create, or delete files or directories.

You followed all the Samba instructions, but have you given file system write access to the directory for whatever user the Samba process is running as?  If you are logging into the samba user as yourself, this should be your own username but I'm not sure what username a guest login uses:

```
chown -R username /var/www
```

Of course, if you really aren't worried about security at all, you could give write access to everybody and render the user running the samba process moot:

```
chmod -R a+w /var/www
```

---

### Post by Lutrova on 2008-08-20
> **Ximbiot said:**
> Of course, if you really aren't worried about security at all, you could give write access to everybody and render the user running the samba process moot:

```
chmod -R a+w /var/www
```

Thank you very much, that worked just like it was supposed to. I don't know why I didn't think about that.

---

