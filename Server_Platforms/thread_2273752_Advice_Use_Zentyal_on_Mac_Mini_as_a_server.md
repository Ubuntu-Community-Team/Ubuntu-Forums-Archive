---
title: "Advice: Use Zentyal on Mac Mini as a server"
date: 2015-04-15
forum: Server Platforms
---

### Post by Matthew_Krell on 2015-04-15
Hello. We are looking at upgrading our school's server infrastructure. Right now we are running Zentyal 3.* on a regular PC and have never upgraded due to the fear of stuff breaking. What we are looking at is buying a Mac Mini and, using virtualbox, running the zentyal server on it. That way we can backup / clone / snapshot and be able to upgrade in good faith.

I was wondering if any Ubuntu super users are doing this or might have a better solution. Frankly I think this is pretty good but I'm curious to know what others are doing. 

Regards,   
Matt

---

### Post by nerdtron on 2015-04-15
How "loaded" is the current server? like how many users accessing it, services running on it, ram cpu usage.
If the mac mini can handle it I think it's ok.

---

### Post by TheFu on 2015-04-15
Which services do you plan to use? How many users? What other alternatives have you looked at?  As an admin, if I were afraid to patch weekly, then I wouldn't deploy the solution until I was confident that weekly patching would be possible, at least for internet facing services.

I wouldn't run any "server" under virtualbox. Use KVM or Xen instead.  The stability requirements for a server requires it. Plus the performance of KVM is better than all the other options - check the SPEC-virt numbers.

A macmini is awfully expensive for something like that and I'd be worried about the complete lack of redundancy. Will you get 2 and mirror them nightly?  What are the RPO and RTO requirements?

Or ... if you prefer more standard "server" hardware, that would mean ECC RAM, multiple NICs, SAS disks, and a RAID controller for better disk performance and redundancy.

Just saw a Dell Xeon-based T110 server for $279. [https://slickdeals.net/f/7797353-dell-poweredge-t110-ii-tower-server-xeon-e3-1220v2-quad-core-cpu-4gb-ddr3-500gb-7200rpm-hdd-279-with-free-shipping](https://slickdeals.net/f/7797353-dell-poweredge-t110-ii-tower-server-xeon-e3-1220v2-quad-core-cpu-4gb-ddr3-500gb-7200rpm-hdd-279-with-free-shipping) That is a low power Xeon CPU.

As for snapshots and backups ... LVM does snapshots and should be in every Linux Admin's toolkit of knowledge. 20 min of reading should bring you up-to speed.  

Versioned backups are the number 1 security tool for any system, especially on a hostile network like a school. If the backup takes more than a few minutes, it won't be done. Automate it to run nightly when nobody is there.  A mix of snapshots and versioned backups is smart.

Creating a clone is easy.  dd, ddrescue, fsarchive, clonezilla, partimage, can each do images.  I prefer rsync for disk-to-disk mirroring, assuming the open files can be quiesced. If not, then take whatever steps are necessary to get that data safely out into a static point and do a normal backup.  For backups, rdiff-backup is my tool of choice for a number of reasons.  Lots of other people prefer duplicity (and tools based on duplicity).

Upgrades for more disks will be an issue for the mini.  External disks connected over USB just aren't the same from a performance standpoint.  eSATA or SATA are necessary if you don't go with SAS.

Zentyal ... never used it, but looked at the architecture a few times over the years. Many of the services are high-risk and need to be run on their own hardware or at least inside their own HVM. I wouldn't run many of these services on the same OS instance - too dangerous, IMHO. But that is a decision you have to make.  Do they release patches in a timely way? An email server that doesn't get patched weekly is asking to be hacked, IMHO.

[http://www.macminiserver.com](http://www.macminiserver.com) - is a pro-Mini site that you might find interesting.

So - how many users and which services do you plan to run?

---

### Post by Matthew_Krell on 2015-04-15
The max active users we have at one time is probably less than 20, usually its like 4 or 5. as for services mostly just a lot of basic stuff. DNS, DHCP, NTP, a web server, some file sharing; that sort of thing. nothing that demands a lot of grinding. we've got 8000 total ram and on average I'd say we are using about 2000 of that (thats what the console tells me at any rate) I don't think we are using too much cpu, 2% on average. 

I did look at KVM and I did notice that it claimed better performance than the rest. I also liked how both Red Hat and Canonical were moving to it. It's still a good option in my mind. 

One of the motivations, however, behind using VirtualBox was that it was dead simple to use. We'd like to remove as much technical knowledge out of our infrastructure as possible so when we are going to train others they don't have to be acknowledgeable sys-admins to do it. The simpler it is to manage, the less brain power we have to throw at it and consequently save our energy for other stuff. That's the reason we chose Zentyal; it might be less stable (it's worked *great* for us), but then we didn't have to have a ton of expertise to manage it (we were doing it before). 

If you are suggesting KVM, perhaps you can help me. I've been using virt-manager as a GUI for KVM, but i've had some occational troubles. Virt-manager didn't have configuration for ubuntu 14.4 (which is what Zentyal 4.1 is) and sometimes the fonts would screw up or the VM would seem to freeze. It could be that the computer I'm testing it on isn't as beefy as it needs to be but on the other hand maybe I just need a better gui. You have any recommendations? I'm not as inclined to use Xen because I'd like to stay on the Ubuntu architecture and (like I said) Canotical a*nd* Red Hat are using it.

---

### Post by TheFu on 2015-04-15
> **Matthew_Krell said:**
> we've got 8000 total ram and on average I'd say we are using about 2000 of that. I don't think we are using too much cpu, maybe 2%. as for services mostly just a lot of basic stuff. DNS, DHCP, NTP, a web server, some file sharing; that sort of thing. nothing that demands a lot of grinding.

You need 3 VMs or (2 VMs and 1 physical box.)

Split off the web server. It is high-risk.

Split off the file sharing - you'll want to run an internal document indexer (like Recoll) and watch for viruses as files are placed into the storage.  You can setup an "internal search page" for the shared files for people on the internal network. They will thank you - it is like having google inside your LAN.

For the other items, I'd want a physical box for security reasons. Use pfSense on a $130 system or [http://www.astaro.com](http://www.astaro.com) or untangle or just run your own with a minimal Ubuntu. These are all very low CPU items. I'd lean towards pfSense - BSD has the best available network stack and it is very easy to use and backup.  After a backup, you can redeploy those settings on another pfsense box in about 2 min. The webgui is intuitive. pfSense is what many Universities use, so it is very capable for this purpose, scalable, and secure.

Hope this helps with the decision, even if you elect to do something else.  I'm not there. You'll have to be comfortable with the choices.

---

### Post by Matthew_Krell on 2015-04-15
Thanks a lot! We'll definitely look into all of that.

---

### Post by Matthew_Krell on 2015-04-18
> I wouldn't run any "server" under virtualbox. Use KVM or Xen instead. The stability requirements for a server requires it. Plus the performance of KVM is better than all the other options - check the SPEC-virt numbers.

Do you have any recommendations for a GUI for KVM? Virt-manager is probably fine but I had some problems with the fonts goofing up and the VM freezing. Could be because I didn't give it enough ram (only 500mb ;) ) . I know it would be good to learn virsh / libvirt but since I'm going for simplicity I'd like a nice GUI.

---

### Post by TheFu on 2015-04-18
A VM server with 500MB of RAM won't work.
4G is what I consider min for this, but I suppose you could squeeze into 2G (I have, once, for a test, using a chromebook).

virt-manager is just a GUI (like virsh) over libvirt. Both of those tools use libvirt, which is a library. There are other users of libvirt too.

500MB is an odd size for a VM - 512MB would be better, provided you don't run any GUI inside the VM.  Using virt-manager for anything other than setting up, starting and shutting down VMs is a mistake.  Use ssh for all other access. Don't use virt-manager as a GUI.

Font issues have nothing to do with virt-manager.

To manage servers, use ssh.

---

