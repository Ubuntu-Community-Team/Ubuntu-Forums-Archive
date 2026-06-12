---
title: "How to set kernel boot option?"
date: 2015-10-20
forum: Ubuntu Phone and Tablet
---

### Post by kuh74 on 2015-10-20
I bought BQ Aquaris 4.5 Ubuntu Edition and had a full linux distro in my hand, literally.

Now I want to use Tomoyo Linux MAC for security reason.

To activate Tomoyo MAC, I need to add 'security=tomoyo' in kernel boot option.


But, how can I set kernel boot option in Ubuntu Touch?

On Ubuntu Desktop, I can edit 'grub.conf'.

On Ubuntu Touch, I can't find 'grub.conf'.

Any advice or link will be welcome.

---

### Post by Drwd on 2015-10-23
[https://sturmflut.github.io](https://sturmflut.github.io)

I hope the website solve your question.

---

### Post by grahammechanical on 2015-10-23
Ubuntu Phone use AppArmor among other things as part of its security model.

[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

[https://developer.ubuntu.com/en/publish/security-policy-groups/](https://developer.ubuntu.com/en/publish/security-policy-groups/)

[https://developer.ubuntu.com/en/start/platform/guides/content-hub-guide/](https://developer.ubuntu.com/en/start/platform/guides/content-hub-guide/)

[https://developer.ubuntu.com/en/start/platform/guides/app-confinement/](https://developer.ubuntu.com/en/start/platform/guides/app-confinement/)

Are you sure that Ubuntu phone devices use Grub as the boot loader? And not some Android boot loader? Anyway check out the heading Device-specific changes in this page. It will tell where the kernel config file resides

[https://developer.ubuntu.com/en/start/ubuntu-for-devices/porting-new-device/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/porting-new-device/)

Regards.

---

### Post by kuh74 on 2015-10-25
> **Drwd said:**
> [https://sturmflut.github.io](https://sturmflut.github.io)

I hope the website solve your question.

Thank you for the link.

I found next link about abootimg is particularly relevant.

([https://sturmflut.github.io/ubuntu/bq/2015/07/02/hacking-the-bq-part-4-building-and-booting-a-kernel/](https://sturmflut.github.io/ubuntu/bq/2015/07/02/hacking-the-bq-part-4-building-and-booting-a-kernel/))

After trying to install abootimg on the phone with apt-get, I realized that abootimg is only available for i386 or amd64.

I will try again with abootimg after I get access to i386 or amd64 ubuntu machine.

Thank you for the guide.

---

### Post by kuh74 on 2015-10-25
> **grahammechanical said:**
> 
Are you sure that Ubuntu phone devices use Grub as the boot loader? And not some Android boot loader? 


I am now sure that Ubuntu phone does not use GRUB as the boot loader.


Most of the instruction on setting linux kernel boot option leads to editing grub.conf,

and by following that instruction, I mistakenly treated the Ubuntu phone just as ubuntu on x86.

As Drwd gave hint, I should have used abootimg.

Thanks

---

