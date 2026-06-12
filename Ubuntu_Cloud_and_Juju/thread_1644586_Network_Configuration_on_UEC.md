---
title: "Network Configuration on UEC"
date: 2010-12-13
forum: Ubuntu Cloud and Juju
---

### Post by drpsycho on 2010-12-13
Hi, I have one computer that is the cloud controller with only one  interface configured with a public ip and other computer that is the  node controller with only one interface also configured with a public  ip. Both are clients of a big network that have a dhcp-server that  distributes public ips for them and for any other computer that is  mapped in the server. My intention is that the vms get ips from this  dhcp server and not from the eucalyptus dhcp server, just like a bridge  in virtualbox or vmware. The vms should have public ips and be acessible  by everybody in the world.

What vnet_mode I have to configure on UEC? system, static, ..??

---

### Post by kim0 on 2010-12-13
Hi there,

According to the table on [http://open.eucalyptus.com/wiki/EucalyptusNetworkConfiguration_v2.0](http://open.eucalyptus.com/wiki/EucalyptusNetworkConfiguration_v2.0)

You need SYSTEM mode

---

### Post by drpsycho on 2010-12-14
Ok, I configured eucalpytus in system mode, but now I have another problem. My dhcp server is mac mapped, and I need the mac address of the instance. How can I connect to the vm to get it? I tried virt-manager to connect to the node and it shows my instances but when I try to open the graphic console It say that it's not configured for guests.

---

### Post by kim0 on 2010-12-15
Hi .. which logged into the NC (KVM box) .. try doing the following. Here is an example for me


# virsh list --all
 Id Name                 State
----------------------------------
  - openstack1           shut off
  - openstack2           shut off


# virsh dumpxml openstack1 | grep 'mac address'
      <mac address='52:54:00:99:d0:d8'/>

---

### Post by drpsycho on 2010-12-17
Hi, I'm on vacation now, but once I'm back to work I'll try this, thanks. But is there a method to connect to the instances in graphic mode? I think it would be necessary in windows instances sometimes.. I know that there is VNC and RDP but if the instance dont have network connection? And if for some reason I need to see the instance booting?
 
 
Another question: There is nothing in UEC that is like VMware VCenter, where you can see the the amount of processor/memory/disk each vm is using, where you can manage the amount of resources of the nodes, manage the vms, the clusters??
In hybridfox for example you can only start and stop instances or other little tasks.. you can't see the status and resources of the vms, etc.

---

### Post by raymdt on 2010-12-17
Hi drpsycho
1- you can try this  method to connect to an instance without IP-address. But it's only for debugging  not for production.

[http://open.eucalyptus.com/participate/wiki/using-vnc-debug-image](http://open.eucalyptus.com/participate/wiki/using-vnc-debug-image)

2- You can get informations about an instance using the virsh  command on the Node or using the virt manager.

  use " man virsh " for the man page.


Regards

---

### Post by drpsycho on 2010-12-18
> **raymdt said:**
> Hi drpsycho
1- you can try this  method to connect to an instance without IP-address. But it's only for debugging  not for production.

[http://open.eucalyptus.com/participate/wiki/using-vnc-debug-image](http://open.eucalyptus.com/participate/wiki/using-vnc-debug-image)

2- You can get informations about an instance using the virsh  command on the Node or using the virt manager.

  use " man virsh " for the man page.


Regards

 I tried virt-manager to connect to the node and it shows my instances  but when I try to open the graphic console It say that it's not  configured for guests.

---

### Post by raymdt on 2010-12-18
[https://help.ubuntu.com/community/KVM/VirtManager](https://help.ubuntu.com/community/KVM/VirtManager)

---

### Post by drpsycho on 2010-12-27
> **kim0 said:**
> Hi .. which logged into the NC (KVM box) .. try doing the following. Here is an example for me


# virsh list --all
 Id Name                 State
----------------------------------
  - openstack1           shut off
  - openstack2           shut off


# virsh dumpxml openstack1 | grep 'mac address'
      <mac address='52:54:00:99:d0:d8'/>

Hi, I tried "virsh list --all" in NC but it doesn't show my domains but euca-describe-instances say that my instances are running. And I still can't make virt-manager work.

Another question: What's the default user and password of the images in the store? I think I will need them if I make vnc or virt-manager work.

---

### Post by raymdt on 2010-12-27
Try this
[http://open.eucalyptus.com/participate/wiki/using-vnc-debug-image](http://open.eucalyptus.com/participate/wiki/using-vnc-debug-image)

---

### Post by drpsycho on 2010-12-30
> **raymdt said:**
> Try this
[http://open.eucalyptus.com/participate/wiki/using-vnc-debug-image](http://open.eucalyptus.com/participate/wiki/using-vnc-debug-image)

Ok, VNC worked. But now I have another question. What's the default user and password of the ubuntu images in  the store?

---

### Post by raymdt on 2010-12-30
Hi,
i think, the password ist been ramdomly generated, when booting an instance the first time (but i'm not sure, please ask  Kim0).
You can either try to get virsh (virt manager) working or build your own images.
Here is a nice howto
[https://help.ubuntu.com/community/UEC/Images](https://help.ubuntu.com/community/UEC/Images)

---

### Post by kim0 on 2010-12-31
Yes, by default the password is auto-generated and you're supposed to login using your ssh keys. If you could access the console over vnc, feel free to reset the password though

---

### Post by raymdt on 2011-01-02
Hi Drpsycho,
you can solve all your problems with "cloud-init"(nice thing) :lolflag:

you just need to create a shell script that will be launched when running the instance.
Also
Example  myscript.sh

```

#!/bin/bash

#delete the password for ubuntu

ubuntu_pass=`awk -F: '/ubuntu/ {print $2}' /etc/shadow`

sed  -e "s#$ubuntu_pass##"  /etc/shadow > /etc/shadowx

mv --force /etc/shadowx /etc/shadow


#show your network configuration so you can pick-up the mac address to put in your dhcp config

ifconfig 

#check if the password was deleted

cat /etc/shadow


```

Now launch the an instance

```

euca-run-instance emi-xxxx -k mykey  -f myscript.sh

```

euca-get-console-output  will give you the output of your script and you can use VNC
to log into the instance with  username: ubuntu  and no password

Regards

---

### Post by drpsycho on 2011-04-15
Hi, I tried the script to reset the password but it didn'd work. I can only connect to the instance using vnc but it keeps asking for password. I don't know other methods to reset the password, only using grub but using vnc thats impossible. SSH isn't working for some reason, the console output shows this:

...
Caught exception reading instance data: [http://169.254.169.254/2009-04-04/meta-data/](http://169.254.169.254/2009-04-04/meta-data/)
Caught exception reading instance data: [http://169.254.169.254/2009-04-04/meta-data/](http://169.254.169.254/2009-04-04/meta-data/)
Caught exception reading instance data: [http://169.254.169.254/2009-04-04/meta-data/](http://169.254.169.254/2009-04-04/meta-data/)
Caught exception reading instance data: [http://169.254.169.254/2009-04-04/meta-data/](http://169.254.169.254/2009-04-04/meta-data/)
...

Thanks.

---

