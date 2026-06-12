---
title: "mdadm or zfs - should I migrate before my system gets to big and complex?"
date: 2017-06-04
forum: Server Platforms
---

### Post by jason63 on 2017-06-04
Hey guys, I won't dispense with pleasantries, I lurk around and read as much as I can, but lets get down to business!

Ubuntu Server 16.04.1
-headless (has monitor currently hooked up for trouble shooting but will be stuffed into a closet when finished)
-intel i5-4570
-16gb ram
-120 GB ssd boot 
-3ware 9690SA 8-port Sata2 SAS->SATA Expander/Raid (I use this simply to add more drives as pass them to the os-not for hwraid)
-5 x 4TB WDRED (currently in mdadm raid 5-running off motherboard sata)
-3 x 3TB WDGREEN (jbod-running off 3ware raid card-just as pass through - not using the built in raid functionality)
-1 x 3TB WDPURPLE (single disk being fed network security cameras)
-GbE - I'm already saturating the network while copying data.
-UPS and Volrage regulator

Software
-webmin
-mdadm
-samba
-ssh
-bluecherry dvr (security camera server)
-plex media server (serving all my content to chomecasts, roku stick and an Nvidia Shield)

Use
-The WD Reds are used for backup from computers in the house, they almost never get read - only dumped to.
-The WD Greens just store music and movies and tv shows for plex to organize and serve
-The WD Purple is a surveillance drive, it just takes the live streams from the BlueCherry DVR and stores them.

This is a personal system with no mission critical data. 

Eventual configuration will be the entire system populated with WDREDS and/or Seagate IronWolf drives in 2 arrays (obviously different brands/models not on same array). One array for backup (doesn't get used much on the day to day) and one array for Media that gets used daily. My thought is that I don't want one big array storing stuff I can't afford to lose while also being used to view content I access on a daily basis but in all likelihood CAN afford to lose.

As money allows, arrays will be converted to R6 or R10. Rebuild time isn't THAT important.
Generally read speed is slightly more important that write, as my daily use I'm reading 90% of the time.


I'm fairly happy with this setup, and I REALLY like the webmin interface, especially the MDADM raid portion for managing my drives. This being said, I'm scared of bitrot and all those other scary things that raid5/6 doesn't protect you from.



_**So the question is, before this system gets CRAZY (it sort of already is) do I make the switch to ZFS???**_

Data on the server ***IS*** stored in at least one other place (depending on content, up to 2 other places) Its just a physically separate system networked into my setup that I can dump to.

Thoughts? Keeping in mind, I very much appreciate the imbedded nature of MDADM management in Webmin. I'll give it up if I have to.



Edit: Im the 4 hours since posting this, Ive created a VM with Ubuntu Server 16.04.2 and all my trimmings, webmin, samba, plex, mdadm, bluecherry and ZFS with webmin plugin.

Ive created 2 sets of virtual drives, one to is a 4 disk  raid5, the other is a 4 disk raidz pool. No custom configuration, no tweaking, just all default settings. I did samba share for each array, and did a basic network crystaldiskmark bench test. The specifics of the test are not whats important, the fact that its an identical test on both drives is.

It seems than the ZFS lacking in performance compared to the standard raid5 mdadm array Im currently using. 

Raid5 on the left, ZFS on the right. Both arrays are in a VM and both on the same SSD hosting the VM.

Thoughts?

---

### Post by howefield on 2017-06-04
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by jason63 on 2017-06-04
I figured server platforms would be more accurate, but I might get more responses in General. But thanks!

---

