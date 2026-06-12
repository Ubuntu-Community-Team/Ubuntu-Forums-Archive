---
title: "Can't connect to ESXi server from Ubuntu !"
date: 2013-02-02
forum: Virtualisation
---

### Post by diski on 2013-02-02
Hi
I am trying to connect to my ESXi server from my laptop using (vmware view open client) but it gives me an error msg that I have to check the server address,port,network and SSL settings !!..the connection is ok and I can ping the ESXi server from the terminal but I can't get into it through any vmware or RDP viewer !!
I have attached a screenshot of the error

Thanks

---

### Post by dcstar on 2013-02-04
> **diski said:**
> Hi
I am trying to connect to my ESXi server from my laptop using (vmware view open client) but it gives me an error msg that I have to check the server address,port,network and SSL settings !!..the connection is ok and I can ping the ESXi server from the terminal but I can't get into it through any vmware or RDP viewer !!
I have attached a screenshot of the error

Thanks

Open View only connects to Windows VMs running inside a Vmware View environment. RDP only connects to Windows VMs.

You can only "connect" to an ESXi server using the VMware Windows vSphere client.

---

### Post by diski on 2013-02-05
That's what I am doing now..installing windows as a vm on Vbox and connecting from there to ESXi server..
Thank you for your reply

---

