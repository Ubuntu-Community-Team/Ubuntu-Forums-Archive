---
title: "Full Screen, Ubuntu Guest VM on Ubuntu Host"
date: 2021-05-04
forum: Virtualisation
---

### Post by webmanoffesto on 2021-05-04
How can I make my VM truly full screen?

I tried using the "Install Guest Additions" in my Virtual Box Ubuntu VM so that I could get true full screen. Right now the "full screen" fills about 1/4 of my monitors screen space. 
I tried using the instructions at [https://askubuntu.com/questions/18425/how-to-use-ubuntu-in-full-screen-mode-on-virtualbox](https://askubuntu.com/questions/18425/how-to-use-ubuntu-in-full-screen-mode-on-virtualbox). But I got some error messages. 
Now when I do "Install Guest Additions" I get:Unable to insert the virtual optical disk /usr/share/virtualbox/VBoxGuestAdditions.iso into the machine Ubuntu20_04.
"Could not mount the media/drive '/usr/share/virtualbox/VBoxGuestAdditions.iso' (VERR_PDM_MEDIA_LOCKED).
Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component:  ConsoleWrap
Interface: IConsole {872da645-4a9b-1727-bee2-5585105b9eed}
Callee: IMachine {85632c68-b5bb-4316-a900-5eb28d3413df}"

---

### Post by dddman on 2021-05-04
The error just means your virtual CD drive is already mounted.  Open your file manager in the guest system and eject CD that will remove the error.  There are different ways to install virtualbox.  How did you install?  What version?  Did you install the package build-essential to the guest before adding guest additions to it?  If guest additions successfully installed you would of received a message to reboot.  Did you?

PS
There is also a seamless mode, is it grayed out in the menu?

---

### Post by webmanoffesto on 2021-05-04
Okay that helped. Now I get the error I got the first time. What does this mean and how do I resolve it?
```
Verifying archive integrity... All good. 
Uncompressing VirtualBox 6.1.22 Guest Additions for Linux........ 
VirtualBox Guest Additions installer 
Removing installed version 6.1.22 of VirtualBox Guest Additions... 

Copying additional installer modules ... 

Installing additional modules ... 
VirtualBox Guest Additions: Starting. 
VirtualBox Guest Additions: Building the VirtualBox Guest Additions kernel  
modules.  This may take a while. 
VirtualBox Guest Additions: To build modules for other installed kernels, run 
VirtualBox Guest Additions:   /sbin/rcvboxadd quicksetup <version> 

VirtualBox Guest Additions: or 

VirtualBox Guest Additions:   /sbin/rcvboxadd quicksetup all 
VirtualBox Guest Additions: Building the modules for kernel 5.8.0-50-generic. 
 
This system is currently not set up to build kernel modules. 
Please install the gcc make perl packages from your distribution. 
VirtualBox Guest Additions: Running kernel modules will not be replaced until  

the system is restarted 

Press Return to close this window...
```

---

### Post by rbmorse on 2021-05-04
Try installing the package ```
build-essential
``` from repository.  That should supply the missing capabilities.

---

### Post by webmanoffesto on 2021-05-04
> **dddman said:**
> Open your file manager in the guest system and eject CD that will remove the error. 

Okay that's working better now. 
I ran "sudo apt install build-essential". 
Then I did "Insert Guest Additions". But I still got error messages.

```

Verifying archive integrity... All good. 
Uncompressing VirtualBox 6.1.22 Guest Additions for Linux........ 
VirtualBox Guest Additions installer 
Removing installed version 6.1.22 of VirtualBox Guest Additions... 
Copying additional installer modules ... 
./install.sh: 100: cannot create /var/lib/VBoxGuestAdditions/filelist: Directory nonexistent 
./install.sh: 100: cannot create /var/lib/VBoxGuestAdditions/filelist: Directory nonexistent 
./install.sh: 100: cannot create /var/lib/VBoxGuestAdditions/filelist: Directory nonexistent 
./install.sh: 100: cannot create /var/lib/VBoxGuestAdditions/filelist: Directory nonexistent 
Installing additional modules ... 
./install.sh: 420: cannot create /var/lib/VBoxGuestAdditions/filelist: Directory nonexistent 
./install.sh: 420: cannot create /var/lib/VBoxGuestAdditions/filelist: Directory nonexistent 
./install.sh: 436: cannot create /var/lib/VBoxGuestAdditions/config: Directory nonexistent 
Configuration file /var/lib/VBoxGuestAdditions/config not found 
The log file /var/log/vboxadd-setup.log may contain further information. 
./install.sh: 478: cannot create /var/lib/VBoxGuestAdditions/filelist: Directory nonexistent 
./install.sh: 581: cannot create /var/lib/VBoxGuestAdditions/filelist: Directory nonexistent 
./install.sh: 583: cannot create /var/lib/VBoxGuestAdditions/filelist: Directory nonexistent 
./install.sh: 597: cannot create /var/lib/VBoxGuestAdditions/filelist: Directory nonexistent 
chmod: cannot access '/opt/VBoxGuestAdditions-6.1.22/bin/VBoxDRMClient': No such file or directory 
Press Return to close this window...

```

---

### Post by dddman on 2021-05-04
> **webmanoffesto said:**
> Okay that's working better now. 
I ran "sudo apt install build-essential".

Good

Eject the virtual CD and reboot the guest.  Then add guest additions.

Should work

---

### Post by webmanoffesto on 2021-05-04
> **dddman said:**
> Eject the virtual CD and reboot the guest.  Then add guest additions.

Okay, I did that. It doesn't give me the true full screen that I was hoping to get. How do I know if this worked?
How do the VM to display in real full screen.

---

### Post by dddman on 2021-05-04
Full screen should show nothing but the guest system.  Use your right "Ctrl + f" to toggle full screen.

---

### Post by TheFu on 2021-05-05
BTW, there are multiple hypervisors available.  KVM + libvirt + virt-viewer using QXL and Spice don't have any "guest additions" and are what enterprises use for their virtual machines.  Who?  Amazon, Linode, Oracle, Redhat, .... you get the idea.  KVM is part of the Linux kernel, so it is extremely well tested and constantly improving.  I think it is the fastest hypervisor available today.

With virt-manager, the GUI to setup VMs is very much like VMware Workstation ... but better, since it can be managed both locally or remotely over ssh. There's an ssh+qemu:// connection URL.

Anyways, just thought I'd mention this.  Plus, KVM doesn't have a proprietary license, unlike the Oracle Guest Additions for virtualbox require.

---

### Post by dddman on 2021-05-05
Kernel support has to make it fast and probably easy on resources.  Virtualbox is hard on resources.  I host using windows and don't have such kernel options.  Maybe one day, but I'm currently running a tablet and find running both OS concurrently a productive plus.  I have gone the extra step and setting up a ubuntu tablet mode guest system.  It better utilizes the space when screen is sideways :)

---

### Post by TheFu on 2021-05-05
> **webmanoffesto said:**
> Okay, I did that. It doesn't give me the true full screen that I was hoping to get. How do I know if this worked?
How do the VM to display in real full screen.

There's the VM aspect, controlled by the VM settings - this is the full-screen vs "windowed" choice.
and 
there's the screen resolution controlled inside the guest by normal display controls.  I use **lxrandr** to set the resolution inside the client VM, but any display resolution setting tool should work on all the modern hypervisors with a graphical interface.

---

### Post by dddman on 2021-05-05
Works in virtualbox and its a keeper, off to the toy box with it.

---

### Post by webmanoffesto on 2021-05-05
Host-C, Scaled Mode is close. That makes my Virtual Ubuntu window fill the whole screen. But then it's kind of stretched out in the left-right aspect. I wonder how I fix that.

---

### Post by TheFu on 2021-05-05
> **webmanoffesto said:**
> Host-C, Scaled Mode is close. That makes my Virtual Ubuntu window fill the whole screen. But then it's kind of stretched out in the left-right aspect. I wonder how I fix that.

Inside the VM, use any display resolution control tool that you like. I use **lxrandr** because it is bonehead simple.
It is always best to run at the monitor's native resolution.

---

### Post by ajgreeny on 2021-05-05
> **TheFu said:**
> Inside the VM, use any display resolution control tool that you like. I use **lxrandr** because it is bonehead simple.
It is always best to run at the monitor's native resolution.
I agree with TheFu except that I simply use **xrandr** in terminal.

That lists all resolutions available to your system, marks what is in use with an asterisk but allows you to choose the resolution you want with a simple command, eg ```
xrandr -s 1920x1080
```
I no longer use VirtualBox having moved to QEMU/KVM many months ago so I'm not sure how well xrandr or lxrandr work in VBox but they certainly do the job very easily in QEMU/KVM.

---

### Post by dddman on 2021-05-05
Yes, scaled mode will stretch things out if taken too far.  Stay off of scaled mode, you want full screen.  Do what others have said.  Find the native resolution and set it.  If not with xrandr, then system settings>display will also change resolutions.  

You want to know if guest additions took or not?  If "seamless" is grayed out in the virtualbox menu>view>seamless; then guest additions is not yet working or not properly installed.

---

