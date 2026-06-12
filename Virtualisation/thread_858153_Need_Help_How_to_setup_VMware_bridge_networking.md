---
title: "Need Help: How to setup VMware bridge networking?"
date: 2008-07-13
forum: Virtualisation
---

### Post by subratabera on 2008-07-13
Hello friends,

I am new here and also new to virtualization techniques. Without wasting your time let me explain my problem. I have installed vmware server in my Ubuntu Hardy box which have just one NIC card. I have several VMs installed and always used host only and NAT networking for various experimentations but never tried bridge networking. Now the problem is, I want to configure bridge networking between host(Ubuntu) and guest(Win XP SP2). After following several guides and various forum posts, I failed to connect both systems. They can't ping each other. Here are the specifications of both systems:

Ubuntu (using 2.6.24-19-generic kernel and vmware-any-any-update 116 to configure vmware):

> 
eth0      Link encap:Ethernet  HWaddr 00:16:76:6f:93:a8  
          inet addr:192.168.0.250  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:164600 (160.7 KB)  TX bytes:164600 (160.7 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.13.1  Bcast:192.168.13.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.238.1  Bcast:192.168.238.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Win XP:

> 
Windows IP Configuration
  Host Name : winxp
  Primary DNS Suffix :
  Node Type : Unknown
  IP Routing Enabled : No
  WINS Proxy Enabled : No
Ethernet adapter local Area Connection:
  Connection-specific DNS Suffix :
  Description : VMware Accelerated AMD PCNet Adapter
  Physical Address : 00-0C-29-FE-36-25
  IP Address : 192.168.0.240
  Subnet Mask : 255.255.255.0
  Default Gateway : 


Win XP .vmx file contents:

> 
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4"
scsi0.present = "TRUE"
memsize = "512"
ide0:0.present = "TRUE"
ide0:0.fileName = "Windows XP Professional.vmdk"
ide0:0.writeThrough = "TRUE"
ide1:0.present = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "atapi-cdrom"
floppy0.fileName = "Auto detect"
Ethernet0.present = "TRUE"
Ethernet0.connectionType = "bridged"
displayName = "Windows XP Pro"
guestOS = "winxppro"
priority.grabbed = "normal"
priority.ungrabbed = "normal"
powerType.powerOff = "hard"
powerType.powerOn = "hard"
powerType.suspend = "hard"
powerType.reset = "hard"

ide0:0.redo = ""
ide1:0.startConnected = "TRUE"
ethernet0.addressType = "generated"
uuid.location = "56 4d 2c 9e 43 17 e3 9a-2b b2 65 95 06 fe 36 25"
uuid.bios = "56 4d 2c 9e 43 17 e3 9a-2b b2 65 95 06 fe 36 25"
ethernet0.generatedAddress = "00:0c:29:fe:36:25"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "FALSE"

usb.present = "FALSE"
usb.generic.autoconnect = "FALSE"

floppy0.startConnected = "FALSE"

snapshot.disabled = "TRUE"

ide1:0.autodetect = "TRUE"

usb.autoConnect.device0 = ""

floppy0.autodetect = "TRUE"

ethernet0.vnet = "/dev/vmnet0"

sound.present = "FALSE"
sound.fileName = "/dev/dsp"
sound.autodetect = "FALSE"

sound.virtualDev = "es1371"


"ps ax | grep -i bridge" returns:

> 
 5860 ?        S      0:00 /usr/bin/vmnet-bridge -d /var/run/vmnet-bridge-0.pid /dev/vmnet0 eth0
 6514 pts/3    R+     0:00 grep -i bridge


Firewalls are disabled on both systems.

I have tried almost everything to setup bridge networking but no success. I will really appreciate you help. Please also share any specific link where step by step tutorials are available for vmware products for various problems if any.

Thanks in advance.

Regards,

SB.

---

### Post by dwanders on 2009-10-07
Did you ever get this issue resolved? I think I am experiencing the same kind of problem.

---

### Post by dcstar on 2009-10-10
> **dwanders said:**
> Did you ever get this issue resolved? I think I am experiencing the same kind of problem.

What issue?, bridging is set up by default in VMWare server and works fine for virtually everyone.

If **you** have specific problems, then post the details and people may be able to assist.

---

### Post by dwanders on 2009-10-10
Huh - I was stating that I think I am experiencing the same problem as the original poster, and since there was no resolution posted - I asked them if they had found one.

---

