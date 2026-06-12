---
title: "Ubuntu 11.10 Oneiric Ocelot!"
date: 2011-10-13
forum: System76 Support
---

### Post by isantop on 2011-10-13
Today is the big day, and the team at Canonical have got another new Ubuntu release out the door! They all deserve a big round of applause!

System76 customers are clear to upgrade to the new release. For users performing a fresh installation, you're free to download the CD image and upgrade as soon as you're ready. 

If you want to perform an online upgrade to 11.10, then, as always, we recommend you wait a week or two to let the load on the servers cool down. When the servers are heavily loaded, the chances of completing an upgrade successfully drop, and that can mean data loss!

Nevertheless, we'd recommend backing up data just in case. It's always better to be safe.

Full upgrade instructions are available at [this knowledge base article](http://knowledge76.com/index.php/OneiricUpgrade).

---

### Post by jxn on 2011-10-13
I gave it a try on my Serval Pro w/ SSD, and do-release-upgrade failed hard with an exception, choking on something in /etc/fstab, it looks like.  I have not changed the install, fstab configuration, or added/replaced any drives, so this should be set as it was at factory....just a warning/(and request for ideas to get past the problem) from a s76 user who had to cancel the upgrade process...


here's the exception:
```

Calculating the changes

Calculating the changes


A fatal error occurred 

Please report this as a bug and include the files 
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in 
your report. The upgrade has aborted. 
Your original sources.list was saved in 
/etc/apt/sources.list.distUpgrade. 

Traceback (most recent call last): 

File "/tmp/update-manager-ziDSBy/oneiric", line 7, in <module> 
sys.exit(main()) 

File "/tmp/update-manager-ziDSBy/DistUpgradeMain.py", line 199, in 
main 
if app.run(): 

File "/tmp/update-manager-ziDSBy/DistUpgradeController.py", line 
1670, in run 
return self.fullUpgrade() 

File "/tmp/update-manager-ziDSBy/DistUpgradeController.py", line 
1627, in fullUpgrade 
if not self.askDistUpgrade(): 

File "/tmp/update-manager-ziDSBy/DistUpgradeController.py", line 895, 
in askDistUpgrade 
if not self._checkFreeSpace(): 

File "/tmp/update-manager-ziDSBy/DistUpgradeController.py", line 861, 
in _checkFreeSpace 
with_snapshots = self._is_apt_btrfs_snapshot_supported() 

File "/tmp/update-manager-ziDSBy/DistUpgradeController.py", line 
1005, in _is_apt_btrfs_snapshot_supported 
apt_btrfs = apt_btrfs_snapshot.AptBtrfsSnapshot() 

File "/tmp/update-manager-ziDSBy/apt_btrfs_snapshot.py", line 85, in 
__init__ 
self.fstab = Fstab(fstab) 

File "/tmp/update-manager-ziDSBy/apt_btrfs_snapshot.py", line 53, in 
__init__ 
entry = FstabEntry.from_line(line) 

File "/tmp/update-manager-ziDSBy/apt_btrfs_snapshot.py", line 31, in 
from_line 
return FstabEntry(*line.split()) 

TypeError: __init__() takes at most 7 arguments (9 given) 
=== Command detached from window (Thu Oct 13 10:37:27 2011) ===
=== Command terminated with exit status 1 (Thu Oct 13 10:37:27 2011) ===

```

Also, I'm not completely sure that I reverted the upgrade process entirely.  I simply ran vi search/replace in /etc/apt/sources.list, replacing oneiric where-ever I found it.  Anything else I should have done?

---

### Post by isantop on 2011-10-13
That should be fine to revert the change.

In the future, you should wait a week or so before attempting to upgrade to a new release. If you want to upgrade on release day, we recommend doing a fresh-install.

---

### Post by zoso375 on 2011-10-13
My upgrade seemed to go well, but I can't boot into Oneiric. Boot hangs on "Stopping System V runlevel compability".

If I Alt-F6 into a command prompt and attempt to log in, here's what I get: 

```
libindicate-ERROR **: Unable to get session bus: Command line 'dbus-launch --autolaunch=78bf8294bb46d639695a66e500000009 --binary-syntax --close-stderr" exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n
```

Not sure where to go from here.

---

### Post by vanhenryjr on 2011-10-13
You are all much braver than I am-upgrading right at distribution. I am just thrilled that I got my first program (kindle reader for PC) to work via wine!

---

### Post by cheesekiller on 2011-10-13
Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'


and now it does this everytime i open update manager.....   so would an upgrade by cd work better?  i want to upgrade BUT I DONT WANT A FRESH INSTALL....  because i currently have too much to backup......

also when i upgrade will my update manager be fixed from saying that everytime i open her?

---

### Post by Kacey on 2011-10-13
With the release having just started today its never a good idea to do a online upgrade, DVD would always be the better option. 

Also as System76 has stated - 

"If you want to perform an online upgrade to 11.10, then, as always, we recommend you wait a week or two to let the load on the servers cool down. When the servers are heavily loaded, the chances of completing an upgrade successfully drop, and that can mean data loss!"

 This isn't just a good warning its a law to live by with all Ubuntu releases.

Oh try 'apt-get clean' and see if that will clear the error.

---

### Post by regixmfn on 2011-10-13
I'm glad I hopped right into the beta. >.<

---

### Post by cheesekiller on 2011-10-13
i finally got upgraded, it failed to upgrade like 5 times  and a fresh instal took forever and then FROZE at installing system at the end when i rebooted it booted into ubuntu but when i go to install the system76 driver it says that i need a cd-rom and i installed off a flash stick does this mean that i NEED to make a cd-rom or wtf?

I'm currently installing my nvidia driver the old fashioned way and hoping everything goes fine...    I probably messed up somewhere and the 5 failed attempts and 3 hours of waiting has caused me to delete multiple bad words in this post

if i install fresh again................................................................     i swear im unplugging the internet because the what feels like an hour of "downloading packages"....   I love Ubuntu but the installer this time around.................

---

### Post by amphoterous on 2011-10-13
I'm getting the same error as CheeseKiller. The ```
sudo apt-get clean
``` didn't help. I guess that is what I get for trying to upgrade right away. Next time I'll read the forums first. :neutral:

---

### Post by cheesekiller on 2011-10-13
i used to cd to try to "force upgrade"   ask cheese how google chrome won't install..............  go ahead ask him...................................................

is there a way to bring back my launcher button......  and the old way of top left reveal?      11.04's controls for opening and even revealing the launcher worked good this just gets annoying

---

### Post by Kacey on 2011-10-13
I did it with a CD but I always burn a copy of the CD to archive it in case I am in need of a new install. So that said I have no idea about the USB install issues. 

I also had issues with installing chrome. 

I downloaded it and clicked the .deb to load with the software center, This failed. At this point I ran the following command.

```
sudo dpkg -i chrome.deb
``` 

I still had issues doing this so I then ran 
```
sudo apt-get install -f
```

After that I re-ran 

```
sudo dpkg -i chrome.deb
``` 


Chrome works find now.

---

### Post by cheesekiller on 2011-10-13
why can't we do it in the software center?

---

### Post by cheesekiller on 2011-10-13
Selecting previously deselected package google-chrome-stable.
(Reading database ... 129800 files and directories currently installed.)
Unpacking google-chrome-stable (from google-chrome-stable_current_amd64.deb) ...
dpkg: dependency problems prevent configuration of google-chrome-stable:
 google-chrome-stable depends on libnspr4-0d (>= 4.7.3-0ubuntu1~); however:
  Package libnspr4-0d is not installed.
 google-chrome-stable depends on libxss1; however:
  Package libxss1 is not installed.
 google-chrome-stable depends on libcurl3; however:
  Package libcurl3 is not installed.
dpkg: error processing google-chrome-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Errors were encountered while processing:
 google-chrome-stable

when running the first command

I ran the rest of your commands and it installed fine.   I have found out that I can install any .deb by doing it from the term but when i use the software center i get the same error. also the system76 driver won't install it asks for the cd..... any ideas?

---

### Post by Kacey on 2011-10-14
After doing more digging there are major problems with doing a DVD upgrade. 

I am going to be doing a complete install.

I had to manually install nvidia again, synaptik for the trackpad, I also needed to delete my .pulse folder in my home dir to get sound back, the list goes on and on.

---

### Post by Tart on 2011-10-14
Hey All,

After fresh install of 11.10, I downloaded and installed system76 driver.
I'm not able to start it however. It asks for a password and then disappears. If I do it in terminal I get the following message.

```
(system76-driver:5130): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(system76-driver:5130): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(system76-driver:5130): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(system76-driver:5130): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Traceback (most recent call last):
  File "/usr/bin/system76-driver", line 50, in <module>
    main()
  File "/usr/bin/system76-driver", line 44, in main
    os.environ['GDMSESSION'] == 'default'
  File "/usr/lib/python2.7/UserDict.py", line 23, in __getitem__
    raise KeyError(key)
KeyError: 'GDMSESSION'

```

I'm on Lemur UltraThin. 

Ilya

---

### Post by mpwoodward on 2011-10-15
Same for me, also on Lemur. Going to upgrade my Serval this weekend as well!

---

### Post by gman16000 on 2011-10-15
I just bought a Gazelle a month ago and went for the 11.10 upgrade the day it came out. I've been using Ubuntu for 5+ years and I always take chances and go for the latest software. I'll share my experience in case it helps someone out.

**_Bad Experience_**
[LIST]
[*]Used Update Manager to perform the upgrade
[*]Took 5 hours to download (heavy server load--duh)
[*]After reboot, I lost almost everything. Wireless, ethernet, touchpad, usb mouse.
[*]Updated System76 driver to Oct 12 version and did a restore system.
[*]A cold reboot left me without video. Nvidia would try to load and xserver would fail.
[*]I needed my computer for the next morning work so I "upgraded" from 11.10 to 11.04 using a normal boot CD.
[/LIST]

**_Good Experience_**
After thinking about it a bit I tried a different approach the next night.
[LIST]
[*]Created a 11.10 live CD and booted fresh with it
[*]Noticed that everything worked (wireless, touchpad, usb ports, sound, lcd brightness)
[*]Rebooted to existing 11.04 and uninstalled the system76 driver package.
[*]Rebooted with live 11.10 CD and did an upgrade "11.04 to 11.10"
[*]Almost thought it hung when it was removing old packages...gave it about 15 minutes and the install completed successfully (patience payed off)
[*]System rebooted and everything appears to be working fine. Wireless, VPN, Ethernet, Bluetooth, USB2/3.0 ports, touchpad, sound, sound keys, lcd brightness keys
[*] Even Chrome Browser (google-chrome-stable and google-chrome-beta) each worked for me with no issues.
[/LIST]

I don't know all the things the System76 driver does but I do not think that I'm going to try installing it again since everything for me is working. While I can uninstall the deb package, it seems like the "restore" option runs a script that makes file level changes to the system that I'm not sure how to back out of. 

I've been playing with Gnome Shell 3 non stop and installing shell extensions and the cool factor of running kernel 3.0.0-12 has been worth it.

Hopefully this helps somebody. System76 is awesome laptop and really works well with linux.  Happy hunting.

---

### Post by Kacey on 2011-10-15
Have you tried dual monitors? 

That is the last real issue that I am having at the moment.

---

### Post by howlofdawn on 2011-10-15
I did a DVD upgrade to start off. Downloading the iso took about 5 hours so no difference there. 
Ran the installation and decided to upgrade to keep files 11.04 to 11.10. Seemed to take longer than it needed to once it rebooted though quite a few things weren't working. 
On the upside, my files were still there. but the programs wouldn't run although it seemed to go online without a problem and no display issues. Other than programs closing and opening but not showing a GUI.
Next sensible thing, a clean install using the same DVD. Everything worked and as it didn't try to restore my programs and all, didn't take too long. 
No programs have closed, restored my files from a backup and the programs are reading them.
All devices seem to work, save for the Bison webcam, its detected and it runs with programs but there seems to be an uneven ratio of red to blue and green.
Nvidia is working fine on Pangolin although I ran the sys76 driver just to check if anything was missing and got a this:
[http://1dl.us/qf4.png](http://1dl.us/qf4.png)
Still messing around with Oneiric. happy upgrading

---

### Post by gman16000 on 2011-10-16
> **Kacey said:**
> Have you tried dual monitors? 

That is the last real issue that I am having at the moment.

I haven't yet. I will be doing that first thing Monday morning when I get into work via HDMI port.

---

### Post by sderrick on 2011-10-16
> **Kacey said:**
> Have you tried dual monitors? 

That is the last real issue that I am having at the moment.

I also must have dual monitor support.  I have a NVidia card and the NVidia XServer application works OK enabling dual monitor though it does put the dash on the left monitor which I don't especially like. I've heard this will be fixed in 12.4.  

I usually use an application called disper tied to a keyboard shortcut to enable dual monitors, disper -e -t left, but that is failing. I may just need to change the parameters to get it to work but haven't had the time to play with it. 

Scott

---

### Post by sderrick on 2011-10-16
Fingerprint reader not working correctly.

I upgraded through the software update app.  From 10.10, to 11.4 then to 11.10, in quick succession(1 day).  I stayed with 10.10 until 11.10 came out as 11.4 just seemed to raw to me. 

Now the fingerprint reader doesn't come up at all for GUI sudo sign ins.  It does come up when I do sudo in a terminal and it does work but i get the following err.

```

(process:12093): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
QGtkStyle was unable to detect the current GTK+ theme.

```

---

### Post by cheesekiller on 2011-10-16
> **sderrick said:**
> Fingerprint reader not working correctly.

I upgraded through the software update app.  From 10.10, to 11.4 then to 11.10, in quick succession(1 day).  I stayed with 10.10 until 11.10 came out as 11.4 just seemed to raw to me. 


you missed out cause 11.04 seemed better then 11.10, mainly because of features that were left out in gnome 3..... gawd i hope theres a default menu editor in 12.04

---

### Post by Flyers2391 on 2011-10-16
> **howlofdawn said:**
> I did a DVD upgrade to start off. Downloading the iso took about 5 hours so no difference there...

You should use the torrent link.  It will be less demand on the servers, a much faster download and you can leave transmission (or whatever you use) open for a while to "give back" to others doing the same thing.  

[http://www.ubuntu.com/download/ubuntu/alternative-download#bt](http://www.ubuntu.com/download/ubuntu/alternative-download#bt)

---

### Post by cheesekiller on 2011-10-17
ok when i try to desktop record while playing minecraft now it just laggs.....  before (11.04) i could take perfect video but now its like my video card is being raped.....

---

### Post by mahermali on 2011-10-17
Hi all
I've updated with lot of problems I have the Serp7

I lost the wireless connection

```
dmesg | grep iwl
[   20.580303] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   20.580306] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   20.580408] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   20.580439] iwlagn 0000:04:00.0: setting latency timer to 64
[   20.580515] iwlagn 0000:04:00.0: Detected Intel(R) Centrino(R) Advanced-N 6230 AGN, REV=0xB0
[   20.596426] iwlagn 0000:04:00.0: device EEPROM VER=0x716, CALIB=0x6
[   20.596430] iwlagn 0000:04:00.0: Device SKU: 0Xb
[   20.596432] iwlagn 0000:04:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   20.597484] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   20.597616] iwlagn 0000:04:00.0: irq 51 for MSI/MSI-X
[   20.685636] iwlagn 0000:04:00.0: loaded firmware version 17.168.5.1 build 33993
[   20.687984] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   22.215823] iwlagn 0000:04:00.0: Error sending REPLY_TX_LINK_QUALITY_CMD: time out after 500ms

```and the command
```
dmesg | grep wlan0
[   22.220235] ADDRCONF(NETDEV_UP): wlan0: link is not read
```I can switch the wireless card on and off using the keyboard keys but I can't connect to any network

and the output of other commands:
```
uname -a
Linux TAO76 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
``````
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 88:53:2e:19:4c:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```I've tried everything available online but no success.

Also I've noticed another problem after upgrading: the webcam when used the LED is not turned on (very weird!!)

For the strange problems happened regarding the desktop: [http://ubuntuforums.org/showthread.php?t=1862625](http://ubuntuforums.org/showthread.php?t=1862625)

I hope if there is someone here to help with the wireless.

Thanks

---

### Post by anewnham on 2011-10-17
I upgraded via update manager. It failed a few times saying the internet connection went down and when it finally worked I rebooted, got to the login screen no problems, logged in and it then tells me it's connected to my wireless network and that's it... I can see unity on the left and my folders on the desktop, the wireless notification doesn't dissappear and I'm unable to click on anything. Alt+tab, ctrl+alt+delete all do nothing and I'm stuck!

Any help?

---

### Post by mahermali on 2011-10-17
I got a solution for Ubuntu Wireless card on Serval7 after upgrading to 11.10

I just made the connection open and the connection is established there must be a problem with WPA module I'll investigate the problem and let you know.

---

### Post by mahermali on 2011-10-17
The problem is with wpa_supplicant the wireless manager can't communicate with the wpa_supplicant.

I've used wpa_gui: the program didn't recognize any wireless card
I've tries sudo wpa_gui and I was able to configure the wireless card and establish the connection but the probelm I can't save the configuration because the update_conf should be 1

I'll try to see what's happening apparently the problem is that: services are not given root access when running from the desktop like: software-center and synaptic and network-manager

it doesn't even ask for root password.

---

### Post by mahermali on 2011-10-17
I was able to solve this strange problem

run

sudo wpa_gui

in the system settings --> network --> wireless
you can find the wireless network but if it is using WPA or WEP you won'tbe able to connect what I did:

choosing the wireless network (NetworkA)
It will appear in wpa_gui
then write down the PSK (or any other configuration) --> connect then the status will be changed to connect in the network manager.

---

### Post by taixuanjunzi on 2011-10-21
%I must inform you your ([wow gold](http://www.bestwowgolds.com)) substance will be very identified. That offers myself fresh tips along with it really is ([cheap diablo 3 gold](http://www.cheapdiablo3golds.com)) composed together with ease as opposed to people intricate kinds We have examine. Many thanks to your substance, may([diablo 3 gold](http://www.cheapdiablo3store.com)) My partner and i nonetheless notice people in the foreseeable future!

---

### Post by chownoir on 2011-10-28
Hi,

I have the Starling 5 and only for a few months. Is it now safe to update to 11.10 and not worry about the wifi? I've been traveling and unwilling to deal with any potential problems since I need connectivity on the road. I've held off on updating anything for a few weeks now. 

I'm pretty inexperienced with Ubuntu. Thanks!

---

### Post by mahermali on 2011-10-29
No avoid the pain
even when I try to install the System76 drivers it gives me message: drivers are provided by ubuntu

The webcam led doesn't work
The wireless problem should be solved as I said in this thread by installing wicd
the fingerprint --> I think it will never work

Stick to 11.04 is the best option

---

### Post by sderrick on 2011-10-29
> **chownoir said:**
> Hi,

I have the Starling 5 and only for a few months. Is it now safe to update to 11.10 and not worry about the wifi? I've been traveling and unwilling to deal with any potential problems since I need connectivity on the road. I've held off on updating anything for a few weeks now. 

I'm pretty inexperienced with Ubuntu. Thanks!

I experienced so many "known bugs", with no known fix after I upgraded to 11.10 I switched to Linux Mint. After 6+ yeas of Ubuntu and being a vocal Ubuntu fan boy I have left the fold. I think Canonical has really let us down in the quality of product.

---

### Post by spideryada on 2011-11-01
First tried to upgrade 11.10 from 11.04 on my Meerkat Ion -> disaster; Did a fresh install -> Totally unusable; Reinstalled 11.04 -> rescued; Good that I have /home on a separate partition.

Then tried to install it on my Star1. There I have two partitions that can be alternated for installing different distros. Fresh install -> disaster; After many failed attempts to get it to boot to 11.04 as default, I achieved success using "Boot Repair Disc" using the advanced option to remove the 11.10 Grub2 and reinstalling the 11.04 Grub2.

I hope this can be of use to anyone that has made the mistake of installing 11.10.

I do have to mention that some friends have upgraded with no problems.

---

### Post by chownoir on 2011-11-02
Thanks! Appreciate the help. I won't upgrade then. I'll just stick with the regular updates. I really don't need to do much except for being able to do word processing, spreadsheets and web surfing. As long as I can do all that and no problems with wifi, I'm happy.

---

### Post by bro brian on 2011-11-03
> **sderrick said:**
> I experienced so many "known bugs", with no known fix after I upgraded to 11.10 I switched to Linux Mint. After 6+ yeas of Ubuntu and being a vocal Ubuntu fan boy I have left the fold. I think Canonical has really let us down in the quality of product.
I agree! Not so much about the 'bugs', but with the Unity completely. It's like Ubuntu has reversed direction, and has taken a step backwards. Unity is harder to navigate than Gnome (at least harder than Gnome2 - Don't know much about Gnome3). I hope that Ubuntu re-thinks this thing with Unity before the next LTS comes out. Unity SUCKS, and no support for Compiz SUCKS! They are definitely loosing users at this very moment. System76, it may do you well to make note of this.
***Having stated the above, it is possible to revert to either the Gnome shell or Lubuntu desktop (which is what I've done while playing with 11.10 in Virtualbox) by typing in Konsole: sudo apt-get install lubuntu-desktop . The end result gives me different desktop environments to choose from. You can see how this is done by doing a search on Youtube for the video (by LinuxSpatry) named, "Install LXDE over Ubuntu 11.10". I'm sure there are other varying methods to accomplish similar alternatives. By the time the next LTS comes out, I want to have researched my options as much as I can.

---

### Post by isantop on 2011-11-03
What is it specifically you find difficult to navigate? They're designed with very different usage schemes in mind, but once you adapt to Unity's, it is actually very fast, and far faster than Gnome 2. 

As for Compiz support, Unity (3D, which is supported on most System76 computers) is implemented as a Compiz plugin, so Compiz support is required for Unity. There are a few plugins that don't work with it, but these have all got replacement funtionality built into Unity.

---

### Post by bro brian on 2011-11-03
> **isantop said:**
> What is it specifically you find difficult to navigate? They're designed with very different usage schemes in mind, but once you adapt to Unity's, it is actually very fast, and far faster than Gnome 2. 

As for Compiz support, Unity (3D, which is supported on most System76 computers) is implemented as a Compiz plugin, so Compiz support is required for Unity. There are a few plugins that don't work with it, but these have all got replacement functionality built into Unity.
So what you're saying is that Compiz Config works with Unity? I've heard to the contrary, but haven't tried the Compiz Config out as of yet. I can say that I would rather have the "Ubuntu Software Center" still listed. All I can see is a box to type in (whatever application I'm looking for). I would rather see a list of applications. Believe me when I say that it's not just me that feels this way. You can simply read the forums - or check out some of the Linux channels ("This Week in Linux", "The Linux Action Show", etc.). I'm not the only one questioning the Unity interface.
*** I guess the Ubuntu Software Center is still included. It took me a while to find it, but I did. I guess what (I am) saying is that the layout is difficult for me. It's different. I suppose with time, I would get used to it, but right now I feel like a 'fish out of water' trying to get around this new (and so-called improved) shell. Many people are being scared away by this. I don't know (shaking my head). Hmmm
**** Probably the main 'beef' with Unity is that many just aren't comfortable with the layout, or simply don't like the way their desktop environment looks in Unity, period. They feel like Canonical is trying to stick everyone into a neat, little box. They don't like the big, ugly looking boxes on the left side of the screen, or that it doesn't resemble the older Gnome layout at all. There are many who love the KDE layout - others hate it. I learned Linux on a Mandriva os with a KDE desktop environment. It took me a little while getting used to the Gnome DE, but I eventually adapted to it, and even liked it more than KDE. I understand this. Linux users don't like being 'told' what they're going to use, and what they're not going to use. If this were the case, half the Linux users would still be using Windows. They find what they like the best, and usually stick with it if it works for them, and if it works, don't fix it. Many ex-Ubuntu users have gone to either Mint or Pinguy with the thought that Ubuntu should've been doing what they're doing all along. These are my thoughts on this. Many won't agree with my thinking on this, and that's ok. I'm not trying to persuade anyone into my wave of thought, but this is important to me, and I'm expressing just how I feel about it.

---

### Post by isantop on 2011-11-04
Yes; in fact, you can control several options with Unity through the settings in the Unity Plugin.

Unity is pretty heavily keyboard driven, which is different from Gnome 2. To open the Dash, you can click on the Ubuntu Icon, but it is much faster to hit the super key (Windows key on most keyboards, or Ubuntu key on keyboards from System76). At this point, the fastest way to open an application is to type the name. You'll usually only need to type the first few characters until it's the first result listed, then hit enter to open it. 

If you prefer to simply browse a list of installed applications, the fastest way to do this is to hit Ubuntu+A. This will open up the Dash to the "Applications Lens" that will automatically list applications. Click on "Installed" to view all of your applications. You can also browse them by category by clicking on the "Filter Results" option, then click on the category you want to browse.

One of the best things about the dash is it isn't limited to listing applications. By default, it will list music in your Banshee library, recently accessed files, and Applications, and it can be expanded to include even more results by installing additional Scopes (Results providers) and Lenses (lists of results).

---

### Post by Eyore15 on 2011-11-06
I upgraded my Star1 to 11.10 today; I've had nothing but trouble ever since.

The cursor keeps "hanging up" on me.  When it is visible on the screen, it won't move.  Half the time it isn't even visible.

I started with Skype; as soon as the program opened the cursor quit.  The only way to do anything is to turn the power off; you can't do any kind of a re-start; can't get to a terminal to kill the Skye process.

The third time I figured out enough of the new system to uninstall Skype [thought that might be the problem].  You guessed it, another hang-up.  I let the computer sit for 10 minutes before I did the hard re-boot.  When it came back up, Skype was gone.  I went to Firefox to go to a favorite site, and it locked up again.

The 4th time [I'm a glutton for punishment] I re-installed Skype to see if I could get it to work -- installed OK, but hung up again when I tried to use it.

This time I left it turned off and am using the computer as a paper weight.

Anyone got any idea of what I can do to fix this problem?  I'd like to at least try 11.10.

---

### Post by bro brian on 2011-11-07
Have you tried doing all the updates yet? Everything seems to work on my Pangolin laptop - even with 11.10 loaded in Virtualbox (minus Comiz/wobbly windows, etc.).
** I know this sounds too easy, but there is the possibility (IF you are using a plug-in mouse) that you simply need to re-seat it - unplug it, and plug it back in again. lol...I wonder...

---

### Post by Eyore15 on 2011-11-07
> **bro brian said:**
> Have you tried doing all the updates yet? Everything seems to work on my Pangolin laptop - even with 11.10 loaded in Virtualbox (minus Comiz/wobbly windows, etc.).
** I know this sounds too easy, but there is the possibility (IF you are using a plug-in mouse) that you simply need to re-seat it - unplug it, and plug it back in again. lol...I wonder...

I can't get to the updates because the cursor (I use the mouse pad) keeps hanging up.

---

### Post by bro brian on 2011-11-08
> **Eyore15 said:**
> I can't get to the updates because the cursor (I use the mouse pad) keeps hanging up.
Hmmm... I wonder what would happen if you just plugged a real mouse (with USB plugin) in the laptop. You may have some sort of mousepad driver issue going on?

---

### Post by ubuntu27 on 2011-11-08
> **Eyore15 said:**
> I** upgraded** my Star1 to 11.10 today; I've had nothing but trouble ever since.

The cursor keeps "hanging up" on me.  When it is visible on the screen, it won't move.  Half the time it isn't even visible.

....

Did you upgrade or Clean install?

Try to do a Clean Install.

---

### Post by bro brian on 2011-11-08
> **ubuntu27 said:**
> Did you upgrade or Clean install?

Try to do a Clean Install.
.... And if you're installing it on a 76 laptop, don't forget to install the 76 drivers.

---

### Post by ubuntu27 on 2011-11-10
> **Eyore15 said:**
> I upgraded my Star1 to 11.10 today; I've had nothing but trouble ever since.
....

> **ubuntu27 said:**
> Did you upgrade or Clean install?

Try to do a Clean Install.

> **bro brian said:**
> .... And if you're installing it on a 76 laptop, don't forget to install the 76 drivers.


Eyore. After you are done doing a clean install *install the OS--Ubuntu on top of your current installed system), install the System76 driver (if you bought their computer :KS ).

You can install the System76 driver by following their instruction:

[Restoring Your System76 Computer ]("http://knowledge76.com/index.php/Restoring_Your_System"), go to **"Install the System76 Driver**"

---

### Post by bro brian on 2011-11-23
Alright... I take back everything I said in previous posts relating to Ubuntu's new, sucky look. I recently saw several Youtube videos on the newest Microsoft os, Windows 8. Now I'm starting to get the picture. My thought is that Ubuntu has made some drastic decisions, and changes to their newer os's in order to keep up with the times. Ubuntu isn't the only one who has done this. I've recently seen a video on the new Mandriva os (2011), which is following a similar look to Ubuntu as well. 
 I don't know about anyone else, but after seeing what they've done with the new Windows os, I'm pretty glad I switched to Linux operating systems years ago. I imagine that far more Windows users are screaming as well. LOL!!! The new Ubuntu look & feel is nothing compared to the new Windows look. I think that I can get used to it, for sure.

---

### Post by isantop on 2011-11-23
The industry is simply following user demands. For better or worse, products like the iPad and iPhone have fundamentally changed the consumer's perspective on computing. It made them realize that computers, even simple tablet computers, could be simpler and easier to operate. Unity is actually quite a powerful environment, once you get used to it, and it provides a simple interface for new users, and a powerful one for experienced users.

---

### Post by jdb on 2011-11-23
> **bro brian said:**
> 
 I don't know about anyone else, but after seeing what they've done with the new Windows os, I'm pretty glad I switched to Linux operating systems years ago.

I agree, but what's even better, with Linux you have a choice.
I don't much like Unity, but I love Xubuntu with xfce4.

jdb

---

### Post by bro brian on 2011-11-24
> **jdb said:**
> I agree, but what's even better, with Linux you have a choice.
I don't much like Unity, but I love Xubuntu with xfce4.

jdb
Absolutely! Windows users won't have a choice. Microsoft is going with the same os for both the touchpads & desktops. Ubuntu has several choices including Xubuntu.
PS. Happy Thanksgiving to all! I have an 11-1/2 pound ham in the oven, and I'm watching the Thanksgiving Day parade that's going on in New York right now. When the ham is finished baking, I'll be taking it to the folks house in Colorado Springs where they will have a turkey ready as well, and all the fixin's. I'm extremely thankful to be a Linux user, and to be part of this forum with all of it's participants. I'm also thankful that we don't bake penguins on Thanksgiving!

---

### Post by benhill70 on 2011-11-29
Finally, updated my Bonobo laptop, no problems so far.

---

### Post by bro brian on 2011-12-04
> **jdb said:**
> I agree, but what's even better, with Linux you have a choice.
I don't much like Unity, but I love Xubuntu with xfce4.

jdb
I am seriously looking at the Xubuntu when the next LTS comes out. I also have some optimism that the system76 driver may install on this os. I've been checking out a few videos related to the Xubuntu 11.10.
[http://www.youtube.com/watch?v=hmvXVIDzmEs&feature=colike](http://www.youtube.com/watch?v=hmvXVIDzmEs&feature=colike)

** I just figured out that I can change the desktop environment in Ubuntu by simply installing LXDE or XFCE (or both) from the Synaptic Package Manager. Then, I simply log into whatever desktop environment I wish. Best of all worlds, eh?

---

### Post by douglasbrooksjr on 2012-01-13
[URL="http://ubuntuforums.org/member.php?u=1311971"][QUOTE=All devices seem to work, save for the Bison webcam, its detected and it  runs with programs but there seems to be an uneven ratio of red to blue  and green.]

[/QUOTE][/URL]

[howlofdawn]("http://ubuntuforums.org/member.php?u=1311971")

Did you find a solution to this issue?  I'm having the same problem.

---

