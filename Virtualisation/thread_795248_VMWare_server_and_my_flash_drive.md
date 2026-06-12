---
title: "VMWare server and my flash drive"
date: 2008-05-15
forum: Virtualisation
---

### Post by ekmon1582 on 2008-05-15
I installed 8.04 on VMWare server, and VMWare server asked me to disable auto-run, because it could have unpredictable results. While now since auto-run is disable, when I put my flash drive into my computer, Ubuntu doesn't see it. Windows sees it fine. Anyone know how I can get Ubuntu to see my flash drive?

---

### Post by bodhi.zazen on 2008-05-15
Fire up Ubuntu in VMWare.

Plug in your flash drive.

Go to the menu at the top of VMWare server 

VM -> Removable devices -> select your flash drive.

Alternate is to share the device via a network protocol, such as samba. Samba should be working "out of the box", share the flash drive from Windows and mount it from Ubuntu (Under network places).

---

### Post by ekmon1582 on 2008-05-16
Thanks for the reply. VMWare doesn't show my flash drive under that menu, and I tried samba, but couldn't get it installed.

---

### Post by bodhi.zazen on 2008-05-16
I assume windows is the host and Ubuntu guest ?

Samba == windows share so there is nothing to install, works out of the box on both OS.

For your USB, plug in the device, go to my computer, Right click the USB device , select sharing and security, share the device as say "USB" without quotes.

Now fire u Ubuntu guest, go to Places -> Network . Navigate to your windows share, click USB -> Enter Windows login and password.

If that fails, put

//xxx/yyy.zz/USB in the Ubuntu Browser location bar (xxx.yy.zz == your windows IP address)

---

### Post by ekmon1582 on 2008-05-19
When I go to sharing and security in Windows, I get taken to this screen. What do I do at this screen?
[IMG]http://i267.photobucket.com/albums/ii293/ekmon1582/forum%20shots/helpplz.jpg[/IMG]

---

### Post by bodhi.zazen on 2008-05-19
Run the "Network setup wizard"

---

### Post by ekmon1582 on 2008-05-20
I ran it, and tried setting it up... did I do it right?
[IMG]http://i267.photobucket.com/albums/ii293/ekmon1582/forum%20shots/usbshotplz.jpg[/IMG]

---

### Post by fjgaude on 2008-05-20
If you wish to both read and write to the shared files I would check the "Allow network users to change files" box.

---

### Post by ekmon1582 on 2008-05-20
Awesome that was it, thank you both!!

---

### Post by fjgaude on 2008-05-20
With the forums here sooner or later we get to where we wish to be, eh?

---

### Post by ekmon1582 on 2008-05-20
Indeed :).

---

