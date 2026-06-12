---
title: "Network is unreachable."
date: 2009-04-21
forum: Server Platforms
---

### Post by svennam on 2009-04-21
Hi ...
Help please.
I have installed Ubuntu Server 8.10 on a new desktop.  Then I installed desktop environment into that server to download oracle Express Edition Database Software to install it.  My problem is the Firefox worked a couple of days well.  Suddenly it started not working showing Network is in reachable.  I opened Terminal window and typed as follows:

ping 91.189.94.249 
I got network is unreachable. 
The fact is I have wired network,which is working yesterday.
Then I typed ping 127.0.0.1
Then it is transmitting packets and received packets.
Then I typed ifconfig eth0
I got eth0: error fetching interface information: Device not found.
If ping anything other than 127.0.0.1, I am getting network is unreachable.
Don't have more ideas.   Need help.

---

### Post by daboroe on 2009-04-22
> **svennam said:**
> Hi ...
Help please.
I have installed Ubuntu Server 8.10 on a new desktop.  Then I installed desktop environment into that server to download oracle Express Edition Database Software to install it.  My problem is the Firefox worked a couple of days well.  Suddenly it started not working showing Network is in reachable.  I opened Terminal window and typed as follows:

ping 91.189.94.249 
I got network is unreachable. 
The fact is I have wired network,which is working yesterday.


> 
Then I typed ping 127.0.0.1
Then it is transmitting packets and received packets.
Then I typed ifconfig eth0
I got eth0: error fetching interface information: Device not found.
If ping anything other than 127.0.0.1, I am getting network is unreachable.
Don't have more ideas.   Need help.
Pinging 127.0.0.1 is back and forth to your network card. I would tried to reseed it on the motherboard. It sounds like it is detecting it and not at the same time. If it was not in right then you would not be able to ping 127.0.0.1. 

this is very interesting. 

try to run this command see what happens:
> 
#Sudo ifup eht0


---

### Post by netztier on 2009-04-22
> **daboroe said:**
> Pinging 127.0.0.1 is back and forth to your network card.

Sorry, that's wrong. 

Packets to/from 127.0.0.1 should never even get close to any network card - you can even have such a loopback interface without even having a physical network card in your system. It's completely "virtual".

regards

Marc

---

### Post by netztier on 2009-04-22
> **svennam said:**
> 
Then I installed desktop environment into that server


Great! :-/ Now /etc/network/interfaces and NetworkManager are possibly in conflict about who manages which network interface card. Again a reason why I personally never suggest to run the ubuntu-desktop package on a server.

If you absolutely need a GUI, install Ubuntu Desktop; you can always add a server or custom kernel with it's special optimisations later on, if you need them.

> 
ping 91.189.94.249 
I got network is unreachable. 


We need the outputs of these commands (working from upper to lower layers in the ISO/OSI network layer model):

to see which DNS servers are configured: **cat /etc/resolv.conf**
to see if there's manually configured interfaces: **cat /etc/network/interfaces**
to see the local routing table: **netstat -nr**
to see the state of the interfaces: **ifconfig -a **
to see if and what ethernet IFs were seen during startup: **dmesg | grep eth**


regards

Marc

---

### Post by svennam on 2009-04-22
Thanks Marc.  I will execute commands you suggested and post the output when I get back home.

---

### Post by Iowan on 2009-04-22
> **netztier said:**
> Sorry, that's wrong. 
Packets to/from 127.0.0.1 should never even get close to any network card I, too, thought pinging 127.0.0.1 checked whether network card was functional...
Won't be the last time I'm wrong...

---

### Post by mlinux on 2009-04-22
127.0.0.1 just a virtual network loop back, no network card require.

As what netztier recommend, server should not have the desktop GUI. Yes, is tough for window user to navigate the server using command line. If you must have the GUI, can consider remote access via webmin but now  you have to resolve the network problem first before remote access.

---

### Post by svennam on 2009-04-22
> **netztier said:**
> Great! :-/ Now /etc/network/interfaces and NetworkManager are possibly in conflict about who manages which network interface card. Again a reason why I personally never suggest to run the ubuntu-desktop package on a server.

If you absolutely need a GUI, install Ubuntu Desktop; you can always add a server or custom kernel with it's special optimisations later on, if you need them.



We need the outputs of these commands (working from upper to lower layers in the ISO/OSI network layer model):

to see which DNS servers are configured: **cat /etc/resolv.conf**
to see if there's manually configured interfaces: **cat /etc/network/interfaces**
to see the local routing table: **netstat -nr**
to see the state of the interfaces: **ifconfig -a **
to see if and what ethernet IFs were seen during startup: **dmesg | grep eth**


regards

Marc


Here are the outputs for the commands you suggested:


cat /etc/resolv.conf:
domain Belkin
search Belkin
nameserver 192.168.2.1

cat /etc/network/interfaces:
#The file describes the network interfaces available on your system
#and how to activate them.  For more information, see interfaces(5)
#The loopback network interface
auto lo
iface lo inet loopback
#The primay network interface
auto eth0
iface eth0 inet dhcp

netstat -nr:
Kernel IP routing table
Destination   Gateway   Genmask   Flags   MSS Window   irtt  Iface

ifconfig -a
lo   Link encap:Local Loopback
     inet  addr:127.0.0.1  Mask:255.0.0.0
     inet6 addr: ::1/128 Scope: Host
     UP LOOPBACK RUNNING MTU:16436 Metric:1
     RX packets:20550 errors:0 dropped:0 overruns:0 frame:0
     TX packets:20550 errors:0 dropped:0 overruns:0 carrier:0
     collision:0 txqueuelen:0
pan0 Link encap:Ethernet HWaddr 96:49:56:2e:c6:63
     BROADCAST MULTICAST MTU:1500 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes:0(0.0 B) TX bytes:0(0.0 B)

dmesg | grep eth:
[   3.126692] Driver 'sr' needs updating - please use bus_type methods
[   3.129345] Driver 'sd' needs updating - please use bus_type methods

---

### Post by aesis05401 on 2009-04-22
The please use bus type methods messages are supposedly just noise.  I have seen that conversation done to death on Launchpad and lkml - and the resolution is always that those messages are not related to the issues.

Here is one example: [https://bugs.launchpad.net/ubuntu/+bug/186167](https://bugs.launchpad.net/ubuntu/+bug/186167)

That thread has a link to a lkml conversation, and I have seen others including one where a kernel hacker explained where those messages are coming from and why they don't matter.

---

### Post by mlinux on 2009-04-23
Your eth0 is gone? Not listed with the ifconfig -a. Hardware problem? May be should force fix ip address to the

 /etc/network/interfaces

---

### Post by netztier on 2009-04-23
> **svennam said:**
> 
```
cat /etc/resolv.conf:
domain Belkin
search Belkin
nameserver 192.168.2.1

```


Suggestion: use [CODE ][/CODE ] tags around text snippets from console commands and console output. The text becomes a lot easier to read. Now. That's interesting. Assuming you have no eth0 nor a wlan0 interface - these informations must be a leftover from the time when DHCP was still working. 

> ```
cat /etc/network/interfaces:
#The file describes the network interfaces available on your system
#and how to activate them.  For more information, see interfaces(5)
#The loopback network interface
auto lo
iface lo inet loopback
#The primay network interface
auto eth0
iface eth0 inet dhcp

```

Hm. So we have a DHCP configuration for eth0 - still, we don't know if the kernel has actually seen an ethernet interface and if it had named it "eth0".


> ```
netstat -nr:
Kernel IP routing table
Destination   Gateway   Genmask   Flags   MSS Window   irtt  Iface

```

Empty routing table, not even a local subnet route - ok, that's to be expected when there is no active LAN interface.

> ```

ifconfig -a
lo   Link encap:Local Loopback
     inet  addr:127.0.0.1  Mask:255.0.0.0
     inet6 addr: ::1/128 Scope: Host
     UP LOOPBACK RUNNING MTU:16436 Metric:1
     RX packets:20550 errors:0 dropped:0 overruns:0 frame:0
     TX packets:20550 errors:0 dropped:0 overruns:0 carrier:0
     collision:0 txqueuelen:0
pan0 Link encap:Ethernet HWaddr 96:49:56:2e:c6:63
     BROADCAST MULTICAST MTU:1500 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes:0(0.0 B) TX bytes:0(0.0 B)

```

Allright then, the kernel has not seen any other interfaces than lo (Loopback).

> ```

dmesg | grep eth:
[   3.126692] Driver 'sr' needs updating - please use bus_type methods
[   3.129345] Driver 'sd' needs updating - please use bus_type methods
```

Commonly, the kernel writes out someting to dmesg that contains the string "eth" if it discovers and activates an ethernet interface.

Hm. 

Now we need to dig deeper. It might be a lot of text output, so I suggest to copy&paste it into a text file and usb-stick-copy it over to a working computer and add it as a file attachment to your posting.

To find out what NIC is in your computer and to see how it is seen by the kernel, can you please show us the outputs of these commands?

[LIST]
[*]**lspci** 
[*]**sudo lshw -c network** 
[*]**cat /etc/udev/rules.d/70-persistent-net.rules**
[*]**lsmod**
[/LIST]



regards

Marc

---

### Post by netztier on 2009-04-23
> **aesis05401 said:**
> That thread has a link to a lkml conversation, and I have seen others including one where a kernel hacker explained where those messages are coming from and why they don't matter.

Agreed, these messages that showed up from dmesg are irrelevant to this thread.

I was hoping to see some substrings *eth* from "ethernet" or "eth0" or "eth1", hence I asked the OP to grep dmesg's output for "eth".

regards

Marc

---

### Post by svennam on 2009-04-23
I will try.  The problem is, I have to write the output from each command on paper and use another computer, type and post.   I will see whether I can do it.

---

### Post by svennam on 2009-04-23
I could do it easily following your suggestions.  The following is the output for each of the commands:

lspci:
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)

sudo lshw -c network:
*-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:ba:f4:5b:a3:41
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

cat /etc/udev/rules.d/70-persistent-net.rules:
# This file was automatically generated by the /lib/udev/write_net_rules
# program run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single line.

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:1d:24:d6:c6", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

lsmod:
Module                  Size  Used by
binfmt_misc            16904  1 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ipv6                  263460  24 
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  2 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
wmi                    14504  0 
container              11520  0 
sbs                    19464  0 
pci_slot               12552  0 
video                  25104  0 
output                 11008  1 video
sbshc                  13440  1 sbs
battery                18436  0 
af_packet              25600  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
loop                   23180  0 
pcspkr                 10624  0 
psmouse                45200  0 
serio_raw              13444  0 
evdev                  17696  7 
parport_pc             39460  1 
parport                42604  3 ppdev,lp,parport_pc
snd_hda_intel         381360  1 
snd_pcm_oss            46720  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83332  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38400  0 
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29832  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 14224  0 
snd                    63268  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 38036  0 
pci_hotplug            35236  1 shpchp
soundcore              15328  1 snd
snd_page_alloc         16264  2 snd_hda_intel,snd_pcm
ext3                  132872  4 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usbhid                 35968  0 
hid                    50560  1 usbhid
sd_mod                 42264  6 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43040  1 sr_mod
sg                     39220  0 
pata_acpi              12160  0 
ata_piix               24708  5 
ata_generic            12804  0 
libata                176032  3 pata_acpi,ata_piix,ata_generic
scsi_mod              155212  4 sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43916  0 
uhci_hcd               30864  0 
usbcore               149360  4 usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42284  4 acpi_cpufreq,thermal
fan                    12420  0 
fbcon                  47392  0 
tileblit               10752  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60700  3

---

### Post by netztier on 2009-04-24
a suggestion: when you copy&paste commands or output from the command line, enclose it in CODE tags by highlighting the text with the mouse and klicking the **#** button in the toolbar above the edit box. It makes reading a lot easier, because you can instantly tell apart what is text and what ist - well... "code".

> **svennam said:**
> 
```

lspci:
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)

```

That's not good. There's no ethernet controller in there! 
> ```

sudo lshw -c network:
*-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: [COLOR="Red"]pan0[/COLOR]
       serial: 96:ba:f4:5b:a3:41
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Hm. "pan0" makes me think of firewire or bluetooth, but not ethernet. I have a similarly looking pan0 on my PC here - it certainly does not refer to a real ethernet interface.


> ```

cat /etc/udev/rules.d/70-persistent-net.rules:
# This file was automatically generated by the /lib/udev/write_net_rules
# program run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single line.

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:1d:24:d6:c6", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

```

That must be a leftover from when the NIC was still working. I would suspect that this NIC has somehow "disappeared" from the PCI bus.

> ```

lsmod:
Module                  Size  Used by
binfmt_misc            16904  1 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
...
...
...
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60700  3

```

Hm. Now it's expected that no module for the r8169-based NIC appears in this list, since we're the PCI device is missing in the first place.

Can you get into the BIOS of that computer to see if the (onboard?) ethernet interface is disabled? Now why and how that could happen, I have no clue at all...

regards

Marc

---

### Post by svennam on 2009-04-24
I can see that.  What should I do, If it is disabled?
By the way I am new to this form.  I did not understand your following suggestion.  Can you explain more on this
"a suggestion: when you copy&paste commands or output from the command line, enclose it in CODE tags by highlighting the text with the mouse and klicking the # button in the toolbar above the edit box. It makes reading a lot easier, because you can instantly tell apart what is text and what ist - well... "code"."
I don't see # button in toolbar. I don't see CODE tag, but I see Wrap [Code] tags.

---

### Post by koenn on 2009-04-24
> **svennam said:**
> 
I don't see # button in toolbar. I don't see CODE tag, but I see Wrap ```
 tags.

yes, it's that one;
like so:
[CODE]
 ________________
< that's the one >
 ----------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||


```

---

### Post by svennam on 2009-04-24
> What happens if I use quote.  Just testing..
I am just testing what happens if I use >  

---

### Post by netztier on 2009-04-26
> **svennam said:**
> I can see that.  What should I do, If it is disabled?


Well - what about enabling it? Then reboot and look at the output of **lspci** first, if it lists an "Ethernet conroller". On my system with Intel NICs, these look like this in lspci:

```
01:08.0 [COLOR="Red"]Ethernet controller[/COLOR]: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
05:00.0 [COLOR="Red"]Ethernet controller[/COLOR]: Intel Corporation 82572EI Gigabit Ethernet Controller (Copper) (rev 06)

```

Guessing from the leftovers we saw in **/etc/udev/rules.d/70-persistent-net.rules** on your system, I would expect the name "Realtek" to show up in there somewhere.

If the onboard Ethernet NIC is activated in BIOS but does not show up in lspci, something's seriously wrong. In that case, I suggest to disable it in the BIOS and installing a PCI or PCIe-NIC instead. 

regards

Marc

---

### Post by svennam on 2009-04-26
Marc,
     I appollogise my delay.   I have entered into bios.  But I could not find (onboard?) ethernet interface. But I found the following:
On board H/W Lan   Enabled
On board LAN Boot ROM  Disable
On board Serial Port 1 [3F8/IRQ 4]
On board Serial Port 2 [2F8/IRQ 3]
On board parallel Port [378/IRQ 7]

When I entered Bios I found the following options.  I appreciate If you could tell me which option should I select to see what you wnated.

MB Intelligent Tweaker
Standard CMOS feature
Advanced BIOS feature
Integrated peripherils
Power Management set up
PnP/PCI configurations
PC Health status
Load Fail-defaults
Load Optimized defaults
Set Supervisor Password
Set User password etc., etc.

---

### Post by mlinux on 2009-04-27
> **svennam said:**
> 
On board H/W Lan   Enabled


This indicate that your onboad network is enabled. Next is to look at the network cable connector at the server, when is up and running, you should see 2 LED light next to the socket. If not, the network card may be at fault.

Quick fix would be disable the on board lan and install a PCI NIC.

---

### Post by svennam on 2009-04-27
Hi mlinux,
           I don't know where is on board lan.  Then how to install PCI NIC.  Little more explanation would held me.

---

### Post by mlinux on 2009-04-28
> **svennam said:**
> Hi mlinux,
           I don't know where is on board lan.  Then how to install PCI NIC.  Little more explanation would held me.

You can not see the on boad lan but the network socket normally at the back above the USB connector. The place you plug in your RJ45 network cable.

Before you proceed, may be you should get a copy of the linux that run on CD only. If you can access internet from the CD verion, your on board network is working. We can then diagnose from there.

---

