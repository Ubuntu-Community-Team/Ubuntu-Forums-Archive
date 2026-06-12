---
title: "I can't figure out how to get full screen. Please help!"
date: 2024-05-25
forum: Virtualisation
---

### Post by pwilliams90 on 2024-05-25
Hello, I want to start out by saying I am very new to Linux and virtual machines. I am trying to learn some new things here so please don't bite my head off. I have ubuntu 22.04 LTS running on VMWare workstation pro 17. I have been able to get everything up and running so far, however I cannot for the life of me figure out how to get full screen resolution. When I type in xrandr, this is what I get:
$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 200, current 1176 x 885, maximum 1176 x 885
default connected primary 1176x885+0+0 0mm x 0mm
   800x600       60.00    85.00    75.00    72.00    56.00     0.00  
   1152x864      75.00     0.00  
   1024x768      85.00    75.00    70.00    60.00     0.00  
   1024x576      60.00  
   832x624       75.00  
   960x540       60.00  
   864x486       60.00  
   640x480       85.00    75.00    73.00    60.00     0.00  
   720x405       60.00  
   720x400       85.00  
   640x400       85.00     0.00  
   640x360       60.00    59.00  
   640x350       85.00  
   320x240        0.00  
   400x300        0.00  
   512x384        0.00  
   854x480        0.00  
   720x480        0.00  
   720x576        0.00  
   320x200        0.00  
   800x480        0.00  
   1176x885       0.00*
 If I set the monitor settings in VMware display section then power on the VM, I am able to login, but I get this error "The virtual machine could not be changed to the selected monitor layout. If you just added a monitor to the host computer, you must power off and power on the virtual machine to use that monitor." and the screen goes black.
I have gone into the grub menu and did the "nomodeset" input next to the quiet splash. 
I have installed the vmware tools but haven't noticed any changes. 
I have updated the nvidia drivers to 535 version. I have nvidia geforce  RTX 3600 and intel uhd graphics 770
I have dual monitors both are 1080p 75hz HDMI monitors.
I do not really know what else to try and do. 
Any help would be greatly appreciated.

---

### Post by TheFu on 2024-05-26
Not really a Linux question. Mostly a VMware question.  I haven't used VMware Workstation since the 1990s, but almost all of the GUI-based hypervisors like it work the same way.

First, the actual GPU doesn't matter. The VM doesn't see it.  It sees a virtual GPU only.

With the VMware Tools installed (and updated after every new kernel installed/patched), resizing is normally accessed from a menu in the top-center of the window containing the VM.  You may need to move your mouse up there for the little icon to be displayed. Click that, then other menu options will be displayed.   There must be 500 youtube videos that will show this.  Look for "Full Screen" as the option.

xrandr is for X/Windows.  Are you using X/Windows?  It is quite possible you are not and Wayland is being used.  Before you login, but on the login screen, there is usually a gear-tool, click on that to choose the X/Windows (xorg) display server.

BTW, when you are in full screen mode, you'll need to know the keyboard chord to switch out of full-screen mode. This is set either globally in VMware Workstation settings or for the specific VM in those settings. IDK which.  I like to override the default to use alt-F12 - it is out of the way and unlikely to be accidentally hit.

And if this isn't it, you should use that commercial support you paid for - call VMware. Bet the answer take them less than 30 seconds, after you spend 10 minutes on hold and 5 minutes proving you have a legal license.  Paid customers come first, right?

BTW - google found this: [https://docs.vmware.com/en/VMware-Workstation-Player-for-Windows/17.0/com.vmware.player.win.using.doc/GUID-291EA0CB-D11F-456C-9A3C-F1D69BEA6B0E.html](https://docs.vmware.com/en/VMware-Workstation-Player-for-Windows/17.0/com.vmware.player.win.using.doc/GUID-291EA0CB-D11F-456C-9A3C-F1D69BEA6B0E.html) 
and
[https://www.youtube.com/watch?v=vmF5CW40gxE](https://www.youtube.com/watch?v=vmF5CW40gxE)

After you are fullscreen, only then can you use the Ubuntu Display settings applet to change the resolution.  Think of the VM as the hardware platform that needs to be setup before the software can make use if it.  This is the same for the virtual hard disks - if you need to resize them or add another.

---

### Post by currentshaft on 2024-05-26
apt

---

### Post by pwilliams90 on 2024-05-27
Thank you for the response and the information added. 
I'm on x11. Im using a Linux version of VMware 
on my windows pc. know how to select full screen, I should have spoken better in my response. It's the resolution I'm having the issue with. Because I cannot get the proper resolution, full screen is still filled with black borders. 
That's good, advice, I can try to reach out to vmware.

---

### Post by pwilliams90 on 2024-05-27
Yea, I was referring to screen resolution. I did install VMware tools inside the VM. I've also made sure all of the apps have been updated.

---

### Post by TheFu on 2024-05-27
Resolutions are limited to what will fit inside the window.  If you don't run the VM in full-screen mode, it won't show 1920x1080 as possible.  That's step one, then it should be possible to select that resolution from inside the VM Display settings.

But the release and DE would be the basic information needed to point to instructions for this for noobs.  Every release AND every DE is a little different.  In the Pre-Wayland days, I could just say -
. set the VM to full screen AND set the display memory setting in the VM (before starting it) to the highest allowed value
. install **lxrandr**
. run it and select the desired resolution.

It was easy.  Since Wayland and Gnome3+ things have gotten messy - especially for nvidia where people easily have the wrong drivers .... and in laptops that have dual GPUs, there's some other stuff necessary to ensure a specific GPU is used, not the other one.  I've avoided laptops like that and only had iGPUs from Intel.

---

### Post by MAFoElffen on 2024-05-27
I was going to answer this yesterday, but I was confused by what they were actually looking to do. Some of the app's I have to test & support is VMware's Workstation, Player, & Fusion.

If they were asking about how to go into full-screen mode with that type of VMware product, you open the Menu and select FullScreen, or, use the hot-key <Cntrl><F>. This does not follow the norm. I had to look it up in their VMware Docs. At least for Fusion, which is the MAC OSX version of Workstation.

Which is confusing as all get-out. Because the usual standardization universally accepted with the industry across the board for applications and OS'es, <Cntrl><F> is usually the hot-key for search, and <F11> is the hotkey for FullScreen. At least, that standardization was what I was taught to try to follow in Cross-Platform UI Development. I guess they just wanted to be different, and away from the norm? IDK.

For resolution, (just) for VMware, you have to set the display in the VM config (which is not what you do with any other VM Guest product from others), then set then set the resolution in the OS. I guess thta follows the logic that the way they implement that, the display in settings is only going to be seen by the VM in it's capabilities as what it is set to. By what yours is set to now, you are limited to 1152x864...

---

### Post by pwilliams90 on 2024-05-27
When I am in the VM, I have it set to full screen. When I go inside the settings on ubuntu the resolution still will only go to 1176 x 885. I'm still at a loss here. Thank you all for all of your time and help with this. I really do mean that.

---

### Post by TheFu on 2024-05-27
> **pwilliams90 said:**
> When I am in the VM, I have it set to full screen. When I go inside the settings on ubuntu the resolution still will only go to 1176 x 885. I'm still at a loss here. Thank you all for all of your time and help with this. I really do mean that.

Well, perhaps you need a better hypervisor then?
Inside a libvirt/KVM VM connected through QXL display drivers ... over a network connections (not even local), while the VM window is used (not even full screen), 
```
$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 16384 x 16384
DisplayPort-0 disconnected primary (normal left inverted right x axis y axis)
HDMI-A-0 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   [B]1920x1200     59.95*+
[/B]   1920x1080     60.00  
   1600x1200     60.00  
   1680x1050     59.88  
   1280x1024     60.02  
   1440x900      59.95  
   1280x960      60.00  
   1280x800      59.95  
   1280x720      59.95   
....
```
I bolded the native resolution of the monitor, even without running "full screen", it is available.  I don't use any DE, but lxrandr would let me select any resolution from the list.
As you can see, the maximum resolutions would need to be virtual, which is also supported if I wanted a single workspace.  I with with 1x3 workspaces, but that is completely separate from VMs and resolutions. Virtual workspaces are 100% logical ideas.

Again, all this is running a full VM that could be local, but it isn't. That barely matters, since QXL is tunneled over ssh automatically through the **virt-viewer** tool.
The connection command looks like this 
```
 $ /usr/bin/virt-viewer --connect qemu+ssh://istar/system deneb
```

istar is the VM host hostname (aka the VM server)
deneb is the VM name, also called the "guest"
I have ssh-keys setup from my workstation to the VM host system, so the ssh tunnel is allowed without password prompts, but when the window opens, it is at a login screen waiting for my username and password, just like I walked up to a computer and moved the mouse.  Typically, I wouldn't connect to the system with all this overhead.  I'd directly run any programs on it over an normal ssh-tunnel and the window for each program would integrate with my normal workstation desktop. No need for a full remote desktop and all that overhead just to run a few programs remotely.

---

