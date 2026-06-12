---
title: "Minimal Ubuntu Install Advise"
date: 2011-02-03
forum: Server Platforms
---

### Post by Tactical Fart on 2011-02-03
I have a decade+ old computer collecting dust in the corner of my room. The specs (off the top of my head) are that it has 192 MB of RAM, 10 GB HDD, and a 533 MHz CPU. 
I'm extremely reluctant to throw it in the trash, so I want to repurpose it. My plan is to get a 2TB hard drive (maybe two, along with the proper controller cards because I'm certain it does not support SATA) and turn it into a personal file server. I want to run mediatomb, samba(maybe), proftpd, and maybe x forwarding as a crutch for anything I can't handle in the CLI. I also do not plan to use it as a performance machine. The most CPU intensive thing I may do might be to rip a CD or to run a deamon controller I have. I plan to have the system headless so it will be controlled mostly through the command line (ssh) and the absence of a GUI should improve performance.
Should I use the minimal installer or should I go with another distro? I know I meet the requirements for the server edition, but "should" I go this route? FreeNAS looks tasty but I like the CLI. It may be harder to configure, but that will make it more fun, right?

---

### Post by volkswagner on 2011-02-03
With 192MB RAM, I suggest using the Server install.  From reading your post, I don't think you will need a GUI.  I think you will surprise yourself how far you'll get with just a CLI.  If down the road you want to add X stuff you can.  Either way you way, I don't think the limited RAM will offer much joy in forwarding X sessions anyway.

You could also add web based management such as Webmin.

Be careful with 2TB drives.  You may be limiting your selection of SATA interface cards.  I would stick with 1TB drive if you can, and get an inexpensive 4port SATA card.  Just my opinion, but from feedback on 2TB drives failure rate is too high for my liking.

---

### Post by Vegan on 2011-02-03
I have noted a lot of problems with WD, not as many with Seagate.

---

### Post by Tactical Fart on 2011-02-03
@Volkswagner
When I use x forwarding now, I use it on single programs. If I use it on this machine for something like nautilus, will it matter or is x forwarding too intensive, period?

---

### Post by kevinthecomputerguy on 2011-02-03
I would take his suggestion of webmin, and not x or forwarding x
 
one thing to remember with webmin is your https uploads are loaded into ram first, then the disk.
 
So use webmin to administer it, then use ftp, ssh, and or samba to the upload files. http \ https are normally download in nature, so when your using web based apps with under 100mb of ram, dont upload large files via that interface.
 
But webmin for administering it is an awesome sugestion!

---

### Post by doogy2004 on 2011-02-03
Here is what I have:
330Mhz P2
512 MB ram
10 Gb HDD
3x320 Gb HDD in mdadm software raid.

Here is what I use it for:
Samba (windows file sharing)
NFS (unix file sharing) (i use this for my VMware ESXi servers datastores)
SSH/SFTP
NoMachine NX (terminal server)
Transmission (bittorent downloading)
SABnzbd (usenet client)
VMware Server (i used to run VMs on this machine till I got the ESXi server)
Webmin
and other stuff i can't think about right now

My recommendation is to give it a try, but you may want to upgrade the ram to the max if you can.  If you can't, run a swap file/partition on a USB drive to increase performance (assuming you have USB 2.0).

---

### Post by Tactical Fart on 2011-02-08
I managed to get it running. Thanks for the help everyone!

Also any suggestions on a good controller? My only option is to use PCI cards.

edit: Also the cpu is 633 MHz, not 533. My bad.

---

