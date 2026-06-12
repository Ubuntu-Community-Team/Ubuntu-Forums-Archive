---
title: "KVM + Virt-Manager = no go"
date: 2011-12-01
forum: Server Platforms
---

### Post by Colo2 on 2011-12-01
Hi there.

I managed to get this working once before, but after a restore of the Ubuntu server, it hasn't worked.

I add a new connection in Virt Manager, and it gives me the following:

> Unable to open a connection to the libvirt management daemon.

Libvirt URI is: qemu+ssh://root@XX.XX.XXX.X/system

Verify that
- The 'libvirt-bin' package is installed
- The 'libvirtd' daemon has been started
- You are a member of the 'libvirtd' group.

As far as I can see, each of those suggestions are covered. I don't understand what's up.

I've raked the internet, and can't find a solution. Help would be great. Thanks :)

Tom

---

### Post by Colo2 on 2011-12-01
problem fixed by a friend:

"dpkg-reconfigure locales" on the server!
And the rm -r .ssh on the client

---

