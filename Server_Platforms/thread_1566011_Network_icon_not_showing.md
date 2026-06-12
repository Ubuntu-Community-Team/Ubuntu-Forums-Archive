---
title: "Network icon not showing"
date: 2010-09-01
forum: Server Platforms
---

### Post by PHANTOM X on 2010-09-01
I just recently been trying to switch to Ubuntu server, but the Network Icon is not showing up in the right corner. The driver for the card was installed via ethernet, but I'm not sure how to locate the wireless networks available? I checked under Network Connections, but nothing is listed for ethernet or wireless.

Edit: Should note I installed the Ubuntu Desktop after installing the server edition. No servers(lamp, openssh whatever) are installed.

---

### Post by Iowan on 2010-09-01
I've never tried to put a desktop on a server, so I'm not sure if it installs Network Manager. Most servers are configured via */etc/network/interfaces*. What is there?

---

### Post by PHANTOM X on 2010-09-01
I haven't checked there as I'm brand new to the Ubuntu Server thing. Have instructions for setting it up?

---

### Post by PHANTOM X on 2010-09-01
I just found the file.


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

---

### Post by PHANTOM X on 2010-09-02
Bump

---

### Post by arrrghhh on 2010-09-02
> **PHANTOM X said:**
> Edit: Should note I installed the Ubuntu Desktop after installing the server edition. No servers(lamp, openssh whatever) are installed.

So start over.  Install ubuntu-desktop, don't install server then install ubuntu-desktop over it - what advantage would that provide?  Just install the vanilla desktop edition if you want a GUI.

---

### Post by PHANTOM X on 2010-09-02
I redid the installation after that with all the servers and everything. However, I want a server that can be wireless, but I want a gui. Never heard of Vanilla Desktop. Do you have a link?

Edit: I think I get what your saying on the first part. Install Ubuntu Desktop edition, then the servers after.:)

---

### Post by arrrghhh on 2010-09-02
Yes.  If you want a GUI, skip the server edition entirely.  Install Ubuntu Desktop as you would a normal PC - and you can install all of the same services, and have them run sessionless just like a server.

So there's nothing you're missing by not using the server edition.  The server edition is for people who want minimal overhead - no extras basically.  If you want a GUI, instead of fitting a square peg into a round hole, just start with Ubuntu Desktop edition.  Much easier/simpler setup then :D

---

### Post by PHANTOM X on 2010-09-02
Just did and works great. Thanks.:)

---

### Post by Iowan on 2010-09-02
*Almost* anything you can install on a server can be installed on a desktop. My "servers" tend to be older machines that can't handle a GUI. Glad you got it going. If it "stays fixed", consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").
Thanks! :)

---

