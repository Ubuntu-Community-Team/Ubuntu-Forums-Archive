---
title: "Faster and easier way to copy data"
date: 2016-07-30
forum: Windows
---

### Post by tech291083 on 2016-07-30
Hi Friends,

I often copy a lot of data (using a 32 GB USB 3.0 pen drive) from my laptop running windows 7 (with 1 USB 3.0 port) to a PC (only USB 2.0 ports) of mine with 3 hard drives, the 1st one running windows 7, 2nd one running Ubuntu 16.4 Desktop 32 bit and the 3rd running Fedora 23 Workstation 32 bit.

Each of the above 3 OSes is fully updated. Windows 7 is running a reputed Internet Security product, which is fully updated. 

My laptop has one USB 3.0 port, while my PC has none. Pen drive is working fine, no virus isses as such to my knowledge. But it take a lot of time to copy data from laptop to PC and vice versa. Although, copy and paste is always much slower than cut and paste. I only use pen drive to copy data, often spending a lot of time doing so. 

Is there a faster and easier way to copy data in my situation?

Thanks.

---

### Post by oldfred on 2016-07-31
Are both PCs networked?
I used to use Samba to copy data from my Ubuntu desktop to XP laptop. But I was reinstalling Ubuntu every 6 months & any XP update to system, firewall, or virus seemed to make me redo Samba. 
I got so frustrated I just installed Ubuntu to laptop to move data and then stopped using XP on laptop.

I now use NFS as I can script the install part with a new install and then just use rsync to copy data.

Some others suggested I just use SSH as it may be a bit easier to set up. But with my scripts NFS is automatic as part of every new install.

---

### Post by sudodus on 2016-07-31
+1 for the ssh method. 

I have installed **openssh-server**

```
sudo apt-get install openssh-server
```

I use ***sftp*** and ***rsync*** (the simple command line programs) via the network (from linux to linux). In Windows I have used both ***WinSCP*** and ***Filezilla*** to transfer files to and from my linux computer (with openssh-server installed). It is faster than USB 2 and more convenient than to mess with a pendrive, that you have to both write to and read from.

---

### Post by JayKay3OOO on 2016-08-01
I would buy a nas box or build your own. (Network attached storage)

You can plug it into a gigabit ethernet switch or router and then get to the data from any pc or distro.

I have this so I can listen to my music from my pc, phone or laptop without ever having to copy the songs to the different devices while in the house. The nas box can be seen by windows, mac, linux and android so it doesn't matter what machine I pick up, I can listen.

Transferring large amounts of data over wifi is fairly slow so try and set it up so you have a gigabit wired link. Streaming over wifi is OK, but moving several gigabytes is a lot faster on a gigabit link.

I think you wanted a different command to copy, but to me a nas has been the best way to move files between computers. It's certainly been worth the cost. It also means if I delete stuff it's being deleted from one place with no duplicates and set up as raid 1 it will mirror your data so should be ok if one drive fails.

---

### Post by tech291083 on 2016-08-03
> **JayKay3OOO said:**
> I would buy a nas box .
You can plug it into a gigabit ethernet switch or router and then get to the data from any pc or distro.


Never heard of it, but looks interesting, but need to consider cost as well, thanks.

---

### Post by JayKay3OOO on 2016-08-04
Hi.

I've tried to be thorough in my reply. This should cover any questions you have regarding a network attached storage device. I hope I'm not being too technical.

Cost is an issue. 

I got mine 3 years ago when I was on social security. At the time it was a massive spend. (thankfully those days are distant memory)

 A two bay nas, and 2 1TB WD red 'supposed to be better for nas boxes' cost me around $220, that could be dropped to $182 with 2 wd blue 1tb drives.

However, you could just get the nas box -D-Link share center (still seems to be one of the cheapest) 2 bay and 1 1tb hard drive $126 (500GBs seem to be nearly as cheap as 1tb at the moment).

I used to copy data to external drives and then plug them in. I found the bays would break down and be fragile and I could not copy stuff all at once. USB drives would get lost, or found in the washing machine needing careful drying and praying to the data gods to give me my preciouse files back. With the NAS I can go to any network capable device and get data. You can even stream stuff to your modern TV if it can read the files. A mobile phone connected to good speakers streaming your music from your nas can fill a room with gloriouse sounds while you coppy your latest youtube masterpiece to your nas, from your laptop to then download it to your decent pc for editing. 

Speeds

Ethernet / wireless

2016 built i5 desktop with samsung evo SSD - Max of 42MB/sec copying a 2.5GB file from desktop to the nas via 1GB ethernet switch (wired) (2 minutes)
Same PC - Max of 68MB/sec copying a 2.5GB file from the NAS to the SSD via 1GB ethernet switch (wired) (1 minute)

2006 mac book pro copies the same file from the nas at a max of 54mb/sec (to a mechanical hard drive - 6 month old hdd)  (wired) (2 minutes)

low spec windows 10 laptop copies the same files at a max of 4mb/sec from nas to a mechanical hard drive (wireless) (6 minutes)
low spec windows 10 laptop copies the same files at a max of 72mb/sec from nas to a mechanical hard drive (wired) (1 minute)

(times were rough guesses put in later) 

Of course, 1gigabit ethernet works out to (googles) 125mb/sec theoretical so we're down around 40% on what is theoretically possible in this test. 72mb copy is still OK.
Note, that lots of smaller files, just like using the USB may be slower individually.

Flash Drive 

2006 mac book pro USB 2.0, 2GB flash drive copying a smaller 1.6GB file from the mac book pro to the flash drive at 2.5MB/sec (that's 8 minutes)

New VS old

PC speed is semi important, of course, an old hard drive will kill copying from performance more than a slow cpu, the mac had a new hard drive over last winter and some extra RAM, but it's still a bit slower than the newer cheapo (falling apart) laptop.

2006mbp vs 2014 $250 laptop

2006 mac Core 2 duo 2.16Ghz, 3GB DDR2 ram

2014 laptop Core 2 dueo 2.16, 4GB DDR3 ram

Overview.

In the end I would never go back to using flash drives, I sometimes have to use them in work for pcs that hate their network cards, but for the most part I copy stuff to and from the network as I would my nas. You could call a nas a file server as it gives you a web interface to control it. In extreeeme cases I run virtual machines from the nas. It's certainly faster than trying to run an OS installed to a flash drive (tried ubuntu once and never again, puppy is an exception)

Internet, no, you don't need the internet. Connect the nas to the external switch or router (why not the router, because in my case the routers switch is only 100mb and that is so slow and I had this gigabit switch lying around). Connect the router to the external switch then connect your wired devices to the external switch. Turn it all on and the router will hand out IPs even if you don't have internet connected. It's pretty idiot proof. You can exclude a router if you don't need internet or the way your setup works, but this might be a bit fiddly. A router does all the IP fluff for you. Wireless devices will be handed out IPs as usual and you'll be able to connect to the nas exactly the same. Ofcourse, you may only be able to stream one thing without interruption using the wireless device. I.e, I can't copy music to my phone for playing in the car and play music from the nas using the same phone. I can, but the song may buffer.

I could probably solve this wireless speed issue by buying a faster router with a faster wireless part.

Anyway. I hope this helps. I don't work for D-Link or WD. I just remember seeing a friend using the mac equivalent as he used a phone to play music from the mac nas to his (presumably) bluetooth speakers and then I decided I had to have the poor version!

---

### Post by tech291083 on 2016-08-05
JayKay3000,

Thanks a lot for the detailed reply, appreciated, but I will have to think about it. Thanks a lot for the help.

---

### Post by tech291083 on 2016-08-05
Hi Oldfred,

I just watched a YouTube video showing 2 Windows 7 PCs being connected via LAN cable for sharing data. But it also requires assigning IP addresses to both the PCs and enabling sharing options, but this looks much easier than methods (SSH and NFS) you have suggested, may be its my lack of knowledge that is making me think like that. Sorry about that.

While your methods make sense, but I have yet to do any serious scripting on my own. But if you can send me links to sites that teach your methods, simple enough that I can understand, then I will definitely give them a go.

Thanks a lot.

---

### Post by tech291083 on 2016-08-05
> **sudodus said:**
> 

I have installed **openssh-server**

```
sudo apt-get install openssh-server
```

I use ***sftp*** and ***rsync*** (the simple command line programs) via the network (from linux to linux). In Windows I have used both ***WinSCP*** and ***Filezilla*** to transfer files to and from my linux computer (with openssh-server installed). It is faster than USB 2 and more convenient than to mess with a pendrive, that you have to both write to and read from.

OK.

So, what I understand is as follows

To transfer data between Windows and Linux PCs, I need WinSCP and FileZilla, right?

And to transfer data between 2 Linux PCs, I need sftp and rsync, right?

I have a router at home, but do I need internet to use (WinSCP and FileZilla) and/or (sftp and rsync)?

Thanks a lot.

---

### Post by oldfred on 2016-08-05
HOWTO: NFS Server/Client if no windows 
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889) 
   [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I install both server & client software to both laptop & desktop so I can copy data both ways. I modify exports with the mount point(s) I have in remote computer to be able to link to them. I then create local mount to remote mount, then use rsync to copy data. I have /mnt/data in both system and want to sync all folders in that mount between systems.

I have had several routers over time, some 168.... and others 10.... and I have mounted both a data partition that was ext4 and a shared NTFS partition in the past. The mount must be something you have already mounted in remote computer.

 sudo nano /etc/exports
/mnt/data   192.168.1.0/24(rw,no_root_squash,async)
/mnt/shared 192.168.1.0/24(rw,no_root_squash,async)
or
/mnt/data   10.0.0.0/24(rw,no_root_squash,async)
/mnt/shared 10.0.0.0/24(rw,no_root_squash,async) 

 # For NFS /etc/exports already edited 
sudo apt-get install nfs-kernel-server nfs-common rpcbind
sudo dpkg-reconfigure rpcbind
sudo exportfs -a 

Then on local computer must create mount point for remote mount. I used data_LT as data partition on LapTop.  So I am mounting my /mnt/data partition on remoter laptop to /mnt/data_LT. 
      
 sudo mkdir /mnt/data_LT
sudo mkdir /mnt/shared_LT
sudo mount 192.168.1.100:/mnt/data /mnt/data_LT
sudo mount 192.168.1.100:/mnt/shared /mnt/shared_LT 
        
I then rsync data from  remote /mnt/data_LT to local desktops /mnt/data.
sudo rsync -aruvP /mnt/data_LT/Documents /mnt/data
sudo rsync -aruvP /mnt/data_LT/Downloads /mnt/data

Once mounts are created you can also see folders in remote system with Nautilus. 

I have not use SSH.
       Morbius1 on SSH and Samba
[http://ubuntuforums.org/showthread.php?t=2326477&p=13498242#post13498242](http://ubuntuforums.org/showthread.php?t=2326477&p=13498242#post13498242)
[http://ubuntuforums.org/showthread.php?t=1354897](http://ubuntuforums.org/showthread.php?t=1354897)
[http://lifehacker.com/5831841/know-your-network-lesson-4-accessing-your-home-computers-from-anywhere](http://lifehacker.com/5831841/know-your-network-lesson-4-accessing-your-home-computers-from-anywhere)

---

### Post by tech291083 on 2016-08-06
Excellent, thanks a lot. I will try my best to do this process.

---

### Post by sudodus on 2016-08-06
> **tech291083 said:**
> OK.

So, what I understand is as follows

To transfer data between Windows and Linux PCs, I need WinSCP and FileZilla, right?

And to transfer data between 2 Linux PCs, I need sftp and rsync, right?

I have a router at home, but do I need internet to use (WinSCP and FileZilla) and/or (sftp and rsync)?

Thanks a lot.

To log in with ssh and transfer files with sftp, rsync WinSCP or FileZilla, you need an ***ssh server***, and it is easy to make a Ubuntu based linux system into one by installing **openssh-server**.

Then you can connect to that ssh server from Windows with WinSCP or FileZilla. You can connect from other linux systems with ssh, sftp and rsync, but there is also a FileZilla version for linux, so you can use the same software if you wish. (You can probably also find Windows versions of the command line tools ssh and sftp, if you like them.)

-o-

You have several alternatives now, and I suggest that you browse the internet and read about them before you decide which way to go.

---

### Post by tech291083 on 2016-08-12
> **sudodus said:**
> 
To log in with ssh and transfer files with sftp, rsync WinSCP or FileZilla, you need an ***ssh server***, and it is easy to make a Ubuntu based linux system into one by installing **openssh-server**.


Ok.

> 
Then you can connect to that ssh server from Windows with WinSCP or FileZilla. You can connect from other linux systems with ssh, sftp and rsync, but there is also a FileZilla version for linux, so you can use the same software if you wish. (You can probably also find Windows versions of the command line tools ssh and sftp, if you like them.)


Right, I get this.

> 
You have several alternatives now, and I suggest that you browse the internet and read about them before you decide which way to go.

Now, you have given me some good info, I will try my best to read about these options and try my best, thanks a lot.

---

