---
title: "Installing Gui without internet connection ??"
date: 2009-02-21
forum: Server Platforms
---

### Post by police512 on 2009-02-21
hey,

Is it possible to install a gui user interface in ubuntu server edition 8.10 without a internet connection... 
sorry i no it has been brought up a couple of times but i dont have a internet connection because my modem isnt compacatible with ubuntu. so is it possible to install Gnome to ubuntu server edition wheather i can download it put it on a usb, ow btw im using Vmware and i have installed in Vmware! and ive isntalled it on a dell studio 15 laptop

Thx if anyone can get back to me A.S.A.P 
then i would be gratefull

---

### Post by theozzlives on 2009-02-21
There's a way to add the alternate CD to the repositories but for the life of me I can't remember. My suggestion is to burn the CD and someone will be along that remembers how to add a CD.

---

### Post by police512 on 2009-02-21
Do u mean burn the cd to add the GUI to ubuntu server? and i only have the .iso file that i downloaded and run it through Vmware, i want if i can to install a gui gnome if possible!

Any help??

---

### Post by theozzlives on 2009-02-21
ok, edit your sources.list:
```
sudo vi /etc/apt/sources.list
```
and add this line:
```
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted
```
then type:
```
sudo apt-get update
```
with the CD in, then type:
```
sudo apt-get install ubuntu-desktop
```
I'm pretty sure that'll do it.

---

### Post by theozzlives on 2009-02-21
> **police512 said:**
> Do u mean burn the cd to add the GUI to ubuntu server? and i only have the .iso file that i downloaded and run it through Vmware, i want if i can to install a gui gnome if possible!

Any help??

you are running the server software in VMWare??? Why?

---

### Post by police512 on 2009-02-21
Yeah im running in vmware and its cuz i want to test it and get everything running...

sorry to be a pain but how and where do u do this ??...
where do u put it in
and how in 1 line or underneath each ova??

---

### Post by theozzlives on 2009-02-21
> **police512 said:**
> Yeah im running in vmware and its cuz i want to test it and get everything running...

sorry to be a pain but how and where do u do this ??...
where do u put it in
and how in 1 line or underneath each ova??

In Ubuntu, I think it best to use the desktop version of Ubuntu.

---

### Post by police512 on 2009-02-21
Why? 
i want to install a GUI in ubuntu server edition...
but i havent gt a internet connection...
so can i still do it make a server in ubuntu desktop edition as well... by either adding software to it and so on

---

### Post by theozzlives on 2009-02-21
On the desktop you can run LAMP (Linux Apache MySQL PHP), DHCP. DNS, Mail Server, FTP Server, File Server. Print Server. etc. I think the only dif is GUI and the kernel. I'm running my web site with the Desktop and Apache. I used to run the server but found it pointless.

---

### Post by police512 on 2009-02-21
so u can basically do the same things on ubuntu desktop 
so il try ubuntu desktop 8.10 and install those packages to it

thx for ur help :)

---

### Post by theozzlives on 2009-02-21
I'm pretty sure the server is meant for an actuall server computer.

---

### Post by police512 on 2009-02-21
yeah but u can make any desktop or laptop into a server
even though a laptop isnt exactly the best but it still can be done, and i didnt want to make my laptop into a server i wanted to test ubuntu server and get everything right b4 i install it to a actauly desktop computer that will be made into a server!!

---

