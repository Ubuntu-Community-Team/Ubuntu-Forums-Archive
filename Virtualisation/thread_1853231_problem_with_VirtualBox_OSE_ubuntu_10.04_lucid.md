---
title: "problem with VirtualBox OSE ubuntu 10.04 lucid"
date: 2011-10-01
forum: Virtualisation
---

### Post by linux300 on 2011-10-01
hi every body 
what's this ..? 
[[IMG]http://i.iimmgg.com/images/is8th/ed09d0d030e35de8e8956920490c1397.png[/IMG]]("http://www.iimmgg.com/image/72e45c26750973b03d9a619480610942") 

:confused: :confused:
thank you

---

### Post by LinuxFan999 on 2011-10-01
Which version of Virtualbox OSE are you using?

By the way, next time you post a screenshot, please upload it directly to this site.

---

### Post by linux300 on 2011-10-01
thank you mr.LinuxFan999 ):P

i am using V 3.1.6_OSE r59338

---

### Post by 2F4U on 2011-10-02
Is this a fresh installation? If not, I would guess that a kernel update happened and you don't have dkms installed. Try the following

```

sudo /etc/init.d/vboxdrv setup
sudo modprobe vboxdrv

```

---

### Post by linux300 on 2011-10-02
> **2F4U said:**
> Is this a fresh installation? If not, I would guess that a kernel update happened and you don't have dkms installed. Try the following

```

sudo /etc/init.d/vboxdrv setup
sudo modprobe vboxdrv

```

Is this a fresh installation? no 
i am using this [http://netinfinity.org/](http://netinfinity.org/)
kernel 2.6.32-34-generic 

result  :sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found

result : sudo modprobe vboxdrv
FATAL: Module vboxdrv not found.

thank you for help me

---

### Post by linux300 on 2011-10-02
[SIZE=3]how i can update VirtualBox to V 4[/SIZE][B] ):P
[/B]

---

