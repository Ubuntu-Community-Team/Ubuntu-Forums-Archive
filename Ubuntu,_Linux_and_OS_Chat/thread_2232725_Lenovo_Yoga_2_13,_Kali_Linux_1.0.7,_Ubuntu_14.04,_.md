---
title: "Lenovo Yoga 2 13, Kali Linux 1.0.7, Ubuntu 14.04, Windows 8.1 install, config, wifi"
date: 2014-07-03
forum: Ubuntu, Linux and OS Chat
---

### Post by skylersampson on 2014-07-03
I wanted to share an experience with everyone I hope will help others avoid what I have gone through the past 3 days. I bought a Yoga 11s that I loved but had some issues with the wireless, Lenovo being awesome replaced it with a Yoga 2 13. I love this laptop but ran into some issues with Linux install/wireless, which I wanted to show how to resolve in one place. Hopefully this will help someone else get through this quicker
 
I am going to try and write this for someone with little Linux experience, if I miss the mark please let me know and I will clarify the best I can.
For work I need Windows 8.1 and Kali Linux, while for home I prefer Ubuntu. 
 
My Yoga 2 13:
I5 1.6 ghz
8 GB ram
256 GB SSD
ORANGE! :D
 
My requirements: 
I need Windows
I need Kali Linux (livecd, even with persistent mode was not an option as it would not save the wireless fix or system updates) – I would also like this on a USB drive and not the internal SSD
I would like Ubuntu
 
Needed to do this:
1. 2 USB thumb drives (at least 8gb in size each) I used 2 Leef Supra 32GB drives. They are my favorite right now and are only about $27 at amazon.
2. Phone that can USB Tether or a USB Ethernet card (External USB wireless will show as "Hardware Locked"). Again you can pick one up for sub $10 if you need the USB Ethernet route. I used my Galaxy S5, you will need to download 200-300 mb of items through this so make sure you have the data if you go that route.
3. You may be able to get a USB wifi card to work if you do the following after boot. This only worked once for me.
                a.Type ‘sudo rmmod iwlmvm’
b.Type ‘sudo rmmod iwlwifi’
4. ISOs of Ubuntu and Kali Linux (I used Ubuntu 14.04 and Kali Linux 1.0.7)
5. Software to unzip the ISOs. I recommend 7-ZIP and will be referencing this in this guide.
6. I will include the EFI boot files and the WiFi fix files if I can attach. Otherwise I will provide a link to them.
   Link: [https://www.dropbox.com/s/puxnnoft3gn2b6l/WiFiFix.zip](https://www.dropbox.com/s/puxnnoft3gn2b6l/WiFiFix.zip)
 
Recommended (these are just in case you corrupt something making your system not see any OS 
1.  I would call Lenovo beforehand and get a set of recover disks (this will take 2-3 days)
2. In the meantime a USB Windows 8.1 or 8 ISO (the repair feature may save you)
 
*Note: At many points in this guide I detail steps and commands. Please double check that you understand the step before proceeding. There are multiple points where a mistyped command or clicking the wrong option will cause your entire system to fail and you will need to reformat the entire drive and start over. This also will make One Touch recovery not work. Proceed with caution.*
 
I did not need to disable ‘secure boot’ to do this, but keep in mind that you may need to.
 
Steps:
 
First let’s go through the installs, and then we will go through grub config and wireless fix
 
1. In Windows scroll to computer and right click, select manage.
2. Go to “Disk Management”
3. Select the main HDD (notice Lenovo puts a stupid number of partitions on here)
a. I deleted the D: drive on here, if you do this make sure to copy the drives over to your main C: drive. You will want to run each of the installers and repair the drivers after.
4. I used the space from the D: drive and pulled a little more creating a 50 GB partition for Ubuntu and my swap file
a. You can also add more space by right clicking your C drive and selecting shrink
b. Do not format the partitioned data as this will make identifying it later much easier.
5. Open a command line
                a. Swipe from the right of the screen and select search
                b. Type ‘cmd’
                c. right click and select ‘run as admin’
6. For Ubuntu: Type ‘diskpart’ into the command line
                a. type ‘list disk’
i. You should see 2-3 disks depending on if you have one or both usb drives in the laptop at the time. I would suggest only doing 1 at a time so you don’t lose track.
                b. type ‘select disk $’ (Replace the $ with the number of the drive)
c. ***** Before proceeding make sure you have the correct drive selected or you can ruin your Windows install and Lenovo one touch recovery will not fix it since we have changed the partitions *****
d. type ‘clean’
e. type ‘create partition primary’
f. type ‘active’
g. type ‘format  fs=fat32 quick’
h. type ‘assign’
i. type ‘exit’
6. For Kali Linux: Type ‘diskpart’ into the command line
                a. type ‘list disk’
i. You should see 2-3 disks depending on if you have one or both usb drives in the laptop at the time. I would suggest only doing 1 at a time so you don’t lose track.
                b. type ‘select disk $’ (Replace the $ with the number of the drive)
c. ***** Before proceeding make sure you have the correct drive selected or you can ruin your Windows install and Lenovo one touch recovery will not fix it since we have changed the partitions *****
d. type ‘clean’
e. type ‘create partition primary size= 3272
f. type ‘active’
g. type ‘format  fs=fat32 quick’
h. type ‘assign’
i. type ‘exit’
j. By doing this we can maintain a portion of this drive as the install CD and still have linux install/ liveCD if we need to run it on another machine.
 
7. At this point the drive is ready to have the contents of the ISO copied over.
8. Right click the ISO and select 7-zip then ‘zip to /’ This should unzip the ISO to the location of the ISO into a folder named exactly the same as the ISO.
9. Once this is done for Ubuntu ISO it is done
10. Kali requires a little bit more to be ready
                a. Kali will need some files added for EFI boot. --$--
                               i. Thanks to: [https://forums.kali.org/showthread.php?271-How-to-EFI-install-Kali-Linux](https://forums.kali.org/showthread.php?271-How-to-EFI-install-Kali-Linux)
                               ii. EFI files are located within the wifi fix folder _[https://www.dropbox.com/s/puxnnoft3gn2b6l/WiFiFix.zip](https://www.dropbox.com/s/puxnnoft3gn2b6l/WiFiFix.zip)_
11. Now let’s start with Ubuntu
 

Ubuntu install
 
1.     Place USB drive into the laptop and press the “Lenovo boot” button next to the power button
2.     Select ‘Boot Menu’
3.     Select ‘EFI USB Device (Name of drive)’ Mine stated Leef Supra
4.     Select ‘install Ubuntu’
5.     Go through the Ubuntu install until you get to select the install drive
6.     Once you get to the install portion it will ask you to select from one of 4 options. Select ‘Manually select partition’
7.     Select the “Free Space” where we opened up some of the drive
8.     You will need to create 2 partitions, I usually create the swap partition at the end of the drive
a.     First I create the swap 
                                          i.    Set at the end of the drive
                                         ii.    Set size to 1024 mb
                                        iii.    Set type to ‘swap’
b.     Second create the ext 4 partition
                                          i.    Set to beginning of drive
                                         ii.    Set to remainder of the space
                                        iii.    Set type to ext4
                                        iv.    Set mount point to /
9.     Finish the install and boot into Ubuntu
10.   You will notice that your wireless is ‘disabled by hardware’ This is fine for the time being and we will worry about this after the kali install. If we fix it now for some reason after installing kali we get the error again and would just need to fix it again.
 
Kali Linux install 
 
1.     Place USB drive into the laptop and press the “Lenovo boot” button next to the power button
2.     Select ‘Boot Menu’
3.     Select ‘EFI USB Device (Name of drive)’ Mine stated Leef Supra
4.     From the grub menu select ‘install kali linux’ both graphical and text work. I much prefer text install
5.     You will get a few errors through the install but that is fine
6.     The first we see is about network hardware and ‘load missing firmware from removable media?’ – Select ‘no’
7.     Then select no ethernet card
8.     It will have you name your machine then it will ask you for the root password
a.     If you want to just use root *not recommended* place the password here
b.     If you wish to use a non-root account then leave these blank and it will ask you for a name, username, and password of the new machine *Very Recommended* - this will also add this user to the sudoers file
9.     It will then ask you to ‘partition disks’
10.   Select manual
11.   Now here is where it can get a little confusing so read twice click once :D
12.   Select the USB drive from this list
13.   Mine shows up under (sdb) – Leef Supra
a.     It could be sdc, sdd, sde, etc… depending on how many drives you have plugged in. 
14.   You should see one primary drive that is 3gb or so that is formatted as FAT32. – DO NOT TOUCH THIS PARTITION!
15.   You should see the remainder of this drive as ‘FREE SPACE’ select that
16.   Create a partition at the end at size 1024mb and swap
17.   Then create another one for the remainder of the drive and set it to ext4 with mountpoint of /
18.   Continue through the install after you should see an error warning you that ‘you may not be able to boot’ that is fine, select continue 
19.   Then select from the menu of all the options ‘continue without bootloader’
20.   It should finish up then reboot on its own.
 
First setup/boot/fix grub
 
1.     You should  be able to boot up into GRUB2 menu now. 
2.     You may not see kali linux in this menu (make sure you have your towel and don’t panic!)
3.     Boot into Ubuntu
4.     Once you log in you should see that you still cannot use wireless due to being locked by hardware
5.     This is expected
6.     Let’s fix grub then we will come back to fixing wireless
7.     Plug in your device to connect to the internet (USB Tethering or USB Ethernet) 
8.     Once you verify that you now have an internet connection run the following from terminal
a.     ‘sudo add-apt-repository ppa:danielrichter2007/grub-customizer’
b.     ‘sudo apt-get update’
c.     ‘sudo apt-get install grub-customizer’
9.     You can also edit the grub.cfg manually if you know what you are doing… I did not
10.   Open grub  customizer
11.   It should auto populate and you should see ‘debian (kali linux)’ somewhere in the list
12.   It should be mounted to /dev/sdb2 or /dev/sdc2 depending on how many devices you have
13.   At this point go ahead and save
14.   Reboot and test that you can get into each OS
15.   This is where my inexperience got me. I spent 2 of my days so I am including this error: If when you boot into Kali you get an error somewhere that says ‘/bin/sh: can’t access tty: job control turned off’ look above it for an error that looks similar to ‘ALERT! /dev/sdc2 does not exist. Dropping to a shell!!’ 
a.     That error is due to the mount point being incorrect in grub, reboot and from within grub highlight the kali boot. Press ‘e’ then towards the bottom you should see ‘root=/dev/sdc2’ change this to ‘root=/dev/sdb2’ again the number doesn’t matter just make sure it stays the same. 
b.     Press F10
c.     If this boots fine then you will need to go back and fix the grub.cfg or load into Ubuntu and open grub customizer again, it should fix this 
16.   Now you have 3 working OS on the machine with one being on a USB! Congrats!
17.   You can remove the USB with no worry of screwing up your install, but you will not be able to boot into Kali Linux until you replace it. I would suggest only removing it and replacing it while the machine is powered off, but that’s just me.
 
Fix Wireless
 
Now is the time to do what probably ¾ of you came here for. FIX THE DANG WIRELESS. This is a huge problem from Lenovo’s side that I hope they realize how important Linux is and will fix. I won’t hold my breath though. 
 
Log into Ubuntu : This is well documented in the following forum post on page 3 by user Haohe:
[http://ubuntuforums.org/showthread.php?t=2215044&page=3](http://ubuntuforums.org/showthread.php?t=2215044&page=3)
His has you download quite a large file, mine should be much smaller.
[https://www.dropbox.com/s/puxnnoft3gn2b6l/WiFiFix.zip](https://www.dropbox.com/s/puxnnoft3gn2b6l/WiFiFix.zip)
 
1.     Download the attached package with the fix.
2.     Connect your USB internet device (tether or ethernet)
3.     Place the packages somewhere easy to access, in this example I will place them under ~/Desktop/WiFiFix
4.     Type ‘cd ~/Desktop/WiFiFix/’
5.     Now we need to prep the tools we need.
6.     Type ‘sudo apt-get update’ – we did this before, but you know, just in case :D
7.     Type ‘sudo apt-get install linux-headers-`uname –r`’   Note around uname-r they are the ` symbol not the ‘ this is located just above the tab on the same key as ~.
8.     Type ‘make’
9.     Type ‘sudo cp /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/ideapad-laptop.ko ~/ideapad-laptop.ko.backup’
10.   Type ‘sudo cp ~/Desktop/WiFiFix/ideapad-laptop.ko /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/’
11.   Type ‘sudo modprobe -r ideapad-laptop’
12.   Type ‘sudo modprobe ideapad-laptop’
13.   Type ‘sudo rfkill unblock all’
14.   Type ‘sudo modprobe -r ideapad-laptop’
15.   Type ‘sudo mv ~/ideapad-laptop.ko.backup /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/ideapad-laptop.ko’
16.   Next we need to blacklist the ideapad module
17.   Type ‘sudo echo 'blacklist ideapad-laptop' > /etc/modprobe.d/blacklist-ideapad.conf’
a.     The first time I tried this it wouldn’t work. So I did the following
b.     ‘sudo touch /etc/modprobe.d/blacklist-ideapad.conf’
c.     ‘sudo vim /etc/modprobe.d/blacklist-ideapad.conf’
d.     Enter     blacklist ideapad-laptop
e.     Exit and save
18.   Reboot your Yoga 2 13
19.   Boot into kali and see if you have wireless, if you do then you are done. If not we will need to repeat this process with one small little change. 
Kali Wifi Fix
 
1.     Copy the sources.list from the package provided
2.     Replace /etc/apt/sources.list with the included
3.     Some of the file path changes but the process remains the same from here.
Congratulations you now have 3 OSes one portable to other machines and working wifi!
 
Thank you
SirGed

---

### Post by slickymaster on 2014-07-03
Hi skylersampson, welcome to the forums. Since your post isn't a support request, I'm moving it to the **Ubuntu, Linux and OS Chat** sub-forum.

---

### Post by skylersampson on 2014-07-08
Okay thank you.

---

