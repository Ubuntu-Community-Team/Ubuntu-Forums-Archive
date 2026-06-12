---
title: "Nfs security"
date: 2011-10-24
forum: Security
---

### Post by linuxyogi on 2011-10-24
Hi,

Today I purchased a network switch & connected 2 of my PCs. An DSL router is also connected to the switch.

I want to make one of the PCs a NFS server but since eth0 is the external interface I am worried about security.

I have used NFS before but ppp0 was my external interface back then.

Now that eth0 is dealing with all the work, do I need to open a port ?  I am worried about security.

Please tell me how to go about this.

---

### Post by Dangertux on 2011-10-24
> **linuxyogi said:**
> Hi,

Today I purchased a network switch & connected 2 of my PCs. An DSL router is also connected to the switch.

I want to make one of the PCs a NFS server but since eth0 is the external interface I am worried about security.

I have used NFS before but ppp0 was my external interface back then.

Now that eth0 is dealing with all the work, do I need to open a port ?  I am worried about security.

Please tell me how to go about this.

Do you want to be able to share files over the Internet or only the local network? 

If you want the files to be accessible from a remote location, you would need to allow access from the router to the machine in question (via port forwarding). However if this is the case I recommend using something like SSH not NFS

Hope this helps.

---

### Post by linuxyogi on 2011-10-24
> **Dangertux said:**
> Do you want to be able to share files over the Internet or only the local network? 

If you want the files to be accessible from a remote location, you would need to allow access from the router to the machine in question (via port forwarding). However if this is the case I recommend using something like SSH not NFS

Hope this helps.

I want to share the files  over the local network only. I did a port scan at GRC.com which showed some ports as closed & some as stealth.

So, opening the NFS port for purpose is safe right ?

---

### Post by Dangertux on 2011-10-24
> **linuxyogi said:**
> I want to share the files  over the local network only. I did a port scan at GRC.com which showed some ports as closed & some as stealth.

So, opening the NFS port for purpose is safe right ?

Since you're only sharing over the local network, you don't have to forward the port from the router. Which would be "opening" the port to the outside world. Since the port scan you did does not show any listening services, (assuming it scans NFS), you're good.

That being said, the difference between 'stealth' and closed ports is, well negligible... It's a silly catch phrase that I hate that was ever coined.

---

### Post by drdos2006 on 2011-10-24
No, you do not need to open a port on your server.
If you are running Ubuntu server, then it is easier to have the server use a fixed IP address, e.g. 192.168.0.111. This is performed from the server by editing /etc/network/interfaces with vi. 
Command is :
sudo vi /etc/network/interfaces

Comment out the "iface eth0 inet dhcp" and press INSERT key, 
type :
iface eth0 inet static
	address 192.168.0.111
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
Now press ESC key,  the colon key ( : ), and w ( to write ) and q ( to quit ).
The gateway address is the IP of your router.
Reboot your server and make sure you can ping to the server IP address from another machine on your LAN.
Once that is correct install "nfs-kernel-server  nfs-common" on your server with "sudo apt-get install nfs-kernel-server  nfs-common".
On your second client machine, install "nfs-common".

The server now needs to know which directory/files to share. This is done by editing the "/etc/exports" file.
Use vi to edit, add the directory/files, nominate the IP network address that can connect to server in this manner.
/media/sda3-shared	    192.168.0.0/24(rw,sync,fsid=0,crossmnt,no_subtree_check)
/media/sdb1-shared	    192.168.0.0/24(rw,sync,fsid=1,crossmnt,no_subtree_check)
/media/sdc1-shared	    192.168.0.0/24(rw,sync,fsid=2,crossmnt,no_subtree_check)
/media/sdd1-shared	    192.168.0.0/24(rw,sync,fsid=3,crossmnt,no_subtree_check)
/var/www	    192.168.0.0/24(rw,sync,fsid=4,crossmnt,no_subtree_check)

Reboot the server. Mount the server directories from your second machine from the terminal by :
sudo mkdir /media/server-share-sda3
sudo mkdir /media/server-share-sdb1
sudo mkdir /media/server-share-sdc1
sudo mkdir /media/server-share-sdd1
sudo mkdir /media/server-share-www
then
sudo mount 192.168.0.111:/media/sda3-shared   /media/server-share-sda3
sudo mount 192.168.0.111:/media/sdb1-shared   /media/server-share-sdb1
sudo mount 192.168.0.111:/media/sdc1-shared   /media/server-share-sdc1
sudo mount 192.168.0.111:/media/sdd1-shared   /media/server-share-sdd1
sudo mount 192.168.0.111:/media//var/www      /media/server-share-www

Then you can access the server files on your desktop.
There may be 1 or 2 steps I have missed but these can be sorted out.

regards

---

### Post by linuxyogi on 2011-10-25
Thanks to both for your replies.

When I try to mount the nfs share I get this 


```
$ sudo mount 192.168.1.3:/home/tux/nfs /home/tux/nfs/
mount.nfs: mount to NFS server '192.168.1.3:/home/tux/nfs' failed: RPC Error: Program not registered

```


Usernames of both the PCs is tux.

I have set ip addresses of bot the PCs manually.

---

### Post by linuxyogi on 2011-10-25
Any ideas ???

I have tried restating the nfs-kernel-server but same thing.

---

### Post by linuxyogi on 2011-10-25
I am totally stuck.

---

### Post by bootedguy on 2011-10-25
Just some thoughts.

You should be running NFS server on the source PC, and NFS client on the client PC.  If you installed the recommended Ubuntu packages, you will install both server and client on both PCs, which is fine.

Did you create a folder named NFS on the client PC as well as the server PC? I am assuming you are using the folders named NFS specifically for sharing.  There is nothing wrong with that, but it is not necessary.  Just about any folder on a server PC can be mounted on a client PC, as long as the folder name has been created on the client PC before mounting.

BTW, I have found NFS works much better than Samba, and is worth the extra effort.

John

---

### Post by linuxyogi on 2011-10-25
> **bootedguy said:**
> Just some thoughts.

You should be running NFS server on the source PC, and NFS client on the client PC.  If you installed the recommended Ubuntu packages, you will install both server and client on both PCs, which is fine.

Did you create a folder named NFS on the client PC as well as the server PC? I am assuming you are using the folders named NFS specifically for sharing.  There is nothing wrong with that, but it is not necessary.  Just about any folder on a server PC can be mounted on a client PC, as long as the folder name has been created on the client PC before mounting.

BTW, I have found NFS works much better than Samba, and is worth the extra effort.

John

I have successfully setup NFS multiple occasions. Problems of these kind usually went away restarting the service. I dunno what happened this time.

I have left NFS & started suing a app called [Giver.]("http://tombuntu.com/index.php/2008/12/19/simple-desktop-file-sharing-with-giver/")

Thanks for a all the help.

---

