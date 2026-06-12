---
title: "HOW TO: Compiling and Installing the OpenChrome Graphical VIA Driver"
date: 2007-06-27
forum: Tutorials
---

### Post by TuxCrafter on 2007-06-27
Hereby I post my script as attachment for installing and compiling the open source OpenChrome graphical driver for via Chipsets.

-- -- -- -- -- --
To install on Hardy:

sudo apt-get install xserver-xorg-video-openchrome
-- -- -- -- -- --

To install on Gusty: 
HOW TO: Compiling and Installing the OpenChrome Graphical VIA Driver

#Version:       0.1.2
#Date:          17-03-07 / 08-06-07 / 17-06-07 /26-07-2007 /31-07-2007
#Date:          21-10-07 / 25-10-07 / 05-11-07 / 08-11-07 / 06-03-2008
#Description:    Install openchrome video drivers from cvs source

These script has both community support and commercial support.

Please post all your feedback about this script so I can continuously keep improving it.

I hope this script will help a lot of people!

Where to find support if the driver installed but did not work:
[http://wiki.openchrome.org/mailman/listinfo/openchrome-users](http://wiki.openchrome.org/mailman/listinfo/openchrome-users)
[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats)

To test if the openchrome driver is working after restart of the xserver:

```
 grep openchrome /var/log/Xorg.0.log
```(II) LoadModule: "openchrome"

```
glxinfo | grep render
```direct rendering: Yes
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX/SSE2

To disable 3D rendering add the following in you xorg.conf file. 3D is causing instability on some of the openchrome systems.

```
 Section "Module"
    Disable "glx"
    Disable "xtrap"
    Disable "record"
    Disable "GLcore"
    Disable "dri"
EndSection
```

To find information about the openchrome driver options that can be used, please read the following man page.
```
man openchrome
```

The 2D openchrome driver is NOT responsible for the 3D MESA driver. The 3D MESA driver does not support some of the textures necessary to be able to run desktop effects like compiz. So its currently impossible to have desktop effects with via chipsets. The only good solution for this is to make VIA release documentation about there chipsets so developers can create working software. So first ask VIA to release documentation and then ask developers to use this documentation, not the other way around.

217 + 20  + 1002 + 443 views +  the below

---

### Post by kwacka on 2007-07-03
This shell removes/install openoffice & sun java.

Or has the brandy & coke got to me?

---

### Post by TuxCrafter on 2007-07-26
> **kwacka said:**
> This shell removes/install openoffice & sun java.

Or has the brandy & coke got to me?

Thank you for noticing! I uploaded the openoffce.sh instead of the openchrome.sh. The problem is fixed now!:lolflag:

Please leave a message if you use the script.

---

### Post by TuxCrafter on 2007-07-31
I made some enhancements to the script,

There is a bug in the automatic downloaded mesa drm code. I automatically fixed this.

---

### Post by tech0007 on 2007-10-16
HI,

Is this for Feisty or Gutsy?

Thanks

---

### Post by TuxCrafter on 2007-10-16
The works for both Feisty as Gutsy. However under Gusty you don't have to install the 3D driver. You must skip this step, because 3D will work out of the box after running the script.

---

### Post by &#1050;&#1085;&#1077;&#1083;&#1077; on 2007-10-19
It does not work for me. I have Fujitsu-Siemens AMILO Pro V2030, Intel Celeron 1.4GHz, 512MB of ram, Chipset Via P4M800CE, Via S3G UniChrome Pro IGP. I have installed fresh copy of new Ubuntu 7.10. The script ran well (did not ask for installation of 3D driver), and the xorg.conf file has changed to VIA driver etc., but then, after reboot, there was a mess with the colours and I had to do sudo dpkg-reconfigure -phigh xserver-xorg. Any ideas? Thanks in advance.:(

EDIT: Never mind. It's now open SUSE on that laptop since the modem is not supported by Ubuntu, too.

---

### Post by carlvillan on 2007-10-21
hi i tried your scrip openchrome sh with no luck ,i i got a x error at the end i dont know if there were more errors but i didnt notice any more. my chip is p4m890 ,ubuntu feisty,7.04   biostar mobo  any new ideas for this.iam a newbee in ubuntu .

---

### Post by TuxCrafter on 2007-10-21
there has just been a new official release of the openchrome driver. It changes the name of the xorg module from via to openchrome. I had to figure this out and it took some time. I uploaded a new script that has been tested under gusty gibbon.

---

### Post by TuxCrafter on 2007-10-21
Everybody that had no luck with the script, please try again. It should work perfectly now. Make sure to reboot your computer after the installation.

---

### Post by Tedd81 on 2007-10-21
Hello,

I'm using a Packard Bell Easynote with S3 Unichrome Pro VGA Adapter.
The script gave me 2D setup but no 3D.
Is this correct?

---

### Post by n00b@linux on 2007-10-21
> **TuxCrafter said:**
> there has just been a new official release of the openchrome driver. It changes the name of the xorg module from via to openchrome. I had to figure this out and it took some time. I uploaded a new script that has been tested under gusty gibbon.Thanks TuxCrafter!  You've saved me a LOT of hurt and pain.  I installed it using Synaptic and my results:```
user@nano-itx:~$ glxinfo | grep rendering
direct rendering: Yes
user@nano-itx:~$ sudo cat /etc/X11/xorg.conf | grep via
        Driver          "via"
user@nano-itx:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02)
user@nano-itx:~$
``` \\:D/

---

### Post by markp1989 on 2007-10-21
> **&#1050 said:**
> It does not work for me. I have Fujitsu-Siemens AMILO Pro V2030, Intel Celeron 1.4GHz, 512MB of ram, Chipset Via P4M800CE, Via S3G UniChrome Pro IGP. I have installed fresh copy of new Ubuntu 7.10. The script ran well (did not ask for installation of 3D driver), and the xorg.conf file has changed to VIA driver etc., but then, after reboot, there was a mess with the colours and I had to do sudo dpkg-reconfigure -phigh xserver-xorg. Any ideas? Thanks in advance.:(

EDIT: Never mind. It's now open SUSE on that laptop since the modem is not supported by Ubuntu, too.

i have the same laptop and i cannt get it to work with gusty eaither

---

### Post by Velenoso on 2007-10-22
Hi there, 

Do you need to be connected to the internet for this script to work? I haven't set up my internet connection in Ubuntu as yet. Is it possible to do this without being online?

Thanks

---

### Post by Tedd81 on 2007-10-22
I used both the script and Synaptic but suffered very poor window scrolling, freezing  and just blank windows.. Arrrg :(
I think I'm using VT8237

I followed: [http://ubuntuforums.org/showthread.php?t=465298&highlight=S3+Unichrome+Pro](http://ubuntuforums.org/showthread.php?t=465298&highlight=S3+Unichrome+Pro)

The glitches have now gone but no 3D.... arrg

now looking at:
[http://unichrome.sourceforge.net/](http://unichrome.sourceforge.net/)

Help!!!

---

### Post by n00b@linux on 2007-10-22
@Velenoso:
Yes, you need to be connected to the internet to use either the script or to use Synaptic (the repo packages).
 
@Tedd81:
Please post the results of 'lspci' so that we can identify your chipset (certain chipsets work with 'trunk' others require the 'experimental branch' of the openchrome driver). Also, have you looked at the output of /var/log/Xorg.0.log for any X errors?

---

### Post by Tedd81 on 2007-10-22
Results of 'lspci' :

> 00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)


Looking at Xorg.0.log now. I need to restart X after undoing my last actions to recreate any faults.

---

### Post by Tedd81 on 2007-10-22
There are no errors in Xorg.0.log but a couple of warnings i don't understand so i have attached it.

Also:
> root@ted-laptop:~# glxinfo | grep rendering
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.
direct rendering: Yes


What do i do with this?
(sorry a bit new to linux)  ;)  

Thanx for help, sorry for any silly questions!!!!!!!:)

---

### Post by n00b@linux on 2007-10-22
> 00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host BridgeThe K8M800 northbridge is supported by both the Unichrome and Openchrome drivers. However, the Openchrome web site says of the K8M800:
 
"2D acceleration should work just fine and **3D acceleration works fine as well, except on K8M/N800 chips** where there are frequent hangs, probably due to timing problems"
 
Hence, the 3D bug you experienced from running the Openchrome driver is known about (but not fixed). It's possibly the same bug that's showing up when you invoke 'glxinfo | grep rendering'. And there are no silly questions on the Ubuntu forums. We were all new to linux once.
 
It would appear, that if you want 3D, your best bet is the Unichrome driver. You had the link in one of your previous posts. It contains some rudimentary instructions on how to compile it but before you do that, check the Gutsy repos to see if it's available as a package.
 
To clarify what's going on: the openchrome video drivers (both 'trunk' and 'experimental_branch') produce a 2D driver which is only capable of 3D 'acceleration' ('direct rendering', 'hardware acceleration', or whatever name is your favourite) when using the unichrome_dri.so module.  The unichrome_dri.so module is maintained by the unichrome project - a different project to the openchrome project.  The unichrome project also has a 2D driver (commonly known as the unichrome driver).  Therefore, BOTH the openchrome and unichrome 2D drivers rely on the *unichrome* 3D 'driver' to get direct rendering.  As the openchrome project does not maintain the unichrome 3D driver (unichrome_dri.so) it has not fixed the problems your chipset (K8M800) is experiencing when you combine the openchrome 2D driver with the unichrome 3D driver.  However, it would appear from the unichrome project's web site on sourceforge, that the unichrome 2D driver works well with the unichrome 3D driver for the chipsets the unichrome project supports - of which, the KM800 is one.  Hence, it would appear your best bet is to try the Unichrome driver if you want stable 3D.  Of course, the openchrome project's 2D drivers also enable 'accelerated' MPEG2 decoding on certain chipsets but the unichrome project does not.  So, the choices for your chipset (K8M800) are one or the other (2D video + 3D video vs. 2D video + MPEG2 acceleration) but you can't have it all (2D video + 3D video + MPEG2 acceleration) :(
 
Let us know if you require any further help.

---

### Post by TuxCrafter on 2007-10-22
[http://ubuntuforums.org/showthread.php?t=485646](http://ubuntuforums.org/showthread.php?t=485646)

I uploaded a new version of the script, I tested it on a fresh installation and it works perfectly. Please try the script and any feedback is welcome.

The script is on the first post of this topic!

---

### Post by CANDYBOi on 2007-10-23
Great effort!
Good news is is it didn't mess anything up, the script itself works as far as I can tell. On the downside it got me no closer to 3D (CN400/PM880).

---

### Post by TuxCrafter on 2007-10-23
The 3D driver stands totally separated from the 2D openchrome driver.

The 3D driver is maintained by the mesa project and should work out of the box after installing the 2D driver.

I have a CN700 based chipset and here it works. Maybe you can contact the Mesa developers?

OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX/SSE2
OpenGL version string: 1.2 Mesa 7.0.1

---

### Post by CANDYBOi on 2007-10-23
> **TuxCrafter said:**
> The 3D driver stands totally separated from the 2D openchrome driver.

The 3D driver is maintained by the mesa project and should work out of the box after installing the 2D driver.

I have a CN700 based chipset and here it works. Maybe you can contact the Mesa developers?

OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX/SSE2
OpenGL version string: 1.2 Mesa 7.0.1

That's what I meant by the "downside". It should be working, and yet it isn't. I'm looking through some recent mesa releases, to see if there's a clue in any of them as to why.

On the other hand, I've already tried the last three without success.
I'm gonna see if I can't get my hands on another CN400-chipped notebook and try it out, to rule out my computer being retarded. :D

**EDIT:**
Nope. It seems mesa's loading just fine. Going to try downgrading a bit further.

---

### Post by n00b@linux on 2007-10-23
I got things working (both 2D and 3D) on my CN400 by first installing from the repos using Synaptic.  Try that and then upgrade to the latest trunk using TuxCrafter's script.

---

### Post by CANDYBOi on 2007-10-23
I did, only it would for some reason not upgrade the Mesa DRI to 7.0.1, but 6.5.2, which has me confused I must say.

---

### Post by n00b@linux on 2007-10-23
I'm speculating, but it could be because of the known problems with the unichrome "3D driver" above MESA 6.4 - see [http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=3DTroubleShooting](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=3DTroubleShooting)

---

### Post by tjazar on 2007-10-23
I downloaded and ran the script, and everything appears to have worked... except that my monitor's native resolution (1280x800) still doesn't work; I'm stuck in 800x600.  My Graphics Card is openchrome, but changing the monitor to "LCD Panel 1280x800" yields a screen full of garbled lines with one perfectly clear box asking me if I want to keep these settings.  Any advice?  By the way, thanks so much for supporting this script.  I've been searching for a solution to this problem, and I certainly appreciate someone who will stand by their work.

- Thomas

lspci output:
```
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

```

---

### Post by xak on 2007-10-24
I just used this script on a fresh Gutsy install on a Phylon 7F2WE mini-ITX board, with a CN700 chipset (2GHz CPU, 512MB DDR533).  Direct Rendering is now working, and I get  just under 1,000FPS in glxgears!  3D has been broken since Edgy for me so I'm very thankful for Gutsy and for this script.  Cheers and thanks very much!

I did have some errors during the script, but I just waited them out and haven't seen any problems yet (there were about 50 or so errors regarding scrollkeeper, message was "extra content at the end of the document")

---

### Post by n00b@linux on 2007-10-24
> **tjazar said:**
> I downloaded and ran the script, and everything appears to have worked... except that my monitor's native resolution (1280x800) still doesn't work; I'm stuck in 800x600.  My Graphics Card is openchrome, but changing the monitor to "LCD Panel 1280x800" yields a screen full of garbled lines with one perfectly clear box asking me if I want to keep these settings.  Any advice?Try running a ModeLine in your /etc/X11/xorg.conf.  That's how I fixed my 1680x1050 problem.  Look at your /var/log/Xorg.0.log file for the values you need.  

If you have any problems with this make a new thread, link to it in this one and I'll take a look.

---

### Post by TuxCrafter on 2007-10-24
I just read a post somewhere about some 3D troubles with gusty. If you cant get 3D to work try to install the following package, it should be installed already: ```
sudo apt-get install libgl1-mesa-dri
```I can create scripts for installing LCD screens with there correct native resolution. Also I can create scripts for solving font rendering problems with LCD screens. However this will take a lot of time supporting. If there is enough amino I will publish them. Because the discussed openchrome driver is a 2D driver only, I thought it was out of the scope of this topic to discuss 3D rendering, LCD setup and font rendering :-D. Any thoughts?

---

### Post by n00b@linux on 2007-10-24
> **TuxCrafter said:**
> I thought it was out of the scope of this topic to discuss 3D rendering, LCD setup and font rendering :-D. Any thoughts?That's why I suggested tjazar start a new thread (I didn't want to hijack this thread).  If you're happy for 3D and resolution to be discussed then let us know.  I think it would be a good idea as 2D, 3D and X are all inter-twined IMHO.

---

### Post by climatewarrior on 2007-10-24
The script worked pefectly on the computer and it correctly installed the openchrome dirver and all but i cant still use compiz fusion,any ideas?

thanks!

---

### Post by n00b@linux on 2007-10-24
> **climatewarrior said:**
> The script worked pefectly on the computer and it correctly installed the openchrome dirver and all but i cant still use compiz fusion,any ideas?
 
thanks![http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=3DStatus](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=3DStatus)

---

### Post by laby70 on 2007-10-24
i have a problem with the script when execute the line:
svn co [http://svn.openchrome.org/svn/trunk](http://svn.openchrome.org/svn/trunk) openchrome

i got...
svn: PROPFIND di '/svn/trunk': Could not resolve hostname 

...i'm behind ISA Server and i use ntlmaps for access Internet

i have put in the lines:
http-proxy-host = localhost
http-proxy-port = 5865

on .subversion/servers file

but don't work

can you help me??

---

### Post by TuxCrafter on 2007-10-24
> **laby70 said:**
> i have a problem with the script when execute the line:
svn co [http://svn.openchrome.org/svn/trunk](http://svn.openchrome.org/svn/trunk) openchrome

```
svn co http://svn.openchrome.org/svn/trunk openchrome
```

The above command is working fine here. Did you successfully installed the necessary tools?

```
sudo apt-get update
sudo apt-get build-dep xserver-xorg-video-via
sudo apt-get install build-essential libgl1-mesa-dri xserver-xorg-video-via subversion autoconf automake1.9 libtool xorg-dev libdrm-dev libgl1-mesa-dev git-arch
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by laby70 on 2007-10-24
i think the problem is the method PROPFIND of svn.....maybe is not supported by ntlmaps!!!

i have installed the necessary tools without problem...

---

### Post by TuxCrafter on 2007-10-24
> **laby70 said:**
> i think the problem is the method PROPFIND of svn.....maybe is not supported by ntlmaps!!!

i have installed the necessary tools without problem...

The commands I used are farly default ones, if the ntlmaps system gives you trouble, i  would be able to help you with community support.

 If you find the solution please let us know. :KS

---

### Post by tjazar on 2007-10-24
> Because the discussed openchrome driver is a 2D driver only, I thought it was out of the scope of this topic to discuss 3D rendering, LCD setup and font rendering . Any thoughts?

I apologize for seemingly hijacking this thread, as that was not my intention at all.  I assumed that my problems lay with something I did wrong installing openchrome, so I sought advice from this thread.  Since it's apparently a disconnect between my LCD and Ubuntu, I'll look elsewhere.

---

### Post by TuxCrafter on 2007-10-24
> **tjazar said:**
> I apologize for seemingly hijacking this thread, as that was not my intention at all.  I assumed that my problems lay with something I did wrong installing openchrome, so I sought advice from this thread.  Since it's apparently a disconnect between my LCD and Ubuntu, I'll look elsewhere.

No need to apologize for anything, btw i just posted all the how to's you needed for you lcd setup but they are awaiting approval by the moderators, so standby for a while.

---

### Post by tjazar on 2007-10-24
Well, I got my widescreen resolution working by running "sudo dpkg-reconfigure xserver-xorg" and following the screens.  Everything is in its proper proportion, and that's the last I'll say about LCDs.  :)

---

### Post by climatewarrior on 2007-10-25
Update: OpenChrome doesnt work well with my friends  Gateway MX3228 laptop. There is a lot of buggy and crazy stuff that happens on the desktop.

---

### Post by kc9bop on 2007-10-25
It didn't work for me. I have Gateway MX3228 Notebook with an Intel Celeron 1.5GHz, 512MB of ram, Via P4M800CE Chipset, and Via S3G UniChrome Pro IGP (VT3314 Chipset).  I did a fresh install of Ubuntu 7.10 and ran your script.

Everything worked... no errors during compile, and the xorg.conf was edited to "openchrome".  I rebooted the machine, but when it tried to start the xserver, the screen flashes for a moment to the right resolution, then crashes, then tries again.  This keeps happening until I reboot the machine into recovery mode and change the display back to vesa.

---

### Post by n00b@linux on 2007-10-25
> **kc9bop said:**
> It didn't work for me. I have Gateway MX3228 Notebook with an Intel Celeron 1.5GHz, 512MB of ram, Via P4M800CE Chipset, and Via S3G UniChrome Pro IGP (VT3314 Chipset). I did a fresh install of Ubuntu 7.10 and ran your script.
 
Everything worked... no errors during compile, and the xorg.conf was edited to "openchrome". I rebooted the machine, but when it tried to start the xserver, the screen flashes for a moment to the right resolution, then crashes, then tries again. This keeps happening until I reboot the machine into recovery mode and change the display back to vesa.
Did you try the experimental branch of the openchrome driver? (it's commented out in TuxCrafter's script).
 
Failing that, try the unichrome driver.

---

### Post by kc9bop on 2007-10-25
I switched to the experimental branch, and now OpenChrome works.  Unfortunately I'm getting the same random screen garble thing that the other Gateway MX3228 user is getting.

I'll try the unichrome driver next.  Thanks for the help.

---

### Post by TuxCrafter on 2007-10-26
On requests of some people I posted some other howto's. Also two for font settings.

Also the LCD setup how to is posted and the XFCE font rendering how to. See my new signature for the forum links.

---

### Post by virtual_reality on 2007-10-27
I followed the script but after restart I had white belts on the screen :( what did I wrong?

---

### Post by TuxCrafter on 2007-10-27
> **virtual_reality said:**
> I followed the script but after restart I had white belts on the screen :( what did I wrong?

What are white belts exactly? You can try the experimental branch?

---

### Post by virtual_reality on 2007-10-27
Diagonal, broken, white belts  :( experimental branch?

---

### Post by TuxCrafter on 2007-10-27
> **virtual_reality said:**
> Diagonal, broken, white belts  :( experimental branch?

open the script in you favorite editor commend out the current trunk and remove the commend from the experimental branch then retry the script.

(maybe i should make it a option in the script)

---

### Post by Vox1512 on 2007-10-28
I have an Everex Stepnote NC1500 laptop. The Script Works great. 

I ran the script on a fresh install of Ubuntu 7.10. After running the script I had to select the screen(1280x800 LCD) and graphics card (other-->openchrome) and after a restart of X (ctrl-alt-backspace) i had native resolution. Much faster than the VESA driver.

Thank you, Thank you. Thank you!

Here is the hardware info the script produced

version: 0.0.9
command: chmod +x openchrome.sh; ./openchrome.sh
-- -- -- -- --
26: PCI(AGP) 100.0: 0300 VGA compatible controller (VGA)
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3344
  Unique ID: VCu0.dIeHsiODd01
  Parent ID: vSkL.S16qDHSKEeD
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "FIRST INTERNATIONAL UniChrome Pro IGP"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3344 "UniChrome Pro IGP"
  SubVendor: pci 0x1509 "FIRST INTERNATIONAL Computer Inc"
  SubDevice: pci 0x4330 
  Revision: 0x01
  Memory Range: 0xf0000000-0xf3ffffff (rw,prefetchable)
  Memory Range: 0xd1000000-0xd1ffffff (rw,non-prefetchable)
  IRQ: 10 (no events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001106d00003344sv00001509sd00004330bc03sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (PCI bridge)

Primary display adapter: #26
-- -- -- -- --
09: PCI(AGP) 00.0: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_314
  Unique ID: qLht.0A+c5I7kRQ3
  SysFS ID: /devices/pci0000:00/0000:00:00.0
  SysFS BusID: 0000:00:00.0
  Hardware Class: bridge
  Model: "FIRST INTERNATIONAL P4M800CE Host Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x0314 "P4M800CE Host Bridge"
  SubVendor: pci 0x1509 "FIRST INTERNATIONAL Computer Inc"
  SubDevice: pci 0x3149 
  Driver: "agpgart-via"
  Driver Modules: "via_agp"
  Memory Range: 0xe0000000-0xefffffff (rw,prefetchable)
  Module Alias: "pci:v00001106d00000314sv00001509sd00003149bc06sc00i00"
  Driver Info #0:
    Driver Status: via_agp is active
    Driver Activation Cmd: "modprobe via_agp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

10: PCI 00.1: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_1314
  Unique ID: hgAj.6grGtcE79aF
  SysFS ID: /devices/pci0000:00/0000:00:00.1
  SysFS BusID: 0000:00:00.1
  Hardware Class: bridge
  Model: "VIA P4M800CE Host Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x1314 "P4M800CE Host Bridge"
  Module Alias: "pci:v00001106d00001314sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

11: PCI 00.2: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_2314
  Unique ID: Z+fY.MqRPx8GEF_A
  SysFS ID: /devices/pci0000:00/0000:00:00.2
  SysFS BusID: 0000:00:00.2
  Hardware Class: bridge
  Model: "VIA P4M800CE Host Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x2314 "P4M800CE Host Bridge"
  Module Alias: "pci:v00001106d00002314sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

12: PCI 00.3: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3208
  Unique ID: QK9O.ndAIs8NWMH8
  SysFS ID: /devices/pci0000:00/0000:00:00.3
  SysFS BusID: 0000:00:00.3
  Hardware Class: bridge
  Model: "VIA PT890 Host Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3208 "PT890 Host Bridge"
  Module Alias: "pci:v00001106d00003208sv00000000sd00000000bc06sc00i00"
  Driver Info #0:
    Driver Status: via_agp is active
    Driver Activation Cmd: "modprobe via_agp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

13: PCI 00.4: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_4314
  Unique ID: HfeD.s8eg3nrbTpE
  SysFS ID: /devices/pci0000:00/0000:00:00.4
  SysFS BusID: 0000:00:00.4
  Hardware Class: bridge
  Model: "VIA P4M800CE Host Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x4314 "P4M800CE Host Bridge"
  Module Alias: "pci:v00001106d00004314sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

14: PCI 00.7: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_7314
  Unique ID: ud6k.cdQ4GV+Dq3B
  SysFS ID: /devices/pci0000:00/0000:00:00.7
  SysFS BusID: 0000:00:00.7
  Hardware Class: bridge
  Model: "VIA P4M800CE Host Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x7314 "P4M800CE Host Bridge"
  Module Alias: "pci:v00001106d00007314sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

15: PCI 01.0: 0604 PCI bridge (Normal decode)
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_b198
  Unique ID: vSkL.S16qDHSKEeD
  SysFS ID: /devices/pci0000:00/0000:00:01.0
  SysFS BusID: 0000:00:01.0
  Hardware Class: bridge
  Model: "VIA VT8237 PCI Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0xb198 "VT8237 PCI Bridge"
  Module Alias: "pci:v00001106d0000B198sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

22: PCI 11.0: 0601 ISA bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3227
  Unique ID: 7EWs.YZVJ6lFy0D6
  SysFS ID: /devices/pci0000:00/0000:00:11.0
  SysFS BusID: 0000:00:11.0
  Hardware Class: bridge
  Model: "FIRST INTERNATIONAL VT8237 ISA bridge [KT600/K8T800/K8T890 South]"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3227 "VT8237 ISA bridge [KT600/K8T800/K8T890 South]"
  SubVendor: pci 0x1509 "FIRST INTERNATIONAL Computer Inc"
  SubDevice: pci 0x3227 
  Module Alias: "pci:v00001106d00003227sv00001509sd00003227bc06sc01i00"
  Driver Info #0:
    Driver Status: i2c_viapro is active
    Driver Activation Cmd: "modprobe i2c_viapro"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
-- -- -- -- --
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

---

### Post by Vox1512 on 2007-10-28
I spoke too soon. 

The openchrome.sh script is great. Compiles the driver and modifies xorg.conf to use the driver. X starts up using the openchrome driver,

I do get 3d direct rendering and respectable speed in glxgears but the 2d is scrambled for the the main and experimental trunks.

Its almost as if old screen memory is getting switched in that shows a history of the cursor locations and window positions. for example, If I drag a dialog box across the screen. It will land and position fine, but I will eventually get a screen that shows its trails. Windows and Dialog box contents disappear, have to cursor over them or resize the windows to get them to redraw. Strange.

This is on an Everex StepNote NC1500  (VN800) 

For now its back to the vesa driver

Thanks.

---

### Post by virtual_reality on 2007-10-28
> **TuxCrafter said:**
> What are white belts exactly? You can try the experimental branch?

which words should I remove exacly?

---

### Post by TuxCrafter on 2007-10-29
> **Vox1512 said:**
> I have an Everex Stepnote NC1500 laptop. The Script Works great. 

I ran the script on a fresh install of Ubuntu 7.10. After running the script I had to select the screen(1280x800 LCD) and graphics card (other-->openchrome) and after a restart of X (ctrl-alt-backspace) i had native resolution. Much faster than the VESA driver.

Thank you, Thank you. Thank you!

Here is the hardware info the script produced


Hi, thanks for your feedback, please post your info in a separated file to prevent clouding up this topic for other readers.

---

### Post by TuxCrafter on 2007-10-29
> **Vox1512 said:**
> I spoke too soon. 

The openchrome.sh script is great. Compiles the driver and modifies xorg.conf to use the driver. X starts up using the openchrome driver,

I do get 3d direct rendering and respectable speed in glxgears but the 2d is scrambled for the the main and experimental trunks.

Its almost as if old screen memory is getting switched in that shows a history of the cursor locations and window positions. for example, If I drag a dialog box across the screen. It will land and position fine, but I will eventually get a screen that shows its trails. Windows and Dialog box contents disappear, have to cursor over them or resize the windows to get them to redraw. Strange.

This is on an Everex StepNote NC1500  (VN800) 

For now its back to the vesa driver

Thanks.

Please post you problem on the openchrome mailing list, maybe they can fix it.

---

### Post by harrydb on 2007-10-29
Great script, worked like charm. 

However some configurations (like mine) require 
```
Option "VBEModes" "true"
```
in xorg.conf, to work with a panel display (on the dvi port in my case) otherwise X will run but the display just turns black. For those chipsets it might be nice if the script asks whether you are using a panel display (on the dvi port?) and if so add the above line to xorg.conf (if chosen to configure x).

The following page gives an overview of which chipsets need that option: [http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats)
Maybe the current chipset can be detected with 'lspci' or something.

Regards,
Harry

---

### Post by evilspy on 2007-10-30
Script worked fine, laptop (Fujitsu-Siemens Amilo L 7300T) booted fine. But as soon as I tried to do anything I got corruption as seen in screenshot.

---

### Post by TuxCrafter on 2007-10-30
I have asked the openchrome developers and the mailing list if they can help me provide better support solving openchrome driver issues. I hope to here from them soon.

---

### Post by Vox1512 on 2007-10-30
Do not know if this is the proper place to share this but:

I found a fix for Scambled/Corrupted Screens in the OpenChrome Mailing List Archives - Turn Off AGP DMA with:

Option "EnableAGPDMA" "false"

---

### Post by thenetduck on 2007-10-31
This is my read out.

I don't know how to test if this worked but I think it did. 

I have a P4M800CE chipset

I was trying to install this because the vesa drivers were still freezing up my system and making it crash randomly. (very annoying when in a programming project) 

The Net Duck

---

### Post by Stimy on 2007-10-31
I got it working  on Amilo Pro V2055 with:
[LIST]
[*]script
[*]dpkg-reconfigure xserver-xorg //i had to try this twice, first time didn't work, don't know why
[*]Option "EnableAGPDMA" "false" 
[*]Option "VBEModes" "true" // Not sure if this one is important
[/LIST]

But my main problem still exists. My gutsy freezes if i use openchrome driver when i start wine or Wolfram mathematica 6.0. It worked fine on feisty, so i think that is kernel bug. That's way i'm still on vesa drivers.

---

### Post by TuxCrafter on 2007-10-31
> **Stimy said:**
> I got it working  on Amilo Pro V2055 with:[LIST]
[*]script
[*]dpkg-reconfigure server-xorg //i had to try this twice, first time didn't work, don't know why
[*]Option "EnableAGPDMA" "false"
[*]Option "VBEModes" "true" // Not sure if this one is important[/LIST]
But my main problem still exists. My gutsy freezes if i use openchrome driver when i start wine or Wolfram mathematica 6.0. It worked fine on feisty, so i think that is kernel bug. That's way i'm still on vesa drivers.

Hmm if this is the freezing problem that i have been debugging for 1 year now and recently solved it. It has nothing to do with the openchrome driver you will also have lockups with vesa only less regularly. If i see more reports abouts lockups and freezes I will create a separate topic for it how to solve it.

---

### Post by Deividson on 2007-10-31
desktop effects should work after installing this, right? the script ran like a charm, both the grep openchrome and the glxinfo tests says its loaded and running, but when i try to enable desktop effects i get the message "Desktop Effects Could Not be Enabled".

im on Ubuntu 7.10, and really wanted to check how the desktop effects looks like :X

---

### Post by evilspy on 2007-10-31
> **Stimy said:**
> I got it working  on Amilo Pro V2055 with:
[LIST]
[*]Option "EnableAGPDMA" "false" 
[*]Option "VBEModes" "true" // Not sure if this one is important
[/LIST]
.

I got mine work with these too.

(edit), using 3d causes crash, gdm restarts and shows login screen but when I try to access terminals (alt-f1) screen corrupts (I can return to login screen).

---

### Post by TuxCrafter on 2007-10-31
> **evilspy said:**
> I got mine work with these too.

(edit), using 3d causes crash, gdm restarts and shows login screen but when I try to access terminals (alt-f1) screen corrupts (I can return to login screen).

Ok that last one sounds like a xorg issue indeed.

---

### Post by Stimy on 2007-10-31
> **TuxCrafter said:**
> Hmm if this is the freezing problem that i have been debugging for 1 year now and recently solved it. It has nothing to do with the openchrome driver you will also have lockups with vesa only less regularly. If i see more reports abouts lockups and freezes I will create a separate topic for it how to solve it.

Well a lot of people has the same issue. There is also a bug report : [https://bugs.launchpad.net/xorg-server/+bug/43154](https://bugs.launchpad.net/xorg-server/+bug/43154) ,and some others.
I know that here isn't the right place for discussing  this, but only for information.

---

### Post by TuxCrafter on 2007-10-31
Hello everybody, I got a lot of messages about freezing and lock-ups on via systems, i solved this by doing the following, please report if this worked:

# step 1: Installation of 368 kernel as a solution for system lockups on system with the VIA CN700 chipset and VIA C7 cpu
```
sudo apt-get remove libc6-i686
sudo apt-get install linux-image-386
```# note 1: Check libc6
```
sudo dpkg -S libc6-i686
sudo dpkg -l libc6
```# step 3: reboot system
```
sudo reboot
```# note 2: Check the kernel version
```
uname -a
```# step 4: Recompile the openchrome driver with the following script and provide some feedback to on the topic:
[http://ubuntuforums.org/showthread.php?p=3679548](http://ubuntuforums.org/showthread.php?p=3679548)

---

### Post by linfun on 2007-11-03
# TuxCrafter,

Excellent work you have done. 

I run Debian Lenny, because all newer Ubuntu distros are too slow on my passive cooled box.

I downloaded and executed  your script and everything seems to work;  my slow box is now faster:)


However, I have a problem with DVD playback:

My passive cooled CPU is a 1,2GHz VIA C7 and the graphic chipset is CN700.

When I try to playback a DVD too many frames are dropped.
In the xorg.conf openchrome is the driver.
Xine is using the xv video driver.

I believe it is because the mpeg2 hardware decoder of CN700  is not in use.

Any suggestions how to enable the mpeg2 hardware decodere of CN700?

All the best,
LinFun

---

### Post by TuxCrafter on 2007-11-03
> **linfun said:**
> # TuxCrafter,

Excellent work you have done. 

I run Debian Lenny, because all newer Ubuntu distros are too slow on my passive cooled box.

I downloaded and executed  your script and everything seems to work;  my slow box is now faster:)

However, I have a problem with DVD playback:

My passive cooled CPU is a 1,2GHz VIA C7 and the graphic chipset is CN700.

When I try to playback a DVD too many frames are dropped.
In the xorg.conf openchrome is the driver.
Xine is using the xv video driver.

I believe it is because the mpeg2 hardware decoder of CN700  is not in use.

Any suggestions how to enable the mpeg2 hardware decodere of CN700?

All the best,
LinFun


Hi, it seems you have the same hardware as me, I have an EN12000E 1,2GHz VIA C7 + CN700. 

The mpeg2 decoder should work perfect out of the box. at leased it does by me. I advice you to install totem-xine and run my multimedia script (see signature) also install xubuntu and with a bit of fine tuning you got a great system.

---

### Post by linfun on 2007-11-03
Hi TuxCrafter,

I don't know yet what I need to get DVD playback working smooth.

We have the same hardware, but when I try to playback a DVD the picture is stutting, i.e. loosing frames.

A few minutes ago I read that mpeg2 hardware acceleration requires a patch to Mplayer: [http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=XvMC#Mplayer](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=XvMC#Mplayer)

I normally use a player based on the xine engine. I have noticed that the xvmc video driver should be used. I have also tried xv.


I stay with Debian, it works really good and is much faster than xubuntu, since only a few things are loaded during boot. With Debian I know what is on the disk, and therefore this decision can't be changed :-)


Also, my DVI adapter card for EN12000 is still not working, only VGA is working.


Here is what I get when I type glxinfo:

> 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX/SSE2
OpenGL version string: 1.2 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod
Segmentation fault



You can see there is a "segmentation fault".
I don't know what that is, is it because of an error in xorg.conf or ?


Here is my xorg.conf:
> 
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg



Section "Module"
#	Load	"extmod"
#	Load	"xie"
#	Load	"pex5"
#	Load	"GLcore"
#	Load	"dbe"
#	Load	"record"
#	Load	"type1"
#	Load	"freetype"
	Load	"glx" # This loads the DRI module Load "dri"
EndSection


Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"openchrome"
	Option		"EnableAGPDMA" "false"
	Option		"VBEModes" "true"
	VideoRam	65536 
	Option		"XVideo" "On" 
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1280x768" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI" 
	Mode 0666 
EndSection



I still need to find the secret for smooth DVD-playback.

Best regards,
LinFun

---

### Post by TuxCrafter on 2007-11-03
> **linfun said:**
> Hi TuxCrafter,

I don't know yet what I need to get DVD playback working smooth.

We have the same hardware, but when I try to playback a DVD the picture is stutting, i.e. loosing frames.

A few minutes ago I read that mpeg2 hardware acceleration requires a patch to Mplayer: [http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=XvMC#Mplayer](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=XvMC#Mplayer)

I normally use a player based on the xine engine. I have noticed that the xvmc video driver should be used. I have also tried xv.

I stay with Debian, it works really good and is much faster than xubuntu, since only a few things are loaded during boot. With Debian I know what is on the disk, and therefore this decision can't be changed :-)

Also, my DVI adapter card for EN12000 is still not working, only VGA is working.

Here is what I get when I type glxinfo:

You can see there is a "segmentation fault".
I don't know what that is, is it because of an error in xorg.conf or ?

Here is my xorg.conf:

I still need to find the secret for smooth DVD-playback.

Best regards,
LinFun

I used debian before and my mpeg decoder always worked out of the box with gxine and totem-xine after using my openchrome and multimedia scripts.  I know of the mplayer paches but never used them. 

Debian is nice, xubuntu indeed loads much stuff by default, but after some fine tuning my system starts up in 25 seconds and use 78MB when my desktop is fully loaded.

I only remember that somewhere there is an option in the totem-xine config file to use the correct decoder.

Sadly I can't help further with your mpeg problem here it always worked...

---

### Post by Djainette on 2007-11-03
> **Stimy said:**
> I got it working  on Amilo Pro V2055 with:
[LIST]
[*]script
[*]dpkg-reconfigure xserver-xorg //i had to try this twice, first time didn't work, don't know why
[*]Option "EnableAGPDMA" "false" 
[*]Option "VBEModes" "true" // Not sure if this one is important
[/LIST]

But my main problem still exists. My gutsy freezes if i use openchrome driver when i start wine or Wolfram mathematica 6.0. It worked fine on feisty, so i think that is kernel bug. That's way i'm still on vesa drivers.

Oh man, I'm so glad, I thought I was the only one with X freezes after launching wine !
Does it work with vesa ?

---

### Post by Stimy on 2007-11-03
Yes it works with vesa. I also tried the advice Tuxcrafter gave, but it didnt work.

---

### Post by Djainette on 2007-11-03
> **Stimy said:**
> Yes it works with vesa. I also tried the advice Tuxcrafter gave, but it didnt work.

I tried the openchrome driver, X still crashes when I run winecfg.
And I can't use vesa because of this bug :[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853)

It seems I'm doomed...

---

### Post by cf1709 on 2007-11-03
I do have a bit of problems with wine also with this driver installed. Opening wineconfig freezes my system.

Another one, after the install of the drivers, video playback went smoothly but after some hours, the video quality gets back into vesa-style. A log-out, ctrl-alt-backspace,log-in fixes the thing though. Quite minor, but for person like me who spends most of his PC time watching videos, it's annoying.

A Linux n00b here so please respond in layman's terms.

---

### Post by Matataki on 2007-11-04
K8M800 user here with an Averatec 3715 laptop. If I installed the beta version of the driver it works okay, as long as I disable AGPDMA. The only thing is that anything using 3D will hard lock the system, which I have never been able to cure in Ubuntu. It worked okay in PCLinuxOS for half of what I tossed at it, but the other half would freeze it up.

In short, the script worked well but I still dislike Via's driver support haha.:mad:

---

### Post by coady on 2007-11-04
@Tuxcrafter,
Does the script need to be run on a clean install of Gutsy? I made a clean install of Gutsy and then built the openchrome drivers (2D and 3D) manually before I found your post/thread. After that I could not get Gusty to run except in low graphics mode and it kept asking me to install a graphics driver. I then ran your script (nice one BTW) which ran without trouble, but now Gutsy hangs (non-recoverable) when launching X. Is this because of running the script after having manually built and loaded the openchrome drivers, or is it a problem specific to the chipset and Gutsy -- i.e. UniChrome Pro IGP (rev 01) with VN800? Note, I know that this chipset will never run 3D but I have had no problem with 2D and high quality video playback. Thanks.
coady

---

### Post by Djainette on 2007-11-04
How about a new option for the poll ?
- yes, the script worked perfectly, but the problem remains.

Because the compilation was flawless, but X still hangs.

---

### Post by TuxCrafter on 2007-11-04
> **coady said:**
> @Tuxcrafter,
Does the script need to be run on a clean install of Gutsy? I made a clean install of Gutsy and then built the openchrome drivers (2D and 3D) manually before I found your post/thread. After that I could not get Gusty to run except in low graphics mode and it kept asking me to install a graphics driver. I then ran your script (nice one BTW) which ran without trouble, but now Gutsy hangs (non-recoverable) when launching X. Is this because of running the script after having manually built and loaded the openchrome drivers, or is it a problem specific to the chipset and Gutsy -- i.e. UniChrome Pro IGP (rev 01) with VN800? Note, I know that this chipset will never run 3D but I have had no problem with 2D and high quality video playback. Thanks.
coady

Hmm it should work every time. With every new kernel release i rerun the script with success. However maybe something strange happened with your xorg.conf file. I think you have to manually check it out.

---

### Post by karamell3d on 2007-11-04
> **Stimy said:**
> I got it working  on Amilo Pro V2055 with:
[LIST]
[*]script
[*]dpkg-reconfigure xserver-xorg //i had to try this twice, first time didn't work, don't know why
[*]Option "EnableAGPDMA" "false" 
[*]Option "VBEModes" "true" // Not sure if this one is important
[/LIST]

But my main problem still exists. My gutsy freezes if i use openchrome driver when i start wine or Wolfram mathematica 6.0. It worked fine on feisty, so i think that is kernel bug. That's way i'm still on vesa drivers.

i have a Amilo pro v2055 laptop to. Al went well, but my X still not starting. Whe it gets to the Login screen it restarts a few times then a screen appears with the messege: ...Something bad is happening... Waiting 2 min.
I've played with the vsync, hsync no results... :(
Strange is that now i use X started manually front the prompt with "startx" and it's working with proper resolution (1280x800). I don't understand why it wont start automatically at boot???
But starting X manually every time is not really a good option... :(

---

### Post by mahousaru on 2007-11-04
Many thanks TuxCrafter this is an absolutely great script.  Worked on my VIA Unichrome Pro PN800 with no errors.  I can actually run Google Earth now, but I still get the wine freeze I had with the S3 drivers.  If I don't disable dri in xconf my laptop locks up if I run wine.  Does anyone know of any resolutions to this?

If i don't disable dri then if i run glxinfo I get a seg fault.  If I do disable it i loose direct rendering :( 

Anyway still an improvement from before, thanks again

I'm running Ubuntu 7.10, currently with disable dri in the xorg.conf.

---

### Post by TuxCrafter on 2007-11-04
> **mahousaru said:**
> Many thanks TuxCrafter this is an absolutely great script.  Worked on my VIA Unichrome Pro PN800 with no errors.  I can actually run Google Earth now, but I still get the wine freeze I had with the S3 drivers.  If I don't disable dri in xconf my laptop locks up if I run wine.  Does anyone know of any resolutions to this?

If i don't disable dri then if i run glxinfo I get a seg fault.  If I do disable it i loose direct rendering :( 

Anyway still an improvement from before, thanks again

I'm running Ubuntu 7.10, currently with disable dri in the xorg.conf.

Nice to hear, btw dri==3D and has nothing to do with the openchrome driver. It is controlled by the mesa system.

I also have segmentation fault when running glxinfo... cant do anything about it. its in the hands of the mesa project... I discovered i sometimes also got a freezing x server not the system freezes but x, I think i will try to make a script that restarts x when it hangs. or i buy a intel onboard graphical card.

---

### Post by mahousaru on 2007-11-04
> **TuxCrafter said:**
> Nice to hear, btw dri==3D and has nothing to do with the openchrome driver. It is controlled by the mesa system.

I also have segmentation fault when running glxinfo... cant do anything about it. its in the hands of the mesa project... I discovered i sometimes also got a freezing x server not the system freezes but x, I think i will try to make a script that restarts x when it hangs. or i buy a intel onboard graphical card.

Many thanks for the info.  Very impressed with the script and very impressed with the results.  Not only does Google Earth* run slowly now via OpenGL instead of crashing X, but I can now play h.264 with no artefacts appearing on the edge of the screen :)  Big thumbs up 

*Not that I actually use it, but it was the program I happen to use to test my graphics  :p

---

### Post by TheArseneLupin on 2007-11-05
Thanks for your great efforts ;
am using an AmiloPro 5515 with integrated via PM900 card;
i didnt work for me ,and even when i try to compile the driver myself i get this error 

checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking if RANDR is defined... no
checking if RENDER is defined... no
checking if XV is defined... no
checking if XF86DRI is defined... no
checking if DPMSExtension is defined... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... configure: error: Package requirements (xorg-server xproto xvmc fontsproto libdrm ) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'xvmc' found
No package 'fontsproto' found
No package 'libdrm' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

----------------------

So can anyone please tell me what exactly i need to do?
it relly sucks when you can't do 3d games on your computer ,or when firefox is on 800x600 resolution !!!
N.B: am on an Amilo Pro 5515

thanks in advance


NB:
Am ready to coperate and work on a better driver if you want :)

---

### Post by TuxCrafter on 2007-11-05
> **TheArseneLupin said:**
> Thanks for your great efforts ;
am using an AmiloPro 5515 with integrated via PM900 card;
i didnt work for me ,and even when i try to compile the driver myself i get this error 

checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking if RANDR is defined... no
checking if RENDER is defined... no
checking if XV is defined... no
checking if XF86DRI is defined... no
checking if DPMSExtension is defined... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... configure: error: Package requirements (xorg-server xproto xvmc fontsproto libdrm ) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'xvmc' found
No package 'fontsproto' found
No package 'libdrm' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

----------------------

So can anyone please tell me what exactly i need to do?
it relly sucks when you can't do 3d games on your computer ,or when firefox is on 800x600 resolution !!!
N.B: am on an Amilo Pro 5515

thanks in advance


NB:
Am ready to coperate and work on a better driver if you want :)

Have you successfully installed the necessarily tools?

hmmm are you using the gusty gibbon release? If you are using dapper uncomment the dapper install lines.

---

### Post by Djainette on 2007-11-05
> **TuxCrafter said:**
> ... or i buy a intel onboard graphical card.
Let's group order :D

---

### Post by linfun on 2007-11-05
After a weekend of serious work I never got the VIA xvmc video driver with hardware acceleration to work for smooth dvd/mpeg2 playback. Therefore I am putting this motherboard away for a while (if not forever), The VIA C7 cpu is by the way extremely slow (if you are used a Core2Duo).
Anyway, the script is working, but the code is not fully working, not yet.

Good luck.

---

### Post by giannidr on 2007-11-07
Doesn't work with my VIA Technologies, Inc. Chrome9 HC IGP (rev 01). The script work well, but no supported device detected from glxinfo.

mainboard : Asus P5VD2-VM SE
videocard : Via P4M900

Thanks.

---

### Post by TuxCrafter on 2007-11-08
> **giannidr said:**
> Doesn't work with my VIA Technologies, Inc. Chrome9 HC IGP (rev 01). The script work well, but no supported device detected from glxinfo.

mainboard : Asus P5VD2-VM SE
videocard : Via P4M900

Thanks.

Did you try the experimental branch, the Chrome9 are relative new chip sets.

---

### Post by TuxCrafter on 2007-11-08
Suggestion for openchrome.sh added to the script so new version uploaded.

---

### Post by coady on 2007-11-09
I reinstalled 7.10 and then downloaded and ran the updated 'openschrome.sh' script. It ran without problem, but whereas before running the script I could boot into 'X' and run GDM at only "800x600" screen res, after compiling and running openchrome 'X' and GDM fail and will not load. The 'xorg.conf' looks strange as it has only listed "800x600" screen res (see attached). If I manually edit this to any other res, I cannot run 'X'/GDM at all.

I have compiled the openchrome driver manually many times and in numerous Debian based distros with no trouble in the past and successfully run at "1024x768" screen res with glxgears running at a high frame rate. The chipset will never run 'compiz' etc. but I am not interested in this anyway... just actually using the computer is all I need.

Any help would be greatly appreciated

Here is the output from 'lspci':
```
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0c.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
00:0c.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

```

Thanks and cheers :)

---

### Post by TuxCrafter on 2007-11-10
> **coady said:**
> I reinstalled 7.10 and then downloaded and ran the updated 'openschrome.sh' script. It ran without problem, but whereas before running the script I could boot into 'X' and run GDM at only "800x600" screen res, after compiling and running openchrome 'X' and GDM fail and will not load. The 'xorg.conf' looks strange as it has only listed "800x600" screen res (see attached). If I manually edit this to any other res, I cannot run 'X'/GDM at all.

I have compiled the openchrome driver manually many times and in numerous Debian based distros with no trouble in the past and successfully run at "1024x768" screen res with glxgears running at a high frame rate. The chipset will never run 'compiz' etc. but I am not interested in this anyway... just actually using the computer is all I need.

Any help would be greatly appreciated

Here is the output from 'lspci':
```
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0c.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
00:0c.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

```Thanks and cheers :)

Hi, could you please explain your problem again, I have read it two times but i am not getting the problem, its still early here so it could be me :-p. The drivers installed and xorg has the correct drivers and it runs whats the problem?

---

### Post by coady on 2007-11-10
Sorry, I actually wrote the post very late :( The situation is this:
With a clean install of 7.10, I can boot into the X server and run GDM, load the desktop and log into the system. However, the default screen res is only "800x600" and I know this screen will run at "1024x768".

I then ran the 'openchrome' script. This should allow me to correct the screen res problem, but the only entry for "Modes" under the section is "Screen" is "800x600". The driver has changed from 'vesa' to 'openchrome' which is correct. If I try to edit the 'xorg.conf' by adding "1024x768" (in screen > display > modes), for example, then the X server fails and I cannot run GDM and load the desktop, at all.

In the previously attached 'xorg.conf file, you can see```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"openchrome"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"800x600"
	EndSubSection
EndSection

```
The section 'Modes' should be "1024x768" "800x600" "649x480" (I assume), but if I add these lines I get the failure I described. Sorry if I have not been clear.
Thanks for you help,
coady

---

### Post by coady on 2007-11-10
I don't know if this is any help, but here is the 'xorg.conf' from my installation of ubuntu 7.04 (on the same laptop, ie. FSC Amilo Pro V2030):
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"synaptics"
EndSection

Section "InputDevice"
	Identifier "touchpad"
	Driver "synaptics"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "LeftEdge" "130"
	Option "RightEdge" "840"
	Option "TopEdge" "130"
	Option "BottomEdge" "640"
	Option "FingerLow" "7"
	Option "FingerHigh" "8"
	Option "MaxTapTime" "180"
	Option "MaxTapMove" "110"
	Option "EmulateMidButtonTime" "75"
	Option "VertScrollDelta" "20"
	Option "HorizScrollDelta" "20"
	Option "MinSpeed" "0.25"
	Option "MaxSpeed" "0.75"
	Option "AccelFactor" "0.030"
	Option "EdgeMotionMinSpeed" "200"
	Option "EdgeMotionMaxSpeed" "200"
	Option "UpDownScrolling" "1"
	Option "CircularScrolling" "1"
	Option "CircScrollDelta" "0.1"
	Option "CircScrollTrigger" "2"
	Option "SHMConfig" "on"
	#always usefull
	Option "Emulate3Buttons" "on"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option          "SHMConfig"             "on"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"via"
	BusID		"PCI:1:0:0"
	Option		"SWcursor"	"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	#InputDevice "touchpad" "AlwaysCore"
EndSection

Section "DRI"
	Mode	0666
EndSection
``` 

Thanks again,
coady

---

### Post by TuxCrafter on 2007-11-10
Using the following modeline should work:
    SubSection "Display"
        Depth        16
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection

Maybe you have the same problem that I encountered lately,
The driver would not use any mode of my TFT anymore, I had to add a modeline to my display section...
I will look into it right know

EDIT: I alert the openchrome.sh, please try to reinstall.

---

### Post by TuxCrafter on 2007-11-10
To disable 3D rendering add the following in you xorg.conf file. 3D is causing instability on some of the openchrome systems.

Section "Module"
    Disable "glx"
    Disable "xtrap"
    Disable "record"
    Disable "GLcore"
    Disable "dri"
EndSection

---

### Post by Djainette on 2007-11-10
> **TuxCrafter said:**
> To disable 3D rendering add the following in you xorg.conf file. 3D is causing instability on some of the openchrome systems.

Section "Module"
    Disable "glx"
    Disable "xtrap"
    Disable "record"
    Disable "GLcore"
    Disable "dri"
EndSection
Great, now I can run wine without freezing \o/

---

### Post by coady on 2007-11-10
TuxCrafter, I re-ran the script. It added```
Modes "1024x768" "800x600" "640x480"
``` I can confirm that X server will not run with these settings in the 'xorg.conf'. It will only run if Modes looks like this```
Modes          "800x600"      
``` It does not make a difference if 3D is disabled or not. It also does not matter if "Depth" is set to '16' or to '24'. Here is the current 'xorg.conf' that allows X to run and load the desktop```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"openchrome"
	BusID		"PCI:1:0:0"
	Option		"SwCursor" "On"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes	"800x600"
	EndSubSection
EndSection

#Section "Module"
#	Disable "glx"
#	Disable "xtrap"
#	Disable "record"
#	Disable "GLcore"
#	Disable "dri"
#EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```I have also attached the 'xorg.0.log' file and the information log generated by 'openchrome.sh'

Thanks for you help.
coady

---

### Post by TuxCrafter on 2007-11-10
> **coady said:**
> TuxCrafter, I re-ran the script. It added```
Modes "1024x768" "800x600" "640x480"
``` I can confirm that X server will not run with these settings in the 'xorg.conf'. It will only run if Modes looks like this```
Modes          "800x600"      
``` It does not make a difference if 3D is disabled or not. It also does not matter if "Depth" is set to '16' or to '24'. Here is the current 'xorg.conf' that allows X to run and load the desktop

I have also attached the 'xorg.0.log' file and the information log generated by 'openchrome.sh'

Thanks for you help.
coady

(--) VIA(0): Virtual size is 800x600 (pitch 800)
(II) VIA(0): Trying VBE Mode 800x600 (0xc115) Refresh 60.31:

I don't see the exact problem right know, the openchrome driver is loaded. Please subscripe to the openchrome mailing list and post your info there.

I have the suspicion it has something to do with wrong DDC of your panel and the VDE modes of the driver. You can try a manual modeline, manual panel freq ranges and disable DDC.

---

### Post by coady on 2007-11-10
OK, I will do both things you suggested. This has really had me baffled. Do you have any suggestions as to what I would include in the 'xorg.conf' to add the manual lines you mentioned? Thanks again.
coady

---

### Post by coady on 2007-11-10
> **coady said:**
> ... Do you have any suggestions as to what I would include in the 'xorg.conf' to add the manual lines you mentioned? Thanks again.
coadyI found the following, is this what you had in mind? It is old information, but refers to the same laptop.```
Section "Monitor"
  DisplaySize  280 224
  HorizSync    28-48
  Identifier   "Monitor[0]"
  ModelName    "1024X768@60HZ"
  Option       "DPMS"
  VendorName   "--> VESA"
  VertRefresh  50-60
  UseModes     "Modes[0]"
EndSection
```Again, thanks :)

---

### Post by void_false on 2007-11-11
Oh man! Thank you very much for the script! Installed and worked flawlessly. At last I have decent video performance and can switch between virtual terminals. (Although Direct Rendering says no ???). 
Again. Thanks a lot and keep great work rolling.

P.S. 
I own VIA VN 896 chipset if this helps to anybody. :)

---

### Post by pumpkinegan on 2007-11-11
This does not solve my Chrome9 graphics card problem on a Pentium D.  It is close though, and thank you for your efforts with the script.

I get white horizontal lines in a diagonal direction across the screen and the screen appears to be wrapped in half (that is, the power off button appears just left of center and the applications button appears just right of center).


```
version: 0.1.1
-- -- -- -- --
32: PCI 100.0: 0300 VGA compatible controller (VGA)
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3371
  Unique ID: VCu0.GgJgDwPMNZ6
  Parent ID: vSkL.S16qDHSKEeD
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "Micro-Star International VGA compatible controller"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3371 
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x7255 
  Revision: 0x01
  Memory Range: 0xc0000000-0xdfffffff (rw,prefetchable)
  Memory Range: 0xfd000000-0xfdffffff (rw,non-prefetchable)
  Memory Range: 0xfeaf0000-0xfeafffff (ro,prefetchable,disabled)
  IRQ: 11 (no events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001106d00003371sv00001462sd00007255bc03sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #17 (PCI bridge)

Primary display adapter: #32
-- -- -- -- --
09: PCI 00.0: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_364
  Unique ID: qLht.6OF83IMq_u8
  SysFS ID: /devices/pci0000:00/0000:00:00.0
  SysFS BusID: 0000:00:00.0
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x0364 
  SubVendor: pci 0x1106 "VIA Technologies, Inc."
  SubDevice: pci 0x0364 
  Memory Range: 0xf0000000-0xf7ffffff (rw,prefetchable)
  Module Alias: "pci:v00001106d00000364sv00001106sd00000364bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

10: PCI 00.1: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_1364
  Unique ID: hgAj.cyeUhpBIUfE
  SysFS ID: /devices/pci0000:00/0000:00:00.1
  SysFS BusID: 0000:00:00.1
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x1364 
  SubVendor: pci 0x1106 "VIA Technologies, Inc."
  SubDevice: pci 0x1364 
  Module Alias: "pci:v00001106d00001364sv00001106sd00001364bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

11: PCI 00.2: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_2364
  Unique ID: Z+fY.6X2rJDe9u+4
  SysFS ID: /devices/pci0000:00/0000:00:00.2
  SysFS BusID: 0000:00:00.2
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x2364 
  SubVendor: pci 0x1106 "VIA Technologies, Inc."
  SubDevice: pci 0x2364 
  Module Alias: "pci:v00001106d00002364sv00001106sd00002364bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

12: PCI 00.3: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3364
  Unique ID: QK9O.s7ZTRfJZWoD
  SysFS ID: /devices/pci0000:00/0000:00:00.3
  SysFS BusID: 0000:00:00.3
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3364 
  Module Alias: "pci:v00001106d00003364sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

13: PCI 00.4: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_4364
  Unique ID: HfeD.6grXa8wUn61
  SysFS ID: /devices/pci0000:00/0000:00:00.4
  SysFS BusID: 0000:00:00.4
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x4364 
  SubVendor: pci 0x1106 "VIA Technologies, Inc."
  SubDevice: pci 0x4364 
  Module Alias: "pci:v00001106d00004364sv00001106sd00004364bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

15: PCI 00.6: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_6364
  Unique ID: 0Jdu.ccLtdpw1r1D
  SysFS ID: /devices/pci0000:00/0000:00:00.6
  SysFS BusID: 0000:00:00.6
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x6364 
  Module Alias: "pci:v00001106d00006364sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

16: PCI 00.7: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_7364
  Unique ID: ud6k.smx+hvUIzS5
  SysFS ID: /devices/pci0000:00/0000:00:00.7
  SysFS BusID: 0000:00:00.7
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x7364 
  Module Alias: "pci:v00001106d00007364sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

17: PCI 01.0: 0604 PCI bridge (Normal decode)
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_b198
  Unique ID: vSkL.S16qDHSKEeD
  SysFS ID: /devices/pci0000:00/0000:00:01.0
  SysFS BusID: 0000:00:01.0
  Hardware Class: bridge
  Model: "VIA VT8237 PCI Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0xb198 "VT8237 PCI Bridge"
  Module Alias: "pci:v00001106d0000B198sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

18: PCI 02.0: 0604 PCI bridge (Normal decode)
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_a364
  Unique ID: _Znp.g78+51qvkd0
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: bridge
  Model: "VIA PCI bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0xa364 
  Revision: 0x80
  Driver: "pcieport-driver"
  IRQ: 27 (no events)
  Module Alias: "pci:v00001106d0000A364sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

19: PCI 03.0: 0604 PCI bridge (Normal decode)
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_c364
  Unique ID: 3hqH.ASKGEfPHzS4
  SysFS ID: /devices/pci0000:00/0000:00:03.0
  SysFS BusID: 0000:00:03.0
  Hardware Class: bridge
  Model: "VIA PCI bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0xc364 
  Revision: 0x80
  Driver: "pcieport-driver"
  IRQ: 31 (no events)
  Module Alias: "pci:v00001106d0000C364sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

27: PCI 11.0: 0601 ISA bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3337
  Unique ID: 7EWs.PUIb66z2lP9
  SysFS ID: /devices/pci0000:00/0000:00:11.0
  SysFS BusID: 0000:00:11.0
  Hardware Class: bridge
  Model: "Micro-Star International VT8237A PCI to ISA Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3337 "VT8237A PCI to ISA Bridge"
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x7255 
  Module Alias: "pci:v00001106d00003337sv00001462sd00007255bc06sc01i00"
  Driver Info #0:
    Driver Status: i2c_viapro is active
    Driver Activation Cmd: "modprobe i2c_viapro"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

28: PCI 11.7: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_287e
  Unique ID: BWxi.NhM1uBZ0XP5
  SysFS ID: /devices/pci0000:00/0000:00:11.7
  SysFS BusID: 0000:00:11.7
  Hardware Class: bridge
  Model: "VIA VT8251 Ultra VLINK Controller"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x287e "VT8251 Ultra VLINK Controller"
  SubVendor: pci 0x1106 "VIA Technologies, Inc."
  SubDevice: pci 0x337e 
  Module Alias: "pci:v00001106d0000287Esv00001106sd0000337Ebc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

30: PCI 13.0: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_337b
  Unique ID: HSco.jfGiUiN+dB5
  SysFS ID: /devices/pci0000:00/0000:00:13.0
  SysFS BusID: 0000:00:13.0
  Hardware Class: bridge
  Model: "VIA VT8237A PCI to PCIE Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x337b "VT8237A PCI to PCIE Bridge"
  Module Alias: "pci:v00001106d0000337Bsv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

31: PCI 13.1: 0604 PCI bridge (Subtractive decode)
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_337a
  Unique ID: 9n5e.HHSMJjh6gC5
  SysFS ID: /devices/pci0000:00/0000:00:13.1
  SysFS BusID: 0000:00:13.1
  Hardware Class: bridge
  Model: "VIA VT8237A PCI to PCI Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x337a "VT8237A PCI to PCI Bridge"
  Module Alias: "pci:v00001106d0000337Asv00000000sd00000000bc06sc04i01"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
-- -- -- -- --
00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
-- -- -- -- --
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"openchrome"
	BusID		"PCI:1:0:0"
EndSection

Section "Module"
	Disable "glx"
	Disable "xtrap"
	Disable "record"
	Disable "GLcore"
	Disable "dri"
EndSection

Section "Monitor"
	Identifier	"M220Z1_L01"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"M220Z1_L01"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x192"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

---

### Post by TuxCrafter on 2007-11-12
> **pumpkinegan said:**
> This does not solve my Chrome9 graphics card problem on a Pentium D.  It is close though, and thank you for your efforts with the script.

I get white horizontal lines in a diagonal direction across the screen and the screen appears to be wrapped in half (that is, the power off button appears just left of center and the applications button appears just right of center).


Please report your problem on the opensource mailinglist, to see if they can help you. (ps the logs could be attached as attachment in you message)

---

### Post by Propaganda on 2007-11-12
Thanks a lot for this script, it worked fine on my Fujitsu Siemens Amilo Pro V3515. I only had to change the monitor from Plug&Play to LCD Panel 1280x800 after using your script.
The highest screen resolution I can choose with this monitor is 1024x768, any ideas why 1280x800 is not listed there?

3D is not working but that doesn't matter, afaik there is no 3D support for my graphics card, so I didn't expect it to work. Also this laptop is a present for my mother, she wants to have a computer for writing documents, internet and collecting her digital images, that should work fine with just 2D support, shouldn't?

I've attached the log your script created, if you want to have a look at it.

You rescued this project, my sisters wanted me to install windows after they saw the 800x600 resolution, that was the highest possible before :)

---

### Post by void_false on 2007-11-12
> The highest screen resolution I can choose with this monitor is 1024x768, any ideas why 1280x800 is not listed there?

Type in terminal 
gtf 1280 800 60 and then paste the output to /etc/X11/xorg.conf in Monitor section like that:

```
Section "Monitor"
        Identifier      "Failsafe Monitor"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1280x800"
        Horizsync       31.5-50.0
        Vertrefresh     56.0 - 65.0
         # 1280x800 @ 60.00 Hz (GTF) hsync: 49.68 kHz; pclk: 83.46 MHz
        Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync

        Gamma   1.0

EndSection
```

---

### Post by coady on 2007-11-13
> **TuxCrafter said:**
> (--) VIA(0): Virtual size is 800x600 (pitch 800)
(II) VIA(0): Trying VBE Mode 800x600 (0xc115) Refresh 60.31:

I don't see the exact problem right know, the openchrome driver is loaded. Please subscripe to the openchrome mailing list and post your info there.

I have the suspicion it has something to do with wrong DDC of your panel and the VDE modes of the driver. You can try a manual modeline, manual panel freq ranges and disable DDC.TuxCrafter,
I have followed this up on the openchrome user list and resolved it, but not for Ubuntu 7.10, only for my installation of Fedora 8!

WIth Fedora the problem (noticed by a very persistent and dedicated developer) was that the default setting for SELinux is 'restrictive'. Even though the file permissions on 'xorg.conf' seemed to be OK I needed to set SELinux to 'permissive'.

I am not sure why this was a problem. I think the answer is that when I was originally setting up the partitions with the new distro's (Fedora, Ubuntu, etc.) I used a live CD to boot in and make some changes. As I recall I may have edited the 'xorg.conf' file in Fedora (and Ubuntu) to save time but I don't remember exactly. Changing the SELinux setting immediately solved the problem, however. So Fedora is running "1024x768" screen res and using the openchrome driver on the same laptop as Ubuntu, but Ubuntu keeps failing to run the X server and then reverts to a failsafe 'xorg.conf'.

Do you have any ideas what the problem might be in Ubuntu? Do you think the permissions/SELinux issue could be a similar problem in Ubuntu 7.10? 

I have attached the 'Xorg.0.log' again. The only problem I can see is the following lines (but I am not an authority on this ;))```
(II) VIA: driver for VIA chipsets: CLE266, KM400/KN400, K8M800,
	PM800/PM880/CN400, VM800/CN700/P4M800Pro, K8M890, P4M900/VN896,
	CX700, P4M890
(II) Primary Device is: PCI 01:00:0
(--) Chipset **VM800/CN700/P4M800Pro** found
(!!) VIA Technologies does not support or endorse this driver in any way.
(!!) For support, please refer to http://www.openchrome.org/ or
(!!) your X vendor.
```My laptop has the 'CN700/**VN800**/P4M800CE/Pro' chipset and not the one identified in the log (above). Something is wrong here. It looks like the chipset is being incorrectly identified. The openchrome driver has been working for the VIA **VN800** in previous Debian based distributions and is currently working in other distro's. Any ideas...?
All the best, and thanks.
coady

EDIT: I have been checking the 'Xorg.0.log' files of some archived debian distributions where I compiled and used the openchrome driver on this laptop with the VIA VN800 chipset. They all show very different responses for 'Chipset found' so my comments above may not be so decisive.

However, any help anyone can provide is greatly appreciated!

---

### Post by Propaganda on 2007-11-13
> **void_false said:**
> Type in terminal 
gtf 1280 800 60 and then paste the output to /etc/X11/xorg.conf in Monitor section

That worked, thanks a lot.

---

### Post by smellydog on 2007-11-15
> **mahousaru said:**
> Many thanks TuxCrafter this is an absolutely great script.  Worked on my VIA Unichrome Pro PN800 with no errors.  I can actually run Google Earth now, but I still get the wine freeze I had with the S3 drivers.  If I don't disable dri in xconf my laptop locks up if I run wine.  Does anyone know of any resolutions to this?

If i don't disable dri then if i run glxinfo I get a seg fault.  If I do disable it i loose direct rendering :( 

Anyway still an improvement from before, thanks again

I'm running Ubuntu 7.10, currently with disable dri in the xorg.conf.

How did you disable dri in your xorg.conf? 

Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Driver		"via"
	BusID		"PCI:1:0:0"
**	Option		"DisableDRI"**
EndSection

Like so?

---

### Post by TuxCrafter on 2007-11-15
Thanks for all the positive feedback that is why I do it.

To disable 3D rendering add the following in you xorg.conf file. 3D is causing instability on some of the openchrome systems. (this info is also in the fists post of this topic)

```
Section "Module"
    Disable "glx"
    Disable "xtrap"
    Disable "record"
    Disable "GLcore"
    Disable "dri"
EndSection
```

---

### Post by coady on 2007-11-16
Any ideas... I would be very grateful. Thanks

---

### Post by supercompman on 2007-11-16
First, I want to say thanks for this script. It worked very well for me. The openchrome driver that is packaged for Gutsy is not at all stable on this system (it's a gOS Development Kit board; video is CN700) but this script creates a driver and configures X so that it is very stable. 3D works pretty well (as well as I could expect for this video chip), Xv works well, and the 2D rendering seems very snappy. There are few things I have noticed however. Running Wine causes a hard lock of the system when using this driver; if I switch to the VESA driver, Wine works fine. I don't know if this is Wine's fault or this driver. When I start the game Neverball, in the title screen, the title is missing. It's just a white texture. Again, I don't know if the game or the driver is the cause of it. Just thought I would share my experiences and see if anyone has had the same problems and might have solutions.

---

### Post by TuxCrafter on 2007-11-16
> **supercompman said:**
> First, I want to say thanks for this script. It worked very well for me. The openchrome driver that is packaged for Gutsy is not at all stable on this system (it's a gOS Development Kit board; video is CN700) but this script creates a driver and configures X so that it is very stable. 3D works pretty well (as well as I could expect for this video chip), Xv works well, and the 2D rendering seems very snappy. There are few things I have noticed however. Running Wine causes a hard lock of the system when using this driver; if I switch to the VESA driver, Wine works fine. I don't know if this is Wine's fault or this driver. When I start the game Neverball, in the title screen, the title is missing. It's just a white texture. Again, I don't know if the game or the driver is the cause of it. Just thought I would share my experiences and see if anyone has had the same problems and might have solutions.

There are still bugs in the 3D mesa driver in combination i with the via hardware that is causing lockups. Tho solve the lockups in wine disable the 3D rendering as explained in the first topic of the post,

---

### Post by supercompman on 2007-11-16
Thanks for the quick reply TuxCrafter.

---

### Post by mwoc on 2007-11-17
Hi there.

I'm new here, and join this forum looking for some help.

I want warning you, that my english is very sad, but I don't find a solution to my problem.

I use the openchrome.sh to download and compile the openchrome driver, but when the installation is complete, gdm doesn't works, 

If I stop the gdm and run startx in the prompt, the X inits, but freeze in a few minutes, or few seconds.

Here some informations about my laptop, if you can help me, I will be very happy.

My video card is:
VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)


```
00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)
06:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

```

---

### Post by TuxCrafter on 2007-11-17
> **mwoc said:**
> Hi there.

I'm new here, and join this forum looking for some help.

I want warning you, that my english is very sad, but I don't find a solution to my problem.

I use the openchrome.sh to download and compile the openchrome driver, but when the installation is complete, gdm doesn't works, 

If I stop the gdm and run startx in the prompt, the X inits, but freeze in a few minutes, or few seconds.

Here some informations about my laptop, if you can help me, I will be very happy.

My video card is:
VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)

Please joint the openchrome maillinglist and post your problem including the file with information the openchrome.sh script provides. Hope they can help you.

---

### Post by f37u5g0d on 2007-11-19
I ran the script but I am still not able to run the desktop effects or compiz - fusion.  Also my games that use Open GL don't run at all (neverball & neverputt).

---

### Post by TuxCrafter on 2007-11-19
> **f37u5g0d said:**
> I ran the script but I am still not able to run the desktop effects or compiz - fusion.  Also my games that use Open GL don't run at all (neverball & neverputt).

The mesa 3D driver for via chipsets does not support compiz, and opengl is not stable. See the openchrome project website for more information.

---

### Post by f37u5g0d on 2007-11-19
Is there a driver that does support those features for the via unichrome pro chipset?  (I have a cn700),

---

### Post by TuxCrafter on 2007-11-19
> **f37u5g0d said:**
> Is there a driver that does support those features for the via unichrome pro chipset?  (I have a cn700),

Nope not yet maybe over a few years, to bad...

---

### Post by mpieru on 2007-11-21
The script works well, but i cannot get the driver working...
i have this error on Xorg.0.log:

(....)
(EE) VIA-0: Unknown Card-IDs (1462|7255); please report to [email]openchrome-users@openchrome.org[/email]


I think to have tested both branchs (trunk/experimental). Is there a way to test which version is currently loaded (i'm working on runlevel 2, text only) ?

---

### Post by TuxCrafter on 2007-11-21
> **mpieru said:**
> The script works well, but i cannot get the driver working...
i have this error on Xorg.0.log:

(....)
(EE) VIA-0: Unknown Card-IDs (1462|7255); please report to [EMAIL="openchrome-users@openchrome.org"]openchrome-users@openchrome.org[/EMAIL]


I think to have tested both branchs (trunk/experimental). Is there a way to test which version is currently loaded (i'm working on runlevel 2, text only) ?


please report to the openchrome mailing list they have to add your Card-ID's [EMAIL="openchrome-users@openchrome.org"]openchrome-users@openchrome.org[/EMAIL]

Please include the log file the script created when mailling the list.

---

### Post by riussimbolon on 2007-11-22
hi dear...
please help me, i install ubuntu gusty gibbon
i not found driver vga "via", if i use driver vga "via" in xorg.conf blank screen when resarted

this result: lspci

00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP [VIA P4M890 Chipset] (rev 01)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

please help me. ASAP

---

### Post by TuxCrafter on 2007-11-22
Please use the openchrome script to setup the xorg file. The driver should be named "openchrome" instead of "via".

---

### Post by coady on 2007-11-24
> **coady said:**
> TuxCrafter,
I have followed this up on the openchrome user list and resolved it, but not for Ubuntu 7.10, only for my installation of Fedora 8!
I have resolved this issue after much research and the kind help of the openchrome devs. Please see the following thread for the details:

[Problem: Openchrome, Ubuntu 7.10, and VN800 [Solved]]("http://ubuntuforums.org/showpost.php?p=3829543&postcount=3")

coady

---

### Post by DaveRowell on 2007-11-24
The install script worked flawlessly as far as I can tell.  There were no error messages.  Install was pretty quick.  ;-)

BUT: The on-screen fonts are jagged and ugly - the cursor is displayed on top of the screen saver (I tried several) in a square block that pulsates slowly - nothing short of cycling the power would break out of the screen saver - displayed colors don't seem as vivid.

Compaq Presario SR1265 - 1 GB - KM400/A - VT8378 S3 UniChrome - Ubuntu 7.10, Gutsy

I am having issues with Gutsy and will reformat and fresh install Feisty, 7.04 this afternoon.  I will NOT be reinstalling the OpenChrome drivers.

---

### Post by killme on 2007-11-26
Finally.  Wine works again!!!!

I was about to scrap Gutsy, reformat and reinstall Feisty from the CD.  The xorg-video-via drivers are garbage...

Thanks for that script! :)
Now if I can only get my SanDisk 5 in 1 working again... :(

---

### Post by TuxCrafter on 2007-11-26
> **killme said:**
> Finally.  Wine works again!!!!

I was about to scrap Gutsy, reformat and reinstall Feisty from the CD.  The xorg-video-via drivers are garbage...

Thanks for that script! :)
Now if I can only get my SanDisk 5 in 1 working again... :(

No problem, nice the script helped you, What is that SanDisk 5 in 1 for device, is this a card reader? If so just buy a new one for 18 euro's it is not worth the hassle :-p. Or it's a build in device in a laptop that would be different.

---

### Post by steveo_mcg on 2007-11-29
Thanks for the script. There was one unresolved dependency which i never couldn't work out libviaxvmc1. Two quick questions, should the driver be via or openchrome? What is that file? I'm guessing that the file hasn't in fact installed but the via drivers under lenny support widescreen, so while the screen is good and crisp its going to be unusable for mpg.

---

### Post by TuxCrafter on 2007-11-30
> **steveo_mcg said:**
> Thanks for the script. There was one unresolved dependency which i never couldn't work out libviaxvmc1. Two quick questions, should the driver be via or openchrome? What is that file? I'm guessing that the file hasn't in fact installed but the via drivers under lenny support widescreen, so while the screen is good and crisp its going to be unusable for mpg.

The drivers name is openchrome, and should be used in the xorg.conf file. I do not understand the rest of you comments.

Hope this helped you.

---

### Post by steveo_mcg on 2007-11-30
Sorry i'll try to be clear this time :)

I ran the script and it seemed to compile ok, it left me with a .deb file. When i try to install said deb it fails with a dependency error" libviaxvmc1" this file doesn't appear in the lenny repos.  
I ran dpkg-reconfig and set tried the via dirver, which i was sure i uninstalled so i assumed that was something installed by the scripts. I also reset the screen resolution to 1440x900 which wasn't supported before but now is, However it's starting to look like the via driver in lenny supports widescreen, it wasn't supported in etch.

---

### Post by TuxCrafter on 2007-11-30
> **steveo_mcg said:**
> Sorry i'll try to be clear this time :)

I ran the script and it seemed to compile ok, it left me with a .deb file. When i try to install said deb it fails with a dependency error" libviaxvmc1" this file doesn't appear in the lenny repos.  
I ran dpkg-reconfig and set tried the via dirver, which i was sure i uninstalled so i assumed that was something installed by the scripts. I also reset the screen resolution to 1440x900 which wasn't supported before but now is, However it's starting to look like the via driver in lenny supports widescreen, it wasn't supported in etch.

Please use the last openchrome script in the first post. This script should not create a deb file and will work fine. It will also give you the option to automatically setup xorg to use the openchrome driver. You should be able to just run the script then restart the computer and the openchrome driver will be used. Also this script has been made for the gusty release.

---

### Post by ineiti on 2007-12-02
Hi,
finally I managed to get the thing working, kind of. Material is:

Amilo La 1703
PCI-Id: 0x1106, 0x3230

To install using VESA I had to append
BOOT_DEBUG=3
and then, after the graphic-boot fails, change to the first console (<alt>+<f1>) and type "startx". Normal installation follows.

After installation, the script works fine, only I can't restart the X-server! So I can go into rescue-mode and type "startx" and it works. But as soon as I try to quit the server (<ctrl><alt><bs>), it turns white and nothing works anymore!

As the normal startup seems to restart the server at least once, I can't let it startup normally... Too bad.

Anyone solved this one?

Thanks,

Ineiti

---

### Post by TheArseneLupin on 2007-12-03
hi all

i tried to install with the newely added script ,but it doesnt work .This si the error i got :
...create new symbolic link
Prepare the installation files [Y/n]?Y
Install the via openchrome 2D driver [Y/n]?Y
svn: Échec de la requête PROPFIND sur '/svn/branches/experimental_branch'
svn: PROPFIND de '/svn/branches/experimental_branch': Could not resolve hostname `svn.openchrome.org': Aucune adresse associ  e avec le nom de l'h  te ([http://svn.openchrome.org](http://svn.openchrome.org))
./openchrome.sh: line 77: cd: openchrome: Aucun fichier ou répertoire de ce type
./openchrome.sh: line 78: ./autogen.sh: Aucun fichier ou répertoire de ce type
make: *** Pas de cibles spécifiées et aucun makefile n'a été trouvé. Arrêt.
make: *** Pas de règle pour fabriquer la cible « install ». Arrêt.
--------------

am using AmiloPro 5515 with gcard via PME900

when i want to complie the driver ,i get error (xorg-server ,xproto ,xvmc .. not found )
i couldnt install them with apt get ,neither i found them on any repos on the net !!!!
so what can i do to make this card work??

---

### Post by TuxCrafter on 2007-12-03
> **TheArseneLupin said:**
> hi all

i tried to install with the newely added script ,but it doesnt work .This si the error i got :
...create new symbolic link
Prepare the installation files [Y/n]?Y
Install the via openchrome 2D driver [Y/n]?Y
svn: Échec de la requête PROPFIND sur '/svn/branches/experimental_branch'
svn: PROPFIND de '/svn/branches/experimental_branch': Could not resolve hostname `svn.openchrome.org': Aucune adresse associ  e avec le nom de l'h  te ([http://svn.openchrome.org](http://svn.openchrome.org))
./openchrome.sh: line 77: cd: openchrome: Aucun fichier ou répertoire de ce type
./openchrome.sh: line 78: ./autogen.sh: Aucun fichier ou répertoire de ce type
make: *** Pas de cibles spécifiées et aucun makefile n'a été trouvé. Arrêt.
make: *** Pas de règle pour fabriquer la cible « install ». Arrêt.
--------------

am using AmiloPro 5515 with gcard via PME900

when i want to complie the driver ,i get error (xorg-server ,xproto ,xvmc .. not found )
i couldnt install them with apt get ,neither i found them on any repos on the net !!!!
so what can i do to make this card work??


Hello,

It seem you cannot reach the openchrome website, i just tested it and on this moment i advice you to retry. You also need a working internet connection to be able to download the files. I hope it works now.

```
svn co http://svn.openchrome.org/svn/branches/experimental_branch openchrome  
```

---

### Post by MoridinBG on 2007-12-04
The script almost did it for me. Everything downloaded and compiled with no problems, but there are some problems when starting X. Without the VBE option the screen is blanc (the Wiki states VBe is needed for CX700M(2). 

With VBE KDM starts, the cursor appears, I can move it, but after 3 or 4 seconds the screen turns black. Ctrl+Alt+FX doesn't do anything. At the end of Xorg.0.log it seems that the driver unloads itself.

Disabling dri/glx/whatever doesn't help. Neither do loading drm and via modules. EnableAGPDMA "false" doesn't do anything too.

And what is more interesting Vesa stopped working too o.O
Again, cursor appears, loads fo a while and then drops me into terminal. Shock. No errors in Xorg.0.log

---

### Post by TuxCrafter on 2007-12-04
> **MoridinBG said:**
> The script almost did it for me. Everything downloaded and compiled with no problems, but there are some problems when starting X. Without the VBE option the screen is blanc (the Wiki states VBe is needed for CX700M(2). 

With VBE KDM starts, the cursor appears, I can move it, but after 3 or 4 seconds the screen turns black. Ctrl+Alt+FX doesn't do anything. At the end of Xorg.0.log it seems that the driver unloads itself.

Disabling dri/glx/whatever doesn't help. Neither do loading drm and via modules. EnableAGPDMA "false" doesn't do anything too.

And what is more interesting Vesa stopped working too o.O
Again, cursor appears, loads fo a while and then drops me into terminal. Shock. No errors in Xorg.0.log

If the vesa driver doesn't work either the problem is probably something else, and not related to openchrome driver.

If the problem remains, I advice you to subscribe to the openchrome mailing list. Hopefully they can help, they will ask you for all the debug information you can get related tot the problem.

---

### Post by MoridinBG on 2007-12-04
The whole setup was a mess after two days of fighting the WiFi, video and sound. And the installation from the beginning was a mess (upgraded Vmware base install to native kubuntu...), so I did fresh reinstall of ubuntu and will try the script again.

EDIT: OK, this time it worked. Only for 640x480. I played with VIA proprietary drivers, there I got just white screen, no matter the resoliution. And what is more interesting, if i startx in recovery (root) mode it starts with 800x480. Immediate reboot into normal mode and the screen just blinks for a fraction of the second with cursor in the middle and then it fils with colors (mostly red :-D).

So 640x480 in user mode and 800x480 in root mode..

---

### Post by MoridinBG on 2007-12-06
First of all sorry for writing after my own message, but a little bump is needed.

I almost found the problem. As I mentioned before X works in single user mode. But I found out that the user mode is not the problem. The problem seems to be in GMD. I found out that if I start GMD as root even in single mode the screen is scrambled too.
If I start in normal mode and then "sudo startx" (avoiding GDM) X starts at 800x480, but as Super User (Not a good thing). 

And as a regular user I can start with GDM only at 640x480. "startx" obviously is disabled for normal users (startx as normal user tells me it is disabled for users).

It seems that something breaks GDM for 800x480. I wouldn't mind if I disable it and have to log in text mode and then type startx. In fact I have been doing this all the way from Slackware 9.1 to 11. Just how to enable startx for normal user?

Also another question. Is there a way to scale the screen? Under windows I can switch between a number of display resolutions and they are all scaled to fit the 800x480 panel. There is ignorable loss of quality, but for example 1024x600 is just fine.

---

### Post by ShinBaba on 2007-12-07
Hello TuxCrafter,
I cannot get DRI working on my VN800 on a fresh Gutsy. The problem is with **libdri.so**, which doesn't load, because it cannot find the symbol **drmSetServerInfo**.

I had to move/rename libdri.so to make X start. Otherwise, the only thing I get would be a black screen.

- Kernel is 2.6.22-14-generic
- Mesa is 7.0

Any suggestions?

Thank You in advance...
ShinBaba

---

### Post by xfaethorx on 2007-12-09
The script worked for on Gutsy nicely..

However I only have 640x480 as an available resolution! Now this might be down to the mini itx board im running which is an EPIA EN 12000 and i think theres some oddities there but i've not had it confirmed.

I diffed the version of xorg.conf before and after the file change and the only difference was OpenChrome replacing the default vesa driver. 

It hadn't mangled any other settings in that file...


I wondered if anyone had encountered this and had a resolution for it?
I'm stumped at my side as it jsut seems that the driver wont give me higher resolutions...

any ideas?

---

### Post by Peter09 on 2007-12-09
Ihave exactly the same problem on a friends computer, If I run the script it works but only in 800x600. :(

---

### Post by tech0007 on 2007-12-09
Hi,

Try the binary driver from VIA.  I got 3D finally working on Gutsy.  I think they have one for Feisty.

Check this link:  [http://ubuntuforums.org/showthread.php?t=636368](http://ubuntuforums.org/showthread.php?t=636368).

Good luck.

---

### Post by teseglet on 2007-12-09
I've worked with Windows computers for a number of years but am new to Linux having bought one of those $199 Everex machines just to see what Linux is about.  I installed Ubuntu on it in place of gOS and have been happy with all but my Via graphics package.  I have installed Openchrome via the Synaptic Program Manager as well as through the help of another Ubuntu forum but now have issues with my screensaver (kicks me out to the reboot screen).  I also don't have 3D graphics.  From your forum it seems installing the latest Openchrome.sh script is the way to go.

However, I'm such a newbie I don't know where to download your script to or what command to enter in the terminal to get it going.  Any guidance that could be provided would be appreciated.  In all the pages of the forum nobody started from the very beginning.

---

### Post by Djainette on 2007-12-10
> **teseglet said:**
> I've worked with Windows computers for a number of years but am new to Linux having bought one of those $199 Everex machines just to see what Linux is about.  I installed Ubuntu on it in place of gOS and have been happy with all but my Via graphics package.  I have installed Openchrome via the Synaptic Program Manager as well as through the help of another Ubuntu forum but now have issues with my screensaver (kicks me out to the reboot screen).  I also don't have 3D graphics.  From your forum it seems installing the latest Openchrome.sh script is the way to go.

However, I'm such a newbie I don't know where to download your script to or what command to enter in the terminal to get it going.  Any guidance that could be provided would be appreciated.  In all the pages of the forum nobody started from the very beginning.

First of all, go to the first post of this thread and download the attachment into your home folder.
Then open a terminal (you should end up in your home folder).
type 
```
chmod 755 openchrome.sh
```
to make the script executable then
```
sudo ./openchromesh
```
to launch it. Follow the script instructions.

---

### Post by agsamek on 2007-12-11
Amilo Pro v3515, Ubuntu 7.04, VN896 and the script worked perfectly. Thanks!

---

### Post by fitlad on 2007-12-15
Thanks a million :) you have helped me to install my graphic card on my Amilo Pro V2030 and it's working like a charm :KS. I wouldn't be able to sort it out without your support. :popcorn:

---

### Post by TuxCrafter on 2007-12-15
> **fitlad said:**
> Thanks a million :) you have helped me to install my graphic card on my Amilo Pro V2030 and it's working like a charm :KS. I wouldn't be able to sort it out without your support. :popcorn:

Thanks for your feedback, this is always welcome.

---

### Post by Bawl on 2007-12-15
> **&#1050 said:**
> It does not work for me. I have Fujitsu-Siemens AMILO Pro V2030, Intel Celeron 1.4GHz, 512MB of ram, Chipset Via P4M800CE, Via S3G UniChrome Pro IGP. I have installed fresh copy of new Ubuntu 7.10. The script ran well (did not ask for installation of 3D driver), and the xorg.conf file has changed to VIA driver etc., but then, after reboot, there was a mess with the colours and I had to do sudo dpkg-reconfigure -phigh xserver-xorg. Any ideas? Thanks in advance.:(

EDIT: Never mind. It's now open SUSE on that laptop since the modem is not supported by Ubuntu, too.

I second this. I'm sitting with the exact same laptop, (trying to liberate my parents) :) and oddly enough the screen works perfectly in 1024x768 in the NCURSES installer (Ubuntu Alternate Install CD), but when it boots the very first time, nothing higher than 800x600 is availiable as resolution.

Having read the first couple of pages in this post, and tried the script (which completed without a hitch), I simply end up with a "defective" x-server on reboot, and my linux know-how is limited enough to that being a problem.

I tried downloading the latest SuSE KDE CD instead, and it also boots the installer in 1024x768 without problems. It, however, froze on me, after a few pages of preliminary setup and on reboot it simply refused to show anything.
When I eject the CD, though, the screen changes from black to visible output, and I see some error message, about not being able to read from the CD, because it was removed.


My thoughts was that it must be less of a hassle to get it working, as it appears to work just jolly and dandy in the NCURSES-installer. That shows it must be working already?

EDIT: I see however, that it should somehow be possible to get it working, but I'd sure like to know what 'fitlad' did, besides following the instructions.

> **fitlad said:**
> Thanks a million :) you have helped me to install my graphic card on my Amilo Pro V2030 and it's working like a charm :KS. I wouldn't be able to sort it out without your support. :popcorn:

---

### Post by ma_tomim on 2007-12-20
Hi,

I used the script and everything seemed to be OK, until I restarted the X server. The screen resolution that used to be 1280x1024 became 800x600. I tried to use ubuntu gutsy' s GUI to change screen settings, but the only option available was 800x600. Ho do I make it go back to normal, i.e., 1280x1024?

Thanks for the effort put into this script!

---

### Post by TuxCrafter on 2007-12-20
> **ma_tomim said:**
> Hi,

I used the script and everything seemed to be OK, until I restarted the X server. The screen resolution that used to be 1280x1024 became 800x600. I tried to use ubuntu gutsy' s GUI to change screen settings, but the only option available was 800x600. Ho do I make it go back to normal, i.e., 1280x1024?

Thanks for the effort put into this script!

Hmm, this is getting strange I am hearing a lot of people talking about the 800x600 resolution and the driver. I think you need to check your xorg logs and maybe set a the settings in you monitor section (hor, ver freq, resolution etcetra)

I will recompile my openchrome driver and see if it still works.

---

### Post by TuxCrafter on 2007-12-20
I just recompiled my driver and I can confirm there is a major issue with the experimental release, my resolution also dropped to a minimal like 800x600.

I did some testing and I tested the stable branch, and my resolution is fine again.

So for everybody with problems used the newly added openchrome-stable.sh script and see if you problem get solved.

Hope this helps everybody.

---

### Post by ma_tomim on 2007-12-20
Thanks for the new script!
Now the resolution is fine, 1280x1024 as it was supposed to be.
However, when I execute glxinfo, the whole computer freezes. The only alternative left to me was switching back to via driver. I know the 3D rendering works, with the via driver, because the high number of frames per second yielded by glxgears, even though glxinfo still ends with a segmentation fault. I am sending enclosed the hardware info file generated by the openchrome-stable script for more information regarding my computer.

My objective is to make 2D and 3D rendering work along with wine, which also freezes whenever glx and dri modules are loaded. Any ideas on how to that?

Thanks for your attention.

---

### Post by TuxCrafter on 2007-12-20
> **ma_tomim said:**
> Thanks for the new script!
Now the resolution is fine, 1280x1024 as it was supposed to be.
However, when I execute glxinfo, the whole computer freezes. The only alternative left to me was switching back to via driver. I know the 3D rendering works, with the via driver, because the high number of frames per second yielded by glxgears, even though glxinfo still ends with a segmentation fault. I am sending enclosed the hardware info file generated by the openchrome-stable script for more information regarding my computer.

My objective is to make 2D and 3D rendering work along with wine, which also freezes whenever glx and dri modules are loaded. Any ideas on how to that?

Thanks for your attention.

My advice is to disable 3D totally on via chipsets, 3D (opengl) is very unstable and can cause complete system lockups. In the first post you can find information how to disable 3D rendering.

---

### Post by chowanec on 2007-12-21
> **harrydb said:**
> Great script, worked like charm. 

However some configurations (like mine) require 
```
Option "VBEModes" "true"
```
in xorg.conf, to work with a panel display (on the dvi port in my case) otherwise X will run but the display just turns black. For those chipsets it might be nice if the script asks whether you are using a panel display (on the dvi port?) and if so add the above line to xorg.conf (if chosen to configure x).

The following page gives an overview of which chipsets need that option: [http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats)
Maybe the current chipset can be detected with 'lspci' or something.

Regards,
Harry

This little tweak worked for me as well -- thank you, thank you, thank you.  Seriously, this script is a god-send... I was beginning to think I would NEVER get Mint running on my mini-ITX!

If there were paypal, I'd donate. :P

---

### Post by TuxCrafter on 2007-12-22
> **chowanec said:**
> This little tweak worked for me as well -- thank you, thank you, thank you.  Seriously, this script is a god-send... I was beginning to think I would NEVER get Mint running on my mini-ITX!

If there were paypal, I'd donate. :P

Thanks for the feedback, this is always welcome.

---

### Post by Houssema on 2007-12-27
This is the log i got after launching the script ;
i didnt work for me the first time
i ll try an other time ;
now it works ,but the cursor of the mouse doesnt appear properly;it's just like a " | " that moves only vertically;

---

### Post by Houssema on 2007-12-30
Salem guys,

does anybody know a solution for the problem i posted (the mouse cursor doesnt appear anymore ,i can guess it's position sometimes ,and when i click the action associated is done ,but i still cant see the cursor);
In fact ,i have a  other problem ,when i play avi files ,the picture is decaled to the left pf my screen ,and there is a rectangle on the right where there is no images at all ?? 

have a nice day/dream ,babay

---

### Post by TuxCrafter on 2007-12-30
Have you tried the softcursor option?
See the "man openchrome"

---

### Post by Houssema on 2007-12-30
Salem bro
Thanks TuxCrafter for your unvaluable help ;
excuse me to ask such a silly question ,but should i add that in  xorg.conf

in this section for example :
Section "Device"
	Identifier	"Carte vidéo générique"
	Driver		"openchrome"
	BusID		"PCI:1:0:0"
        Option          "SWCursor" "true"
EndSection

---

### Post by TuxCrafter on 2007-12-30
> **Houssema said:**
> Salem bro
Thanks TuxCrafter for your unvaluable help ;
excuse me to ask such a silly question ,but should i add that in the beginning of xorg.conf

open the xorg.conf file as root and make the matching section look like below:

```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "openchrome"
        Option         "EnableAGPDMA" "false"
        Option         "HWCursor"  "false"
        BusID          "PCI:1:0:0"
EndSection
```

---

### Post by Houssema on 2007-12-30
Thanks man  ,that solved the problem of the cursor ,but unfortunately i still have that unclear zone (in the right of my screen everytime  i play video files;
so i just want to ask you if there is any solution to that ;
and something else Option "VBEModes" "true" ,what is it exactly for ?

thanks in advance:KS

Rmrque:
I triedto include a screenshot of my video display (while playing video files) ,but the screenshot is black (several times)

---

### Post by Houssema on 2007-12-30
i guess i should use this option "NoXVDMA" "true"
,what do u guys think ??

---

### Post by srn on 2008-01-02
I own a Via Epia EN1200 board and the script seems to work smoothly but the desktop seems to run with few colours making it hard to make out text and browsing looks just awful. I've attached an image of the default Firefox window. Any help would be greatly appreciated.

---

### Post by TuxCrafter on 2008-01-02
> **srn said:**
> I own a Via Epia EN1200 board and the script seems to work smoothly but the desktop seems to run with few colours making it hard to make out text and browsing looks just awful. I've attached an image of the default Firefox window. Any help would be greatly appreciated.

I have a EN12000E motherboard, the screen shot looks fine. Make sure you use 24 depth in you xorg file. Also i recommend you to completely disable 3D for system stability, see the first post for more information.

Hope this helps you.

---

### Post by srn on 2008-01-02
OK, this is weird. The screen shot actually looks fine (currently using a XP machine) but when I took the screen shot the colors were kinda "washed out". I'm pretty sure that 24 bit should be the default according to xorg.conf. I will try disabling 3D as I really don't need it. Thanks for the quick reply.

---

### Post by srn on 2008-01-03
I really can't figure how to fix this. The screen shot I posted looks ok, but my desktop looks no better (perhaps even worse) than when using VESA mode. My guess is that I'm running with a low color depth but the only thing in my xorg.conf is this

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```

Anyone have any pointers?

---

### Post by TuxCrafter on 2008-01-03
> **srn said:**
> I really can't figure how to fix this. The screen shot I posted looks ok, but my desktop looks no better (perhaps even worse) than when using VESA mode. My guess is that I'm running with a low color depth but the only thing in my xorg.conf is this

```

Section "Screen"
    Identifier    "Default Screen"
    Device        "Generic Video Card"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```Anyone have any pointers?

I think its a problem with your hardware. Have you tried  the auto adjustment of you samsung screen? If this does not work maybe configure the monitor section of you xorg.conf with the correct frequency's.

---

### Post by KryoMouse on 2008-01-03
2D perfect, Direct Rendering is a no-go.

Ubuntu 7.10, VN896 graphics, on an Amilo Li1705 (yes, I am poor!)

Thank you very much. ^^

---

### Post by srn on 2008-01-04
I decided to install Windows XP just to verify that everything looks OK. This wasn't the case. XP has the same blurry colors so either it is something with the D-Sub interface or perhaps something can be tweaked in the bios. Initial attempts hasn't been successful. Since you own the same board perhaps you could elaborate whether you have done anything to the bios configuration?

---

### Post by gary4gar on 2008-01-05
anyone tried new VIA binary driver?
does it removed lock-up?

---

### Post by runemaste644 on 2008-01-06
EDIT: This broke my computer! Great, now how do i fix it????? It wont let me get to a console, so my only hope is the cd boot! i tried changing 'savage' to 'vesa' in xorg.conf but its still broken!

---

### Post by mikef187 on 2008-01-06
WOW THANK YOU... THIS WORKED LIKE A CHAMP ON DEBIAN LENNY...
no errors and worked flawlessly

---

### Post by teseglet on 2008-01-08
Bad news.  I've been using Openchrome with my Via graphics in Kubuntu 7.10 with no problems.  I just installed Kubuntu with KDE4 RC2 and it won't launch past the splash screen.  Something tells me it is related to Via graphics.  Anyone know differently?

---

### Post by techgeek40 on 2008-01-12
Here is my info - can someone tell me why mine is not working
This is what I get when I do the following command in terminal window
glxifno | grep rendering

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

This is from my xorg.conf file

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

 Section "Module"
    Disable "glx"
    Disable "xtrap"
    Disable "record"
    Disable "GLcore"
    Disable "dri"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"openchrome"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Acer"
	Modelname	"Acer AL1914"
	Horizsync	30.0-83.0
	Vertrefresh	55.0-75.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@75"	"1024x768@70"	"832x624@75"	"1024x768@60"	"800x600@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "ServerFlags"
EndSection

This is from hwinfo-2008-01-12-02:51.txt

version-stable: 0.1.1
-- -- -- -- --
33: PCI(AGP) 100.0: 0300 VGA compatible controller (VGA)
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3371
  Unique ID: VCu0.kqXiTutahq5
  Parent ID: vSkL.S16qDHSKEeD
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "Biostar Microtech Int'l VGA compatible controller"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3371 
  SubVendor: pci 0x1565 "Biostar Microtech Int'l Corp"
  SubDevice: pci 0x1207 
  Revision: 0x01
  Memory Range: 0xd0000000-0xd7ffffff (rw,prefetchable)
  Memory Range: 0xfb000000-0xfbffffff (rw,non-prefetchable)
  Memory Range: 0xfc000000-0xfc00ffff (ro,prefetchable,disabled)
  IRQ: 11 (no events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001106d00003371sv00001565sd00001207bc03sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (PCI bridge)

Primary display adapter: #33
-- -- -- -- --
10: PCI(AGP) 00.0: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_364
  Unique ID: qLht.6OF83IMq_u8
  SysFS ID: /devices/pci0000:00/0000:00:00.0
  SysFS BusID: 0000:00:00.0
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x0364 
  SubVendor: pci 0x1106 "VIA Technologies, Inc."
  SubDevice: pci 0x0364 
  Memory Range: 0xd8000000-0xdfffffff (rw,prefetchable)
  Module Alias: "pci:v00001106d00000364sv00001106sd00000364bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

11: PCI 00.1: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_1364
  Unique ID: hgAj.MpMCJ1kBIz9
  SysFS ID: /devices/pci0000:00/0000:00:00.1
  SysFS BusID: 0000:00:00.1
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x1364 
  Module Alias: "pci:v00001106d00001364sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

12: PCI 00.2: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_2364
  Unique ID: Z+fY.czyKNZlION5
  SysFS ID: /devices/pci0000:00/0000:00:00.2
  SysFS BusID: 0000:00:00.2
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x2364 
  Module Alias: "pci:v00001106d00002364sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

13: PCI 00.3: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3364
  Unique ID: QK9O.s7ZTRfJZWoD
  SysFS ID: /devices/pci0000:00/0000:00:00.3
  SysFS BusID: 0000:00:00.3
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3364 
  Module Alias: "pci:v00001106d00003364sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

14: PCI 00.4: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_4364
  Unique ID: HfeD.6I9cVBLgcC9
  SysFS ID: /devices/pci0000:00/0000:00:00.4
  SysFS BusID: 0000:00:00.4
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x4364 
  Module Alias: "pci:v00001106d00004364sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

16: PCI 00.6: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_6364
  Unique ID: 0Jdu.ccLtdpw1r1D
  SysFS ID: /devices/pci0000:00/0000:00:00.6
  SysFS BusID: 0000:00:00.6
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x6364 
  Module Alias: "pci:v00001106d00006364sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

17: PCI 00.7: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_7364
  Unique ID: ud6k.smx+hvUIzS5
  SysFS ID: /devices/pci0000:00/0000:00:00.7
  SysFS BusID: 0000:00:00.7
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x7364 
  Module Alias: "pci:v00001106d00007364sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

18: PCI 01.0: 0604 PCI bridge (Normal decode)
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_b198
  Unique ID: vSkL.S16qDHSKEeD
  SysFS ID: /devices/pci0000:00/0000:00:01.0
  SysFS BusID: 0000:00:01.0
  Hardware Class: bridge
  Model: "VIA VT8237 PCI Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0xb198 "VT8237 PCI Bridge"
  Module Alias: "pci:v00001106d0000B198sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

19: PCI 02.0: 0604 PCI bridge (Normal decode)
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_a364
  Unique ID: _Znp.g78+51qvkd0
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: bridge
  Model: "VIA PCI bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0xa364 
  Revision: 0x80
  Driver: "pcieport-driver"
  IRQ: 16 (no events)
  Module Alias: "pci:v00001106d0000A364sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

20: PCI 03.0: 0604 PCI bridge (Normal decode)
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_c364
  Unique ID: 3hqH.ASKGEfPHzS4
  SysFS ID: /devices/pci0000:00/0000:00:03.0
  SysFS BusID: 0000:00:03.0
  Hardware Class: bridge
  Model: "VIA PCI bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0xc364 
  Revision: 0x80
  Driver: "pcieport-driver"
  IRQ: 17 (no events)
  Module Alias: "pci:v00001106d0000C364sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

28: PCI 11.0: 0601 ISA bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3337
  Unique ID: 7EWs.srXdOY83sLD
  SysFS ID: /devices/pci0000:00/0000:00:11.0
  SysFS BusID: 0000:00:11.0
  Hardware Class: bridge
  Model: "Biostar Microtech Int'l VT8237A PCI to ISA Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3337 "VT8237A PCI to ISA Bridge"
  SubVendor: pci 0x1565 "Biostar Microtech Int'l Corp"
  SubDevice: pci 0x3206 
  Module Alias: "pci:v00001106d00003337sv00001565sd00003206bc06sc01i00"
  Driver Info #0:
    Driver Status: i2c_viapro is active
    Driver Activation Cmd: "modprobe i2c_viapro"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

29: PCI 11.7: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_287e
  Unique ID: BWxi.NhM1uBZ0XP5
  SysFS ID: /devices/pci0000:00/0000:00:11.7
  SysFS BusID: 0000:00:11.7
  Hardware Class: bridge
  Model: "VIA VT8251 Ultra VLINK Controller"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x287e "VT8251 Ultra VLINK Controller"
  SubVendor: pci 0x1106 "VIA Technologies, Inc."
  SubDevice: pci 0x337e 
  Module Alias: "pci:v00001106d0000287Esv00001106sd0000337Ebc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

31: PCI 13.0: 0600 Host bridge
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_337b
  Unique ID: HSco.jfGiUiN+dB5
  SysFS ID: /devices/pci0000:00/0000:00:13.0
  SysFS BusID: 0000:00:13.0
  Hardware Class: bridge
  Model: "VIA VT8237A PCI to PCIE Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x337b "VT8237A PCI to PCIE Bridge"
  Module Alias: "pci:v00001106d0000337Bsv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

32: PCI 13.1: 0604 PCI bridge (Subtractive decode)
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_337a
  Unique ID: 9n5e.HHSMJjh6gC5
  SysFS ID: /devices/pci0000:00/0000:00:13.1
  SysFS BusID: 0000:00:13.1
  Hardware Class: bridge
  Model: "VIA VT8237A PCI to PCI Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x337a "VT8237A PCI to PCI Bridge"
  Module Alias: "pci:v00001106d0000337Asv00000000sd00000000bc06sc04i01"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
-- -- -- -- --
00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
-- -- -- -- --
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"openchrome"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Acer"
	Modelname	"Acer AL1914"
	Horizsync	30.0-83.0
	Vertrefresh	55.0-75.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1024x768@75"	"1024x768@70"	"832x624@75"	"1024x768@60"	"800x600@60"	"1152x864@75"	"800x600@75"	"1280x1024@75"	"800x600@72"	"1280x960@60"	"800x600@56"	"1280x1024@60"	"640x480@75"	"1280x960@75"	"640x480@72"	"1400x1050@60"	"640x480@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"	"1792x1344@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "ServerFlags"
EndSection

---

### Post by Nerdriot on 2008-01-16
Has anyone managed to get the 3D working with Unichrome? After installing it, everything seems to be working just fine. Only problem is, when I load any game with 3D (SuperTuxKart, for example), it seems to start working fine, but then freezes after a few seconds, then the mouse lags terribly, and I have to force quit the game.

That's generally followed by a reboot, as the lags continues to drag on, even after the game has been killed.

---

### Post by effenberg0x0 on 2008-01-23
After a lot of time trying to use my Laptop (with a VIA VN800 Graphics Chipset) and trying the official driver as well as the good efforts from Openchrome and Unichrome projects, I gave up and tried to get help at VIA Technologies Official Forum (see [http://www.tkarena.com/forums/linux-...hat-going.html](http://www.tkarena.com/forums/linux-...hat-going.html)).

The idea of a petition came out from that thread. I have started this petition at [http://www.petitiononline.com/vialinux/](http://www.petitiononline.com/vialinux/) .

If you plan on using your VIA based hardware on Linux, with a decent performance, stability and security and if you think Linux users should have the same support as Windows users receive from the company, I ask you to sign this petition as well as help me spread this URL to your friends, family and coworkers.

Regards,
Effenberg

---

### Post by TuxCrafter on 2008-01-27
> **effenberg0x0 said:**
> After a lot of time trying to use my Laptop (with a VIA VN800 Graphics Chipset) and trying the official driver as well as the good efforts from Openchrome and Unichrome projects, I gave up and tried to get help at VIA Technologies Official Forum (see [http://www.tkarena.com/forums/linux-...hat-going.html](http://www.tkarena.com/forums/linux-...hat-going.html)).

The idea of a petition came out from that thread. I have started this petition at [http://www.petitiononline.com/vialinux/](http://www.petitiononline.com/vialinux/) .

If you plan on using your VIA based hardware on Linux, with a decent performance, stability and security and if you think Linux users should have the same support as Windows users receive from the company, I ask you to sign this petition as well as help me spread this URL to your friends, family and coworkers.

Regards,
Effenberg

I read the petition, but i do not fully stand behind it. I want VIA to provide free and open documentation for all there chipsets, in a extent so that everybody can help creating GPL Linux drivers for all VIA chips.

---

### Post by Cybrarian on 2008-02-10
Hi.

I downloaded the openchrome-stable.sh script and works well, but when I run Google Earth the X-Server is restarted :( 

I run grep openchrome /var/log/Xorg.0.log with this result

(II) LoadModule: "openchrome"
(II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
(!!) For support, refer to [http://www.openchrome.org/](http://www.openchrome.org/).

but the command glxinfo | grep render reports this

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

Seems some problems with 3D? How can I fix it? :confused:

My lspci:

00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)
04:05.0 Communication controller: Conexant Unknown device 2702 (rev 01)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

Sorry the English, I'm Brazilian and don't speak English very well...

---

### Post by TuxCrafter on 2008-02-10
> **Cybrarian said:**
> Hi.

I downloaded the openchrome-stable.sh script and works well, but when I run Google Earth the X-Server is restarted :( 

I run grep openchrome /var/log/Xorg.0.log with this result

There are a lot of problems with the VIA chips and 3D, 3D is provided bij the MESA project and has sadly nothing to do with the OpenChrome 2D project.

3D is verry unstable, i even advise to disable it and do not use 3D applications.

Sorry i can only give you info and no real solution. (real solution is to buy intel chipset, but they are not perfect either)

---

### Post by homeriq5 on 2008-02-10
when I ran 
```

homeriq5@homeriq5-desktop:~$ glxinfo | grep render
```

I got the following strange message:

```
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.
direct rendering: Yes
OpenGL renderer string: Mesa DRI UniChrome (K8M800) 20060710 x86/MMX+/3DNow!+/SSE2
```

what does it mean?

---

### Post by TuxCrafter on 2008-02-11
> **homeriq5 said:**
> when I ran 
```

homeriq5@homeriq5-desktop:~$ glxinfo | grep render
```I got the following strange message:

```
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.
direct rendering: Yes
OpenGL renderer string: Mesa DRI UniChrome (K8M800) 20060710 x86/MMX+/3DNow!+/SSE2
```what does it mean?

3D rendering is done by MESA there is no support for MESA and VIA on ubuntu. I am sorry I cant help you with this, it could mean a lot of things. Best is to ask the mesa developer that wrote the code?.

---

### Post by fktt on 2008-02-12
did not work for a VIA P4M800 thats on ASUS P4V8X-MX MoBo. :( currently typing on another machine because the problematic one is impossible to use without the urge to make a pancake out of it with a sledge hammer.. :-x

edit: nvm. seems that something did start working after 4 or so days(eg. 4+ boots)

---

### Post by Azul93gt on 2008-02-15
> **TuxCrafter said:**
> Hereby I post my script as attachment for installing and compiling the open source OpenChrome graphical driver for via Chipsets.

-- -- -- -- -- --
To install on Hardy:

sudo apt-get install xserver-xorg-video-openchrome
-- -- -- -- -- --

To install on Gusty: 
HOW TO: Compiling and Installing the OpenChrome Graphical VIA Driver

#Version:       0.0.9
#Date:          25-10-07
#Description:    Install openchrome video drivers from cvs source

I see the command for installing the OpenChrome driver on Ubuntu Feisty, but I don't see the command/instructions for installing the driver on Ubuntu Gutsy. Can someone elaborate?

---

### Post by TuxCrafter on 2008-02-16
> **Azul93gt said:**
> I see the command for installing the OpenChrome driver on Ubuntu Feisty, but I don't see the command/instructions for installing the driver on Ubuntu Gutsy. Can someone elaborate?

Run the script to install the driver in Gusty and Feisty is unsupported.

---

### Post by terry_gardener on 2008-02-17
Hello 

I have just installed the openchrome stable script and everything seems to worked .
when i run glxinfo | grep render i get the expected: 
direct rendering: Yes
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX/SSE2

but i still cant use compiz-fuzion, will running the other script give me 3d. 

Thanks for the script, seemed to work seemlessly. 

i have the K8m890 chrome9 chipset. 

Thanks

---

### Post by TuxCrafter on 2008-02-17
> **terry_gardener said:**
> Hello 

I have just installed the openchrome stable script and everything seems to worked .
when i run glxinfo | grep render i get the expected: 
direct rendering: Yes
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX/SSE2

but i still cant use compiz-fuzion, will running the other script give me 3d. 

Thanks for the script, seemed to work seemlessly. 

i have the K8m890 chrome9 chipset. 

Thanks

Compiz textures are sadly unsupported on via chipsets! So it will not work.

---

### Post by faktorqm on 2008-02-18
Hi, thank you for your script, but i have k8m890 and don't work for me (stable version). 
This is the hwinfo result for your backtracing:

```

version-stable: 0.1.1
-- -- -- -- --
37: PCI 100.0: 0300 VGA compatible controller (VGA)
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3230
  Unique ID: VCu0.AP8kOdRTmsD
  Parent ID: vSkL.CP+qXDDqow8
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "ASUSTeK VGA compatible controller"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3230 
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x81b5 
  Revision: 0x01
  Driver: "via_v4l"
  Driver Modules: "via_v4l_drv"
  Memory Range: 0xd0000000-0xdfffffff (rw,prefetchable)
  Memory Range: 0xfa000000-0xfaffffff (rw,non-prefetchable)
  Memory Range: 0xfbef0000-0xfbefffff (ro,prefetchable,disabled)
  IRQ: 22 (no events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001106d00003230sv00001043sd000081B5bc03sc00i00"
  Driver Info #0:
    Driver Status: via_v4l_drv is active
    Driver Activation Cmd: "modprobe via_v4l_drv"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (PCI bridge)

Primary display adapter: #37
-- -- -- -- --
10: PCI 00.0: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_336
  Unique ID: qLht.ObLc8r13xl2
  SysFS ID: /devices/pci0000:00/0000:00:00.0
  SysFS BusID: 0000:00:00.0
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x0336 
  Driver: "agpgart-via"
  Driver Modules: "via_agp"
  Memory Range: 0xf0000000-0xf7ffffff (rw,prefetchable)
  Module Alias: "pci:v00001106d00000336sv00000000sd00000000bc06sc00i00"
  Driver Info #0:
    Driver Status: via_agp is active
    Driver Activation Cmd: "modprobe via_agp"
  Driver Info #1:
    Driver Status: amd64_agp is active
    Driver Activation Cmd: "modprobe amd64_agp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

11: PCI 00.1: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_1336
  Unique ID: hgAj.elxkCxbJ3BB
  SysFS ID: /devices/pci0000:00/0000:00:00.1
  SysFS BusID: 0000:00:00.1
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x1336 
  Module Alias: "pci:v00001106d00001336sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

12: PCI 00.2: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_2336
  Unique ID: Z+fY.uvXtGTdQ9b6
  SysFS ID: /devices/pci0000:00/0000:00:00.2
  SysFS BusID: 0000:00:00.2
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x2336 
  Module Alias: "pci:v00001106d00002336sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

13: PCI 00.3: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3336
  Unique ID: QK9O.8480LZBhH0F
  SysFS ID: /devices/pci0000:00/0000:00:00.3
  SysFS BusID: 0000:00:00.3
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3336 
  Module Alias: "pci:v00001106d00003336sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

14: PCI 00.4: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_4336
  Unique ID: HfeD.OEk8P5DoNQA
  SysFS ID: /devices/pci0000:00/0000:00:00.4
  SysFS BusID: 0000:00:00.4
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x4336 
  Module Alias: "pci:v00001106d00004336sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

16: PCI 00.6: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_6290
  Unique ID: 0Jdu.py34_bWpsQ6
  SysFS ID: /devices/pci0000:00/0000:00:00.6
  SysFS BusID: 0000:00:00.6
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x6290 
  SubVendor: pci 0x0008 
  SubDevice: pci 0x0000 
  Module Alias: "pci:v00001106d00006290sv00000008sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

17: PCI 00.7: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_7336
  Unique ID: ud6k.8jWYbpMQkg6
  SysFS ID: /devices/pci0000:00/0000:00:00.7
  SysFS BusID: 0000:00:00.7
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x7336 
  Module Alias: "pci:v00001106d00007336sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

18: PCI 01.0: 0604 PCI bridge (Normal decode)
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_b188
  Unique ID: vSkL.CP+qXDDqow8
  SysFS ID: /devices/pci0000:00/0000:00:01.0
  SysFS BusID: 0000:00:01.0
  Hardware Class: bridge
  Model: "VIA VT8237 PCI bridge [K8T800/K8T890 South]"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0xb188 "VT8237 PCI bridge [K8T800/K8T890 South]"
  Module Alias: "pci:v00001106d0000B188sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

19: PCI 02.0: 0604 PCI bridge (Normal decode)
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_a238
  Unique ID: _Znp.LUQ1QvXEEDB
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: bridge
  Model: "VIA K8T890 PCI to PCI Bridge Controller"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0xa238 "K8T890 PCI to PCI Bridge Controller"
  Driver: "pcieport-driver"
  IRQ: 16 (no events)
  Module Alias: "pci:v00001106d0000A238sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

20: PCI 03.0: 0604 PCI bridge (Normal decode)
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_c238
  Unique ID: 3hqH.rocIYX7cS2F
  SysFS ID: /devices/pci0000:00/0000:00:03.0
  SysFS BusID: 0000:00:03.0
  Hardware Class: bridge
  Model: "VIA K8T890 PCI to PCI Bridge Controller"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0xc238 "K8T890 PCI to PCI Bridge Controller"
  Driver: "pcieport-driver"
  IRQ: 17 (no events)
  Module Alias: "pci:v00001106d0000C238sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

28: PCI 11.0: 0601 ISA bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3337
  Unique ID: 7EWs.TX0cu_Oy3JD
  SysFS ID: /devices/pci0000:00/0000:00:11.0
  SysFS BusID: 0000:00:11.0
  Hardware Class: bridge
  Model: "ASUSTeK VT8237A PCI to ISA Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3337 "VT8237A PCI to ISA Bridge"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x81b5 
  Module Alias: "pci:v00001106d00003337sv00001043sd000081B5bc06sc01i00"
  Driver Info #0:
    Driver Status: i2c_viapro is active
    Driver Activation Cmd: "modprobe i2c_viapro"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

29: PCI 11.7: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_287e
  Unique ID: BWxi.NhM1uBZ0XP5
  SysFS ID: /devices/pci0000:00/0000:00:11.7
  SysFS BusID: 0000:00:11.7
  Hardware Class: bridge
  Model: "VIA VT8251 Ultra VLINK Controller"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x287e "VT8251 Ultra VLINK Controller"
  SubVendor: pci 0x1106 "VIA Technologies, Inc."
  SubDevice: pci 0x337e 
  Module Alias: "pci:v00001106d0000287Esv00001106sd0000337Ebc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

31: PCI 13.0: 0604 PCI bridge (Normal decode)
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_337b
  Unique ID: HSco.nV1YXpODSg1
  SysFS ID: /devices/pci0000:00/0000:00:13.0
  SysFS BusID: 0000:00:13.0
  Hardware Class: bridge
  Model: "VIA VT8237A PCI to PCIE Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x337b "VT8237A PCI to PCIE Bridge"
  Module Alias: "pci:v00001106d0000337Bsv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

32: PCI 13.1: 0604 PCI bridge (Subtractive decode)
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_337a
  Unique ID: 9n5e.HHSMJjh6gC5
  SysFS ID: /devices/pci0000:00/0000:00:13.1
  SysFS BusID: 0000:00:13.1
  Hardware Class: bridge
  Model: "VIA VT8237A PCI to PCI Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x337a "VT8237A PCI to PCI Bridge"
  Module Alias: "pci:v00001106d0000337Asv00000000sd00000000bc06sc04i01"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

33: PCI 18.0: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1022_1100
  Unique ID: fiDB.ptk_g9XAN03
  SysFS ID: /devices/pci0000:00/0000:00:18.0
  SysFS BusID: 0000:00:18.0
  Hardware Class: bridge
  Model: "AMD K8 [Athlon64/Opteron] HyperTransport Technology Configuration"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1100 "K8 [Athlon64/Opteron] HyperTransport Technology Configuration"
  Module Alias: "pci:v00001022d00001100sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

34: PCI 18.1: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1022_1101
  Unique ID: W1j0.KIhk9ketuO3
  SysFS ID: /devices/pci0000:00/0000:00:18.1
  SysFS BusID: 0000:00:18.1
  Hardware Class: bridge
  Model: "AMD K8 [Athlon64/Opteron] Address Map"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1101 "K8 [Athlon64/Opteron] Address Map"
  Module Alias: "pci:v00001022d00001101sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

35: PCI 18.2: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1022_1102
  Unique ID: OMCs.ridUeImaQn3
  SysFS ID: /devices/pci0000:00/0000:00:18.2
  SysFS BusID: 0000:00:18.2
  Hardware Class: bridge
  Model: "AMD K8 [Athlon64/Opteron] DRAM Controller"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1102 "K8 [Athlon64/Opteron] DRAM Controller"
  Module Alias: "pci:v00001022d00001102sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

36: PCI 18.3: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1022_1103
  Unique ID: Fhhh.M7aE7ttHy94
  SysFS ID: /devices/pci0000:00/0000:00:18.3
  SysFS BusID: 0000:00:18.3
  Hardware Class: bridge
  Model: "AMD K8 [Athlon64/Opteron] Miscellaneous Control"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1103 "K8 [Athlon64/Opteron] Miscellaneous Control"
  Driver: "k8temp"
  Driver Modules: "k8temp"
  Module Alias: "pci:v00001022d00001103sv00000000sd00000000bc06sc00i00"
  Driver Info #0:
    Driver Status: k8temp is active
    Driver Activation Cmd: "modprobe k8temp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
-- -- -- -- --
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6290
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3230 (rev 01)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
-- -- -- -- --
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"freetype"
	Load	"int10"
	Load	"vbe"
	Load	"extmod"
	Load	"dri"
	Load	"glx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	BusID		"PCI:1:0:0"
	BoardName	"via"
	VendorName	"VIA Tech"
	Driver		"openchrome"
	Option		"NoDDCValue"
EndSection

Section "Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
	Identifier "MonitorGeneric Video Card"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"MonitorGeneric Video Card"
	DefaultDepth	24
	SubSection "Display"
		Modes  "1024x768"         
		Depth		1
	EndSubSection
	SubSection "Display"
		Modes  "1024x768"         
		Depth		4
	EndSubSection
	SubSection "Display"
		Modes  "1024x768"         
		Depth		8
	EndSubSection
	SubSection "Display"
		Modes  "1024x768"         
		Depth		15
	EndSubSection
	SubSection "Display"
		Modes  "1024x768"         
		Depth		16
	EndSubSection
	SubSection "Display"
		Modes  "1024x768"         
		Depth		24
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode 0666
	Group 0
EndSection

```

i follow this guide in spanish to setup but have problems too. 

[http://ubuntuforums.org/showthread.php?p=4354435#post4354435](http://ubuntuforums.org/showthread.php?p=4354435#post4354435)

thank you again, and go for a stable installation script full feature :D

---

### Post by TuxCrafter on 2008-02-19
> **faktorqm said:**
> Hi, thank you for your script, but i have k8m890 and don't work for me (stable version). 
This is the hwinfo result for your backtracing:

```

version-stable: 0.1.1
-- -- -- -- --
37: PCI 100.0: 0300 VGA compatible controller (VGA)
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3230
  Unique ID: VCu0.AP8kOdRTmsD
  Parent ID: vSkL.CP+qXDDqow8
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "ASUSTeK VGA compatible controller"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3230 
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x81b5 
  Revision: 0x01
  Driver: "via_v4l"
  Driver Modules: "via_v4l_drv"
  Memory Range: 0xd0000000-0xdfffffff (rw,prefetchable)
  Memory Range: 0xfa000000-0xfaffffff (rw,non-prefetchable)
  Memory Range: 0xfbef0000-0xfbefffff (ro,prefetchable,disabled)
  IRQ: 22 (no events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001106d00003230sv00001043sd000081B5bc03sc00i00"
  Driver Info #0:
    Driver Status: via_v4l_drv is active
    Driver Activation Cmd: "modprobe via_v4l_drv"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (PCI bridge)

Primary display adapter: #37
-- -- -- -- --
10: PCI 00.0: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_336
  Unique ID: qLht.ObLc8r13xl2
  SysFS ID: /devices/pci0000:00/0000:00:00.0
  SysFS BusID: 0000:00:00.0
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x0336 
  Driver: "agpgart-via"
  Driver Modules: "via_agp"
  Memory Range: 0xf0000000-0xf7ffffff (rw,prefetchable)
  Module Alias: "pci:v00001106d00000336sv00000000sd00000000bc06sc00i00"
  Driver Info #0:
    Driver Status: via_agp is active
    Driver Activation Cmd: "modprobe via_agp"
  Driver Info #1:
    Driver Status: amd64_agp is active
    Driver Activation Cmd: "modprobe amd64_agp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

11: PCI 00.1: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_1336
  Unique ID: hgAj.elxkCxbJ3BB
  SysFS ID: /devices/pci0000:00/0000:00:00.1
  SysFS BusID: 0000:00:00.1
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x1336 
  Module Alias: "pci:v00001106d00001336sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

12: PCI 00.2: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_2336
  Unique ID: Z+fY.uvXtGTdQ9b6
  SysFS ID: /devices/pci0000:00/0000:00:00.2
  SysFS BusID: 0000:00:00.2
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x2336 
  Module Alias: "pci:v00001106d00002336sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

13: PCI 00.3: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3336
  Unique ID: QK9O.8480LZBhH0F
  SysFS ID: /devices/pci0000:00/0000:00:00.3
  SysFS BusID: 0000:00:00.3
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3336 
  Module Alias: "pci:v00001106d00003336sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

14: PCI 00.4: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_4336
  Unique ID: HfeD.OEk8P5DoNQA
  SysFS ID: /devices/pci0000:00/0000:00:00.4
  SysFS BusID: 0000:00:00.4
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x4336 
  Module Alias: "pci:v00001106d00004336sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

16: PCI 00.6: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_6290
  Unique ID: 0Jdu.py34_bWpsQ6
  SysFS ID: /devices/pci0000:00/0000:00:00.6
  SysFS BusID: 0000:00:00.6
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x6290 
  SubVendor: pci 0x0008 
  SubDevice: pci 0x0000 
  Module Alias: "pci:v00001106d00006290sv00000008sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

17: PCI 00.7: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_7336
  Unique ID: ud6k.8jWYbpMQkg6
  SysFS ID: /devices/pci0000:00/0000:00:00.7
  SysFS BusID: 0000:00:00.7
  Hardware Class: bridge
  Model: "VIA Host bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x7336 
  Module Alias: "pci:v00001106d00007336sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

18: PCI 01.0: 0604 PCI bridge (Normal decode)
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_b188
  Unique ID: vSkL.CP+qXDDqow8
  SysFS ID: /devices/pci0000:00/0000:00:01.0
  SysFS BusID: 0000:00:01.0
  Hardware Class: bridge
  Model: "VIA VT8237 PCI bridge [K8T800/K8T890 South]"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0xb188 "VT8237 PCI bridge [K8T800/K8T890 South]"
  Module Alias: "pci:v00001106d0000B188sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

19: PCI 02.0: 0604 PCI bridge (Normal decode)
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_a238
  Unique ID: _Znp.LUQ1QvXEEDB
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: bridge
  Model: "VIA K8T890 PCI to PCI Bridge Controller"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0xa238 "K8T890 PCI to PCI Bridge Controller"
  Driver: "pcieport-driver"
  IRQ: 16 (no events)
  Module Alias: "pci:v00001106d0000A238sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

20: PCI 03.0: 0604 PCI bridge (Normal decode)
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_c238
  Unique ID: 3hqH.rocIYX7cS2F
  SysFS ID: /devices/pci0000:00/0000:00:03.0
  SysFS BusID: 0000:00:03.0
  Hardware Class: bridge
  Model: "VIA K8T890 PCI to PCI Bridge Controller"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0xc238 "K8T890 PCI to PCI Bridge Controller"
  Driver: "pcieport-driver"
  IRQ: 17 (no events)
  Module Alias: "pci:v00001106d0000C238sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

28: PCI 11.0: 0601 ISA bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3337
  Unique ID: 7EWs.TX0cu_Oy3JD
  SysFS ID: /devices/pci0000:00/0000:00:11.0
  SysFS BusID: 0000:00:11.0
  Hardware Class: bridge
  Model: "ASUSTeK VT8237A PCI to ISA Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3337 "VT8237A PCI to ISA Bridge"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x81b5 
  Module Alias: "pci:v00001106d00003337sv00001043sd000081B5bc06sc01i00"
  Driver Info #0:
    Driver Status: i2c_viapro is active
    Driver Activation Cmd: "modprobe i2c_viapro"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

29: PCI 11.7: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_287e
  Unique ID: BWxi.NhM1uBZ0XP5
  SysFS ID: /devices/pci0000:00/0000:00:11.7
  SysFS BusID: 0000:00:11.7
  Hardware Class: bridge
  Model: "VIA VT8251 Ultra VLINK Controller"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x287e "VT8251 Ultra VLINK Controller"
  SubVendor: pci 0x1106 "VIA Technologies, Inc."
  SubDevice: pci 0x337e 
  Module Alias: "pci:v00001106d0000287Esv00001106sd0000337Ebc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

31: PCI 13.0: 0604 PCI bridge (Normal decode)
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_337b
  Unique ID: HSco.nV1YXpODSg1
  SysFS ID: /devices/pci0000:00/0000:00:13.0
  SysFS BusID: 0000:00:13.0
  Hardware Class: bridge
  Model: "VIA VT8237A PCI to PCIE Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x337b "VT8237A PCI to PCIE Bridge"
  Module Alias: "pci:v00001106d0000337Bsv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

32: PCI 13.1: 0604 PCI bridge (Subtractive decode)
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1106_337a
  Unique ID: 9n5e.HHSMJjh6gC5
  SysFS ID: /devices/pci0000:00/0000:00:13.1
  SysFS BusID: 0000:00:13.1
  Hardware Class: bridge
  Model: "VIA VT8237A PCI to PCI Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x337a "VT8237A PCI to PCI Bridge"
  Module Alias: "pci:v00001106d0000337Asv00000000sd00000000bc06sc04i01"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

33: PCI 18.0: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1022_1100
  Unique ID: fiDB.ptk_g9XAN03
  SysFS ID: /devices/pci0000:00/0000:00:18.0
  SysFS BusID: 0000:00:18.0
  Hardware Class: bridge
  Model: "AMD K8 [Athlon64/Opteron] HyperTransport Technology Configuration"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1100 "K8 [Athlon64/Opteron] HyperTransport Technology Configuration"
  Module Alias: "pci:v00001022d00001100sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

34: PCI 18.1: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1022_1101
  Unique ID: W1j0.KIhk9ketuO3
  SysFS ID: /devices/pci0000:00/0000:00:18.1
  SysFS BusID: 0000:00:18.1
  Hardware Class: bridge
  Model: "AMD K8 [Athlon64/Opteron] Address Map"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1101 "K8 [Athlon64/Opteron] Address Map"
  Module Alias: "pci:v00001022d00001101sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

35: PCI 18.2: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1022_1102
  Unique ID: OMCs.ridUeImaQn3
  SysFS ID: /devices/pci0000:00/0000:00:18.2
  SysFS BusID: 0000:00:18.2
  Hardware Class: bridge
  Model: "AMD K8 [Athlon64/Opteron] DRAM Controller"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1102 "K8 [Athlon64/Opteron] DRAM Controller"
  Module Alias: "pci:v00001022d00001102sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

36: PCI 18.3: 0600 Host bridge
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1022_1103
  Unique ID: Fhhh.M7aE7ttHy94
  SysFS ID: /devices/pci0000:00/0000:00:18.3
  SysFS BusID: 0000:00:18.3
  Hardware Class: bridge
  Model: "AMD K8 [Athlon64/Opteron] Miscellaneous Control"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1103 "K8 [Athlon64/Opteron] Miscellaneous Control"
  Driver: "k8temp"
  Driver Modules: "k8temp"
  Module Alias: "pci:v00001022d00001103sv00000000sd00000000bc06sc00i00"
  Driver Info #0:
    Driver Status: k8temp is active
    Driver Activation Cmd: "modprobe k8temp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
-- -- -- -- --
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6290
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3230 (rev 01)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
-- -- -- -- --
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/cyrillic"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "freetype"
    Load    "int10"
    Load    "vbe"
    Load    "extmod"
    Load    "dri"
    Load    "glx"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "es"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "Generic Video Card"
    BusID        "PCI:1:0:0"
    BoardName    "via"
    VendorName    "VIA Tech"
    Driver        "openchrome"
    Option        "NoDDCValue"
EndSection

Section "Monitor"
    Option        "DPMS"
    HorizSync    28-51
    VertRefresh    43-60
    Identifier "MonitorGeneric Video Card"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Generic Video Card"
    Monitor        "MonitorGeneric Video Card"
    DefaultDepth    24
    SubSection "Display"
        Modes  "1024x768"         
        Depth        1
    EndSubSection
    SubSection "Display"
        Modes  "1024x768"         
        Depth        4
    EndSubSection
    SubSection "Display"
        Modes  "1024x768"         
        Depth        8
    EndSubSection
    SubSection "Display"
        Modes  "1024x768"         
        Depth        15
    EndSubSection
    SubSection "Display"
        Modes  "1024x768"         
        Depth        16
    EndSubSection
    SubSection "Display"
        Modes  "1024x768"         
        Depth        24
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus"    "SendCoreEvents"
    InputDevice     "cursor"    "SendCoreEvents"
    InputDevice     "eraser"    "SendCoreEvents"
EndSection

Section "DRI"
    Mode 0666
    Group 0
EndSection

```i follow this guide in spanish to setup but have problems too. 

[http://ubuntuforums.org/showthread.php?p=4354435#post4354435](http://ubuntuforums.org/showthread.php?p=4354435#post4354435)

thank you again, and go for a stable installation script full feature :D

I think your hardware is not recognised, please install the experimental branch and post your xorg.conf file to the openchrome mailing list after rebooting.

---

### Post by adzik on 2008-02-19
Thanks for all your hard work Tuxcrafter.  Everything here has really helped educate me on this issue. 

As far as the script goes, I have tried both the stable and experimental and neither has worked at all after installing. Machine reboots in either 800x600 or brings up the screen for a split second and disappears.  I have tried all the possible options I have read in this thread to correct it and done two fresh installs of Ubuntu 7.10 to test all possible options. Still no go.
I have an Everex nc1503 laptop which uses Chrome9 HC (VN896 I believe is the chipset).
Does anyone know what else I can try that has not been mentioned here in this thread?
I know it was suggested to also try the Unichrome project driver, but to be completely honest, I don't really have enough experience to know how to install it as there aren't any .deb or binary files on the Unichrome project page.

The only intention I have for this laptop is basic office work with some streaming radio from time to time.

Thanks again Tuxcrafter.  Your dedication & knowledge in this area is appreciated.

---

### Post by TuxCrafter on 2008-02-20
> **adzik said:**
> Thanks for all your hard work Tuxcrafter.  Everything here has really helped educate me on this issue. 

As far as the script goes, I have tried both the stable and experimental and neither has worked at all after installing. Machine reboots in either 800x600 or brings up the screen for a split second and disappears.  I have tried all the possible options I have read in this thread to correct it and done two fresh installs of Ubuntu 7.10 to test all possible options. Still no go.
I have an Everex nc1503 laptop which uses Chrome9 HC (VN896 I believe is the chipset).
Does anyone know what else I can try that has not been mentioned here in this thread?
I know it was suggested to also try the Unichrome project driver, but to be completely honest, I don't really have enough experience to know how to install it as there aren't any .deb or binary files on the Unichrome project page.

The only intention I have for this laptop is basic office work with some streaming radio from time to time.

Thanks again Tuxcrafter.  Your dedication & knowledge in this area is appreciated.

do not try the unichrome driver this is a waste of time, post your gz compressed /var/log/Xorg.0.log tpt the openchrome mailing list they will change to code for you.

---

### Post by juggleitall on 2008-02-21
I am trying to run the scripts on an Everex gPC with a VIA C7-D processor and a CN700 graphics processor.  I have a Panasonic HD plasma display that includes a standard computer Mini D-sub 15P connector.  The display works well at 800X600 resolution, but should be capable of 1280x768 and I would like to see if openchrome would fix problems with stuttering on utube videos.

I just installed Ubuntu 7.10 this week.  I first tried openchrome.sh and the script generated the following message:
  ./openchrome.sh: line 78: ./autogen.sh: No such file or directory

The package did not compile.

I then tried openchrome-stable.sh and it compiled and I had a display at 1280x768, but the display was shifted off to the left about 5%.  I rebooted the computer and the boot process stopped after the rc.local files were loaded.  I never could get a display and had to hook up another monitor to change xorg.conf files.

I tried the openchrome.sh script again today with the same no autogen.sh results.  Is this a problem with the openchrome site?

Thanks for the support.  I will keep you posted on my efforts.

---

### Post by TuxCrafter on 2008-02-21
> **juggleitall said:**
> I am trying to run the scripts on an Everex gPC with a VIA C7-D processor and a CN700 graphics processor.  I have a Panasonic HD plasma display that includes a standard computer Mini D-sub 15P connector.  The display works well at 800X600 resolution, but should be capable of 1280x768 and I would like to see if openchrome would fix problems with stuttering on utube videos.

I just installed Ubuntu 7.10 this week.  I first tried openchrome.sh and the script generated the following message:
  ./openchrome.sh: line 78: ./autogen.sh: No such file or directory

The package did not compile.

I then tried openchrome-stable.sh and it compiled and I had a display at 1280x768, but the display was shifted off to the left about 5%.  I rebooted the computer and the boot process stopped after the rc.local files were loaded.  I never could get a display and had to hook up another monitor to change xorg.conf files.

I tried the openchrome.sh script again today with the same no autogen.sh results.  Is this a problem with the openchrome site?

Thanks for the support.  I will keep you posted on my efforts.

jups, they removed the experimental branches  so only the stable branches is working on this moment. I hope you find the correct xorg.conf setup for your monitor.

---

### Post by drose28357 on 2008-02-23
I used openchrome-stable.sh at Hardy Alpha 5 on an P4V900 Chipset. Installation seems to be o.k.. But i can not use advanced visual effects.

---

### Post by TuxCrafter on 2008-02-24
> **drose28357 said:**
> I used openchrome-stable.sh at Hardy Alpha 5 on an P4V900 Chipset. Installation seems to be o.k.. But i can not use advanced visual effects.

visual effects do not use on via based video chips this is because via does not release documentation

---

### Post by juggleitall on 2008-02-26
> **TuxCrafter said:**
> jups, they removed the experimental branches  so only the stable branches is working on this moment. I hope you find the correct xorg.conf setup for your monitor.

TuxCrafter,
I got my xorg.conf working.  It was quite a struggle.  I had a major problem in the xorg.conf file being tossed out and the xorg.conf.failsafe being used any time I added HorizSync and VertRefresh.  I finally generated a new xog.conf using dpkg-reconfigure, removed all of the modelines and just added the HorizSync and VertRefresh.  The openchrome driver then started loading.  After that, it was just a matter of finding the right single modeline to use with my monitor.  The "cvt" calculator generated codes that worked.  I didn't have as much luck with the calculators on the internet.  The resolution, speed, and smoothness are much improved with the openchrome driver.  Here is the Modeline that works well for me:
  HorizSync       15-110
  VertRefresh     48-120
  Modeline "1280x768_75.00"  102.25  1280 1360 1488 1696  768 771 781 805 +hsync +vsync

This is using a Via C7 processor and CN700 graphics accelator with a Panasonic TH-58PH10UK 58" Plasma 720 monitor.

Thanks for the script.  It made installing openchrome totally painless.

---

### Post by WernerBrandt on 2008-02-29
Thanks Jelle,

Script worked ok!

Question:
Does it install a lot of things not really nescesary? I saw alot of things beeing installed as it ran...

Remark:
The script generated no errors but my X restart (CRTL+ALT+Backspace) did not work. After a reboot it all went ok..

Thanks again for all the hard work!

(Bedankt ;) )

---

### Post by TuxCrafter on 2008-02-29
> **WernerBrandt said:**
> Thanks Jelle,

Script worked ok!

Question:
Does it install a lot of things not really nescesary? I saw alot of things beeing installed as it ran...

Remark:
The script generated no errors but my X restart (CRTL+ALT+Backspace) did not work. After a reboot it all went ok..

Thanks again for all the hard work!

(Bedankt ;) )

```
sudo apt-get remove  build-essential subversion autoconf automake1.9 libtool xorg-dev libdrm-dev libgl1-mesa-dev git-arch linux-headers-$(uname -r)
```

I think it is save to remove the above after the installation.

---

### Post by adzik on 2008-03-04
I've managed to get the openchrome driver working, and at the correct max. resolution, so all is great in that department.  :)
The one thing that does occur, is screen artifacting/corruption. (squares and rectangles randomly strewn about the screen).  I would say this happens 1 out of 8-9 cold starts/boots.  I have no clue why, but I thought I would bring this to the table and see if this sounds familiar. I will also take this to the mailing list.
Has this kind of situation occurred for anyone?? Also, in very specific instances, the mouse cursor disapears. For instance, when attempting to view a full image in Firefox, the zoom-in feature, the cursor will vanish if hovering over the image. 
Otherwise, everthing is perfect at this point, including MPEG2 acceleration. 

(using on VN896 chipset - Everex Stepnote nc1503)

---

### Post by carbonyc on 2008-03-06
Hi, I'm having some troubles with this script...
at the end of the installation, after the question: "Install the via openchrome 2D driver [Y/n]?y"
this happens:

A    openchrome/README
Generated work copy for review 534.
/home/carbonyc/openchrome.sh: line 78: ./autogen.sh: File or directory does not exist.
make: *** No target indicated and any make files found.  Stop.
make: *** No rule to process the target "install". Stop.

Then i reboot the computer and Xserver doesn't work!
What's the problem?

---

### Post by adzik on 2008-03-06
Carbonyc, are you using the openchrome-stable.sh script, or just the openchrome.sh?  You need to use the stable one as it has been stated here that the experimental branch does not work at the moment.

---

### Post by TuxCrafter on 2008-03-06
> **carbonyc said:**
> Hi, I'm having some troubles with this script...
at the end of the installation, after the question: "Install the via openchrome 2D driver [Y/n]?y"
this happens:

A    openchrome/README
Generated work copy for review 534.
/home/carbonyc/openchrome.sh: line 78: ./autogen.sh: File or directory does not exist.
make: *** No target indicated and any make files found.  Stop.
make: *** No rule to process the target "install". Stop.

Then i reboot the computer and Xserver doesn't work!
What's the problem?

Did you use the openchrome-stable.sh if not please try again with that script.

---

### Post by rjmoerland on 2008-03-06
For me, the script (stable version) ran perfectly on Xubuntu 7.10 + Acer Aspire 1352XC, KM400 chip set, and thank you for that. 

After a reboot, I got the normal desktop again, but unfortunately 3D went from software mode to crash mode ;) Everytime something GL related started, X just hang. Moreover, video playback (which was just fine with preinstalled Xorg via driver) was corrupted. I saw green blocks at the bottom of the screen and colors were, er, 'striped'. Luminance did seem to be working. 

So, I reverted to the original via driver, and as a suprise (to me) 3D now *did* work! However, video was still corrupted and I disabled the extensions as per the first post in this topic, which restored solid playback. I don't have the openchrome driver anymore, but at least I can now choose between video and 3D :D

---

### Post by TuxCrafter on 2008-03-06
New version of the script added the option to remove the used development packages. Also did some cosmetic changes and removed the unstable version.

---

### Post by Djainette on 2008-03-06
Vote !
[http://brainstorm.ubuntu.com/idea/1313/](http://brainstorm.ubuntu.com/idea/1313/)

---

### Post by carbonyc on 2008-03-07
ok!
It seems to be working nicely now, but I still can't enable desktop efects...
how can I enable 3D efects?

Thanx a lot!

---

### Post by TuxCrafter on 2008-03-07
> **carbonyc said:**
> ok!
It seems to be working nicely now, but I still can't enable desktop efects...
how can I enable 3D efects?

Thanx a lot!

The 2D openchrome driver is NOT responsible for the 3D MESA driver. The 3D MESA driver does not support some of the textures necessary to be able to run desktop effects like compiz. So its currently impossible to have desktop effects with via chipsets. The only good solution for this is to make VIA release documentation about there chipsets so developers can create working software. So first ask VIA to release documentation and then ask developers to use this documentation, not the other way around.

---

### Post by carbonyc on 2008-03-07
Ok TuxCrafter!
thank you for your atention and patience!
See ya'

---

### Post by TuxCrafter on 2008-03-08
> **carbonyc said:**
> Ok TuxCrafter!
thank you for your atention and patience!
See ya'

Ho, sorry, I now see the tone of the message comes over very hard. I am sorry for this. was not really my intention. Its a bit of a frustrating issue but totally not your fault in any way.

Kind regards

---

### Post by Chokkan on 2008-03-08
Script worked like a charm and it was fascinating to watch it do its stuff.:popcorn:

I decided to add libgl1-mesa-dri through synaptic to get DRI working as shown in the first post.

My monitor is set up properly with the native resolution and it looks great. I really appreciate the work that must have gone into this...well actually I don't as I have no idea about writing scripts but you get the idea :)

What should I do with the device info that was produced?

---

### Post by TuxCrafter on 2008-03-09
> **Chokkan said:**
> Script worked like a charm and it was fascinating to watch it do its stuff.:popcorn:

I decided to add libgl1-mesa-dri through synaptic to get DRI working as shown in the first post.

My monitor is set up properly with the native resolution and it looks great. I really appreciate the work that must have gone into this...well actually I don't as I have no idea about writing scripts but you get the idea :)

What should I do with the device info that was produced?

Thanks, the device info can go to the trash bin, it is only for debug information, that is not necessary in your case.

---

### Post by cor2y on 2008-03-11
First off thank you for the script.
However it didn't work for me.
All i want is xv/xvmc playback for videos, while i would like compiz or working 3d for xscreensaver its not a priority.

Ok so i tried this script twice on my msi k9vgm-v motherboard which uses the k8m890ce chipset.
On the first try the system hanged after the ubuntu progress bar the whole screen just went black and no more progress.
Luckily since i have dealt with ATI cards before  dpkg-reconfigure xserver-xorg is one cmd i know by heart so a quick boot into recovery brought back the vesa driver.
The second time i made sure to disable 3d in xorg.conf after the install like whats suggested on the first page. This time at reboot i got past the black screen and bullet proof x came up telling me that ubuntu would now be running in safe graphics mode, again one more dpkg-reconfigure and i was back in vesa.
Frankly i don't know what is wrong so i am attaching the hwinfo that was with the second install try.

---

### Post by TuxCrafter on 2008-03-11
> **cor2y said:**
> First off thank you for the script.
However it didn't work for me.
All i want is xv/xvmc playback for videos, while i would like compiz or working 3d for xscreensaver its not a priority.

Ok so i tried this script twice on my msi k9vgm-v motherboard which uses the k8m890ce chipset.
On the first try the system hanged after the ubuntu progress bar the whole screen just went black and no more progress.
Luckily since i have dealt with ATI cards before  dpkg-reconfigure xserver-xorg is one cmd i know by heart so a quick boot into recovery brought back the vesa driver.
The second time i made sure to disable 3d in xorg.conf after the install like whats suggested on the first page. This time at reboot i got past the black screen and bullet proof x came up telling me that ubuntu would now be running in safe graphics mode, again one more dpkg-reconfigure and i was back in vesa.
Frankly i don't know what is wrong so i am attaching the hwinfo that was with the second install try.

hmm, i would advice to gzip the xorg.log and the hardware log to the openchrome mailinglist. I think the driver compiled and installed fine but it does not work on your chipset yet.

---

### Post by cor2y on 2008-03-11
Ok for anyone with the k8m890ce VIA chipset here is how i got openchrome working.
If you are on Gutsy all you need is the svn source code and nothing else.
Follow the first half of the instructions on this page.
[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code)
And don't forget to change the driver from vesa to openchrome as listed below in the instructions there, IGNORE the part about rebuilding the drm kernel, just do the first half with compiling the openchrome driver and the final part of changing from vesa to openchrome.
Why TuxCrafter's script did not work for me i don't know.
And how do i know not to use the drm kernel section in the guide?
by reading this thread in the openchrome forums.
[http://wiki.openchrome.org/tikiwiki/tiki-view_forum_thread.php?comments_parentId=4903&topics_threshold=0&topics_offset=1&topics_sort_mode=lastPost_desc&topics_find=&forumId=1](http://wiki.openchrome.org/tikiwiki/tiki-view_forum_thread.php?comments_parentId=4903&topics_threshold=0&topics_offset=1&topics_sort_mode=lastPost_desc&topics_find=&forumId=1)

---

### Post by TuxCrafter on 2008-03-11
> **cor2y said:**
> Ok for anyone with the k8m890ce VIA chipset here is how i got openchrome working.
If you are on Gutsy all you need is the svn source code and nothing else.
Follow the first half of the instructions on this page.
[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code)
And don't forget to change the driver from vesa to openchrome as listed below in the instructions there, IGNORE the part about rebuilding the drm kernel, just do the first half with compiling the openchrome driver and the final part of changing from vesa to openchrome.
Why TuxCrafter's script did not work for me i don't know.
And how do i know not to use the drm kernel section in the guide?
by reading this thread in the openchrome forums.
[http://wiki.openchrome.org/tikiwiki/tiki-view_forum_thread.php?comments_parentId=4903&topics_threshold=0&topics_offset=1&topics_sort_mode=lastPost_desc&topics_find=&forumId=1](http://wiki.openchrome.org/tikiwiki/tiki-view_forum_thread.php?comments_parentId=4903&topics_threshold=0&topics_offset=1&topics_sort_mode=lastPost_desc&topics_find=&forumId=1)


The install script of this topic does the same thing and it also setup the xorg file and installs the correct building dependency's.

If you tried to do your suggested steps on a clean install it will not work, unless you install all the build dependency first.

---

### Post by cor2y on 2008-03-11
like i said i don't know why that method worked while your script didn't.
The svn link is the same and the script does the same thing (at least to my untrained eyes) as the manual method listed there.
So why it would hang or go into graphics safe mode after the reboot i don't know.

---

### Post by TuxCrafter on 2008-03-11
> **cor2y said:**
> like i said i don't know why that method worked while your script didn't.
The svn link is the same and the script does the same thing (at least to my untrained eyes) as the manual method listed there.
So why it would hang or go into graphics safe mode after the reboot i don't know.

Yes it should have worked..

Did you make any changes to your xorg file beside the vesa to openchrome? The safe mode system of ubuntu is in my eyes also a very irritating system, bad designed and makes debugging more difficult. (the openchrome driver is also not detected correctly by the save mode system)

---

### Post by cor2y on 2008-03-11
yes thats all i changed.
vesa to openchrome in xorg.conf using the manual method.

---

### Post by keratos on 2008-03-15
Hi TuxCrafter

Currently using vesa (stock vanilla) driver on my K8M890 (chrome 9) VGA chip.

I compiled and installed this driver, X runs but it is painfully slow. Clicking between windows takes about 2 seconds and "top" reveals X using about 60% CPU?

Any ideas?

---

### Post by TuxCrafter on 2008-03-15
> **keratos said:**
> Hi TuxCrafter

Currently using vesa (stock vanilla) driver on my K8M890 (chrome 9) VGA chip.

I compiled and installed this driver, X runs but it is painfully slow. Clicking between windows takes about 2 seconds and "top" reveals X using about 60% CPU?

Any ideas?

are you sure you are using the openchrome driver? please check your xorg file and xorg logs after restarting. (failsave system of ubuntu is messing thinks up)

---

### Post by keratos on 2008-03-15
absolutely TuxCrafter.

Xorg.0.log attached

Any ideas? Would be very appreciated.

X is taking 50 to 60 % CPU ??

---

### Post by keratos on 2008-03-15
bump (sorry!)

xorg.conf attached

---

### Post by TuxCrafter on 2008-03-15
> **keratos said:**
> absolutely TuxCrafter.

Xorg.0.log attached

Any ideas? Would be very appreciated.

X is taking 50 to 60 % CPU ??

Hmm the driver seems to be loaded ok. I did see that XvMC is not yet supported on your chip this can cause high cpu load when playing movies.

An ohterthing you can try is to disable all 3D rendering modules, see the first post for that.

(WW) CHROME(0): [XvMC] XvMC is not supported on this chipset

---

### Post by keratos on 2008-03-15
Hi

3D rendering disabled as per ..


 Section "Module"
    Disable "glx"
    Disable "xtrap"
    Disable "record"
    Disable "GLcore"
    Disable "dri"
EndSection


No difference.

BTW, I am not playing any video etc.

This is just logging in and opening a window, say Xterm, clicking the window title and moving around the screen ...

Sloooooooow

vesa driver is 500% better !!

wierd?

---

### Post by TuxCrafter on 2008-03-15
yes its unwanted behaviour, please report the issue at the openchrome mailinglist with all the xorg logs.

---

### Post by keratos on 2008-03-15
OMG

I could have done that in the first place and got where I am now. NOWHERE

Thanks a lot.

"unwanted behavior"

I have another synopsis for it , alas not wishing to go against the forum rules, I will resist the very great temptation.

vesa it is then.

---

### Post by TuxCrafter on 2008-03-15
> **keratos said:**
> OMG

I could have done that in the first place and got where I am now. NOWHERE

Thanks a lot.

"unwanted behavior"

I have another synopsis for it , alas not wishing to go against the forum rules, I will resist the very great temptation.

vesa it is then.

Its not my fault it does not work, its VIA's fault they do not release enough documentation.

You may try to reset your bios to default settings maybe that helps..

---

### Post by keratos on 2008-03-15
sorry
SORRY

yes SORRY

I was not having a go at you,

just my frustration at lack of success.

YES , you are awesome and I take my hat off to you.

Its just that I was NEARLY there, nearly. 

Actually, the decent thing to do is for me to go and purchase a bloody good graphics card in the first place, rather than some naff useless onboard VGA.

Ah well.

And boo to VIA as well. Infact, because they are closed source, I'm going to buy a card now , not sure what would be good, dont want to spend too much as I dont game, but some desktop eye candy wouldnt go amiss. Suppose I need to do more googling now to find a linux video card that works.

Bye

---

### Post by chromedome on 2008-03-15
Thank you Tuxcrafter, that worked well for me.  Back in the summer, as a total LInux noob, I spent several frustrating hours trying to get that driver working.  Your script made it a breeze on my new install of Gutsy.

It's a shame about the 3D, but I'm not a gamer and I can live without the eye candy for a while.

---

### Post by keratos on 2008-03-16
For information, I've been playing a little, trying to debug and offer the results to this post...

I managed to get the system more stable...

The driver and the system, performs excellent, far better than the vesa driver in 2D (of course no 3D) however I had to disable composite manager in xfce's System->WindowTweaks.

This is a shame because xfce has out of the box window shadowing, transparency etc.
 
If I go back to the vesa driver then I can re-enable composite and the system flies once more? Note that all I do is change the "Device..." from openchrome to vesa.

All other xorg.conf settings are as suggested in first post.

How strange.

---

### Post by gary4gar on 2008-03-18
i Finally gave up, after trying for two years, i brought a AGP card for my display. THis Unichorme has worst support:x

---

### Post by TuxCrafter on 2008-03-18
> **gary4gar said:**
> i Finally gave up, after trying for two years, i brought a AGP card for my display. THis Unichorme has worst support:x

If you have this option than it is a good solution, VIA has indeed bad support, i hope you did not direct your frustration about the support on me.

---

### Post by keratos on 2008-03-19
I'm giving up too.

My chip is K8M890 and is not widely supported.

For the sake of about 20GBP I can buy an nvidia card, no fancy gaming, but with XGL and desktop eye candy support. 

Anyway, well done tuxcrafter for stickign with it, you have the patience of  saint.

---

### Post by TuxCrafter on 2008-03-19
> **keratos said:**
> I'm giving up too.

My chip is K8M890 and is not widely supported.

For the sake of about 20GBP I can buy an nvidia card, no fancy gaming, but with XGL and desktop eye candy support. 

Anyway, well done tuxcrafter for stickign with it, you have the patience of  saint.

I also bought a intel based mini-itx systems with onboards graphics, but these things are not perfect and not cheap. So I am just supporting openchrome installation on ubuntu/debian as long as it works.

---

### Post by venomrat on 2008-03-23
Hi,

I'm sorry if this is the wrong place to ask and ubuntu is very new to me.

I recently bought a Artigo builder kit with a pico-itx motherboard.

The specs state that it has a VX700 chipset with Integrated VIA UniChrome Pro™ II 3D/2D AGP graphics.

Does the openchrome driver support this chipset? I don't see it mentioned in th openchrome web site.

I'm trying to get the board to display at a resolution of 1680x1050.

I fail with windows xp. I'm now trying with ubuntu. I did a persistent usb pendrive install using this guide:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

I then downloaded the openchrome drivers using synaptic manager.

They display card is still not recognised. :(

Any tips or help would be great.

---

### Post by TuxCrafter on 2008-03-24
> **venomrat said:**
> Hi,

I'm sorry if this is the wrong place to ask and ubuntu is very new to me.

I recently bought a Artigo builder kit with a pico-itx motherboard.

The specs state that it has a VX700 chipset with Integrated VIA UniChrome Pro™ II 3D/2D AGP graphics.

Does the openchrome driver support this chipset? I don't see it mentioned in th openchrome web site.

I'm trying to get the board to display at a resolution of 1680x1050.

I fail with windows xp. I'm now trying with ubuntu. I did a persistent usb pendrive install using this guide:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

I then downloaded the openchrome drivers using synaptic manager.

They display card is still not recognised. :(

Any tips or help would be great.

Hi there, nice motherboard you got ;-p, the openchrome project is the only project that has the change of succeeding. You can try this driver installation, if it fault try to use the experimental source tree instead of the stable. If that fails contact the openchrome mailinglist and give them your gzipt xorg.log file. If openchrome does not work use the vesa driver that way you have at leased some functionality. until it gets supported.

---

### Post by wintersmith on 2008-03-24
> **venomrat said:**
> Hi,

I'm sorry if this is the wrong place to ask and ubuntu is very new to me.

I recently bought a Artigo builder kit with a pico-itx motherboard.

The specs state that it has a VX700 chipset with Integrated VIA UniChrome Pro™ II 3D/2D AGP graphics.

Does the openchrome driver support this chipset? I don't see it mentioned in th openchrome web site.

I'm trying to get the board to display at a resolution of 1680x1050.

I fail with windows xp. I'm now trying with ubuntu. I did a persistent usb pendrive install using this guide:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

I then downloaded the openchrome drivers using synaptic manager.

They display card is still not recognised. :(

Any tips or help would be great.

Hey there,

I have the same kit that you do, but I don't have the same resolution needs. 

I did get the graphics (2D only) to work, but I had to install directly from source. You can find detailed instructions for that at:

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Mine is working in 1280x1024. I read a review site that could not get anything working well at resolutions greater than 1024x768, but you never know.

Good luck!

---

### Post by tdebruin on 2008-03-27
mmmh, I have an integrated Via Chipset on my motherboard (P4M800CE/Pro with UniChrome Pro IGP rev 01). I used to have it working under Ubuntu Dapper, but later I installed a Nvidia AGP card. After recently upgrading to Hardy I decided to give the VIA chipset another go (I needed the Nvidia card on another machine). 

Now just doing a 
```
sudo apt-get install xserver-xorg-video-openchrome
```
and restarting the xserver by doing ctrl-alt-bckspace, everything seems fine, but:
I wanted to check the fps with glxgears, but apparently somewhere down the line I broke the glx:
```
$ glxgears -info
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```
and also:
```
 $ grep "^(EE)" /var/log/Xorg.0.log 
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```

Somehow I cannot figure what's wrong. Does someone have an idea what I could do to at least locate the problem?

---

### Post by venomrat on 2008-03-28
Thanks TuxCrafter and wintersmith.

@ TuxCrafter, the script did not work for me. I had some error stating something SVN missing. I did not capture the error in detail. Sorry.

I'll retry soon.

@ wintersmith, I'll give it a try.

---

### Post by Djainette on 2008-03-30
Dri is working again with the via driver in Hardy.

---

### Post by tdebruin on 2008-03-31
Aha,
I reported having 'lost' the glx extension after installing openchrome driver in hardy. 
After (re)  installing the following packages:
```
Installed the following packages:
libgl1-mesa-dri (7.0.3~rc2-1ubuntu2)
xorg-driver-fglrx (1:7.1.0-8-3+2.6.24.11-12.31)
xorg-driver-fglrx-dev (1:7.1.0-8-3+2.6.24.11-12.31)

Reinstalled the following packages:
devede (3.6-0.0ubuntu1)
libgl1-mesa-dev (7.0.3~rc2-1ubuntu2)
libgl1-mesa-glx (7.0.3~rc2-1ubuntu2)

```
glxgears works again. Magic! I'm not sure which of these packages did the trick, honestly, but hey, it works...

Thx tuxcrafter (and ubuntu community support)!

---

### Post by Modplanman on 2008-04-01
Does this work for 64 bit? 

Also, to be more precise, 64 but for P4M900?

I was gonna try try this, but one of the packages installs in 32 bit, when obviously it would be more appropriate for the 64 one to be installed, surely? (the package was libc6-dev).

---

### Post by dariusdwtt on 2008-04-06
Does not work. I have it installed, but am stuck on vesa.

So either all the people in the poll have the same chip/card or the problem is with Ubuntu.

We need to find the common denominator between all the people who took the poll.
Either some have a varient of the chip, or a varient of Ubuntu?

darius@darius-desktop:~$ sudo apt-get install xserver-xorg-video-openchrome
[sudo] password for darius: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-openchrome is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
darius@darius-desktop:~$

---

### Post by dariusdwtt on 2008-04-06
P4M890 + VT8237R Plus

---

### Post by dariusdwtt on 2008-04-07
WORKING NOW!!!

after sudo dpkg-reconfigure -phigh xserver-xorg

went to screen resolution, changed it now no more flicker.

---

### Post by mark1981 on 2008-04-22
hi!
i am an "ubuntian" from italy.
i have just installed openchrome with the script!
it's great but i have a maximum resolution of 1024x768!
i have fujitsu amilo li1705, is that correct?

---

### Post by TuxCrafter on 2008-04-22
> **mark1981 said:**
> hi!
i am an "ubuntian" from italy.
i have just installed openchrome with the script!
it's great but i have a maximum resolution of 1024x768!
i have fujitsu amilo li1705, is that correct?

possible this is correct with your current settings, maybe changing some settings like the vbe mode can provide you with higher resolutions the name of the laptop sounds very familiar it is possible somebody else in this topic provided some solution.

---

### Post by mark1981 on 2008-04-23
> **TuxCrafter said:**
> possible this is correct with your current settings, maybe changing some settings like the vbe mode can provide you with higher resolutions the name of the laptop sounds very familiar it is possible somebody else in this topic provided some solution.

now the resolution problem is solved but i have strange behaviour, like mouse's scrolling in a strange way. i am going to do some tests then i will report.
thanks a lot
Marco

---

### Post by bonz042 on 2008-04-26
Thank you! I had given up since i couldn't even get 7.10 to install and couldn't get openchrome to compile in 7.04. Running great now in 8.04 with openchrome installed

---

### Post by TuxCrafter on 2008-04-26
> **bonz042 said:**
> Thank you! I had given up since i couldn't even get 7.10 to install and couldn't get openchrome to compile in 7.04. Running great now in 8.04 with openchrome installed

Ah nice to here somebody else has it also working on 8.04. Thanks for reporting back.

---

### Post by chromedome on 2008-04-26
I guess I should have mentioned...I compiled mine under Gutsy, and it went fine; got the Hardy beta a week before the Release Candidate and it found the existing OpenChrome drivers without issue.

---

### Post by TuxCrafter on 2008-04-27
> **chromedome said:**
> I guess I should have mentioned...I compiled mine under Gutsy, and it went fine; got the Hardy beta a week before the Release Candidate and it found the existing OpenChrome drivers without issue.

Jups that can indeed be true. I gusty the problem was the old version of the package that made users recompile the new version with this script. If the new package stays updated this script is depreciated.

---

### Post by PhatKat on 2008-04-29
Hi all!! I have just finished my first DIY Ubuntu box over the weekends and so far so good but i am using Biostar K8M800 and am stuck in 640 x 480 screen resolution so help!! I am posting this from my new box but the online experience would be better with at least 1024 x 768. I had read through some pages of this thread and i am still confused cos i am an Ubuntu noob (been using Windows all the while ^^) Heck i don't even know how to install stuff on Ubuntu! So could anyone help me in my wish to have at least 1024 x 768 on integrated graphics with this mobo or should i just get a cheap AGP card? Thanks in advance!

---

### Post by TuxCrafter on 2008-04-29
> **PhatKat said:**
> Hi all!! I have just finished my first DIY Ubuntu box over the weekends and so far so good but i am using Biostar K8M800 and am stuck in 640 x 480 screen resolution so help!! I am posting this from my new box but the online experience would be better with at least 1024 x 768. I had read through some pages of this thread and i am still confused cos i am an Ubuntu noob (been using Windows all the while ^^) Heck i don't even know how to install stuff on Ubuntu! So could anyone help me in my wish to have at least 1024 x 768 on integrated graphics with this mobo or should i just get a cheap AGP card? Thanks in advance!

welcome to the forum,

first some basics to say: if you buy a new motherboard go for one with an intel onboard grapics so intel intel intel this also counts for laptops.

If you want a 3D experience you should buy a new nvidia grapics cards.

If you can live with only 2D and want to get your current system up and running try this first:

open a terminal and type:
sudo apt-get install libviaxvmc1 libviaxvmcpro1 xserver-xorg-video-openchrome

restart your computer, and check if you can change your resolution.

if this does not work please come back and report.

---

### Post by PhatKat on 2008-04-29
Hi and thanks a lot! Didn't expect such a quick response hehe Ok i did what u suggested and it didn't allow me to set resolution. You are referring to System--> Pref--> Screen Resolution right? Also this is what was the output in terminal:

gogo@gogo-desktop:~$ sudo apt-get install libviaxvmc1 libviaxvmcpro1 xserver-xorg-video-openchrome
[sudo] password for gogo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libviaxvmc1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libchromexvmc1
E: Package libviaxvmc1 has no installation candidate
gogo@gogo-desktop:~$

---

### Post by TuxCrafter on 2008-04-29
> **PhatKat said:**
> Hi and thanks a lot! Didn't expect such a quick response hehe Ok i did what u suggested and it didn't allow me to set resolution. You are referring to System--> Pref--> Screen Resolution right? Also this is what was the output in terminal:

gogo@gogo-desktop:~$ sudo apt-get install libviaxvmc1 libviaxvmcpro1 xserver-xorg-video-openchrome
[sudo] password for gogo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libviaxvmc1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libchromexvmc1
E: Package libviaxvmc1 has no installation candidate
gogo@gogo-desktop:~$

Ok just try the following commands and do a reboot:
```
sudo apt-get install xserver-xorg-video-openchrome
sudo cp /etc/X11/xorg.conf /etc/X11/xorg-backup.conf
sudo sed -i -e "/Section \"Device\"/,/EndSection/s,.*Driver.*,\tDriver\t\t\"openchrome\",g" /etc/X11/xorg.conf

```

---

### Post by PhatKat on 2008-04-29
Hi again! No can do i'm afraid :( However appreciate your suggestions ^^

---

### Post by TuxCrafter on 2008-04-29
> **PhatKat said:**
> Hi again! No can do i'm afraid :( However appreciate your suggestions ^^

??? you are afraid? and cant execute the commands?? i don't understand what you mean :-p

Please expand your feedback

---

### Post by PhatKat on 2008-04-30
> **TuxCrafter said:**
> Ok just try the following commands and do a reboot:
```
sudo apt-get install xserver-xorg-video-openchrome
sudo cp /etc/X11/xorg.conf /etc/X11/xorg-backup.conf
sudo sed -i -e "/Section \"Device\"/,/EndSection/s,.*Driver.*,\tDriver\t\t\"openchrome\",g" /etc/X11/xorg.conf

```


Oh did as suggested above and still can't set resolution above 640 x 480 >.< Hmm is GeForce FX5500 good enough for just the net/office Ubuntu box? See a few used ones real cheap hehe

---

### Post by TuxCrafter on 2008-04-30
> **PhatKat said:**
> Oh did as suggested above and still can't set resolution above 640 x 480 >.< Hmm is GeForce FX5500 good enough for just the net/office Ubuntu box? See a few used ones real cheap hehe

Yes the GeForce will be fine.

Can you show me the output of the commands you tried.

---

### Post by PhatKat on 2008-04-30
Ok this is the output from terminal:

gogo@gogo-desktop:~$ sudo apt-get install xserver-xorg-video-openchrome
[sudo] password for gogo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-openchrome is already the newest version.
The following packages were automatically installed and are no longer required:
  classpath-gtkpeer classpath-common cacao libgcj-common classpath
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gogo@gogo-desktop:~$

Edit: Hmm just in case i didn't mention : am using 8.04

---

### Post by TuxCrafter on 2008-04-30
> **PhatKat said:**
> Ok this is the output from terminal:

gogo@gogo-desktop:~$ sudo apt-get install xserver-xorg-video-openchrome
[sudo] password for gogo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-openchrome is already the newest version.
The following packages were automatically installed and are no longer required:
  classpath-gtkpeer classpath-common cacao libgcj-common classpath
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gogo@gogo-desktop:~$

Edit: Hmm just in case i didn't mention : am using 8.04

ok that is good this means you should be able to use the openchrome driver

did you executed the following command:
```
sudo sed -i -e "/Section \"Device\"/,/EndSection/s,.*Driver.*,\tDriver\t\t\"openchrome\",g" /etc/X11/xorg.conf
```
yes that is one command

then post the output of the following command as an text file on this forum:

```
sudo cat /etc/X11/xorg.conf
```

then reboot your system.

---

### Post by PhatKat on 2008-04-30
gogo@gogo-desktop:~$ sudo sed -i -e "/Section \"Device\"/,/EndSection/s,.*Driver.*,\tDriver\t\t\"openchrome\",g" /etc/X11/xorg.conf
[sudo] password for gogo: 
gogo@gogo-desktop:~$ sudo cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"OpenChrome"
	Busid		"PCI:1:0:0"
	Driver		"openchrome"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic CRT Display"
	Modelname	"Monitor 1024x768"
	Horizsync	31.5-61.0
	Vertrefresh	50-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1024x768@75"	"1024x768@70"	"832x624@75""1024x768@60"	"800x600@60"	"1280x960@60"	"800x600@75"	"800x600@72""800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
gogo@gogo-desktop:~$

---

### Post by TuxCrafter on 2008-04-30
> **PhatKat said:**
> gogo@gogo-desktop:~$ sudo sed -i -e "/Section \"Device\"/,/EndSection/s,.*Driver.*,\tDriver\t\t\"openchrome\",g" /etc/X11/xorg.conf


Not really as an text file attachment, but make sure to do this next time!

the driver seems to be loaded correctly, you should be able to select the correct resolution.
if not this is probably due to your monitor settings and you can try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This was not a laptop correct? just a simple vga connection to a crt screen?

---

### Post by PhatKat on 2008-05-01
Thanks! Ok think we are making progress cos after that i see that there is an option of setting 1440 x 900 resolution and 640 x 480 and no other options. Setting 1440 x 900 makes the screen huge and i can move the entire screen with my mouse? Please advise... Oh ya i am using a 19" LCD

---

### Post by TuxCrafter on 2008-05-01
> **PhatKat said:**
> Thanks! Ok think we are making progress cos after that i see that there is an option of setting 1440 x 900 resolution and 640 x 480 and no other options. Setting 1440 x 900 makes the screen huge and i can move the entire screen with my mouse? Please advise... Oh ya i am using a 19" LCD

What is your native resolution of your monitor? and how is it connected? (vga)
I will make a config file with this date, that you can use.

---

### Post by PhatKat on 2008-05-02
Hmm how do i find out my monitor's native resolution? It i connected via VGA and shall fill you in on more details when i knock off work! :P Thks

edit: had a spare HDD lying around and installed buntu 7.10 and resolution is fine! wifi slow though :( Still want to make 8.04 work cos it's really cool (cept for resolution)

---

### Post by TuxCrafter on 2008-05-02
> **PhatKat said:**
> Hmm how do i find out my monitor's native resolution? It i connected via VGA and shall fill you in on more details when i knock off work! :P Thks

edit: had a spare HDD lying around and installed buntu 7.10 and resolution is fine! wifi slow though :( Still want to make 8.04 work cos it's really cool (cept for resolution)

we will get it working dont worry i will help you through it..

your native resolution is most time the maximum resolution it is also documentation in the manuals of your monitor.

---

### Post by PhatKat on 2008-05-02
Ok upon goggling these are my LCD's specs:
[http://www.viewpoints.com/Hanns-G-JW199D-Monitor-review-ca8a](http://www.viewpoints.com/Hanns-G-JW199D-Monitor-review-ca8a)
Think it's native resolution is 1440 x 900

---

### Post by TuxCrafter on 2008-05-02
> **PhatKat said:**
> Ok upon goggling these are my LCD's specs:
[http://www.viewpoints.com/Hanns-G-JW199D-Monitor-review-ca8a](http://www.viewpoints.com/Hanns-G-JW199D-Monitor-review-ca8a)
Think it's native resolution is 1440 x 900

ok, first install this great text editor:
```
sudo apt-get install geany
```then make a backup of your old xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```then open your configuration file
```
 sudo geany /etc/X11/xorg.conf
```

replace all the text with the text in the attachment of this message (xorg.txt)

then reboot your system

---

### Post by PhatKat on 2008-05-02
Wow thanks! Will hook up my HDD with 8.04 as soon as i can and try the steps you stated ^^ Shall post back to share hehe

---

### Post by PhatKat on 2008-05-02
OK finally got the HDD with 8.04 hooked back in :P Hmm definitely on to something here - now i am able to set resolution to 800 x 600 max and this is much better than 640 x 480! Still short of 1024 x 768 but with your help i am sure we can do it hehe. One more thing: i have not been able to play DVDs with Totem and all i get is a green screen and audio :confused: Thks for your patience thus far though :popcorn:

---

### Post by uhappo on 2008-05-11
Any news on getting resolution better?

---

### Post by PhatKat on 2008-05-12
Hmm from me - i just hold off the 8.04 upgrade and running gutsy for now w/o any issues :P

---

### Post by TuxCrafter on 2008-05-12
> **PhatKat said:**
> Hmm from me - i just hold off the 8.04 upgrade and running gutsy for now w/o any issues :P

please try this xorg settings, and reply with an attached zip file of the following file:
```
sudo cat /var/log/Xorg.0.log
```

---

### Post by uhappo on 2008-05-12
```

sudo cat /var/log/Xorg.0.log

```

---

### Post by uhappo on 2008-05-12
I DID IT!!!

Well, on my laptop, I chose openchrome for driver, and changed the screen for LCD-screen 1024-768 (just tried it for the heck of it), restarted X-server and voilla!!!

And now I'm back on business!!!

---

### Post by TuxCrafter on 2008-05-12
> **uhappo said:**
> I DID IT!!!

Well, on my laptop, I chose openchrome for driver, and changed the screen for LCD-screen 1024-768 (just tried it for the heck of it), restarted X-server and voilla!!!

And now I'm back on business!!!


please post your xorg file

---

### Post by uhappo on 2008-05-12
```

Section "Module"
    Disable			"glx"
    Disable			"dri"
EndSection

Section "InputDevice"
	Identifier		"Generic Keyboard"
	Driver			"kbd"
	Option			"XkbRules"		"xorg"
	Option			"XkbModel"		"pc105"
	Option			"XkbLayout"		"us"
	Option			"XkbOptions"	"compose:ralt"
EndSection

Section "InputDevice"
	Identifier		"Configured Mouse"
	Driver			"mouse"
	Option			"CorePointer"
EndSection

Section "Device"
	Identifier		"Configured Video Device"
EndSection

Section "Monitor"
	Identifier		"Configured Monitor"
EndSection

Section "Screen"
	Identifier		"Default Screen"
	Monitor			"Configured Monitor"
	Device			"Configured Video Device"
	DefaultDepth    16
EndSection

Section "ServerLayout"
	Identifier		"Default Layout"
	Screen			"Default Screen"
EndSection

```

---

### Post by ScorpKing on 2008-05-12
> **uhappo said:**
> I DID IT!!!

Well, on my laptop, I chose openchrome for driver, and changed the screen for LCD-screen 1024-768 (just tried it for the heck of it), restarted X-server and voilla!!!

And now I'm back on business!!!

I can conferm that this is working. Thanks uhappo! :D

---

### Post by TuxCrafter on 2008-05-12
> **uhappo said:**
> I DID IT!!!

Well, on my laptop, I chose openchrome for driver, and changed the screen for LCD-screen 1024-768 (just tried it for the heck of it), restarted X-server and voilla!!!

And now I'm back on business!!!

Good to see that my suggestion works with the new xorg file.

---

### Post by uhappo on 2008-05-12
I booted once, I had to set same settings again, I'll see how it goes next time, but at least it is now working. I'm veeery happy! Glad I could help!

---

### Post by PhatKat on 2008-05-13
Whoa tis is exciting news! Gonna try this first thing after knocking off work :P

---

### Post by PhatKat on 2008-05-13
Still have 1440 x 900, 800 x 600 and lower resolution options :( Below is the output:

size)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 832x624 (57284)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x768 (80140)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x800 (83460)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x768 (64995)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (121500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1152x864" (vrefresh out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1440x900 (108840)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): CrtcHSyncEnd out of range.
(II) CHROME(0): Not using default mode "1440x900" (horizontal sync too wide)
(II) CHROME(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1440x900 (106500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (36000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (30240)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (25200)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 720x400 (28320)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using driver mode "1280x1024" (height too large for virtual size)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78800)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (75000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (65000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 832x624 (57284)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (50000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1152x864 (108000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using driver mode "1280x1024" (height too large for virtual size)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (104000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Required bandwidth is not available. (148932608 > 74000000)
(II) CHROME(0): Not using driver mode "1152x864" (mode clock too high)
(II) CHROME(0): Not using driver mode "1280x960" (height too large for virtual size)
(II) CHROME(0): ViaValidMode: Validating 1440x900 (136750)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Required bandwidth is not available. (194359632 > 74000000)
(II) CHROME(0): Not using driver mode "1440x900" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1440x900 (106500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Required bandwidth is not available. (155228256 > 74000000)
(II) CHROME(0): Not using driver mode "1440x900" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1440x900 (106500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Required bandwidth is not available. (155228256 > 74000000)
(II) CHROME(0): Not using driver mode "1440x900" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1280x800 (83460)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Required bandwidth is not available. (122876472 > 74000000)
(II) CHROME(0): Not using default mode "1280x800" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (108000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Required bandwidth is not available. (149299200 > 74000000)
(II) CHROME(0): Not using driver mode "1152x864" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (108000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Required bandwidth is not available. (149299200 > 74000000)
(II) CHROME(0): Not using default mode "1152x864" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1280x768 (80140)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Required bandwidth is not available. (117970688 > 74000000)
(II) CHROME(0): Not using default mode "1280x768" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1152x768 (64995)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Required bandwidth is not available. (96935040 > 74000000)
(II) CHROME(0): Not using default mode "1152x768" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78800)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Required bandwidth is not available. (118084680 > 74000000)
(II) CHROME(0): Not using driver mode "1024x768" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (75000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Required bandwidth is not available. (110209568 > 74000000)
(II) CHROME(0): Not using driver mode "1024x768" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (65000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Required bandwidth is not available. (94377880 > 74000000)
(II) CHROME(0): Not using driver mode "1024x768" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78750)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Required bandwidth is not available. (118009752 > 74000000)
(II) CHROME(0): Not using default mode "1024x768" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (75000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Required bandwidth is not available. (110209568 > 74000000)
(II) CHROME(0): Not using default mode "1024x768" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (65000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Required bandwidth is not available. (94377880 > 74000000)
(II) CHROME(0): Not using default mode "1024x768" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 832x624 (57284)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Required bandwidth is not available. (77409264 > 74000000)
(II) CHROME(0): Not using driver mode "832x624" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 832x624 (57284)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Required bandwidth is not available. (77409264 > 74000000)
(II) CHROME(0): Not using default mode "832x624" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (50000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (36000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (50000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (36000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (30240)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (25200)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (25175)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 720x400 (28320)
(II) CHROME(0): ViaModePrimaryVGAValid
(--) CHROME(0): Virtual size is 1440x900 (pitch 1440)
(**) CHROME(0): *Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) CHROME(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) CHROME(0): *Driver mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
(II) CHROME(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) CHROME(0): *Driver mode "800x600": 40.0 MHz (scaled from -0.0 MHz), 37.9 kHz, 60.3 Hz
(II) CHROME(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) CHROME(0): *Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
(II) CHROME(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) CHROME(0): *Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) CHROME(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) CHROME(0): *Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
(II) CHROME(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) CHROME(0): *Default mode "800x600": 40.0 MHz (scaled from -0.0 MHz), 37.9 kHz, 60.3 Hz
(II) CHROME(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) CHROME(0): *Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
(II) CHROME(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) CHROME(0): *Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) CHROME(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) CHROME(0): *Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
(II) CHROME(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(**) CHROME(0): *Driver mode "640x480": 30.2 MHz (scaled from 0.0 MHz), 35.0 kHz, 66.7 Hz
(II) CHROME(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(**) CHROME(0): *Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) CHROME(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) CHROME(0): *Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) CHROME(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) CHROME(0): *Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
(II) CHROME(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) CHROME(0): *Default mode "640x480": 25.2 MHz (scaled from -0.0 MHz), 31.5 kHz, 59.9 Hz
(II) CHROME(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) CHROME(0): *Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
(II) CHROME(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) CHROME(0): Display dimensions: (410, 260) mm
(**) CHROME(0): DPI set to (89, 87)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) CHROME(0): VIAUnmapMem
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf4000000 - 0xf4ffffff (0x1000000) MS[B]
	[1] 0	0	0xf0000000 - 0xf3ffffff (0x4000000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xf6001000 - 0xf60010ff (0x100) MX[B]
	[7] -1	0	0xf6000000 - 0xf60000ff (0x100) MX[B]
	[8] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[9] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[18] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[19] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[20] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[22] -1	0	0x0000df00 - 0x0000df0f (0x10) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[24] -1	0	0x0000dd00 - 0x0000dd0f (0x10) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[26] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[28] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) CHROME(0): VIAScreenInit
(II) CHROME(0): VIAMapFB
(--) CHROME(0): mapping framebuffer @ 0xf0000000 with size 0x4000000
(==) CHROME(0): Write-combining range (0xf0000000,0x4000000)
(--) CHROME(0): Frame buffer start: 0x7f9ba8eb0000, free start: 0x278d00 end: 0x4000000
(II) CHROME(0): VIAMapMMIO
(--) CHROME(0): mapping MMIO @ 0xf4000000 with size 0x9000
(--) CHROME(0): mapping BitBlt MMIO @ 0xf4200000 with size 0x20000
(II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) CHROME(0): VIASave
(II) CHROME(0): Primary
(II) CHROME(0): Crtc...
(II) CHROME(0): TVSave...
(II) CHROME(0): VIAWriteMode
(II) CHROME(0): ViaModePrimary
(II) CHROME(0): ViaModePrimaryVGA
(II) CHROME(0): ViaModePrimaryVGA: Setting up 800x600
(II) CHROME(0): CrtcHTotal: 0x420
(II) CHROME(0): CrtcHDisplay: 0x320
(II) CHROME(0): CrtcHBlankStart: 0x320
(II) CHROME(0): CrtcHBlankEnd: 0x420
(II) CHROME(0): CrtcHSyncStart: 0x330
(II) CHROME(0): CrtcHSyncEnd: 0x380
(II) CHROME(0): CrtcVTotal: 0x271
(II) CHROME(0): CrtcVDisplay: 0x258
(II) CHROME(0): CrtcVSyncStart: 0x259
(II) CHROME(0): CrtcVSyncEnd: 0x25C
(II) CHROME(0): CrtcVBlankStart: 0x258
(II) CHROME(0): CrtcVBlankEnd: 0x271
(II) CHROME(0): Offset: 0x168
(II) CHROME(0): Fetch Count: 0x0C8
(II) CHROME(0): ViaTVPower: Off.
(II) CHROME(0): ViaSetPrimaryFIFO
(II) CHROME(0): ViaSetPrimaryDotclock to 0xa48c04
(II) CHROME(0): ViaSetUseExternalClock
(II) CHROME(0): VIAAdjustFrame
(II) CHROME(0): VIAAdjustFrame
(II) CHROME(0): - Blanked
(II) CHROME(0): - Visuals set up
(II) CHROME(0): VIAInternalScreenInit
(II) CHROME(0): - B & W
(II) CHROME(0): Using 2700 lines for offscreen memory.
(II) CHROME(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	8x8 color pattern filled rectangles
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		21 256x256 slots
		7 512x512 slots
		32 8x8 color pattern slots
(==) CHROME(0): Backing store disabled
(II) CHROME(0): - Backing store set up
(II) CHROME(0): - SW cursor set up
(II) CHROME(0): VIAHWCursorInit
(II) CHROME(0): - Def Color map set up
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): - Palette loaded
(II) CHROME(0): DPMS enabled
(II) CHROME(0): - DPMS set up
(II) CHROME(0): - Color maps etc. set up
(II) CHROME(0): direct rendering disabled
(II) CHROME(0): Using default xfree86 memcpy for video.
(WW) CHROME(0): [XvMC] Cannot use XvMC without DRI!
(II) CHROME(0): - Done
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "compose:ralt"
(**) Generic Keyboard: XkbOptions: "compose:ralt"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) CHROME(0): VIAAdjustFrame
(II) CHROME(0): VIAAdjustFrame
SetClientVersion: 0 9
gogo@gogo-desktop:~$

---

### Post by TuxCrafter on 2008-05-13
(II) CHROME(0): ViaValidMode: Validating 1440x900 (108840)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): CrtcHSyncEnd out of range.
(II) CHROME(0): Not using default mode "1440x900" (horizontal sync too wide)

found your issue, i will give you a new xorg file

---

### Post by TuxCrafter on 2008-05-13
Here you go, this one should do the trick

---

### Post by PhatKat on 2008-05-13
Hiya! Thanks so much for your patience! Shall try this 1st thing when i finish work hehe

---

### Post by coady on 2008-05-14
I recently did a clean install of Hardy 8.04 from CD. The openchrome driver was loaded and present in the 'xorg.conf' but after booting into the graphical desktop I got only one screen resolution which is too high for the panel on this laptop. I modified the 'xorg.conf' to give me the correct  screen res (see below), but the splash screen is still at the original (incorrect) resolution. I can modify the boot line to omit the splash and use only the text screen, but I would like to know how to get the correct splash to load. Any other comments on similar experience with problems concerning the openchrome driver and no available screen res options would also be helpful. Thanks.

Modified 'xorg.conf':
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"openchrome"
	BusID		"PCI:1:0:0"
	Option		"SWcursor"	"true"
	Option		"EnableAGPDMA"	"off"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    31-48
	ModelName    "1024X768@60HZ"
	Option       "DPMS"
	VertRefresh  50-60
	# V-freq: 60.00 Hz  // h-freq: 47.80 KHz
	# Modeline	 "1024x768" 60.80  1024 1056 1128 1272   768  768  770  796 
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Attached: 'HARDY_Xorg_0_log.zip'

---

### Post by PhatKat on 2008-05-14
Hmm updated the xorg - still no change :(

---

### Post by PhatKat on 2008-05-14
Edit: By some strange miracle or beginner's luck i have managed to get my wish of 1024 x 768 on 8.04LTS!!!! This was how i did it:

I have a HDD with Gutsy installed and VIA IGP runs fine with it so all i did was a distro upgrade!

Edit: The IGP returned to its old ways (forgotten what i did to trigger it)  but i had saved the xorg file from Gutsy and simply pasted into 8.04 and so far all is well :lolflag:

---

### Post by mark1981 on 2008-05-15
I have still some problem with the driver, or I think so: while i am writing,  
the cursor moves by itself (often to the center of the next line).
i am sorry for my english...
:roll:

---

### Post by MayOne.Net on 2008-05-28
Thanks to this thread I finally got openchrome to work this afternoon. I have an old gateway laptop with VIA chipset and 1280x768 screen, and had fiesty up and running using openchrome from svn. Unfortunately when I did a fresh install of hardy for some reason the screen size came up 1600x1200 and freaked out when I tried to change it.

It doesn't quite work perfectly, but after the following steps, I can now at least see the whole screen.

First, I installed openchrome:
sudo apt-get install xserver-xorg-video-openchrome

Then I ran this command (trusting the other forum users wouldn't lead me astray):
sudo sed -i -e "/Section \"Device\"/,/EndSection/s,.*Driver.*,\tDriver\t\t\"openchrome\",g" /etc/X11/xorg.conf

And finally modified my xorg.conf adding the appropriate line for openchrome and the screen size. (See attached).

I still need to get video play back working and the screen occasionally freaks out on me, but it at least I can see it.

Also for some reason when I log in, the waiting screen still shows up at 1600x1200.

Any suggestions on fixing these issue would be greatly appreciated.

---

### Post by icodeme on 2008-11-03
neolinux@neoLinux:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)
06:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

---

### Post by TuxCrafter on 2008-11-03
Is the installation script still working? It is kind of while back since i tested it, because i moved all my systems to intel based graphical chipsets. If it does not work i can release a new version somewhere next week.

---

### Post by Yar4ek on 2008-11-06
Please check my logo.
Everything works nicely but I do not have a refresh of 60 Hz. : (
My version of Linux to Ubuntu 8.10.
Thank you in advance for your help.



PZDR

---

### Post by TuxCrafter on 2008-11-06
> **Yar4ek said:**
> Please check my logo.
Everything works nicely but I do not have a refresh of 60 Hz. : (
My version of Linux to Ubuntu 8.10.
Thank you in advance for your help.
PZDR

Let see if I can help you with this, It might be an issue with your tft and not the via graphical chipset but i try to help 

can you remove your default xorg file and restart the system to see whats happens:
```
sudo  mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by dkaddict on 2008-11-18
I have been using the Openchrome drivers since Edgy and have always had to compile from source. Then I found the Via driver that's supposed to be able to handle the big bit maps for 3D for Feisty. It isn't as good as Openchrome. The 3D is so bad it isn't worth the bother.

My problem is that I can't get past Feisty. I can't get any live CD later than Feisty to work and my laptop crashes every time I try to upgrade. I have burnt loads of 7.10 live CDs but can't even get the Alternatives to load in safe graphics mode. Could this be because of the Via driver and my xorg.conf? The only live CDs that give me a screen are SLAX and pre 7.10 Ubuntu, which load the VESA driver. If I can get a Live CD screen I can do the rest. I am going to try 8.04 after doing a clean Feisty install and leaving the graphics on VESA. If it gives me a screen, instead of switching it off, I take it that the Openchrome driver can be installed from the repository? Does it work ok or am I better off compiling myself?

I would have thought that the Live CDs would get better at detecting hardware but they seem to have gone backwards. They don't even come with cheat codes do they?

???

---

### Post by TuxCrafter on 2008-11-18
> **dkaddict said:**
> I have been using the Openchrome drivers since Edgy and have always had to compile from source. Then I found the Via driver that's supposed to be able to handle the big bit maps for 3D for Feisty. It isn't as good as Openchrome. The 3D is so bad it isn't worth the bother.

My problem is that I can't get past Feisty. I can't get any live CD later than Feisty to work and my laptop crashes every time I try to upgrade. I have burnt loads of 7.10 live CDs but can't even get the Alternatives to load in safe graphics mode. Could this be because of the Via driver and my xorg.conf? The only live CDs that give me a screen are SLAX and pre 7.10 Ubuntu, which load the VESA driver. If I can get a Live CD screen I can do the rest. I am going to try 8.04 after doing a clean Feisty install and leaving the graphics on VESA. If it gives me a screen, instead of switching it off, I take it that the Openchrome driver can be installed from the repository? Does it work ok or am I better off compiling myself?

I would have thought that the Live CDs would get better at detecting hardware but they seem to have gone backwards. They don't even come with cheat codes do they?

???

You should be able to use any live cd to boot as long as the kernel comes up. It may require some basic knowledge of Linux systems however.

When booting the cd change the boot options,and boot to single mode. now you can change everything via the cli, and maybe start x with changed xorg settings.

you can also just change your source.list to a newer apt repo update your cache install the new drivers and refert the apt-repo back, but this is not recommended.

I would recommend buying a new system with an intel gpu!

---

### Post by dariusdwtt on 2008-11-18
@dkaddict

It's unfortunate but VIA compatibility has always been a problem.
I've struggled too, but the best I could get had a low refresh rate, and it drove me bonkers! + headaches etc.

So even after doing all that, you may sit with a bit of a "lemony" setup.

If you can afford it, why not get an nvidia gpu :) (no more problems)
even a cheapy will give you better results than VIA. (8600gt ? value for money)

or better yet, what are your thoughts on DELL?

---

### Post by AndBurns on 2008-11-30
Great script.  It worked for me bringing to an end a 48 hour wander through the desert of not quite right solutions.

---

### Post by TuxCrafter on 2008-11-30
> **AndBurns said:**
> Great script.  It worked for me bringing to an end a 48 hour wander through the desert of not quite right solutions.

your welcome :-p, next if you got the possibility look for a computer with an intel on-board grapical chip, this will save you some troubles.

---

### Post by galojze on 2008-12-09
Any1 managed to get it working on Amilo LA1703?, after lots of surfing and many lost hours... I gave up. I had to install Xp back :S

---

### Post by volatino on 2008-12-11
great! the script worked.....the problem is that my mouse pointer disappeared...I am on ub 8.04.

any hints?

thanks in advance, and thanks for the script.

---

### Post by TuxCrafter on 2008-12-11
> **volatino said:**
> great! the script worked.....the problem is that my mouse pointer disappeared...I am on ub 8.04.

any hints?

thanks in advance, and thanks for the script.

Try using a software or hardware mouse pointer, you can configure this in the xorg.conf file.

[http://linux.die.net/man/4/openchrome](http://linux.die.net/man/4/openchrome)

**Option SWCursor** *boolean* Disable or enable the use of a software cursor. The default is disabled. 

```
Section "Device"
    Identifier      "Configured Video Device"
    Driver            "openchrome"    
    Option            SWCursor True 
EndSection
```

I hope that works, i have not tested it, since i dont own any via hardware anymore, i switched to intel grapical chipsets.

---

### Post by volatino on 2008-12-11
thanks but..nothing. Anyway, I even do not have this:

Section "Device"
    Identifier      "Configured Video Device"
    Driver            "openchrome"    
    Option            SWCursor True 
EndSection

in my xorg.conf. I tried to put in this section with both false and true, but nothing. It's a pity, anyway I think I wont' go on since the idea is to use the pc for video conferences. the same videoconf software on that pc is sooo slow with ubuntu (native linux, not under wine) compared to windows version, I suppose via is too blame for that, too.

Many thanks for your efforts.

---

### Post by TuxCrafter on 2008-12-11
> **volatino said:**
> thanks but..nothing. Anyway, I even do not have this:

Section "Device"
    Identifier      "Configured Video Device"
    Driver            "openchrome"    
    Option            SWCursor True 
EndSection

in my xorg.conf. I tried to put in this section with both false and true, but nothing. It's a pity, anyway I think I wont' go on since the idea is to use the pc for video conferences. the same videoconf software on that pc is sooo slow with ubuntu (native linux, not under wine) compared to windows version, I suppose via is too blame for that, too.

Many thanks for your efforts.

No problem, next time try to buy a laptop or system with a Intel chip set this allows you to have a far better Linux experience. Linux is not really to blame for the not fully working VIA chip-sets. You may to try out the Thanks button on the forum ;-p

---

### Post by allfootballgoals on 2008-12-11
I found a really good website with latest football video highlights, Allfootballgoals.com
it's highly updated and it has the premier league, la liga, serie a, german league + all national cups and european cups and national teams.

---

### Post by volatino on 2008-12-11
> **TuxCrafter said:**
> No problem, next time try to buy a laptop or system with a Intel chip set this allows you to have a far better Linux experience. Linux is not really to blame for the not fully working VIA chip-sets. You may to try out the Thanks button on the forum ;-p

I know, Linux is not to blame, I am enjoying it on my laptop of course :-)

---

### Post by volatino on 2008-12-11
I have to say that, before throwing the pc away, I tried with opensuse.....and everything worked without tweaks... :eek::???:

beside all, I wonder just why.

---

### Post by TuxCrafter on 2008-12-11
> **volatino said:**
> I have to say that, before throwing the pc away, I tried with opensuse.....and everything worked without tweaks... :eek::???:

beside all, I wonder just why.

If you are really into it you can try comparing the xorg.0.logs. btwI assume you tried installing the default xserver-xorg-video-openchrome drivers before trying out my script?

---

### Post by volatino on 2008-12-12
yes, I already had the driver before running the script. 
I will give a look at the xorg log, even if ... there is no trace of ubuntu anymore on that pc, maybe with a live? mmmhhh, no I do not think so. Maybe in a rainy day I could try to install ubuntu again :-) and look at that log.

Ciao

---

### Post by TsUPeR on 2009-02-04
I saw an early post about someone having trouble getting DVI to work on their VIA EPIA EN12000eg board. I just managed to get 1280x720 on my SONY tv.

Here is my xorg.conf (ubuntu 8.10)

```
Section "Device"
        Identifier      "Openchrome Device"
        Driver          "openchrome"
        Option "VBEModes" "true"
EndSection

Section "Monitor"
        Identifier  "DVI"
        Modeline "1280x720" 74.48 1280 1336 1472 1664 720 721 724 746 -HSync +HSync
EndSection


Section "Screen"
        Identifier      "Default Screen"
        Device          "Openchrome Device"
        Monitor "DVI"
        SubSection "Display"
         Depth 24
         Virtual 1280 720
         Modes "1280x720"
        EndSubSection
EndSection

```

If someone got any ideas as how to get DVD playback smooth I would be happy

:D

---

### Post by bonnyfused on 2009-05-26
Hy people.

How high should "glxgears" FPS be with openchrome drivers on an Acer Aspire 1355 (AMD Athlon XP-M 2600+)?
I get around 50-52 FPS...

Moving windows in Xorg I see them somehow "sticky" movement...

Any help will be appreciated.

Thanks.

---

### Post by TuxCrafter on 2009-05-27
> **bonnyfused said:**
> Hy people.

How high should "glxgears" FPS be with openchrome drivers on an Acer Aspire 1355 (AMD Athlon XP-M 2600+)?
I get around 50-52 FPS...

Moving windows in Xorg I see them somehow "sticky" movement...

Any help will be appreciated.

Thanks.

It should hire then 100 at leased, while this is always speculation glxgears is not a benchmarking tool. You can only use it to see if 3D rendering is working. What does glxinfo say? And you should use the drivers that come with Ubuntu, there should not be a need to compile the driver manually.

Cheers

---

### Post by bonnyfused on 2009-05-27
Hello all! Everything ok, thanks for the great script! Succeeded in installing Ubuntu 9.04 on an Acer Aspire 1355!!!

Used this guide (script):

[http://ubuntuforums.org/showthread.php?p=7357750](http://ubuntuforums.org/showthread.php?p=7357750)

---

### Post by gevork on 2009-07-14
create new symbolic link
Prepare the installation files [Y/n]?y
Install the via openchrome 2D driver [Y/n]?y
/home/gevork/Desktop/xf86-video-unichrome-0.2.6/openchrome-stable.sh: line 76: svn: command not found
/home/gevork/Desktop/xf86-video-unichrome-0.2.6/openchrome-stable.sh: line 78: cd: openchrome: No such file or directory
/home/gevork/Desktop/xf86-video-unichrome-0.2.6/openchrome-stable.sh: line 79: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.


WHat to do? I have just clicked on this .sh file attached at first of the topic and get at the end this problem... Please help...

---

### Post by gary4gar on 2009-07-15
> **gevork said:**
> create new symbolic link
Prepare the installation files [Y/n]?y
Install the via openchrome 2D driver [Y/n]?y
/home/gevork/Desktop/xf86-video-unichrome-0.2.6/openchrome-stable.sh: line 76: svn: command not found
/home/gevork/Desktop/xf86-video-unichrome-0.2.6/openchrome-stable.sh: line 78: cd: openchrome: No such file or directory
/home/gevork/Desktop/xf86-video-unichrome-0.2.6/openchrome-stable.sh: line 79: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.


WHat to do? I have just clicked on this .sh file attached at first of the topic and get at the end this problem... Please help...
you seem to be missing subversion(svn), install it and then try
```
sudo apt-get install subversion
```

---

### Post by CosSin on 2011-08-08
I know it's nearly two and a half years since these posts, but i was wondering of the progress made in the openchrome project on the K8M890CE chipset. I have a laptop (so i can't really change the video card) and i want to get the openchrome driver working on ubuntu 11.04. If any1 still picks up on this thread I would gladly apreciate any help.

---

### Post by vijayrao on 2012-04-06
yes
worked well
thanx

---

### Post by sshaitan on 2012-04-24
&#1064;&#1083;&#1072;&#1082; &#1082;&#1072;&#1082;&#1086;&#1081;-&#1090;&#1086;, &#1074;&#1084;&#1077;&#1089;&#1090;&#1086; &#1090;&#1072;&#1082;&#1080;&#1093; &#1080;&#1079;&#1074;&#1088;&#1072;&#1097;&#1077;&#1085;&#1080;&#1081;, &#1083;&#1091;&#1095;&#1096;&#1077; &#1073; &#1088;&#1072;&#1089;&#1089;&#1082;&#1072;&#1079;&#1072;&#1083; &#1082;&#1072;&#1082; &#1087;&#1086;&#1089;&#1090;&#1072;&#1074;&#1080;&#1090;&#1100; &#1076;&#1088;&#1086;&#1074;&#1072; &#1085;&#1072; Unichrome pro

---

### Post by emeraldknight1977 on 2012-12-31
I know this is an old post, and might not be ment for current Ubuntu. It did run with errors, but I'm still using the Gallium 0.4 on llvmpipe (LLVM 0x300) instead of OpenChrome. I have the factory drivers for my integrated graphics card, but I they don't seam to work with Ubuntu 12.04.

---

