---
title: "VMware Player running Windows XP as guest question"
date: 2008-07-19
forum: Virtualisation
---

### Post by tom1371 on 2008-07-19
Hello everyone,

I am new to Ubuntu so excuse my ignorance. I installed Ubuntu LTS8.04 on my laptop with no problems at all. I can access the internet via my wired and also via wireless connection. 
I wanted to run Windows XP on a vmware virtual machine I have, so I installed vmware player in Ubuntu. I then proceeded to load the virtual machine and it comes up fine. The only problem I am having is that I cannot access the internet from the XP virtual machine. The vmware player states that the ethernet is connected and bridged, but inside the windows xp virtual machine I am not able to get an IP address. When I try to start vmware from a terminal windows I get the following:
Starting VMware services:
   Virtual machine monitor                                            failed
   Blocking file system:                                              failed
   Virtual ethernet                                                   failed
   Bridged networking on /dev/vmnet0                                  failed
   Host network detection                                             failed
   Host-only networking on /dev/vmnet1 (background)                    done
   DHCP server on /dev/vmnet1                                         failed
   Bridged networking on /dev/vmnet2                                  failed
   Host-only networking on /dev/vmnet8 (background)                    done
   DHCP server on /dev/vmnet8                                         failed
   NAT service on /dev/vmnet8                                         failed
touch: cannot touch `/etc/vmware/not_configured': Permission denied
chmod: cannot access `/etc/vmware/not_configured': No such file or directory
./vmware: 932: cannot create /etc/vmware/locations: Permission denied

Any ideas to fix my networking on the windows xp vm would be greatly appreciated.

---

### Post by tom1371 on 2008-07-19
Here is an update:
I connected he laptop to a wired network and then booted the XP virtual machine and everything worked fine. I was able to access the internet. 
I guess the question is:
Why can't I access the internet using the Hosts wireless adapter using bridged network?

Thanks for any advice.

---

### Post by WutCake on 2010-03-06
-deleted post-

---

### Post by fjgaude on 2010-03-06
I'm not sure I have an answer to your problem, but suggest you try NAT instead of Bridged. Under brigded each access point gets a different IP address. Maybe your router, if you have one, isn't set for several IPs at a time. With NAt you the access points of the guest get the same IP as the host.

Let us know what happens. Thanks!

---

### Post by dcstar on 2010-03-06
> **fjgaude said:**
> 
..........
Let us know what happens. Thanks!

Do you reckon this problem from** July 2008** is still there?

---

### Post by fjgaude on 2010-03-06
Well, who knows! <smile>

---

