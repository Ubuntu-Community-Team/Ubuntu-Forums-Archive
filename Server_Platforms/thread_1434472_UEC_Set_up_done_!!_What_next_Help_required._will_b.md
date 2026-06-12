---
title: "UEC Set up done !! What next? Help required. will be helpful for everyone"
date: 2010-03-20
forum: Server Platforms
---

### Post by Sivaa on 2010-03-20
Hi
I have successfully set up a private cloud (on a single blade) based on Ubuntu 9.1 and Eucalyptus. The image store is up and am able to install images.
 
The eucalyptus console has very limited features for creating and managing virtual appliances and for the common cloud management activities.
 
I searched the available documentations but could not find any useful references for taking it further from the cloud setup. I have seen many posts in the forums requesting for the same.
 
It would be great, helpful and useful if someone can share their experience/knowledge as to how to actually utilize the features of the setup cloud and how to take it to the user.
 
Appreciate your help on this.
 
 
Cheers
Siva

---

### Post by kiranmurari on 2010-03-24
Hi Sivaa,

   You can install eucalyptus command line tools to manage your cloud setup. Using these tools you can:     
[LIST]
[*]start instances of the installed images
[*]bundle custom images
[*]start instances of these custom images
[*]create ssh keypairs and use these keys to have a password-less access through
  ssh.
[*]get the status information about the installed images and running instances
[/LIST]
You can also use Hybridfox ([http://www.code.google.com/p/hybridfox](http://www.code.google.com/p/hybridfox)) for connecting to your UEC cluster and perform the above listed tasks using Hybridfox also.
   
Please take a look at the below link on how to bundle a custom image using euca-tools. [http://kiranmurari.wordpress.com/2010/03/23/bundling-linux-image-for-uec/](http://kiranmurari.wordpress.com/2010/03/23/bundling-linux-image-for-uec/)
   
Hope this helps.

---

### Post by Sivaa on 2010-03-25
I did image installation from store, key pair set up and other required configuration setup. When I try running the instance, I get an error "Not enough resources. Try -addressing private". 
 
When I tried -- addressing private, the instance status was pending and after sometimes changed to terminated. Also the guide states that an ip address will be assigned to the instance. But it was always 0.0.0.0 0.0.0.0. I dont see any error log.
 
My server uses a static ip address. Even if I want to use an ip address for vm/instance, I will have to get a static ip address from network team and use it. So I have not provided the public ip pool during installation.
 
I have very limited understanding of networking. So not sure which mode I have to use and which parameters to set.
 
Appreciate any help on this.
 
Cheers
Siva

---

### Post by kiranmurari on 2010-03-26
Hi

In case of SYSTEM mode, your dhcp server present in the network serves ip addresses to the instances. So both private and public ip would be same and would belong to your UEC subnet.

In MANAGED_NOVLAN, eucalyptus uses its own dhcp server to assign private ip address. The public ip addresses can be a range of unused ip addresses belonging to your UEC subnet, which will be associated with a running instance.
   
For MANAGED_NOVLAN mode eucalyptus.conf should be something like this:
```
VNET_PUBINTERFACE="br0"
VNET_PRIVINTERFACE="br0"
VNET_BRIDGE="br0"
VNET_DHCPDAEMON="/usr/sbin/dhcpd3"
VNET_DHCPUSER="dhcpd"
VNET_MODE="MANAGED-NOVLAN"
VNET_SUBNET="172.19.0.0"
VNET_NETMASK="255.255.0.0"
VNET_DNS="my dns ip" # replace with dns ip of your network
VNET_ADDRSPERNET="32"
# Assuming br0 is in the subnet of A.B.C.x, allocate a range of unused ip addresses in that subnet
VNET_PUBLICIPS="A.B.C.10-A.B.C.20"

```For SYSTEM mode eucalyptus.conf should be something like this:
```
VNET_PUBINTERFACE="br0"
VNET_PRIVINTERFACE="br0"
VNET_BRIDGE="br0"
VNET_MODE="SYSTEM"

```Hope this helps.

---

