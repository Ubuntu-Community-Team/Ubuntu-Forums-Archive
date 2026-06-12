---
title: "Ubuntu 20.04 VM under Windows Hyper-V"
date: 2021-11-01
forum: Virtualisation
---

### Post by thuleni on 2021-11-01
I have created an Ubuntu 20.04 Desktop under Windows 10 Hyper-V and I need to get the screen/monitor/display to be full screen.  Ubuntu does not recognise the monitor/display and has set the resolution to : 1024x768 (4:3).  And that is the only option in the drop-down menu in settings.
Questions is: **How do I get it to increase this to take full advantage of my large screen.**
I also installed 18.04.3 LTS, which sets the screen resolution to 1920x1080 (16:9) and has no drop-down in settings.  ie. thats it, the only resolution/size available, which is is OK, as it it full screen.  Fires up xrdp as the login screen?
Not sure if this is an Ubuntu setting or a Windows Hyper-V setting - the online documentation is very scant with regards to video/display/monitor information.

---

### Post by mIk3_08 on 2021-11-01
> **thuleni said:**
> I have created an Ubuntu 20.04 Desktop under Windows 10 Hyper-V and I need to get the screen/monitor/display to be full screen.  Ubuntu does not recognise the monitor/display and has set the resolution to : 1024x768 (4:3).  And that is the only option in the drop-down menu in settings.
Questions is: **How do I get it to increase this to take full advantage of my large screen.**
I also installed 18.04.3 LTS, which sets the screen resolution to 1920x1080 (16:9) and has no drop-down in settings.  ie. thats it, the only resolution/size available, which is is OK, as it it full screen.  Fires up xrdp as the login screen?
Not sure if this is an Ubuntu setting or a Windows Hyper-V setting - the online documentation is very scant with regards to video/display/monitor information.

can you run this command below in your Linux Ubuntu Operating System  terminal and paste the results wrap with code here in thread.
Thanks a lot.
```
sudo lshw
``` 
```
sudo dmesg
```
```
hostnamectl status
```

---

### Post by thuleni on 2021-11-01
Here are the first two - I will need to split the other file into chunks, or let me know what you are interested in and I will edit the file to remove all the unnecessary stuff (like disk information...)

---

### Post by mIk3_08 on 2021-11-02
> **thuleni said:**
> Here are the first two - I will need to split the other file into chunks, or let me know what you are interested in and I will edit the file to remove all the unnecessary stuff (like disk information...) 
I just want your display information and hope you can follow the instructions to paste and wrap with code the result here in thread. Thanks Good Luck.

---

### Post by TheFu on 2021-11-02
Few people here will be using hyper-v.  We tend to use Virtualbox or KVM/QEMU or "Boxes" as our hypervisors with a few people using Xen/XCP.  Anyway, inside a VM, none of your real hardware matters.  In the VM settings, you'd setup which fake hardware to present to the guest VM.  That includes the CPU, RAM, GPU, NIC, and storage stuff like size, controller, and bus to be used.

So, if the hypervisor settings limit the faked GPU, then the resolution will be limited to that. I don't know the options available from hyper-v - never seen it and don't use Windows as a base for virtual machines here.  I typically use the VMVGA "card" for non-GUI servers and the QXL "Spice" card for desktop systems that need more RAM and faster fake GPU support.  In my hypervisor, controlling the amount of video-RAM provided to the fake GPU isn't available in teh GUI, but it can be modified in the VM definition file.  I know that virtualbox has a slider bar to control the fake video-RAM ... the default of 9M generally has very poor performance. By upping that to 128MB, 2D and 3D graphics acceleration can be emulated in virtualbox.  Perhaps this is in hyper-V VM settings too?   That's the first half of solving this problem.

The 2nd half is controlled inside the VM.  Remember, inside the VM, it doesn't know that fake hardware is being provided, so drivers and settings there need to match the fake hardware.  Inside Linux systems with a GUI, using X11 as the display host subsystem, the **xrandr** program will show all available resolutions. Just open a terminal and run that program. Then copy the output and paste is here.  If using Wayland (not X11), I don't know any of the tools for controlling resolution, but the X/Windows programs don't work.  xrandr can be used to set the screen resolution, but there are probably 10 other, easier, GUI, tools for this.  I will usually install **lxrandr** which is bonehead simple with a GUI to make changing resolutions easy.
```
$ xrandr 
Screen 0: minimum 8 x 8, current 1920 x 1200, maximum 32767 x 32767
DVI-D-0 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200     59.95*+
   1920x1080     60.00  
   1680x1050     59.95  
   1600x1200     60.00  
   1280x1024     60.02  
   1280x960      60.00  
   1024x768      60.00  
   800x600       60.32  
   640x480       59.94  
HDMI-0 disconnected (normal left inverted right x axis y axis)
```
That's an example.  Inside a VM (I use spice/qxl in my KVM VMs), ... 
```
Screen 0: minimum 320 x 200, **current 1680 x 1050**, maximum 8192 x 8192
Virtual-1 connected primary 1680x1050+0+0 0mm x 0mm
   1024x768      60.00 +
   2560x1600     59.99    59.97  
   1920x1440     60.00  
   1856x1392     60.00  
   1792x1344     60.00  
   2048x1152     60.00  
   1920x1200     59.88    59.95  
   1920x1080     60.00  
   1600x1200     60.00  
   [B]1680x1050     59.95*   59.88  
[/B]   1400x1050     59.98    59.95  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      59.89    59.90  
   1280x960      60.00  
   1280x854      59.95  
   1366x768      59.79    60.00  
   1360x768      60.02  
   1280x800      59.81    59.91  
```
That's the current resolution while running in a window.  There is a "View" menu and inside it is a "full screen (F11)" option. After selection of "full screen" (or using F11 to toggle between window <--> full screen), I see this:
```
Screen 0: minimum 320 x 200, **current 1920 x 1200**, maximum 8192 x 8192
Virtual-1 connected primary 1920x1200+0+0 0mm x 0mm
   1024x768      60.00 +
   2560x1600     59.99    59.97  
   1920x1440     60.00  
   1856x1392     60.00  
   1792x1344     60.00  
   2048x1152     60.00  
   **1920x1200     59.88*   59.95**  
   1920x1080     60.00  
   1600x1200     60.00  
   1680x1050     59.95    59.88  
   1400x1050     59.98    59.95  
   1600x900      60.00  
   1280x1024     60.02  
```
that is the native resolution for my monitor.  

Newer Ubuntu systems try to default to using Wayland, but on the pre-login screen, there is a gear icon which will let you specifically choose NOT to use Wayland ... something like "Ubuntu on Xorg" is the option you want.  I think 20.04 still defaults to Xorg's X11 server, so you should be fine.  21.04 and 21.10 both default to Wayland, for reference and future lurkers.  X/Windows has been the GUI display system for 30+ yrs, so Wayland is new and not supported by all programs today. Some will never move to support it. Wayland breaks a number of my workflows, so I'll never use it.

So, assuming you have the hypervisor allowing plenty of RAM and have set the resolutions inside the VM to whatever the highest available is for your screen - I run at 1920x 1200.

To get better screen/mouse integration, some hypervisors require "guest tools" to be installed inside the VM.  KVM/QEMU don't. Virtualbox does. I suspect hyper-v does as well.  May need to check into that.  [https://medium.com/@labappengineering/ubuntu-20-04-on-hyper-v-8888fe3ced64](https://medium.com/@labappengineering/ubuntu-20-04-on-hyper-v-8888fe3ced64) says something about *Hyper-V Linux Integration Service* - this is typically used to ensure graphics and more efficient network and storage drivers are used.  In the Linux terminology, we'd say "virtio" drivers.  

[https://github.com/microsoft/linux-vm-tools](https://github.com/microsoft/linux-vm-tools) is where that guide points. In it, it says that it is archived and that wsl2 should be used instead, whatever that is.  I'm not really an MS-Windows person. Sorry.  I'm huge into virtualization but just have never seen hyper-v used anywhere.

[https://www.serverwatch.com/guides/installing-and-activating-hyper-v-linux-integration-services/](https://www.serverwatch.com/guides/installing-and-activating-hyper-v-linux-integration-services/) doesn't list Ubuntu as supported by Linux Integration Services.

---

### Post by MAFoElffen on 2021-11-05
In Hyper-V, default your thinking back to what TheFu said early on (the basics of hypervisors...) that the guest is only going to see the capabilities of the VM Host, the VM defintion, and the config of the VM Guest. (and how they all play together.) And if you are familair with Hyper-V, then you know there are different limits and possibilities between Gen 1 and Gen 2 VM's. I know this is going to sound a bit "on both sides"... But this post is going to go between what is documented & supported... and what really works and is possible,

Officially, it all depends if you are using the VM Viewer of Hyper-V, [X]RDP or any other Viewers... Some viewers ask you if you want to "scale", meaning asking you what resolution you want to view as... A cheat I used to use was to create an xorg.conf file at a resolution or range of resolution's, so that when a VM started, the VM started it in "that" resolution and saw those other resolutions as options. 

What is in the MS docs is that your create all Linux Guests as Gen 1... Well, that train of thought is a bit outdated. If you are Gen 1, then use an xorg.conf file in the Linux Guest to set your resolution...

Hyper-V is round-about and not straight forward... If you use Hyper-V,  you already know that, even with Windows Guests. Some of those "same  things" work for Ubuntu Guests.

Hyper-V leans the advanced graphics support to their own OS flavors as guests. It doesn't officially add much graphics support or advanced desktop sharing support between Linux Guests and their host OS. Most of that is going to be in other types of viewers, besides the default Hyper-V Guest Viewer. Other VM Host Systems are a lot more friendly on those kinds of things between OS'es... Which other VM Host system's usually refer to as a type of Guest Services, or Guest Additions. Or in Window-eeze referred to as "Enhanced Session". But there is some support, that is underlying, and not real well documented.

So following that... Here is the reality of what does work and adds some of those those same to a Linux Guest under Hyper-V:

Create your Ubuntu VM as a Hyper-V "Generation 2" VM... after you install and config, then right click on the VM Name in the Hyper-V Manager left pane... Select Hyper-V settings... When that window opens, go down in the left pane down to "Enhanced Session Mode Policy" and select. In the right Pane when that is selected, select "Allow Enhanced Session Mode" (check the box)... If the VM is running, it will have to be restarted to pick up the change.

(Note- This is documented for Windows Guests, but not for Linux Guests. Yet it works for modern Linux Guests also...)

This will turn on cut-and-paste and other Desktop enhancements and resource sharing between the Guest, host, and VM viewers. Some of those enhancements are graphical scaling.

And you know that installing as Gen 2, then you have to install in the constrains of: UEFI, 64bit, and SecureBoot. But if you go to "Add Hardware" in Gen 2, you can disable SecureBoot in the UEFI. But if you leave SecureBoot enabled, then, as per Ubuntu, installation of 20.04 LTS and newer.

---

### Post by bunny9000 on 2021-11-06
Don't use console.

Install x2go server on the ubuntu vm and then install x2go client on your windows machine or whatever computer you're connecting to the Linux VM then connect to the Linux VM via the x2go client which you can set a better resolution and it'll pull the sound through as well.

---

### Post by MAFoElffen on 2021-11-07
> **bunny9000 said:**
> Don't use console.

Install x2go server on the ubuntu vm and then install x2go client on your windows machine or whatever computer you're connecting to the Linux VM then connect to the Linux VM via the x2go client which you can set a better resolution and it'll pull the sound through as well.

I and other's here love x2go... But be advised that x2go's non-support for Gnome 3 and above, you have to do work-arounds to get around it's failure to support that directly. That is still a known limitation of x2go, current (still as of a few weeks ago AFAIK). The work around for Ubuntu Desktop was to either install Gnome Fallback as a DE, or to install a minimal DE of another flavor (MATE, xfce, etc.).

It works. Just not 'out-of-the-box' for Ubuntu Desktop.

---

### Post by TheFu on 2021-11-07
x2go has some huge technical debt - I think they used the 2009 version of xorg as their base for the port of VNC before they optimized it for NX use.

On the LAN, I don't typically use x2go at all.  It is used over the internet.  On the LAN, I'll use X11Forwarding through ssh 99% of the time if I need a GUI and about 1% of the time, I'll connect to a virtual machine using the SPICE/Qxl connection built-into KVM/QEMU (a hypervisor) and either virt-viewer or virt-manager. Hyper-V doesn't support SPICE, but the X11Forwarding would be separate, as would x2go.  virt-viewer runs on MS-Windows.

I seldom want a GUI to a remote server, so it is only for fairly specific reasons where I'd using anything other than ssh.

I've used 2xgo from multiple continents and with a few DEs and without **any** DE - which is how I like to run most of my desktops. X2go clients exist for Windows, Linux and that other OS.  I don't know if there are ARM-CPU versions. Last time I checked, which was a few years ago, there wasn't any x2go for tablets.  I have run Ubuntu inside a chroot on android and used VNC --> X11 to connect to other systems, but all those layers were unsatisfying for usability and performance.  From android, it is just easier to have local apps for the stuff I use - nextcloud, openvpn, wireguard, vlc, jellyfin, wallabag, Aldiko, M.A.L.P, and other typical "consumption" needs, even with a keyboard connected.  If I need to do more than watch, listen or read on the tablet, I'll use a laptop instead.

---

