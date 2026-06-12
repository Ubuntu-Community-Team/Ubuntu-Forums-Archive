---
title: "Virtualbox USB Devices not functional in guest"
date: 2008-03-29
forum: Virtualisation
---

### Post by Adman on 2008-03-29
Hi all

Background
-----------------

I have gone through many of the steps to get Virtualbox to recognize my USB devices.  I have:

edited the /etc/init.d/mountdevsubfs.sh
added the USB user group
edited the /etc/udev/rules.d/40-permissions.rules
Have "busy" on VBoxManage list usbhost as follows:

UUID:               56aa82bd-2aaf-4e7e-8784-7a8334681294
VendorId:           0x0d9a (0D9A)
ProductId:          0x0004 (0004)
Revision:           1.0 (0100)
Manufacturer:       RTX Telecom A/S
Product:            Cordless USB Phone
SerialNumber:       00000000
Address:            /proc/bus/usb/002/011
Current State:      Busy

Problem
-----------
**My problem is** that when I boot into Windows guest (from Gutsy), the device is said to be malfunctioning and Windows cannot recognize it.  The cordless phone also says that the "PC is unavailable".

I have tried to reboot/reconnect...

Can anyone help please?

Thanks

---

### Post by VitaLiNux on 2008-04-05
> **Adman said:**
> Hi all

Background
-----------------

I have gone through many of the steps to get Virtualbox to recognize my USB devices.  I have:

edited the /etc/init.d/mountdevsubfs.sh
added the USB user group
edited the /etc/udev/rules.d/40-permissions.rules
Have "busy" on VBoxManage list usbhost as follows:

UUID:               56aa82bd-2aaf-4e7e-8784-7a8334681294
VendorId:           0x0d9a (0D9A)
ProductId:          0x0004 (0004)
Revision:           1.0 (0100)
Manufacturer:       RTX Telecom A/S
Product:            Cordless USB Phone
SerialNumber:       00000000
Address:            /proc/bus/usb/002/011
Current State:      Busy

Problem
-----------
**My problem is** that when I boot into Windows guest (from Gutsy), the device is said to be malfunctioning and Windows cannot recognize it.  The cordless phone also says that the "PC is unavailable".

I have tried to reboot/reconnect...

Can anyone help please?

Thanks
Have you got virtualbox-ose installed? That version doesn't have usb support. Try the latest version of Virtualbox.  Download it from [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI").

---

### Post by VitaLiNux on 2008-04-05
If that worked for you, don't forget to come back and tell us!

---

### Post by Adman on 2008-04-08
hey!

Thanks a lot for the advice VitaLiNux.  I was actually using the version directly from the VirtualBox site - it has USB support.  Unfortunately, I'm still having trouble getting the devices recognized in the host.  VirtualBox says they're captured, and some of the devices do detect in windows (while others don't), but installing them doesn't work...

Thanks

---

### Post by hitspace on 2008-04-08
im having the same problem and i keep getting this error 


Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
0x80004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}

 
how exactly do you fix this ? i dont exactly understand which lines of  code that need to be changed and what not . can this be solved with a few commands in terminal ?

---

### Post by Adman on 2008-04-08
> **hitspace said:**
> im having the same problem and i keep getting this error 


Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
0x80004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}

 
how exactly do you fix this ? i dont exactly understand which lines of  code that need to be changed and what not . can this be solved with a few commands in terminal ?

hitspace,

That is not the same problem that I'm having.  Your problem is easily solvable:

[n00buntu Tutorial]("http://n00buntu.blogspot.com/2007/11/tutorial-ubuntu-compiz-virtualboxmagic.html") (page 1 of tutorial)
and
[http://ubuntuforums.org/archive/index.php/t-614576.html]("http://ubuntuforums.org/archive/index.php/t-614576.html")

Essentially, you need to do a :
sudo gedit /etc/init.d/mountdevsubfs.sh 
(you're enabling usbfs)

Find the following lines, and uncomment the bottom 4:
     # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb

Reboot Ubuntu, and the problem should be fixed.  Make sure you downloaded Virtualbox from the Virtualbox site (rather than the repositories)

Hope that solves your problem :)

---

### Post by hitspace on 2008-04-08
uhh not to try to look stupid but what do you mean uncomment the bottome 3 lines. u mean in the code right ? uhh i dont know how to 
get to it . and to uncomment i need to get rid of the pound sign correct ?

---

### Post by Adman on 2008-04-09
Hi

You should read those tutorials since they will give a more in depth set of instructions... But, do you know how to open up a console window ?  Go to Applications --> Accessories --> and click on Terminal.  You should see a command-line window open up.

Then, you type: ```
sudo gedit /etc/init.d/mountdevsubfs.sh 
```
into the console window.  It will prompt you for your password, so type that in.  After this, an editor will open up (since you requested 'gedit'.  

Scroll down in the file until you see those lines that I mentioned above, starting with the comment: 	
# Magic to make /proc/bus/usb work

Now, the '#' symbol (hash/pound sign) essentially defines the line as a comment.  By removing that symbol, you will uncomment the line.  Be careful to remove only the # symbol though,

You mentioned 3 lines, but I actually said the bottom 4 lines - so be careful with this.  In the end, it should look something like this:

```
	#
	# Magic to make /proc/bus/usb work
	#
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
}
```

Save and exit.  A reboot should fix the error you're having.

Cheers

---

### Post by hitspace on 2008-04-09
wow thanks ill try it . i knew what you meant :) just wanted to make sure again .

---

### Post by vcarbon on 2008-04-09
At this point I have uncommented the lines and ran that command. I added my device to the USB devices in the Virtual box setting and booted into windows. Windows seems to load a usb driver but my devies is not showing up in the MyComputer screen. Please advise me on my next steps. I saw something about adding a usb group? BTW I did add myself to the vbox group.

Thanks

update 43min later

added the usb group and also add the line for fstab still no luck

it should only take 43mins till Im up in running total I spent all day doing this...I gave up on converting my vmware image now the usb doesnt work

helppppppppppppp

19mins later

Im upgrading to hardy...its going to break my firefox extentions and who knows hat else but I hear usb works gawd and I said I was going to wait to upgrade lol

dunno how much time has passed

upgraded to hardy still doesn't work, at least now it is seeing my device in windows although I still can access it. BTW this may have worked in Feisty if I would have gotten my group id correct. well I think Im going to install windows  jk...this non free version seems to mess up my blue tooth adapter which from what I gather is on my USB bus, seems windows is finding the drive but it doesn't show up in my Mycomputer screen...500GB seagate external usb drive formated NTFS or what ever that format is. I going to change my id to the usb group and see if that helps...

more time goes by

well I decided to try another drive and it WORKS!!!. The drive I used is formatted fat32 and seems to be quite available in general. The 500GB NTSF seems to need to be mounted alot and doesnt show up much. I think I will reformat Fat32 and see if that works.

As a reminder for all who read this, using hardy, I used [http://reachbeyondgrasp.blogspot.com/2007/04/how-to-install-virtualbox-in-ubuntu.html](http://reachbeyondgrasp.blogspot.com/2007/04/how-to-install-virtualbox-in-ubuntu.html) and used the non-free feisy repositories to install making sure I had the proper kernel driver installed.

---

### Post by milky2313 on 2008-04-15
I'm having similar problems running Windows XP on a virtualbox machine under Ubuntu 7.10. I'm using virtualbox 1.5.6 by the way...

I did the edting to fstab to get usbfs to work.  I also took care of the permissions and my virtualbox will load the usb keyboard and jumpdrive that i have.  The only thing that i can't get to work is my HP Photosmart 7400 printer.  Windows just gives me the message that the device is malfunctioning and cannot be recognized.  Looks like it's not a permissions problem like most people have had trouble with.  Any ideas?...

---

### Post by milky2313 on 2008-04-15
**Update**

Looks like my problem was just a bug with virtualBox.  All I did was disable the USB 2.0 support in the settings of my virtual machine.  After that it all worked perfectly!!

---

### Post by chiacchio on 2008-05-24
Wow!

Thank you man! I was looking to use my Ipod on VirtualBox. With your tip, finally it works. Thank you.

---

### Post by huffy318 on 2008-06-28
For others that see captured but can't see the device:  I found out thet VirtualBox can capture the device even if the Windows usb driver is not functioning.  This makes sense, actually, but didn't occur to me at first.

The answer for me, quoted from this thread [http://ubuntuforums.org/archive/index.php/t-541195.html](http://ubuntuforums.org/archive/index.php/t-541195.html) was: "uninstall the USB driver (update driver in device manager didn't help), select Install new hardware and just wait for the correct driver to be installed. All this after mounting the Guest additions image of course."

---

