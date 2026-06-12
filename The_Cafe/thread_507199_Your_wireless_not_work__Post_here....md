---
title: "Your wireless not work?  Post here..."
date: 2007-07-22
forum: The Cafe
---

### Post by TheeMahn2003 on 2007-07-22
I am the writer of [Ubuntu Ultimate]("http://ubuntusoftware.info/ultimate/"), I would like to help those of you that can't get their wireless working in Feisty Fawn...  Please post the model number of your wireless card that does not work in Feisty Fawn.  I will make an attempt to have it included in Ubuntu Ultimate 1.4 DVD,  I understand not having internet is a "show stopper" for most people and will work to have it integrated on the DVD.

Please understand I can not go out and purchase each and every wireless card to test, but will "attempt" to have it integrated on the DVD.

Thanks,

TheeMahn

---

### Post by Fubie on 2007-07-22
Hello TheeMahn,

I think it's great that you are going even further than you already have to make Ubuntu one of the greatest distro's out there!

The wireless card I cannot get to work is a Broadcom 54g MaxPerformance 802.11g

I would be so greatfull if you can figure this out.

---

### Post by geraldb on 2007-07-23
First, thanks for all you do for the community.  My son has been having fits trying to get a Sprint card to work in Feisty.  It is a Pantech PX-500.

---

### Post by fak3r on 2007-07-23
First of all, love the ultimate edition, really happy with it (plus I have a nic and a long cat5 - so I still have network), so thanks.  I have a regular Netgear Wifi card (311?) checking in dmesg and it does see the card:

```
[   16.277031] prism2pci_init: prism2_pci.o: 0.2.5 Loaded
[   16.277429] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 17 (level, low) -> IRQ 22
[   16.277442] A Prism2.5 PCI device found, phymem:0xd0000000, irq:22, mem:0xe0a26000
```

Later I see the Ornoco driver loading:

```
[   17.716819] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   17.718441] orinoco_pci 0.15 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean 
Tourrilhes <jt@hpl.hp.com>)
```

But it never connects to my access point - I've even turned off WPA, so no encryption, still nothing.  I run network-manager, choose to connect to my wireless AP - but it fails and falls back to the wired.  Only thing I see is this message in dmesg:

```
[ 1691.045729] eth0: no IPv6 routers present
```

This has always "just worked" in Ubuntu for at least the last 2 years, so I'm not sure why it's failing in Ultimate.

Thanks

fak3r

---

### Post by adewale on 2007-07-24
well in my case its merlin c201 work and zte mg166 cards and both are just new users to linux. so they are stuck.

---

### Post by init1 on 2007-07-24
Mine is recognized in Mepis, but not ubuntu. I have a Compaq Presario C304NR.

---

### Post by rjs82vette on 2007-07-24
I have a Belkin USB network card, but my problem is the card works fine if I can get the USB ports to recognize it but all I get is "not accepting address". 

Still working this issue, but I am getting closer......

---

### Post by jeyaganesh on 2007-07-24
Ubuntu found my **belkin usb adapter** but it says my hardware is not supported for security.

---

### Post by doodaad_1 on 2007-07-25
> **rjs82vette said:**
> I have a Belkin USB network card, but my problem is the card works fine if I can get the USB ports to recognize it but all I get is "not accepting address". 

Still working this issue, but I am getting closer......



Check out my post my symptoms were slightly different but disabling network manager and following the steps in the link solved my problem.....



[http://ubuntuforums.org/showthread.php?p=3072597#post3072597](http://ubuntuforums.org/showthread.php?p=3072597#post3072597)

---

### Post by Enedok on 2007-07-26
I was struggling to get it to work and after about 2 hours i figure out that i must have 64/128 bit ascii and not (only) 128 bit.#-o

Great distro! I'm about to get the hang of ubuntu now.:mrgreen:

---

### Post by TheeMahn2003 on 2007-07-27
I don't want you all thinking I have forgot you all.  I have built what I hope to be my last build of "Ubuntu Ultimate 1.4 DVD" or next to the last ;)  If all goes smoothly, I will go back and try to integrate all drivers posted in this thread.  The last build I made (running now) is by all means awesome, but has 1 bug hopefully fixed.  Please bear in mind even though I add the drivers listed here I have no way to officially test them.  It is burnt, however I am waiting for an upload of 1.4 CD to a mirror to finish before testing it.

If it does not work I did at least try, don't come unglued on me, if it does work I would appreciate at the least a thanks.  Better then most distro makers try to do for their people.

Best regards,

TheeMahn

---

### Post by TheeMahn2003 on 2007-07-27
"Ultimate" failure, will start over, won't get into the details, it did hand me my a** should have built from known good.  Delay is the answer.  133 upgrades should I see it as the problem?, probably should take a leap back and re-start....

---

### Post by Iandefor on 2007-07-27
If it's not too late to suggest a chipset for inclusion whenever, then Broadcom 4318 support would be great. It has a driver in the mainline kernel (bcm43xx) but you have to get the supporting firmware elsewhere.

---

### Post by TheeMahn2003 on 2007-07-29
> **Iandefor said:**
> If it's not too late to suggest a chipset for inclusion whenever, then Broadcom 4318 support would be great. It has a driver in the mainline kernel (bcm43xx) but you have to get the supporting firmware elsewhere.

You made the quota, I am addressing all issues above currently, even though it is built and could upload it right now, I am going to address the above issues, please stand by.  I have not injected any wireless tools YET, nor drivers but works perfectly...  As I have promised I will "attempt" to address the above issues before posting it for everyone.  You can view screenshots [here]("http://ubuntuforums.org/showpost.php?p=3102419&postcount=363"), [here]("http://ubuntuforums.org/showpost.php?p=3102427&postcount=364") and [here]("http://ubuntuforums.org/showpost.php?p=3102433&postcount=365").

The begining:

```
Running Module: mod-install-network_tools.rmod
Running Network Tools...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libadns1 libgdchart-gd2-noxpm libnasl2 libnessus2 nessus-plugins
  snort-common snort-rules-default wireshark wireshark-common
Recommended packages:
  libadns1-bin snmp snort-doc oinkmaster
The following NEW packages will be installed:
  busybox ethereal libadns1 libgdchart-gd2-noxpm libnasl2 libnessus2 nessus
  nessus-plugins nessusd ngrep nmap nmapfe snort snort-common
  snort-rules-default wireshark wireshark-common
0 upgraded, 17 newly installed, 0 to remove and 6 not upgraded.
Need to get 12.7MB of archives.
After unpacking 56.5MB of additional disk space will be used.
```

General:
```
The following extra packages will be installed:
  kdebase-data kicker libbtctl4 libgnomebt0 libopenobex1 ndiswrapper-utils-1.9
Suggested packages:
  khelpcenter kicker-applets menu ndiswrapper-source
The following NEW packages will be installed:
  gnome-bluetooth gnome-ppp kdebase-data kicker kppp kwifimanager libbtctl4
  libgnomebt0 libopenobex1 ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
  netapplet wifi-radar wlassistant
0 upgraded, 15 newly installed, 0 to remove and 6 not upgraded.
Need to get 13.2MB of archives.
After unpacking 31.6MB of additional disk space will be used.
```

Specific comes later...  I will inform all those involved snort is a very heavy security tool which keeps people out of your system, this tool is included in 1.3 however, I feel is responsible for lost internet connections... When someone attempts to hack or hijack your connection it will close the net to you as well as cut them off, this pisses alot of users off, and naturally they blame me.  I feel it is more important to protect you then to lose your internet connection for a few minutes.  For those that hate this feature you can remove it using the following command in a terminal:

```
sudo apt-get remove snort snort-common
```

---

### Post by TheeMahn2003 on 2007-07-29
> **Fubie said:**
> Hello TheeMahn,

I think it's great that you are going even further than you already have to make Ubuntu one of the greatest distro's out there!

The wireless card I cannot get to work is a Broadcom 54g MaxPerformance 802.11g

I would be so greatfull if you can figure this out.

WOW, your card is indeed a huge [issue]("http://www.google.com/search?q=Broadcom+54g+MaxPerformance+802.11g+ubuntu+feisty&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a").

Does this mean you are screwed no, it appears as it sits the best I can do is integrate your driver "windows" based onto the DVD (you would have to load it in with ndis-wrapper, now integrated on the DVD), work off the rip no, at least so far.  I will look further into your situation.  Don't get mad if I fix someone else's first.  I am going to tackle each problem one at a time and come back to visit yours.

EDIT: O.K.  I have decided to integrate your driver onto the DVD just a screenshot of your adapter ;)  And done so while building Ultimate and to top it off using wine ;)  My, my windows seems to become more, and more useless.

The disk is now 17MB larger BTW, hopefully others use the same wireless as you, still have about 3 GB to fill lol.  hmm 17MB times 150,000+ downloads of the CD just from my download server not including mirrors, one can start seeing the math?  I hope your card is popular ;)

---

### Post by TheeMahn2003 on 2007-07-29
> **geraldb said:**
> First, thanks for all you do for the community.  My son has been having fits trying to get a Sprint card to work in Feisty.  It is a Pantech PX-500.

Yours may be an easy [fix]("http://www.raincitystory.com/wp/2007/05/31/pantech-px-500-evdo-rev-a-card-on-linux/") :)

Will let you know when it is integrated, probably in a few minutes ;)


Well I will inform you first thing I see as a problem even though it is indeed an upgraded kernel over feisty UUE 1.4 DVD is at current "2.6.20-15-generic".  If I were to upgrade it to the newest the "restricted drivers" goes to the curb although I have done this before in the past, not w/o re-percussions IE kernel panics etc. from other users.  The script on the desktop will do this for you, however if you have no net connection a show stopper.  I am looking for a work around.

EDIT:  Yours is fixed.. I don't know if you will have to do so or not but to initiate your card you may have to open a terminal and initiate the following command:

```
/usr/sbin/pppd call Sprint_EVDO updetach
```

Once it is released please let me know how it goes for you.

---

### Post by TheeMahn2003 on 2007-07-30
> **fak3r said:**
> First of all, love the ultimate edition, really happy with it (plus I have a nic and a long cat5 - so I still have network), so thanks.  I have a regular Netgear Wifi card (311?) checking in dmesg and it does see the card:

```
[   16.277031] prism2pci_init: prism2_pci.o: 0.2.5 Loaded
[   16.277429] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 17 (level, low) -> IRQ 22
[   16.277442] A Prism2.5 PCI device found, phymem:0xd0000000, irq:22, mem:0xe0a26000
```

Later I see the Ornoco driver loading:

```
[   17.716819] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   17.718441] orinoco_pci 0.15 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean 
Tourrilhes <jt@hpl.hp.com>)
```

But it never connects to my access point - I've even turned off WPA, so no encryption, still nothing.  I run network-manager, choose to connect to my wireless AP - but it fails and falls back to the wired.  Only thing I see is this message in dmesg:

```
[ 1691.045729] eth0: no IPv6 routers present
```

This has always "just worked" in Ubuntu for at least the last 2 years, so I'm not sure why it's failing in Ultimate.

Thanks

fak3r

OK, sorry did not look into this issue along time ago.. Mine is the same way as long as I have a wired connection it always takes presidency, I have (2) gigabit lan connections and wireless, wireless does not work for me no matter what I do as long as lan is there, when I disable both onboard in the bios and disconnect the RJ45 I borrow the neighbors wireless connection ;)  Even from the DVD, I want to touch bases with you to see if this is the same issue you have.

---

### Post by TheeMahn2003 on 2007-07-30
> **adewale said:**
> well in my case its merlin c201 work and zte mg166 cards and both are just new users to linux. so they are stuck.

You may be in the same [situation]("http://www.google.com/search?q=merlin+c201+ubuntu+feisty&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a") as Fubie @ lease for now on the Merlin, please stand by.  Actually both amazing.  Please allow me to continue down the list, will come back to you as well.

EDIT:  Yours as well as others within this forum minus the ones I have fixed will be done as exact same way integrated onto the DVD, I don't know how large yours is.  None the less the same applies.  Please view previous posts.

---

### Post by TheeMahn2003 on 2007-07-30
> **init1 said:**
> Mine is recognized in Mepis, but not ubuntu. I have a Compaq Presario C304NR.

Yours[ thus far]("http://ubuntuforums.org/showthread.php?p=2214468").  Now to integrate it so you don't need to know squat :)

I may have to integrate it as an inf on the DVD, you will have to use ndis-wrapper, as 2 above I hope this is acceptable.  At least you are not 100% out in the cold.  Once again I will come back to the 3 of you to see if there is any way to integrate it into ndis-wrapper.

Edit:
Please review the title of that page: Re: solved presario c304nr ndiswrapper driver, alternative to non-functioning hp down

It is now on the DVD under /wireless/BCM4318/

It is probably best if I do so for each one, it is not that I don't care but wireless issues are probably more then I want to bite off, I have my hands full as it is I will post a how to for those of you that have posted here, that I did not "fix".

---

### Post by TheeMahn2003 on 2007-07-30
I am calling it an eve.  will pick up on it tommorow ;)

---

### Post by Fubie on 2007-07-30
TheeMahn!  Thank you so much for adding it to the DVD.  I appreciate it very much.  I will let you know how it works.  I hope you get to release the DVD this week yet.

> **TheeMahn2003 said:**
> WOW, your card is indeed a huge [issue]("http://www.google.com/search?q=Broadcom+54g+MaxPerformance+802.11g+ubuntu+feisty&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a").

Does this mean you are screwed no, it appears as it sits the best I can do is integrate your driver "windows" based onto the DVD (you would have to load it in with ndis-wrapper, now integrated on the DVD), work off the rip no, at least so far.  I will look further into your situation.  Don't get mad if I fix someone else's first.  I am going to tackle each problem one at a time and come back to visit yours.

EDIT: O.K.  I have decided to integrate your driver onto the DVD just a screenshot of your adapter ;)  And done so while building Ultimate and to top it off using wine ;)  My, my windows seems to become more, and more useless.

The disk is now 17MB larger BTW, hopefully others use the same wireless as you, still have about 3 GB to fill lol.  hmm 17MB times 150,000+ downloads of the CD just from my download server not including mirrors, one can start seeing the math?  I hope your card is popular ;)

---

### Post by TheeMahn2003 on 2007-07-31
> **adewale said:**
> well in my case its merlin c201 work and zte mg166 cards and both are just new users to linux. so they are stuck.

Ok, I have included a script on the disk, you will have to modify: /etc/ppp/chap-secrets to replace the phone number password etc below is what it looks like:
```
# File: /etc/ppp/chap-secrets
#
# Secrets for authentication using CHAP
# client                                server   secret   IP addresses
YOUR_CELLULAR_PHONE_NUMBER@vzw3g.com    verizon  vzw      *

```

This is for your merlin c201, below is the script for the dialer (you don't have to know any of this):
```
# File: /etc/ppp/peers/verizon
#
/dev/ttyACM0    # device
# The following two settings need a corresponding entry in
# /etc/ppp/chap-secrets.
user YOUR_CELLULAR_PHONE_NUMBER@vzw3g.com
remotename verizon
115200        # speed
defaultroute  # use the cellular network for the default route
usepeerdns    # use the DNS servers from the remote network
nodetach      # keep pppd in the foreground
crtscts       # hardware flow control
lock          # lock the serial port
noauth        # don't expect the modem to authenticate itself
novj
novjccomp
# scripts for connection/disconnection
connect    "/usr/sbin/chat -v -f /etc/chatscripts/verizon-connect"
disconnect "/usr/sbin/chat -v -f /etc/chatscripts/verizon-disconnect"
```

Connection-disconnection script (don't have to know any of this as well):
```
# File: /etc/chatscripts/verizon-connect
#
TIMEOUT 10
ABORT   'BUSY'
ABORT   'NO ANSWER'
ABORT   'NO CARRIER'
SAY 'Starting CDMA connect script\n'

# Get the modem's attention and reset it.
''  'ATZ'

# E0=No echo, V1=English result codes
OK      'ATE0V1'

# Dial the number
SAY 'Dialing...\n'
OK  'ATD#777'
CONNECT ''

# File: /etc/chatscripts/verizon-disconnect
#
""  "\K"
""  "+++ATH0"
SAY "CDMA disconnected."
```

the following to connect once set:
```
pppd call verizon
```

 as root and press Ctrl-C when done.

Best I can do for that 1, looking into the other...  Can't find any sort of fix nor driver for the other card sorry.  ZTE is tight nit and doesn't just allow downloading of drivers.

---

### Post by adewale on 2007-08-01
thanks i'll give it a shot

---

### Post by adewale on 2007-08-02
Themann here's a little problem, my friends can't download the ultimate dvd cause of our internet, so i was wondering can u give me a link to download the script ? or would this work with an original fiesty. Thanks

---

### Post by jeanniegenie on 2007-08-02
i have Ubuntu 6.10 and i cannot get wireless. 

I typed in lspci | grep Broadcom\ Corporation and I get:

```
05:00.0 network controller: Broadcom Corporation Unknown device 4311 (rev 01)
08:00.0 NEthernet controller: Broadcom Corporation BCM4401-B0 100Base -TX (rev 02)
```

I also tried using the ndiswrapper on the bcm4318.all.tar.gz file but that did not work.

---

### Post by maven2k on 2007-08-06
This is great.  I have a Hawking Technologies HWC54D.  Any help would be much appreciated!

Update:  This is what Hawking sent me when I asked them about it:

We don't support Linux but it uses the Ralink RT256x driver
You can get it here
[http://www.ralink.com.tw/Home/Support/Linux.html](http://www.ralink.com.tw/Home/Support/Linux.html)

---

### Post by TheeMahn2003 on 2007-08-07
I'm sorry fellas I did fix the ones up until I posted that I was building the disk, you can try 1.4 DVD, I'm sorry I can no longer dedicate the time to resolve all wireless issues.

---

### Post by TheeMahn2003 on 2007-08-07
> **adewale said:**
> Themann here's a little problem, my friends can't download the ultimate dvd cause of our internet, so i was wondering can u give me a link to download the script ? or would this work with an original fiesty. Thanks

I see no reason it shouldn't work you can get the script [here]("http://repoubuntusoftware.info/upgrades/gamers.sh").

---

### Post by hessiess on 2007-08-07
[http://ubuntuforums.org/showthread.php?t=434944]("http://ubuntuforums.org/showthread.php?t=434944"):(

---

### Post by adewale on 2007-08-08
thanks theemann but i think i got the wrong scrpt. i meant the script for the wireless. or would your previous post work without a script thanks.

---

### Post by BuildComp123 on 2007-08-21
Can you get the belkin pre n card -> [http://catalog.belkin.com/IWCatProductPage.process?Product_Id=186931]("http://catalog.belkin.com/IWCatProductPage.process?Product_Id =186931") and the belkin n1 notebook card verison. 1000 [http://catalog.belkin.com/IWCatProductPage.process?Product_Id=273544]("http://catalog.belkin.com/IWCatProductPage.process?Product_Id =273544") to work thanks

---

### Post by shelbycobra on 2007-09-05
I cannot wait to try this distro.  I have been very impressed with Fiesty Fawn upto the point when I could not get my wireless to work.  I have a Atheros AR5BXB67 a/b/g/n card.  So far the driver installs with ndiswrapper, but the wlan0 card will not present itself.

Thank you,

---

### Post by booster614 on 2007-09-08
Hey...i gotta say i love the look of the ultimate gamers edition, but i cant configure my wireless card/cards...i have 2 of them and ive tried them both...with no luck, one of my cards worked with the regular ubuntu 7.04 fiesty fawn, but not with the ultimate??? i cant figure it out, the name of the 2 cards i have are Trendnet TEW-423PI and the other is a airlink101 AWLH3026 802.11g PCI, please tell me what i need to do to get my wifi runing on this OS. thanks in advance

---

### Post by ONoff on 2007-09-25
BCM 1390 in a Dell D620

I can get this to work with ndiswrapper, but the config is very unstable, and will sometimes corrupt itself...or I corrupt it...

Thanks, and keep up the excellent work!
ONoff

---

### Post by defconoii on 2007-09-29
Bus 004 Device 003: ID 050d:705a Belkin Components rt73
Not working out of the box, never did, I know how to install drivers from serialmonkey and these hang gutsy after blacklisting other drivers and all, posted various bug reports,

---

### Post by davidyu on 2007-10-02
I can use LEAP support  in Ubuntu 7.04.
I upgrade to Ubuntu 7.10 yesterday. and then LEAP not working any more.  In 7.04, I modify /etc/wpa_supplicant/wpa_supplicant.conf and issue command "dhclient ath0" to make leap working.
    Unlucky, in 7.10 Beta, it not working any  more
anybody know why ?

---

### Post by savemekaizer on 2007-10-02
Mine is on/off; I'm thinking it's more a router problem (I had issues even when I was with Windows). It'll work like magic for about an hour, then just.. die. I'll have to restart the router, unplug and replug my adapter, and do the whole 'sudo /etc/init.d/networking restart' (or something like it) deal.

I'm using a Netgear WG111V1, with an Actiontec MI-numbernumbernumber router; the black box of heat that Verizon gave us for FiOS.

---

### Post by glabbott on 2007-10-15
I have a Dell 640m with a Dell Wireless 1390 WLAN mini card installed, checking the hardware profile in ubuntu it shows but I cant connect to my wireless router, I have the WPA/PSK TKIP code and the SSID but it just wont connect.  I have tried many many times, I even tried running the driver from dell for windows xp installing using the wise installer but it crashes.

Any help would be great peeps.

Thanks.

---

### Post by jblake on 2008-05-08
Hi, very impressed with Ultimate 1.7 live not installed - not tried the wireless issue yet. The only distros I have got to work (and then only live) are Xandros Open Source 4 and PCLinuxOS 2007 - after install they fell over!) Using an Atheros based Netgear USB dongle WG111T.

---

### Post by gali98 on 2008-05-08
> **jblake said:**
> Hi, very impressed with Ultimate 1.7 live not installed - not tried the wireless issue yet. The only distros I have got to work (and then only live) are Xandros Open Source 4 and PCLinuxOS 2007 - after install they fell over!) Using an Atheros based Netgear USB dongle WG111T.

hey man.... this thread is really old and I doubt it will get answered.
Kory

---

### Post by liquidfunk on 2008-05-08
WG111v3 would be nice, and under 64bit too ^^

---

### Post by coyotech on 2008-05-11
Verizon UM150 USB modem...once I got it almost connecting. Now it always says the modem isn't responding. It changes ttyUSBx everytime I connect, sometimes even while connecting. The dialup manager in networking manager keeps calling it a ppoe connection over ethernet...no matter what I do it puts it back to that, which is wrong. I think I should wipe out my previous attempts and start over, but don't know how! I'm going to have to switch back to Windows if I can't get it figured out soon, even though I'm starting to get around in Linux OK now and get other things configured. I hope you have some info that will help!

---

### Post by Jaxl on 2008-05-11
Hello and thank you for this forum. I have a Verizon Wireless EVDO
EV720. 1xEVDO Rev-A. I have been throught countless forums sites and i cannot get the concept of some of it and i get lil frazzled XD but i also dont know if it matters if i follow a diff tut then my verizon card ..

---

### Post by -gabe-noob- on 2008-05-11
yeah my restricted drivers wont work  :mad::mad::mad:

---

### Post by kate_gareth on 2008-06-04
Help desperately needed!

I have an external Wireless card (EDUP IEEE 802.11G) and a wireless router(Netgear).  Everything was working fine (internet wise)and I decided to re-format my hard drive and re-install Windows XP.  After I had finished the wireless card will not connect to the internet. It can see thenetwork but will not connect.  

I thought the card may have broken so I borrowed a friend and this doesn't work either.  Other people in my household can access the wireless router and get online with no issues. 

I can get on with an ethernet cable but just not wirelessly!

Any ideas? I'm going out of my mind trying to work out what is causing it!

Thanks very much

---

### Post by theemahn on 2008-12-24
Blows my mind, but is it my job to resolve.  Why?  Merry Xmas, I am no joke they will wake up & wont understand how...  They now want me to work for them?  Why ask?  If I am a big screw up.  Watch  Ultamatix closely, I will re-establish.  Never talk squat about me.  I would have used much bolder statements, but I do understand there are children here as well.

Remember me wholeheartedly as "TheeMahn", search that on google once.  Just once ;)

Let me currently help you out:  Results 1 - 10 of about 83,500 for TheeMahn. (0.20 seconds) 


Am I making a name for myself?  Or are others doing so for me?  Talked about like I am a god, that is coming, sit tight.  I was the one that has been threatened to be sued.  Why would you do that when I can deliver you greater traffic?  Oh I am sorry, I am stupid. Don't ask me to join you again, and on your forum ;)  Stoke me...

Kudos,

TheeMahn

TheeMahn

---

### Post by ve3bwp on 2008-12-27
I'm new to Linux but old at Dos etc. Wanted to learn this to be able to move away from windows where possible. Vista pushed me over the edge.

I just installed Ubuntu 8.10 on my old HP Omnibook 6100. So far so good but the wireless is not connecting. Before this I tried Xubuntu 8.10 live and the wireless worked great.It connected to both of my routers no problem with WEP64. Wired works fine.

The card is an Actiontec 802MIP. It lets me see the signal strength but will not connect even when I dropped WEP64 and used no security.

Below is the IFCONFIG output: To my untrained eye it looks like the wireless card is not assigned properly. Hoping some one can point me in the right direction. Thanks.

eth1      Link encap:Ethernet  HWaddr 00:c0:9f:06:53:ed  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe06:53ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57278 (57.2 KB)  TX bytes:5326 (5.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-20-E0-88-87-D6-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:24 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59355 (59.3 KB)  TX bytes:0 (0.0 B)
          Interrupt:10 

wlan0     Link encap:Ethernet  HWaddr 00:20:e0:88:87:d6  
          inet6 addr: fe80::220:e0ff:fe88:87d6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:109 errors:0 dropped:68 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:38100 (38.1 KB)  TX bytes:5256 (5.2 KB)
          Interrupt:10

---

### Post by ve3bwp on 2008-12-27
TheeMahn2003 on reading the entire thread I realize now I should have posted elsewhere. sorry no intent to destract your thread. I will repost in a more appropriate location.

---

### Post by sacullmot on 2009-03-07
Mine is the Netgear WG111T USB dongle.  Any Ideas?

---

