---
title: "&quot;VirtualBox kernel driver not installed&quot; error after Hardy upgrade"
date: 2008-03-27
forum: Virtualisation
---

### Post by omegamormegil on 2008-03-27
Just wanted to let anyone else having this problem know that  you need to install your kernel headers to correct this problem.  You can install the correct headers for your system via the terminal with this command: "sudo aptitude install linux-headers-$(uname -r)" followed by this command to install the vbox kernel driver: "sudo /etc/init.d/vboxdrv setup"

I found this information in this thread, courtesty of bodhi.zazen: [http://www.ubuntu-forums.com/showthread.php?t=458494](http://www.ubuntu-forums.com/showthread.php?t=458494)  I happen to be running the PUEL version, but I believe this information would also pertain to the FOSS version.

---

### Post by mlissner on 2008-04-20
> **omegamormegil said:**
> Just wanted to let anyone else having this problem know that  you need to install your kernel headers to correct this problem.  You can install the correct headers for your system via the terminal with this command: "sudo aptitude install linux-headers-$(uname -r)" followed by this command to install the vbox kernel driver: "sudo /etc/init.d/vboxdrv setup"

I found this information in this thread, courtesty of bodhi.zazen: [http://www.ubuntu-forums.com/showthread.php?t=458494](http://www.ubuntu-forums.com/showthread.php?t=458494)  I happen to be running the PUEL version, but I believe this information would also pertain to the FOSS version.

Hmmmm..this didn't work for me. I am still getting an error saying that I don't have a suitable module for the kernel. I am using the RC1 of Hardy.

EDIT: I figured out how to get this to work. Per the bug here: [https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/214393](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/214393), it appears that I had installed kernel specific modules rather than modules that would update when I updated the machine. 

The solution was to run ```
sudo aptitude install virtualbox-ose-modules-generic
```

That's apparently the metapackage, and it fixed my issues (with a score of -241).

---

### Post by lnicolao on 2008-04-20
> **mlissner said:**
> Hmmmm..this didn't work for me. I am still getting an error saying that I don't have a suitable module for the kernel. I am using the RC1 of Hardy.

EDIT: I figured out how to get this to work. Per the bug here: [https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/214393](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/214393), it appears that I had installed kernel specific modules rather than modules that would update when I updated the machine. 

The solution was to run ```
sudo aptitude install virtualbox-ose-modules-generic
```

That's apparently the metapackage, and it fixed my issues (with a score of -241).

Great find! Thanks for posting this. I was having the same problem.

---

### Post by diablo75 on 2008-04-20
Appears I should have caught this thread an hour ago before I tried to fix this on my own.  I selected the 386 kernel instead of the generic, and my video would crash after reboot, unless I punched Grub and selected the generic kernel out of the list....  Got it fixed though (fresh system, so I just formatted the HD again because I'm short on time to sit and tinker around).

---

### Post by ale3andro on 2008-04-26
That worked for me too. Thanks.

---

### Post by lunadesign on 2008-04-30
> **mlissner said:**
> 
EDIT: I figured out how to get this to work. Per the bug here: [https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/214393](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/214393), it appears that I had installed kernel specific modules rather than modules that would update when I updated the machine. 

The solution was to run ```
sudo aptitude install virtualbox-ose-modules-generic
```

That's apparently the metapackage, and it fixed my issues (with a score of -241).

Perfect! 
Thanks,
Andrew

---

### Post by bigtel on 2008-05-01
I had the same issue after upgrading - I will try the fix tonight - Thanks

---

### Post by lik3n on 2008-05-01
This did not work for me. I guess I'm the odd man out. :-/

---

### Post by mlissner on 2008-05-01
> **lik3n said:**
> This did not work for me. I guess I'm the odd man out. :-/

If you post your error messages, maybe we can help? 
 
[FONT=arial,sans-serif]
[/FONT]

---

### Post by RowanC on 2008-05-03
I have the same problem today after upgrading the kernel version to .17, tried installing the virtualbox-ose-moduels-generic package, but it doesn't look like there is an up-to-date package available.
Also tried to /etc/init.d/vboxdrv start in case that method worked for me (my kernal headers seem to be installed, heck I'll try anything) but it returned the following error:
```
* Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.

```
and I was just getting to like the fact that I could use other OS under ubuntu....

---

### Post by mlissner on 2008-05-03
What was the error message when you tried to install virtualbox-ose-modules-generic? Do you have all of the repos enabled?

EDIT: I also just found this blog entry by an author that usually figures things out that are far above my abilities. I'll betcha it will work: [http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/)

---

### Post by RowanC on 2008-05-04
Thanks for your reply :-)

I received no error message when I installed the generic modules, synaptic worked fine, and the dependencies also seem good (when I tried to remove module....16 it now lists the generic modules for removal)
However the same error message still occurs in virtualbox:

```
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```

However, as a workaround, if I reboot into the .16 kernel version, it works a treat.

I'm not sure I want to go via the method that blog used for vmware, I figure for now I'm happy to stay with the .16 kernel version when I know I'm going to need virtualbox....but it will be nice when the new modules version comes through the repo's (assuming this is the case....)
Cheers.

---

### Post by OldTimeTech on 2008-05-04
Read in another forum that if you upgraded to .17 that it is only a proposed upgrade and that you need to uncheck on your repositories page the hardy proposed...because .17 is not ready for prime time yet.

---

### Post by RowanC on 2008-05-06
Genius!!! Didn't even know it was checked. Big Time thanks - hopefully this will solve future possible conflicts too :-)

---

### Post by hodenkat on 2008-05-21
I don't even know why they offer virtualbox in add/remove programs since it's broken and takes days to fix. What a pain in the ***. I've wasted so much time trying to get any virtualbox to work it's become easier to wipe my system clean and set up a dual boot!

---

### Post by mlissner on 2008-05-21
> **hodenkat said:**
> I don't even know why they offer virtualbox in add/remove programs since it's broken and takes days to fix. What a pain in the ***. I've wasted so much time trying to get any virtualbox to work it's become easier to wipe my system clean and set up a dual boot!

Strange. It's really not that bad. I installed it without too much trouble at all. I had some issues updating it, since I didn't have the right kernel modules, but otherwise, all is well. 

Anyway, dual booting causes many headaches too. I'd much rather virtualize anyday.

---

### Post by RowanC on 2008-05-21
> **hodenkat said:**
> I don't even know why they offer virtualbox in add/remove programs since it's broken and takes days to fix. What a pain in the ***. I've wasted so much time trying to get any virtualbox to work it's become easier to wipe my system clean and set up a dual boot!

Now that I've got it going, (unchecking the proposed upgrades has made a world of difference, (and the fact that the .17 module is now available in proposed) and it really only took an hour). I love it, it's so much easier than dual booting, which I've usually done in the past, and gives me a lot more flexibility.

Only wish I'd chosen dynamic HD rather than static when setting up my other OS, as now, if I want to completely back it up, it takes up way too much room.

I'd almost be dissapointed if everything just worked, it's sometimes only by fixing things that you learn how they work.

---

### Post by joeriben on 2008-05-27
Hi all,

I'm a ubuntu newbie having the same problem. Which packets do I have to uninstall exactly? Is it

linux-image-2.6.24-17-generic AND
linux-ubuntu-modules-2.6.24-17-generic?

Thanks for your help.

---

### Post by RowanC on 2008-05-27
For a while I just used grub when booting (esc at bootup) to choose kernel .16, which was fine, but now the .17 module for virtualbox is under hardy proposed, so if you tick that box in your sources, it'll be there....and it'll mean you won't have to uninstall .17....I did this, but I havn't really considered the consequences of having half the system with proposed updates, and half without.... (after installing the virtualbox module, you could untick the proposed updates).

---

### Post by joeriben on 2008-05-27
Thanks, that did it. I did not have the "proposed" packages activated in synaptic.

Best
Benjamin

---

### Post by jbirdjavi on 2008-05-27
Yeah same problem here.  The 17 kernel that I installed came from hardy-updates.  But Virtualbox doesn't yet have an updated kernel module.  Guess I'll be booting into 16 until that time...

---

### Post by ivze on 2008-05-27
Kernel module may also be obtained by compiling it from sources (that exist in the repository - search for "virtualbox" in synaptic). For me that worked fine.

---

### Post by ubuntism on 2008-05-27
but how do i compile it then? :)

---

### Post by _angel__ on 2008-05-27
I got the same problem after today's kernel update. Reinstall virtualbox solved it.

---

### Post by destiney on 2008-05-27
Try this:

[http://destiney.com/blog/virtualbox-no-workie-after-kernel-upgrade](http://destiney.com/blog/virtualbox-no-workie-after-kernel-upgrade)

---

### Post by ubuntism on 2008-05-27
> **destiney said:**
> Try this:

[http://destiney.com/blog/virtualbox-no-workie-after-kernel-upgrade](http://destiney.com/blog/virtualbox-no-workie-after-kernel-upgrade)

That's a good one. Although, i wish they'd make sure it works before releasing the kernel to the public.

Edit: Disclaimer: I haven't actually tried the proposed solution, but it looks like a good one. A temporary fix until the real one is released. I went with the "boot into the old kernel"-option, which is alot easier. :)

---

### Post by ubuntism on 2008-05-28
Shows over. It works now. Just upgrade from the repository. Thanks ubuntu people. Whoever you all are, thanks.

---

### Post by michaelzap on 2008-05-28
> **ubuntism said:**
> Shows over. It works now. Just upgrade from the repository. Thanks ubuntu people. Whoever you all are, thanks.

THANKS for posting this! I was pulling my hair out trying to get this to work right now and if I hadn't seen your post I never would've looked for another update since I booted this morning. Now I just need to log out and back in for the change to take effect...

---

### Post by michaelzap on 2008-05-28
> **michaelzap said:**
> THANKS for posting this! I was pulling my hair out trying to get this to work right now and if I hadn't seen your post I never would've looked for another update since I booted this morning. Now I just need to log out and back in for the change to take effect...

Er... I didn't read the VirtualBox error message that carefully, but it did also say that I should add my user to the virtualbox user group (which I hadn't done, since this was a fresh install and I didn't pay attention). So of course THAT was why I needed to log out and back in...

Once I applied the kernal driver update, added myself to the virtualbox user group, and logged out and back in, my virtual machine worked again.

---

### Post by nunki on 2008-05-28
I had the 64bit deb installed and got this same error this morning after the upgrade. I just ran
```

sudo dpkg-reconfigure virtualbox

```

Seemed to clear the problem up.

---

### Post by aks2008 on 2008-05-29
I agree with _angel__. For my closed source virtualbox version reinstalling from sun site deb package solved the problem. It didn't affect my machines.
thanks _angel__.

---

### Post by ColdFusionEESG on 2008-06-03
> **mlissner said:**
> Hmmmm..this didn't work for me. I am still getting an error saying that I don't have a suitable module for the kernel. I am using the RC1 of Hardy.

EDIT: I figured out how to get this to work. Per the bug here: [https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/214393](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/214393), it appears that I had installed kernel specific modules rather than modules that would update when I updated the machine. 

The solution was to run ```
sudo aptitude install virtualbox-ose-modules-generic
```

That's apparently the metapackage, and it fixed my issues (with a score of -241).

Thanks!!

---

### Post by bmoney80 on 2008-06-04
> **omegamormegil said:**
> Just wanted to let anyone else having this problem know that  you need to install your kernel headers to correct this problem.  You can install the correct headers for your system via the terminal with this command: "sudo aptitude install linux-headers-$(uname -r)" followed by this command to install the vbox kernel driver: "sudo /etc/init.d/vboxdrv setup"

I found this information in this thread, courtesty of bodhi.zazen: [http://www.ubuntu-forums.com/showthread.php?t=458494](http://www.ubuntu-forums.com/showthread.php?t=458494)  I happen to be running the PUEL version, but I believe this information would also pertain to the FOSS version.

Thanks a lot man ... worked perfectly.

Ben

---

### Post by benhur99ph on 2008-06-04
> **_angel__ said:**
> I got the same problem after today's kernel update. Reinstall virtualbox solved it.

Yep! This solved it for me. Just did a quick reinstall of Virtualbox. But I opted to remove my virtual machines first -- just to be sure. Hehe. Anyway, it worked out fine. Thanks!

---

### Post by OBE1 on 2008-06-04
**For those of you that tried the fix suggested in the popup box and still cannot launch your VB Machines - try this fix suggested in the User Manual (see below)**

  sudo dpkg-reconfigure virtualbox

I tried all the other suggestions - this worked for me.   

Here's the output you should see:


warden@Chino:~$ sudo dpkg-reconfigure virtualbox again.
 * Stopping VirtualBox kernel module                                             *  done.
 * Shutting down VirtualBox host networking                                      *  done.
addgroup: The group `vboxusers' already exists and is not a system group. Exiting.
Messages emitted during module compilation will be logged to /var/log/vbox-install.log.
Success!
 * Starting VirtualBox kernel module                                             *  done.
 * Starting VirtualBox host networking                                           *  done.



HAPPY UBUNTU-ING!:)

---

### Post by grem91 on 2008-06-04
Please Help. I have tried all sorts to get it working.

I put:

sudo dpkg-reconfigure virtualbox

into the terminal, and got this back:

Package `virtualbox' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: virtualbox is not installed.

And VirtualBox IS installed.

---

### Post by arak on 2008-06-04
Had the same problem.  Just reinstall Virtualbox.  You don't lose your data.

---

### Post by grem91 on 2008-06-04
Nevermind, I uninstalled and downloaded the .deb version from Sun's website and that works. Thanks anyway.

---

### Post by buntunub on 2008-06-04
Same issue here and none of the posted "fixes" work for me. Do we have to go through this with each kernel upgrade??

Cant one of the upstream guys coordinate getting the new virtualbox kernel module into the same upgrade like they do with the restricted-modules??

Come on guys!

---

### Post by vexorian on 2008-06-04
> **grem91 said:**
> Please Help. I have tried all sorts to get it working.

I put:

sudo dpkg-reconfigure virtualbox

into the terminal, and got this back:

Package `virtualbox' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: virtualbox is not installed.

And VirtualBox IS installed.
Yes this works, reinstalling works because it does exactly that.

You can use synaptic (GUI) as well, open synaptic, find the installed "virtualbox" package then go to the "package" menu and click "configure..."

---

### Post by mariuss on 2008-06-05
> **grem91 said:**
> Please Help. I have tried all sorts to get it working.

I put:

sudo dpkg-reconfigure virtualbox

into the terminal, and got this back:

Package `virtualbox' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: virtualbox is not installed.

And VirtualBox IS installed.

Got the same error, you probably are using the OSE version, in which case the command is:
> sudo dpkg-reconfigure virtualbox-ose

Anyhow, this did not solve the problem, getting "No suitable module for running kernel found."

---

### Post by Paresh on 2008-06-05
When I run 
> sudo dpkg-reconfigure virtualbox-ose
I also get "No suitable module for running kernel found."

I have also tried uninstalling through synaptic, but this made no difference.

I had the same problem with v17 of the kernel a few days ago and had to wait for the vbox guys to update the repository.  Hopefully it won't be too long before they do it for V18.

---

### Post by buntunub on 2008-06-05
> **Paresh said:**
> When I run 

I also get "No suitable module for running kernel found."

I have also tried uninstalling through synaptic, but this made no difference.

I had the same problem with v17 of the kernel a few days ago and had to wait for the vbox guys to update the repository.  Hopefully it won't be too long before they do it for V18.

Yes, exactly, the issue is the Ubuntu guys do these kernel updates without coordinating it with the virtualbox-ose guys (I guess), so that the new vboxdrv module will come along with the updates, exactly like with the restricted-module for Nvidia or ATi. Really shoddy imo, but its free, so who's to complain?

---

### Post by buntunub on 2008-06-06
Anyone know the status on the fix for this? Perhaps a bug report might be in order here?

---

### Post by spandanj on 2008-06-07
so, hardy updated its kernel to 2.6.24-**17** to 2.6.24-**18**. But, they didn't update the virtualbox-ose-module-generic to 2.6.24.18. thus, it is still stuck in "**17**" while kernel is "**18**".

I am not going through the hassle of uninstalling VBox from synaptic and installing from source from VBox website....OK! so when do we get the updated Vbox module in synaptic?

---

### Post by buntunub on 2008-06-07
[This]("https://answers.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+question/33296") worked for me. This should work on a previously working version. If that does not work then you will probably need to reinstall or wait for the new module. Here is the recap of it.


>  drkitty said 8 hours ago:

See x7y7 and Ronny under bugs - This works!

sudo apt-get install virtualbox-ose-source
sudo m-a update
sudo m-a prepare
sudo m-a a-i virtualbox-ose
sudo /etc/init.d/vboxdrv restart

---

### Post by spandanj on 2008-06-07
that worked for me too...

1 complication was that the audio stopped working. i changed the audio driver from ALSA to pulse in Vbox. that solved the sound.

however, had ubuntu repos were updated in coordination - it would have prevented such unwanted hassle to ubuntu users.

---

### Post by BlackDragonBE on 2008-06-07
I just installed the deb package from their site, worked like a charm.

Cheers

---

### Post by tenmoi on 2008-06-07
all of you could have saved tons of your time if you had downloaded the deb file from virtualbox.org or sun.com. The deb file will just compile a kernel module so every time you upgrade the linux kernel all you have to do is to click on the deb file and you're ready to go.

on the sun website there is already a deb file for hardy, which does a better job of allowing you to install ubuntu servers.

---

### Post by spandanj on 2008-06-07
to tenmoi, and else,


Yes, deb package from Vbox website works like charm, except you gotta reinstall after every kernel that may disrupt the program.

To AVOID this hassle of reinstalling, and establish a sort of compatibility of Vbox and other software with newer updates of ubuntu---T H A T is the goal of automatic update conducted by synaptic. so that, auto updating will update not only the operating system, but also the softwares on it. I have been proud of this fact for ubuntu so far.

Until now. This is my first experience that a software has stopped workign after an update.

---

### Post by vexorian on 2008-06-07
with the deb file you only need to reconfigure it, not reinstall it.

This must be a heads up to the packagers of virtual-box-OSE, anyway, ubuntu users that don't want the hassle may just use the older kernel when they intend to use virtualbox.

---

### Post by buntunub on 2008-06-07
Virtualbox from SUN is NOT the Open Source Edition, aka it is not free software under the terms of the GPL. Some of us like to use Free Software with the Source Code being open and free to modify and redistribute without restrictive licensing agreements involved. Besides, the only real problem we have here is that the Ubuntu devs are not properly packaging and releasing kernel mods correctly. They do a good job (finally) of preparing the restricted-modules with it, but they are not including the virtualbox modules.

---

### Post by mariuss on 2008-06-07
The other thing to keep in mind is that by installing random .debs you may run into problems when you upgrade your system. Always try first to install from the official repositories.

If the software you are looking for has a slightly older version in the official repository (as opposed to a downloadable .deb or a third party repository) then ask yourself if you really need the extra features or bug fixes in the newer version. If not, then stick with the official one, in a few months you can upgrade your whole system and you will most likely get that newer version anyhow.

That being said, the [closed source edition of VirtualBox]("http://www.virtualbox.org/wiki/Downloads") does have some nice extra features you may need, like USB support:
[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

Just make sure you know what you are doing.

---

### Post by buntunub on 2008-06-07
We, as the virtualbox using community, need to start raising some noise about this issue to Canonical as well - not just about the kernel update issue as it affects us, but also about the apparent lack of QA involved when they throw kernel updates about willy nilly as they have over the last couple of weeks. Obviously, kernel updates should and very much need to be exhaustively tested prior to upstream release due to their critical nature.

---

### Post by mariuss on 2008-06-07
> **buntunub said:**
> We, as the virtualbox using community, need to start raising some noise about this issue to Canonical as well - not just about the kernel update issue as it affects us, but also about the apparent lack of QA involved when they throw kernel updates about willy nilly as they have over the last couple of weeks. Obviously, kernel updates should and very much need to be exhaustively tested prior to upstream release due to their critical nature.

Good point. What can be done?

Is there a Launchpad issue opened for this? If there was, we could direct all users with problems there to add their comments.

---

### Post by oscuro on 2008-06-07
I still can not get this to work, I have tried everything here. Still no good. Hardy is my first run with Ubuntu. I am a noob to linux. Any help would be great thanks

---

### Post by mariuss on 2008-06-07
> **oscuro said:**
> I still can not get this to work, I have tried everything here. Still no good. Hardy is my first run with Ubuntu. I am a noob to linux. Any help would be great thanks

You have two options:

[LIST=1]
[*]**Boot a previous kernel** - reboot and right after the BIOS screen you will see a message about hitting 'Esc' in order to get into the Grub menu; do that and select the previous kernel, that would be "2.6.24-17 generic".
[*]**Download and install the closed source version** - first uninstall all virtualbox-ose* packages and then [download and install VirtualBox 1.6.2]("http://www.virtualbox.org/wiki/Downloads"). You will probably have to add yourself to the vboxusers group and then logout/login.
[/LIST]

I would say, stick with option 1 and hopefully in a few days this will be fixed.

---

### Post by oscuro on 2008-06-07
> **mariuss said:**
> You have two options:

[LIST=1]
[*]**Boot a previous kernel** - reboot and right after the BIOS screen you will see a message about hitting 'Esc' in order to get into the Grub menu; do that and select the previous kernel, that would be "2.6.24-17 generic".
[*]**Download and install the closed source version** - first uninstall all virtualbox-ose* packages and then [download and install VirtualBox 1.6.2]("http://www.virtualbox.org/wiki/Downloads"). You will probably have to add yourself to the vboxusers group and then logout/login.
[/LIST]

I would say, stick with option 1 and hopefully in a few days this will be fixed.


I have booted to 16 and 17 and can not get it to work there either....says the kernel driver is not installed.

---

### Post by mariuss on 2008-06-07
> **oscuro said:**
> I have booted to 16 and 17 and can not get it to work there either....says the kernel driver is not installed.

OK, then boot into 17 and then run this command:
```
sudo dpkg-reconfigure virtualbox-ose
```

If this will not work, then I have no clue, sorry. Try downloading the closed source version then.

---

### Post by buntunub on 2008-06-07
> **oscuro said:**
> I have booted to 16 and 17 and can not get it to work there either....says the kernel driver is not installed.

Check out the Virtualbox wiki on Community Docs. Its pretty strait forward.

As far as what can be done, I think we all need to start hitting up launchpad with bug reports and validations about this. Also, not sure if there is an official channel to get through to Canonical or not, but we might check that out as well.

---

### Post by oscuro on 2008-06-07
> **mariuss said:**
> OK, then boot into 17 and then run this command:
```
sudo dpkg-reconfigure virtualbox-ose
```

If this will not work, then I have no clue, sorry. Try downloading the closed source version then.

root@kirk-laptop:/home/kirk# dpkg-reconfigure virtualbox-ose
 * Shutting down VirtualBox host networking...                           [ OK ] 
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Starting VirtualBox host networking...                                [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.
root@kirk-laptop:/home/kirk#

---

### Post by mariuss on 2008-06-07
I was getting this "No suitable module for running kernel found." error with 18, but not with 17. Make sure all the required packages are installed, as per the [Community Ubuntu Documentation]("https://help.ubuntu.com/community/VirtualBox#head-c93d71cad123a3c70e4fa883e531ea85bdebb416").

---

### Post by oscuro on 2008-06-07
I got it working, I had to remove the modules, then install them again, then reconfigure and it worked.

---

### Post by buntunub on 2008-06-07
> **oscuro said:**
> I got it working, I had to remove the modules, then install them again, then reconfigure and it worked.

It works on the -18 kernel?

---

### Post by oscuro on 2008-06-07
> **buntunub said:**
> It works on the -18 kernel?

No sorry the 17

---

### Post by mvanlint on 2008-06-08
Hi,

After upgrading the kernel, the error "VirtualBox kernel driver not installed" appeared.

At the Virtual Box forum I found the following solution to be successful:

sudo rm /etc/vbox/vbox.cfg
sudo /etc/init.d/vboxdrv setup

[http://www.virtualbox.org/ticket/1613](http://www.virtualbox.org/ticket/1613)

Michel

---

### Post by bark50 on 2008-06-08
This guy has a solution that some have apparently found successful for the Virtualbox-ose:  http://mcb.lessthanthree.se/?p=26[/url]

I haven't tried it, though.  I'll wait for the fix to show up in the repository.

---

### Post by tenmoi on 2008-06-10
> **spandanj said:**
> to tenmoi, and else,


Yes, deb package from Vbox website works like charm, except you gotta reinstall after every kernel that may disrupt the program.

, and establish a sort of compatibility of Vbox and other software with newer updates of ubuntu---T H A T is the goal of automatic update conducted by synaptic. so that, auto updating will update not only the operating system, but also the softwares on it. I have been proud of this fact for ubuntu so far.

Until now. This is my first experience that a software has stopped workign after an update.

"To AVOID this hassle of reinstalling" you RUN INTO the hassle of WAITING FOR A NEW KERNEL.

I think no one should be afraid of compiling software on Linux, especially when all you have to do is to CLICK one or two times. And being less dependent is why one switches to Linux.

---

### Post by qbox on 2008-06-12
qbox@qbox:~/Desktop$ sudo dpkg -i virtualbox_1.6.2-31466_Ubuntu_hardy_amd64.deb
(Reading database ... 170625 files and directories currently installed.)
Unpacking virtualbox (from virtualbox_1.6.2-31466_Ubuntu_hardy_amd64.deb) ...
dpkg: error processing virtualbox_1.6.2-31466_Ubuntu_hardy_amd64.deb (--install):
 trying to overwrite `/lib/modules/2.6.24-16-rt/misc/vboxdrv.ko', which is also in package virtualbox-ose-modules-2.6.24-16-rt
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 virtualbox_1.6.2-31466_Ubuntu_hardy_amd64.deb
qbox@qbox:~/Desktop$ sudo dpkg-reconfigure virtualbox
/usr/sbin/dpkg-reconfigure: virtualbox is not installed
qbox@qbox:~/Desktop$ 

I can't RUN this
Any help

---

### Post by osx on 2008-06-14
It's been posted a couple of times already, but mixed in with other "fixes" so it can be easy to miss; however, I just want to point out to people that the VirtualBox manual has a section specific to kernel modules.

You can download the VirtualBox manual from here: [http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

Then, go to page 17 of the manual and read section "2.3.2 The VirtualBox kernel module".

To paraphrase what it says, if the Linux kernel on your system is updated, you may have to reinstall VirtualBox or recreate the VirtualBox kernel module by running this command:

*sudo /etc/init.d/vboxdrv setup*

I'm running the non-OSE version. After running the above command, everything works for me again.

Just thought people might miss this in some of the other posts since it is mixed in with other suggestions. It's definitely worth a try before reinstalling since the problem may happen again with the next kernel update.

---

### Post by bark50 on 2008-06-16
A new day, a new kernel and once again my Virtualbox-ose would not work.  I got the critter working by following the instructions here:

http://mcb.lessthanthree.se/?p=26[/url]

(My apologies if the above is not a live link; I don't know how to do that.)

I followed the instructions, and Virtualbox did work after a restart.  However, for some reason, I had to have Amarok rescan my music collection -- it was gone from Amarok!  The music was still on my pc; I just had to have Amarok rescan to "see" it.  I haven't found any other possible conflicts, and for all I know it might have been one of the Ubuntu updates that messed with my Amarok.

---

### Post by Ubeaut on 2008-06-16
Many of the solutions suggested in this thread involve doing a temporary fix after every kernel upgrade.  I found an easy permanent fix for the situation where there is an Ubuntu Host and an Ubuntu Guest.  The VirtualBox Help/Contents suggests installing the package dkms from the Ubuntu repository into both the Guest and the Host.  

Briefly, the purpose of dkms is to coordinate upgrades of individual applications with upgrades of the linux kernel, so they always stay in synch.  And it works!

The first time after you've installed dkms in the Host, you probably need to reinstall VirtualBox.  This is not at all difficult - it just installs over the top of the existing version and keeps all your existing machines and vdi disks.  I did this and also installed dkms in my Ubuntu Guest. The latest kernel upgrade in my Hardy Guest virtual machine ran like clockwork (after disasters without dkms).

---

### Post by pwc on 2008-06-17
Thanks Ubeaut for the input, before I try it I want to be clear about what I'm doing. So I'll install dkms with Synaptic, simple enough, but how do I go about installing dkms onto my guest(in my case Windows XP)?

Thanks again,
pwc

---

### Post by Ubeaut on 2008-06-17
Hi pwc

I didn't explain it very well above.

dkms is a linux-only application so it can't be installed in a Windows guest and would serve no purpose because there's no linux kernel in the guest for dkms to work with. 

But I believe there is still benefit in installing dkms in the Ubuntu host, because it co-ordinates upgrades of the host linux kernel with upgrades of VirtualBox in the host.  This forum has plenty of reports of trouble with VirtualBox ceasing to function after a HOST kernel upgrade, and dkms can help with that.  It's just a bonus if you can install it in a guest too, but not essential.

You are quite correct in saying it can be installed via synaptic; that's what I did.  

There's almost no publicity about dkms and few users seem to be aware of it.  But the fact that it's been included in the repositories indicates that it must have passed some scrutiny in the linux community.  A google search brings up the following Dell site as a starting place for info (Dell are the developers of dkms, but it is meant for any hardware).

[http://linux.dell.com/projects.shtml](http://linux.dell.com/projects.shtml)

Now here I'm a little uncertain, but I think it's true to say that VirtualBox will only link into dkms if VirtualBox is reinstalled after dkms is on your system.  

As I said above, I've had absolutely no problems from any of the steps above - nothing got broken, the last Hardy kernel upgrade went smoothly, and my VirtualBox guest still works!

---

### Post by dellboy on 2008-06-22
thank you mlissner this help me and now it works cheers mate 
> **mlissner said:**
> Hmmmm..this didn't work for me. I am still getting an error saying that I don't have a suitable module for the kernel. I am using the RC1 of Hardy.

EDIT: I figured out how to get this to work. Per the bug here: [https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/214393](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/214393), it appears that I had installed kernel specific modules rather than modules that would update when I updated the machine. 

The solution was to run ```
sudo aptitude install virtualbox-ose-modules-generic
```

That's apparently the metapackage, and it fixed my issues (with a score of -241).

---

### Post by Dan Hinojosa on 2008-06-27
Well this worked for me:

```
sudo apt-get install virtualbox-ose-source
sudo m-a update
sudo m-a prepare
sudo m-a a-i virtualbox-ose
sudo /etc/init.d/vboxdrv restart
```

---

### Post by Harpz on 2008-08-19
Ive just figured out how to get Virtualbox 1.5.6_OSE on system and im just putting XP on it to see what it runs like,

Only problem i had with Virtualbox so far is i have to boot off Ubuntu 8.04 kernal 2.6.24.16-generic instead of my 8.04 kernal 2.6.24.19-generic from the menu.

Also for some reason my GeForce 6600GT or my onboard sound aren't detected in Ubuntu 8.04 kernal 2.6.24.16 for some reason.

Ive only been using ubuntu for just over a week how would i get my 6600GT and sound recognized? or should i just wait for an update on Virtualbox 1.5.6_OSE so that it works with new kernal

Mike

---

### Post by jimmysheldon on 2008-08-20
So what is the current situation with virtual box and these kernel updates?

i installed virtual box ose, to get a virtual windows xp machine running, but got the error of 'virtual box kernel driver not installed' so i've tried most of the 'fixes' in this thread and none that i've tried are yet to work.

so i've just installed virtual box. and now i'd like to know the best way to do it? should i install the close-source version, or persevere with the ose?

---

### Post by Hazer on 2008-08-24
Hi, I had the same problem but I managed to work it out,
(for virtualbox-ose)

go to terminal and type in "uname -r" which will tell you your kernel version. so if my kernel was "2.6.24-19-generic" to get virtualbox working I would type:
```
sudo apt-get install virtualbox-ose-modules-2.6.24-19-generic
``` after that just go to system --> administration --> users and groups, click unlock and type in your password.  Then press manage groups and find the group vboxusers, select it and click properties then just tick your username and root and click ok. now logout and log back in and virtualbox should work! :guitar:

---

### Post by jimmysheldon on 2008-08-30
that worked perfectly, thanks hazer!

when the kernel gets updated again, do i just have to download the new package, and not fiddle about with groups again?

---

### Post by Hazer on 2008-08-30
Yeah I'm not sure if you even need to install the new package! I think it gets installed automatically as i think i have upgraded my kernel and it still works! but if it doesn't just install the new package, you will not need to fiddle with groups :)

---

### Post by jimmysheldon on 2008-09-01
awesome.

thanks for all the help.

---

### Post by Hazer on 2008-09-01
No problem, I'm new here and my goal was to help people (and have some questions of my own!) :)

---

### Post by Zezu on 2008-09-07
Hey everyone!
After searching 9 pages of this thread, I still have not found an answer that will work for me. I think that the problem is I am running the newest Kernel, 2.6.24-21-generic. Does anyone know if this is even supported by vbox? I will jump back to one of the older kernels if it will work, but it would be nice to not have to. 

Just as a little background, I just upgraded from Gutsy to Hardy and vbox worked perfectly for me before. I really need to get my virtual machine up and running relatively quickly as a bunch of my engineering programs for class are loaded on it.

from the vbox-install.log:
```
Makefile:138: *** Error: /usr/src/linux (version 2.6.24.3) does not match the current kernel (version 2.6.24-21-generic).  Stop.
```

Thanks

---

### Post by Zezu on 2008-09-09
Well, between the release of new modules combined with my realization that my current kernel had a broken a few links, notably, the one found at /usr/src/linux, I was able to get Vbox working. Woo...

EDIT:
So, the problem was not fixed as suspected. I tried to get help on the virtualbox.org site. No dice. I finally found something in an obscure bug fix from a vbox version or two ago about installing dkms to fix some error. Installed the package and it worked! wooo!

The ticket is below 

[http://www.virtualbox.org/ticket/1622]("http://www.virtualbox.org/ticket/1622")

---

### Post by slick666 on 2008-12-01
This worked for me too

```
sudo apt-get install virtualbox-ose-source
sudo m-a update
sudo m-a prepare
sudo m-a a-i virtualbox-ose
sudo /etc/init.d/vboxdrv restart
```

---

### Post by atlaslion on 2009-05-22
thanks a lot.. that worked for me

---

### Post by LuisRo on 2009-06-23
> **mlissner said:**
> Hmmmm..this didn't work for me. I am still getting an error saying that I don't have a suitable module for the kernel. I am using the RC1 of Hardy.

EDIT: I figured out how to get this to work. Per the bug here: [https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/214393](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/214393), it appears that I had installed kernel specific modules rather than modules that would update when I updated the machine. 

The solution was to run ```
sudo aptitude install virtualbox-ose-modules-generic
```That's apparently the metapackage, and it fixed my issues (with a score of -241).

This didn't worked for me. But I tried the following and it worked for me```
sudo /etc/init.d/vboxdrv setup
``` It seems to be different problems. Thanks.

---

### Post by mindgrind on 2009-07-01
YOU ROCK!!! worked for me. thank you so much for the solution

had this problem with upgrading to kernel 2.6.24-23-rt


> **slick666 said:**
> This worked for me too

```
sudo apt-get install virtualbox-ose-source
sudo m-a update
sudo m-a prepare
sudo m-a a-i virtualbox-ose
sudo /etc/init.d/vboxdrv restart
```

---

### Post by kryos on 2009-08-18
> **vexorian said:**
> Yes this works, reinstalling works because it does exactly that.

You can use synaptic (GUI) as well, open synaptic, find the installed "virtualbox" package then go to the "package" menu and click "configure..."

YES!  Simple and just works.
Thanks

---

### Post by ozzman2 on 2009-09-15
> **vexorian said:**
> You can use synaptic (GUI) as well, open synaptic, find the installed "virtualbox" package then go to the "package" menu and click "configure..."

**Sept 15, 2009**

Can someone please help me undo this?
(I'm running **Ubuntu 8.04 - Hardy**)

Yesterday, I was following along trying everything in this thread.
Then I went into **Synaptic** and searched for "**Virtualbox**".
With the list that came up, I checked off;
[INDENT][B]virtualbox-ose-modules-generi (ver 24.0.10)
virtualbox-ose-modules-openv (ver 24.0.10)
virtualbox-ose-modules-rt (ver 24.0.10)
virtualbox-ose-modules-server (ver 24.0.10)
[/B][/INDENT]My computer downloaded a lot of stuff, then did a reboot.  I lost my graphics and sound.

Since then, I've been able to get my screen resolution back up to 1024x768 (from 800x600).  However, I cannot use any visual effects (found in control center > appearance > visual effects tab).  I still have no sound.

I think maybe my kernal has been switched???  I dunno.  I'm pretty much a linux noob.  If anyone can get me out of this, I'd really appreciate it.  :confused:

---

### Post by scrooge_74 on 2009-09-15
I guess when booting choose another kernel by going into grub.

Also you can remove that version of Virtualbox and fetch the one from their site is pretty much up to date and had prettier things ;)  In fact I think they had an update today (havent installed it yet)

---

### Post by ozzman2 on 2009-09-16
I've tried pressing escape during the linux bootup for the kernal boot options.
(That's how I was even able to get my resolution back up to 1024x768 ).

Which kernal should I be using?
I'm pretty sure I was using 2.6.24 before my computer shat the bed.
I really just want everything put back the way it was.
(I'll worry about Virtualbox another time)

---

### Post by scrooge_74 on 2009-09-16
go into synaptics and pick a newer one, I think you could be using 2.6.30 (Im using Debian Lenny with backports so I guess that is close to latest Hardy one) I just powered down the one running Hardy and Im too lazy to get off the chair and go fired it up again 

Damn I read this 30 secs to late 
;)

---

### Post by ozzman2 on 2009-09-16
Okay, so I just did the GRUB thing again.  This time chose **2.6.24-23 Generic** .  That seems to have everything working again.

It doesn't boot to that one by default.  Guess I'll have to figure out how to make it do that later.  I've had enough for today.  :D

---

### Post by scrooge_74 on 2009-09-16
to change the booting order of kernels you just need to to change the settings in /boot/grub/menu.lst  look for a line that says 0 which means it boots the first kernel in the list that is at the bottom of that file.

You can also just remove the offending kernel by sudo apt-get remove kernel_#_so_and_so

---

### Post by savin on 2010-03-11
virtualbox is not starting:

error details:

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.


so i recompiled


recompiling  /etc/init.d/vboxdrv setup:

 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong

this s d log:

make KBUILD_VERBOSE=1 -C /lib/modules/2.6.31-20-generic-pae/build SUBDIRS=/tmp/vbox.1 SRCROOT=/tmp/vbox.1 modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (            \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";      \
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)
mkdir -p /tmp/vbox.1/.tmp_versions ; rm -f /tmp/vbox.1/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.1




help me on tis

---

### Post by Omim on 2010-03-18
> **savin said:**
> virtualbox is not starting:

error details:

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.


so i recompiled


recompiling  /etc/init.d/vboxdrv setup:

 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong

this s d log:

make KBUILD_VERBOSE=1 -C /lib/modules/2.6.31-20-generic-pae/build SUBDIRS=/tmp/vbox.1 SRCROOT=/tmp/vbox.1 modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (            \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";      \
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)
mkdir -p /tmp/vbox.1/.tmp_versions ; rm -f /tmp/vbox.1/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.1




help me on tis

Same problem here :(

---

### Post by khughitt on 2010-05-03
sudo service virtualbox-ose start

---

### Post by Eiht on 2010-05-23
I had the same basic issue on UNR Lucid with the full(not ose) version of virtualbox 3.1.  The fix that worked for me was to install the full(usb available version) and then add the package virtualbox-ose-dkms in synaptic and that fixed it.

---

### Post by notesetter on 2010-05-29
Try this:

In a terminal, do ```
sudo apt-get install --reinstall virtualbox-ose-dkms
``` For me, this reinstalled virtaulbox-ose-dkms (as one would expect) and also rebuilt the dkms package with kernel support. It fixed the problem for me.

---

### Post by eimhin85 on 2010-07-05
> **notesetter said:**
> Try this:

In a terminal, do ```
sudo apt-get install --reinstall virtualbox-ose-dkms
``` For me, this reinstalled virtaulbox-ose-dkms (as one would expect) and also rebuilt the dkms package with kernel support. It fixed the problem for me.

I was having this problem but the above fix worked perfectly for me. Thanks!

---

### Post by jhoseini on 2010-11-07
ubuntu 10.10
Sun virtualbox 3.2

try thid command
/etc/init.d/vboxdrv.dpkg-dist setup

---

