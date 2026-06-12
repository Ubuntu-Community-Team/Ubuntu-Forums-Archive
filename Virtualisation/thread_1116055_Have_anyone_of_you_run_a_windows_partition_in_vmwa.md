---
title: "Have anyone of you run a windows partition in vmware?"
date: 2009-04-04
forum: Virtualisation
---

### Post by ubantuwannabe on 2009-04-04
with reference to [http://imrannazar.com/Running-a-Windows-Partition-in-VMware](http://imrannazar.com/Running-a-Windows-Partition-in-VMware)

the main purpose of this configuration is to run vmware with windows xp as the guess operating system running on windows partition not on the ubuntu partition, right?

the initial WindowsXP.vmdk in stage 1 is just a rough guide right since actual values has to be determined when running "parted /dev/hda"

regarding "copying the bootsector"

how do I determine the value of bs?

regarding stage 2 VMware information file

"the information file: windowsXP.vmx

how do i determine the value of memsize?

Under Stage 3 Setting up Windows

[http://ftp.snt.utwente.nl/pub/os/linux/gentoo/distfiles/VMware-workstation-5.5.3-34685.tar.gz](http://ftp.snt.utwente.nl/pub/os/linux/gentoo/distfiles/VMware-workstation-5.5.3-34685.tar.gz)

this link does not work.

can anyone tell me an alternative link?

under stage 4

under snags: getting the network running, how do i get the address of the wireless network? i run /sbin./ifconfig

Link encap:Ethernet  HWaddr 00:1f:3c:a2:ba:9e  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0

so in the above case what's my network address?

the equivalent of  /etc/conf.d/local.start is /etc/rc.local, right?

I'm using DHCP. Is there any issues?

thanks a lot!

---

### Post by Mark20 on 2009-04-05
> the main purpose of this configuration is to run vmware with windows xp as the guess operating system running on windows partition not on the ubuntu partition, right?
Yep, that's the plan.

> how do I determine the value of bs?
It is right beside "Sector size" further up in the tutorial.  In the vast majority of cases you just use 512.

> can anyone tell me an alternative link?
[Here]("www.justfuckinggoogleit.com/"), or [here]("http://www.vmware.com/download/ws/")

> Link encap:Ethernet HWaddr 00:1f:3c:a2:ba:9e
inet addr:192.168.1.101 Bcast:192.168.1.255 Mask:255.255.255.0

so in the above case what's my network address?
Your local address would be 192.168.1.101.  But just out of curiosity have you actually finished attempting to set up the virtual machine?  Because I never had network issues, you might end up not needing to do any extra configuration...

HTH

Mark

---

### Post by ubantuwannabe on 2009-04-06
I'm now using a single boot ubuntu system.

I have in fact finished installing vmware way even before I posted this article.

I'm looking at ways to reduced redundancy.

if I'm in windows xp, the file I save cannot be read from ubuntu unless according to [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

I used the third last partitioning scheme.

which is as follow

ntfs, ext3 ubuntu home, swap

I mean it does not really make sense to me to have duplicate copies just becoz I have different operating system.

I'm also not sure whether this link [http://imrannazar.com/Running-a-Windows-Partition-in-VMware](http://imrannazar.com/Running-a-Windows-Partition-in-VMware) applies to my case.

In all cases, I a noob and trying to try out all scenarios.

---

