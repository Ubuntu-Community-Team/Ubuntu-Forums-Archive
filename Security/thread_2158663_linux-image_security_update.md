---
title: "linux-image security update"
date: 2013-06-30
forum: Security
---

### Post by register88 on 2013-06-30
I want install ubuntu's linux-image on my debian system, because debian's linux-image does not support apparmor's network rule.

my question is, how to I know ubuntu's linux-image has security update?
since I  download ubuntu's linux-image from website manually (not apt),
so I want to know, when linux-image update is ready, but don't want manually check the website everyday.

anyone use ubuntu's kernel on non *buntu system like this?

thanks.

---

### Post by Bucky Ball on 2013-06-30
If you add the ppa it should update as normal with everything else. You could then set the machine to check for updates everyday or just update the kernel ppa everyday.

---

### Post by register88 on 2013-06-30
> **Bucky Ball said:**
> If you add the ppa it should update as normal with everything else. You could then set the machine to check for updates everyday or just update the kernel ppa everyday.

I'm not to use ppa, I download from "http://packages.ubuntu.com/raring/linux-image" those mirror.
thank you.

Or can I download official ubuntu linux-image from PPA?

---

### Post by deadflowr on 2013-06-30
Can you even run ppas on debian?

---

### Post by Bucky Ball on 2013-06-30
> **deadflowr said:**
> Can you even run ppas on debian?

If you have a ppa installed you pretty much are already as Ubuntu shares quite a bit of DNA with Debian. Check here:

[https://duckduckgo.com/?q=debian+ppa](https://duckduckgo.com/?q=debian+ppa)

@ register88: Which kernel were you looking for?

@deadflowr: Looks like you might be right. PPAs look like they were being developed for Deb then stalled. Odd as the Ub and Deb are so similar in so many other ways ...

---

### Post by register88 on 2013-06-30
> **Bucky Ball said:**
> 
@ register88: Which kernel were you looking for?

this one: linux-image-generic (ubuntu default kernel)
[http://packages.ubuntu.com/raring/linux-image](http://packages.ubuntu.com/raring/linux-image)
thank you

---

### Post by Bucky Ball on 2013-06-30
Interesting:

[http://www.exton.net/?p=153](http://www.exton.net/?p=153)

Also:

[http://linuxg.net/install-linux-kernel-3-8-6-on-ubuntu-debian-and-linux-mint-operating-systems/](http://linuxg.net/install-linux-kernel-3-8-6-on-ubuntu-debian-and-linux-mint-operating-systems/)

These instructions might work for Debian too:

[http://www.ubuntukiller.com/2013/01/how-to-install-linux-kernel-380-rc2-in.html](http://www.ubuntukiller.com/2013/01/how-to-install-linux-kernel-380-rc2-in.html)

---

