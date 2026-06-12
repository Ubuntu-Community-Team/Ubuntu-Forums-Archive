---
title: "Lost all sound support - how to restore everything"
date: 2013-09-20
forum: Ubuntu Studio
---

### Post by James_Schrage on 2013-09-20
I'm not sure what I did, but I have lost all my sound support in Ubuntu_Studio.  
After I installed initially, I was using my Logitech headphones (G430) on a USB port,
now that doesnt work either.
I am running 13.04 and I am not even seeing a speaker icon on the top panel.
I've tried a zillion things but nothing have seems to have helped so far.

Motherboard is an Asus Z87A with 8GB of memory.  There is an on-board
which does not appear to be detected:
Realtek audio device: Realtek ALC892 8-Channel High Definition Audio CODEC 
- Supports : Jack-detection, Multi-streaming, Front Panel Jack-retasking
with audio feature :
- Absolute Pitch 192kHz/ 24-bit True BD Lossless Sound
- DTS Ultra PC II
- DTS Connect
- Optical S/PDIF out port(s) at back panel
- BD Audio Layer Content Protection

aplay -l
---------------------------------------------------------------------------------
aplay: device_list:252: no soundcards found...

speaker-test -c 2
------------------------------------------------------------------------------
speaker-test 1.0.25

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
Playback open error: -2,No such file or directory

sudo lshw
---------------------------------------------------------------------------------- 
    description: Desktop Computer
    product: All Series (All)
    vendor: ASUS
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=desktop family=ASUS MB frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=All uuid=80D91A2C-DAD7-DD11-997C-74D02B960974
  *-core
       description: Motherboard
       product: Z87-A
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev 1.xx
       serial: 130612942000173
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1007
          date: 05/17/2013
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-memory:0 UNCLAIMED
          physical id: 1
        *-bank UNCLAIMED
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 0
             serial: [Empty]
             slot: ChannelA-DIMM0
     *-memory:1
          description: System Memory
          physical id: 46
          slot: System board or motherboard
        *-bank:0
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: CMX8GX3M1A1600C11
             vendor: AMI
             physical id: 0
             serial: 00000000
             slot: ChannelA-DIMM1
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [Empty]
             slot: ChannelB-DIMM0
        *-bank:2
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 2
             serial: [Empty]
             slot: ChannelB-DIMM1
     *-cache:0
          description: L1 cache
          physical id: 4c
          slot: CPU Internal L1
          size: 256KiB
          capacity: 256KiB
          capabilities: internal write-back
     *-cache:1
          description: L2 cache
          physical id: 4d
          slot: CPU Internal L2
          size: 1MiB
          capacity: 1MiB
          capabilities: internal write-back unified
     *-cache:2
          description: L3 cache
          physical id: 4e
          slot: CPU Internal L3
          size: 6MiB
          capacity: 6MiB
          capabilities: internal write-back unified
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-4670K CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 52
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-4670K CPU @ 3.40GHz
          slot: SOCKET 1150
          size: 800MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid cpufreq
          configuration: cores=4 enabledcores=4 threads=4
     *-memory:2 UNCLAIMED
          physical id: 2
     *-memory:3 UNCLAIMED
          physical id: 3
     *-pci
          description: Host bridge
          product: Haswell DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Haswell PCI Express x16 Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:f6000000-f70fffff ioport:e0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GK107 [GeForce GTX 650]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
           *-multimedia UNCLAIMED
                description: Audio device
                product: GK107 HDMI Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:f7080000-f7083fff
        *-usb:0
             description: USB controller
             product: Lynx Point USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:41 memory:f7200000-f720ffff
        *-communication
             description: Communication controller
             product: Lynx Point MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:44 memory:f721a000-f721a00f
        *-usb:1
             description: USB controller
             product: Lynx Point USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:f7218000-f72183ff
        *-multimedia UNCLAIMED
             description: Audio device
             product: Lynx Point High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: latency=0
             resources: memory:f7210000-f7213fff
        *-pci:1
             description: PCI bridge
             product: Lynx Point PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:f2200000-f23fffff ioport:f2400000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: Lynx Point PCI Express Root Port #3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:d000(size=4096) memory:f7100000-f71fffff ioport:f2100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168 PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 11
                serial: 74:d0:2b:96:09:74
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-1_0.0.3 10/23/12 ip=192.168.1.115 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:42 ioport:d000(size=256) memory:f7100000-f7100fff memory:f2100000-f2103fff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm subtractive_decode bus_master cap_list
           *-pci
                description: PCI bridge
                product: ASM1083/1085 PCIe to PCI Bridge
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pci subtractive_decode bus_master cap_list
                resources: iomemory:202001f10-202001f0f
        *-usb:2
             description: USB controller
             product: Lynx Point USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7217000-f72173ff
        *-isa
             description: ISA bridge
             product: Lynx Point LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: Lynx Point 6-port SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:f7216000-f72167ff
        *-serial UNCLAIMED
             description: SMBus
             product: Lynx Point SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7215000-f72150ff ioport:f000(size=32)
     *-scsi:0
          physical id: 4
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10EZEX-00R
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 80.0
             serial: WD-WCC1S4354748
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=000559a4
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 7cdb-3190
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2013-08-13 00:59:13 filesystem=ntfs label=System Reserved state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: 5443ab1d-624e-0543-baf1-bf7f1e9febf0
                size: 453GiB
                capacity: 454GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2013-08-13 00:59:47 filesystem=ntfs label=Windows 7 state=clean
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                size: 477GiB
                capacity: 477GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 469GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 8129MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 5
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DRW-24B1ST   c
             vendor: ASUS
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.05
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh

lspci
---------------------------------------------------------------------------------
00:00.0 Host bridge: Intel Corporation Haswell DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Haswell PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation Lynx Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Lynx Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point PCI Express Root Port #1 (rev d4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point PCI Express Root Port #3 (rev d4)
00:1c.6 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1d.0 USB controller: Intel Corporation Lynx Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GTX 650] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 11)
04:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03)

lsmod
---------------------------------------------------------------------------------
Module                  Size  Used by
nfnetlink_log          17816  0 
nfnetlink              14406  1 nfnetlink_log
nvram                  14362  0 
snd                    69496  0 
soundcore              12680  1 snd
joydev                 17377  0 
coretemp               13355  0 
kvm                   443215  0 
parport_pc             28152  0 
ppdev                  17073  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55440  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
bnep                   18036  2 
rfcomm                 38545  0 
bluetooth             232544  10 bnep,rfcomm
nouveau               943184  2 
ttm                    83187  1 nouveau
eeepc_wmi              13151  0 
asus_wmi               24213  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
drm_kms_helper         49394  1 nouveau
video                  19390  2 nouveau,asus_wmi
drm                   277836  4 ttm,drm_kms_helper,nouveau
mxm_wmi                13021  1 nouveau
psmouse                95905  0 
lpc_ich                17061  0 
wmi                    19070  3 mxm_wmi,nouveau,asus_wmi
serio_raw              13215  0 
mac_hid                13205  0 
mei                    41158  0 
i2c_algo_bit           13413  1 nouveau
dm_multipath           22843  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
binfmt_misc            17500  1 
microcode              22881  0 
scsi_dh                14843  1 dm_multipath
btrfs                 781743  0 
zlib_deflate           26885  1 btrfs
libcrc32c              12615  1 btrfs
hid_microsoft          12798  0 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  3 hid_generic,hid_microsoft,usbhid
raid10                 48081  0 
raid456                65798  0 
async_raid6_recov      12795  1 raid456
async_memcpy           12529  1 raid456
async_pq               12912  1 raid456
async_xor              12777  2 async_pq,raid456
async_tx               13291  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
raid6_pq              101908  2 async_pq,async_raid6_recov
raid1                  35316  0 
ahci                   25731  2 
raid0                  17159  0 
libahci                31364  1 ahci
multipath              13145  0 
r8169                  67466  0 
linear                 12894  0 
dm_raid45              76725  0 
xor                    17116  2 async_xor,dm_raid45
dm_mirror              21900  0 
dm_region_hash         20820  1 dm_mirror
dm_log                 18529  3 dm_region_hash,dm_mirror,dm_raid45

---

