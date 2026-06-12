---
title: "XEN 3.1 Network problem (ubuntu 7.10) cannot ping gateway"
date: 2007-10-23
forum: Virtualisation
---

### Post by feeling367 on 2007-10-23
**[SIZE="5"]THE CONFIG[/SIZE]**

I use the 2.6.22-14-xen kernel on my kubuntu 7.10.

I've installed xen utils & co, and created a domain (called server.cabestan.be)

here is my server.cabestan.be.cfg:
```

kernel      = '/boot/vmlinuz-2.6.22-14-xen'
ramdisk     = '/boot/initrd.img-2.6.22-14-xen'
memory      = '128'
root        = '/dev/hda1 ro'
disk        = [ 'file:/home/xen/domains/server.cabestan.be/disk.img,hda1,w', 'file:/home/xen/domains/server.cabestan.be/swap.img,hda2,w' ]
name        = 'server.cabestan.be'
vif         = [ 'ip=192.168.1.254' ]
on_poweroff = 'destroy'
on_reboot   = 'restart'
on_crash    = 'restart'

```

and my xend-config.sxp config:
```

(xend-relocation-server yes)
(xend-relocation-hosts-allow '^localhost$ ^localhost\\.localdomain$')
(network-script network-bridge)
(vif-script vif-bridge)
(dom0-min-mem 196)
(dom0-cpus 0)
(vncpasswd '')

```

I have only one adatper
```

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

```

**[SIZE="5"]THE PROBLEM[/SIZE]**

When I Start xend in bridged mode, network goes completely down (even without domains started). The gateway become unpingable from the host, the guests are unpingable from the host (when domain started of course)...

It seems to be a big bridge problem :-/

Here are the brctl show :
```

bridge name bridge id STP enabled interfaces
xenbr0 8000.feffffffffff no vif0.0
                            peth0

```

And the xm list :
```
Name ID Mem VCPUs State Time(s)
Domain-0 0 922 2 r----- 67.4

```

route is ok, I'm blocked :-/ 

does anybody have an idea ?

thanx !
Laurent.

---

### Post by ph8 on 2008-01-15
I have the same problem and have not yet found a way around it :(

---

### Post by bxgrant on 2008-01-16
I too have this exact problem.  It's preventing me from moving forward with XEN.  I have a suspicion that it's my network card which is exactly the same as yours:

```
03:00.0  Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
```

But after spending countless hours on this issue I haven't taken the time to swap out the card and see if it works.  I will probably this weekend.  If you do and it works, let us know.

thanks,

BX

---

### Post by Jason Vaughan on 2008-01-29
Hello, I'm a newbie to the Ubuntu on XEN issue.

I am trying to install Ubuntu 7.10 on Citrix Xen Enterprise ver 4.  When it boots all i get is a loading screen.  I've attached an image.  Just sits there and never boots.

I was wondering if you were using 3.1 because of this problem and if anyone has tried installing 7.10 or 6.x on Xen 4 yet.



Thank you,


Jason Vaughan

---

### Post by hurenkam on 2008-03-09
I've been using Xen for several years now on my server, and am currently in the process of moving from a gentoo/xen3.0.2 based system to an ubuntu/xen3.1.3 based system.

My way to avoid problems as listed above, is to not use the default 'network-bridge' script, but rather I create 2 bridges myself (always, regardless wether xen is active or not), and upon xen startup, I simply have a custom script that adds vif0.0 to the dmz bridge, and vif0.1 to the loc bridge.

My virtual machines can then choose with 'bridge=dmz' or 'bridge=loc' in which network domain they want to reside.

This way, there is no 'magic' involved in joggling with the existing network devices (moving mac & ip addresses, moving routes, renaming network devices) and thus if the network was up prior to starting xend, it will still be up after starting xend.

One issue that I did encounter, is that the xen bridges do not work nicely with shorewall firewall (as of xen3.1/shorewall 3.4), I was not able to ping between machines on the same bridge anymore. Thus I now run the firewall in a seperate guest domain, and the problem is solved.

If you're interested in my /etc/network/interfaces, /etc/xen/xend.sxp and /etc/xen/scripts/network-custom I can post them for you.

Mark.

---

### Post by Closed85 on 2008-10-19
@hurenkam
i am interested in these files. could you post them here?

thanks

---

