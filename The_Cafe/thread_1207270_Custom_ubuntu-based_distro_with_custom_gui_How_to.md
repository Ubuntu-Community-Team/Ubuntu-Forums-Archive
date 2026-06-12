---
title: "Custom ubuntu-based distro with custom gui? How to?"
date: 2009-07-08
forum: The Cafe
---

### Post by codyxx on 2009-07-08
Is there an easy way to do this? Essentially, I wanted to embed my desktop layout (global menu, system fonts, dock, custom icons, Ubuntu System Panel, etc.) into a distro for my friends and possibly to share.

---

### Post by aysiu on 2009-07-08
Here are instructions for how to do it:
[http://psychocats.net/ubuntu/remastersys](http://psychocats.net/ubuntu/remastersys)

---

### Post by codyxx on 2009-07-08
So essentially, that would clone the gui I currently have as well, I take it?

---

### Post by aysiu on 2009-07-08
> **codyxx said:**
> So essentially, that would clone the gui I currently have as well, I take it?
There are basically two parts to this:

1) The system settings and 2) the user settings

1) All your system files and settings will be cloned exactly as is, with the exception of the GDM configuration file, unfortunately. So whatever programs you have installed at the time will also be in this new live/installer CD. Whatever repos you have enabled will be enabled. Whatever obscure configuration file you edited will be edited.

2) Nothing in /home will be saved. So if you have special user settings (moved panel, different icon or theme in use, different wallpaper, edited applications menu), you have to copy those to the /etc/skel directory in order for those to apply to the live session user and the first user created during installation.

---

### Post by codyxx on 2009-07-08
Thank you very much.

---

