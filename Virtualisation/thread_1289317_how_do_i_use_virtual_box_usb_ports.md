---
title: "how do i use virtual box usb ports?"
date: 2009-10-12
forum: Virtualisation
---

### Post by kaboyish on 2009-10-12
hi. i just installed ubuntu 9.04, and I'm currently using virtual box to run windows xp professional service pack two. unfortunately i don't know how to use my flash disk on the virtual machine. the machine doesn't even mount it. 
please help. thanks

---

### Post by coldReactive on 2009-10-12
This might help: [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

You also have to be using the non-OSE ( [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) ) version.

---

### Post by kaboyish on 2009-10-12
> **coldReactive said:**
> This might help: [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

You also have to be using the non-OSE ( [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) ) version.

thanks man. i'll try the solutions and let you now if they worked.

---

### Post by gacb on 2009-10-12
I have the non-free edition (3.08 r53138) on both my laptop and desktop. USB devices work fine on the laptop but not the desktop - mostly the same USB devices. The desktop allows the devices to be loaded in Settings but are greyed out in Devices. I have both Karmic and Jaunty installed on both machines.
 
It's a puzzle.

---

### Post by Perryg on 2009-10-13
Did you install the Guest Additions on the desktop?

---

### Post by kaboyish on 2009-10-16
> **coldReactive said:**
> This might help: [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

You also have to be using the non-OSE ( [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) ) version.

i tried using the above solution but the usb ports aren't working yet. any other suggestions?

---

### Post by kaboyish on 2009-10-19
> **Perryg said:**
> Did you install the Guest Additions on the desktop?

please tell me how to install the guest additions

---

### Post by Perryg on 2009-10-19
Beginners guide for installing guest additions desktop editions.
The steps also show the installation of Linux headers and build essential to allow compiling external modules. You can skip this part if you already have them installed.

[list]Start the guest
Open a terminal.
Type sudo -i <press enter> (enter your password) <press enter>
type apt-get update <press enter>
type apt-get upgrade <press enter>
after this reboot
Open the terminal again.
Type sudo -i <press enter> (enter your password) <press enter>
Type apt-get install linux-headers-generic <press enter>
Type apt-get install build-essential <press enter>
Now look up at the top left of the VBox window and click devices then click install guest additions.  
If they do not show on the desktop then click devices and unmount CD, then click install guest additions again.
At this point they should be on your desktop.  Dbl click to open the CD.
Look for the Linux Guess Additions that fits your install.  More than likely the VBoxLinuxAdditions-x86.run
Position the terminal windows and the opened file system to where you can see them both.
Click and drag the right additions file and drop it on the terminal window.
Click on the terminal window to get focus and hit enter.
Watch for any errors that show and when they are complete reboot.
If all is well you use the click drag to make the window  bigger or use the host+F toggle to go in and out of full screen as well as being able to use USB and VBox Shared Folders.  
[/list]

Note: For USB you must be using the PUEL version of VBox because it is not supported in the OSE version.

---

### Post by kaboyish on 2009-10-19
> **Perryg said:**
> Beginners guide for installing guest additions desktop editions.
The steps also show the installation of Linux headers and build essential to allow compiling external modules. You can skip this part if you already have them installed.

[list]Start the guest
Open a terminal.
Type sudo -i <press enter> (enter your password) <press enter>
type apt-get update <press enter>
type apt-get upgrade <press enter>
after this reboot
Open the terminal again.
Type sudo -i <press enter> (enter your password) <press enter>
Type apt-get install linux-headers-generic <press enter>
Type apt-get install build-essential <press enter>
Now look up at the top left of the VBox window and click devices then click install guest additions.  
If they do not show on the desktop then click devices and unmount CD, then click install guest additions again.
At this point they should be on your desktop.  Dbl click to open the CD.
Look for the Linux Guess Additions that fits your install.  More than likely the VBoxLinuxAdditions-x86.run
Position the terminal windows and the opened file system to where you can see them both.
Click and drag the right additions file and drop it on the terminal window.
Click on the terminal window to get focus and hit enter.
Watch for any errors that show and when they are complete reboot.
If all is well you use the click drag to make the window  bigger or use the host+F toggle to go in and out of full screen as well as being able to use USB and VBox Shared Folders.  
[/list]

Note: For USB you must be using the PUEL version of VBox because it is not supported in the OSE version.

thanks man. will try this and let you know.

---

### Post by Dougie187 on 2009-10-19
> **kaboyish said:**
> thanks man. will try this and let you know.

Those instructions are only for a Linux guest (if your virtual machine was running ubuntu or something else), but you are running a windows guest inside a linux host.

It's not too difficult to install the guest additions. All you have to do is turn on your guest operating system, log in, and then click on at the top in the "Devices" menu, and go down to "Install Guest Additions", this will download a cd and mount it, and it may let you install it inside of windows. If not you might have to reboot into safe mode. Now, if you don't know how to do this, it's pretty easy to find step by step instructions on google, but just to give you an idea, you watch the screen as it's booting, and press F8 right before the windows loading screen comes up (the one with the blue bar that progresses from left to right). Once inside of safe mode (assuming you needed to use  safe mode) you click "Devices" and "install guest additions" again, and your guest additions should install.

After Guest Additions are installed, you will be able to select the USB device you want to run in your guest in the Devices menu.

---

### Post by kaboyish on 2009-10-23
hi. this is the message that i get when i try to install the guest additions. what should i do?:confused:

---

### Post by coldReactive on 2009-10-23
> **kaboyish said:**
> hi. this is the message that i get when i try to install the guest additions. what should i do?:confused:

Wait a while and try again. There's no real other way to get around that error. The virtualbox.org servers are pretty limited, often times they time out.

---

### Post by kaboyish on 2009-10-23
> **coldReactive said:**
> Wait a while and try again. There's no real other way to get around that error. The virtualbox.org servers are pretty limited, often times they time out.


thanks. let me give it a few minutes and try again later

---

### Post by kaboyish on 2009-10-25
hi guys. i finally figured out the problem. the version that i was using was outdated. i downloaded the latest version from the virtual box website, and that did the trick. I'd advice people to download the deb package from the virtual box website cause the ubuntu repository doesn't offer the latest version.
thanks for the support :guitar:

---

