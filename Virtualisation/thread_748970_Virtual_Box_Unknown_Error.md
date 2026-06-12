---
title: "Virtual Box Unknown Error"
date: 2008-04-08
forum: Virtualisation
---

### Post by hitspace on 2008-04-08
i was using virtual box ose for a while untill i realized the usb support was on the licensed version so i got it of suns website

it all installed well 
i was setting up the parameters on the settings panel 

it gave me this warning

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
0x80004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}


can someone tell me what its pertaining to and how it will effect my virtual computer . will i still be able to use my usbs . if not some code to fix it would be nice . thanks

---

### Post by thinkerisme on 2008-05-04
> **hitspace said:**
> i was using virtual box ose for a while untill i realized the usb support was on the licensed version so i got it of suns website

it all installed well 
i was setting up the parameters on the settings panel 

it gave me this warning

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
0x80004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}


can someone tell me what its pertaining to and how it will effect my virtual computer . will i still be able to use my usbs . if not some code to fix it would be nice . thanks


sudo gedit /etc/init.d/mountdevsubfs
find these 
    #
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb
and uncomment these
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb

---

