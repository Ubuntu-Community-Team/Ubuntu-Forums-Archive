---
title: "My own repo?"
date: 2009-02-13
forum: Server Platforms
---

### Post by EvilMarshmallow on 2009-02-13
I'm gradually building more and more linux servers at my company; as I do this, I realize just how many updates my systems receive.

In the windows world where I'm also a sysadmin, they use WSUS... an update server application... that allows for all the MS patches to be loaded to a single server on your local network and distributed to all the PCs that need them.  This prevents every server/workstation from having to hit the internet to get updates, and ultimately conserves bandwidth.

Is there a parallel feature in ubuntu somehow?  I'm imagining setting up a single ubuntu server as an update repository.  Each day, it would download every update needed by all the boxes on my network, and then it would be the only entry in sources.list on each of my servers so they'd get all their updates from there.

Any ideas where to start learning about this?

---

### Post by unixeducation on 2009-02-13
Try this tutorial on creating your own local network repository: [http://keystoneit.wordpress.com/2006/08/25/local-network-ubuntu-repository/](http://keystoneit.wordpress.com/2006/08/25/local-network-ubuntu-repository/)

---

### Post by jimv on 2009-02-14
I think this is a bit easier:

[http://www.arsgeek.com/2007/02/14/how-to-set-up-your-own-local-repositories-with-apt-mirror/](http://www.arsgeek.com/2007/02/14/how-to-set-up-your-own-local-repositories-with-apt-mirror/)

Once that is setup, you simply add your server as the only repo for the other machines.

I did this last week for all my home machines...it's ungodly how fast it is.

---

### Post by ugm6hr on 2009-02-14
apt-proxy is supposed to do this without necessitating downloading and mirroring the entire repository.

[https://help.ubuntu.com/community/AptProxy?action=show&redirect=AptProxyHowTo](https://help.ubuntu.com/community/AptProxy?action=show&redirect=AptProxyHowTo)

I never got around to doing this, since I only have 2 systems per location, and figure it's not worth the bother.

---

### Post by hyper_ch on 2009-02-14
here's another guide for apt-mirror. It's very simple actually:

[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)

---

