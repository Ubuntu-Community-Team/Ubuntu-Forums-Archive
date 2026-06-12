---
title: "Can't detect onboard lan"
date: 2008-04-01
forum: Server Platforms
---

### Post by hosea_sanchez on 2008-04-01
big time newbie... working on a server kernel 2.6.15-51-server  

sudo vi /etc/network/interfaces

responds with
eth0 and my static address...

if I enter <ifconfig>

I get the response that it cannot find any devices...

I am running this in the shell or terminal

I see code that tells me that it has found the on board lan... I have cloned the drive and loaded it in the same model motherboard/have tried  an intel mb.

If I load the drive with the original mb.. everything is ok... 

I am lost.. lost ... lost.. search the web and tried most suggestions that I found on forums... any help would be appreciated... I am reading, reading and reading

---

### Post by JLB on 2008-04-01
Can you open a terminal and post the output of > lspci -v and ```
lsmod
``` and ```
ifconfig
```This should help someone pinpoint what kind of network card you have and then it is a lot easier to figure out if you have the correct module loaded.

---

### Post by cdenley on 2008-04-01
The ethernet adapter assignments are persistent for the mac address. If you replace the ethernet card, it gives the new card a new number. I believe you are using dapper, correct? I think on dapper, if you wanted to clear the previous ethernet assignments, you could do
```

sudo rm /etc/iftab

```
On newer releases, the persistent ethernet assignments are stored in /etc/udev/rules.d/70-persistent-net.rules. I'm guessing if you run "ifconfig -a" you will see the new ethernet adapter is eth1, but is not configured in /etc/network/ineterfaces so it is disabled. You either need to fix it so it is eth0, or edit /etc/network/interfaces to use eth1.

---

### Post by netlogic on 2008-04-01
> **hosea_sanchez said:**
> big time newbie... working on a server kernel 2.6.15-51-server  

sudo vi /etc/network/interfaces

responds with
eth0 and my static address...

if I enter <ifconfig>

I get the response that it cannot find any devices...

I am running this in the shell or terminal

I see code that tells me that it has found the on board lan... I have cloned the drive and loaded it in the same model motherboard/have tried  an intel mb.

If I load the drive with the original mb.. everything is ok... 

I am lost.. lost ... lost.. search the web and tried most suggestions that I found on forums... any help would be appreciated... I am reading, reading and reading

dmesg |grep eth
dmesg |grep ath
lspci |grep Ethernet 
sudo lshw

and post Ethernet related things for us

after that type "lsmod" and make sure ethernet device described by the kernel messages are loaded. there is a chance it is loading the wrong module. let's take it one step at a time.

---

### Post by hosea_sanchez on 2008-04-01
First... I am missing the first few lines of the output lspci - v as they are at the top of the screen and I can't figure out how to scroll up...

and... other than typing all the output, is there any way to get the code?

so here is what I have

Output lspci - v

Flags: bus master, 66mhz, medium devsel, latency 64, IRQ 209
Memory at dffe0000 (32bit, non-prefetchabel) [size_128k]
I/O ports at ef80 [size=64]
Capabilities:  [dc] Power Management version 2
Capabilities:  [e4] PCI-X non-bridge device.

0000:02:00:0 PCI bridge: Intel Corporation 6700PXH PCI Express-to-PCI Bridge A (rev 09) (prog-if 00 [Normal decode ])

Flags: bus master, fast devsel, latency 0
Bus:  primary=02, secondary-04, subordinate=04, sec-latency=48
Capabilities: [44] #10 [0071]
Capabilities: [5c] Message signaled Interrupts: 64bit= Queue=0/0 Enable-
Capabilities: [6c] Power Management version 2
Capabilities: [d8]

0000:02:00.2 PCI Bridge: Inter Corporation 6700PXH PCI Express-to PCI Bridge B (rev 09) (prog-if 00 [Normal decode])

Flags: bus master, fast devsel, latency 0
Bus:  primary=02, secondary-03, subordinate=03, sec-latency=64
Capabilities:  [44] #10 [0071]
Capabilities: {5c] Message signaled Interrupts: 64bit= Queue=0/0 Enable-

Capabilities: [6c] Power Management version 2
Capabilities: [d8]

Output  lsmod

evdev	           11136	     0
sg	               40992	        0
ext3	            148232            1
jbd		      62996	        1	ext3
ide generic	   2432	             0
ehci_hcd	   37128	     0
uhci_hcd		36112	     0
usbcore		    139140	    4	usbhid,ehci_hcd,uhci_hcd
sd_mod		21248	            3
generic		5892		      0
ata_piix		12292	     4
ahci			19204	        0
libata			84248	        2   ata_piix,ahci
scsi_mod		146312	   4  sg,sd_mod,ahci,libata
thermal		14728	              0
processor		27592	    1	thermal
fan			5764		0
fbcon		44448	              0
tileblit		3712		1	fbcon
font			9216		1	fbcon
bitblit		7424		        1	fbcon
softcursor		3200		1	bitblit
capability		5896		0
commoncap	8192		2	capability

ifconfig

no output


sudo vi /etc/network/interfaces

auto eth0
iface  eth0 inet static

address 192.168.0.198
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.1268.0.255
gateway 192.168.0.1

I have the same problem if I take a cloned hd and drop it into the identical mboard.... If I take the clone and drop it into the original mboard, i have lan

Thanks

---

### Post by cdenley on 2008-04-01
Did you read my post? What is the output of "ifconfig -a"?

> 
other than typing all the output, is there any way to get the code?

You can pipe output to a file. For example:
```

ifconfig -a>output.txt

```

---

### Post by hosea_sanchez on 2008-04-01
config -a

eth2

Link encap: Ethernet  HW addr mac address.........
BROADCAST MULTICAST MTU:1500 Metric :1


lo

Link encap:Local Loopback
LOOPBACK MTU: 16436 Metic:1

........ RX and TX packets etc.. all at 0



I edited the above so that eth0 had the above address and it still didn't work.

The software on this machine adds Ethernet ports for every machine added to it's network with it's mac address...

There are some machines with 16 Ethernet ports...

My difficulty is getting the output.txt...there is no printer installed or way to save the file... there are no other drives on this machine...

This is a bit overwhelming at the moment...

---

### Post by cdenley on 2008-04-01
```

sudo rm /etc/iftab
reboot
```
If you read my post, I explained what is going on. Every time the operating system sees an ethernet adapter, it gives it a number. The number matches the mac address. It will keep this assignment forever, and the number will never be re-used for a new device unless you manually delete it. When you copy from one system, to another, to another (booting each system before you copy it), then on the last copy, ubuntu will have assigned a number to all the ethernet adapters in all your computers. See for yourself:
```

sudo nano /etc/iftab

```
If you create all your copies from a single hard drive, then all your copies should see the ethernet adapter as eth1.

---

### Post by netlogic on 2008-04-01
> **hosea_sanchez said:**
> config -a

eth2

Link encap: Ethernet  HW addr mac address.........
BROADCAST MULTICAST MTU:1500 Metric :1


lo

Link encap:Local Loopback
LOOPBACK MTU: 16436 Metic:1

........ RX and TX packets etc.. all at 0



I edited the above so that eth0 had the above address and it still didn't work.

The software on this machine adds Ethernet ports for every machine added to it's network with it's mac address...

There are some machines with 16 Ethernet ports...

My difficulty is getting the output.txt...there is no printer installed or way to save the file... there are no other drives on this machine...

This is a bit overwhelming at the moment...

Ah... You did had ethernet. Next time, please post the complete information. We can't help you without it.

---

### Post by hosea_sanchez on 2008-04-01
I need to clarify.... My "master drive" did work in the original mboard.  I cloned the drive and installed it with an identical mboard.  That system did not find the network.  I then tried the clone in another server with an intel mboard.  It did not find the network either.

I am trying to understand why the clone did not work in the indentical mboard or the intel mboard.

---

### Post by netlogic on 2008-04-01
> **hosea_sanchez said:**
> 
I am trying to understand why the clone did not work in the indentical mboard or the intel mboard.

Because you still had the mac address of older machine on eth0. It was being occupied.

less /etc/iftab

---

### Post by hosea_sanchez on 2008-04-01
cdenley - rm'd the /etc/iftab and everything worked... THANKS  SO MUCH for humoring me!!! Thanks everyone who posted.

---

### Post by netlogic on 2008-04-01
Now, you know something new today. Now, if someone has the same question, it is up to you to step in and help out.

---

