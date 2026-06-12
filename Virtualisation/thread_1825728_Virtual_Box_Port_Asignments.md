---
title: "Virtual Box Port Asignments"
date: 2011-08-15
forum: Virtualisation
---

### Post by Babyd3k on 2011-08-15
I need to assign 19 usb ports to 9 different virtual copies of Win XP so  I can slim down a data collection set up from 10 computers to 1. The  reason I have to assign all these ports is because the usb devices I am  using are literal clones of each other and there is no way to pick one  device from the pile and it is very important that every device gets  routed to the correct Win install or all the data will be ruined. 

Now here is what I have, I have a default install of 10.04 it has the  default install of the newest virtual box from sun downloaded last week.  There are 9 cloned VM's of Win XP Pro all set and ready. I have figured  out how to assign the 4 usb ports on the motherboard. What I had to do  to make those 4 work is as follows

 I issued the: 

VBoxManage list usbhost

command the output looks like this:
Address:            sysfs:/sys/devices/pci0000:00/0000:00:04.1/usb1/1-4//device:/dev/vboxusb/001/009


In a vbox forum post I was told that I find:
Address:            sysfs:/sys/devices/pci0000:00/0000:00:04.1/usb1/1-4

Then subtract 1 from the end and that would make this port 3 so I go  into the vbox control panel for usb make a filter and tell it to send  port 0003 to whatever v machine I'm in and it works slick. 

FYI: you can just put 3 but vbox will add the leading zeros

Now the problem starts here. I need 19 usb ports, I only have 4 on the  motherboard so I need to know the syntax for other controllers or usb  hubs. When I plug into a 5 port controller card I get this output 

Address:            sysfs:/sys/devices/pci0000:00/0000:00:04.0/usb5/5-5//device:/dev/vboxusb/005/002

Anyone have any ideas at all on how I turn this into a port number?

---

### Post by Jake.Debord on 2011-08-16
do you have the usb drives already mounted to the host?

---

### Post by Babyd3k on 2011-08-16
These aren't USB drives, they are an array of USB based sensors and cameras. I can mount and make any combination of them work correctly up to the 4 that connect to the motherboard, but that leaves me 15 usb ports short because I don't know the syntax for the connecting to the USB add in cards I have.

---

### Post by Jake.Debord on 2011-08-16
so your host doesn't recognize the pci cards? just the onboard? I would google the brand/model and host and see if your missing a driver or something simple hopefully. Past that, I apologize but I have nothing else to offer hopefully someone else does!

---

### Post by Babyd3k on 2011-08-16
No, it sees the cards fine, they work fine, it has nothing to do with the cards. I need to permanently assign the ports on the cards so say card 2 port 3 always gets sent to virtual os 3. I can do this with the first 4 ports because they number 1-1 though 1-5 which virtual box interprets as ports 0001-0004 when you move to a controller card the ports are labeled 2-1 though 2-5 so the formula I have no longer works. This is what I am looking for. 

The formula to turn port 5-1 into something that vbox can understand.

Just so people know, vbox with NOT except anything but a block of 4 numbers 0-9 as the port. Literally you can not enter any other value, non numeric keys are blocked out. If you enter less then 4 digits it will add leading zero's if you add more digits, say 5 it will just not work. 

Also I plugged in a device to address 2-1 and then just guessed every port from 5-22 just to see if I can happen on a pattern. It didn't work.

---

