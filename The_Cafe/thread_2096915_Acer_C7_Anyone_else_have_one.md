---
title: "Acer C7: Anyone else have one?"
date: 2012-12-21
forum: The Cafe
---

### Post by Warpnow on 2012-12-21
I picked an Acer C7 Chromebook knowing I could install ubuntu on it. Other than the firmware giving me a nasty message that I've disabled OS verification it works seemingly perfect so far. Haven't tested bluetooth or video out yet though. 

Essentially, for $199 you get:

-No Windows
-Dual Core Intel CPU that while not a speed demon, isn't a slouch.
-Webcam
-1366x768 resolution LCD, way better than the 1024x600 ones in netbooks before it.

To me it might be the perfect ubuntu laptop for the price. Anyone else picked one up?

Wondering if anyone's tried to put grub on it. Right now custom scripts boot into chrome or ubuntu per the developer of Chrubuntu's guide. Wondering if anyone knew why grub wasn't used.

Also wondering if anyone's found a better driver for the trackpad. A little frustrating when right clicking.

---

### Post by gomab2k4 on 2012-12-22
I have one. I use a Samsung ARM Chromebook while I am away from my Ubuntu laptop. I picked up the Acer to compare and to MAYBE upgrade it and add Ubuntu. For $200, it is a nice little device.

---

### Post by grahammechanical on 2012-12-22
>  Wondering if anyone knew why grub wasn't used

I have done very little research on this but might I offer a couple of guesses?

> Because Chromebooks use a special BIOS and bootloader that is distinct from the ones used in standard Windows laptops, you can't use them to boot just any operating system. 

> After entering developer mode, your Chromebook will boot to a scary screen telling you that OS verification has been disabled. 

Taken from here:

[http://arstechnica.com/gadgets/2012/12/how-to-install-ubuntu-on-acers-199-c7-chromebook/]("http://arstechnica.com/gadgets/2012/12/how-to-install-ubuntu-on-acers-199-c7-chromebook/")

"OS verification?" What is that? Anything like Secure Boot? At the moment Ubuntu 12.10 is the only Ubuntu version that can install on a machine with Secure Boot enabled. Perhaps, when the developer of ChrUbuntu moves on the 12.10 or when 12.04 is upgraded with a signed kernel that will load onto a Secure boot enabled machine then we might get Grub on the chrome book as well as Ubuntu.

Or does something else have to be done?

**Verified Boot**

[http://www.chromium.org/chromium-os/chromiumos-design-docs/verified-boot]("http://www.chromium.org/chromium-os/chromiumos-design-docs/verified-boot")

> This document describes the cryptographic primitives and building blocks used for implementing verified boot in the firmware. The document is primarily targeted at Google Chrome OS-based devices running Google-signed firmware and software. Chromium OS devices may use similar verified boot schemes with their own (non-Google-signed) chain of trust. We want to emphasize this does not prevent devices based on the open source Chromium OS project from having their own firmware. The goal here is to assure customers of Google Chrome OS devices that they are actually running Google Chrome OS. 

Sounds familiar? But more open.

Regards.

---

### Post by Shi Maebure on 2012-12-26
I also have one... and I forgot my password. So if someone knows how to activate Recovery Mode without the grub menu I'd greatly appreciate it.

---

### Post by KosakiHook on 2012-12-26
I've been very interested in the Chromebooks and loading Ubuntu on them.  I haven't tried either the Samsung or Acer.  If I were to get the Acer, I'd like to upgrade the HD to a SSD.

I'm sure there will be better and more exciting versions coming out in the next year.

---

### Post by spandexman on 2013-01-03
I am also an Acer C7 owner - bought this after doing a lot of research on Ubuntu (I am also a new Ubuntu user) and decided shortly after finding information on installing Chrubuntu onto it. Within a few hours of purchasing the C7 I installed Chrubuntu, following the directions from the second post in this thread, and voila' I'm now never using any other OS than linux. 

Also, this: 
> **Warpnow said:**
> 
Also wondering if anyone's found a better driver for the trackpad. A little frustrating when right clicking.

I am using a wireless USB mouse when I'm at my desk, but I'd prefer to not have to bring it with me whenever I leave. Unfortunately the track pad did work much better in Chrome OS - but that's hardly a reason to make me turn away from Chrubuntu.

---

### Post by AlphaLupi on 2013-01-05
I got a netbook when they first started coming out because I was very hard on my laptops; having to replace them every year or two. I thought that a small machine with an SSD would stand up to more punishment, and I was right!

So when my HP mini-110 died, I got an Acer C7 planning to upgrade it to an SSD and add some RAM (you can read how here: [http://normcf.net/~john/chromebook/Acer/acerC7ChromebookUpgrade.html](http://normcf.net/~john/chromebook/Acer/acerC7ChromebookUpgrade.html) ).

In fact I installed a 64GB SSD and 8GB DDR3 DIMM just yesterday and am still test driving things.

I'm using the Chrubuntu setup written by Jay Lee and it's pretty good for what I want: basic net access, some office/typing work/simple stuff like that.

It seems like a pretty good little machine as long as you remember you're not buying a desktop replacement.

The dual-boot environment is annoying though, I'm hoping in the future someone figures out a way to trick the OS verification system into thinking stock/near stock Ubuntu is legitimate.

Also, you get used to the trackpad faster than you might think.

---

### Post by jfaust97 on 2013-01-09
I've also installed CHrUbuntu and then promptly upgraded to 12.10
Last night I installed Cinnamon as well and it's much better than Unity IMHO.
The trackpad seems better since the Cinnamon install but that may be my imagination because that shouldn't have impacted it I don't think??

I plan to get an SSD and memory upgarde.

AlphaLupi... you've installed an SSD and then installed CHrUbuntu?
That install went okay without Chrome being installed on the SSD?
I wasn't sure if you needed the ChromeOS there for any reason?
Thanks!

---

### Post by AlphaLupi on 2013-01-11
I used the USB image restore program Chrome OS comes with, imageburner. You can access at chrome://imageburner . It's a lot like a Windows System Restore disk. You can enter recovery mode by hitting ESC+F3+power and then insert the USB stick you created with imageburner and it it puts stock Chrome OS onto the SSD almost like it was there in the first place. From there you can install Chrubuntu.

Be sure to get an SSD that fits thought! The HDD in the C7 is a little shorter than the standard 2.5" HDD. It stands about 7.5 mm I think. The SSD I got stands 9.51 mm. I had to remove all the rubber and silicon padding and it still pokes the case out a little.

---

### Post by Pierce Randall on 2013-01-13
> **jfaust97 said:**
> Last night I installed Cinnamon as well and it's much better than Unity IMHO.

I did this on my girlfriend's C7 as well. I wanted something that runs less ram than Unity. If there's one thing I learned from the C7, in fact, it's that I might like Ubuntu + Cinnamon more than Linux Mint (which I use on my laptop).

Personally, I gotta say, while I like the results of ChruBuntu (the gf really needed a way to run a fully featured word processor for school), I don't think the C7 is quite there as a mainly-Ubuntu machine. She seems to find herself using Chrome OS for normal use more than I think either of us thought that she would.

---

### Post by AlstonA on 2013-01-13
> **Warpnow said:**
> I picked an Acer C7 Chromebook knowing I could install ubuntu on it. Other than the firmware giving me a nasty message that I've disabled OS verification it works seemingly perfect so far. Haven't tested bluetooth or video out yet though. 

Essentially, for $199 you get:

-No Windows
-Dual Core Intel CPU that while not a speed demon, isn't a slouch.
-Webcam
-1366x768 resolution LCD, way better than the 1024x600 ones in netbooks before it.

To me it might be the perfect ubuntu laptop for the price. Anyone else picked one up?

Wondering if anyone's tried to put grub on it. Right now custom scripts boot into chrome or ubuntu per the developer of Chrubuntu's guide. Wondering if anyone knew why grub wasn't used.

Also wondering if anyone's found a better driver for the trackpad. A little frustrating when right clicking.

I just installed this yesterday on my Chromebook and the only problem I seem to be having is that is crashes and displays an out of memory message. I may have to format and re-install it again to get it to work.

---

### Post by Joespower on 2013-01-18
I have the C7 and I've installed chrUbuntu, but I noticed the chrUbuntu install doesn't create a swap partition.  I'm sure that would help out with the "out of memory" errors.  My interest in creating one is to see if it will allow me to turn on hibernation.  Has anyone attempted this yet?  Is it difficult (I'm pretty green)...

---

### Post by AlphaLupi on 2013-02-08
I should update from what I said earlier: 

DO NOT install an SSD in an Acer C7 Chromebook. It turns out that the C7 BIOS does not support SSD's at all. 
Mine kept locking up for no apparent reason. I thought it was a flaw in the Chrubuntu script or something I'd done to it or a problem with the SSD itself. But after talking to the manufacturer, I figured out that the SSD was fine and it was the C7 itself that was causing the problem.
I finally fixed the issue by replacing it with another HDD and now everything's fine.

Sorry for any confusion I caused.

---

### Post by rickyrockrat on 2013-02-10
How do you right-click, anybody? ED: two finger click @ bottom middle. How do you middle-button press??

 I'm running a C7 stock with xfce4, and it's quite snappy.  A SSD will run, but you have to have the right specifications for it.  Check the chromeos developer forums.

A swap can be added, but it will require re-partitioning the drive.  When I figure it out, I'll let you know. You will have to use gdisk, since the drive is GPT.

Anybody have a USB mouse working? It seems that someone somewhere broke USB mouse detection. I have a 3.0.4 kernel that the mouse works fine, but 3.4.0 doesn't. It sees it, but fails to detect it as a mouse.

---

### Post by catco_designs on 2013-02-21
I have one.  The Acer Chromebook C7 the standard $199 model

I installed the Chrubuntu 12.04 build and I love it.

IMHO Chrome OS is very limited. 

The only issues I have are 
Trackpad (right/left click) function ;works well with external mouse
OS verification screen requires Ctrl+d to bypass or wait for 30+ seconds to boot

What I do like
several full size usb ports
vga port and ethernet port


for the money not a bad netbook

---

### Post by Sinsinnati on 2013-03-26
I just invested in the C7. Pretty good buy. But there are some bugs to be worked out and that makes it a little more advanced than other machines I've gotten used to over the years. Thankfully, there's always an answer. Right now I'm getting weird messages about repositories when I go to update. So I just unquoted all of the repos, updated and it seems to be working fine.

---

### Post by thetechguy911 on 2013-03-31
Hello Warpnow. I have also picked up a C7 and it runs chrubuntu great. 
By the way Alphalupi, if you want to wipe your ubuntu partition, turn os verification on, then, plug a 4gb of more flash drive into your computer, then type this in the ominibox
[I]chrome://imageburner
[/I]and follow the instructions.
After it tells you that you can remove the flash drive, press esc and F3 together while pressing the power button.
after your device has been restored, reinstall chrubuntu

---

### Post by rickyrockrat on 2013-04-17
So I've found some interesting things out. First, NFS is not built into the kernel, and many of the drivers are not built, even as modules, so I built my own kernel. Here's how I did it. I've attached the files that I used, except I changed a few things in linux-build.txt   I built all of the code in my $HOME/src directory.
BACK UP before you start:
I backed up /boot and /lib/modules/3.4.0 like so:
cd /
sudo cp -a boot boot.orig
cd lib/modules
sudo cp -a 3.4.0 3.4.0.orig
sudo dd if=/dev/sda6 of=/kernel.orig

You need the keys from the chromeos:
mkdir m
sudo mount -o ro /dev/sda3 m
sudo cp -a m/usr/share/vboot to /usr/share
sudo umount m

The git clone of the kernel is pulling the Linux kernel from GIT, and it's about 1.2G, so it will take some time to download.
If you want to keep the kernel pristine, at the level you did the git command (lndir -> apt-get install xutils-dev), do:
mkdir -p build/kernel
cd build/kernel
lndir ../../kernel
Then run all the commads from there: make oldconfig/make-kpkg kernel_image kernel_headers
In linux-build.txt, Ignore the patch of the base.config, and instead copy the chromiuos-3.4.0.config to .config in the kernel build directory, then do:

make oldconfig

Ignore the part where it does the vbutil_kernel --verify, and use the kernel-cmd.txt file in place of the config-$tstamp.txt

The above config and kernel command line fix drivers not loading, and of course give you a ton more input drivers (for mice and such). This was why one of my USB mice would not work - no driver built. I also added NTFS file systems and other basic optional drivers.

If for some reason the vbuil tools don't work as copied, do this:
sudo apt-get install libyaml-dev liblz-dev liblzma-dev lzma-dev uuid-dev libssl-dev libtspi-dev 
git clone [http://git.chromium.org/chromiumos/platform/vboot_reference.git](http://git.chromium.org/chromiumos/platform/vboot_reference.git)
cd vboot_reference
make
sudo make install
Cheers!

---

### Post by TBABill on 2013-04-27
I have had a Chromebook C7 for months now but ChromeOS is just too limited in abilities for times when I need to work on large spreadsheets or word documents. I thought I could get by with Google Docs, or even Skydrive, but we have some business spreadsheets that just bring it to a slow crawl. I installed 12.04 and it was ok, but Unity was still a large drain. I installed the PPA for cinnamon and I feel like I'm back in Mint heaven again. The desktop is fast and everything works great.

I also installed the Ubuntu Tweak PPA so I could get natural scrolling back. After so long on a Macbook Pro, scrolling in Linux feels so backwards. For some reason I can manage it just fine on a Windows mouse wheel, but in two finger scrolling I feel like I have to retrain my brain. Then I'd grab a Macbook again and feel lost again. Natural scrolling took care of it and Ubuntu Tweak has so much to offer besides just that.

Anyway, loving my C7 with Ubuntu. I'm sure 13.04 is much nicer since it's Unity version is less resource hungry, but I'm not confident enough with Ubuntu on a Chromebook to be willing to attempt 2 upgrades. On a normal machine I would, but it's a lot more work to get it on a Chromebook and working properly. I hate upgrades anyway and prefer fresh installs....look at me just talking myself out of changing anything!

---

### Post by PhoHammer on 2013-04-28
It's fanless right? I would get it just for that "feature". There's nothing better than not hearing that constant whirrrrr of a fan or HDD.

---

### Post by aysiu on 2013-04-29
> **PhoHammer said:**
> It's fanless right? I would get it just for that "feature". There's nothing better than not hearing that constant whirrrrr of a fan or HDD. No, the C7 has a fan. The Samsung Chromebook and the Pixel are fanless.

---

### Post by oldrocker99 on 2013-04-30
I have been having a great deal of fun with ChrUbuntu, using razor-qt as a DE, and using a USB mouse, BTW, which eliminated the "how do you middle-click with the trackpad?" question.

Oh, yes, I'm upgrading RAM. Soon. SSD? Maybe; I like the HD capacity I have.

---

### Post by gecko2 on 2013-08-25
> **rickyrockrat said:**
> So I've found some interesting things out. First, NFS is not built into the kernel, and many of the drivers are not built, even as modules, so I built my own kernel. Here's how I did it. I've attached the files that I used, except I changed a few things in linux-build.txt   I built all of the code in my $HOME/src directory.
BACK UP before you start:
I backed up /boot and /lib/modules/3.4.0 like so:
cd /
sudo cp -a boot boot.orig
cd lib/modules
sudo cp -a 3.4.0 3.4.0.orig
sudo dd if=/dev/sda6 of=/kernel.orig

You need the keys from the chromeos:
mkdir m
sudo mount -o ro /dev/sda3 m
sudo cp -a m/usr/share/vboot to /usr/share
sudo umount m

The git clone of the kernel is pulling the Linux kernel from GIT, and it's about 1.2G, so it will take some time to download.
If you want to keep the kernel pristine, at the level you did the git command (lndir -> apt-get install xutils-dev), do:
mkdir -p build/kernel
cd build/kernel
lndir ../../kernel
Then run all the commads from there: make oldconfig/make-kpkg kernel_image kernel_headers
In linux-build.txt, Ignore the patch of the base.config, and instead copy the chromiuos-3.4.0.config to .config in the kernel build directory, then do:

make oldconfig

Ignore the part where it does the vbutil_kernel --verify, and use the kernel-cmd.txt file in place of the config-$tstamp.txt

The above config and kernel command line fix drivers not loading, and of course give you a ton more input drivers (for mice and such). This was why one of my USB mice would not work - no driver built. I also added NTFS file systems and other basic optional drivers.

If for some reason the vbuil tools don't work as copied, do this:
sudo apt-get install libyaml-dev liblz-dev liblzma-dev lzma-dev uuid-dev libssl-dev libtspi-dev 
git clone [http://git.chromium.org/chromiumos/platform/vboot_reference.git](http://git.chromium.org/chromiumos/platform/vboot_reference.git)
cd vboot_reference
make
sudo make install
Cheers!

The trackpad works a lot better under Chrome OS... Will your kernel improve the trackpad under ubuntu?

I don't really understand what to do after "sudo umount m"

Sorry, I am new to ubuntu.

---

### Post by rickyrockrat on 2013-08-25
Gecko2,
Make sure you read all provided info. If you don't, you will find the open source community will quickly loose patience with you. RTFM is often said, which means Read The Fine Manual (Fine was another word, but I don't use it). 

There are three attached files. Download & read them. In linux-build.txt, there is a section that shows how to git clone the kernel.  linux-build.txt can be run by doing:
bash linux-build.txt
That command tells the shell to run the file as a shell script, executing all the instructions in there as thought you had typed them yourself.

But make sure you understand what it is doing! Some people will tell you to run commands that are malicious, and even if they are not malicious, there could be a mistake that wipes your system.

If you don't trust linux-build.txt to be correct, just cut & paste sections of it into some file, then do the bash some-file. Alternatively, you can make your script executable with:
chmod 755 some-file
then run it
./some-file.
If you really don't trust it, run the commands by typing (or cutting & pasting each line) them one at a time. REALLY examine commands like mv, rm, fdisk, mk* (mkfs, mke2fs, etc) especially when run as root.
One more thing, don't use root to run commands unless you HAVE to. I always configure and make softwre as a normal user. 

A command like chown -R user:user path/to/some/directory will change that dirctory and all files under it (-R) so they are owned and in the same group as the user named 'user'. Only do this to directories that have software source. Doing that to directories on the root file system can do Bad Things.

---

### Post by Donna_Harris on 2013-09-09
Hey rickyrockcat, and friends --

I've bought myself a C7 with the intention of using it as a thin client to remote into work, etc.  I need PPTP to connect to the VPN at the office, but all the necessary modules are not part of the kernel.  So I've been trying to piece things together in an attempt to configure/recompile the kernel to add this support.  Your post is the closest thing I've found to what I've been hoping to accomplish, so thank you for that glimmer of hope.

I *think* I have the config file altered to include all of the PPTP related modules.  Things seemed to be going fairly smoothly tonight, until I get to [FONT=courier new]make-kpkg kernel_image kernel_headers[/FONT]

I run as "sudo" and get the output included below, with the errors in bold at the end.... Everything looks like it's going fine (to me, anyway) and then gcc complains about a parameter and it quits.  Any suggestions on what's happening or for how to troubleshoot this further?

Thanks!!


```
exec make kpkg_version=12.036+nmu3 -f /usr/share/kernel-package/ruleset/minimal.mk debian
====== making target debian/stamp/conf/minimal_debian [new prereqs: ]======
This is kernel package version 12.036+nmu3.
test -d debian             || mkdir debian
test ! -e stamp-building || rm -f stamp-building
install -p -m 755 /usr/share/kernel-package/rules debian/rules
for file in ChangeLog  Control  Control.bin86 config templates.in rules; do                                      \
            cp -f  /usr/share/kernel-package/$file ./debian/;                               \
        done
for dir  in Config docs examples ruleset scripts pkg po;  do                                      \
          cp -af /usr/share/kernel-package/$dir  ./debian/;                                 \
        done
test -f debian/control || sed         -e 's/=V/3.4.0/g'  \
                -e 's/=D/3.4.0-10.00.Custom/g'         -e 's/=A/i386/g'  \
        -e 's/=SA//g'  \
        -e 's/=I//g'                    \
        -e 's/=CV/3.4/g'                \
        -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g'                \
        -e 's/=ST/linux/g'      -e 's/=B/i386/g'    \
                  /usr/share/kernel-package/Control > debian/control
test -f debian/changelog ||  sed -e 's/=V/3.4.0/g'       \
            -e 's/=D/3.4.0-10.00.Custom/g'        -e 's/=A/i386/g'       \
            -e 's/=ST/linux/g'     -e 's/=B/i386/g'         \
            -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g'                            \
             /usr/share/kernel-package/changelog > debian/changelog
chmod 0644 debian/control debian/changelog
test -d ./debian/stamp || mkdir debian/stamp 
make -f debian/rules debian/stamp/conf/kernel-conf
make[1]: Entering directory `/home/user/build/kernel'
====== making target debian/stamp/conf/kernel-conf [new prereqs: ]======
make    ARCH=i386 \
                    oldconfig;
make[2]: Entering directory `/home/user/build/kernel'
scripts/kconfig/conf --oldconfig Kconfig
#
# configuration written to .config
#
make[2]: Leaving directory `/home/user/build/kernel'
make    ARCH=i386 prepare
make[2]: Entering directory `/home/user/build/kernel'
scripts/kconfig/conf --silentoldconfig Kconfig
make[2]: Leaving directory `/home/user/build/kernel'
make[2]: Entering directory `/home/user/build/kernel'
make[3]: Nothing to be done for `all'.
make[3]: Nothing to be done for `relocs'.
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  CC      kernel/bounds.s
[B]gcc: error: unrecognized command line option '-fstack-protector-strong'
make[3]: *** [kernel/bounds.s] Error 1
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/home/user/build/kernel'
make[1]: *** [debian/stamp/conf/kernel-conf] Error 2
make[1]: Leaving directory `/home/user/build/kernel'
make: *** [debian/stamp/conf/minimal_debian] Error 2
Failed to create a ./debian directory:  at /usr/bin/make-kpkg line 984.[/B]
```

---

### Post by rickyrockrat on 2013-09-09
Make sure gcc is up to date.  Do apt-cache search gcc |grep gcc to get the correct name for apt. In fact, perhaps just do:
sudo apt-get update
sudo apt-get upgrade
should bring your system up to date.
It acts like gcc is building for the wrong target or the config/gcc is mis-matched.
Google (in this case) is sorta your friend (actually, they are the ones that messed it up in the first place, not to mention that nasty NSA thing):
googling : unrecognized command line option "-fstack-protector-strong"
returns:
[I]So, depending on your gcc and when you get the kernel source you may need to edit /usr/src/kernel/arch/x86 Makfile
Line 78 change "stackp-y := -fstack-protector-strong" to stackp-y := -fstack-protector-all
apparently google added the strong option to their build of gcc and you may get an error saying this is not defined[/I]
from here:
[https://groups.google.com/forum/#!msg/chromebook-central/PPQFpC7mYzk/WUIALBzD4R0J](https://groups.google.com/forum/#!msg/chromebook-central/PPQFpC7mYzk/WUIALBzD4R0J)
references:
[http://ml.reddit.com/r/chrubuntu/comments/1e7gjs/i_need_help_compiling_kernel_modules_eg/](http://ml.reddit.com/r/chrubuntu/comments/1e7gjs/i_need_help_compiling_kernel_modules_eg/)
Cheers

---

