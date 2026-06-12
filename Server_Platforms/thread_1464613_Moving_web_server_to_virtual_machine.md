---
title: "Moving web server to virtual machine"
date: 2010-04-28
forum: Server Platforms
---

### Post by cr0nick on 2010-04-28
Hey everyone. Im having some trouble moving my ubuntu web server over to a machine running VMWare Server 2.0. I tried using the VMWare Converter tool but I cant get it to work properly in Linux. For some reason It wont let me convert the machine then save the image locally or to a remote source as a .vmdk file or whatever, it keeps asking for the ip and logon info of a remote ESX or ESXi server. 

Ive heard that I could just do a clean install of ubuntu on a virtual machine and then copy all my data/programs over? Or if anyone could help me convert this machine using the converter tool.

Thanks!

---

### Post by windependence on 2010-04-28
You have your target set as am ESX host instead of just converting it to an appliance. 

Aside from that, I would scrap the VMware server and install ESXi on that machine. It's free and much better than VMware server for virtualization. You do not need a host OS, you just install ESXi directly ion the hardware. To avoid problems with hard disc controllers, install ESXi on to a memory stick or get an adapter to use a CF card inside the machine. If you can't find one I have them here cheaper than you can buy them anywhere else. After you have ESXi installed and running you can convert your machine directly to the ESXi box. 

You can definitely convert the machine for use on the VMware server box if you really insist on doing that but walking you through it may take more than I can write here. You probably could get a quick answer on the VMware forums though. Essentailly, you need to pick a different target than you are, that is the problem but I'm not in front of my VMware box right now and don't remember what target you need to choose.

-Tim

---

### Post by cr0nick on 2010-04-28
> **windependence said:**
> You have your target set as am ESX host instead of just converting it to an appliance. 

Aside from that, I would scrap the VMware server and install ESXi on that machine. It's free and much better than VMware server for virtualization. You do not need a host OS, you just install ESXi directly ion the hardware. To avoid problems with hard disc controllers, install ESXi on to a memory stick or get an adapter to use a CF card inside the machine. If you can't find one I have them here cheaper than you can buy them anywhere else. After you have ESXi installed and running you can convert your machine directly to the ESXi box. 

You can definitely convert the machine for use on the VMware server box if you really insist on doing that but walking you through it may take more than I can write here. You probably could get a quick answer on the VMware forums though. Essentailly, you need to pick a different target than you are, that is the problem but I'm not in front of my VMware box right now and don't remember what target you need to choose.

-Tim

Thanks for the response. As far as ESXi goes I would change alot of things around here if I could. Unfortunately im an IT Assistant and our Sys Admin is pretty stubborn.

---

### Post by windependence on 2010-04-28
I gotcha. Let me see if i can get to my VM box and tell you what you want to pick for a target. What version of converter are you using?

-Tim

---

### Post by cr0nick on 2010-04-28
Im using  Vmware vCenter Converter Standalone Client v4.0.1 on Ubuntu Linux. 

Here is what I do

1:) Select Convert Machine
2 ) Source type = Powered on Machine
3 ) I cant select local machine but it says "To convert local machine enter its IP address below. So I do. 
4 ) After I click next the Destination type says "VMWare infrastructure virtual machine" (I cannot select any other option). 
5 ) If i try to type in the IP and logon info for our VMware server it says that the connection is refused.

---

### Post by windependence on 2010-04-28
The problem is in step 4 you should be able to choose "other" and then select VMware workstation 6, etc. 

Try dowloading Vmware converter 3.03 and use that as this is what I am currently using. Here are some screen shots:

---

### Post by cr0nick on 2010-04-28
Now im getting an error saying unable to connect to the vmWare converter agent. The remote host is not accessible using Microsoft network services, it might be down or firewalled. 

Dose this version work on linux?

---

### Post by windependence on 2010-04-28
I don't see why not? It installed right? Can you convert it from a Windoze machine?

-Tim

---

### Post by cr0nick on 2010-04-28
> **windependence said:**
> I don't see why not? It installed right? Can you convert it from a Windoze machine?

-Tim

I couldnt find a version of 3.0.3 for linux so i installed the windows version and tried to do it remotely and Its giving me the above error

---

### Post by windependence on 2010-04-28
[http://downloads.vmware.com/d/details/conv_303_starter/ZGQqYkAlaGJAZA==](http://downloads.vmware.com/d/details/conv_303_starter/ZGQqYkAlaGJAZA==)

---

