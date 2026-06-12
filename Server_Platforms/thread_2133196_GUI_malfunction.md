---
title: "GUI malfunction"
date: 2013-04-07
forum: Server Platforms
---

### Post by Nickswitz on 2013-04-07
This is a problem I am having with Ubunutu 12.04 LTS running on server hardware.

The problem is upon start up I can open programs, however, once they are open I can only use some of the GUI interface. I am unable to use the close, minimize, and maximize buttons. As well as being unable to use most of the "OK" or "continue" dialogue buttons that come up. Almost all areas that are text entry allow for me to enter text.  There were no problems similar to this during installation and I have used the exact same build on identical hardware without any similar problems.  

Also, a side question since I haven't been able to find this through anything online, I have a RAID controller hooked into the Ubuntu build and 4 2TB drives connected with RAID 10.  How do I go about mounting that configuration into the operating system?

---

### Post by Bucky Ball on 2013-04-07
*Thread moved to **Server Platforms**.*

---

### Post by MAFoElffen on 2013-04-07
On the mount, since you are using Desktop Edition... If you can mount the file system through nautilus, pop to a terminal session and 
```

sudo blkid
cat /etc/mtab

```
The first would ID all the attached drives and file systems that are present on that box. The second will list all mounts to the system, including temp mounts to files systems via nautilus...  and use that mount line in fstab. You may have to tweak that, but it's a quick way to get a jump on that. 

On running full blown Ubuntu Desktop Edition on server hardware... Server hardware boards are not know for their fancy graphics capabilities, because that's not really a priority in providing network services nor running server apps... so they usually have a minimally capable graphics GPU installed. If you could run in a terminal:
```

lspci -vnn | grep -i VGA

```
And post the results... Then people could advise you on a graphics fix for the graphics capabilities you have at the moment.

---

### Post by Nickswitz on 2013-04-07
Thanks for the reply on the mounting.  As for the graphics, I will post the results of that however I do not believe that it is a Graphics issue, the problem with it is that it is not allowing me to click the buttons, not that they are not visible.  Them not being visible I have seen many many fixes for, but I have been unable to find an answer to them being unselectable.  However thank you for the information and when I get access to the server I will run that and post results.

---

### Post by MAFoElffen on 2013-04-07
As reference from my sticky in my sig line might indicate... I sort of specialize in the UNIX and Linux graphics layer.

The kernel is always running underneath it all. Layers and modules tie into it. When the graphics layers starts on top of those, then keyboard and mouse drivers are added through the xorg-xserver... to act as a go between to the Graphics UI. The video driver selected also affect those. So putting it into those terms, if you can't select a button via a mouse click-select or via a keyboard tab-to enter-select, there is a graphics layer problem in the UI, right? Meaning something is not talking with something else.

---

### Post by Nickswitz on 2013-04-07
Ok, first of all, thank you very much for the very detailed description of how it may be a problem with graphics themselves even though it is not a graphics problem per se.  I enjoy learning more and more about these problems as this is the field that I am going into and eventually I will have to deal with these problems and have to come up with the solutions either myself or with similarly minded people, possibly on the spot.  

Here is the read out that I got from the command.

01:01.0 [COLOR=#ff0000]VGA [/COLOR]compatible controller [0300] : ASPEED Technology, Inc. ASPEED Graphics Family [1a03:2000] (rev 10) (prog-if 00 [[COLOR=#ff0000]VGA[/COLOR]&#8203; controller])

---

### Post by MAFoElffen on 2013-04-08
ROTFLMAO!!!

Sorry. I haven't seen that GPU in years. Not well supported internally by Xorg... likewise, causing your specific problem. But the good news- The ASpeed site does have linux drivers to download for your hardware. Current from them is file v96_whql.zip. In that archive, go the the linux folder and extract "lxdrv.tar.gz". After extracting that, read the readme file. Before executing the install script, you have to create your own blank xorg.conf file with the SECTION DEVICE, driver line pointing to "ast" driver... and you have to set the properties of the install script file to be executable. Their install script includes checks for "ubuntu".

I think I remember that it may still only do 2D graphics and not 3D... but they may have got around that, not positive on that. It's been awhile. That is how it used to be with that GPU in Linux. 

After you install the new driver (including rebooting to use the new xorg.conf), then run:
```

/usr/lib/nux/unity_support_test -p

```
That will output the capabilities of your GPU using that driver... And if it is capable of running Unity 3D or if you will have to run Unity 2D. If still just 2D graphics capable, then Unity 2D is not installed as a fallback any longer, so you'd have to install it to be able to use Unity 2D for the DE.

Hope that info helps.

---

### Post by Nickswitz on 2013-04-08
Ok, I looked at the ASpeed website and was unable to find the specific driver for this device, would you be able to point me in A more specific direction?

---

### Post by MAFoElffen on 2013-04-08
> **Nickswitz said:**
> Ok, I looked at the ASpeed website and was unable to find the specific driver for this device, would you be able to point me in A more specific direction?
[http://www.aspeedtech.com/support.php?fPath=24](http://www.aspeedtech.com/support.php?fPath=24)

Look to the last line of the "BIOS/Driver Package Downloads" section --or--...

The direct download link is:
[http://upload.aspeedtech.com/BIOS/v096_whql.zip](http://upload.aspeedtech.com/BIOS/v096_whql.zip)

 I tried to extracting just the tar you need and attaching to this post, but I guess 8MB is too large to attach here.

---

### Post by Photonic Nature on 2013-10-19
_***First off, we need to verify information about hardware before offering advice.***_
Why? Because if anyone with a DELL PowerEdge C1100 CS24-TY attemps to update the firmware they will brick the server. (I know... nobody mentioned it... Yet.)
That Aspeed chip has VGA tacked onto it but it is NOT just a video chip. 
It is Dell's embedded BMC Remote Management Console and most of the Cheap CS24-TY's everyone is pouncing on are in fact custom builds that are totally different animals than Dell's standard offerings, whereby even Dell's firmware will brick these machines.

Got One? Your first clue is that the Service Tag is not recognized by Dell.
Your 2nd clue is to take the first 6 characters of the ASPEED Mac address on the bottom of the chips label to: [http://www.macvendorlookup.com/](http://www.macvendorlookup.com/)
Where you will most likely find that this is a custom built Quanta machine. (Made in Taiwan)
Your 3rd clue would be to run this in your terminal if you installed Linux on it: **lspci -v** ... nothing extra - no grep!
Where the last listing should be the VGA compatible controller and you will want to look at the **Subsystem:** name... It probably is QUANTA Computer Inc.

You can read the last 3 posts of mine at the bottom of this page: [http://en.community.dell.com/support-forums/cloud/f/4715/p/19492940/20459150.aspx#](http://en.community.dell.com/support-forums/cloud/f/4715/p/19492940/20459150.aspx#)
to find a whole bunch more information on these goose eggs.
The CS24-TY is actually a S99...
**Brochure:** [http://203.75.58.18/UPFile/QSSC-S99K.pdf](http://203.75.58.18/UPFile/QSSC-S99K.pdf)
 **Support / Downloads **([COLOR=#ff0000]Select Product Model:[/COLOR] **QSSC-S99K 1U **/ 2U)**:** 
[http://www.quantaqct.com/en/02_support/02_download.php?page=10&actions=1&xauthorise=77]("http://www.quantaqct.com/en/02_support/02_download.php?page=10&amp;actions=1&amp;xauthorise=77")

Sorry boys and girls, these machines and their vendors do not support Debian based distros.
However, You could try the NVIDIA-173.14.25 driver as the ASPEED2000 series are supposedly compatible with the Quadro FX2000.
  [ ]("http://ubuntuforums.org/member.php?u=1044547")[**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1044547") is correct, these chips do **not** support 3D acceleration.

P.S. CenOS 6.4 x86_64 works OKish out of the box with it's Gnomeo2 desktop, but at least you can get and install the RedHat supported drivers from Quanta.
Also worthy of mention here is that MacPup 528 works too, if you Must desktop an enterprise class server with a ASPEED BMC chip. (Expect a lot of hardware errors / blinking orange lights.)

---

