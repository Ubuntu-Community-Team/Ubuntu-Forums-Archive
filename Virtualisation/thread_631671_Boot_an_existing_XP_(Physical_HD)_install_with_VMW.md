---
title: "Boot an existing XP (Physical HD) install with VMWare"
date: 2007-12-04
forum: Virtualisation
---

### Post by gumbi18 on 2007-12-04
After some digging around the interweb a while back I discovered that there is two separate methods to running an existing Windows partition in VMware.

I take credit for none of these websites- 
[http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/]("http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/")
This I have tested and does work, however as McMonarch mentioned there is issues with using the same Windows partition. There is a method around this which I will mention further down.
[http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/]("http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/")
Another example of the VMware server method.


[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html")
This method involves a little bit of trickery with the program 'parted'. The instructions are clear. I couldn't get this method to work mainly because of my slightly dodgy MBR.

 To get around the activation problems with running Windows on effectively two machines I discovered this tutorial that works, I have tested and confirmed this myself.
[http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/]("http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/")
This may be technically illegal in most countries so I don't endorse it, but I am willing to make the information available to the community.

Hopefully that helps the previous posters.


[color=blue]EDIT: Thanks [/color][gumbi18]() [color=blue]for collating this information.[/color]

[img]http://img381.imageshack.us/img381/4226/xubuntulogo2small0lj.png[/img][size=4]*[color=navy][font=times]bodhi.[/color][color=darkgray]zazen[/font][/size][/color]*

---

### Post by Victory on 2007-12-06
I'd like to note that the instructions for the first method are for users with SCSI hard drives. Using the SCSI instructions on a IDE drive often results in BSODs when launching Windows in the VM. For those using IDE a set of instructions are available here: [http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu](http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu)

---

### Post by toobuntu on 2007-12-10
For the more adventurous, a gentleman by the name of Bob Brandt scripted the whole process - including a modification to the boot process - on the SUSE (SLED 10) Wiki:
[http://wiki.novell.com/index.php/SLED10_Dual_Boot_with_VMware_Player]("http://wiki.novell.com/index.php/SLED10_Dual_Boot_with_VMware_Player")

It's based in part on Blackmh's guide.  Obviously, there may be slight variations for Ubuntu, but if someone feels like making the modifications, this could greatly simplify the process for many people.

Another site giving instructions for this process, with many comments, is [http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition]("http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition").

---

### Post by jimmydean on 2008-01-25
I went through this and had everything working perfect for vmware. I later found I had issues with youtube playback in Ubuntu, so I followed the steps laid out in the multimedia thread and got my youtube issues resolved.

Now all I get is a black screen after selecting the hardware profile for XP when trying to start the vm.

I rebooted into XP to make sure nothing was wrong with the native drive, then I tried creating a new VM using the XP partition, same results. It never loads the login screen for XP.

Any ideas?

---

### Post by dark_phantom on 2008-01-25
I played around with this yesterday for a few hours.  It's a total pain in the ****, since XP is so sensitive as to how it handles drivers.  I was unable to successfully launch XP, I kept getting the blue screen of death.  It appears that the more matured the installation is, the harder it is to get it to work right.  I need to spent more hours on this though, I'm not giving up yet.

---

### Post by jimmydean on 2008-01-25
This was the tutorial that got my youtube issues resolved: [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

But I have gone so far as removing and reinstalling VMWare to no avail. I would rather not undo all the mutimedia changes I did, but I might have too.

---

### Post by big dizzle on 2008-01-27
I just got this working after a couple of failures, so if you are having any problems w/using vmware to run an os installed on an existing partition, here is what i suggest.

1) Uninstall any vmware stuff that you have (assuming your vmware isn't working)

2) Use synaptic and search for vmware, check all the vmware stuff (probably not needed, but I mark them all to make sure) and install it.
NOTE:  It will ask for a serial number, go to the vmware website and register to get one: [http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)

3) Follow the steps in this AWESOME howto:
[http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu](http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu)

WARNING:  If you look towards the end of the howto in step 3, it mentions that b/c the vm boots in grub, and if you let grub boot ubuntu (which it does by default unless you changed the menu.lst file) then it could potentially damage some of your files.  So don't just start the vm and let it run, PAY ATTENTION!

---

### Post by DamagePlan on 2008-01-27
Is this possible if your running vista?

In vista you cant create hardware profiles.

Thanks

---

### Post by rosegarden78 on 2008-01-27
VMware is commercial product try open source much easier to use: [http://ubuntuforums.org/showthread.php?t=679884](http://ubuntuforums.org/showthread.php?t=679884)

---

### Post by jimmydean on 2008-01-28
I was able to resolve my issue by removing the xserver-xgl package. I am going to see if there are some settings I can use that will allow me to use both. But for now I'm happy to be functional.

---

### Post by Lumenos on 2008-02-11
> **gumbi18 said:**
> 
[http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/]("http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/")
This I have tested and does work...
I was able to boot an XP installation that is on the end of an extended partition (250GB SATA hard disk) using this guide. (It boots XOSL and from there I boot the XP partition.) However you don't need to download VMware tools and those may be out of date anyway. Go to the menu at the top of the window running VMware Server while you have your virtual machine booted, select VM, then "Install VMware Tools".

Thanks for the guide! I tried a few others using VMware Player and they didn't work for me. This one definitely deserves the sticky. Just wish I had found it earlier.

---

### Post by sirlancelot on 2008-02-11
Thanks for the links! I've been wanting to do this for a while, but always got permissions errors when trying to add a physical disk as a drive...

---

### Post by Lumenos on 2008-02-12
(Update: There are apparently a few ways to fix USB for Ubuntu and I am having different problems with some of my USB devices. I posted more info in [[COLOR="Blue"]this article in my wiki[/COLOR]]("http://lumeniki.scribblewiki.com/Fixes_for_USB_problems_with_virtual_machines").)

To enable USB first go to "Edit virtual machine settings" and add USB. 

WARNING: I have no idea if this might screw something else up. To get USB working on Gutsy (7.10) I had to use instructions I found at the end of [[COLOR="Blue"]this thread[/COLOR]]("http://www.vmware.com/community/thread.jspa?threadID=66096&tstart=0"). I had already installed VMware tools as I describe above. Dismount and disconnect all drives. Shut down any virtual machine. Next I did a ```
sudo rmmod usb-storage
``` (I'm not sure all that is necessary.) Next do ```
sudo mount -t usbfs none /proc/bus/usb
``` and add the following line to the /etc/fstab file: ```
usbfs /proc/bus/usb usbfs auto 0 0
``` You can edit fstab with ```
sudo pico /etc/fstab
``` then use "CTRL + o" to write it and "CTRL + x" to exit. 

I guess Ubuntu 7.10 mounts USB devices in a different place from what VMware expects. Does anyone know why Ubuntu mounts USB devices where it does, or whether changing this will mess something up?

There was one other thing I forgot to mention when I first got it to boot. My USB mouse was not working. I thought the USB keyboard wasn't working either because I was trying to use the arrow keys to make a selection in the 1st dialog box, but I was able to use the tab key to make that selection. After rebooting Windows the mouse worked also. You might have to use the Windows Key to reboot, but I think the prompt allowed me to do so.

---

### Post by Lifeless1 on 2008-02-14
I can't install VMWare.:(:cry::confused:

---

### Post by tobydeemer on 2008-02-14
Hi-

I got things kind of rolling, but when the Grub screen loads, it skips the menu part and goes right to loading the kernel. Of course I panic and shut down all VMware stuff as soon as I see that happen, and things are still ok. But does anyone know why it would skip the selection screen? 

I did forget to boot into windows and create a new hardware profile, although I did load the SCSI drivers. Could that be the issue? Any ideas would be awesome. Thanks.

---

### Post by Lumenos on 2008-02-24
> **Lifeless1 said:**
> I can't install VMWare.:(:cry::confused:
[[COLOR="Blue"]Here are my notes on Azimi's guide[/COLOR]]("http://lumeniki.scribblewiki.com/Boot_an_existing_Windows_installation_as_a_virtual_machine"). It tells you how to install VMware Server also.

---

### Post by Dojan5 on 2008-02-26
WAIT, does this mean that i would be able to install and Boot win XP like a normal XP without haveing to go through Ubuntu as most Virtual Machines?
Cause VMWare is Virtual Machines, right?

---

### Post by Dojan5 on 2008-02-26
> **tobydeemer said:**
> Hi-

I got things kind of rolling, but when the Grub screen loads, it skips the menu part and goes right to loading the kernel. Of course I panic and shut down all VMware stuff as soon as I see that happen, and things are still ok. But does anyone know why it would skip the selection screen? 

I did forget to boot into windows and create a new hardware profile, although I did load the SCSI drivers. Could that be the issue? Any ideas would be awesome. Thanks.

Not anything about press ESC to open a menu?
If else, open up the terminal and run ```
gksudo gedit /boot/grub/menu.lst
```
And a bit in the top there should be somerthing with time in sec, if it is on zero it wont have a menu...

---

### Post by iheartubuntu on 2008-03-13
On the website... [http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu](http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu)

Im trying to run the setup, but during the Windows steps, Im stuck on the highlighted part...
> 
Now to configure the IDE drivers to work with VMWare:

    * Click Start > Control Panel > Systems
    * On the Hardware tab, select Device Manager
    * Select the IDE Controller object and edit its properties
    * Click the Driver tab, then click the Update Driver button
    * Click Next
    * [B]Select Display a list of the known drivers, then click Next.
    * Select Standard Dual channel PCI IDE controller instead of the driver that matches your physical IDE controller.[/B]
    * Click Next, then click Next again.
    * Click Finish, then Close.

I dont have any option to "select a list of known drivers" so I cant "select standard dual channel PCI IDE" What else can I do now?

Sounds like people got this working too :| Im stuck at the blue screen of death while trying to boot up XP virtually.

---

### Post by Kiri on 2008-03-14
Is it possible to do the same thing in virtualbox? (run an existing XP install as a virtual machine)

Running windows this way (in VMWare), is there ability to use the windows graphic drivers in the VM? thus enabling the full use of high end graphics programs (photoshop etc, even 3D)?

---

### Post by mahasmb on 2008-03-16
Everything works fine until Windows loads up and I get a BSOD like three seconds later.

I'm using Gutsy Gibbon with Windows XP Home. Is it because I'm using Windows XP Home instead of Windows XP Professional? FAT32 instead of NTFS?

Please help :(.

---

### Post by louca on 2008-03-16
Sounds like you didn't install the SCSI drivers on the correct hardware profile.

Why isn't my sound working. :?

---

### Post by mahasmb on 2008-03-17
Okay, forget that Windows gives me a BSOD for now. I have even bigger problems.

Because VMWare wasn't working as I'd like I tried installing Virtual Box, but I didn't finish the  Virtual Box installation due to an error*. I then needed to restart. And after I did, neither my sound nor Compiz-Fusion worked anymore. What in the world went wrong???

*The Virtual Box error:

E: virtualbox: subprocess post-installation script returned error exit status 1

I used these instructions: [http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu](http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu)

I've already uninstalled both VMWare and Virtual Box, but neither have helped. Even after restarting.

And now GNOME keeps on restarting and I get this error: The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".

And I also get this error with Nautilus: 
**Nautilus can't be used now, due to an unexpected error.**
Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem.

---

### Post by louca on 2008-03-17
There may be a more "fancy" way of approaching your problem but here is what i would do:

Uninstall both virtual machine programs, then:

```

sudo apt-get --purge remove gdm ubuntu-desktop
sudo apt-get install gdm ubuntu-desktop
```

To uninstall then reinstall gnome.

It is what I would do with my limited experience, you should get an opinion from someone who knows a bit more first. :)

---

### Post by mahasmb on 2008-03-18
> **louca said:**
> Sounds like you didn't install the SCSI drivers on the correct hardware profile.

Why isn't my sound working. :?

Okay, I fixed my previous problems, but I still get the BSOD when I try to boot Windows in Ubuntu. Also, I'm not using SCSI, I'm using IDE.

Anyone have any ideas about the Blue Screen of Death (BSOD)? I thought it may because Windows always runs a chkdsk at boot but I disabled that and I'm still getting the BSOD.

---

### Post by dbsoundman on 2008-04-01
Ok, I just tried this using the method listed on the blog page (can't remember which one it is, I had to use waybackmachine.org to find it), and I am getting a GRUB error 17 when I try to start the VM. I wasn't sure which partition contained my actual Linux installation, so I gave it access to both partitions it could be (one is home, one is filesystem). I figured that way I could get to the actual saved files that way anyway.

Anyway, what's the deal with the error? I almost remember reading about that error somewhere, but I can't remember where or how to fix it...

-Dan

---

### Post by jakornblum on 2008-04-04
If you have Windows XP Home Edition, use the following method:
[http://ubuntuforums.org/showthread.php?p=4644845](http://ubuntuforums.org/showthread.php?p=4644845)

---

### Post by dasunsrule32 on 2008-04-05
> **Kiri said:**
> Is it possible to do the same thing in virtualbox? (run an existing XP install as a virtual machine)

Running windows this way (in VMWare), is there ability to use the windows graphic drivers in the VM? thus enabling the full use of high end graphics programs (photoshop etc, even 3D)?

The only way that I know of right now is VMGL, it will give you full OpenGL support inside your VM machine. Check out the website: [http://www.cs.toronto.edu/~andreslc/xen-gl/]("http://www.cs.toronto.edu/~andreslc/xen-gl/")

Hope that helps somewhat, as of now, I have not found anything that will emulate Direct3D well. If I am wrong, please correct me. :-\"

---

### Post by dbsoundman on 2008-04-06
jakornblum, are you saying this is a solution for my Grub Error 17 issue, or for someone else?

-Dan

---

### Post by andrewisett on 2008-04-08
> **shirteesdotnet said:**
> 

I dont have any option to "select a list of known drivers" so I cant "select standard dual channel PCI IDE" What else can I do now?
.

Did you have any luck with this?  I run into the same problems, then receive a stop error 07B when starting the machine in VMware.

BTW - machine is an HP dc5750 - which has an ATi based chipset.

---

### Post by rax_m on 2008-04-10
Hi 

I tried to use this method : [http://mazimi.wordpress.com/2007/06/...-within-linux/](http://mazimi.wordpress.com/2007/06/...-within-linux/)

However, when I get to step 12(?) where I have to select the partitions for linux and windows I run into a problem. On my setup, I have linux and windows on separate drives. Like so:
Linux, swap : sda
Windows, /home : sdb

I can't really change this as it is the way the company has setup the computer. 

Any ideas how I select the correct partitions? 

Thanks
Rax

---

### Post by dbsoundman on 2008-04-10
I'm having 3 interesting issues with my physical HD VM:
1) windows appears to not be grabbing the mouse for some reason, so I have to use the keyboard only.
2) it appears that it can't find the network (or maybe I need a wired connection to take care of #3)
3) windows is telling me that I must "activate" it before I can log in, meaning it needs to connect to microsoft and do something.

Am I right in thinking that I need a wired ethernet connection to do this? That doesn't solve my mouse cursor problem though. Any suggestions?

Thanks,
Dan

---

### Post by mallegonian on 2008-04-13
@dbsoundman: Did you install the vmware tools? Is the network set to bridged or NAT?


[EDIT]  I read the howto linked from the 1st post, and found the part about adding the linux partition as well, which I totally forgot about. Trying that now.
[EDIT2]  Pwned. That was why, but now I get a bluescreen on boot. Working on that now, probably the SCSI drivers. Anyone have a way to make it so that there is no need to have grub wait forever at boot, and it boots straight to windows? But NOT when not virtual?

For reference, my original problem:
I am using Ubuntu 7.10, fully updated, and the latest vmware 6.x.
I have a sata drive in my laptop so changing it to IDE is not an option.

I set up a preexisting 8g Win XP Pro installation in vmware, running as root so as to be able to access the partition.
When I boot up the virtual machine I get Grub error 17. I googled it and found only things about LBA and drive orders. The vmware bios won't let me change the drive off of auto, and it is detected as the only HD, the secondary master.

I would first expect the secondary master detected vs. sata 1 real to be the problem, but can't find any way to change it.

---

### Post by dbsoundman on 2008-04-14
The problem I'm having now is twofold:
1) Windows doesn't seem to see my mouse, so I can't click on anything.
2) Windows wants me to validate my installation or something like that. I think for one my problem is that I haven't yet done that with a wired LAN connection, but I'm wondering if it will work either way. Nothing weird happens when I boot into Windows at startup, but the VM is not so hot yet.

-Dan

---

### Post by mallegonian on 2008-04-15
Is your LAN in the VM set to NAT?

I solved my problem by installing the SCSI driver.

---

### Post by dbsoundman on 2008-04-15
I've tried LAN bridged and NAT. I did finally get the validation thing done, all I needed was a wired network connection, but I still don't have any mouse control (and yes I am clicking into the VM). Additionally, it seems to consume an inordinate amount of resources. I gave it 512MB of RAM to use out of the 1 or 2 (can't remember) GB of RAM on the laptop, but it also seems to just eat my processor speed, which is weird because it's a dual core processor and usually works fine. I'm not even running anything in Ubuntu, but everything (both OSes) get really sluggish and almost freeze. Windows actually usually does freeze when I try to install VMware Tools. It's just strangely slow, and I don't know why; maybe because I have both OSes on a single drive but different partitions? Any help?

-Dan

---

### Post by dbsoundman on 2008-04-15
OK, I finally got it running. It was extremely slow, and it's still not really fast, but I finally got it to behave long enough to get VMware Tools installed (it took a lot of waiting), and now the mouse works and everything. The only issue I still have is I need to figure out how I can access my shared "media" partition from the Windows VM. It is a partition that has my /home directory, which is also used by Windows for my documents and such. When I try to go direct in the Windows VM, it says that the drive is not formatted. I have already installed Ext2IFS, so that's not the issue I don't think. What do I need to do to set this up?

Thanks,
Dan

---

### Post by mallegonian on 2008-04-15
DO NOT mount the same partition from two operating systems at the same time. This could seriously mess up the filesystem.

I am also having CPU time problems. I gave windows one cpu, but it totally freezes linux when it is thinking at all. On the other hand this is the fastest windows has ever run for me...

Do not use ext2ifs, because this will try to mount it, which is only safe if it is exclusively or read only for both. Open the vmware tools dialog inside the vm and on one of the tabs there is a shared folder option.

You may be able to drag and drop stuff into the vmware window and it will copy it. For shared folders I'm not sure, because in my vm it won't let me enable them. I really don't know why. This would be very helpful for programs that certain parts like updaters only work in windows but the actual program runs fine in wine.

---

### Post by dbsoundman on 2008-04-15
I didn't think the double mount would work...

I recall that I was able to set up a shared folder one time on a different VM setup...it was a Windows 2000 install that I did through VMware though, it wasn't pre-existing. I used it to rip music from CDs, so I would rip them into a folder in windows, which was shared via a networked folder in Ubuntu. So when the VM was running, I could open that folder in Ubuntu and get my windows documents. I guess what I need to figure out is how to do the opposite; set up a shared folder that I can access from the VM Windows to get to the files in the Ubuntu /home partition. Does that make sense? How do I do it?

-Dan

---

### Post by mallegonian on 2008-04-15
I can't explain it too well right now as I just managed to get  windows to keep BSOD'ing on boot again. something about "login", and it's really short, so idk.

Google it. There should be something in the vmware tools dialog in the virtual windows.

---

### Post by dbsoundman on 2008-04-15
I'm actually halfway there; I figured out how to get my /home folder shared via samba, so that's all set. I just need to figure out what I need to put in the Windows "add network place" thing to get the shared folder on there. I'm not exactly sure what the folder's address should be.

-Dan

---

### Post by dbsoundman on 2008-04-17
OK, I still can't get the windows network connection thing down. I go My Network Places>Tools>Map Network Drive, and I put in \\<my ip address>\dan (which is my shared folder), and it prompts me for a username and password. I'm not quite sure what I should be putting here, but the only user on my laptop is "dan", so I enter dan and my password, but it doesn't work. What am I doing wrong?

Thanks,
Dan

---

### Post by dbsoundman on 2008-04-17
I figured it out! I was thinking it was some sort of password/username issue. I did some searching, and found this solution:

```
sudo smbpasswd -a 'username'
```

Then, enter a password for your username. Go back to windows, map the drive with \\<your ip address>\<share>, then the username is just your username and whatever password you entered for that command. Easy! Now I have a Z:\ drive in Windows and life is good.

-Dan

---

### Post by anthill27 on 2008-07-16
Does anyone know if this works with RAID. I'm dual boot Ubuntu 8.04.1 and XP on two 500GB HDD in RAID 0.

It's set up like this using dmraid,
/dev/mapper/isw_chijicei_ge = RAID name (used dmraid for ubuntu)
/dev/mapper/isw_chijicei_ge1 = 906GB Ubuntu
/dev/mapper/isw_chijicei_ge2 = 4GB SWAP
/dev/mapper/isw_chijicei_ge3 = 90GB Windows XP

I have VMware Workstation installed.
Can i reference the XP partition?

---

