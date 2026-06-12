---
title: "making a VM using QEMU KVM with static IP and NFS."
date: 2015-06-30
forum: Virtualisation
---

### Post by er-srivastavarohit on 2015-06-30
I am trying to do a VM install using virt-install. 
following is the command that I am using. 

    virt-install --connect=qemu:///system --name=kickStarthost  --disk=/var/lib/libvirt/images/kickStarthost.img,sparse=true,size=40,format=qcow2 --location="nfs://172.31.97.197/var/nfs/centos6.5/" --initrd-       inject=/var/nfs/anaconda-ks-staticIP.cfg  --extra-args="ks=file:./anaconda-ks-staticIP.cfg" --ram=1024 --graphics vnc  --vcpu 2 --network=network=default --os-type linux --os-variant rhel6


The kickstart file defines the network as following 

    network --onboot=on --device=eth0 --bootproto=dhcp . 

and the installation goes completely fine. 
   
Since the next step for us to move the installation with the static IP (we require it as there are some project dependencies.) I changed the line to 

    network  --bootproto=static --device=eth0 --gateway=172.31.97.193 --ip=172.31.97.200 --nameserver=172.31.100.1 --netmask=255.255.255.240 --onboot=on
 
This fails as the centos installation cannot mount the nfs server. 
The firewall is off so I cannot blame the ports blocking for NFS over static IP.
I am able to mount the NFS from the different server in the same subnet (ip 196) manually.  

I think I am missing some small details for  network setup, Just not sure how I can check for it and the options that I can try. 
Any insight should be helpful.

---

### Post by slickymaster on 2015-06-30
Hi er-srivastavarohit, welcome to the forums.

I've moved your thread to the **Virtualisation** sub-forum, which is the proper venue for it and where you might get the better help for your problem.

---

### Post by er-srivastavarohit on 2015-06-30
THanks .. :)

---

