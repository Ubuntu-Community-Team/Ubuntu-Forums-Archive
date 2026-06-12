---
title: "usb ethernet adapter interface not available in ubuntu 21.10"
date: 2022-04-21
forum: Virtualisation
---

### Post by drc0rt3x on 2022-04-21
Dear to all, I have the following scenario: I have as host operating system windows 10 x64 and as guest operating system linux ubuntu 21.10 in virtual machine.
I want use a usb/ethernet adapter 3.0 type c in linux o.s. and also add a vlan interface.
when I try to make virtual machine with vmware workstation the usb device isn't found with "lsusb" command, while with virtualbox usb device is founded but connection is grayed... if I give "nmcli device status" the row of connection is showed but the status is unavailable. 


I have added Oracle VM VirtualBox Extension Pack. In the following image there are the settings
[https://i.stack.imgur.com/xiswv.png](https://i.stack.imgur.com/xiswv.png)

[https://i.stack.imgur.com/52dy2.png](https://i.stack.imgur.com/52dy2.png)

[https://i.stack.imgur.com/MqNbC.png](https://i.stack.imgur.com/MqNbC.png)

[https://i.stack.imgur.com/JJ5O5.png](https://i.stack.imgur.com/JJ5O5.png)

following there are output of lsusb and nmcli

```
fra@fra-Linux:~/Scrivania$ sudo lsusb
Bus 002 Device 002: ID 0b95:1790 ASIX Electronics Corp. AX88179 Gigabit Ethernet
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
fra@fra-Linux:~/Scrivania$ nmcli device status
DEVICE           TYPE      STATE            CONNECTION             
enp0s3           ethernet  collegato        Connessione via cavo 1 
enx000ec6556c66  ethernet  non disponibile  --                     
enx000ec6556.83  vlan      non disponibile  --                     
lo               loopback  non gestito      --                     
fra@fra-Linux:~/Scrivania$ 
```


state "non disponibile" means "unavailable" or "not available"


state "collegato" means "linked"


state "non gestito" means "not managed"


in the prompt "Scrivania" means desktop


in the following 2 screenshot you can view that connessione ethernet 1 isn't showed to desktop applet

[https://i.stack.imgur.com/n6udt.png](https://i.stack.imgur.com/n6udt.png)

[https://i.stack.imgur.com/7adGU.png](https://i.stack.imgur.com/7adGU.png)

How can I fix this issue?

---

### Post by DuckHook on 2022-04-21
Please do not add images to the body of your post. This is problematic for those using small screens or who are on restricted bandwidth. If you need to include images, do so as attachments using the paperclip icon in the "adv reply" toolbox.

Also, please use only default fonts and styles. Non-default styles are hard to read and can display poorly on different browsers and setups.

---

### Post by drc0rt3x on 2022-05-04
nobody?

---

### Post by &amp;KyT$0P# on 2022-05-04
Try running these commands in Terminal in your Ubuntu guest -
```
sudo touch /etc/NetworkManager/conf.d/10-globally-managed-devices.conf
sudo systemctl restart NetworkManager
```

---

### Post by drc0rt3x on 2022-05-14
> **halogen2 said:**
> Try running these commands in Terminal in your Ubuntu guest -
```
sudo touch /etc/NetworkManager/conf.d/10-globally-managed-devices.conf
sudo systemctl restart NetworkManager
```

These command I should use in vmware or in virtual box?

---

### Post by &amp;KyT$0P# on 2022-05-14
> **drc0rt3x said:**
> These command I should use in vmware or in virtual box?

Sorry, I missed that you mentioned a VMware machine in the original post.  Those commands are to try in your VirtualBox Ubuntu guest.

---

### Post by drc0rt3x on 2022-05-14
> **halogen2 said:**
> Sorry, I missed that you mentioned a VMware machine in the original post.  Those commands are to try in your VirtualBox Ubuntu guest.

I have tried your commands but nothing is changed... the usb network adapter is always unavailable

p.s.: I have uodated ti ubuntu 22.04 both vmware that virtualbox machine

---

