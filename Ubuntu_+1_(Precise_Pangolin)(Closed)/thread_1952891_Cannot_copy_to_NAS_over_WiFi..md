---
title: "Cannot copy to NAS over WiFi."
date: 2012-04-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by VeeDubb on 2012-04-05
Since upgrading to 12.04 I cannot copy large files to my network attached storage box.  This configuration worked perfectly before the update, and no other system or network changes have been made.

The box is a Seagate BlackArmor NAS that is connect to my router via Cat6.  The sharing on the NAS is through samba.

lspci reports my WiFi as:

```
Network controller: Ralink corp. RT2800 802.11n PCI
```


I have overall good network performance, and I am able to access browse, move, and delete any file.  However, when I attempt to copy any file of more than a few MB from my desktop to the NAS, the transfer will get to somewhere between 2 and 3 MB, and then hang.  I don't receive any errors on my desktop until it has hung for at least a minute, and then I only get an error stating that the connection has timed out.

Once this has happened, I loose all network connectivity, but the network indicator still shows that I am connected.  The only way I have found to restore connectivity is to disconnect from the network and then reconnect.

Any ideas on how to go about troubleshooting this?  I haven't been able to find a bug report that quite fit, and I haven't posted one yet because I don't know enough about what's going on to post a useful report.  

Oh, and all software packages are fully up to date.

---

### Post by cariboo on 2012-04-05
Try in a terminal:

```
tail -f | dmesg
```

when copying a file to see what error shows up.

---

### Post by VeeDubb on 2012-04-05
No errors or new feedback of any kind showed up running tail.  I got all the usual feedback when I ran it, but nothing new showed up while trying to copy the file or closing the error message.

The error message was the same as always and said:

```
Error while copying "big_file.mkv"

There was an error copying the file into smb://seagate0/public/Our%20Videos/Movies.


```

Clicking on "Show more details" adds a line that says "Connection timed out."

As usual, the only way I was able to restore connectivity was to disconnect from the network and then reconnect.  None of which created feedback in the console from tail.

---

### Post by cariboo on 2012-04-05
The command I gave you doesn't work the way I expected it would, try:

```
tail -f /var/log/{messages,kernel,dmesg,syslog}
```

then try to copy a large file.

---

### Post by VeeDubb on 2012-04-06
I still didn't get anything at all when the connection froze up, but I did at least get feedback when I restarted the connection.  I don't see anything useful in it, but here's what it returned.

```
Apr  6 09:11:16 desktop avahi-daemon[1158]: Joining mDNS multicast group on interface wlan1.IPv6 with address [MAC address redacted].
Apr  6 09:11:16 desktop avahi-daemon[1158]: New relevant interface wlan1.IPv6 for mDNS.
Apr  6 09:11:16 desktop avahi-daemon[1158]: Registering new address record for [MAC address redacted] on wlan1.*.
Apr  6 09:11:17 desktop dhclient: DHCPREQUEST of 192.168.1.7 on wlan1 to 255.255.255.255 port 67
Apr  6 09:11:17 desktop dhclient: DHCPACK of 192.168.1.7 from 192.168.1.1
Apr  6 09:11:17 desktop dhclient: bound to 192.168.1.7 -- renewal in 36378 seconds.
Apr  6 09:11:17 desktop NetworkManager[1160]: <info> (wlan1): DHCPv4 state changed preinit -> reboot
Apr  6 09:11:17 desktop NetworkManager[1160]: <info>   address 192.168.1.7
Apr  6 09:11:17 desktop NetworkManager[1160]: <info>   prefix 24 (255.255.255.0)
Apr  6 09:11:17 desktop NetworkManager[1160]: <info>   gateway 192.168.1.1
Apr  6 09:11:17 desktop NetworkManager[1160]: <info>   nameserver '192.168.1.1'
Apr  6 09:11:17 desktop NetworkManager[1160]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr  6 09:11:17 desktop NetworkManager[1160]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) started...
Apr  6 09:11:17 desktop avahi-daemon[1158]: Joining mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.7.
Apr  6 09:11:17 desktop avahi-daemon[1158]: New relevant interface wlan1.IPv4 for mDNS.
Apr  6 09:11:17 desktop avahi-daemon[1158]: Registering new address record for 192.168.1.7 on wlan1.IPv4.
Apr  6 09:11:18 desktop NetworkManager[1160]: <info> DNS: starting dnsmasq...
Apr  6 09:11:18 desktop dnsmasq[11230]: exiting on receipt of SIGTERM
Apr  6 09:11:18 desktop NetworkManager[1160]: <info> (wlan1): writing resolv.conf to /sbin/resolvconf
Apr  6 09:11:18 desktop dnsmasq[11258]: started, version 2.59 cache disabled
Apr  6 09:11:18 desktop dnsmasq[11258]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Apr  6 09:11:18 desktop dnsmasq[11258]: using nameserver 8.8.4.4#53
Apr  6 09:11:18 desktop dnsmasq[11258]: using nameserver 8.8.8.8#53
Apr  6 09:11:18 desktop NetworkManager[1160]: <info> (wlan1): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr  6 09:11:18 desktop NetworkManager[1160]: <info> Policy set 'APT207 1' (wlan1) as default for IPv4 routing and DNS.
Apr  6 09:11:18 desktop NetworkManager[1160]: <info> Activation (wlan1) successful, device activated.
Apr  6 09:11:18 desktop NetworkManager[1160]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) complete.
Apr  6 09:11:25 desktop kernel: [78577.712051] wlan1: no IPv6 routers present
Apr  6 09:11:28 desktop ntpdate[11292]: step time server 91.189.94.4 offset 1.622090 sec
Apr  6 09:11:36 desktop NetworkManager[1160]: <info> (wlan1): IP6 addrconf timed out or failed.
Apr  6 09:11:36 desktop NetworkManager[1160]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr  6 09:11:36 desktop NetworkManager[1160]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr  6 09:11:36 desktop NetworkManager[1160]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) complete.


```

---

### Post by cariboo on 2012-04-06
It seems the problem is with ipv6, other wise the output looks ok to me.Have a look at this [page]("https://wiki.ubuntu.com/IPv6"), at the very bottom it tells you how to disable ipv6.

---

### Post by VeeDubb on 2012-04-07
I followed the link, read the page, and followed the instructions, including running "lsmod | grep ipv6" to verify that ipv6 was fully disabled.  No change in behavior except that browsing files on my network seems marginally faster.  

My network still grinds to a complete halt when trying to copy a large file from my desktop to the NAS.  It still happens somewhere between 2.4 and 2.9MB transferred, and still eventually times out the connection with no way to restore connectivity other than dropping the connection and reconnecting.

I really do appreciate the help, I'm just surprised that this isn't a more common problem.  There's nothing unusual about my setup, and my setup was working flawlessly with the 11.04 and 11.10

---

### Post by VeeDubb on 2012-04-07
For lack of other options at the moment, I went poking around the web interface of my NAS, and enabled FTP.  Unfortunately, I had the exact same experience over FTP using filezilla.  The transfer worked perfectly right up to 2.9MB, at which point it hung for about half a minute, and then said transfer failed.

That doesn't tell me much, but it does confirm that the issue is not directly related to SMB.  As with browsing the samba shares, I was able to add, delete, and move files just fine, but adding large files is still a no-go.

Also, just for the sake of a sanity check, I verified that my NAS isn't getting full.  I currently have around 300GB of free space and the S.M.A.R.T. checking built in reports the physical drive as being in good health.

---

### Post by VeeDubb on 2012-04-09
Anyone have any other thoughts on this?  So far we've only managed to eliminate samba and IPv6.  After all of the updates, this problem persists, and I've yet to find any meaningful error.

---

### Post by cariboo on 2012-04-09
The the same problem appear if you are connected to your network with a cable? I suggest this just to make sure it isn't a problem with the NAS.

---

### Post by VeeDubb on 2012-04-10
I'll be trying the cable shortly.  I was trying to avoid it because it involves either buying a 25' network cable or dragging out an extension cord to move my computer closer to my router.

However, I've found that this affects more than my ability to copy to NAS.  I tried to upload about a gig of large jpg files to blurb.com so I can get a photo-book published for a client, and I ran into the exact same problem.  

While doing this, I had other devices connected to the internet through the same router.  My set-top box was connected by cat6, and my tablet was connected by WiFi.  Both continued to operate normally.  This eliminates, with absolute certainty, my router, and my NAS box as possible problems.  The issue is 100% with my desktop.

So, I now know the following:

Happens consistently with uploading very large files (1.5GB and larger)  

Happens when uploading a large volumes of files in the 2-10MB range.

Does not happen when downloading or streaming files, browsing, etc.  

Does not happen when sending single files of 1MB and less.

Is not directly related to my router or NAS box.

Is not directly related to any one protocal, as it has now happened while using samba, ftp, and http.


I'll post back after I try the net cable.

---

### Post by VeeDubb on 2012-04-10
Well, I found a Cat5 cable in the closet that was long enough to hook it up without going through extreme measures and it is definitely a problem with the wireless.  Cable works just fine and I was able to upload my photo books without issue and transfer about 1GB/minute from my desktop to NAS.

---

### Post by NHclimber on 2012-04-10
Please post the output of:
```
lsmod
lspci -nnk
ifconfig -a
iwconfig
nm-tool
```

---

### Post by VeeDubb on 2012-04-10
> **NHclimber said:**
> Please post the output of:
```
lsmod
lspci -nnk
ifconfig -a
iwconfig
nm-tool
```

Here's all the output.  For lsmod and lspci I've marked what I believe to be the related entries in bold.

```
$ lsmod
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  12 
bnep                   18281  2 
binfmt_misc            17540  1 
vesafb                 13844  1 
joydev                 17693  0 
btusb                  18288  2 
bluetooth             180104  23 rfcomm,bnep,btusb
usbhid                 47199  0 
hid                    99559  1 usbhid
snd_hda_codec_realtek   223867  1 
snd_usb_audio         122982  1 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_usbmidi_lib        25395  1 snd_usb_audio
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                97188  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
arc4                   12529  2 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
[B]rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci[/B]
crc_ccitt              12667  1 rt2800lib
[B]rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci[/B]
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
snd_timer              29990  2 snd_pcm,snd_seq
eeprom_93cx6           12725  1 rt2800pci
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
sp5100_tco             13791  0 
i2c_piix4              13301  0 
snd                    78855  19 snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87603  0 
k10temp                13166  0 
nvidia              12281608  40 
edac_core              53746  0 
edac_mce_amd           23709  0 
serio_raw              13211  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
uas                    18027  0 
usb_storage            49198  0 
pata_atiixp            13204  0 

```

```
$ lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] nee ATI RX780/RX790 Chipset Host Bridge [1002:5957]
	Subsystem: Advanced Micro Devices [AMD] nee ATI RX780/RX790 Chipset Host Bridge [1002:5957]
00:02.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (external gfx0 port A) [1002:5978]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (PCI express gpp port C) [1002:597c]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7599]
	Kernel driver in use: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7599]
	Kernel driver in use: ohci_hcd
00:12.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7599]
	Kernel driver in use: ohci_hcd
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7599]
	Kernel driver in use: ehci_hcd
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7599]
	Kernel driver in use: ohci_hcd
00:13.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7599]
	Kernel driver in use: ohci_hcd
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
	Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
	Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 3c)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7599]
	Kernel modules: sp5100_tco, i2c-piix4
00:14.1 IDE interface [0101]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7599]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7599]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
	Subsystem: Advanced Micro Devices [AMD] nee ATI Device [1002:4383]
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
	Subsystem: Advanced Micro Devices [AMD] nee ATI Device [1002:4396]
	Kernel driver in use: ohci_hcd
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
	Kernel modules: amd64_edac_mod
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
	Kernel driver in use: k10temp
	Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G92 [GeForce 9800 GT] [10de:0614] (rev a2)
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nvidia_current_updates, nouveau, nvidiafb
[B]03:07.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
	Subsystem: Linksys Device [1737:0067]
	Kernel driver in use: rt2800pci
	Kernel modules: rt2800pci[/B]

```

```
$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:989 errors:0 dropped:0 overruns:0 frame:0
          TX packets:989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:102334 (102.3 KB)  TX bytes:102334 (102.3 KB)

wlan1     Link encap:Ethernet  HWaddr [MAC address redacted for privacy]  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9afc:11ff:fecd:b250/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37504 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9767 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7619792 (7.6 MB)  TX bytes:2147169 (2.1 MB)

```

```
$ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11abgn  ESSID:"APT207"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: [MAC address redacted for privacy]   
          Bit Rate=130 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6332  Invalid misc:329   Missed beacon:0

```

```
$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan1  [APT207 1] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        98:FC:11:CD:B2:50

  Capabilities:
    Speed:           130 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    myqwest6055:     Infra, 00:24:7B:A5:0A:38, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    Vinyard:         Infra, C0:C1:C0:1C:44:E2, Freq 5180 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    hpsetup:         Ad-Hoc, 02:13:CE:00:01:4E, Freq 2462 MHz, Rate 54 Mb/s, Strength 77
    NETGEAR:         Infra, 00:24:B2:10:C5:FA, Freq 2412 MHz, Rate 54 Mb/s, Strength 50
    *APT207:         Infra, [MAC address redacted for privacy], Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA2
    Vinyard:         Infra, C0:C1:C0:1C:44:E1, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             8.8.8.8
    DNS:             8.8.4.4

```

---

### Post by VeeDubb on 2012-04-11
Any more thoughts or ideas on this one?  Another round of updates today and no change in this problem.  I can download or stream files of any size, but when I try to send/upload/etc files with a total size of more than a few MB I'm toast.

---

### Post by NHclimber on 2012-04-11
Looks like rt2x00 drivers are broken in 3.2.

Here's a *very* technical discussion [http://marc.info/?l=linux-wireless&m=132534063601847&w=2](http://marc.info/?l=linux-wireless&m=132534063601847&w=2) regarding changes to the mac80211 driver that are causing problems for rt2x00 devices (that they don't want to revert because other devices work fine with the new changes).

Also, looks like there's been some recent work to not lockup on SMP machines [http://marc.info/?l=linux-wireless&w=2&r=3&s=rt2x00&q=b](http://marc.info/?l=linux-wireless&w=2&r=3&s=rt2x00&q=b)

Eventually these changes make their way to compat-wireless so I would recommend keeping an eye here [http://rt2x00.serialmonkey.com/phpBB/viewforum.php?f=5](http://rt2x00.serialmonkey.com/phpBB/viewforum.php?f=5)
and upgrading then.

Sorry for the bad news.
[]("http://marc.info/?l=linux-wireless&w=2&r=3&s=rt2x00&q=b")

---

### Post by VeeDubb on 2012-04-11
Well, at least that gives me some information.  Everyone, including me, knows the risk of upgrading during beta.  I guess now I have to decide whether to live with, buy yet another wireless card to maintain compatibility, or wipe my computer to downgrade to 11.10 and wait.

After 12 years of using linux almost exclusively at home, it's frustrating to see this kind of breakage.  I usually expect more from Ubuntu.  To knowingly roll out a kernel, even on a beta, that has this kind of serious regression to something as mission critical as networking is really surprising.

---

### Post by cariboo on 2012-04-11
Have you tried any of the newer kernels available [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"), to see if the problem has been fixed?

---

### Post by VeeDubb on 2012-04-11
> **cariboo907 said:**
> Have you tried any of the newer kernels available [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"), to see if the problem has been fixed?

For the most part, I haven't touched non-stock kernels in years, although back in my Mandrake days I had to compile my own to get half of my hardware working.  I guess I'll give one or two of those a try.  Worst case scenario I bork my entire system.  :popcorn:

edit: Just read the notice of no binary drivers.  Doesn't the realtech chipset giving me problems depend on binary firmware?  Either way, I guess I'll be stuck manually installing nvidia again.  Haven't done that in years.  Good times.

---

### Post by VeeDubb on 2012-04-15
Well, the mainline kernels turned out to be more work than they were worth with nvidia drivers and all of that.  However, I was able to find a temporary solution to my problem by setting my router to G only.  G is still faster than my internet connection, so the only time it slows things down is when I'm transferring large files, but transferring large files slowly is better than not at all.  I'll just have to try setting it back after each kernel update and see what fixes it.

---

