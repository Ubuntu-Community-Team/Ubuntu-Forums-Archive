---
title: "Can't set up Wireless"
date: 2012-04-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Kay Tee Ess on 2012-04-03
I'm having issues setting up Wireless for Ubuntu 12.04. I have my wireless card plugged in and from my knowledge, Ubuntu can read it, but, I can't enable wireless.

Whenever I try and turn off Airplane Mode or when I'm in the menu for Networking at the top of the screen and click "Enable Wireless", my computer freezes.

Anyone know what may be causing this issue? It was working fine when I first installed ubuntu about an hour ago but now, it just doesn't work.

Any suggestions?

---

### Post by lordbux on 2012-04-03
> **Kay Tee Ess said:**
> I'm having issues setting up Wireless for Ubuntu 12.04. I have my wireless card plugged in and from my knowledge, Ubuntu can read it, but, I can't enable wireless.

Whenever I try and turn off Airplane Mode or when I'm in the menu for Networking at the top of the screen and click "Enable Wireless", my computer freezes.

Anyone know what may be causing this issue? It was working fine when I first installed ubuntu about an hour ago but now, it just doesn't work.

Any suggestions?

This usually happens when the driver is not working properly 
you can try running 
AFTER CONNECTING TO INTERNET WITH CABLE
```
jockey-gtk
```

It will try and make sure the driver is ok

if that does not work you will have to 

Download and install the compat wireless drivers from linuxwireless.org/

---

### Post by Kay Tee Ess on 2012-04-03
It says "No proprietary drivers are in use on this system."

I haven't installed any drivers yet, I'm still trying to figure out Linux. I know that I have to use ndiswrapper to I guess you  could say "adapt" the Windows drivers to work on Linux. But, I haven't quite figured out how it works. And I'm pretty sure I didn't even get ndiswrapper correctly. I will try that website you suggested for now.

---

### Post by leily on 2012-04-17
Hi friends,

I have the same error, I can not connect to the wireless with Ubuntu 12.04. I installed it on VMware and I have downloaded  Ubuntu from the internet, its size is 701M. Is it possible that this software is not complete? 

Regards.

---

### Post by wildmanne39 on 2012-04-17
Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by leily on 2012-04-17
Hi
Thank you so much for your reply.
I've done these commands and the results are:

```
leily@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"
Linux ubuntu 3.2.0-20-generic-pae #33-Ubuntu SMP Tue Mar 27 17:05:18 UTC 2012 i686 i686 i386 GNU/Linux
leily@ubuntu:~$ lspci -nnk | grep -iA2 net
02:01.0 Ethernet controller [0200]: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] [1022:2000] (rev 10)
	Subsystem: Advanced Micro Devices [AMD] PCnet - Fast 79C971 [1022:2000]
	Kernel driver in use: pcnet32
	Kernel modules: pcnet32
02:02.0 Multimedia audio controller [0401]: Ensoniq ES1371 [AudioPCI-97] [1274:1371] (rev 02)
	Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128 [1274:1371]
leily@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
leily@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

leily@ubuntu:~$ rfkill list all
leily@ubuntu:~$ lsmod
Module                  Size  Used by
vmwgfx                102138  0
ttm                    65344  1 vmwgfx
drm                   197551  2 vmwgfx,ttm
snd_ens1371            24819  2
gameport               15060  1 snd_ens1371
snd_ac97_codec        106082  1 snd_ens1371
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_ens1371,snd_ac97_codec
snd_seq_midi           13132  0
snd_rawmidi            25424  2 snd_ens1371,snd_seq_midi
ppdev                  12849  0
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
vmw_balloon            12700  0
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                72846  0
serio_raw              13027  0
snd                    62064  11 snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bnep                   17830  2
rfcomm                 38139  0
bluetooth             158438  10 bnep,rfcomm
soundcore              14635  1 snd
snd_page_alloc         14108  1 snd_pcm
parport_pc             32114  1
i2c_piix4              13093  0
mac_hid                13077  0
shpchp                 32325  0
lp                     17455  0
parport                40930  3 ppdev,parport_pc,lp
pcnet32                41110  0
mptspi                 22474  2
mptscsih               39530  1 mptspi
mptbase                96852  2 mptspi,mptscsih
floppy                 60310  0
leily@ubuntu:~$

```

---

### Post by wildmanne39 on 2012-04-17
Hi leily, in a virtual machine you do not need to set up a wireless connection because your internet runs off of your hosts internet connection if you set it up properly.

I am not saying that it can not be done but it is just not needed.
Thanks

---

### Post by leily on 2012-04-19
Hi 
Thank you for the reply.

But in network icon, there is not Wireless connection, only wired and vpn connection. I attached its photo.
How can I add the wireless connection?

---

### Post by cariboo on 2012-04-19
You won't see a wireless connection in vbox, as you are using a virtual network adapter. I'd suggest you probably have the virtual network device bound to your wired ether connection. Go into Network settings, and bind the virtual network device to your wireless device.

---

### Post by wildmanne39 on 2012-04-19
Hi, I have my virtual machine where I can see my usb adapter but every time I capture it ubuntu locks up and I have tried it in three different buntu versions so I am afraid I am not able to help you.

Do you have internet through a wired connection on your host if so you can use it or try has cariboo907 has recommended in your host, it will still show as a wired connection in your virtual machine but you will be able to use your wireless connection in your host to access the internet in your virtual machine.

---

### Post by haqking on 2012-04-19
I might be misreading this but, you cannot use wireless in a VM unless it is a USB device.

If its a built in wireless or PCMCIA then the VM has to use the virtual NIC attached to that device and so seen as a ethernet device in the VM.

Using either NAT or Bridged in the VM settings.

Edit: rereading it i think i may have misread it, though what i said is still correct ;)

---

### Post by leily on 2012-04-22
Hi,

Thank you dear friends. My problem is solved but I don't know how!!
In Edit/virtual network editor I click on "restore default" and I can connect to the Internet,however, when the wireless network is changed I have do this action again.

---

