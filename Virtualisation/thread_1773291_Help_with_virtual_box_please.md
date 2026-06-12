---
title: "Help with virtual box please?"
date: 2011-06-01
forum: Virtualisation
---

### Post by Tasogoro on 2011-06-01
I got this error 
 p, li { white-space: pre-wrap; }  Failed to open a session for the virtual machine Windows XP.
 Configuration error: Querying "DmiSystemVersion" as a string failed (VERR_CFGM_NOT_STRING).
 Unknown error creating VM (VERR_CFGM_NOT_STRING


 after following these
 [http://forums.virtualbox.org/viewtopic.php?f=8&t=28281](http://forums.virtualbox.org/viewtopic.php?f=8&t=28281)


 My BIOS info: 

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Dell Inc.
    Version: 1.0.0
    Release Date: 04/01/2008
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 1024 kB
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Dell Inc.
    Product Name: Inspiron 518
    Version: 00
    Serial Number: BDXB3H1
    UUID: 44454C4C-4400-1058-8042-C2C04F334831


 Help please, I don't know what to put in for system version.

---

### Post by Tasogoro on 2011-06-01
Ah never mind, I fixed it with 

VBoxManage setextradata "Windows XP" VBoxInternal/Devices/pcbios/0/Config/DmiSystemVersion ""

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2011-10-23
Tasogoro thanks a lot for sharing the solution. It helped me a lot when I got stuck with <EMPTY> instead of an empty string :)

---

