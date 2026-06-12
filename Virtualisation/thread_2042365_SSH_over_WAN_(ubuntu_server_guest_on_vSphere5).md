---
title: "SSH over WAN (ubuntu server guest on vSphere5)"
date: 2012-08-14
forum: Virtualisation
---

### Post by diadem0 on 2012-08-14
I am running a ubuntu server guest on a vSphere 5 host. having issue connecting to it Via SSH while out side the local network, on the local network it works fine.

I have setup fire wall rules for the port Im running SSH over on both the server and router, but I am unable to connect using the public ip/domain.

I can connect to my vSphere 5 management client without a problem.

Anyone got an idea on what the cause could be?

---

### Post by papibe on 2012-08-14
Hi diadem0. Welcome to the forums ):P

I an not familiar with vSphere, but in VirtualBox besides router-to-machine port forwarding, you also need to forward a port from the host OS to the guest OS.

Here are a couple of examples for VB using the [GUI]("http://www.rustyrazorblade.com/2010/12/virtualbox-4-nat-port-forwarding-gui/") and the [terminal]("http://www.virtualbox.org/manual/ch06.html#natforward").

I hope that points you in the right direction.
Regards.

---

### Post by TheFu on 2012-08-14
vsphere allows so very many different network configurations that it is almost impossible for us to help with the information provided.  I'll ask a few questions to get started.

* Is the VM on a normal subnet like any physical server or is it on an internal VMware NAT network?
* Did you trace the entire set of firewalls and port forwards from the public internet through routers, through NAT server to the client OS?
* Are you using port translation correctly?
* Are you using the public IP and correct port in your ssh command?  It is often easier to setup an easy-to-use alias in the remote ~/.ssh/config file.
* Is the sshd actually running on the port you believe it does on the server?

Anyway, I hope these questions will help you find the issue. When I have a failure of this type, it is usually something simple that I did wrong.

---

### Post by Dedoimedo on 2012-08-16
What kind of network type did you configure?
Dedoimedo

---

