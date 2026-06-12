---
title: "HOWTO: Topfield PVR and Ubuntu"
date: 2006-11-26
forum: Tutorials
---

### Post by belgrave on 2006-11-26
This mini howto deals with getting your [Topfield PVR]("http://www.Topfield.co.uk/") working with Ubuntu. 

If you want to ask general questions or discuss things, please use the [Topfield For Ubuntu/Unix forum]("http://www.deepnerd.com/forum/53").

Currently, there are a few hard working people developing some pretty good software for the Topfield and *nix; primarily [Puppy]("http://www.nslu2-Linux.org/wiki/Puppy/HomePage") (a command line tool that started its life as/is an application to turn a [Netgear Slug]("http://en.wikipedia.org/wiki/NSLU2") running the [SLUG OS]("http://www.nslu2-Linux.org/") into a network access point for the Topfield) and [Guppy]("http://guppy.nongnu.org/index.html") - a GUI for Puppy. If you know of other *nix apps or other aspects of using Ubuntu and your Topfield, please post and I'll include them. Also, if you've had success on other systems/kernels/versions etc, let me know and I'll include the info. If anyone wants to help in maintaining this, please do! There will probably always be items in the Todo list for this guide. This howto was developed after discussions on [another Ubuntu forum thread]("http://ubuntuforums.org/showthread.php?t=294411") and because there is no concise info out there (at the time of writing) for getting your Topfield to play nice with Ubuntu.

This howto is not meant to hold your hand. I am assuming that you know a few things about Ubuntu and your Topfield before you start. BUT! I am expecting this to grow over time. Please feel free to ask questions, and if the answers clear up anything, I will expand the howto to include them. The only thing I ask is that you read *all* of the following before asking questions and you ensure that all of the listed dependencies are installed.


*Assumptions*
The following assumes that you:[LIST]
[*] know how to get to a command line and (generally) use it
[*] know your way around your Topfield's menus, configuration etc
[*] can install applications/packages either on the command line or through Synaptic[/LIST]
*Tested on*
The following has been tested/created using:[LIST]
[*] Ubuntu Edgy Eft ( 2.6.17-10-generic SMP i686)
[*] Gnome v2.16.1
[*] Puppy v1.11
[*] Guppy v1.0.1RC1
[*] Topfield TF5800PVR (UK version)[/LIST]
*Dependencies*
The following requires that these packages are installed (additional to a standard Ubuntu install - I have probably missed some):[LIST]
[*] usbutils
[*] gdebi (not required, but handy)
[*] Python 2.2 (gdebi should take care of this for you)
[*] PyGtk 2.6 (gdebi should take care of this for you)[/LIST]

*General help*
From, 15/12/2007, all testing, detail and logs behind this howto are hosted at [http://www.deepnerd.com/]("http://www.deepnerd.com/topics/52/Topfield") - this is to provide detail for those who want it without clogging this howto for those who just want to get things working. If you run into trouble, want more info etc, try these:[LIST]
[*] [toppy.org.uk]("http://toppy.org.uk"): The place for help, applications, news, TAPs, firmware, and anything else related with the Topfield (UK based, but covers other models as well).
[*] [Converted RPM's debs and hacks]("http://www.kauhajoki.fi/%7Epeti/puppy-deb/"): Packages created from the official Fedora RPMs and work arounds by [forum contributor x-na]("http://ubuntuforums.org/member.php?u=79656") during [this discussion]("http://ubuntuforums.org/showthread.php?t=294411"). If you run into trouble, these might be worth a try.
[*] [Topfield Live CD]("http://ozi4ums.homedns.org/downloads/dsl/DSLTopfield.htm"): If all else fails, and you just want to get it working, this Live CD gives you ftp access to your topfield out of the box. Download the image, burn it and boot from it without needing to touch your installed OS.[/LIST]

*Todo...*[LIST]
[*] Getting [ftpd_Topfield]("http://www.nslu2-Linux.org/wiki/Puppy/FtpdTopfield") working. This is an FTP server that hooks onto the USB port the Topfield is attached to allowing you to copy files using a normal FTP client. Does not work out of the box on the latest Edgy Eft.[/LIST] *Credits*
Most of this has come from my experience, but has also been built through info submitted by the Ubuntu community, correspondence with Tony Tsui (the author of Guppy) and from the [Puppy]("http://www.nslu2-Linux.org/wiki/Puppy/HomePage") & [Guppy]("http://guppy.nongnu.org/index.html") home pages.




**[SIZE=4]Howto setup file transfer to/from your Topfield PVR[/SIZE]**
If you want to be able to transfer files to/from your Topfield with a nice GUI....[LIST=1]
[*]_Preparation_: Make sure your Topfield is turned on and connected to your PC using a USB cable. It might be best during the initial setup to make sure you have no TAPs running; just to make sure nothing is interacting strangely. To do this, hold down the "0" key on your Topfield remote while it boots until you see it switching between screen ratios (this just stops any TAP from loading during boot).
[*]_Topfield connection_: On the command line, run ```
lsusb | grep -i Topfield
``` You should get something like ```
Bus 005 Device 002: ID 11db:1000 Topfield Co., Ltd. PVR
``` If not, you could try ```
lsusb
``` to see all the USB devices connected to your system - your Topfield may be announcing itself strangely. If you can't see your Topfield connected, there isn't much need to continue. Try the standard things first (disconnect/reconnect the USB cable, reboot the toppy etc), then start digging further into your USB subsystem.
[*]_Puppy install_: Download the latest version of the Puppy Deb from [here]("http://download.savannah.gnu.org/releases/guppy/") and install it.
 *note - [COLOR="DarkRed"]Ubuntu  >= 7.10[/COLOR] users (Gutsy Gibbon): please see [this post below]("http://ubuntuforums.org/showpost.php?p=3580402&postcount=20") for info on getting USB into a normal state for use with Puppy.*
[*]_Puppy testing_: With your Topfield turned on/plugged in and visible to your system, run ```
sudo puppy -c dir
``` If all went well, you should see the top level directory of your Topfield's hard drive, something like:
```

d                    0 Wed Jan  1 00:00:00 2003 DataFiles
d                    0 Wed Jan  1 00:00:00 2003 ProgramFiles

```
[*]_Guppy install_: Download the latest version of the Guppy Deb from [here]("http://download.savannah.gnu.org/releases/guppy/") and install it.
 *note: Support for Edgy Eft (and newer) was added in v1.0.1RC1.* 
 *note #2 - [COLOR="DarkRed"]Ubuntu  >= 7.04[/COLOR] users (>= Feisty Fawn): please see [this post below]("http://ubuntuforums.org/showthread.php?p=2716955&posted=1#post2716955") for info on working around the new version of python.*
[*]_Guppy testing_: Run ```
sudo guppy
``` This can take a little bit to load (you may get an empty window), especially if you have a lot of files on your Topfield - Guppy builds a cache of everything on your Topfield when it boots. If you eventually get the Guppy main window with detail of space remaining and you can see the files in the root directory of your Topfield, you're all done - you can now start transferring files!
[*]_Getting it working for normal users_:
Add a new file named "40-tf5000pvr.rules" to the directory "/etc/udev/rules.d". Into this file add following line:

```

SYSFS{idVendor}=="11db", SYSFS{idProduct}=="1000",      MODE="0660", GROUP="video"

```

Next time you plug your Topfield you will be able to run guppy as non-root user. (taa alex_k!)

[*]_Menu item_: To add a menu item (in Gnome), right click your system menu and select "Edit Menus". Pick the category you want the item to appear in (I use "Sound & Video") and click "New Item" on the right. In the pop-up, enter a name and a description. Under "command" enter [FONT=Courier New]gksudo guppy[/FONT]. Download the [Guppy icon]("http://guppy.nongnu.org/images/guppy_logo.png") used on the [Guppy home page]("http://guppy.nongnu.org/index.html") and save it somewhere. Click the "No Icon" button, find the image you just downloaded and select it. Click OK and you're done![/LIST]



**[SIZE=4]Howto view .rec files transferred from your Topfield[/SIZE]**
[VideoLan]("http://www.videolan.org/") plays .rec files (the Topfield's native recording format) out of the box. Make sure you have the universe and multiverse repositories enabled and install [FONT=Courier New]vlc[/FONT]. you will then have "VLC media player" available under "Sound & Video" in your main menu.



**[SIZE=4]Howto manually upgrade firmware[/SIZE]**
[COLOR="DarkRed"]Before you go any further[/COLOR]: upgrading the firware on any piece of hardware, let alone your (expensive) Toppy has the ability to brick (i.e. render it not working forever) whatever it is you are upgrading. We are not responsible if you damage anything.[LIST]
[*] grab the HDFW tap from: [http://www.toppy.org.uk/downloads/info.php?tid=261](http://www.toppy.org.uk/downloads/info.php?tid=261) and install it using Guppy. **read the instructions that come with it**
[*] grab the latest firmware from somewhere like [http://www.toppy.org.uk/downloads/firmware.php](http://www.toppy.org.uk/downloads/firmware.php) and copy it to the topfield
[*] run HDFW on the Topfield
[/LIST]

---

### Post by desperado666 on 2007-03-27
Very nice article. congratulations :)

I wrote this topfield 4000 article (german) here
[http://wiki.ubuntuusers.de/Topfield](http://wiki.ubuntuusers.de/Topfield)

Do you know how to get write privilegies for TF 4000 ?

---

### Post by belgrave on 2007-03-28
Can't help directly on the TF4000 sorry as I don't have access to the hardware and the [google translate version]("http://translate.google.com/translate?u=http%3A%2F%2Fwiki.ubuntuusers.de%2FTopfield&langpair=de%7Cen&hl=en&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools") of your post does not do it justice (sorry, don't speak german either :( ), but it does give the general flow.

When you have the FAT24 file system mounted, can you write to it as root? Try
```

sudo su -
cd /media/topf
touch test
```

if so, then you'll need to muck around with the options ([FONT="Courier New"]-o[/FONT]) part of the mount command or the permissions on the mount point.

---

### Post by desperado666 on 2007-03-28
kann &#8222;test&#8220; nicht berühren: Read-only file system
means : no write privilegies.

yesterday i could finally reach read/write privilegies with the tool TFDISK from here

[http://www.glasstetter.net/dvbcut/](http://www.glasstetter.net/dvbcut/)

Are you informed about plans to support fat24 system for future versions of linux kernel?

---

### Post by Alex_K on 2007-04-11
**Running Guppy as non-root user:**

Ubuntu does not use hotplug, so you can't use the hotplug scripts from the Guppy homepage.
You have to use udev:

Add a new file named "40-tf5000pvr.rules" to the directory "/etc/udev/rules.d". Into this file add following line:

```

SYSFS{idVendor}=="11db", SYSFS{idProduct}=="1000",      MODE="0660", GROUP="video"

```

Next time you plug your Topfield you will be able to run guppy as non-root user.

---

### Post by belgrave on 2007-04-20
sweeeet.. thanks alex_k... folded into the howto

many kudos for you

---

### Post by walding on 2007-05-23
Hi,

I get as far as the guppy testing, and get the following error...

sudo guppy
Traceback (most recent call last):
  File "/usr/bin/guppy", line 82, in <module>
    from guppy import GuppyWindow
ImportError: No module named guppy


Can anyone help?

I use Kubuntu 7.04.
I have tried this with guppy 1.01all, RC1 & RC2.

AW

---

### Post by belgrave on 2007-05-25
> **walding said:**
> 
sudo guppy
Traceback (most recent call last):
  File "/usr/bin/guppy", line 82, in <module>
    from guppy import GuppyWindow
ImportError: No module named guppy


hmmm.... I do remember dealing with this error a while ago, but for the life of me cannot remember how I got it fixed. I have a nagging suspicion it was related to paths. You'll be wanting to use at least RC1, but I would be using RC2 (newer is (nearly) always better).  

I haven't tested guppy under Feisty (my lounge pc is still running edgy), but have just done a clean install of puppy 1.11 & guppy 1.0.1RC2 and replicated the error you got. Puppy is working fine.
 
After a bit of digging, it seems that Feisty is using Python 2.5 but the deb's of Guppy are expecting python 2.4. I tried doing something like:
```
 sudo ln -s /usr/lib/python2.4/site-packages/guppy/ /usr/lib/python2.5/site-packages/guppy
```
But this just threw up a whole new world of pain with python version conflicts etc. I eventually got it working by changing the first line in ```
/usr/bin/guppy
``` from:
```
#!/usr/bin/python
```
to
```
#!/usr/bin/python2.4
```

/usr/bin/python is a symlink to the latest python interpreter installed. by chaning the line above, you have just told the system to use the older version of the python interpreter when running Guppy.

can you test and feedback? I don't have my Toppy connected to this PC, so I can only test so far.

---

### Post by walding on 2007-06-16
HI,

Sorry for delay (hols).  This works better in that the GUI loads up.  However, there is no connection evident.  grep command shows that the PVR is connected properly etc.  It works under Windows (Altair).  So there is something in 7.04 stopping it working that wasn't the case in 6.10.

I can't test anything else at the moment as Feisty is broken completely today!

AW

---

### Post by belgrave on 2007-06-16
Are you running guppy as root? try:

```
sudo guppy
```

any luck?

is puppy working (check the main howto)? If it isn't, then the problems are lower level than the GUI; if it is, then guppy is definitely to blame

---

### Post by walding on 2007-06-16
Hi,

Well, it works after a clean install (for other reasons) and following the above instructions.  I guess I'll never really know what the source of the problem was!

Thanks for your help,

AW

---

### Post by stfu on 2007-06-19
Thanks belgrave for your tips on how to get guppy working.

---

### Post by grunta on 2007-09-07
In Australia the guys here have made a "Live cd" using DSL to connect to 
our 5000xxx pvrt

[http://www.topfield-australia.com.au/phpbb2/viewtopic.php?t=9218&highlight=live]("http://www.topfield-australia.com.au/phpbb2/viewtopic.php?t=9218&highlight=live")


I think they have posted it at **Tapworld**

here's a link anyway, while not using Ubuntu, their work may help you or give you some ideas, the best thing about this project was its simple and non invasive

[http://ozi4ums.homedns.org/downloads/dsl/DSLTopfield.htm]("http://ozi4ums.homedns.org/downloads/dsl/DSLTopfield.htm")

---

### Post by belgrave on 2007-09-08
that's great! good work to the devs on that one, should make the toppy more accessible to everyone, especially new linux users.

Make sure you let the people over at [toppy.org.uk]("http://toppy.org.uk") know about this - I'm sure they'll give you some exposure on it. I've added this into the general help section of the howto as I'm sure there are some people out there who don't want to get their hands dirty on a command line and just want to mess around with their PVR.

---

### Post by bekowsquap on 2007-10-05
I've just upgraded to Gutsy and have found that puppy (and unsurprisingly) guppy no longer work. I'm getting the following error from puppy when running 
```
sudo puppy -c dir
ERROR: Can not perform autodetection.
ERROR: /proc/bus/usb/devices can not be open for reading.
ERROR: No such file or directory

```

I can see the Topfield listed in the USB devices.

Has anyone else tried this in Gutsy?

I'll freely admit to being a noob.

---

### Post by belgrave on 2007-10-06
hmmmm..... not gone to Gutsy yet, waiting for the official launch etc.

Looks like things may have changed in USB handling..... 

But, flying blind, from behind the bleeding edge, some ideas:
[LIST]
[*] what does: *[FONT="Courier New"]sudo ls -la /proc/bus[/FONT] *show?
[*] anything else in /proc that looks like a new home for USB?
[*] *[FONT="Courier New"]lsusb -v[/FONT]* should give you detail on each USB device connected, and where it is connected. Each entry will be headed with something like [FONT="Courier New"]*Bus 001 Device 001: ID 0000:0000*[/FONT] which gives you the (old) location of the device under /proc/bus/usb (using the bus and device numbers)
[*] if you can track down where the USB devices hide in Gutsy, then using puppy like *[FONT="Courier New"]puppy -d /proc/bus/usb/001/003[/FONT] *should help 
[/LIST]

post whatever you can find and we'll help out if we can.

---

### Post by bekowsquap on 2007-10-08
> **belgrave said:**
> hmmmm..... not gone to Gutsy yet, waiting for the official launch etc.

Looks like things may have changed in USB handling..... 

But, flying blind, from behind the bleeding edge, some ideas:
[LIST]
[*] what does: *[FONT="Courier New"]sudo ls -la /proc/bus[/FONT] *show?
```
dr-xr-xr-x   5 root root 0 2007-10-08 18:40 .
dr-xr-xr-x 115 root root 0 2007-10-08 18:39 ..
dr-xr-xr-x   2 root root 0 2007-10-08 19:51 input
dr-xr-xr-x   4 root root 0 2007-10-08 18:40 pci
dr-xr-xr-x   2 root root 0 2007-10-08 19:51 usb

```


> **belgrave said:**
> [*] anything else in /proc that looks like a new home for USB?

Not sure on this, this is an ls output
```
1     28    4816  5     5697  5777  asound       ioports     stat
152   3     4829  5128  5699  5805  buddyinfo    irq         swaps
175   3808  4843  5265  5707  5829  bus          kallsyms    sys
176   3825  4844  5350  5710  5839  cmdline      kcore       sysrq-trigger
177   4     4863  5351  5711  6     cpuinfo      key-users   sysvipc
2     4426  4864  5365  5718  7     crypto       kmsg        timer_list
2022  4427  4905  5387  5720  9359  devices      loadavg     timer_stats
2023  4430  4906  5397  5723  9371  diskstats    locks       tty
2136  4432  4907  5398  5728  9375  dma          meminfo     uptime
229   4433  4908  5404  5729  9391  driver       misc        version
2364  4434  4909  5437  5737  9396  execdomains  modules     version_signature
2365  4607  4912  5451  5742  9397  fb           mounts      vmcore
2371  4637  4962  5570  5751  9655  filesystems  mtrr        vmstat
2584  4717  4965  5649  5752  9656  fs           net         zoneinfo
26    4777  4968  5652  5754  9658  ide          partitions
27    4779  4988  5691  5756  9719  interrupts   scsi
2789  4800  4989  5693  5758  acpi  iomem        self

```

> **belgrave said:**
> [*] *[FONT="Courier New"]lsusb -v[/FONT]* should give you detail on each USB device connected, and where it is connected. Each entry will be headed with something like [FONT="Courier New"]*Bus 001 Device 001: ID 0000:0000*[/FONT] which gives you the (old) location of the device under /proc/bus/usb (using the bus and device numbers)

```
Bus 003 Device 005: ID 11db:1000 Topfield Co., Ltd. PVR
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x11db Topfield Co., Ltd.
  idProduct          0x1000 PVR
  bcdDevice            1.01
  iManufacturer           1 Topfield Co., Ltd.
  iProduct                2 Topfield (http://www.topfield.co.kr)
  iSerial                 3 1000
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

```

> **belgrave said:**
> [*] if you can track down where the USB devices hide in Gutsy, then using puppy like *[FONT="Courier New"]puppy -d /proc/bus/usb/001/003[/FONT] *should help 
[/LIST]

post whatever you can find and we'll help out if we can.

/proc/bus/usb is empty. I'm not really sure where else to look.

Thanks for your help so far.

---

### Post by belgrave on 2007-10-08
still flying blind on this one, but some more things to try and hunt down what gutsy does with USB devices:

[LIST]
[*] [FONT="Fixedsys"]*ls -la /*[/FONT]
[*] [FONT="Fixedsys"]*ls -la /proc/bus/*/*[/FONT]
[*] unplug the topfield, [FONT="Fixedsys"]*sudo "tail -f /var/log/udev"*[/FONT] then plug in the topfield
[*] unplug the topfield, [FONT="Fixedsys"]*sudo "tail -f /var/log/messages"*[/FONT] then plug in the topfield
[*] [FONT="Courier New"]*fdisk -l*[/FONT]
[/LIST]

any Gutsy users out there? know what it is doing with USB devices?

---

### Post by bekowsquap on 2007-10-18
Thought I'd wait until the official release

> **belgrave said:**
> 
[LIST]
[*] [FONT="Fixedsys"]*ls -la /proc/bus/*/*[/FONT]
```

dr-xr-xr-x 2 root root 0 2007-10-18 22:45 .
dr-xr-xr-x 5 root root 0 2007-10-18 22:30 ..
-r--r--r-- 1 root root 0 2007-10-18 22:45 devices
-r--r--r-- 1 root root 0 2007-10-18 22:45 handlers

/proc/bus/pci/:
total 0
dr-xr-xr-x 4 root root 0 2007-10-18 22:30 .
dr-xr-xr-x 5 root root 0 2007-10-18 22:30 ..
dr-xr-xr-x 2 root root 0 2007-10-18 22:45 00
dr-xr-xr-x 2 root root 0 2007-10-18 22:30 02
-r--r--r-- 1 root root 0 2007-10-18 22:45 devices

/proc/bus/usb/:
total 0
dr-xr-xr-x 2 root root 0 2007-10-18 22:45 .
dr-xr-xr-x 5 root root 0 2007-10-18 22:30 ..

```

> **belgrave said:**
> [*] unplug the topfield, [FONT="Fixedsys"]*sudo "tail -f /var/log/udev"*[/FONT] then plug in the topfield

Nothing useful

> **belgrave said:**
> 
[*] unplug the topfield, [FONT="Fixedsys"]*sudo "tail -f /var/log/messages"*[/FONT] then plug in the topfield


```
Oct 18 22:39:31 Cassy kernel: [  566.654859] usb 3-1: USB disconnect, address 2
Oct 18 22:39:31 Cassy kernel: [  566.654865] usb 3-1.1: USB disconnect, address 4
```

Plugging back in gives the following

```
Oct 18 22:39:31 Cassy kernel: [  566.654859] usb 3-1: USB disconnect, address 2
Oct 18 22:39:31 Cassy kernel: [  566.654865] usb 3-1.1: USB disconnect, address 4
Oct 18 22:45:55 Cassy kernel: [  950.138518] usb 3-1: new high speed USB device using ehci_hcd and address 5
Oct 18 22:45:55 Cassy kernel: [  950.272261] usb 3-1: configuration #1 chosen from 1 choice
Oct 18 22:45:55 Cassy kernel: [  950.272568] hub 3-1:1.0: USB hub found
Oct 18 22:45:55 Cassy kernel: [  950.272899] hub 3-1:1.0: 4 ports detected
Oct 18 22:45:55 Cassy kernel: [  950.578583] usb 3-1.1: new high speed USB device using ehci_hcd and address 6
Oct 18 22:45:55 Cassy kernel: [  950.672229] usb 3-1.1: configuration #1 chosen from 1 choice

```

---

### Post by dougaus on 2007-10-20
Thanks to everyone for all the hints in this thread about getting puppy and guppy to work.

I just found how out the other thing to do to get puppy and guppy going under Gutsy Gibbon, besides the edit to use python2.4 here:

[https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/151585]("https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/151585")

i.e. you need to uncomment the following lines in 

/etc/init.d/mountdevsubfs.sh

mkdir -p /dev/bus/usb/.usbfs
    domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount --rbind /dev/bus/usb /proc/bus/usb

then do a restart: sudo /etc/init.d/mountdevsubfs.sh start

This is my first post in the Ubuntu Forums, so please let me know if there are any issues with this post.

---

### Post by bekowsquap on 2007-10-21
Excellent. All working now.

Many thanks Dougaus.

---

### Post by belgrave on 2007-11-02
thanks heaps for the feedback - I've been waiting for the servers to calm down before upgrading. Will update the howto for Gutsy as soon as I can test it out myself. Thanks to all posters for the help and problem diags (current install is happening on a 64 bit system being logged here: [http://www.deepnerd.com/node/73](http://www.deepnerd.com/node/73))

Will most likely log the debug on Gutsy for the Toppy  at [http://www.deepnerd.com/plogs](http://www.deepnerd.com/plogs) as well.

---

### Post by belgrave on 2007-12-15
it has been nearly 2 months, but the howto has been updated to get your Toppy working with the latest Ubuntu Release (7.10 - Gutsy Gibbon) - many apologies for the delay and kudos to dougaus for finding the solution.

USB probs were confirmed, logged and documented [URL="http://www.deepnerd.com/gutsy-topfield"]
here[/URL].

Also rolled in detail on how to upgrade firmware without windows/over the air upgrade.

Further detail and testing behind the howto (so as not to clog it up with irrelevant detail) can be found here: [http://www.deepnerd.com/topics/52/Topfield]("http://www.deepnerd.com/topics/52/Topfield")

---

### Post by machare on 2007-12-16
I have Gusty Gibbon and a slug.  Using Mozilla Firefox I can see the files on my TF5800.

I have found that VLC running under Gusty will play .rec files already stored on my PC much better than when running under Vista.

So I wondered whether I could use VLC to directly play files on the PVR.

Using 'Places', 'Connect to server' I can see the slug as an FTP folder.  When I open this folder I see  '1970  firmware',  '2003  DataFiles',  '2003 ProgramFiles', '2003 MP30'.  I don't know where the 1970 and 2003 come from.   If I try and open the Datafiles folder I get the message 'The folder contents could not be displayed.'

Why do I get these strange names?
Is there a way that I can open the folders?
Or is there any other way that I can directly play files on the PVR using VLC?

---

### Post by belgrave on 2007-12-16
Hi Machare,

gonna have to ask a few questions here as I'm flying blind; don't have a Slug to test this on, but I can make a few (un)educated guesses.

I'm assuming here that when you say:

> **machare said:**
> Using 'Places', 'Connect to server' I can see the slug as an FTP folder.

This is the 'Places' menu item under Gnome....

When I get a directory listing of the Toppy, I get something like this:
```

d                    0 Wed Jan  1 00:00:00 2003 DataFiles
d                    0 Wed Jan  1 00:00:00 2003 ProgramFiles
```

I'm thinking the strange directories you are seeing ('2003 DataFiles') are because of a problem with either Gnome or the way the Slug is presenting the directory listing to Gnome - instead of showing "ProgramFiles", it's also giving the year part of the modification date.

Try this: Once connected via 'Places > Connect To Server'. instead of clicking the directory, try adding 'ProgramFiles' manually at the end of the location bar (you may need a trailing slash - if you can't see the location bar, click the button on the left that looks like a pen&paper).

With any luck, this should let you browse into directories on the Toppy. As for VLC..... what you get in Nautilus (the Gnome file browser), may not be available to other applications like VLC.

From a quick bit of research, it looks like the Slug supports NFS mounts - with this, you should be able to mount your Topfield onto a directory on your local computer. This will allow applications like VLC to use files on the Toppy as if they were local files on your PC. Have a search on Google for "NFS slug" - but the following looks promising (from the NSLU2 home page):

[http://www.nslu2-linux.org/wiki/Optware/Nfs-utils](http://www.nslu2-linux.org/wiki/Optware/Nfs-utils)

let us know how you get on, I'd be interested to see if the Toppy could be mounted on the local file system (think: mythtv + toppy)

---

### Post by machare on 2007-12-18
> **belgrave said:**
> This is the 'Places' menu item under Gnome....

When I get a directory listing of the Toppy, I get something like this:
```

d                    0 Wed Jan  1 00:00:00 2003 DataFiles
d                    0 Wed Jan  1 00:00:00 2003 ProgramFiles
```

I'm thinking the strange directories you are seeing ('2003 DataFiles') are because of a problem with either Gnome or the way the Slug is presenting the directory listing to Gnome - instead of showing "ProgramFiles", it's also giving the year part of the modification date.

You are right it was a problem with the ftpd-topfiled software that runs in the slug and makes the files in the PVR appear as if on an FTP server. I have found a later version of this software where this bug has been corrected.

> **belgrave said:**
> Try this: Once connected via 'Places > Connect To Server'. instead of clicking the directory, try adding 'ProgramFiles' manually at the end of the location bar (you may need a trailing slash - if you can't see the location bar, click the button on the left that looks like a pen&paper).

That idea did work, unfortunately the file names were also preceded by 2007

> **belgrave said:**
> With any luck, this should let you browse into directories on the Toppy. As for VLC..... what you get in Nautilus (the Gnome file browser), may not be available to other applications like VLC. 
If I open the text editor I can drill down the directories and select a file on the PVR.  VLC however does not find the ftp server icon on the desktop. i.e. it is not listed under 'File, quick open file'. Further if open the ftp server icon on the desktop, drill sound the directories to a '.rec' file and use 'open with' VLC it still does not work!  

> **belgrave said:**
> From a quick bit of research, it looks like the Slug supports NFS mounts - with this, you should be able to mount your Topfield onto a directory on your local computer. This will allow applications like VLC to use files on the Toppy as if they were local files on your PC. Have a search on Google for "NFS slug" - but the following looks promising (from the NSLU2 home page):
[http://www.nslu2-linux.org/wiki/Optware/Nfs-utils](http://www.nslu2-linux.org/wiki/Optware/Nfs-utils)

let us know how you get on, I'd be interested to see if the Toppy could be mounted on the local file system (think: mythtv + toppy)

I am not sure if ftpd-topfiled would be compatible with nfs. I will try the [www.toppy.org.uk](www.toppy.org.uk) forum as I can not be the first person to have encountered this problem.  Thanks for your help.

---

### Post by belgrave on 2007-12-18
> **machare said:**
> I am not sure if ftpd-topfiled would be compatible with nfs. I will try the [www.toppy.org.uk](www.toppy.org.uk) forum as I can not be the first person to have encountered this problem.  Thanks for your help.

glad to have helped, and please let us know how you get on with VLC&the slug.

Something else that may help is mounting the toppy using an ftp filesystem:

[http://ubuntuforums.org/showthread.php?t=117827](http://ubuntuforums.org/showthread.php?t=117827)

once mounted, this will present the topfild as a normal directory on your local filesystem, letting apps like VLC that don't have nautilus integration to get to it.

---

### Post by belgrave on 2007-12-18
We have decided to split this a little bit. Based on recent requests, there seems to be a need for a general forum to discuss things relating to Ubuntu and the Topfield.

As such, we have established a general Topfield Ubuntu (and linux/unix) forum at:

[http://www.deepnerd.com/forum/53](http://www.deepnerd.com/forum/53)

Please use this if you need general help or have questions relating to the above. We will try and keep this howto focussed on getting Ubuntu and the Toppy to play nice, just so things don't get too cluttered here.

---

### Post by machare on 2007-12-18
> **belgrave said:**
> glad to have helped, and please let us know how you get on with VLC&the slug.

I have found that I can get VLC to play files on the PVR by using the 'Open Network Stream' option, selecting FTP and entering a URL that points to a file on the PVR.  It actually works quite well.

I have also found that this method works on Vista, and is better than using the Windows Explorer FTP facility to display the files on the PVR and then clicking on them so that VLC starts. 

> **belgrave said:**
> Something else that may help is mounting the toppy using an ftp filesystem:
[http://ubuntuforums.org/showthread.php?t=117827](http://ubuntuforums.org/showthread.php?t=117827)

once mounted, this will present the topfild as a normal directory on your local filesystem, letting apps like VLC that don't have nautilus integration to get to it.

Interesting, I might try that sometime.

---

### Post by Fraser67 on 2008-04-08
I have been trying to complie a version of Puppy that does not use the CRC checking. Hence I can't use the packages that have been produced and need to got to basics.

I had one problem that seemed to be cured by commenting out the #include <linux/usb.h> in usb_io.h and forcing it to use #include "usb_ch9.h" instead. It appeared to make ok.

However it complains when I try and intsall. See below

root@home1:/usr/src/puppy_1.11# make
cc -std=gnu99 -Wall -W -Wshadow -Wstrict-prototypes -pedantic -fexpensive-optimizations -fomit-frame-pointer -frename-registers -O2   -c -o puppy.o puppy.c
cc -std=gnu99 -Wall -W -Wshadow -Wstrict-prototypes -pedantic -fexpensive-optimizations -fomit-frame-pointer -frename-registers -O2   -c -o crc16.o crc16.c
cc -std=gnu99 -Wall -W -Wshadow -Wstrict-prototypes -pedantic -fexpensive-optimizations -fomit-frame-pointer -frename-registers -O2   -c -o mjd.o mjd.c
cc -std=gnu99 -Wall -W -Wshadow -Wstrict-prototypes -pedantic -fexpensive-optimizations -fomit-frame-pointer -frename-registers -O2   -c -o tf_bytes.o tf_bytes.c
cc -std=gnu99 -Wall -W -Wshadow -Wstrict-prototypes -pedantic -fexpensive-optimizations -fomit-frame-pointer -frename-registers -O2   -c -o usb_io.o usb_io.c
cc -Wl,-O2  puppy.o crc16.o mjd.o tf_bytes.o usb_io.o   -o puppy

root@home1:/usr/src/puppy_1.11# make install
make: *** No rule to make target `install'. Stop.

Any ideas how to get it to install?

---

### Post by TimoS on 2008-04-22
I've been banging my head against the wall this evening with trying to get my  old laptop running Ubuntu working with Topfield. So far I've managed to compile the puppy, and uncomment the lines mountdevsubfs.sh, but I'm STILL getting one error message when trying to use Puppy

ERROR: Can not open /proc/bus/usb/002/012 for read/write: Permission denied

Now what do I do? I've called my friend a couple of times, but he's not using Ubuntu, so he can't help much (besides, he always tells me to install a proper Linux :))

---

### Post by Fraser67 on 2008-04-23
Have you tried this (it was detailed on the bottom of page 2 of this thread)

[https://bugs.launchpad.net/ubuntu/+s...ox/+bug/151585](https://bugs.launchpad.net/ubuntu/+s...ox/+bug/151585)

i.e. you need to uncomment the following lines in 

/etc/init.d/mountdevsubfs.sh

mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

then do a restart: sudo /etc/init.d/mountdevsubfs.sh start

---

### Post by TimoS on 2008-04-23
Yep, did that already. Still getting that one error message, but I'll double check when I get home

edit: checked and I had done all those

edit 2: well, looks like it was yet another stupid user error. I fixed the thing by typing sudo in front of the command and now it worked. Oh well, on to next challenge

---

### Post by gavinjb on 2008-05-26
Hi,

Try downloading the .deb files from here 

[http://download.savannah.gnu.org/releases/guppy/](http://download.savannah.gnu.org/releases/guppy/)

Last time I tried though if you use the Guppy Gui there was an issue with the version from here which required Python 2.3/2.4 and would not work with 2.5 so you might want to re-compile that from source.

Note: If you find a way of uploading firmware from Ubuntu I would be interested, I might have to try and see if I can connect to my Toppy though VirtualBox.

---

### Post by gavinjb on 2008-06-25
> **Alex_K said:**
> **Running Guppy as non-root user:**
Add a new file named "40-tf5000pvr.rules" to the directory "/etc/udev/rules.d". Into this file add following line:

```

SYSFS{idVendor}=="11db", SYSFS{idProduct}=="1000",      MODE="0660", GROUP="video"

```

Next time you plug your Topfield you will be able to run guppy as non-root user.

Does anyone know what I need to change in this to get it to work with a TF5800, as if I put this in when I try to run Guppy I get a load of errors relating to Puppy and Guppy fails to start.

I know I need to get the info for the device, but not sure how to do that with the Topfield, I know with a HD you just do udevinfo -a -p /block/sdb/sdb1 (assuming your disk is sdb)


Thanks,


Gavin

---

### Post by Esa on 2008-07-18
> **gavinjb said:**
> Does anyone know what I need to change in this to get it to work with a TF5800


Is 

lsusb

telling the numbers? (TF5800 connected and powered on).

---

### Post by Life On Mars on 2008-08-16
> **gavinjb said:**
> 
Note: If you find a way of uploading firmware from Ubuntu I would be interested, I might have to try and see if I can connect to my Toppy though VirtualBox.

You can just use the [HDFW]("http://www.toppy.org.uk/downloads/info.php?tid=261") TAP to update your firmware on your Toppy.

---

### Post by putt1ck on 2008-12-06
Anyone got a how-to for making this work on Intrepid? I've got the usbfs working insofar as I have successfully got a response from puppy using:

sudo puppy -d /dev/bus/usb/007/0<**> -c dir

(having previously added

none /proc/bus/usb usbfs devgid=46,devmode=666 0 0

to fstab)

However, this is not consistent and in particular the device number being used continually changes. Any ideas or this one for (a) resorting to Windows and (b) complaining to the supplier about their lack of support for Linux, given they've supported other minority OS like Vista ;)

Any clues gratefully received.

Chris

---

### Post by hughyb on 2008-12-10
Help!!

this was working and I have successfully got Puppy working fine and it finds the Topfield fine.  However when trying to get guppy to open I get this message in terminal

[B]Traceback (most recent call last):
  File "/usr/bin/guppy", line 82, in <module>
    from guppy import GuppyWindow
  File "/usr/lib/python2.5/site-packages/guppy/GuppyWindow.py", line 36, in <module>
    from about import *
  File "/usr/lib/python2.5/site-packages/guppy/about.py", line 28
SyntaxError: Non-ASCII character '\xc3' in file /usr/lib/python2.5/site-packages/guppy/about.py on line 28, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details
[/B]

Im quite a newbie at this but It was working but it think that was with python 2.4 not 2.5.  

Any ideas?

Hugh

---

### Post by Leechpool on 2009-01-17
I got puppy (and so guppy) and ftpd-topfield working in intrepid (they were fine before upgrade as was) using patched versions of puppy and ftpd-topfield from here

[http://birdman.dynalias.org/R2-D2/]("http://birdman.dynalias.org/R2-D2/")

This made life much easier.

For these to work I have to right click and unmount the topfield because since intrepid my topfield was automatically mounted and an icon of a camera appeared. But if i click on it the window which opens crashes.

Does anyone know how to stop the automount of the topfield - I read somewhere that it is something to do with libgphoto2 but don't want to uninstall it.

Cheers :)

---

### Post by bjmennen on 2009-01-23
> **Leechpool said:**
> Does anyone know how to stop the automount of the topfield - I read somewhere that it is something to do with libgphoto2 but don't want to uninstall it.

Hi Leechpool,

Found this thread while looking for a solution to this exact problem. I managed to work out how to stop this annoying behaviour so for you and any body who finds this thread searching for a solution see below

```
cd /usr/share/hal/fdi/preprobe/10osvendor
sudo nano 20-libgphoto2.fdi
```

Find the entry for Topfield ( Ctrl+W and Type Topfield )

Remove
```

<match key="usb.vendor_id .....
    <match key="usb.product_id .....
    ....
    ....
    </match>
</match>
```

and save the file CTRL+O

From now on the Topfield will not be mounted as a camera and all actual cameras will mount as per normal. Hope this helps.
Reference [http://gphoto.sourceforge.net/doc/manual/permissions-usb.html](http://gphoto.sourceforge.net/doc/manual/permissions-usb.html)

Regards

---

### Post by gavinjb on 2009-02-04
Hi,

Has anyone managed to get Puppy/Guppy to see there Toppy on 8.10 yet!  I have managed to stop mine trying to auto-mount (thanks bjmennen), but when I run Puppy I get the following

```

gavin@dell-desktop:~$ sudo puppy -c dir
ERROR: Can not perform autodetection.
ERROR: /proc/bus/usb/devices can not be open for reading.
ERROR: No such file or directory

```

Thanks,



Gavin,

---

### Post by Leechpool on 2009-02-05
> Hi Leechpool,

Found this thread while looking for a solution to this exact problem. I managed to work out how to stop this annoying behaviour so for you and any body who finds this thread searching for a solution see below

Code:

cd /usr/share/hal/fdi/preprobe/10osvendor
sudo nano 20-libgphoto2.fdi

Find the entry for Topfield ( Ctrl+W and Type Topfield )

Remove
Code:

<match key="usb.vendor_id .....
    <match key="usb.product_id .....
    ....
    ....
    </match>
</match>

and save the file CTRL+O

From now on the Topfield will not be mounted as a camera and all actual cameras will mount as per normal. Hope this helps.
Reference [http://gphoto.sourceforge.net/doc/ma...sions-usb.html](http://gphoto.sourceforge.net/doc/ma...sions-usb.html)

Regards

bjmennen,
Thank you so much- this worked perfectly for me. My Topfield is no longer mounted automatically.....
Cheers
:D

---

### Post by another-birdman on 2009-02-05
> **gavinjb said:**
> Hi,

Has anyone managed to get Puppy/Guppy to see there Toppy on 8.10 yet!  I have managed to stop mine trying to auto-mount (thanks bjmennen), but when I run Puppy I get the following

```

gavin@dell-desktop:~$ sudo puppy -c dir
ERROR: Can not perform autodetection.
ERROR: /proc/bus/usb/devices can not be open for reading.
ERROR: No such file or directory

```

Thanks,



Gavin,
Looks like you need a libusb version.
Have a look at: [http://birdman.dynalias.org/R2-D2/](http://birdman.dynalias.org/R2-D2/)

---

### Post by gavinjb on 2009-02-09
Thanks, but I already have libusb-0.1-4 installed, any other ideas, this worked on 8.04 so my thought is either the upgrade removed a file or it has made a config change which has impacted this.


Gavin,

---

### Post by matt.a on 2009-03-10
Hi Gavin, not sure if you've sorted this already but you need to **update** the *mod to /etc/init.d/devmountdevsubfs.sh*. 

That is, edit: /etc/init.d/devmountdevsubfs.sh

In the "do_start ()" function add the following lines:
[FONT="Lucida Console"]
[INDENT]
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs "" -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb
[/INDENT][/FONT]
then load the changes: sudo /etc/init.d/mountdevsubfs.sh start

***Note** there's now an additional argument to the 'domount' utility, which breaks the mount. 

***If you've already** got this stanza then just add the additional empty arg to domount: 
[FONT="Lucida Console"].../dev/bus/usb/.usbfs **>> "" <<** -obusmode...[/FONT]

It harks back to the [usb bug from 7.10]("https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/151585"). Although /proc/bus/usb is apparently no longer supported.

Hope this helps. It got puppy working for me on 8.10.

---

### Post by gavinjb on 2009-03-13
Thanks matt.a will give this a try, I have been having to run WinXP to transfer to/from my Toppy, so will be nice to not have to re-boot my machine just to achieve this.

---

### Post by bozzy on 2009-03-22
> **matt.a said:**
> Hi Gavin, not sure if you've sorted this already but you need to **update** the *mod to /etc/init.d/devmountdevsubfs.sh*. 

It harks back to the [usb bug from 7.10]("https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/151585"). Although /proc/bus/usb is apparently no longer supported.

Hope this helps. It got puppy working for me on 8.10.

Great post. Did not "get it" first time round, but now working away sweetly.

Thanks - this was truly appreciated!

---

### Post by Cams123 on 2009-05-03
Help would be appreciated using 9.04 but problem apperas to be Pygtk

sudo guppy
Traceback (most recent call last):
  File "/usr/bin/guppy", line 80, in ?
    import gtk
ImportError: No module named gtk

---

### Post by dougaus on 2009-06-02
> **Cams123 said:**
> Help would be appreciated using 9.04 but problem apperas to be Pygtk

sudo guppy
Traceback (most recent call last):
  File "/usr/bin/guppy", line 80, in ?
    import gtk
ImportError: No module named gtk
Cams123,

    I haven't researched this much but I think doing:

sudo apt-get install python-gtk2

should resolve that particular issue.

I did a google for ImportError: No module named gtk and got this page:

[http://roscidus.com/desktop/node/245](http://roscidus.com/desktop/node/245)

which seems to suggest that would be the solution.

It's not a bad idea to paste error messages directly into google search and see what comes up (helps solve many of my problems at home and at work).  From memory, that's how I came up with the solution I posted earlier in the thread.

I'll be plugging in the topfield again some time this year to archive recordings I want from it but I can't say when -- too many other projects now I've switched to mythtv.

Hope that helps.

---

### Post by physwizz on 2009-06-03
> **matt.a said:**
> Hi Gavin, not sure if you've sorted this already but you need to **update** the *mod to /etc/init.d/devmountdevsubfs.sh*. 

That is, edit: /etc/init.d/devmountdevsubfs.sh

In the "do_start ()" function add the following lines:
[FONT=Lucida Console][INDENT]
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs "" -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb
[/INDENT][/FONT]
then load the changes: sudo /etc/init.d/mountdevsubfs.sh start

***Note** there's now an additional argument to the 'domount' utility, which breaks the mount. 

***If you've already** got this stanza then just add the additional empty arg to domount: 
[FONT=Lucida Console].../dev/bus/usb/.usbfs **>> "" <<** -obusmode...[/FONT]

It harks back to the [usb bug from 7.10]("https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/151585"). Although /proc/bus/usb is apparently no longer supported.

Hope this helps. It got puppy working for me on 8.10.

Thanks for this.
I've now got puppy working but sudo guppy gives

Traceback (most recent call last):
  File "/usr/bin/guppy", line 82, in <module>
    from guppy import GuppyWindow
ImportError: No module named guppy

I tried 
sudo apt-get install python-gtk2
with no luck

Any advice?:(

---

### Post by SYC_21 on 2009-06-06
hello
 I have ubuntu 9.04 installed to my laptop and I tried to mount my topfield tf5500 pvr according to your instructions  but when I write 
sudo puppy -c dir 
I get this message

yorgos@yorgos-laptop:~$ sudo puppy -c dir
[sudo] password for yorgos: 
ERROR: Can not perform autodetection.
ERROR: /proc/bus/usb/devices can not be open for reading.
ERROR: No such file or directory
yorgos@yorgos-laptop:~$ 


can someone tell me what to do?

---

### Post by Life On Mars on 2009-06-14
I've just installed puppy and guppy on Ubuntu Jaunty 9.04 following the instructions in this thread and it seems to be working fine. 

For those who haven't been as lucky as me, here's what I did after downloading and installing the puppy .deb, downloading and unpacking guppy and reading the README file:

```

guppy-1.0.2$ sudo make install
guppy-1.0.2$ sudo make DESTDIR=/usr/ install
guppy-1.0.2$ sudo guppy

```

I'm getting some gtk errors, but it does seem to be copying my recordings over without any other problems.

---

### Post by rewire on 2009-07-03
Don't know about guppy, which I haven't tried yet, but getting* ftpd-topfield* up and running fast and flawlessly on 64 bit jaunty 9.04 was a snap with the mods to *mountdevsubfs.sh* detailed in previous posts in this thread.   Highly recommended.

---

### Post by gavinjb on 2009-08-06
Hi,

Just got round to playing and have managed to access my Toppy with puppy again :) but when I try to compile Guppy I get the following, any ideas?

```

sudo make install
python setup.py install --prefix=/usr/local
running install
running build
running build_py
running build_scripts
running install_lib
running install_scripts
changing mode of /usr/local/bin/guppy to 755
running install_data
compiling po/de.po -> locale/de/LC_MESSAGES/guppy.mo
sh: msgfmt: not found
Error while running msgfmt
make: *** [install] Error 1

```

Thanks,



Gavin,

---

### Post by ttsui on 2009-08-16
Hi Gavin,

You need to install the gettext package.

Cheers,
Tony

> **gavinjb said:**
> Hi,

Just got round to playing and have managed to access my Toppy with puppy again :) but when I try to compile Guppy I get the following, any ideas?

```

sudo make install
python setup.py install --prefix=/usr/local
running install
running build
running build_py
running build_scripts
running install_lib
running install_scripts
changing mode of /usr/local/bin/guppy to 755
running install_data
compiling po/de.po -> locale/de/LC_MESSAGES/guppy.mo
sh: msgfmt: not found
Error while running msgfmt
make: *** [install] Error 1

```Thanks,



Gavin,

---

### Post by ttsui on 2009-08-16
Hi,

After a very long time I'm happy to announce a new Guppy release.

Features:

[LIST]
[*] Support transfer with USB accelerator TAP.
[*] Include version of Puppy which enables access to the Toppy without requiring root user file permissions.
(Mark Colclough)
[*] Fix bug where files with multiple spaces fail to download.
[*] Fix bug where transfer Stop/Remove button becomes very thin.
[/LIST]

I'm working on an Ubuntu package but for the moment you can download the source from [URL="http://guppy.ttsui.net/download"]http://guppy.ttsui.net/download
[/URL] 
Also the Guppy website has been revamped and moved to [http://guppy.ttsui.net]("http://guppy.ttsui.net/")

Feedback welcomed on the [guppy]("http://groups.google.com/group/guppy-app") forum.

Tony

---

### Post by mallan157 on 2009-08-24
I had a similar problem - can't revert to Python2.4 as suggested above because it has no gtk module (& couldn't find a suitable library in Synaptic), so decided to run it in Python 2.6 which has gtk support, but 2.6 puts its site-packages folder in /usr/local/lib instead of /usr/lib (which is where it sits for 2.4).

So, I copied the guppy modules folder to the 2.6 location...
$ sudo cp /usr/lib/python2.4/site-packages/guppy /usr/local/lib/python2.6/site-packages

...and created a symlink where the /usr/bin/guppy script expects to find things...
$ cd /usr/lib/python2.6
$ ln -s /usr/local/lib/python2.6/site-packages

This resolved the "not found" messages, but there was an "unexpected encoding" error which seemed to point to an umlaut in an author's name in the site-packages/guppy/about.py module, so I added the following line at the top of the file...

# -*- coding: iso-8859-15 -*-

Guppy now runs from the menu (after changing the rules file as shown at the top of the thread) - there are various attribute error warnings about gtk.Widget objects when starting from a console, but they seem to have no effect.

---

### Post by ttsui on 2009-08-26
Hi,

I'm happy to announce Ubuntu Jaunty packages for Guppy.

You can download them from: [http://guppy.ttsui.net/download](http://guppy.ttsui.net/download)

Tony

---

### Post by Russel_Winder on 2009-09-13
Apologies for wading into this with size 14 boots but . . . 

I am getting the:

[COLOR="Sienna"]|> puppy -c dir
ERROR: Can not perform autodetection.
ERROR: /proc/bus/usb/devices can not be open for reading.
ERROR: No such file or directory[/COLOR]

problem.  However rather than fiddle with all the /dev and /proc stuff, shouldn't the puppy source be fixed to work properly with the current USB infrastructure?

Also shouldn't puppy and guppy get packaged for Debian and hence Ubuntu?

---

### Post by ttsui on 2009-09-13
> **Russel_Winder said:**
> Apologies for wading into this with size 14 boots but . . . 

I am getting the:

[COLOR=Sienna]|> puppy -c dir
ERROR: Can not perform autodetection.
ERROR: /proc/bus/usb/devices can not be open for reading.
ERROR: No such file or directory[/COLOR]

problem.  However rather than fiddle with all the /dev and /proc stuff, shouldn't the puppy source be fixed to work properly with the current USB infrastructure?

The version of puppy shipped with Guppy 1.0.3.1 uses sysfs, so no fiddling with /proc required.

> 
Also shouldn't puppy and guppy get packaged for Debian and hence Ubuntu? I'm not a a Debian developer but I'm willing to support anyone who wants to submit Guppy into the Debian repositories.

Tony

---

### Post by Russel_Winder on 2009-09-13
Tony,

Thanks for responding quickly.  I had pulled the Git repository of guppy and the CVS of puppy on the grounds they would be more up-to-date than any released distribution, but the Ubuntu debs works far better :-)

Have you published the source for guppy-puppy?

---

### Post by Russel_Winder on 2009-09-19
Does anyone know why Ubuntu insists on mounting Toppy as a gphoto2 filestore (I get gphoto2://[usb:001,023])?

Furthermore, it loses the first letter from each of the directories so shows ataFiles, P3 and rogramFiles directories, which of course, can't be opened.

---

### Post by putt1ck on 2009-11-02
@Russell: earlier in the thread there is instruction for deleting the gphoto related entry for Topfield.

@anyone else:

so me, having failed to keep up with this software since I last failed to get my laptop to talk to my Toppy, have just learnt of the lovely integrated deb :), have also just upgraded to 9.10... the deb installs fine, no errors, and both guppy and guppy-puppy run as such.

But I cannot see the contents of the Toppy with either. Running guppy-puppy gets me:

ERROR: Can not set interface zero: Protocol error  

and some fiddling suggests it is trying to talk to the correct USB device (i.e. adding the -d switch and deliberately setting it wrong gets a different error).

Any ideas welcome...

---

### Post by physwizz on 2009-11-28
I was able to get puppy working in Ubuntu 8.10 by editing the /etc/init.d/mountdevsubfs.sh file but not such file exists in 9.10.

Why is it so difficult to access the toppy under linux?

Help!:o

---

### Post by physwizz on 2009-11-30
> **ttsui said:**
> Hi,

I'm happy to announce Ubuntu Jaunty packages for Guppy.

You can download them from: [http://guppy.ttsui.net/download](http://guppy.ttsui.net/download)

Tony

Thank you 
This also seems to work with 9.10 :D

---

### Post by rickbeton on 2010-02-06
> **physwizz said:**
> I was able to get puppy working in Ubuntu 8.10 by editing the /etc/init.d/mountdevsubfs.sh file but not such file exists in 9.10.

Why is it so difficult to access the toppy under linux?

Help!:o

There is a related thread [here]("http://art.ubuntuforums.org/showthread.php?p=8785561").

---

### Post by Russel_Winder on 2010-11-15
After something of an hiatus, I am back on the "our Linux workstation must be able to (up|down)load things to our Toppy".  Topics of interest are:

1.  On connecting the USB to my Maverick machine it mounts the device as Topfield ([http://www.topfield.co.kr](http://www.topfield.co.kr)) which is sort of fine, but it also pops up the dialog asking me if I want to start f-spot, which is less fine but not entirely troublesome as a simple NO gets rid of thhe dialog.  Have I just lost the configuration to stop this happening?

2.  The DataFiles directory looks fine in Nautilus except that it takes an almost infinite amount of time for the icons to switch from the general "time" icon to the 70mm film icon.

3.  Double clicking an icon results in Totem being lauched but after a while thinking it says "An error occurred:  could not open location; you might not have permission to open the file."

4.   We need to be able to install some non-default EPG and record system that understands series and such better than the default EPG.

If the answer to any and/or all of these is "we need to do some Python and/or C and/or C++ hacking" then "let us begin".  If not that would be even better :-)

---

### Post by Russel_Winder on 2010-11-15
Sorry I forgot to add:

516 anglides:/home/Checkouts/Git/Git/Guppy/guppy
|> ll
total 184
drwx------  2 russel russel  4096 2010-01-12 16:20 ./
drwx------ 10 russel russel  4096 2010-01-12 16:48 ../
-rw-------  1 russel russel  1480 2010-01-12 16:20 about.py
-rw-------  1 russel russel 21633 2010-01-12 16:20 FileSystemModel.py
-rw-------  1 russel russel  1333 2010-01-12 16:20 FileTransfer.py
-rwx------  1 russel russel  2963 2010-01-12 16:20 guppy*
-rw-------  1 russel russel 41041 2010-01-12 16:20 guppy.glade
-rw-------  1 russel russel  1550 2010-01-12 16:20 guppy-gtk.xml
-rw-------  1 russel russel 41056 2010-01-12 16:20 GuppyWindow.py
-rw-------  1 russel russel   776 2010-01-12 16:20 __init__.py
-rw-------  1 russel russel 12758 2010-01-12 16:20 PathBar.py
lrwxrwxrwx  1 russel russel    11 2010-03-03 19:06 pixmaps -> ../pixmaps//
-rw-------  1 russel russel  8842 2010-01-12 16:20 puppy.py
-rw-------  1 russel russel  3742 2010-01-12 16:20 PVRErrorWindow.py
-rw-------  1 russel russel  5773 2010-01-12 16:20 TransferThread.py
-rw-------  1 russel russel  3133 2010-01-12 16:20 util.py
517 anglides:/home/Checkouts/Git/Git/Guppy/guppy
|> ./guppy 
Traceback (most recent call last):
  File "./guppy", line 73, in <module>
    from guppy import GuppyWindow
ImportError: No module named guppy
518 anglides:/home/Checkouts/Git/Git/Guppy/guppy
|> 


which implies there is a problem with the structure of the filestore in the Git repository?

Or perhaps I am doing something silly?

---

### Post by racb on 2011-12-24
I found this trying to get puppy to work in Oneiric. Thanks to all who contributed.

usbfs is no longer compiled in the kernel, so puppy does not work as is. I found a patch here: [http://www.cm.ph.bham.ac.uk/software/source/puppy_1.14.sysfs.patch](http://www.cm.ph.bham.ac.uk/software/source/puppy_1.14.sysfs.patch)

puppy is also no longer maintained (see [http://peteru.blogspot.com/2009/09/puppy-is-old-dog-now.html](http://peteru.blogspot.com/2009/09/puppy-is-old-dog-now.html)). So to make things easier, I created a github repository and packaged it myself.

So in case this is of use to someone else:

Github: [https://github.com/basak/puppy](https://github.com/basak/puppy)

Package for Ubuntu: [https://launchpad.net/~racb/+archive/extra](https://launchpad.net/~racb/+archive/extra)

---

### Post by mactece on 2012-12-26
I thought I'd add to this post because I was having a lot of trouble with gtkam. It seems it didn't like my laptop (very old hardware now) or OS (Linux Mint 14 "Nadia") or something. Anyway, the connection kept "dropping" and I would get an error message saying it couldn't access the Toppy. I needed a cast-iron way of getting the files to download.

So here's how I fixed it, which I thought I'd share in case anyone else was in the same position as me...(ideally you'll need to be familiar with the linux terminal, but if you're not try copying and pasting the commands in and see what happens. If you want to know more about the commands type "gphoto2" into a browser and look for chapter 2 of its manual, or type the commands into a browser and see what they bring up).

nb the use of "Sudo" seemed to over-ride the objections I was getting about the Toppy being "in use" or "unavailable". if you don't know what Sudo is you should probably stop here and do some research before you go any further.

First, install gphoto2 and any libraries it needs. You can do this from Synaptic or in a terminal ("sudo apt-get install gphoto2")

Connect the Toppy, then unmount it in the file manager (as described in the post above).

Start a terminal and change the active (current) directory to the location where you want to store the downloaded files. In my case this was the Desktop, so "cd Desktop"

Check the Topfield is visible "sudo gphoto2 --auto-detect" (the long dash before "auto-detect" is a double dash, ie "-" then another "-" straight after it. Similarly for "--list-files" and "--get-file", below)

Get a list of all the files available for download "sudo gphoto2 --list-files"

Scoll up through the list and find the number of the file you want to download e.g. #133. Ignore the "#", so in my example just "133"

Download the file "sudo gphoto2 --get-file 133" and the file should download to the current directory (Desktop, in my case)

There are ways to download more than one file at a time, which are listed in the gphoto MAN pages, but I'm happy with one at a time.

Enjoy!

---

