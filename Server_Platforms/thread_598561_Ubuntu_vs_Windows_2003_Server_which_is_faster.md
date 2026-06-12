---
title: "Ubuntu vs Windows 2003 Server which is faster"
date: 2007-10-31
forum: Server Platforms
---

### Post by th3joker on 2007-10-31
Hi,

My server at home just failed and I have had a replacement here waiting for this as I knew it was imminent.

My question is this: - 

I have a 10 user license for Windows 2003 SBS but would like to consider Ubuntu Server as an alternative. 

I mainly need to transfer pretty large files (800MB+) to and from the server.

What would be that fastest performer for File Serving only Linux or Windows 2003 Server. Also which would be faster NFS or Samba. Finally if I use Linux which FS would be quickest and best for this environment EXT2/3, XFS, ReiserFS etc..

I have 2 Mac OS X systems both running Leopard (10.5) OS, I also 
have 4 PC's all running Vista & XP in Dual Boot setups.

I am unsure if NFS would perform better than Samba for the 2 Mac's, if I use Ubuntu for a server. I can use DiskShare for NFS on the PC's or Samba whichever is the fastest.

Any help or pointers would be most gratefully received.

Adrian :-)

---

### Post by dantrevino on 2007-11-03
Any claims to being "faster" by either would be arbitrary.  You're unlikely to stress the OSs, protocols, or filesystems with your configuration.

Samba has some nice CIFS speed ups when connecting to another samba machine.  NFS has advantages in specific configurations.  XFS is claimed to be faster for large files, but I think the benchmarks that show this generally use multi-gigabyte size files, may be outdated, and would be largely irrelevent when transferring files over a network.

All of that will be moot if you're using a 10 Mb hub, or 802.11b from across your home.

In other words, use what you feel most comfortable with and which ever lets you sleep better at night (*cough* ubuntu *cough*).

dan

---

### Post by HermanAB on 2007-11-03
On a home network, you won't notice any speed difference between Windoze and Linux.

What may be more important is that a server with Linux and JFS, will be able to store about 20% more data on the HDD than Windoze with NTFS.

---

### Post by th3joker on 2007-11-03
Hi,

Thanks for all the help :-)

I ran some tests with a variety of file types, sizes and Server set ups. 

2003 server was the slowest to upload to but the fastest to download.
Ubuntu Samba was the fastest to upload to but the second slowest to download.
Ubuntu NFS to Mac NFS was the 2nd fastest to upload to but the slowest to download.

So a mixed bag really, the set up for Ubuntu was straight out of the box, defaults all round but the FS was xfs. 2003 Server all defaults too. Same with the Ubuntu NFS setup.

I was quite surprised that the NFS didn't do better, quite a few people thought this would win hands down. I didn't do any tweaking with the NFS or Samba configs though so that may explain it

I am going to stick with 2003 Server in the short term as I need a couple of big drives to backup the data, reformat as xfs and then move over to Ubuntu samba. I may experiment with NFS & Samba tweaks to see if I can improver throughput.

---

