---
title: "Ubuntu Cloud - VmWare Esxi"
date: 2011-06-30
forum: Ubuntu Cloud and Juju
---

### Post by deaner75 on 2011-06-30
I have done a lot of reading and google-ing and utube-ing regarding this subject. I understand the concepts, and what this setup can do. 
 
My question is the hypervisor concept, the fact that I alreay have VM Esxi environment at home and the need to really utilize the cloud experience at all? 
 
I understand that all current VM images are Linux, that although with some work, Windows Images can also be setup and deployed. Plus, the benifit with the Ubuntu cloud is the ability to utilize Amazon's EC2 moving VM's from your private to a public cloud and vice versa, based on need and neccesity. 
 
In all honesty the need for the cloud really falls down to your hardware, local hardware to you. If you can support and create a cloud infistructure to allow you to deploy at will and need, awesome. Hence my referance to my current Esxi setup. I have that very avilability already. Yet, I have also seen the ability of the interaction of the cloud and a VM deployment to your Esxi setup, seen in real time, start and deploy to Esxi system shown in your v-sphere client, fully managable and interactive.
 
Am I missing something regarding the "cloud" or basically in essence it is just another form of hypervisor with the abiltity to move and postion needs private and public based on need? 
 
thoughts.. :-k

---

### Post by kim0 on 2011-07-01
Hi,
So I think you're interested in figuring out whether ESXi is all you need or not. ESX is a hypervisor, and a hypervisor is a big component of the cloud, but it's not everything. Basically things you'd be typically missing would be multitenancy, the ability for each user to directly define and interact with her own resources on the cloud. Also a big one, is laying an API layer on top of infrastructure. It would be great if that API is the Amazon ec2 api as well. Most of that is not directly in ESXi. I know however VMware has built more cloud oriented products (vcloud?) which may have all or some of those features (not following closely). Just hope this reply opens some points to think about. If you're the only user of this cloud, then probably ESXi is good enough though :)

---

