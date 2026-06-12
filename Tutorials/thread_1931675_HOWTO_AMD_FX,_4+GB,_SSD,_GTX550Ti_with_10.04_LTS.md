---
title: "HOWTO: AMD FX, 4+GB, SSD, GTX550Ti with 10.04 LTS"
date: 2012-02-25
forum: Tutorials
---

### Post by LinuxSailor on 2012-02-25
**Introduction**

Ubuntu 10.10 64-bit and onward have issues with newer AMD FX processors and motherboard combinations (FX-4100, 6100, 8120, 8150) that prevent them from recognizing more than 4GB of RAM.  This is due to a kernel issue that exists in versions beyond the 2.6.32 version that ships with 64-bit 10.04 LTS such as on 10.10 or 11.x.  

This issue is reported in your boot logs when the [FONT=Courier New]dmesg[/FONT] command is run.  Here is an example:

```

[    0.000000] e820 update range: 00000000cfe00000 - 000000042f000000 (usable) ==> (reserved)
[    0.000000] WARNING: BIOS bug: CPU MTRRs don't cover all of memory, losing 13040MB of RAM.
[    0.000000] ------------[ cut here ]------------
[    0.000000] WARNING: at /home/kernel-ppa/mainline/build/arch/x86/kernel/cpu/mtrr/cleanup.c:1121 mtrr_trim_uncached_memory+0x343/0x350()
[    0.000000] Hardware name: GA-970A-UD3
[    0.000000] Modules linked in:
[    0.000000] Pid: 0, comm: swapper Not tainted 2.6.33-02063302-generic #02063302
[    0.000000] Call Trace:
[    0.000000]  [<ffffffff81ad4423>] ? mtrr_trim_uncached_memory+0x343/0x350
[    0.000000]  [<ffffffff8106073c>] warn_slowpath_common+0x8c/0xc0
[    0.000000]  [<ffffffff81060784>] warn_slowpath_null+0x14/0x20
[    0.000000]  [<ffffffff81ad4423>] mtrr_trim_uncached_memory+0x343/0x350
[    0.000000]  [<ffffffff81ac7140>] ? early_idt_handler+0x0/0x71
[    0.000000]  [<ffffffff81ac7140>] ? early_idt_handler+0x0/0x71
[    0.000000]  [<ffffffff81acd9b5>] setup_arch+0x435/0x6e0
[    0.000000]  [<ffffffff81ac7cd9>] start_kernel+0xa9/0x390
[    0.000000]  [<ffffffff81ac7140>] ? early_idt_handler+0x0/0x71
[    0.000000]  [<ffffffff81ac7325>] x86_64_start_reservations+0x65/0x90
[    0.000000]  [<ffffffff81ac742d>] x86_64_start_kernel+0xbd/0xe0
[    0.000000] ---[ end trace a7919e7f17c0a725 ]---
[    0.000000] update e820 for mtrr

```The [FONT=Courier New]WARNING: BIOS bug: CPU MTRRs don't cover all of memory, losing 13040MB of RAM[/FONT] line is the indicator your hardware has a problem with Ubuntu and will not work correctly on numerous releases.

**Target Audience**

This HOWTO is targeted at users looking to do AMD FX 64-bit installs where 10.10 and beyond exhibit this memory issue on their particular hardware combination and/or they want to use Solid State Drives (SSDs) as the primary boot/OS drive.  SSD usage is not optimal on 10.04 LTS and below due to lack of TRIM support that extends the life of SSDs and 10.10 will exhibit the memory hole.  This HOWTO allows these two worlds to come together.

The steps in this HOWTO will assist you if you have one or more the following circumstances:

[LIST]
[*]You want to install to an SSD as a primary OS/boot drive and want it optimized on 10.04 LTS
[*]You have more than 4GB RAM on 10.10 and your system is reporting only 3.2 GiB
[*]You have a newer generation nVidia graphics board that isn't supported fully in graphics mode (10.10 and beyond).
[/LIST]
**Hardware Configuration**

This HOWTO was derived from my efforts to get Ubuntu 10.x up and running on the following hardware combination:

[LIST]
[*]AMD FX-8120 8-core processor
[*]Gigabyte GA-970A-UD3 motherboard
[*]16GB DDR3-1333 RAM
[*]OCZ Agility 3 120GB SSD w/SATA 6GBs interface
[*]eVGA nVidia GTX550Ti 1GB graphics board
[*]LG 22x DVD Burner
[/LIST]
Your mileage may vary but if you encounter memory issues and/or want to support SSDs on a 10.04 LTS installation, these steps should hopefully assist you.  

This hardware build was targeted as a development, video processing and moderate gaming workstation for those who are interested.

[SIZE=3]**Steps**[/SIZE]

**0) Note**

Many of the steps in this HOWTO use the [FONT=Courier New]sudo[/FONT] command.  You will be prompted for your password.  This HOWTO assumes for the sake of brevity you will enter your user password whenever prompted.

[B]1) Install Ubuntu 10.x using your favorite medium.  
[/B]
For this HOWTO, a CD with the 10.04.4 LTS ISO image was used from [**http://www.ubuntu.com/download/ubuntu/download**]("http://www.ubuntu.com/download/ubuntu/download").  Upon boot, you will see the proper amount of memory in your system via the System Monitor application (under System menu > System Monitor).  

***Advanced: If Installing to an SSD***

If you are installing to an SSD, delete the swap partition the default installer creates or select the "Advanced" partitioning option.  Click "Add' in the dialog and let the new partition take up the entire disk.  Check "Format", make your mount point '/' and make sure the filesystem type is set to 'Ext4'.  The 'Ext4' filesystem is the only one that is viable for SSDs in default Ubuntu installs.

Allow the installation to complete after the partitioning and reboot into your new system.  It will be very fast and the graphics mode comes up normally on 10.04 LTS but although you will have your full amount of memory, the SSD is not going to be used and managed optimally and you lack hardware acceleration on the nVidia graphics card.

**2) Upgrade the 2.6.32 kernel to the latest backport from Oneiric Ocelot (11.10)**

Perform this step **only** if you have an SSD **and** have more than 4GB RAM.

The solution to getting more than 4GB to be visible is to upgrade the Linux kernel to a version that fixes the CPU MTRR error reported by ```
dmesg
``` on boot and one that supports TRIM for the SSD.  This support begins with 2.6.35 of the Linux kernel.  

The solution is to upgrade to the later 3.0.0 kernel from Ubuntu 11.10 and backport it to your version of Ubuntu.  This particular version of the kernel does not exhibit the memory problem of the intermediate kernels that ship with 10.10 onward.

To upgrade your kernel, open a Terminal window from the Accessories under the Applications menu and issue the following command:

[FONT=Courier New]sudo apt-get install linux-image-generic-lts-backport-oneiric linux-headers-generic-lts-backport-oneiric
[/FONT]
After some busy work, your new kernel will be installed.  This will restore your full amount of memory.  However, the newer kernel has issues with the (currently) default *nouveau* graphics driver. If you reboot now, you will wind up in text mode rather than your comfortable graphics mode.

To rectify this, you need to modify your boot configuration.  In your Terminal window, perform the following steps:

[LIST=1]
[*]Type [FONT=Courier New]cd /etc/default[/FONT] and press Enter.
[*]Type [FONT=Courier New]sudo nano grub[/FONT] and press Enter.
[*]Find the line [FONT=Courier New]GRUB_HIDDEN_TIMEOUT=0[/FONT] and put a # in front of it.  This comments it out and will cause your boot menu to appear on startup.  This is always a useful thing to do whenever you add multiple kernels to your OS.  The line will now look like this: [FONT=Courier New]#GRUB_HIDDEN_TIMEOUT=0[/FONT].
[*]Find the line [FONT=Courier New]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/FONT] and change it to [FONT=Courier New]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"[/FONT].  The [FONT=Courier New]nomodeset[/FONT] parameter changes the behavior of the graphics driver and allows the graphics mode to come up properly on the new kernel.
[*]Press Ctrl+O to save your changes and Ctrl+X to exit.
[*]Type [FONT=Courier New]sudo update-grub[/FONT] to update the boot configuration.
[*]Close the terminal and restart your computer.
[*]Select the 'Linux 3.0.0 generic' entry from your boot menu.
[/LIST]
If all goes well, your machine will start on the SSD with the graphics mode. Log in to your user account and open a Terminal window again.  Type [FONT=Courier New]uname -a[/FONT] and your should now be able to verify your are on the 3.0.0 kernel similar to the following:

[FONT=Courier New]Linux artemis 3.0.0-15-generic #26~lucid1-Ubuntu SMP Wed Jan 25 15:37:10 UTC 2012 x86_64 GNU/Linux[/FONT]

Open the System Monitor and you should also see your full amount of memory installed.

Congratulations, you're over the first major hurdle!  You've gotten around the AMD memory issue and installed a kernel that will properly support your SSD.

The next steps will allow you to optimize your SSD configuration and enable accelerated graphics.

**3) Optimize configuration for your SSD**

This step modifies your system configuration to work best with your SSD.  Most importantly, it adds TRIM support the OS which will help dramatically increase the lifespan of the SSD.

Open a Terminal window from the Applications Accessories men and do the following:

Type [FONT=Courier New]cd /etc[/FONT] and press Enter.
Type [FONT=Courier New]sudo nano fstab[/FONT] to open the filesystem configuration file.

Find the entry that has the [FONT=Courier New]/ ext4[/FONT] in it.  This will typically indicate your primary boot drive.  You will add the discard,noatime,nodiratime options to your SSD partition.  The disable option enables SSD TRIM support and the noatime,nodiratime options minimize writes to the drive.

You will add these entries before the errors=remount-ro 0 1 section.  So your line will go from something like this:

[FONT=Courier New]# / was on /dev/sda1 during installation
UUID=c947ee9c-cef4-4ef1-985c-e981cf69fa97 / ext4 errors=remount-ro 0 1[/FONT]

to something like this:

[FONT=Courier New]# / was on /dev/sda1 during installation
UUID=c947ee9c-cef4-4ef1-985c-e981cf69fa97 / ext4 discard,noatime,nodiratime,errors=remount-ro 0 1[/FONT]

Another optimization you want to make at this time is add the following line to the bottom of the file:

[FONT=Courier New]tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0[/FONT]

This line will enable RAM cache support of temporary files and prevent them from being written to the SSD.  This increases speed on your system and extends the life of the SSD.  Only do this if you have more than 4GB of RAM.

Press Ctrl+O and Ctrl+X to save your changes and then reboot your computer.  It will start up normally and now TRIM support will be properly enabled on your system.

**Advanced:** You can also perform the additional steps such as updating your scheduler and configuring Firefox for RAM caching found at [http://www.ab9il.net/linux/solid-state-drives1.html](http://www.ab9il.net/linux/solid-state-drives1.html).  The basic steps presented above, however, should always be done on any Linux system using an SSD as a primary drive.

**4) Enable proprietary accelerated graphics for nVidia card**

With an updated kernel and optimizations completed for your SSD, the last step that you need to perform is to get the latest nVidia driver for your graphics card.  10.x Ubuntu systems with newer nVidia graphics cards such as the GTX550Ti aren't detected and will not offer you the option of installing the proprietary drivers.

This step is necessary to override the internal nouveau graphics driver and ensure you get 3D acceleration along with the ability to configure graphics settings via the NVIDIA X Server Settings application.

To install the latest nVidia binary drivers, open a Terminal windows from Application Accessories and perform the following commands in the order stated (courtesy of [http://mygeekopinions.blogspot.com/2011/06/how-to-install-nvidia-2750907-driver-in.html]("http://ubuntuforums.org/%28courtesy%20of%20http://mygeekopinions.blogspot.com/2011/06/how-to-install-nvidia-2750907-driver-in.html%29")):

```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
sudo nvidia-xconfig

```The last command will write a new [FONT=Courier New]xorg.conf[/FONT] file to [FONT=Courier New]/etc/X11[/FONT].  Restart your computer and the nVidia binary drivers will now be in effect and you'll be able to run the nVidia X Server Settings from the System menu to change resolution, monitor the card and configure graphics settings.

** Conclusion**

Congratulations!  You have successfully updated and modified your system to allow you to run the latest greatest AMD and nVidia hardware with the 10.04 LTS release of Ubuntu.  For those that prefer the older Gnome interface over Unity or want to stay on their current version of Ubuntu with newer hardware, this will hopefully assist you.

**References**

The following links were used to help assemble these instructions that allows you to arrive at a complete system.

[http://mygeekopinions.blogspot.com/2011/06/how-to-install-nvidia-2750907-driver-in.html](http://mygeekopinions.blogspot.com/2011/06/how-to-install-nvidia-2750907-driver-in.html)
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
[http://handbrake.fr/](http://handbrake.fr/)
[https://launchpad.net/~stebbins/+archive/handbrake-releases]("https://launchpad.net/%7Estebbins/+archive/handbrake-releases")
[http://www.ab9il.net/linux/solid-state-drives1.html](http://www.ab9il.net/linux/solid-state-drives1.html)

---

### Post by Hitman_Forhire on 2012-03-21
Excellent guide, I have just built a new rig myself:

AMD 8150 8-Core Black Edition
Same Series board as you but with the 990FX chipset...
EVGA 550Ti
16GB Corsaire 

..I guess I was lucky because once I fired up 11.10 it booted perfectly but failed to load the GUI. I then simply used the 64-bit alternate installer disk to do a fresh install on my drive and Everything was great on my first bootup. I'm glad to see I wasn't the only one with a hiccup on this hardware.

I run Folding@Home, Heat is my enemy now, 2 minutes into folding I hit 60C on my proc so I'm still hunting a cheap solution for fix that. Artic Silver, and removing the lid off of the rackmount case didn't change a thing

---

### Post by LinuxSailor on 2012-03-25
60C for this processor under load near the top but not bad.  61C is the recommend top temperature for the chip.  If you're on the stock cooler, that's about as good as you're going to get.

My processor is on a closed liquid loop, an Antec Kuhler 620.  I have three machines on this system and it works great for the price.  If you have room for a 120mm with about 2 inches of clearance between the back of the case and any motherboard features (like a chipset heatsink), it mounts neatly inside.

Matt

---

### Post by nothingspecial on 2012-03-26
*Thread moved to **Tutorials & Tips**.*

---

### Post by WotWhere on 2012-06-02
Hi,

Went through hell trying to install Ubuntu 12.04 on a  new Rig:confused:

AMD FX- 8120
MSI 990FXA GD65
Gigabyte Radeon 7770OC 
corsair 8 GB
WD 500 Gb

Other : Mobile broadband : reliance EVDO

Got the ISO and installed via dvd  32bit ubuntu( recommended)
Win7 was already installed and worked great. but I wanted Linux:P
am coming back after a long gap.. forgot some of the commands..

the system kept hanging on starting any app
only gedit seemed to work
Guessed it would be the drivers.. 
had read somewhere that AMD has stopped producing drivers at 890 Chipset
and wont be providing 990FX drivers for Linux..  
did a software update 
didnt help
went the Debian way using apt to update and installed a few packs
Unity Software updater kept saying system is uptodate
no sound

kept sending apport error messages.. all this time
the mobile Broadband worked wihout a hitch:)
had to keep  doing a hard reset as the system wud hang invariably

installed the fglrx drivers manually.. coz when I used System Setings->Addtional hardware (jockey) and enabled the FGLRX update it wud disable the FGLRX driver itself:confused:

no clue.. to what was happeninig.. and googling about the hardware.. no help came up

went to #ubuntu to ask quests there.. 
got one helpful answer after a lot of garbage
to try and update again..  I dont remember how i got around to it.. 
but I figured that should try to install the Sound drivers
doind that manually Fixed it.. atleast the system wasnt Hanging now

Now the Screen would show Garbled Pixels for maybe a milli second
again went to #kubuntu (this time.. .as was using kde at the time)
NO help! there either...:sad:

after a day of troubleshooting.. found on google that FSAA in catalyst needed to be disabled
so followed the instructions and checked xorg.conf
which did  not have a fglrx section

but the FGLRX was installed (using fglrxinfo)
on doing 
aticonfig --initial=check 
no flgrx Section

so did
configured xorg.conf with 
aticonfig --initial

And I think thats fixed it
:popcorn:

-----------------------------
All the above is a summary of the steps taken.... 
I am Happy that its working.. After 2 Weeks.. phew..

Wanted to share this with Ubuntu.. so that the next guy doesnt have to go thru the sam e.


Bye

---

### Post by WotWhere on 2012-06-05
Hi,

Well i  spoke too soon:mad:

FGLRX does not  behave like it should after taking all the steps mentiond above... the problem remains
Garbled Pixel images!  in firefox and everywhere Else

It happens all the time when I use the mouse scroll wheel

thinking of playing around with FSAA setings (0,2,4.. etc)

(I know ubuntu doesnt provide support for propreitory drivers)
any clues/hints anyone?
also is this the right thread for posting this?

):P

---

### Post by floortester on 2012-06-05
I have never been able to get decent resolution with Linux, I started with Suse 8 and have tried 4 other varieties and am now on Ubuntu 12.04. The downloaded upgrade from 11.1 left me with the lovely warning " Unable to complete installation, you have a unstable system" so I bought a copy of Ubuntu 12.04 and it installed very well. 

I have found that Nvidia supplies a video drive for my card, a basic Geforce 7600GS, version 295.53, the best I can get with the updated driver section is 295.40 with a maximum resolution of 1360x768 and a "laptop as the screen, version 295.49 has coloured shadows around text. I am using a new Dell with a maximum resolution of 1920x1200 and would like to get near to this - the splash screen says it is displaying in this mode. When using the card with Windows XP it would display at 1920x1080, I have not tried the card at 1920x1200.

When I try and install the Nvidia driver it tells me that I need to turn off the X display, this appears to be easier said than done. I have tried the solution above, editing grub and adding nomodeset to the quiet splash and commenting the hidden Terminal line but to no avail, it still boots into the X Display system.

I suppose I have four queries
If I manage to install the 295.53 software does it work at better resolutions?
If it does, how do I start in a terminal system to install it?
Is there a list of video cards that have drivers available? It would seem easier to replace the card with one that performs under Ubuntu than fight 
Does Linux have the capability to display at better resolutions, as I have only found it just acceptable for email, I certainly would not use it for graphics work or even word processing as the text quality and size is poor.

I hope this is the correct place for this query, 
Thanks in advance for your help

---

