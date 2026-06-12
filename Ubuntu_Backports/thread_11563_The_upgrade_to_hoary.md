---
title: "The upgrade to hoary"
date: 2005-01-17
forum: Ubuntu Backports
---

### Post by HiddenWolf on 2005-01-17
I reverted my backports, and went to hoary.

There was a major problem there.
After I removed my backports, firefox wouldn't load.
I thought, fine. I'll upgrade to hoary anyhow.

However, on the upgrade path, i got stuck several times, due to firefox and one of it's libs not being properly set up.
I had to remove firefox, and thus lost all cookies and bookmarks and stuff before I could install ubuntu-desktop

The same would've applied for Gimp, but I removed that one before I upgraded.

---

### Post by jdong on 2005-01-17
I'll definitely have to play with it. It's definitely possible that FF 1.0 has new configuration options that FF 0.9.x is unable to parse. However, getting FF 1.0 back from Hoary should resolve that -- just don't use firefox in the meantime!

I've got to do a lot more testing from backports to Hoary. I'm mirroring about 5 copies of my Warty chroot environment for this purpose.

---

### Post by HiddenWolf on 2005-01-18
[QUOTE=jdong]I'll definitely have to play with it. It's definitely possible that FF 1.0 has new configuration options that FF 0.9.x is unable to parse. However, getting FF 1.0 back from Hoary should resolve that -- just don't use firefox in the meantime!

I've got to do a lot more testing from backports to Hoary. I'm mirroring about 5 copies of my Warty chroot environment for this purpose.[/QUOTE]

In the meantime, I had a rough path getting to hoary
Somehow the dist-upgrade froze, I had to hard-reboot, corrupted my filesystem, broke   dpkg and my ppp internet module at the same time.

So I reverted back to warty, but then had no internet, since those ppp scripts are hellish to get going, especially without help from irc/google.
This morning I bought a router, so now I've got internet over dhcp, and I'm again upgrading to hoary.

---

### Post by nocturn on 2005-01-18
[QUOTE=jdong]I'll definitely have to play with it. It's definitely possible that FF 1.0 has new configuration options that FF 0.9.x is unable to parse. However, getting FF 1.0 back from Hoary should resolve that -- just don't use firefox in the meantime!

I've got to do a lot more testing from backports to Hoary. I'm mirroring about 5 copies of my Warty chroot environment for this purpose.[/QUOTE]

Jdong, normally the 1.0 config files should be allright under 0.9.
Before installing your backport, my wife was using 0.9 with the config she had from 1.0 under Gentoo...

---

