---
title: "Howto: Connect ZTE MF627 3G modem with NM0.7"
date: 2008-12-21
forum: Tutorials
---

### Post by jfernyhough on 2008-12-21
**Updated**
With Jaunty this is now not necessary and there is an easier way around. First, install udev-extras:

$ sudo aptitude install udev-extras

Depending on if/when my patch* gets accepted you will likely need to add information about the modem to the HAL infomation:

$ sudo cp /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi /etc/hal/fdi/information/
$ gksudo gedit /etc/hal/fdi/information/10-modem.fdi

Add the following:
```
        <!-- ZTE MF627 HSDPA USB dongle -->
        <match key="@info.parent:usb.product_id" int="0x0031">
          <match key="@info.parent:usb.interface.number" int="3">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
          </match>
        </match>

```
and save the file.

Now plug in your modem. It should mount as the ZeroCD device (1). Now right-click the icon on the desktop and eject. Wait a moment, and the light on the modem will go dark, then relight red then green. It should now mount as a modem and be detected by Network Manager (2).

A note should be made about udev-extras, though:> This package contains additional rules and add-ons for udev that are not yet mature enough for the base udev package.  Many of these are intended for use with DeviceKit, replacing parts of HAL.YMMV.

1)lsusb:```
ID 19d2:2000 ONDA Communication S.p.A.
```
2)lsusb:```
ID 19d2:0031 ONDA Communication S.p.A.
```

*
[https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/407679](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/407679)
########

I recently bought a 3G mobile broadband modem and then realised I'd bought the wrong model - instead of getting a Huawei E160 or E169 that reportedly work OOTB with Intrepid I got a ZTE MF627 for which no information exists. On the plus side, it has a built-in MicroSD reader...

I initially submitted a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/310025"). Since then, however, I have got it working and so here is a how-to. I hope someone else finds this useful. :D

**1) Download and install usb_modeswitch**

Go [here]("http://www.draisberghof.de/usb_modeswitch/#download") and download the deb file. A direct link is [here]("http://www.draisberghof.de/usb_modeswitch/usb-modeswitch_0.9.5_i386.deb"). Then install it.

This provides a way of switching the USB modem from its initial useless mode to its correct, functional modes. It will need configuring to apply to the modem.

**2) Edit /etc/usb_modeswitch.conf to apply to the MF628+**

Either comment the first modem configuration out, then find and uncomment the section for the MF628+, or (more easily) replace the content of the file with:

```
########################################################
# ZTE MF628+ (tested version from Telia / Sweden)
#
# Contributor: Joakim Wennergren
#
# Also applies to MF627 (Tested 3 UK) JF

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0031

MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
```Save it.

**3) Create a udev rule to automatically run usb_modeswitch when the modem is plugged in**

Create a new file called 999-zte-rules:
gksudo gedit /etc/udev/rules.d/999-zte.rules

Its content should be as follows:
```
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", RUN+="/usr/sbin/usb_modeswitch"
```This will trigger usb_modeswitch every time you plug in the modem. Which is useful if you want it to work automatically. You can of course run it manually if you want.

**4) Add device information to HAL so network-manager recognises the device as a modem**

Finally, in order for Network Manager to recognise the modem information has to be added to HAL.

Create a new file:
gksudo gedit /usr/share/hal/fdi/information/20thirdparty/20-zte-mf627.fdi

Its content should be as follows:
```
<!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
      <!-- ZTE MF627 HSDPA USB dongle -->
      <match key="@info.parent:usb.vendor_id" int="0x19d2">
        <match key="@info.parent:usb.product_id" int="0x0031">
          <match key="@info.parent:usb.interface.number" int="3">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
            <append key="info.capabilities" type="strlist">modem</append>
          </match>
        </match>
      </match>
  </device>
</deviceinfo>
```Save it.

**5) Plug in the modem**
Make sure the SIM card is in the modem (and if you're using 3 UK make sure you're in a 3G area. otherwise it won't work) and plug it into your PC.

After a little while (several seconds) the LED should light red as it powers up, then switch to blue when it finds a network. You can check it's working by checking dmesg. Once modeswitch has been triggered and the modem reboots you will be presented with the ZeroCD device (e.g. containing the 3connect software), a USB MicroSD card reader, and if everything has gone correctly, Network Manager will detect a new mobile broadband modem.

Feel free to ignore the ZeroCD device and unmount it from the desktop.

If everything has gone correctly dmesg should read something like:
```
[52189.029694] usb 5-1: new high speed USB device using ehci_hcd and address 32
[52189.177064] usb 5-1: configuration #1 chosen from 1 choice
[52189.192061] usb-storage: device ignored
[52194.546308] usb 5-1: USB disconnect, address 32
[52200.032140] usb 5-1: new high speed USB device using ehci_hcd and address 33
[52200.183440] usb 5-1: configuration #1 chosen from 1 choice
[52200.184979] option 5-1:1.0: GSM modem (1-port) converter detected
[52200.185184] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
[52200.185453] option 5-1:1.1: GSM modem (1-port) converter detected
[52200.185592] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
[52200.200858] scsi28 : SCSI emulation for USB Mass Storage devices
[52200.204904] usb-storage: device found at 33
[52200.204909] usb-storage: waiting for device to settle before scanning
[52200.205113] option 5-1:1.3: GSM modem (1-port) converter detected
[52200.205304] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB2
[52205.205580] usb-storage: device scan complete
[52205.207696] scsi 28:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[52205.210603] scsi 28:0:0:1: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[52205.226669] sd 28:0:0:0: [sdb] Attached SCSI removable disk
[52205.228914] sd 28:0:0:0: Attached scsi generic sg2 type 0
[52205.345654] sr1: scsi-1 drive
[52205.345837] sr 28:0:0:1: Attached scsi CD-ROM sr1
[52205.346023] sr 28:0:0:1: Attached scsi generic sg3 type 5
[52218.692468] ISO 9660 Extensions: Microsoft Joliet Level 1
[52218.699732] ISOFS: changing to secondary root
```

References:
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)
[http://blog.ufsoft.org/2007/11/30/zte-mf622-usb-modem-under-linux](http://blog.ufsoft.org/2007/11/30/zte-mf622-usb-modem-under-linux)
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/267727](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/267727)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/259028](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/259028)
[https://answers.launchpad.net/ubuntu/+source/network-manager/+question/48520](https://answers.launchpad.net/ubuntu/+source/network-manager/+question/48520)
Probably some others I've forgotten.

---

### Post by andlun57 on 2009-01-06
Thank you for an excellent description. However, to get the Network Manager to recognise the modem, as a last step I have to call insmod, everytime i plug in the modem. I use the command:
```

insmod /lib/modules/2.6.27-9-generic/kernel/drivers/usb/serial/
usbserial.ko vendor=0x19d2 product=0x0031
```

Any idea why?

---

### Post by peteatrom on 2009-02-11
New to ubuntu followed the instructions but the modem is not recognized. I cannot understand the last reply the part of the path "2.6.27-9-generic" does not exist!

---

### Post by erikbergstrom on 2009-03-10
Thanks, I finally got it to work!

I changed one thing though:

In step 4 when we created the file I renamed it, 

from 
gksudo gedit /usr/share/hal/fdi/information/20thirdparty/20-zte-mf627.fdi

to
gksudo gedit /usr/share/hal/fdi/information/20thirdparty/20-zte-mf628+.fdi

I thought it would maker more sense and then everything justed worked!

Thanks!

---

### Post by craigmcfly on 2009-03-15
Thanks. Those instructions worked a treat and it was up and running in a couple of minutes. 

The ppp process binds to ttyUSB2. Is there any way you know of to get the signal strength, possibly from one of the other ttys?

---

### Post by CCK on 2009-03-15
Thanks. The australian three supplies a mf627 modem with product id 0064 instead of 0031. I changed all references to product id 0031 to 0064 in the suggestions and it worked. Except that there was one problem - NM0.7 does not recognise it until I changed the line 
```

          <match key="@info.parent:usb.interface.number" int="3">
```to ```

          <match key="@info.parent:usb.interface.number" int="2">
```in the fdi file.

---

### Post by euriconeto on 2009-03-31
Hello Everyone!

I have exactly the same modem (ZTE627) working through 3 (australia) and even though every thing is very well explained in this thread, because I'm very new Ubuntu user (have a 8.10 version) I simply can't follow up the instructions.

Any one with patience to lead me through a very basic and (even more) detailed 'how to' to set my modem?

Thank you!!

---

### Post by CCK on 2009-04-07
See if I can explain how I got my Austrlian version MF627 USB key working on my 2 laptops (dell and hp) with ubuntu 8.10.

Firstly you should have got the usb_modeswitch in [http://www.draisberghof.de/usb_modeswitch/#download](http://www.draisberghof.de/usb_modeswitch/#download) as mentioned in previous post.

Then backup your /etc/usb_modeswitch.conf somewhere - your home directory as an example.

Now replace your /etc/usb_modeswitch.conf with the following content:

```

########################################################
# ZTE MF628+ (tested version from Telia / Sweden) 
# ZTE MF626 
# 
# Contributor: Joakim Wennergren

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0064

MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"

```

Now create a file /etc/udev/rules.d/999-zte.rules with the following content:
```
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", RUN +="/usr/sbin/usb_modeswitch"
SUBSYSTEM=="usb", SYSFS{idProduct}=="0064", SYSFS{idVendor}=="19d2", RUN +="/sbin/modprobe usbserial vendor=0x19d2 product=0x0064"

```

For the above file there were a couple of typo - please check my follow up post.

Then create a file /usr/share/hal/fdi/information/20thirdparty/20-zte-mf627.fdi with the following content:

```
<!-- -*- SGML -*- -->
<deviceinfo version="0.2">
<device>
<!-- ZTE MF627 HSDPA USB dongle -->
<match key="@info.parent:usb.vendor_id" int="0x19d2">
<match key="@info.parent:usb.product_id" int="0x0064">
<match key="@info.parent:usb.interface.number" int="2">
<append key="modem.command_sets" type="strlist">GSM-07.07</append>
<append key="modem.command_sets" type="strlist">GSM-07.05</append>
<append key="info.capabilities" type="strlist">modem</append>
</match>
</match>
</match>
</device>
</deviceinfo>

```

Plug in your USB modem now. Around 5 to 10 seconds later "do lsusb" to check the output. There should be a line with some entry like "ID 19d2:0064" after around 5 to 10 seconds. This means that your udev rules together with usb_modeswitch is working.

Do a ls -l /dev/ttyUSB0 and ls -l /dev/ttyUSB1. You should see those entries.

By this time if you are alreday logged in to gnome you may see network manager prompt you on entering mobile broadbank setup for the detected modem.

---

### Post by mediumhouse on 2009-04-08
Hi,

I have done everything here and still nothing is working.  I manage to get it to switch from 2000 to 0064 [I am in Australia so am trying that one - the 0031 didn't work when I tried it], but it is not getting recognised as a modem in network manager or anywhere.  Has anyone got any ideas as to where in the problems lies?

Thanks

---

### Post by CCK on 2009-04-09
Hi mediumhouse,

Can you try the following udev rules file instead:

```

SUBSYSTEM=="usb", SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000", RUN+="/usr/sbin/usb_modeswitch"
SUBSYSTEM=="usb", SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="0064", RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0x0064"

```

Looks like I put a "space" after RUN in the post. I do not have the space between RUN and +.

If it works you should see /dev/ttyUSB0 and /dev/ttyUSB1 created.

---

### Post by Totzo on 2009-04-09
just got my mf627 on 3 uk working using these instructions, I found this post [http://ubuntuforums.org/showthread.php?t=1065934](http://ubuntuforums.org/showthread.php?t=1065934) (post #5) which was the crunch for me- permissions on /etc/resolv.conf It wouldn't connect until that was sorted. Hope this helps someone else! :p

---

### Post by AndyCee on 2009-04-17
@CCK: Thank you! Got my (wife's) 3 modem working now, after following your guide.

I had to change the APN to "3services", and BAM! Interweb enabled.

[Why can't i thank anyone?]

---

### Post by cresswell on 2009-04-26
Hi

New to linux and having a few problems despite a very good tutorial.
> 

########################################################
# ZTE MF628+ (tested version from Telia / Sweden)
#
# Contributor: Joakim Wennergren
#
# Also applies to MF627 (Tested 3 UK) JF

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0031

MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
 I have created the **/etc/usb_modeswitch.conf **asrequested - the target vendor and product numbers are the same as the ones I get when using lsusb to list usb devicesCreated the udev rule and assume it runs automatically but have tried to run it manually also - it said:
target devices found - 1
default devices found  - 0 - is the device connected - bye

so I assume it is working and switching the mode correctly[B]

Added the device information to hal as written here

[/B]> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
      <!-- ZTE MF627 HSDPA USB dongle -->
      <match key="@info.parent:usb.vendor_id" int="0x19d2">
        <match key="@info.parent:usb.product_id" int="0x0031">
          <match key="@info.parent:usb.interface.number" int="3">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
            <append key="info.capabilities" type="strlist">modem</append>
          </match>
        </match>
      </match>
  </device>
</deviceinfo>
So I thought it was all correct however I am not getting the 3 ttyusb drives (modems) I am only seeing the usb drive with 3connect software in it - this 3connect usb drive that I can see has the windows installers and autorun files in and also has a folder called LINUXFILES which does have and .rpm package in.

will post my dmesg results in a sec too

I welcome any help on this I must be close but too much of  a linux noob to cross the final few hurdles!

Thanks in advance

---

### Post by cresswell on 2009-04-26
here is my dmesg readout too
[FONT=Arial][B]
[   28.404095] usb 1-4: new high speed USB device using ehci_hcd and address 3
[   28.550305] usb 1-4: configuration #1 chosen from 1 choice
[   28.578570] scsi3 : SCSI emulation for USB Mass Storage devices
[   28.580059] usb-storage: device found at 3
[   28.580074] usb-storage: waiting for device to settle before scanning
[   31.368487] r8169: eth0: link down
[   31.430279] NET: Registered protocol family 17
[   31.483131] [drm] Initialized drm 1.1.0 20060810
[   31.488557] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   31.488567] pci 0000:00:02.0: setting latency timer to 64
[   31.489884] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   33.581351] usb-storage: device scan complete
[   33.583340] scsi 3:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[   33.586830] scsi 3:0:0:1: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[   33.610359] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[   33.611197] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   33.639757] sr1: scsi-1 drive
[   33.640008] sr 3:0:0:1: Attached scsi CD-ROM sr1
[   33.640008] sr 3:0:0:1: Attached scsi generic sg3 type 5
[  255.000006] ieee80211_crypt: registered algorithm 'TKIP'
[  260.706715] NET: Registered protocol family 10
[  260.710970] lo: Disabled Privacy Extensions
[  260.713424] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  269.478802] ISO 9660 Extensions: Microsoft Joliet Level 1
[  269.482096] ISOFS: changing to secondary root
[  271.032016] eth1: no IPv6 routers present
[  328.279196] ttyS1: LSR safety check engaged!
[  328.279236] type=1503 audit(1240789059.822:5): operation="capable" name="sys_admin" pid=6126 profile="/usr/sbin/cupsd"
[  434.763644] usb 1-4: USB disconnect, address 3
[  434.864647] scsi 3:0:0:1: rejecting I/O to dead device
[  448.776064] usb 1-7: new high speed USB device using ehci_hcd and address 4
[  448.932057] usb 1-7: configuration #1 chosen from 1 choice
[  448.934045] usb-storage: device ignored
[  454.412616] usb 1-7: USB disconnect, address 4
[  459.780073] usb 1-7: new high speed USB device using ehci_hcd and address 5
[  459.957784] usb 1-7: configuration #1 chosen from 1 choice
[  460.000074] scsi5 : SCSI emulation for USB Mass Storage devices
[  460.000918] usb-storage: device found at 5
[  460.000923] usb-storage: waiting for device to settle before scanning
[  465.001400] usb-storage: device scan complete
[  465.003392] scsi 5:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[  465.006394] scsi 5:0:0:1: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[  465.019650] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  465.020520] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  465.041733] sr1: scsi-1 drive
[  465.042036] sr 5:0:0:1: Attached scsi CD-ROM sr1
[  465.042361] sr 5:0:0:1: Attached scsi generic sg3 type 5
[  477.974367] ISO 9660 Extensions: Microsoft Joliet Level 1
[  477.977866] ISOFS: changing to secondary root
[/B][/FONT]

---

### Post by pablo180 on 2009-04-28
> **cresswell said:**
> Hi

New to linux and having a few problems despite a very good tutorial.

I am only seeing the usb drive with 3connect software in it - this 3connect usb drive that I can see has the windows installers and autorun files in and also has a folder called LINUXFILES which does have and .rpm package in.

I received the ZTE MF627 today from 3 UK, the customer service people and technical support all told me it worked on Linux but I was a little sceptical. 

Amazingly I plugged it in and it does have Linux drivers on the USB drive - and they work in Ubuntu!

There's no instructions however, and I am certainly no Ubuntu expert but I managed to get it working in about 30 seconds. As I said though, I am no expert so you may want to get confirmation from someone else before following what I did but it is up to you. 

I copied the Linux files across to my Desktop, then opened a terminal and navigated to the folder on the desktop:

```
cd Desktop
```

```
cd LinuxUI
```

One inside the folder I noticed a file named install.sh so I did something that I remembered from another Linux installation years ago, I am not sure if this is how you are meant to do it on Ubuntu. 

```
sudo sh install.sh
```

That installed the drivers and the little 3 UK program under Applications>Internet>3UK. 

I plugged it in ran the program and it works perfectly. I don't think you can use it as USB storage though.

---

### Post by Totzo on 2009-04-28
> **pablo180 said:**
> I received the ZTE MF627 today from 3 UK, the customer service people and technical support all told me it worked on Linux but I was a little sceptical. 

Amazingly I plugged it in and it does have Linux drivers on the USB drive - and they work in Ubuntu!

There's no instructions however, and I am certainly no Ubuntu expert but I managed to get it working in about 30 seconds. As I said though, I am no expert so you may want to get confirmation from someone else before following what I did but it is up to you. 

I copied the Linux files across to my Desktop, then opened a terminal and navigated to the folder on the desktop:

```
cd Desktop
```

```
cd LinuxUI
```

One inside the folder I noticed a file named install.sh so I did something that I remembered from another Linux installation years ago, I am not sure if this is how you are meant to do it on Ubuntu. 

```
sudo sh install.sh
```

That installed the drivers and the little 3 UK program under Applications>Internet>3UK. 

I plugged it in ran the program and it works perfectly. I don't think you can use it as USB storage though.

I think the jist of this thread is about using network manager as opposed to the bundled software with the **ZTE MF627**, I may be wrong though?

---

### Post by cresswell on 2009-04-29
Thank you very much for the quick and easy to follow reply pablo - i will give it a go but i did loose paitience and eventually reinstalled xp as my main os on the laptop. 

thanks

---

### Post by chender on 2009-05-02
Here are the steps I followed.  Note mine as a MF636 purchased Apr2009

1. Download and install usb_modeswitch.  Go here and download the deb file. A direct link is here. Then install it.
2. Edit usb_modeswitch.conf
	sudo gedit /etc/usb_modeswitch.conf
	delete all content, and REPLACE with this - paste in this content.  I know that the text does not match the modem, but I went for simple and it works.  The text behind # is commented out in any event:

	########################################################
# ZTE MF636 (tested Rogers AT+T canada)
#
# Contributor: Joakim Wennergren
#
# 

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0031

MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"

3. Create a udev rule to automatically run usb_modeswitch when the modem is plugged in

Create a new file called 999-zte.rules:
sudo gedit /etc/udev/rules.d/999-zte.rules
paste in this content:  
SUBSYSTEM="usb", SYSFS(idVendor)=="19d2", SYSFS(idProduct)=="2000", RUN+="/usr/sbin/usb_modeswitch"


4. finally update HAL:
Create a new file:
sudo gedit /usr/share/hal/fdi/information/20thirdparty/20-zte-mf627.fdi

Its content should be as follows:
Code:

<!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
      <!-- ZTE MF627 HSDPA USB dongle -->
      <match key="@info.parent:usb.vendor_id" int="0x19d2">
        <match key="@info.parent:usb.product_id" int="0x0031">
          <match key="@info.parent:usb.interface.number" int="2">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
            <append key="info.capabilities" type="strlist">modem</append>
          </match>
        </match>
      </match>
  </device>
</deviceinfo>


5.  Now this is where I deviate and hopefully simplify for newbies such as me.  First the problem.  If you plug the stick in, you will see the lights go green then blue.  The stick is really a cell phone and its awaiting instructions.  However Rogers in their keenness to make it user friendly set the stick up as a storage device to install the windows software and initiate the modem.  That autorun software prevents ubuntu from seeing the modem inside the stick.

Type lsusb in terminal before plugging the stick in.  You will see a set of rows.  Plug the stick in, and a new row appears at the top.  The last 4 digits are 2000 which means storage device.  They should be 0031 which means the modem. 

The simple solution for me was to plug the stick into an old windows laptop, install everything and run it once.  After that the stick is initiated, and go back to ubuntu.

Untick the wireless connection, and select edit connections from your wireless applet.  

select mobile broadband
input username (12 digit number on the SIM car beneath the bar code)
password is 1234

At that stage i was immediately online.  Some people have issues with firefox going offline.  Simply untick offline, and done.




with particular thanks to [http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630) for most of the breakthrough for me here.

---

### Post by jfernyhough on 2009-05-03
With Jaunty this is now not necessary and there is an easier way around. First, install udev-extras:

$ sudo aptitude install udev-extras

Now plug in your modem. It should mount as the ZeroCD device (1). Now right-click the icon on the desktop and eject. Wait a moment, and the light on the modem will go dark, then relight. It should now mount as a modem and be detected by Network Manager (2).

How easy was that?

A note should be made about udev-extras, though:> This package contains additional rules and add-ons for udev that are not yet mature enough for the base udev package.  Many of these are intended for use with DeviceKit, replacing parts of HAL.YMMV.

1)lsusb:```
ID 19d2:2000 ONDA Communication S.p.A.
```
2)lsusb:```
ID 19d2:0031 ONDA Communication S.p.A.
```

---

### Post by BrinX on 2009-05-21
hey, i have followed the guide here exactly, 

but my dongle cuts out, or rather unmounts itself after around 30 mins.. 

PLEASE HELP 


this is my only internet access and i am tied to a two year contract.. it runs fine in windows ... but i dont want to go back to that... 

this is driving me insane..

works perfectly for 30 mins or so.. then i have to physically pull the dongle from the usb port and re insert it to get back online...


PLEASE PLEASE HELP ME FIX THIS - updates impossible - online business impossible... PLEASE DONT TELL ME I HAVE TO GO BACK TO WINDOWS¬!

Juanty 

lsusb output: 
Bus 001 Device 013: ID 19d2:0031  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0443:001c Gateway, Inc. 
Bus 002 Device 002: ID 0443:001d Gateway, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by caliston on 2009-05-23
BrinX, can you post a dmesg and /var/log/syslog excerpt?


Anyone having any luck on jaunty?  I have  3 UK MF627.  I've installed udev-extras, but I don't think it's kicking in.

dmesg says this:
```

[40732.620069] usb 1-1: new high speed USB device using ehci_hcd and address 3
[40732.768214] usb 1-1: configuration #1 chosen from 1 choice
[40732.954729] Initializing USB Mass Storage driver...
[40732.965516] usb-storage: device ignored
[40732.965639] usbcore: registered new interface driver usb-storage
[40732.965650] USB Mass Storage support registered.

```

and lsusb has it as a mass storage device (with no name supplied by Linux in the first line, as is usual):

```

$ sudo lsusb -v
Bus 001 Device 003: ID 19d2:2000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x19d2 
  idProduct          0x2000 
  bcdDevice            0.00
  iManufacturer           2 ZTE,Incorporated
  iProduct                1 ZTE CDMA Technologies MSM
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
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
        bEndpointAddress     0x81  EP 1 IN
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
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

```

But nothing else happens.  As it says 'device ignored' I can't get at the mass storage volume.

I tried grabbing the usb_modeswitch config from [http://www.greenhughes.com/content/zte-mf627-easy-way](http://www.greenhughes.com/content/zte-mf627-easy-way)
and trying to 'flip' it manually:

```

$ sudo usb_modeswitch -c /etc/usb_modeswitch_zte_mf627.conf 

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Prepare switching, accessing device 003 on bus 001 ...
Looking for active driver ...
 No driver found. Either detached before or never attached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 Sending the message returned error -110. Trying to continue
-> Run lsusb to note any changes. Bye

```

No change there.  Error -110 is ETIMEOUT.

I had a poke around the kernel source - in drivers/usb/storage/unusual_devs.h the device is listed:
```

UNUSUAL_DEV(  0x19d2, 0x2000, 0x0000, 0x0000,
                "Onda ET502HS",
                "USB MMC Storage",
                US_SC_DEVICE, US_PR_DEVICE, NULL,
                US_FL_IGNORE_DEVICE),

```

That's what's causing the 'device ignored' messages.  But it's slightly odd that the name at least isn't showing in lsusb.

Do I have to recompile my kernel without this entry?

---

### Post by Meads on 2009-05-28
> **CCK said:**
> See if I can explain how I got my Austrlian version MF627 USB key working on my 2 laptops (dell and hp) with ubuntu 8.10.

Firstly you should have got the usb_modeswitch in [http://www.draisberghof.de/usb_modeswitch/#download](http://www.draisberghof.de/usb_modeswitch/#download) as mentioned in previous post.

Then backup your /etc/usb_modeswitch.conf somewhere - your home directory as an example.

Now replace your /etc/usb_modeswitch.conf with the following content:

```

########################################################
# ZTE MF628+ (tested version from Telia / Sweden) 
# ZTE MF626 
# 
# Contributor: Joakim Wennergren

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0064

MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"

```

Now create a file /etc/udev/rules.d/999-zte.rules with the following content:
```
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", RUN +="/usr/sbin/usb_modeswitch"
SUBSYSTEM=="usb", SYSFS{idProduct}=="0064", SYSFS{idVendor}=="19d2", RUN +="/sbin/modprobe usbserial vendor=0x19d2 product=0x0064"

```

For the above file there were a couple of typo - please check my follow up post.

Then create a file /usr/share/hal/fdi/information/20thirdparty/20-zte-mf627.fdi with the following content:

```
<!-- -*- SGML -*- -->
<deviceinfo version="0.2">
<device>
<!-- ZTE MF627 HSDPA USB dongle -->
<match key="@info.parent:usb.vendor_id" int="0x19d2">
<match key="@info.parent:usb.product_id" int="0x0064">
<match key="@info.parent:usb.interface.number" int="2">
<append key="modem.command_sets" type="strlist">GSM-07.07</append>
<append key="modem.command_sets" type="strlist">GSM-07.05</append>
<append key="info.capabilities" type="strlist">modem</append>
</match>
</match>
</match>
</device>
</deviceinfo>

```

Plug in your USB modem now. Around 5 to 10 seconds later "do lsusb" to check the output. There should be a line with some entry like "ID 19d2:0064" after around 5 to 10 seconds. This means that your udev rules together with usb_modeswitch is working.

Do a ls -l /dev/ttyUSB0 and ls -l /dev/ttyUSB1. You should see those entries.

By this time if you are alreday logged in to gnome you may see network manager prompt you on entering mobile broadbank setup for the detected modem.

Works brilliantly, thank you.

Seems so much faster than my E220 which i have been using.

---

### Post by Meads on 2009-05-28
> **caliston said:**
> BrinX, can you post a dmesg and /var/log/syslog excerpt?


Anyone having any luck on jaunty?  I have  3 UK MF627.  I've installed udev-extras, but I don't think it's kicking in.

dmesg says this:
```

[40732.620069] usb 1-1: new high speed USB device using ehci_hcd and address 3
[40732.768214] usb 1-1: configuration #1 chosen from 1 choice
[40732.954729] Initializing USB Mass Storage driver...
[40732.965516] usb-storage: device ignored
[40732.965639] usbcore: registered new interface driver usb-storage
[40732.965650] USB Mass Storage support registered.

```

and lsusb has it as a mass storage device (with no name supplied by Linux in the first line, as is usual):

```

$ sudo lsusb -v
Bus 001 Device 003: ID 19d2:2000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x19d2 
  idProduct          0x2000 
  bcdDevice            0.00
  iManufacturer           2 ZTE,Incorporated
  iProduct                1 ZTE CDMA Technologies MSM
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
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
        bEndpointAddress     0x81  EP 1 IN
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
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

```

But nothing else happens.  As it says 'device ignored' I can't get at the mass storage volume.

I tried grabbing the usb_modeswitch config from [http://www.greenhughes.com/content/zte-mf627-easy-way](http://www.greenhughes.com/content/zte-mf627-easy-way)
and trying to 'flip' it manually:

```

$ sudo usb_modeswitch -c /etc/usb_modeswitch_zte_mf627.conf 

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Prepare switching, accessing device 003 on bus 001 ...
Looking for active driver ...
 No driver found. Either detached before or never attached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 Sending the message returned error -110. Trying to continue
-> Run lsusb to note any changes. Bye

```

No change there.  Error -110 is ETIMEOUT.

I had a poke around the kernel source - in drivers/usb/storage/unusual_devs.h the device is listed:
```

UNUSUAL_DEV(  0x19d2, 0x2000, 0x0000, 0x0000,
                "Onda ET502HS",
                "USB MMC Storage",
                US_SC_DEVICE, US_PR_DEVICE, NULL,
                US_FL_IGNORE_DEVICE),

```

That's what's causing the 'device ignored' messages.  But it's slightly odd that the name at least isn't showing in lsusb.

Do I have to recompile my kernel without this entry?

Got mine going in Jaunty, udev-extras did not seem to do anything so i followed CCk's instructions and i am using it now.

Checking lsusb does not give a description of the device, but if you check dmesg you should see "usb 2-5: GSM modem (1-port) converter now attached to ttyUSB0" it's actually there 3 times but at least it is working.

---

### Post by caliston on 2009-05-28
I had another go.  I installed the kernel from karmic (2.6.30-5-generic) and was able to see the /dev/ttyUSB0 device in the log:

```
kernel: [  570.520055] usb 1-1: new high speed USB device using ehci_hcd and address 5
kernel: [  570.666039] usb 1-1: configuration #1 chosen from 1 choice
kernel: [  570.668743] option 1-1:1.0: GSM modem (1-port) converter detected
kernel: [  570.668930] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
kernel: [  570.752362] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
kernel: [  570.752409] option 1-1:1.0: device disconnected

```

I think this was an interaction with udev.  I killed udev and hal and managed to get the /dev/ttyUSB0 device to stay up, but I couldn't get any sense out of it with minicom.  The syslog does suggest NetworkManager was interacting with the device on one occasion (not when I tried minicom, as I had no X)

But having broken the nvidia video driver by forcing a karmic kernel on top of jaunty, it was not very usable so I had to drop back to the jaunty standard kernel (2.6.28-11-generic, as used in my previous post).

I also tried some USB diagnostic programs: [usb-robot](http://usb-robot.sourceforge.net/) and [usbreset](http://marc.info/?l=linux-usb&m=121459435621262&w=2).  I got somewhere with these - tried to send the USB modeswitch packet by hand - it didn't complain, but I wasn't able to reset the device properly to make Linux spot that it had flipped mode.  I did get a -2 error from usb_modeswitch afterwards which matches the error in the troubleshooting section of the usb_modeswitch page for MF626 (the answer: rebuild the kernel without the unusual_devs.h entry.  Not tried that yet).

The Russian Gentoo thread linked to on the usb_modeswitch page ([(Google English translation)](http://translate.google.com/translate?prev=hp&hl=en&js=n&u=http%3A%2F%2Fru.gentoo-wiki.com%2Fwiki%2FMF626&sl=ru&tl=en&history_state0=) has some other things to try, including killing the ZeroCD function permanently.  Perhaps I'd be best trying to rebuild my usb_storage module as a start.

---

### Post by amj on 2009-05-30
> **caliston said:**
> 
Anyone having any luck on jaunty?  I have  3 UK MF627.  I've installed udev-extras, but I don't think it's kicking in.


Hi caliston, 

I'm also trying to get an MF637 from 3 UK working.   I'm having the exact same problem as you.   I have installed udev-extras, but I'm not even getting it mounted as a drive.    

Anyone in the UK on Jaunty getting it to work?

Cheers, 
AJ

---

### Post by amj on 2009-05-30
I'm getting much closer ... 
Since the udev-extras tip didn't work for me, I went back to jfernyhough's original post.  
Now, I see the 3Connect icon on the desktop, and unmount it.

Here's where it goes a little funny.  If I click on Network Manager, I see 
"Mobile Broadband (ZTE Incorporated ZTE CDMA Technologies MSM), along with three choices: two for O2 (which I had working with a different phone with an O2 SIM) and one for 3, with I added manually in NetworkManager under the "Edit Connections" option. 

If I look at the options for 3, all I have is 
 Number = *99#
 APN = 3internet

This is different from the O2 settings, which also include username and password, and the APN is mobile.o2.co.uk

Are there any changes I should have here?

Otherwise, when I try to connect to "3", I get the swirling connection icon followed by the message "GSM Network Disconnected - You are now offline"

I should be in a 3G coverage area for 3 (I'm going to pop the SIM into a 3G phone next to verify), but according to 3's coverage maps, I should be fine. 

Cheers, 
AJ

---

### Post by amj on 2009-05-30
I've confirmed via a handset that I'm getting a 3G signal from 3 at my house.

Update: I've tried the dongle with a Win2K laptop, and it worked fine.   So the dongle and my coverage are ok.   It's my Ubuntu setup that still needs tweaking then.

---

### Post by amj on 2009-05-30
I decided to delete all the Mobile Broadband connections (O2 and 3), reboot, and plug in again.   When I did that, the modem was detected, and the broadband setup app popped up.   I selected 3, and took the defaults.   
Same result ... tries to connect, but then disconnects.   Oddly, there are two lines for selecting 3.

I'm wondering if the fact that two connections are being listed is part of the problem.    I've tried three ways to set up:
 - the udev-extras method
 - the shell script on the USB stick
 - the original method as outlined in this thread. 

I wonder if I have two slightly different modems set up as a result.   
Please advise which files I can post here to analyse?

Cheers, 
AJ

---

### Post by nickpiggott on 2009-06-07
I notice a few people having the same symptoms as my system:

[LIST]
[*] eee-pc 901
[/LIST]

[LIST]
[*]Stock 9.04 Jaunty
[/LIST]

[LIST]
[*]Network Manager 0.7.0.100
[/LIST]
I had already disabled the auto-run on the MF627 by sticking it in a Windows machine, and sending it an AT+ZCDRUN=8 command. I had also used the Network Manager "wizard" to create a connection for Three UK.

However, when I tried to connect, it had that endless swirling, followed by "You are disconnected" message.

I dropped it into Gnome Dialler (which is basically a GUI for wvdial), and looked at the log. What it was showing as a connection happening (via ttyUSB2) and then pppd was failing to start correctly. (That's odd, as I use Gnome Dialler to connect to Orange 3G via Bluetooth and a Nokia N95, and it's fine for that - using /dev/rfcomm0 as a port).

What fixed it for me was setting pppd to setuid to root, so that it always runs with root privs. That involved doing a:

```
sudo chmod +s /usr/sbin/pppd
```

Now it connects fine. No idea *what* it is that's requiring root level to operate, and I haven't the patience to try going through everything.

**However** I am also seeing the problem of the device just disappearing randomly, and needing replugging. Would love to see a fix for that one.

---

### Post by GeorgeVita on 2009-06-07
Hi, I would like to add a note:
ZTE modems when attached to the USB port, kernel/udev/hal (I don't know exactly) assigns at least 3 ports:
/dev/ttyUSB0 /dev/ttyUSB1 /dev/ttyUSB2 (and sometimes /dev/ttyUSB3)
assuming that there is NO other usbserial-ised peripheral. This behaviour is different if you boot with or without the modem attached.

The usable port for data communication is the highest (2 or 3) and the highest minus 2 (0 or 2), resulting to a connection via /dev/ttyUSB0 or /dev/ttyUSB2 when there is no /dev/ttyUSB3. If the last one exists you must use /dev/ttyUSB1 or /dev/ttyUSB3!

This is because the ZTE modems use other ports for firmware update or GPS interface and the designers choose this port numbering. The 2 usable ports are the one used for data (ppp) and the other used for telemetry (signal strength, volume of data traffic, etc).

Huawei modems usually attached as 3 ports: /dev/ttyUSB0 /dev/ttyUSB1 /dev/ttyUSB2
At Huawei modems the 2 first two (0,1) are for data and telemetry, both work to connect as with the ZTE but with the different numbering.

Most developers have access to Huawei or "like Huawei" modems. That's why they have debugged them. We (users of ZTE modems) must provide specific info to developers to help them solve our bugs (including usb modeswitch or other "tricks"). A modem must be pluged in and go. Rarely the modem manufacturer supplies technical info to developers.

In the case above where Network Manager assigns 2 set of provider, the possible good one is the last shown (2nd or 4th in my case!).

Regards,
George

EDIT: info about "Using ZTE MF636 with various UBUNTU versions" at:
[http://www.acomelectronics.com/GeorgeVita/ZTEonUBUNTU.html](http://www.acomelectronics.com/GeorgeVita/ZTEonUBUNTU.html)

---

### Post by dc2447 on 2009-06-16
I'm on Jaunty with the same symtoms as others, install udev-extras but get no icon on desktop etc

---

### Post by RickPJ on 2009-06-19
I've been wrestling with one of these on Jaunty for a few weeks now, and come to some interesting conclusions.

It has been working, but erratically in that sometimes it just does not want to make a connection - I think many people here have experienced this. It was getting so bad, including the symptom of the device spontaneously unmounting, that I thought it was a fault with the dongle and I got "3" to send me a new one under warranty. Guess what? the new one behaves exactly the same, so it's not the hardware.

I was using usb_modeswitch, but then I found AT+ZCDRUN and turned off the zero-CD mode permanently. That seems to have stopped the weird dismounts (also speeds up the device plug-in time), but the connection problem is no better.

To try to get a handle on things I've been playing with the raw ttyUSB devices, and this is where things are erratic. E.g. sometimes the output (responses to AT commands and unsolicited messages) has one blank line between items, sometimes three. Sometimes one port is detected as a modem, sometimes two. Sometimes when I send a command to the port it is echoed back in the output, sometimes not, etc.

The cause of this turns out to be the stty modes of the ttyUSB ports. They are not consistently initialised, presumably just picking up random settings. The single/triple blank line symptom depends on the value of icrnl. Whether the port is detected as a modem seems to depend on the echo flag (it should be off). Twiddling these setting once the port is created [ stty flags </dev/ttyUSBx ] can improve matters.

Should usbserial set known stty modes when it creates a port, or is it up to an application to set them? If the latter then should it be NM, or the "option" driver (which is what the ZTE actually seems to be)? Seeing that it affects how a port is detected, I guess they should be set pretty early on.

I'm sure that if the stty modes were set to a known state, then at least the behaviour would be consistent, and if there are other bugs it might be possible to identify them.

I'd file a bug report but I'm not sure where to direct it!

BTW, I sniffed out the modeswitch string that 3's Windows software uses to switch the device mode, and it's not the same as the 628+, which is what usb_modeswitch.conf tells you to use.

The actual string is: "55534243b8b79c822400000080000685000000240000000000000000000000"

This does switch the device, but as I've stopped using this anyway I don't know if it makes it any more stable.

Another BTW, I recommend enabling serial debug in NM, then you can see the conversation with the modem in the log. Add the line
export NM_SERIAL_DEBUG
to /etc/init.d/NetworkManager somewhere near the top.

I hope this is useful, and that the issue can be taken forward. I'm going to be away for a week and probably won't be able to follow this until I get back.

Cheers
Rick Jones

---

### Post by nickpiggott on 2009-06-22
Rick - it sounds like you're making really good progress, so I hope you're able to put a bit more time to this.

My symptoms are very similar to yours. Your theory about how the ttyUSBx devices are allocated to functions on the device rings true with me - I suspect  that NM is occasionally trying to communicate with the device down the telemetry channel (which *seems* to stream back a signal strength heartbeat, plus information on currently connected network) and that causes lots of fail.

I'm similarly frustrated, particularly when on the move - it can sometimes take 30-45 minutes to get a stable connection. It should work, but oh heck, it's a frustration now.

---

### Post by Sergiu Bivol on 2009-06-29
There are several layers that have to be fixed for ZTE modems to work in Ubuntu. It's way too hard to get them connected, so things need to improve.
I own a MF637 modem, and even in Karmic things are very bad. Sometimes it takes a lot of time to get the modem up and running.

We should report bugs for each component, to help the developers, so I suggest:

1) „/var/lib/misc/usb.ids” does not contain information about ZTE. This is the file that *lsusb* uses to tell us the device names.
The lines in bold have to be added:
```
19d2  ONDA Communication S.p.A.
     **2000  ZTE Virtual CD-ROM**
     **0031  ZTE MF6xx Broadband Modem**
```

2.a) the package *usb-modeswitch* has to be installed by default, with the appropriate configuration rules. There is a problem though: 19d2:2000 identifies **all** ZTE modems, but the sequences required to mode-switch each model are different.

2.b) in Karmic, ejecting the virtual CD device causes the proper driver to load for the modem, so adding to */etc/udev/rules.d/* a rule like:
```
SUBSYSTEM=="usb", SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000", RUN+="(command to eject the new /dev/srx)"
``` 
could do the trick. I'm afraid that this method is slower, as it has to wait for the CD-ROM device to settle before it can be ejected (however, I could be wrong).

3) In Kubuntu, plasma-widget-network-manager uses invalid settings when creating the connection file.
The appropriate file in „~/.kde/share/apps/networkmanagement/connections” should contain:
```
baud=0
mru=1440
mtu=1440
baud=0
bits=0
parity=
```
instead of its values for these parameters.

4) I experience frequent kernel oops's, and the system sometimes completely freezes ~10-20 times per day. This happens **only** when the modem is plugged in, so I suspect the „option” driver to be responsible.
Does anybody using ZTE modems get something like this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/386764](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/386764)

To check, please do: ```
cat /var/log/syslog | grep BUG:
```

---

### Post by RickPJ on 2009-06-30
I've spent a lot more time (too much!) poking and probing and come up with a much better idea of what's going on - and wrong - with these things, as well as some workrounds.

There are a number of issues.

1. Ports

The device has 3 serial ports on interfaces 0, 1, & 3 (interface 2 is the mass storage device). These are always assigned to ttyUSB* numbers 0, 1, & 2 respectively. ttyUSB0 is the NMEA port, ttyUSB1 is the monitor, and ttyUSB2 is the modem. However, after these ports are created, the system is inconsistent in deciding which is a modem, in particular, sometimes ttyUSB1 is seen as a second modem, and sometimes ttyUSB2 is not seen as a modem. There seem to be two stages - firstly a modem port is hooked by the "option" driver, then NetworkManager probes the ports to see if they behave as modems (presumably by sending AT commands).

This is why you sometimes get two connections listed in NetworkManager, when it thinks there are two modems, but if you try to use the one that's on ttyUSB1, chances are it won't connect.

I don't know how the system decides to use the "option" driver for a given port. I think this is handled by HAL, but I don't really understand HAL or how its config files work. When I originally got this device working on Hardy I had to add a .fdi file to get NM to see the device. I'm now on Jaunty, with a 2.6.29 kernel, and it turns out the .fdi file is no longer needed, but I can't find where the device is defined in the standard files.

I would have thought it should be possible to tell the system to only load the option driver for interface 3. This may help NM to see only ttyUSB2 as the modem.

2. tty modes

When the ports are first created, their tty modes are random. This is a major cause of erratic behaviour, and in some cases can crash the kernel. The device should have the settings that correspond to "stty raw". This can be tweaked by running the command "stty raw -F /dev/ttyUSB2" each time the modem is plugged in.

I think this is an omission in the option driver - it should set the modes as part of its initialisation. I also suspect this is related to why NM is inconsistent about whether it thinks ports are modems or not.

3. Unsolicited messages (UMs)

Both the modem and monitor ports continually stream +ZUSIMR:2 at 2 second intervals, and UMs cause a problem with AT commands. The response to an AT command should be interleaved with the UMs, but it turns out that to guarantee to get the response, you must start reading the port at least 2 secs. before sending the AT command. But modem AT drivers (including in NM) work by sending the command, then reading the response. This results in missed responses, and is the primary reason for NM failing to get an initialisation response to the modem, and hence unable to dial.

I haven't been able to find out what +ZUSIMR means, but it must be something to do with SMS, because if you issue any version of the AT+CPMS command, the stream of UMs stops permanently on both ports (until you plug the modem in again). As with setting the tty modes, this has a dramatic effect in making the modem reliable.

There are other UMs from time to time, mainly those that report the current network and connection mode (+ZDONR & +ZPASR). If you happen to attempt to connect at the moment the modem is issuing one of these then dialling will likely fail, but as these UMs aren't continuous a retry will usually work.

4. Timeouts

NM only allows 15 secs for ppp to establish a connection. This is after the transition from state 6->7 as seen in the log. This isn't always long enough, especially on roaming connections. Using the "3" network in the UK, its 2G fallback is a roaming connection on Orange, and this can be quite hard to connect to. Sometimes it connects after nearly 15 secs just before the timeout, so I think that if given more time it would be more sucessful. There doesn't seem to be any way to configure this externally.


5. An oddity

A couple of times the device has got into the state of being detected as 4 serial ports, and no mass storage device. This results in ttyUSB2 being assigned to interface 2 (which should be mass storage), and ttyUSB3 as the modem. I say "got into the state" because this persisted even after re-plugging the device and even re-booting Linux. Some time later it then behaved normally. Weird!


I've knocked up some scripts that help do the extra initialisation, and also support listing and selecting the network, and reading SMS messages. 
They are attached here (ZTE-scripts.tar), if you try them, please post your results.

There seem to be several areas that need cleaning up. The option driver certainly looks like one, but I'm sure more could be done with HAL to improve the initialisation. I just don't know enough about HAL to work this out :(

HTH

Cheers
Rick Jones

(edit - small update to scripts to improve usability)

---

### Post by Sergiu Bivol on 2009-06-30
Hi Rick!

> **RickPJ said:**
> 
1. Ports
...
This is why you sometimes get two connections listed in NetworkManager, when it thinks there are two modems, but if you try to use the one that's on ttyUSB1, chances are it won't connect.

This behaviour is reported by many users. On Kubuntu Karmic, I mostly get two modems listed, but sometimes it's only one (the right one, BTW).

> I don't know how the system decides to use the "option" driver for a given port. I think this is handled by HAL, but I don't really understand HAL or how it's config files work. When I originally got this device working on Hardy I had to add a .fdi file to get NM to see the device. I'm now on Jaunty, with a 2.6.29 kernel, and it turns out the .fdi file is no longer needed, but I can't find where the device is defined in the standard files.

Apparently, creating UDEV rules is the recommended approach, so HAL .fdi files are not needed any more (at least in Karmic, probably in Jaunty too).

> I would have thought it should be possible to tell the system to only load the option driver for interface 3. This may help NM to see only ttyUSB2 as the modem.

Looks like a bug that has to be reported.

> 
2. tty modes

When the ports are first created, their tty modes are random. This is a major cause of erratic behaviour, and in some cases can crash the kernel. The device should have the settings that correspond to "stty raw". This can be tweaked by running the command "stty raw -F /dev/ttyUSB2" each time the modem is plugged in.

Yay! I get tens of kernel crashes, and only when the *option* module is loaded.

> I think this is an omission in the option driver - it should set the modes as part of its initialisation. I also suspect this is related to why NM is inconsistent about whether it thinks ports are modems or not.

Bug?

> 
3. Unsolicited messages (UMs)

Both the modem and monitor ports continually stream +ZUSIMR:2 at 2 second intervals, and UMs cause a problem with AT commands. The response to an AT command should be interleaved with the UMs, but it turns out that to guarantee to get the response, you must start reading the port at least 2 secs. before sending the AT command. But modem AT drivers (including in NM) work by sending the command, then reading the response. This results in missed responses, and is the primary reason for NM failing to get an initialisation response to the modem, and hence unable to dial.

I haven't been able to find out what +ZUSIMR means, but it must be something to do with SMS, because if you issue any version of the AT+CPMS command, the stream of UMs stops permanently on both ports (until you plug the modem in again). As with setting the tty modes, this has a dramatic effect in making the modem reliable.

You are right, **+ZUSIMR: 2** means that the modem does not know where to store the SMS messages. I found that issuing the commands 
```
AT+CPBS="SM"\r\n
AT+CPMS="SM","SM",""\r\n

```
solve this problem until unplugging the modem. However, I cannot test them, since I do not get the +ZUSIMR messages. I believe this is because your operator locked the device. My ZTE MF637 modem is from Orange Moldova - they are very permissive in terms of network settings and the device does not appear to be locked.

Users of locked MF626 modems report that installing _[a new firmware]("http://forum.ixbt.com/topic.cgi?id=16%3A39216-41#1454")_ for the device solves the +ZUSIMR issue.

> There are other UMs from time to time, mainly those that report the current network and connection mode (+ZDONR & +ZPASR). If you happen to attempt to connect at the moment the modem is issuing one of these then dialling will likely fail, but as these UMs aren't continuous a retry will usually work.

Good point. Sometimes it just requires a second attempt in order to connect successfully.

> 
There seem to be several areas that need cleaning up. The option driver certainly looks like one, but I'm sure more could be done with HAL to improve the initialisation. I just don't know enough about HAL to work this out :(

We should gather as much useful info as possible and report bugs upstream. As users, this is the right thing to do.

Thank you for the excellent information! I will try your scripts and report back.

---

### Post by RickPJ on 2009-06-30
Hi, thanks for your comments.

> Apparently, creating UDEV rules is the recommended approach, so HAL .fdi files are not needed any more

I now understand that HAL is being obsoleted in favour of UDEV, so clearly udev is what needs looking at. I'll see if I can understand udev a bit better!

> +ZUSIMR:2 means that the modem does not know where to store the SMS messages.

Interesting. It's funny, but any +CPMS command will stop it, even just AT+CPMS, which is illegal and results in ERROR response - still stops +ZUSIMR !

> We should gather as much useful info as possible and report bugs upstream. As users, this is the right thing to do.

That's what I intend to do, I just need to work out where to report the different bugs :confused: !

Looking forward to hearing how you get on with the scripts.

Cheers, Rick

---

### Post by GeorgeVita on 2009-07-01
[COLOR="Blue"]STOP PRESS![/COLOR]
Just installed 9.10 (testing, updated 30-Jun-09), 2.6.30-10-generic and tried my ZTE MF636:
After plugged in, lsusb shows 19d2:2000
ZeroCD icon appeared, pop up window anounces Software...
I Eject it (from desktop environment)
the lsusb changed to 19d2:0031
two (2) providers found via network manager icon
I got connected from the 2nd one and ... Everything seems OK!
----- ----- -----
[COLOR="Red"]... and a newer update to kernel 2.6.31-1-generic broke it! The system got frozen![/COLOR]
We must be patient!
----- ----- -----

Hi, I would like to add the following notes (most are the same as yours):

My ZTE MF636 ( 19d2:0031 after AT+ZCDRUN=8 ) works with 9.04 after editing HAL info:

**sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi**
search (ctrl-F) for **19d2**, after line "<!-- ZTE MF628 HSDPA USB dongle -->" change "**usb.product_id**" from "0015" to "**0031**"

Reboot with the modem _attached_! Wizard configures 2 modems resulting to 4 "providers" and I am connecting sucessfully using the last one (another one is usable).

Trying with an RCx kernel I found that when udev fails the system tries the HAL info!

My opinion is that debugging must be done to a 'cleaner' Operating System (as 8.04) with less or no support of these modems. After determining what 'should be done' somebody must compare 'working' actions with the recent 'buggy' support.

If you would like to connect from one port and check/debug the other one (working on 8.04 with minicom) take a look at: [http://ubuntuforums.org/showpost.php?p=7443556&postcount=24](http://ubuntuforums.org/showpost.php?p=7443556&postcount=24)
With above test you can see the 3G/HSPA mode switching and try some commands such as AT+CSQ (GSM signal strength).

Finally: the modem will NEVER scramble its responds! The 'mess up' showing the 'echo' of your command and the periodic status report can be altered with the ATE0 (echo off). You may use lower case letters to control the modem and get UPPER case results (simple programming). Of course it is better to remove this 'auto reporting' with an AT command, but which one?

I thing that the problem can be solved from persons knowing the USB protocol. Determining the modem port (query? scanning?) a usbserial device must be created. For minimal support (connection only) only one port is enough. If scanning results to the same product other ports can be ignored. For ZTE the  default numbering starts from the end (ZTE comm port = last port)!
(... if vendorID=0x19d2 port# is MaxPort# else port#=0 ...)

Regards,
George

---

### Post by dc2447 on 2009-07-01
So - bring the modem to my other jaunty install, install udev-extras and I am up and running in < 30 seconds.

I can see no difference between my laptop (not working jaunty) and desktop (working jaunty)

I am going to push laptop to karmic...

---

### Post by GeorgeVita on 2009-07-02
Hi **aa52828**,
to help we have to know more technical info:
- exact ubuntu version
- model of modem
- from terminal try: **lsusb** (post here the output)
- which actions and what respond you had
Regards,
George

P.S. my MF636 stopped working with 9.10 (testing) after a kernel update!

---

### Post by dc2447 on 2009-07-02
> **dc2447 said:**
> So - bring the modem to my other jaunty install, install udev-extras and I am up and running in < 30 seconds.

I can see no difference between my laptop (not working jaunty) and desktop (working jaunty)

I am going to push laptop to karmic...Upgraded to Karmic and it works straight away

---

### Post by GeorgeVita on 2009-07-02
Hi **dc2447**,
do you have MF627 or other type of ZTE modem?
Is it working booting with it AND attaching after boot?
Also check from terminal: **uname -a**
and post here the kernel number!

Thanks,
George

---

### Post by dc2447 on 2009-07-02
> do you have MF627 or other type of ZTE modem?

MF627

> 
Is it working booting with it AND attaching after boot?

I haven't rebooted yet, I just tried unplugging the modem and reinserting the modem but although it mounts the volume network manager doesn't spring back into life when I unmount it :(

trying a reboot

> Linux d420 2.6.31-1-generic #13-Ubuntu SMP Fri Jun 26 16:53:22 UTC 2009 i686 GNU/Linux

althouh my jaunty desktop also works on 2.6.28-11

Update:

Reboot - modem won't work in karmic.

Put modem straight into Jaunty desktop, works first time and connects:

> ppp0      Link encap:Point-to-Point Protocol
          inet addr:10.212.28.2  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:146 (146.0 B)  TX bytes:185 (185.0 B)

So here is my kernel output from the latop, see the device get disconnected when I try and connect:

> Jul  2 13:09:42 d420 kernel: [ 2067.732097] usb 1-6: new high speed USB device using ehci_hcd and address 19
Jul  2 13:09:43 d420 kernel: [ 2067.876604] usb 1-6: configuration #1 chosen from 1 choice
Jul  2 13:09:43 d420 kernel: [ 2067.877998] scsi17 : SCSI emulation for USB Mass Storage devices
Jul  2 13:09:43 d420 kernel: [ 2067.878256] usb-storage: device found at 19
Jul  2 13:09:43 d420 kernel: [ 2067.878262] usb-storage: waiting for device to settle before scanning
Jul  2 13:09:48 d420 kernel: [ 2072.877643] usb-storage: device scan complete
Jul  2 13:09:48 d420 kernel: [ 2072.879586] scsi 17:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 0
Jul  2 13:09:48 d420 kernel: [ 2072.903729] sr0: scsi3-mmc drive: 0x/52x cd/rw xa/form2 cdda tray
Jul  2 13:09:48 d420 kernel: [ 2072.905946] sr 17:0:0:0: Attached scsi CD-ROM sr0
Jul  2 13:09:48 d420 kernel: [ 2072.907296] sr 17:0:0:0: Attached scsi generic sg1 type 5
Jul  2 13:10:01 d420 kernel: [ 2086.410301] UDF-fs: No VRS found
Jul  2 13:10:01 d420 kernel: [ 2086.410311] UDF-fs: No partition found (1)
Jul  2 13:10:38 d420 kernel: [ 2123.465845] usb 1-6: USB disconnect, address 19
Jul  2 13:10:43 d420 kernel: [ 2128.736193] usb 1-6: new high speed USB device using ehci_hcd and address 20
Jul  2 13:10:44 d420 kernel: [ 2128.878168] usb 1-6: configuration #1 chosen from 1 choice
Jul  2 13:10:44 d420 kernel: [ 2128.880690] option 1-6:1.0: GSM modem (1-port) converter detected
Jul  2 13:10:44 d420 kernel: [ 2128.880843] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
Jul  2 13:10:44 d420 kernel: [ 2128.881021] option 1-6:1.1: GSM modem (1-port) converter detected
Jul  2 13:10:44 d420 kernel: [ 2128.881138] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
Jul  2 13:10:44 d420 kernel: [ 2128.881422] scsi18 : SCSI emulation for USB Mass Storage devices
Jul  2 13:10:44 d420 kernel: [ 2128.881753] option 1-6:1.3: GSM modem (1-port) converter detected
Jul  2 13:10:44 d420 kernel: [ 2128.881923] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2
Jul  2 13:10:44 d420 kernel: [ 2128.882047] usb-storage: device found at 20
Jul  2 13:10:44 d420 kernel: [ 2128.882052] usb-storage: waiting for device to settle before scanning
Jul  2 13:10:47 d420 kernel: [ 2131.904141] CE: hpet increasing min_delta_ns to 22500 nsec
Jul  2 13:10:49 d420 kernel: [ 2133.881092] usb-storage: device scan complete
Jul  2 13:10:49 d420 kernel: [ 2133.882424] scsi 18:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Jul  2 13:10:49 d420 kernel: [ 2133.884780] sd 18:0:0:0: Attached scsi generic sg1 type 0
Jul  2 13:10:49 d420 kernel: [ 2133.900816] sd 18:0:0:0: [sdb] Attached SCSI removable disk
Jul  2 13:11:33 d420 kernel: [ 2178.000592] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Jul  2 13:11:33 d420 kernel: [ 2178.000642] option 1-6:1.0: device disconnected
Jul  2 13:11:33 d420 kernel: [ 2178.002721] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jul  2 13:11:33 d420 kernel: [ 2178.002756] option 1-6:1.1: device disconnected
Jul  2 13:11:33 d420 kernel: [ 2178.002863] option: option_instat_callback: error -108
Jul  2 13:11:33 d420 kernel: [ 2178.003010] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Jul  2 13:11:33 d420 kernel: [ 2178.003052] option 1-6:1.3: device disconnected
Jul  2 13:11:33 d420 kernel: [ 2178.112197] usb 1-6: reset high speed USB device using ehci_hcd and address 20
Jul  2 13:11:48 d420 kernel: [ 2193.224151] usb 1-6: device descriptor read/64, error -110


Edit2:

More annoying still, if I delete the APN from network manager - reinsert the mode, readd the APN... it connects first time

---

### Post by GeorgeVita on 2009-07-02
> I wonder if there is some type of issue with my laptop usb 

No, it is the same as with my netbook. I have not yet test a desktop but I think it is just "floating" as 9.10 is on development.

We (you other ZTE modem users and I) could test it after an Ubuntu 9.10 "milestone" as Alpha 3 and possibly report a bug to launchpad. Till then we must have a "typical" testing procedure. We must NOT involve in usb-modeswitch programming as this will be encapsulated to the kernel. My opinion is that we can just test various types of ZTE modems and conclude with the 'bug report'.

A 'typical' test procedure could be the one described at:
**[http://ubuntuforums.org/showthread.php?p=7550364](http://ubuntuforums.org/showthread.php?p=7550364)**

I think we must try before final release coming on October!

Regards,
George

---

### Post by RickPJ on 2009-07-02
More information ...

Via the NetworkManager developers mailing list, I've been in contact with one of the lead NM developers, and there are definite problems in the way these ZTE devices interact.

NM 0.7.1 (as in Jaunty, not sure about Karmic) probes any serial ports on the device using AT commands to find which is a modem. It tries to avoid choosing two ports on the same parent device, but it's slightly out of sync with the latest version of HAL so it's not working properly. This is why you often get two devices listed.

You can fix this by adding a .fdi file that restores the previous HAL behaviour, but the problem is that it's then random whether it chooses ttyUSB1 or ttyUSB2. They both appear to behave as modems, but only ttyUSB2 will actually make a connection, ttyUSB1 will just hang. (Strictly speaking these are USB interfaces 1 and 3, which normally get assigned to ttyUSB 1 & 2.)

I've found that it's best to let it possibly detect two devices, then work our which is the correct one to use (see my scripts below).

The NM people now understand the problem and are trying to produce a solution that isn't a horrible hack.

However, there are still other issues that result in erratic behaviour. Sometimes you can plug the device in and it will connect immediately, other times you'll be fighting it for ages.

The issues are the serial port modes (which I think is a bug in the "option" driver, I'm trying to work that one out), and the continuous +ZUSIMR:2 messages that the modem spits out - these can be stopped by sending an initialisation command to the modem.

See my earlier post #35, with scripts attached that work round these problems. They're not pretty, they run in a terminal window, but for now they do the job!

Cheers, Rick

---

### Post by dc2447 on 2009-07-02
I thought I had a reliable method of connecting.

* delete all apn
* plug in modem
* eject volume
* follow wizard

That worked at least five times in a row but now it doesn't.

Time to revisit unlocking my huawei

---

### Post by GeorgeVita on 2009-07-02
Hi again,
as **Sergiu Bivol** has already report to:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/386764](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/386764)

I think that I faced an "Oops" with kernel [B]2.6.30-10-generic #12-Ubuntu[
```
[  242.768726] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  242.768844] option 1-2:1.0: device disconnected
[  242.769752] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  242.769857] option 1-2:1.1: device disconnected
[  242.770004] option: option_instat_callback: error -108
[  242.770985] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  242.771094] option 1-2:1.3: device disconnected
[  242.880144] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  243.015049] option 1-2:1.3: GSM modem (1-port) converter detected
[  243.015398] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[  243.015520] option 1-2:1.1: GSM modem (1-port) converter detected
[  243.015733] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB4
[  243.015844] option 1-2:1.0: GSM modem (1-port) converter detected
[  243.016157] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB5
[  248.985672] BUG: unable to handle kernel NULL pointer dereference at 0000002b
[  248.985699] IP: [<c03da6d3>] usb_kill_urb+0x13/0xa0
[  248.985728] *pde = 7e5c7067 
[  248.985740] Oops: 0000 [#2] SMP 
[  248.985753] last sysfs file: /sys/devices/LNXSYSTM:00/device:00/ASUS010:00/rfkill/rfkill0/state
```

Above problem was reported by me at:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/373821](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/373821)

I am not sure if we can help by generating more 'bug reports' or just test and report somewhere how we manage it to work!
Also I do not know if developers have (physically) these modems to test them. If not we are ready to follow their instructions instead of trying blindly after every update!

Regards,
George

---

### Post by GeorgeVita on 2009-07-02
Hi **RickPJ**,
your post#35 ([http://ubuntuforums.org/showpost.php?p=7539275&postcount=35](http://ubuntuforums.org/showpost.php?p=7539275&postcount=35)) is very informative and of course is the result from your efforts to get the device working.

Can you confirm: Your scripts need a 'running' PC and can be used after creation of the ttyUSBx ports (after ejecting the 19d2:2000 drive).

As 9.10 is on development, do you feel it will help anyone doing tests with any pre-released version or we must just wait for the final release? If we can help doing tests, can you suggest a "typical" test procedure? My test procedure is on the link into my signature.

EDIT:> ...then NetworkManager probes the ports to see if they behave as modems (presumably by sending AT commands).
This is why you sometimes get two connections listed in NetworkManager, when it thinks there are two modems, but **if you try to use the one that's on ttyUSB1**, chances are it won't connect...

**For ZTE modems, if you make this test starting form the last port (ttyUSB3 or ttyUSB2) the result is always a connection!**
"*for modemport=0 to lastport*" works some times,
"*for modemport=lastport to 0*" works always!

Regards,
George

---

### Post by RickPJ on 2009-07-04
Hi George

Yes, you run the scripts after plugging in the modem. You can start running mblog at any time, but mbmgr will only work once the ttyUSB devices have been created.

I've avoided having to do the "eject" or usb-modeswitch by turning off ZeroCD mode using the AT+ZCDRUN=9 command. You can do this manually in minicom, or even with the command "echo -en 'AT+ZCDRUN=9\r' >/dev/ttyUSB2", and you only need to do it once. This makes things much simpler, and makes the device a lot quicker to start up.

The NetworkManager developers have made a fix to deal with the problem of using the correct port, and choosing only one. The update is on Launchpad BUT it has introduced a regression which means it fails to connect for a different reason. So don't use this update yet until the regression is fixed.

The second major problem is the issue of random ttyUSB port modes. This makes systematic tests very difficult, as behaviour is not always exactly repeatable. Just because you plug it in once and it works doesn't mean it will always work! Running my mbmgr script after the modem is plugged in works round this. I think the bug is in the "option" driver module but I'm trying to confirm this. I have also definitely linked this problem to kernel panics - i.e. if the port modes are correct you don't get crashes.

The final problem is stopping the modem outputting +ZUSIMR:2 all the time. This can be fixed with an extra initialisation command (again, mbmgr does this), but it's unlikely this can be integrated until we have NetworkManager 0.8 which introduces ModemManager as a separate entity. This allows for custom per-modem configurations etc.

Which version of NetworkManager is in Karmic at the moment?

Cheers, Rick

---

### Post by GeorgeVita on 2009-07-04
> **RickPJ said:**
> ...Which version of NetworkManager is in Karmic at the moment?

0.7.1-0ubuntu1 (karmic) on kernel 2.6.31-1-generic #14-Ubuntu

Thanks for above info,
George

---

### Post by Sergiu Bivol on 2009-07-05
> **RickPJ said:**
> I think the bug is in the "option" driver module but I'm trying to confirm this. I have also definitely linked this problem to kernel panics - i.e. if the port modes are correct you don't get crashes.


As far as i can tell, I get kernel panics **only** when the modem is connected. The *option* driver gives me headaches... There is something interesting in the panics I get lately.
kern.log shows:
```

...
Jul  5 15:32:58 dell kernel: [  196.988874] CR2: 0000000100000047 CR3: 0000000082916000 CR4: 00000000000026a0                
Jul  5 15:32:58 dell kernel: [  196.988878] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000                
Jul  5 15:32:58 dell kernel: [  196.988882] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400                
Jul  5 15:32:58 dell kernel: [  196.988887] **Process nm-modem-probe** (pid: 4240, threadinfo ffff8800828a8000, task ffff8800828759c0)                                                                                                                        
Jul  5 15:32:58 dell kernel: [  196.988890] Stack:                                                                           
Jul  5 15:32:58 dell kernel: [  196.988893]  00000044001280d2 0000004000000000 ffffe20001fdd648 ffff880082876070             
Jul  5 15:32:58 dell kernel: [  196.988899]  ffff8800828a9d18 ffffffff806da689 ffff880082cb6c00 0000000000000018             
Jul  5 15:32:58 dell kernel: [  196.988906]  ffff8800828a9d58 ffffffffa0525aeb ffff8800828a9d78 ffff880082cb6c00    
...

```

This happens immediately after plugging in the modem, and it appears that nm-modem-probe is the cause.

---

### Post by RickPJ on 2009-07-05
> **Sergiu Bivol said:**
> As far as i can tell, I get kernel panics **only** when the modem is connected. The *option* driver gives me headaches... There is something interesting in the panics I get lately.
kern.log shows:

This happens immediately after plugging in the modem, and it appears that nm-modem-probe is the cause.

I've made an experimental patch to the Option driver that sets up the port modes correctly right at the start. If my theory is correct, then this should stop the panics. I've attached the driver as a DKMS package so it will compile correctly for your kernel. You will need DKMS installed if it's not already (install with apt / synaptic), and you will also need the kernel headers (you probably have those anyway).

** I've subsequently concluded that this is not the problem (attachment removed). See later posts **

Cheers
Rick Jones

---

### Post by GeorgeVita on 2009-07-07
Hi, just for your info;
testing ZTE MF636 on Karmic kernel now is 2.6.31-2-generic #15-Ubuntu, when everything updated, trying to get /dev/ttyUSBx I ejected the drive. Most times this causes a "total froze" of my EeePC 1000H (some notes are in my previous posts). I removed network-manager from Synaptic, eject the drive but it reappeared after 15 seconds. Within this period I can see 19d2:0031 and use **wvdial** to connect in a very steady state! Some times I have to try 2 times the "sudo wvdial" command. But the system is always active!

My "wish" for the future remains to learn how to dismiss all 'buggy' mechanisms and use the old usbserial driver with the 'hard' wvdial!
 
Regards,
George

---

### Post by RickPJ on 2009-07-07
There is now a new version of NetworkManager available on the Launchpad site. This incorporates specific rules for ZTE modems to ensure that only the correct port is used. There are builds for Intrepid, Jaunty & Karmic, I've tested on Jaunty and it's a lot better.

Go here: [launchpad.net/~network-manager/+archive/ppa]("https://launchpad.net/~network-manager/+archive/ppa"), and follow the instructions for adding the repository and key. Then run Update Manager, and your NM should update automatically.

However, I found that sometimes it didn't detect a modem port at all, requiring the modem to be re-plugged. I've been looking at the nm-modem-probe program (part of NetworkManager), which is what actually does the detection.

I've patched this to make it initialise the modem better, this seems to be the problem area, not the option driver. I've attached a copy compiled for Jaunty for anyone who would like to try it.

Please update NM to the version above first, then try the attached nm-modem-probe. I don't know whether it will run on Karmic, but it's a simple program and shouldn't have specific kernel dependencies. You can test it in isolation first as follows:

Extract the program from the tar file to any convenient location.
Open a terminal session in the same directory.
Plug in the modem and wait for it to settle, but don't connect.
From the command line, run "./nm-modem-probe -v /dev/ttyUSBx" - where x is according to the number of your device's modem port (probably 2).
The output should show commands sent to the modem, and responses.

If you get this, it's working. If it's incompatible with the kernel you'll probably get nothing, or it will crash.

To install it, just copy into /lib/udev - save the existing one first so you can replace it if required.

Again, please post your results with either just the new NM, or with the nm-modem-probe update as well.

Cheers, Rick

---

### Post by GeorgeVita on 2009-07-07
> **RickPJ said:**
> There is now a new version of NetworkManager available on the Launchpad site. This incorporates specific rules for ZTE modems to ensure that only the correct port is used. There are builds for Intrepid, Jaunty & Karmic, I've tested on Jaunty and it's a lot better.

Go here: [launchpad.net/~network-manager/+archive/ppa]("https://launchpad.net/~network-manager/+archive/ppa"), and follow the instructions for adding the repository and key. Then run Update Manager, and your NM should update automatically.
...

Hi **RickP**, I tested only the above as it is very difficult to change the SIM from ZTE to the Huawei modem each time(or remove NM and connect again via wvdial!).

Tested N.M.0.7.1.git.4.364ab2f86-0ubuntu1~nm1 (karmic) on kernel 2.6.31-2-generic #16-Ubuntu with the same results! System is totally frozen some seconds after ejecting ZeroCD, just after the reappearance of this ZeroCD drive. An 'option driver' error also noted at dmesg.

As I have some other errors with Gdm making tries 'harder' and my pre-paid bandwidth is closer to my limit (every update is 30-150MBytes) I will wait for the Alpha 3 to do a clean install and use again the PPA version of N.M.

Thanks,
George

---

### Post by RickPJ on 2009-07-07
Hi George

I'm keeping away from Karmic until it's a bit more stable and nearer release!

Have you tried using AT+CDRUN=9 to turn off ZeroCD mode? That would reduce the amount of driver loading/unloading. It might not solve the problem, but it would determine if it's caused by "ejecting" the CD, or is purely a serial-USB problem.

Cheers, Rick

---

### Post by GeorgeVita on 2009-07-07
I think that **AT+ZCDRUN=8** turns off the ZeroCD and **AT+ZCDRUN=9** turns it on again.
([http://ubuntuforums.org/showpost.php?p=6511814&postcount=2](http://ubuntuforums.org/showpost.php?p=6511814&postcount=2))

At this time I am testing the modem to its original state 19d2:2000 (as bought). If you send the AT+ZCDRUN=8 it goes to 19d2:0031 and the problem is possibly easier. Also how can we send an AT command when the system has not created the /dev/ttyUSBx ports?

G

EDIT: I am running also a full updated 9.04 installation from SDHC card, but I am afraid to do more test on this 'full working' O.S.!

---

### Post by dc2447 on 2009-07-07
> **RickPJ said:**
> There is now a new version of NetworkManager available on the Launchpad site....

First, thanks for following this up.

I have upgraded NM and used your copy of nm-modem-probe

I can now connect every time.

I can now disconnect the modem, reattach and connect.

In summary, it works great.

Remaining issues for me are speed and making the modem auto connect.

> davidcam@d420:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu karmic (development branch)"
davidcam@d420:~$ uname -r
2.6.31-1-generic
davidcam@d420:~$ uname -a
Linux d420 2.6.31-1-generic #13-Ubuntu SMP Fri Jun 26 16:53:22 UTC 2009 i686 GNU/Linux
davidcam@d420:~$ dpkg-query -W network-manager
network-manager 0.7.1.git.4.364ab2f86-0ubuntu1~nm1


---

### Post by RickPJ on 2009-07-07
@George:
> I think that AT+ZCDRUN=8 turns off the ZeroCD and AT+ZCDRUN=9 turns it on again.
Correct, my typo!

Yes, there is a need to support the device as new, I was just hoping that this might be a way of finding where your problem was - even if you have to put the modem in another machine to send the AT command.

@dc2447:
> First, thanks for following this up.
I have upgraded NM and used your copy of nm-modem-probe
I can now connect every time.
I can now disconnect the modem, reattach and connect.
In summary, it works great.
No problem - I've been trying to get it working reliably for my own use for ages! Great to hear that the new NM works well, and that nm-modem-probe is compatible with Karmic.

Speed is generally a question of signal strength as well as the Carrier - they ration out the total bandwidth according to number of users etc.

I agree about auto-connect, it works sometimes, but usually not. When it does try to connect on plug-in I find it often fails, and needs manual retry anyway. I think this is because of status messages coming from the modem as it finds a network which confuse the dialling protocol. Can't win 'em all!

Cheers, Rick

---

### Post by Sergiu Bivol on 2009-07-16
It's been a while since the usb_modeswitch rules for udev do not work anymore in Karmic. Even running usb_modeswitch from the console gives errors most times ("could not claim interface").
The good news is that this program is not needed anymore. Just create a new file *ZTE.rules* under */etc/udev/rules.d*, containing: ```
SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"
```
Delete any usb_modeswitch rules you have.
This solves the "switching" part.

---

### Post by Sergiu Bivol on 2009-07-16
> **RickPJ said:**
> 
I've patched this to make it initialise the modem better, this seems to be the problem area, not the option driver. I've attached a copy compiled for Jaunty for anyone who would like to try it.


On Karmic, it works without updating NM. Your version of nm-modem-probe is more reliable.

However, I still get two modems listed...

NM info:
Architecture: amd64
Version: 0.7.1-0ubuntu1

---

### Post by RickPJ on 2009-07-16
> **Sergiu Bivol said:**
> On Karmic, it works without updating NM. Your version of nm-modem-probe is more reliable.

However, I still get two modems listed...

The NM fix to pick only one modem port is not in Karmic (yet). You still need the Launchpad update for that. Problem is that only one of those modems shown in NM will actually work - and you can only guess which one!

I've made some additional changes to nm-modem-probe, and it now really does seem 100% reliable (my previous version still sometimes failed to detect correctly). I'll post the update here soon.

Cheers, Rick

---

### Post by Sergiu Bivol on 2009-07-16
I have just discovered a funny (and useful) thing: *wvdial* is too smart for my ISP (Orange Moldova), and it waits for a prompt for ~20 seconds before starting *pppd*. Since the ISP is not [supposed to be] sending any, wvdial says: 
```
--> Carrier detected.  Waiting for prompt.          
--> Don't know what to do!  Starting pppd and hoping for the best.
```
So, adding **Stupid Mode = 1** to Dialer Defaults in *wvdial.conf* makes things much simpler - the program won't wait for the prompt and will start pppd immediately. 
As far as I can tell, this works great. NetworkManager does the same thing, starting pppd early.

---

### Post by RickPJ on 2009-07-17
> **Sergiu Bivol said:**
> I have just discovered a funny (and useful) thing: *wvdial* is too smart for my ISP (Orange Moldova), and it waits for a prompt for ~20 seconds before starting *pppd*.
I think this is common to all mobile providers. pppd was written to work with traditional dialup lines which would first see a *login* prompt from the remote server.

But with mobile modems, the pppd server is actually in the device, and the *99... dial string just fires up that pppd session. NM passes a plugin to pppd which handles the details of opening the connection, which is how it gets round this issue.

Cheers

---

### Post by gregnbanks on 2009-07-17
Sigh, this ZTE modem is really giving me the irrits.
 
Last week I followed the advice in this forum (thanks guys) to get my MF627 working on Jaunty.  I used "AT+ZCDRUN=8" from Windows to get around the USB mode switching issue.  With the PPA version of NetworkManager and Rick's binary of nm-modem-probe, everything started (mostly) working.  Sometimes it would take a couple of attempts, but usually a connection would Just Happen.
 
(I say mostly working because the modem would just die after about half an hour of use and require re-plugging.  This was very annoying but I could live with it).  
 
Then two days ago it stopped working.
 
There were two distinct stages of not working.  In the first stage, NetworkManager showed an available modem, but it would never connect when asked.  Syslog shows that it was consistently trying the wrong device (ttyUSB2 instead of ttyUSB1).  Experiment showed that nm-modem-probe was reporting thus:
 
ID_NM_MODEM_PROBED=1
 
for ttyUSB0 and ttyUSB2, and 
 
ID_NM_MODEM_PROBED=1
ID_NM_MODEM_GSM=1
 
for ttyUSB1.  During this stage, restarting NetworkManager using "/etc/init.d/NetworkManager restart" made the problem go away.  This was annoying, but at least I had a workaround.
 
Then yesterday it suddenly flipped into the next stage of not working.   Now NetworkManager shows no available modem device at all after plug-in.  Syslog shows that it has seen all the new ttyUSB* devices but thinks none of them have GSM capability.  Nm-modem-probe is still reporting correctly, AFAICS.  "udevadm info" shows that the udev database contains the right ID_NM_MODEM_* environment variables for the right devices.  I even wrote a shell script to replace nm-modem-probe and emit the above lines directly, still no joy.
 
So now what's wrong with it?  Any clues?

---

### Post by RickPJ on 2009-07-18
I've done another update to nm-modem-probe, as I found my first fix wasn't as reliable as I'd thought - or hoped.

The new version is attached. It's called nm-modem-probe.new just to differentiate - either rename it, or edit the udev rules file that invokes it.

In particular it makes sure the modem has properly settled before testing the capbilities. This actually takes around 8 secs. from when nm-modem-probe is invoked. The standard one only allows 6 secs before it gives up!

Some of the changes are ZTE-specific, so it may mess up if used with other modems. I shall submit this fix to the NM people when I've made these ZTE bits optional.

Let me know if this helps.

Cheers, Rick

---

### Post by Sergiu Bivol on 2009-07-18
> **RickPJ said:**
> Let me know if this helps.
Yay! It helps. I have tested: stopping the modem, starting a connection, suspending/resuming, and everything works good (lots of other bugs in various system layers are still making my life a hell, though :) ).

Tested with:
Kubuntu Karmic, NM 0.7.1-0ubuntu1, x86_64 (the default network-manager, NOT the one from PPA)
ZTE MF637

While still not perfect, your version is really a great improvement over the NM's default one.

Thank you!

---

### Post by GeorgeVita on 2009-07-18
Hi **Sergiu Bivol**,
at your test with the **MF637 on Kubuntu Karmic**, do you have the modem at the 'original state' (as bought 19d2:2000) or you have the ZeroCD off via AT+ZCDRUN=8 (19d2:00xx)? What is the actual productID for the MF637 (0031)?

Regards,
George

---

### Post by cyberram on 2009-07-19
Hi All,

I have the same problem, I went through almost all the posts in the thread to learn wat could make my ZTE MF627 modem working on my Ubuntu 9.04. I am a newbie to linux and wat to switch entirely to Linux. But this modem trouble is a big issue which keeps me switch back to windows. I really want to move out of windows and need your help.

I got it this modem from 3-Australia. I followed all the steps mentioned in the first post like installing the usb_modeswitch, creating usb_modeswitch.conf file and 999-zte.rules file. And the fdi file too. But I don't think my NM recognizes it still and I am not able to get it connected.

Here is a copy of my dmesg. 
[ 1766.316070] usb 2-4: new high speed USB device using ehci_hcd and address 2
[ 1766.462072] usb 2-4: configuration #1 chosen from 1 choice
[ 1766.811791] Initializing USB Mass Storage driver...
[ 1766.813395] usb-storage: device ignored
[ 1766.813451] usbcore: registered new interface driver usb-storage
[ 1766.813456] USB Mass Storage support registered.

And this is wat I get out of lsusb
Bus 002 Device 002: ID 19d2:2000  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I really need some help guyz. And I wanna contribute more to Ubuntu in future. Please help me out.

Thanks.

---

### Post by RickPJ on 2009-07-19
Hi cyberram

It looks like usb_modeswitch is not doing its work. Your device in lsusb is showing as 19d2:2000 - that's the initial CD-installer mode.

Try just running "sudo usb_modeswitch" at a shell prompt and see what happens. If it works then you should see the red light on the modem go out, and come back on again a few seconds later. Then lsusb should show 19d2:0031 (or 192d:something-not-2000).

If that doesn't work then you haven't got the right magic string enabled in usb_modeswitch.conf - re-check what you've done when configuring that file.

If it works then the .rules file is wrong and not invoking it properly when it's plugged in.

Unfortunately in Jaunty you can't use the eject-CD trick, because they deliberately disabled all known ZeroCD devices. That was a very bad idea, and has been taken out again in Karmic.

BTW you don't need the .fdi file in Jaunty, that's a hang-over from Intrepid where you do need it. You also don't need the entry in the .rules file that loads usb-serial, Jaunty has built-in recognition of the ZTE devices, once the mode has been switched.

HTH, Rick

---

### Post by Sergiu Bivol on 2009-07-19
> **GeorgeVita said:**
> Hi **Sergiu Bivol**,
at your test with the **MF637 on Kubuntu Karmic**, do you have the modem at the 'original state' (as bought 19d2:2000) or you have the ZeroCD off via AT+ZCDRUN=8 (19d2:00xx)? What is the actual productID for the MF637 (0031)?

Yes, the modem is as bought, with ZeroCD active (19d2:2000).
I have a simple udev rule (posted above) that ejects the CD-ROM when detected, thus switching the device to 19d2:0031.

There is no need for usb_modeswitch: the device understands the eject command and switches automatically (modeswitching is built in these devices). It works the same on Windows - inserting the modem without installing drivers gives you a CD-ROM device, which you can eject, and it switches to modem mode, exactly as it does on Linux.

---

### Post by Sergiu Bivol on 2009-07-19
> **cyberram said:**
> 
And this is wat I get out of lsusb
Bus 002 Device 002: ID 19d2:2000  


Run this command:
```
sudo update-usbids.sh
```

It updates the USB ID database, so that lsusb will display something more familiar, like: 
```

Bus 002 Device 021: ID 19d2:0031 ONDA Communication S.p.A. ZTE MF636
or
Bus 002 Device 022: ID 19d2:2000 ONDA Communication S.p.A. ZTE MF627/MF628/MF628+ HSDPA

```

It's purely informational, though.

---

### Post by gregnbanks on 2009-07-19
Rick: thanks, it seems to be working again (fingers crossed).  I actually used a shell script wrapper for your older nm-modem-probe to add an extra 8 seconds delay, and that seems to have cured it.

---

### Post by cyberram on 2009-07-22
Thanks RickPJ.

I think I am getting closer. I rechecked the conf file again and made some minor changes. Now when I connect my modem, the red light turns off and then comes up again. I suppose this means tht the usb_modeswitch is working.

But I am still missing the NM pop-up which was mentioned in the previous posts. I checked the lsusb and it shows 19d2:0064 instead of 19d2:2000. I think its because my modem is from Australia as mentioned by CCK on his post on March 15th 2009.

I checked the messages in dmesg. I see tht the MMC reader, which is build in the modem is detected. But the modem itself is not detected.

Do you have any idea of wats goin on????

---

### Post by cyberram on 2009-07-22
Thanks Sergiu Bivol.

Seems like the command u gave, needs internet. I will do it once I get my Internet working in Ubuntu :)

---

### Post by RickPJ on 2009-07-23
> **cyberram said:**
> I think I am getting closer. I rechecked the conf file again and made some minor changes. Now when I connect my modem, the red light turns off and then comes up again. I suppose this means that the usb_modeswitch is working.
Correct!
> But I am still missing the NM pop-up which was mentioned in the previous posts. I checked the lsusb and it shows 19d2:0064 instead of 19d2:2000. I think its because my modem is from Australia as mentioned by CCK on his post on March 15th 2009.
Try installing the Launchpad PPA build of NM. This has some special code added to deal with ZTE modems, which are a bit of a pain because all their models are slightly different from each other. You might also need my modified nm-modem-probe (above).

It sounds like you can't get onto the net via WiFi or ethernet - in which case you can download the deb file from launchpad (launchpad.net/~network-manager/+archive/ppa) using a different m/c or OS, then copy into Linux and run the file to install it.

I can't think of any other reason why it wouldn't work.

Cheers

---

### Post by GeorgeVita on 2009-07-23
Hi **jfernyhough**, **RickPJ**, **Sergiu Bivol** and any other that can help by **testing ZTE MF636 on Ubuntu 9.10 Alpha3** (or similar modem that has original state **19d2:2000** and changes to **19d2:0031** after ejecting it).

Please read my recent 'bad' results:
[http://ubuntuforums.org/showpost.php?p=7667091&postcount=4](http://ubuntuforums.org/showpost.php?p=7667091&postcount=4)
and propose any further test I can do.

As now I have the Alpha3 iso it is easy to format again and try any idea from a 'clean install' state.

Thanks in advance,
George

---

### Post by jonkirton on 2009-07-24
I'm using Netbook Remix.  Installed udev-extras but I don't see it mount on my desktop:(

---

### Post by RickPJ on 2009-07-25
> **jonkirton said:**
> I'm using Netbook Remix.  Installed udev-extras but I don't see it mount on my desktop:(
It didn't work for me either. I don't think you will ever get it to be seen in Jaunty unless you've got a non-standard kernel. There is some hard-coded stuff in the 9.04 USB layer that ignores all known ZeroCD device IDs.

I don't know who thought that was a good idea, but it's been taken out again in 9.10.

AFAIK usb-modeswitch is the only guaranteed way to flip the device in 9.04. IMO, the best thing to do once you've got the modem ports recognised is to send it the AT+ZCDRUN=8 command to permanently disable ZeroCD mode (use minicom, or even just echo in a shell prompt - e.g. echo -en AT+ZCDRUN=8\\r >/dev/ttyUSB2 )

---

### Post by jonkirton on 2009-07-25
Did the AT+ZCDRUN=8 on a windoze machine ( I cheated!)it now recognises the modem.  The linux software on the stick (again removed under windoze) seems to have installed and knows the modem is there.  Guess I just need to get the login and password from 3 now, it doesn't connect - yet.

---

### Post by RickPJ on 2009-07-25
> **jonkirton said:**
> Did the AT+ZCDRUN=8 on a windoze machine ( I cheated!)it now recognises the modem.  The linux software on the stick (again removed under windoze) seems to have installed and knows the modem is there.  Guess I just need to get the login and password from 3 now, it doesn't connect - yet.

I'm not convinced about the Linux s/w they include. It can certainly conflict with NetworkManager. NM should be able to handle the device itself, and is the easiest way to do it. But you need the Launchpad update to it, and preferably my nm-modem-probe as well.

There's no login or password, just the APN "3internet", and the default "dial" number *99#. If you add a mobile broadband connection in NM, you can just choose "3" from the carrier list and it will set it up correctly.

---

### Post by Jazzzeee on 2009-07-26
Hi All,

Will Ubuntu 9 be updated to run the MF627 modem automatically and if so any idea when.

I have tried to install it using the helpful instruction on this forum, but no joy.....  

I would love to say bye bye to Windows XP, but I am stuck with it until ubuntu is up dated.

Cheers,

Steve

---

### Post by RickPJ on 2009-07-26
> **Jazzzeee said:**
> Will Ubuntu 9 be updated to run the MF627 modem automatically and if so any idea when.

If Ubuntu 9.10 picks up all the current NM 0.7.1 fixes by the time it's released in October, then yes.

I don't know if there will be anything standard to automatically switch out of CD mode, but it should show up as a mounted device and be ejectable, which will switch it.

I've no inside knowledge though, just making na educated guess :)

Cheers

---

### Post by Jazzzeee on 2009-07-27
OK, I'll stick with windows for the next 2mths hoping that they do the fix.

Just an idea, is there a wifi router that I can run the MF627 through??? maybe this could be the answer???

[IMG]http://www.bablotech.com/wp-content/uploads/2009/01/windows-xp-nix-linux.jpg[/IMG]

:D:D

Steve

---

### Post by GeorgeVita on 2009-07-27
Hi **Jazzzeee**, why not trying some ideas step by step and manage it?

The first you can do is to boot Ubuntu (LiveCD or LiveUSB is OK) open a terminal window (Applications > Accessories > Terminal) and try: **lsusb**

Confirm that you found a line with **19d2 : 2000**

Then read the following and tell us if you understand and if you want to try:> ...I think that ZTE MF636 3G modem responds by default as an autorun CD drive or as the internal USB hub (**19d2:2000**) but we need the actual modem which selected after issuing the **AT+ZCDRUN=8** (then it responds **19d2:0031** on **lsusb** terminal command).

You can try the following steps:

1. on WinVista through control panel ADD the extra init command  **AT+ZCDRUN=8**
2. try to connect once with the providers s/w (WinVista)
3. remove the above command through control panel (WinVista)

**>>> IMPORTANT NOTE:** After issuing the above command you can use the modem for Windows and Ubuntu but you cannot install it to another Windows PC. To return the modem to its default condition you have to send **AT+ZCDRUN=9** following steps 1,2 and 3.

All the above are needed because there is no Hyperterminal into WinVista. You could also use a serial communication terminal program and send the command AT+ZCDRUN=8 directly to the port (comX) assigned for the ZTE MF636.
Regards,
George

---

### Post by Jazzzeee on 2009-07-28
Hi 

 Thanks for the kind offer.....   I am working 24/7 at present, if I get some time to my self I will have another go.

Steve
:D:D:D:D:D:D

---

### Post by JohnTheLutheran on 2009-07-29
I've managed (eventually!) to get my 3 UK modem working using NM 0.7.1 from Launchpad and the nm-modem-probe attached to an earlier message in this thread. So thanks to everyone who's contributed to this discussion - it's been a real help. 

However, I'm still having trouble with getting connected. Once I'm connected things seem to be fine, but it is taking numerous attempts to get connected successfully in the first place. This may be just an NM timeout issue (on which I've posted [separately]("http://ubuntuforums.org/showthread.php?t=1226018")) but I thought I'd post the logs here in case there is another problem. 

Here is the output I get in /var/log/daemon.log on an unsuccessful connection attempt: 

```
Jul 29 12:53:00 [computername] NetworkManager: <WARN>  init_done(): Modem initialization timed out 
Jul 29 12:53:00 [computername] NetworkManager: <info>  (ttyUSB2): device state change: 4 -> 9 (reason 28) 
Jul 29 12:53:00 [computername] NetworkManager: <debug> [1248868380.002683] nm_serial_device_close(): Closing device 'ttyUSB2' 
Jul 29 12:53:00 [computername] NetworkManager: <info>  Marking connection '3' invalid. 
Jul 29 12:53:00 [computername] NetworkManager: <info>  Activation (ttyUSB2) failed. 
Jul 29 12:53:00 [computername] NetworkManager: <info>  (ttyUSB2): device state change: 9 -> 3 (reason 0) 
Jul 29 12:53:00 [computername] NetworkManager: <info>  (ttyUSB2): deactivating device (reason: 0). 
Jul 29 12:53:00 [computername] NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Jul 29 12:53:00 [computername] NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
```

And here's what I get on a successful connection: 

```
Jul 29 12:53:07 [computername] NetworkManager: <info>  Activation (ttyUSB2) starting connection '3' 
Jul 29 12:53:07 [computername] NetworkManager: <info>  (ttyUSB2): device state change: 3 -> 4 (reason 0) 
Jul 29 12:53:07 [computername] NetworkManager: <info>  Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 29 12:53:07 [computername] NetworkManager: <info>  Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started... 
Jul 29 12:53:07 [computername] NetworkManager: <debug> [1248868387.416636] nm_serial_device_open(): (ttyUSB2) opening device... 
Jul 29 12:53:07 [computername] NetworkManager: <info>  Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete. 
Jul 29 12:53:07 [computername] NetworkManager: <info>  (ttyUSB2): powering up... 
Jul 29 12:53:07 [computername] NetworkManager: <info>  Registered on Home network 
Jul 29 12:53:07 [computername] NetworkManager: <info>  Associated with network: +COPS: 0,0,"3",2 
Jul 29 12:53:07 [computername] NetworkManager: <info>  Connected, Woo! 
Jul 29 12:53:07 [computername] NetworkManager: <info>  Activation (ttyUSB2) Stage 2 of 5 (Device Configure) scheduled... 
Jul 29 12:53:07 [computername] NetworkManager: <info>  Activation (ttyUSB2) Stage 2 of 5 (Device Configure) starting... 
Jul 29 12:53:07 [computername] NetworkManager: <info>  (ttyUSB2): device state change: 4 -> 5 (reason 0) 
Jul 29 12:53:07 [computername] NetworkManager: <info>  Starting pppd connection 
Jul 29 12:53:07 [computername] NetworkManager: <debug> [1248868387.864072] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute ttyUSB2 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/1 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so 
Jul 29 12:53:07 [computername] NetworkManager: <debug> [1248868387.866473] nm_ppp_manager_start(): ppp started with pid 7011 
Jul 29 12:53:07 [computername] NetworkManager: <info>  Activation (ttyUSB2) Stage 2 of 5 (Device Configure) complete. 
Jul 29 12:53:07 [computername] NetworkManager: <info>  (ttyUSB2): device state change: 5 -> 6 (reason 0) 
Jul 29 12:53:07 [computername] NetworkManager: <info>  (ttyUSB2): device state change: 6 -> 7 (reason 0) 
Jul 29 12:53:11 [computername] NetworkManager: <info>  PPP manager(IP Config Get) reply received. 
Jul 29 12:53:11 [computername] NetworkManager: <info>  Activation (ttyUSB2) Stage 4 of 5 (IP Configure Get) scheduled... 
Jul 29 12:53:11 [computername] NetworkManager: <info>  Activation (ttyUSB2) Stage 4 of 5 (IP Configure Get) started... 
Jul 29 12:53:11 [computername] NetworkManager: <info>  Activation (ttyUSB2) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jul 29 12:53:11 [computername] NetworkManager: <info>  Activation (ttyUSB2) Stage 4 of 5 (IP Configure Get) complete. 
Jul 29 12:53:11 [computername] NetworkManager: <info>  Activation (ttyUSB2) Stage 5 of 5 (IP Configure Commit) started... 
Jul 29 12:53:13 [computername] NetworkManager: <info>  (ttyUSB2): device state change: 7 -> 8 (reason 0) 
Jul 29 12:53:13 [computername] NetworkManager: <info>  Policy set '3' (ppp0) as default for routing and DNS. 
Jul 29 12:53:13 [computername] NetworkManager: <info>  Activation (ttyUSB2) successful, device activated. 
Jul 29 12:53:13 [computername] NetworkManager: <info>  Activation (ttyUSB2) Stage 5 of 5 (IP Configure Commit) complete.
```

Any suggestions gratefully received...

---

### Post by RickPJ on 2009-07-29
Hi John

It's pretty normal for the device to fail to connect first time, and sometimes 2nd & 3rd times. The problem is that as the modem finds the network it spews out messages giving the network id etc. NM ignores these because it doesn't need them, but they seem to block the modem's response to the initialisation commands that NM sends. Once the modem has settled and the messages have been flushed out, then it connects OK.

You can see more of what's going on in the log by adding this line to /etc/init.d/NetworkManager:

export NM_SERIAL_DEBUG=1

Edit the file under sudo, and add this line near the top, after the block of comments. Then run:

sudo /etc/init.d/NetworkManager restart

You'll then see in the log the full conversation between NM and the modem as it initialises and dials.

I'm hoping there will be a way for NM to deal with this problem, but I suspect if there is it won't be until 0.8.

HTH, Rick

---

### Post by cyberram on 2009-07-31
Hey Rick,

Sorry mate. I used to do these things only from a free wireless point near my home. I hav been busy for sometime. Thts y it took me so long to try it.....

Anyway I tried to update with the ppa-network-manager through the link u gave. Unfortunately, the keyserver doesn't seem to work.[BC8EBFE8]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0x8B6C49916FD28CBDFC5DA3A2248DD1EEBC8EBFE8&op=index") this is the key right.....

I am getting an error when i use the sudo apt-key utility.

I also tried to open the keyserver.ubuntu.com and its not reachable. :(

wat should I do now?????

---

### Post by GeorgeVita on 2009-07-31
Hi **cyberram**, just for your info I just test and configured the use of N.M. PPA following instructions from the page that **RickPJ** mentioned:
[https://launchpad.net/~network-manager/+archive/ppa](https://launchpad.net/~network-manager/+archive/ppa)

System >Administration > Software Sources > Third-Part Software > Add
```
deb http://ppa.launchpad.net/network-manager/ppa/ubuntu karmic main
```
Add 2nd:
```
deb-src http://ppa.launchpad.net/network-manager/ppa/ubuntu karmic main
```

and from terminal:```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BC8EBFE8
```

You must have a working internet connection.
Check above with your actions.

Regards,
George

---

### Post by RickPJ on 2009-07-31
Hi cyberram

> **cyberram said:**
> Anyway I tried to update with the ppa-network-manager through the link u gave. Unfortunately, the keyserver doesn't seem to work.[BC8EBFE8]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0x8B6C49916FD28CBDFC5DA3A2248DD1EEBC8EBFE8&op=index") this is the key right.....
That's the one.
> I am getting an error when i use the sudo apt-key utility.

I also tried to open the keyserver.ubuntu.com and its not reachable. :(
This is the command to use for apt-key:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com BC8EBFE8

I've just re-tried that and there's no problem. That command will work for any launchpad key, just use the appropriate key-id.

You can't open keyserver.ubuntu.com in a browser on the default port, but [http://keyserver.ubuntu.com:11371](http://keyserver.ubuntu.com:11371) will give you the home page with manual search.

If you were doing all that it might just have been that the keyserver was down when you tried it.

Cheers.

---

### Post by dc2447 on 2009-08-01
Just a quick update to say that everything works great on Karmic still, even after all the updates

---

### Post by wild_oscar on 2009-08-19
**SOLUTION**

I couldn't make it work with the instructions on the 1st page.

However, I got it working on **Jaunty** with the instructions at [http://www.greenhughes.com/content/zte-mf627-easy-way](http://www.greenhughes.com/content/zte-mf627-easy-way)

Basically, it's a 30 sec procedure of adding a PPA location and 

sudo apt-get install zte-mf627-switch


Kudos for Liam Green-Hughes for providing the solution!

---

### Post by Jazzzeee on 2009-08-19
Hi all

I managed to pick up a second hand modem ZTE MF622  works fine without changing any of the settings.

Steve

---

### Post by Andysan on 2009-08-25
Hi all,

I've installed Liam Greens fix via the PPA on his blog (thanks man if you're reading) on my Jaunty desktop machine and can confirm that all works well.

I've done the same on my Intrepid laptop running 2.6.27-9-generic and when i run the following:

```
sudo sh zte_mf627_switch
```

I get the following:

```
...
No devices in target mode or class found
...
Found default devices (1)
...
No driver found.  Either detached before or never attached
...
Sending the message returned error -2
```

(Note that i've omitted a few standard lines as i am typing each line out - can supply if necessary).

lsusb then returns the following:

```

Bus 001 Device 003:  ID 19d2: 2000

```


So essentially the modem isn't switching modes.  I've happily browsed the web using my dongle in Jaunty, just not on my Intrepid laptop.  Anybody have any ideas please?

Thanks.

---

### Post by Andysan on 2009-08-25
> **Andysan said:**
> Hi all,

I've installed Liam Greens fix via the PPA on his blog (thanks man if you're reading) on my Jaunty desktop machine and can confirm that all works well.

I've done the same on my Intrepid laptop running 2.6.27-9-generic and when i run the following:

```
sudo sh zte_mf627_switch
```

I get the following:

```
...
No devices in target mode or class found
...
Found default devices (1)
...
No driver found.  Either detached before or never attached
...
Sending the message returned error -2
```

(Note that i've omitted a few standard lines as i am typing each line out - can supply if necessary).

lsusb then returns the following:

```

Bus 001 Device 003:  ID 19d2: 2000

```


So essentially the modem isn't switching modes.  I've happily browsed the web using my dongle in Jaunty, just not on my Intrepid laptop.  Anybody have any ideas please?

Thanks.

As a last resort I tried the above using the custom Acer Aspire One 2.6.28 kernel and suprisingly everything works perfectly.  Confused.:confused:

---

### Post by freddy.junior on 2009-08-28
Hi all, I've tried to use a ZTE MF627 with "3" (Tre) Italia on my Ubuntu 9.04 but had no luck.

I tried both the way of Liam Greens and the one of original poster. I also had to change all the references from product id 0031 to 0064 (and int="3" to "2") as CCK suggested (it seems that italian modems have the same hardware of the australian ones...).

Now, when I plug in the modem a red light appears, then blank, then red again and finally green. But network manager 0.7.1 doesn't pop up the connection wizard.

Following are some logs.

lsusb:
```

Bus 001 Device 013: ID 19d2:0064 ONDA Communication S.p.A. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

dmesg:
```

[ 3498.360020] usb 1-2: new high speed USB device using ehci_hcd and address 12
[ 3498.506273] usb 1-2: configuration #1 chosen from 1 choice
[ 3498.507897] usb-storage: device ignored
[ 3504.297785] usb 1-2: USB disconnect, address 12
[ 3509.368022] usb 1-2: new high speed USB device using ehci_hcd and address 13
[ 3509.511375] usb 1-2: configuration #1 chosen from 1 choice
[ 3509.512973] usbserial_generic 1-2:1.0: generic converter detected
[ 3509.513092] usb 1-2: generic converter now attached to ttyUSB0
[ 3509.513737] scsi12 : SCSI emulation for USB Mass Storage devices
[ 3509.514278] usbserial_generic 1-2:1.2: generic converter detected
[ 3509.514346] usb 1-2: generic converter now attached to ttyUSB1
[ 3509.514941] usb-storage: device found at 13
[ 3509.514944] usb-storage: waiting for device to settle before scanning
[ 3514.513401] usb-storage: device scan complete
[ 3514.515627] scsi 12:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[ 3514.557222] sd 12:0:0:0: [sdb] Attached SCSI removable disk
[ 3514.557343] sd 12:0:0:0: Attached scsi generic sg2 type 0

```

What's going wrong ?

---

### Post by mo.reina on 2009-10-09
i managed to get the zte working on ubuntu 8.10 but besides following all the instructions above, i have to type in this additional command to make network manager recognize the modem, otherwise i just get the autorun from the usb modem that tries to install the windows drivers.

```
sudo modprobe usbserial vendor=0x19d2 product=0x0031
```

essentially i have to plug in the dongle, enter the above command, remove the dongle, then plug it in again.  after this network manager will recognize it and allow me to connect.  otherwise like i said above i just get the autorun script and usb icon appears on my desktop, but network manager can't access it.

anyone have any idea on why this happens?

---

### Post by Andysan on 2009-10-09
> **mo.reina said:**
> i managed to get the zte working on ubuntu 8.10 but besides following all the instructions above, i have to type in this additional command to make network manager recognize the modem, otherwise i just get the autorun from the usb modem that tries to install the windows drivers.

```
sudo modprobe usbserial vendor=0x19d2 product=0x0031
```

essentially i have to plug in the dongle, enter the above command, remove the dongle, then plug it in again.  after this network manager will recognize it and allow me to connect.  otherwise like i said above i just get the autorun script and usb icon appears on my desktop, but network manager can't access it.

anyone have any idea on why this happens?

Hi,

The ZTE dongle when plugged into a PC can operate in two modes; the first is as a USB mass storage device whereby it simply presents itself as a disk with Windows drivers on.  The second mode is where it makes itself accessible as a modem.  Under Windows the modem will make itself available in the first mode to install the drivers and then switch to the second mode to operate as a modem, but this doesnt quite work under Linux.

The code that you are using:

```
sudo modprobe usbserial vendor=0x19d2 product=0x0031
```

Is loading the usbserial module into the kernel so that the dongle can be recognised, then **the usb_modeswitch command can flick it from mass storage mode into modem mode so that it can operate as a modem** (thanks for correcting me on that mo.reina!).  In the above command, the vendor ID is the unique ID of the manufacturer (Huwaei) and the product ID, well the product ID.:)

When you run this line of the code Ubuntu can recognise the hardware and then your script containing the usb_modeswitch command will knock it into modem mode, and thus Network Manager can dial it.  More or less anyway.:)

You can run this code automatically everytime you boot your PC/laptop if you like by editing the modules.conf file.  **EDIT - I've just checked and on my Intrepid install this is just called "modules" - no extension.**  You may wish to backup this file first.  From a terminal run:

```
sudo cp /etc/modules.conf  /etc/modules.conf.bak
```  

To backup the file, now to edit it:

```
gksudo gedit /etc/modules.conf
```

Enter your password and a text file should open probably with some stuff already in it (if not check that you entered the above code correctly).

At the end, on a new line add the following:

```
usbserial vendor=0x19d2 product=0x0031
```

This is fine, but I would recommend adding a comment on the line above, which can be done with a hash, such as this:

```

#Driver for Huwaei ZTE MF627 3G Modem
usbserial vendor=0x19d2 product=0x0031

```

Save, close, reboot and test!

---

### Post by mo.reina on 2009-10-09
shouldn't the usb_modeswitch make the usb function as a modem instead of a storage device?

this is my /etc/usbmodeswitch.conf

```
########################################################
# ZTE MF628+ (tested version from Telia / Sweden)
#
# Contributor: Joakim Wennergren
#
# Also applies to MF627 (Tested 3 UK) JF

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0031

MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
```

---

### Post by Andysan on 2009-10-09
Sorry, yeah, I remember now.  You are indeed correct, but you still need the relevant module loaded into the kernel before you can do that, and thats what the [modprobe ]("http://linuxcommand.gds.tuwien.ac.at/man_pages/modprobe8.html")command does.

```
sudo modprobe usbserial vendor=0x19d2 product=0x0031
```

Sorry if i confused you, I have been out of the dongle loop for a while and didnt explain myself too well.  Modprobe used first to recognise the dongle and modeswitch to flick it into modem mode.

:guitar:

---

### Post by mo.reina on 2009-10-09
that worked perfectly.  last question, just curious but should that addition to the modules file be added to the this guide or is it just my unit that's playing hokey.

---

### Post by RickPJ on 2009-10-10
> **mo.reina said:**
> that worked perfectly.  last question, just curious but should that addition to the modules file be added to the this guide or is it just my unit that's playing hokey.
The modprobe is only required with 8.10 (or earlier). 9.04 onwards has recognition of the ZTE device ids built-in, so usbserial is loaded automatically.

Somewhere earlier in this thread I posted some files for 8.10, which includes a udev rules file that runs modprobe when the device is plugged in. That seemed the cleanest way to do it.

---

### Post by Swagman on 2009-10-10
Upgraded to Karmic.

3 Dongle now works perfectly

---

### Post by toasty525 on 2009-10-13
I have my ZTE MF627 dialing and connecting to the 3G service with no problems but the modem keeps turning off completley and dosnt show up in lsusb every hour or so and i then have to unplug it and plug it back in to get it working again....

Any ideas what is cuasing this ?

Thanks,
Mark H.

---

### Post by nickpiggott on 2009-10-13
I recently flashed my stick to the generic firmware, and written a small script to send AT+COPS=0,0 (to force it to find 3, rather than keep wandering off to Orange GPRS). Those two things seem to have dramatically improved the performance, and it seems to hold connections more persistently. It's not perfect, but it's much better.

However, I'm also seeing the problem of the stick going completely dead (apparently losing power) after an hour or so of continuous use. dmesg reveals nothing helpful other than the usb subsystem saying it's disconnected, so I'm assuming it's just the stick blowing out? Pulling it out and putting it back in again resolves it.

It's annoying that I can't find where the modem init commands are sent by NM, so that I can manually add the AT+COPS=0,0 commands...

---

### Post by mo.reina on 2009-10-14
what are the commands to connect through the terminal?  i removed NM, now using wicd

---

### Post by funqshun on 2009-10-27
Hello,

I'm on Karmic. I've the suggestions here and my dongle still does not work.

Here is my lsusb:

Bus 001 Device 010: ID 19d2:0064 ONDA Communication S.p.A. 
Bus 001 Device 002: ID 04b3:4482 IBM Corp. Serial Converter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

What do I do on Karmic?

---

### Post by liamgh on 2009-11-01
I've been working on my config package for the ZTE MF627 again to get it working properly in Karmic, a friend kindly lent me the device for a week so I could work with it. You'll need to install it from my PPA (instructions at: [http://www.greenhughes.com/ppa](http://www.greenhughes.com/ppa)).

This package should also work on Intrepid/8.10 as well, I've put in an extra bit in the script to load up usbserial as required.

Hope this helps!

---

### Post by useopenstupid on 2009-11-08
I am using karmic, I am on the three mobile network in UK, I have a SKYPE S2 mobile phone and a ZTE MF627 HSDPA USB dongle

I followed the above the instructions above and got my ZTE modem working straight away, I am currently swapping my sim card between my phone and modem but I would like to use my phone as a USB modem but I am unable to figure out how to get it to work via USB 

how can I get the SKYPE S2 mobile phone working as a USB modem?

peter@HP-dv6000-Ubuntu:~$ lsusb
Bus 004 Device 009: ID 1614:0407 Amoi Electronics 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 19d2:0031 ONDA Communication S.p.A. 
Bus 002 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

cheers

---

### Post by useopenstupid on 2009-11-08
I am using karmic, I am on the three mobile network in UK, I have a SKYPE S2 mobile phone and a ZTE MF627 HSDPA USB dongle

I followed the above the instructions above and got my ZTE modem working straight away, I am currently swapping my sim card between my phone and modem but I would like to use my phone as a USB modem but I am unable to figure out how to get it to work via USB 

how can I get the SKYPE S2 mobile phone working as a USB modem?

peter@HP-dv6000-Ubuntu:~$ lsusb
Bus 004 Device 009: ID 1614:0407 Amoi Electronics 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 19d2:0031 ONDA Communication S.p.A. 
Bus 002 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

cheers

---

### Post by cataztrophe on 2009-11-13
wow,,, thnx for this info!! really need this!!
anyway, if i wanna connect it with gammu, is it posible?
or gammu doesnt support this modem??
and another Question is, is this modem GSM/CDMA?
thnx a lot! :D

---

### Post by Lomnar on 2009-11-23
Hi folks!

I have a MF627 modem as well, and Ubuntu 9.10. But I have not the "LINUXFILES" on my dongle as Pablo180 and cresswell has.

> I received the ZTE MF627 today from 3 UK, the customer service people and technical support all told me it worked on Linux but I was a little sceptical. 

Amazingly I plugged it in and it does have Linux drivers on the USB drive - and they work in Ubuntu!

From where can I download the file 3UK_PC_LinuxUI.tar.gz or the "Linuxfiles" directory, because I did not find them on the ZTE's webpage neither.

Thanks

---

### Post by volaer on 2009-12-21
> **jfernyhough said:**
> **Updated**
With Jaunty this is now not necessary and there is an easier way around. First, install udev-extras:

$ sudo aptitude install udev-extras

Depending on if/when my patch* gets accepted you will likely need to add information about the modem to the HAL infomation:

$ sudo cp /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi /etc/hal/fdi/information/
$ gksudo gedit /etc/hal/fdi/information/10-modem.fdi

Add the following:
```
        <!-- ZTE MF627 HSDPA USB dongle -->
        <match key="@info.parent:usb.product_id" int="0x0031">
          <match key="@info.parent:usb.interface.number" int="3">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
          </match>
        </match>

```
and save the file.

Now plug in your modem. It should mount as the ZeroCD device (1). Now right-click the icon on the desktop and eject. Wait a moment, and the light on the modem will go dark, then relight red then green. It should now mount as a modem and be detected by Network Manager (2).

A note should be made about udev-extras, though:YMMV.

1)lsusb:```
ID 19d2:2000 ONDA Communication S.p.A.
```
2)lsusb:```
ID 19d2:0031 ONDA Communication S.p.A.
```

*
[https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/407679](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/407679)
########

I recently bought a 3G mobile broadband modem and then realised I'd bought the wrong model - instead of getting a Huawei E160 or E169 that reportedly work OOTB with Intrepid I got a ZTE MF627 for which no information exists. On the plus side, it has a built-in MicroSD reader...

I initially submitted a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/310025"). Since then, however, I have got it working and so here is a how-to. I hope someone else finds this useful. :D

**1) Download and install usb_modeswitch**

Go [here]("http://www.draisberghof.de/usb_modeswitch/#download") and download the deb file. A direct link is [here]("http://www.draisberghof.de/usb_modeswitch/usb-modeswitch_0.9.5_i386.deb"). Then install it.

This provides a way of switching the USB modem from its initial useless mode to its correct, functional modes. It will need configuring to apply to the modem.

**2) Edit /etc/usb_modeswitch.conf to apply to the MF628+**

Either comment the first modem configuration out, then find and uncomment the section for the MF628+, or (more easily) replace the content of the file with:

```
########################################################
# ZTE MF628+ (tested version from Telia / Sweden)
#
# Contributor: Joakim Wennergren
#
# Also applies to MF627 (Tested 3 UK) JF

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0031

MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
```Save it.

**3) Create a udev rule to automatically run usb_modeswitch when the modem is plugged in**

Create a new file called 999-zte-rules:
gksudo gedit /etc/udev/rules.d/999-zte.rules

Its content should be as follows:
```
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", RUN+="/usr/sbin/usb_modeswitch"
```This will trigger usb_modeswitch every time you plug in the modem. Which is useful if you want it to work automatically. You can of course run it manually if you want.

**4) Add device information to HAL so network-manager recognises the device as a modem**

Finally, in order for Network Manager to recognise the modem information has to be added to HAL.

Create a new file:
gksudo gedit /usr/share/hal/fdi/information/20thirdparty/20-zte-mf627.fdi

Its content should be as follows:
```
<!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
      <!-- ZTE MF627 HSDPA USB dongle -->
      <match key="@info.parent:usb.vendor_id" int="0x19d2">
        <match key="@info.parent:usb.product_id" int="0x0031">
          <match key="@info.parent:usb.interface.number" int="3">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
            <append key="info.capabilities" type="strlist">modem</append>
          </match>
        </match>
      </match>
  </device>
</deviceinfo>
```Save it.

**5) Plug in the modem**
Make sure the SIM card is in the modem (and if you're using 3 UK make sure you're in a 3G area. otherwise it won't work) and plug it into your PC.

After a little while (several seconds) the LED should light red as it powers up, then switch to blue when it finds a network. You can check it's working by checking dmesg. Once modeswitch has been triggered and the modem reboots you will be presented with the ZeroCD device (e.g. containing the 3connect software), a USB MicroSD card reader, and if everything has gone correctly, Network Manager will detect a new mobile broadband modem.

Feel free to ignore the ZeroCD device and unmount it from the desktop.

If everything has gone correctly dmesg should read something like:
```
[52189.029694] usb 5-1: new high speed USB device using ehci_hcd and address 32
[52189.177064] usb 5-1: configuration #1 chosen from 1 choice
[52189.192061] usb-storage: device ignored
[52194.546308] usb 5-1: USB disconnect, address 32
[52200.032140] usb 5-1: new high speed USB device using ehci_hcd and address 33
[52200.183440] usb 5-1: configuration #1 chosen from 1 choice
[52200.184979] option 5-1:1.0: GSM modem (1-port) converter detected
[52200.185184] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
[52200.185453] option 5-1:1.1: GSM modem (1-port) converter detected
[52200.185592] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
[52200.200858] scsi28 : SCSI emulation for USB Mass Storage devices
[52200.204904] usb-storage: device found at 33
[52200.204909] usb-storage: waiting for device to settle before scanning
[52200.205113] option 5-1:1.3: GSM modem (1-port) converter detected
[52200.205304] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB2
[52205.205580] usb-storage: device scan complete
[52205.207696] scsi 28:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[52205.210603] scsi 28:0:0:1: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[52205.226669] sd 28:0:0:0: [sdb] Attached SCSI removable disk
[52205.228914] sd 28:0:0:0: Attached scsi generic sg2 type 0
[52205.345654] sr1: scsi-1 drive
[52205.345837] sr 28:0:0:1: Attached scsi CD-ROM sr1
[52205.346023] sr 28:0:0:1: Attached scsi generic sg3 type 5
[52218.692468] ISO 9660 Extensions: Microsoft Joliet Level 1
[52218.699732] ISOFS: changing to secondary root
```

References:
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)
[http://blog.ufsoft.org/2007/11/30/zte-mf622-usb-modem-under-linux](http://blog.ufsoft.org/2007/11/30/zte-mf622-usb-modem-under-linux)
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/267727](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/267727)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/259028](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/259028)
[https://answers.launchpad.net/ubuntu/+source/network-manager/+question/48520](https://answers.launchpad.net/ubuntu/+source/network-manager/+question/48520)
Probably some others I've forgotten.



Hey you all!!!  

I just want to share this....
I am using a Smart Broadband USB Model: ZTE MF 627. I worked for so many hours but haven't get it. 

Finally I found this post on a blog and I got my broadband working great. 

So, here's the link to the post. Hope you'll also enjoy your broadband:

[http://knightlust.blogspot.com/2009/06/smartbro-zte-mf627-on-ubuntu-jaunty.html](http://knightlust.blogspot.com/2009/06/smartbro-zte-mf627-on-ubuntu-jaunty.html)


Enjoy!!!

---

### Post by volaer on 2009-12-25
Hello guys, I just want to ask a question. I have ZTE MF-627. I was able to activate it. However, with the solutions posted that I tried to follow in the earlier post of this thread, my laptop booting up went up very slow. Before it only takes me 15-20 seconds of booting time, now it takes me 3-4 minutes booting time. Any solutions my friends?

---

### Post by ChrisinNorway on 2010-05-03
Hi,

I'm trying to get ZTE MF636 to be connectable under Ubuntu 9.10 and have observed and performed your suggested installs and additions to the configuration files. Alas I still have a stable red light and no recognition as amodem by the NM app.Regarding the .fdi file, I am not experienced to know the significance of the statement 
<match key="@info.parent:usb.interface.number""int=3". Can you please explain.
I am connecting from  Norway and I was wondering if this has a bearing on the value to be set.

Regards
Chris

---

### Post by GeorgeVita on 2010-05-04
Hi **ChrisinNorway**,
MF636 will or not ( ! ) work directly with Ubuntu 9.10 and 10.04...
Some users can connect, I cannot ... (ZTE MF636 from cosmote Greece)

[bug#408555]("https://bugs.launchpad.net/bugs/408555") is active

My relatively stable connection comes using the following procedure:
- boot without modem
- from terminal:
```
sudo stop network-manager
sudo killall modem-manager
```
- attach modem
- at 9.10 wait for the cd-rom icon to appear, right click & eject it
(fully updated 9.10 may not need the eject as 10.04 does not need it)
- connect using alternative methods (wvdial, gnome-ppp, long pppd command)

For more info, read: [http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)

Regards,
George

---

### Post by taamir on 2010-09-12
Thanks Allot ! ! !



Ubuntu can do anything

---

### Post by alMubarmij on 2011-11-25
It seems complicated !

Is there more easier way like a new setup program or some Shell script ?

---

