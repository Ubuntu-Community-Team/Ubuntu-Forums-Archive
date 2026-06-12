---
title: "Wireless BCM4318 AirForce Card"
date: 2006-06-05
forum: Tutorials
---

### Post by piracyrocks on 2006-06-05
Ok, so there are other tutorials out there for the other 43xx cards, but from my experience, none of them have worked with the specific 4318 card.  This way i will explain below is the only way i have gotten my 4318 card to work with 6.06

**Step 1: Disabling bcm43xx**
Ok, so first thing we need to do is make it so that the pre-installed driver, bcm43xx, doesn't attach to the hardware on bootup.  The way we do this is by blacklisting it.  In a terminal window type:

```
sudo gedit /etc/modprobe.d/blacklist
```

in the window that pops up, find a new line and type: blacklist bcm43xx

After this, reboot and make sure that when you go to System > Administration > Networking there isnt a listing for your wireless connection

**Step 2: Get ndiswrapper**

Make sure you have the universe repositories enabled. (google it if you dont know how) and go to a terminal and type the following:

```
sudo apt-get install ndiswrapper-utils
```

this might prompt you for your password and ask you to continue and such, its very easy, just go through it.

**Step 3: Use ndiswrapper to configure the drivers**

Get the drivers you need, i suggest [these ones]("ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip"), and make sure u have the .inf and .sys files of the driver.  If you use the ones i suggested they will be bcmwl5.sys and bcmwl5.inf

Once you have the driver, put them on the desktop and then go to a terminal and type:

```
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
```

this will install the driver

then, in the same terminal window, type:

```
sudo ndiswrapper -m
```

now restart and you will be able to connect to wireless networks.  If you have a wep encryption on your wireless network, go on to step 4 below.  

**Step 4: Installing Network Manager**

Network manager will allow you to connect to those wep encrpypted networks.

Simply go to a terminal window and type:

```
sudo apt-get install network-manager-gnome
```

Let that install by typing your password and whatnot, then restart and you will be good to go, just click on it up in the corner and select your wireless network.

**Still not working?**
If you still cannot connect to a wireless network try running the following commands in terminal

```
modprobe ndiswrapper
```

and

```
echo ndiswrapper >> /etc/modules
```

**Thanks esavato**

Lemme know if anyone experiences any problems with this, however, i have this exact card and did this exact procedure from a fresh install and it worked flawlessly.  If anyone needs person to person help just catch me on aim at r0nchetti.

---

### Post by esavato on 2006-06-08
This was an elegant and simple guide that worked great for me.  I did have to run the following commands to get this to work properly on my system.  THANKS

modprobe ndiswrapper

echo ndiswrapper >> /etc/modules

---

### Post by Slicedbread on 2006-06-08
It should also be noted that if that does no work try ```
sudo gedit /etc/modprobe.d/ndiswrapper

``` and then changing "alias wlan0 ndiswrapper" to "alias eth1 ndiswrapper"

---

### Post by maddbaron on 2006-06-08
doesnt work 4 me. everything was installed i have a network manager but wireless doesnt work.

any ideas?

---

### Post by maddbaron on 2006-06-08
here is my desktop i downloaded the filmware and extract it to desktop. i did your solution last nite and i have the gnome manager but the wireless doesnt work.

would it be too much trouble to write out step by step i have to do based on this screen shot?

---

### Post by scenestar on 2006-06-08
[QUOTE=maddbaron]here is my desktop i downloaded the filmware and extract it to desktop. i did your solution last nite and i have the gnome manager but the wireless doesnt work.

would it be too much trouble to write out step by step i have to do based on this screen shot?[/QUOTE]
you need to use a shell script to connect or modify your inet.d scripts.

---

### Post by maddbaron on 2006-06-08
is there a walk thru link or web page i can look at to do so please?

I am a newbie.

---

### Post by scenestar on 2006-06-08
> is there a walk thru link or web page i can look at to do so please?

Yes there is.

---

### Post by piracyrocks on 2006-06-10
make sure u are trying this off of a clean install of ubuntu, even though u black list bcm43xx.

if you are not trying this from a clean install then there might be other things you are messing up

---

### Post by johnthejack on 2006-06-12
I've followed these instructions but when I enter modprobe ndiswrapper I get "FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-23-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted".
I tried again but as sudo and get the same reply. I haven't a clue what this means as I installed Ubuntu for the first time this weekend. Could someone help, please? Thanks.

---

### Post by Jerim on 2006-06-12
I am thinking of doing a clean install. The question I have is by clean install, do you mean erasing everything and starting over from scratch or is there a way to just reinstall the OS files, without touching the applications? (I believe you can do that with Ubuntu, but don't know if that would fall under the definition of a clean install.)

My only concern is that it took me a while to get Ubuntu setup just the way I like it. Other than this wireless issue, it is perfect. I would hate to start from scratch.

---

### Post by piracyrocks on 2006-06-12
johnthejack,

go to a terminal and type this:

sudo ndiswrapper -l

what comes up?  If you get anything other than "driver present, hardware present" post back and i will guide you from there.

Jerim,
I do not know of a way to re-install just the os files without touching the applications...sorry

what i suggest is u just deal with it and re-install everything after u get this working, it cant take u longer than an hour

---

### Post by johnthejack on 2006-06-13
Thanks for the reply. I'm in the wrong thread as I have a different card. 
I have a Belkin. I downloaded and installed what I think is the correct driver: ndiswrapper -l is showing the driver and hardware present, but I still can't connect.

---

### Post by ????? on 2006-06-13
I tried this howto, and it works on networks without wep/wpa, and when I turn on WEP on my AP, and I reboot my computer, the light blinks on and off, and back on, and off, etc. Also networkManager says "no network devices have been found"

---

### Post by nbound on 2006-06-16
Works perfectly for me on a clean install, even without the 2 extra instructions :)

System: Compaq Presario 2148AU

---

### Post by losthornet on 2006-06-17
[QUOTE=johnthejack]Thanks for the reply. I'm in the wrong thread as I have a different card. 
I have a Belkin. I downloaded and installed what I think is the correct driver: ndiswrapper -l is showing the driver and hardware present, but I still can't connect.[/QUOTE]

John, I got to this point on my laptop and found the way to get it going was to actually use the fn + wireless key combo. suddenly the green light came on and wireless worked (even after restart). the drivers i used were on the ndiswrapper wiki. btw my machine is a Dell inspiron 1300. I assumed the fn keys would only work in windows, but they all seem to work in ubuntu 6 out of the box.

---

### Post by tehownt on 2006-06-20
Hi,
 
I'm a tremendously lucky owner of that shitty wifi card, and I've been trying to make it work for too long.

_First I tried with ndiswrapper_, as after reading on quite some forums, it seems the BCM4318 might only work with it.

So I blacklisted bcm43xx, modprobe -r bcm43xx, rmmod bcm43xx.
I installed ndiswrapper-utils (and the gnome networking util), then got a copy of the exact .inf and the .sys files I was using under windows for that card, and installed it using ndiswrapper -i. 
ndiswrapper -l showed up correctly too.
I did the alias too.
I did modprobe ndiswrapper too, just to be sure.
I did a reboot to apply those settings, but on restart, the little light did not lit up.
I checked dmesg and everything seemed fine, it told me the eth1 interface was up.
So I then, checked ifconfig, it showed up the interface correctly, as if it was up.
Everything seemed fine except the little light, but who cares.
So I tried iwconfig to see, and the card showed correctly but the essid was set to off, so well, I tried to set it, the channel, but everytime I didn't tell me squat, and just didn't change anything, the iwconfig showed up exactly the same.
iwlist scan told me that there was no result and obviously dhclient didn't work either, and just sends discovers in loop.
I also checked in the gnome network manager, and It doesn't even show.

_So, what the hell, I tried the bcm43xx stuff instead:_

Deinstalled all the ndiswrapper stuff (modprobe -r, rmmod, blacklist, remove from /etc/modules), and did a reboot.

I then followed the instructions there : [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

and installed bcm43xx-fwcutter, installed all the cut files in /lib/firmware and /lib/firmware/2.6.15.25/, unblacklisted it, and then modprobe bcm43xx.

Now the little light shows up on boot, but the interface doesn't show up in gnome manager, it shows up in ifconfig, I can call up on it, it shows up in iwconfig, the a/p shows "Invalid" (instead of just off with ndiswrapper), and the essid is good.
The only problem is that I can't change anything using iwconfig, iwlist scan doesn't give anything either, and dhclient runs in the empty...

It was really pissing me off, so I tried to get other newer drivers, using the same method, always removing all the firmwares installed in /lib/firmwares and in 2.6.., I even installed a more recent version of bcm43xx-fwcutter in order for it to get compatibility with a newer driver.

After haing tried the ones I had under windows, I tried the drivers from the ndiswrapper site, from the big 802.11 package, from the ubuntu thread up there, from that ubuntu thread too:[http://ubuntuforums.org/showpost.php?p=1105667&postcount=218](http://ubuntuforums.org/showpost.php?p=1105667&postcount=218), and this, either with ndiswrapper or bcm43xx.



So now I'm a bit clueless on what to do next, its not my laptop, otherwise I would just have bought a pcmcia wifi card that I know would work under ubuntu, but I would really like to know if someone has another idea.

It is really absolutely stupid, I hate hardware manufacturers, and I am really glad and impressed of the job done for ndiswrapper/bcm43xx that is a really nice trick that was achieved, plus the tutorials on those forums are really explicit.

Oh, and by the way, I'm using a Dell Inspiron V2405.

So if anyone has some news on that issue...

Here is a little sumup of the drivers I've tried (inf files accordingly).

38ca1443660d0f5f06887c6a2e692aeb  ./80211g/bcmwl5.sys
185a6dc6d655dc31c0b228cc94fb99ac  ./bcmwl5_.sys
69f940672be0ecee5bd1e905706ba8ce  ./sp32/bcmwl5.sys
fa4a4a50b4b2647afedc676cc68c69cc  ./sp31/bcmwl5.sys


](*,)

---

### Post by JonAre on 2006-06-25
I have a BCM4318 (HP nx6125) and have problems too. I've tried everything in this thread and other threads too (including the 43xx-driver approach).

```

jonare@ubuntu:~$ modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-25-386/misc/ndiswrapper.ko): Operation not permitted
jonare@ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-25-386/misc/ndiswrapper.ko): Invalid argument
jonare@ubuntu:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

```

Any ideas? I have to boot with the "noapic" option by the way.

---

### Post by JonAre on 2006-06-25
[QUOTE=JonAre]I have a BCM4318 (HP nx6125) and have problems too. I've tried everything in this thread and other threads too (including the 43xx-driver approach).

```

jonare@ubuntu:~$ modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-25-386/misc/ndiswrapper.ko): Operation not permitted
jonare@ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-25-386/misc/ndiswrapper.ko): Invalid argument
jonare@ubuntu:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

```

Any ideas? I have to boot with the "noapic" option by the way.[/QUOTE]

I don't know what just happend. I've previously installed the BCM43xx-firmware/driver, which didn't work. Then I followed this thread, which didn't work. Then I installed ndiswrapper like it's described in [this thread](http://www.ubuntuforums.org/showthread.php?t=197102), which didn't work. I then decided to try the BCM43xx-approach one more time and in preperation to this I blacklisted ndiswrapper and unblacklisted the BCM-driver and rebooted. *And then it just worked*. I don't know why or how but I'm posting this thru those elusive electromagnetical waves.

---

### Post by punkybouy on 2006-06-25
You need the right inf file.  I tried several including the one from Belkin.  None worked.  I found the right one somewhere on this forum.  I got so excited it worked I forgot where!  Anyway the inf you want is version 3.64.100.0 and is 606 kb or so.  All the ones from Belkin are about half that size. All the others locked up my laptop. I am using the Belkin part F5D7010 version 4000.  I got it at Staples for about $35.  The laptop is a three year old Dell Inspiron 8200.

---

### Post by punkybouy on 2006-06-25
Here it is.

[http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+wireless]("http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+wireless")

Middle of the page under the heading "Process".  Download and unzip the first one in the list.

---

### Post by gotfoo on 2006-06-26
I followed the instructions and I got my wifi card running in Xubuntu!!:D 

I have a Gateway MX6440 laptop (1.8 Ghz Turion 64 / 1GBRAM / 15.4 WideScreen) and I've got wifi running!!!

---

### Post by Cornmuffin on 2006-06-28
I tried doing this with a fresh install of ubuntu (except I had network manager and wireless assistant isntalled) and finally both of those programs can SEE my wifi connection.  They see the connection and its information, but both fail when trying to connect to it.  I go through this about twice a month, I fresh install ubuntu and try frantically for three days to get wifi working, fail, give up, wait a few weeks and start over.  I have a completely functioning linux webserver that I built/installed/maintain, but what do you know, I can't even get my laptop wifi working](*,) .

This is the closest I have been in months....help!  Why won't it connect!?

---

### Post by wilk on 2006-06-28
Someting stranged happened with this card. I had it working on a hp Pavilion dv5xxx with ndiswrapper and gnome-network-manager (and also bcm43xx and gnome-network-manager) then for some reason I tried to use wifi-radar. 

All of a sudden, the card doesn't work anymore : the module (ndiswrapper or bcm43xx) can be loaded, the wifi LED is lit, but for example, I cannot scan the networks :

$ iwlist eth0 scan :
etho No scan results

After one night ](*,)  of trying several firmwares with the two methods] on a fresh install of  Dapper I finally got it working again, in Dapper, by initialising the card in Windows  (which I also had to reinstall for the occasion :( ) Don't know if that makes sense :-k .

To make it short : Don't ever touch wifi-radar or anything when you've got this card working and if it seems the card doesn't work even though the module is inserted, try booting (just once ;) ) in Windows, activate the card here and you could have  a nice surprise.

Let me know If you experience the same.

---

### Post by Raistlin355 on 2006-06-28
[QUOTE=wilk]Someting stranged happened with this card. I had it working on a hp Pavilion dv5xxx with ndiswrapper and gnome-network-manager (and also bcm43xx and gnome-network-manager) then for some reason I tried to use wifi-radar. 

All of a sudden, the card doesn't work anymore : the module (ndiswrapper or bcm43xx) can be loaded, the wifi LED is lit, but for example, I cannot scan the networks :

$ iwlist eth0 scan :
etho No scan results

After one night ](*,)  of trying several firmwares with the two methods] on a fresh install of  Dapper I finally got it working again, in Dapper, by initialising the card in Windows  (which I also had to reinstall for the occasion :( ) Don't know if that makes sense :-k .

To make it short : Don't ever touch wifi-radar or anything when you've got this card working and if it seems the card doesn't work even though the module is inserted, try booting (just once ;) ) in Windows, activate the card here and you could have  a nice surprise.

Let me know If you experience the same.[/QUOTE]

Man I did the same stupid thing, the card would work just fine at home and had been for about a week.  Then I took the laptop to work and gnome-network-manage wouldn't connect so I used the built-in network manager and it shot everything to hell.  If you get the card working don't mess with it!!!!!!!

---

### Post by Traudel on 2006-06-30
Tried the original guide by piracyrocks with several inf file, best result i get is make the card finding my private network. wlan led blinks once a while, but i can't connect to my ap :(
btw, i have the bcm4318 in my hp nx6125 notebook.

---

### Post by gotfoo on 2006-07-05
I don't know if has already been mentioned but if you are having trouble try using the **bcmwl5a.inf** driver instead.

At **Step 3** do this instead:

```
sudo ndiswrapper -i ~/Desktop/**bcmwl5a.inf**
```

Oh if I didn't mention it before I got this tutorial to work with Kubuntu, Xubuntu amd Knoppix 5.01.

And if you are using Xubuntu then you already have network-manager-gnome  mentioned in **Step 4**.

---

### Post by mdoube on 2006-07-07
> **JonAre said:**
> I don't know what just happend. I've previously installed the BCM43xx-firmware/driver, which didn't work. Then I followed this thread, which didn't work. Then I installed ndiswrapper like it's described in [this thread](http://www.ubuntuforums.org/showthread.php?t=197102), which didn't work. I then decided to try the BCM43xx-approach one more time and in preperation to this I blacklisted ndiswrapper and unblacklisted the BCM-driver and rebooted. *And then it just worked*. I don't know why or how but I'm posting this thru those elusive electromagnetical waves.

Yeah I know what you mean about elusive. I did this too: did a fresh install of Dapper 6.06 this afternoon. I could *see* the AP but not connect to it using the bcm43xx driver and firmware. Then after a few reboots setting up XGL etc. I couldn't see anything on the airwaves! So I tried ndiswrapper, which I was familiar with from the Fedora Core 4 installation that I've just overwritten. No radio action. So, I tried this, blacklisting ndiswrapper and un-blacklisting bcm43xx. All of a sudden NetworkManager can see my AP (and my neighbour's), and happily connects to it.

I'm writing this post using my bcm43xx driver. No idea what I did,  but it goes.

Previously on the Acer Aspire 3023 you had to install acerhk to turn the card on at boot. I have noticed some weird thing where it enables/disables depending on what I do in WinXP (dual boot). 

Hopefully the bcm43xx programmers can figure out what's up and improve their driver!

Cheers, and enjoy the footy this weekend.

Mike

---

### Post by compwiz18 on 2006-07-07
Not that it matters, but I took those drivers from the first post in this thread - they should be the same ;)

---

### Post by lechbialek on 2006-07-25
It works! Thanks so much, not being able to use wifi has kept me from using linux as my main O.S. for the past few months.

I'd like to add something I learned from another post to get network-manager working. I used to get an error on logon from the network-manager applet.

**sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/**

(I have no idea what it does but it fixes the "The NetworkManager Applet could not find some required resources. It cannot continue." error on logon)

I got it from this post:

[http://www.ubuntuforums.org/showthread.php?t=199045](http://www.ubuntuforums.org/showthread.php?t=199045)

Lech

---

### Post by wrgross on 2006-07-29
If you try to load ndiswrapper-utils and it fails as such...

```
laptop:~$ sudo apt-get install ndiswrapper-utils
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ndiswrapper-utils
```

Update your application cache by selecting
Applications -> Add/Remove
and let the package database update itself.

Enjoy.

---

### Post by compuguy1088 on 2006-07-29
I have the same interegated card (0000:00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)), which in 5.10 I used ndiswrapper, but when I loaded 6.06, I decided to use the bcm43xx drivers and the whole fw_cutter routine, with a little work, as well as backlisting ndiswrapper I got it to work. The laptop that Im using is a Acer Aspire 3003LCi. With some more tinkering, I also got network manager to work. It took alot of guess and check, but its working..

---

### Post by ivan.virtuale on 2006-07-30
thank you very much!!!
my wireless card "Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)" on my Compaq nc6120 is working ...finaly!!!

Ivan

---

### Post by Bruhthakuga on 2006-08-12
I followed your instructions on a "fairly" clean install and I get the,"SIOCGIFFLAGS error: No such device" error message.  Also, when I go to Systems, Administration, Networking there is no eth1 for the wireless card.

Terminal Results:[COLOR="RoyalBlue"]

n@n-laptop:~$ sudo lspci
0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
0000:05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:05:09.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
n@n-laptopn@n-laptop:~$

n@n-laptop:~$ sudo apt-get install ndiswrapper-utils
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.2kB of archives.
After unpacking 139kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main ndiswrapper-utils 1.8-0ubuntu2 [28.2kB]
Fetched 28.2kB in 0s (48.6kB/s)
Selecting previously deselected package ndiswrapper-utils.
(Reading database ... 71984 files and directories currently installed.)
Unpacking ndiswrapper-utils (from .../ndiswrapper-utils_1.8-0ubuntu2_amd64.deb) ...
Setting up ndiswrapper-utils (1.8-0ubuntu2) ...

n@n-laptop:~$

n@n-laptop:~$ sudo apt-get install ndiswrapper-utils
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.2kB of archives.
After unpacking 139kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main ndiswrapper-utils 1.8-0ubuntu2 [28.2kB]
Fetched 28.2kB in 0s (48.6kB/s)
Selecting previously deselected package ndiswrapper-utils.
(Reading database ... 71984 files and directories currently installed.)
Unpacking ndiswrapper-utils (from .../ndiswrapper-utils_1.8-0ubuntu2_amd64.deb) ...
Setting up ndiswrapper-utils (1.8-0ubuntu2) ...

n@n-laptop:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
Password:
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
n@n-laptop:~$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
n@n-laptop

n@n-laptop:~$ man fsch
No manual entry for fsch
n@n-laptop:~$ fsch
bash: fsch: command not found
n@n-laptop:~$ modprobe ndiswrapper
n@n-laptop:~$ echo ndiswrapper >> /etc/modules
bash: /etc/modules: Permission denied
n@n-laptop:~$ sudo gedit /etc/modprobe.d/ndiswrapper
Password:
n@n-laptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
n@n-laptop

n@n-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:2C:7D:F2
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe2c:7df2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2551 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2595464 (2.4 MiB)  TX bytes:288548 (281.7 KiB)
          Interrupt:217 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

n@n-laptop:~$


n@n-laptop:~$ sudo ethtool eth0
Password:
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes

n@n-laptop:~$ sudo ethtool eth1
Password:
Settings for eth1:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available
n@n-laptop:~$


n@n-laptop

n@n-laptop:~$ cat /etc/network/intefaces
cat: /etc/network/intefaces: No such file or directory
n@n-laptop


[/COLOR]

I was instructed to put the bcmwl5.inf and bcmwl5.sys on the desktop but I didn't do anthing with the "sys" is it needed?  How do I get my eth1 device working?

---

### Post by uzoomy on 2006-08-18
Thank you piracyrocks for that tutorial! I FINALLY succeeded with setting up my wlan. :)

I did not start from a clean install of the OS, I have been running it for a couple of months, so try it first before you reinstall.

For any user of Acer Aspire 3003WLMi (my laptop):
A thing that almost got me was that I had to press the "wireless-light" on the front (the one that blinks in WinXP) to activate it. After a reboot all was fine, using WEP.

I'm gonna try it with WPA later, since i thing an updated network-manager-gnome supports it. Does anyone have experiences from that?

zoomy

---

### Post by dbbolton on 2006-08-19
i followed your instructions, and something obviously happened. now, the wireless light on my notebook blinks (something that never happened in windows), or it can be turned off completely by pressing the button. however, i still can't get online through the eth1 connection.

i have a linksys wrt54g v5 router. i went to the router's ip and got all of the proper information for eth1'a "properties."

any ideas?

---

### Post by amirnathoo on 2006-08-27
This didn't work for me. The system locked up after the rebooting.
It won't pass "Network Interfaces"

Had to re-install everything.

---

### Post by prince_niceguy on 2006-08-29
it didn't work for me too. After reboot the screen does not proceed after net work interface. In the recorvery mode it stops after ndis-wrapper. Please help...](*,)

---

### Post by blueidealist on 2006-08-29
Ok, my 2 cents.

I had the same problem and had installed amd64 Ubuntu.
The method indicated in this thread did not work.  I got through the whole read & do without any errors, yet still no internet card recognized in network-manager-gnome.

I tried this several times... re-installing Ubuntu twice and trying again, this as well as other threads.

Finally, in desperation, I installed i386 Ubuntu and applied this method once more...  This time it works.

David

---

### Post by prince_niceguy on 2006-09-03
> **prince_niceguy said:**
> it didn't work for me too. After reboot the screen does not proceed after net work interface. In the recorvery mode it stops after ndis-wrapper. Please help...](*,)

At last after lot of tinkering and other things I got this working... Not sure how it worked however would try to list down the steps over here...

1. Get the source for the ndiswrapper from the sourceforge.
2. Compile the source with you 64 bit Ubuntu
3. For compilation you will require make, gcc compiler.
4. After compilation, black list bcm43xx and reboot. If the LED on your switch blinks means you are good to go... :-)...

I will try to put step by step instruction with script but will take time...

Good luck... the compilation is the key here... I tried ndiswrapper bundled with ubuntu but didn't work for me.

After compilation it worked simply great... I posted this over the net through wireless.. :D

---

### Post by namit on 2006-09-09
> 
modprobe ndiswrapper

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

I am getting this!

Any ideas of what to do

---

### Post by putzig on 2006-09-13
I've been tring to get this wireless card to work for a while. After I finished this tutorial my wireless doesn't show up at all. All I have is eth0 in the Connection Properties. Any ideas on how to get it to recognize the wireless again?

I get this on the terminal

putzig@Azul:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

My wireless used to be called eth1

---

### Post by ChunkyBustout on 2006-09-14
Thanks for the instructions! I just can't connect because my router is using WPA. Does anyone know what is needed to be able to use WPA?

---

### Post by prince_niceguy on 2006-09-21
> **ChunkyBustout said:**
> Thanks for the instructions! I just can't connect because my router is using WPA. Does anyone know what is needed to be able to use WPA?

I too have WPA enabled on my laptop. The steps I followed are almost similar the only difference is I did the following things.

1. Instead of using ndisutils from synaptics. I compiled them by downloading them from the sourceforge.net site. The installation instructions are quite elaborated on the site. You will require make, gcc and build utils for compiling and installing.

2. Install wifi radar. Use wifi radar to enable your WPA.

I am a linux new bie and know a little commands not much. I will try to help you :-)

---

### Post by lokakuu on 2006-10-12
can't seem to do it..
i'm a newbie, so maybe i'm not doing something properly..

i get this error when i'm installing the bcmwl5:
couldn't copy ~Desktop/bcmwl5.inf at /usr/sbin/ndiswrapper line 135.

can u help me out here?

---

### Post by msimon1960 on 2006-10-19
This works for my Belkin F5D7001 Wireless PCI card.  Thanks for the clear explanation of the steps involved and the 'why' for each step.

---

### Post by jsnelgrove on 2006-10-19
I have the dreaded Broadcom 4318 Rev02 card integrated in my Compaq V5000. The only distro that has succesfully run this card is "FREESPIRE" and I'm not a big fan. I refuse to use NDISWRAPPER, So I run natively with a USB WLAN stick for now.

However, I see today on Distrowatch that a developmental version of VINE has been released which supports the BCM4318xx cards.

It looks like there are cracks in the ice and we're getting close. I hope someone can take a look at what they've done and see if they can figure it out. Freespire and Vine have managed to get this card going. The question is what have they done and how.
Edit/Delete Message

---

### Post by msimon1960 on 2006-10-20
This worked perfectly for me!  Many thanks to 'PiracyRocks' for the solution.

I have a Belkin Wireless G model F5D7001.  You must use the bcmwl5.inf/sys files in the instructions.  The ones on the installation CD that came with the card do not work with ndiswrapper.

This should be listed as a 'How to install Belkin F5D7001 Wireless NIC' so that it easy to separate from the dozens of problem reports on this card.

Matt.

---

### Post by DannyG on 2006-11-07
thank you kind sir!

i have spent days trying to get my card to work, this did it perfectly.

for the record, i'm using Dell Inspiron 1300 with the BCM4318 Card.

thank you so much!

---

### Post by radek_t on 2006-11-11
alright ... after a couple of days of playing around with this here is where i got ...

when i do "iwconfig" i get the following:

[FONT="Courier New"]
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"radek"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:46:3F:15:C4   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr: off   Fragment thr: off
          Link Quality=56/100  Signal level=-57 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
[/FONT]

then when i do "sudo iwlist eth1 scan" i get the following:

[FONT="Courier New"]eth1      Scan completed :
          Cell 01 - Address: 00:13:46:3F:15:C4
                    ESSID:"radek"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-48 dBm  
                    Extra: Last beacon: 56ms ago
          
Cell 02 - Address: 00:80:C8:0C:3D:AE
                    ESSID:"karam"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Quality=100/100  Signal level=-81 dBm  
                    Extra: Last beacon: 528ms ago
          
Cell 03 - Address: 00:0C:41:A2:87:FB
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-83 dBm  
                    Extra: Last beacon: 480ms ago
[/FONT]
so it sees my network (Cell 01) plus other two networks (Cell 02 and Cell 03) ... but it won't connect ... 

any ideas?

---

### Post by radek_t on 2006-11-12
problem solved :)

---

### Post by q335r49 on 2006-11-14
Woohoo!  PiracyRocks -- thx, finally got it working after a week, after switching from the 64bit of edgy to the 32 bit.  (I have an Presario v2000z AMD64 Turion)  God bless you all on this glorious day, we are truly as brothers, yea, and our claims are I dare say just as legitimate as those in whom the same blood courses and those who from the same teat have suckled since birth, so shall we be joined in a bond stronger than flesh and death: i offer the peace pipe as a marker of this glorious bond, may the signature in blood mark this occasion, and may the sacred totem and mark be able to carry this moment through the generations, into our grandson and their grandson's grandson's, forever and ever, as long as this heavenly orb does turn rigidly about its axis: -- and though we may die, le resistance lives on -- The light of truth shineth like a glorious beacon from the sky, illuminating all about it but itself a glorious blindness, but where there was once darkness, there is now the everlasting life, truth, and glory, forever and ever, the christ-child from across the seas: for he is truly his brothers keeper and the finder of lost children.  None of that matters what matters is that I felt the *touch of God*  :KS

---

### Post by gtkourounis on 2006-12-13
this How-To worked great for me, thank you very much!!!!

---

### Post by savantelite on 2006-12-20
Step 4. modprobe ndiswrapper

the terminal shows FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernal/drivers/net/ndiswrapper.ko): operation not permitted

I am running Ubuntu 6.10 CE with a fresh install

Dell Lattitude D610

Installed ndis drivers show 
bcmwl5    driver present , hardware present

I still can't get wireless internet!
Please help

---

### Post by ibc on 2006-12-27
I finally got my infamous Linksys-G (BCM4318) card working.  Everything appeared to be configured properly (as perlsmod, iwconfig, ifconfig, dmesg etc...) on my Fujitsu-Siemens w/ a BCM4318 v.02.  But I couldn't get it to actually ping the gateway to save my life.

So I installed network-manager-gnome, network-manager, and wpasupplicant via "System" -> "Administration" -> "Synaptic Package Manager" (using the install CD).

Then I cleared out the old interfaces config data w/:

```
sudo vi /etc/network/interfaces
```

Commenting out everything other than “lo” entries, and saving the file.

Then I created a file ```
/etc/default/wpasupplicant
```, adding a single entry "ENABLED=0" and saved the file

```
sudo touch /etc/default/wpasupplicant
```

Reboot your system or use the following command

```
sudo /etc/init.d/dbus restart
```

Once, that was restarted, I could click on the NetworkManager icon in the "system tray" (right next to the date, and speaker volume icon) and choose a SSID from the drop-down.

epilogue: For some reason, the bottom line was that my interface config (/etc/network/interfaces) as generated by "System -> Administration -> Networking" wasn't getting the job done, and when I installed NetworkManager, it was screwing that up too.

---

### Post by logitron on 2007-01-13
I think it's important to note that if you are having problems with the "modprobe ndiswrapper" command, like I did, you need to install ndiswrapper-utils-1.8, instead of ndiswrapper-utils.  That should resolve your issue.

---

### Post by tacm on 2007-01-19
First Id like to say that this write up is excelent.  It is not working for me, but it is the first description of how to fix this problem that I can even understand.  I am BRAND new to linux and Ubuntu.  I am on a personel mission against microsoft so I am running Ubuntu as my only OS.  I ran the procedure step by step on the first page, here are my results.  When I go into system-administration-networking all i see are the wired connection and a disabled modem connection.  When I run the code from page two of this post [sudo ndiswrapper -l] I get a response 
Installed ndis drivers:
bcmwl5  invalid driver!
.  In addition when I downloaded the drivers subjested in step 3 and unziped the I have the file on my desk top with a littke orange padlock on the uper right hand corner of the icon and I cannot move or remove the icon.  When I try I get message “Cannot move "/home/tacm...op/80211g" to the trash because you do not have permissions to change it or its parent folder.”  I will include all information i have on my computer and hardware.  My laptop is an HP Pavilion dv8000, my wireless card is BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller.  I am a total novice with very rudimentary computer skills.  Any help I can get by this site, e-mail, or phone would be GREATLY appreciated as Im about to dropkick my computer.  Thank you. Steven  [email]tacm@e28bmw.com[/email] 407-221-1492

---

### Post by msimon1960 on 2007-01-20
The solution at top works perfectly for my Belkin 54g wireless NIC.  My model number is F5D7001

You must use the drivers supplied in this thread.  The ones that came with the card are not compatible.

Many thanks!

Matt.

---

### Post by Heartarchy on 2007-01-31
Alright, so I've been trying for roughly a week now to get this card to word on my Sony Vaio PCG-FXA36. I've tried ndiswrapper (while and while not blacklisting bcm43xx) and bcm43xx (while and while not blacklisting ndiswrapper). I've upgraded the kernel and installed new firmware. I've tried them all at least 2 times and am just wondering how big of a chance I have of this never working. Once the card lit up while booting ubuntu, but turned off when booted. Ndiswrapper says driver and hardware are present. If you feel up for the challenge or have any ideas as how to get this to work, please share. I am new to linux, but picked up most everything pretty quick. 

Cheers,
Troy

---

### Post by chipyoung on 2007-02-02
Yes, still trying to get this card to work.  I believe I am very close thanks to all the great posts at the ubuntu forum.

First of all I know my linksys card is working (WPC54G) because the laptop that has it runs a dual boot and it works fine in Windows XP.

Secondly I cleared out all prior attempts(many) by running the following;

sudo modprobe -r bcm1l5
sudo modprobe -r ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

Then I ran all commands (installing and setting up ndiswrapper) that piracyrocks posted on this forum. In etc/modprobe.d I changed wlan0 to eth1 which is my wireless connection.  I put in the ssid and my wep code in the network administrator.  Both lights are on ...on the card.  The link light stays lit, does not blink as it should.

By the way my chip is a broadcom 4318 (ugg).

Both my bcmwl5 files were downloaded from the ubuntu site. I am running dapper.

Please, any help would be greatly appreciated.

Thank you in advance,
Chip

---

### Post by msimon1960 on 2007-02-04
This guide always worked for me until I upgraded to 6.10.

Just a couple of refinements to this excellent guide.

1. Use the synaptic manager to get the v1.8 of the ndiswrapper-utils.  Version 1.1 doesn't appear to work with 6.10.

2. Uninstall the card before doing any of this.  Install the card when all the software is complete.  I had all kinds of trouble until I did it this way.  Some sort of dependency / configuration file problem?

Matt.

---

### Post by Valtor on 2007-02-06
Hi, I'm still getting problems with my wireless card.... it seems that it doesn't even detect the card, even though I can see that I have this card with lspci. It worked before, with Dapper Drake, but now  there's nothing I can do. Here's my log file. Can anybody help?

---

### Post by m0rpheu5 on 2007-02-13
i have a HP Compaq NX6125, with broadcom 4318, i follow the tutorial to install the driver, but when i use iwconfig, apeear to me:

root@unnic-laptop:~# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

if you look the Access Point appears: Invalid, and the light of the button from wireless continuos off, what could be?? I have many otths notebooks in the network, using wireless with no problem.

And, when i use the command modprobe ndiswrapper appears the error:

root@unnic-laptop:~# modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

What could be too?

Thanks

---

### Post by klatu on 2007-02-22
# modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

same here was working prior to the kernel upgrade.. Installed ndis drivers:
bcmwl5  driver present, hardware present 

eth1 not showing at all :( 

any suggestions would be greatly appreciated..

---

### Post by earthmeLon on 2007-03-15
This worked beautifully for me, but I kept messing up my graphics card settings and having to reformat ubuntu, so I kept having to re-download the drivers.

...but this time the link is broken v_v


Could someone please repost the drivers?  All of the drivers I find give me weird errors.


Thanks in advance!!

---

### Post by jbaerbock on 2007-03-23
I have looked at many solutions but no forum mentioned the key component you did, blacklisting the drive Linux auto selects for the wireless card. Thank you do much for the information as the lack of wireless would have been the only thing driving me away from Linux and back to crappy windows, thankfuly now I don't have to go back. Thanks again!



Long Live Linux!


And my touchpad's scroll feature works better in Linux anyway :-).

---

### Post by dewme5 on 2007-05-01
I've just done a fresh install of Fiesty, and the BCM4318 works automatically.  literally plug and play..

---

### Post by odzangba on 2007-05-15
Cool man. It works beautifully. These are very concise instructions and you have a nice writing style.  Let me point out though that you have to load the ndiswrapper module before the card will work.

---

### Post by patmalcolm91 on 2007-05-18
I've been trying for 3 days now to get my wireless to work, I cant get the ndiswrapper to install because my wireless doesn't work. (I'm on another machine right now), how do i get the ndiswrapper to install if i cant connect to the internet?

---

### Post by olskar on 2007-07-09
I did just as in the first post..except I wrote sudo modprobe ndiswrapper.. But I get no device..When I write ndiswrapper -l  I get good output..but iwconfig shows just lo and eth0

---

### Post by wallaper on 2007-07-11
Piracyrocks

thankyou thankyou thankyou!

I've been trying to get this card to work for I dont know how long now (must be at least 3 weeks) 

Even removed it ready to take it back.  Numerous installs of dapper as well.  But finally it works!

Only thing I changed was used drivers that came with wlcard.   Your link didn't work for me!  But the rest of it certainly did.

BTW  - I used the drivers on supplied disc marked Win XP bcmwl5.inf & .sys 

(they also have drivers for 93 ME etc!

again thanks, all I have to hope for now is that it still works after the update downloads (this was another fresh install!)

cheers!    :)=D>

---

### Post by 3ark on 2007-07-21
Completely new to linux so please bear with me for a moment. I tried the instructions on this page, using the bcmwl5.sys and bcmwl5.inf that was in my windows partion. That all seemed to go good, and the light is now on. System->admin->networking shows that its active. Typing 'sudo ndiswrapper -l' tells me that driver is present and hardware is present. I installed network manager but when i tell it to connect to the default network it tries but doenst connect. Everything seems to be ok but it wont connect. Any help would be greatly appreciated as I'm pretty much lost.

---

### Post by 3ark on 2007-07-21
I'm posting this wirelessly. Turns out that everything was working ok. All I did since my last post was backclick on the network manager icon and clicked 'remove'. Then I clicked on the network connection icon and changed it to wlan0 (which wasnt an option when network manager was there). I'm on a Compaq Presario V2000 lappy. I'd like to thank everyone who contributed in this thread. I was already liking linux but now that I have wireless there is much less reason for me to load up windows... not that I really have anything against windows but linux just runs way faster for me.:popcorn:

---

### Post by anilv on 2007-08-01
Here comes the ultimate solution to deal with this problem ... Just kidding ... Please visit the following ... The steps are straight forward and worked well for me ... Hope you also can advantage ..

[http://www.tecpages.com/installing-and-configuring-bcm4318-broadcom-driver-using-ndiswrapper/](http://www.tecpages.com/installing-and-configuring-bcm4318-broadcom-driver-using-ndiswrapper/)

---

### Post by T-mo on 2007-08-20
I finished all the steps and tried to use it, but to no avail. When i wrote the command:

modprobe ndiswrapper it stated Fatal Error, then permission denied when i wrote echo ndiswrapper >> /etc command.

I typed in ndiswrapper -l and recieved this message:

bcmwl5 driver present, hardware present
bcmwl5.sys invalid driver!

How do i resolve this issue and how do i remove bcmwl5.sys?

i cannot remove it using the sudo apt-get remove command

Please Help

T-mo

---

### Post by crazybilly on 2007-09-09
well, to remove the current driver, use the following command:

ndiswrapper -r bcmw5.sys

before you do, though, try 

sudo modprobe ndiswrapper 
and
sudo echo ndiswrapper >> /etc blah blah blah

---

### Post by crazybilly on 2007-09-09
I used these command successfully until recently (well, it was sort of these--installing ndiswrapper w/ apt never worked for me and I had to build it myself.  And wifi-radar always seemed to work better than Network Manager).

Recently, though, something went wrong.  I'm not sure if it was a kernel update or if I uninstalled something important (I was trying to install something else, decided to remove it, did some updates (including a kernel update) and now, crap's broke.

The steps that normally work (all the above) don't seem to be working for me.

Anybody got any clues how to troubleshoot it?

---

### Post by deimios on 2007-09-12
I had a working wireless (bcm43xx+firmware) in Feisty but since it had the problem with broadcast range I tried to ndiswrapper method. It didn't work (it loads drivers, creates device, sees AP but doesn't connect) but when I switched back to the bcm43xx that didn't work either. So repeating the advice: If you can get it to work, DON'T MESS WITH IT!

Will try again in Gutsy.

---UPDATE---
Finally have it working with the bcm43xx+firmware. Had to uninstall everything ndiswrapper and had to rmmod all the ieee80211 modules (main, crypt, crypt_tkip, softmac) then after a modprobe bcm43xx (and several tries with knetworkmanager) it started working. I'm NOT touching this config ever again.

---

### Post by dukejones on 2007-09-14
The other methods sure acted like they wanted to work. but every time I'd connect to a wireless network, my system would hang.  :-(  Very frustrating.

I'm on a Dell Inspiron 1100, Ubuntu 7.04, with a Linksys WPC54Gv3 card (Broadcom 4318 chip inside, of course).  

Eventually, I did a search on the "a" version of the driver I'd overheard rumors of.  (bcmwl5a), found a copy, did an ndiswrapper install on it, 
ndiswrapper -i bcmwl5**a**.inf
and poof, works great.  [Looks like just the inf is different?  No idea why this works, but I'm not complaining.]

---

### Post by vector92 on 2007-09-14
Help.  I have a Gateway MX6421 with an AMD Turion and the BCM4318 wireless card.  

   I tried to follow the instructions.  I got the drivers:
 bcmwl5.sys and bcmwl5a.inf

  I typo'ed one of the commands and wrote 
"sudo ndiswrapper -i ~/Desktop/bcmwl5.inf"
instead of 
"sudo ndiswrapper -i ~/Desktop/bcmwl5a.inf"

I then entered the correct command, but now the response to typing "ndiswrapper -l"  is this:

bcmwl5 : invalid driver!
bcmwl5a : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)

How do I undo this?   I am a total newbie, so please be specific with any instructions.  Thanks!!!

---

### Post by Salt and Light on 2007-09-20
> **JonAre said:**
> I don't know what just happend. I've previously installed the BCM43xx-firmware/driver, which didn't work. Then I followed this thread, which didn't work. Then I installed ndiswrapper like it's described in [this thread](http://www.ubuntuforums.org/showthread.php?t=197102), which didn't work. I then decided to try the BCM43xx-approach one more time and in preperation to this I blacklisted ndiswrapper and unblacklisted the BCM-driver and rebooted. *And then it just worked*. I don't know why or how but I'm posting this thru those elusive electromagnetical waves.


I signed up to this forum to say it worked for me too by installing the ndiswrapper way completely, then blacklisting it and installing the fw cutter way.

For me, with my Acer Aspire 5000 with the 4318 wireless card builtin, I could not get either one of those solutions to work by themselves.  Spent 3 days on this, and finally what worked was fully installing the wrapper, then like I said, black listing it and fully installing the fw cutter method.

---

### Post by Salt and Light on 2007-09-21
I had a real struggle with the 4318 in my Acer Aspire 5000 with AMD64 Feisty ubuntu 7.04, but I got it working. No one solution worked. Proper procedure for me is to install ndiswrapper on a fresh install of ubuntu, then blacklist it and then do fwcutter method.

At the end of all this, detects AP and all wireless networks in range. Wireless works correctly. 




Outline of what worked for me:

fresh ubuntu AMD64 7.04 install
compile new ndiswrapper version 1.48 as of 19th Sept 07.
then turn around and blacklist ndiswrapper in /etc/modprobe.d/blacklist
take ndiswrapper out of /etc/modules

and then do only these two steps of the fwcutter routine:
sudo apt-get install bcm43xx-fwcutter
sudo apt-get install bcm43xx-firmware

upon reboot at this stage, it all works.




My install log:


Prereq:
FRESH INSTALL AMD64 ubuntu 7.04 Feisty


**1st Step - INSTALL NDISWRAPPER**

sudo cp /etc/apt/sources.list /etc/apt/sources.bak
echo 'deb [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) feisty-cafuego bcm43xx' | sudo tee -a /etc/apt/sources.list
wget [http://ubuntu.cafuego.net/969F3F57.gpg](http://ubuntu.cafuego.net/969F3F57.gpg) -O- | sudo apt-key add -
sudo apt-get update

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx 
cd bcm43xx/
wget [http://dlsvr03.asus.com/pub/ASUS/wireless/WL-100g-03/Driverv3100640.zip](http://dlsvr03.asus.com/pub/ASUS/wireless/WL-100g-03/Driverv3100640.zip)
sudo ndiswrapper -i bcmwl5.inf
unzip Driverv3100640.zip 
cp Driver/WinXP/* ./
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

REBOOT


At this point, nothing worked. I had stock ndiswrapper. So I decided to compile a new one. Fortunately for me, there was a new version 1.48 released two days ago on 19th of Sept 07.

sudo modprobe -r ndiswrapper
sudo ndiswrapper -r bcmwl5
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
mkdir -p ~/bcm43xx/ndiswrapper
cd ~/bcm43xx/ndiswrapper
sudo wget [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.48.tar.gz](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.48.tar.gz) -Ondiswrapper.tar.gz
tar xvzf ndiswrapper.tar.gz 
cd ndiswrapper-1.48/
make distclean
make
sudo make install
cd ~/bcm43xx/
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo modprobe ndiswrapper
sudo ndiswrapper -m

make sure to change the alias in /etc/modprobe.d/ndiswrapper from wlan0 to eth1:
sudo gedit /etc/modprobe.d/ndiswrapper

REBOOT



Nothing worked still. I had the new version of ndiswrapper freshly compiled at this point. So I decided to go ahead with the fwcutter method.


**2nd Step - INSTALL FWCUTTER and BCM43XX NATIVE DRIVERS**

sudo apt-get install bcm43xx-fwcutter
sudo apt-get install bcm43xx-firmware

Ignore all errors.

At this point I noticed /lib/firmware contained the .fw files I needed, so I thought I'd stop here and blacklist the ndiswrapper:

**3rd Step - BLACKLIST NDISWRAPPER**

sudo gedit /etc/modprobe.d/blacklist added line at end that says: blacklist ndiswrapper
sudo gedit /etc/modules take out ndiswrapper line

REBOOT

I stopped here and rebooted. It all came up. I realize this is only a partial install of the fwcutter method. Why it works? I don't know. All I know is any one solution never worked.

---

### Post by fusionpit on 2007-09-30
I recently decided to try Ubuntu out on my laptop, and surprise it had this card in it.

I spent hours trying all different methods from all around the web, but I finally got one to work without any hassle.

On my v2000 Compaq (v2424NR) I installed amd64 7.04.  I found that none of the methods would show the wireless card in the network manager no matter what method I used.  I did, however, find that you have to use the 64 bit driver on amd64.

[ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip)

Use that and follow the instructions outlined in OP.  It works flawlessly without having to do a bunch of other stuff.

---

### Post by Zerol on 2007-10-17
Finally made the switch again, this time followed the guide WITH the CD in the drive.. and still it ISNT working, how is this possible..

I couldnt find a log on the desktop if I remember correctly. I did try all the commands and here you can see a list of what happened when I ticked in the commands;
PC info;
AMD Turion 64

zerol@zerol-laptop:~$ sudo ndiswrapper -a 14e4:4319 bcmwl5

Password:

sudo: ndiswrapper: command not found

zerol@zerol-laptop:~$ sudo rmmod bcm43xx

ERROR: Module bcm43xx does not exist in /proc/modules

zerol@zerol-laptop:~$ sudo rmmod ndiswrapper
zerol@zerol-laptop:~$ sudo modprobe ndiswrapper

zerol@zerol-laptop:~$ sudo apt-get install ndiswrapper-utils-1.8 ndiswrapper-utils-1.1 ndiswrapper-utils ndiswrapper-common

Reading package lists... Done

Building dependency tree       

Reading state information... Done

E: Couldn't find package ndiswrapper-utils-1.8

zerol@zerol-laptop:~$ sudo ifdown eth1

ifdown: interface eth1 not configured

zerol@zerol-laptop:~$ sudo ifup eth1

eth1: ERROR while getting interface flags: No such device

There is already a pid file /var/run/dhclient.eth1.pid with pid 6847440

Internet Systems Consortium DHCP Client V3.0.4

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)


SIOCSIFADDR: No such device

eth1: ERROR while getting interface flags: No such device

eth1: ERROR while getting interface flags: No such device

Bind socket to interface: No such device

Failed to bring up eth1.

zerol@zerol-laptop:~$ sudo dhclient

Internet Systems Consortium DHCP Client V3.0.4

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:d4:35:93:09

Sending on   LPF/eth0/00:16:d4:35:93:09

Sending on   Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

zerol@zerol-laptop:~$ 


Really hope someone can help me because I want to leave Windows behind but without even getting WLAN that would be impossible..

---

### Post by gl0wst1ckn1nja on 2007-10-19
> **maddbaron said:**
> doesnt work 4 me. everything was installed i have a network manager but wireless doesnt work.

any ideas?

get a network manager called wicd ... that solved all of my problems ... i have used wicd for some time and it has never failed me ... the only thing is that sometimes you have to restart or
```
sudo modprobe ndiswrapper
```
or 
```
sudo ifup eth1
```
using wicd and these techniques will solve 90% of any problems if you have them

let me know if you have any further questions

---

### Post by gl0wst1ckn1nja on 2007-10-19
LOOK INTO WICD

it will solve a lot of your problems

heres how you do it

add this to your third party repositories (System>Administration>Software Sources)--third party tab

deb [http://apt.wicd.net](http://apt.wicd.net) feisty extras

(this will also work for gutsy gibbon users)

then 

```
sudo apt-get install wicd
```

it will remove the network manager applet and replace it with this very nice one that can be found in Applications>Internet>Wicd

then to get Wicd to start on boot add this to System>Preferences>Sessions

sudo ln -s /opt/wicd/tray.py ~/.kde/Autostart/tray.py

close all

restart

enjoy

let me know if you have questions or comments

---

### Post by novithor on 2008-03-28
Thank you a lot WICD works very well

---

### Post by jadrevenge on 2008-04-16
Just got it to work in 7.10 Gutsy not using ndiswrapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)

which lead to:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

added the bcm*cutter packages in add/remove programs

clicked on the "Restricted Driver Manager" and enabled the firmware.

i rebooted (but i'm pretty sure i didn't need too) and it still didn't seem to be working.

i noticed that the wireless switch on this laptop didn't have the light on, pushed it and ran 'sudo iwlist scan' and there were all the networks in all their glory :)

---

### Post by 1caras on 2008-04-30
With only a bit of experience in eeeXubuntu, I'm somewhat of a newbie at Linux, so I might not make myself clear at times, but this solution does work perfectly (albeit with some minor link redirecting) for my computer:

Compaq Presario V2000
AMD Turion 64 Mobile @ 1.8 GHz
ATI Radeon Xpress 200M
Broadcom AirForce One BCM 4318
Ubuntu **Hardy Heron 8.04** installed via Wubi
Target Wireless Network: WPA with SSID broadcast disabled

Again, more information than you may need, but it helps.

[SIZE="5"]Changes To The Guide[/SIZE]

> **Step 2: Get ndiswrapper**

Make sure you have the universe repositories enabled. (google it if you dont know how) and go to a terminal and type the following:

```
sudo apt-get install ndiswrapper-utils
```

this might prompt you for your password and ask you to continue and such, its very easy, just go through it.

The original suggested file seems to be missing from the database, however, adding "-1.9" at the end as such:

```
sudo apt-get install ndiswrapper-utils-1.9
```

redirects aptget to what seems to be a [newer version](http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9) of the same file for Heron. For me, it works all the same.

> Get the drivers you need, i suggest [these ones]("ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip"), and make sure u have the .inf and .sys files of the driver.  If you use the ones i suggested they will be bcmwl5.sys and bcmwl5.inf

The link provided for the drivers download is dead. [This one works for me, though](ftp://ftp.support.acer-euro.com/notebook/aspire_3020)

All in all, the installation process was very successful, and I got wireless working with this specific card in Hardy Heron. Thanks to the OP for a straightforward, simple guide!

---

### Post by WishingForGoats on 2009-02-02
Hooray! It worked! No more windows.

I got ndiswrapper by using the gui.  System/Administration/Synaptic Package Manager.  Search for ndiswrapper.  Select ndiswrapper-utils-1.9.  Add it.

As described in post #74, go to the following site for the files:
[http://rapidshare.com/files/40644803/tecpages.com-bcm4318.zip]("http://rapidshare.com/files/40644803/tecpages.com-bcm4318.zip")

Download the files to Desktop and extract.  When it asks for the password, type: [http://tecpages.com](http://tecpages.com)

The files are named: bcmwl5.inf and bmcwl5.sys

In the terminal, 
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf

check your installation with:
ndiswrapper -l

RESTART THE COMPUTER.

And, since I am a complete newbie, it took a minute to find how to connect to the internet.  For others like me, double click on the icon near the date.  It should list the available networks.

Now my only question is: do I have to leave those files on my Desktop forever?

---

### Post by impervius on 2009-09-13
am having difficulty with the two extra commands- they are not running properly

"modprobe ndiswrapper" returns


WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper , it will be ignored in a future release.

WARNING: All config files need .conf: /etc/modprobe.d/blacklist , it will be ignored in a future release.

---

### Post by strongfan on 2010-04-03
How exactly am I supposed to use apt-get to install the driver if I can't even get on the internet in the first place?

---

### Post by NUboon2Age on 2010-05-15
> **impervius said:**
> am having difficulty with the two extra commands- they are not running properly

"modprobe ndiswrapper" returns


WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper , it will be ignored in a future release.

WARNING: All config files need .conf: /etc/modprobe.d/blacklist , it will be ignored in a future release.

That just means you have to add a ".conf" to the end of those two files.  So you rename 
/etc/modprobe.d/ndiswrapper      
**to **
/etc/modprobe.d/ndiswrapper.conf

and

/etc/modprobe.d/blacklist        
**to**
/etc/modprobe.d/blacklist.conf

I'm not sure if it stops the function of the program or is just warning that in future Linux versions these configuration files may be ignored theoretically at that future time your configuration files will be ignored.

---

### Post by NUboon2Age on 2010-05-15
> **strongfan said:**
> How exactly am I supposed to use apt-get to install the driver if I can't even get on the internet in the first place?

Usually the wired ethernet connector still works so you have to plug in to do these steps.

---

### Post by NUboon2Age on 2010-05-15
Following these directions (including the two "extra steps") worked for me to get a Lucid Lynx 10.4 system working.  After trying **many** other things this worked.  So many thanks!

---

### Post by Riffronan on 2010-09-26
I just want to thank the Ubuntu community for making this work!  I have an Acer Aspire 3690 that I couldn't get the wireless to work.  i went to the site below and did step 1, then step 2a and finally step three which runs the drivers in ndis wrapper and the wireless now works perfectly...JOY.  Saving yet another machine from Windows..

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Tank997 on 2010-11-14
> **Riffronan said:**
> I just want to thank the Ubuntu community for making this work!  I have an Acer Aspire 3690 that I couldn't get the wireless to work.  i went to the site below and did step 1, then step 2a and finally step three which runs the drivers in ndis wrapper and the wireless now works perfectly...JOY.  Saving yet another machine from Windows..

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Thanks, this post got me working!

Like the Porcupine Tree Icon ;)

---

### Post by Riffronan on 2010-11-14
My Pleasure, Tank :)  and thanks for the Kudos..love these guys

   :guitar:

---

### Post by chaocat on 2011-03-25
My issue is solved
[http://ubuntuforums.org/showthread.php?t=1649426&page=2](http://ubuntuforums.org/showthread.php?t=1649426&page=2)

---

### Post by ea00 on 2011-06-17
I'm glad this works for all you guys but nothing works for me at this moment. I'm using Kubuntu 11.04 right now.

---

### Post by gabak on 2011-09-29
here there is other solution.

If you have a wired connection, make sure you have the universe repositories enabled and install synaptic package manager. Once you have synaptic installed search for firmware-b43-installer, right-click to mark it for installation, then click apply. After the packages have downloaded, open the install terminal, and watch to see if the firmware is installed properly. If the firmware installed properly all you should have to do is reboot, and once at the desktop you should have working wireless.

greating
gabriel
from
gabak technologies
[www.gabak.com.ar](www.gabak.com.ar)

> **piracyrocks said:**
> Ok, so there are other tutorials out there for the other 43xx cards, but from my experience, none of them have worked with the specific 4318 card.  This way i will explain below is the only way i have gotten my 4318 card to work with 6.06

**Step 1: Disabling bcm43xx**
Ok, so first thing we need to do is make it so that the pre-installed driver, bcm43xx, doesn't attach to the hardware on bootup.  The way we do this is by blacklisting it.  In a terminal window type:

```
sudo gedit /etc/modprobe.d/blacklist
```

in the window that pops up, find a new line and type: blacklist bcm43xx

After this, reboot and make sure that when you go to System > Administration > Networking there isnt a listing for your wireless connection

**Step 2: Get ndiswrapper**

Make sure you have the universe repositories enabled. (google it if you dont know how) and go to a terminal and type the following:

```
sudo apt-get install ndiswrapper-utils
```

this might prompt you for your password and ask you to continue and such, its very easy, just go through it.

**Step 3: Use ndiswrapper to configure the drivers**

Get the drivers you need, i suggest [these ones]("ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip"), and make sure u have the .inf and .sys files of the driver.  If you use the ones i suggested they will be bcmwl5.sys and bcmwl5.inf

Once you have the driver, put them on the desktop and then go to a terminal and type:

```
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
```

this will install the driver

then, in the same terminal window, type:

```
sudo ndiswrapper -m
```

now restart and you will be able to connect to wireless networks.  If you have a wep encryption on your wireless network, go on to step 4 below.  

**Step 4: Installing Network Manager**

Network manager will allow you to connect to those wep encrpypted networks.

Simply go to a terminal window and type:

```
sudo apt-get install network-manager-gnome
```

Let that install by typing your password and whatnot, then restart and you will be good to go, just click on it up in the corner and select your wireless network.

**Still not working?**
If you still cannot connect to a wireless network try running the following commands in terminal

```
modprobe ndiswrapper
```

and

```
echo ndiswrapper >> /etc/modules
```

**Thanks esavato**

Lemme know if anyone experiences any problems with this, however, i have this exact card and did this exact procedure from a fresh install and it worked flawlessly.  If anyone needs person to person help just catch me on aim at r0nchetti.

---

### Post by dishonest.jack on 2012-01-16
I am posting this here. So that it might help someone.

I tried a thousand things for the Cisco Linksys WPC54G PC card.Finally the simplest of simplest things worked. After a clean install (which I think was the 6th installation of Linux and six others of Windows) I just followed instructions from [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_Internet_access"). 
```
sudo apt-get install b43-fwcutter

``` then restarted. Thats it! 

Its amazing that it was what it boiled down to after days of work!!! No ndiswrapper or anythingelse like that!

10.04 Lucid Lynx

---

