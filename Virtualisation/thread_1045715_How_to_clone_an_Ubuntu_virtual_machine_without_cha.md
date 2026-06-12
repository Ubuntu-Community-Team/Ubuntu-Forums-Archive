---
title: "How to clone an Ubuntu virtual machine without changing 70-persistent-net.rules?"
date: 2009-01-20
forum: Virtualisation
---

### Post by grittyminder on 2009-01-20
Greetings,

Anybody who has run Ubuntu server in a virtualized environment (ESX, VMware Server, etc.)knows that a cloned Ubuntu server will be assigned a different set of network interface names, and unless you manually change the names in the appropriate config file (i.e. /etc/udev/rules.d/70-persistent-net.rules, or /etc/iftab) and reboot, the server will be unable to connect to the network. If you're in a test virtual environment making a lot of server clones, you're having to look up the location of the arcane config file, change the interface names, and reboot the server every... single... time. Also, dealing with Windows people who try to clone the Ubuntu server and complain when "it doesn't work" when they turn it on is really, really annoying.

I'm fed up. I don't want to have to change the interface names each time I (or somebody else) makes a clone. Does anybody have any ideas, or better yet, has anybody found a solution to this problem?

---

### Post by windependence on 2009-01-20
Have you tried running converter on them to clone them? I have never had this issue, I just copy them and they work fine.

-Tim

---

### Post by dmizer on 2009-01-21
> **windependence said:**
> Have you tried running converter on them to clone them? I have never had this issue, I just copy them and they work fine.

-Tim

Thanks Tim, I wasn't aware that this was available.

This does indeed appear to be the answer, and vmware-server 1.x is supported: [http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

---

### Post by grittyminder on 2009-01-21
> Have you tried running converter on them to clone them? I have 
> never had this issue, I just copy them and they work fine.

This sounds very, very promising. 

Actually, to be honest, I've tried to use VMware Converter in the past with no success. I tried again just minutes ago and got this error message: "Unable to connect to VMware Converter Agent on the local machine." I didn't look into the error message previously because it wasn't that big of a deal (I just used vmkfstools to clone the disk files). 

I looked up the error message. It seems that this error message will crop up if you've turned off the VMware Converter service on your local machine. I started the service and started a new clone of an Ubuntu virtual machine. An unusual error message appeared stating something to the affect that the virtual disks couldn't be detected (I don't 100% remember the contents of the message, sorry). Anyhow, I started the clone task, and in about 30 minutes or so we'll see how it went!

---

### Post by grittyminder on 2009-01-21
Bad news. I just checked up on the cloned Ubuntu server and it seems that the interface names changed again (i.e. I'm seeing the same problem as before). I'm using Ubuntu Server 8.04, VMware Converter 3.0.3, and ESXi 3.5.0. Tim, you've cloned your servers without any problems, right? What could the problem be...?

---

### Post by stefangr1 on 2009-01-21
I also copy them without doing anything else and never experienced any trouble. How are your vm's connected to the internet? I use host-only network interfaces combined with my own dhcp-server, maybe that has to do something with it.

---

### Post by grittyminder on 2009-01-21
> I also copy them without doing anything else and never 
> experienced any trouble. How are your vm's connected to the
> internet? I use host-only network interfaces combined with my 
> own dhcp-server, maybe that has to do something with it.

I just tried cloning again with a different Ubuntu virtual machine--no good. (This virtual machine had 1 interface; the previous one had 4). All my virtual machines are on a host only network (they do not connect to the local network). The networking for the virtual machine I just tested was set to use DHCP. The networking for the previous virtual machine I tested was static. This is really frustrating. What OS/Software versions are you guys using when you clone?

P.S. The error message I'm seeing before the clone operation is "Warning: cannot configure the source image." I think that this message is related to the virtual disks and not the networking component, but not 100% sure...

---

### Post by stefangr1 on 2009-01-21
My host runs Ubuntu 7.10 x86 (cli), the guests run Ubuntu JEOS 8.04LTS x64.

EDIT: I just tried out and (even though I'm pretty sure I didn't have this problem a few years ago), I now have the same problem as you described if I duplicate an entire machine including it's virtual disk. However, I have switched to using my server vm's as diskless clients some time ago, and then apparently this problem does not occur.

---

### Post by grittyminder on 2009-01-21
Using diskless VMs I'm afraid is not an option for me. I'm still searching for a solution to this problem.

This network interface name situation has become a bit of a touchy subject as of late. Yesterday somebody said something like, "well, Windows doesn't have this problem." Yeah, that's just what I need--more fodder for the Windows people. Please, if somebody has found a work-around or something, anything, please post.

---

### Post by koenn on 2009-01-21
I've seen this problem, although i 'clone' slightly differently ; I make a copy of the vmdx file of a model system and create a new vm using the copied vmdx as "existing disk" for the primary hard disk (in a VMware server on Debian host)

I usually work around it by editing /etc/interfaces to use the new device name, as I usually just do this copying if I quickly want to set up a test machine.

What i suspect is happening is that the copied disk (/machine) already has a udev rule for eth0, with the MAC address of the original nic. The new machine's nic has a new nic with a different MAC, so udev rule generator adds a new line with eth1 for the new MAC, and consequently the nic will come up as eth1, even though "eth0" (the original MAC) is no longer present in the system.

If my hunch is correct (haven't checked), I suppose this may be considered a bug in udev - the 'old' eth0 rule should be deleted as the nic with the old MAC is no longer present in the system.
Or it may be considered a bug in vmware, in that it should provide a way to make clones unique and clean up such things ... (maybe vmware does have the tools for this, but I don't now)


I guess it's possible to work around it by doing a find and replace in the udev rules, something like (not tested)
```

# remove obsolete eth0 line
sed -i /eth0/d /etc/udev/...rules

# replace eth1 with new eth0
sed -i s/eth1/eth0/g /etc/udev/...rules

```
or something similar in /etc/interfaces - although that's not so clean.
Assuming there are other things you'll want or need to make unique in a cloned machine (hostnames ?), you could just add this the checklist.

Windows probably doesn't have this problem because it derives the NIC "name" from the driver. you can claim that this is  a sloppiness in the design (try having 3 nics of the same make and model in 1 machine - you can't tell them apart) that just happens to have a positive side effect in this particular case. :)
Or just admit it's a bug.

---

### Post by dmizer on 2009-01-21
> **grittyminder said:**
> Using diskless VMs I'm afraid is not an option for me. I'm still searching for a solution to this problem.

This network interface name situation has become a bit of a touchy subject as of late. Yesterday somebody said something like, "well, Windows doesn't have this problem." Yeah, that's just what I need--more fodder for the Windows people. Please, if somebody has found a work-around or something, anything, please post.

Actually, if your virtual host is Windows you will still have this problem. If you copy the virtual machine you will need a new network interface. This does not matter if your host is Linux or Windows. Otherwise you have multiple computers with the same MAC address which causes routing problems.

Perhaps this is a question best directed to the vmware forums? [http://communities.vmware.com/index.jspa](http://communities.vmware.com/index.jspa)

I'm also moving this thread to the virualization subforum where more people with virtual machines can provide support to you.

---

### Post by grittyminder on 2009-01-22
koenn, thanks for the useful information. Now I see the difference in how Windows and Ubuntu derive their interface names. Anyhow, I've scoured the vmware forums for information on this subject in the past, although not very recently. The general attitude I sensed from the VMware forums was that modifying 70-persistent-net.rules (or, alternatively, /etc/interfaces) was something you just had to do when cloning a virtual machine and/or its disk files.

Thank you for the suggestions, but essentially I'm looking for a solution where you need only turn on a cloned VM and it will simply work; no logging into the command line, no editing of files, and no system reboot required. Until I find a way to do this I'm afraid that my co-workers will be irate at me!

---

### Post by koenn on 2009-01-22
What if you'd clone from a model that has a blank /etc/udev/...persistent-net... file ? My guess is that a correct new file would be created when the clone boots for the first time, with a correct udevs net rules file.
Of course, every time you run the model, it would also create its udev rules file, so you'd have to remove that before cloning it again.

---

### Post by koenn on 2009-01-22
did some research.
This has been filed as a bug with Debian, and is said to be solved
[http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg136139.html](http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg136139.html)

Maybe it's worth filing this as an Ubuntu bug against udev in launchpad, and referring to the debian bug number.

A possible fix is apparently to exclude VMWare NIC's from the udev rule generator, by adding these lines to /etc/udev/...persistent-net-generator.rules - possibly something like 
```

# ignore VMware network interfaces identified by vendor part of MAC addr
ENV{MATCHADDR}=="00:0c:29:*", GOTO="persistent_net_generator_end"

```

you'd do this in the machine you clone from, obviously, and you would also need to remove the line in persistent-net.rules where the model's mac address is already mapped to eth0

downside : virtual machines with multiple nics may have their nic device names swapped at reboot, because there won't be a rule to match names with MAC addresses

---

### Post by jimisaacs on 2010-08-06
Hello, I'm new to this forum and I am a Fedora user myself.

I came across this thread as the top result when searching for a solution to the same problem on Fedora 13 using kvm virtualization.

After being guided to the rules file the solution was pretty simple.
(until this is all automated sooner or later).

It may or may not be a bug combined with the fact that I am using a separate logical volume group for all my virtual machines, and I only recently fixed an selinux labeling issue on those volumes.

Anyway, I fixed the selinux labeling, then created a new clone once again using virt-manager.

The new logical volume storage gets created just fine, selinux was silent, but the mac address is still wrong.

So then I found these threads pointing me to that rules file and I only had to do 3 things:
Edit: /etc/sysconfig/network-scripts/ifcfg-eth0
Make it the new MAC that virt assigned to the cloned machined.

Edit: /etc/udev/rules.d/70-persistent-net.rules
Make the MAC of the eth0 interface the same as above...
and delete the eth2 interface that was created during the cloning process to compensate.

Then reboot the system.
run ifconfig and you should see the eth0 interface there with the correct MAC.

---

### Post by Warren MacEvoy on 2010-10-23
Here's a way that does "change" the 70-persistent-net.rules, but automatically, so you don't have to worry about copying the vm.  Note that if you have a complex setup (more than 1 interface) this may rewrite the order of the interfaces.  Just put this in /etc/rc.local (Ubuntu 10.04LTS, but should work in other versions 9+, maybe earlier).  It only reboots once to rewrite the persistent rules.  If eth0 is still not there after the automatic reboot, then the /var/log/rewriting-net-rules file will prevent an infinite reboot loop.

if ! ifconfig eth0 && ! -f /var/log/rewriting-net-rules; then
  echo "rebuiding persistent rules for eth0 (rebooting)"
  /bin/rm -rf /etc/udev/rules.d/70-persistent-net.rules
  touch /var/log/rewriting-net-rules
  /sbin/reboot
else
  /bin/rm /var/log/rewriting-net-rules
fi

---

### Post by a_deano on 2011-01-31
All I wanted to say was kudos to Warren, and unicies in general.

I had been struggling with this one for a while. I often use vm's to demonstrate capability or as a staging environment for a new bit of wizardry. I was stumped as to why the networking was always an issue. While it may or may not be a bug in udev the beautiful thing is that a simple script provides a workaround.

I have tested this with a VM server copied across a network using VMware player on windows (yeah I know, testing only), ubuntu lucid and maverick and virtual box lucid and maverick. All works fine, for my purposes as a q and d demo platform anyway. Although I should mention that bridging wlan0 in linux hosts is still an (unrelated I think) issue. Solutions here would be gleefully accepted.

So that 'a famous web search engine' and others might pick up this solution, here goes;

virtual machine copied cloned linux ubuntu debian guest no network eth0

Lessons I learnt;
1. dmesg and grep are your first port of call. I searched around thinking it was an issue with the vmware image I was using and that in linux I was on a wlan (wlan0). The eventual path to here started with ```
dmesg | grep eth
```. The clue was that somehow eth0 was being renamed to eth1. If I had done it ```
ifconfig -a
``` might have also led me down this path.

2. Once the issue is found (in this case udev rules) search forums. Some kind soul will have an answer.

---

### Post by fest3er on 2011-09-22
There are really two ways to solve this problem. You should be able to specify the MAC address of NICs when you start the VM. This is useful if you want to temporarily replicate an environment.

If you need to permanently change the NICs, you *must* change 70-persistent-net.rules. But there's no need to reboot after changing the file. You need to 'rmmod' the NIC driver(s) then tickle udev to handle those devices again. This script should do the trick, though some local tweaks might be needed:
```

#! /bin/sh

# Stop networking
/etc/init.d/networking stop

# Get the drivers and bounce the NICs
lspci -nnv | awk '{
  if ($0 ~ /^$/) { getDriver = 0; }
  if (getDriver == 0 && $0 ~ /.*Ethernet controller.*/) { getDriver=1; }
  if (getDriver == 1 && $0 ~ /.*Kernel driver.*/) { printf ("%s\n", $5); }
}' | sort | uniq | while read a; do
  rmmod $a
done

# Tickle udev
/sbin/udevadm trigger 

# Start networking
/etc/init.d/networking start

```

---

### Post by HermanAB on 2011-09-24
Hmm, you should also change the hostname.

---

### Post by lisati on 2011-09-24
Although not completely dead, this thread is very sleepy, and has been closed so it can have some rest.

<aside>
@fest3er:
When everything is working as it should, you shouldn't have to tinker with the MAC address. In some situations, MAC address spoofing could be (mis)interpreted as someone getting up to mischief.
</aside>

---

