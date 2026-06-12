---
title: "[Ubuntu 9.10] Root seems faster than normal user"
date: 2009-12-09
forum: The Cafe
---

### Post by zyborg on 2009-12-09
I'm a Newbie to Linux environment. My root user seems somewhat faster than normal user (Speed application execution, disk access). Consider that nothing other than the drivers were installed at the time this was experienced. How is it possible? Any reasons for that?

My laptop configs are: 

AMD Athlon Neo MV-40 @ 1.6 Ghz
2GB RAM
ATI Radeon HD3410

---

### Post by SuperSonic4 on 2009-12-09
My guess is that root has less stuff going on in the background

---

### Post by snowpine on 2009-12-09
I think you are confused; there is no "root user" in Ubuntu.

Check it out: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Ubuntu is not designed for root login, therefore it's probably faster for you because many important/necessary processes aren't running.

A good analogy is "my car goes faster if I cut the brakes". :)

---

### Post by SuperSonic4 on 2009-12-09
> **snowpine said:**
> I think you are confused; there is no "root user" in Ubuntu.

Check it out: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Ubuntu is not designed for root login, therefore it's probably faster for you because many important/necessary processes aren't running.

A good analogy is "my car goes faster if I cut the brakes". :)

There is, it's just not enabled by default

[QUOTE=https://help.ubuntu.com/community/RootSudo]Enabling the root account...[/QUOTE]

I could go on but it's against forum policy

---

### Post by snowpine on 2009-12-09
> **SuperSonic4 said:**
> There is, it's just not enabled by default


I would go a step further and say rather than "not enabled by default" it is "deliberately locked for a good reason."

---

### Post by zyborg on 2009-12-09
> **snowpine said:**
> I think you are confused; there is no "root user" in Ubuntu.

Check it out: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Ubuntu is not designed for root login, therefore it's probably faster for you because many important/necessary processes aren't running.

A good analogy is "my car goes faster if I cut the brakes". :)
Sorry, I forgot to mention I had the root enabled for educational purposes.

However, I think I got the answer. Could you please suggest me some ways I could get the OS faster. :)

---

### Post by snowpine on 2009-12-09
One suggestion is to go into System->Preferences->Startup Apps and disable anything you don't need (for example, my computer doesn't have Bluetooth, and I don't need any assistive technologies).

---

