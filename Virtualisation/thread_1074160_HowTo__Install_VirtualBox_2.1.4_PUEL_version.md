---
title: "HowTo:  Install VirtualBox 2.1.4 PUEL version"
date: 2009-02-18
forum: Virtualisation
---

### Post by HotShotDJ on 2009-02-18
The new version of Sun xVM Virtual Box -- version 2.1.4 -- has been released.  This version includes many bug fixes and includes Windows 7 support, 3D Acceleration via OpenGL, and "out-of-the-box" USB support.  Unlike the OSE version that is installable through the standard Ubuntu Repositories, the Personal Use and Evaluation Licensed (PUEL) version includes USB support and easy installation of the Guest Additions.

Most users of the OSE version also install the Guest Additions.  By installing this software, users agree to the PUEL, even though they are using the more limited OSE version.  If you are going to use the Guest Additions, you are agreeing to the PUEL but NOT getting the advantages of the full PUEL version of VirtualBox.

So, you want to install the full version of VirtualBox AND get automatic upgrade notification through the Synaptic Upgrade Manager?  It is as Easy as Falling Of A Log.

**I.  Getting VirtualBox 2.1.4 PUEL edition**

************************************
KDE USERS: To access software sources & software installation in KDE, see [Repositories/Kubuntu]("https://help.ubuntu.com/community/Repositories/Kubuntu") -- These instructions are for Ubuntu with the Gnome desktop environment.  KDE users will use "Package Manager (Adept Manager)" to alter their software sources and add the signing key.
************************************

If you've previously installed the OSE version of VirtualBox, you'll need to completely remove it.  Use System &#8594; Administration &#8594; Synaptic Package Manager and search for "virtualbox" and completely remove any virtualbox related packages.  Right click on the package(s) you want to remove and select "Mark for Complete Removal."  Simply using "Mark for Removal" may leave files behind that could block the installation of the PUEL version.  Click on "Apply" then confirm the changes and click apply again.  When done, go ahead and close Synaptic Package Manager.

Go to System &#8594; Administration &#8594; Software Sources.  Click on the &#8220;Third-Party Software&#8221; tab.  Now, click on the &#8220;Add&#8221; button near the bottom of the window.  Paste the following into the &#8220;APT line&#8221; box:```
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
```If you are running Hardy (8.04 LTS) replace &#8220;intrepid&#8221; with "hardy". At the time of this writing, packages for later versions are not available. If you are using a version older than hardy (such as gutsy, feisty, etc.) you might have trouble getting up-to-date versions of VirtualBox.  Since Ubuntu versions prior to hardy are either no longer supported or will soon reach their [end-of-life]("https://wiki.ubuntu.com/Releases"), this would be a good time to upgrade to at least hardy (8.04 LTS).  

Click &#8220;Add Source&#8221;  Do not close Software Sources yet..

Get the signing key directly from Sun at [http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc](http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc). In Software Sources, click on the Authentication tab and then click on  &#8220;Import Key File...&#8221;   Browse to the location of sun_vbox.asc.  Click on the file and then press OK.  Notice that  a key has been added to Trusted software providers for Sun Microsystems, Inc. (xVM VirtualBox archive signing key).  Now you can close Software Sources.

**II.  Install VirtualBox 2.1.4**

Open System &#8594; Administration &#8594; Synaptic Package Manager.  Click on the Reload button.  Now search for virtualbox (the Quick search box sometimes does not work with third-party repositories, so use the Search button instead).  Click on the check box next to &#8220;virtualbox-2.1&#8221;.  Click &#8220;Apply&#8221; and follow the on-screen instructions.  Once VirtualBox is installed, close Synaptic Package Manager

**III.   Add User(s) to the "vboxusers" Group**

Go to System &#8594; Administration &#8594; Users & Groups.  Unlock  "Users Settings" using the "Unlock" button near the lower right of the box (next to the close button) then click on &#8220;Manage Groups&#8221;

Scroll through the list of group names until you find &#8220;vboxusers&#8221; then click on it to highlight and click on the &#8220;Properties&#8221; button.  You'll see a list of users on your system.  Check off all the users who you will want to give access to VirtualBox.  Do NOT check off &#8220;root&#8221;. After you've made your changes, click "OK" and then close groups settings and user's settings.

A reboot should not be required. Simply log out, and then back in.  If you get an error when you try to start your guest OS, then go ahead and reboot and then try again.  Leave a message on this thread if you find that you need to reboot before you are able to run your virtual machine so that I can change the instructions.

**IV.  Install Guest Additions**

This part of the HOWTO assumes that you have already created a Virtual Machine.  Instructions on how to create a VM and install an operating system can be found [elsewhere]("https://help.ubuntu.com/community/VirtualBox#Using%20Virtual%20Box") and is outside the scope of this HOWTO.  While not required, you will enjoy a much better user experience with your VirtualBox guest operating systems if you install the guest additions. Improved video support and sharing folders with the hostOS are among the benefits of using the Guest Additions. For a Windows guest, start your guest OS. After it is booted up and ready to use, make sure you are in windowed mode (as opposed to full screen), open "Devices" from the menu bar, and select "Install Guest Additions..." Normally, it will start up automatically, but if it doesn't, just open the Windows "start" menu, go to "My Computer" (or "Computer" in Vista) and double click on the CD labeled "VirtualBox Guest Additions."

**V.  Enable USB Support**

Open VirtualBox and click on your Virtual Machine then click &#8220;Settings&#8221; -- In the left panel, click on USB. Check off &#8220;Enable USB Controller&#8221; and &#8220;Enable USB 2.0 (EHCI) Controller". Do this for each VM in which you wish to have USB access.

Here is a brief list of some common USB problems under VirtualBox:

*_My USB keyboard and/or USB mouse is not working or is behaving erratically_*.  DO NOT activate these devices for your virtual machines.  VirtualBox uses virtual drivers for these devices.  Activating them in your virtual machine may cause erratic behavior in both the guest and host OS.  ALSO, for proper mouse integration, you will need to install the Guest Additions (see instructions in section IV of this HowTo)

*_I can activate my USB Hard Drive and/or Flash Drive, but it is not working in the guest OS_*.  You'll need to create a device filter. Before opening VirtualBox, plug in your flash drive and/or your USB hard drive. Open VirtualBox and select your guest OS. Do NOT start the guest, just highlight it. Click on "Settings" in the toolbar and select USB in the left pane. Notice a large white area just below the heading "Device Filters." Right click anywhere in that large white area and select "Add filter from device." Now select your USB hard drive or Flash drive. Notice that the name of the device will now appear in the large white area with a checked box next to it. Repeat for other USB hard drives or flash drives as desired.  In some cases, you'll need to unmount the device from your Ubuntu desktop before starting the guest OS.  Once the guest OS has been started and is ready to use, plug in the USB hard drive or flash drive.  The guest OS should recognize and mount it properly now.

*_When I activate a USB device (such as my USB printer) in my guest OS, I can no longer use it from my host OS_*.  This is normal.  When you enable a USB device, it will be inaccessible to your host OS until you release it from your guest OS.

**VI.  Enable CD Burner and/or DVD Burner**

You're actually better off using tools such as Brasero or K3B in Ubuntu to burn CD's or DVD's ... but if you must use your guest OS, it can be done very easily.  If you are using an external USB CDRW/DVDRW drive, plug it in now. Open VirtualBox and select your guest OS.  Do not start it yet.  Open "Settings" and select "CD/DVD-ROM" from the left panel.  In the right panel, check off "Mount CD/DVD Drive" and then select the "Host CD/DVD Drive radio button.  Select your CDRW/DVDRW drive from the drop down list.  Now, check off "Enable Passthrough."  Click OK.  Start your guest OS.  You should now have full burning support for the drive in the guest.

---

### Post by 02741 on 2009-02-18
can you help me, please?
 this is the specs of my desktop PC Intel(r) Celeron(r)
2.6ghz, 512 MB, 40gig... my pc got slow motion now.i only installed the AWN, Virtualbox.

---

### Post by HotShotDJ on 2009-02-18
> **02741 said:**
> can you help me, please?
 this is the specs of my desktop PC Intel(r) Celeron(r)
2.6ghz, 512 MB, 40gig... my pc got slow motion now.i only installed the AWN, Virtualbox.I'm concerned about the amount of physical RAM that you have in your system.  In order to run a guest OS in VirtualBox, I strongly recommend at least 1 Gig of RAM (preferably more).  With only 512 MB of RAM, you are going to have A LOT of swapping to the hard drive in order for the host OS to keep up with the demands of running both the host OS and the guest OS.  This is creating a serious bottleneck on your system, resulting in the poor performance that you are experiencing.  Upgrading your RAM is really the only way to get things running at a tolerable speed.

---

### Post by mpl34 on 2009-02-19
I have previously installed vista and was under the impression that this software would allow me to boot my vista partition while running linux. Is this correct?

---

### Post by bodhi.zazen on 2009-02-19
Thanks [HotShotDJ]("http://ubuntuforums.org/member.php?u=196293")

I updated the Mega Thread, adding a link to your newest tutorial.

---

### Post by bodhi.zazen on 2009-02-19
> **mpl34 said:**
> I have previously installed vista and was under the impression that this software would allow me to boot my vista partition while running linux. Is this correct?

See the tutorials linked in the mega thread.

IMO booting a physical partition is in "Beta" meaning it can be done, but it is not the default behavior and can cause breakage.

---

### Post by HotShotDJ on 2009-02-20
> **bodhi.zazen said:**
> IMO booting a physical partition is in "Beta" meaning it can be done, but it is not the default behavior and can cause breakage.+1

One ignores the warning contained the the [VirtualBox User Manual]("http://download.virtualbox.org/virtualbox/2.1.4/UserManual.pdf") at their own peril:[QUOTE="User Manual, Page 123"]Warning: Raw hard disk access is for expert users only. Incorrect use or use of an outdated configuration can lead to total loss of data on the physical disk. Most importantly, do not attempt to boot the partition with the currently running host operating system in a guest. This will lead to severe data corruption.
[/QUOTE]

---

### Post by griztown on 2009-02-24
Hi all,

This worked great, VirtualBox is a life saver.  My wife hates my linux installation and kept threatening to force me to put Windows back on.  Now I've got both! 

One issue I had was with my Western Digitial My Book USB external hard drive.  I couldn't seem to get the guest OS to recognize it, in this case Windows XP.  I installed the guest additions, setup the USB stuff in the settings, etc, etc.  It got my printer working but still wouldn't recognize my hard disk.  I found in the device list a question mark next to a USB bus.  Right clicking on it and having it find a driver it got installed no problem.  Once that was solved I had no problems using my USB hard drive.  Thought I'd share this.

Thanks!

---

### Post by HotShotDJ on 2009-02-25
> **griztown said:**
> I found in the device list a question mark next to a USB bus.  Right clicking on it and having it find a driver it got installed no problem.  Once that was solved I had no problems using my USB hard drive.  Thought I'd share this.Thank you for letting us know about this.  Most USB hard drives do not require additional drivers, so I find this strange.  I also have a WD My Book, and never had to install any special drivers for it.  Do you know which driver Windows XP needed to install?  I wonder if it was the regular USB Mass Storage driver -- which would lead the question: Why  didn't Windows XP detect and install it when you activated your USB drive?

---

### Post by binbash on 2009-02-26
Good howto, thanks !

---

### Post by nimishprasad on 2009-02-26
I can't get the mouse to work. I installed Vista in the Virtual Box but it just keeps saying you clicked inside the virtual box and your host key blah blah. My keyboard works though inside the VM.

---

### Post by HotShotDJ on 2009-02-26
> **nimishprasad said:**
> I can't get the mouse to work. I installed Vista in the Virtual Box but it just keeps saying you clicked inside the virtual box and your host key blah blah. My keyboard works though inside the VM.You'll need to install the Guest Additions to get proper mouse integration.  See section IV of the howto.

---

### Post by Green_Grenade on 2009-03-15
I cant get Virtualbox 2.1.4 Only 2.0.4... Tried the reload button and restarting still.. nothing.. can you help?!?

---

### Post by welby on 2009-03-20
Mine took a little while to show up but eventually did. The only problem i have now is getting my flash drive to be recognised in the VM.

---

### Post by Savta Savta on 2009-03-25
Maybe you can help me with my USB devices:
I successfully installed  VirtualBox 2.1.4.PUEL on my Ubuntu 8.10 Multi Media System and set up a Windows XP virtual machine. In the settings I enabled all the USB devices and made sure that I was added in the vboxusers. All the USB devices appear in the list of USB devices, however none of them are recognized as active by the guest OS. I tried disconnecting them/unmounting them, restarting the virtual machine and reconnecting and still have no success. 
Any suggestions?

---

### Post by mikhmv on 2009-04-29
I have same problem like Savta Savta but in Jaunty with VirtualBox 2.2.2

P.S. Resolved by: [http://ubuntuforums.org/showthread.php?t=1015763&highlight=virtualbox+usb](http://ubuntuforums.org/showthread.php?t=1015763&highlight=virtualbox+usb)

---

### Post by calvinps on 2009-05-02
> [http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc](http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc)

That link is broken

---

### Post by krippa on 2009-07-27
Hi,

I am running Ubuntu Jaunty 9.04 64-bit and virtualbox 2.1.4_OSE and I can't even see "USB" on the left side of the settings for a given virtual machine.

Any ideas?

---

### Post by Rob Maurer on 2009-08-07
I am having a similar problem (WD Passport 3200 external USB hard drive, USB power only) in my Windows 7 guest, Ubuntu Jaunty host. The Win7 OS sees it in "Devices and Printers" as a "External HDD" but not under "Computer" at all. Updating drivers did not change this problem (I tried what's listed here [http://social.technet.microsoft.com/Forums/en-US/w7itprohardware/thread/3544ebe2-5339-441b-b65d-60c8c399fa4f](http://social.technet.microsoft.com/Forums/en-US/w7itprohardware/thread/3544ebe2-5339-441b-b65d-60c8c399fa4f))

Any other ideas? How exactly did you get XP to show you a question mark, I'm curious?
Thanks,
Rob Maurer

---

### Post by rldev on 2009-08-24
I am using Jaunty 64bit and Vbox 3 64bit. While I am able to get USB to work, I am unable to get USB 2.0 running. VBox sees everything, but the usb devices do not work. If I disable 2.0 support, then there is no problem.

---

### Post by bn1 on 2009-09-13
> **krippa said:**
> Hi,

I am running Ubuntu Jaunty 9.04 64-bit and virtualbox 2.1.4_OSE and I can't even see "USB" on the left side of the settings for a given virtual machine.

Any ideas?

I have exactly the same problem :( (same linux, same virtualbox version..) Even I can't see any USB device on "usb device list" (via virtualbox menubar - there I can see (in every case empty) usb device list)

---

### Post by krippa on 2009-09-13
I solved this problem by installing a newer version of virtualbox. I think the 2.1.4_OSE doesn't really contain this functionality but the in the 3.0.4. that I downloaded from the virtualbox site, this works out of the box...

---

### Post by bn1 on 2009-09-14
> **krippa said:**
> I solved this problem by installing a newer version of virtualbox. I think the 2.1.4_OSE doesn't really contain this functionality but the in the 3.0.4. that I downloaded from the virtualbox site, this works out of the box...

:lolflag:..I've done the same thing last night! So, now I can see USB device list with usb devices, but they are grey.. Also I can see USB options in wm settings :-) but for now it's enough for me..

---

### Post by rldev on 2009-09-17
I can use usb, but not usb 2.0. When I check usb 2.0, the systems sees the devices, but can not talk to them. Virtualbox 3.04 64bit

---

### Post by bn1 on 2009-09-26
ehh..I don't know, what's changed, but now it works fine! I've done really the same things as before..

&#8594; enable USB support &#8594; enable USB 2.0 &#8594; add devices to filter list

(tested with BackBerry phone and Livescribe pen :))

---

### Post by kulambi on 2009-12-14
Thanks for the detailed HOW TO. I installed Virtualbox 3.1 on Ubuntu 9.10 and the menus dint appear even after logging out and logging in. I think this HOW TO needs to be updated on how to launch the virtualbox in such cases. The executable location is /usr/bin/VirtualBox

---

### Post by rob22941 on 2010-04-18
I just installed Windows via virtualbox 3.0.8, I can't get the USB to work. I've tried both your work arounds and they aren't working. If I uninstalled my virtualbox 3.0.8 and installed 3.1 would I run into any issues with the windows I just installed? Is that my issue? I'm running intel 32bit, if it makes any difference. I experiment on this pc before my better one haha.

---

