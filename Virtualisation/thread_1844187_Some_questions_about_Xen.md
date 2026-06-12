---
title: "Some questions about Xen"
date: 2011-09-14
forum: Virtualisation
---

### Post by brenden1030 on 2011-09-14
Hi. I'm thinking of running Xen on my server but I'm kinda have some questions I hope someone will be able to answer for me.

[LIST]
[*]Can I configure Xen to use my router's DHCP server assign an IP to the VM?(Like you can with VirtualBox)

[*]Any tutorials on setting up Xen on Ubuntu 11.04? (It seems like all the tutorials I find is for older versions. Just being a bit cautious.)
[/LIST]

All I want to do is run maybe 2-3 VMs to seperate some stuff out for security, mess around, and etc. I only have 1943MB for disposal so I'm not sure if Xen would be the best option? (Possibly OpenVZ despite the fact of it being a container.)

---

### Post by Dangertux on 2011-09-14
Xen should be fine for your system specifications, depending on the usage level obviously.

Things to consider in regards to Xen are the following

- Ubuntu versions after 9.04 have terrible support for Xen (get ready to custom compile a kernel)

- You can assign dhcp from Dom0 OR your router , however static ip's are generally preferred. You may find your VM's having network issues otherwise. 

- Do NOT firewall Dom0 you will break  your VM instances.

Hope this helps.

---

### Post by haqking on 2011-09-14
> **brenden1030 said:**
> Hi. I'm thinking of running Xen on my server but I'm kinda have some questions I hope someone will be able to answer for me.

[LIST]
[*]Can I configure Xen to use my router's DHCP server assign an IP to the VM?(Like you can with VirtualBox)
[*]Any tutorials on setting up Xen on Ubuntu 11.04? (It seems like all the tutorials I find is for older versions. Just being a bit cautious.)
[/LIST]

All I want to do is run maybe 2-3 VMs to seperate some stuff out for security, mess around, and etc. I only have 1943MB for disposal so I'm not sure if Xen would be the best option? (Possibly OpenVZ despite the fact of it being a container.)


+1 to Dangertux

Canonical and Rehat dropped support for XEN in favour of KVM [http://blog.jdpfu.com/2010/05/14/ubuntu-10-04-and-xen-dom0-not](http://blog.jdpfu.com/2010/05/14/ubuntu-10-04-and-xen-dom0-not)

---

### Post by brenden1030 on 2011-09-14
Ah. I see. I have looked at KVM before but when I have tried before I had issues with trying to have it I guess "request" an IP from my router. I did try googling about it but no one anything on setting up KVM to request an IP from a router. Is it possible with KVM?

---

### Post by brenden1030 on 2011-09-14
> **Dangertux said:**
> Xen should be fine for your system specifications, depending on the usage level obviously.

Things to consider in regards to Xen are the following

- Ubuntu versions after 9.04 have terrible support for Xen (get ready to custom compile a kernel)

- You can assign dhcp from Dom0 OR your router , however static ip's are generally preferred. You may find your VM's having network issues otherwise. 

- Do NOT firewall Dom0 you will break  your VM instances.

Hope this helps.

That is a bit disappointing since Xen is such great software. 

Anyways. Could I have OpenVZ or KVM request an IP from my router? (I have google'd but haven't been able to find really anything besides VirtualBox related stuff with IPs.)

(Whoops I redid a post since Chrome didn't even show my post submitted.)

---

