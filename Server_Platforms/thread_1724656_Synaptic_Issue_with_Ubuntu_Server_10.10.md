---
title: "Synaptic Issue with Ubuntu Server 10.10"
date: 2011-04-08
forum: Server Platforms
---

### Post by sojakfa on 2011-04-08
Hi all. I have an old box I'm converting into a server for shared network storage, print server, etc. I've installed the latest Ubuntu Server 32 bit on it, along with a gui.

I'm having an issue when I attempt to launch Synaptic Package Manager. When it launches it asks for my administrator password. So I type in the password I set when the server installation created my non-root user. This is the same password I use whenever I sudo anything on the command line.

But for some reason, Synaptic says it is an invalid password. Anybody have any ideas?

---

### Post by sojakfa on 2011-04-08
Nevermind, I resolved this. Apparently it attempts to launch by default with the root user, the password of which is disabled by default in the install. Issuing a 'sudo passwd root' resolved the issue.

---

