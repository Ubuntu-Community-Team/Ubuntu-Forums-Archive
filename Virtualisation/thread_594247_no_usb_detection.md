---
title: "no usb detection"
date: 2007-10-27
forum: Virtualisation
---

### Post by Tucatts on 2007-10-27
There is supposed to be a tab in Virtualbox settings that is : USB Device filters.

It just ain't there in my VB install on Gutsy. I am trying to install my Epson scanner which connects by USB of course and the install goes fine until I have to connect the USb. Then it tells me that it can't find the printer. I have done lsusb in terminal and the usb device (Epson) shows up. The Virtualbox manual tells me to click on "USB Deivde Filters and add the printer/scanner ID which I could do if I could fine USB Device filters!. Any suggestions? Maybe there is a settings tab that is different from the one on the main window? 
Thanks!

---

### Post by timgrin on 2007-10-31
bump(*,)

I am having the same problem]

---

### Post by Runamok on 2007-11-01
Are you saying the USB setting options are gone on your version of VirtualBox? 

Open VirtualBox.
Click on Settings
Then on the left hand list box click USB.
Then connect your USB device
then click the little USB icon on the right with the green plus sign next to it...

---

### Post by cowb0y on 2007-11-03
If there is no USB item in the Virtualbox Settings dialog (on the left side), see  **[this post]("http://ubuntuforums.org/showthread.php?t=598390")**.

---

### Post by timgrin on 2007-11-20
I fixed this by changing the vmode=666 for the usbfs line to devmode=664 - somewhere I think someone has posted a fstab example with vmode rather than devmode

---

### Post by teja483 on 2011-05-23
hii all

even i have similar problem.........

but not in Virtualbox..... in UBUNTU 10.04 LTS itself. when i mount my USB. it is not getting detected....

so i went for seartching threads . i stopped here and tried to append 

" none /proc/bus/usb/ usbfs devmode=664 0 0"   to the /etc/fstab.
 and typed the command sudo mount -a

for which i got 

root@testuser:/etc# sudo mount -a
mount: mount point /proc/bus/usb does not exist


what should i do guys.......?????????:)

---

