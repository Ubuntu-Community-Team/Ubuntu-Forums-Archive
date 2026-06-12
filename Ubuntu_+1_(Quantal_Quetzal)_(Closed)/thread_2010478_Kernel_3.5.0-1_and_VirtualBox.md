---
title: "Kernel 3.5.0-1 and VirtualBox"
date: 2012-06-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by loukingjr on 2012-06-25
Installed xubuntu 12.10 from the daily build today. I couldn't get the 4.1.8 guest additions to build because it thinks the headers don't match the running kernel. I noticed there are two different linux-images installed, both the same except one says "extra". There are no "extra" headers but when I typed uname -r I get back the normal 3.5.0-1 kernel and not the "extra" one.

I managed to get things working by installing the 4.1.6 guest additions from the repo but it would be nice to have 4.1.8 running.

---

### Post by pressureman on 2012-06-25
The "extra" package is not a separate variant of the kernel. It's a package that contains the majority of kernel modules (eg. including device drivers) that are required on a typical desktop PC.

Virtual machines, due to their limited and semi-standardised virtual hardware, don't require this "extra" package.

Note that quantal has done away with the "virtual" kernel flavour that was available in precise, due to the reasons explained above.

---

### Post by loukingjr on 2012-06-25
> **pressureman said:**
> The "extra" package is not a separate variant of the kernel. It's a package that contains the majority of kernel modules (eg. including device drivers) that are required on a typical desktop PC.

Virtual machines, due to their limited and semi-standardised virtual hardware, don't require this "extra" package.

Note that quantal has done away with the "virtual" kernel flavour that was available in precise, due to the reasons explained above.

I thought as much but I don't understand why I can't install 4.1.8 guest additions yet the 4.1.6 additions from the repos install and work.

---

### Post by CharlesA on 2012-06-25
Did you install the guest additions from the hardware drivers area? I had to do that in 12.04, so maybe it works that way in 12.10.

---

### Post by loukingjr on 2012-06-25
> **CharlesA said:**
> Did you install the guest additions from the hardware drivers area? I had to do that in 12.04, so maybe it works that way in 12.10.
actually I had no trouble installing the guest additions the "normal" way in any 12.04 guest. I've only run into one 12.04 spin that needed the additional driver enabled. not sure why.

---

### Post by CharlesA on 2012-06-25
> **loukingjr said:**
> actually I had no trouble installing the guest additions the "normal" way in any 12.04 guest. I've only run into one 12.04 spin that needed the additional driver enabled. not sure why.
Interesting. I don't think I've actually tried the guest additions from the ISO itself.

Thanks for that.

---

### Post by loukingjr on 2012-06-25
> **CharlesA said:**
> Interesting. I don't think I've actually tried the guest additions from the ISO itself.

Thanks for that.
you're welcome. :)

---

