---
title: "How do you make a proper USB start up for remix"
date: 2009-12-20
forum: Ubuntu Moblin Remix
---

### Post by Pycnopodia on 2009-12-20
Please help.
I have tried making several already, I have tried it first on a mac at work with the instructions on the ubuntu homepage. It did not work. Then I tried 4-5 times on ubuntu, which I installed on the netbook using a external cd drive but is not the remix, just the regular ubuntu. I have tried using gparted afterwhich I used the usb startup creator, I have tried using a couple other programs and even terminal code (I am not so good with terminal yet), all of which has failed. I actually thought that I had made one just a little while ago but my computer does not recognize it when I restart the computer, it just goes straight to the ubuntu that I have installed already. Now I am almost ready to give up and just continue using the regular ubuntu (even though it does not resize firefox correctly and it does not recognize when I plug my headphones in), but I thought I would ask to see if anybody could help me out. If not thanks for at least reading this thread.

---

### Post by con_ritmo on 2009-12-22
if this is in regards to UNR,  i install remix 9.04 and then upgrade up to remix 9.10 through the update manager. that seems to do the trick for me.  I could never get 9.10 to boot off from USB.  neither ubuntu nor unr. 

you dont actually need an external cd drive...pendrivelinux has a method of installing the 9.04 remix img to a usb flash drive.   and from that usb you do a normal install...either to the hd, or to another usb flash/sd card. what's neat is that if you install to a flash drive/sd card...it will act like a NORMAL hd installation...meaning you can do system updates.  afaik those persistent usb install techniques dont allow you to do system updates.  

id make sure to format all the applicable devices/partitions.  

now if you just wanted to install to hd and boot off of usb... run the install.  select and format one hd partition for "\"...and then select and format your usb drive for "\boot".  before you're done installing, make sure to click "advanced" and select your usb drive as the location for your boot.  provided you're starting with a 9.04 install...that should do it.  at least it did for me.

---

