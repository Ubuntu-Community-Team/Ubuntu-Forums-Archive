---
title: "HOWTO: Mount a folder/HDD on another computer in the network"
date: 2007-02-26
forum: Tutorials
---

### Post by Bossieman on 2007-02-26
I have 2 computers at home, both runing Ubuntu (6.10 & Herd 4). I have a 400Gb HDD mounted on the stationary computer with all my media. I also have a laptop (Aspire 1300) with a 20Gb harddrive. 
What I have done is that I have mounted the 400Gb harddrive in the root of the Laptop. 
[IMG]http://bp0.blogger.com/_JGCUC3b0VFQ/ReHt2VwYLCI/AAAAAAAAAJI/IutzYDdjU5o/s400/mount.png[/IMG]
This guide will show how to mount a folder/HDD on a computer in your homenetwork.

Start with the following on the computer that has the folder/HDD you want to share.
[B]
sudo apt-get install nfs-commons nfs-kernel-server[/B]

then

**sudo gedit /etc/exports**

you will see something like this

[IMG]http://bp3.blogger.com/_JGCUC3b0VFQ/ReHwNFwYLDI/AAAAAAAAAJQ/bpEvYXhsnA4/s1600/export.png[/IMG]

/400Gb is the path to the folder/HDD I want to share. 192.168.1.64 is the ip-number of the computer on my  network that will have the /400Gb folder mounted (My laptop).
If you want to allow the client computer to be root in the mounted folder you write rw,no_root_squash,async instead of rw,async

Save and exit gedit. 
Now do
[B]sudo /etc/init.d/portmap restart

sudo /etc/init.d/nfs-common restart

sudo /etc/init.d/nfs-kernel-server restart[/B]

Now we are done with the server computer. Now we configure the client computer (my laptop)

Start with creating a directory for the mounted folder/HDD and name it to what ever you want. In my realworld example I did
[B]
sudo mkdir /400Gb/[/B]

After that,  we do

**sudo gedit /etc/fstab**

Add the following to the document.

192.168.1.65:/400Gb /400Gb nfs _netdev,auto,user 0 0

192.168.1.65 is the IP-number for my stationary  computer. :/400Gb is the folder/HDD on my stationary computer that I want to mount. The last /400Gb is the folder on the client computer where the mounted folder/HDD will be located.

Save and exit gedit. Reboot your system and everything should work.

To find out your internal IP number just do
[B]
/sbin/ifconfig[/B]

[IMG]http://bp2.blogger.com/_JGCUC3b0VFQ/ReH541wYLEI/AAAAAAAAAJg/TReF9P_6sM4/s1600/ip.png[/IMG]

Hopefully it works out just as easy as it did for me.

---

### Post by cantator on 2007-03-10
I believe it is:

sudo apt-get install nfs-common nfs-kernel-server

There is no s on the common

Cheers :)

---

### Post by private_lock on 2009-02-21
Absolutely ingenious how easy this was :-)

Thank you very much!

private_lock

PS: There is no need to work your way through those lengthy "share your internet connection"-HowTos. Just plug a crossover cable in and assign two different IPs of the same subnet. E.g.:
```

on the first computer
sudo ifconfig eth0 192.168.5.1
on the second computer
sudo ifconfig eth0 192.168.5.2

```
where eth0 is your network device. Check with "ifconfig" without parameters.

---

### Post by msmoore on 2012-07-04
Is there an updated version of these instructions for 12.04 LTS 64 bit OS?

---

