---
title: "Samba Write Performance Poor.  Need Expert Help."
date: 2012-08-22
forum: Server Platforms
---

### Post by Colin R on 2012-08-22
Hi All,

Having some problems with a new server at a customer site.
First;
The server is a Fujitsu TX100 S3
CPU is Xeon Quad Core
RAM = 8Gb
Disks = 2 x 500Gb SATA (RAID turned off and Only 1 disk in use)
No of networked users = 38 (all running Windows XP)
DHCP is handled by a Watchguard Firewall
Network is built arount 2 x 24 port 10/100Mb Ethernet switches

The problem;
The system runs an old DOS Accounting/Stock package written in Clipper s87 and performance, generally, is excellent. Writing files, however, is S L O W and, in that department, the system is shown a very clean pair of heels by their (the customers) Netware 4.11 server (P4, 2Gb RAM)
As an example;
On entry into one procedure, it creates 3 Temporary files for data storage.  This is taking around 14 secs where, on the Netware box, it is almost instant.

The smb.conf file is pretty much the vanilla 'out of the box' offering with the following items added;
oplocks = false
level2 oplocks = false
with 'socket options = TCP_NODELAY' uncommented

Strange thing is that another system (at a different site) running the same software, with a similar number of users, on an almost identical network, under Ubuntu 10 on a home built server (P4, 4Gb) doesn't have this problem.

Hardware issues? Driver Problems? Bottlenecks? Past Experiences? 
The customer is threatening to go back to his Netware box so, any suggestions would be appreciated.

---

### Post by Colin R on 2012-08-31
Customer has now told me to "GET THAT PIECE OF *!"£ OUT OF HERE.  "

Desperate.

Any suggestions

---

### Post by SeijiSensei on 2012-08-31
Have you read through this: [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html?](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html?)

Do the temporary files actually need to be written to disk, or could you write them to a [shared memory device]("http://askubuntu.com/questions/169495/what-are-run-lock-and-run-shm-used-for") or some other ramdisk option?  How big are they?  If it's an old DOS program they cannot be very large.  Try pointing temporary storage to /dev/shm (or /run/shm) if it exists on your machine, or set up a shared memory device.

---

### Post by Colin R on 2012-08-31
Thanks for the reply.

I don't think that using RAM drives (or similar) will be effective.

eg;
A 'Month End' process that takes about 20 minutes on the old Netware 4.11 box took 1 hr 55 minutes on the new, much faster, Linux Box.

I've been through all (the ones I could find) the Samba guides and have tried a large variety of different options but, the problem remains that performance with this program is way down on the Netware box.

I suspect that there might be a network driver issue on the new sever although ethtool etc seem to indicate that the setup is correct and that everything is fine.

Network interface(s) in the Server is an Intel 82574L (eth0) + 82579M (eth1)

It is also possible that the 64bit nature of the Server just doesn't like 16 bit DOS software as all Windows based apps seem to run just fine.

---

### Post by SeijiSensei on 2012-09-01
Back in the day when we all ran Netware and IP was just coming into fashion, we built some Linux servers with [mars_nwe]("http://ubuntuforums.org/showthread.php?t=1196058"). I believe it only emulates Netware 3.  By the time Netware 4 was released we were already migrating to TCP/IP with Win95 desktops and Linux servers.

There is also lwared, which I've never used.  You might want to take a look at the [IPX-HOWTO](http://oss.sgi.com/LDP/HOWTO/IPX-HOWTO-10.html).

Another possibility might be to run a VirtualBox VM on the server with a NetWare server running in it.  You could configure it to provide access to the same set of directories via NW or via Samba.

---

### Post by ian dobson on 2012-09-01
Hi,

Maybe try optimizing your samba configuration. This is what I'm using and am getting approx 50Mbyte/sec write speed over GBit lan from a windows7 box to the linux server.

```

client ntlmv2 auth = yes
read raw = yes
write raw = yes
wide links=yes
getwd cache=yes
stat cache = yes
strict sync = no
use sendfile = yes
large readwrite = yes
oplock contention limit = 5
oplock break wait time = 100
case sensitive = true
strict allocate = yes
max xmit = 131072
use sendfile = Yes
dead time = 15
getwd cache = Yes

min receivefile size = 13638
aio read size = 64360
aio write size = 64360
aio write behind = true

##Optimize tcp
socket options = TCP_NODELAY SO_RCVBUF=262144 SO_SNDBUF=262144 IPTOS_LOWDELAY SO_KEEPALIVE

write cache size = 12826144

```

The aio and socket options seem to make the biggest differences. Note you need to have enough ram for the best performance. Just edit  /etc/samba/smb.conf and restart samba and test.

Also are your network ports running at 100Mbit rather that 10Mbit?

Regards
Ian Dobson

---

### Post by kevinthecomputerguy on 2012-09-01
You might be getting a half-duplex connection on your nic, run these commands and make sure your not getting half-duplex. 

ethtool eth0

mii-tool

Also make sure your MTU is right. (usually 1500)

I give brief examples of this problem here, [http://woodel.com/page2.html](http://woodel.com/page2.html)

---

### Post by xdracco on 2012-09-02
It could very well be your network interface. I encountered the same issue with samba. it was so painfully slow that I tried using Netatalk (my network is mostly OSX) but that didn't help. Then my root partition took a crap so I ended up just buying an entirely new server. Now, samba and netatalk both scream in terms of speed with no special tweaking with the new network interface.

The server was 7 years old so it's no surprise that it started to fail. This may not be your issue but it's something to consider.

---

### Post by Colin R on 2012-09-02
OK All, Thanks for the replies and suggestions.

I took the time to read through them and see just what you were doing.
Some decent ideas but not to sure about AIO.  Does it work with Windows XP terminals?

Update.

Worked on the beast most of yesterday and, although I made some slight improvements, it was still far from satisfactory.

Today, I decided to take an old Core2 Pentium, 2Gb RAM, 100Mb NIC and, 160Gb SATA disk on an experimental journey.

Loaded v12.04 32bit (not 64) and used an old Dell 1.6Mhx Laptop with 512Mb RAM as a terminal.  Guess what, performance was about 10% better than the Netware box and way better than the new server.

I'm really puzzled at this point and can only assume that either the new server doesn't like my program or that the 64bit version of Ubuntu doesn't like it.

Network card on new server reports 1000Mb Full Duplex etc. and the new smb.conf was identical to the old one.  Nothing else was changed.

MTU is 1500

---

### Post by redmk2 on 2012-09-02
> **Colin R said:**
> ...
I'm really puzzled at this point and can only assume that either the new server doesn't like my program or that the 64bit version of Ubuntu doesn't like it.

I have both 32 bit and 64 bit Ubuntu running Samba with no problems.  Some are P3 with 512MB RAM with no speed problems.

There are 2 things that I find crucial.  First is disk I/O.  What file system are you using on your HDD's?  Using NTFS on Ubuntu hosts can cause I/O problems.  All of my Ubuntu machines use ext4.

The second is using the best NIC driver.  I have not had any problems with this, but others have.  What chip set on the second machines NIC more common than the first NIC?

---

### Post by Colin R on 2012-09-02
> **redmk2 said:**
> I have both 32 bit and 64 bit Ubuntu running Samba with no problems.  Some are P3 with 512MB RAM with no speed problems.

There are 2 things that I find crucial.  First is disk I/O.  What file system are you using on your HDD's?  Using NTFS on Ubuntu hosts can cause I/O problems.  All of my Ubuntu machines use ext4.

The second is using the best NIC driver.  I have not had any problems with this, but others have.  What chip set on the second machines NIC more common than the first NIC?

OK, 
Both machines are using SATA drives formatted to EXT4.  The new server has a pair of 7200 rpm 500Gb drives (only 1 is used) whilst the Core2 P4 has a 5400 rpm 160Gb drive.
The new server has a 1Gb intel chipset NIC whilst the Core2 (HP Compaq 7700) has an Intel based 1Gb NIC (not sure which right now).

I was leaning a little towards the NIC in the new server being faulty or having 'bad' drivers but, every test I have run seems to be fine.

I will download the latest drivers for the Intel chipset later on and, install them in the morning.

---

