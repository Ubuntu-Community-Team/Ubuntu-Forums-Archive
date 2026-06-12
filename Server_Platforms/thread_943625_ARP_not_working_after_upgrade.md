---
title: "ARP not working after upgrade"
date: 2008-10-10
forum: Server Platforms
---

### Post by Astro6312 on 2008-10-10
I have ubuntu 6.06 LTS server.  After a standard update, the ARP request do no get answered by the server, thus I cannot connect or ping from the network.

EX: Server : 10.1.1.35
My PC is : 10.1.1.220

If I ping the server from my PC, no response.  I go on the server, ping my PC, it works.  Go back to my PC, I can ping the server and connect, until the ARP table is cleared, which is happening after around 10 minutes.

The kernel version is : 2.6.15-52-server

Everything was ok before the upgrade.  I simply did a simple apt-get update... apt-get upgrade.

Any ideas?

Thanks,

---

### Post by Astro6312 on 2008-10-14
My investigation is showing a difference in /proc/net/arp_tables_names.  On my server that do not respond to ARP, I see filter. On other servers, I do not have that file in /proc/net.

---

### Post by Astro6312 on 2008-10-14
If I arping this server from another server, no response.

I have booted the server from a ubuntu live cd 8.0.4 and can arping from another server.  So the hardware is fine, the software is somehow faulty.

Any ideas what to do next... Anyone?

---

### Post by iponeverything on 2008-10-14
This is pretty cool problem. 

Do you have an earlier kernel to boot to?

If you don't you might find one to install in /var/cache/apt/archives

---

### Post by Astro6312 on 2008-10-14
I did not try to boot from another kernel, but I did boot from a live CD.  
Ubuntu 8.1 did not detect any network card...
Ubuntu 8.04 did work on both network card on that server

I rebooted the server with the "not working" ubuntu 6 and switch to eth1 and everything is fine now.

Somehow, eth0 is faulty on the software side.

I was able to simulate the problem on a ubuntu 8.4 desktop with this command
sysctl -w net.ipv4.conf.all.arp_ignore=8 (to disable it)
sysctl -w net.ipv4.conf.all.arp_ignore=0 (to enable it)
See [this for more ]("http://fasterdata.es.net/TCP-tuning//ip-sysctl-2.6.txt").

---

### Post by iponeverything on 2008-10-14
> **Astro6312 said:**
> I did not try to boot from another kernel, but I did boot from a live CD.  
Ubuntu 8.1 did not detect any network card...
Ubuntu 8.04 did work on both network card on that server

I rebooted the server with the "not working" ubuntu 6 and switch to eth1 and everything is fine now.

Somehow, eth0 is faulty on the software side.

I was able to simulate the problem on a ubuntu 8.4 desktop with this command
sysctl -w net.ipv4.conf.all.arp_ignore=8 (to disable it)
sysctl -w net.ipv4.conf.all.arp_ignore=0 (to enable it)
See [this for more ]("http://fasterdata.es.net/TCP-tuning//ip-sysctl-2.6.txt").

Arp is handled by the kernel. Well more specifically, the kernel module for network device that your using or one of its dependent modules, if it is compiled as module. 

```
lsmod |grep mac

```
So, as I see it, you have a few options:

- Use an earlier kernel
- Rebuild the modules for network device on the current kernel and make sure that the kernel is loading the correct one - and not more than one driver for your device.
- Let go of the past and and upgrade to newer version of Ubuntu!

---

### Post by Astro6312 on 2008-10-15
Here's the lsmod output.. no mac...
```
Module                  Size  Used by
vmnet                  43044  17 
vmmon                 118508  48 
af_packet              25864  0 
rfcomm                 44564  0 
l2cap                  29056  5 rfcomm
bluetooth              54756  4 rfcomm,l2cap
nfsd                  241668  13 
exportfs                7296  1 nfsd
ppdev                  10628  0 
radeon                120864  1 
drm                    78996  2 radeon
agpgart                37580  1 drm
ipv6                  287840  35 
nfs                   238536  6 
lockd                  68360  3 nfsd,nfs
sunrpc                159420  10 nfsd,nfs,lockd
cpufreq_userspace       7328  0 
cpufreq_stats           7488  0 
freq_table              5792  1 cpufreq_stats
cpufreq_powersave       2816  0 
cpufreq_ondemand        8616  0 
cpufreq_conservative     9960  0 
video                  17284  0 
tc1100_wmi              7812  0 
sony_acpi               6540  0 
pcc_acpi               13312  0 
hotkey                 12452  0 
dev_acpi               12164  0 
container               5504  0 
button                  7568  0 
acpi_sbs               21132  0 
battery                10884  2 acpi_sbs
ac                      6148  1 acpi_sbs
i2c_acpi_ec             6016  1 acpi_sbs
i2c_core               23296  1 i2c_acpi_ec
dm_mod                 63768  1 
tsdev                   8896  0 
md_mod                 76756  0 
lp                     13220  0 
e1000                 125884  0 
parport_pc             38724  1 
parport                39624  3 ppdev,lp,parport_pc
serio_raw               8580  0 
floppy                 65252  0 
pcspkr                  3204  0 
psmouse                40708  0 
shpchp                 50144  0 
pci_hotplug            30652  1 shpchp
sg                     40992  0 
evdev                  11136  1 
ext3                  148232  3 
jbd                    62996  1 ext3
ide_generic             2432  0 
ehci_hcd               37128  0 
uhci_hcd               36112  0 
usbcore               139140  3 ehci_hcd,uhci_hcd
ata_piix               12292  4 
libata                 84240  1 ata_piix
ide_cd                 36740  0 
cdrom                  42272  1 ide_cd
piix                   12420  1 
generic                 5892  0 
sd_mod                 21248  7 
3w_9xxx                36612  4 
scsi_mod              146312  4 sg,libata,sd_mod,3w_9xxx
thermal                14728  1 
processor              27592  1 thermal
fan                     5764  1 
capability              5896  0 
commoncap               8192  1 capability
vga16fb                14856  1 
vgastate               11136  1 vga16fb
fbcon                  44448  72 
tileblit                3712  1 fbcon
font                    9216  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3200  1 bitblit

```

This server is running VMware 1.0.4 and is build for the kernel. I am not sure anyway that it is a kernel problem since using eth1 works ok now.

I will upgrade that server soon, but was waiting to see if ubuntu 8.1 would solve the speed of  DISK I/O issues I am having with 8.0.4.  So far, the beta of 8.1 does not detect my network cards...

[See here for the discussion on I/O]("http://ubuntuforums.org/showthread.php?t=941421")...

---

### Post by iponeverything on 2008-10-15
what is your ethernet hardware?

The e1000 module in the listing below is not in use.
If it is not being used you should blacklist it so that it does not get in the way.

Is the Ethernet driver compiled into the kernel?

what is the the output of "lspci"

Look in /var/log/dpkg.log post the packages that upgraded during the last upgrade.

tail -500 /var/log/dpkg.log |grep installed

---

### Post by Astro6312 on 2008-10-15
iponeverything,

First, thanks for helping... Good to know there are people out there with knowledge and willing to share.

The hardware is a supermicro X7QC3 motherboard with two integrated NIC.  From what I read in the manual, the chipset for the NIC is 82575EB (Giga-Bit LAN ports).  I have ubuntu 6.06LTS server installed and did not have to do anything to configure those NICs.

I see in the doc ATI ES1000 graphic ctrl... not sure if there is a relation with the E1000?

Here's the output of lspci
```
0000:00:00.0 Host bridge: Intel Corporation Server Memory Controller Hub (rev b1)
0000:00:02.0 PCI bridge: Intel Corporation Server PCI Express x8 Port 2-3 (rev b1)
0000:00:04.0 PCI bridge: Intel Corporation Server PCI Express x8 Port 4-5 (rev b1)
0000:00:06.0 PCI bridge: Intel Corporation Server PCI Express x8 Port 6-7 (rev b1)
0000:00:08.0 System peripheral: Intel Corporation Server DMA Controller (rev b1)
0000:00:10.0 Host bridge: Intel Corporation Server Error Reporting Registers (rev b1)
0000:00:10.1 Host bridge: Intel Corporation Server Error Reporting Registers (rev b1)
0000:00:10.2 Host bridge: Intel Corporation Server Error Reporting Registers (rev b1)
0000:00:11.0 Host bridge: Intel Corporation: Unknown device 25f1 (rev b1)
0000:00:13.0 Host bridge: Intel Corporation: Unknown device 25f3 (rev b1)
0000:00:15.0 Host bridge: Intel Corporation Server FBD Registers (rev b1)
0000:00:16.0 Host bridge: Intel Corporation Server FBD Registers (rev b1)
0000:00:1c.0 PCI bridge: Intel Corporation Enterprise Southbridge PCI Express Root Port 1 (rev 09)
0000:00:1d.0 USB Controller: Intel Corporation Enterprise Southbridge UHCI USB #1 (rev 09)
0000:00:1d.1 USB Controller: Intel Corporation Enterprise Southbridge UHCI USB #2 (rev 09)
0000:00:1d.2 USB Controller: Intel Corporation Enterprise Southbridge UHCI USB #3 (rev 09)
0000:00:1d.7 USB Controller: Intel Corporation Enterprise Southbridge EHCI USB (rev 09)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d9)
0000:00:1f.0 ISA bridge: Intel Corporation Enterprise Southbridge LPC (rev 09)
0000:00:1f.1 IDE interface: Intel Corporation Enterprise Southbridge PATA (rev 09)
0000:00:1f.2 IDE interface: Intel Corporation Enterprise Southbridge SATA cc=IDE (rev 09)
0000:00:1f.3 SMBus: Intel Corporation Enterprise Southbridge SMBus (rev 09)
0000:01:00.0 PCI bridge: Intel Corporation Enterprise Southbridge PCI Express Upstream Port (rev 01)
0000:01:00.3 PCI bridge: Intel Corporation Enterprise Southbridge PCI Express to PCI-X Bridge (rev 01)
0000:02:00.0 PCI bridge: Intel Corporation Enterprise Southbridge PCI Express Downstream Port E1 (rev 01)
0000:02:02.0 PCI bridge: Intel Corporation Enterprise Southbridge PCI Express Downstream Port E3 (rev 01)
0000:03:00.0 PCI bridge: Intel Corporation 6700PXH PCI Express-to-PCI Bridge A (rev 09)
0000:03:00.2 PCI bridge: Intel Corporation 6700PXH PCI Express-to-PCI Bridge B (rev 09)
0000:06:00.0 Ethernet controller: Intel Corporation Enterprise Southbridge DPT LAN Copper (rev 01)
0000:06:00.1 Ethernet controller: Intel Corporation Enterprise Southbridge DPT LAN Copper (rev 01)
0000:07:01.0 RAID bus controller: 3ware Inc: Unknown device 1003
0000:0b:01.0 VGA compatible controller: ATI Technologies Inc: Unknown device 515e (rev 02)

```

Here you see the output of tail -500 /var/log/dpkg.log |grep installed.  You can see I have tried reinstall some network packages and remove iptables...

```
2008-10-08 03:32:57 status half-installed stress 0.18.4-1
2008-10-08 03:32:59 status installed stress 0.18.4-1
2008-10-10 07:52:53 status half-installed cpio 2.6-10ubuntu0.2
2008-10-10 07:52:53 status half-installed cpio 2.6-10ubuntu0.2
2008-10-10 07:52:54 status half-installed locales 2.3.18.13
2008-10-10 07:52:54 status half-installed locales 2.3.18.13
2008-10-10 07:52:56 status half-installed openssh-server 1:4.2p1-7ubuntu3.4
2008-10-10 07:52:57 status half-installed openssh-server 1:4.2p1-7ubuntu3.4
2008-10-10 07:52:57 status half-installed openssh-client 1:4.2p1-7ubuntu3.4
2008-10-10 07:52:57 status half-installed openssh-client 1:4.2p1-7ubuntu3.4
2008-10-10 07:52:58 status half-installed firefox-gnome-support 1.5.dfsg+1.5.0.15~prepatch080614d-0ubuntu1
2008-10-10 07:52:58 status half-installed firefox-gnome-support 1.5.dfsg+1.5.0.15~prepatch080614d-0ubuntu1
2008-10-10 07:52:59 status half-installed libnspr4 2:1.firefox1.5.dfsg+1.5.0.15~prepatch080614d-0ubuntu1
2008-10-10 07:52:59 status half-installed libnspr4 2:1.firefox1.5.dfsg+1.5.0.15~prepatch080614d-0ubuntu1
2008-10-10 07:52:59 status half-installed libnss3 2:1.firefox1.5.dfsg+1.5.0.15~prepatch080614d-0ubuntu1
2008-10-10 07:52:59 status half-installed libnss3 2:1.firefox1.5.dfsg+1.5.0.15~prepatch080614d-0ubuntu1
2008-10-10 07:53:00 status half-installed firefox 1.5.dfsg+1.5.0.15~prepatch080614d-0ubuntu1
2008-10-10 07:53:01 status half-installed firefox 1.5.dfsg+1.5.0.15~prepatch080614d-0ubuntu1
2008-10-10 07:53:03 status half-installed linux-headers-2.6.15-52 2.6.15-52.71
2008-10-10 07:53:05 status half-installed linux-headers-2.6.15-52 2.6.15-52.71
2008-10-10 07:53:12 status half-installed linux-headers-2.6.15-52-server 2.6.15-52.71
2008-10-10 07:53:32 status half-installed linux-headers-2.6.15-52-server 2.6.15-52.71
2008-10-10 07:53:48 status half-installed linux-image-2.6.15-52-server 2.6.15-52.71
2008-10-10 07:54:07 status half-installed linux-image-2.6.15-52-server 2.6.15-52.71
2008-10-10 07:54:14 status half-installed ssh 1:4.2p1-7ubuntu3.4
2008-10-10 07:54:14 status half-installed ssh 1:4.2p1-7ubuntu3.4
2008-10-10 07:54:14 status half-installed ssh-askpass-gnome 1:4.2p1-7ubuntu3.4
2008-10-10 07:54:14 status half-installed ssh-askpass-gnome 1:4.2p1-7ubuntu3.4
2008-10-10 07:54:15 status installed cpio 2.6-10ubuntu0.3
2008-10-10 07:54:16 status installed locales 2.3.18.14
2008-10-10 07:54:19 status installed openssh-client 1:4.2p1-7ubuntu3.5
2008-10-10 07:54:28 status installed openssh-server 1:4.2p1-7ubuntu3.5
2008-10-10 07:54:38 status installed libnspr4 2:1.firefox1.5.dfsg+1.5.0.15~prepatch080614e-0ubuntu3
2008-10-10 07:54:38 status installed libnss3 2:1.firefox1.5.dfsg+1.5.0.15~prepatch080614e-0ubuntu3
2008-10-10 07:54:38 status installed firefox 1.5.dfsg+1.5.0.15~prepatch080614e-0ubuntu3
2008-10-10 07:54:39 status installed firefox-gnome-support 1.5.dfsg+1.5.0.15~prepatch080614e-0ubuntu3
2008-10-10 07:54:39 status installed linux-headers-2.6.15-52 2.6.15-52.72
2008-10-10 07:54:39 status installed linux-headers-2.6.15-52-server 2.6.15-52.72
2008-10-10 07:54:51 status installed linux-image-2.6.15-52-server 2.6.15-52.72
2008-10-10 07:54:52 status installed ssh 1:4.2p1-7ubuntu3.5
2008-10-10 07:54:52 status installed ssh-askpass-gnome 1:4.2p1-7ubuntu3.5
2008-10-10 11:56:53 status half-installed ethereal-common 0.99.0-1ubuntu1
2008-10-10 11:56:57 status half-installed ethereal 0.99.0-1ubuntu1
2008-10-10 11:56:58 status installed ethereal-common 0.99.0-1ubuntu1
2008-10-10 11:56:58 status installed ethereal 0.99.0-1ubuntu1
2008-10-10 12:45:30 status half-installed arptables 0.0.3-1
2008-10-10 12:45:31 status installed arptables 0.0.3-1
2008-10-10 12:47:24 status installed arptables 0.0.3-1
2008-10-10 12:47:25 status half-installed arptables 0.0.3-1
2008-10-10 12:47:25 status not-installed arptables <none>
2008-10-10 12:47:25 status half-installed arpwatch 2.1a13-2
2008-10-10 12:47:28 status installed arpwatch 2.1a13-2
2008-10-14 08:05:27 status half-installed netbase 4.24ubuntu3
2008-10-14 08:05:27 status half-installed netbase 4.24ubuntu3
2008-10-14 08:05:30 status installed netbase 4.24ubuntu3
2008-10-14 09:23:42 status half-installed net-tools 1.60-16ubuntu2
2008-10-14 09:23:42 status half-installed net-tools 1.60-16ubuntu2
2008-10-14 09:23:43 status installed net-tools 1.60-16ubuntu2
2008-10-14 09:47:42 status installed ubuntu-standard 0.120
2008-10-14 09:47:42 status half-installed ubuntu-standard 0.120
2008-10-14 09:47:42 status not-installed ubuntu-standard <none>
2008-10-14 09:47:42 status installed iptables 1.3.3-2ubuntu4.1
2008-10-14 09:47:43 status half-installed iptables 1.3.3-2ubuntu4.1
2008-10-14 09:47:43 status not-installed iptables <none>

```

Not sure how to blacklist a module.

Thanks,

---

### Post by iponeverything on 2008-10-15
First remove this package.

dpkg -r arptables

Flush and firewall rules have:

sudo iptables -F
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT

If you need it back later, it is easy to reinstall. It just tool for mac based filtering. Now if this didn't solve our problem.. 

I think that e1000 is the driver that your using.. not positive though. 

So If the above didn't do the trick. blacklist it and reboot see that works:

echo "blacklist e1000" >> /etc/modprobe.d/blacklist

To remove it from the blacklist just open /etc/modprobe.d/blacklist and remove the last line.

Lets see how this goes.. if your not fixed we can do some more digging tomorrow.

Its bed time here.

---

### Post by Astro6312 on 2008-10-15
It's going to be hard for me to try those, since that server is back in prod after I found a work around with eth1.

The thing I don't get is why eth1 is ok but no eth0? 

I would assume they where using the same kernel drivers.

I did try the iptables -F before without success.

Thanks again.

---

