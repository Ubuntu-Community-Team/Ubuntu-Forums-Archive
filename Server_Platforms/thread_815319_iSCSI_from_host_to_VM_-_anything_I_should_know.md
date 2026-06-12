---
title: "iSCSI from host to VM - anything I should know?"
date: 2008-06-01
forum: Server Platforms
---

### Post by robgolding63 on 2008-06-01
I am considering a slight overhaul of my network, which at present has a VMware host server with 3 VMs, and an IPCop firewall, although the firewall is irrelevant to this post.

The host is running Windows Server 2003 has 2.5GB RAM, and is a DC, DNS, File Server, and WSUS Server for the network, it runs 3 VMs – an Exchange Server, a Cacti Server and a Web Server. It has 5 hard drives – 2x 500GB SATA in RAID1 with a hardware RAID controller (PCI), and 3 x 80GB IDE drives, 2 in “fake” RAID1 (PCI again), and one directly attached to the motherboard.

The 500 GB array is split 470GB/30GB – for file server data, and exchange mailbox data – although seeing as the Exchange server is a VM, the mailboxes are on a VMDK which sits in the 30GB partition of the large RAID array.

The 80GB RAID1 is split 40GB/40GB, for Host O/S and VM O/Ss. Finally, the 80GB single disk is used for swap files, with 3 VMDKs – one for each VM.

The host has 2 NICs – a Gigabit Netgear and a 100Mb crappy one – the gigabit for the host, exchange, and cacti servers, and the 100mb for the web server, as it is in the DMZ so needs its own card.
When copying files to and from the file server, I am not getting the speeds I would hope for on a gigabit network (about 18MB/sec max). I believe this is because I am maxing out the PCI bus – with 2 RAID controllers and 2 NICs. The data has to be transferred over the network using the NIC, and onto the hard drives using the PCI RAID controller – so effectively halving the available bandwidth on the PCI bus. I can’t really rectify this without buying a new server – as this one does not support PCI-E.

My main question, however, is to do with changing the host O/S to Ubuntu, using software RAID (mdadm), and installing iscsi-target in order to access the host’s drives from the Windows guests. Does anyone have experience with this, or happen to know of any pitfalls or horror stories? The main reason for doing this is to get rid of the crappy PCI fake-RAID controller, and attach all 3 IDE hard drives directly to the motherboard, and use mdadm to the same effect (one RAID1 and one single disk), hopefully freeing up some bandwidth on the PCI bus, while also gaining the flexibility of Linux software RAID. I would then run the DC/File Server as a VM, using ISCSI to target the 500GB mdadm array on the host, to share the same file server data – and install cacti on the Ubuntu host to get rid of one of the VMs – so I’d be left with 3 VMs as before.

If this plan worked, then I would effectively have a mini-SAN inside the Virtual Host, which is a very fast network as I understand it (as fast as the memory on the host), so latency shouldn’t be a problem – honestly I wouldn’t be disappointed if the speeds stayed exactly the same – as long as they don’t go down, as I’d like to have the flexibility of mdadm.

If anyone recommends against this then I’d like to hear why – at the moment it’s just an idea and I’ll be doing some testing first, but it would be a learning experience as well to get this running. Also helpful would be any info on VMware Server for Ubuntu, RAM usage, and whether I should install Gnome or not - for maximum available RAM.

Thanks a lot,

Rob

---

### Post by gtdaqua on 2008-06-02
I have used a similar one. The base is 64-bit Ubuntu and I installed Openfiler on a VM. Now, on a linux VM, in order to get Gigabit speed you need to install a 64-bit Linux VM. Only then VMNET modules at work at a gigabit speed (at least on my scenario). 

On Windows, you would definitely need vmware tools to achieve greater network performance. 

Software raid is not as effective as hardware raid. The hardware ones specifically designed sustain harder inputs. Software ones still have to work with shared resources with the OS. 

If your harware RAID is good, then there is no need to create an iSCSI-target and software raid - unnecessary complications. You can simply create a fresh VMDK files and assign them to the WinOS instead of using iscsi-targets. This way, you are maxing on the PCI than on the NIC. 

As far as linux servers are concerned, never install GUI. Why do you need them? There are no special ways to administer (not something that is incredibly necessary) a server via GUI. Learn CLI. If you install GUI, you will still have to open Terminal or Konsole  type the commands! 

VMWare server is by far the best in the industry now. You can confidently deploy them on Production servers. You may have to do a little tweaking to get a fantastic performance on your VMs. But Windows is Windows. It will suck the memory and speed. But we got to live with it and do the best we can.

Some nice tips on virtualization are [here]("http://ubuntuforums.org/showthread.php?t=646613").

---

### Post by windependence on 2008-06-02
I agree with gtdaqua, I would not use software RAID. 3Ware makes some great RAID controllers for SATA drives if you are using them, and if you are using SCSI, then there are a number of good controllers out there, some of which can be purchased on eBay for as little as $60 new.

You should notice a large difference running on Linux vs. Windows hosts.

-Tim

---

