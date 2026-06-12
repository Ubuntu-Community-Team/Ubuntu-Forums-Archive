---
title: "Server with X"
date: 2009-09-09
forum: Server Platforms
---

### Post by Axrst on 2009-09-09
I' ve just set up a server machine. I'd like to install a light X environment, so according to docs,

To install a minimal X11 on Ubuntu Server Edition enter the following:

```
sudo apt-get install xserver-xorg xserver-xorg-core
```

Next install a Window Manager:
```

sudo apt-get install fluxbox
```

How i start the X session? It doesn't start with startx (i have to install initx...) I don't want to install un-needed packages.

PS. I'd also like not to start X automatically. It is preferred to start in CLI and typing somemething to start the X environment.

---

### Post by Bachstelze on 2009-09-09
Put this into your ~/.xinitrc (create it if it doesn't exist):

```
exec /usr/bin/fluxbox
```

Now when you run startx, it will launch fluxbox. Of course you can also add other commands to it, and they will also be run with startx, for example:

```
exec /usr/bin/fluxbox
exec /usr/bin/xterm
exec /usr/bin/filezilla
```

---

### Post by lykwydchykyn on 2009-09-09
I generally just install the "xorg" package when I need X on a machine.  It installs a few more packages than what xserver-xorg does, but looking down the dependency list they mostly seem necessary.

---

### Post by Bachstelze on 2009-09-09
Yes, you probably want to install xorg too.

---

### Post by ddrichardson on 2009-09-09
This is the second time I've seen this recently, most distro's have a basic .xinitrc launching a couple of xterms using TWM as the WM. Never having run Ubuntu without a GUI does our package have this? Really just interested.

---

### Post by wojox on 2009-09-09
> **ddrichardson said:**
> This is the second time I've seen this recently, most distro's have a basic .xinitrc launching a couple of xterms using TWM as the WM. Never having run Ubuntu without a GUI does our package have this? Really just interested.

No not on the server edition.

---

### Post by ddrichardson on 2009-09-09
> **wojox said:**
> No not on the server edition.
Really? I thought it was part of the X.org reference implementation.

---

### Post by wojox on 2009-09-09
Just the way the kernel is compiled and what's loaded in the filesystem. Very lightweight. Pure terminal.

---

### Post by Axrst on 2009-09-09
> **HymnToLife said:**
> Put this into your ~/.xinitrc (create it if it doesn't exist):

```
exec /usr/bin/fluxbox
```

Now when you run startx, it will launch fluxbox.

Thank you, that worked!

---

### Post by lykwydchykyn on 2009-09-09
> **ddrichardson said:**
> This is the second time I've seen this recently, most distro's have a basic .xinitrc launching a couple of xterms using TWM as the WM. Never having run Ubuntu without a GUI does our package have this? Really just interested.

If you install the xorg package you get this.  The OP just install xserver-xorg and xserver-xorg-core (which was redundant, since the former is a dependency of the latter).

The xorg package will install both of those other packages, plus a bunch of other things such as TWM, xterm, fonts, etc.

---

### Post by ddrichardson on 2009-09-10
> **lykwydchykyn said:**
> If you install the xorg package you get this.  The OP just install xserver-xorg and xserver-xorg-core (which was redundant, since the former is a dependency of the latter).

The xorg package will install both of those other packages, plus a bunch of other things such as TWM, xterm, fonts, etc.
I see now, thanks.

---

