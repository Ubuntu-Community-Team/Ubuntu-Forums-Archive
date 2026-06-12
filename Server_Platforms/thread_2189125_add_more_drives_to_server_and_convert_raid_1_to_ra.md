---
title: "add more drives to server and convert raid 1 to raid 5 (new to servers)"
date: 2013-11-20
forum: Server Platforms
---

### Post by darksidedude on 2013-11-20
Hello everyone. I recently acquired a Dell poweredge 2950 (dual quad core xeon processors and 16GB of ram) beside the fact that it is super loud. it does a fantastic job of being my VM + Plex media server + seedbox +DNS/DHCP +squid

it came with 2 1TB hard drives in a raid 1 configuration with perc 5/i I installed ubuntu server 13.10 in a LVM on the virtual disk created by the RAID controller. with my expanding media needs I acquired 4 more 1TB drives. this server does 6 hot swap drive bays (if that effects it in any way?) 

my goal is to have as limited downtime as possible (preferably none) while adding the extra drives.

should I leave the original 2 drives in raid 1 with the os and Vm's on it and add the extra 4 drives into a separate array? afterwards migrate the media files?
or is it possible to add the extra drives and convert my current raid 1 to a raid 5 or 6 without losing the data or OS. 

forgive me if my question is vague and broad I have some Linux experience but not much with servers/raid/lvm

---

### Post by SeijiSensei on 2013-11-21
If you want to continue to use the PERC card, then you'd need to reconfigure the array with the [built-in BIOS utility]("https://cs.uwaterloo.ca/~brecht/servers/docs/PowerEdge-2600/en/Perc4scdc/UG/bios.htm").  That's probably the best long-run choice since you'll still have an array that looks like a single device at the operating system level.

Another option is to use a smallish drive like a 40-160GB device as the location for the primary filesystem tree, then mount the array to a location like /home or /media.  I prefer this approach since it isolates the data drives from the operating system image.  Plus if you mount the array to /home, you can use multiple boot images on the single drive that all share the same set of files.  I often keep a spare partition on the boot drive so I can test out new releases.

---

