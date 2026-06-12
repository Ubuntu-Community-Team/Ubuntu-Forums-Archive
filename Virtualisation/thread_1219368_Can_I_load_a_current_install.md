---
title: "Can I load a current install"
date: 2009-07-21
forum: Virtualisation
---

### Post by VastOne on 2009-07-21
Can I load an already installed Windows that is on a partition on this machine in VirtualBox?

It would be nice to be able to do this but I will install it from scratch if needed.

I am looking to run a Quickbooks 2009 Pro setup from here, any opinions on that?

---

### Post by bacil on 2009-07-21
Yes you can.

there is couple of things you need to do first tho.

1. while booted to your windows create new hardware profile 
2. boot to your linux
3. create boot disk that will link to your exiating win and provide mbr for it
4. boot in an dont forget to switch profile

detailed step by step guide is here

[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

it is for slightly older version but it works fine on current 3.0

---

### Post by VastOne on 2009-07-21
> **bacil said:**
> Yes you can.

there is couple of things you need to do first tho.

1. while booted to your windows create new hardware profile 
2. boot to your linux
3. create boot disk that will link to your exiating win and provide mbr for it
4. boot in an dont forget to switch profile

detailed step by step guide is here

[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

it is for slightly older version but it works fine on current 3.0

Thanks Bacil

I was hoping for this little nugget!

---

