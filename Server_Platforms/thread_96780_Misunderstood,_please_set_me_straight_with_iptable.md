---
title: "Misunderstood, please set me straight with iptables, etc."
date: 2005-11-29
forum: Server Platforms
---

### Post by Il_Tuo_Nome on 2005-11-29
Before I came to Ubuntu, I used Mandrake/Mandriva for awhile, using guarddog as a frontend. At that time, I misunderstood that iptables and shorewall were the same thing, and that all Linux Distro's had iptables installed as default and guarddog/firestarter were the frontends for that. I've now learned iptables and shorewall are seperate and must be configured for a firewall to even be present. Unless of course one of the frontends are used.

Now I've tried following different threads regarding iptables and it's need, but my disability prevents me from keeping things seperate, so it's hard to follow along. All I'm looking to do is run a stand alone PC to re-learn CLI from several years past. While doing that, I want my broadband connection to be protected by a firewall. At the same time, my firewall letting programs like bittorrent and file sharing use whatever ports needed. For me firestarter is not going to work, to complicated to configure. Do I have the option to use guarddog with Ubuntu 5.10, since it's gnome based? Or do I need to learn how to write a script for iptables, and if so are there tutorials for that?

I apologize for being a neussance and posting this type of concern again, but I could really use the help, so I can get things back to normalcy.

Thank you in advance

---

### Post by cactus on 2005-11-29
netfilter is (the kernel hooks for ip_tables).
sometimes people say iptables, and they are referring to netfilter in the kernel (ip_tables).
sometimes they mean the iptables userspace interface.

They are not the same. The iptables program (/sbin/iptables) is used to set the policy in kernel space. Guardog and firestarter also set the policy for the kernel space counterpart. They are just alternate userspace utilities.

to further complicate things, some userspace utilities, are just front ends for the iptables userspace utility.
neat huh?

for more info than you can shake a stick at...
[http://www.netfilter.org/](http://www.netfilter.org/)
[http://www.netfilter.org/projects/iptables/index.html](http://www.netfilter.org/projects/iptables/index.html)

---

