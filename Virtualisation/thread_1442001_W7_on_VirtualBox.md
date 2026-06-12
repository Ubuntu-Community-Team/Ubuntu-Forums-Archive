---
title: "W7 on VirtualBox"
date: 2010-03-29
forum: Virtualisation
---

### Post by arashiko28 on 2010-03-29
I installed W7 with VirtualBox and get a message every time I boot. Screenshot below.

I already checked it's set to 32 bits, but the message keeps showing up.

The other thing is that can't set the screen resolution higher tan 800x600 because other way, I have to be releasing the mouse in order to scroll up and down the window to see the full desktop.
My laptop screen is 15.4 widescreen, according to help it's supposed to 1150 or something like that, but nothing works, not even on fullscreen mode.

I already miss terminal and synaptic...

Oh! I almost forgot... how do I transfer files between OS's? Like from my ubuntu desktop to windows desktop?

---

### Post by arashiko28 on 2010-03-29
HELP please, at least on the last item... how do I transfer files between ubuntu and virtualbox windows?

---

### Post by arashiko28 on 2010-03-29
Is there a way to transfer files??? I have tried everything, won't recognize USB drive, mounted, unmounted, plugged while running w7, plugged before starting... How can I transfer files between both????

I already added it on settings, but when I start w7, the checkbox is empty and the options disabled!

---

### Post by Marlonsm on 2010-03-29
The first thing you'll need is to install VBox guest additions.
Open the virtual machine and in the "Devices" menu you'll have to option to do so. When you click the "Install guest additions" button it'll mount a virtual CD in Windows and it should auto-run and prompt you to install.

This alone should fix the color/resolution problem after a reboot.

Now to file transfer. In that bar under the VM, right click the folder button and add a shared folder, give it any name and make it permanent.
Now in the VM, press [Windows key]+R, type cmd and hit Enter. It'll open the command prompt (just like the Linux terminal). Now type ```
net use X: \\vboxsvr\FolderName
``` changing "FolderName" for the name you've given to your folder, and hit Enter
Now every file you drop in that shared folder, will be in the X: drive in Windows 7 and every file you put in X: will be on the folder.

For USB support you'll need the Puel version of VBox, the open source one (found in the software center) doesn't work. With that, you'll need to add your user to the vboxusers group, take a look here for more details: [http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml](http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml)

---

### Post by arashiko28 on 2010-03-29
Thanks, I had found a way for it to work.

---

