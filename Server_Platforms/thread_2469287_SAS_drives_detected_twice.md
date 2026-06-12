---
title: "SAS drives detected twice"
date: 2021-11-24
forum: Server Platforms
---

### Post by clarknova on 2021-11-24
Ubuntu Server 20.04.3
Linux 5.4.0-89-generic
[Dell Poweredge R630]("https://www.dell.com/en-ca/work/shop/productdetailstxn/poweredge-r630")
[Atto H1280 GT SAS HBA]("https://www.atto.com/products/adapters/sas-sata/gt-12gb/ESAH-1280-GT0")
[Jetstor 824JXD storage shelf]("https://www.acnc.com/p/JetStor_824JX")
[22x Toshiba MG07SCA12TE 12TB SAS drives]("https://toshiba.semicon-storage.com/us/storage/product/data-center-enterprise/cloud-scale-capacity/articles/mg07scaxxx.html")

I set all of this up on a bench and connected the shelf to the head with a pair of mini-SAS SFF-8644 cables and Ubuntu detected the 22 SAS drives in the shelf as expected. I then shipped everything to a datacentre where remote hands racked and recabled it all. Now that I'm able to ssh into the system, I see that Ubuntu is detecting 44 SAS drives, as evidenced by fdisk and the contents of /dev/, /sys/block/, /sys/class/sas_*/, etc.

It appears that the SAS drives are being detected twice and I have no idea why it would be when it didn't on the bench. Given that the shelf has more than two SAS ports, I suppose this has something to do with how it has been cabled, although I don't have those details at the moment.

Is this something to do with multipath? Is it a good thing or a bad thing? I have some experience with drive shelves and HBAs, but I have no experience with multipath and this is something I've never seen before. Any help in identifying what's going on here and recommendations on configuring the hardware or software are appreciated.

---

### Post by MAFoElffen on 2021-11-26
Being it is a "Jetstor 824JX[COLOR=#ff0000]D[/COLOR]", it has two controllers and is identidied as both single or dual path... Dual path being mulitpath... and can be used in either mode. If cabled in both ports 1 in both controllers, then it is in mulitpath mode. 

Then:
> 
Linux Multipath command is used to manage storage SAN (storage area network) disks on OS side. ... Without DM Multipath, each path from a server node to a storage controller is treated by the system as a separate device, even when the I/O path connects the same server node to the same storage controller.

So then, if not configured right, or if it is not working, then it shows up as two devices/twice... I have seen where it initially shows up as one, then later shows as duplicated. That is an indicator that something is  wrong with mulipathd.. .

```

sudo systemctl status multipathd
multipath -v3 -d -ll

```
Will show the status of mulipathd and show the configuration of mulipath without trying to update the paths of...

---

### Post by clarknova on 2021-11-26
Thank you! You are right about the Jetstor having two controllers, which I did not realise before I shipped it out. With the multipath command I was able to confirm that the drives in the shelf are multipath enabled, and I've created my RAID using their multipath name. Output [linked here]("https://paste.ubuntu.com/p/HRvG4bwsBG/") for posterity.

---

