---
title: "USB Device not showing up"
date: 2008-03-21
forum: Virtualisation
---

### Post by watsgoodg on 2008-03-21
Hey Guys,

My base system is ubuntu guysty, i installed vmware and built a vm with xp.  Within the xp virtual machine i cant get usb keys or any devices to show up.  I checked the settings everythings enabled.  Any ideas?

---

### Post by fjgaude on 2008-03-21
Have fixed this doing this:

Uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs
```

gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Like so:

    	```

        mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Then place in the fstab file this line:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Good to add this line into your guest .vmx file using text editor:

```
mainMem.useNamedFile=FALSE
```

You will have full copy, paste from host to and from guest, and USB device handling capability, drives, scanners, printers, etc.

Let us know how you are doing.

---

### Post by watsgoodg on 2008-03-21
Where it says the command "like so" i pasted it into terminal and get the following:

test@test-laptop:~$ mkdir -p /dev/bus/usb/.usbfs
test@test-laptop:~$ domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
bash: domount: command not found
test@test-laptop:~$ ln -s .usbfs/devices /dev/bus/usb/devices
ln: creating symbolic link `/dev/bus/usb/devices' to `.usbfs/devices': Permission denied
test@test-laptop:~$ mount --rbind /dev/bus/usb /proc/bus/usb

---

### Post by watsgoodg on 2008-03-21
test@test-laptop:~$ usbfs /proc/bus/usb usbfs auto 0 0
bash: usbfs: command not found
test@test-laptop:~$

---

### Post by OmegaBLK on 2008-03-21
> **watsgoodg said:**
> test@test-laptop:~$ usbfs /proc/bus/usb usbfs auto 0 0
bash: usbfs: command not found
test@test-laptop:~$

Append the line **fjgaude** posted:
```
 usbfs /proc/bus/usb usbfs auto 0 0
```

into your **/etc/fstab** file.

Also the permission issue is due to you not having permission to write to that directory (you need to be root/superuser):
```

test@test-laptop:~$ ln -s .usbfs/devices /dev/bus/usb/devices
ln: creating symbolic link `/dev/bus/usb/devices' to `.usbfs/devices': Permission denied

```

You need to prefix the **ln** command with **sudo**.  Like so:

```

sudo ln -s .usbfs/devices /dev/bus/usb/devices

```

---

### Post by fjgaude on 2008-03-21
> **watsgoodg said:**
> Hey Guys,

My base system is ubuntu guysty, i installed vmware and built a vm with xp.  Within the xp virtual machine i cant get usb keys or any devices to show up.  I checked the settings everythings enabled.  Any ideas?

Let's start over... and I'll try to be clearer about what is what. In a terminal enter:

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Enter your password. We are now in gedit, using root permissions. Uncomment four lines in the file you are looking at starting with line #42. Do this by deleting the "#" in front of each of the four lines so that the lines look like this:
```

    	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Save the file and exit the editor. Next we will edit your fstab using the same gedit program, in a terminal enter:

```
gksudo gedit /etc/fstab
```

Enter your password. Then copy this line and paste it into the end of the file:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Save the file. Exit the editor. Reboot your computer.

Let's see how this goes before going further. Let us know how you are doing.

---

### Post by burlington1963 on 2008-03-22
> **fjgaude said:**
> Let's start over... and I'll try to be clearer about what is what. In a terminal enter:

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Enter your password. We are now in gedit, using root permissions. Uncomment four lines in the file you are looking at starting with line #42. Do this by deleting the "#" in front of each of the four lines so that the lines look like this:
```

    	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Save the file and exit the editor. Next we will edit your fstab using the same gedit program, in a terminal enter:

```
gksudo gedit /etc/fstab
```

Enter your password. Then copy this line and paste it into the end of the file:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Save the file. Exit the editor. Reboot your computer.

Let's see how this goes before going further. Let us know how you are doing.

I am having the same problem getting my usb ports working on the guest machine.  I have tried the steps above with no success.  Any additional ideas.

Burlington

---

### Post by fjgaude on 2008-03-23
What OS are you using?

---

### Post by watsgoodg on 2008-03-24
Thanks for the help fjgaude, usb devices are showing up in my vm.  Great write up.  I will keep this for future reference.  I think they should create a sticky for this.

---

### Post by fjgaude on 2008-03-24
You are welcome... I've posted these instructions many times, each time getting a little clearer English. Yes, it should go as a Sticky, but I don't know how to do such.

Have fun with your VM.

---

### Post by Jim_in_Germany on 2008-04-03
Just like to add that these instructions totally sorted me out too. Thanks ever so much  - should definitely be made into a sticky.

---

### Post by dwasifar on 2008-04-03
Okay, this makes USB drives work in VMWare, but now I don't know where to find them in the Linux filesystem.  They don't seem to mount up automatically in /media any more.  What am I missing?

---

### Post by luvit on 2008-04-04
i have mixed results.
[LIST]
[*] my devices are reported by XP as being plugged into a USB1.1 device.
[*]my thumb drive operates as USB 1.1
[*]but my Zyxel (USB wireless G) ZyAir G-220 (v1 US) blue screens my XP with either of 3 different versions of the driver...[/LIST]  I've used this USB wireless adapter with vmware workstation hosted on a XP PC... so I know it works in vmware, but not my current config.
[INDENT]Ubuntu Disktop, VMware Server 1.05, hosting XP.the USB wireless device works great (natively) in Ubuntu.

[/INDENT][LIST]
[*]is there a way to make my virtual machine (XP) report this as a USB2?
[*]any ideas on why my thumb drive works, but my USB wireless bluescreen my XP vm?[/LIST]

---

### Post by luvit on 2008-04-05
.
[COLOR="Blue"]nevermind... only the paid version (WMware Workstation) supports USB 2.0
VMware surver looks like it supports most USB 2.0 hard drives, but printers and other items tend to crash.[/COLOR]

> **luvit said:**
> [COLOR="Silver"][SIZE="1"]i have mixed results.
[LIST]
[*] my devices are reported by XP as being plugged into a USB1.1 device.
[*]my thumb drive operates as USB 1.1
[*]but my Zyxel (USB wireless G) ZyAir G-220 (v1 US) blue screens my XP with either of 3 different versions of the driver...[/LIST]  I've used this USB wireless adapter with vmware workstation hosted on a XP PC... so I know it works in vmware, but not my current config.
[INDENT]Ubuntu Disktop, VMware Server 1.05, hosting XP.the USB wireless device works great (natively) in Ubuntu.

[/INDENT][LIST]
[*]is there a way to make my virtual machine (XP) report this as a USB2?
[*]any ideas on why my thumb drive works, but my USB wireless bluescreen my XP vm?[/LIST][/SIZE][/COLOR]

---

### Post by kobusven on 2008-12-17
Hi

I have a simmilar problem to this one - except that I am using Ubuntu 8.10, and VM Ware 1.0.7 build-108231. It does give me the option to enable USB devices, but NOTHING shows up as available devices to add it to the VM session. As there is some critical USB devices which I should be able to access (as it does not work in Linux (Sunix USB - Serial adapter)) I have to get this going, in order for me to get rid of dual boot. 

Kobus

---

### Post by rhonaldmoses on 2008-12-31
Check out this page for more information on enabling the usb support for VirtualBox.

[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)

---

