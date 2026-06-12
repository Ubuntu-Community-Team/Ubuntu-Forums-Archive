---
title: "Is the server kernel included with hardy tickless?"
date: 2008-09-25
forum: Server Platforms
---

### Post by bmc3 on 2008-09-25
Hello!

I'll shortly update a 6.06/dapper system to hardy and i'm trying to figure out if I have to compile my own kernel. The only reason for doing so is that VMware Server can handle tickless systems far better than systems with timer interrupts. (According to the VMware Time Keeping Guide)

I got the linux-image-2.6.24-19-server_2.6.24-19.41_i386.deb file and extracted the contents. When I look for the kernel options I see this:
```
$ cat config-2.6.24-19-server | grep HZ
# CONFIG_HZ_1000 is not set
# CONFIG_HZ_300 is not set
CONFIG_HZ=100
CONFIG_HZ_100=y
# CONFIG_HZ_250 is not set
CONFIG_MACHZ_WDT=m
CONFIG_NO_HZ=y
```

Tickless timing seems to be enabled (CONFIG_NO_HZ=y), but there are also configuration options set for timer interrupts (CONFIG_HZ*).
Is the latter only relevant if tickless timers are disabled at the boot prompt? How can I check if a running system is running tickless? (/proc, /sys?)

I appreciate your time for reading this and if you reply your effort for doing so.

Bye!

---

### Post by windependence on 2008-09-25
You're already set to 100Hz on your clock so you should be fine.

Also, be aware, ESXi is a much better product and it is now free. It runs on bare metal, so no host OS is necessary, hence no time problems. This was just recently a $599 product.

Here are some useful links:

[https://www.vmware.com/tryvmware/login.php?eval=esxi&t=1](https://www.vmware.com/tryvmware/login.php?eval=esxi&t=1)

[http://www.vmware.com/download/esxi/](http://www.vmware.com/download/esxi/)

Let me know if you need any help. ;)

-Tim

---

### Post by bmc3 on 2008-09-25
Thank you for your reply. It seems as if I've been unclear. I'll try to explain again. ;-)

VMware has trouble to supply all the tick interrupts to all running VMs. Especially under high CPU loads. The VMware Time Keeping Guide states that tickless kernels can handle situations where they don't get all ticks better than kernels which need the timer interrupts.
Currently im using 6.06/dapper and the included kernels definately keep track of time with interrupts. - And my clocks drift bad as hell.

I _hope_ that this will improve with tickless kernels. I want a tickless kernel, but I can't find out if the CONFIG_NO_HZ=y option really makes the kernel tickless or not.

I looked at ESXi but since I'm using unsupported hardware that is not an option. Additionally it doesn't look like the management client is for free, too.
As far as I understand one needs Virtual Infrastructure 3 - which need Windows to run on. I don't want to introduce any Windows Software into my systems. ;-)

Ubuntu ftw!

---

### Post by Robstarusa on 2008-09-25
> **bmc3 said:**
> Thank you for your reply. It seems as if I've been unclear. I'll try to explain again. ;-)

VMware has trouble to supply all the tick interrupts to all running VMs. Especially under high CPU loads. The VMware Time Keeping Guide states that tickless kernels can handle situations where they don't get all ticks better than kernels which need the timer interrupts.
Currently im using 6.06/dapper and the included kernels definately keep track of time with interrupts. - And my clocks drift bad as hell.

I _hope_ that this will improve with tickless kernels. I want a tickless kernel, but I can't find out if the CONFIG_NO_HZ=y option really makes the kernel tickless or not.

I looked at ESXi but since I'm using unsupported hardware that is not an option. Additionally it doesn't look like the management client is for free, too.
As far as I understand one needs Virtual Infrastructure 3 - which need Windows to run on. I don't want to introduce any Windows Software into my systems. ;-)

Ubuntu ftw!

Actually, forcing you to buy windows to manage a "free" product makes the product no longer free.  People can't really say esxi is free......I have tried it and when I realized there was no way to manage it via linux, I gave up on it.

---

### Post by windependence on 2008-09-25
> **Robstarusa said:**
> Actually, forcing you to buy windows to manage a "free" product makes the product no longer free.  People can't really say esxi is free......I have tried it and when I realized there was no way to manage it via linux, I gave up on it.

Actually, there IS a CLI interface for ESXi.

Also, the VIC (Virtual Infrastructure Client) does only run on Windoze, however, it will soon be supported on Linux as well as the iPhone and Mac as stated at the VMware convention in Las Vegas this month. The VIC is free.

In addition, you can use the web interface for some things.

Personally, most people have Windows anyway, and I think that is splitting hairs for something that is a really very useful and feature rich product. There are also some open source management consoles out there.

-Tim

---

### Post by bmc3 on 2008-09-26
> **windependence said:**
> Actually, there IS a CLI interface for ESXi.

Also, the VIC (Virtual Infrastructure Client) does only run on Windoze, however, it will soon be supported on Linux as well as the iPhone and Mac as stated at the VMware convention in Las Vegas this month. The VIC is free.

In addition, you can use the web interface for some things.

Personally, most people have Windows anyway, and I think that is splitting hairs for something that is a really very useful and feature rich product. There are also some open source management consoles out there.

Can you get the Virtual Infrastructure Client off of the Web-Interface of the ESXi? (Like VMware Console and VMware Server)
I'll take a look again if there are ways to manage it in a comfortabe way from Linux/Mac ... and when I get compatible hardware. This could take a while! ;-)

---

### Post by Robstarusa on 2008-09-26
> **windependence said:**
> Actually, there IS a CLI interface for ESXi.

Also, the VIC (Virtual Infrastructure Client) does only run on Windoze, however, it will soon be supported on Linux as well as the iPhone and Mac as stated at the VMware convention in Las Vegas this month. The VIC is free.

In addition, you can use the web interface for some things.

Personally, most people have Windows anyway, and I think that is splitting hairs for something that is a really very useful and feature rich product. There are also some open source management consoles out there.

-Tim

windependence>  I am not most people unfortunately.  The only windows box I have in my house is my wifes, and it is exclusively hers.  IMHO it should be other way around.  They should start off with a linux client (since anyone can download a linux distro for free) and make the windows client afterwards...but what do I know ;)

If I actually upgrade my servers so that they have virtualization extensions (I have some dual 940, and a single 939 box at home), I will probably go Xen instead of esxi, but if they come out with a linux native client for esxi before I upgrade, I'll try that.

Also:  If you have pointers to 3rd party management consoles that work well for esxi, post please and I will try them out.  I appreciate the help.

---

### Post by windependence on 2008-09-26
I am the same as you are. The only Windows box I have is the wife's. :)

I do have a vm on my Mac thru VMware Fusion (better than parallels) and sometimes I do use that, but mostly I use my FreeBSD machines to manage everything.

I am actively looking for tools to get me away from Windoze myself and still be able to use VMware. You can probably tell from my screen name I am on your side. ;) When I find something useful, I'll post it here for all. In ESXi, you can use the RCLI to manage the host from the command line.

Supposedly, they will have a VIC for Mac and Linux by the end of this year. That's not that far off, fortunately.

-Tim

---

