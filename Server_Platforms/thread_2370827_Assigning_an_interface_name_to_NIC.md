---
title: "Assigning an interface name to NIC"
date: 2017-09-07
forum: Server Platforms
---

### Post by p2bc on 2017-09-07
Let me start by saying I am perplexed, IT WAS ALL WORKING, now not so much.

So yeah it was working, change the "/etc/network/interfaces" to make the en0s3p a static IP address, rebooted to ensure the settings would take on system reboot because this is suppose to be a headless machine, all good.

Had to re-install the linux-image, because there was missing config files to enable UFW. Used "apt -reinstall install linux.x.x....", it worked fine, enable UFW and was good to go or I thought. 

Rebooted and nothing, no network connectivity.

Check "dmesg", nothing

Did "ifconfig", just come back with "lo"

Did "lspci | grep -i ent", comes back with my ethernet card:" 04:00.0 Ethernet Controller: Realtec Semiconducttor Co., Ltd ..."

Do a "service networking status", comes back with errors to raise en0s3p.

I go edit "etc/network/interfaces" and comment out the static and auto for the en0s3p

Do a "service networking status" again, comes back with no errors with it "active"

Reboot and do a ifconfig , and still only have the "lo"

Do a "cat /proc/net/dev" and still only comes back with "lo"

Do a "service networking status" again, comes back with no errors with it "active"

So there are no more errors, awesome, so I start trying to rebuild. Look around and everywhere say to use "ip link" to give a name to a NIC. I go to the manpage for ip and read up, I find "ip link show" that only brings up "lo" not all the possible NIC according to what I read. I try "ethtool" with "ethtool -h", which does not help because I don't pass the parameter of the interface name, which I am trying to create.

So I am at a lost, some help would be appreciated.

So to summarize, "lspci" does detect the NIC, but no other means has work to associate the nic to a interface name in order to configure it. 
Also I tried modifying grud "/etc/default/grub" changing line to "GRUB_CMDLINE_LINUX="net.ifnames=0 biosdevname=0" and updating grub and rebooting, with no success.

Thanks again.

---

### Post by darkod on 2017-09-08
I assume you tried disabling ufw too, or even removing the package? It doesn't help much anyway, it's just a front for iptables, and not a very good one. Best to use iptables directly instead of ufw.

Does lshw list the nic and the assigned name? Usually it should.

And you never tried to actually change the name, right? Because some people seem to be doing that, trying to use the old fashioned eth0.

---

### Post by p2bc on 2017-09-08
> **darkod said:**
> you never tried to actually change the name, right? Because some people seem to be doing that, trying to use the old fashioned eth0.
I tried, that was what the grub edit was for, to force a "new" naming,  as a last ditch effort, but it did not work so I removed the code.

As for "lshw" command, was not aware of it.
```

sudo lshw -numeric
...
*-network UNCLAIMED
      description: Ethernet controller
      product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10EC:8168]
      vendor: Realtek Semiconductor Co., Ltd [10EC]
      physical id: 0
      bus info: pci@0000:04:00.0
      version: 03
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi pciexpress msix vpd bus_master cap_list
      configuration: latency=0
      resources: ioport:ce00(size=256) memory:efef000-efefffff memory:efef8000-efefbfff memory:efc00000-efc1ffff
...

```

> **darkod said:**
> 
I assume you tried disabling ufw too, or even removing the package? It  doesn't help much anyway, it's just a front for iptables, and not a very  good one. Best to use iptables directly instead of ufw.

I do know that UFW is a simple wrapper for ipTables, and yes I disable it with no success.

---

### Post by SeijiSensei on 2017-09-08
Does the interface en0s3p appear if you run "ifconfig"?

If so, try configuring the interface manually with

```
sudo ifconfig en0s3p 10.10.10.10
```

replacing 10.10.10.10 with the correct IP address.  Does this work?

---

### Post by darkod on 2017-09-08
I don't see any interface name in that output of lshw but I'm not sure if that is normal for that format of the command. Try this:
```
sudo lshw -short | grep network
```

Does it list the Ethernet NIC and any interface name?

---

### Post by p2bc on 2017-09-08
@SeijiSensei

I don't see how that would work, since when en0s3p was configured in "/etc/network/interfaces" , the "service networking status" returned an error failing to raise the en0s3p.

Anyways, tried it, and got:
```

en0s3p: ERROR while getting interface flags: No such device

```



@darkod

```

sudo lshw -short | grep network

/0/100/1c.5/0               network         RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 

```

---

### Post by p2bc on 2017-09-08
> **darkod said:**
> 
Does it list the Ethernet NIC and any interface name?


That is what I am trying to re-establish because there is no interface name. Most places say to use "ip link *******" as the command, but I don't see how.
But for all account the NIC is present, but has no assign interface name.

---

### Post by darkod on 2017-09-08
You are right. No name seems to be assigned to the device. It should be in front of the network column. And you didn't try changing the interface name before all this started right? (not counting the grub command line addition).

I have never seen it so far... Time to google a lot I guess. And those interface names are rather new, since 16.04 so there might not be much help online...

I wonder if the Networking subforum is a better place for this thread to be moved now, knowing what is probably the issue.

---

### Post by darkod on 2017-09-08
I wonder if some of this can help you... Just be careful which commands you run and write them down, don't just run anything you find online... :)
[https://askubuntu.com/questions/767786/changing-network-interfaces-name-ubuntu-16-04](https://askubuntu.com/questions/767786/changing-network-interfaces-name-ubuntu-16-04)
[https://askubuntu.com/questions/689070/network-interface-name-changes-after-update-to-15-10-udev-changes](https://askubuntu.com/questions/689070/network-interface-name-changes-after-update-to-15-10-udev-changes)
[http://www.itzgeek.com/how-tos/mini-howtos/change-default-network-name-ens33-to-old-eth0-on-ubuntu-16-04.html](http://www.itzgeek.com/how-tos/mini-howtos/change-default-network-name-ens33-to-old-eth0-on-ubuntu-16-04.html)

From that second link, does this list a device name at all (except lo)?
```
ls /sys/class/net/
```

---

### Post by p2bc on 2017-09-08
I am all for moving it, if it will help.

And no, I never "changed" the name interface, because truthfully if I knew how I would problem not be asking on how to now. :)

---

### Post by p2bc on 2017-09-08
> **darkod said:**
> 
From that second link, does this list a device name at all (except lo)?


Nope, just "lo"


I will check out the links, thx.

---

### Post by p2bc on 2017-09-08
The links provided use the technique of modifying the grub, to force a change on boot, which I tried.

---

### Post by darkod on 2017-09-08
Can you post the output of the following:
```
ifconfig -a
cat /etc/network/interfaces
```

---

### Post by p2bc on 2017-09-08
```

ifconfig -a

lo      Link encap: Local loopback
        inet addr:127.0.0.1 Mask:255.0.0.0
        inet6 addr:  ::1/128 Scope:Host
        UP LOOPBACK RUNNING MTU:65536 Metric:
        RX packets:14944 errors:0 dropped:0 overruns:0 frame:0
        TX packets:14944 errors:0 dropped:0 overruns:0 carrier:0
        collision:0 txqueuelen:1
        RX bytes:1108720 (1.1 MB) TX bytes:1108720 (1.1 MB)


```

```

cat /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5)

source /etc/network/interfaces.d/*

$ The loopback net interface
auto lo
iface lo inet loopback

# The primary network interface
# auto enp4s0
# iface enp4s0 inet static

# address 10.0.1.10
# network 10.0.1.0
# netmask 255.255.255.0
# gateway 10.0.1.1
# broadcast 10.0.1.255

# dns-nameserver 10.0.1.1 8.8.8.8 8.8.4.4

```

Now all that last part is comment out because of the errors from "sudo service networking status". If I uncomment "auto enp4s0 iface enp4s0 inet dhcp" is get this error:
```

sudo service networking status

networking.service - Raise network interface staus
   Loaded: loaded (/lib/systemd/system/networking.service; enable; vendor preset: enabled)
   Drop-In: /run/systemd/generator/networking.service.d
                 --50-insserv.conf-$network.conf
    Active: [COLOR=#ff0000]failed[/COLOR] (Result: exit-code) since Fri 2017-09-08 11:56:00 EDT; 8min ago
       Doc: man:interfaces(5)
 Process: 804 ExecStart=/sbin/ifup -a --read-enviroment [COLOR=#ff0000](code=exited, status=1 /FAILURE)[/COLOR]
 Process: 687 ExecStartPre=/bin/sh -c [ "CONFIGURE_INTERFACES" != "no" ] && [ -n "$(ifquery --read-enviroment --list -- exclude=lo)"] && udevadm settle (code=exited, status=0/success)
Main PID: 804 (code=exited, status=1/FAILURE)

Sep 08 11:55:59 BACKUP-Server dhclient[847]: [COLOR=#ff0000]bugs on either our web page at www.isc.org or in the README file[/COLOR]
Sep 08 11:55:59 BACKUP-Server dhclient[847]: [COLOR=#ff0000]before submitting a bug. These pages explain the proper[/COLOR]
Sep 08 11:55:59 BACKUP-Server dhclient[847]:[COLOR=#ff0000] process and the information we find helpful for debugging..[/COLOR]
Sep 08 11:55:59 BACKUP-Server dhclient[847]:
Sep 08 11:55:59 BACKUP-Server dhclient[847]: [COLOR=#ff0000]exiting.[/COLOR]
Sep 08 11:55:59 BACKUP-Server ifup[804]: Failed to bring up enp4s0.
Sep 08 11:55:59 BACKUP-Server systemd[1]: Networking.service: Main process exited, code=exited, status=1/FAILURE
Sep 08 11:55:59 BACKUP-Server systemd[1]: [COLOR=#ff0000]Failed to start Raise network interfaces.[/COLOR]
Sep 08 11:55:59 BACKUP-Server systemd[1]: networking.service: Unit entered failed state.
Sep 08 11:55:59 BACKUP-Server systemd[1]: networking.service: Failed with result 'exit-code'.

```


This part is new, never seen this part before:
```

Sep 08 11:55:59 BACKUP-Server dhclient[847]: [COLOR=#ff0000]bugs on either our web page at www.isc.org or in the README file[/COLOR]
Sep 08 11:55:59 BACKUP-Server dhclient[847]: [COLOR=#ff0000]before submitting a bug. These pages explain the proper[/COLOR]
Sep 08 11:55:59 BACKUP-Server dhclient[847]:[COLOR=#ff0000] process and the information we find helpful for debugging..[/COLOR]
Sep 08 11:55:59 BACKUP-Server dhclient[847]:
Sep 08 11:55:59 BACKUP-Server dhclient[847]: [COLOR=#ff0000]exiting.
[/COLOR]
```[COLOR=#ff0000]
[/COLOR]

---

### Post by darkod on 2017-09-08
It might be a case where the driver/module that is used for the nic is not actually the correct one. Try checking again the card with lspci and the realtek modules:
```
lspci
lsmod | grep rt
```

---

### Post by p2bc on 2017-09-08
```

lsmod | grep rt

parport_pc                32768  0
parport                     49152  2 ppdev,parport_pc
scsi_transport_iscsi  98304  4 iscsi_tcp,ib_iser,libiscsi

```

---

### Post by darkod on 2017-09-08
Strange. There don't seem to be any realtek modules loaded. They usually start with rt. The lspci does list the card and the model, right? You didn't post it's output to see exactly.

---

### Post by darkod on 2017-09-08
From your post #3 you seem to have the same ethernet NIC as here:
[https://askubuntu.com/questions/819376/ethernet-connection-issues-on-ubuntu-16-04](https://askubuntu.com/questions/819376/ethernet-connection-issues-on-ubuntu-16-04)

Maybe installing that r8168-dkms package will help you? It will be a bit of a challenge to install it without working internet connection, I know... That is why I asked earlier to confirm which chipset model you have exactly and which module/driver if any is getting loaded...

Another problem might be if it doesn't even reach the stage to detect the NIC and load a module for it. You might need to dig into the dmesg log or syslog and check that you see the NIC as detected during boot... That is also something you need to be 100% sure of, that it is being detected at all.

---

### Post by p2bc on 2017-09-08
I can always chroot into the system from a LiveCD, and update the system that way. I wish I could say I did not have experience with that solution, but I would be lying.

Will give it a try tonight, thanks for the help.

---

### Post by darkod on 2017-09-09
If you notice in that last link, the driver module starts with r, not rt. So I was wrong in my lsmod command above. You can run it again to check which module is loaded, if any, something like:
```
lsmod | grep r816
```

That can detect both r8168 or r8169 and list them.

---

### Post by p2bc on 2017-09-20
[SIZE=2][I]OMG where to begin. I apologise if the sequence of events seem confusing, they may be slightly out of order since honestly I did so many things that I might not recall them in perfect order.
[/I][/SIZE]Ok, not sure where I got this page ([http://forums.debian.net/viewtopic.php?t=104167](http://forums.debian.net/viewtopic.php?t=104167)), not sure if was linked here, I concluded that it was exactly as you suggested (darkod) that is was the lack of module (r8169) for the network card.

So I figured, boot into a LiveCD and chroot into the root system and do the update, since the LiveCD detects the network card should have no problems. HA!
- So I mount the root system, chroot into it, and to make sure I "lsmod | grep r8", and no "r8169" is present. 
- "ping google.com" , no connection!   ??? , Go to the host the system (LiveCD) and open Firefox and surf the web. Of course I forgot to "bind" the two systems.
```
[SIZE=2]
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /run /mnt/run
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
[/SIZE]
```[SIZE=2]
[I][SIZE=1]Now for those that see the problem, and are starting to laugh whole heartedly at my big huge mistake, don't ruin it for the others.
[/SIZE][/I][/SIZE][SIZE=2]- Log back into the root system from the LiveCD with "chroot", test again[/SIZE] so  I "lsmod | grep r8", and no "r8169" is present, and "ping google.com" and get back a dozen or so callbacks, awesome.
- Do a " sudo apt update" and "sudo apt install r8168-dkms". Everything completes. Feeling super good.
- Run  "lsmod | grep r8", and IT IS THERE. Fantastic!!!
[I][SIZE=1]Shhh, I can hear you laughing, patients, soon[/SIZE]
[/I][SIZE=2]- Feeling pretty satisfied with myself, I confidently reboot after "umount" all the mount points.  [SIZE=1]*Its coming*[/SIZE]
- Evering thing boots, login, do a "ifconfig" nadda, just the "lo" entry. WTF!!!
- Ah!, I forgot I commented out the IP info in "interface", Check '/etc/network/interfaces', NO! it is set to "DHCP" should have assign the network interface name.
- Check dmesg "dmesg | grep network", nohing. ???
- Check the module "lsmod | grep r8", nadda, WTF!!!!!!
- Few hundred curse words later I boot back into the LiveCD and do and the mounting and binding from earlier, chroot into root system, and do "lsmod | grep r8", and it is there.  !!!!WTF!!!!
- Do some Googling. Now for those that don't know, or don't see my HUGE MISTAKE and are not in on the joke, modules are short in the "proc" folder, so with all this work and frustration I simply managed to install the module to the LiveCD since the the root "proc" folder was bound to the LiveCD "proc" folder so that they could share resources like internet connectivity. And yes without the binding the two folders I could not do the installation because there was no connectivity.

So with all the frustration, and all the time, weeks at this point, wasted on this I decide to re-install. And yes it did not go smoothly.

I wanted this server to be a backup server for multiple laptops and other computers, I want a dedicated network card to do that service, and one so I could do maintenance and in case of hiccups. So I did what I was planning on doing after fixing this original problem and install another NIC. So this time I install it first and start the installation process. It recognises the the two cards. Turns out they are both a Realtek 8618 and r8619. I select the on-board NIC for the configuration, do everthing, and reboot.
- Run "ifconfig", just "lo". WTF sensing a pattern here.
- Run "service networking status", a whole punch of errors
- Skipping ahead a few step, do [SIZE=2] "dmesg | grep network" , "Fail to re-name eth0 to enp4s0, and eth1 to enp5s4"
- Check "/etc/network/interfaces" and there is no entries other than "lo", ok so I manually do entries for [SIZE=2][SIZE=2]enp4s0, and enp5s4, reboot.
- Run "ifconfig" and they are there. Ping "google.com" and works.
- Tried with the other NIC and nothing, can't connect. 
I am going to stop here. There is still some problems even after re-installing. The second NIC won't initialise, even though it is recognised by the system, and the module is install. At least for now there is one NIC working.

--== So why write all this ==--
To share, and so others can learn from my troubles. If your network card stops working after an update, check the make of the card with "lspci" and make sure the module is installed "lsmod".
As for the rest of my ramblings, it just there to show that even though Linux can be FRUSTRATING at times, it is pretty awesome too if you can roll with it, even if it make you do all that cursing.
As for chrooting into a system to "fix" a problem, that is a valid options as long as what you need to fix does not rest in a folder that you need to manipulate to initiate the fix.


I will address the other problem at a later time. Which is really just the other NIC not initialising.
[/SIZE][/SIZE]
[/SIZE] [/SIZE]

---

