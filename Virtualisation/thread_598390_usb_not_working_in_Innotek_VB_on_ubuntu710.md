---
title: "usb not working in Innotek VB on ubuntu710"
date: 2007-10-31
forum: Virtualisation
---

### Post by keiffee30 on 2007-10-31
I have installed innotek VB (1.5.2) and im having some problems with the USB

Every time i open up a virtual mac i get............


Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code:
0x80004005
Component:
Host
Interface:
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee:
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}


I have given myself access to the /etc/udev directory as i have seen that many post have been access issues. I can get some information on the USB posts used by typing LSUSB and the output is

bus001 device005: ID03f0:1016 ipaq/hp

So i am happy that the ipaq is connected to the PC. but i can not connect the usb to a VBox. Can anyone help out with this?

Many thanks
Keith

---

### Post by rubinstein on 2007-10-31
Maybe this will help you: [http://www.arsgeek.com/?p=2776](http://www.arsgeek.com/?p=2776) "Get USB devices mounted on your Virtualbox XP machine in Gutsy (Ubuntu 7.10)"

---

### Post by Steve1961 on 2007-10-31
or just add this line to /etc/fstab

none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0

the devgid number is the vboxusers group id (check to see if yours is different)

Once you've saved and closed fstab just do a sudo mount -a and you should be good to go.

---

### Post by fdimmling on 2007-11-01
> **Steve1961 said:**
> or just add this line to /etc/fstab

none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0
[...]

Does this work without enabling the "Magic to make /proc/bus/usb work" mentioned in the posting before? I am wondering if such modifications of files in /etc/init.d might have unwanted side effects. I would feel more comfortable if changing /etc/fstab would be enough. :confused:

Friedrich

---

### Post by Steve1961 on 2007-11-01
The fstab line is all you need.  Obviously make sure that your also a member of the vboxusers group and that you use the correct devgid id.

---

### Post by keiffee30 on 2007-11-01
Steve

you are a complete life saver. Many thanks for finding and passing on that link. By the way yes it not works now.

---

### Post by 52rockwell on 2007-11-03
Thanks Steve for a simple fix .. 

It workede for me

---

### Post by Steve1961 on 2007-11-04
> **52rockwell said:**
> Thanks Steve for a simple fix .. 

It workede for me

You're welcome :)

---

### Post by serfcx on 2007-11-04
Hi everyone,
Does this thread and solution refer to the virtualbox in the repos ? That is the ose form rather than that from the innotek website which I read on another thread has usb support ?

And do you need to have build-essentials installed in order to get XP installed in virtualbox ?

Thanks for any help

---

### Post by Steve1961 on 2007-11-04
I don't think the ose version supports usb.  I installed the version from the virtualbox site by adding their repo to my /etc/apt/sources.list.  As a kernel module needs to be compiled you should have build-essential installed

---

### Post by serfcx on 2007-11-04
> **Steve1961 said:**
> I don't think the ose version supports usb.  I installed the version from the virtualbox site by adding their repo to my /etc/apt/sources.list.  As a kernel module needs to be compiled you should have build-essential installed

Thanks for that steve, as I thought. Will I also need the kernel source and headers ?

---

### Post by Steve1961 on 2007-11-04
You don't need the kernel source, only the headers.  Not sure, but these might even be installed automatically along with build-essential, but if not just install them from synaptic.  Or just issue the command:

sudo apt-get install build-essential linux-headers-`uname -r`

---

### Post by serfcx on 2007-11-04
> **Steve1961 said:**
> You don't need the kernel source, only the headers.  Not sure, but these might even be installed automatically along with build-essential, but if not just install them from synaptic.  Or just issue the command:

sudo apt-get install build-essential linux-headers-`uname -r`

Thanks once again.

I will give it a go this pm.

---

### Post by serfcx on 2007-11-04
Tried all above and failed with error message
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED)

Ran sudo /etc/init.d/vboxdrv setup twice as suggested on other posts and still nothing

dmesg gave error about adding nmi_watchdog=0 to the kernel command

Is this normal and safe to do ?

dmesg output is just over 19.5 limit as one file so have split into 2 attached

---

### Post by chrisch on 2007-11-12
Brilliant!  Thank you very much.

---

### Post by Lothas on 2007-11-22
Thanks Steve! I used your solution and now I get to use my USB camera under windows. I also have a USB wireless keyboard and mouse. When I add those to the virtual machine, I get proper input for windows (e.g.: keys stay pressed instead of being repeatedly pressed). The problem is that I'm loosing keyboard support for Ubuntu.

So, under the present configuration I can have a proper keyboard in windows at the cost of loosing it for Ubuntu (while XP is running) or I can have seamless Ubuntu+XP but without proper keyboard support.

Any ideas?

---

### Post by pr144 on 2007-12-23
I have followed directions here after installing the latest from the virtualbox site for my AMD computer.

Now my problem is that the CD is not mounted and does not show upin the drop down.

I tried mounting with,
sudo ln -fs /media/cdrom0 /dev/cdrom 

...this allows me to browse the CD ROM


If mount from within the Virtual Box GUI I can't install the OS and I get a fata error when starting the VM.  How can I get the mounted CD ROM to show up in the "Settings"?

pr

---

### Post by bobpress on 2007-12-27
> **Steve1961 said:**
> or just add this line to /etc/fstab

none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0

the devgid number is the vboxusers group id (check to see if yours is different)

Once you've saved and closed fstab just do a sudo mount -a and you should be good to go.

Thanks.  This worked for me.  After VirtualBox was updated, I kept getting error messages about not able to connect to USB Device 'Failed to create a proxy device for the USB device. (Error: VERR_FILE_NOT_FOUND).'    My vboxusers group id was different than yours, but looked in System/Administration/Users and Groups/Manage Groups - Properties and changed the 1002 (group id),

---

