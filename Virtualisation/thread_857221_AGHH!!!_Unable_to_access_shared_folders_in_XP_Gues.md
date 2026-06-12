---
title: "AGHH!!! Unable to access shared folders in XP Guest in VirtualBox"
date: 2008-07-12
forum: Virtualisation
---

### Post by fogster74 on 2008-07-12
Hey guys,

Sorry for shouting in the title, but I am getting SO frustrated with trying to get access to a shared folder on my Linux Host from my XP guest in VirtualBox. I've been at this for hours...!

**System details:**
Host - Ubuntu 8.04
Guest: Windows XP SP3
Firewall (on guest) - all turned off
VirtualBox 1.6.2 personal use (not OSE) with Guest Additions

**Folders I have tried to access:**
1) Desktop - \steve\Desktop
2) Shared file created for this -\home\steve\share

Have added all to the Settings -> Shared Folders in VBox...

**How have I tried to access?**
1) From the shell - (cmd.exe):
net use f: \\vboxsvr\<folder name> and
net use f: \\vboxsvr\home\steve\<folder name>

Both result in "Error 67 - The Network name cannot be found"

2) Browsing 'entire network' - I can see:
a) Microsoft Windows Network -> Workgroup -> Vbdell -> 'Printers and faxes' / 'Scheduled tasks'
b) "VirtualBox Shared Folders" -> Empty

I've tried everything I can find off the net, including switching off all Firewalls on the guest and resinstalling the VirtucalBox Guest Additions (without removing it first, as instructed on the net in numerous locations).

I have nothing left now to try - please can anyone help?!

PS I really don't know how to set up a Samba share but would be willing to give this a go, although this is the reason I wanted to use VirtualBox rather than VMWARE. If this may be an option, can anyone provide me with step-by-step instructions or a link to tell me exactly what I need to do?



All result in

---

### Post by dark_phantom on 2008-07-12
Is /home/steve/share created?  Did you select transient or machine (permanent) folder?  You could try the command instead, VBoxManage sharedfolder add "VMName" -name "sharename" -hostpath "C:/test".

---

### Post by fogster74 on 2008-07-13
Ok, finally solved this - not quite sure how but hope the following will help people:

I finally gave up on trying to get VirtualBox to use my specified shared folder as it should and instead attempted trying to set up a samba file share. Somewhere along the line of trying to get Samba working, VirtualBox sorted itself out!

Unsure of whether I needed to or not, I went into User and Groups (in Admin), unlocked the settings, chose Root then Properties. Selected the User Privileges tab and clciked "Share files in the local network". I also checked that my user account had this option selected (it did, by default). (I don't think any of this was necessary, you could probably try the next thing first and skip this bit - but I thought I should include it for completeness).

Next I went into the Synaptic package manager and searched for "Samba". "Samba-Common" was already installed but, above that, was the package "Samba" - I downloaded and installed that. Then I rebooted.

I then mounted my second internal hard drive manually and was trying to get the drive to automatically mount on boot (I wish there was an easier way of doing it that messing around with fstab - I find that very confusing and don't really understand it... if you're reading this and wondering what on earth fstab is, it's file found in /etc/ that stands for [I think[ file system table - it 'maps' a physical drive to a 'location'  (e.g. "Home", etc) in the Unix file system, 'mounting' the drive). 

I also (for whatever reason), tried one final time to reinstall the 'Guest Additions' Now, I may be a bit slow, but I couldn't actually work how to reinstall these - from within your VirtualBox environment (ie.e when your Virtual OS is actually running), choose (from the task bar) Devices, then "Install Guest Additions". If you look under 'Start' on the Windows OS, you will find, under 'all programs', a Virtual Box additions folder with the option to uninstall Guest Additions - DON'T DO THIS! I'm not sure why, but everywhere on the web tells you not to - just reinstall Guest additions from the taskbar -> Device -> Install Guest additions.

I tried this - and found that sometime, within the Windows OS, the Guest Additions install would start, and other times it wouldn't. If it doesn't start automatically, try browsing (in the Windows OS) to My Computer - I found that VirtualBox had 'mounted' what must be CD ISO image - so it looked like, in my CD drive, I had a CD containing the guest additions. I double clicked on this and the install started. (Note - after you've finished the install, the CD ROM appears to keep the 'guest additions' image. Right click on it and pick 'eject' and it goes away - once you've finished with it, obviously).

At this point I went into the VirtualBox Shared Folders (My Network places -> Entire Network -> VirtualBox Shared Folders) and was pleased to find that I could see my shared folder, //home/steve/share (shown as "\\XBOXSVR\share").

I saved a file there (from within XP) and switched to linux - and, sure enough, the file was sitting in the //home/steve/share file - excellent!! It was now working!

I have no idea at what point this was 'fixed' - I'd reinstalled Guest Additions a number of times and it was doing nothing, I also don't think it was adding 'share files' to the root account (once this was all working, I removed that option, and the shared files are still working fine). The Ubuntu 8.04 system I was using was brand new and fully patched, so it couldn't be any of that. The only thing I can think of is the Samba install I did (even though I just installed the package and didn't configure anything else).

The last thing I had to do then was share the actual drive that I wanted to see in both Ubuntu and the VirtualBox guest XP OS. This was much easier than it seems, I'll outline the steps here:

1) I identified the drive I wanted to share - did this by opening a terminal window and typing 'sudo fdisk -l' (whcih prompts you for your password). This lists all the current physical drives in your computer. Typically hard drives start hda (e.g. hda1, hda2 etc), but in laptops, SCSI drives or SATA drives, these seem to be listed sda1, sda2 etc (no other diffeence from my perspective for this purpose). I knew my data drive was about 100GB and was in the NTFS file system (as it was created for use with windows), and I hence identified the drive to be sda3.

2) I wanted to double check I had the right drive - I'd actually already mounted the data drive on my ubuntu desktop (this was done automatically when I clicked on the drive under Places), and I then (in the terminal window) typed 'mount'. This told me all drives that were mounted - and I could see sda3. I then right clicked on the data drive on the desktop, clicked 'unmount' and the drive disappeared from the desktop. I then returned to the terminal window and typed mount again - sure enough, sda3 was gone. I now knew I had the right drive.

3) Final thing was to edit the fstab file to get the data drive to automatically mount. I did this by, within the same terminal window, typing 'gedit /etc/fstab'
This opened the fstab file int he gedit editor.

4) I added the following line to the file:
/dev/sda3	/media/data   ntfs   user,fmask=0111,dmask=0000   0   0	

This wasn't the actual line I found on the 'net - I made the following changes:
a) I had to specify my drive in the first bit (i.e. sdfa3 - the example I found was hda1)
b) I specified where I wanted this mounted, and the 'share' name - so I created a directory in /media/ called 'data' and then told the fstab file to mount sda3 to 'media/data'. You could put the 'contianer' fodler (called 'data' here) anywhere I guess, but it makes sense to put it in '/media/'.
c) I specified 'ntfs' - the example I found was for 'ext3' (the linux file system). Everything I copied identically (i.e. everything from user,fmask onwards...)
d) I saved the file, exited the terminal and rebooted the whole computer.

On rebooting into Linux, sure enough I now had my data drive automatically mounted on my desktop.

The final thing was then go into VirtualBox, add this as a shared folder (poiinting the shared folder at '/media/data/'), started the machine and browsed the XP netwrok - and there was the data drive!

Important - it takes about 5-10 seconds to read your shared fodler - so don't be disillusioned if you double the click your share folder and it appears empty - give it a few seconds and you should see your files appear. I mapped this drive to F: (you can find out how to do this anywhere here by googling it - I won't cover that) and then pointed MY Documents to the F: drive - so now I have seamless use of a shared data drive, and I'm delighted!

I know this is all really basic stuff for most people, but I really hope this can help some newbies like me!

---

### Post by frereonline on 2008-08-14
Hello everybody,

I had the same problem but was hesitating to apply complicated fixes. One forum mentioned reinstalling the Guest Additions. This simply did the trick for me, with minimal work and fuss.
This is the procedure I followed:
- Uninstall On XP:
  Start > Programs > Sun Guest Additions > Uninstall
- Reinstall on the running XP machine:
  Devices > Install Guest Additions

I then had the shared folders showing up under
My Network Places/Entire Network/Virtualbox Shared Folders

Mounting a shared folder to an X: drive then was a piece of cake.
In XP, go to Start > Run... 
Type "cmd" and press Enter
Paste the following command, with your shared folder name
[ net use x: \\vboxsvr\your_shared_folder ]
You should now have a new X: drive with your shared folder.
Note: you can choose any free drive letter, such as D: or Z:

All the best,

Fred
___

---

### Post by AlanQ on 2008-08-27
After re-installing Guest Additions (didn't uninstall first) I found that 'net use x: \\vboxsvr\your_shared_folder' still gave Error 67.

My solution was to do it the graphical way:
Start > All Programs > Accessories > Windows Explorer
Right-Click 'My Network Places'
Select 'Map Network Drive'
Choose a drive letter.
Click 'Browse...'
Expand 'VirtualBox Shared Folders'
You should see your shared folder -- Click on it.
Click OK, ...etc.

I now have a shared folder -- and it works.

Cheers
Alan

---

### Post by poojac20 on 2009-01-10
This happened for me and got resolved by uninstalling and installing the VBoxAdditions. I used the same iso that I had used earlier for the installation. Hardy Host - XP Guest. 

What was interesting was that Windows DETECTED a couple of hardware devices after I uninstalled the VBoxAdditions. These were not detected before my first additions install. It seems that if you directly install GuessAdditions after the XP installation is complete, the installation is not successful though it reports as such. 

You should restart windows once after an OS install and before installing the additions. Just a guess, [but it being windows I won't be surprised if the guess is right]("http://xkcd.com/528/"). 

- Pooja.

---

### Post by HermanAB on 2009-01-11
Hmm, I circumvent the whole problem by using Filezilla and Proftp.  Simple, easy, it just works and I get to keep what little hair I have left.

Cheers,

Herman

---

