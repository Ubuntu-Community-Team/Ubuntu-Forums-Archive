---
title: "physical server (Ubuntu 10.04) migration to virtual"
date: 2014-07-30
forum: Virtualisation
---

### Post by avatara9 on 2014-07-30
I have Ubuntu 10.04 server, all works fine, is there a method to convert it to virtual image to use it with openVz or KVM on another server ?
I have only SSH-acces to both servers

---

### Post by TheFu on 2014-07-30
Sure. Back it up, create a VM with at least that much storage, then restore it - however, it would be really, smart to migrate to 12.04 or 14.04 at the same time, since you'll probably retain the old physical machine for some period and will have a fall-back point.
[http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview) explains a few options and how I do it.
10.04 server support ends in about 6 months - time to migrate is NOW.

There are a few "gotchas", but anyone running a server should easily be able to avoid those.  Mainly - things change from release to release, so steps to address that are needed - resolv.conf burned me for awhile on 12.04. I still don't like the new way, but have gotten over it.

There are UUID changes - so fixing the /etc/fstab will probably be necessary on any new system - even if virtual.

There will be NIC MAC changes - at least there should be - so you'll manually want to clear/delete any udev rules in /etc/udev/....*net*. That should make sense.

There has been major changes to some common servers - like apache, samba, and probably others, so that config file changes will need to rectify that.

There have been major updates to OS installed scripting files - Perl 5.8 is now 5.14 (or is it 5.18?). Similar for php, python, ruby, ....   for these languages, it is best to avoid the OS-provided versions completely by using something like rvm or perlbrew if you have custom apps anyway. You already know this if you code in those languages and keep up with changes inside those communities.

Anyway - I hope this gets you started on a checklist so the first attempt is 100% successful. If not - well, it is just a VM, so blow it away and start over. That's easy too. ;)

---

