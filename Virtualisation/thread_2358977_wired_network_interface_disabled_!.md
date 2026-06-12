---
title: "wired network interface disabled !"
date: 2017-04-19
forum: Virtualisation
---

### Post by sofianito on 2017-04-19
Hi,

My ethernet interface has been disabled, and I can't find the root cause. I think the issue happened while creating the bridge in the following tutorial while trying to enable KVM GPU passthrough: [https://ycnrg.org/vga-passthrough-with-ovmf-vfio/](https://ycnrg.org/vga-passthrough-with-ovmf-vfio/)

Any help appreciated.

```
cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS"
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS"

```

```

uname -a
Linux bumbara 4.4.0-72-generic #93-Ubuntu SMP Fri Mar 31 14:07:41 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

```

sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 78
       serial: xx:xx:xx:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-72-generic firmware=22.361476.0 ip=192.168.1.181 latency=0 link=yes multicast=yes
       resources: irq:129 memory:edb00000-edb01fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: virbr0-nic
       serial: yy:yy:yy:yy:yy:yy
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s

```

```

lspci -nn | grep -i net
02:00.0 Network controller [0280]: Intel Corporation Device [8086:24fd] (rev 78)

```

```

ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether xx:xx:xx:xx:xx:xx brd ff:ff:ff:ff:ff:ff
3: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default qlen 1000
    link/ether 00:00:00:00:00:00 brd ff:ff:ff:ff:ff:ff
4: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT group default qlen 1000
    link/ether 52:54:00:a0:4c:28 brd ff:ff:ff:ff:ff:ff

```

```
ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether xx:xx:xx:xx:xx:xx brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.181/24 brd 192.168.1.255 scope global dynamic wlp2s0
       valid_lft 42125sec preferred_lft 42125sec
    inet6 fe80::6f95:66d3:5498:12cf/64 scope link 
       valid_lft forever preferred_lft forever
3: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 00:00:00:00:00:00 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
4: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 52:54:00:a0:4c:28 brd ff:ff:ff:ff:ff:ff

```

```

cat  /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

I added the following to /etc/sysctl.conf:
```

# Enable IPv4 forwarding
net.ipv4.ip_forward=1  
net.ipv4.conf.all.rp_filter=1  
net.ipv4.icmp_echo_ignore_broadcasts=1  
net.ipv4.conf.default.proxy_arp=1

```

```

cat /etc/modules
pci_stub  
vfio  
vfio_iommu_type1  
vfio_pci  
vfio_virqfd  
kvm  
kvm_intel

```

I added the following to /etc/default/grub and run after sudo update-grub:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=on iommu=pt"

```

I added the following to /etc/initramfs-tools/modules and run after sudo update-initramfs -u:
```

pci_stub ids=8086:591b,10de:13b6

```

I had before persistent net rules to rename interfaces to wlan0 and eth0, but after the issue I disabled the rules.
```

cat /etc/udev/rules.d/70-persistent-net.rules 
# PCI device 0x10ec:0x8xxxx (ethernet)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="yy:yy:yy:yy:yy:yy", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0xyyy (wifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="xx:xx:xx:xx:xx:xx", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```

```

cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
#dns=dnsmasq

[ifupdown]
managed=false

```

```

lsmod
Module                  Size  Used by
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  3
ccm                    20480  3
rfcomm                 69632  2
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 24576  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack_ipv4      16384  2
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          106496  5 nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                126976  0
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
ip_tables              24576  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               36864  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
nvram                  16384  0
msr                    16384  0
cmac                   16384  2
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
btusb                  45056  0
btrtl                  16384  1 btusb
bbswitch               16384  0
bnep                   20480  2
hid_multitouch         20480  0
nls_iso8859_1          16384  1
arc4                   16384  2
iwlmvm                425984  0
snd_hda_codec_hdmi     49152  1
mac80211              700416  1 iwlmvm
dell_led               16384  1
i2c_designware_platform    16384  0
i2c_designware_core    20480  1 i2c_designware_platform
snd_hda_codec_realtek    90112  1
dell_wmi               16384  0
mxm_wmi                16384  0
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
dcdbas                 16384  0
dell_smm_hwmon         16384  0
iwlwifi               315392  1 iwlmvm
snd_hda_intel          40960  3
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
rtsx_pci_ms            20480  0
memstick               20480  1 rtsx_pci_ms
cfg80211              589824  3 iwlwifi,mac80211,iwlmvm
snd_hda_core           90112  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
compat                 16384  4 cfg80211,iwlwifi,mac80211,iwlmvm
x86_pkg_temp_thermal    16384  0
coretemp               16384  0
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
aesni_intel           167936  8
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
joydev                 20480  0
input_leds             16384  0
snd                    81920  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
serio_raw              16384  0
soundcore              16384  1 snd
mei_me                 36864  0
shpchp                 36864  0
idma64                 20480  0
virt_dma               16384  1 idma64
mei                    98304  1 mei_me
processor_thermal_device    16384  0
intel_lpss_pci         16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
hci_uart               77824  0
btqca                  16384  1 hci_uart
btbcm                  16384  2 btusb,hci_uart
btintel                16384  2 btusb,hci_uart
bluetooth             520192  31 bnep,btbcm,btqca,btrtl,btusb,hci_uart,rfcomm,btintel
dell_smo8800           16384  0
intel_lpss_acpi        16384  0
wmi                    20480  3 dell_led,dell_wmi,mxm_wmi
int3403_thermal        16384  0
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
int340x_thermal_zone    16384  2 processor_thermal_device,int3403_thermal
int3400_thermal        16384  0
mac_hid                16384  0
intel_hid              16384  0
acpi_thermal_rel       16384  1 int3400_thermal
sparse_keymap          16384  2 dell_wmi,intel_hid
acpi_als               16384  0
kfifo_buf              16384  1 acpi_als
acpi_pad               24576  0
industrialio           61440  2 acpi_als,kfifo_buf
kvm_intel             172032  0
kvm                   544768  1 kvm_intel
vfio_pci               40960  0
vfio_virqfd            16384  1 vfio_pci
irqbypass              16384  2 kvm,vfio_pci
vfio_iommu_type1       20480  0
vfio                   28672  2 vfio_iommu_type1,vfio_pci
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
btrfs                 987136  0
raid10                 49152  0
raid456               110592  0
async_raid6_recov      20480  1 raid456
async_memcpy           16384  2 raid456,async_raid6_recov
async_pq               16384  2 raid456,async_raid6_recov
async_xor              16384  3 async_pq,raid456,async_raid6_recov
async_tx               16384  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
xor                    24576  2 btrfs,async_xor
raid6_pq              102400  4 async_pq,raid456,btrfs,async_raid6_recov
libcrc32c              16384  1 raid456
raid1                  36864  0
raid0                  20480  0
multipath              16384  0
linear                 16384  0
dm_mirror              24576  0
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
pci_stub               16384  0
hid_logitech_hidpp     20480  0
hid_logitech_dj        20480  0
usbhid                 49152  0
rtsx_pci_sdmmc         24576  0
i915_bpo             1302528  5
intel_ips              20480  1 i915_bpo
i2c_algo_bit           16384  1 i915_bpo
drm_kms_helper        155648  1 i915_bpo
psmouse               131072  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
ahci                   36864  2
fb_sys_fops            16384  1 drm_kms_helper
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
libahci                32768  1 ahci
drm                   364544  6 i915_bpo,drm_kms_helper
i2c_hid                20480  0
hid                   118784  6 i2c_hid,hid_multitouch,usbhid,hid_logitech_dj,hid_logitech_hidpp
pinctrl_sunrisepoint    28672  0
video                  40960  2 i915_bpo,dell_wmi
pinctrl_intel          20480  1 pinctrl_sunrisepoint

```

---

### Post by sofianito on 2017-04-19
I connected my ethernet to the cable:

```

sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 78
       serial: xx:xx:xx:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-72-generic firmware=22.361476.0 ip=192.168.1.181 latency=0 link=yes multicast=yes
       resources: irq:129 memory:edb00000-edb01fff
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: virbr0-nic
       serial: 52:54:00:a0:4c:28
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s
  *-network:1
       description: Ethernet interface
       physical id: 3
       logical name: enxd481d72f5303
       serial: yy:yy:yy:yy:yy:yy
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.08.2 duplex=full ip=192.168.1.180 link=yes multicast=yes port=MII speed=1Gbit/s

```

```

rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

```

iwconfig
lo        no wireless extensions.


virbr0    no wireless extensions.


virbr0-nic  no wireless extensions.


wlp2s0    no wireless extensions.


enxd481d72f5303  no wireless extensions.

```

---

### Post by ajgreeny on 2017-04-19
*Thread moved to **Virtualisation**.* which is more appropriate for your problem will probably be a better fit.

---

### Post by KillerKelvUK on 2017-04-19
So unless I'm misunderstanding your question I think you are using the incorrect commands to view your wired ethernet connections.  From the look of your post when you connected the cable and ran the lshw command for the 2nd time the following section appeared in the output...

```

*-network:1
       description: Ethernet interface
       physical id: 3
       logical name: enxd481d72f5303
       serial: yy:yy:yy:yy:yy:yy
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.08.2 duplex=full ip=192.168.1.180 link=yes multicast=yes port=MII speed=1Gbit/s
```

This shows your wired ethernet connection is named enxd481d72f5303 and it has an IP address of 192.168.1.180.

You then used the iwconfig command which only reports wireless devices and so enxd481d72f5303 was listed as having no wireless connections as it won't have...its wired.  To view wired you need to use ifconfig.

---

### Post by sofianito on 2017-04-19
Sorry but I am a bit confused. Do I really need to plug a cable to my ethernet in order to communicate the host with virtual machines in bridged mode?

I'm looking to write a shell script that would bridge eth0 if it is connected, else fallback using dummy module?! May be something roughly like this?:

```

sudo service network-manager stop
sudo ip link show eth0 || (sudo modprobe dummy && sudo ip link set name eth0 dev dummy0)
ip addr flush dev eth0
sudo ifconfig eth0 hw ether `genmacaddr.sh`
sudo brctl addbr vbr0
sudo brctl addif vbr0 eth0
sudo ip link set dev vbr0 up
# sudo dhclient vbr0
sudo ip addr add 192.168.10.100/24 via 192.168.10.1 dev eth0
sudo service network-manager start

```

---

### Post by KillerKelvUK on 2017-04-20
Well yes and no...depends on what you want to do, your specific use case is needed here to be certain.

So IP communications 101...you need to have both a source and destination; so your host needs an IP address as does your guest.  If you want to be able to spontaneously connect _**to**_ the guest _**from**_ the host you need a bridged network however if you just need the guest to be able to access outside networks like the internet then NAT is sufficient.

As your attempting to create a bridged network we'll stick with this example...  A bridge of the type you have created can be thought of like a network switch, not the fancy enterprise grade kind you see in big business but the dumb kind you find in home routers aka its unmanaged.  So an unmanaged switch is going to sit their and do nothing when it has no ethernet cables plugged into any of its ports.  If you then go and plug a single device like a PC into one of its ports its still going to do nothing as there are no other devices to communicate with.  However as soon as you connect a second device into another of its ethernet ports then you have the potential for network communications.  The point here is a bridge needs two connected devices which can be physical or virtual which then means you have both a source and destination.

There is no evidence from your postings so far that you have a) created a bridge (network switch) b) connect a guest to this bridge and c) added a second connection to the bridge that links it to a home network on which your host is also connected.

What is evident is that you have two physical network connections on your host, one wired and one wireless and that both are functioning and have IP addresses which are likely in the same subnet/network.

To fix a) and b) above then you need to follow 'Network Prep' section of that guide you linked as evidently you haven't populated the necessary configurations into you /etc/network/interfaces file.

Regards you scripting a fallback to a dummy interface I don't see what you are trying to achieve here so you'll need to explain more.  If you are just wanting to be able to use your virtual machine and have network access whether your host is connected via wired or wireless then this should be simple I think, you'd bridge both your wired and wireless connections into your virbr0 bridge.

---

### Post by sofianito on 2017-04-21
> **KillerKelvUK said:**
> Well yes and no...depends on what you want to do, your specific use case is needed here to be certain.

So IP communications 101...you need to have both a source and destination; so your host needs an IP address as does your guest.  If you want to be able to spontaneously connect _**to**_ the guest _**from**_ the host you need a bridged network however if you just need the guest to be able to access outside networks like the internet then NAT is sufficient.

As your attempting to create a bridged network we'll stick with this example...  A bridge of the type you have created can be thought of like a network switch, not the fancy enterprise grade kind you see in big business but the dumb kind you find in home routers aka its unmanaged.  So an unmanaged switch is going to sit their and do nothing when it has no ethernet cables plugged into any of its ports.  If you then go and plug a single device like a PC into one of its ports its still going to do nothing as there are no other devices to communicate with.  However as soon as you connect a second device into another of its ethernet ports then you have the potential for network communications.  The point here is a bridge needs two connected devices which can be physical or virtual which then means you have both a source and destination.

There is no evidence from your postings so far that you have a) created a bridge (network switch) b) connect a guest to this bridge and c) added a second connection to the bridge that links it to a home network on which your host is also connected.

What is evident is that you have two physical network connections on your host, one wired and one wireless and that both are functioning and have IP addresses which are likely in the same subnet/network.

To fix a) and b) above then you need to follow 'Network Prep' section of that guide you linked as evidently you haven't populated the necessary configurations into you /etc/network/interfaces file.

Regards you scripting a fallback to a dummy interface I don't see what you are trying to achieve here so you'll need to explain more.  If you are just wanting to be able to use your virtual machine and have network access whether your host is connected via wired or wireless then this should be simple I think, you'd bridge both your wired and wireless connections into your virbr0 bridge.

Thanks for the update.


Let me provide you a more granular context: I am using a Dell Precision 5520 laptop, and at my office we only use wireless connections, we don't have anymore ethernet cables or plugs. At home I have a router and I use sometimes the ethernet plug to speed up downloading big files.


My requirements are the following:
- I want to be able to always allow communication between host and guests uniformly at home or office whether eth0 and wlan0 are assigned an IP or not. Hence, if both eth0 and wlan0 are not connected, I still want to be able allow communication between host and guests.


- I want NetworkManager to ignore any interface that I have explicitly configured in /etc/network/interfaces, but still allows me to use NetworkManager for WiFi, Bluetooth, and VPN configuration.



According to [https://wiki.debian.org/KVM#Setting_up_bridge_networking](https://wiki.debian.org/KVM#Setting_up_bridge_networking), one may setup a macvlan bridge on top a dummy interface. I guess I would just need add the gateway:
```

modprobe dummy
ip link add dummy0 type dummy
ip link add link dummy0 eth0 type macvlan mode bridge
ifconfig dummy0 up
ifconfig eth0 192.168.10.10 broadcast 192.168.10.255 netmask 255.255.255.0 up

```

```

$ ip route show
default via 172.20.10.7 dev wlan0

```

How to forward eth0 packets to wlan0?



Does it make sense?




Here is the actual content of my /etc/network/interfaces:
```

$ cat /etc/network/interfaces

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# Set up interfaces manually, avoiding conflicts with, e.g., network manager
auto eth0 wlan0
iface eth0 inet manual

# Bridge setup
auto br0
iface br0 inet dhcp
  bridge_ports eth0
  bridge_stp off
  bridge_waitport 0
  bridge_fd 0

```


I tried to add wlan0 either in /etc/network/interfaces or manually with brctl command but I get an error:
```

sudo brctl addif br0 wlan0
can't add wlan0 to bridge br0: Operation not supported

```

According to Ubuntu wiki, most wireless devices do not support bridging (source: [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking))


```

$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
#dns=dnsmasq


[ifupdown]
managed=false

```


```

$ brctl show
bridge name    bridge id        STP enabled    interfaces
br0        8000.000000000000    no
virbr0        8000.000000000000    yes

```


```

$ ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether xx:xx:xx:xx:xx:xx brd ff:ff:ff:ff:ff:ff
3: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/ether 9a:67:1b:20:64:76 brd ff:ff:ff:ff:ff:ff
4: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default qlen 1000
    link/ether 00:00:00:00:00:00 brd ff:ff:ff:ff:ff:ff
5: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT group default qlen 1000
    link/ether 52:54:00:a0:4c:28 brd ff:ff:ff:ff:ff:ff

```


```

$ ip address show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether xx:xx:xx:xx:xx:xx brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.73/24 brd 192.168.1.255 scope global dynamic wlan0
       valid_lft 41860sec preferred_lft 41860sec
    inet6 fe80::b217:4b42:b871:8997/64 scope link
       valid_lft forever preferred_lft forever
3: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN group default qlen 1000
    link/ether 9a:67:1b:20:64:76 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::9867:1bff:fe20:6476/64 scope link
       valid_lft forever preferred_lft forever
4: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 00:00:00:00:00:00 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
5: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 52:54:00:a0:4c:28 brd ff:ff:ff:ff:ff:ff

```


```

$ ifconfig -a
br0       Link encap:Ethernet  HWaddr 9a:67:1b:20:64:76
          inet6 addr: fe80::9867:1bff:fe20:6476/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:9780 (9.7 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1041 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:77336 (77.3 KB)  TX bytes:77336 (77.3 KB)


virbr0    Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


virbr0-nic Link encap:Ethernet  HWaddr 52:54:00:a0:4c:28
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:192.168.1.73  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::b217:4b42:b871:8997/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6628 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5302573 (5.3 MB)  TX bytes:1263463 (1.2 MB)

```

---

### Post by KillerKelvUK on 2017-04-21
Okay so specific requirements then!

So I wasn't aware of the restriction on wifi drivers and bridging sorry, I've never had a practical use case so I made an incorrect assumption obviously.  The articles stating this do look dated so if you haven't already tried it I'd suggest you give it a go as you may get luck, if not then NAT is your only route here as this does work with qemu guests and reading your posts it may just been you don't need anything other than NAT?  Another note is that bridging can be setup using Network Manager, this maybe the only way to go for your wifi adapter if that does work at all, but as I think you understand, if you configure a network adapter from /etc/network/interface then using Network Manager isn't possible and vice versa.

Regards your requirement, there are a couple of routes (pun intended) you could take, you can do host to guest communication without IP e.g. unix sockets using qemu guest agents/tools and I think virsh will give you console access via a unix socket.  I realise you have explicitly said IP communications so I just offer these in case you haven't thought of them.

Regards IP comms, your desire to have this "fallback" approach for me is a little over-complicated...have you considered two separate IP networks for your guests, one for management which is permanently in place on a separate subnet and then a second network that is via the bridge which will give outside world network access only if your bridge is connected?  I've just tested this myself and it was pretty straight forward...

[LIST]
[*]Ensure the dummy network module is loaded at boot time on your host by adding in a new line "dummy" into /etc/modules
[*]Add the dummy0 network adaptor configuration in your hosts /etc/network/interfaces
[LIST]
[*]define the interface with "auto dummy0"
[*]set the interface configuration to manual with "iface dummy0 inet manual"
[*]create the management bridge with "auto mgtbr0 \n address x.x.x.x \n netmask x.x.x.x etc \n bridge_ports dummy0"
[*]create the internet bridge with "auto intbr0 \n xxx etc \n bridge_ports xxx"
[/LIST]

[*]Then configure your guest to have two network interfaces, one bridged to mgtbr0 and the other bridge to intbr0.
[*]Id suggest you use static addressing with mgtbr0 and then the intbr0 can be assigned by DHCP.
[/LIST]

So this way you now have a permanent management network between host and guest(s) regardless of whether your host is connected to an outside network or not.

**EDIT:**

Your attempt to bridge the wifi network is flawed I believe as you are using Network Manager to connect it to a wifi network but then are trying to manually add the interface to a bridge using brctl.  I believe you'd need to exclusively use Network Manager or the init scripts to test this properly.

---

### Post by efflandt on 2017-04-22
I am not familiar with KVM, but it looks like what you are trying to do would be much easier using virtualbox which has a drop down list for network settings which by default I think is "NAT", but can easily be switched to "Bridged Network" even to a wireless device.

On the guest (DHCP IP assigned by DSL gateway):```
efflandt@vb1604-32:~$ ifconfig
enp0s3    Link encap:Ethernet  HWaddr 08:00:27:5a:02:b3  
          inet addr:172.16.0.145  Bcast:172.16.0.255  Mask:255.255.255.0
          inet6 addr: fe80::af77:4c1e:6164:5aab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4482 (4.4 KB)  TX bytes:9790 (9.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:2440 (2.4 KB)  TX bytes:2440 (2.4 KB)

efflandt@vb1604-32:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.16.0.254    0.0.0.0         UG    100    0        0 enp0s3
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s3
172.16.0.0      0.0.0.0         255.255.255.0   U     100    0        0 enp0s3

efflandt@vb1604-32:~$ ping -c4 172.16.0.55
PING 172.16.0.55 (172.16.0.55) 56(84) bytes of data.
64 bytes from 172.16.0.55: icmp_seq=1 ttl=64 time=0.783 ms
64 bytes from 172.16.0.55: icmp_seq=2 ttl=64 time=0.217 ms
64 bytes from 172.16.0.55: icmp_seq=3 ttl=64 time=0.208 ms
64 bytes from 172.16.0.55: icmp_seq=4 ttl=64 time=0.273 ms

--- 172.16.0.55 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 0.208/0.370/0.783/0.239 ms
```On the host (static IP). Note that guest IP does not even show on host (except arp cache), but is reachable:```
efflandt@msata512-1610:~$ ifconfig
enp5s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether a4:ba:db:f8:d5:a1  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 17  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 5018901  bytes 339374855 (339.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5018901  bytes 339374855 (339.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.16.0.55  netmask 255.255.255.0  broadcast 172.16.0.255
        inet6 fe80::3351:5235:e6f9:97d7  prefixlen 64  scopeid 0x20<link>
        ether 78:e4:00:26:b8:ac  txqueuelen 1000  (Ethernet)
        RX packets 29327255  bytes 28771644658 (28.7 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 23743868  bytes 7143611581 (7.1 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

efflandt@msata512-1610:~$ ping -c4 172.16.0.145
PING 172.16.0.145 (172.16.0.145) 56(84) bytes of data.
64 bytes from 172.16.0.145: icmp_seq=1 ttl=64 time=0.347 ms
64 bytes from 172.16.0.145: icmp_seq=2 ttl=64 time=0.341 ms
64 bytes from 172.16.0.145: icmp_seq=3 ttl=64 time=0.410 ms
64 bytes from 172.16.0.145: icmp_seq=4 ttl=64 time=0.370 ms

--- 172.16.0.145 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3049ms
rtt min/avg/max/mdev = 0.341/0.367/0.410/0.027 ms

efflandt@msata512-1610:~$ arp -a
unknown0021b7c8a365.domain_not_set.invalid (172.16.0.60) at 00:21:b7:c8:a3:65 [ether] on wlp4s0
dsldevice.domain_not_set.invalid (172.16.0.254) at 00:26:42:82:fe:b0 [ether] on wlp4s0
unknown78e40026b8ac.domain_not_set.invalid (172.16.0.145) at 08:00:27:5a:02:b3 [ether] on wlp4s0
LexmarkC543.domain_not_set.invalid (172.16.0.69) at 00:21:b7:00:9d:a6 [ether] on wlp4s0
```

---

