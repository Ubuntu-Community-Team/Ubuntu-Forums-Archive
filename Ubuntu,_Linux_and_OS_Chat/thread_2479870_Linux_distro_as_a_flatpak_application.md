---
title: "Linux distro as a flatpak application?"
date: 2022-10-11
forum: Ubuntu, Linux and OS Chat
---

### Post by &amp;KyT$0P# on 2022-10-11
Was browsing Flathub, and noticed [this]("https://flathub.org/apps/details/io.github.paledega.alpine-rootfs").

Seems to be an entire Linux distro packaged to run as a flatpak application?  What's your take on this?  Could it be useful for security and/or sandboxing/containerizing?

---

### Post by grahammechanical on 2022-10-12
There is next to no information as to the purpose of this Flatpak application. The link to the website gives no extra information. So, I am going to say something that will upset certain people. Microsoft has Windows Subsystem for Linux (WSL). This is Alpine Subsystem for Linux. Alpine Linux does not come with a GUI. It uses Busybox Bash as the default shell. I am guessing that this is command line Linux in a container. It is an example of doing something because it can be done. How is this an improvement over existing virtual machine and Linux container technology?

Regards

---

### Post by &amp;KyT$0P# on 2022-10-14
Thanks grahammechanical for looking into it.  Doesn't sound like something I would want to use where security matters.

---

### Post by TheFu on 2022-10-14
Alpine is a light, minimal, distro.  There are lots and lots of reasons for those everywhere.  Whether the flatpak sandbox is more or less security than what an lxc or docker linux container provides, I don't know.  But if you know the flatpak system and don't know the linux container system(s), having access to a tiny, minimal, linux server distributed as a flatpak (flatpaks are meant for desktops hosts, not servers), isn't the worst option.  

It might even be brilliant as a classroom teaching solution to ensure everyone starts with exactly the same thing ... perhaps for a test?  Also, I assume since alpine linux is less than 20MB, the flatpack will be small too, unlike a full VM. Plus flatpaks can be handed around and don't need WAN connectivity like some other single-file installation options.

---

### Post by grahammechanical on 2022-10-16
> How is this an improvement over existing virtual machine and Linux container technology?

Looking at that question I realise that it might seem sarcastic. But I asked that question to keep the discussion going. One of the great things about Linux is the choice available to users. It used to be said "Ubuntu is not a democracy." It is not a cult either. We can share developments in Linux and not restrict ourselves only to Ubuntu related stuff.

Regards

---

