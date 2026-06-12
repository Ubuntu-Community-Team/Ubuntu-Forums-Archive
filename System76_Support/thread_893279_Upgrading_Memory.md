---
title: "Upgrading Memory?"
date: 2008-08-18
forum: System76 Support
---

### Post by kevin11951 on 2008-08-18
Hi,

I have a Gazv5 Nvidia, and was wondering if i were to go on newegg and get more memory, and stick in in my laptop, what would that do to my warranty?

i believe i asked this before, but i dont remember the answer...

also, what memory type and speed do i tell newegg? [http://www.newegg.com/Store/SubCategory.aspx?SubCategory=381&name=Laptop-Memory](http://www.newegg.com/Store/SubCategory.aspx?SubCategory=381&name=Laptop-Memory)

and how many open slots are there on my computer? (i ordered it with 2 gb)

---

### Post by amo-ej1 on 2008-08-18
Install the package 'dmidecode', then run 

sudo dmidecode and look at the output on my laptop it says for example:

```

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM Slot 1
	Bank Connections: 0 1
	Current Speed: 155 ns
	Type: DIMM SDRAM
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM Slot 2
	Bank Connections: 2 3
	Current Speed: 155 ns
	Type: DIMM SDRAM
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

```

Which shows I've got two slots and that one of them is filled with  2 gigabyte.

usually upgrading ram will not influence you warranty, and usually vendors place 2x1gb instead of 1x2gb.

---

### Post by thomasaaron on 2008-08-18
Kevin, your Gazelle can handle 4GB or RAM if you are running 64-bit Ubuntu. You have two slots (total) in your machine. But I don't remember how much memory you purchased your machine with.

cat /proc/meminfo
...will tell you how much is currently installed.

You need DDR2 / 667MHz RAM.

---

### Post by kevin11951 on 2008-08-18
so this means i have one in both slots?

```
Handle 0x000E, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x000D
	Error Information Handle: No Error
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: SODIMM
	Set: 1
	Locator: M1
	Bank Locator: Bank 0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: Mfg 0
	Serial Number: 1234-B0
	Asset Tag: Not Specified
	Part Number: SODIMM000

Handle 0x000F, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x000D
	Error Information Handle: No Error
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: SODIMM
	Set: 1
	Locator: M2
	Bank Locator: Bank 1
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: Mfg 1
	Serial Number: 1234-B1
	Asset Tag: Not Specified
	Part Number: SODIMM001

```

---

### Post by thomasaaron on 2008-08-18
Indeed.

So, to upgrade to 4GB, you would need to purchase two more memory sticks.

Hey, Kevin, remove the smallest rectangular panel on the bottom of your gazzy and have a lookie-see. Those are the memory cards.

You're our up-and-coming padawan around here. In order to be a true warrior you must have both a highly developed *knowledge* of linux and the ability to disassemble and reassemble your machine... blindfolded... under extreme stress... while fighting the forces of evil... with your light saber... and saving a damsel in distress at the same time... eight days a week, 25 hours a day without rest...

Do not fear and don't remove *anything* *ever* without first disconnecting both your ac adapter and battery.

---

### Post by benjo316 on 2008-08-18
Also a good idea to turn off the laptop computer before unplugging it. ;)

---

### Post by thomasaaron on 2008-08-18
Yes. I forgot that technique. =D>

---

