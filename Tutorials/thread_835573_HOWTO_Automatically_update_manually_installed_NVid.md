---
title: "HOWTO: Automatically update manually installed NVidia drivers after kernel updates"
date: 2008-06-20
forum: Tutorials
---

### Post by sdennie on 2008-06-20
**Overview**
If you've manually installed the NVidia drivers from the NVidia website, when major kernel releases come out it's necessary to re-install the drivers for the new kernel.  This guide aims to automate that process so that it happens when the new kernel is installed and requires no user intervention.

This HOWTO assumes you have correctly installed the NVidia drivers from the website and that you have rebooted after installing them at least once (this is very important because, if you haven't installed them correctly, upon reboot they will not work).  This guide is not aimed at users who have installed the drivers using EnvyNG or via the default Ubuntu mechanism.

(Note: This has only been tested on 8.04 and may not work or be needed in later versions)

**Implementation**

*Update: After finding an easier method to this, I've modified the directions slightly.  People using the old method can continue to use it or, see [this post]("http://ubuntuforums.org/showpost.php?p=5315880&postcount=17") to revert the changes from the old method.*

*Another Update: I've changed the script very slightly to provide a status message depending on whether or not building the new driver worked.  People can replace nvidia-update with this new script or continue to use the old.  I've also changed the testing instructions slightly.*

The first thing I recommend doing this is to move the driver you are using to /usr/src and make a symlink to it.  For example:

```

sudo mv NVIDIA-Linux-x86-173.14.05-pkg1.run /usr/src
sudo ln -s /usr/src/NVIDIA-Linux-x86-173.14.05-pkg1.run /usr/src/nvidia-driver

```

The reason for doing this is so that if you change the driver you are using, you can simply remove the symlink and point it at the new driver and not have to modify the script we are about to install.

The script we will use to automate this process is here:

```

#!/bin/bash
#

# Set this to the exact path of the nvidia driver you plan to use
# It is recommended to use a symlink here so that this script doesn't
# have to be modified when you change driver versions.
DRIVER=/usr/src/nvidia-driver


# Build new driver if it doesn't exist
if [ -e /lib/modules/$1/kernel/drivers/video/nvidia.ko ] ; then
    echo "NVIDIA driver already exists for this kernel." >&2
else
    echo "Building NVIDIA driver for kernel $1" >&2
    sh $DRIVER -K -k $1 -s -n 2>1 > /dev/null

    if [ -e /lib/modules/$1/kernel/drivers/video/nvidia.ko ] ; then
        echo "   SUCCESS: Driver installed for kernel $1" >&2
    else
        echo "   FAILURE: See /var/log/nvidia-installer.log" >&2
    fi
fi

exit 0

```

Essentially, what it does is check to see if the kernel we are installing has the proprietary nvidia driver installed.  If not, it will build the module for that kernel.

Name the script update-nvidia and install it with:

```

sudo mkdir -p /etc/kernel/postinst.d
sudo install update-nvidia /etc/kernel/postinst.d

```

That's it.  The next time you install a kernel that doesn't have the NVidia driver, it will automatically build it for you at installation time.

**Testing**
You can test it by either waiting for the next kernel release or by temporarily installing the -386 kernel to verify that it really does work properly.  If you choose the later method of testing, this is how to do it:

```

sudo apt-get install linux-image-386 linux-headers-386

```

You should see a long pause as it says it's building the nvidia driver for the -386 kernel and then a success message.  If it works, you can then remove the -386 kernel we installed for testing with:

```

sudo apt-get remove linux-headers-2.6.24-19-386 linux-headers-386 linux-image-2.6.24-19-386 linux-image-386 linux-ubuntu-modules-2.6.24-19-386

```


Comments/Questions/Suggestions welcome.

---

### Post by aaargh486 on 2008-06-20
Wow you must be psychic. I was just thinking of a way too do that.

Thanks a bunch!

---

### Post by atlas95 on 2008-06-20
Very usefull howto !
Thanks a lot guy !

---

### Post by Gina on 2008-06-24
Thank you :):) That looks great :)  Just on the point of manually installing the new nVidia driver on my AMD64 machine.  Got fed up with trying to use 640x480 display!!  Seems unlikely to me that we will see automatic nVidia driver installation very soon, so that HowTo will be invaluble.

---

### Post by sdennie on 2008-06-24
> **Gina said:**
> Thank you :):) That looks great :)  Just on the point of manually installing the new nVidia driver on my AMD64 machine.  Got fed up with trying to use 640x480 display!!  Seems unlikely to me that we will see automatic nVidia driver installation very soon, so that HowTo will be invaluble.

You'll still have to manually install the first time because the nvidia drivers aren't just a kernel module.  I'll edit the howto and make it clearer that you need to have manually installed and rebooted at least once before the tutorial will work.

---

### Post by hkbruvold on 2008-06-24
Thank you, this is great. I'll soon get a Nvidia card and this wil be very useful. :)

---

### Post by sdennie on 2008-06-24
I'd like to point out that it's still possible for the nvidia installation to break when the xserver-xorg-core package updates.  The drivers will still work (you'll be at normal resolution when you login) but, that package conflicts with some of the files in the nvidia manual installer and so direct rendering will be turned off (so, compiz will no longer work).  If I can figure out a solution to prevent that as well, I will post it in the HOWTO.

---

### Post by ktechman on 2008-06-26
Vor, 

I am getting this error when I try to accomplish the renaming of the file update-grub

>  sudo install update-nvidia-grub /usr/sbin
install: cannot stat `update-nvidia-grub': No such file or directory
 when attempting to replace the kernel installation rule with the script.  I am very new so I may be missing an elementary step.   Any help would be appreciated. Thank You

---

### Post by sdennie on 2008-06-26
Before running that command run "ls" and see if you see a file named "update-nvidia-grub".  It's possible that when you saved the file, you named it something slightly different or saved it in a different location.

---

### Post by KubuntuKilledMe on 2008-06-26
This is really cool. Thanks!

---

### Post by Brando569 on 2008-06-27
luckily i saw this while i was reading your reply to my intel/alsa thread since i was also trying to figure out a way to do this.

---

### Post by sdennie on 2008-06-27
> **Brando569 said:**
> luckily i saw this while i was reading your reply to my intel/alsa thread since i was also trying to figure out a way to do this.

I actually just updated the HOWTO to use a more generic method to install the driver.  There is also another example of installing the virtualbox driver using the same method here: [http://ubuntuforums.org/showpost.php?p=5271094&postcount=7](http://ubuntuforums.org/showpost.php?p=5271094&postcount=7)

---

### Post by master_kernel on 2008-06-27
Thanks! I think I'll integrate this method into the release after KernelCheck HopeStar!

MK

---

### Post by sdennie on 2008-06-27
> **master_kernel said:**
> Thanks! I think I'll integrate this method into the release after KernelCheck HopeStar!

MK

You could probably also check for a bunch of other things like virtualbox, vmware, ndiswrapper drivers, firmware, etc and use the same basic method to have them auto-install into new kernels.  I'm using this method for both nvidia and virtualbox with custom compiled kernels and it works great.  Once you know where the hooks are, there are a lot of possibilities.

---

### Post by ktechman on 2008-07-03
Vor,

     To be completely honest I do not even know if I entered the script correctly.  Here is what I did I followed you instruction to 

> The first thing I recommend doing this is to move the driver you are using to /usr/src and make a symlink to it. For example:

Code:

sudo mv NVIDIA-Linux-x86-173.14.05-pkg1.run /usr/src
sudo ln -s /usr/src/NVIDIA-Linux-x86-173.14.05-pkg1.run /usr/src/nvidia-driver



Then I attempted to install the script by a copy and paste of the entire entry > #!/bin/bash
#

# Set this to the exact path of the nvidia driver you plan to use
# It is recommended to use a symlink here so that this script doesn't
# have to be modified when you change driver versions.
DRIVER=/usr/src/nvidia-driver


# Build new driver if it doesn't exist
if [ -e /lib/modules/$1/kernel/drivers/video/nvidia.ko ] ; then
    echo "NVIDIA driver already exists for this kernel." >&2
else
    echo "Building NVIDIA driver for kernel $1" >&2
    sh $DRIVER -K -k $1 -s -n 2>1 > /dev/null
fi
all at once except for "exit" then I was lost at how to name the script and install it.  When I tried to google the answer for "installing a script Ubuntu" I ran into a wall.  :confused:I am a complete noobe here at the Ubuntu wheel. Thank you for your reply.

---

### Post by atlas95 on 2008-07-03
Coould you repost the old way to do it, I want to clean and do the new methode but I have forget what was the old..; thanks ;)

---

### Post by sdennie on 2008-07-03
> **atlas95 said:**
> Coould you repost the old way to do it, I want to clean and do the new methode but I have forget what was the old..; thanks ;)

I think this should be sufficient to revert the old way and let you follow the instructions for the new way.

First:

```

sudo rm /usr/sbin/update-nvidia-grub

```

Then, ensure that the file /etc/kernel-img.conf looks exactly like this:

```

do_symlinks = yes
relative_links = yes
do_bootloader = no
do_bootfloppy = no
do_initrd = yes
link_in_boot = no
postinst_hook = update-grub
postrm_hook   = update-grub

```

After that, you should be able to follow the instructions for the new method.

---

### Post by sdennie on 2008-07-03
> **ktechman said:**
> Vor,

     To be completely honest I do not even know if I entered the script correctly.  Here is what I did I followed you instruction to 



Then I attempted to install the script by a copy and paste of the entire entry all at once except for "exit" then I was lost at how to name the script and install it.  When I tried to google the answer for "installing a script Ubuntu" I ran into a wall.  :confused:I am a complete noobe here at the Ubuntu wheel. Thank you for your reply.


Are you certain that you need to use this tutorial?  Have you downloaded and installed the nvidia drivers directly from nvidia?

If you are sure you need to use it, just use Applications->Accessories->Text Editor, paste the script into it (including the "exit" part) and save it as update-nvidia in your home directory.  You should be able to follow the rest of the guide after that.

---

### Post by ktechman on 2008-07-04
Vor,

     I have not been at this very long but when I updated from kernel 18 to 19 none I mean none of the settings for my driver were in tact.  So for now I reinstalled the driver the manual way and everything is back to normal until another kernel upgrade.  I believe that some things that Ubuntu veterans take for granted should be put in the instructions just for the simple reason that even with all of my windows experience I spent little or no time with the command line or adding scripts.  MS has babied us with so many user friendly self explaining programs that getting a handle on something new such as Ubuntu takes a bit of a kick in the seat of the pants, so to speak. And with all of my attention being spent on the newest threat from MS who has time to focus on anything else.  Please endure with this new generation of users who have ventured over to the other side of the fence where the grass is truly greener. I am eternally grateful for being pulled from the clutches of MS even if they do seem benign, the alternative of going back gives me great pause so I will muddle through over here learning what should already be second nature if not for the constant lulling of a company who's only concerned is with their bottom line, hiding behind the guise of being benevolent with the highly publicized facts of  Bills philanthropy.  With all that said I appreciate your response and the help. BTW went without a hitch.

Best Regards

---

### Post by drdaz on 2008-07-06
> **vor said:**
> 
```

    echo "Building NVIDIA driver for kernel $1" >&2
    sh $DRIVER -K -k $1 -s -n 2>1 > /dev/null

```


Why are we piping output to /dev/null here? This strikes me as a bad idea. If something goes wrong in this step, the script dies silently, making debugging a real pain. I know this because it just happened to me. :-)

I would suggest not hiding the output from the sh command - it may make your log file look 'ugly', but usually ugly is preferred to invisible in case of failure.

Many thanks for this btw; I use a number of patched modules in my systems and was unaware of this hook. Now I don't need to wait to upgrade my kernel until I have 'enough time'. :-)

/drdaz

---

### Post by lazertek on 2008-07-06
installing video card drivers with **envy or the newer ENVY NG** is another option too... takes away the manual labor of installing and updating...

---

### Post by sdennie on 2008-07-06
> **drdaz said:**
> Why are we piping output to /dev/null here? This strikes me as a bad idea. If something goes wrong in this step, the script dies silently, making debugging a real pain. I know this because it just happened to me. :-)

I would suggest not hiding the output from the sh command - it may make your log file look 'ugly', but usually ugly is preferred to invisible in case of failure.

Many thanks for this btw; I use a number of patched modules in my systems and was unaware of this hook. Now I don't need to wait to upgrade my kernel until I have 'enough time'. :-)

/drdaz

Well, I was kind of torn between displaying the output and even using "exit $?".  The reason I'm not displaying the output is because if building the driver fails, you are no worse off than before you used the guide.  The reason I'm not using "exit $?" is because when /etc/kernel/postinst.d scripts fail, it makes apt-get/dpkg upset and it may not be obvious how to fix the error that apt-get/dpkg will now be reporting.

Having said that, you are probably right in that I could detect the output value of the install and, if it fails, report it and point them at the installer log file (while still using exit 0).  I'll modify the script a bit later to do that.

---

### Post by sdennie on 2008-07-06
> **aslam said:**
> installing video card drivers with **envy or the newer ENVY NG** is another option too... takes away the manual labor of installing and updating...

Yes, envyng is a very useful tool for installing the nvidia drivers.  There are valid reasons for using the drivers directly from nvidia but, most people will do just fine with envyng.

---

### Post by showgun22 on 2008-07-11
I am no expert at this stuff and I am running into a small problem.
I have installed NVIDIA-Linux-x86-173.14.09-pkg1.run last week
and it has been running flawlessly.

I am trying to set up the above recommendation I created an empty file and pasted the above code and name it as stated. Unfortunately I am not sure where I should put the script?

I have tried a few different folder I could think of but everytime I run
sudo install update-nvidia /etc/kernel/postinst.d

I get an error
Thanks

---

### Post by sdennie on 2008-07-15
> **showgun22 said:**
> I am no expert at this stuff and I am running into a small problem.
I have installed NVIDIA-Linux-x86-173.14.09-pkg1.run last week
and it has been running flawlessly.

I am trying to set up the above recommendation I created an empty file and pasted the above code and name it as stated. Unfortunately I am not sure where I should put the script?

I have tried a few different folder I could think of but everytime I run
sudo install update-nvidia /etc/kernel/postinst.d

I get an error
Thanks

Did you save the file as "update-nvidia" and save it in, for instance, your home directory?  Also did you first run this before trying the install command?

```

sudo mkdir -p /etc/kernel/postinst.d

```

---

### Post by showgun22 on 2008-07-15
I had it just about every where else except the home directory <LOL>
Saved it there did
sudo install update-nvidia /etc/kernel/postinst.d
no problem...
Thanks

---

### Post by potiphera on 2008-07-16
This guide worked perfectly for me! Thanks, **vor**, you're my new hero.

---

### Post by freakwillie on 2008-07-24
[COLOR=Red]**EDIT**[/COLOR]: **I solved that. But now I'm having another problem. This is my [COLOR=LightBlue][/var/log/nvidia-installer.log]("http://pastebin.com/m3a5150c7")[/COLOR]. Any help is much appreciated.**

[CENTER]________________________________________________________________________________________[/CENTER]
Hello,

I'm having a couple problems here. I'm using 

```
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers 
```to create debs that setup the configs for me. Well, when I do a 

```
dpkg -i linux-image-2.6.26-custom_2.6.26-custom-10.00.Custom_i386.deb
```it tries to run the script to no avail. I think it`s not running the NVidia script, since it creates no log in /var/log. It does shows the failure message though. 

I`m also trying to make a script myself to keep the drivers for my wifi card, but that`s something to be spoken of after I can even get your script to work.

Thanks in advance,
Willie.

---

### Post by sdennie on 2008-07-25
> **freakwillie said:**
> [COLOR=Red]**EDIT**[/COLOR]: **I solved that. But now I'm having another problem. This is my [COLOR=LightBlue][/var/log/nvidia-installer.log]("http://pastebin.com/m3a5150c7")[/COLOR]. Any help is much appreciated.**

[CENTER]________________________________________________________________________________________[/CENTER]
Hello,

I'm having a couple problems here. I'm using 

```
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers 
```to create debs that setup the configs for me. Well, when I do a 

```
dpkg -i linux-image-2.6.26-custom_2.6.26-custom-10.00.Custom_i386.deb
```it tries to run the script to no avail. I think it`s not running the NVidia script, since it creates no log in /var/log. It does shows the failure message though. 

I`m also trying to make a script myself to keep the drivers for my wifi card, but that`s something to be spoken of after I can even get your script to work.

Thanks in advance,
Willie.

The stock 173.14.05 drivers won't build against the 2.6.26 kernel.  You'll need to use 173.14.09: [http://www.nvnews.net/vbulletin/showthread.php?t=114873](http://www.nvnews.net/vbulletin/showthread.php?t=114873)  Also, when you install custom kernels and are using this method, it's best to install the headers with the image or scripts in /etc/kernel won't work (which I suspect is what was causing your original problem).

---

### Post by freakwillie on 2008-07-25
> **vor said:**
>  Also, when you install custom kernels and are using this method, it's best to install the headers with the image or scripts in /etc/kernel won't work (which I suspect is what was causing your original problem).

Do you mean I should make and make install_modules instead of using make-kpkg to create the debs?

I'm also trying to make a script that involve the process of compiling, but I can't get the make install to move the files to /lib/modules/(kernel that's being compiled) instead of /lib/modules/(actual kernel). Any hints about it?

thanks.

---

### Post by sdennie on 2008-07-25
> **freakwillie said:**
> Do you mean I should make and make install_modules instead of using make-kpkg to create the debs?

I'm also trying to make a script that involve the process of compiling, but I can't get the make install to move the files to /lib/modules/(kernel that's being compiled) instead of /lib/modules/(actual kernel). Any hints about it?

thanks.

No, you should certainly use make-kpkg to build the kernel image and headers.  I would use one of the many guides that exist for building a kernel the Ubuntu way.

---

### Post by freakwillie on 2008-07-25
Just using the new nvidia driver solved the problem, thanks for the attention. But do you know how to redirect a make install to a diferent kernel library that the one of the kernel being used using flags (or must I edit the Make file?).

---

### Post by sdennie on 2008-07-25
It will depend on the makefile but, a modification of this script might be what you are looking for: [ Automatically update VirtualBox driver after kernel updates]("http://ubuntuforums.org/showpost.php?p=5271094&postcount=7")

---

### Post by nycste on 2008-07-25
hey all great thread props to thread starter i got a couple quick questions and concerns

1. im using nvidia driver 173.14.09 installed by envyng and currently using kernal 2.6.19 i believe

2. i love updating everything i can get my hands on so i went to software sources and clicked proposed updates for hardy, and it installed a bunch of stuff like firefox 3.0.1 and a new kernel 2.6.20 i think i didnt realize this so after i rebooted well my xserver or xorg settings or nvidia stuff (excuse my linux newbness i dont know which it was) but buttom line is that my visual settings where all messed up and lacking tons of linux power i jsut cant do everything from the terminal

blah i just keep typing lol, so anyways i found this thread and thought to myself oo this might be the way to fix my kernel .20 that i wont use because nvidia settings are messed up... so i clicked on load .19 kernal i prayed and everything im doing has been fine since, but in grub loader kernal .20 is listed as my newest, but isnt .26 the newest?

so should i follow this guide?
or

should i just figureout how to use envyng to reinstall or something while i boot the .20 kernel or what

thanks for any help, and if you dont mind me asking what kernels are you guys using, thread starter im curious most about...

and is updating kernals a good thing? or much greater chance thinsg will break and shouldnt be done by new linux users right? maybe not idk im asking ! thanks

---

### Post by sdennie on 2008-07-26
> **nycste said:**
> hey all great thread props to thread starter i got a couple quick questions and concerns

1. im using nvidia driver 173.14.09 installed by envyng and currently using kernal 2.6.19 i believe

2. i love updating everything i can get my hands on so i went to software sources and clicked proposed updates for hardy, and it installed a bunch of stuff like firefox 3.0.1 and a new kernel 2.6.20 i think i didnt realize this so after i rebooted well my xserver or xorg settings or nvidia stuff (excuse my linux newbness i dont know which it was) but buttom line is that my visual settings where all messed up and lacking tons of linux power i jsut cant do everything from the terminal

blah i just keep typing lol, so anyways i found this thread and thought to myself oo this might be the way to fix my kernel .20 that i wont use because nvidia settings are messed up... so i clicked on load .19 kernal i prayed and everything im doing has been fine since, but in grub loader kernal .20 is listed as my newest, but isnt .26 the newest?

so should i follow this guide?
or


If you are using envyng, this guide is probably not applicable to you.  I will clarify the first post a bit to reflect that.

> 
should i just figureout how to use envyng to reinstall or something while i boot the .20 kernel or what


You can either try to re-install with envyng or you can uninstall the envyng drivers and download the nvidia drivers from the website and then use this guide.  I'm not sure which would be easier.

> 
thanks for any help, and if you dont mind me asking what kernels are you guys using, thread starter im curious most about...


I use a custom compiled 2.6.26 kernel with PAE support and some minor configuration tweaks.

> 
and is updating kernals a good thing? or much greater chance thinsg will break and shouldnt be done by new linux users right? maybe not idk im asking ! thanks

I don't recommend using a custom kernel unless you want to learn how to do it or you have a pressing need to do it.  I also don't recommend it at the moment because the nvidia drivers don't play nicely with kernels later than 2.6.24 and the performance of things like compiz noticeably suffers (it's almost impossible to get smooth animations).

---

### Post by nycste on 2008-07-26
hey thanks for the quick and simple reply

2.6.24-19 is what im currently using and 2.6.24-20 is whats installed but the drivers conflict, soo i think ill test envyng alittle and try and fix and run off kernal 2.6.24-20...

maybe ill try and find a changelog btw 2.6.24-19 and 2.6.24-20 and see if its even worth it otherwise i should just maybe remove .20 till its offically approved by ubuntu or something?

---

### Post by freakwillie on 2008-07-26
Hey, Vor, thanks.

Based on that other thread I could write the script. I didn't know how to pass arguments to the makefile.

---

### Post by zalmoxes on 2008-08-16
this is not working for me. the nvidia kernel is repeatedly getting rebuilt at startup, regardless of whether i have done a kernel update.

 how do i remove the script??

---

### Post by sdennie on 2008-08-19
> **zalmoxes said:**
> this is not working for me. the nvidia kernel is repeatedly getting rebuilt at startup, regardless of whether i have done a kernel update.


I'm not sure how that's possible as those scripts only get executed by a post install script that lives in a kernel package made with make-kpkg.  Are you sure you aren't seeing something else going on?

> 
how do i remove the script??

To remove it, just delete the script that you installed:

```

sudo rm /etc/kernel/postinst.d/update-nvidia

```

---

### Post by Cammy on 2008-11-30
Sorry to resurrect this thread, but I'm having driver problems.

I have an NVidia 6200LE card, and am using the latest beta driver from NVidia's website that I've installed manually with the 'sh' command.  The other day I had a kernel update that left me with 640x480 resolution, and I've been unable to get the proper driver to "stick" even after reinstalling it repeatedly.

Right now I can only get the machine to work by doing the following:

1) Boot up into the latest kernel, recovery mode.

2) Go in as root and get a command prompt (3rd option I think)

3) Find the current video driver, and reinstall it using 'sh driver-name'

4) After the install, type "exit" then pick "resume normal boot.

That gets me in with a proper driver. Anything else gets 640x480.

I tried the steps outlined in post 1 of this thread, but so far no dice.  Any tips as to what I'm doing wrong would be helpful.

---

### Post by Cammy on 2008-12-01
Ok, seems I fixed it with some help from the nvidia forum.  I had nvidia-kernel-common installed, so I removed it and its dependencies.  After that, the new driver stuck.

---

### Post by sleepyjon on 2008-12-02
I wish I had seen this two days ago when I updated my kernel. Thank you!

---

### Post by huntzire on 2008-12-27
Well I have a question, Before I atempt the measures presented in this thread, every time I run the nvidia updater, its unable to compile a interface to my kernel, every time and tells me to check the /var/log/ which tells me the same thing and no new infomation is provided. I'm currently using a custom 2.6.27.10 with special considersations to reduce desktop latency and I'm 64 bit.



 I mean I have serously broken my system before in the past trying to get this driver to work in 7.x series of ubuntu, but it seems to me like the nvidia installer is just crap and it never gives me any useful infomation to go off troubleshooting with.

If anyone knows how to get around this or atleast tell me if i do remove the dkms based nvidia drivers that the installer will beable to compile a interface, that would rock as i always look forward to nice features of the kernel.

One im excited about is the prospect of GEM graphical memory management component and the new Ext4 support with extents and delayed allocation.

But i can't enjoy its goodness when Nvidia hoses any prospect of gaming simply because the stupid installer cant compile a interface to the 2.6.28 kernel :/

---

### Post by sdennie on 2008-12-27
> **huntzire said:**
> Well I have a question, Before I atempt the measures presented in this thread, every time I run the nvidia updater, its unable to compile a interface to my kernel, every time and tells me to check the /var/log/ which tells me the same thing and no new infomation is provided. I'm currently using a custom 2.6.27.10 with special considersations to reduce desktop latency and I'm 64 bit.


The nvidia installer is not happy when you compile Xen functionality into the kernel.  From menuconfig it's Processor Type and Features->Paravirtualized Guest Support.  Make sure that is off.  Also, for the newer kernels you will need to use the newer (possibly even beta) drivers.  I'm running 2.6.28 at the moment and the 180.18 driver works.

> 
One im excited about is the prospect of GEM graphical memory management component and the new Ext4 support with extents and delayed allocation.


You won't get GEM with nvidia.  Right now it only works on Intel cards and I doubt if the nvidia proprietary driver will ever support it.  ext4 is nice though.  You really need to properly reformat as ext4 to see the benefits of it though.

---

### Post by zalmoxes on 2008-12-27
> **vor said:**
> I'm not sure how that's possible as those scripts only get executed by a post install script that lives in a kernel package made with make-kpkg.  Are you sure you aren't seeing something else going on?


i'm quite sure, its repeatedly and unnecessarily executing the script at startup it says even though i have not done a kernel update it says "executing nvidia-update" and then the nvidia splash screen appears.
and the login screen appears.

---

### Post by huntzire on 2008-12-27
I would just like ti post, VOR IS THE **MAN!**

I have been running into that hurdle since 7.x and he solved it in one post!

Thanks man all I had to do is get a beta driver and boom it worked like a beautiful charm!

Vor is the man!!

---

### Post by kamitsukai on 2009-04-11
Ok wait for the noob question...but

What do I do with the script? I've put the driver in /usr/src/ and created a sylink but now what? do I have to copy & paste the script into a file? and where do I have to put it after that?

Thanks in Advance!

---

### Post by donaldt on 2009-04-23
OK, let's see if someone can solve this one.

I have installed the Nvidia driver.  It is the only one shown.  It is shown as activated and currently in use.  It works on the primary screen, but I cannot configure anything else.
When I open Nvidia X server settings my laptop computer screen shows normally at 1280 x 800 pixels.  My GeForce 8400M GS card is shown and my second monitor is listed (DFP-1  LG-L196 WQT), but will not configure or light up the display.   Native, best fit, front end and back end resolution  is listed as “unknown” as is refresh rate.  

The second screen is always shown as disabled.  When I change the screen configurations around to show the correct relative position and enable the LPG monitor at 1440 x 900 and try apply, I get “cannot apply” with 5 possible reasons why.

When I follow the instructions to “save the configuration to the X config file and restart the X server”, I click on SAVE and I get a Red bar and “unable to remove old X config backup file '/etc/x11/xorg.conf.backup”  After I click OK, then quit (to shut down x server) and then re-start xserver, the configuration returns to the same settings prior to all the changes. 

Any help will be appreciated.  

donaldt

---

### Post by akoskm on 2009-05-04
Thank you! I hope that works. :)

---

### Post by Cammy on 2009-05-04
> **donaldt said:**
> When I follow the instructions to “save the configuration to the X config file and restart the X server”, I click on SAVE and I get a Red bar and “unable to remove old X config backup file '/etc/x11/xorg.conf.backup”  After I click OK, then quit (to shut down x server) and then re-start xserver, the configuration returns to the same settings prior to all the changes.

Donald,

This may be a dumb question, but are you running the NVidia X server settings app as root?  I had to edit my menu entry for it and append a "gksu" so it would run as root, otherwise it would give me the same problem with not being able to remove the old backup file.

---

### Post by amesdaq on 2009-08-27
Is it just me or did anyone else have errors with the script because of the license agreement not  being accepted? I think the link in the script that reads

```
sh $DRIVER -K -k $1 -s -n 2>1 > /dev/null
```

should maybe be modified to look like

```
sh $DRIVER -K -k -a $1 -s -n 2>1 > /dev/null
```

But I am no pro at all so maybe I am just doing something wrong but that change worked for me

---

### Post by secUnd3r on 2009-09-14
Hi, I followed the directions in this thread as well as the directions in this thread: [http://ubuntuforums.org/showthread.php?t=1125400.]("http://ubuntuforums.org/showthread.php?t=1125400") Everything is running smoothly and looking good, only tonight when Ubuntu tried to update it gave me an error message.
```

Errors were encountered while processing:
 linux-image-2.6.28-15-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.28-15-generic (2.6.28-15.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-15-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.28-15.49 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.28-15.49 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.28-15-generic

   ...done.
run-parts: executing /etc/kernel/postinst.d/update-nvidia
run-parts: failed to exec /etc/kernel/postinst.d/update-nvidia: No such file or directory
run-parts: /etc/kernel/postinst.d/update-nvidia exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28-15-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.28-15-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.28-15-generic

```

I followed the exact directions of the first post in this thread, and rechecked it plenty of times. Can anyone help me out?

---

### Post by secUnd3r on 2009-09-16
> **secUnd3r said:**
> Hi, I followed the directions in this thread as well as the directions in this thread: [http://ubuntuforums.org/showthread.php?t=1125400.]("http://ubuntuforums.org/showthread.php?t=1125400") Everything is running smoothly and looking good, only tonight when Ubuntu tried to update it gave me an error message.
```

...
run-parts: executing /etc/kernel/postinst.d/update-nvidia
run-parts: failed to exec /etc/kernel/postinst.d/update-nvidia: No such file or directory
run-parts: /etc/kernel/postinst.d/update-nvidia exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28-15-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.28-15-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.28-15-generic

```I followed the exact directions of the first post in this thread, and rechecked it plenty of times. Can anyone help me out?
Any assistance with my issue would be greatly appreciated.

---

### Post by secUnd3r on 2009-09-16
I think I just missed something in the implementation of the script... being pretty new at Linux, I don't know what it is though. I hate to keep bumping but I would like to take care of this! Please help guys!

---

### Post by secUnd3r on 2009-09-18
Still need help with this problem if anyone out there is paying attention!

---

### Post by sunbear on 2009-09-28
> **secUnd3r said:**
> Still need help with this problem if anyone out there is paying attention!

From your error message it looks like you didn't create the script " /etc/kernel/postinst.d/update-nvidia"
> run-parts: failed to exec /etc/kernel/postinst.d/update-nvidia: No such file or directory

Follow the instructions in the first post in this thread exactly and this script should be there afterwards.

Also make sure that you followed the steps in the first post of this thread too:
[http://ubuntuforums.org/showthread.php?t=1125400&highlight=latest+NVidia+drivers](http://ubuntuforums.org/showthread.php?t=1125400&highlight=latest+NVidia+drivers)

---

### Post by NoonienSoong97 on 2009-11-20
Hi,

I have successfully installed the nvidia driver, and the nvidia-update program. I tested out the update by installing the 386 image and header. However there were also three other files that came along with the install. I think one of these files messed with my resolution. I believe one of those files were the direct cause of the initial resolution problems with 9.10. However I am using 8.04. Now my computer can only use a lower resolution setting of 800 x 600 at 72 hertz.

Update: I went into safe mode, and ubuntu fixed the problem. However I don't have the card installed after fixing the problem. Also I can't stop the gnome display manager when I try to reinstall the driver.

---

### Post by veli on 2009-11-20
Nice work, thanks for this really useful How-to.

Will this method work for Debian?

---

### Post by NoonienSoong97 on 2009-11-20
I am some what new to ubuntu, but I don't see why it can't work with debian since ubuntu came from debian.

---

### Post by Hells_Dark on 2010-02-10
While testing the script, I got a FAILURE message.

but the /var/log/nvidia-installer.log ends with ```
Your X configuration file has been successfully updated
```…

so ?

---

### Post by gillza on 2010-02-27
Hmm... Just though i'd mentions this.

Today after kernel update the drivers died even with this script. It has been working for a while until today. Had to reboot in safe mode and reinstall the drivers automatically as well as updating the drivers version. 

I also updated the simlink to the new driver and hope that it will work next time update comes.

---

### Post by Utsukushii Tsubasa on 2010-03-11
alright, this might be an older thread, but i get an error myself, such as this

```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-386 is already the newest version.
linux-headers-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 232 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.31-20-386 (2.6.31-20.57) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-386
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-386
Found initrd image: /boot/initrd.img-2.6.31-20-386
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/update-nvidia
run-parts: failed to exec /etc/kernel/postinst.d/update-nvidia: Exec format error
run-parts: /etc/kernel/postinst.d/update-nvidia exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31-20-386.postinst line 1002.
dpkg: error processing linux-image-2.6.31-20-386 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-386:
 linux-image-386 depends on linux-image-2.6.31-20-386; however:
  Package linux-image-2.6.31-20-386 is not configured yet.
dpkg: error processing linux-image-386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 linux-image-2.6.31-20-386
 linux-image-386
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Utsukushii Tsubasa on 2010-03-12
any help? please someone? im trying t not to screw up my graphics again. lol again. anyway, please help?

---

### Post by mocha on 2010-03-12
> **gillza said:**
> Hmm... Just though i'd mentions this.

Today after kernel update the drivers died even with this script. It has been working for a while until today. Had to reboot in safe mode and reinstall the drivers automatically as well as updating the drivers version. 

I also updated the simlink to the new driver and hope that it will work next time update comes.

What happened was that there was an xserver update and it broke the libGL.so symlink, that's why this script didn't work as you expected.  You didn't need to reinstall the driver, just re-do the libGL symlink.

---

### Post by gillza on 2010-03-13
> **mocha said:**
> What happened was that there was an xserver update and it broke the libGL.so symlink, that's why this script didn't work as you expected.  You didn't need to reinstall the driver, just re-do the libGL symlink.

Thank you for the reply, unfortunately I am not quite sure how to do it. I would appreciate if you could post the command. Also after a bit of googling I got this:
[https://bugs.launchpad.net/ubuntu/+bug/231930/comments/3](https://bugs.launchpad.net/ubuntu/+bug/231930/comments/3)
Could this have worked?

Thank you.

---

### Post by mocha on 2010-03-16
Next time this happens just make sure that the symlink "/usr/lib/xorg/modules/extensions/libglx.so" points to the proper opengl library, which in my case is the file "/usr/lib/xorg/modules/extensions/libglx.so.190.42"

---

### Post by gillza on 2010-03-16
Thank you for the reply! Much appreciated!

---

### Post by alvin1472 on 2010-04-14
Hello there, 

The script is sound so good after I see its function.

I am a newbie to those staff things, I don't even know where and how to key in the code..

Can anyone please show me some steps to do it?

Your help will appreciated..

---

### Post by shivkrish22 on 2010-10-18
Does this method still work for Maverick?

---

### Post by gillza on 2010-10-18
worked for me.

---

### Post by gillza on 2010-12-03
This weekend I'll be installing Ubuntu on a machine with nvidia card. Planning on using tis script. Will post here if it worked :)

(yes that is a double post, for the sake of a bump in case someone finds this helpful )

---

### Post by Mobidoy on 2010-12-25
Can someone tell me how to revert those changes. The Nvidia drivers (powermizer) cause my screen to blinks when the speed setting is changed on a GTX 460 M so, I would like to try different things...

---

### Post by gillza on 2010-12-26
I havent tried to remove the drivers myself but here is what I have found: 

[http://ubuntuforums.org/showpost.php?p=4065515&postcount=2](http://ubuntuforums.org/showpost.php?p=4065515&postcount=2).

BTW how is Ubuntu on g73jw-a1, any issues besides video?


I got to say that this thread is still very useful. I followed the guide and have a fully functional system with latest drivers that survived several Kernel updates on 10.10.  Big thanks to the OP!!!!

---

### Post by Mobidoy on 2010-12-28
> **gillza said:**
> I havent tried to remove the drivers myself but here is what I have found: 

[http://ubuntuforums.org/showpost.php?p=4065515&postcount=2](http://ubuntuforums.org/showpost.php?p=4065515&postcount=2).

BTW how is Ubuntu on g73jw-a1, any issues besides video?


I got to say that this thread is still very useful. I followed the guide and have a fully functional system with latest drivers that survived several Kernel updates on 10.10.  Big thanks to the OP!!!!

Thanx, I dont tink that the drivers in the Repos are any different from the Nvidia ones, same version so, I wont revert. Yeah for me too, several kernel changes on 10.10 and never even noticed it :) 

G73JW-A1 works great other than the video as you said and well, the subwoofer is not yet detected but I think it is more of a sound chip that does not have a driver yet than anything else  :)

It is a beast andraw performances are awesome.... Heat is dissipated really efficiently. Even if you make it run an hour or 2 at full performance (intense gaming session lets say), you will notice a slight increase in temperature when you have it on your lap but, really really small one...

---

### Post by Cavsfan on 2011-03-31
I just upgraded my nvidia geforce 9800 gt with default Lucid drivers (195 something) to the latest driver released this month - version 260.19.44

I went by these [[COLOR=blue]_instructions on how to install it._[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html") (This has worked for me in the past)

Then I went by the instructions on page one of this tutorial for future kernels. Which by the way is great!!!

I guess I am good to go, however I noticed on the [[COLOR=blue]_driver download page_[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us") in the _README_ section under _Additional information_ there were instructions on updating it.

Guess I'll find out when a new kernel is installed. I love surprises - NOT.

---

### Post by Cavsfan on 2011-03-31
Had to jump through several hoops to get my **NVIDIA X Server Settings** back under **System** > **Preferences**.
And then a few more hoops to get the icon back like it was, but what the heck, it was fun!

Now I am back to cooking with gas! :guitar:

---

### Post by Cavsfan on 2011-04-22
Just thought I would mention this: in order to update the nvidia driver to the newest one (like I just did) you need to 
uninstall the previous version and manually install the new one first. Then update the nvidia-driver mentioned on page one.
Subsequent kernels that are installed will then be updated with this new driver.

I updated to driver 270.41.06 which was released 2 days ago on 2011.04.20.
These instructions as I mentioned above were used to install the newest driver: [[COLOR=blue]_Installing a new driver._[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")

Since I had already blacklisted the files listed on that site, all I had to do was step 4 through 8 on the site above.

And before moving the new driver into /usr/src as page one describes, I first deleted both the **old driver** and **nvidia-driver** 
from /usr/src and then redid the commands on page one with the new driver name.

I also purged the 2 kernels I had and re-installed them. It was pretty sweet to see that after it displayed 
**Building NVIDIA driver for kernel blah, blah blah**, It displayed **SUCCESS: Driver installed for kernel blah, blah blah**

EDIT: Forgot to mention that this is a pretty nice HOWTO! Thanks!

---

### Post by iowabeakster on 2011-04-23
I'm a total newbie, and a computer incompetent.

I did manage to manually install the driver after this last kernel update (without my brother's help!).  And I've installed the script from this tutorial.  I want to see if I did it correctly.

The test provided in the first post is long obsolete.  Can anybody provide a couple command lines for a test kernel install (and then restore back to where I am)?

---

### Post by Cavsfan on 2011-04-25
> **iowabeakster said:**
> I'm a total newbie, and a computer incompetent.

I did manage to manually install the driver after this last kernel update (without my brother's help!).  And I've installed the script from this tutorial.  I want to see if I did it correctly.

The test provided in the first post is long obsolete.  Can anybody provide a couple command lines for a test kernel install (and then restore back to where I am)?

I am not sure what kernels you could use for Maverick but for Lucid these are how I removed and reinstalled the kernel to test this script:
These commands delete the kernel:
```
sudo apt-get purge linux-headers-2.6.32-31 linux-headers-2.6.32-31-generic linux-image-2.6.32-31-generic
```These commands reinstall the kernel:
```
sudo apt-get install linux-headers-2.6.32-31 linux-headers-2.6.32-31-generic linux-image-2.6.32-31-generic
```**uname -r** will tell you the name of the kernel you are using.

```
cavsfan@cavsfan-desktop:~$ **uname -r**
2.6.32-31-generic
```You could take the output of the command above and look in Synaptic and verify the exact name of the 3 parts of the kernel.

These are the 3 parts of my kernel:
[B]linux-headers-2.6.32-31 
linux-headers-2.6.32-31-generic 
linux-image-2.6.32-31-generic[/B]

You really have to be careful with this as you probably already know. These are simply suggestions and what worked for me. 

Also, be aware that if you are using a modified Grub like the one in the tutorial in my sig. that whichever kernel is installed latest 
becomes the "current" kernel, not the highest numbered kernel.
So, if you remove and reinstall an older kernel than the latest one, you would be using the older one once you rebooted.

It is best to do this in a terminal so that you can hopefully see the "**SUCCESS: Driver installed for kernel blah blah blah**" message and know you are good.

---

### Post by iowabeakster on 2011-04-27
Awesome.  Thanks a million.  I'll give it a go soon.  We're using the same kernel.

---

### Post by iowabeakster on 2011-04-27
I forgot to switch to a different kernel when I did the above test (like I said, I'm a computer incompetent).

So, when I gave the command to reinstall the kernel, it gave me the message that the driver was already installed (from the auto-update script).  So, I take it that it should've worked (except for my incompetence).

Then, I checked and found that there was a newer driver available from NVIDIA.  I tried my best to uninstall the old driver.  When I went to install the updated driver... I got several dozens of errors.  I just kept hitting "OK".  In the end, it appears that it did install and is working correctly.  WOO HOO!

I've now updated the symbolic link and placed the updated driver in usr/src.  I figure that is enough for today.  I'll wait for the next kernel update, to make sure it works.

---

### Post by Cavsfan on 2011-04-28
> **iowabeakster said:**
> I forgot to switch to a different kernel when I did the above test (like I said, I'm a computer incompetent).

So, when I gave the command to reinstall the kernel, it gave me the message that the driver was already installed (from the auto-update script).  So, I take it that it should've worked (except for my incompetence).

Then, I checked and found that there was a newer driver available from NVIDIA.  I tried my best to uninstall the old driver.  When I went to install the updated driver... I got several dozens of errors.  I just kept hitting "OK".  In the end, it appears that it did install and is working correctly.  WOO HOO!

I've now updated the symbolic link and placed the updated driver in usr/src.  I figure that is enough for today.  I'll wait for the next kernel update, to make sure it works.

You could have just removed the kernel and then reinstalled it. But, it sounds like you are good to go. Glad you got it to work.
I have messed my system up messing with kernels before, so I am glad you got the new driver installed.

I had to go by the instructions in my previous post to uninstall the old driver before installing the newer one. [[COLOR=blue]_Installing a new driver._[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")
You have to print out step 4 through 8 or else your system will be messed up.
Then I updated the script after that. Are you running on the new driver?
If so, you could test the script by uninstalling the kernel and then reinstalling it and if you see the **SUCCESS: Driver installed for kernel blah, blah blah** message you know you are good to go.

---

### Post by iowabeakster on 2011-04-29
Yep, I'm running on the new driver.  Script is in place, and working as it should.

Thanks for the help.

---

### Post by iowabeakster on 2011-05-01
Well, I updated to 10.10 yesterday.

I saw during the installation process, I saw the "SUCCESS driver has been installed for this kernel" message (or whatever exactly is says).

It fired up correctly (1600x900 res), the NIVIDA xserver said that the correct driver (new updated one) was installed.  Everything seemed perfect, until I tried to start FlighGear flight simulator.  Then I tried another game.  Both had problems, and were not functional.

I installed the driver manually, and both games started working again.  I have a feeling that some 32 bit compatibilities were left out with the automatic driver install.  I get a prompt during a manual install that asks if I want to install the 32 bit stuff.

Oh well, I am getting more proficient every day.

---

### Post by iClouseau88 on 2011-05-02
Hi,

First of all, how do I manually install proprietary Nvidia drivers in Natty?

Thnaks for your help.

---

### Post by iowabeakster on 2011-05-02
Is natty different than any other release?

I just made the jump to maverick.

But, this is what I've been doing.

Kill the xserver

 ```
sudo /etc/init.d/gdm stop
```

Login as root.

Change to directory where you have your driver.

```
cd /path/to/directory/with/NVIDIA-whatever.whatever.run
```Make it executable

```
chmod +x NVIDIA-whatever.whatever.run
```Install it

```
sh NVIDIA-whatever-whatever.run
```reboot

---

### Post by Cavsfan on 2011-05-03
You have to blacklist some files. This is mentioned on a previous post of mine, a link called "Installing new drivers".

However, my system became totally unstable several days ago and I had to do another clean install with Lucid 10.04.2.
Don't think it was the driver. I don't know what it was but, leaving everything default this time.
So, I have the default Lucid nVidia driver 195.36.24.

---

### Post by Cavsfan on 2011-06-24
Sweet! I just updated the nVidia driver to 275.09.07!  My 28' monitor had stopped waking from sleep and had to RMA it.
Luckily it was 2 yrs old and had a 3 yr warranty and a 4th year I had also purchased.
I was using a 17" monitor as back up and that was about to kill me.

So, When I got the gargantuan monitor back the other day, I thought I would update. (My TV is only 36"!)

I went by these [[color=blue]_instructions on how to install it._[/COLOR]](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)
But, since I could not uninstall the previous version, when I dropped into the console via safe mode, it said I needed 
to enter "telinit3" to be in the right mode. Everything worked well after that.

Then I went by this tutorial to prepare for the future and it still works great!

I just used these 4 commands afterward to test it. One to remove the previous kernel and the next to re-install and 
look for the message **SUCCESS: Driver installed for kernel blah, blah blah...**

I have the 2 most recent kernels for Lucid:

```
sudo apt-get purge linux-headers-2.6.32-31 linux-headers-2.6.32-31-generic linux-image-2.6.32-31-generic
sudo apt-get install linux-headers-2.6.32-31 linux-headers-2.6.32-31-generic linux-image-2.6.32-31-generic

sudo apt-get purge linux-headers-2.6.32-32 linux-headers-2.6.32-32-generic linux-image-2.6.32-32-generic
sudo apt-get install linux-headers-2.6.32-32 linux-headers-2.6.32-32-generic linux-image-2.6.32-32-generic
```

Oh, the remove command for the 32 kernel above removed 4 files. **linux-headers-generic** was not automatically reinstalled.
I installed in via synaptic under missing recommends.

Note: the last kernel you install will be the "current one" not the one with the highest number. So, I did the 31 kernel and then the 32 kernel.

---

### Post by gillza on 2011-10-02
This script still works for 11.04

I installed the new drivers and this script (following an advanced version of manual install in the post above) on my new and shiny G53SX-A1

Thank you author and all those who participated in this thread :)

---

### Post by Cavsfan on 2011-10-03
I upgraded to a newer nVidia driver the other day and could not get this to update the kernels.
Then I thought DUH! I had to manually install the newer driver first and then this worked to update the kernels.

So, it is a 2 step process if upgrading the driver to a newer version. Simply updating this script did not do the trick.

But, this is a very handy **HowTo** as it apparently works with any version of Ubuntu.

---

### Post by gillza on 2011-10-03
um not completely correct. The script installs the driver after the kernel update. it checks if the driver module is present and if not installs the driver you linked before the script. so if you link the new driver 

sudo mv new_driver.run /usr/src
sudo ln -s /usr/src/new_driver.run /usr/src/nvidia-driver

the script will install it when kernel is next updated.

---

### Post by Cavsfan on 2011-10-03
> **gillza said:**
> um not completely correct. The script installs the driver after the kernel update. it checks if the driver module is present and if not installs the driver you linked before the script. so if you link the new driver 

sudo mv new_driver.run /usr/src
sudo ln -s /usr/src/new_driver.run /usr/src/nvidia-driver

the script will install it when kernel is next updated.

It was not a kernel update, it is always a new kernel install and it does not work.

I tried all of that 7 or 8 times at least. It did not work. I tried the same thing many times in the past. Each time it did not work.
I gave up and just manually installed the new driver and then updated the script and then it finally worked.

If it worked for you, fine. It did not work for me and I know what I am doing.
I was almost left with an unbootable Ubuntu system (windows 7 would have still been fine).

I believe the whole key here is "new kernel" versus "updated kernel"
I will do the same in the future.

---

### Post by gillza on 2011-10-03
by updated kernel i meant new kernel :)
Strangely it does work for me. I can update the driver manually ofcourse or just drop it into /usr/src, link it and wait for new kernel if im lazy. Well I hope the issue resolves itself.

Good luck!

---

### Post by gillza on 2011-10-04
Hmm, don't know if it has anything to do with the drivers but after I installed them my few working function keys on G53sx-a1 (like brightness) stopped working. Worked without the driver (before installing the driver and tried live cd after install).

---

### Post by Cavsfan on 2011-10-06
> **gillza said:**
> by updated kernel i meant new kernel :)
Strangely it does work for me. I can update the driver manually ofcourse or just drop it into /usr/src, link it and wait for new kernel if im lazy. Well I hope the issue resolves itself.

Good luck!

While trying to simply update the script with the new driver, it kept saying FAILURE when re-installing the kernel. 
But, I finally found one of the files had a broken link.  I cannot recall which one, but I guess it doesn't work like it should for me. 
I have a Geforce 9800GT.  I go by the instructions to install a new driver, then re-create the stuff from this tutorial.

Hope you get your other issue resolved.

---

### Post by Cavsfan on 2011-10-26
I think I figured out why I couldn't update this script last time I installed a new driver.
DO'H! When all else fails - read the instructions.

I didn't remove the 2 files - old driver and the nvidia-driver files from /usr/src/ prior to putting the new ones there.

I just installed 285.05.09 for my Geforce 9800GT. Everything looks sweet. 

This is still a great HOWTO! :guitar:

---

