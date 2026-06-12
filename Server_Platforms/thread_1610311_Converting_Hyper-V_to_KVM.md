---
title: "Converting Hyper-V to KVM"
date: 2010-10-31
forum: Server Platforms
---

### Post by M.a.d on 2010-10-31
Hi

I have searched but haven't found anything on how to convert a Hyper-V virtual machine to KVM - only the other way around.

Does anybody here knwo how to do that, or can point me in the right direction? :-)

Any help is much appeciated ;-)

---

### Post by Keraos on 2011-01-11
I'm running into the same issue, can't find any guides on moving from Hyper V to KVM. Does anyone have any advice or help on the matter?

---

### Post by matthew.mattoon on 2011-03-25
A bit late, but I have written an article documenting converting Hyper-V VHD's to KVM.

[http://blog.allanglesit.com/2011/03/linux-kvm-migrating-hyper-v-vhd-images-to-kvm/](http://blog.allanglesit.com/2011/03/linux-kvm-migrating-hyper-v-vhd-images-to-kvm/)

---

### Post by mon_r on 2011-10-07
Hi Matthew, have you tested this on 11.04? I have hyper-v machines that I'd like to use on 11.04 64-bt. At the moment, I'm planning on asking help from someone with VMWare.

---

### Post by Vegan on 2011-10-07
I found it easier when I converted a shop to setup a new server and then sync/copy data from one to the other

This way no HAL problems etc

Windows is very sensitive to the HAL

---

### Post by matthew.mattoon on 2011-10-07
> **mon_r said:**
> Hi Matthew, have you tested this on 11.04? I have hyper-v machines that I'd like to use on 11.04 64-bt. At the moment, I'm planning on asking help from someone with VMWare.

Your question is a bit vague, but I use Ubuntu 11.10 as my hypervisors now, but I did use 11.04 prior to 11.10 being released, my hypervisors run KVM.  The disk images are able to be converted quite easily (fixed images actually don't need to though, and dynamic over 127GB have some sort of limitation), so if your disk is larger than that fixed type is better.

I have a ton of KVM-related articles on my blog which cover conversions, and other key parts of KVM administration.  I also have some Hyper-V ones from back in my Hyper-V days.

Also please keep in mind, someone from VMWare is going to be unable to help you convert VMs from Hyper-V to KVM on 11.04 or anything else for that matter.  They will however be quite good at selling you VMWare.

You can use the contact form on my blog if you are looking for a consulting arrangement.

[http://blog.allanglesit.com](http://blog.allanglesit.com)

-matt

---

