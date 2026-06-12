---
title: "HOWTO: Install Nvidia drviers including DKMS module"
date: 2009-01-11
forum: Tutorials
---

### Post by Npl on 2009-01-11
I figured out the last days how to correctly setup DKMS for newer Versions of the NVidia-Driver. In case you dont know, DKMS is a nifty little system that will ensure you dont run into trouble if you install a new kernel. Running a new Kernel requires ALL modules to be recompiled, and in the case of propietary drivers (ie drivers you dint install through apt-get) this task is left to you.
DKMS is there to automate this very task, you wont ever have to care for kernel-upgrades again.

I wrote a little script(attached) that extracts the necessary parts from the NVIDIA-Driver and can configure DKMS.

[SIZE="3"]Who can use this tutorial[/SIZE]
Theoretically the procedure should work on all Ubuntus that have the necessary packages (Gutsy and later), I only tested this on Intrepid tough. It should work with all current and future NVIDIA-Installers (180, 173, 96 and 71 Series ).
[LIST]
[*]Your OS should be Ubuntu - Gutsy or later. Earlier versions should work too if you manage to manually install DKMS but I wont cover that
[*]You need a Nvidia Card obviously, and the official NVIDIA-Installer [Latest Versions can be found here](http://www.nvnews.net/vbulletin/showthread.php?t=122606)
[/LIST]

Heres the instructions how to use the latest NVIDIA-Driver on Ubuntu and configure DKMS for it:

[SIZE="3"]Step 1: Uninstall the Nvidia-driver from the repositories (if you installed it from there)[/SIZE]
Use the Restricted Driver Manager and/or do it by commandline.
This depends on your Version of Ubuntu and the Driver you previously installed (via apt-get or Restricted driver manager). Search for packages containing nvidia in the name in synaptic, generally you should unistall all nvidia*glx* and nvidia*kernel* packages. for example:
```
sudo apt-get remove nvidia-glx-180 nvidia-180-kernel-source nvidia-xconfig nvidia-settings
```

[SIZE="3"]Step 2: Keep Ubuntu from using the driver in the repos[/SIZE]
Open the file /etc/default/linux-restricted-modules-common

```
sudo gedit /etc/default/linux-restricted-modules-common
```
and add the modules nv nvidia_new to the list of disabled modules.
```
DISABLED_MODULES="nv nvidia_new"
```
This will keep the restricted driver Manager from nagging.

[SIZE="3"]Step 3: Prepare the Files and packages you will need[/SIZE]
Packages necessary to build the kernel module:
```
sudo apt-get install dkms build-essential make
```
You will also need the Kernel-header for ALL the kernels you plan to use (typically linux-headers-generic or linux-headers-rt), you need to make sure you pick the right one(s). To install the headers for Ubuntu`s normal Kernel:
```
sudo apt-get install linux-headers-generic
```

Get the NVIDIA Binary driver for your system (32 or 64 Bit). Follow the links from [here](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

Grab my script (attached) for configuring DKMS and unpack it in the same directory as the NVIDIA-Driver.

running the script as non-root will only do some sanity-checks so I suggest you so so now by typing (replace 180.37 with the version you are installing)
```
sh ./installdkms.sh 180.37
```


[SIZE="3"]Step 4: Installing the driver[/SIZE]
Reboot ubuntu into safe mode and choose root-prompt, this is IMHO the easiest way to drop into an environment where you can safely install the driver. You might not have internet-connectivity tough, thats why you installed all the packages before.

Now cd into the directory where you saved the NVIDIA-Driver and the script. For example:
```
cd /home/<yourusername>
```

First part is to install the Driver, the command ofcourse depends on the filename, example:
```
sh ./NVIDIA-Linux-x86_64-180.37-pkg0.run
```
Follow the instructions, they are pretty obvious I guess. If it complains about beeing in runlevel 1 just tell it to continue anyway.
If you are on Hardy or later I suggest you **dont** let the Installer configure your xorg.conf but do so yourself. The Installer will produce a working configuration, but its better to do so by Hand, read up Appenix A before rebooting.

now run the script, you need to replace 180.37 with the driverversion you are going to install 
```
sh ./installdkms.sh 180.37
```
If everything turns out ok, you can query the state of DKMS. Heres the output on my system:
```
dkms status
nvidia, 180.37, 2.6.27-11-generic, x86_64: installed 

```

last Step is to exit the commandline and boot into ubuntu normally
```
shutdown -r 0
```

[SIZE="3"]Appendix A: Telling X to use the nvidia driver[/SIZE]
If you told the installer to adjust the xorg.conf file you dont need to do anything.
And if you have trouble with this step you can still do it automatically by running "nvidia-xconfig"

If you choose to edit it manually (highly recommended) then execute
```
vim /etc/X11/xorg.conf
```

Hardy and later have a pretty minimalistic or even nonexistant xorg.conf, this is the whole file for my system:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection
```

[SIZE="3"]Appendix B: Script for running the nvidia-installer[/SIZE]
I also added a script which installs the base driver, creates a xorg.conf only if noone exists and then runs the installDKMS.sh script. This should work well if you already have xorg.conf edited or are running a fresh Ubuntu (Hardy or newer) which has no xorg.conf.
Simply follow the steps in this tutorial untill you have to run the NVIDIA-Installer and instead run (replace 180.37 with your version)
```
sh ./fullinstallNV.sh 180.37
```
Then reboot

[SIZE="3"]Appendix C: Removing old DKMS Modules[/SIZE]
If you installed previous drivers you will have multiple Nvidia Modules. You can delete the old DKMS Modules with
```
sudo dkms remove -m nvidia -v <oldversion> --all
```
Unfortunatly that still leaves the source behind, so delete that aswell:
```
sudo rm -rf /usr/src/nvidia-<oldversion>
```


Update 23.1.2008: Added fixes from jdillaczek and jocko - Script is at V2
Update 26.1.2008: Now also works if NVIDIA-Installer is not marked executable, added lotsa comments - Script is at V3
Update 10.3.2008: Now needs driverversion as argument, tested and worked with all current (legacy) NVIDIA Installers - Script is at V4

---

### Post by Mr. Picklesworth on 2009-01-19
Nifty!
Just trying this out now, but thanks in advance :)

---

### Post by Npl on 2009-01-19
Hmm, hope everything goes well for you. The script got DL 19 times with one response, so if I dont hear back from you I will assume I`m responsible for 19 blownup Computers.

---

### Post by jdillaczek on 2009-01-22
That is a nifty little script -- thanks for figuring this out and sharing the solution! Here are a few typos I noticed (and I had to remove the -q option from the dkms commands; otherwise the script would just exit at that point -- not sure what's up with that): change line 48 from

```
if [ sanity != 1 ]
```

to

```
if [ $sanity != 1 ]
```

and line 71 from

```
$installername --extract-only --target $tempdir/installer
```

to

```
./$installername --extract-only --target $tempdir/installer
```

and line 80 from

```
cp $tempdir/installer/$installersourcedir/* $destsourcedir
```

to

```
cp -r $tempdir/installer/$installersourcedir/* $destsourcedir
```

(and remove the -q option from dkms commands on lines 95, 100, 103, and 106).

---

### Post by jocko on 2009-01-23
One more typo at row 16:
Change from:
```
packagedepencies=(dkms build-essentials make)
```To:
```
packagedepencies=(dkms build-essential make)
```But there seems to be one more problem. When I run the script it ends with:
```
Moving kmodule-source to /usr/src/nvidia-180.22
Creating dkms-configuration /usr/src/nvidia-180.22/dkms.conf
Delete temporary directory
Removing all previous DKMS Modules

[COLOR=Red]Error! There are no instances of module: nvidia
180.22 located in the DKMS tree.[/COLOR]

```**Edit:** I managed to get it to complete successfully by commenting out line 95, so that it does not try to remove something that is not there (is it likely that anyone would need to run the script again if the module is already in the dkms tree?).
I don't know much about bash, but wouldn't it be possible to make the script first check if there are any nvidia modules in the dkms tree, and only try to remove them if they really are there?

**Edit 2:** I tried again. First I removed the module with:
```
dkms remove -m nvidia -v 180.22 --all
```Then I reverted line 95 to it's original form:
```
dkms remove -m nvidia -v $driverversion --all -q
```And it worked without errors. So the -q needs to be there on line 95, otherwise the script will stop with an error if the module does not already exist...

**Edit 3:** I added a line (72) to the script to get it to run the actual installer as well.
So I attach a [modified version of the script]("http://ubuntuforums.org/attachment.php?attachmentid=100783&stc=1&d=1232692001") (with both jdillaczek's and my fixes).

The instructions for using the script to both install using nvidia's installer and add the module to dkms:
1. Unpack the tar.gz containing the script to the same folder as the nvidia installer (~/Desktop).
2. Go to cli-only mode (by some reason required by nvidia's installer):```
sudo /etc/init.d/gdm stop
```
3. Navigate to where the installer and script is located:```
cd ~/Desktop
```
4. Run the script:```
sudo ./installdkms.sh
```
5. Restart gnome:```
sudo gdm
```

---

### Post by Npl on 2009-01-23
Thanks for the feedback, I added jdillaczek fixes and made sure the script is not stopping at errors from the dkms-commands - they have undocumented returnvalues and generally are behaving a bit weird. Now theres a bit more verbose output since i removed the -q options aswell.

jocko: You need to drop out of the GUI since you cant replace kernelmodules while you are using them. Also I dont want to call the NVIDIA-Installer from within the script, its complex enough to warrant its explicit call.

---

### Post by sdennie on 2009-01-23
Nice tutorial.  Moved to tutorials and tips.  You may also want to point out that this is for Intrepid and above.  The same can be accomplished on Hardy (or any version actually) with: [ HOWTO: Automatically update manually installed NVidia drivers after kernel updates]("http://ubuntuforums.org/showthread.php?t=835573")

---

### Post by jocko on 2009-01-23
> **Npl said:**
> jocko: You need to drop out of the GUI since you cant replace kernelmodules while you are using them. Also I dont want to call the NVIDIA-Installer from within the script, its complex enough to warrant its explicit call.
I knew why nvidia wants the installer to run from a pure cli, I just think it would be equally good if the installer just built the module and let the user restart xorg afterwards to load the new module.

And I noticed one thing in your howto that may cause problems:
Nvidia's installer does not run from runlevel 1 (single user mode/recovery mode).
At least in my case it just complains about the runlevel and exits, so I have to boot normally (runlevel 2) and exit the gui by stopping gdm (sudo /etc/init.d/gdm stop), then run the installer with sudo.
Or have nvidia changed this behaviour of the installer lately (I know that at least the first beta version of the 180.xx series driver still did this)?

Other than that, I just tested your new script with a clean dkms tree and now it works fine and continues even if the "dkms remove" command can't find a module to remove.
Thank you for an excellent howto.

---

### Post by Npl on 2009-01-23
> **jocko said:**
> And I noticed one thing in your howto that may cause problems:
Nvidia's installer does not run from runlevel 1 (single user mode/recovery mode).It will warn about the runlevel but continue if you say so. Since Ubuntu uses runlevels quite differently it doesnt matter. In my case I dont have network-access tough.

Anyway I found installing the driver in fail-safe mode through Grub(runlevel 1) alot easier than stopping all relevant services. Sometimes the kernelmodule dint get replaced when I just stopped gdm.

sdennie: I know this will work for Intrepid and Nvidia 180.xx, but I think it should work with Hardy and eventually previous Ubuntus that have the necessary packages. Should also work the same with other Nvidia-Drivers...

---

### Post by jocko on 2009-01-23
> **Npl said:**
> It will warn about the runlevel but continue if you say so. Since Ubuntu uses runlevels quite differently it doesnt matter. In my case I dont have network-access tough.

Anyway I found installing the driver in fail-safe mode through Grub(runlevel 1) alot easier than stopping all relevant services. Sometimes the kernelmodule dint get replaced when I just stopped gdm.

Nevermind. I was wrong on the runlevel thing, it was apparently just a warning and the installer actually continues if I say "no"... I just didn't read it properly last time... so leave that part as it is now, it's easier and more reliant than just stopping gdm.

But I realized one more tip: When you are in runlevel 1 after booting to recovery mode, you don't have to reboot to reach the gui, just run "init 2". That will be faster than a complete reboot but will have the exact same result.

---

### Post by Shazaam on 2009-01-24
Npl...
Followed your instructions and I get an error running your script (as root)...
```
./installdkms.sh: line 71: ./NVIDIA-Linux-x86-180.22-pkg1.run: Permission denied

```
Steps to get error...
1. Boot in Recovery Mode-root shell.
2. Ran NVIDIA installer, success.
3. Ran your script=error message.
Up to date Intrepid with required headers and deps kernel 2.6.27.9-generic; permissions correct for both the NVIDIA installer and your script.

---

### Post by Npl on 2009-01-24
Hi, its possibly because the installer isnt marked executeable.

You can mark the installer executeable by doing (add sudo if it complains about rights):
```
chmod +x ./NVIDIA-Linux-x86-180.22-pkg1.run
```

I gotta leave for a while now, gonna workaround that in the script later.

---

### Post by Shazaam on 2009-01-24
Thanks, that worked out fine. I have another error but I don't think its related...
```
dkms status 
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.
vboxnetflt, 2.1.0, 2.6.27-9-generic, i686: installed 
nvidia, 180.22, 2.6.27-9-generic, i686: installed (original_module exists)
```
I am missing a vboxdrv listing that was there before running your script. I am listed as a member of vboxusers in Users and Groups. No idea what happened. Not a big deal as everything still works.

---

### Post by Npl on 2009-01-26
> **Shazaam said:**
> Thanks, that worked out fine. I have another error but I don't think its related...
```
dkms status 
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.
vboxnetflt, 2.1.0, 2.6.27-9-generic, i686: installed 
nvidia, 180.22, 2.6.27-9-generic, i686: installed (original_module exists)
```
I am missing a vboxdrv listing that was there before running your script. I am listed as a member of vboxusers in Users and Groups. No idea what happened. Not a big deal as everything still works.You can look at my script, it shouldnt be possible to touch other DKMS-Modules by running it.
Sorry if you somehow messed other drivers while tinkering around... I think reinstalling vbox should easily fix it tough. You dont have problems now, but you will probably get them the next time you install a kernel-update.

---

### Post by sdennie on 2009-01-26
The first few steps about installation are very good but, the DKMS step seems to be having problems.  I've never quite understood why DKMS was included in Intrepid (the functionality it provides has been in Ubuntu since day 1) but, after following the driver installation steps, this guide really does seem infinitely easier: [ HOWTO: Automatically update manually installed NVidia drivers after kernel updates]("http://ubuntuforums.org/showthread.php?t=835573")

---

### Post by Npl on 2009-01-26
> **sdennie said:**
> The first few steps about installation are very good but, the DKMS step seems to be having problems.  I've never quite understood why DKMS was included in Intrepid (the functionality it provides has been in Ubuntu since day 1) but, after following the driver installation steps, this guide really does seem infinitely easier: [ HOWTO: Automatically update manually installed NVidia drivers after kernel updates]("http://ubuntuforums.org/showthread.php?t=835573")Thats the second time you advertise your own tutorial in this thread. Do you have constructive critism to improve my tutorial? What problems are you talking about?

Yes I know you can keep the whole NVIDIA-Installer around, yes I know there are several other ways to do the same thing. The good thing about using a DKMS is that its a maintained solution, aslong as you have your sources and the dkms.conf file setup it should be painless to upgrade whatever part of your system. It beats carrying the whole Installer around forever IMHO.

---

### Post by sdennie on 2009-01-26
> **Npl said:**
> Thats the second time you advertise your own tutorial in this thread. Do you have constructive critism to improve my tutorial? What problems are you talking about?

Yes I know you can keep the whole NVIDIA-Installer around, yes I know there are several other ways to do the same thing. The good thing about using a DKMS is that its a maintained solution, aslong as you have your sources and the dkms.conf file setup it should be painless to upgrade whatever part of your system. It beats carrying the whole Installer around forever IMHO.

I admit that I am biased because I think DKMS is completely pointless.  I'm happy to point people at very simple ways to keep nvidia, vbox, ALSA, v4l, etc. up to date on kernel updates.  They all consist of 10-20 line scripts that are readable, understandable, and work without any "magic".  It's quite obvious what they are trying to do and many hundreds (thousands (no, millions)) of kernels have been installed using these methods.  The link I've pointed to twice us literally the method in which grub updates itself.  Kernel updates for proprietary drivers have never been broken.  DKMS tries to fix something that was never a problem in the first place.

---

### Post by Shazaam on 2009-01-27
Npl...
It's ok, everything still works fine so no problems. And once again thank you for your help.

---

### Post by Npl on 2009-03-10
just a shameless bump since I just updated the script, improved the tutorial and successfully tested the script with legacy drivers (173, 96 and 71).

Oh, and is there a way to fix the typo in the thread title? :oops:

---

### Post by PtitLu on 2009-06-05
Will test this script with 185.18.14 . Thanks for this "tip".

---

### Post by ozzyprv on 2009-06-07
After three days searching for this info....I got the driver installed.

The key point for me was making sure that
linux-headers-2.6.28-11-server
was installed. I am running that kernel to get the 4GB RAM recognized.

Thank you NPL!

---

### Post by ozzyprv on 2009-06-07
> **Npl said:**
> 

[SIZE="3"]Step 2: Keep Ubuntu from using the driver in the repos[/SIZE]
Open the file /etc/default/linux-restricted-modules-common

```
sudo gedit /etc/default/linux-restricted-modules-common
```
and add the modules nv nvidia_new to the list of disabled modules.
```
DISABLED_MODULES="nv nvidia_new"
```
This will keep the restricted driver Manager from nagging.


I have a question (well...two).

What exactly does Step 2 do?

And, why I still see two nVidia driver "suggestions", 180 and 173 -to be installed- at Administration > Hardware Manager ?

I just want to be 100% sure that the driver is properly installed before moving into troubleshooting my Compiz Fusion installation.

Thanks.

---

### Post by Npl on 2009-06-08
> **ozzyprv said:**
> I have a question (well...two).

What exactly does Step 2 do?keep ubuntu from installing nvidia kernel-drivers automatically.
> **ozzyprv said:**
> And, why I still see two nVidia driver "suggestions", 180 and 173 -to be installed- at Administration > Hardware Manager ?Thats a GUI-App called "Jockey", its quite possible not smart enough to look into "/etc/default/linux-restricted-modules-common" to figure out it shouldn`t/can`t install those drivers.

Remove the packages "nvidia-173-modaliases", "nvidia-180-modaliases", "nvidia-71-modaliases", "nvidia-96-modaliases" and "nvidia-common" to make it stop displaying the nvidia-driver. you could ofcourse remove jockey altogether =)
> **ozzyprv said:**
> I just want to be 100% sure that the driver is properly installed before moving into troubleshooting my Compiz Fusion installation.just run glxinfo or open the nvidia-settings. Both should tell if you run the nvidia-driver or not.

---

### Post by ozzyprv on 2009-06-24
Tested again, I thought I provide some feedback.

Updated to 2.6.28-13-server (from 2.6.28-11-server).

All I had to do to get the nVidia driver back was to install linux-headers-2.6.28-13-server.

It worked perfectly.

Cheers!

---

### Post by starscalling on 2009-06-29
ok trying a modification of this: i grabbed the 190.09 drivers, and to make the scripty be happy did this:
cp cudadriver_2.3-beta_linux_32_190.09.run NVIDIA-Linux-x86-190.09-pkg0.run

will update here if anything worx.

this is precipitated because i installed an older 180 driver and somehow left some kernel module remnants giving version mismatch's. 

so far we are at:

# sh installdkms.sh 190.09Checking for kernel-sources for the running kernel
Kernel-sources seem to be installed
Important: You should install the correct Packages
for ALL kernels you are using

Installing necessary packages

Nvidia Driver Version    190.09
Nvidia Installer Binary  ./NVIDIA-Linux-x86-190.09-pkg0.run
DKMS Module Directory    /usr/src/nvidia-190.09

Running Kernel           2.6.28-13-generic
Expect Kernel-Sources in /usr/src/linux-headers-2.6.28-13-generic

DKMS Version             dkms: 2.0.21.1
Unpacking installer
Moving kmodule-source to /usr/src/nvidia-190.09
Creating dkms-configuration /usr/src/nvidia-190.09/dkms.conf
Delete temporary directory
Removing eventual existing DKMS-Modules for the same driverversion
Done.
Adding Module to DKMS build system
Module Name: nvidia 190.09

Creating symlink /var/lib/dkms/nvidia/190.09/source ->
                 /usr/src/nvidia-190.09

DKMS: add Completed.
Doing initial module build

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.28-13-generic module KERNDIR=/lib/modules/2.6.28-13-generic IGNORE_XEN_PRESENCE=1 IGNORE_CC_MISMATCH=1 SYSSRC=/lib/modules/2.6.28-13-generic/build......
cleaning build area....

DKMS: build Completed.
Installing initial module

nvidia.ko:
Running module version sanity check.
 - Original module
   - Found /lib/modules/2.6.28-13-generic/kernel/drivers/video/nvidia/nvidia.ko
   - Storing in /var/lib/dkms/nvidia/original_module/2.6.28-13-generic/i686/
   - Archiving for uninstallation purposes
 - Installation
   - Installing to /lib/modules/2.6.28-13-generic/updates/dkms/

depmod......

DKMS: install Completed.
Done. Status of DKMS is:
nvidia, 190.09, 2.6.28-13-generic, i686: installed (original_module exists)

---

### Post by starscalling on 2009-06-29
worked perfectly. i get one error 4 times while installing any proprietary drivers:

unable to open '/usr/lib/xorg/modules/extensions/libglx.so' for reading (no such file or directory)

which supposedly may mean its looking for xorg's libglx instead of its own libglx - however none i've talked to yet seems to know how to fix whatever the problem is lol. 

and my sysinfo readout saved:
System information report, generated by Sysinfo: 6/29/2009 6:04:32 PM
[http://sourceforge.net/projects/gsysinfo](http://sourceforge.net/projects/gsysinfo)

SYSTEM INFORMATION
	Running Ubuntu Linux, the 5.0 release.
	GNOME: 2.26.1 (Ubuntu 2009-05-06)
	Kernel version: 2.6.28-13-generic (#44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009)
	GCC: 4.3.3 (i486-linux-gnu)
	Xorg: unknown (09 April 2009  02:10:02AM)
	Hostname: smashing-thunder
	Uptime: 0 days 1 h 37 min

CPU INFORMATION
	GenuineIntel, Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
	Number of CPUs: 4
	CPU clock currently at 3348.120 MHz with 4096 KB cache
	Numbering: family(6) model(15) stepping(11)
	Bogomips: 6696.24
	Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority

MEMORY INFORMATION
	Total memory: 3528 MB
	Total swap: 1953 MB

STORAGE INFORMATION
	SCSI device -  scsi2
		Vendor:  ATA      
		Model:  ST3500641AS      
	SCSI device -  scsi6
		Vendor:  PIONEER  
		Model:  DVD-RW  DVR-108  

HARDWARE INFORMATION
MOTHERBOARD
	Host bridge
		Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
		Subsystem: Giga-byte Technology Device 5000
	PCI bridge(s)
		Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
		Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
		Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
		Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
		Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01)
	USB controller(s)
		Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
		Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
		Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
		Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
		Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
		Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
		Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
		Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
	ISA bridge
		Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
		Subsystem: Giga-byte Technology Device 5001
	IDE interface
		JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 85 [Master SecO PriO])
		Subsystem: Giga-byte Technology Device b000

GRAPHIC CARD
	VGA controller
		nVidia Corporation GeForce 8600 GT (rev a1)
		Subsystem: Device 196e:0440

SOUND CARD
	Multimedia controller
		Creative Labs SB Audigy (rev 04)
		Subsystem: Creative Labs Device 1007

NETWORK
	Ethernet controller
		Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
		Subsystem: Giga-byte Technology Device e000

NVIDIA GRAPHIC CARD INFORMATION
	Model name: GeForce 8600 GT
	Card Type: PCI-E 16x
	Video RAM: 512 MB
	GPU Frequency: 576 MHz
	Driver version: NVIDIA UNIX x86 Kernel Module  190.09  Mon Jun 15 07:21:02 PDT 2009


again i repeat i get the same error on ANY proprietary driver, so i'm all ears. however i will say my settings for compiz and nvidia-settings that seem to work with no vid tearing in compiz:

a. i'm using fusion icon to activate; and i have loose bindings checked.
b. sync to vblank in ccsm, x server xvideo settings, and opengl settings.

and for my monitor i kept seeing 60hz refresh, and manually had to make it 50, as thats all my monitor was trying to say it could do or so. now tearing is at an absolute minimum, with almost none ever when fullscreen vid. good luck!

---

### Post by Rovies on 2009-08-02
Thank you Npl for a well written "howto" and to the many others for the editing.
I downloaded upgrades to Ubuntu 9.04, three days ago, and my monitor would only work in default configuration, or not at all. Nvidia X server settings were missing.

I am so glad that I can across this thread, as I am new to Linux, and the terminal stuff was a bit scary. I am now back in full working order, and have learned a lot.

(By the way, Mcafee doesn't like your link to the nvidia drivers, if you are browsing on a Windows PC. - [www.Nvidia.com](www.Nvidia.com) may be a better source).

Thanks:D

---

### Post by Ulukai on 2009-08-19
Thanks for the fine script. I just installed the latest 173.14.20 driver for my Geforce FX 5900 XT with it. 

But would you also be so kind to tell what we have to do to completely remove the installed driver and all DKMS settings? I know the Nvidia driver can be removed by nvidia-uninstall, but wouldn't leave this all the DKMS stuff? Will it be sufficient to remove the DKMS .conf file? And what other files have to be removed to clean up my system including all temp files your cript created? 

I don't ask this to be rude, but I read about the Nouveau driver and the Nvidia beta drivers which could offer me a better 2D support, so that's why I would like to know :-)

EDIT: 
Sorry, I didn't notice at first you already mentioned it in Appendix C :)

Appendix C: Removing old DKMS Modules
If you installed previous drivers you will have multiple Nvidia Modules. You can delete the old DKMS Modules with
Code:

sudo dkms remove -m nvidia -v <oldversion> --all

Unfortunatly that still leaves the source behind, so delete that aswell:
Code:

sudo rm -rf /usr/src/nvidia-<oldversion>

---

### Post by ozzyprv on 2009-10-25
Anyone had problems with the recent kernel upgrade? I am still trying to get through. So far no luck. Flying without nVidia driver.

---

### Post by ozzyprv on 2009-10-27
> **ozzyprv said:**
> Anyone had problems with the recent kernel upgrade? I am still trying to get through. So far no luck. Flying without nVidia driver.

It seems like the latest kernel (server at least) was not compatible with the nVidia driver I was using.
I haver kernel: 2.6.28-16-server
I had: NVIDIA-Linux-x86-185.18.14-pkg1

Just updating to linux-headers-2.6.2816-server did not work as before.

I had to start from scratch from post #1, deleting the other dkms instances and installing NVIDIA-Linux-x86-185.18.36-pkg1.

It is working now.

---

### Post by Liveforthenight on 2009-10-27
did all that you told me to do, now my computer is running in ultra low res.
it also will not let me fix it.
where did i screw up?

---

### Post by Npl on 2009-10-27
> **Liveforthenight said:**
> did all that you told me to do, now my computer is running in ultra low res.
it also will not let me fix it.
where did i screw up?No idea, Im no psychic. Start with posting the xorg.conf file, and which driver did you have before?

---

### Post by Liveforthenight on 2009-10-27
> **Npl said:**
> Im no psychic.

sorry forgot that part, :redface:
 is this what you are looking for there?
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder63)  Fri Aug 14 17:55:55 PDT 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Fri Aug 14 17:54:58 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

I know that I used to have the 180.xx and through your howto thingy i upgraded to 185.xx.
I used the thing you attached to the how to page, and told the installer to monkey with my xorg file.  then i rebooted and got super low graphics, but it is now using the 185.xx which is were i am stuck

---

### Post by Liveforthenight on 2009-10-27
I just took a look, there are quite a few

This is one
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

---

### Post by Liveforthenight on 2009-10-27
This is another
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon Mar 23 15:33:27 PST 2009

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Virtual     1024 768
        Depth       24
    EndSubSection
EndSection

---

### Post by Liveforthenight on 2009-10-27
And here is a third
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Fri Aug 14 17:54:58 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by Npl on 2009-10-28
Seems like theres nothing nontrivial in your xorg.conf file. If the driver works (which should be the case if you followed the procedure)then you should be able to run the "nvidia-settings" utility - might have to sudo it.
Try if you can fix your problem with that tool (it should atleast tell you if the driver is indeed loaded and working), also you can replace your xorg.conf with the minimalistic one (so there cant be messed up settings in this file):
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection
```
(and try running "nvidia-settings" again if you couldnt get it to work before).

---

### Post by Andymeows on 2009-11-15
I recently upgraded from 9.04 to 9.10 and got the flashing text login prompt. I was able to resolve it by running 'apt-get install dkms nvidia-185-kernel-source'. Hopefully this will help someone else.

---

### Post by go_beep_yourself on 2009-12-27
> **Npl said:**
> [SIZE=3]Step 2: Keep Ubuntu from using the driver in the repos[/SIZE]
Open the file /etc/default/linux-restricted-modules-common

```
sudo gedit /etc/default/linux-restricted-modules-common
```and add the modules nv nvidia_new to the list of disabled modules.
```
DISABLED_MODULES="nv nvidia_new"
```This will keep the restricted driver Manager from nagging.

This file does not exist in Ubuntu 9.10. How can the modules be disabled in 9.10?

---

### Post by aboud on 2009-12-29
did any one had a low res problem and fixed it? 

with no xorg.conf in karmic it seems to be inpossible to fix this very low res issue, i tried many ways to create one 'xorg.conf' but non worked. 
it the fourth time i reinstall karmic trying to get this nvidia working.

---

### Post by go_beep_yourself on 2009-12-29
> **aboud said:**
> did any one had a low res problem and fixed it? 

with no xorg.conf in karmic it seems to be inpossible to fix this very low res issue, i tried many ways to create one 'xorg.conf' but non worked. 
it the fourth time i reinstall karmic trying to get this nvidia working.

You are not the only one. I think it's time lots of people file bug reports at [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+filebug](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+filebug)
to get the developers' attention. They could try to blame this on nvidia, but I even have low resolution using the nv driver. Ubuntu (Looking in System>Pref>Display) can no longer detect the model of my monitor like it has in the past or with my other monitor (dual monitors), possibly the reason why resolution can't be set higher.

---

### Post by robertsaron on 2010-05-17
This how to is amazing. Parts of it helped. I got to the step where it says to run the script, then had to quit.There are several questions I need help with. First off where to get the script? I did not see a link anywhere to download it.

Second, the path to /etc/default/linux-restricted-modules-common does not exist on my system. I am using the latest version of Kbuntu. So maybe it is different. What is the path then if it is different?

The next thing, only thing the machine boots into is shell. So how to boot into safe mode from shell? I already have the latest driver for nvidia downloaded. When doing the install, Here is an error of comes up.

ERROR: unable to load the kernel module'nvidia.ko'. This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb/nvidiafb is present and preevents the NVIDIA kernel module from obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU installed in this system is not supported by this NVIDIA Linux graphics driver release.

My card is a nvidia FX 5800 Geforce, Kernel version is 2.6.32.22-generic, Nvidia version trying to install: 195.36.24

---

### Post by uniden9 on 2010-10-11
It appears nvidia has changed the extract folder structure.  The  usr/src/nv is now kernel folder in the newer 256.53 driver. 

Edit line 40 of installdkmc.sh  V4 and change it from:
readonly installersourcedir=usr/src/nv
to
readonly installersourcedir=kernel

With out this change, you will get a error similar to
cp: cannot stat `/tmp/tmp.{Random Text}/installer/usr/src/nv/*': No such file or directory

For information on the extraction change, just run:
./NVIDIA-Linux-x86_64-256.53.run --extract-only --target nvidia_extract
and compare it to a older driver.

---

### Post by Nitronium on 2011-07-06
What a fracking awesome thread. Npl, you're a dude, many thanks. I chose not to run your script, but rather do it manually so that I know exactly what's going on. Love it, cheers man...

---

### Post by spleach on 2012-04-24
Cheers for the script. I also went through each step manually and am using it now with 295.20 drivers.
I did two things differently though:-
1) After extracting, moved the kernel sources from ./NVIDIA-Linux_x86_64-295.20/kernel/ rather than from ./NVIDIA-Linux_x86_64-295.20/usr/src/nv. This is as uniden says above.

2) I didn't have a Makefile in that directory, so a simple `make` doesn't work. Instead, there are three alternatives: makefile, Makefile.kbuild and Makefile.nvidia
    So I added a PRE_BUILD command to dkms.conf:-
PRE_BUILD="make -f makefile"

This pre-build step creates a sym-link from Makefile to Makefile.kbuild, allowing the normal make command to work. I'm updating to the latest kernel now... If this works, it'll be the first time in ages(!) I've ever rebooted cleanly after upgrading the kernel. Fingers crossed!

---

