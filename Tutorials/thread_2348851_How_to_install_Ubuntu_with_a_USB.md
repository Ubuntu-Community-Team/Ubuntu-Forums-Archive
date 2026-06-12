---
title: "How to install Ubuntu with a USB"
date: 2017-01-08
forum: Tutorials
---

### Post by thecrazydude778 on 2017-01-08
If you need a slightly more detailed Ubuntu USB install than the one on the Ubuntu website you have come to the right place. So...

Here's how to install Ubuntu 16.04 THE SEMI-EASY WAY

You Will Need:
- A USB that can store at least 2 GB and is empty
- A computer that meets the System Requirements (to install Ubuntu)
- A computer that can download the disk image (Around a 1.5 to 2.0 GB File) and has Windows Vista or later installed
- An Internet connection
- Some patience

**Recommended System Requirements** (Day to Day Ubuntu)**:**
- 2Ghz processor or better
- 2Gb of RAM
- 25Gb of ***free*** Hard Drive space
- A USB Port
- Internet is useful

**Minimum System Requirements** (Just putting an OS on an old computer)[B]:
- [/B]1000Mhz (1Ghz) processor
- 1024MB of RAM
- 5GB of Storage Space
- 3D Acceleration Capable Video Card with at least 256 MB
Note: System requirements for Ubuntu 14.04 and earlier have different System Requirements. Check link for more information. 
Help article about minimum system specifications: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

The Steps:

1. Get Ubuntu from the official download page ([https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)) and wait until it's downloaded

2. Get Rufus ([https://rufus.akeo.ie/](https://rufus.akeo.ie/)) and open it.

3. Once Rufus has started, look at the Format Options and find Create a Bootable Disc.

4. There should be a button with an image of a CD on top of a Hard Drive. Click on it.       

[IMG]https://i0.wp.com/www.techfleece.com/wp-content/uploads/2015/07/select-ISO-file.jpg?resize=369%2C519[/IMG]

5. Find your the file that you got from the Ubuntu website and double click it. It should be named something like ubuntu-1x.xx-desktop-amd64.iso or 

6. Make sure that the USB device is selected and that all files that you want to keep are somewhere safe.

7. Click Start. 
- Note that there might be a dialog box saying to either write in DD mode or to write normally. Choose 'Write in ISO Image Mode' and if another dialog box shows up warning about the drive being formatted then click Okay and just wait until the operation is complete. The USB will be formatted and all the data will be gone so keep that in mind. If there is a box that tells you that it needs to download click Yes.

8. Once the operation has finally completed, remove the USB and plug it into the computer you want to install Ubuntu in.

9. Then start the computer up and continue pressing F12 (Or Delete) until you see a Boot device screen. It will look something like this:

[IMG]https://i.stack.imgur.com/xSqQs.jpg[/IMG]

10. Choose the USB device you inserted and press Enter.

11. Wait until Ubuntu loads

12. After it loads you should be at a screen that looks like this:


[IMG]http://1.bp.blogspot.com/-Np4zZtDeymI/Txq-_PrVf-I/AAAAAAAAAFA/IENzw2nISuc/s1600/Install-01_Try_Install.png[/IMG]

13. Now just click on Install Ubuntu

14. You will then be greeted by a screen like this:

[IMG]https://assets.ubuntu.com/v1/3bbb0e35-download-desktop-install-ubuntu-desktop_2.jpg[/IMG]

If you want to complete your installation to complete faster (or you have no Internet) make sure to leave the top check box unticked. However if you do have Internet it's best to leave this on. Keep the 'Install third-party software' box ticked as it installs stuff that allows you to play stuff on the Internet and other good things. This will also install some useful programs as well.

15. Now (after you pressed Continue) you will be greeted by another step in the installation process. The screen will look something like this:

[IMG]https://assets.ubuntu.com/v1/b42312cd-download-desktop-install-ubuntu-desktop_4.jpg[/IMG]

This screen is to create the necessary disk changes and partitions to run and install Ubuntu. Normally you would get a screen like this if you have no OS(s) installed on your hard drive. Normally (in that case) all you would have to do is to select 'Erase disk and install Ubuntu' and the system would then format the drive and install Ubuntu. If you have a Dual-Boot setup with an OS already installed on the Hard Drive, you would probably have a setting that would allow you to keep the installation of the OS already on the disk and run Ubuntu alongside it. You could also manually select the partitions yourself by selecting 'Something Else'. (for people that know what their doing). There are also 2 boxes that you can select for...

- Encrypting the installation (Ubuntu's version of BitLocker) and
- Using Logical Volume Management (LVM) with the partition to allow easier Partition Resizing and taking 'Snapshots' of Ubuntu partitions.

These are mostly for people who experiment and/or tinker with Ubuntu and it's Partitions and people who really want to keep their Hard Drives safe and encrypted. 

You can get more information on those here:
[http://askubuntu.com/a/430310](http://askubuntu.com/a/430310) 
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

16. A summary of the partitioning operation with be shown (like below) then all you need to do is press Install Now.

[IMG]https://assets.ubuntu.com/v1/6d01bd8c-download-desktop-install-ubuntu-desktop_5.jpg[/IMG]

17. If you haven't connected to the Internet you will be then be shown a world map. All you have to do if you are shown this is select the time zone by clicking on the map or by typing your city's name in the box below the world map. Press Continue after that's been done.

18. Almost there! Now you have to choose your keyboard layout. Usually for most people it's already set for their keyboard and all you have to do is press continue to the next step. But if you don't have the right keyboard setting then find your keyboard layout and press Continue.

HINT: If you don't know your keyboard layout just click the handy 'Detect Keyboard Layout' button and answer the questions and it will find your keyboard layout for you.

19. Now have reached the final step. Now all you have to do is answer the questions and you're done! Here are the meaning of the questions that you will answer:
- Your Name = Put your name in the box

- Your computers name[SUP]1[/SUP] = The name that your computer broadcasts to other computers in a network

- A Username[SUP][SUB]1[/SUB][/SUP] = The Username can be whatever you want as long as there's no Capital Letters, Special Characters (@#$%&^(!^) and/or Spaces.

- Password = This can be*** whatever*** you want as Capital Letters and Special Characters are useful in making a strong password.
Note: This password is very important as it allows you access to your computer, administrative functions (installing software, etc.) and using most Terminal commands. Make sure that you can remember it too.

- Log-in Automatically = This will log you in automatically when the system starts (Not good if you're sharing the computer).

- Require Password to Log-In = This requires you to enter the Password you made when you start the computer. This should be selected if you want to share the computer and don't want someone else accessing your Flies, Settings and Important Stuff.

- Encrypt my Home Folder = This will require you to enter a password every time you want to access your files and folders stored in the Home folder. Not Recommended to people who haven't used Ubuntu (or Linux) before ([https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)).

After selecting the options you want you can finally click the glorious Continue button to finally start installing Ubuntu.

[SUP]1 [/SUP]Ubuntu will usually auto-fill these so you don't really have to enter anything other than your name and they will be auto-filled.

20.  Depending on your system, your installation might take 5 minutes up to an 1 hour so relax and do something else while the system is installing.

15. Once the installer has completed installing Ubuntu click Restart Now, Pull out the USB and then wait until the System reboots again. After the system reboots (If you have a dual-boot) you should be at a screen that has a purple background with white writing. Make sure that Ubuntu 1x.xx is selected and press enter. If you didn't get the screen (Ubuntu Only Installation) just wait a bit then after a small wait you should be at a login screen (or your Desktop), all you have to do now is login with the password you made in the installer and you're done!

16. Enjoy your new install of Ubuntu!

---

### Post by LastDino on 2017-06-08
Good tutorial.

Could accommodate some steps with Gparted to make "/", separate "/home" and maybe even swap (seems to be that Ubuntu is now moving towards swap file). As a beginner, that is where the most people struggle.

I remember going through dozens of pages for this when I first installed Linux. Might as well provide link to info on typical Linux partition schemes.

---

