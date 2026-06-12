---
title: "How can I create my own spin off or customization"
date: 2010-11-09
forum: The Cafe
---

### Post by nolag on 2010-11-09
I am thinking of making a spin off (or customization) of ubuntu.  What I want to do is 1) add my own repos (I have a few programs that I think I will be making) 2) change the defaults (like puting in compiz) 3) rebrand (I want people to know it is my customization).  4) use different themes.  Ideally I would like to do something similar to what mint did (with different packages and themes though).  I still want to use the ubuntu repos, and its updates.  I know how to make my own disk with the repos and default installs, but I want to know some  things:
 
1) how can I rebrand it (ie change all the images and references to ubuntu, except in the packages, like the kernel can say ubuntu I don't care it is theirs)
 
2) what are the rules (ie am I allowed to use Ubuntu's logos and other stuff?)
 
3) What is the difference between a disto and a customization?
 
4) What tools are avalible to help me (remastersys I know of, Suse Studios like thing for ubuntu or debian would be better) and do any of them have boot disks like the ubuntu one? 
 
5) would people suggest renaming the kernel (like mint did) if there are no changes (idk if there are any in mint), I guess in case in the future I change something (or whatever)?
 
Thanks for any help
 nolag

---

### Post by forrestcupp on 2010-11-09
You could check out [Remastersys](http://remastersys.sourceforge.net/) or [Reconstructor](https://projects.lumentica.com/projects/reconstructor/wiki).  I don't know if they're still supported or not, but that's what you're looking for.

edit:  Nevermind.  I didn't read your post well enough.  But with those programs, you should be able to set it up exactly how you want things, including adding custom repos to the list, then make a disc.

You can't use Ubuntu's logo or name, or even similar logos or names without their permission.  They'll shut you down.

---

### Post by nolag on 2010-11-09
> **forrestcupp said:**
> You could check out [Remastersys]("http://remastersys.sourceforge.net/") or [Reconstructor]("https://projects.lumentica.com/projects/reconstructor/wiki"). I don't know if they're still supported or not, but that's what you're looking for.
 
edit: Nevermind. I didn't read your post well enough. But with those programs, you should be able to set it up exactly how you want things, including adding custom repos to the list, then make a disc.
 
You can't use Ubuntu's logo or name, or even similar logos or names without their permission. They'll shut you down.
 
Thanks for the reply.  I guess most of the questions are still out there.  Do you know how I would go about asking for permission to use their logos (or similar)?  How about on Ubuntu packages that I include, can those have their logos (since they made it)?
 
Quick additional question, if I include a package dose it have to be GPL?  I would like to include Compiz (I think ubuntu did that once no?) but it is MIT licenced and I don't own it.

---

### Post by forrestcupp on 2010-11-09
> **nolag said:**
> Thanks for the reply.  I guess most of the questions are still out there.  Do you know how I would go about asking for permission to use their logos (or similar)?  How about on Ubuntu packages that I include, can those have their logos (since they made it)?
 
Quick additional question, if I include a package dose it have to be GPL?  I would like to include Compiz (I think ubuntu did that once no?) but it is MIT licenced and I don't own it.

[Here is Ubuntu's trademark policy](http://www.ubuntu.com/aboutus/trademarkpolicy).  Read through it, and if you need to, there's a link on that page to contact them for permission.  You don't have to ask their permission to include their software that happens to have their logo in it.

You can include any packages you want, even if they're not GPL.  Ubuntu, itself has packages that aren't GPL.  You just need to make sure that it's legal to distribute whatever you include.

As for Compiz, it's already included in Ubuntu.  That's what Visual Effects are.

As for your original post, it's pointless to modify the kernel, unless you have a specific reason to do that.

---

### Post by Dustin2128 on 2010-11-09
It might be a bit in depth, but Linux From Scratch is where I'd start.
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)
Compiling can be annoying though.

---

### Post by Naiki Muliaina on 2010-11-09
A couple of old posts on my now very defunct blog.

A few links to various things :

[http://naiux.wordpress.com/building-your-own-distro/](http://naiux.wordpress.com/building-your-own-distro/)

Second post was La Rozas old post in the now gone Other OS sub forum. It was a thread where people posted links to remastering stuff. The Other OS forum disappeared ages ago. The link in the bottom of the post takes you to the original thread but like said, the forum got closed ages ago.

[http://naiux.wordpress.com/2008/11/14/43/](http://naiux.wordpress.com/2008/11/14/43/)

---

### Post by cariboo on 2010-11-09
[https://help.ubuntu.com]("https://help.ubuntu.com"), is a great place to look for help with something you're not sure about. Check out [this]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch") page.

---

### Post by nolag on 2010-11-10
Thank you all for your help!  You ahve given me a great start on the project I am considering undertaking.  I thought that compiz was no longer used for the desktop (switched it to something that starts with an m)?  I want that cube thing in my customization/derivative.  Anways thanks again, I will be looking more heavily into all this tomorrow and hopefully it won't be too hard to do what I want :D.

---

### Post by slackthumbz on 2010-11-10
> **nolag said:**
> Thank you all for your help!  You ahve given me a great start on the project I am considering undertaking.  I thought that compiz was no longer used for the desktop (switched it to something that starts with an m)?  I want that cube thing in my customization/derivative.  Anways thanks again, I will be looking more heavily into all this tomorrow and hopefully it won't be too hard to do what I want :D.

set your visual effects to 'normal' or 'extra' in System->Preferences->Appearance

```
sudo apt-get install compizconfig-settings-manager 
```
Then enable 'desktop cube' and 'rotate cube'

Bingo, you get a cube.

Personally, I can't see the point of creating yet another re-spin to achieve a few goals that can nominally be added to a normal install with very little effort.

---

### Post by nolag on 2010-11-10
> **slackthumbz said:**
> set your visual effects to 'normal' or 'extra' in System->Preferences->Appearance
 
```
sudo apt-get install compizconfig-settings-manager 
```
Then enable 'desktop cube' and 'rotate cube'
 
Bingo, you get a cube.
 
Personally, I can't see the point of creating yet another re-spin to achieve a few goals that can nominally be added to a normal install with very little effort.
 
As I stated in my original post, I plan to make a few packages (and my own repository, I am open to suggestions right now).  I have not yet done so, and so as of now my customizations would not be worth it.  In fact they would only be a remix that I could distribute with the ubuntu logos and everything.  I do want to make some more changes as I start to see what I want to add myself.  Also, there is not that many things you can do and consider it a remix, since changes to desktop stuff seems to disquailfy you.  Also another reason to do so, it's fun (and possibly educational)!

---

### Post by Megaptera on 2010-11-10
You mention Mint, you could also look at what the developer of Pinguy did with an Ubuntu base. No Ubuntu logos but very strong links to the Ubuntu 'family'.

[http://www.ubuntugeek.com/pinguy-osa-ubuntu-fork.html](http://www.ubuntugeek.com/pinguy-osa-ubuntu-fork.html)

---

### Post by linuxforartists on 2010-11-23
For more inspiration (or checking out the competition), I'd recommend taking a look at [Desktop Linux Reviews]("http://desktoplinuxreviews.com/").  That's the first place I go before doing any distro-hopping.  

The webmaster, Jim Lynch, has done a great job.  By reading his reviews of various distros, you'll get an insight of how to make your OS more user-friendly.  Always good stuff for a developer to know.

Good luck with your project!  By the way, have you chosen a name for your spin-off yet?

---

### Post by nolag on 2010-11-23
> **linuxforartists said:**
> For more inspiration (or checking out the competition), I'd recommend taking a look at [Desktop Linux Reviews]("http://desktoplinuxreviews.com/"). That's the first place I go before doing any distro-hopping. 
 
The webmaster, Jim Lynch, has done a great job. By reading his reviews of various distros, you'll get an insight of how to make your OS more user-friendly. Always good stuff for a developer to know.
 
Good luck with your project! By the way, have you chosen a name for your spin-off yet?
 
Thanks for the sites everyone :D! I have not yet had time to make the apps or customize my ubuntu yet so the project may be delayed until next January when I am back in school :P (co-op is great but keeps me busy). I was thinking of making the name after the distro, possibly naming it pending on what it does. The other name I had in mind was green tea (I love green tea), but then I was thinking a cute animal may be better so idk XD.
 
Also I am open for suggestions, if there are packages or other things people would like by default, or programs people want they can suggest them to me (here or PM).

---

### Post by swejap on 2010-12-12
I borrow this thread and ask here because searching through all topics on this question will take forever. I tried remastersys and chose to create a distro that I could share with friends. It worked fine, but didn't copy the configuration of my desktop and I'm not using the Gnome-panel. Is there a way to make a live-cd Ubuntu remix that copy exactly how my system is configured but excludes sensitive information? Or are all tools and scripts just for making a live-cd out of the installed packages and repos?

---

### Post by Paqman on 2010-12-12
> **swejap said:**
> I borrow this thread and ask here because searching through all topics on this question will take forever. I tried remastersys and chose to create a distro that I could share with friends. It worked fine, but didn't copy the configuration of my desktop and I'm not using the Gnome-panel. Is there a way to make a live-cd Ubuntu remix that copy exactly how my system is configured but excludes sensitive information? Or are all tools and scripts just for making a live-cd out of the installed packages and repos?

The template for a user is contained at /etc/skel. If you want new users to have certain customisations in their account when it's created, you need to copy your customisations to there.

---

### Post by swejap on 2010-12-13
> **Paqman said:**
> The template for a user is contained at /etc/skel. If you want new users to have certain customisations in their account when it's created, you need to copy your customisations to there.

Meaning I have to do that after installing Ubuntu? All I want is to make a distribution exactly how my system is configured. Create a live-cd/dvd that after its been installed looks just the way my customized Ubuntu 10.10 does.

---

### Post by Sean Moran on 2010-12-13
> **swejap said:**
> Meaning I have to do that after installing Ubuntu? All I want is to make a distribution exactly how my system is configured. Create a live-cd/dvd that after its been installed looks just the way my customized Ubuntu 10.10 does.

Keep the files pertaining to the customisations to menus, panel, desktop etc. in a subdirectory within the working directory where you're building your custom .iso.  Obtaining the files and directories required in the freshest possible condition is best done in the second stage of a two stage build process:

Before you begin, **apt-get install squashfs-tools** to your host machine.  Then, on a partition with 4-5Gb free space, create a working directory named **work** (or anything you like). Within that working directory, make another directory named **sto**, (or as you choose), and copy the standard ubuntu .iso (or a link to it) to that **work/sto** directory.   [I]
(sto stands for store - I'm stuck in my ways enough to still think from the basis of IPSO; input, process, store, output.)[/I]

From here you can repeat the build process as many times as you have the patience to.

1.A Mount the standard .iso to a subdirectory within your working directory.  
For IPSO simplicity, we'll call this *input* subdirectory **in**, and the final *output* directory **out**.   

```

cd work
sudo mkdir in out
sudo mount -o loop sto/ubuntu-10.10-desktop-i386.iso in

```1.B Copy everything on the mounted 'mock-live-cd' located in EXCEPT **/casper/filesystem.squashfs** to **out**.  This is the standard 'running-gear' for the live-cd.
```

sudo rsync --exclude=/casper/filesystem.squashfs -a in/ out

```1.C Unsquash the **in/casper/filesystem.squashfs** file.  We'll nominate **work/pro** as the process directory, but do not mkdir pro because squashfs-tools will do it for you, and get upset if you try to be helpful.
```

sudo unsquashfs -d pro in/casper/filesystem.squashfs

```1.D Copy required files into **work/pro**, (such as /var/cache/apt/archives for the additional packages you intend to install; (saves having to re-download .deb files you already have on localhost).  You will also need etc/resolv.conf and /etc/hosts to enable networking in your chroot session so that you can retrieve any extras that might be needed:
```

sudo cp /var/cache/apt/archives/* pro/var/cache/apt/archives/
sudo cp /etc/resolv.conf /etc/hosts pro/etc/

```1.E  You can then chroot into the new filesystem, mount things, and apt-get the packages you need:
```

sudo chroot pro
mount -t proc none /proc/
mount -t sysfs none /sys/
mount -t devpts none /dev/pts/
export HOME=/root
apt-get update                              # update sources - this is an online job.
apt-get -y --force-yes install fortunes-min # example of an additional package
apt-get -y --force-yes install xgalaga      # and another additional package.
cp /var/cache/apt/archives/*.deb /var/tmp   # saving out newly downloaded .deb files.
apt-get -y --force-yes autoremove           # cleaning up new custom filesystem.
apt-get clean
umount -l /proc/
umount /sys/
umount /dev/pts/
exit                                          # exit chroot and return to host session

```1.F Copy any other additional files you intend to use, eg. /usr/share/backgrounds.
```

sudo cp -a /usr/share/backgrounds pro/usr/share/backgrounds/

```1.G Save those extra .deb files so you don't have to download them over the Internet twice, remove the **pro/etc/hosts** and **resolv.conf**, and clear out **pro/tmp** and **pro/var/tmp** directories:
```

sudo cp pro/var/tmp/*.deb /var/cache/apt/archives/
sudo rm -rf pro/etc/hosts pro/etc/resolv.conf
sudo rm -rf pro/var/tmp/* pro/var/tmp/.*
sudo rm -rf pro/tmp/* pro/tmp/.*

```1.H Squash the new filesystem into the **work/out/casper** directory:
```

sudo mksquashfs pro out/casper/filesystem.squashfs

```1.I Calculate the new md5sum and manifest:
```

sudo chmod 777 out/casper/filesystem.manifest
sudo chroot pro dpkg-query -W --showformat='${Package} ${Version}\n' > out/casper/filesystem.manifest
sudo cp out/casper/filesystem.manifest out/casper/filesystem.manifest-desktop
echo CALCULATING NEW MD5SUM for DISTRIBUTION ...
sudo chmod 777 out
cd out
sudo chmod 755 casper/filesystem.squashfs
sudo rm -rf md5sum.txt
sudo find . -type f -print0 | xargs -0 md5sum > md5sum.txt

```1.J Build your new custom .iso file:
```

sudo mkisofs -r -V "CustomDistro" -b isolinux/isolinux.bin -c isolinux/boot.cat -cache-inodes -J -l -no-emul-boot -boot-load-size 4 -boot-info-table -o ../sto/Custom-Distro-10.10-i386.iso .

```1.K Now burn the .iso to CD/DVD or preferably use **unetbootin** to copy to USB flash drive, which saves a fortune in experimental CD burns.

[CENTER]NOW WE ARE READY FOR STAGE TWO!

[LEFT]Bootstrap into the new Live-CD or Live-USB and install onto a spare partition on your host system.  Then reboot back into that freshly installed custom distro.  Here is where you can make the changes to desktop and panel backgrounds, adjust menus, and other little tweaks such as adding or removing things to/from panels and desktops.

For these particulars, take a copy of the ~/.config/menus directory for menu changes, ~/.gconf/apps/ and ~/.gconf/desktop for panel, window-size and placement, and desktop backgrounds etc.

Put these files somewhere that you can retrieve them when you reboot back into your host machine's installation to complete stage two, then reboot back into your host machine's installation to complete stage two.

2.A. From your **work** directory, mkdir etc and mkdir etc/skel, then copy the new custom user configs to that /work/etc/skel directory.  If you look in the host machine's etc/skel directory, you will also find **.bash_logout**, **.bashrc**, and **.profile** in there. Copy those as well, just to be thorough.

2.B Repeat steps 1.A to 1.G.  Before squashing the new filesystem again, copy your custom user settings to the work/pro/etc/skel directory:
```

sudo rm -rf pro/etc/skel
sudo cp -a etc/skel pro/etc/

```2.C Continue from step 1.H and when you boot the new Live-CD or USB, you should theoretically see those adjustments you made at the end of stage one apparent on the new stage two desktop.  

Custom distros are rather a black art in some unpredictable sorts of ways, so don't expect everything to work out perfectly the first time, or the second time.  That is why it can save time and bandwidth to make sure to keep all the new .deb files you download from within a chroot session for later use.

Good luck.
[/LEFT]
  [/CENTER]

---

### Post by swejap on 2010-12-14
Really appreciate your reply! Very informative and useful for me and others in the future. Thanks for taking time to write it down and share it!

---

