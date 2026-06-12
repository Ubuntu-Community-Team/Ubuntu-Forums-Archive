---
title: "Fully automated network, host name configure and DNS register in the first boot"
date: 2011-07-29
forum: Server Platforms
---

### Post by showmanlkz on 2011-07-29
Hi guys,

My organization is running a VMware vSphere based platform. On top of that we have a Sun Gridengine cluster consists of a number of ubuntu VMs.

At the moment, we deploy new cluster nodes from the VM template. Although it already saves us lots of time, we still need to configure the network, host name, register DNS record manually.

In a near future, we will need to add 100+ more hosts to the cluster. So we are seeking a automated deployment so that a VM does the following during its first boot:

1)configure the network for the correct IP with DHCP or manual.

2)request a designate host name (maybe from a pre-defined datasource?) and configure host name.

3)register itself to our DNS servers.

We don't really have experiences for running big cluster. So welcome to share your opinions and experiences.

Specially I'd very keen to find out if there is any well-proven solution right there or I will need to implement from the scratch.

Cheers,
Derrick

---

### Post by Wayne_V on 2011-07-29
The DHCP server should hand out valid IPs.   If configured, the client can request a specific hostname (see dhclient.conf).   The DHCP server should then register the new IP/hostname with the DNS server, not the client.

---

### Post by Wayne_V on 2011-07-29
[http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/](http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/)

---

### Post by showmanlkz on 2011-07-31
> **Wayne_V said:**
> [http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/](http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/)

thanks Wayne. Dynamically update DNS server via DHCP server is a doable solution for part of my issue. :D

But how to automatically request a correct IP from DHCP server is still unclear to me.

I know that our DHCP server can assign a preserved correct IP based on a machine's MAC.

But I won't know the VM's MAC until I deploy one from the template. At this stage, I have to copy down the MAC and enter into the DHCP server manually.

I wonder if I can make the VM proactively register its MAC on the DHCP then receive the IP?

Cheers,
Derrick

---

### Post by showmanlkz on 2011-08-02
bump!

---

### Post by Wayne_V on 2011-08-04
I don't know of any way for a system to go out and configure the DHCP server with static info on boot.  I suppose you could write a 'first run' init.d script to do that but I don't think it would be trivial.

What type of platform are the vm's hosted on?   Could you write a script there that would extract the MAC from the vm's config file and then update the dhcp server with the required IP/hostname, before the vm is ever turned on?

---

### Post by showmanlkz on 2011-08-04
> **Wayne_V said:**
> I don't know of any way for a system to go out and configure the DHCP server with static info on boot.  I suppose you could write a 'first run' init.d script to do that but I don't think it would be trivial.

What type of platform are the vm's hosted on?   Could you write a script there that would extract the MAC from the vm's config file and then update the dhcp server with the required IP/hostname, before the vm is ever turned on?

Hey Wayne, our cluster is VMware vSphere 4 based. We use vCenter for managing the VMs.

VMware provides SDK/API for the external apps to interact with its vSphere infrastructure. So I think extract MAC and register the MAC to DHCP server before the VM is turned on is possible. But it won't be trivial to write such plug-in either.

I am just curious about for those guys managing several thousands hosts in the data centers, what do they do to make their life easier? :confused:

The closest example I could find is deploying VM on Amazon Cloud, obviously a VM has had IP, host name & DNS setup when it's on without user's interaction. I am wondering how it happens...

---

### Post by Wayne_V on 2011-08-05
see pg 46 here:  [http://www.vmware.com/pdf/vsphere4/r41/vsp_41_vm_admin_guide.pdf](http://www.vmware.com/pdf/vsphere4/r41/vsp_41_vm_admin_guide.pdf)

is this the process you use for creating the new vm's from the template?   If so, then you should be able to customize the vm to have a specific hostname and then the (properly configured) dhcp server should be able to update the dns with that hostname and whatever IP it just handed out.   If you *must* have a specific IP assigned to a specific hostname you might as well do it in the vsphere admin utility when you clone it.  But isn't the point of DNS that you don't need to know the actual IP, all you need is the hostname and then you can find it?

---

