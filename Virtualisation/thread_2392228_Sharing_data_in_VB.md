---
title: "Sharing data in VB"
date: 2018-05-18
forum: Virtualisation
---

### Post by nooshinnr on 2018-05-18
Hi
I have recently installed ubuntu 16.04 and Virtual box 5.1.34. the guest OS is win7.
Now I have created the share folder but I can't share some files. small files can be shared but others are not. Beside all my usb ports are usb 3 and I can't access to my usb drivers and flash disks. So I totally can't transfer files in any way except via the mailing them!!!

I have tried to install the extension pack for vb but it didn't work.

---

### Post by The Cog on 2018-05-18
Can you use networking and SCP the files across? Just a thought.

---

### Post by ajgreeny on 2018-05-18
I suggest you update to VBox 5.2, and for usb3, you **must** have the Guest additions installed in the guest OS.

It's easiest to go to the **Debian-based Linux distributions** section of [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) and follow the instructions to add their repos to your system, then update install virtualbox-5.2 in the normal way. It will remove the 5.1 version automatically.

---

### Post by nooshinnr on 2018-05-20
sharing data is working between the two OS which means networking is ok. but some files can not be share in windows when i send them to share folder an error displays.I think its a problem with guest windows :(

---

### Post by howefield on 2018-05-20
Thread moved to the more appropriate "*Virtualisation*" forum.

---

### Post by SeijiSensei on 2018-05-20
Are you trying to share files on the virtual machine with other machines on a network besides the VirtualBox host?  I'm not really sure exactly what the problem is. 

If you want to see the virtual machine from other computers on the network, you must used "bridged" networking in VirtualBox rather than the default NAT.  NAT hides the VM behind the host the same way the computers on your network are hidden from the public Internet via your router. In bridged mode, the VM gets an address on the same network as the host computer and can be seen by other machines on the network.

Open the VirtualBox manager, select the Windows machine, and choose Settings > Network.  You can change from NAT to bridged there.

It sounds like this might be your problem, but I'm really not sure.

---

### Post by nooshinnr on 2018-05-22
> **SeijiSensei said:**
> Are you trying to share files on the virtual machine with other machines on a network besides the VirtualBox host?  I'm not really sure exactly what the problem is. 

If you want to see the virtual machine from other computers on the network, you must used "bridged" networking in VirtualBox rather than the default NAT.  NAT hides the VM behind the host the same way the computers on your network are hidden from the public Internet via your router. In bridged mode, the VM gets an address on the same network as the host computer and can be seen by other machines on the network.

Open the VirtualBox manager, select the Windows machine, and choose Settings > Network.  You can change from NAT to bridged there.

It sounds like this might be your problem, but I'm really not sure.



I had installed Vbox 5.1.34 on my ubuntu 16.04 and the guest OS on the VBox was a win7. the USB 3 was not working which I found out is a problem with the version of virtual box. but the main problem was the point that I was not able to share every file between the to OS.  was able to access to the share folder via both OS and some file were shared but when I tried to share large files or some other files an error was displayed in win7.

---

### Post by nooshinnr on 2018-05-22
Hello every one 
I uninstalled Vbox 5.1
and now I'm trying to install vbox 5.2
but I keep to receive the following error:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox-5.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'virtualbox-5.2' has no installation candidate

---

### Post by ajgreeny on 2018-05-22
Have you enabled the VBox repos as I suggested in post #3, above?
That will certainly make the 5.2 version available.

---

### Post by nooshinnr on 2018-05-22
> **ajgreeny said:**
> Have you enabled the VBox repos as I suggested in post #3, above?
That will certainly make the 5.2 version available.

I did but I receive this:There are no enabled repos.

---

### Post by monkeybrain20122 on 2018-05-22
> **nooshinnr said:**
> I had installed Vbox 5.1.34 on my ubuntu 16.04 and the guest OS on the VBox was a win7. the USB 3 was not working which I found out is a problem with the version of virtual box. but the main problem was the point that I was not able to share every file between the to OS.  was able to access to the share folder via both OS and some file were shared but when I tried to share large files or some other files an error was displayed in win7.

You have to setup a shared folder and mount it in VB. Make a folder then go to VBOX's Settings > Shared folders, you can set it to automount and grant full access to VBox guest.

To use usb device in vbox you have to install the guest additions 

and 

add yourself to the  vboxusers group

```
sudo usermod -a -G vboxusers $USER
```

Then logout and login again.

---

### Post by deadflowr on 2018-05-22
> **nooshinnr said:**
> I did but I receive this:There are no enabled repos.

Have you updated yet, so the repos can be found?
```
sudo apt update
```

as well,
Could you walk through the steps you ran when trying to enable the repos?

---

