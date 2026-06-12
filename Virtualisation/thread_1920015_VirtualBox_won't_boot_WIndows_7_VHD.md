---
title: "VirtualBox won't boot WIndows 7 VHD"
date: 2012-02-03
forum: Virtualisation
---

### Post by Radioman991 on 2012-02-03
Hello:

I used Disk2VHD to grab my Windows 7 boot drive from my work laptop.  When I try to bring it into VirtualBox, I get a " Missing Operating Sys" message and it won't boot.

I tried converting it to a vdi and still no success.  Any ideas on a solution would be appreciated.

Thanks

---

### Post by japzone on 2012-02-04
If you still have the source Laptop harddrive then I'd reccomend trying again but using VMware's [**VMware vCenter Converter**](http://www.vmware.com/products/converter/). It's more well known and is usually very successful and the VMDKs will work in VirtualBox as is or can be converted to VDI.

---

### Post by Radioman991 on 2012-02-04
Thank you.  I will try that.

-pk

---

### Post by Radioman991 on 2012-02-04
That seemed to do the trick after a little tweaking.  Thanks again.

---

### Post by japzone on 2012-02-04
Glad I could help.

---

### Post by LostinTranslation76 on 2012-11-02
> **Radioman991 said:**
> That seemed to do the trick after a little tweaking.  Thanks again.

I have to do the same conversion due to software that will only run on windows and the old PIII hardware it is currently running on is more than a little long of tooth.  I found this thread via a Google search and I will also try the conversion with VMware's [**VMware vCenter Converter**]("http://www.vmware.com/products/converter/").

Radioman, Is there any chance that you can share what the tweaking you had to do to get it working was?

Thank you both for this info to this point.  It should save me a *lot* of trial and error.

---

