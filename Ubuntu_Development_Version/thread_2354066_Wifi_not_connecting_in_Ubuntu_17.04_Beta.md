---
title: "Wifi not connecting in Ubuntu 17.04 Beta"
date: 2017-02-27
forum: Ubuntu Development Version
---

### Post by samuelkenno on 2017-02-27
Hello. 

I ran the Ubuntu 17.04 from USB stick. in order to test it. 

Wifi works normally out of the box in Kubuntu 16.04 and 16.10 but not in 17.04.

However I am unable to connect to any wifi network. I'm able to scan the wifi networks around but it happens an error when I try to connect.

I tested also in Kubuntu 17.04 same problem. I already collected some information that could be useful.

I think this might be important to fix before release once this might affect other ubuntu users.

Already tried to google for some solutions but looks like a new problem.

```
Feb 27 22:21:23 ubuntu-budgie NetworkManager[1845]: <info>  [1488234083.4743] Config: added 'ssid' value 'Valim'
Feb 27 22:21:23 ubuntu-budgie NetworkManager[1845]: <info>  [1488234083.4746] Config: added 'scan_ssid' value '1'
Feb 27 22:21:23 ubuntu-budgie NetworkManager[1845]: <info>  [1488234083.4749] Config: added 'key_mgmt' value 'WPA-PSK'
Feb 27 22:21:23 ubuntu-budgie NetworkManager[1845]: <info>  [1488234083.4751] Config: added 'auth_alg' value 'OPEN'
Feb 27 22:21:23 ubuntu-budgie NetworkManager[1845]: <info>  [1488234083.4753] Config: added 'psk' value '<omitted>'
Feb 27 22:21:23 ubuntu-budgie NetworkManager[1845]: <info>  [1488234083.4765] sup-iface[0x560c6965ec30,wlx48ee0cd9b398]: config: set interface ap_scan to 1
Feb 27 22:21:23 ubuntu-budgie wpa_supplicant[2260]: wlx48ee0cd9b398: SME: Trying to authenticate with 18:62:2c:ca:90:8c (SSID='Valim' freq=2432 MHz)
Feb 27 22:21:23 ubuntu-budgie kernel: [  242.954905] wlx48ee0cd9b398: authenticate with 18:62:2c:ca:90:8c
Feb 27 22:21:23 ubuntu-budgie NetworkManager[1845]: <info>  [1488234083.5114] device (wlx48ee0cd9b398): supplicant interface state: inactive -> authenticating
Feb 27 22:21:23 ubuntu-budgie kernel: [  242.979527] wlx48ee0cd9b398: send auth to 18:62:2c:ca:90:8c (try 1/3)
Feb 27 22:21:23 ubuntu-budgie kernel: [  242.981346] wlx48ee0cd9b398: authenticated
Feb 27 22:21:28 ubuntu-budgie wpa_supplicant[2260]: wlx48ee0cd9b398: SME: Deauth request to the driver failed
Feb 27 22:21:28 ubuntu-budgie wpa_supplicant[2260]: wlx48ee0cd9b398: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Valim" auth_failures=1 duration=10 reason=CONN_FAILED
Feb 27 22:21:28 ubuntu-budgie NetworkManager[1845]: <info>  [1488234088.5225] device (wlx48ee0cd9b398): supplicant interface state: authenticating -> disconnected
Feb 27 22:21:38 ubuntu-budgie NetworkManager[1845]: <info>  [1488234098.5279] device (wlx48ee0cd9b398): supplicant interface state: disconnected -> scanning
Feb 27 22:21:39 ubuntu-budgie wpa_supplicant[2260]: wlx48ee0cd9b398: CTRL-EVENT-SSID-REENABLED id=0 ssid="Valim"
Feb 27 22:21:39 ubuntu-budgie wpa_supplicant[2260]: wlx48ee0cd9b398: SME: Trying to authenticate with 18:62:2c:ca:90:8c (SSID='Valim' freq=2432 MHz)
Feb 27 22:21:39 ubuntu-budgie kernel: [  259.320219] wlx48ee0cd9b398: authenticate with 18:62:2c:ca:90:8c
Feb 27 22:21:39 ubuntu-budgie NetworkManager[1845]: <info>  [1488234099.9080] device (wlx48ee0cd9b398): supplicant interface state: scanning -> authenticating
Feb 27 22:21:39 ubuntu-budgie kernel: [  259.376041] wlx48ee0cd9b398: send auth to 18:62:2c:ca:90:8c (try 1/3)
Feb 27 22:21:39 ubuntu-budgie kernel: [  259.377651] wlx48ee0cd9b398: authenticated
Feb 27 22:21:44 ubuntu-budgie wpa_supplicant[2260]: wlx48ee0cd9b398: SME: Deauth request to the driver failed
Feb 27 22:21:44 ubuntu-budgie wpa_supplicant[2260]: wlx48ee0cd9b398: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Valim" auth_failures=2 duration=20 reason=CONN_FAILED
Feb 27 22:21:44 ubuntu-budgie NetworkManager[1845]: <info>  [1488234104.9171] device (wlx48ee0cd9b398): supplicant interface state: authenticating -> disconnected
Feb 27 22:21:48 ubuntu-budgie NetworkManager[1845]: <warn>  [1488234108.7306] device (wlx48ee0cd9b398): Activation: (wifi) association took too long, failing activation
Feb 27 22:21:48 ubuntu-budgie NetworkManager[1845]: <info>  [1488234108.7307] device (wlx48ee0cd9b398): state change: config -> failed (reason 'ssid-not-found') [50 120 53]
Feb 27 22:21:48 ubuntu-budgie NetworkManager[1845]: <info>  [1488234108.7312] manager: NetworkManager state is now DISCONNECTED
Feb 27 22:21:48 ubuntu-budgie NetworkManager[1845]: <warn>  [1488234108.7328] device (wlx48ee0cd9b398): Activation: failed for connection 'Valim'
Feb 27 22:21:48 ubuntu-budgie NetworkManager[1845]: <info>  [1488234108.7346] device (wlx48ee0cd9b398): state change: failed -> disconnected (reason 'none') [120 30 0]
Feb 27 22:21:48 ubuntu-budgie kernel: [  268.204887] IPv6: ADDRCONF(NETDEV_UP): wlx48ee0cd9b398: link is not ready
Feb 27 22:21:49 ubuntu-budgie NetworkManager[1845]: <info>  [1488234109.3045] device (wlx48ee0cd9b398): set-hw-addr: set MAC address to 9E:60:F8:99:EF:36 (scanning)
Feb 27 22:21:49 ubuntu-budgie kernel: [  269.038123] IPv6: ADDRCONF(NETDEV_UP): wlx48ee0cd9b398: link is not ready
Feb 27 22:21:50 ubuntu-budgie NetworkManager[1845]: <info>  [1488234110.9051] device (wlx48ee0cd9b398): supplicant interface state: disconnected -> inactive
```

```
root@ubuntu-budgie:~# lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 002: ID 3538:0059 Power Quotient International Co., Ltd 
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 2001:3c22 D-Link Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 04b3:310c IBM Corp. Wheel Mouse
Bus 005 Device 002: ID 258a:0001  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@ubuntu-budgie:~# ifconfig
enp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether fc:aa:14:71:67:27  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)ls
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 43  bytes 6028 (6.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 327  bytes 24241 (24.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 327  bytes 24241 (24.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlx48ee0cd9b398: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 9e:60:f8:99:ef:36  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

```
root@ubuntu-budgie:~# lsmod | grep -i rt
rt2800usb              28672  0
rt2x00usb              20480  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              53248  3 rt2800lib,rt2800usb,rt2x00usb
mac80211              778240  3 rt2800lib,rt2x00lib,rt2x00usb
cfg80211              589824  2 rt2x00lib,mac80211
parport_pc             32768  0
parport                49152  3 lp,parport_pc,ppdev
```

---

### Post by howefield on 2017-02-27
Moved to the "*Ubuntu/Debian BASED*" forum and code tags added to the OP.

---

### Post by davidmohammed on 2017-02-28
@howefield - wrong forum - should be here [https://ubuntuforums.org/forumdisplay.php?f=427](https://ubuntuforums.org/forumdisplay.php?f=427)

---

### Post by howefield on 2017-02-28
@davidmohammed - correct forum.

> Ubuntu Specialised Support
Specialised categories of support for the recognised Ubuntu flavours: Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, Mythbuntu, Ubuntu Mate, and Ubuntu Kylin.

With the release of 17.04 Ubuntu Budgie will be added to the above tagline for the main support forums.

Good to see you here, perhaps you can give the OP some advice.

---

### Post by davidmohammed on 2017-02-28
@howefield - this is not a flavour specific issue - probably something to-do with the 4.10 kernel at a guess.  As the OP mentioned this affects Kubuntu as well.  Those that hang out in development 17.04 forum would be a better bet here.

---

### Post by cariboo on 2017-02-28
Moved to here, for quicker help.

---

### Post by ventrical on 2017-02-28
> **samuelkenno said:**
> Hello. 

I ran the Ubuntu 17.04 from USB stick. in order to test it. 

Wifi works normally out of the box in Kubuntu 16.04 and 16.10 but not in 17.04.

However I am unable to connect to any wifi network. I'm able to scan the wifi networks around but it happens an error when I try to connect.

I tested also in Kubuntu 17.04 same problem. I already collected some information that could be useful.

I think this might be important to fix before release once this might affect other ubuntu users.



16.04 release presented this very same problem. You have to go into network connections, open a wireless instance, and enter your WEP. I forget exactly what the bug was.

Regards..

---

### Post by cariboo on 2017-02-28
Nobody uses WEP any more, as it is so easy to hack, you should use WPA & WPA2

---

### Post by ventrical on 2017-03-01
> **cariboo said:**
> Nobody uses WEP any more, as it is so easy to hack, you should use WPA & WPA2

I must be a dinosaur then :)

---

### Post by cariboo on 2017-03-01
There are enough access points in my neighbourhood, that I don't want to take the chance.

[[img]https://s8.postimg.org/pvfblpz0x/Screenshot_2017_03_01_02_11_18.png[/img]](https://postimg.org/image/pvfblpz0x/)

---

### Post by rrnbtter on 2017-03-01
Greetings,
I have had no problems with my 17.04 WIFI.  In addition I use WPA2 with a 63 character PW and a 18 character AP name (calculate a rainbow table for that).  Remember, just because you are not paranoid doesn't mean nobody is out to get you!

---

### Post by samuelkenno on 2017-03-01
My Router doesn't even have the option to chose WEP.

Anyway. I tried to connect to open network but got the same error.

---

### Post by cariboo on 2017-03-01
Have you run the wireless-info script?

Make sure you have pastebinit installed, it's in the repositories. Then when asked when the script is finished running it will automatically upload the results to pastebin. Copy the url it gives, and paste it into your next post.

```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

---

### Post by samuelkenno on 2017-03-01
Hello. Here is the info you requested:

This is the output ran from Ubuntu 17.04 beta which is not working.

[http://pastebin.com/ESx2DTnX](http://pastebin.com/ESx2DTnX)

---

### Post by samuelkenno on 2017-03-01
May be it's useful to post the wireless-info output from my Kubuntu 16.10 which is working normally. 

[http://pastebin.com/z5HMWLP4](http://pastebin.com/z5HMWLP4)

---

### Post by ventrical on 2017-03-02
> **samuelkenno said:**
> Hello. Here is the info you requested:

This is the output ran from Ubuntu 17.04 beta which is not working.

[http://pastebin.com/ESx2DTnX](http://pastebin.com/ESx2DTnX)

I notice kernel 4.9.0-15 on your install

Current kernel is 4.10.0-8

edit:

Actually 4.10.0-9 now

I wonder if update/upgrade might help.

Regards..

---

### Post by wildmanne39 on 2017-03-02
Please do:
```
sudo dpkg-reconfigure resolvconf
```
then answer 'Yes' to the "Prepare /etc/resolv.conf for dynamic updates?" question and 'No' to the one about temporarily appending your existing config to the dynamic one, then reboot. It may not ask the second question in the newer version of Ubuntu.

Then do:
```
echo "options rt2800usb nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800usb.conf 
sudo modprobe -rfv rt2800usb 
sudo modprobe -v rt2800usb 
```
The first command should make you able to connect and the second one will make the connection more stable and faster, there are other things  to improve connection that can be done later.
Thanks

---

### Post by cariboo on 2017-03-02
Thanks Wild Man.

---

### Post by wildmanne39 on 2017-03-03
Your welcome cariboo.

---

### Post by samuelkenno on 2017-03-03
I got this output from 1st command.

[FONT=monospace][COLOR=#000000]dpkg-query: package 'resolv.conf' is not installed and no information is available[/COLOR]
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: resolv.conf is not installed

[/FONT]

---

### Post by wildmanne39 on 2017-03-03
Did you try to install the package?

---

### Post by wildmanne39 on 2017-03-03
I fixed the command, it should not have  the period in it, sorry about that.

---

### Post by samuelkenno on 2017-03-04
> **wildmanne39 said:**
> Please do:
```
sudo dpkg-reconfigure resolvconf
```
then answer 'Yes' to the "Prepare /etc/resolv.conf for dynamic updates?" question and 'No' to the one about temporarily appending your existing config to the dynamic one, then reboot. It may not ask the second question in the newer version of Ubuntu.

Then do:
```
echo "options rt2800usb nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800usb.conf 
sudo modprobe -rfv rt2800usb 
sudo modprobe -v rt2800usb 
```
The first command should make you able to connect and the second one will make the connection more stable and faster, there are other things  to improve connection that can be done later.
Thanks


I tried this process. And I upgraded all the packages. Now i'm running Kernel 4.10.
Unfortunately. No Success. :(

---

### Post by samuelkenno on 2017-03-04
This is the information updated in pastebin:

[http://pastebin.com/g1qjFhXe](http://pastebin.com/g1qjFhXe)

I moved the PC to a place close to router in order to connect a cable and update the system. 
Still trying to fix the wifi.

---

### Post by wildmanne39 on 2017-03-04
With the new kernel the resolvconf file is still this:
```
nameserver 127.0.0.53
```
Let's just add the google nameserver they are always faster anyway.

To add the google nameservers 8.8.8.8 and 8.8.4.4) in "IPv4-settings" in the network-manager applet.

Right-click->Edit connections->choose your connection->Edit->IPv4-setings

Change to "Automatic (DHCP), addresses only" and add the nameservers in the field "DNS-servers" like this
```
8.8.8.8,8.8.4.4
```
Then go into IPV6 tab and set to ignore, save and close network manager, please refer to the screenshots.

Restart the network after that by doing:
```
sudo systemctl restart NetworkManager.service
```
We are going to turn power management off:
```
sudo sed -i 's/wifi.powersave = 2/wifi.powersave = 3/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Let's set the country code for the router:
If you are in Brazil please do:
```
sudo iw reg set BR
sudo sed -i 's/^REG.*=$/&BR/' /etc/default/crda
```
If it does not connect post a new file and tell me the name of the network you are trying to connect too.

Also dmesg shows your device is being seen as two different devices.

---

### Post by samuelkenno on 2017-03-04
Hey. 

resolv.conf is right. I ran the commands and set the network settings like you said, still no success. 

I'm trying to connect to Valim network.

[http://pastebin.com/nNDj2xPc](http://pastebin.com/nNDj2xPc)

---

### Post by user817 on 2017-03-04
I was testing out 17.04 and I had the same results as you Samuel. When I typed in my wifi password it would just spin for a second then stop. It never connected. I'm hoping whatever solves your problem will solve mine too. I got pissed and uninstalled it, but I'm going to install the latest iso as of March 4. I'll let you know if this one works any better.

**EDIT: **new version never worked either. I'm not sure where to go from here.

---

### Post by tajreed on 2017-03-05
Re-installed 17.04 from latest release Mar 4th and all is well with wi-fi.

---

### Post by samuelkenno on 2017-03-05
> **tajreed said:**
> Re-installed 17.04 from latest release Mar 4th and all is well with wi-fi.


I today tried with 17.04 Mar 5th release but still no success. 


In 16.10 release it works just out of the box.

---

### Post by samuelkenno on 2017-03-05
I just found that many people are facing this problem when upgraded to kernel 4.9 and 4.10. 

Many people downgraded the kernel in order to fix.

May be this is a bug in new kernel it self and not just in ubuntu.

---

### Post by wildmanne39 on 2017-03-05
>  May be this is a bug in new kernel it self and not just in ubuntu. 
I suspect it may be but we work around most of them all the time in networking.
>  resolv.conf is right. I ran the commands and set the network settings like you said, still no success. 
When did you run the command to change resolvconf it was before you installed the new kernel right? if so that probably voided the change.

According to the new file you posted this:
```
nameserver 127.0.0.53
```
never did change and if you changed the setting in network manager like I suggested in my last post for the nameserver 8.8.8.8,8.8.4.4 they did not stick. 

The IPV6 to ignore stuck but it is for the valim 1 which needs to be completely removed and then reboot and let network manager find your connection, then change the settings in network manager to match the screenshots for the correct network.

Your network needs to connect to valim but it is connecting to valim1 and that is the name of the network you changed the settings for, see below.

```
[[/etc/NetworkManager/system-connections/Valim 1]] (600 root)
[connection] id=Valim 1 | type=wifi | permissions=user:valim:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Valim
[ipv4] method=auto
[ipv6] method=ignore
```
This is the only one you want to change and the only one that needs to be listed:
```
[[/etc/NetworkManager/system-connections/Valim]] (600 root)
[connection] id=Valim | type=wifi | permissions=user:ubuntu-budgie:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Valim
[ipv4] method=auto
[ipv6] method=auto
 
```

This is what I was referring to in my other post about an error in dmesg:
```
[   12.843323] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5392, rev 0223 detected
[   12.871944] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5372 detected
```
Your card is being detected has two different cards,  I believe they both use the same driver but it is probably creating confusion.

Please post the output for:
```
modinfo rt2800usb | grep 3c22
```
I apologize for replying slow but I am a little under the weather at the moment.

---

### Post by samuelkenno on 2017-03-05
Yes I did the resolvconf reconfigure before the kernel update.

I fixed the Valim network and removed Valim 1

```

root@valim-pc:/etc/NetworkManager/system-connections# cat Valim
[connection]
id=Valim
uuid=152d3322-5810-4eaf-9e6f-eabe000dea93
type=wifi
permissions=user:valim:;
secondaries=


[wifi]
mac-address=48:EE:0C:D9:B3:98
mac-address-blacklist=
mac-address-randomization=0
mode=infrastructure
seen-bssids=
ssid=Valim


[wifi-security]
group=
key-mgmt=wpa-psk
pairwise=
proto=
psk=1qaz2wsx


[ipv4]
dns=8.8.8.8;8.8.4.4;
dns-search=
ignore-auto-dns=true
method=auto


[ipv6]
addr-gen-mode=stable-privacy
dns-search=
ip6-privacy=0
method=ignore



```


The command ""[COLOR=#000000][FONT=&amp]modinfo rt2800usb | grep 3c22"" returned no output so I added -i to grep:


[/FONT][/COLOR]```


root@valim-pc:/# modinfo rt2800usb | grep -i 3c22
alias:          usb:v2001p3C22d*dc*dsc*dp*ic*isc*ip*in*





```

---

### Post by jeremy31 on 2017-03-05
> **samuelkenno said:**
> I just found that many people are facing this problem when upgraded to kernel 4.9 and 4.10. 

Many people downgraded the kernel in order to fix.

May be this is a bug in new kernel it self and not just in ubuntu.
I think you should submit a bug report against package linux, see [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

This info needs to be submitted so that it can be corrected before the release if it is possible

---

### Post by wildmanne39 on 2017-03-05
We have done almost all we can do, but I would like to see a new file to see if the changes in network manger of setting the nameservers to google 8.8.8.8,8.8.4.4 took effect and is so it just needs to be reported as a bug.

---

### Post by wildmanne39 on 2017-03-05
Everything you posted looks good.

---

### Post by wildmanne39 on 2017-03-05
Looks like you also have a network manager bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1576747](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1576747)
there is a work around but it seems it may not work in 17.04, but run the following command and see if it will connect please:
```
sudo systemctl restart NetworkManager.service
```
if it does that is because of the other clean up work we have done.
Thanks

---

### Post by samuelkenno on 2017-03-07
Sorry. For taking log to respond.

I did the last changes no success yet and ran the command "[COLOR=#000000][FONT=&quot]sudo systemctl restart NetworkManager.service"

[/FONT][/COLOR]No Luck.

---

### Post by Cheltspy on 2017-03-12
Same issue after upgrade from Yakkety will not connect to anything even though logs says  authenticated

It's not kernel 4.10 either I have been using that for weeks on 16.10.

It seems like Network Manger issue

---

### Post by Cheltspy on 2017-03-14
Downgrading Network Manger to 1.2.6 restores normal operation.

Packages from 16.10 needed to downgrade.
libnma0_1.2.6-0ubuntu1.1
libnma-common_1.2.6-0ubuntu1.1_all
network-manager_1.2.6-0ubuntu1
network-manager-gnome_1.2.6-0ubuntu1.1

---

### Post by grahammechanical on 2017-03-15
I have had this problem for some weeks. Today's ISO image (20170315) does not have Internet access. I have both ethernet and WiFi. The ethernet connection is not recognized. When trying to install I am asked to set up a WiFi connection but even with the correct wireless passphrase the live session fails to connect to the router.

The installation can proceed but without updates being installed at the same time. And the newly installed 17.04 does not have Internet access. This command

```
nmcli networking connectivity
```

gives the response *full* This means the system is connected to the router and the Internet. If the response was *limited* it would indicate *host connected to network but no access to internet*

The nmcli diagnostic commands lie. They do not detect any problem. I now have 3 x 17.04 installs without Internet access. (a) an install from the beginning of the development period that lost Internet access a couple of months ago after an update; (b) a 16.10 install that was online upgraded to 17.04 and lost Internet access once the upgrade was completed; (c) a fresh install of the latest daily ISO image.

Is this a conspiracy to prevent me from reading fake news? :)

Regards

---

### Post by wildmanne39 on 2017-03-15
The OP has a network manager bug and a bug that shows his device as two different devices, I recommend filing a bug report.

---

### Post by Cheltspy on 2017-03-16
I have found a fix that has been reported here to bugzilla.
[https://bugzilla.gnome.org/show_bug.cgi?id=780119](https://bugzilla.gnome.org/show_bug.cgi?id=780119)

Open
/etc/NetworkManager/NetworkManager.conf

add lines
[device]
wifi.scan-rand-mac-address=0

This got me connected again.

---

### Post by user817 on 2017-03-18
> **Cheltspy said:**
> I have found a fix that has been reported here to bugzilla.
[https://bugzilla.gnome.org/show_bug.cgi?id=780119](https://bugzilla.gnome.org/show_bug.cgi?id=780119)

Open
/etc/NetworkManager/NetworkManager.conf

add lines
[device]
wifi.scan-rand-mac-address=0

This got me connected again.

That worked for me too. Not really sure what that code does as I'm relatively new to Ubuntu, but thank you.

---

### Post by 00b00nt00 on 2017-03-18
Kernel 4.10 doesn't play nicely with the Realtek adapter in my HP Stream 11. Wifi connects, then stalls in Firefox. Oddly enough, I'm able to download updates via the terminal. Unfortunately, kernel 4.4 in 16.04 doesn't support my Stream well, so 16.10 is the only option for me.

---

### Post by jeremy31 on 2017-03-18
> **00b00nt00 said:**
> Kernel 4.10 doesn't play nicely with the Realtek adapter in my HP Stream 11. Wifi connects, then stalls in Firefox. Oddly enough, I'm able to download updates via the terminal. Unfortunately, kernel 4.4 in 16.04 doesn't support my Stream well, so 16.10 is the only option for me.

If the Realtek wifi is an rtl8723be, the ant_sel parameter of the module is important with the newer HP laptops

---

### Post by samuelkenno on 2017-03-20
> **Cheltspy said:**
> I have found a fix that has been reported here to bugzilla.
[https://bugzilla.gnome.org/show_bug.cgi?id=780119](https://bugzilla.gnome.org/show_bug.cgi?id=780119)

Open
/etc/NetworkManager/NetworkManager.conf

add lines
[device]
wifi.scan-rand-mac-address=0

This got me connected again.

I fixed my wifi as well thank you.

---

### Post by mibakh on 2017-03-27
Hi,
I upgrade from 16.10 to 17.04 and my realtek wireless device not working...(still connecting...)

lsusb :

```
Bus 003 Device 012: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
-------------------------------
dmesg :

```
[57066.196508] usb 3-1: new high-speed USB device number 12 using xhci_hcd
[57066.353368] usb 3-1: New USB device found, idVendor=148f, idProduct=3070
[57066.353370] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[57066.353372] usb 3-1: Product: 802.11 n WLAN
[57066.353373] usb 3-1: Manufacturer: Ralink
[57066.353374] usb 3-1: SerialNumber: 1.0
[57066.472611] usb 3-1: reset high-speed USB device number 12 using xhci_hcd
[57066.623391] ieee80211 phy6: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[57066.633789] ieee80211 phy6: rt2x00_set_rf: Info - RF chipset 0005 detected
[57066.634256] ieee80211 phy6: Selected rate control algorithm 'minstrel_ht'
[57066.647976] rt2800usb 3-1:1.0 wlxc4e9840f3c86: renamed from wlan0
[57066.677710] IPv6: ADDRCONF(NETDEV_UP): wlxc4e9840f3c86: link is not ready
[57066.677760] ieee80211 phy6: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[57066.677807] ieee80211 phy6: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[57067.191615] IPv6: ADDRCONF(NETDEV_UP): wlxc4e9840f3c86: link is not ready
[57067.735739] IPv6: ADDRCONF(NETDEV_UP): wlxc4e9840f3c86: link is not ready
[57067.796403] IPv6: ADDRCONF(NETDEV_UP): wlxc4e9840f3c86: link is not ready
[57077.475570] IPv6: ADDRCONF(NETDEV_UP): wlxc4e9840f3c86: link is not ready
[57078.845439] wlxc4e9840f3c86: authenticate with f4:3e:61:bd:c4:42
[57078.902915] wlxc4e9840f3c86: send auth to f4:3e:61:bd:c4:42 (try 1/3)
[57078.904947] wlxc4e9840f3c86: authenticated
[57085.353173] wlxc4e9840f3c86: authenticate with f4:3e:61:bd:c4:42
[57085.414402] wlxc4e9840f3c86: send auth to f4:3e:61:bd:c4:42 (try 1/3)
[57085.416243] wlxc4e9840f3c86: authenticated
[57092.272535] wlxc4e9840f3c86: authenticate with f4:3e:61:bd:c4:42
[57092.333649] wlxc4e9840f3c86: send auth to f4:3e:61:bd:c4:42 (try 1/3)
[57092.335531] wlxc4e9840f3c86: authenticated
[57099.676635] wlxc4e9840f3c86: authenticate with f4:3e:61:bd:c4:42
[57099.737323] wlxc4e9840f3c86: send auth to f4:3e:61:bd:c4:42 (try 1/3)
[57099.739393] wlxc4e9840f3c86: authenticated
[57102.323708] IPv6: ADDRCONF(NETDEV_UP): wlxc4e9840f3c86: link is not ready
[57102.857826] IPv6: ADDRCONF(NETDEV_UP): wlxc4e9840f3c86: link is not ready
[57111.789812] IPv6: ADDRCONF(NETDEV_UP): wlxc4e9840f3c86: link is not ready
[57111.810208] wlxc4e9840f3c86: authenticate with f4:3e:61:bd:c4:42
[57111.836358] wlxc4e9840f3c86: send auth to f4:3e:61:bd:c4:42 (try 1/3)
[57112.042005] wlxc4e9840f3c86: send auth to f4:3e:61:bd:c4:42 (try 2/3)
[57112.043863] wlxc4e9840f3c86: authenticated
[57129.574248] wlxc4e9840f3c86: authenticate with f4:3e:61:bd:c4:42
[57129.635724] wlxc4e9840f3c86: send auth to f4:3e:61:bd:c4:42 (try 1/3)
[57129.637566] wlxc4e9840f3c86: authenticated
[57137.321518] IPv6: ADDRCONF(NETDEV_UP): wlxc4e9840f3c86: link is not ready
[57137.840231] IPv6: ADDRCONF(NETDEV_UP): wlxc4e9840f3c86: link is not ready
```

---------------------------------

lsmod :

```
Module                  Size  Used by
rt2800usb              28672  0
rt2x00usb              20480  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              53248  3 rt2800lib,rt2800usb,rt2x00usb

```

--------------------------------

I tried tips in previous post but still not working...

Thanks a lot.

---

### Post by w00sterf1 on 2017-04-03
I upgraded from 16.10 to 17.04 today and I do also have the same problem but just with one of my wifi adapters.

This adapter does not allow me to connect:
```
Bus 001 Device 066: ID 148f:3572 Ralink Technology, Corp. RT3572 Wireless Adapter
```

and

```
rt2800usb              28672  0
rt2x00usb              20480  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              53248  3 rt2800lib,rt2800usb,rt2x00usb
mac80211              782336  3 rt2800lib,rt2x00lib,rt2x00usb

cfg80211              602112  3 rt2x00lib,mac80211,rndis_wlan

```


But when I connect a Linksys adapter, I can connect just fine:

```
Bus 001 Device 047: ID 13b1:000e Linksys WUSB54GS v1 802.11g Adapter [Broadcom 4320 USB]

```
Basically, I have the same issue as [COLOR=#DD4814][COLOR=#000000][mibakh]("https://ubuntuforums.org/member.php?u=2062875") [/COLOR][/COLOR]above does.

This seems to be a realtek issue as my Linksys Broadcom based wifi adapter works just fine. So, no this issue can not be called resolved.

Edit: Ok, this is a 4.10.x kernel issue!

By installing the 4.11-rc5 kernel, my Realtek wifi is now working again.

```
sudo wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11-rc5/linux-headers-4.11.0-041100rc5_4.11.0-041100rc5.201704022131_all.deb
sudo wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11-rc5/linux-headers-4.11.0-041100rc5-generic_4.11.0-041100rc5.201704022131_amd64.deb
sudo wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11-rc5/linux-image-4.11.0-041100rc5-generic_4.11.0-041100rc5.201704022131_amd64.deb
sudo dpkg -i *.deb
sudo reboot

```

---

### Post by grahammechanical on 2017-04-03
For me, installing the 4.11 rc kernel did and it didn't work.

I used the live session to download the kernel deb files and copy them to the relevant 17,04 partition. After installing & rebooting the 17.04 install was still unable to connect to the Internet even with ethernet. So, I disabled the USB-WiFi in the BIOS. Still no Internet until I deleted the WiFi connection from Network manager.

> graham@sda6-zesty:~$ uname -a
Linux sda6-zesty 4.11.0-041100rc5-generic #201704022131 SMP Mon Apr 3 01:33:30 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
graham@sda6-zesty:~$ nmcli general status
STATE      CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN    
connected  full          enabled  enabled  enabled  enabled 


With WiFi disabled in the BIOS and Network Manager not showing any available WiFi access points, why is nmcli showing WiFi enabled?

UPDATE:

Curses. Foiled again!

On subsequent reboot Internet access is broken. I have ungraded x 3 17.04 installs to the 4.11 rc kernel and Internet access is still broken with WiFi disabled in BIOS and WiFi connections deleted from Network Manager.

Regards.

---

### Post by gstanden on 2017-04-14
The fix worked for me also running Ubuntu 17.04 fresh install on Lenovo P70 Mobile Workstation.  Had to add:

[device]
wifi.scan-rand-mac-address=0

to the /etc/NetworkManager/NetworkManager.conf file as described above.  Thanks!

---

### Post by faure212 on 2017-04-15
I have the same pesky problem-- "upgraded" to 17.04 (on a Yoga 2 Pro, runnning Lubuntu 16.10), and WiFi stopped working.  
Editing /etc/NetworkManager/NetworkManager.conf did not fix it. 
Running (in terminal) 

sudo ifconfig wlan0 up
service network-manager restart

does work, but must be done with every reboot.    This bug has been around for several "upgrades" now, and it is like crabgrass-- always comes back.  Shame on you, Ubuntu developers.

---

### Post by rrnbtter on 2017-04-15
Greetings,

[COLOR=#000000]*Open*[/COLOR]
[COLOR=#000000]*/etc/NetworkManager/NetworkManager.conf*[/COLOR]

[COLOR=#000000]*add lines*[/COLOR]
[COLOR=#000000]*[device]*[/COLOR]
[COLOR=#000000][I]wifi.scan-rand-mac-address=no

then
[/I][/COLOR]sudo service network-manager restart

PS : I suggest IPv6 be set to Automatic

---

### Post by tajreed on 2017-04-15
Not solved here on fresh install of Ubuntu 17.04. Same problems that I've had all along. I can connect to my password protected home network but not at my favorite coffee which also requires a password. Nor can I connect to the city network which requires no password. Never had this problem with other Ubuntu versions. I've tried the edits to /etc Networkmanager conf. as shown in this thread but to no avail. My machine is dual boot with W10 and W10 connects-no problem

The error message is something to the effect that 'cannot find the dns server you are looking for'.

Any thoughts? This has to be a bug some where in 17.04.

Thanks to all who are trying to fix this.

---

### Post by wildmanne39 on 2017-04-15
Start a thread in networking and wireless please.
Thanks

---

### Post by howefield on 2017-04-16
Closed.

---

