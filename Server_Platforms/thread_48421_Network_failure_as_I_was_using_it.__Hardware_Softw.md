---
title: "Network failure as I was using it.  Hardware? Software?"
date: 2005-07-12
forum: Server Platforms
---

### Post by thorndike on 2005-07-12
Good afternoon all, (if this is a double post, I apologize...)

While preparing this Kubuntu server for a small office, I ran into a problem that has completely baffled me. Twice.

First, the hardware is an HP LH6000 Netserver with dual 550Mhz Xeon processors with 1 Gig of ram.  Also this box has multiple network interfaces and the NETRAID raid controller supporting 2 raid arrays.

I am using Kubuntu on this box because it is the only distribution that has the drivers to support the NETRAID (megaraid) raid controller.  I would prefer to use Debian on a server box, but no one has been able to tell me how to get the RAID controller working.  Any help on this point would be appreciated greatly as the problem I am currently having is a showstopper.

Now on to the fun.

I have had the server up and running for days.  I have been adding users, configuring Samba and just getting the server ready to take in to demonstrate and begin the installation process.  Out of the blue last night, the network communications seemed to slow down to a crawl.  They were working, but very slowly.  Even though I have not had to do this with my other Linux box, I decided to reboot to see if the problem would clear up (I still havent pulled myself completely from the MS way of solving problems).  Upon reboot, the network interfaces would fail and I could not get them restarted.  Thinking I might have a heat problem, I decided to shut the machine down for the night and let everything cool off.  Well this morning, I booted up and the server was in the same shape.  The network interfaces could not be coaxed into working.  In order to verify hardware or software, I booted off a MEPIS live cd and the network came up perfectly so I know it is NOT a hardware problem.

I said this was the second time.  The first time I had just done an apt-get upgrade so I thought I had installed a problem package.  To solve the problem that time, I just reinstalled.  This time I can reinstall.  I have to know the solution or I can not put this server in play.
inter
I have tried adding noapic to my GRUB menu...no luck
I have tried other network interfaces on the server...no luck

Interface file:


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.


mapping hotplug
	script grep
	map eth0

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.104
netmask 255.255.255.0
gateway 192.168.1.1

iface eth2 inet 

iface eth3 inet 

iface eth1 inet 



So any help with either fixing this network problem, or getting the right drivers loaded with Vanilla Debian, I would appreciate it.

I am off to the office today to tell them their migration is being pushed back.  They are going to love me for it.


Thorndike
thorndike AT plwireless DOT com

---

### Post by varunus on 2005-07-12
Did a reinstall make the network interfaces work again, even if just temporarily?  Also, what is the output of "sudo ifconfig" at a terminal?  What about "lsmod" at a terminal?

I have never heard of this type of problem before.  What network cards are in the system?

I'll try and help you as best I can.

---

### Post by thorndike on 2005-07-12
Here is the information that you requested!



ifconfig eth0

eth0      Link encap:Ethernet  HWaddr 00:10:83:FD:58:03
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


lsmod

Module                  Size  Used by
ipv6                  229504  8
af_packet              20744  0
proc_intf               4100  0
cpufreq_powersave       1920  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
freq_table              4100  0
video                  16260  0
battery                10244  0
container               4608  0
button                  6800  0
pcc_acpi               11264  0
sony_acpi               6280  0
ac                      4996  0
uhci_hcd               30224  0
ohci_hcd               19848  0
ehci_hcd               29444  0
usbcore               107384  3 uhci_hcd,ohci_hcd,ehci_hcd
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
serverworks             8840  1
i2c_piix4               8592  0
i2c_core               21264  1 i2c_piix4
e100                   32384  0
mii                     4736  1 e100
sworks_agp              8864  0
agpgart                31784  1 sworks_agp
floppy                 54864  0
rtc                    12216  0
pcspkr                  3816  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
tsdev                   7488  0
evdev                   9088  0
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_generic             1664  0
ide_disk               18176  0
ide_cd                 38532  0
ide_core              118988  4 serverworks,ide_generic,ide_disk,ide_cd
cdrom                  36508  1 ide_cd
reiserfs              225616  3
sd_mod                 16784  6
megaraid               37960  8
aic7xxx               185304  0
scsi_mod              119936  3 sd_mod,megaraid,aic7xxx
unix                   26164  296
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

Now Below is something strange.

When I tried to activate sudo kcontrol the following lines appeared in the terminal window.  Kcontrol did run in the foreground though.  Read until the row of =========

sudo kcontrol
Error: "/var/tmp/kdecache-robert" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
ERROR: Communication problem with kcontrol, it probably crashed.
robert@wnaserver:~$ Error: "/tmp/ksocket-robert" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"
Error: "/var/tmp/kdecache-robert" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-robert" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-robert" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-robert" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
QMetaObject::findSignal:KNetworkConfModule: Conflict with KCModule::changed(bool)
QMetaObject::findSignal:KNetworkConfModule: Conflict with KCModule::changed(bool)
XML -d list_ifaces: <?xml version='1.0' encoding='UTF-8' standalone='yes'?>

====================================================================================
While in kcontrol, I went to look at the network interfaces.  When I did, the below text appeared in the terminal window.


<!DOCTYPE network-ifaces []>

<network-ifaces>

  <interface>
    <dev>eth2</dev>
    <enabled>0</enabled>
    <hwaddr>00:D0:B7:C8:46:73</hwaddr>
    <type>ethernet</type>
  </interface>

  <interface>
    <dev>eth3</dev>
    <enabled>0</enabled>
    <hwaddr>00:D0:B7:47:5E:21</hwaddr>
    <type>ethernet</type>
  </interface>

  <interface>
    <dev>lo</dev>
    <enabled>0</enabled>
    <type>loopback</type>
  </interface>

  <interface>
    <dev>eth1</dev>
    <enabled>0</enabled>
    <hwaddr>00:D0:B7:47:6F:C4</hwaddr>
    <type>ethernet</type>
  </interface>

  <interface>
    <dev>eth0</dev>
    <enabled>0</enabled>
    <hwaddr>00:10:83:FD:58:03</hwaddr>
    <type>ethernet</type>
  </interface>

</network-ifaces>

<!-- GST: end of request -->


Now i am REALLY confused.

Thorndike
thorndike AT plwireless DOT com

---

### Post by thorndike on 2005-07-12
I forgot to post this.  When I tried to get to Kcontrol after doing an SU instead of kdesu, this is the error message I got.


Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kcontrol: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-6745' to 'kcontrol'
ERROR: Communication problem with kcontrol, it probably crashed.

It appears that the more I work on this, the more the server forgets.  My wife, who is a UNIX wiz, compared it to a machine that has alzheimers.  It is getting worse and worse.  I will probably have to do a reload tonight but this time I will only do a bare server load and forego X Windows.

Thorndike
thorndike AT plwireless DOT com

---

### Post by moopere on 2005-07-12
[QUOTE=thorndike]
I am using Kubuntu on this box because it is the only distribution that has the drivers to support the NETRAID (megaraid) raid controller.  I would prefer to use Debian on a server box, but no one has been able to tell me how to get the RAID controller working.  Any help on this point would be appreciated greatly as the problem I am currently having is a showstopper.[/QUOTE]

Whats the actual part number of the NETRAID controller?  

I'm a bit surprised it won't work with the standard megaraid module.  On my Sarge server here there is a megaraid.o as standard with the 2.4.x kernel, I'm pretty sure it will still be there in the 2.6.x kernel if thats what you want to use (though I'm not using a megaraid controller).  In my other office I've got an old HP Netserver LH Pro (PPro 200) with a PCI 428 Megaraid, this works fine under Debian and Ubuntu.

What error message/logs do you get using Sarge when you try and load the megaraid module?

Or is the problem that you don't have the megaraid module compiled into the debian kernel you are trying to use?[/QUOTE]

[QUOTE=thorndike]Upon reboot, the network interfaces would fail and I could not get them restarted.[/QUOTE]

What did you do to try and get them restarted?  Are you sure that the modules for the card(s) are loaded?  If so, what error messages do you get when you try to bring the card up manually using ifconfig?


[QUOTE=thorndike]I booted off a MEPIS live cd and the network came up perfectly so I know it is NOT a hardware problem.[/QUOTE]

Thats good to know.   Same kernel?  Hotplug?  How is Mepis startup different from your Ubuntu?


[QUOTE=thorndike]I said this was the second time.  The first time I had just done an apt-get upgrade so I thought I had installed a problem package.  To solve the problem that time, I just reinstalled.  This time I can reinstall.  I have to know the solution or I can not put this server in play.[/QUOTE]

Sure, you're confidence level is probably low, understandable.

All this installing and deinstalling in the hope the problem will 'go away' though is not what I'd do in the first instance as even if it does work you will be left with an unknown problem and still no confidence.  

You could try finding the fault using the available command line tools, modprobe, insmod, ifconfig etc etc etc.

If you know the network card type, make sure the module for it is loaded - if this fails you've either got the wrong module (small variations in network card manufacturing build could cause this) or the kernel module in the build of kernel you are using is faulty.  Try a different version kernel.  If you can't then try changing from 686 to 386 or similar of the version that is available to you.

If the module loads you're halfway there.  Bring the interface up using ifconfig.  Problems here are possibly config related, but you can cut through all this by using a full set of command line options.

Good luck
Craig

---

### Post by LordHunter317 on 2005-07-13
Your X errors are normal for the way you're trying to run apps, I think.  Without the actual commands you ran, there's no way to tell.

As your NIC, I'm going to make a wild guess of failing card, or an external problem.  Networks shouldn't do that.

---

### Post by thorndike on 2005-07-13
[INDENT]Or is the problem that you don't have the megaraid module compiled into the debian kernel you are trying to use?[/INDENT]

Craig, I am assuming that the above is the problem.  While Linux is not completely new to me, I have not taken the steps to compile a new kernel.  I have been walking a fine line with the company I am supporting with this move to Linux.  They have that old fear of 'lack of support' with Linux but the idea that they get lots of support from Microsoft.  I have tried to tell them otherwise and that when there have been problems with NT I never get support from MS, but from the web.  Anyway, they would be very concerned if I went in and tried to explain to them that "I" rebuilt the software for them.   Also, I don't know how to go about recompiling the kernel!


[INDENT]What did you do to try and get them restarted? Are you sure that the modules for the card(s) are loaded? If so, what error messages do you get when you try to bring the card up manually using ifconfig?
[/INDENT]
When I did ifconfig absolutely nothing happened.  



[INDENT]
Thats good to know. Same kernel? Hotplug? How is Mepis startup different from your Ubuntu?[/INDENT]

I don't know how they are different at the kernel level.  I have to assume that they are just compiled with different drivers.

[INDENT]
All this installing and deinstalling in the hope the problem will 'go away' though is not what I'd do in the first instance as even if it does work you will be left with an unknown problem and still no confidence.[/INDENT]

Yeah, I wasn't thrilled about reinstalling the first time either.

[INDENT]
You could try finding the fault using the available command line tools, modprobe, insmod, ifconfig etc etc etc.[/INDENT]

I will be getting these shortly.

Thorndike

---

### Post by alastair on 2005-07-13
Shouldn't need a reboot to solve things - but you knew that! Reinstall is crazy ...

Anyway - apart from forgetting about using GUI network tools, if you want to understand things - the system logs (e.g. /var/log/syslog) should always be the first port of call. See if anything odd, network related, in them. No need to complicate network problems by bringing in GUI/desktop problems as well.

Then things like :

/etc/init.d/networking restart
ifdown eth0 ; ifup eth0

Checking logs etc.

---

### Post by gruepig on 2005-07-13
Re: megaraid.  I could have sworn the Sarge installer had support for megaraid(2).  I once had success with the Woody boot floppies referenced here on a Dell: [http://linux.dell.com/storage.shtml#megaraid](http://linux.dell.com/storage.shtml#megaraid).

Re: ethernet.  What kind of ethernet card do you have?  Is the driver loaded?  I strongly second the recommendation that you debug using command line tools; it really does simplify things.  Try running 'ifup eth0'.

---

### Post by moopere on 2005-07-14
[QUOTE=thorndike][INDENT]Or is the problem that you don't have the megaraid module compiled into the debian kernel you are trying to use?[/INDENT]

Craig, I am assuming that the above is the problem.  While Linux is not completely new to me, I have not taken the steps to compile a new kernel.[/QUOTE]


I would have thought that the initrd of the standard Sarge installer (or Ubuntu) would include the module for the megaraid.  If you don't know, or can't find out, tug my ear and I'll try booting up Sarge with my old LH Pro (with Megaraid 428) and a boot floppy to see what happens.

As for compiling a new kernel...you'll see lots of advice on doing or not doing this.  For mine, I try hard to never do this.  The reason is pretty simple, standard kernels give less trouble (ie, predictably broken hehe) and allow an easy upgrade when kernels are released due to security fixes etc.  

Unless I can guarentee that I'll be the only guy admining a box for the rest of its life I will almost never put a self compiled kernel into production.

Anyway, these days the once important reasons for doing so are mostly gone.  The optimisation factor is almost irrelvent given todays overpowered processors, the problems of incompatible hardware (modules) are also almost gone.

Anyway, I'm getting way off track here.  What does "lspci" say about your megaraid controller?


[QUOTE=thorndike]I have been walking a fine line with the company I am supporting with this move to Linux.  They have that old fear of 'lack of support' with Linux but the idea that they get lots of support from Microsoft.  I have tried to tell them otherwise and that when there have been problems with NT I never get support from MS, but from the web.  Anyway, they would be very concerned if I went in and tried to explain to them that "I" rebuilt the software for them.   Also, I don't know how to go about recompiling the kernel![/QUOTE]

Yep, I understand and agree with you.  Don't frighten management in this way - there really should not be any need.


[QUOTE=thorndike][INDENT]What did you do to try and get them restarted? Are you sure that the modules for the card(s) are loaded? If so, what error messages do you get when you try to bring the card up manually using ifconfig?
[/INDENT]

When I did ifconfig absolutely nothing happened.  [/QUOTE]

Right.  Did you check first to see if the network cards' kernel driver (module) was loaded?  Perhaps hotplug is not picking it up correctly??  What NIC are we talking about anyway?  Again, lspci should shed some light on this.


[QUOTE=thorndike][INDENT]
Thats good to know. Same kernel? Hotplug? How is Mepis startup different from your Ubuntu?[/INDENT]

I don't know how they are different at the kernel level.  I have to assume that they are just compiled with different drivers.[/QUOTE]


I don't think this will be a kernel problem in the end, though we shouldn't rule out the possibility later on if nothing else works.

What I meant by 'difference' above was the potential for difference in hotplug or discover services used by the OS to find what hardware is present and load the appropriate driver.

This would be the first thing I'd check - is the -correct- driver being loaded?  Note that similar drivers may not be good enough, you probably have a HP branded NIC and you need to find the correct module for it.  If its generic then fine....

Also, you have more than one NIC in the machine (I seem to remember), do any of them work?  Are they all the same?  Is the interface that the system thinks is Eth0 swapping around between one reboot and the next (yes, this does happen in some cases).

Check the MAC address of each NIC and then try to determine if eth0 is always assigned to the MAC you think it is (eek!).


[QUOTE=thorndike][INDENT]
You could try finding the fault using the available command line tools, modprobe, insmod, ifconfig etc etc etc.[/INDENT]

I will be getting these shortly.

Thorndike[/QUOTE]

All the tools you need will be part of the stock (base) Ubuntu (or Debian) install.

I don't want to tell you how to suck eggs but I'd be looking at debugging this like:

  1) What NIC do I have?  Is the module being loaded without error (dmesg or /var/log/messages)

  2) If the module is being loaded successfully then bring the interface up with ifconfig with full command line switches (to bypass possibly faulty conf files).  Check /var/log/messages or syslog again to look for anything fishy.  Don't use dhcp, use static IP for now

  3) If the logs say everything is ok at this point, but you still can't get network connectivity then you either have a subtle hardware fault (which you've already checked against using Mepis) or the module for the card is acting up.  Hard to check this, but I can't think of a quicker way than to use a different version of the kernel

  4) If it does work at this point, but after a reboot it doesn't then you probably have a munged config which can be fairly easily checked or else you have a case of the infamous changing Eth0 problem (different cards are initialised as different interfaces almost randomly at bootup).  This mostly happen to folks who have multiple card which are exactly the same type/brand/model etc in the machine at the same time.  The module README will usually have something to say about this.

Good luck.
Craig

---

### Post by thorndike on 2005-07-14
Thanks for all the assistance folks, but I found a solution that makes me and the company owners much less worried.

After a bit of searching I discovered this sight  [http://wiki.osuosl.org/display/LNX/Debian+on+Dell+Servers](http://wiki.osuosl.org/display/LNX/Debian+on+Dell+Servers) .  The author of the iso on this page has created exactly what I needed.  The kernel he created supports the Megaraid drivers AND has SMP activated so my servers are now running flawlessly.  At least for now.  The kernel is 2.4.31 but for a server this is just fine with me.   Also, there are no included packages so I can install only what I need straight from the Debian repositories.

I appreciate all the help everyone offered.  The community behind LINUX has always been helpful regardless of the distro being used.  While everyone I have chatted with on both  LINUX forums and MS forums has been very helpful, the difference seems to be that on the LINUX forums there is a real interest in the problem and SOLVING the problem either at a 'local' level or at the developer level.  On the MS boards the answers always seem to be along the line of 'I had the same problem 2  (3 or 4 or 5) years ago and MS hasnt fixed it yet. Here is the solution."  Everyone on the MS forums just seem to be resigned to the fact that they have to live with problems.

Thanks again for all the responses and the effort put into them.

Thorndike
thorndike AT plwireless DOT

---

### Post by moopere on 2005-07-16
[QUOTE=thorndike]Thanks for all the assistance folks, but I found a solution that makes me and the company owners much less worried.[/QUOTE]

I'm glad you found a solution, however:

[QUOTE=thorndike]After a bit of searching I discovered this sight  [http://wiki.osuosl.org/display/LNX/Debian+on+Dell+Servers](http://wiki.osuosl.org/display/LNX/Debian+on+Dell+Servers) .  The author of the iso on this page has created exactly what I needed.  The kernel he created supports the Megaraid drivers AND has SMP activated so my servers are now running flawlessly.  At least for now.  The kernel is 2.4.31 but for a server this is just fine with me.   Also, there are no included packages so I can install only what I need straight from the Debian repositories.[/QUOTE]

The potential, actually, -probable- problem with this approach is that you are going to be stuck when it comes to a replacement kernel.  Why replace the kernel?  Well, if a serious security concern arises what will you do?  The original problem will come back to haunt you unless the author or the ISO you mention above does some work, or unless the newer kernel "just works" - I wouldn't be betting on either.

I'm guessing that you've run out of time trying to solve this problem for the customer, we've all been there and I understand the pressure you are probably under, but if an opportunity arises for further testing, to really get to the bottom of this problem I think you'll sleep better at night knowing that a future kernel upgrade won't break the server.

Best regards,
Craig

---

### Post by thorndike on 2005-07-18
In the end, I recompiled the standard Debian 2.4.31 kernel with the appropriate drivers and settings to take advantage of the hardware.  I discovered that Kubuntu didn't even have SMP activated, so I activated SMP, USB and the appropriate Megaraid drivers.  The server smokes now!

This should eliminate any problems with distribution upgrades.

Thanks again for the asstance....

Thorndike

---

### Post by Yagisan on 2005-07-19
G'day,

Like the OP I have also encountered the network slows to a crawl problem. I can reliably reproduce it on two machines connected with a crossover cable (eliminates the rest of the network as the cause).

I find that for short bursts of network traffic all is well, but the moment I rsync my ubuntu repository to my webserver my network connections seize up. There is no message in syslog at all when this happens (I was running tail -f on var/log/syslog on the workstation)

On the server I'm getting the following messages appearing in syslog around the time of the network seizures ```
Jul 20 00:53:23 gateway kernel: NETDEV WATCHDOG: eth1: transmit timed out
Jul 20 00:53:23 gateway kernel: eth1: Transmit timeout, status 0c 0005 c07f media 00.
Jul 20 00:53:23 gateway kernel: eth1: Tx queue start entry 7262  dirty entry 7258.
Jul 20 00:53:23 gateway kernel: eth1:  Tx descriptor 0 is 000ea5ea.
Jul 20 00:53:23 gateway kernel: eth1:  Tx descriptor 1 is 000ea5ea.
Jul 20 00:53:23 gateway kernel: eth1:  Tx descriptor 2 is 000ea5ea. (queue head)
Jul 20 00:53:23 gateway kernel: eth1:  Tx descriptor 3 is 000ea5ea.
Jul 20 00:53:24 gateway kernel: eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 20 00:53:35 gateway kernel: NETDEV WATCHDOG: eth1: transmit timed out
Jul 20 00:53:35 gateway kernel: eth1: Transmit timeout, status 0c 0005 c07f media 00.
Jul 20 00:53:35 gateway kernel: eth1: Tx queue start entry 65  dirty entry 61.
Jul 20 00:53:35 gateway kernel: eth1:  Tx descriptor 0 is 000ea5ea.
Jul 20 00:53:36 gateway kernel: eth1:  Tx descriptor 1 is 000ea5ea. (queue head)
Jul 20 00:53:35 gateway kernel: eth1:  Tx descriptor 2 is 000ea5ea.
Jul 20 00:53:36 gateway kernel: eth1:  Tx descriptor 3 is 000ea5ea.
Jul 20 00:53:35 gateway kernel: eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 20 00:53:47 gateway kernel: NETDEV WATCHDOG: eth1: transmit timed out
Jul 20 00:53:47 gateway kernel: eth1: Transmit timeout, status 0c 0005 c07f media 00.
``` It repeats with different start entry and dirty entry numbers. Something disturbing is I've found several entries like this  in var/log/messages on the server near times that the network has "seized" up```
Jul 19 13:35:45 gateway kernel: NETDEV WATCHDOG: eth1: transmit timed out
Jul 19 13:35:45 gateway kernel: eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 19 13:35:53 gateway kernel:  [bad_page+80/129] bad_page+0x50/0x81
Jul 19 13:35:53 gateway kernel:  [free_hot_cold_page+86/206] free_hot_cold_page+0x56/0xce
Jul 19 13:35:53 gateway kernel:  [poll_freewait+55/62] poll_freewait+0x37/0x3e
Jul 19 13:35:53 gateway kernel:  [do_select+637/658] do_select+0x27d/0x292
Jul 19 13:35:53 gateway kernel:  [__pollwait+0/154] __pollwait+0x0/0x9a
Jul 19 13:35:53 gateway kernel:  [sys_select+770/1122] sys_select+0x302/0x462
Jul 19 13:35:53 gateway kernel:  [syscall_call+7/11] syscall_call+0x7/0xb
Jul 19 13:35:56 gateway kernel: NETDEV WATCHDOG: eth1: transmit timed out
Jul 19 13:35:56 gateway kernel: eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
```Obviously the kernel is unhappy with something.

The is only one network interface in my workstation (onboard Realtek 8169 Gigabit) and two network interfaces on the webserver (Realtek 8139 100Mb), drivers all load fine, everything is detected, all static IP's.

I'm using the stock Ubuntu Hoary kernel (2.6.10-5-amd64-generic on the workstation, 2.6.10-5-386 on the webserver) Any ideas on how to fix this ?

---

