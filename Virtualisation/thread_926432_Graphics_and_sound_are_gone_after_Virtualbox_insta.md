---
title: "Graphics and sound are gone after Virtualbox install"
date: 2008-09-21
forum: Virtualisation
---

### Post by Todaro on 2008-09-21
Dear experts,

In order to resume Virtualbox installation I run Synaptic to get some drivers Virtualbox needs to work.

After that, my Soundblaster sound card and my NVIDIA GeForce 8400 graphic card stopped working.

On Add/Remove, **NVidia binary X.Org driver** is shown as installed but Hardware Drivers doesn't show anything (it showed before Virtualbox). I tried deinstalling/reinstalling **NVidia binary X.Org driver**, no effect.

I also removed Virtualbox and all packs I installed after. Nothing worked.

Could anyone give me a hand please?

Thanks,

Marcelo

---

### Post by Todaro on 2008-09-22
I can`t believe I posted a problem nobody knows how to solve.

Does it mean that I`ll have to wipe Ubuntu from my HD and restart from scratch? Please someone tell me that it`s not true!

Any tip will be greatly appreciated.

Thanks!

---

### Post by overdrank on 2008-09-22
Hi and I have moved your thread to Virtualization.
As for your issue I have only encountered this once. It appears that when you installed the kernel mods for VB this has disabled those needed for your nvidia graphics and sound card. Sorry I do not have a resolution for your issue.

---

### Post by stuv812 on 2008-09-23
Spaces are updated or when a visitorEasy way to stay in the forum Good ServicesAbout all go to [shanghai massage](http://www.massageinchina.com) Good Services ok!sites where they can express&#65281;[massage shanghai](http://www.massageinshanghai.org/)-Relax web site from massage in shanghai[beijing massage](http://www.full-body-massage.cn/)-this service for  massage beijing[massage shanghai](http://www.topsexymassage.cn/)-this service for  massage china[shanghai massage](http://www.wowpowerleveling-wow.com/)-massage vip service in shanghai

---

### Post by Todaro on 2008-09-24
Dear folks,

Since I haven't been able to get help anywhere nor could wait any longer I decided to take the last and more radical choice: wipe the whole thing and restart from scratch.

Now I've got back sound, video and Virtualbox (the villain of the story) up and running.

So, whenever someone else comes here with a similar issue, you may rest assure that the only effective solution is healing the disease by killing the patient.

Best regards,

Marcelo

---

### Post by Tiler on 2008-09-29
I don't have the option to kill the patient, so I'll post the solution.

First thing I have done is uninstall the VirtualBox and uninstalled the nvidia drivers.  Next my plans are to reboot and reinstall the Nvidia drivers and Nvidia Settings.  I'll be back.

---

### Post by Todaro on 2008-09-30
It didn't work for me. Seemed that the system had been damaged beyond any fixing. That's why I killed the patient. 

Good luck.

---

### Post by webmoose on 2008-09-30
I ran into this problem and I **completely removed** all Virtualbox packages.
I then **completely removed** all Linux Restricted modules and then re-install them. This didn't make any differences but after i logged in I did the following:

cd /etc/X11
sudo mv xorg.conf xorg.conf.bak
sudo mv xorg.conf.***x*** xorg.conf (where ***x*** indicates the oldest backup version of xorg.conf)
I then restarted ubuntu and It worked for me.

Next step ... try to re-install Virtualbox !!!

Hope this helps !

Webmoose.

---

### Post by Tiler on 2008-09-30
Virtualbox is the sacrificial lamb in this case.  I'll save that for another day, on a test install.

**Here's what I found:**

I [did these things]("http://ubuntuforums.org/showthread.php?t=931130&highlight=nvidia+reinstall") to completely remove NVIDIA.  Also used the synaptic complete remove of all things NVIDIA:

sudo apt-get remove envyng-core
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove

sudo dpkg-reconfigure -phigh xserver-xorg 

**Next**, I tried to reinstall Nvidia from a command line after killing Gnome, [like it says here]("http://ge.ubuntuforums.com/showthread.php?t=880787").

**What happened next, exposed the real problem**.  Nvidia couldn't find its own Kernel because I had removed it.  It also couldn't find the Ubuntu Kernel (or that's how I read it).

*_From /var/log/nvidia-installer.log:_*
Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 173.14.12.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

**Now**, I'm looking for threads about the poor peeps who have had Kernel issues in the past to try figuring out how to rebuild.  Any assistance in that direction will be greatly appreciated.

**That's the update folks.**

---

### Post by Tiler on 2008-09-30
Also because I know people will ask:

Uname -a
2.6.24-19-386 #1 Wed Aug 20 21:59:50 UTC 2008 i686 GNU/Linux
[B]
Updated:[/B]  Running Kernel Update with KernelCheck.

---

### Post by Tiler on 2008-10-01
2.6.26.5-ultimate #1 Tue Sep 30 22:48:20 CDT 2008 i686 GNU/Linux

I recommend KernelCheck.  *Be advised*, it takes a couple of hours.

After I finished, I went back the latter thread (posted above), killed Gnome, installed the newest Nvidia driver from command line, let it rebuild its Kernel and restarted Gnome.
[B]
Next[/B] I did an apt-get install nvidia-settings and everything is running fine sans VirtualBox.  I'm more concerned with having my dual monitor setup because of telecommuting, than I am with virtualbox.

After I finish this post, I'm going to reestablish my dual monitor setup and try to find a way to clean up my grub menu. I have about 30 options when I boot and I need only the current kernel and XP.

**Note to mods:**  I chose the wrong thread to post this to because I was more interested in resolving the Nvidia problems than the virtualization.  Please excuse my oversight but there seems to be a dearth of information on this topic either way.

I'm not super technical but my theory is that 2.6.24-19 +Nvidia +VirtualBox create an incompatible situation, Kernel wise.

Nvidia still isn't showing up in the Proprietary Drivers list but I don't think it matters now that I have the driver installed and can use nvidia-settings.

If anyone wants to see the new info from the Nvidia Driver Install Log, message me.  It's over 600 lines long and probably irrelevant to the average user trying to resolve this.

---

### Post by dmflad on 2009-02-19
Have 8.04LTS 32-bit running on Dell Latitude D620 LT. All working great until used synaptic to install VirtualBox. VirtualBox killed my sound and my wireless. LT reported "no sound card available" and "no wireless card available" when checked.  

I didn't really want to rebuild LT again. (Have rebuilt it three times in two months due to other issues, one hardware, one Ubuntu. Didn't wantto have to set up confs and Firefox and Juniper again.

So I got out my 8.04LTS CD and booted up and in live mode checked that wireless and sound cards did exist and did work. They worked just fine. Then I booted up with the CD and went thru like doing install to hard drive (fresh install) - BUT with some careful key tapping.

In section where I set up partitions I edited each of my partitions so they got their label/name again. I made sure that "format partition" was NOT checked for each of my partitions.  In section for user info I made sure to but all info in as before VirtualBox. Then I let the install proceed.

It looked like lots of packages got installed and at end I was told to boot without the CD. Ubuntu came up fine, sound worked wireless worked, and icon popped up that I had updates ready. I did the updates and had to boot again.

All looks fine on the LT. My files and settings are as before VirtualBox.And I am a happy camper once again.  

I had VirtualBox working on this LT before hardware problems cause major rebuilds and I need it for a WinXP guest because not all my critical work software runs under Linux, Crossover Linux or Wine. Next step is to try installing VirtualBox again, maybe getting it from their website instead of thru synaptic connection.

---

