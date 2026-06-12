---
title: "Ubuntu Server Soft Raid ?"
date: 2008-10-12
forum: Server Platforms
---

### Post by AgentZ86 on 2008-10-12
Hi 

Is there a Soft Raid feature for mirror of 2) IDE drives in Ubuntu Server ?

---

### Post by fjgaude on 2008-10-12
> **AgentZ86 said:**
> Hi 

Is there a Soft Raid feature for mirror of 2) IDE drives in Ubuntu Server ?

Yes, as far as I can remember: raid1, two or four drives.

You can use **mdadm** to create the array.

---

### Post by thefekete on 2008-10-13
This should help you out...

[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

The only time I've ever run linux non-raided is on test machines and laptops. I used this HowTo for my first server (Fedora 5, I think) and have refered to it every time I need to mess with things.

If you are going to run the system off a raid array, you can set it up within the installer.

---

### Post by erwall on 2008-10-13
> **AgentZ86 said:**
> Hi 

Is there a Soft Raid feature for mirror of 2) IDE drives in Ubuntu Server ?
I just followed this guide while building 3 servers, worked great:

[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)

---

### Post by AgentZ86 on 2008-10-20
> **erwall said:**
> I just followed this guide while building 3 servers, worked great:

[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)

Nice, thanks

I guess it's just like installing SME server the screens look very similar, and has the prompt for raid drives as well.

Thanks to all.

---

