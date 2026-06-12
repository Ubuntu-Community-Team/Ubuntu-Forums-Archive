---
title: "Moving complex, mission-critical software from RHEL/CentOS to Ubuntu Server"
date: 2020-04-19
forum: Server Platforms
---

### Post by bdutta on 2020-04-19
Hi,

Wondering if there is any up-to-date, well maintained migration guide or migration document, for porting a rather complex, mission-critical software that is today purpose built to run on RHEL (so far running on RHEL7, but soon to be ported to RHEL8), to Ubuntu server ? I did find this rather dated [article ]("https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux/RedHatEnterpriseLinuxAndFedora"), but much water has flown under the bridge since -- both for RHEL/CentOS and Ubuntu.

We depend on linux-HA / keepalived, systemd, nginx, ip-firewall, linux PAM based authentication, security audit trail feature, SElinux enforcing, SCTP transport (apart from TCP and UDP transport), OpenJDK, tomcat, snmpd etc. (to name a few). This software is often deployed in virtual machines (KVM) that is manually provisioned/managed, or even on OpenStack (and managed through a NFV MANO).

Apart from the SW package management differences -- which is fairly evident, would like to know what are the other differences to watchout for ? Of course, having access to any sort of migration guide, would be great.

cheers,
bd

---

### Post by SeijiSensei on 2020-04-19
Ubuntu/Debian rely on AppArmor rather than SELinux to enforce security on applications. That may or may not be a big deal for you.

Assuming "ip-firewall" means writing firewall rules for the native iptables system in the Linux kernel, I'm pretty sure the packages you list exist on both platforms. Linux is Linux regardless of who puts a distribution together. This is especially true for servers. The arrangement of configuration files in places like /etc will differ between the platforms. You won't be able just to copy the content of /etc on the RH machine to /etc on Ubuntu. 

I don't know what the "security audit trail feature" involves so I can't speak about that, nor about OpenStack nor NFV MANO.

---

### Post by bdutta on 2020-04-20
Thanks for the response. The AppArmor instead of SElinux came as a surprise, so did a quick read on the differences and it seemed like a no-go option, as we already depend on the fine-grain control that SElinux offers, and make some design decisions on the separation of policy vs enforcement. However, I noticed that Ubuntu 20.04 seems to add SElinux as an option now !

Indeed, I meant writing firewall rules for native iptables. The difference in filesystem layout is something to definitely look out for, so thanks for that tip.

---

### Post by LHammonds on 2020-04-21
Just curious but what is the driving force to change distros?  I'm not familiar with RHEL/CentOS.  As an individual, I chose Ubuntu because of the friendly environment (particularly linux-newbie friendly) and the option to buy support if I ever built anything mission-critical.

Thanks,
LHammonds

---

### Post by bdutta on 2020-04-22
Customer request to explore this possibility.

---

