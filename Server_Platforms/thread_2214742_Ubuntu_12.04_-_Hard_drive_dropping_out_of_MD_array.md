---
title: "Ubuntu 12.04 - Hard drive dropping out of MD array on Intel S1200BTL motherboard"
date: 2014-04-02
forum: Server Platforms
---

### Post by Erk1209 on 2014-04-02
Good evening,

I have been wrestling with an issue with my file server that I would be very grateful for some advice about. First, my system:

Intel Xeon E3-1240V2
Intel Server motherboard S1200BTL
8GB Crucial ECC RAM
120GB SSD for Ubuntu 12.04 OS
10x 2TB Seagate Barracuda in MD software array level 6
2x LSI 9211-8i controllers flashed to IT mode
400W Seasonic Gold PSU

I am having issues with drives dropping out of my array. This board has an x16 slot, three x8 slots, and a regular PCI slot. I initially ran 8 hard drives with a Supermicro x4 controller in the top PCI x8 slot for about a year without any issues what so ever. I wanted to add two more drives, so I purchased a Supermicro x8 card which I installed in the topmost x8 slot, moving the x4 Supermicro card to the bottom x8 slot. When attempting to rebuild the array, I had issues with drives dropping out and making horrifying mechanical sounds and was never able to complete a rebuild. Eventually enough drives dropped out that the array failed all together. Even though drives were reported bad, they never tested bad with any program. I removed the x8 Supermicro card, replacing it with my original x4 Supermicro card in the topmost PCIe x8 slot and connected the two extra drives directly to the motherboard. This time the array assembled perfectly and ran smoothly.

Assuming my Supermicro x8 controller was bad, I swapped it for a LSI 9211-8i controller and placed that controller in the bottom most PCIe x8 slot. This also worked perfectly, assembling the MD array and running it without issues.

Encouraged, I purchased a second 9211 and installed it in the 3rd PCIe x8 slot on the board, moving my first 9211 to the topmost PCIe x8 slot. This did not work at all. Drives dropped out (almost always two at a time) or failed to be detected on the controller in the topmost x8 slot. I was never able to get a rebuild complete with this set up.

I was able to get a rebuild completed by moving the 9211 in the topmost x8 slot into the PCI x16 slot, leaving my second 9211 in the third PCIe x8 slot. Not only did this detect all drives and rebuild without a failure, it rebuilt at about twice the speed that the array had been building at with my previous set-ups; over 100000k/sec. I was thrilled, thinking I had figured out the issue. The array rebuilt overnight and ran stable all day.

I came home from work tonight with the intention to close up my tower and get back to normal. As I was standing the case up from lying on it's side (the machine was on) I heard a mechanical sound from a drive (not a click) and poof, two drives had dropped out connected to the 9211 in the third PCIe x8 slot. I was able to immediately re-add the missing drives and the array began rebuilding like normal at high speeds (127000k/sec). This continued uninterrupted for some time. I went back to close up the case and in the process brushed a power cable with the force that a butterfly lands on a flower. Immediately, I heard the mechanical sound and a drive connected to the 9211 in the third PCIe x8 slot dropped out, showing "removed" in mdadm --detail /dev/md0 as has become the norm. The array immediately began to rebuild with one of the "spares" I added back after tonight's initial problem when I stood the tower up and that has been running just fine for about two hours now.

However, I'm really uncomfortable with how volatile things are right now. I don't know if it's a coincidence that I touched a cable or stood the tower up and drives dropped out of the array, or if it really is that sensitive. I'm wondering if there's an issue with this motherboard just not being able to support the two x8 cards. 

The current set up is eight drives connected to a 9211 in the PCIe x16 slot with two connected to the 9211 in the third PCIe x8 slot.

Thank you for reading and please let me know if you have any ideas or if you need anything explained better. I could really use a hand as I'm at my wits end with this...

-Eric

---

### Post by lukeiamyourfather on 2014-04-04
It could be a number of things but most commonly drives in a RAID array are dropped because they are trying to read a bad sector on the disk and it eventually gets kicked from the array. Drives marketed as "RAID" drives will stop after 7 seconds (give or take depending on the drive) and tell the host the sector can't be read and to get the data from another disk in the array. Consumer drives will try forever to read a bad sector because there's an assumption there's no redundancy. Hardware RAID controllers typically kick out disks after 10 seconds of not responding. Normally Linux will try to reset the device after 30 seconds and it will try this a couple of times (negates need for "RAID" drives with Linux software RAID). However this doesn't always work if the hard drive doesn't respond to a reset request which is a known firmware bug in some hard drives. If the drives you have are not listening to the reset command then Linux will try to reset them every 30 seconds for 4 or 5 times (something like that, would need to double check) at which point if the drive never resets it kicks the drive out. I'm not saying that's 100% certain the cause but it would be a good thing to look into. See if Seagate has any firmware updates for that model disk. Also might be a good idea to get in touch with the support folks for the controller cards.

---

