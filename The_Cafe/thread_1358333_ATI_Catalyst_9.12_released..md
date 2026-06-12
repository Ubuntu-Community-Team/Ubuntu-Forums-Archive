---
title: "ATI Catalyst 9.12 released."
date: 2009-12-18
forum: The Cafe
---

### Post by rajeev1204 on 2009-12-18
Here you go . [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)

More control center gui options in linux now.

---

### Post by Excedio on 2009-12-18
If you're as curious as I am
 
> 
[LEFT][FONT=Verdana][FONT=Verdana][SIZE=2]removed incorrect quote.[/SIZE][/FONT][/FONT][/LEFT]


---

### Post by Grenage on 2009-12-18
**get's his ATI card out for another test session**

---

### Post by rajeev1204 on 2009-12-18
> **Excedio said:**
> If you're as curious as I am

YOu have posted for the older 9.11 release.

Here is the release notes for the new **9.12** release

>         The latest version of the ATI CatalystTM Linux software suite is designed to support the
        following Linux distributions:
            Red Hat Enterprise Linux suite
            Novell/SuSE product suite
            **_Ubuntu_**

                  Note: The ATI CatalystTM Linux software suite may install on a
                  number of other Linux distributions. Refer to the Package Generation
                  installation instructions for more information.
                  Note: AMD has contributed packaging scripts to allow creation of
                  other packages, but does not necessarily test, verify or warrant the
                  reliability. Currently Red Hat Enterprise Linux suite and
                  Novell/SuSE product suite are supported Linux distributions.

System Requirements
        Before attempting to install the ATI CatalystTM Linux software suite, the following
        software must be installed:
            XOrg 6.8, 6.9, 7.0, 7.1, 7.2, 7.3 or 7.4
            Linux kernel 2.6 or above
            glibc version 2.2 or 2.3
            POSIX Shared Memory (/dev/shm) support is required for 3D applications
        The ATI CatalystTM Linux software suite no longer provides precompiled Kernel
        Modules; all installations require GCC compiler and kernel-headers or kernel-source in
        order to enable 2D and 3D acceleration.
        For best performance and ease of use, ATI recommends the following:
            Kernel module build environment
            o Kernel source code include either the Kernel Source or Kernel Headers packages
            The RPM utility should be installed and configured correctly on your system, if you
            intend to install via RPM packages
        The following packages must be installed in order for the CatalystTM Linux driver to
        install and work properly:
            XFree86-Mesa-libGL
            libstdc++
            libgcc
            XFree86-libs
            fontconfig
            freetype
            zlib
                                                                                                4
                                  ATI Proprietary Linux Release Notes
              gcc

New Features
          This section provides information on new features found in this release of the RadeonTM
          Display Driver. These include the following:
              Support for New Linux Operating Systems
              ATI Catalyst Control Center Linux Edition: Displays pages: user interface
              enhancements
    Support for New Linux Operating Systems
          This release of ATI CatalystTM Linux introduces support for the following new operating
          system:
              RedFlag DT6.0 SP3
              SLED and SLES 10SP3
    ATI Catalyst Control Center Linux Edition: Displays pages: user
    interface enhancements
          This release of ATI CatalystTM Linux introduces support for a number of new display
          features found in the ATI Catalyst Control Center Linux Edition, highlights include:
              CRT/VGA settings
                  o New Size and Position page
                  o New HDTV page
              TV settings
                  o New option for &#8220;Automatic setting for Size and Position adjustment&#8221;
                  o New image quality settings: &#8220;flicker removal&#8221; and &#8220;S-Video/Composite
                       sharpness&#8221;
              Component Video settings
                  o New Scaling Options page &#8211; new Overscan / Underscan controls
                  o New custom mode support for 576 modes
              Support for display projectors
                  o Enables quick display configuration of display projectors
Resolved Issues
          The following section provides a brief description of resolved issues with the latest
          version of the ATI CatalystTM Linux software suite. These include:
              Desktop resolution changes through Catalyst Control Center are now applied on 
              restart of X 
              Catalyst Control Center: Display is now mapped to the correct desktop/screen after 
              X restarts 
                                                                                                5
                                  ATI Proprietary Linux Release Notes
            In dual&#8208;head mode, performing a XRandR command (rotation or screen resolution 
            change) on screen 1 no longer cause both screens to display corruption 
Known Issues
        The following section provides a brief description of known issues associated with the
        latest version of ATI CatalystTM Linux software suite. These issues include:
            Catalyst Control Center: disabling one of the displays on a multi&#8208;monitor 
            configuration, may become enabled on Xserver restart 
            On some configurations the Operating System may become unresponsive when 
            switching between virtual terminals 
            Catalyst Control Center:  on some systems configurations setting a customized 
            modes may not be applied  
            Some Open GL applications may show corruption when running with CrossFire 
            enabled and Anti&#8208;Alias 16x 
            Some systems may become unresponsive during video play back with certain Dual 
            Head configurations on Ubuntu 9.04 x86 64bit 
            Catalyst Control Center:  on some systems setting a customized modes may not be 
            applied  
            Catalyst Control Center: Red Hat Enterprise Linux 5.4 &#8208; 32 system may stop 
            responding after selecting "Detect Displays button" and hot&#8208;plugging a HDMI display 
            CrossFire may fail to be enabled on some  Ubuntu 9.10 configurations with   ATI 
            Radeon HD 5900 Series adapter  
            X may stop responding after executing multiple Xserver generations with Xinerama 
            enabled on Ubunut 9.10 
             Catalyst Control Center: Super Anti&#8208;Aliasing (16x) mode may not be available on 
            some display adapters when Crossfire is enabled 
            Catalyst Control Center: some system configurations may stop responding when 
            display scalinng has been enebled 
            In some Dual&#8208;Head mode configurations a segmentation fault may occur when X is 
            stopped  
                                                                                               6
                                

ATI Proprietary Linux Release Notes
[Ubuntu 9.04] Some video adapters may stop video output signals when monitor 
has been powered off and powerd on again 
     Note: On Novell's openSUSE, SLED and SLES operating systems
     running &#8220;sax2&#8221; or &#8220;sax2 -r&#8221; on the console overwrites the X.Org
     configuration file xorg.conf, reverting changes made by running
     &#8220;aticonfig --initial&#8221;. As a result subsequent X session may start up
     using the open source Radeon on X-Vesa graphics drivers instead of
     the proprietary ATI Linux Graphics Driver.
     Solution: Do not use Sax2 when the proprietary Linux Graphics
     Driver is installed. Instead configure all display parameters using the
     Catalyst Control Center--Linux Edition or the aticonfig command
     line interface.


As you can see from the notes, a lot many new features are now available from the GUI.

---

### Post by rajeev1204 on 2009-12-18
> **rajeev1204 said:**
> Here you go . [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)

More control center gui options in linux now.

Opengl 3.2 extensions added upto HD 2000 series.

---

### Post by Excedio on 2009-12-18
> **rajeev1204 said:**
> YOu have posted for the older 9.11 release.
 
Here is the release notes for the new **9.12** release
 
 
 
As you can see from the notes, a lot many new features are now available from the GUI.
 
 
Damn them for linking 9.11 release notes on the same page!! :-D

---

### Post by Ylon on 2009-12-18
Didn't notice.. it is really Ati driver about more than 80MiB?


You can get a whole Linux distro in that size! (two "damn small linux")

---

### Post by n0glu3 on 2009-12-18
New options?

---

### Post by rajeev1204 on 2009-12-18
> **Excedio said:**
> Damn them for linking 9.11 release notes on the same page!! :-D

yes i too noticed it later.They need to do some cleanup work.

Anyways, i have installed the new drivers but i dont see the changes in the GUI as they mentioned.

I do see opengl version as 3.2 now.

---

### Post by Excedio on 2009-12-18
Did you completely remove the old driver before installing the new one?

---

### Post by markbuntu on 2009-12-18
There is also a hotfix for the 9.12 driver. It fixes some problems with the 5xxx and 4xxx cards. 

[http://support.amd.com/us/kbarticles/Pages/ATICatalyst912Hotfix.aspx](http://support.amd.com/us/kbarticles/Pages/ATICatalyst912Hotfix.aspx)

---

### Post by handy on 2009-12-18
There some detailed info on this topic, posted here in the Arch forum:

[http://bbs.archlinux.org/viewtopic.php?pid=673866#p673866](http://bbs.archlinux.org/viewtopic.php?pid=673866#p673866)

& in following posts in that thread, as previously linked in post_190 of this thread:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

Unfortunately the patch hasn't made catalyst 9.12 compatible with xorg-server 1.7 yet. :(

---

### Post by Exodist on 2009-12-18
9.12.. ARGHH!!! I just installed 9.11 two hours ago!!! /goes back to AMD site!!

---

### Post by doorknob60 on 2009-12-18
No new Xorg support yet? No thanks...how long can it take them?

---

### Post by Nerd King on 2009-12-18
Just use the open drivers if you want up-to-date xorg support. They're actually pretty bloody awesome now.

---

### Post by handy on 2009-12-18
> **Nerd King said:**
> Just use the open drivers if you want up-to-date xorg support. They're actually pretty bloody awesome now.

I'll wait until the kernel .32 comes out of Arch [testing], which should be any day now, the kernel headers came out yesterday. :)

I'm really in no great rush, though it surely is going to be great to kiss catalyst goodbye forever. :guitar:

---

### Post by Nerd King on 2009-12-18
As I joked in another thread, I thought arch was supposed to be bleeding edge ;) Beaten by Ubuntu? Who'd have thought it?

---

### Post by PurposeOfReason on 2009-12-18
> **handy said:**
> I'll wait until the kernel .32 comes out of Arch [testing], which should be any day now, the kernel headers came out yesterday. :)

I'm really in no great rush, though it surely is going to be great to kiss catalyst goodbye forever. :guitar:
Say what you will, but unless the open drivers can backwards engineer eyefinity I want catalyst.

---

### Post by handy on 2009-12-18
> **Nerd King said:**
> As I joked in another thread, I thought arch was supposed to be bleeding edge ;) Beaten by Ubuntu? Who'd have thought it?

The kernel .32, was released, from memory on the 5-12-09, where it would have gone into the Arch [testing] repo', so as to be sure that it is safe to use as is, or if bugs were found to get them fixed upstream (usually).  

Many are using it with no troubles on Arch & other distros. The guys are getting great results on ATi R600 & R700 core GPUs in Arch.

I just couldn't be bothered these days going jumping through the hoops of using combinations of [testing] .git & the like to get the open-source drivers functioning at their current peak with kernel .32.  

So I'll just wait as I said before until at least the kernel is out of [testing]; I may even decide to wait until kernel .33 comes out of [testing], as open-source 3D will be even faster for my GPU then & other necessary versions of packages will be beyond .git & [testing].

I don't use Arch for its so called cutting edge versioning, or the inherent increases in speed; I just use it because I'm lazy. :lolflag:

---

### Post by handy on 2009-12-18
> **PurposeOfReason said:**
> Say what you will, but unless the open drivers can backwards engineer eyefinity I want catalyst.

Use whatever does it for you! 

I LOVE freedom of choice. :)

---

### Post by Nerd King on 2009-12-18
On the subject of .33 rc1 is now available at [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc1/) for the brave. Combine with xorg-edgers PPA as always, and forget about getting Catalyst to work with it, it aint gonna happen!

---

### Post by spigy11 on 2009-12-19
Cool,  Cairo-Dock is finally working with OpenGL after installing 9.12 --> used sh ./ati* --buildpkg Ubuntu/karmic for Karmic Koala ;)

Cheers :D

---

### Post by kreggz on 2009-12-19
so does video still flicker?

---

### Post by jvdurme on 2009-12-21
Well, the 9.12 didn't work here on Jaunty.
First completely removed old drivers (this worked since this is the 3rd ATI installation I did).
First the package build failed because I had to install libQtGui4, whatever that might be.
Then building went fine, deb installation too. Restart.
Splash screen is there, but when I'm supposed to have the login screen, the screen goes black. I hear the Ubuntu drum, but black.

Couldn't find a solution on the net, so went back to 9.11. Works fine.

I do have a quite complex dual-head set up with SwapScreen and so.... but it works for previous versions ....

---

### Post by rajeev1204 on 2009-12-21
I installed it with the first option , not a package build which failed for me.

But anyways, i cant see the new control center enhancements like HDTV etc ,Flicker free tv out etc as said in the release notes.

Anyone know ?


rajeev

---

### Post by stoner_di on 2009-12-23
My HOWTO for Ati Catalyst 9.12 with kernel 2.6.32:


1 .Create directory and extract ati-driver-installer-9-12-x86.x86_64.run in it with this console command:

sh ati-driver-installer-9-12-x86.x86_64.run --extract YourDirectory

2.Go to the directory:

cd /...../YourDirectory/

3.Download these (gentoo team realise) patch`s:

1.patch

and copy them into /YourDirectory

4.&#1045;xecute these commands:

cat 1.patch | patch -p1

5.Become root user with this command:

sudo su

(You can uninstall the old driver to work in a nice graphical environment)

6.Install drivers with this command

sh ati-installer.sh 8.682 --install

7.Reboot system

Now everything should be fine!!!!

---

### Post by Qola on 2009-12-23
Poor ATI users <3

---

### Post by hornedfiend on 2009-12-26
Hi guys,

Does anybody know if this solves my current 9.11 problem with ubuntu 9.10. The thing is that, after I install the catalyst drivers I get extremely low performance with movies (almost unplayable) and a few other things,but the drivers show up correctly. Anybody know what is that? I have an ati radeon 3470 which, unfortunately, came with my laptop (so I'm unable to change that). Also, does HDMI work (I use that a lot for movies) ?

---

### Post by Pasdar on 2009-12-26
9.12 works great on mine (ATI 4570), first driver that actually works great (ati linux standards)... I play the games in my signature in max settings great FPS...

The only issues i still have is with flickering video, when movie moves fast, etc (tearing)... hope they fix it with 10.1/2

---

### Post by klemi on 2009-12-28
Hello Ubuntu family,

I have for the first time a laptop with graphics card ATI (RADEON HD 4670). I would like to ask what was your motivation to instal the newest Catalyst driver with the patch of Gentoo?

The properitäre driver, to the Ubuntu provides a previous version of Catalyst 9.10 is according to my information.
On an Ubuntu page will get, to instal only distribution-specific version from the repository, to update only with problems on a newer version.

E.g., a difference consists in it which must not be installed the Catalyst driver from ununtu karmic once more if an update of the kernel instal became?

Which experiences do you have?
I am grateful for tips.

Klemi

---

### Post by kronictokr on 2010-01-06
Install the fglrx Driver from ATI Catalyst 9.12 For Ubuntu 9.10 Karmic 64 bit

BACK UP ANY IMPORTANT INFO!!!!!!!!!!!!!

BACK UP ANY IMPORTANT INFO!!!!!!!!!!!!!

[COLOR="black"][COLOR="Green"]**Install the fglrx Driver from ATI Catalyst 9.12 For Ubuntu 9.10 Karmic**[/COLOR][/COLOR]


We have to create a folder to enable the instalation process
          location  filename
            VVVV       VVV
create /usr/share/ati "ati"

to do this, enter in a terminal the following command

sudo nautilus

then click "file system" from the left side of the window, then double click the file "usr" and the same with "share". once inside the "share folder, right click on a blank space, click create file, name it "ati".  

leave the nautilus window open while you do the next step

download the 64bit driver from this link
VVVVVVVV
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run)

now copy the downloaded file, or drag it into the file you created , (/usr/share/ati  <location reminder )still open in your nautilus window.

when you have placed the "ati-driver-installer-9-12-x86.x86_64.run" file into /usr/share/ati , close your nautilus window, and type the next command into a terminal.

sudo sh /usr/share/ati/ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic

this will take a couple minutes as it gathers the proper pakages for your ati gpu. it will create debs and a change log , that will install with the following method

sudo dpkg -i *

there will be missing dependancies, go to SYSTEM>>>SYNAPTICS , and select edit top left , scroll down to and click on fix broken pakages. the click on apply, and lastly click on reload.

now go back to your terminal (to ensure ALL neded pakages are installed, and correctly follow this process exactly)
so, like i was saying, in your terminal, enter the following commands

sudo dpkg -i *

sudo aticonfig --initial

sudo sh /usr/share/ati/ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic


sudo dpkg -i *

sudo aticonfig --initial

sudo reboot

MAKE SURE TO COMPLETE ALL THE STEPS BEFORE YOU REBOOT!!

AFTER YOU REBOOT
vvvvvv
to confirm , in a terminal type

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200
OpenGL version string: 3.2.9232

if you get errors, 
do this again, but i suggest you get it right the first time

sudo sh /usr/share/ati/ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic

sudo dpkg -i *

sudo aticonfig --initial

sudo reboot



references
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_910_linux.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_910_linux.pdf)

---

### Post by Techsnap on 2010-01-06
You know, you should be able to just run the file as is and run through the automatic installation. Unless you're planning to install it on more than one OS building the .deb packages is pointless at best. Install DKMS after so that it won't break with a kernel upgrade.

---

### Post by Methuselah on 2010-01-06
Catalyst!?
Run for your life!

---

### Post by Pasdar on 2010-01-06
whats up with the huge 'how to' on installing this? Just go to hard ware drivers, uninstall your current drivers. Download the file from ATI website, right click file, enable execute under permissions, run file and click install...

Anyway, 9.12 is great... i finally have a great experience on linux. everything works... i hope they fix the video flickering with their next version.

---

### Post by markbuntu on 2010-01-06
> **kronictokr said:**
> 
We have to create a folder to enable the instalation process
          location  filename
            VVVV       VVV
create /usr/share/ati "ati"

to do this, enter in a terminal the following command

sudo nautilus

then click "file system" from the left side of the window, then double click the file "usr" and the same with "share". once inside the "share folder, right click on a blank space, click create file, name it "ati".  



You really do not want to do this since the installer creates the usr/share/ati directory and puts  /amdcccle there along with the uninstall script, install log, and a few other shell scripts, doc lists etc.

You should just run the installer. If it does not work for you then you should file a bug report at launchpad so it can get fixed by the Ubuntu maintainers. I have had no problems myself using the installer for well over a year with hardy and intrepid and jaunty and karmic.

---

### Post by kronictokr on 2010-01-06
you can just run the file , yes, and it gives you generic drivers, mas as well stick to repositories...
simply running the file doest optimise the driver for you specific driver. thats why ati has the --buildpkg option, or am i again wrong. im all for the easy way, but i preffer the right way.

case and point, to install the the way you guys are saying is fine, and i appreciate your point of view

references
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[https://a248.e.akamai.net/f/674/9206..._910_linux.pdf](https://a248.e.akamai.net/f/674/9206..._910_linux.pdf)

edit:techsnap, i know the install does address KDMS as i read the output in terminal
but i dont know enough to say whether it affects the kernel or not. with an update. as of yet im having no problems at all using this method.

id be curious to see the output of "fglrxinfo"
to compare at least

---

### Post by Techsnap on 2010-01-07
> you can just run the file , yes, and it gives you generic drivers, mas as well stick to repositories.

Misinformation at its best. Do the following **Will Reboot After Automatically**: 

```
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run && sudo sh ati-driver-installer-9-12-x86.x86_64.run && aticonfig --initial -f && sudo reboot
```

There, that's installing the ATi driver in one command, when the installer GUI is shown, just run through the whole thing in automatic.

> simply running the file doest optimise the driver for you specific driver. thats why ati has the --buildpkg option,

It's just generating .deb files, it's not optimising ANYTHING.

---

### Post by Pasdar on 2010-01-07
roflmao, you just need to download the file and run it.... nothing more, nothing less.

---

### Post by Techsnap on 2010-01-07
> **Pasdar said:**
> roflmao, you just need to download the file and run it.... nothing more, nothing less.

Apparently some people believe that generating debs makes a difference to the driver.

---

### Post by kronictokr on 2010-01-07
im going to go over my tut, for good measure.
all the info i posted was pretty much taken from the references i posted. being from ubuntu and amd, i would suggest you harp on them. as i cant change the information that THEY provided me with. im just providing information that i thought might help other people. also in the catalyst install from the gui, if you tried it, you would notice there is no option for karmic koala. also with the debs produced, is included a changelog file, wich you would also know if you tried it. but im just a dumb newb, trying to help another newb, and since this method worked for me, and i found the information , right from the source......
its called a binary install, google it.

i was thinking of putting a tut up, using the easy way good thing i dint.  you negative people are the reason microsoft is still number one. positive criticism is great, its gets you more than being a d#@%*%e and putting people down. people that are genuinely trying to help the ubuntu community, in order to make it easier for the first time user . providing people who may not be able to pay 100-300 for an os alone, with an easy to use and reliable , COMPLETE os, including pre built software options.

lets not forget why were here

intuitive advise would be greatly appreciated

---

