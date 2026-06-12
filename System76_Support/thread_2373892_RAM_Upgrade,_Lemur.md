---
title: "RAM Upgrade, Lemur"
date: 2017-10-10
forum: System76 Support
---

### Post by webmanoffesto on 2017-10-10
[FONT=gotham]I have a System 76 Lemur laptop with 4GB RAM, what's the most RAM I can put in this, what type of RAM should I buy.


Is this correct?
System76 Laptop Lemur Compatible Memory / RAM Upgrades
[https://www.mrmemory.co.uk/memory-ram-upgrades/system76/laptop/lemur](https://www.mrmemory.co.uk/memory-ram-upgrades/system76/laptop/lemur)


It recommends DDR3 PC3-12800 1600MHz 204-pin SODIMM but doesn't say the max.


When I find links online to System 76 Lemur specs they just take me to a System76 Laptops page, because they are not selling the Lemur now.

[/FONT]
[FONT=gotham][/FONT]

---

### Post by untrustytahr on 2017-10-10
```
sudo dmidecode -t16 -t17
```

type 16 will give max and type 17 will list banks and memory types.

---

### Post by webmanoffesto on 2017-10-10
I think this tells me that max RAM is 16GB. Is that correct?
"[COLOR=#000000]Maximum Capacity: 16 GB[/COLOR]" That seems pretty clear.

sudo dmidecode -t16 -t17
```
# dmidecode 3.0
Getting SMBIOS data from sysfs.
SMBIOS 3.0.0 present.


Handle 0x0018, DMI type 16, 23 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 16 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2


Handle 0x0019, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x0018
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: SODIMM
    Set: None
    Locator: ChannelA-DIMM0
    Bank Locator: BANK 0
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1600 MHz
    Manufacturer: Samsung
    Serial Number: 25855033
    Asset Tag: 9876543210
    Part Number: M471B5173QH0-YK0  
    Rank: 1
    Configured Clock Speed: 1600 MHz
    Minimum Voltage: Unknown
    Maximum Voltage: Unknown
    Configured Voltage: 1.35 V


Handle 0x001A, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x0018
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: Unknown
    Set: None
    Locator: ChannelB-DIMM0
    Bank Locator: BANK 2
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified
    Rank: Unknown
    Configured Clock Speed: Unknown
    Minimum Voltage: Unknown
    Maximum Voltage: Unknown
    Configured Voltage: Unknown
```

---

### Post by untrustytahr on 2017-10-11
> **webmanoffesto said:**
> I think this tells me that max RAM is 16GB. Is that correct?

Handle 0x0018, DMI type 16, 23 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    [COLOR=#ff0000]**Maximum Capacity: 16 GB**[/COLOR]
    Error Information Handle: Not Provided
    [COLOR=#ff0000]**Number Of Devices: 2**[/COLOR]


Handle 0x0019, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x0018
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    **[COLOR=#ff0000]Size: 4096 MB[/COLOR]**
    **[COLOR=#ff0000]Form Factor: SODIMM[/COLOR]**
    Set: None
    Locator: ChannelA-DIMM0
    Bank Locator: BANK 0
    [COLOR=#ff0000]**Type: DDR3**[/COLOR]
    Type Detail: Synchronous
    **[COLOR=#ff0000]Speed: 1600 MHz[/COLOR]**
    [COLOR=#ff0000]**Manufacturer: Samsung**[/COLOR]
    Serial Number: 25855033
    Asset Tag: 9876543210
    **[COLOR=#ff0000]Part Number: M471B5173QH0-YK0 [/COLOR]** 
    Rank: 1
    Configured Clock Speed: 1600 MHz
    Minimum Voltage: Unknown
    Maximum Voltage: Unknown
    Configured Voltage: 1.35 V


Yes, you have 2 slots that can total 16GB.

4 GB is a bit low depending on what you are doing and what desktop environment you are running, but the real way to know if you need memory is to see if the system is swapping. There are a number of ways you can do that:  The system monitor gui under the process tab will give a graph of memory and swap in use.  The "top" command will also show it along the the bottom of the top section.  You can also use the vmstat command.  The so/si columns will show blocks swapping in/out.

---

### Post by webmanoffesto on 2017-10-11
Yes, according to Top it is swapping. Swap space is about 4GB.
Which raises another question. 
If I upgrade this to (what seems to be its max of) 16GB, would I have to repartition in order to get 16 GB swap space?

---

### Post by untrustytahr on 2017-10-11
Yes, you would need to reallocate space if you wanted to match your RAM size.  How that's done depends on how the system was initially installed (LVM w/encryption or just straight partitiions).  I believe newer non-encrypted installs now use a swap file instead of a partition (but don't quote me on that, I just remember reading something about it).

Is this on a SSD or a regular HDD?  Rather than bump it up to 16 GB you could bump it to 8GB (either 2x4GB or 1X8GB) and put the savings towards a SSD.  Even if it does still swap, swapping to a ssd is still faster than writing to hdd.  If you went the 1x8GB path, you could always still put another 8 in the unused slot if it was still swapping.  Quadrupling your ram in one shot is an awfully big bump.  I guess it would depend on how much your swap was being used.  Just my opinion though... I'm no expert by any means.

---

### Post by kurt18947 on 2017-10-11
A tool I find easy to interpret is htop. It's found in the repository, runs in a terminal window and is quite light on resources. Starting with I think 17.04, Ubuntu no longer creates a swap partition by default. If you want swap, create a swap file as untrustytahr recommends. The only limitation I'm aware of with the swap file is that you can't use hibernation. Suspend works fine, hibernation does not. If you go with an SSD - the best upgrade available IMO - you'll find booting fast enough that I doubt you'd miss hiberation (even if you were able to get it to work reliably). 

It sounds like you have an empty memory slot. If it were me, I'd check Ebay for a vendor offering a SODIMM with the correct specs and preferably the same manufacturer and fill that other slot. Then look at SSDs. Now is not a great time to be shopping for things that use NAND - prices are high compared to where they were and I don't know that they're expected to drop much for some time. There's lots of demand for flash storage and not much new manufacturing capacity in the very near future. I've read maybe mid 2018, NAND and DRAM prices may decrease. It'll be interesting to see what prices do during the holiday shopping season.

---

### Post by 1clue on 2017-10-11
No, you can create a swap space as a real file on the disk, say for example:

```

sudo dd if=/dev/null of=/swapfile bs=1024 count=(whatever number of kilobytes you want your file to be)
sudo mkswap /swapfile
sudo swapon /swapfile

```

This can be done on a running system, and in fact I've done so in emergency situations. ***Edit:** Actually in one case I can think of the file has been there for several years on a production system.*

You would need to modify /etc/fstab if you want the swap space to be permanent.

You can have as many swap spaces as you like, but if you want to hibernate you'll need to have at least one file which can completely contain all of RAM.

---

### Post by kurt18947 on 2017-10-11
Here are another set of instructions to create a swap file. It's fairly verbose. I've used it in the past with no ill effect that I'm aware of.

[https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04)

---

### Post by 1clue on 2017-10-12
Yeah, never occurred to me to use fallocate before.

---

