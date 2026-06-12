---
title: "Is it safe to upgrade my web server from Ubuntu 11.04 to 11.10?"
date: 2012-02-14
forum: Server Platforms
---

### Post by THPubs on 2012-02-14
Currently, im planing to move my site to Mediatemple. When installing an OS in the server, the latest Ubuntu version they show is 11.04. So, is it safe If I update it to 11.10 with "do-release-upgrade"? The server is new and I have nothing to loose yet!

---

### Post by SeijiSensei on 2012-02-14
If you're running a server, I'd stick with LTS versions like 10.04.  Ordinary Ubuntu releases have relatively short support periods compared to the life of an average production server.  Occasionally you'll run into problems with software requiring new versions of your servers; Wordpress is a good example. Otherwise, stable releases with long-term support make the most sense for servers.

Before you move anything, I'd create a VirtualBox VM on a system some place, install 10.04 Server in it, then transfer your current installation to that.  Make sure everything works correctly.  Once you've convinced yourself that you know how to do this without creating problems, you're ready to move on to the new production server.

---

### Post by THPubs on 2012-02-14
> **SeijiSensei said:**
> If you're running a server, I'd stick with LTS versions like 10.04.  Ordinary Ubuntu releases have relatively short support periods compared to the life of an average production server.  Occasionally you'll run into problems with software requiring new versions of your servers; Wordpress is a good example. Otherwise, stable releases with long-term support make the most sense for servers.

Before you move anything, I'd create a VirtualBox VM on a system some place, install 10.04 Server in it, then transfer your current installation to that.  Make sure everything works correctly.  Once you've convinced yourself that you know how to do this without creating problems, you're ready to move on to the new production server.

Thanks my friend, I just found out why Mediatemple is not supporting Oneiric! Ubuntu 11.10 have a nasty bug where the upstart will take nearly 100% of your CPU! It effects some users who use virtual machines! It also doesn't reboot correctly! I think I have to stick with Natty for now. I'll upgrade to 12.04 as soon as they release it! Anyway, thanks for your answers!

---

