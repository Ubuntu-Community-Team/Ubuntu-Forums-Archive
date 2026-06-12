---
title: "Xen 4.4 - AMD A8-5600K PCI PASSTHROUGH"
date: 2014-04-24
forum: Virtualisation
---

### Post by tuxinteger on 2014-04-24
[INDENT]Updates : 
--------------

[LIST=1]
[*=1] Xen  Kernel Crashes preceding Hard Lockup on 3.19.0-24 & 26   -------------- Workaround i found is to run firefox with nicer   scheduling - script nice -n8 /usr/bin/firefox 
[*=1]See grub config updates regards line change iommu=pt iommu=1 
[*=1]Add that the following makes the ati passthrough more stable /reliable on reboot. 
[*=1] Ram size in the Domu set to no more than 6098 Mb The memory speed in your bios to 1333Mhz. 
[*=1]Maybe the fx chipset emulation is the limitation,can we have options for amd chipsets ?. 
[*=1]Although  the memory paging issue seems to be with the ati driver,as  when  setting the driver. the ati driver is seems to have issues paging  and  screen endpoint detection and unable to sync the screen. : 
[*=1]When  the driver is set at default win display adapter the ram size  doesnt  seem an issue,still working on  the  driver mod to change the  paging on  first boot.    :  This issue occurs when the domu memory for a  win8  machine is set above 6098Mb and the ati driver is installed.  
[/LIST]


My experience with Xen and the Asrock FM2A88M Extreme 4+ with the AMD a8-5600k processor.
--------------------------------------------------------------------------------------------------------------------------------------------

After many different tries with xen 4.1-3 and HVM i finally found a solution that works and restarts without windows bsod errors or crashes.

Hardware :

Asrock FM2A88M Extreme 4+
AMD A8-5600K
16 Gb ddr3 ram.

Nvidia Quadro fx570 -pcie - 1st Slot and selected as primary.
AMD HD6950 - 2nd Pcie slot.

14.04 LTS 
Kernel : 3.13.0-19 Saucy Ubuntu - XEN Distribution 4.4 - AMDx64 
* Kernel : 3.13.0-24 & .26 Failing with lock-ups on Xen hypervisor , Page Map Kernel Warnings and Panics.
NON -UEFI Kernel 

Bios Config items ;

Onboard Video (APU) is disabled at present,it has been enabled and does work but radeon blacklisting confuses the issue.
Bios - Version 2.00 January 2014,although i did let Asrock know of the ioapic issue in the bios tables,they seem content with
using redirects for this.


Mainboard bios settings have the onboard coms ports and onboard video disabled,the coms ports are disabled as the local apic 0x05
is not defined and the only work around as you can see by the iovrs redirect in the grub cli below,0x05 being the com port1 on the 
mainboard with its parent id being the pci-isa bridge port.


Asrock ; 

Communications with Asrock have been fruitful ,thankyou Asrock for your support and test bioses ,most of their boards work with Vt-d and IOMMU
,and they are very keen to help.



1 -

Basic Xen install of Xen Hypervisor AMD 64 via sudo apt-get,along with xen tools and qemu.

2 -

I use the pciback script to attached the pci devices in /etc/xen/pciback.conf to the hvm.

pciback.conf

0000:00:01.0 # apu
0000:00:01.1 # apu sound
0000:02:00.0
0000:02:00.1
#
0000:00:13.0 # USB and sound
0000:00:10.1
0000:00:10.0
0000:00:14.2


3-

I use the /etc/initramfs/modules method of hiding the devices via the xen-pciback module,config is shown below and not hide or 
enable the module in the grub config for xen.

/etc/initramfs/modules ; Hiding both the hd6950 and the onboard apu adapter.

xen-pciback passthrough=1 hide=(02:00.0)(02:00.1)(00:01.1)(00:01.0)

update-initramfs -k all -c after modify this file ,update-grub and reboot.


3-

I did'nt use an LVM or PV as this is HVM combined with PV thanks to the dev team ,and i created a boot image using dd and specified
that in the hvm.cfg file shown below.

Show here is the important parts of /etc/xen/hvm.cfg using the xl toolstack ,as xm and 4.3 worked well with the network manager 
on the host.

device_model_version="qemu-xen-traditional"
builder = "hvm"
name = 'vm1'
viridian = 1
# hpet=1 # stabilises the amd vm, not req on xeon intel with asrock extreme 6 -for some reason,bios ? ,# removed 
serial='pty'
# pci_msitranslate= 1 - affects performance -removed.
monitor=1
on_xend_stop="shutdown"
on_poweroff = "destroy"
on_reboot = "restart"
on_crash = "restart"
usb = 1
usbdevice= "tablet"
sdl = 0
vnc = 1
vncunused = 1
keymap= "en-us"
memory = "6098"
gfx_passthru = 0 # not boot secondary hd6950 using quadro fx to be tested using apu gpu 
stvga = 0
vcpus = "4" # works best at 4 cores virtual 
pae = 1 # doesnt affect w7 
acpi = 1
apic = 1
disk = ['file:/yourdrive/vm1.img,hda,w' , 'phy:/dev/cdrom,hdc:cdrom,r' ] # image created using dd and mkdosfs tools.
# vif = ['type=ioemu'] # removed as affects xen pci 
vif = [ 'bridge=xenbr0,mac=00:16:3E:69:7f:02,type=ioemu,mo del=e1000' ]
pci=[ '02:00.0', '02:00.1', '00:10.1', '00:10.0', '00:14.2', '00:13.0' ]
xen_platform_pci = '1' # i have changed this to enable (1)
pci_power_mgmt = '1' # i have changed this to enable (1)

4-

Networking in Xen 4.4 required the manual set-up w/o network manager as since 4.3 and xm tools it is broken ,as far as the xen
bridge dhcp is concerned,this could be issues with nm security ? ,but this was a headache trying to play with nm and bridges,so
out the window went the nm method and the old manual methods that work ok.

DOM0 Setup ,the guest will need a manual network config unless you wish to allow it obtain a dhcp address from a router on your network.

Setup in /etc/network/interfaces ;

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo xenbr0
iface lo inet loopback
allow-hotplug eth0
allow-hotplug eth1
iface eth0 inet static
iface eth1 inet static
iface xenbr0 inet static
bridge_ports eth0
bridge_ports eth1
address 192.168.0.1 # IP of Linux Mint dom0
broadcast 192.168.0.255
netmask 255.255.255.0
gateway 192.168.0.# # IP of router or modem
dns-nameservers 192.168.#.# # IP(s) of DNS name server(s)
bridge_stp off # disable Spanning Tree Protocol - optional

Setup in /etc/rc.local ;

/sbin/ifconfig xenbr0 192.168.0.1
/sbin/route add default gw 192.168.0.2
/bin/cp /myresolv.conf /etc/ # also crontab if you are using wireless 


4 - Grub Config - /etc/default/grub

GRUB_DEFAULT="Xen 4.4-amd64"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
#
GRUB_CMDLINE_LINUX_DEFAULT="radeon.blacklist=1"
#
# GRUB_CMDLINE_LINUX=""
# removed iommu=soft # 1062014 replaced with iommu=pt iommu=1
# 
GRUB_CMDLINE_XEN=" iommu=pt iommu=1 swiotlb=force watchdog radeon.blacklist=1 e820-mtrr-clip=false extra_guest_irqs=,18 lapic x2apic=false irqpoll amd_iommu_dump debug,verbose loglvl=all guest_loglvl=all apic_verbosity=debug e820-verbose=true ivrs_ioapic[5]=00:14.0"
# 
# cpufreq=xen[IMG]http://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA8AAAAPCAMAAAAMCGV4AAAAM1BMVEUAAAAzMzNFRUX/AAD nQD/tAD/ywD/5QD/6gD//RP//pP//8f// v////8A/sAAAD////W0mJCAAAAD3RSTlP//////////////////wDU3JihAAAAZklEQVR4nFWPUQ6AIAxDx9Q6wHj/49o2aOL7gddlbMQtUvgWtmuOASd0Wu9VhT3lOUcENUIBfahoQM9Jdd0d4fLrh7w 7L3a0mYHX16o/1awiQA8DziTytPzFSCXrv0Psr/7//73AALkBhZUoxNsAAAAAElFTkSuQmCC[/IMG]erformance # removed 
The key points in the stability of the guest was the grub config using soft options ,as the iommu=1 was causing instability in the
host and guest acpi with shown in the /var/log/xen logs for the guest.

The instability is probably related to the guest ATI drivers and hardware /acpi calls -BSOD fun # ,as the io ranges that are in the
bsod are the memory ranges of both the pcie bridge and the shared by the pcie adapter in the host and 
guest - ffff8803e8d2209c ffff880405e03e08 ffffffff81715a64 ffff8803e8d22000,irqpolling does nothing ,kvm bios needs irq alignment.

It could be noted also that the win guest doesnt /wouldn't align irq18 correctly ,nor does xen as shown by the stack call issues on
shutdown - This was using HVM access not the iommu=soft .

Logs ; 

* using iommu=1 ,NOT recommended on this hardware ,the following kernel trace came from a dirty domain U destroy after the at issue was occurring
- information only ,see win fixes below .

kernel: [ 8247.094982] irq 18: nobody cared (try booting with the "irqpoll" option)
kernel: [ 8247.094995] CPU: 0 PID: 0 Como: swapper/0 Not tainted 3.13.0-24-generic #46-Ubuntu
kernel: [ 8247.095000] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./FM2A88M Extreme4+, BIOS P2.00 01/17/2014
kernel: [ 8247.095004] ffff8803e8d2209c ffff880405e03e08 ffffffff81715a64 ffff8803e8d22000
kernel: [ 8247.095013] ffff880405e03e30 ffffffff810c19d2 ffff8803e8d22000 0000000000000012


* The above issue does not occur with the grub options for iommu=soft and swiotlb=force ,i have changed this to iommu=pv


3-

The normal update-grub is required.

4-

Grub set-up was interesting as unlike the Intel Vt-d setup i have on another asrock mainboard the AMD board has an ioapic issues
with com 1 ( ioapic 0x05 ) .This bug in the bios is shown in xl dmesg with a standard xen grub w/o the redirection of the 0x05 apic back to 
the pci-isa bridge.

5- 

This setup runs pci passthrough successfully with the latest AMD drivers on a w7 guest,drivers only not ccc,which requires a 
manual extract of the package utilising 7zip or archiver.


6- 

Updates i think would benefit users & admins in Xen future releases ;

Ability to define and reserve the irq for pci passthough and memory addresses in the pv /hvm config file .
Ability to configure the qemu /pv bios for various settings related to pcie lane control /gen.
Win8 compatibility ,this isn't working as yet.
AMD chipset option in the HVM as there seems to be some issues with the AMD machines.
Change vm shadow ,cache and bios settings /variables via the config ?.

--------------------------------------------------------------------------------------------------------------------------------------------------------------

7- Updated - ATI BSOD FIX 

Sorry forgot to include my workaround for the bsod caused by the amdkmdag.sys driver loading early with two adapters
and the ati cards ability to search for crossfire pairs on boot prior to loading the first screen,which is what passthrough 
card seems to be doing via debugging ,although i didnt have these on a predictable basis on boot only.

Win reliability - BSOD atikdag.sys & atikmpag.sys issues.:
---------------------------------------------------------------------------------------------------------------------------------------------------------------

a- The workaround i used for this is to enable the hidden device ( amdkmdag.sys) ( non -pnp driver) ,see this in the device manager
after showing hidden devices,this can be done via the registry in win8.

This must be modified to start after the ati device has detected and rendered,to do this the following steps must be carried out.

b- Backup your registry and create a restore point.

c- The registry keys /HKEY_LOCAL_MACHINE\SYSTEM\CONTROLSET001\SERVICES\A MDKMDAG Start option to be changed from 
the existing demand startup parameter to the automatic startup requirement,this is done by changed the Start hex value from 3 to the value of 2.
The integer values are 0=boot ( good for testing and other debuggin-in win),1=system,2=auto,3 =demand,and 4 =disabled. 

d- Also change the ULPS function EnableULPS from 1 to 0 .

e- The hidden device in device manager should now show it start point as automatic and not on demand,as it will demand this too early with no screen.

f- Install KB2584454 for win7 as this provides even more stability with the 14.4 drivers ! ,without the ccc ,i havent 
bothered with this as it predominantely caused bsod's in the past.

# Update ; See update below on working solution below for the eyefinity & ccc for AMD Driver Version - 13.9 Win64 Bit WHQL
from AMD site.


g- # Updated , go to services and set the AMD external events ( atiesrxx) to manual start.

h - Shutdown or Reboot the xen Domu to test,if you havent restarted the host machine its best to do so after shutting down the guest.

i - Sometimes the HD6950 card has poor performance,using the eject method on the taskbar corrects this,verified by testing before and after -ptest
fps without actaully running the full ptest suite,this is not predicatable or able to be seen via xl utils and the perf reduction is random so i eject the 
card before using 3D.

j - Updated Dom-0 config see above.

k- Eyefinity Install without the Catalyst full install ,the way around the BSOD CCC Install - (1) Extract driver package as per Step (5) prior ,go to the extracted package
OUTDIR/Packages/Apps/CCC2. (2) Install the ccc-mom-installproxy.msi manually . (3) Go to the same CCC2 directory -Install ccc-core-static.msi.
You should now have the Catalyst Control Centre avaialble ,go to preferences and set to advanced to Setup Multiple Monitors.

This was the only way to get multiple monitors working on the Xen W7 guest ,works great.
AMD Driver Version - 13.9 Win64 Bit WHQL from AMD site.


Updates : 
#######################

Kernel 3.13.0-24 Issues as below

Kernel 3.13.0-26 Has Major Issues with page mapping and kernel warnings ,hard lockups ,i have regressed to 3.13.0-24 or 3.13.0-19 as time prevents
tracing the new kernel issues with the firmware updates in the latest 2 updates,there may be a workaround .

See above Xen guest Catalyst Manual Install to avoid the hardware detection which causes the BSOD when using the full compressed utility from AMD.

To Do ; 

I might get to test later the upstream kernel which may have fixed these issues !.
Enable APU 
Have Win8 working properly as this is generally a better platform .



Not too much !.
;).



Thankyou Xen team ! .

& References ; Thankyou Powerhouse ,very helpful .

[http://wiki.xen.org/](http://wiki.xen.org/) 
[http://old-list-archives.xenproject..../msg00464.html]("http://old-list-archives.xenproject.org/archives/html/xen-devel/2011-01/msg00464.html")
[http://wiki.xen.org/wiki/Xen_PCI_Pas...in_xen-pciback]("http://wiki.xen.org/wiki/Xen_PCI_Passthrough#Static_assignment_for_built-in_xen-pciback")
[http://forums.linuxmint.com/viewtopic.php?f=42&t=133089](http://forums.linuxmint.com/viewtopic.php?f=42&t=133089). Enjoy!
[http://www.overclock.net/t/1205216/g...#post_19572876]("http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/550#post_19572876").
[http://forums.linuxmint.com/viewtopic.php?f=29&t=112951](http://forums.linuxmint.com/viewtopic.php?f=29&t=112951)


[/INDENT]

---

### Post by tuxinteger on 2014-12-29
1- Add that the following makes the ati passthrough more stable /reliable on reboot.   

2- Ram size in the Domu set to no more than 6098 Mb The memory speed in your bios to 1333Mhz.        

3- Maybe the fx chipset emulation is the limitation,can we have options for amd chipsets ?.    

4- Although the memory paging issue seems to be with the ati driver,as when setting the driver. the ati driver is seems to have issues paging and screen endpoint detection and unable to sync the screen. :  

5- When the driver is set at default win display adapter the ram size doesnt seem an issue,still working on  the  driver mod to change the paging on first boot.    :  This issue occurs when the domu memory for a win8 machine is set above 6098Mb and the ati driver is installed.    :  HTH



[http://wiki.xen.org/](http://wiki.xen.org/) 
[http://old-list-archives.xenproject.org/archives/html/xen-devel/2011-01/msg00464.html](http://old-list-archives.xenproject.org/archives/html/xen-devel/2011-01/msg00464.html)
[http://wiki.xen.org/wiki/Xen_PCI_Passthrough#Static_assignment_for_built-in_xen-pciback](http://wiki.xen.org/wiki/Xen_PCI_Passthrough#Static_assignment_for_built-in_xen-pciback)
[http://forums.linuxmint.com/viewtopic.php?f=42&t=133089](http://forums.linuxmint.com/viewtopic.php?f=42&t=133089). Enjoy!
[http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/550#post_19572876](http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/550#post_19572876).
[http://forums.linuxmint.com/viewtopic.php?f=29&t=112951](http://forums.linuxmint.com/viewtopic.php?f=29&t=112951)

---

### Post by tuxinteger on 2014-12-29
iommu=pv

---

### Post by tuxinteger on 2014-12-29
Also using on a FX8350 -Asrock 970 extreme ,video work and some steam games ,including opengl,arma3 and direct compute functions are faster than win8.1 native !.
16Gb ddr3,amd r9-280x 3Gb.

win8.1 : # Current xen guest config works w/o fail on ati drivers if memory is at 6098Gb or lower and ram at 1333Mhz.

# No Hap
device_model_version="qemu-xen-traditional"
builder = "hvm"
# hap=0
latency=0
cpu_weight= "512"
name = 'win8'
memory = "6098"
vcpus = "4"  #have 8 specified here on the fx8350 which is more stable than 4,you can still run other guests in the host cpu pool (which is 8 on the fx8350 and 4 on the A8)
# changing below conflicts if win is activated
vif = ['type=ioemu']
viridian = '1'
serial='pty'
gfx_passthru = 0
opengl = 1
stdvga = 0
acpi = 1
apic = 1
localtime = 0
localdate = 0
on_xend_stop="shutdown"
on_poweroff = "destroy"
on_reboot = "restart"
on_crash = "restart" 
usb = 1 
usbdevice= "tablet" 
sdl = 0 
vnc = 1 
vncunused = 1 
keymap= "en-us" 
xen_platform_pci = '1' pci_power_mgmt = '1' 
# pci_msitranslate= 1 
# monitor=1 
disk = ['file:/media/me/ 200GB /win8_260g.img,hda,w' , 'phy:/dev/cdrom,hdc:cdrom,r' ] 
# for new drive imaging and backup # disk = ['file:/media/me/500GBSATA/win8new.img,hda,w' , 'file:/media/me/300GBSATA/# # win8new.img,hda2,w' , 'phy:/dev/cdrom,hdc:cdrom,r' ] 
# boot = "c" 
# boot = "dc" vif = [ 'bridge=xenbr0,mac=00:16:3E:69:7f:02,model=e1000' ] 
parallel = "none" 
serial = "pty" 
# below req for r9280x permissives can be removed for APU on the A8
pci=[ '01:00.0,permissive=1', '01:00.1,permissive=1', '04:00.0', '00:12.2,permissive=1', '00:14.2', '00:12.0,permissive=1' ]


References ; Thankyou Powerhouse ,very helpful .

[http://wiki.xen.org/](http://wiki.xen.org/) 
[http://old-list-archives.xenproject.org/archives/html/xen-devel/2011-01/msg00464.html](http://old-list-archives.xenproject.org/archives/html/xen-devel/2011-01/msg00464.html)
[http://wiki.xen.org/wiki/Xen_PCI_Passthrough#Static_assignment_for_built-in_xen-pciback](http://wiki.xen.org/wiki/Xen_PCI_Passthrough#Static_assignment_for_built-in_xen-pciback)
[http://forums.linuxmint.com/viewtopic.php?f=42&t=133089](http://forums.linuxmint.com/viewtopic.php?f=42&t=133089). Enjoy!
[http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/550#post_19572876](http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/550#post_19572876).
[http://forums.linuxmint.com/viewtopic.php?f=29&t=112951](http://forums.linuxmint.com/viewtopic.php?f=29&t=112951)

---

### Post by tuxinteger on 2015-01-04
With the R9-280x i found that  reducing video card memory clock  to 1400 Mhz from 1550Mhz (std) also helps mitigate the atikmdag and driver issues.

---

