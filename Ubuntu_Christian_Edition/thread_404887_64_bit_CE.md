---
title: "64 bit CE?"
date: 2007-04-09
forum: Ubuntu Christian Edition
---

### Post by accludetuner on 2007-04-09
Hello everyone!  I LOVE the Ubuntu CE.  I just got introduced to it less than 2 weeks ago and I've been super busy with it since then.  

Anyways, I looked and did not see anything on this yet.  I wanted a 64 bit version of CE and didn't find one.  So I decided to take on the task of modifying one for my purposes.

My question is reather general.  I was just looking for some sort of links to "how-to's" for installing most or all of the CE features.  Is it possible to take the CE related files from my x386 CD and applying them to the x64?  I haven't started modifying it yet and wanted to get some general ideas from those of you who have more experience in this area.

Thanks again for awesome Christian OS!!!!

---

### Post by Maintech on 2007-04-09
I installed CE on a dual-core 64 Athlon computer then updated. The headers and kernel for the 64 bit processors were downloaded and installed and SMP was enabled. I now have a dual-core 64 computer with CE and everything runs great. I have completed several hardware checks and speed tests and all indicate the system is runnng at top performance level for a dual-core 64.

---

### Post by accludetuner on 2007-04-09
Patience is a virtue.   I found update scripts for adding CE features to existing Edgy systems and ran the full CE upgrade script on top of the 64.  I encountered lots of errors which most have been resolved but there are plenty more to fix.  It's a learning experience.  The strangest error is when booting the splash/boot screen work fine with the original 64 logo, but when shutting down I get a messed up screen with no logos for either, just placeholders.


Did you have to do anything specific to get the 64 headers and kernel to update (command line) or did it automatically find them and update for you through synaptic.  The reason I'm asking is because I have an CE that updated to the 2.6.17.11-generic kernel automatically but mentioned noting about 64.  I have a 4-boot setup so I could play with each individually (in my sig.).

Also, since your upgrade you have no issues with wine? esword? dasnguardian? virtual rosary? gnomesword? or any of the other 32-bit based apps?

---

### Post by accludetuner on 2007-04-10
I've done some digging and have found that a direct upgrade to 64 is not possible from edgy.  A clean install is the only way to have a 64 bit version.  apt-get won't do it and sticking in a CD does not allow upgrades through synaptic or any other way.  I've tried both and read of others failures with this.  Maybe you know something that everyone else doesn't?

Not related, but I am doing a feisty upgrade now.  Should be done a little bit. 8)


Anyone know which (if any) CE scripts from here ([http://www.ubuntulabs.devubuntu.com/deb/](http://www.ubuntulabs.devubuntu.com/deb/)) will work on a 64 system?  I know I will have to mess with wine to get it to work, but it is possible.  Any other suggestions or ideas?

---

### Post by mysticrider92 on 2007-04-10
Most os's don't support going from 32 to 64 bit directly (the only distro I know can do that is Sabayon). 

All of the wine scripts should work on a 64 bit system, the only difference is that they aren't optimized for the processor.

---

### Post by accludetuner on 2007-04-11
Ok, seeing that I can add *some* of the CE specific features through those scripts is a big relief.  I will probably have plenty more questions as I continue to dig into it (newbie to ubuntu) but my next main question is - Is there a way to install amd64 on the same partition as my current x86 CE and have the choice of which one to boot to in grub?  From what I looked into, there are some installing 64 and running a 32 emulator inside of it.  I actually wanted them seperate but both useable.  My guess is that it's not possible seeing as how the new 64 install would overwrite files and probably keep x86 from ever working correctly again.  Please correct me if I'm wrong tho.

---

### Post by accludetuner on 2007-04-11
This is not in any way a CE specific thing so it might belong in another section, but here it goes!


I would like a CE 64 bit and 32 bit.  I know I've read about all the "marginal gains" and how 64 bit is "not really worth it now" and so on but I want to get it going with all the features of the current CE.  I am willing to put them on seperate partitions if needed, but I would like to have them available on the same partition with seperate grub entries so I have my choice at bootup.

So here is a crazy idea that may or may not work for this.  Maybe I can get some insight before actually going ahead with it.

What about compiling my own kernel and forcing it since there is no way to updgrade architecture directly through the package managers?

get tools needed (already installed)
```
sudo apt-get install kernel-package libncurses5-dev

```

find kernel source:
```
apt-cache search linux-source
```

get kernel source:
```
sudo apt-get install linux-source-2.6.xx

```

change dir & decompressed
```
cd /usr/src
sudo tar -xjf linux-source-2.6.xx.tar.bz2

```

create symlink "linux"
```
sudo ln -sf linux-source-2.6.xx linux

```

get kernel source tree
```
cd /usr/src/linux
```

configure kernel
```
make menuconfig
```

compile & package
```
sudo make-kpkg kernel-image

```

install
```
sudo dpkg -i kernel-image-2.6.xx.xx_custom_x64.deb
```

reboot and test
```
uname -a
```
```
dmesg | less

```


Am I opening up a can of worms attempting something like this?  Is there an easier way or is it even possible to have x86 and x64 on the same partition at all???  Thanks for any help with this.

---

### Post by mysticrider92 on 2007-04-11
I have never heard of trying that, but it actually sounds possible. I would definately make sure to back that partition up, something could go very wrong. You might be able to simplify it by just adding 64bit repos to the 32bit install, then just get that kernel image, and necessary 64bit software, unless you want the custom kernel (which would be a good performance increase). You would just have to add the correct Grub entry with an alternate boot path. I have never tried any of this, but it sounds like it could be possible (Linux is very powerful and suprises me often). My only 64bit experience was a short time with Sabayon 64 and Gentoo 64 (Gentoo AMD64 with a custom kernel is soooo nice...). 

Also, one random tip to make those commands easier would be to enable Ubuntu's root account. Run the command 'sudo passwd' and give it a password, then 'su' to root and run all the commands without sudo.

---

### Post by accludetuner on 2007-04-11
thanks for the suggestion!

I'm going to wait and see if I get any more feedback on this before going ahead and trying it.

---

### Post by cjm5229 on 2007-04-13
If you make a separate /home partition you can put a 32 bit root partition and a 64 bit root partition in as a dual boot and be able to choose which one you use. then if you update the 64 bit to CE and it breaks, you still have all your files in the home partition intact. You will also be able to access it from the 32 bit partition if you need to. I do this quite a bit for testing new Distros or Beta's I also run a 64 bit Ubuntu on one partition and a 32 bit on another sharing the same /home. If you install the 64 bit Feisty Fawn, I believe a lot of the CE software is available in the Feisty repositories. Having a separate /home really makes experimenting easier,because if you mess things up really bad, you can just reinstall the OS to the root partition and not lose any of your Doc's and settings. Good luck and Happy Ubuntuing:)

---

### Post by accludetuner on 2007-04-15
Alright.  Thank you for suggesting the separate /home partition.  I think I will be attempting this either this weekend or early next week.  I'll post back my results and any hints/tips I come across in case anyone else wants to do this.

---

### Post by mysticrider92 on 2007-04-24
I think I too am going to try the seprate /home partition to make things easier. 

Does anyone know if it is possible to have Ubuntu Edgy 32 bit (soon to be Feisty, when CE 3.0 is out) and Feisty 64 bit share a home partition? It seems like they would ignore each other's hidden files and folders for programs, but I would just like to be sure.

---

### Post by cjm5229 on 2007-04-26
Yes you can. Sometimes you have to delete one the dot files to get a particular app to work but that is usually not a big deal. Good Luck.

---

### Post by mysticrider92 on 2007-04-26
Cool, thanks.

---

### Post by Vietman on 2007-07-27
I can help testing if you guys want to make an Ubuntu CE 64 bit .iso. Right now I have Windows x64 and Ubuntu CE 32.

---

