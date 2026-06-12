---
title: "How to ge the IP address of the guest OS in KVM?"
date: 2009-06-05
forum: Virtualisation
---

### Post by meaning.shim on 2009-06-05
I have installed KVM and managed to start VMs using bridged network. Everything works OK and the VM can get an IP address from the DHCP server. However, when I start a VM in a remote server I should be able to ssh onto it with its IP address. But how can I get the IP addres of the guestOS from the hostOS? I do not want to use static IP address because I may want to boot up many VMs with one identical image. So, is there any way to obtain the IP address of the guestOS? KVM installs some virtual network card (name tap0,1 etc.) but they are bridged, and no IP address are assigned with them. Someone can help me? Thanks very much!

---

### Post by bodhi.zazen on 2009-06-05
As far as I know what you are asking can not be done as the ipaddress is assigned by your dhcp router.

You could probably do it by monitoring your network traffic, but IMO static IP is the way to go.

With your template, assign a static IP to say 10.10.10.10, or what you wish.

Once you bring up your VM, ssh in (to the known IP) and change the static IP.

You could likely script the whole thing.

Another option is to go with a web front end for KVM, such as Proxmox (or openvz). Openvz has outstanding performance and it is quiet easy to access guests.

There are other graphical front ends for KVM, but I have not tried them.

[http://www.montanalinux.org/proxmox-ve-review.html](http://www.montanalinux.org/proxmox-ve-review.html)

[http://www.linux-mag.com/id/7333](http://www.linux-mag.com/id/7333)

Alternates include using the vnc server built into kvm and vnc into the guest (rather then ssh, or vnc over ssh ;)).

kvm -vnc :1
kvm -vnc :2

etc ...

---

### Post by rocket777 on 2009-06-08
> **meaning.shim said:**
>  I do not want to use static IP address because I may want to boot up many VMs with one identical image. 

Won't you still have to change the host name inside each VM? If they are truely 100% identical, won't they each have the same host name? Won't you need to duplicate all their files as well - I don't know much about KVM but can you really run multiple guests simultaneously using the same files?

I have several copies of a vm (using vmware player) that I began with, cloned them, but then changed 3 things using static ip's.

1. host name
2. ip address
3. mac address

My vm's are all win2000 systems, so inside the vm I changed the hostname and ip, and set them up as static ip (in this range 192.168.1.**150-160**) and then using vmware (which normally assigns a mac address) I changed to static mac addresses which I set up individually.

Then in each system I created entries for all the static ips in a hosts file (my host is ubuntu so I added all of them in /etc/hosts, my guests are all windows, so there's a hosts file in the drivers/etc directory).

I think you will find it harder to coordinate if you use identical vm's. It will likely be much harder than using static ip's with nearly identical vm's. In my case, I began by forgetting to change the mac address and the results were very strange indeed.

---

