---
title: "Virtualbox no network connections"
date: 2008-10-21
forum: Virtualisation
---

### Post by JakZ on 2008-10-21
Hi,


Yesterday I changed from dual boot to just the ubuntu install (whohoo!) but I'm running into a little trouble with virtualbox. I want my wireless connection to be useable by the VM.

I created a windows XP VM , installed Windows and booted the vm up.

 I'm not seeing any network connections. I activated the network in the settings for the virtual maching, but I don't get a network connection in the VM. I am seeing the hardware network card in hardware manager, but Windows XP VM -> control panel -> network connections is empty.


Please if anyone has a solution for this problem?



thank you

---

### Post by djwisdom on 2008-10-21
Check your Virtualbox Network->Adapter 0->Enable Network Adapter and use Attached to NAT.

Hope that helps.

---

### Post by JohnFH on 2008-10-21
What type of network did you setup in the virtualbox?  The simplest solution by far is to use NAT type and that should be adequate to allow XP to use your host internet connection.
I found the VirtualBox documentation very helpful recently, especially for networking issues:  [https://help.ubuntu.com/community/VirtualBox]("https://help.ubuntu.com/community/VirtualBox")
Hope that helps.

---

### Post by JakZ on 2008-10-21
I reinstalled another copy of ubuntu 8.10 beta (I know, kinda desperate) and installed virtualbox (not the open source version) for hardy heron, which I found on the Sun virtualbox website. I works now for some reason, with the exact same config, as far as I can tell.

On the the USB connectivity...:guitar:

---

