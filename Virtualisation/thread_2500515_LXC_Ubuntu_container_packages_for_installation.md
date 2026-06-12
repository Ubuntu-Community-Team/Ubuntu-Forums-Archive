---
title: "LXC Ubuntu container packages for installation"
date: 2024-09-04
forum: Virtualisation
---

### Post by guitgentlygeeps on 2024-09-04
I've created many instances of Ubuntu images using the LXD CLI and experimented with them. However, when it comes to configuring these system containers I'm a noob. 
I had thought that when inside a container, that I could use apt-get for instance, to install packages. 
For instance, I'd like to have GCC and net-tools installed in my container but there appears to be no internet access back through my host adapter. 
I've done google searches for this kind of thing and looked at the doc but nothing specifically addresses my problem which seem fundamental. 
Obviously I'm missing something here. Can anyone direct me to documentation or examples to get me rolling? 
Should I be using the lower level tools i.e. lxc-* or can I use the lxc commands in the CLI (LXD) to accomplish what I'm trying to do? 
Thanks a lot in advance.

---

### Post by TheFu on 2024-09-05
By default, Linux containers expect for the hostOS to have a port open and forward inbound connections to the Container OS.  I've never used that mode, since I knew it wasn't any use for my needs.

There are 2 other network modes - NAT and bridged.  [https://documentation.ubuntu.com/lxd/en/latest/howto/network_bridge_firewalld/#prevent-connectivity-issues-with-lxd-and-docker](https://documentation.ubuntu.com/lxd/en/latest/howto/network_bridge_firewalld/#prevent-connectivity-issues-with-lxd-and-docker) tries to explain the configuration needs. Basically, you have lots of choices.

What I ended up doing was creating a network bridge on the host system, just like I'd been doing for KVM/QEMU VMs the last 15 yrs, then setting that bridge as the default for all my lxc container network connections.  There are security considerations in doing this, but it makes each lxc container be treated on my LAN segment just like any physical or VM that is there too. An IP address on the LAN segment is provided using DHCP until I set a static IP inside the container like I would for any physical server.  Exactly the same.

BTW, Docker is known to conflict with lxc in some situations.

---

### Post by guitgentlygeeps on 2024-09-09
Thanks. After A LOT of looking I realized that Docker was probably the cause and I completely removed it. Now I can run apt-get update in my instances. When it comes time that I need Docker I guess I will have to figure out how to have the two co-exist. Again thanks for the reply.

---

