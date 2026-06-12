---
title: "Samsung NP-N130 - no wifi"
date: 2009-11-10
forum: Ubuntu Moblin Remix
---

### Post by unplugme on 2009-11-10
Hello

I have the new Samsung NP-N130 with the Realtek wireless card - b/g/n and I cannot get it to work. Someone told me about ndiswrapper but i'm not sure how to set something like this up. Anyone care to help?

I am able to get wired ethernet working, so I do have internet access to download any files I may need. I also have a computer with Mac OS X / Windows XP if I need to use either.

I have some linux command line knowledge, but detailed instructions would be great!

---

### Post by schmickey on 2009-11-11
I had the same problem with an Asus laptop until I upgraded to Ubuntu 9.10.  Except my problem was reversed... I had Wi-Fi but no LAN(ethernet).  Try Ubuntu 9.10 or Ubuntu 9.10 Netbook Remix.  The latest version has more recent drivers.

---

### Post by rj0b on 2009-11-12
i have exatlty the same problem and i am using 9.10

---

### Post by philefluxx on 2009-12-05
Same issue here. Currently running the UNR 9.10 with the Samsung N130 Realtek 8192 wireless. Ive tried installing drivers via ndiswrapper and no matter what I do the system does not recognize I have a wireless card.

---

### Post by philefluxx on 2009-12-05
Ok so I just did another reload and was able to get it to work. Here is what I did:

1. Fresh install 9.10 UNR
2. I installed all updates through the Update Manager using the ubuntu.securedservers.com
3. Installed ndiswrapper through Synaptic Package Manager including gui.
4. Downloaed RT driver [here]("http://www.s5amsung.com/us/support/detail/supportPrdDetail.do?menu=SP01&prd_mdl_cd=NP-N130-KA04US&prd_mdl_name=NP-N130&prd_ia_sub_class_cd=P")
5. Unzipped the file into the same directory
6. Used the Windows Wireless Drivers tool (ndiswrapper gui)
7. Choose the net829xp driver, install

Magically this time it worked, to be perfectly honest I tried all this before but performed it through terminal. Not sure what to think of that...

---

### Post by Strudelmeister on 2009-12-06
I got the wireless to work the exact same way on my n130. It is not working perfectly though. I have connection issues on **battery mode**, once my battery levels reach roughly 20% the wireless connection cycles, then disconnects me, leaving me unable to connect. Which is annoying as hell, to say the least.

Once I connect the power adapter it takes multiple attempts to activate the wireless, or a few restarts.

Can anyone else confirm this is happening to them as well? Is there a configuration setting that allows me to handle my hardware during low battery mode?

---

### Post by philefluxx on 2009-12-06
> **Strudelmeister said:**
> I got the wireless to work the exact same way on my n130. It is not working perfectly though. I have connection issues on **battery mode**, once my battery levels reach roughly 20% the wireless connection cycles, then disconnects me, leaving me unable to connect. Which is annoying as hell, to say the least.

Once I connect the power adapter it takes multiple attempts to activate the wireless, or a few restarts.

Can anyone else confirm this is happening to them as well? Is there a configuration setting that allows me to handle my hardware during low battery mode?

I dont see anything specific to UNR that may be doing that. You might want to check the Phoenix bios settings. My wireless is set to always on and I dont use any of the battery life saver options in it. I am currently sitting at 40%, Ill post back my results when I get around the 20% level.

---

### Post by philefluxx on 2009-12-06
Currently sitting at 18% and not even a hiccup to the wireless, sorry man. But I would suggest a fresh install if you had tried to get the wireless working in any other way then what actually works. Seems UNR is a bit picky, at least on the N130.

---

### Post by Strudelmeister on 2009-12-06
Ah, thanks a lot for testing that.

I'll check the bios, good call... I've noticed it could also be this particular network (through BT in the UK), that has me manually re-logging multiple times and on low battery not at all.

I'll check it across different networks and bios :)

Thanks again!

---

### Post by vze326ff1 on 2009-12-19
I am having the same problem, I just bought a n130 samsung and I am not sure if it has a realtek or a atheros in it.  I already installed ubuntu remix and updated it. I installed  ndiswrapper and installed drivers for both atheros and realtek.  realtek I get invalid driver and atheros I get hardware no persent.   But if I go the system testing  and perform network testing it saids it detects realtek semiconductor co. ltd device 8192 (rev 01)  and  realtek semiconductor co. ltd rtl8101e/rtl8102e pci express fast ethernet controller (rev 2) 
 I have a wireless light on and check my BIOS and it said wireless card on all the time. I hook ethernet cable up and it connects fine and I stole my kids Belkin wifi stick and it connects fine with that    Please Help!!

---

### Post by Dovekie on 2009-12-20
Hello,

I have an N130 with the latest version of Ubuntu, and it will not acknowledge my wifi card. I followed the steps that philefluxx listed (except that the net829xp driver does not seem to exist; is that a typo for net819xp? If not, where can I find net829xp?). The wireless still doesn't work.

I keep seeing a "Unable to see if hardware is present" error in Windows Wireless Drivers.

Any help you can offer would be greatly appreciated.

---

### Post by Doggonit on 2009-12-23
Dovekie, I've had the same issue, and here's the solution:

-After installing the net819xp driver with the Windows Wireless Drivers tool (the ndiswrapper gui) I figured that the issue was that the ethernet and wlan connections can't work at the same time. I came across this before, on 7.10

So, unplug the ethernet cable, then RIGHT click on the little ethernet icon on the top right (next to the date/time) and unselect "Enable Wireless". 

Next, RIGHT click on it, again, reselect it, and in a second or two, you should see the WiFi style strength indicator icon rather than the Ethernet icon. 

Now, just LEFT click on it, and select your access point, wait for it to finish connecting, and presto, you should be up and running.

I'm not sure if it's actually necessary to unselect and deselect the "Enable Wireless", I haven't played around with it much (as I only use Ethernet when there's no wireless, and there is wireless now!), maybe the icon changes automatically after a little time, but this way should definitely work.

Let me know how it works out for you and if you have any further issues with it.

Toodles,

D.

---

### Post by Shake 'n' Bake on 2009-12-26
I've got the same problem, but I don't know where or how to get the driver.  Could anyone enlighten me?

Thanks.

---

### Post by helliewm on 2009-12-27
To compile the Realtek driver. I am using Karmic Netbook Remix UNR

Download driver from here [URL="http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz"]http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz
 [/URL]
[http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz](http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz)
 
On Netbook Remix it should download into your Download folder. Go to your Download folder and Extract the file. Click on it, it will open then click Extract.

Open the Terminal and Change Directory to Extracted file by typing this into the Terminal 

cd Downloads/rtl819Xe

Next in the Terminal type

sudo su

./install.sh

Ignore any error messages it will say kernel mismatched 5 times.

Your wifi driver on the N130 should now work. The above was adapted from this thread  [http://ubuntuforums.org/showthread.php?t=1329254&page=2]("http://ubuntuforums.org/showthread.php?t=1329254&page=2")  

Hope this helps. It worked first time on my N130.

Helen

---

### Post by Shake 'n' Bake on 2009-12-27
I got bored of waiting and found something similar on some guy's blog.  It works, but it's really slow and it takes about a minute just to get to my router's administration page.  Got any tips?

---

### Post by helliewm on 2009-12-27
Have you checked the router setting? Mine is fine faster using the on board n wifi than the wifi usb dongle I was using.

Helen

Ps Did you follow my instructions above?

---

### Post by Shake 'n' Bake on 2009-12-27
I did follow those instructions, but it's still slow.  I'll have to see if another computer is downloading updates or something.

---

### Post by helliewm on 2009-12-27
Try rebooting. Could be your internet is just slow, too many people on line.

---

### Post by ajmatson on 2009-12-28
I had the same issues and after searching and trying to compile a version I found that the Realtek card in the N130 is actually a Realtek 8182E chip. The driver that worked was the rtl819Xe version from Realtek that can be found [here]("http://ajmatson.net/wordpress/?p=84"). Just download it an follow the instructions I have on the page. 

It worked like a charm for me and I have been up and running since Christmas with no wireless issues and no lag at all as seen below on my DSL line over a wireless G connection. (My DSL speeds are 12Mb down and 750Kb up)

[[IMG]http://www.speedtest.net/result/665496208.png[/IMG]](http://www.speedtest.net)

Post on my page if you are having any issues that I can help with.

---

### Post by vze326ff1 on 2009-12-29
> **helliewm said:**
> To compile the Realtek driver. I am using Karmic Netbook Remix UNR

Download driver from here [URL="http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz"]http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz
 [/URL]
[http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz](http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz)
 
On Netbook Remix it should download into your Download folder. Go to your Download folder and Extract the file. Click on it, it will open then click Extract.

Open the Terminal and Change Directory to Extracted file by typing this into the Terminal 

cd Downloads/rtl819Xe

Next in the Terminal type

sudo su

./install.sh

Ignore any error messages it will say kernel mismatched 5 times.

Your wifi driver on the N130 should now work. The above was adapted from this thread  [http://ubuntuforums.org/showthread.php?t=1329254&page=2](http://ubuntuforums.org/showthread.php?t=1329254&page=2)  

Hope this helps. It worked first time on my N130.

Helen
OOOHHH HHEEYY!!!!   this worked like a charm   THANK YOU!!!!!!

---

### Post by helliewm on 2010-01-01
> **helliewm said:**
> To compile the Realtek driver. I am using Karmic Netbook Remix UNR

Download driver from here [URL="http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz"]http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz
 [/URL]
[http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz](http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz)
 
On Netbook Remix it should download into your Download folder. Go to your Download folder and Extract the file. Click on it, it will open then click Extract.

Open the Terminal and Change Directory to Extracted File by typing this into the Terminal 

cd Downloads/rtl819Xe

Next in the Terminal type

sudo su

./install.sh

Ignore any error messages it will say kernel mismatched 5 times.

Your wifi driver on the N130 should now work. The above was adapted from this thread  [http://ubuntuforums.org/showthread.php?t=1329254&page=2]("http://ubuntuforums.org/showthread.php?t=1329254&page=2")  

Hope this helps. It worked first time on my N130.

Helen

RE my instructions above if the wifi driver does not load at start up open up the Terminal and type the following:

sudo gedit /etc/modules

Type in your password

A text file with appear add the following line:

r8192_pci

and SAVED IT.

Reboot and your wifi will start or alternatively to save rebooting in the Terminal type:

sudo modprobe r8192_pci

This command simply restarts your wifi and Text file where you added the line r8192_pci (as the instructions above) restarts wifi every time you reboot 

I have tried this myself.

Any queries leave a post or PM me and I will try to help.

Helen

Ps I have tried to make this as simple as possible for anyone using Ubuntu for the first time.

---

### Post by satismo on 2010-01-09
helen; it's no small wonder you were named after a goddess

---

### Post by blazemore on 2010-01-12
I'm compiling the kernel now.
If it works I'll put it up here as a deb
Only changes will be new wireless card, processor type set as Intel Atom, and no virtualisation. Basically, Samsung n-series netbooks.

---

### Post by helliewm on 2010-01-12
A deb would be excellent. Thanks.

Helen

Ps The guy who runs Linux on my Samsung has an experimental PPA for this wireless driver too on the N130/N140.[http://www.voria.org/forum/viewforum.php?f=15]("http://www.voria.org/forum/viewforum.php?f=15")

---

### Post by blazemore on 2010-01-12
It's a deb for the ENTIRE KERNEL not just the driver. It does have the driver built in however. Only install it if you'd be happy compiling a kernel yourself but can't be bothered.

---

### Post by helliewm on 2010-01-12
Yes thanks for that. I was aware it was a kernel issue. Yes I am too lazy to compile my own :D:D

Helen

---

### Post by pshadey on 2010-01-12
> **helliewm said:**
> RE my instructions above if the wifi driver does not load at start up open up the Terminal and type the following:

sudo gedit /etc/modules

Type in your password

A text file with appear add the following line:

r8192_pci

and SAVED IT.

Reboot and your wifi will start or alternatively to save rebooting in the Terminal type:

sudo modprobe r8192_pci

This command simply restarts your wifi and Text file where you added the line r8192_pci (as the instructions above) restarts wifi every time you reboot 

I have tried this myself.

Any queries leave a post or PM me and I will try to help.

Helen

Ps I have tried to make this as simple as possible for anyone using Ubuntu for the first time.

Thanks Helen, It worked...
I did however go about it a slightly different way and i just wanted to let everyone know how i went about it.
I download the driver, then extracted it just like helen said to, but then instead of typing anything into terminal i just opened the file that i extracted AS ROOT by right clicking on it and selecting OPEN AS ROOT once opened i just selected the install.sh file i then got prompted to run in terminal as well as a few other options. I selected run in terminal and the script did the rest........i then edited the etc/modules folder by adding r8192_pci and saved it. 
ALSO before i ran the script i disabled networking, not sure if that made a difference, just thought i would let it be known....


Thanks Helen For all your help....and hopefully this post helps someone else

---

### Post by blazemore on 2010-01-13
Okay I didn't compile a deb but here's a nice script that will work:

```

sudo su
cd
mkdir wireless
cd wireless
wget http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz
tar xvf rtl819Xe.tar.gz
cd rtl819Xe
./install.sh
echo r8192_pci >> /etc/modules
modprobe r8192_pc
cd ../../
rm -rf wireless
exit
exit

```

Also, I uploaded the tar.gz here just in case that one goes down for whatever reason.

---

### Post by helliewm on 2010-01-13
Thanks so much for this, the script makes it so much easier.

Pshadey so pleased it worked. Yes totally agree there are different ways to do this. I was just trying to make it easy for newbies so they could see what they where doing, hopefully!:D

Wondering if we should make this a Tutorial as it works for both the N130/N140?

Helen

---

### Post by blazemore on 2010-01-13
I have a weird problem. Not all networks are showing up, and it's not just the weakest ones.
For example, my network is the strongest and it isn't showing on the list.
Do you think it could be the wireless frequency channel?

---

### Post by helliewm on 2010-01-13
Could be your wireless channel. If I close my lid sometimes the wifi will not restart. I have to reboot. If you go to [www.linuxonmysamsung.com](www.linuxonmysamsung.com) The guy there has made an experiemental ppa to deal with the wireless issues on the N130/140. I have not recommended it on this thread as its an experimental ppa but that may solve your problem?

Helen

EDit: Here is the experimental ppa [https://launchpad.net/~voria/+archive/archive/]("https://launchpad.net/~voria/+archive/archive/") Also here is the thread discussing it [http://www.voria.org/forum/viewtopic.php?f=3&t=338]("http://www.voria.org/forum/viewtopic.php?f=3&t=338")

---

### Post by tshearman on 2010-02-12
Hey everyone.  I'm experiencing sort of a strange problem related to the samsung n130 wireless.  I ran the short script and everything worked awesome--wireless up and running.

Then, I reboot and the network connection manager reads: device not ready.  I have "Enable Wireless" checked.

I also ensured that r8192_pci is listed in /etc/modules.

lsmod reads: r8192_pci             240564  0 (and others of course).

A little bit confused, anyone else experienced this? Anyone fixed this?
Thanks,
ts

**Update, if I sudo rmmod r8192_pci, then sudo modprobe r8192_pci, the wireless works fine... weird--help

---

### Post by skytail on 2010-04-16
Helen your a star 

thank you

---

### Post by rogerdean on 2010-05-20
Hi there all. I can't get ethernet on my N130... I've got the wifi going at last, but no wired connection. It sees auto eth0 in network manager, but fails to connect. I've tried unticking 'enable wireless' in case only one connection can work at a time, but no change. Does ethernet work for you folks?
Cheers!
Roger

---

### Post by fight2survive on 2010-10-02
helliewm THANK YOU SO MUCH i was scared i wouldnt be able to use ubuntu with internet on my computer but this worked just fine...THANK YOU!!!!

---

### Post by accelerate on 2010-11-15
how do i ignore the warning?

turas@ubuntu:~$ sudo apt-get install build-essential
[sudo] password for turas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
turas@ubuntu:~$ tar -xpf rtl819Xe. tar.gz
tar: rtl819Xe.: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
turas@ubuntu:~$ tar -xpf rtl819Xe.tar.gz
tar: rtl819Xe.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
turas@ubuntu:~$ cd rtl819Xe
bash: cd: rtl819Xe: No such file or directory
turas@ubuntu:~$ cd Downloads/rtl819Xe
turas@ubuntu:~/Downloads/rtl819Xe$ sudo .install.sh
sudo: .install.sh: command not found
turas@ubuntu:~/Downloads/rtl819Xe$ sudo su
root@ubuntu:/home/turas/Downloads/rtl819Xe# .install.sh
.install.sh: command not found
root@ubuntu:/home/turas/Downloads/rtl819Xe# sudo ./install.sh
Building kernel module...
make: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
  CC [M]  /home/turas/Downloads/rtl819Xe/r8192E_core.o
/home/turas/Downloads/rtl819Xe/r8192E_core.c: In function ‘rtl8192_alloc_rx_desc_ring’:
/home/turas/Downloads/rtl819Xe/r8192E_core.c:1579: warning: passing argument 2 of ‘pci_map_single’ makes pointer from integer without a cast
include/asm-generic/pci-dma-compat.h:33: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/turas/Downloads/rtl819Xe/r8192E_core.c: In function ‘rtl8192_rx’:
/home/turas/Downloads/rtl819Xe/r8192E_core.c:5809: warning: passing argument 2 of ‘pci_map_single’ makes pointer from integer without a cast
include/asm-generic/pci-dma-compat.h:33: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/turas/Downloads/rtl819Xe/r8192E_core.c: At top level:
/home/turas/Downloads/rtl819Xe/r8192E_core.c:720: warning: ‘rtl8192_set_mode’ defined but not used
/home/turas/Downloads/rtl819Xe/r8192E_core.c:865: warning: ‘rtl8192_beacon_disable’ defined but not used
/home/turas/Downloads/rtl819Xe/r8192E_core.c:903: warning: ‘rtl8192_reset’ defined but not used
  CC [M]  /home/turas/Downloads/rtl819Xe/r8180_93cx6.o
  CC [M]  /home/turas/Downloads/rtl819Xe/r8192E_wx.o
  CC [M]  /home/turas/Downloads/rtl819Xe/r8190_rtl8256.o
  CC [M]  /home/turas/Downloads/rtl819Xe/r819xE_phy.o
  CC [M]  /home/turas/Downloads/rtl819Xe/r819xE_firmware.o
  CC [M]  /home/turas/Downloads/rtl819Xe/r819xE_cmdpkt.o
/home/turas/Downloads/rtl819Xe/r819xE_cmdpkt.c: In function ‘cmpk_message_handle_tx’:
/home/turas/Downloads/rtl819Xe/r819xE_cmdpkt.c:138: warning: assignment makes pointer from integer without a cast
  CC [M]  /home/turas/Downloads/rtl819Xe/r8192E_dm.o
  CC [M]  /home/turas/Downloads/rtl819Xe/ieee80211/ieee80211_rx.o
/home/turas/Downloads/rtl819Xe/ieee80211/ieee80211_rx.c: In function ‘RxReorderIndicatePacket’:
/home/turas/Downloads/rtl819Xe/ieee80211/ieee80211_rx.c:800: warning: the frame size of 1072 bytes is larger than 1024 bytes
  CC [M]  /home/turas/Downloads/rtl819Xe/ieee80211/ieee80211_softmac.o
  CC [M]  /home/turas/Downloads/rtl819Xe/ieee80211/ieee80211_tx.o
  CC [M]  /home/turas/Downloads/rtl819Xe/ieee80211/ieee80211_wx.o
/home/turas/Downloads/rtl819Xe/ieee80211/ieee80211_wx.c: In function ‘ieee80211_wx_set_gen_ie_rsl’:
/home/turas/Downloads/rtl819Xe/ieee80211/ieee80211_wx.c:979: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘size_t’
  CC [M]  /home/turas/Downloads/rtl819Xe/ieee80211/ieee80211_module.o
/home/turas/Downloads/rtl819Xe/ieee80211/ieee80211_module.c: In function ‘store_debug_level’:
/home/turas/Downloads/rtl819Xe/ieee80211/ieee80211_module.c:304: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/turas/Downloads/rtl819Xe/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/turas/Downloads/rtl819Xe/ieee80211/rtl819x_HTProc.o
  CC [M]  /home/turas/Downloads/rtl819Xe/ieee80211/rtl819x_TSProc.o
/home/turas/Downloads/rtl819Xe/ieee80211/rtl819x_TSProc.c: In function ‘RxPktPendingTimeout’:
/home/turas/Downloads/rtl819Xe/ieee80211/rtl819x_TSProc.c:109: warning: the frame size of 1056 bytes is larger than 1024 bytes
  CC [M]  /home/turas/Downloads/rtl819Xe/ieee80211/rtl819x_BAProc.o
/home/turas/Downloads/rtl819Xe/ieee80211/rtl819x_BAProc.c: In function ‘ieee80211_rx_ADDBAReq’:
/home/turas/Downloads/rtl819Xe/ieee80211/rtl819x_BAProc.c:385: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/turas/Downloads/rtl819Xe/ieee80211/rtl819x_BAProc.c: In function ‘ieee80211_rx_ADDBARsp’:
/home/turas/Downloads/rtl819Xe/ieee80211/rtl819x_BAProc.c:484: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/turas/Downloads/rtl819Xe/ieee80211/rtl819x_BAProc.c: In function ‘ieee80211_rx_DELBA’:
/home/turas/Downloads/rtl819Xe/ieee80211/rtl819x_BAProc.c:614: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/turas/Downloads/rtl819Xe/ieee80211/dot11d.o
  CC [M]  /home/turas/Downloads/rtl819Xe/ieee80211/ieee80211_crypt.o
  CC [M]  /home/turas/Downloads/rtl819Xe/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/turas/Downloads/rtl819Xe/ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /home/turas/Downloads/rtl819Xe/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/turas/Downloads/rtl819Xe/r8192_pci.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: Found 5 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /home/turas/Downloads/rtl819Xe/r8192_pci.mod.o
  LD [M]  /home/turas/Downloads/rtl819Xe/r8192_pci.ko
make: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
Copying firmware...
Installing module and rebuilding dependencies...
Removing r8192e_pci and  r8192se_pci...
ERROR: Removing 'r8192_pci': Device or resource busy
ERROR: Module r8192e_pci does not exist in /proc/modules
ERROR: Module r8192se_pci does not exist in /proc/modules
Loading module...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
 

after that i cant do anythng else

---

### Post by mfkahn on 2011-02-11
Here's what I experienced with Ubuntu Netbook 10.10 on my NP-N130.  Warning: I'm no expert with Ubuntu, linux networking or wifi hardware, I just frigged around until things worked:

- install of ubuntu on the device worked without incident
- wifi seemed to work, but would not establish a connection to my local router (kept re-showing the login screen)
- when I rebooted the wireless adapter was gone, including from iwconfig

Here's what I did, hope this helps:

1) downloaded the appropriate Win7/32bit driver from Samsung (Realtek 8192e), unzipped the driver bundle in by Downloads folder
2) Launched Ubuntu Software Centre tile, installed "Windows Wireless Drivers" (Ndiswrapper driver installation tool)
3) Launched the Applications tile, selected System, then clicked "Windows Wireless Drivers" app
4) installed the appropriate driver (pick RTL819xP_Driver/Win7X86/net819xp.inf).  It is obvious in the app if the driver install succeeded.

Now... things still didn't work.  When I opened a terminal, sudo'd and did an lswh -C network, I saw the driver listed, but it said *-network UNASSIGNED beside the entry.

Next:

5) did a 
modprobe -l | grep rtl 
(to find realtek-looking entries).  Found one, and did 
modprobe r8192e_pci

It found the wireless, scanned, and allowed me to connect to my wireless.  Then I tested suspend and resume (closed the lid then reopened after it had shut down), and a hard restart.  In both cases the wireless adapter was gone.  

So, I added the following script as /etc/pm/sleep.d/99_fixnetwork

#!/bin/sh

case "$1" in 
             thaw)
            # I actually tried it once without the next line, and it didn't work, after I added it it worked
             modprobe -r r8192e_pci
             modprobe r8192e_pci
             ;;
case "$1" in
             resume)
             modprobe -r r8192e_pci
             modprobe r8192e_pci
             ;;
esac

This fixed things for suspend-and-resume, did not check hibernate but will likely fix that too.  No idea why I need to remove and add the module again each time, but it works.

I also added a file in /etc/init.d/customwireless

#!/bin/sh -e

COMMAND=$1
case $COMMAND in
start)
   modprobe -r r8192e_pci
   modprobe r8192e_pci
   ;;
esac

And linked it in rc3.d:

cd /etc/rc3.d
ln -s ../init.d/customwireless S89customwireless

and tested a restart, and wireless automatically connects now.

Yes, I should refactor the repeated modprobe scripts to a common file someplace, and probably will, but I've spent enough time on this for now, and have a working ubuntu netbook (waaaay faster than the stock Win7 Starter that it came with, and worth the investment in frigging around with the drivers).

Hope this helps someone else.

---

### Post by Shake 'n' Bake on 2011-02-11
I had this problem again after a fresh install of 10.10.  None of what was mentioned previously worked, so I did some googling, and found this:

[http://www.greenhughes.com/content/installing-ubuntu-1010-samsung-nb30-touchscreen-netbook](http://www.greenhughes.com/content/installing-ubuntu-1010-samsung-nb30-touchscreen-netbook)

Turns out the NB30 and the NB-130 have the same wireless hardware, so it works just great.  Just keep in mind if you use this, you need to update the samsung-wireless package each time you install a new kernel.

---

### Post by meopoka on 2011-03-10
i love it  Samsung NP-N130 - no wifi

---

### Post by dave92F1 on 2011-03-23
I used the [http://www.greenhughes.com/content/i...screen-netbook](http://www.greenhughes.com/content/i...screen-netbook) fix; it worked great for me (Samsung NB130 on 10.10) until about a week ago.  

After I installed some routine Ubuntu updates, my WiFi stopped working altogether.

I got it back to the original semi-working state (works until you hibernate, but after that no WiFi till you reboot), by uninstalling the fix:

  sudo apt-get remove samsung-wireless

Then comment out the 2 added lines in /etc/modprobe.ds/blacklist.conf that were added in the original fix.

Anybody have an idea how to make it work again after hibernation??

Cheers,

--Dave

---

### Post by duck.asteroid on 2011-06-04
> **helliewm said:**
> To compile the Realtek driver. I am using Karmic Netbook Remix UNR

Download driver from here [URL="http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz"]http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz
 [/URL]
[http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz](http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz)
 
On Netbook Remix it should download into your Download folder. Go to your Download folder and Extract the file. Click on it, it will open then click Extract.

Open the Terminal and Change Directory to Extracted file by typing this into the Terminal 

cd Downloads/rtl819Xe

Next in the Terminal type

sudo su

./install.sh

Ignore any error messages it will say kernel mismatched 5 times.

Your wifi driver on the N130 should now work. The above was adapted from this thread  [http://ubuntuforums.org/showthread.php?t=1329254&page=2]("http://ubuntuforums.org/showthread.php?t=1329254&page=2")  

Hope this helps. It worked first time on my N130.

Helen
I have been having WiFi problems on my Samsung N130 using Ubuntu 11.04 (Natty). I followed the instructions posted by helliewm (post #14 from Dec 2009) and the WiFi seems much better. Will post back with an update after a week or two.

---

### Post by iclestu on 2011-06-05
:(

I followed the above instructions and got this error
```

Building kernel module...
make: *** /lib/modules/2.6.38-8-generic/build: No such file or directory. Stop.
Copying firmware...
Installing module and rebuilding dependencies...
install: cannot stat `r8192_pci.ko': No such file or directory
Removing r8192e_pci and  r8192se_pci...
ERROR: Module r8192_pci does not exist in /proc/modules
ERROR: Module r8192e_pci does not exist in /proc/modules
ERROR: Module r8192se_pci does not exist in /proc/modules
Loading module...
FATAL: Module r8192_pci not found.
..ready

```

Now, after a reboot I cannot get any wireless at all. Im using kubuntu and it just doesnt show. I dont think any wireless driver is loaded at all because

```
lshw -C network
```

gives:

```
  *-network [COLOR=Red]**UNCLAIMED  **[/COLOR]   
       description: Network controller
       product: RTL8192E Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:54:56:8f:d0
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:f0520000-f053ffff

```

can anyone help me?

---

### Post by iclestu on 2011-06-06
hmm, after MUCH mucking about I managed to get back to way it was before by purging then reinstalling the latest kernel (im sure thats not the recommended way!).

that script seemed to get stuck because there was no build directory in /lib/modules/<kernel version>/ but having looked now there still isnt so I dare not run the script again. Can anyone offer any suggestions. I could, of course, just make a build directory in there but surely it cant be that simple!!!?

---

### Post by Drjim on 2011-09-18
I have a Samsung n130 and have been disappointed that I could not get it to recognize my wireless card. Works fine in Windows and the ethernet cable connection works fine just like everyone else. I don't have a lot of skill (next to none) using terminal codes or mucking about with the programming and am afraid or really screwing something up after reading your post.

I've downloaded several updates including the latest 11.04 natty norwhal in hopes newer drivers would solve my problem but no luck. I look forward to a real, safe solution. It WAS good to hear that the belkin wifi stick works so at least I could use that as a solution albiet an unsatiafactory one. 

Has anyone else used a usb modem/wireless device of this type with good compatibility?

Thanks,

Jim

---

### Post by Shake 'n' Bake on 2011-09-18
This solution has worked for me flawlessly since 10.10.  Be warned you may have to re-do this when you install a new kernel, but I haven't had to for some time.

ubuntuforums.org/showthread.php?p=10487458#post10487458

If you need any additional help, don't hesitate to ask.

---

### Post by maul9999 on 2011-10-02
> **unplugme said:**
> Hello

I have the new Samsung NP-N130 with the Realtek wireless card - b/g/n and I cannot get it to work. Someone told me about ndiswrapper but i'm not sure how to set something like this up. Anyone care to help?

I am able to get wired ethernet working, so I do have internet access to download any files I may need. I also have a computer with Mac OS X / Windows XP if I need to use either.

I have some linux command line knowledge, but detailed instructions would be great!

I know about Realtek.  It might not be support.  Unless you have CD driver with wireless driver.  First you will need to look inside wireless folder for file like ".inf"  If it do have, your wifi support.  If not, your wireless is not support by ubuntu.  To inside .inf, you will need get NDSI.  (I'm not sure if i remember.) then use .inf as your wireless installing.  Then you should be done.

---

### Post by cleggton on 2011-10-19
A workaround that I have found to work is to add the PPA ppa:voria/ppa and install the samsung-wireless package. The wireless seems much better and still works after hibernation and suspend.

---

### Post by Drjim on 2011-10-19
> **cleggton said:**
> A workaround that I have found to work is to add the PPA ppa:voria/ppa and install the samsung-wireless package. The wireless seems much better and still works after hibernation and suspend.

Thanks, I appreciate your tip! I'm a bit of a beginner. Can you please tell me:
1. What is a PPA and how do I add it?
2. Where do I get the samsung-wireless package and how do I install it? Is it just something I can get through the Ubuntu software center?

Thanks again,

Jim

---

