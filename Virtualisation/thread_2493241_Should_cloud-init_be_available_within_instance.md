---
title: "Should cloud-init be available within instance?"
date: 2023-12-07
forum: Virtualisation
---

### Post by RRLangly on 2023-12-07
I have cloud-init 22.4 installed with LXD 5.0.2-r3 on a gentoo machine.

My problem is, when I start a gentoo instance, and then login to the instance with:

lxc exec test -- bash

When I run cloud-init status, I git
	bash: cloud-init: command not found
	
However, I have profiles and network settings that I can see that have been executed on the instance which tells me that cloud-init was run when configuring the instance. But then, there are also some areas of the cloud-init settings that are not happening, like my user account is not being setup.

I'm a bit confused as how cloud-init is started. I thought cloud-init would get started when the instance starts and I should be able to command it within the instance.

Anyone have ideas?

---

### Post by MAFoElffen on 2023-12-08
I guess it all depends on the lxd container image. With Ubuntu, usually  we assume there are a ceratain amount of things installed for a certain  image level

For Ubuntu itself, cloud-init is a default installed  program after version Lunar 23.04 if it is "Ubuntu", but not for many of  it's flavors, only because it uses it in the newer Flutter installer to  apply the user data on the first boot...

It is not a default  installed applcication univesally, even in Ubuntu. There is still the  older legacy installer, that does not use that, so it is not installed.  Many other Distro's do not use cloud-init.

You could always install it.

---

### Post by MAFoElffen on 2023-12-08
(dang. Double post)
Sounds like a command-not-found error. You could always install it.

---

### Post by MAFoElffen on 2023-12-08
Most cloud images have things taken out to make the installed image smaller in size...

This is not specifically an Ubuntu Image question. You are asking about a Gentoo container image, which i have no idea what they contain...

---

### Post by ian-weisser on 2023-12-09
> **RRLangly said:**
> I'm a bit confused as how cloud-init is started. I thought cloud-init would get started when the instance starts and I should be able to command it within the instance.

Cloud-init is designed to run just once, during the install process, as a sub-process of the installer.
And that's all.

There's not much secret sauce to it. Just a YAML parser that runs a limited set of a few simple commands. 

If elements of the YAML are not being implemented, check the YAML. Then check for reported bugs in your distro's implementation.

---

