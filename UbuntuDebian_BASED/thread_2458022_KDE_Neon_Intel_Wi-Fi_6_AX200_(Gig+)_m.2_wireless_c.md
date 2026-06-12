---
title: "KDE Neon: Intel Wi-Fi 6 AX200 (Gig+) m.2 wireless card not working"
date: 2021-02-14
forum: Ubuntu/Debian BASED
---

### Post by gus_zernial on 2021-02-14
I have and AMD X570 mobo, AMD 5600X CPU, an installed Intel Wi-Fi 6 AX200 (Gig+) m.2 wireless card, and the KDE neon-user-20210211-0944 distribution. Wired ethernet works, and the wireless card also works on Win10, but wireless does not work on linux/neon.

I did:

% sudo apt install backport-iwlwifi-dkms
... and... 
% git clone [https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git](https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git)
.... and put the .ucode files in /lib/firmware

KDE Neon comes with kernel 5.4.0-65-generic, and I tried with that and with upgrade kernel 5.8.0-43-generic. Neither worked.

Appreciate response as to "should it work", and if so what should I do to further diagnose and/or fix.

See outputs below:

% sudo lshw -C network
*-network                 
       description: Ethernet interface
       product: I211 Gigabit Network Connection
       vendor: Intel Corporation
       ..........
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.6.0-k duplex=full firmware=0. 4-1 ip=192.168.1.18 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:37 memory:fc600000-fc61ffff ioport:f000(size=32) memory:fc620000-fc623ff
       
% sudo lspci -nnk | grep -i intel
05:00.0 Ethernet controller [0200]: Intel Corporation I211 Gigabit Network Connection [8086:1539] (rev 03)
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_inteHere's some outputs:l
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
        
(ie. wired interface is present *but not* wireless)  

% modinfo iwlwifi | grep iwlwifi-cc
firmware:       iwlwifi-cc-a0-56.ucode

(iwlwifi-cc microcode is in /lib/firmware as versions 55 and 59, but not version 56)

% journalctl | grep iwl
Feb 14 10:19:58 Jboat18 kernel: Loading modules backported from iwlwifi
Feb 14 10:19:58 Jboat18 kernel: iwlwifi-stack-public:master:9022:a34beadd
Feb 14 10:19:58 Jboat18 systemd-modules-load[431]: Inserted module 'iwlwifi'

% lsmod | grep iwl
iwlwifi               352256  0
cfg80211              778240  1 iwlwifi

---

### Post by howefield on 2021-02-14
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by gus_zernial on 2021-02-18
After working on my iwlwifi problem for days, the solution below worked for me. Context .... while my system is now running linux KDE Neon, it had previously run Windows 10, and AX200 wifi worked on that. After installing linux, I created a bootable "Win2go" USB flash drive, and booted off that several times just to make sure the AX200 was still working. I never cease to be amazed at how Windows can screw up a system. 

Error message on linux:
iwlwifi: probe of XXXX:YY:ZZ.n failed with error -110

Solution:
[https://askubuntu.com/questions/1083369/ubuntu-18-04-cannot-recognized-intel-wireless-ac-9260](https://askubuntu.com/questions/1083369/ubuntu-18-04-cannot-recognized-intel-wireless-ac-9260)

.....................
"It is a problem with fast startup mode of Windows. I think because in that mode, Windows keeps the wireless adapter for itself when shut down. hence Linux cannot detect it.

Just go into Settings > Power & Sleep > Choose what power button does > Shut down setting > uncheck the Turn on fast startup > save change and it will work."

It might be a good idea for Intel to put this in their linux Wifi Troubleshooting guide.

---

