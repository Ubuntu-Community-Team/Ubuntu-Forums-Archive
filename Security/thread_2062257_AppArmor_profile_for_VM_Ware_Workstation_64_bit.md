---
title: "AppArmor profile for VM Ware Workstation 64 bit"
date: 2012-09-24
forum: Security
---

### Post by Welly Wu on 2012-09-24
I did a couple of searches on Google and within Ubuntu Forums, but I did not find anything useful yet.

I have VM Ware Workstation 9.0.0 64 bit and a Microsoft Windows 7 64 bit Ultimate Edition Service Pack 1 guest virtual machine. I want to either download, load, and enable an existing Novell AppArmor profile or I want to create my own for VM Ware Workstation 64 bit. I read the AppArmor sticky, but I don't feel comfortable creating my own AppArmor profile yet.

How would I go about doing this? I want to restrict VM Ware Workstation by limiting the damage from a VM Escape attack vector.

What do I need to know in order to accomplish this?

I have never created my own AppArmor profile in the past so I need help and I will ask a lot of questions.

Thank you.

---

### Post by Welly Wu on 2012-09-24
It seems that I will have to create my own custom Novell AppArmor profile for VM Ware Workstation 64 bit.

I would like to restrict it from reading my /home directory and my external storage devices which are protected using LUKS encryption. I want it to have normal network access so that I can use a web browser or use a software application that requires Internet access.

What else should I consider?

How do I write my custom AppArmor profile for VM Ware Workstation 64 bit without breaking it and corrupting Windows 7 64 bit?

---

### Post by Hungry Man on 2012-09-24
There's a sticky in this subforum that gives a guide for creating apparmor profiles. I've also written a guide here
[https://insanitybit.wordpress.com/2012/05/29/apparmor-how-to/](https://insanitybit.wordpress.com/2012/05/29/apparmor-how-to/)

Between these two I think you should be able ot create the profile.

---

