---
title: "Ubuntu-minimal only"
date: 2010-11-26
forum: Server Platforms
---

### Post by Snelhest on 2010-11-26
Hello,

As far as I know both the mini and alternate-images installs ubuntu-standard + ubuntu-minimal.

Is there any way to skip the installation of ubuntu-standard completely and just install ubuntu-minimal?

I've been searching for a solution through the forums and Google but I didn't find any.

---

### Post by volkswagner on 2010-11-26
the alternate has an option vm install a command line system, which should give you a minimal system if you don't select any additional packages.  you may need to select expert install.

for a real barebones system check out turnkeylinux has a jeos image.

---

### Post by cj13579 on 2010-11-26
If you just want a bare bones GUI with no frills you could try:

```
sudo apt-get install -no-install-recommends ubuntu-desktop
```

You can obviousely change the ubuntu-desktop to any other flavour of Ubuntu (X/K) that you like.

---

### Post by cj13579 on 2010-11-26
Sorry, probably should have added.. do a server install first and then run the install desktop command.

---

### Post by Snelhest on 2010-11-26
Thanks to both of you who have replied!


I have tried the alternate-command-install. It however automatically installs ubuntu-standard as well which i do not need.

I'm just looking for an Ubuntu install with ubuntu-minimal and nothing more. No GUI and not the ubuntu-standard metapackage. Surely it must exist an easy way to achieve this.

Installing the alternate and then removing ubuntu-standard is not an option really. As I'm going to install it on several computers I want to be able to complete an install very quickly and this just seems like a bad solution for me.

---

### Post by Cheesehead on 2010-11-26
Ubuntu-minimal (only) is distributed as the Minimal CD image.

Images are at [https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

---

### Post by Snelhest on 2010-11-26
> **Cheesehead said:**
> Ubuntu-minimal (only) is distributed as the Minimal CD image.

Images are at [https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

I have already tried that one and it installs the ubuntu-standard package as well.

That CD would be useful as youre always getting the latest packages but when downloading all those packages it takes a while for an installation to complete.

---

