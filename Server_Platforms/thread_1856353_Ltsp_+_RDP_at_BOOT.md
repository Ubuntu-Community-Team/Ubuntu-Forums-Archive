---
title: "Ltsp + RDP at BOOT"
date: 2011-10-08
forum: Server Platforms
---

### Post by SpruceNZ on 2011-10-08
Highly regarded experts, please share some of your wisdom with me.

I didn't get anywhere with my first post here: [http://ubuntuforums.org/showthread.php?t=1852345](http://ubuntuforums.org/showthread.php?t=1852345) 

So I am trying a slightly different (shorter) approach.

I can't get an LTSP thin client to boot into a VM running Windows 7 using lts.conf at boot.

I have tried every variation of:

screen_07 = rdesktop
rdp_server = "192.168.1.71"

Thin client boots, displays Ubuntu splash, then stops at a black screen (with moveable white cursor)

I have no idea what's happening. I am humbly requesting any help. Please!

P.S Does this RDP boot only worth specifically with Terminal servers? Can I just boot into my VM at all?? Running all the commands in the regular terminal fires up the Rdesktop session to the VM like a flash.

Currently running Ubuntu 10.10 with latest distro of LTSP. (Virtualization via KVM/QEMU)

---

### Post by kuala on 2011-12-14
Hello, SpruceNZ,

I have been having a similar issue. My LTSP clients can boot up normally into Gnome with/without Autologin in lts.conf, however, when I add the rdesktop entries to the lts.conf, after the Ubuntu startup screen(ubuntu logo with progress dots or Ubuntu splash login screen) I'm left with a black screen and white mouse arrow/cursor. I am able to switch between other screens using Alt+F1-12, but the screen specified in lts.conf which is the screen that loads up initially(screen07) seems to be a failed rdesktop session.

Have you made any headway? Any tips would be greatly appreciated.

Thank you.

-kuala

---

### Post by SpruceNZ on 2011-12-15
Hi Kuala,

I am pleased to say that I have indeed since fixed the issue.

My setup, required my LTSP thin clients connecting via rdesktop to Windows VMs running on the same server that was hosting the LTSP server.

This meant that the rdesktop traffic had to travel from one NIC to another, which meant that in my case, the solution was setting up NAT on the server. 

The black screen is the result of rdesktop not connecting to the host successfully, rather than falling back into something else or presenting an error, it just hangs. 

If your system is different, I suggest bringing up the thin client, bring up xterm and see what rdesktop is actually doing.

I don't know much about your system, so I can't be of more specific help at this stage!

Alex.

---

### Post by pgemme on 2012-03-21
I seem to run into this issue every time I create a new LTSP server.  I always fix it, but then forget how I did.

Couple things - the nat has to be right: [I]/etc/ltsp/nat

[/I]The other thing I forget is */etc/sysctl.conf*
I find I have to Uncomment the **net.ipv4.ip_forward=1 **line to get it working again.

Also, check your routes - only the local DHCP destination should be that interface 

e.g:[INDENT]192.168.1.0 *     255.255.255.0   U   0   0   eth1
10.10.10.0   *     255.255.252.0  U   0   0   eth0
link-local      *     255.255.0.0    U  1000 0  eth0
default         vlan-r.i1 0.0.0.0   UG  100  0  eth0

[/INDENT]Another way to test - other than staring at the mouse and no RDP session - ctrl-alt-f2.  Use that screen to try pinging gateways and dns names, etc...

---

