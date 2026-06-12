---
title: "should I install via apt-get or flatpak?"
date: 2020-01-02
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2020-01-02
Running Lubuntu 18.04.

RIght now, I'm presented with two install options of Rhythmbox, install through apt-get or install through flatpak. I'm confused as to what method of installation I should go for.

---

### Post by CatKiller on 2020-01-02
If you're getting *those* options then you're doing it wrong. This isn't Windows; going to some random website and downloading some random thing is not the way to go about it. You should be using your package manager to install things: that's what it's there for.

---

### Post by ardouronerous on 2020-01-02
> **CatKiller said:**
> If you're getting *those* options then you're doing it wrong. You should be using your package manager to install things: that's what it's there for.

I've made the flatpak option available to me because I needed some  software that isn't available in the standard Ubuntu repos. Was that a mistake? I shouldn't install via flatpak anything at all?

> This isn't Windows; going to some random website and downloading some random thing is not the way to go about it. 

I didn't say I installed from some random website, I use flathub website, isn't that the official repo for flatpak?

---

### Post by oldfred on 2020-01-02
You can install rythmbox, it looks like you have Lubuntu, so it may install a bunch of gnome dependencies. 
Do not know flatpack. 

This is form my 18.04.
```
fred@bionic-z97:~$ apt show rhythmbox
Package: rhythmbox
Version: 3.4.2-4ubuntu1
Priority: optional
Section: gnome
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>

```

---

### Post by ardouronerous on 2020-01-03
> **oldfred said:**
> You can install rythmbox, it looks like you have Lubuntu, so it may install a bunch of gnome dependencies. 
Do not know flatpack. 

This is form my 18.04.
```
fred@bionic-z97:~$ apt show rhythmbox
Package: rhythmbox
Version: 3.4.2-4ubuntu1
Priority: optional
Section: gnome
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>

```

Thanks for the reply.
I know I can install it, but my question is, which is a better install method, apt-get or flatpak?

---

### Post by Artim on 2020-01-03
Definitely apt-get!  You get automatic updates that way, etc.  Flatpaks should only be used if the software is not available in the standard Ubuntu repositories.

---

### Post by ardouronerous on 2020-01-03
> **Artim said:**
> Definitely apt-get!  You get automatic updates that way, etc.  Flatpaks should only be used if the software is not available in the standard Ubuntu repositories.

Thanks.

---

