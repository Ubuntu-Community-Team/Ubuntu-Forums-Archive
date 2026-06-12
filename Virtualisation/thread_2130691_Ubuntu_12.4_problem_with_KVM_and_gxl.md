---
title: "Ubuntu 12.4 problem with KVM and gxl"
date: 2013-03-30
forum: Virtualisation
---

### Post by Jackout on 2013-03-30
Hi,

I when I am trying to run my vm Windows 7 under buntu 12.4 with qxl as graphic card I can see only black screen.

With vga it works just fine.

I found info about bug [here]("http://osdir.com/ml/ubuntu-bugs/2012-05/msg26747.html") - but I am not sure what to do to make it work.

Could I ask for some help ?

Thanx.

---

### Post by Jackout on 2013-03-31
Hi All,

finally I found solution that works for me, I am pasting it here in case if someone wold have the same issue:

[source]("https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/975165/comments/7")
```

[COLOR=#333333][FONT=Ubuntu Mono]sudo apt-get install qemu-kvm-spice[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]cd /usr/bin/[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]sudo rm kvm[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]sudo ln -s qemu-system-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]x86_64-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]spice kvm
[/FONT][/COLOR]
```

BR.

---

