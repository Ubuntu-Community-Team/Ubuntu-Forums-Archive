---
title: "removing vnet0 wmaster0 extra interfaces"
date: 2008-10-14
forum: Virtualisation
---

### Post by Divan Santana on 2008-10-14
Hello,

I tried searching regarding this but couldn't really find any info.

I like my pcs/servers etc clean and I noticed wmaster0 and vnet0 interfaces on a few pcs...

What is wmaster0 for because I'm kinda sure thats its not being used and can hopefully be disabled.

Secondly the vnet0 interface is for kvm virtual shared/private network which I don't need because I use bridge mode, any idea on how to remove these interfaces/disable them?

Thanks,
Divan
(using mostly 8.10/8.04)

---

### Post by Divan Santana on 2008-10-14
Ok I figured out how to remove vnet0 interface...
using virt-manager(as root only otherwise the option is greyed out) you go to the system detail under networking and stop the vnet0 interface and then can delete it.

Great! :)

Now any idea how to remove wmaster0 and what it is there for?

---

### Post by Divan Santana on 2008-10-14
Ok wmaster0 is some type of master wireless device.
Don't think it can really be removed or hidden(sure it can but wont bother). Anyway at least I know and have removed vnet0 which is on many of my servers.

:)

---

### Post by vikofle on 2008-10-17
Hi Diva,

>Secondly the vnet0 interface is for kvm virtual shared/private network >which I don't need because I use bridge mode, any idea on how to remove >these interfaces/disable them?

Do I get you right? Have yoou been able to set up a working guest/host network with a host being hooked up by a wireless device? 

If so could you please post your config files on both host and guest because I ve been trying to accomplish exactly this for a week now using kvm/qemu

V

---

### Post by Divan Santana on 2008-10-17
Hello,I've disable vnet0 but I only mostly use wired connection using bridge mode not wireless.

Not sure how to get it working using wireless. Perhaps using some fancy firewalling or natting its possible.

---

