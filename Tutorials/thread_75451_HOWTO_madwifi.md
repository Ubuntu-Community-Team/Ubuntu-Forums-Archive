---
title: "HOWTO: madwifi"
date: 2005-10-13
forum: Tutorials
---

### Post by Griffin3 on 2005-10-13
This modules is included in the Ubuntu distribution in linux-modules-restricted. It provides support for wireless devices that use the Atheros chipset, such as, say, the D-Link AirPlus DWL-G650. 

You only need to rebuild this module if you recompile the kernel in such a way that the version changes. You should change the version if you recompile, else Ubuntu's upgrades will stomp on your image.[LIST=1]
[*]Make sure networking is set up so that you can apt-get update.
[*]Login as root
```
sudo -s
#enter password
```
[*]Get what you need to compile the source
```
apt-get -y install build-essential bin86
```
[*]Compile the module
```
cd /usr/src
wget http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz
tar -xzf madwifi-cvs-current.tar.gz
apt-get -y install sharutils
cd /usr/src/madwifi
make clean
make
make install
```
[*]If you are about to reboot anyway, no need to do this (but you can anyway to test your work so far)
```
modprobe ath_pci
```
[*]Make the change permanent
```
gedit /etc/modules
#    add line at end "ath_pci"
```
[*]Configure your new ath0: under System->Administration->Networking, and enjoy![/LIST]

---

### Post by Xenus98 on 2005-10-17
This was clear! Still my Atheros Dlink card was automatically detected, but as you was on this subject, what about a HOW-TO configure WPA-PSK to start up automatically when the card is detected during boot up ? ;)

If you know, I am currently working on that point...

Thanks for any help.

---

### Post by Griffin3 on 2005-10-17
Heh, I don't even have mine consistently getting the network cards configured properly every bootup, I have to poke at Admin->Network every other boot.  But, time to get it working, I'll see if I can't figure out where these settings are all stored.

---

### Post by Rob2687 on 2005-10-19
How can you set up WPA? In the network settings I only see an option for WEP.

Edit: BTW Madwifi works perfectly with my SMCWCB-G. I think it is a pretty new model, I did a quick google and didn't come up with much. I remember there was some compatibility list for wireless cards, what's the link? or somebody just add this card :P
The only thing is that the status lights don't turn on.

---

### Post by pau on 2005-10-20
> what about a HOW-TO configure WPA-PSK to start up automatically when the card is detected during boot up ? 

Hi,

maybe this is of help for you

[http://www.aei.mpg.de/~pau/amilo_1425_linux_en.html](http://www.aei.mpg.de/~pau/amilo_1425_linux_en.html)

(look at WPA-PSK)

Hope it helps,

Pau

---

### Post by munkymonkjr on 2005-10-23
grr....follow this step by step and i get

ath_pci not found :(

---

### Post by barranco on 2005-10-25
[QUOTE=munkymonkjr]grr....follow this step by step and i get

ath_pci not found :([/QUOTE]

Happened the same thing to me but noticed in the echo that produced "make install" that the actual module was copied to the wrong directory *lib/modules/2.6.12* when my actual version is "2.6.12-9-386" yours should be the same if you are using breezy, you can check with the following command though:
```
uname -r
```

so I copied the /net folder that "make install" created to the appropiate directory and it worked.

FYI: I removed the restricted-modules package to have 3D acceleration, thus had to recompile madwifi.

---

### Post by dablitz on 2005-10-25
i have done the how to to the letter I am using kubuntu 5.10. for some reason the command modprobe cannot be found. is there anything I can do.:confused:

---

### Post by Griffin3 on 2005-10-25
If you cannot type modprobe and get a response, then (pardon me for being simple) maybe you are not logged in as root?  Try **sudo modprobe -l**

---

### Post by Xenus98 on 2005-10-25
Griffin3 : I did it ! WPA-PSK ! ! !

Tonight, I made it. My DLINK DWL-G650 is working in WPA-PSK as I am writing these lines ! I am also using Static IP, not DHCP like a lot of Guides are showing.
And for sure, this was not the more difficult.

So what I did ?
I cant tell which step was exactly missing to me but this is what I did tonight and that make me successful...

**1)** after a readme a guide I decided to use wpa_passphrase to encode my secret key instead of having it clearly written in my config file (/etc/wpa_supplicant.conf).

=> **wpa_passphrase your_SSID your_secret_passphrase_in_normal_text**

Ex : **wpa_passphrase HyperNetwork OpenTheDoor**

This command will generate a brief description of your network in WPA syntax.
The most important line to copy from is the "psk=..." with the Hex numbers.
This is the result of encoding your secret key.

**2)** Edit your /etc/wpa_supplicant.conf and modify the definition of your network, adding the newly generated psk secret key.

Here is a part of my wpa_supplicant.conf (network and psk key are fictif).
The line starting with a # are just a comment for reader and are not used by the config file.

....
[B]
#HERE START THE DEFINITION OF MY WIFI NETWORK....
network={
        ssid="HyperNetwork"
        proto=WPA
        scan_ssid=1
        key_mgmt=WPA-PSK
#       psk="OpenTheDoor"
        psk=38144375f57e9bdda07e97ab6a58c3f5cf794fc7d85a83fca95cc2b7
        pairwise=TKIP
        group=TKIP
}
[/B]
**3)** I also edited the file /etc/network/interfaces to remove any line refering to a WEP configuration previoulsy defined. I also fixed the static neetwork address of the interface. The network 11.2.3.0 is given here as an example. Replace these 3 number by your own local network values. If your AP is doing DNS forwarding, use it in the DNS list as a nameservers, if not, replace the IP by another DNS server.

....
[B]
iface ath0 inet static
        address 11.2.3.10
        netmask 255.255.255.0
        network 11.2.3.0
        broadcast 11.2.3.255
        gateway 11.2.3.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 11.2.3.1 66.249.93.99
[/B]

**4)** Run wpa_supplicant. There is a lot of post on how to do that.
You can run it in the background or in the foreground to help debugging.
That what I did. Example :
=>**wpa_supplicant -i ath0 -c /etc/wpa_supplicant.conf -D madwifi -w -d**
Option -d is for debug, you can start without it first even for simple messages.

to run it in the background, use option -B
=>**wpa_supplicant -B -i ath0 -c /etc/wpa_supplicant.conf -D madwifi -w**


**5)** Check that your wifi interface (ath0 for me) is up. This will fick a lot of people. If it doesnt want to go up, put it down first, again, and up again. Also, If you like, put down other interfaces that you dont use.
To be sure the interface wifi is down (replace ath0 by the name of your wifi interface)
=> **ifdown ath0**
put it up now !
=> **ifup ath0**

and try to ping [www.google.com](www.google.com) or to surf !!!

Hope it did help anybody !!
Next step for me is to put all this to start at boot time ! :))
This should be not too difficult.
See you allll ! !! ! ! !

---

### Post by dablitz on 2005-10-29
i got modprobe to work. but am now having this issue and device will not pull ip from my router. I am not running a wep at the moment, for testing purposes. but when I do an iwconfig this is what i get:

sat@ubuntu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

tunl0     no wireless extensions.

gre0      no wireless extensions.

Warning: Driver for device ath0 has been compiled with version 19
of Wireless Extension, while this program supports up to version 18.
Some things may be broken...

ath0      IEEE 802.11  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:0 kb/s   Tx-Power:20 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I have subsequently then tried :

iwconfig ath0 essid dablitz

it gets essid

ath0      IEEE 802.11  ESSID:"dablitz"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:0 kb/s   Tx-Power:20 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

but as you can see access point mac is still 00:00:00:00:00:00

if there is anyone who might be able to help me on this one, that would be great

using kubuntu 5.10, kernel 2.6.14, with a dlink DWL-G510 card.

---

### Post by dablitz on 2005-10-29
after playing with my system a bit i get this is a lsmod 
Module                  Size  Used by
rfcomm                 40232  0
l2cap                  27648  5 rfcomm
bluetooth              51236  4 rfcomm,l2cap
cpufreq_userspace       8352  0
cpufreq_stats           6724  0
freq_table              5760  1 cpufreq_stats
cpufreq_powersave       2688  0
cpufreq_ondemand        8552  0
cpufreq_conservative     9704  0
video                  18184  0
thermal                15884  0
processor              26920  1 thermal
fan                     5832  0
container               5696  0
button                  8288  0
battery                11208  0
ac                      6152  0
ipv6                  263552  14
af_packet              24780  2
floppy                 67848  0
pcspkr                  4808  0
ehci_hcd               33608  0
uhci_hcd               32736  0
ohci_hcd               21444  0
hw_random               6368  0
i2c_amd756              8068  0
amd74xx                15536  0 [permanent]
tpm_atmel               7488  0
tpm_nsc                 8384  0
tpm                    12128  2 tpm_atmel,tpm_nsc
tsdev                   8960  0
ath_pci                81440  0
ath_rate_sample        17104  1 ath_pci
wlan                  138100  2 ath_pci,ath_rate_sample
ath_hal               172144  2 ath_pci,ath_rate_sample
rtc                    14976  0
psmouse                37188  0
mousedev               12768  1
parport_pc             38192  0
lp                     13632  0
parport                40140  2 parport_pc,lp
unix                   31320  320


and when i ifconfig ath0 i get

ifconfig ath0 up
ath0: ERROR while getting interface flags: No such device


help!!!!!!!!!!!!!!!!!!!!!

---

### Post by bockman on 2005-10-30
I couldn't run **make** in the madwifi directory after **export KERNELPATH=/usr/src/linux-2.6.10**. It throws several screenfulls of errors at me:
```
/usr/src/madwifi/hal/ah.h:323: error: syntax error before "HAL_REG_DOMAIN"
/usr/src/madwifi/hal/ah.h:323: warning: type defaults to `int' in declaration of `HAL_REG_DOMAIN'
/usr/src/madwifi/hal/ah.h:323: warning: data definition has no type or storage class
/usr/src/madwifi/hal/ah.h:346: error: syntax error before "u_int8_t"
/usr/src/madwifi/hal/ah.h:346: warning: no semicolon at end of struct or union
/usr/src/madwifi/hal/ah.h:348: error: syntax error before "u_int8_t"
/usr/src/madwifi/hal/ah.h:348: warning: no semicolon at end of struct or union
/usr/src/madwifi/hal/ah.h:349: warning: type defaults to `int' in declaration of `phy'
/usr/src/madwifi/hal/ah.h:349: warning: data definition has no type or storage class
/usr/src/madwifi/hal/ah.h:350: error: syntax error before "rateKbps"
/usr/src/madwifi/hal/ah.h:350: warning: type defaults to `int' in declaration of `rateKbps'
/usr/src/madwifi/hal/ah.h:350: warning: data definition has no type or storage class
/usr/src/madwifi/hal/ah.h:351: error: syntax error before "rateCode"
/usr/src/madwifi/hal/ah.h:351: warning: type defaults to `int' in declaration of `rateCode'
/usr/src/madwifi/hal/ah.h:351: warning: data definition has no type or storage class
/usr/src/madwifi/hal/ah.h:352: error: syntax error before "shortPreamble"
/usr/src/madwifi/hal/ah.h:352: warning: type defaults to `int' in declaration of `shortPreamble'
/usr/src/madwifi/hal/ah.h:352: warning: data definition has no type or storage class
/usr/src/madwifi/hal/ah.h:354: error: syntax error before "dot11Rate"
/usr/src/madwifi/hal/ah.h:354: warning: type defaults to `int' in declaration of `dot11Rate'
/usr/src/madwifi/hal/ah.h:354: warning: data definition has no type or storage class
/usr/src/madwifi/hal/ah.h:356: error: syntax error before "controlRate"
/usr/src/madwifi/hal/ah.h:356: warning: type defaults to `int' in declaration of `controlRate'
/usr/src/madwifi/hal/ah.h:356: warning: data definition has no type or storage class
/usr/src/madwifi/hal/ah.h:358: error: syntax error before "lpAckDuration"
/usr/src/madwifi/hal/ah.h:358: warning: type defaults to `int' in declaration of `lpAckDuration'
/usr/src/madwifi/hal/ah.h:358: warning: data definition has no type or storage class

```
But much, much more. gcc 3.3.5, what should I do?

---

### Post by buddachile on 2005-10-30
I have the same problem trying to make although my KERNELPATH=/usr/src/linux-headers-2.6.12-9-386 and KERNELRELEASE=2.6.12-9-386.Make worked fine in Hoary,
but now with Breezy, no luck.

Actually, my DWL 510 wifi card works in Breezy, I just don't get the wireless connection at boot.  I have to use the System->Administration->Networking to deactivate/reactivate wireless for it to work, which is annoying.

Any ideas?

[QUOTE=bockman]I couldn't run **make** in the madwifi directory after **export KERNELPATH=/usr/src/linux-2.6.10**. It throws several screenfulls of errors at me:
```
/usr/src/madwifi/hal/ah.h:323: error: syntax error before "HAL_REG_DOMAIN"
/usr/src/madwifi/hal/ah.h:323: warning: type defaults to `int' in declaration of `HAL_REG_DOMAIN'
/usr/src/madwifi/hal/ah.h:323: warning: data definition has no type or storage class
/usr/src/madwifi/hal/ah.h:346: error: syntax error before "u_int8_t"
/usr/src/madwifi/hal/ah.h:346: warning: no semicolon at end of struct or union
/usr/src/madwifi/hal/ah.h:348: error: syntax error before "u_int8_t"
/usr/src/madwifi/hal/ah.h:348: warning: no semicolon at end of struct or union
/usr/src/madwifi/hal/ah.h:349: warning: type defaults to `int' in declaration of `phy'
 <snip>

```
But much, much more. gcc 3.3.5, what should I do?[/QUOTE]

---

### Post by bockman on 2005-11-01
[QUOTE=buddachile]I have the same problem trying to make although my KERNELPATH=/usr/src/linux-headers-2.6.12-9-386 and KERNELRELEASE=2.6.12-9-386.Make worked fine in Hoary,
but now with Breezy, no luck.

Actually, my DWL 510 wifi card works in Breezy, I just don't get the wireless connection at boot.  I have to use the System->Administration->Networking to deactivate/reactivate wireless for it to work, which is annoying.

Any ideas?[/QUOTE]
I remember how to fix it. Start **make**ing your kernel, let it run for about a minute, then stop it and then compile madwifi.

---

### Post by suRoot on 2005-11-02
I seem to be having some trouble getting this to work on my thinkpad (t40p).  I've followed the instructions here as well as the official madwifi site, but no dice.

I've built my own kernel based on 2.6.12 from kernel.org.  I built the modules base d on the instructions here:  [http://www.marlow.dk/site.php/tech/madwifi]("http://www.marlow.dk/site.php/tech/madwifi"), and I had no problems building the module.  It seems to load fine with my kernel:

```
$ lsmod | grep ath
ath_pci                70172  0
ath_rate_onoe           7432  1 ath_pci
wlan                  131612  2 ath_pci,ath_rate_onoe
ath_hal               146832  1 ath_pci
```

I've added

```
ath_pci
```

to the end of /etc/modules

I can find no trace of ath0, though!

```
$ ifconfig ath0
ath0: error fetching interface information: Device not found

$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:09:6B:3F:54:95
          inet addr:192.168.99.62  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe70::209:6bff:fe3f:5495/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1373 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1056 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:925233 (903.5 KiB)  TX bytes:162069 (158.2 KiB)
          Base address:0x8000 Memory:c0220000-c0240000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3608 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:328066 (320.3 KiB)  TX bytes:328066 (320.3 KiB)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

Under redhat, we'd always add an entry to /etc/modules.conf with something like "alias ath0 ath_pci", but that doesn't seem applicable with Debian / Ubuntu?  From what I read, it looked like you might do something similar under /etc/modules.d/, create a file with the name of the module, but that didn't make a bit of difference for me.

If I boot the default Breezy kernel, my wireless NIC does show up - it loads the ipw2100 module & shows up as eth1.  However, even though I can see the ssid of any of the access points I've tried, I never associate... never get an address, never get squat.  Based on the reading I've done about the T40P, I suspect that this is the wrong driver, anyway (everything I've read has said to use madwifi).

Can anyone offer any suggestions?  This is the only part of my laptop not working since installing Breezy.

Thanks!

---

### Post by vgeneral on 2005-11-03
Griffin3, I can't seem to get past your step #4.  I can successfully execute the followng:

cd /usr/src
wget [http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz](http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz)
tar -xzf madwifi-cvs-current.tar.gz
apt-get -y install sharutils
cd /usr/src/madwifi

but will receive a "Stop" notice after I try running the "make clean" command.  The error is posted below.

Makefile.inc:113:  ***  KERNALPATH:  does not exist.  Stop.

I'm not sure where the kernal path is.  Any idea on how to resolve this?

Thanks in advance for any help anybody can provide me.
ubuntu 5.10 / 2.6.12-9-386 / SMC2536W-AG card

---

### Post by suRoot on 2005-11-03
Try 

export KERNELPATH=/usr/source/path-to-kernel-source-or-kernel-headers

I actually have the kernel source from kernel.org, so I did:

export KERNELPATH=/usr/src/linux

and that worked, but if you're using the Breezy kernel, I think you have to first install the kernel-headers, sudo apt-get install kernel-headers (which I think installs to /usr/src)

---

### Post by SickTwist on 2005-11-03
I installed Hoary on a friend's laptop and compiled madwifi for her wireless adapter. Just to clarify, if I update her laptop to Breezy, her D-Link DWL-G630 will not need anything to be compiled if I install the restricted-modules package, right? Her set up is working perfect now and I don't want to ruin anything.

---

### Post by kise on 2005-11-12
I got the same error: have you found any solution?


[QUOTE=vgeneral]Griffin3, I can't seem to get past your step #4.  I can successfully execute the followng:

cd /usr/src
wget [http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz](http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz)
tar -xzf madwifi-cvs-current.tar.gz
apt-get -y install sharutils
cd /usr/src/madwifi

but will receive a "Stop" notice after I try running the "make clean" command.  The error is posted below.

Makefile.inc:113:  ***  KERNALPATH:  does not exist.  Stop.

I'm not sure where the kernal path is.  Any idea on how to resolve this?

Thanks in advance for any help anybody can provide me.
ubuntu 5.10 / 2.6.12-9-386 / SMC2536W-AG card[/QUOTE]

---

### Post by omni_Z on 2005-11-15
It's said in README of Madwifi-ng  that you have to do this:

wlanconfig ath0 create wlandev wifi0 wlanmode sta


at it worked with me, I had the same problem with "not such device ath0"


but have to figure out this working with suspend2, as wifi looses a connection and never resumes after resuming unless you unload and load modules and configure the interface again

---

### Post by JoelP on 2005-11-20
I have the same problem as forum member 'SuRoot'. Modules are installed etc. but no /dev/ath0 or /dev/wifi0 etc.

root@joel1:/usr/src/madwifi # modprobe -l | grep ath
/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko
/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ath_hal/ath_hal.ko
/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ath/ath_pci.ko
/lib/modules/2.6.10-5-386/kernel/drivers/md/multipath.ko

root@joel1:/usr/src/madwifi # lsmod | grep ath
ath_pci                55584  0
ath_rate_onoe           8840  1 ath_pci
wlan                  106588  2 ath_pci,ath_rate_onoe
ath_hal               133328  1 ath_pci

Any ideas?

---

### Post by omni_Z on 2005-11-21
[QUOTE=JoelP]I have the same problem as forum member 'SuRoot'. Modules are installed etc. but no /dev/ath0 or /dev/wifi0 etc.

Any ideas?[/QUOTE]


Did you try this command? 

# wlanconfig ath0 create wlandev wifi0 wlanmode sta

---

### Post by TrinitronX on 2005-12-11
Ok... I have just amazingly gotten this to work after a whole day's worth of working at it.  To be honest, I'm a noob at advanced linux stuff like this, so I really have no clue what the real problem was.  With this said, I have no clue how to salvage your current configurations, I only know the magic formula to follow.  The way in which I got to this point included compiling a custom kernel, and installing the current ati drivers to enable 3d accelleration for my card.  If you have no need for doing this, you should probably omit the ati installing part.

Here's what I did:
[list=1]
[*]Compile a new, custom kernel with support for my processor's optimizations/hyperthreading..etc..
[list=a]
[*]During this step, I followed the magic incantations here: [https://wiki.ubuntu.com/KernelHowto](https://wiki.ubuntu.com/KernelHowto)
[*]When I got to the xconfig part, I followed this page's recommendations for some settings related to my ATI card: [http://odin.prohosting.com/wedge01/gentoo-radeon-faq.html#kernel](http://odin.prohosting.com/wedge01/gentoo-radeon-faq.html#kernel)
[*]After I was through with xconfig, I kept following the Kernel How To instructions to the end.
[/list]
[*]Install the ATI drivers for my card.
[list=a]
[*]For this step, I followed the instructions found in this post: [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)
[*]Again, during the configuration part (using fglrxconfig), I went back and used this page as reference again (to make sure settings were correct): [http://odin.prohosting.com/wedge01/gentoo-radeon-faq.html#3_howinst](http://odin.prohosting.com/wedge01/gentoo-radeon-faq.html#3_howinst)
I paid special attention to the part that says "Do you want to use the external AGP GART module (y/n)?".  I remembered that I installed the AGP gart features into the kernel itself, so I answered yes to this question.
[*] After configuring the drivers using that last page, I kept following the instructions here: [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)
[/list]
[*]Install the madwifi drivers (since they weren't included in the kernel compile)
[list=a]
[*]I followed the instructions in this thread to the letter, except instead of doing all the steps in my old kernel (the one that still had wifi access), I did the apt-get steps in there, and then rebooted to perform the rest in my new custom kernel
[*]After the make install command, I went into /lib/modules, and looked around for the folder where the ath_pci and other modules were placed.  For me, they were found in a folder called 12.6.12 (my kernel version without the custom ending).  I then copied the entire /lib/modules/12.6.12/net folder over to my custom kernel folder in /lib/modules/, which happened to be /lib/modules/12.6.12.121005/.
After all this, I ended up with a directory listing like this: ```
trinitronx@Arcturus:/lib/modules/2.6.12.121005$ ls
build   modules.alias   modules.ieee1394map  modules.pcimap    modules.usbmap
kernel  modules.ccwmap  modules.inputmap     modules.seriomap  net
misc    modules.dep     modules.isapnpmap    modules.symbols   source

```
And in the /lib/modules/12.6.12.121005/net/ folder, it looks like this: ```
trinitronx@Arcturus:/lib/modules/2.6.12.121005/net$ ls
ath_hal.ko  ath_rate_sample.ko  wlan_ccmp.ko  wlan_tkip.ko  wlan_xauth.ko
ath_pci.ko  wlan_acl.ko         wlan.ko       wlan_wep.ko
```
[*] Only after copying the files to my kernels folder did the modprobe ath_pci command work.  I then checked if it worked using: lsmod | grep ath
which returned: ```
trinitronx@Arcturus:/lib/modules/2.6.12.121005/net$ lsmod | grep ath
ath_pci                80924  0
ath_rate_sample        17160  1 ath_pci
wlan                  145948  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               149072  3 ath_pci,ath_rate_sample
```
[/list]
[/list]

After a quick configuration of my wireless card from the 'networking' window, I am now able to type this using my new custom kernel.
 (The 'networking' window I'm speaking of is usually found under administration or utilities, depending on if you're using kde or gnome)

---

### Post by benplaut on 2005-12-11
is this the release that can do parallel scanning and connecting? i really want to be able to use GTKwifi...

---

### Post by elgordo123 on 2005-12-14
I just downloaded latest tarball of madwifi-ng and it will not compile.  I have installed sharutils, gcc-3.4 and linux-headers.  Before make I did export of GCC/usr/bin/gcc-3. 4 and also exported the correct linux headers.   here is what happens when I do make. 

Any help is greatly appreciated!  (Using kubuntu 5.10 breezy)

Checking requirements... ok.
Checking kernel configuration... ok.
mkdir -p ./symbols
for i in ./ath_hal ./net80211 ath_rate/sample ./ath ./tools ; do \
        make -C $i || exit 1; \
done
make[1]: Entering directory `/home/mark/madwifi-ng-r1352-20051211/ath_hal'
cp -f ./../hal/public/i386-elf.opt_ah.h opt_ah.h
cp -f ./../hal/linux/ah_osdep.c ah_osdep.c
/usr/bin/uudecode ./../hal/public/i386-elf.hal.o.uu
make -C /usr/src/linux-headers-2.6.12-10-686 SUBDIRS=/home/mark/madwifi-ng-r1352-20051211/ath_hal MODVERDIR=/home/mark/madwifi-ng-r1352-20051211/ath_hal/../symbols modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /home/mark/madwifi-ng-r1352-20051211/ath_hal/ah_osdep.o
  LD [M]  /home/mark/madwifi-ng-r1352-20051211/ath_hal/ath_hal.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /home/mark/madwifi-ng-r1352-20051211/ath_hal/.hal.o.cmd for /home/mark/madwifi-ng-r1352-20051211/ath_hal/hal.o
  CC      /home/mark/madwifi-ng-r1352-20051211/ath_hal/ath_hal.mod.o
  LD [M]  /home/mark/madwifi-ng-r1352-20051211/ath_hal/ath_hal.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make[1]: Leaving directory `/home/mark/madwifi-ng-r1352-20051211/ath_hal'
make[1]: Entering directory `/home/mark/madwifi-ng-r1352-20051211/net80211'
make -C /usr/src/linux-headers-2.6.12-10-686 SUBDIRS=/home/mark/madwifi-ng-r1352-20051211/net80211 MODVERDIR=/home/mark/madwifi-ng-r1352-20051211/net80211/../symbols modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /home/mark/madwifi-ng-r1352-20051211/net80211/if_media.o
cc1: warnings being treated as errors
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/mark/madwifi-ng-r1352-20051211/net80211/if_media.c:60:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
make[3]: *** [/home/mark/madwifi-ng-r1352-20051211/net80211/if_media.o] Error 1
make[2]: *** [_module_/home/mark/madwifi-ng-r1352-20051211/net80211] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/mark/madwifi-ng-r1352-20051211/net80211'
make: *** [all] Error 1

---

### Post by TrinitronX on 2005-12-14
Try searching through the makefile for "-Werror" and removing it.  That way the compiler won't treat the warning as an error.  I found this same problem here: [http://www.mail-archive.com/madwifi-tickets@lists.sourceforge.net/msg00420.html](http://www.mail-archive.com/madwifi-tickets@lists.sourceforge.net/msg00420.html)

---

### Post by CaptainMorgan on 2005-12-15
[QUOTE=vgeneral]Griffin3, I can't seem to get past your step #4.  I can successfully execute the followng:

cd /usr/src
wget [http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz](http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz)
tar -xzf madwifi-cvs-current.tar.gz
apt-get -y install sharutils
cd /usr/src/madwifi

but will receive a "Stop" notice after I try running the "make clean" command.  The error is posted below.

Makefile.inc:113:  ***  KERNALPATH:  does not exist.  Stop.

I'm not sure where the kernal path is.  Any idea on how to resolve this?

Thanks in advance for any help anybody can provide me.
ubuntu 5.10 / 2.6.12-9-386 / SMC2536W-AG card[/QUOTE]


Im still on hoary because of a mishap with Breezy.... I tried to follow instructions.. and I get the same error. I tried export KERNELPATH=/usr/source/path-to-kernel-source-or-kernel-headers and apt-get install-headers... 

any suggestions ?

Thanks

---

### Post by ErikTheRed on 2006-01-13
I tried to follow this guide for installing my dlink card on 64-bit Kubuntu, but I get to the 'make' step and get stuck.

I get this error:
> /bin/sh: /pub/gnu/bin/x86_64-linux-gcc: No such file or directory

I don't even have a /pub folder if that helps at all. Any help would be appreciated.

---

### Post by dninja on 2006-04-20
I've followed these instructions and all works well when I have WEP turned off, as soon as I turn it on I can't get a connection. The card works out the bssid of the AP but won't talk to it any further than that.

This is with the old drivers, with the new ones I can't even get it to associate without WEP.

Any ideas?

---

### Post by m4r3k on 2006-04-20
hi i'm a total newby and i have some porblem with this line
apt-get install build-essential bin86 sharutils gcc-3.4 linux-headers-$(uname -r);
it say's bin86 not found??

can somebody help me??

i have 5.10 ubuntu and d-link dwl g-520 atheros chipset


thnx

---

### Post by slimpinto on 2006-08-06
Kind of in a pinch and need the Ubuntu masters help! I have an Atheros (Cisco) based wireless adapter and was told by a friend that using madwifi, I  could turn my linux box into an access point. When I try to setup madwifi ([http://www.ubuntuforums.org/showthread.php?t=75451](http://www.ubuntuforums.org/showthread.php?t=75451)) it fails:

```
xxxx@xxxx-router:/usr/src/madwifi$ make clean
for i in ./ath ath_rate/sample ./net80211; do \
                make -C $i clean; \
        done
make[1]: Entering directory `/usr/src/madwifi/ath'
rm -f *~ *.o *.ko *.mod.c uudecode .*.cmd
rm -f .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/usr/src/madwifi/ath'
make[1]: Entering directory `/usr/src/madwifi/ath_rate/sample'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/usr/src/madwifi/ath_rate/sample'
make[1]: Entering directory `/usr/src/madwifi/net80211'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/usr/src/madwifi/net80211'
make -C ./tools  clean
make[1]: Entering directory `/usr/src/madwifi/tools'
rm -f athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig core a.out
make[1]: Leaving directory `/usr/src/madwifi/tools'
rm -rf .tmp_versions
rm -f Modules.symvers svnversion.h
xxxx@xxxx-router:/usr/src/madwifi$ make
Checking requirements... ok.
Checking kernel configuration... FAILED
Please enable wireless extensions.
make: *** [configcheck] Error 1
```

```
xxxx@xxxx-router:/usr/src/madwifi$ sudo lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4800] (rev a1)
0000:02:06.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
xxxx@xxxx-router:/usr/src/madwifi$ sudo lsmod | grep ath
ath_pci                80540  0
ath_rate_sample        17160  1 ath_pci
wlan                  144924  3 ath_pci,ath_rate_sample
ath_hal               148816  3 ath_pci,ath_rate_sample
```

I hope I've included enough info...For the record, I have used the almighty SEARCH button, but have had no luck for the past 1.5 days....

My level of expertise is 'so-so' when it comes to Linux in general. But I can follow guides and instructions very well. I think there's a little misconception from the expert Linux users helping us novices. What I mean is, there seems to be a lot of assumptions made, that well...maybe us novices actually know some of the basics that you experts take for granted. Don't take this the wrong way, because I think it's awesome that you even take the time to help, but relaize we probably don't have the same basic skill set that you have, yet...

For example, my problem setting up madwifi...I've had to read at least 4 other Forum threads about updating repositories, installing a plethora of "other" packages, and now it seems I may need to compile a new kernel. Following the guide I mentioned above doesn't have those details and is making this process a bit harder than I feel it should be.

Let me suggest that those expert Linux users when replying to a thread with help, that you include a simple "Prerequisite" section. This way, all of us novices will at least not run into anything unexpected.  End rant...  ;-p

BTW...Thanks in advance for any and all help!

~Slim Out!~

[NOTE: For clarification... I hope this didn't sound too condecending, as that was not my intent. I was only offering friendly suggestions to the experts. Please don't take my comments out of context. Thanks!]

---

### Post by isharra on 2006-08-11
The error message you gave means you are compiling against unconfigured kernel source. Or have no source at all. If you actually compiled a new kernel, you forgot to enable the wireless extensions.

I'm uncertain if you can get away with just installing the kernel headers or if you need to get the full source. (I've always done this with the full source installed.) if you are interested in compiling a custom kernel [Kernel Compilation Dapper]("http://doc.gwos.org/index.php/Kernel_Compilation_Dapper") is a good guide.

To get the headers that match your already installed kernel:  ```
sudo aptitude install linux-headers-`uname -r`
```
I'm afraid I can't give you step by step directions. I have my access point set up under gentoo (the laptop with ubuntu is a supplicant). I do know the madwifi package for debian/ubuntu is heavily modified mix of madwifi-old and madwifi so you might need to recompile for best results.

You need a properly configured kernel (the ubuntu kernel does have the required options already configured), wirless card drivers (madwifi is included in the restricted-modules package which should have been installed when you installed your kernel), wireless-tools (if you compile new versions of madwifi you should compile new wireless-tools as well), hostapd and (only if you are planning on bridging wireless and wired networks) bridge-utils.

One of the clearest writeups of how to configure an access point with madwifi and hostapd was given at linux.com [Create a secure Linux-based wireless access point]("http://www.linux.com/article.pl?sid=06/07/10/1729226"). It does assume you have the required packages already installed.

It's a shame I didn't find this thread until after I had wireless working.

---

### Post by Emo_Samurai on 2006-12-09
The link is kinda outdated. Could somebody update the guide? I'm a complete linux n00b.

---

### Post by tturrisi on 2006-12-09
fyi, there is a new madwifi release to fix a major security issue:
[http://madwifi.org/](http://madwifi.org/)  (see latest news)

---

### Post by antimac on 2008-07-18
so I followed the instructions didn't see any errors, restarted the computer but the device doesn't show up under administrator - Network. If I run any ifconfig, iwconfig, etc....the device is not shown. Any ideas?

---

### Post by masterme120 on 2008-08-08
First of all, I am very new to linux.  I tried to install madwifi, but I got stuck on the last step.  How do I configure ath0?

---

### Post by contrafactus on 2011-03-03
I get: wget: unable to resolve host address `madwifi.otaku42.de'

---

### Post by HackSwiTcH on 2011-09-02
you wrote

[LIST=1]
[*]Compile the module
[code]cd /usr/src
wget http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz
[/LIST]
root@Toshiba-Satellite:/usr/src# wget http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz
--2011-09-02 14:35:39--  http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz
Resolving madwifi.otaku42.de... failed: Name or service not known.
wget: unable to resolve host address `madwifi.otaku42.de'


Above is my output, Is there another place to get mad wifi? a lot of the links on the page are down as well..  I am running Ubuntu 11.4 and using card "Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c]"

---

