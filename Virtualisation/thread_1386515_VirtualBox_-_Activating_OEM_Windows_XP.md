---
title: "VirtualBox - Activating OEM Windows XP"
date: 2010-01-20
forum: Virtualisation
---

### Post by mepaco on 2010-01-20
I have a Dell e1505 that came with Windows XP MCE installed.  I have been dual booting but I'm sick of having to restart for the quick tasks I need to perform in Windows.  I decided to try VirtualBox but I cannot get XP to authenticate correctly.  I have fixed the DMI information and the MAC address as detailed in the following thread but it hasn't helped:

[http://forums.virtualbox.org/viewtopic.php?p=37931&sid=d9f528f0a73c6343b442c32a1f4727dd#p37931](http://forums.virtualbox.org/viewtopic.php?p=37931&sid=d9f528f0a73c6343b442c32a1f4727dd#p37931)

So I'm hoping that either somebody has some other suggestions or can definitively tell me that it is hopeless.

Thanks in advance,
Paco

---

### Post by thegreatpenguin on 2010-01-20
Im not sure what in windows you are wanting to access that you use what i do to access my windows programs that i really like is mount the drive and run them under wine while using ubuntu I have only found a few programs wine will not run.

---

### Post by SteveHillier on 2010-01-20
What are you using as the host system, Windows or Ubuntu?
Are you trying to activate Windows as the host or the guest?

I have only just started using VirtualBox.  I used Ubuntu as the host and installed Xindows XP Pro as a guest and did not get any problem.

More information might help us to help you.

---

### Post by mepaco on 2010-01-20
Thanks for the quick replies.  The main programs that I need to use in Windows would be Paint.NET, Excel, and Internet Explorer (7 or greater).  I also occasionally need to use Visual Studio 2008 and SQL Server 2008.  Those are bigger tasks so I don't mind dual booting for those but if I'm going to switch to virtualization, they have to work there.

Sorry my first post wasn't clear; I'm using Ubuntu as the host and trying to activate XP as the guest.  I initially tried just installing it without any customization but that didn't work.  After finding the thread I referenced in the first post, I altered my DMI information and my MAC address.  Here is the info I used for my DMI values:

```
sudo dmidecode -t0
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Dell Inc.
	Version: A09
	Release Date: 09/29/2006
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 576 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PC Card (PCMCIA) is supported
		...
		Targeted content distribution is supported
	BIOS Revision: 0.9
	Firmware Revision: 0.9

sudo dmidecode -t1
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0100, DMI type 1, 27 bytes
System Information
	Manufacturer: Dell Inc.
	Product Name: MM061                           
	Version: Not Specified
	Serial Number: 76VC1C1
	UUID: 44454C4C-3600-1056-8043-B7C04F314331
	Wake-up Type: Power Switch
	SKU Number: Not Specified
	Family:  

```

Here is what I used to try and get it to activate.

```
#! /bin/bash
VM_NAME="WinTest" # Name of your Virtual Machine
VSETED="VBoxManage setextradata $VM_NAME"
CFG_PATH="VBoxInternal/Devices/pcbios/0/Config"
$VSETED $CFG_PATH/DmiBIOSVendor       "Dell Inc."
$VSETED $CFG_PATH/DmiBIOSVersion      "A09"
$VSETED $CFG_PATH/DmiBIOSReleaseDate  "09/26/2006"
$VSETED $CFG_PATH/DmiBIOSReleaseMajor  0
$VSETED $CFG_PATH/DmiBIOSReleaseMinor  9
$VSETED $CFG_PATH/DmiBIOSFirmwareMajor 0
$VSETED $CFG_PATH/DmiBIOSFirmwareMinor 9
$VSETED $CFG_PATH/DmiSystemVendor     "Dell Inc."
$VSETED $CFG_PATH/DmiSystemProduct    "MM061"
$VSETED $CFG_PATH/DmiSystemVersion    "<EMPTY>"
$VSETED $CFG_PATH/DmiSystemSerial     "76VC1C1"
$VSETED $CFG_PATH/DmiSystemUuid       "44454C4C-3600-1056-8043-B7C04F314331"
$VSETED $CFG_PATH/DmiSystemFamily     ""

```

Unfortunately, the copy of XP that came with my computer (Dell restore disc) doesn't want to authenticate.  Any suggestions?

Thanks,
Paco

---

### Post by Nightstrike2009 on 2010-01-21
I'd just ring Microsoft and activate via the telephone, providing its not already activated on the windows side (If your dual booting).

If you search on Google there is probably some "dodgy" patch you could use to get around this too, but I haven't used anything like that so use at your own risk.

---

### Post by SteveHillier on 2010-01-21
> **Nightstrike2009 said:**
> I'd just ring Microsoft and activate via the telephone, providing its not already activated on the windows side (If your dual booting).

Of course!  If you do phone and there are diffuculties you can get through to an agent who might ask if ths OS is installed anywhere else.  When I have had to do this is the past they have normally given an activation code.  They will ask how many machines it is installed on and with the right answer it is no problem.

---

