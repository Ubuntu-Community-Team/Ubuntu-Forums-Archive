---
title: "Ubuntu 10.04;Samba Fast, then slow???"
date: 2012-05-22
forum: Server Platforms
---

### Post by Thegmandrive on 2012-05-22
I use Ubuntu 10.4.3, I have samba installed. When I transfer to my Mac I can copy at around 34megabytes a second for around 3 min, then it drops the speed to about 2 megabytes a second. The only way I can get the increased speeds again is when I reboot my entire server. I have a 6core with about 7 gigs of ram allocated, 

Note: I run Ubuntu Headless on ESXI 5.0 

Is it possible that 7gigs of ram is not enough? According to the usage statistics the Procs are not being over loaded, but a lot of the ram is being used. 

Wondering if any of you have any ideas, or have experienced similar issues.

---

### Post by Thegmandrive on 2012-05-23
Bump

---

### Post by lukeiamyourfather on 2012-05-23
That's plenty of memory for a virtual machine only serving files to a few users. Can you share other information, like what kind of files are being transferred and how many? Lots of small files can greatly reduce the throughput compared to one large file of equal size.

It could be problems unrelated to Ubuntu like the virtualization software, a bad NIC, bad switch or port, or it could be something with the Mac and how it mounted the share. By eliminating different variables you can figure out what the cause is.

---

### Post by Thegmandrive on 2012-05-23
> **lukeiamyourfather said:**
> That's plenty of memory for a virtual machine only serving files to a few users. Can you share other information, like what kind of files are being transferred and how many? Lots of small files can greatly reduce the throughput compared to one large file of equal size.

It could be problems unrelated to Ubuntu like the virtualization software, a bad NIC, bad switch or port, or it could be something with the Mac and how it mounted the share. By eliminating different variables you can figure out what the cause is.

I was trying to transfer Video files, they are about 2 gigs a piece and I was transferring around 7 equaling to 13 gigs. 

I connected to the samba via my mac as a mounted drive

Is it possible that I'm experiencing a Looping Issue regarding my switches? My network is set up as follows 

I have created a [Diagram]("https://picasaweb.google.com/113418148684206122108/Network?authkey=Gv1sRgCP7lkbryremWGA#5745781778788964850") to make it a little easier the switches are Unmanaged. 
The only reason why I don't think that's the problem is because like I said, it transfers at about 32megs a second for about 2 min, then drops to 2megs a second. 


[IMG]https://picasaweb.google.com/113418148684206122108/Network?authkey=Gv1sRgCP7lkbryremWGA#5745781778788964850[/IMG]

---

### Post by redmk2 on 2012-05-23
> **Thegmandrive said:**
> I was trying to transfer Video files, they are about 2 gigs a piece and I was transferring around 7 equaling to 13 gigs. 

I connected to the samba via my mac as a mounted drive
How did you perform the mount?  Did you mount it via the GUI or via the command line?> 
Is it possible that I'm experiencing a Looping Issue regarding my switches? My network is set up as follows
No.  Even unmanaged switches employ Spanning Tree Protocol. Plus you don't have a physical loop to begin with.>  
I have created a [Diagram]("https://picasaweb.google.com/113418148684206122108/Network?authkey=Gv1sRgCP7lkbryremWGA#5745781778788964850") to make it a little easier the switches are Unmanaged. 
The only reason why I don't think that's the problem is because like I said, it transfers at about 32megs a second for about 2 min, then drops to 2megs a second. 


[IMG]https://picasaweb.google.com/113418148684206122108/Network?authkey=Gv1sRgCP7lkbryremWGA#5745781778788964850[/IMG]

I usually mount Samba shares via the command line or via fstab if I am moving large amounts of data.

---

### Post by Thegmandrive on 2012-05-23
> **redmk2 said:**
> 
I usually mount Samba shares via the command line or via fstab if I am moving large amounts of data.

I did mount the drive via Gui, but that is a good idea, I can try mounting via the terminal commands. I will do that, and try to transfer the same data and report back :)

---

### Post by Thegmandrive on 2012-05-23
Ok I mounted the samba via Mac Terminal and used the "CP" function to copy the files. It did a little better. It still started to download really fast and then slowed to about 3 megabytes a second :( 

Note* I had to restart my server for it to initially start Fast. Is it possible this could be a memory leak of some kind?

---

### Post by redmk2 on 2012-05-24
> **Thegmandrive said:**
> Ok I mounted the samba via Mac Terminal and used the "CP" function to copy the files. It did a little better. It still started to download really fast and then slowed to about 3 megabytes a second :( 

Note* I had to restart my server for it to initially start Fast. Is it possible this could be a memory leak of some kind?

More likely its a buffer overload or an I/O problem.  File transfers don't use a lot of RAM.   You can check the overall load and top individual usage with *htop*.

The command line mount can be customized for receive/send buffers if needed.  What did your mount command look like?

This could also be a hardware problem.  What are we using here; Gigabit Ethernet, Fast Ethernet?  What type of cable Cat5 or 6?

---

### Post by lukeiamyourfather on 2012-05-24
I would spend more time on other factors besides Ubuntu like the NIC or ESXi. Samba is very reliable and that's a release of Ubuntu that has been tested and proven reliable for several years. Assuming you haven't gone through and changed the Samba configuration file without knowing what  each option does.

---

### Post by Thegmandrive on 2012-05-24
> The command line mount can be customized for receive/send buffers if needed.  What did your mount command look like?Mount Command Looks Like 
```
mount -t smbfs //user@server/sharename share
```Then I used this command to copy
```
cp -Rpv Documents "Documents backup"
```
> This could also be a hardware problem.  What are we using here; Gigabit Ethernet, Fast Ethernet?  What type of cable Cat5 or 6? I am using a gigabit Ethernet Intel PWLA8391GT PRO/1000 GT PCI Network Adapter. And I am using Cat5E 



> Assuming you haven't gone through and changed the Samba configuration file without knowing what  each option does. Before coming to this forum, I did try some extra research and did try a couple configuration Changes. Based on an [Article by Samba]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html")
For Example,I have tried adding this criteria at one point
TCP_NODELAY
SO_KEEPALIVE
IPTOS_LOWDELAY

Adding this criteria did in fact increase the speeds, but then it drops again. I even tried at one point setting the socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
but that actually decreased the speed. I just can't figure out why it will transfer at 34 megs a second for 2 min... and then it drops to 2megs a second for the rest of the time, and then I have to restart my entire system to get the 34 meg speeds again.

---

### Post by redmk2 on 2012-05-24
> **Thegmandrive said:**
> Mount Command Looks Like 
```
mount -t smbfs //user@server/sharename share
```
This doesn't look right to me. The basic mount command should look like this```
mount -t cifs //server/share mount_point
```
See ```
man mount.cifs
```> 
Then I used this command to copy
```
cp -Rpv Documents "Documents backup"
```
 I am using a gigabit Ethernet Intel PWLA8391GT PRO/1000 GT PCI Network Adapter. And I am using Cat5E
Cat5E is marginal at gigabit speeds.>  
 Before coming to this forum, I did try some extra research and did try a couple configuration Changes. Based on an [Article by Samba]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html")
For Example,I have tried adding this criteria at one point
TCP_NODELAY
SO_KEEPALIVE
IPTOS_LOWDELAY

Adding this criteria did in fact increase the speeds, but then it drops again. I even tried at one point setting the socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
but that actually decreased the speed. I just can't figure out why it will transfer at 34 megs a second for 2 min... and then it drops to 2megs a second for the rest of the time, and then I have to restart my entire system to get the 34 meg speeds again.
You might want to consider monitoring the system with *dstat* and *iperf* during the transfer.

I have to agree with @lukeiamyourfather, I don't think Samba (used correctly) is your problem.  I have no experience with ESXI so I can't comment on that.

---

### Post by ian dobson on 2012-05-25
Hi,

What does iotop -o -P show when samba is "slow".

I've seen on my backend server (16Gb ram,8 core, 8Tb RAID5 array) that the samba deamon sudenly goes to a very hgh IOWait reading something from the array (even when just writing from another computer).

After a couple of minutes the iowait drops to a "normal" value and the wite speed goes back up to 30-50M/Byte sec.

When transfering large amounts of data (>30Gb) I usually use ftp as that seems to be much quicker than samba.

Regards
Ian Dobson

---

### Post by Thegmandrive on 2012-05-25
> Hi,

What does iotop -o -P show when samba is "slow".
I will try that sometime tonight and report back, 


> You might want to consider monitoring the system with *dstat* and *iperf* during the transfer.
I will try dstat, and I will also try to to mount the share as you suggested I will report. :)

---

### Post by Thegmandrive on 2012-05-28
Well, I was using Samba 3.4, and I decided, since nothing else was working, to try and update to 3.6 

I have now tested transferring over 20 gigs, and only saw a few minor drops in speed, but the average stayed around 34 megabytes a second. Woot!! another thing I noticed is that after the transfer, samba now releases unused memory, which i don't think it was doing before. 

I am on 10.04 so I did need to compile from source to upgrade to 3.6, so I'm not sure I would suggest this as a "fix" to people seeing as 3.6 is not officially supported by Ubuntu repo's yet. 

thanks everyone for your help.

---

