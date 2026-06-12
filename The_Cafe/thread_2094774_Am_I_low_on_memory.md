---
title: "Am I low on memory?"
date: 2012-12-14
forum: The Cafe
---

### Post by sdowney717 on 2012-12-14
I have 4gb and run 64 bit 12.04

I noticed lately, when I have lots of browser tabs open, the hard drive gets hit a lot, and the browsers slow down. Chrome can even stop responding.
By lots of tabs, I mean 20 to 30 for Chrome.
Firefox slows down after 10 tabs, Chrome does better.

I tend to just keep opening tabs and leave them open for days even.
On Chrome, I can open so many the tab icon goes blank white, then its hard to tell what it is.
I can get another 4gb which I think will help.

---

### Post by jerome1232 on 2012-12-14
Pop open system monitor and check when you notice this going on. It has a memory tab that will show you your ram status and swap usage.

It certanly sounds like you might be swap thrashing, try and close a few tabs?

---

### Post by CharlesA on 2012-12-14
> **jerome1232 said:**
> Pop open system monitor and check when you notice this going on. It has a memory tab that will show you your ram status and swap usage.

It certanly sounds like you might be swap thrashing, try and close a few tabs?
+1.

Another option is to run top/htop from a terminal window and check on it once that starts happening.

---

### Post by sdowney717 on 2012-12-14
Is there a command you can run that will tell you what the installed memory is as far as type?

The board is an Asus p5qc

On the Crucial site, it says takes ddr2 or ddr3
I dont know if I can mix ddr3 with ddr2. I have 2 x 2gb ddr2 right now.

---

### Post by jerome1232 on 2012-12-14
```
sudo lshw -C memory
```

If you mix speeds (I'm going off memory) it's likely it will reduce everything to the lowest speed present.

1333 mhz is ddr3, I think 667? is ddr2

---

### Post by sdowney717 on 2012-12-14
I know this board has a lot of memory slots

```
scott@scott-P5QC:~$ sudo lshw -C memory
[sudo] password for scott: 
  *-firmware              
       description: BIOS
       vendor: American Megatrends Inc.
       physical id: 0
       version: 0803
       date: 06/26/2008
       size: 64KiB
       capacity: 960KiB
       capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: 5
       slot: L1-Cache
       size: 64KiB
       capacity: 64KiB
       capabilities: internal write-back data
  *-cache:1
       description: L2 cache
       physical id: 6
       slot: L2-Cache
       size: 4MiB
       capacity: 4MiB
       capabilities: internal write-back unified
  *-memory
       description: System Memory
       physical id: 3a
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: DIMM [empty]
          product: ModulePartNumber00
          vendor: Manufacturer00
          physical id: 0
          serial: SerNum00
          slot: DIMM0
     *-bank:1
          description: DIMM DDR Synchronous 667 MHz (1.5 ns)
          product: ModulePartNumber01
          vendor: Manufacturer01
          physical id: 1
          serial: SerNum01
          slot: DIMM1
          size: 2GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
     *-bank:2
          description: DIMM [empty]
          product: ModulePartNumber02
          vendor: Manufacturer02
          physical id: 2
          serial: SerNum02
          slot: DIMM2
     *-bank:3
          description: DIMM DDR Synchronous 667 MHz (1.5 ns)
          product: ModulePartNumber03
          vendor: Manufacturer03
          physical id: 3
          serial: SerNum03
          slot: DIMM3
          size: 2GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
scott@scott-P5QC:~$ 

```

---

### Post by tgalati4 on 2012-12-14
You can install adblock in both firefox and chrome.  This will help reduce the ad noise and reduce the memory footprint of all of those open tabs.

---

### Post by jerome1232 on 2012-12-14
> **sdowney717 said:**
> I know this board has a lot of memory slots

```
scott@scott-P5QC:~$ sudo lshw -C memory
[sudo] password for scott: 
  *-firmware              
       description: BIOS
       vendor: American Megatrends Inc.
       physical id: 0
       version: 0803
       date: 06/26/2008
       size: 64KiB
       capacity: 960KiB
       capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: 5
       slot: L1-Cache
       size: 64KiB
       capacity: 64KiB
       capabilities: internal write-back data
  *-cache:1
       description: L2 cache
       physical id: 6
       slot: L2-Cache
       size: 4MiB
       capacity: 4MiB
       capabilities: internal write-back unified
  *-memory
       description: System Memory
       physical id: 3a
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: DIMM [empty]
          product: ModulePartNumber00
          vendor: Manufacturer00
          physical id: 0
          serial: SerNum00
          slot: DIMM0
     *-bank:1
          description: DIMM DDR Synchronous 667 MHz (1.5 ns)
          product: ModulePartNumber01
          vendor: Manufacturer01
          physical id: 1
          serial: SerNum01
          slot: DIMM1
          size: 2GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
     *-bank:2
          description: DIMM [empty]
          product: ModulePartNumber02
          vendor: Manufacturer02
          physical id: 2
          serial: SerNum02
          slot: DIMM2
     *-bank:3
          description: DIMM DDR Synchronous 667 MHz (1.5 ns)
          product: ModulePartNumber03
          vendor: Manufacturer03
          physical id: 3
          serial: SerNum03
          slot: DIMM3
          size: 2GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
scott@scott-P5QC:~$ 

```

Looks like DDR2, I would consult your motherboards manual to see if you can mix speed,s it *might* allow ddr3 in slots 0 and 2 to run at full speed and ddr2 in slots 1 and 3 to run at ddr2 speed, it varies by motherboard how this stuff is handled.

---

### Post by Frogs Hair on 2012-12-14
The Chrome cache fills up fast. You can go to settings > advanced settings >  privacy and clear it when you are finished for the day .

---

### Post by sdowney717 on 2012-12-15
It is starting to slow, so looked at system monitor and most of my ram is used up. Have 27 tabs open.

I have read Linux uses up available ram as free ram is wasted ram.
what do you think?

---

### Post by jerome1232 on 2012-12-15
You are swap thrashing, you need to either get more ram, or learn to close tabs in your browsers.

---

### Post by sandyd on 2012-12-15
> **sdowney717 said:**
> It is starting to slow, so looked at system monitor and most of my ram is used up. Have 27 tabs open.

I have read Linux uses up available ram as free ram is wasted ram.
what do you think?

your running out of ram, in fact, im surprised the OOM Killer hasn't popped up yet

---

### Post by cariboo on 2012-12-15
Unfortunately using system monitor, doesn't give you a true picture of resource usages, as it adds it's on overhead to the mix, anywhere from 12% to 20% of resource usage. I still find the command line utilities give a much better picture of resource usage, although it does take a bit more knowledge to understand what you are seeing.

Top, will give you a picture of memory and cpu usage, and another good tool is free.

---

### Post by jerome1232 on 2012-12-15
He's 2 GB's into his swap, I just don't think system monitor is the application hogging those resources. I can personally observe next to no difference between running just system monitor, and running gnome-terminal + htop, and this is on a netbook with 1 GB of ram.

Both top and htop use resources as well, system monitor isn't as heavy as you claim. system monitor is much easier for your standard user to understand.

---

### Post by monkeybrain2012 on 2012-12-15
What kind of tabs? If you have videos and stuffs it may take more memory.

I have 3G of ram running Ubuntu 12.04 32 bits with 100+ tabs open in Firefox with no visible slow down (it can handle ~60 tabs easily) while Chrome can handle about 30.

FF (since 16?) by default only loads tabs on demand that really makes it easy on memory (for older versions you need to enable it from Edit > Preference > General)  Chrome doesn't have this feature but you can install an addon called tabmemfree (Edited: and adblock would be a good idea for both FF and Chrome, though it works better in FF)

---

### Post by odiseo77 on 2012-12-15
> **sdowney717 said:**
> I know this board has a lot of memory slots

```
scott@scott-P5QC:~$ sudo lshw -C memory
[sudo] password for scott: 
  *-firmware              
       description: BIOS
       vendor: American Megatrends Inc.
       physical id: 0
       version: 0803
       date: 06/26/2008
       size: 64KiB
       capacity: 960KiB
       capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: 5
       slot: L1-Cache
       size: 64KiB
       capacity: 64KiB
       capabilities: internal write-back data
  *-cache:1
       description: L2 cache
       physical id: 6
       slot: L2-Cache
       size: 4MiB
       capacity: 4MiB
       capabilities: internal write-back unified
  *-memory
       description: System Memory
       physical id: 3a
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: DIMM [empty]
          product: ModulePartNumber00
          vendor: Manufacturer00
          physical id: 0
          serial: SerNum00
          slot: DIMM0
     *-bank:1
          description: DIMM DDR Synchronous 667 MHz (1.5 ns)
          product: ModulePartNumber01
          vendor: Manufacturer01
          physical id: 1
          serial: SerNum01
          slot: DIMM1
          size: 2GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
     *-bank:2
          description: DIMM [empty]
          product: ModulePartNumber02
          vendor: Manufacturer02
          physical id: 2
          serial: SerNum02
          slot: DIMM2
     *-bank:3
          description: DIMM DDR Synchronous 667 MHz (1.5 ns)
          product: ModulePartNumber03
          vendor: Manufacturer03
          physical id: 3
          serial: SerNum03
          slot: DIMM3
          size: 2GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
scott@scott-P5QC:~$ 

```

I'm not an expert, but shouldn't the first two memory slots be the ones occupied by the memory modules? You seem to have the modules in slot 1 and slot 3, and I think they should be in slot 0 and slot 1 (the first two slots). I don't think it's causing the issue you describe, anyway, but I guess it's better using the first two slots.

---

### Post by CharlesA on 2012-12-15
> **odiseo77 said:**
> I'm not an expert, but shouldn't the first two memory slots be the ones occupied by the memory modules? You seem to have the modules in slot 1 and slot 3, and I think they should be in slot 0 and slot 1 (the first two slots). I don't think it's causing the issue you describe, anyway, but I guess it's better using the first two slots.
Depends on the mobo.

---

### Post by odiseo77 on 2012-12-15
> **CharlesA said:**
> Depends on the mobo.

Thanks for clarifying. I thought it was advisable to use the slots in order, regardless of which mobo one uses.

---

### Post by CharlesA on 2012-12-15
It's best to go off what the manual says, but in this case, I believe the OP's mobo is the kind that can take DDR2/DDR3.

---

### Post by sdowney717 on 2012-12-15
I think it will take either ddr2 or ddr3 but not both at the same time.

I can not run very many Firefox tabs without a big slowdown, certainly not a hundred!
If I get over 15 on Firefox it becomes very unresponsive and slow to scroll pages.
I noticed right away Chrome works better with twice as many tabs open.

---

### Post by CharlesA on 2012-12-16
> **sdowney717 said:**
> I think it will take either ddr2 or ddr3 but not both at the same time.

That is correct. It is an either/or situation.

---

### Post by mips on 2012-12-16
[http://www.asus.com/Motherboards/Intel_Socket_775/P5QC/#specifications](http://www.asus.com/Motherboards/Intel_Socket_775/P5QC/#specifications)

> 2 x DIMM, Max. 8 GB, DDR3 1333/1066/800 Non-ECC,Un-buffered Memory
4 x DIMM, max. 16GB, DDR2 1066 / 800 / 667 MHz, Non-ECC, Un-buffered memory 
Dual channel memory architecture 
When installing total memory of 4GB capacity or more, Windows® 32-bit operation system may only recognize less than 3GB. Hence, a total installed memory of less than 3GB is recommended 
*DDR2 1066MHz DIMMs work only on the black slots for one DIMM per channel. Ensure to install the DDR2 1066MHz DIMMs ONLY on the BLACK slots! 

He will have to remove the 2x DDR2 modules in the black slots and populate them with higher capacity modules 2x 4GB or he would have to populate the 4 DDR3 yellow&orange slots with DDR3 ram.
Either way he would have to dump the 2 x2GB modules.

---

### Post by Paqman on 2012-12-16
> **sdowney717 said:**
> Have 27 tabs open.


I think we've found the problem.

If you really, really need to have that many tabs open, you're going to need a lot more memory. In the short term you could have a look at why you've got so many tabs open and consider switching to a different way of browsing. If you need to have quick access to sites you could use bookmarks instead of leaving a tab open, for example.

---

### Post by sdowney717 on 2012-12-16
Many links just open new tabs. Like using google news.
Anyway, I can fairly quickly open many tabs. And as long as the browser works, and I can see the tabs at the top bar, dont usually think about it or close then until it slows down.

I also sometimes like to think about things and go back to refresh pages where content changes. I do tend to use tab pages like bookmarks.

---

### Post by sdowney717 on 2012-12-16
> **mips said:**
> [http://www.asus.com/Motherboards/Intel_Socket_775/P5QC/#specifications](http://www.asus.com/Motherboards/Intel_Socket_775/P5QC/#specifications)
> 2 x DIMM, Max. 8 GB, DDR3 1333/1066/800 Non-ECC,Un-buffered Memory
4 x DIMM, max. 16GB, DDR2 1066 / 800 / 667 MHz, Non-ECC, Un-buffered memory 
Dual channel memory architecture 
When installing total memory of 4GB capacity or more, Windows® 32-bit operation system may only recognize less than 3GB. Hence, a total installed memory of less than 3GB is recommended 
*DDR2 1066MHz DIMMs work only on the black slots for one DIMM per channel. Ensure to install the DDR2 1066MHz DIMMs ONLY on the BLACK slots!


He will have to remove the 2x DDR2 modules in the black slots and populate them with higher capacity modules 2x 4GB or he would have to populate the 4 DDR3 yellow&orange slots with DDR3 ram.
Either way he would have to dump the 2 x2GB modules.

I saw that too. Dont you think that is only for 1066mhz ddr2 modules?
Meaning I have the 667mhz modules, so could still keep using them?

I was thinking get 2 more 2 gb modules ddr2 
Would a single 4gb ddr added in work?

---

### Post by Paqman on 2012-12-16
> **sdowney717 said:**
> Many links just open new tabs. Like using google news.
Anyway, I can fairly quickly open many tabs. And as long as the browser works, and I can see the tabs at the top bar, dont usually think about it or close then until it slows down.

I also sometimes like to think about things and go back to refresh pages where content changes. I do tend to use tab pages like bookmarks.

It seems to me that by adjusting your behaviour a little you could save yourself having to open your wallet, and have a more pleasant computing experience. Shut down tabs, and use your browser's history to get back to old tabs. Chrome opens the history as a tab, why not have that one permanently open, and use that whenever you want to go back to a page you've been on?

---

### Post by jerome1232 on 2012-12-16
> **sdowney717 said:**
> 
I was thinking get 2 more 2 gb modules ddr2 
Would a single 4gb ddr added in work?

You always want to install memory in matched pairs to take advantage of dual channel (or matched trio's if your board supports triple channel etc...)

---

### Post by mips on 2012-12-16
> **sdowney717 said:**
> I saw that too. Dont you think that is only for 1066mhz ddr2 modules?
Meaning **I have the 667mhz modules**, so could still keep using them?

I was thinking get 2 more 2 gb modules ddr2 
Would a single 4gb ddr added in work?

If you have 667Mhz modules they are probably DDR3 if that is indeed the case then you can get another 2 of the same type.

Best is to open the case and see which colour slots the ram is plugged into.

---

### Post by CharlesA on 2012-12-16
> **mips said:**
> If you have 667Mhz modules they are probably DDR3 if that is indeed the case then you can get another 2 of the same type.

Best is to open the case and see which colour slots the ram is plugged into.

Nah, they are probably DDR2. But yeah, the best way to find out is to actually take the cover off and look at the memory itself (or check the BIOS, as it should tell you what memory you have installed).

---

### Post by mips on 2012-12-16
> **CharlesA said:**
> Nah, they are probably DDR2. 

sudo lshw -C memory list 4 banks while the MB has 6, 4x ddr3 & 2x ddr2 so I suspect it's listing the 4x ddr3 ones while the 2x ddr2 ones are disabled.

---

### Post by sdowney717 on 2012-12-17
I pulled the memmory. I have 2 2gb modules in the black slots.
There are 4 more unpopulated slots, orange and yellow.

here is a pic of one of the modules with numbers.

---

### Post by jerome1232 on 2012-12-17
Based on a google search of that serial number, it's ddr2

[http://www.memory4less.com/m4l_itemdetail.aspx?itemid=1442233727](http://www.memory4less.com/m4l_itemdetail.aspx?itemid=1442233727)

---

### Post by CharlesA on 2012-12-17
PC2-6400 = DDR2 800MHz. ;)

---

### Post by sdowney717 on 2012-12-17
I upgraded the bios from ASUS. Changes included memory compatibility issues.
Looking at some forums,people were saying ddr3 had issues in this board.

So I dont know If I should bother getting 8gb DR3 and selling my 4gb DDR2. Or getting 2 more 2gb DDR2.

The manual though on this board says the black slots are only for DDR2 1066 speeds and if you use the other slots, it will slow to 800. So for speed reasons and keeping up with tech, perhaps good idea to buy 8gb DDR3. DDR3 offers much faster speeds.

I also think the board only supports 8gb DDR3, so should be put into the black slots.

---

### Post by sdowney717 on 2012-12-28
I put in the 8gb memory today. and it is much faster.
PC feels like its on boosters.

This works fine with a P5QC Asus board.

GeIL EVO Veloce Series 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800)
Sold for $28 and I had a 10$ off coupon so it was only $18. and it was new from Ebay.

These fit only on the 2 orange slots. The board has reached its max capability. This should last a few years then a new board.

---

