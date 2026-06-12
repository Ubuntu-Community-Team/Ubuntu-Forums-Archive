---
title: "OpenXenManager with XEN Server and xcp-xapi?"
date: 2013-06-06
forum: Server Platforms
---

### Post by CyberAngel on 2013-06-06
I installed a Xen Server by following the documentation here: [https://help.ubuntu.com/community/Setting%20up%20Xen%20and%20XAPI%20%28XenAPI%29%20on%20Ubuntu%20Server%2012.04%20LTS%20and%20Managing%20it%20With%20Citrix%20XenCenter%20or%20OpenXenManager](https://help.ubuntu.com/community/Setting%20up%20Xen%20and%20XAPI%20%28XenAPI%29%20on%20Ubuntu%20Server%2012.04%20LTS%20and%20Managing%20it%20With%20Citrix%20XenCenter%20or%20OpenXenManager)

The problem is that I cannot connect to it using OpenXenManager (or any other remote tool) as it only listens on [http://localhost:80/](http://localhost:80/)

The server is baremetal so there is no GUI and I do not want to install just to be able to run OpenXenManager locally as they do in this tutorial.

I tried to add the option "http-host = 0.0.0.0" or "http-host = <external-ip>" in /etc/xcp/xapi.conf (which is empty by default) but I had no luck with it.

Does anyone know how can I make this server listen to an external interface?

---

### Post by volkswagner on 2013-06-06
Sorry I have never installed Xen.  I do currently use XenServer and like it very much.  I have tried OpenXenManager a couple years back and found it either buggy or had limited function.

Anyway, provided the GUI is not actually required you could try reverse tunneling via ssh.

```
ssh username@192.168.10.11 -L 80:192.168.10.11:80
``` 

The above assumes 192.168.10.11 is the ip address of your server.

You could then open a web browser from the machine you are ssh'ing from and use localhost as the web address.

Although I said I'm happy with XenServer, I have not been able to install Ubuntu Past version 10.04.  I'm using XenServer 5 though.

You may also look into KVM instead.

---

### Post by CyberAngel on 2013-06-07
Thank you for the answer.

I have managed to connect with ssh tunneling, but it is not a very elegant solution as you need to start an ssh connection before any other connection to the XCP.

The ultimate goal is to try to add Xen hypervisor as a compute node in an openstack cloud and not only connect with OpenXenManager. So I need to have port 80 open in the external IP of the compute node. There should be some options to configure this but I cannot find any working ones at least :(

I mostly use KVM with libvirt or virt-manager. It is straight forward to setup and it simply works beautifully :)

---

### Post by CyberAngel on 2013-06-28
I just solved this problem.

My default network interface is eth1, thus XCP is creating xenbr1 which is the default management interface.
Changing the directive MANAGEMENT_INTERFACE='xenbr0' to MANAGEMENT_INTERFACE='xenbr1' in /etc/xcp/inventory solves the problem.

Also the file /etc/xcp/xapi-ssl.conf looks like it's the main configuration file instead of /etc/xcp/xapi.conf which is intentionally left blank as it says, but it does not exist before you make the change in the MANAGEMENT_INTERFACE directive.

---

