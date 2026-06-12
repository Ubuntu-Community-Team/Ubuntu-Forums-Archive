---
title: "host only mode but see external server share"
date: 2010-02-11
forum: Virtualisation
---

### Post by linuxcss on 2010-02-11
I'm working with virtualbox with network: host only adapter mode running  windows 2000 as a guest session, but i need a share to a remote server (one that is on the local network but not on the VM host machine).

Is it possible to achieve a share of a remote share (not on the host machine)? So that the windows 2000 guest session can see and write only to that remote share and have no other access to the private network and also not to the outside world.

(I installed samba on the VM hosting machine and tried setting up a local share to the remote share but was not successful, is that even possible??)

Or does one have to revert to internal network mode and setup a firewall and alot of other stuff to isolate this window 2000 guest session?

---

