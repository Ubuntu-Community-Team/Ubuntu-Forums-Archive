---
title: "How do you print using VMware Server?"
date: 2008-03-26
forum: Virtualisation
---

### Post by explorer716 on 2008-03-26
I have installed Windows XP  using VMware Server.  Everything is OK, except I cannot get my printer to work.

I am running Ubuntu 7.10 on a Intel HP PC and my printer is an HP Photosmart C5180.  The printer is connected to my PC via USB cable 

Any advice on what to do or where to find assistance will be greatly appreciated.

---

### Post by CheShA on 2008-03-26
Well you'll need to make sure you have a USB controller in your VM (i.e. power off vm, go to vm > settings, add hardware, select USB controller, finish) then when your VM is powered up and has focus,  any USB devices that you connect will be connected to the VM - so plug in your printer and install as normal under Windows. Any further problems you need to hit up a VMWare forum really.

---

### Post by fjgaude on 2008-03-26
> **explorer716 said:**
> I have installed Windows XP  using VMware Server.  Everything is OK, except I cannot get my printer to work.

I am running Ubuntu 7.10 on a Intel HP PC and my printer is an HP Photosmart C5180.  The printer is connected to my PC via USB cable 

Any advice on what to do or where to find assistance will be greatly appreciated.

The way many have had success with any USB device, scanners, printers, drives is to follow this:

Uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/ usbfs in a terminal like so:

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

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

Re-boot your machine and you should see your USB devices in VM/Removable Devices/USB Devices menu.

Let us know how you are doing.

---

### Post by explorer716 on 2008-03-26
I am still new at Linux and I have no code background. So please what is meant by, "
Uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/ usbfs in a terminal like so:"   Also, please the instruction, "hen place in the fstab file this line:"

Sorry for being so inexperienced.

Thank you for helping me.

---

### Post by fjgaude on 2008-03-26
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

### Post by explorer716 on 2008-03-27
Your instructions are great. I completed them and ready for the next step.

Thank you so much for the time and effort you are giving to help me.

---

### Post by fjgaude on 2008-03-27
Wonderful. Good to add this line into your guest .vmx file using text editor:

```
mainMem.useNamedFile=FALSE
```

If you can't find where the .vmx file is, a clue: in the main folder where the Virtual Machine is stored.

---

### Post by explorer716 on 2008-03-27
I apologize for being so ignorant, but I cannot find this file>

Thanks for your patience.

---

### Post by fjgaude on 2008-03-27
Okay, it is in the folder that is named what you name your virtual machine. Click on that folder and notice the file with the .vmx type.

If you are unable to do that try this in a terminal:

```
locate *.vmx
```

That will show where the file is.

Once you have found the file do this also in a terminal:

```
gksudo gedit <full path name of the file you found above>
```

Let us know how things go. You should be able to access all your USBs now, before doing this. Can you?

---

### Post by explorer716 on 2008-03-27
Here is my current status:

When I open VMware-Server and start Windows XP and then go to the top menu bar that drops down when your put your cursor at the top of the screen.  When I click on VM and go Removable Devices > USB Devices I find a checkmark beside " HP Photosmart C5100 series (Port 1).

I also have USB symbol in the right side of the  bar at the bottom of the page.

When I try to print I get an error.

Any suggestions?

Thanks

---

### Post by fjgaude on 2008-03-27
I do believe you have to load the printer driver into Windows as guest just as you did when you were in Windows as host.

Keeping my fingers crossed! <smile>

---

### Post by explorer716 on 2008-04-02
I was never able to get my printer to print using the usb connection.  However, I have gotten my printer to work using an ethernet connection.

I realized that my printer has both usb and ethernet connections.  Without changing the usb cable from the printer to my computer, I added an ethernet cable from the printer to my router.  I booted up VMware virtual Windows XP and it asked me if I wanted to be connected to a network and I replied "yes" and completed the rest of the question needed to create it.

Now, I am able to print from my actual computer using the usb connection and from virtual Windows using the ethernet connection.

I realize I could  use the ethernet connection for all my printer needs, but  this works and have no reason to change.

Again, I thank everyone for helping me.

---

### Post by Glendon on 2008-04-02
I'm attempting this as well. Thanks for the help.

I made the changes to mountdevusbfs.sh.

I'm getting a BSoD in my WinXP guest when I try to access the printer.

The printer is listed in My Printers. 

I've made the change to the vmx file and rebooting the guest. 

Hopefully this will work.

---

### Post by Glendon on 2008-04-02
No joy.

I tried to do a simple print with Notepad.

BSoD.

Any suggestions?

---

### Post by explorer716 on 2008-04-02
Please read all of the posts to this thread.  I completed the suggestions from Fgjude.  While I don't understand all, I know that it was helpful in my computer recognizing my printer.  Please advise if I can help further.

---

