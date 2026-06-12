---
title: "Setup Live Migration Cluster using Heron, Xen, DRBD, Heartbeat"
date: 2008-05-16
forum: Virtualisation
---

### Post by houms on 2008-05-16
Good Afternoon to all of my Ubuntu family. 
I would like to put together a howto on creating a high-availability xen setup in which live migration is possible between 2 nodes using Hardy Heron 8.04server edition... Basically I want to setup two physical PCs/servers(nodes), and have DRBD replicate the partition used for VM's, and have hearbeat perform a live migration of the vm's in case one of the nodes go down? If anyone is willing to assist me in this project, I would be most grateful. Anyone who has any suggestions or experience in this kind of setup please do respond with your ideas... 

I have started by following this howto from howtoforge.com, 
[http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories](http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories)
which is to install xen on Hardy Heron. 
I am not really sure how to proceed with drbd. While i have setup it up in etch, that was building drbd7 from source. Appearently drbd is intergrated into Hardy, but I believe it is version 8. If anyone can confirm this, or perhaps give some insight on how to proceed with the drbd setup... That would be greatly appreciated.

---

### Post by KiloLima on 2008-05-19
Hi,

i am planning the same setup. After some searching i found this:

[heartbeat2-xen-cluster-with-drbd8-and-ocfs2]("http://www.ubuntugeek.com/heartbeat2-xen-cluster-with-drbd8-and-ocfs2.html")

I will try this setup this week with Hardy and hope i will not come across major problems.

bye,
kilolima

---

### Post by houms on 2008-05-19
Thanks for your response. I ran across the same article.. So i have used the howtoforge article on installing xen on Hardy, up to the point right before you 
mkdir /home/xen
the above command is where I stopped. i did not do the above. i then started using the howto you referenced so i could get the replication and such setup so i can then create a vm just on the first node, which should replicate to node2. I have not completed but my disks are syncing as we speak..so at least  drbd is working.... Couple of notes on that ... 
in that tutorial where it says do

sudo dpkg-reconfigure o2cb 

I think this is deprecated because ubuntu will complain it is not installed... Instead I ran 
sudo dpkg-reconfiugre ocfs2-tools
and I just accepted the defaults values when prompted EXCEPT the 
start o2cb on boot, to which i said yes.. 

also where it says 
sudo apt-get install drbd8-utils [COLOR="Red"]drbd8-module-source drbd8-source[/COLOR]  build-essential linux-headers-xen 

the ones in red do not exist in the repositories.. From what I understand module-assistant is no longer necessary as drbd is intergrated into Hardy,
so the following command below should also be left out...
sudo sudo m-a a-i drbd8-module-source
sudo update-modules

So you only need to do 

sudo modprobe drbd and you should be good. I also suggest moving the 

default /etc/drbd.conf file with 

mv /etc/drbd/conf /etc/drbd/conf.orig
that way you have a blank conf file you can copy into

Finally, The first time you look at drbd status it will probably say ds:Inconsistent/Inconsistent and wont let you set your nodes to primary.
To fix this you have to run the following on one of your nodes:
sudo drbdadm -- --overwrite-data-of-peer primary all

I will keep you posted on any more progress I make. Look forward to hearing from you, and possibly working on this collaboration. I hope others will also join in.

Also, have you any thoughts on using JeOS for a xen host.. There is a lot of talk about using them as Xen guests, but I think it would be ideal for a linux/xen hypervisor... Anyway good luck.

---

### Post by danasp on 2008-07-25
Hi guys,

Have a look at my guide at [http://www.asplund.nu/xencluster/xen-cluster-howto.html](http://www.asplund.nu/xencluster/xen-cluster-howto.html)
Should be what you are looking for. :)
It is not finalized yet, planning to add some pictures and diagrams, but for the text it should all be there. Please provide comments if there is something not in order.

I recommend not using OCFS2. It is not needed for this type of setup and will only complicate things and most likely reduce performance. 

Cheers, Daniel

---

