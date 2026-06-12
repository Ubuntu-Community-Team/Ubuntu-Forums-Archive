---
title: "Performance problem"
date: 2009-02-13
forum: Virtualisation
---

### Post by trantor on 2009-02-13
Hi,
I am the owner of an Acer ALTOS G540 server with 4GB RAM and a single Xeon 5205 1.83 DC processor.
Main OS is Ubuntu 8.04 Desktop, with VmWare Server running two virtual machine, Zimbra + Ebox.
The server runs software RAID1 on a couple of 500GB Sata disks.
With this configuration Zimbra is running slow; it happens not always but often.
I was considering how to speed up the server...seems that I have two chances:

1) Build up a second processor

2) Buy an hardware RAID card

Someone suggested me that I need to install Kernel Server as well, (all 4GB RAM support and major performance).
But gives Kernel Server more performance? Will I encounter problems with my VMware server after this Kernel Upgrade?

Here is my **top** result:

top - 10:41:31 up 58 days, 14:30,  2 users,  load average: 0.79, 0.65, 0.48
Tasks: 132 total,   1 running, 131 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.7%us, 47.4%sy,  0.0%ni, 50.6%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3368872k total,  3243000k used,   125872k free,    66124k buffers
Swap:  7815544k total,    38584k used,  7776960k free,  2798388k cached

and here is my **free** result:

stefano@ubuntu:~$ free
             [LEFT]total             used       free        shared    buffers     cached
Mem:       3368872    3246012     122860          0      44412    2855028
-/+ buffers/cache:     346572    3022300
Swap:      7815544      38744    7776800[/LEFT]

Hope that someone could help me in my decision...

Thanks in advance

Stefano

---

### Post by binbash on 2009-02-13
You may need to reinstall vmware kernel module,there is a good tutorial at tutorial section for upgrading the kernel to use more than 3.5gb ram.You should change the kernel inmy opinion.I don't think it will give you more performance unless you recompile your own kernel(except the ram difference)

---

### Post by HermanAB on 2009-02-13
Your machine should be plenty fast enough, so something is wrong - you got to fix the problem.

Zimbra: Are you not just receiving oodles and oodles of spam?  Look at the queues and add better RBLs to cut down on the incoming crud, eg zen.spamhaus.org and spamcop,net.  Spam can bring a mail server to its knees.


Cheers,

Herman

---

