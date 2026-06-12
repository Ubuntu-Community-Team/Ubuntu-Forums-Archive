---
title: "How to check i915.i915_enable_rc6=1 is enabled in Ubuntu 12.10"
date: 2012-12-24
forum: Ubuntu Dev Link Forum
---

### Post by vksingh on 2012-12-24
Hi All,

I am using Ubuntu 12.10. I want to enable i915.i915_enable_rc6=1. I want to know do i need to enable it in /etc/default/grub or it is already enabled in Ubuntu 12.10.

If it is already enabled, please tell me how to check and verify this.

Regards,
Vivek):P

---

### Post by Nephtali on 2013-01-17
You can check the parameters of the i915 module by using the following command as root :
```
for i in /sys/module/i915/parameters/*;do echo ${i}=`cat $i`;done
```
To enable i915.i915_enable_rc6=1 you have to do as you said and don't forget to update grub as explained in the file header.

---

