---
title: "vmware question"
date: 2008-01-27
forum: Virtualisation
---

### Post by DamagePlan on 2008-01-27
If I use vmware to make virtual machine of my vista drive will that mean that It will be just like running my vista os. So I will have everything installed?

Thanks

---

### Post by tribaal on 2008-01-27
The short answer is yes.
(not sure how the 3d desktop capabilities will work tough)

- Trib'

---

### Post by NovaAesa on 2008-01-27
You might want to try using Virtual Box instead of VMWare. I've used Virtual Box for virtualising Vista and it works fine. They work the same, except that Virtual Box is free.

You can install Virtual Box by typing in the terminal:
```
sudo apt-get install virtualbox-ose
```

Or, you can use the GUI method: Search in Synaptic for the package virtualbox-ose and check it's box and hit apply.

EDIT: Unless of course you have another reason for wanting to use VMware.

---

### Post by DamagePlan on 2008-01-27
If I use virtual box then doesnt that mean I will have to install vista again.

---

### Post by rosegarden78 on 2008-01-27
Yes, but see other reply I made for you, if you can make Bootable DVD(s) of your Vista with Norton Ghost then no.
[http://ubuntuforums.org/showthread.php?t=679618&highlight=vmware](http://ubuntuforums.org/showthread.php?t=679618&highlight=vmware)

---

### Post by Achtung on 2008-01-28
> **DamagePlan said:**
> If I use virtual box then doesnt that mean I will have to install vista again.
Yes, you will have to recreate your Vista install in a virtual machine somehow. 

If you plan on using VMWare server (which is free, it only needs you to register with the vmware team to get a serial by email), you can use [VMWare converter]("http://www.vmware.com/products/converter/") v3.0.2 to create a virtual machine from your existing physical Vista computer. That way, you can run a virtual image of your vista install in vmware server on Ubuntu. 
Note that changes you do on your virtual Vista image are confined in the virtual machine file and will not affect your existing Vista install if you are dual booting.

Edited to add : VMWare converter v3.0.2 is beta and might not be stable for everyone!

---

