---
title: "Dell Installation"
date: 2009-10-14
forum: Server Platforms
---

### Post by nrpgeek on 2009-10-14
I've been given a Dell PowerVault 745N server. How do I install Ubuntu with no CD drive?

---

### Post by kevin11951 on 2009-10-14
> **nrpgeek said:**
> I've been given a Dell PowerVault 745N server. How do I install Ubuntu with no CD drive?

In the newer versions of ubuntu (9.04 and 9.10) you can place the ubuntu server image on a usb stick, and install it from there.

And yes, ubuntu server can be installed from usb now.  It can tell and doesn't error out anymore looking for a cd.

---

### Post by nrpgeek on 2009-10-14
Splendid! Thanks Kevin... I'll try that.

---

### Post by BbUiDgZ on 2009-10-14
> **nrpgeek said:**
> I've been given a Dell PowerVault 745N server. How do I install Ubuntu with no CD drive?

sorry to answer a question with a question but is that not a [SAN](http://www1.euro.dell.com/content/products/category.aspx/storage?c=uk&cs=ukbsdt1&l=en&s=bsd&~ck=mn&ST=powervault%20745&dgc=ST&cid=41142&lid=1069631&acd=123807417920567)? and if so can you install an OS on a [SAN](http://www1.euro.dell.com/content/products/category.aspx/storage?c=uk&cs=ukbsdt1&l=en&s=bsd&~ck=mn&ST=powervault%20745&dgc=ST&cid=41142&lid=1069631&acd=123807417920567)?

---

### Post by Pnuts on 2009-10-15
> **BbUiDgZ said:**
> sorry to answer a question with a question but is that not a [SAN](http://www1.euro.dell.com/content/products/category.aspx/storage?c=uk&cs=ukbsdt1&l=en&s=bsd&~ck=mn&ST=powervault%20745&dgc=ST&cid=41142&lid=1069631&acd=123807417920567)? and if so can you install an OS on a [SAN](http://www1.euro.dell.com/content/products/category.aspx/storage?c=uk&cs=ukbsdt1&l=en&s=bsd&~ck=mn&ST=powervault%20745&dgc=ST&cid=41142&lid=1069631&acd=123807417920567)?

yes, its basically a computer geared towards being a storage server. It has all the standard components. It wont be as beefy as other servers, but it functions just the same.

---

### Post by BbUiDgZ on 2009-10-15
> **Pnuts said:**
> yes, its basically a computer geared towards being a storage server. It has all the standard components. It wont be as beefy as other servers, but it functions just the same.

At my work we have 2 powervault 220s SANs and both have no input device ports or VGA outputs of any kind. Each have two scsi ports and two power inputs thats all. Why/How would you even begin to install ubuntu on this?

---

### Post by davepc on 2010-08-16
@nrpgeek
Did you manage to install Ubuntu on it? Ie. get the RAID drivers working?

> At my work we have 2 powervault 220s SANs and both have no input device ports or VGA outputs of any kind. Each have two scsi ports and two power inputs thats all. Why/How would you even begin to install ubuntu on this? 
Its NAS rather then SAN. Basically a P4 raid server.

---

