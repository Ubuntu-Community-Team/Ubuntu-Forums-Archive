---
title: "help in Diskless....plz"
date: 2012-01-07
forum: Server Platforms
---

### Post by Dream4Ever on 2012-01-07
Hello...
i need help at building Cybercafe "GAMING".

i have heard about the technique "Diskless".

from this link
[http://kualalumpurcity.olx.com.my/di...s-iid-66238262]("http://kualalumpurcity.olx.com.my/di...s-iid-66238262")

[http://www.styrex.com/images/DDSsolution.jpg]("http://www.styrex.com/images/DDSsolution.jpg")

Server under Linux OS
100x Client under MS Windows Xp\7 , 32bit\64bit

is diskless better than normal HDD ?
how to build it?
What is the Recommended Server Specifications?

---

### Post by elico on 2012-01-08
well it depends on the hardware you have.
what diskless is really local diskless client but it has hdd on the main  server and the whole network depends on the server and network  performance so 100x clients will be difficult to server for just a  normal and basic infrastructure.
i didnt found any reliable information on how to build such a system based on windows clients.

good luck

---

### Post by rsvancara on 2012-01-08
I run an HPC environment and we can boot over 100 stateless images off of one management server.  Now this is Linux, and our stateless images are around ~500 and live on RAM Disk.  

If you have the right type of environment, meaning a Network Interface card that supports PXE you can boot systems over the network.  There is also possibly ways you could do this maybe with GRUB, but I am not sure.  

Unfortunately, Micro$oft Windows does support these kinds of features.  In fact, we would really love to have this feature for high performance computing environments, lab environments and so on, but because windows builds a unique identifier and restricts how you deploy their systems using bastardized licensing schemes, "stateless" Windows will probably not ever happen.  

What you could do, if your games will run on wine, is configure a "stateless", nfsroot, or partial nfsroot setup.  Your "server" will provide a NFS share that will host your operating system images. For stateless and full nfs root images, you will have to have PXE support on your NIC(s).  There are commodity motherboards that support this feature but you will have to shop around.  Also server class motherboards support this feature as well, but you pay extra for anything that says it is a server motherboard.  You will also need a TFTP server, and a DHCP server that is configured to support PXE and serve out your images.  

I could see this working rather well as you could set up syslinux menu that the user could select which game they wanted to play and the correct Linux image is chosen based on the user selection.  You could even have different images for different sets of hardware and all that can be controlled via MAC address.  

To provide authentication, you could configure a simple LDAP server, and the users would authenticate against the LDAP server.  Time limits could be enforced from the main server and sending notifications to the client could be performed using remote ssh with trusted keys.  

Now here are your challenges you will need to overcome.  Games like World of Warcraft, suck up about 18GB of space.  You will need an instance (or installation profile) for every user session.  That means you will also be running the game over a gigabit network, which can sustain about 100 MB/s throughput.  Probably not a problem for a few clients, but for 20 players, you would see some performance problems.  What you will need on your server is a 10Gb/s uplink port and at least a 1Gb/s to the clients.  Furthermore, you will need a disk system that can sustain that kind of bandwidth.  Ideally something like 10K RPM mini SAS disks or a bank of SSD's

Another option is to look into distributed parallel filesystems like pvfs2, lustre or glusterfs.  10Gb may not be required as you could distribute your I/O potentially accross many storage nodes for increased bandwidth.  

My recommendations is to sit down and think through and define your set of requirements.  

I think you have a good idea, and these kinds of things are catching on especially with our younger generation playing more competitive games.  Now if game makers would just support Linux, this would be trivial to implement.  The other big challenge will be getting today's latest and greatest games to run under Wine.

---

### Post by rsvancara on 2012-01-08
Here is an update.  You can boot diskless windows environments using ISCSI.  I have read where can work, but I am unfamiliar with the details.  

Here is an article that seems to point to what you want to do for windows.

[http://www.thogan.com/site2/archives/10](http://www.thogan.com/site2/archives/10)

---

### Post by rsvancara on 2012-01-08
You need these kinds of Network Cards!

[http://argontechnology.com/PXE-Network-Adapters/Argon-Gigabit-PCI-Ethernet-Adapter-with-Managed-PC-Boot-Agent.html](http://argontechnology.com/PXE-Network-Adapters/Argon-Gigabit-PCI-Ethernet-Adapter-with-Managed-PC-Boot-Agent.html)

or something similar

---

### Post by Dream4Ever on 2012-12-18
Hey all and thanks for reply me.

after long time and many ways to try it i found a software for windows and i did try it and its works but with windows server,

its called CCBOOT

is there any software or any way like this program on Linux server.

and thank you all ^_^

---

