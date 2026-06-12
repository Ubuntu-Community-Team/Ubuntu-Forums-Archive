---
title: "Virtualbox + USB doesn't work + Karmic 9.10"
date: 2010-03-31
forum: Virtualisation
---

### Post by openxs on 2010-03-31
This is a quick tutorial for anyone else who has USB problems with their guest operating systems on Virtualbox. I'm using Virtualbox version 3.6.1 with Windows 7 as a guest, though this should work regardless of the guest OS. 

I wanted to use the wi-spy dongle and my webcam (its built in to laptop & shows up as a usb device).

There are two versions of Virtualbox, OSE (which is in the repositories)and the Enterprise/Home version which is available with a .deb binary installer from [http://www.virtualbox.org/]("http://www.virtualbox.org/")
You have to use the Enterprise/Home version for USB support, the OSE doesn't provide USB support, at least not when I last checked.

Once Virtualbox is installed you obviously need to have a Guest OS installed, Windows 7 in my case. Once that is done. install the 'Guest Additions' pack, follow the Virtualbox installation instructions to do this.

**1)** In the Virtualbox interface click the 'Settings' button & select 'USB'.

**2)** Click the 'Add Filter' button (right hand side on version 3.6.1). You should see your USB devices, select/add them all. Click OK when you're done.

**3)** Open a Terminal by clicking: Applications >> Accessories >> Terminal, once it's open, copy and paste or type the following:

grep vboxusers /etc/group

You should get a result that looks something like: 

vboxusers:x:121:openxs

The number after & before the colons ':' are what you need to make a note of, it's the "121" in the example above.

**4)** Using the terminal again, we need to open the fstab file by typing:

sudo nano /etc/fstab

The following line needs to be placed at the bottom of fstab:

none    /proc/bus/usb   usbfs   devgid=121,devmode=664  0       0

Where this example says 'devgid=121' change the '121' to whatever number you got when you ran the previous grep command.

Press Ctrl + x then press Y to save your changes and exit nano

**5)** Now all thats left to do is to go to 'Users & Groups by clicking: System >> Administration >> Users and Groups

Click the little padlock to make changes and enter your password.

**6)** Select your username then click 'Manage groups', a new box will pop up, scroll down to 'vboxusers' and highlight it, click 'properties'. 

In the box that says 'Group ID' type in the number you used in FSTAB, mine was 121. After, click ok.

**7)** That's it, close the dialogue box and start your Virtual Guest Windows, all being well, you'll have USB available. Have fun!

---

### Post by cforput on 2010-04-04
Need help with this. I followed the directions and my USBs were now seen by VirtualBox. The problem was that it killed all of them including my wireless connection and USB mouse. If I shutdown VBox my wireless activates and my mouse works again.

Anyone have any ideas?  

Karmic
VBox from SUN ver 3.1.6 r59338 (not OSE version)

Help!!!

---

### Post by cforput on 2010-04-04
Never mind. I figured it out. I deleted my OSE version but didn't realize that ~/.virtualbox was left on my drive. I deleted (actually renamed to keep it just in case) it and set up a new XP OS and everything is working OK now.

---

