---
title: "One computer as a router, fileserver, LAMP"
date: 2011-08-06
forum: Security
---

### Post by umsorg on 2011-08-06
I would like to use one computer for a lot of things. I know it is not the best way to do it, but for now it is all I can do. But I can try to ensure the security and with that I could really use some help.

Computer is connected to the Internet via PPPoE (ppp0 & eth0). I use it as a router and eth1 is connected to the local network. For firewall system I use Shorewall. But I need to use this computer more than just a router.

I have couple of domain that I would like to host with this computer. So I need apache2, php, mysql and mail services. Best way do this is with chroot? I also use SSH Server, but for now only connections from local network is accepted. If I open SSH to the Internet I should change the port, use keys (dsa) and use sshknock? Can I run all these services in chroot?

Also for local network I need a file-server (SAMBA & CUPS). Is there anything that I can do to increase the security with it?

Thank you for any comments and ideas. Sorry about my English.

---

### Post by bodhi.zazen on 2011-08-06
> **umsorg said:**
> I would like to use one computer for a lot of things. I know it is not the best way to do it, but for now it is all I can do. But I can try to ensure the security and with that I could really use some help.

Computer is connected to the Internet via PPPoE (ppp0 & eth0). I use it as a router and eth1 is connected to the local network. For firewall system I use Shorewall. But I need to use this computer more than just a router.

I have couple of domain that I would like to host with this computer. So I need apache2, php, mysql and mail services. Best way do this is with chroot? I also use SSH Server, but for now only connections from local network is accepted. If I open SSH to the Internet I should change the port, use keys (dsa) and use sshknock? Can I run all these services in chroot?

Also for local network I need a file-server (SAMBA & CUPS). Is there anything that I can do to increase the security with it?

Thank you for any comments and ideas. Sorry about my English.

Well, as you say, you really should not run all those services on your router. As you are running a LAN that implies you have other resources, so, I would allocate your resources differently.

In terms of a chroot, that is sort of old school and for the most part has been replaced by virtualization, from openvz to LXC to KVM to Virtualbox.

In terms of ssh, use keys and disable passwords. Changing from the default port does very little to increase security, IMO.

If you want increased security:

1. Do not run all this on your router.
2. Use keys for ssh.
3. Do not allow samba shares on "the internet".
4. Learn to secure ssh, your mail server, apache, mysql, and php before you deploy them.
5. Learn to use apparmor or selinux. Learning these tools is about as difficult as learning to us a chroot, but will be more secure.

---

