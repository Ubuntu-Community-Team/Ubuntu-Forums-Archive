---
title: "Virtualbox won't run in Ubuntu 12.10"
date: 2012-11-08
forum: Virtualisation
---

### Post by afz12 on 2012-11-08
I have recently installed Ubuntu 12.10 as a fresh install and then installed Virtualbox 4.2.4. Initially it ran OK using previous XP VM's but then I updated Ubuntu 12.10 and now Virtualbox won't run. It seems to need vboxdrv but can't find it (nor can I). 

I removed all Virtualbox references using Synaptic. I reinstalled using the .deb file - same problem. I repeated the procedure and installed from the software centre - again same problem. This is not a "guest additions" problem. Also the  suggestion to use

[COLOR=#0000ff]sudo /etc/init.d/vboxdrv setup[/COLOR]

in a terminal failed as vboxdrv couldn't be found.

Ubuntu 12.10 appears to work OK with other software and Virtualbox was working OK on Ubuntu 12.04. Which is at fault - Ubuntu 12.10 or Virtualbox for 12.10? I installed Ubuntu 12.10 as a fresh copy rather than an "upgrade".

Is there a work-around? Virtualbox refuses to work in any situation - whether using a previous VM or when trying to create a new one.

---

### Post by mikesmithv on 2012-11-09
I am having the exact same problem.  VirtualBox 4.2.4 worked fine in 12.10 then stopped working after the Ubuntu software update, same error messages.  I went the extra step of uninstalling 4.2.4 and installing the older VirtualBox 4.1.18 in the Ubuntu Software center.  That also failed with the same error message.  Is there anyone out there that is NOT having problems with VirtualBox after this latest update?

---

### Post by Mr_JMM on 2012-11-09
I have 12.10 both upgrade and fresh install and VB is working perfectly.
In an attempt to once again (I see you've tried this already but...) install VB from scratch, remove VB from your system. Find the hidden VB files and delete them (except the ones containing the VB virtual hard disk OS images).
Run sudo apt-get update then autoremove.

Now try again to install VB from the software center.

If you've tried all these steps and still no luck I'm sorry, I can't think of anything else.

---

### Post by afz12 on 2012-11-09
Thanks MrJMM

I'm unsure how to find "hidden files". I removed everything I could find and repeated installations. It is interesting that Virtualbox worked for you - I wonder if there is some hardware interaction going on?

I have another notebook that currently runs Mint Mate. I think I'll switch it to Ubuntu 12.10 later today and see if Virtualbox runs on it, both before and after the Ubuntu update.

I found a much earlier thread reporting a similar problem way back in time to Ubuntu 9.10 or so. It suggested that Oracle can take some time to get Virtualbox organized - perhaps they will fix this issue in due course. Or perhaps not :)

---

### Post by mikesmithv on 2012-11-09
By hidden files I think he means the .virtualbox folder in your home directory when you select "Show Hidden Files" under the View menu.  I tried deleting that and repeated the process of uninstalling everything virtualbox.

sudo apt-get purge virtualbox*

Then I restarted just for good measure, and re-installed VB.  Same error message, no change.  When I reboot under Ubuntu 12.04 (installed on another partition) then VB works fine, latest updates and all.  Very strange.  I am running the 64 bit version of Ubuntu & VB.  Maybe this is a 32 vs 64 bit issue and it is only broken for 64 bit users on 12.10.

---

### Post by afz12 on 2012-11-09
Hi Mikesmithv

Yes it's very odd! I tried something a bit different and installed Mint Mate on this notebook and then installed the .run version of Virtualbox (for all OS). The latest version also worked well. It had some niggly issues with Internet access though (network pipe worked OK and USB worked after I modified the last line of the /etc/group file to ..:125:...) Now Virtualbox seems to be working in Mint Mate!

I am now installing Ubuntu 12.04 on another notebook and I suspect that Virtualbox, latest version, will be OK on this. If not, I'll report back. In any case it seems like Ubuntu 12.04 and Oracle may need to have a few more chats on interoperability, especially when Mint works with Virtualbox even though it is not listed by Oracle as a supported OS!

---

### Post by mikesmithv on 2012-11-11
I finally found a fix.  It was discussed in [this link]("https://forums.virtualbox.org/viewtopic.php?f=7&t=52458").  To summarize, all I did was run these two line:

sudo apt-get install dkms build-essential linux-headers-generic
sudo /etc/init.d/vboxdrv setup

Hope this helps.  It was a real head-scratcher!

---

### Post by afz12 on 2012-11-11
Hi mikesmithv

Thanks for the link - I'll install Ubuntu 12.10 and give it a whirl.

---

### Post by varunendra on 2012-11-12
> **mikesmithv said:**
> I finally found a fix.  It was discussed in [this link]("https://forums.virtualbox.org/viewtopic.php?f=7&t=52458").  To summarize, all I did was run these two line:

sudo apt-get install dkms build-essential linux-headers-generic
sudo /etc/init.d/vboxdrv setup
Yep ! For *vboxdrv* problems this is the definite fix. IIRC, the  error message clearly mentions this fix if you read it carefully  (reinstall dkms package.... then retry).

I haven't tried 12.10  yet, but have read many posts mentioning that it doesn't contain the  'linux-headers' by default, which is causing many such problems.  Apparently, the developers 'forgot' to include it in the default  packages, but I can confirm it is not the first time. I also had to  manually install the headers after normal kernel updates in karmik (it  happened more than once). I even believed that you have to install the  headers manually after each kernel upgrade. Although in recent versions  (from 10.04 upto 12.04) the headers installed by default, the  discrepancy seems to have resurrected in 12.10.

Not only for *vboxdrv*  problem, the 'linux-headers' and 'dkms' are essential packages for ANY  module (driver) upgrades. Make sure they are installed and updated after  each fresh installation/update/upgrade.

---

### Post by Bigfoot73 on 2012-11-18
I'm also having a similar problem.

I Installed Virtualbox today on a fresh Ubuntu 12.10 system.
I copied an existing virtual machine with Windows XP from another computer, when I tried to start it it made the entire host system reboot. I made a new VM and tried to install XP again. During installation the host system reboots again.

I have tried both the version shipped with Ubuntu and the latest version with the same result.

I have also tried the fixes suggested in this thread without any success.


Edit: I tried install Ubuntu as a guest-OS and that will also make the host crash, so it is not caused by XP.

---

### Post by howefield on 2012-11-18
> **Bigfoot73 said:**
> I'm also having a similar problem.

Doesn't sound a similar problem, not even remotely. Start a fresh thread, detailing the errors.

---

### Post by Jan Greeff on 2012-11-28
This fix does not seem to work for me: 

jan@jan-System-Product-Name:~$ sudo apt-get install dkms build-essential linux-headers-generic
[sudo] password for jan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
linux-headers-generic is already the newest version.
The following NEW packages will be installed:
  dkms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/72,8 kB of archives.
After this operation, 348 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package dkms.
(Reading database ... 161082 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1.1ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.2.0.3-1.1ubuntu1) ...
jan@jan-System-Product-Name:~$ sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found

Where do I go from here? Can anyone help, please?

---

### Post by varunendra on 2012-11-28
> **Jan Greeff said:**
> jan@jan-System-Product-Name:~$ sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found

Where do I go from here? Can anyone help, please?
Please post the exact error message you are getting when you try to run virtualbox.

If you installed VBox from Software Center, reinstalling it should automatically fix the error now that dkms is installed. It won't download the Vbox packages again if you haven't manually removed them from /var/cache/apt/archives directory.

Also, make sure you are a member of vboxusers group. You can verify that by 'groups' command -
```
groups
```

---

### Post by Jan Greeff on 2012-11-28
I tried to install virtualbox via these commands: 

echo "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -
sudo apt-get update 
sudo apt-get install virtualbox-4.2

My previous post shows the outcome which ends with "command not found"

During previous attempts to install via package manager vbox would not start. Unfortunately  I did not keep the error report.    

The command "groups"  gives the following result: jan@jan-System-Product-Name:~$ groups
jan adm cdrom sudo dip plugdev lpadmin sambashare

---

### Post by pkadeel on 2012-11-28
> **Jan Greeff said:**
> I tried to install virtualbox via these commands: 

echo "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -
sudo apt-get update 
sudo apt-get install virtualbox-4.2

My previous post shows the outcome which ends with "command not found"

During previous attempts to install via package manager vbox would not start. Unfortunately  I did not keep the error report.    

The command "groups"  gives the following result: jan@jan-System-Product-Name:~$ groups
jan adm cdrom sudo dip plugdev lpadmin sambashare
The solution provided in the thread is not for all types of virtual box errors. You need to provide the actual error message you get when you run virtual box and it will better to open a new thread for your error to get a proper response from other members.

Besides the error one thing which you will need to do is to add yourself to vboxusers group
```

sudo adduser jan vboxusers 

```

---

### Post by varunendra on 2012-11-28
> **pkadeel said:**
> You need to provide the actual error message you get when you run virtual box
..
Besides the error one thing which you will need to do is to add yourself to vboxusers group
```

sudo adduser jan vboxusers 

```+1
Adding yourself to vboxusers group is a must, and maybe your original problem too!

The problem with "vboxdrv" arises 'After' a kernel updgrade when kernel headers and dkms are not installed. But since you are not added to 'vboxusers' group, you were certainly not able to run VBox from the beginning. And the error message should have been something like - *"You do not have permission to run VirtualBox..."*

Adding yourself to the vboxusers group, using *pkadeel*'s command above, should be all you need. Installing dkms, that you have already done, would save you from possible future errors.


Here's just an explanation of a few things (soluion, I believe, is already discussed above) -
> **Jan Greeff said:**
> I tried to install virtualbox via these commands: 

echo "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -
sudo apt-get update 
sudo apt-get install virtualbox-4.2
Those commands^ added a repository to your software sources list and the last command downloaded & installed it just like it would from its default Software Center (only this one would be a newer version). As such, the downloaded .deb files should still be in the apt-cache (/var/cache/apt/archives directory). So it's easier to simply re-install it in case you still get some error even after adding yourself to vboxusers group.

> My previous post shows the outcome which ends with "command not found"
That was the error you got while trying to run '*vboxdrv setup*', while I was interested in the error you got while trying to run virtualbox itself (which should have been the 'permission' related one as I guessed above).

```
During previous attempts to install via package manager vbox would not start. Unfortunately  I did not keep the error report.
```Should have been same (or similar) error, for same reason.

Remember - Error messages are windows to the heart of a problem, never overlook them. Most often, they give you a precise idea of what is causing a problem, and sometimes they even suggest you a solution too.

Hope you get it going.
Cheers!

---

### Post by Jan Greeff on 2012-11-29
Thanks varunendra.

  	 	 	 	 	 	   I tried to install virtualbox via these commands: 
[I]
echo "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
wget -q [http://download.virtualbox.org/virtu...racle_vbox.asc]("http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc") -O- | sudo apt-key add -
sudo apt-get update 
sudo apt-get install virtualbox-4.2

[/I]Previous attempts to install via package manager, vbox would not start. These error reports were received:  
 *Because the USB 2.0 controller state is part of the saved VM state, the VM cannot be started. To fix this problem, either install the **'Oracle VM VirtualBox Extension Pack'** or disable USB 2.0 support in the VM settings (VERR_NOT_FOUND).*
 

  	 	 	 		 			Result Code:  			
 		 		 			[FONT=Courier New, courier]NS_ERROR_FAILURE (0x80004005)[/FONT]
 		 	 	 		 			Component:  			
 		 		 			Console
 		 	 	 		 			Interface:  			
 		 		 			IConsole {db7ab4ca-2a3f-4183-9243-c1208da92392}
 		 	  

 I installed the extension pack, no change in result. I have added myself as user, but the error report says user must be added, when I redo add user, it says user is already added. 

The following outputs were also received: 
   
 *Failed to open a session for the virtual machine **Nuwe skelm**.*
*Implementation of the USB 2.0 controller not found!*
 I cannot access the USB 2.0 setting to disable it.

---

### Post by pkadeel on 2012-11-29
> **Jan Greeff said:**
> *Because the USB 2.0 controller state is part of the saved VM state, the VM cannot be started. To fix this problem, either install the **'Oracle VM VirtualBox Extension Pack'** or disable USB 2.0 support in the VM settings (VERR_NOT_FOUND).*
 

                                      Result Code:              
                               [FONT=Courier New, courier]NS_ERROR_FAILURE (0x80004005)[/FONT]
                                         Component:              
                               Console
                                         Interface:              
                               IConsole {db7ab4ca-2a3f-4183-9243-c1208da92392}
                

This message was definately because of missing Extenssion pack and your saved VMs had usb support enabled. anyway now you have added the extenssion pack and have also added your user to vboxusers group, it should be fine.

>   I installed the extension pack, no change in result. I have added  myself as user, but the error report says user must be added, when I  redo add user, it says user is already added. 

The following outputs were also received: 
   
 *Failed to open a session for the virtual machine **Nuwe skelm**.*
*Implementation of the USB 2.0 controller not found!*
 I cannot access the USB 2.0 setting to disable it.[/QUOTE]
One thing which I forgot to mention in my previous post was that you need to logout and then again login to take the effect of adding user to the group.

---

### Post by varunendra on 2012-11-29
> **Jan Greeff said:**
> I installed the extension pack, no change in result. I have added myself as user, but the error report says user must be added,
Can you post the full and exact error report ?

Also, how and from where did you install the Extension pack? They are different for different versions. From VBox's official site, the correct one for version 4.2 -
> VirtualBox 4.2.4 Oracle VM VirtualBox Extension Pack  [All platforms]("http://download.virtualbox.org/virtualbox/4.2.4/Oracle_VM_VirtualBox_Extension_Pack-4.2.4-81684.vbox-extpack")

For a test, can you create a new, blank virtual machine and run it ?
If possible, please also post a screenshot of the settings window of the VM in question.

.

---

### Post by Jan Greeff on 2012-11-29
Thanks pkadeel, I found this site  [http://www.howopensource.com/2012/10/w-duplicate-sources-list-entry-ubuntu-12-10-12-04/](http://www.howopensource.com/2012/10/w-duplicate-sources-list-entry-ubuntu-12-10-12-04/) 
then deleted the duplicates, installed ext pack and ran the rest of the  commands and Vbox is up and running. Hooray and praise to our King!

---

### Post by varunendra on 2012-11-29
Congrats! :)

Please mark the thread as **[Solved]** using **Thread Tools** at the top of first post above.

Thanks !


**EDIT:**
Which means 'My post' :) *(didn't realize it's going on a new page)*.

---

### Post by Jan Greeff on 2012-11-29
Thanks varunendra, I tried but there is no link to "solved" in thread tools...

---

### Post by varunendra on 2012-11-29
> **Jan Greeff said:**
> Thanks varunendra, I tried but there is no link to "solved" in thread tools...

Ouch ! I'm terribly sorry! I totally forgot that it's not your thread. That link is available for only the person who starts the thread.

Nevermind, it's enough to have successful posts in the last :)

Enjoy !

---

### Post by Jan Greeff on 2012-11-29
Thanks, makes sense and another learning curve for me!

---

### Post by K0ldBl00d on 2012-12-20
I'm creating my own network in VirtualBox, but when I go to the settings for my DHCP machine and add my 12.10 Server 32bit or 64bit ISO. I get this error message... 

Failed to open the CD/DVD image /Documents/ubuntu-12.10-server-i386.iso.
Could not get the storage format of the medium '/Documents/ubuntu-12.10-server-i386.iso' (VERR_NOT_SUPPORTED).

Result Code: 
VBOX_E_IPRT_ERROR (0x80BB0005)
Component: 
Medium
Interface: 
IMedium {53f9cc0c-e0fd-40a5-a404-a7a5272082cd}
Callee: 
IVirtualBox {c28be65f-1a8f-43b4-81f1-eb60cb516e66}

Why won't it work?

---

### Post by allenA on 2013-01-17
My error to run VB is :

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

I have tried to run commands
sudo apt-get install dkms
but there are no /etc/init.d/vboxdrv and /dev/vboxdrv in my directory. 

I also tried to update and autoremove, then reinstall VB. It still doesn't work.

Anyone has the same problem?

---

### Post by varunendra on 2013-01-21
> **K0ldBl00d said:**
> Failed to open the CD/DVD image /Documents/ubuntu-12.10-server-i386.iso.
Could not get the storage format of the medium '/Documents/ubuntu-12.10-server-i386.iso' (VERR_NOT_SUPPORTED).
Not sure, but have you checked the integrity of the ISOs?
How to MD5Sum : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

> **allenA said:**
> sudo apt-get install dkms
but there are no /etc/init.d/vboxdrv and /dev/vboxdrv in my directory.
Have you checked your usergroup? Command to check that-
```
groups
```
You should see 'vboxusers' in the output. If not, do-
```
sudo adduser <your user ID> vboxusers
```
Then retry.

---

### Post by Objekt on 2013-02-26
I'm at about the same stage as Allen.  I did check the md5sum of the .iso I used to install Ubuntu, which was fine.  I don't know what else to do.

---

### Post by varunendra on 2013-02-26
> **Objekt said:**
> I'm at about the same stage as Allen.  I did check the md5sum of the .iso I used to install Ubuntu, which was fine.  I don't know what else to do.
Posted on your thread : [http://ubuntuforums.org/showthread.php?t=2120198](http://ubuntuforums.org/showthread.php?t=2120198)

---

