---
title: "VMware Server performance issues"
date: 2009-05-15
forum: Virtualisation
---

### Post by maflynn on 2009-05-15
I'm having performance issues with one of my VMs. I set this one up a little different so in one sense its no surprise that I'm having "issues"

I'm running kubuntu 9.04 (32bit), on a MacBook Pro with 4 gig of ram. Because I have VMware fusion on my OSX partition and a winxp VM on that partition, I copied that to my ubuntu partition and created a new VM used the option to use an existing vmdk (which I then pointed to that winxp.vmdk).

Booting up was painfully slow, probably 4x slower then the fresh winxp vm I created.  Interacting with guest OS was probably slower about 20-30%.  I have it 512meg, initially and when I get home I'll give it a gig to see if that fixes it but swapping wasn't an issue, and I wasn't running anything. IE too forever to boot up.  By contrast the new VM was snappy and IE came right up and I while I had given that a bit more ram - 768meg  it wasn't enough to cause the difference IMO.  

Could there be a difference in the vmdk file formats between vmware fusion and vmware server?  Also when I initially setup the winxp vm in vmware fusion, I used the defaults which I believe is auto grow, and use 2 gig files. That's a different default to what I see in vmware server (auto grow but don't use 2 gig files)

Any advice, the advantage of using the exiting VM is obvious, I don't need to spend a whole night downloading all of the updates M$ pukes out and then load the handful of applications I need.

Any suggestions?

---

### Post by richard.scott on 2009-06-15
Have you figured this performance issue out yet?

I have a 9.04 desktop system setup with Vmware Server running and it is so slow its not usable!

All my vmware guest OS's (which are linux) just freeze as it takes for ever to write to disk.

---

