---
title: "Testing Vivid Vervet: Suspend Mode Problem / Wireless Keyboard USB Key Stays ON"
date: 2015-03-21
forum: Ubuntu Development Version
---

### Post by MikeMecanic on 2015-03-21
On suspend mode, the USB key light stays ON and mouse and keyboard are frozen.  The only way to get rid of that is 1) pressing shortly the on/off switch. 2) use the suspend mode switch on the keyboard but this solution is intermittent.  **The main problem is that** **the light of the USB key stays ON instead of being ****off bias on suspend mode**.  It was not the case in previous versions (10.04-14.04 LTS).  The problem appears to be intermittent and the desktop environment becomes unstable.

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Vivid Vervet (development branch)
Release:    15.04
Codename:    vivid


Regards,

---

### Post by MikeMecanic on 2015-03-21
Not able to reproduce the problem no more.  The sleep mode button (keyboard) reacts slowly and there is a noise that occurs that remind me the action of a relay that goes on and off.  Things seem to be back to normal. That's all I can say for the moment.

---

### Post by ventrical on 2015-03-22
Thats very interesting.  does that sound come from the keyboard or the mobo.

---

### Post by MikeMecanic on 2015-03-22
Comes from the motherboard

---

### Post by MikeMecanic on 2015-03-22
Intermittent problem:  keyboard suspend mode switch and with the mouse.  Try it several times and it comes back let say 1 time out 10.

---

### Post by ventrical on 2015-03-22
Usually the ATX PSU has the microswitch but then again , mobos have them too. This could be a power setting in BIOS. Are you using standard S3 .. and btw .. what type of mobo/PSU do you have .

Regards..

---

### Post by MikeMecanic on 2015-03-22
Inglewood/Intel [COLOR=#000000][FONT=HPRegular]647610-001[/FONT][/COLOR]
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1631871](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1631871)

 sudo lshw | grep -A5 "Motherboard"
       description: Motherboard
       product: 2ABB
       vendor: Quanta
       physical id: 0
       version: 101
     *-firmware
hp@hp-610-1130f:~$ dmidecode
# dmidecode 2.12
/dev/mem: Permission denied
hp@hp-610-1130f:~$ sudo dmidecode  | grep -A4 '^Base'
Base Board Information
	Manufacturer: Quanta
	Product Name: 2ABB
	Version: 101
	Serial Number:  
hp@hp-610-1130f:~$ sudo dmidecode -t 2
# dmidecode 2.12
SMBIOS 2.6 present.


Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: Quanta
	Product Name: 2ABB
	Version: 101
	Serial Number:  
	Asset Tag:  
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis:  
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

---

### Post by ventrical on 2015-03-23
Must admit that I haven't worked with those hp touch screen all-in-ones.

Regards..

---

