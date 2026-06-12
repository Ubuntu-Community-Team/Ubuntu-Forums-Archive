---
title: "Is there a Kubuntu Server edition?"
date: 2009-05-06
forum: Server Platforms
---

### Post by geek2330 on 2009-05-06
I've been playing with Kubuntu. I see there's a Ubuntu Server edition but wondering if there's a Kubuntu Server, or can I install Ubuntu Server and then install the KDE platform on top, if so how please ?

---

### Post by x33a on 2009-05-06
afaik, by default the server edition doesn't have a gui, desktop environment etc. 

but you should be able to install kde on top of that.

i haven't used the server edition, but i think kubuntu-desktop or kubuntu-kde4-desktop metapackage should do the trick.

install it with apt-get or aptitude.

---

### Post by geek2330 on 2009-05-06
yeah, was just reading and realized that; thanks

---

### Post by uelkfr on 2011-10-11
My boss in previous organization also told me why a server should have a GUI. But I still say that in a market economy a server with GUI will win. It is not needed to install performance consuming GUI like Unity, GNOME or KDE. You would install some special GUI for low resource consuming, so it is important for Ubuntu Server developer to choose appropriate GUI and develop GUI applications for configuring server. Even UEFI has GUI and it won.

---

### Post by 2F4U on 2011-10-11
> **geek2330 said:**
> yeah, was just reading and realized that; thanks

The basic setup of Ubuntu Server is barebone but you can install any GUI you like, as well as any additional application you like. However, not every application gets the same level of long-term support. As far as I know only what Ubuntu calls the server packages get the long-term support.

---

### Post by arrrghhh on 2011-10-11
> **2F4U said:**
> The basic setup of Ubuntu Server is barebone but you can install any GUI you like, as well as any additional application you like. However, not every application gets the same level of long-term support. As far as I know only what Ubuntu calls the server packages get the long-term support.

Indeed.

With the ability to forward X apps that require a GUI over SSH, there's no need for a GUI.  Just adds complications and complexities that are completely unnecessary.

For those that want a GUI, they can install it - but it probably would be nice to have a choice on install if the user wants a GUI, that Ubuntu could pretty easily support one for Ubuntu Server.  It certainly should not be forced on the users, like Landscape was on servers...

---

### Post by uelkfr on 2011-10-25
It is gold idea to configure server using GUI, but launch X11 Server only by demand: either local user demand or lan user demand (X11 forward over SSH, VNC :0, SPICE), and shutdown X11 Server after it with full resource unloading consumed by X11 Server. If it would be realized by Ubuntu Server team, Ubuntu really could replace CentOS/Red Hat Enterprise and FreeBSD altogether!!!

---

