---
title: "samba - not showing up in &quot;Network&quot;"
date: 2013-04-26
forum: Server Platforms
---

### Post by megadave on 2013-04-26
**Solved**
Since I had nothing on the SSD, I just wiped it and installed 13.04.  I did the "right click"->Properties->Share thing on a folder, which then asked to install samba.  It did, and then success, my ubuntu box shows up in the network of the macbooks and the wd live.

I think I created the problem by installing samba myself, then installing some samba admin tools and whatnot.  As for what the actual problem was, I did not figure it out.  The cause of the problem.....me.

//Updating this on the off chance this helps someone else in the future.  



Hi all,

**The setup**

My hard drive developed a rash of bad sectors, so I took the opportunity to upgrade to an ssd, which has been great.  I did a fresh install of 12.04 LTS, got everything up and running.

My network consists of:

1.  an ubuntu box serving up media
2.  a few macbook pros
3.  WD LIVE box playing media off of the server on my tv.


samba works great using the server IP from any laptop , but does not show up in the network.  This is a problem because the WD LIVE box only enumerates the available "Windows Shares" by name and doesn't allow me to do so by IP.

Oddly enough, what does show up is the Network of the osx laptos is "Screen Sharing" from the ubuntu server (which also works fine).

[IMG]http://i.imgur.com/UizSevm.png[/IMG]

**Troubleshooting so far**
1.  I recovered my smb.conf file from the corrupted drive, restored it - no change
2.  disable the firewall - no change
3.  uninstalled, reinstalled samba - no change
4.  added netbios name to smb.conf - no change
5.  enabled wins server - no change
6.  changed order of the name resolution in smb.conf - no change
7.  service restarts/reboots
8.  host name and netbios name are same.

I am at a loss.  This worked great before the re-installation.  I even tried enabling "Windows File sharing" on the macbook to test things out, and it popped up on the network and in the WD LIVE's list of Windows Shares and on the Ubuntu computer under Network ->Windows Network -> Workgroup where I can see the Macbook and the WD LIVE (they both can serve windows shares) but not the Ubuntu box.

[IMG]http://i.imgur.com/HZzIYml.png[/IMG]

It appears that samba is not announcing it's presence to the other devices on my network. Anyone have ideas?

---

### Post by cbanakis on 2013-04-26
Not sure if it is related, but I have been having a ton of problems with our Windows, and Ubuntu computers not connecting to our mac's at work.

The problem I am having, is that appearantly Apple decided not to use SAMBA, as of Lion.

Instead, they decided to make their own so called SAMBA, and it is terrible.

I can access the mac shares from Ubuntu by browsing my local network, but cannot do a direct mount via ip.

I can do a direct mount via ip on windows machines, but cannot browse.

Apple support claims they are working on the problem, but it has been ongoing for about 2 years now, so I don't think they consider it a priority.

---

### Post by stoute on 2013-04-26
I don't know if you have a windows computer on that network but I'd check to see if you can get it to show up on that. I know that i am having the same issue on my windows network and will be curious to see what you come up with.

---

### Post by darkod on 2013-04-26
Try also comparing the DNS servers on the machines and the server. I think it helps if they use the same DNS server. For example, if the router is the dns for your machines, but on the server you set a manual public dns, try setting the router IP also as dns.

EDIT PS: It might, or might not be a proof, but I just checked and my home server has same dns servers as my win7 desktop. And in Network it does show the server by name, even though I always do Superkey + R, \\IP. I never go into Network.

The win7 desktop receives dynamic IP from the router with a reservation, but for dns I have manual setup of the google nameservers 8.8.8.8 8.8.4.4.
On my ubuntu home server, the nameservers are identical, 8.8.8.8 8.8.4.4.

---

### Post by megadave on 2013-04-26
darkod:

The Ubuntu box and the WD Live have the same DNS, the one handed out by the router.  My macbook had the google one hardcoded in.  I've removed that.  Now everything uses the one handed out by the dhcp server.

Updates since I last posted/performed the above:

The ubuntu box now lists itself in the network and I can connect from it to it's own shares.  At least it seems to acknowledge its own samba shares.  That's progress, but I can't attribute it to anything but the passage of the last 4 hours.

I see an entry now in the macbook network for "dingo" which is my ubuntu box.  But trying to connect to it fails.  Still works fine with the IP.  Not showing on the WD Lives list of "Windows shares" either.

stoute:  Unfortunately I don't have a windows computer.

cbanakis:  I am running 10.6....yes I'm a bit behind the times.

I've continued to research.  Turns out samba's tools are also on osx.

smbtree (run from a macbook)
```

Password: 
WORKGROUP
	\\WDTVLIVE       		WD TV Live
		\\WDTVLIVE\IPC$           	IPC Service (WD TV Live)
	\\DINGO          		dingo
cli_start_connection: failed to connect to DINGO<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\BENDER         		Bender
		\\BENDER\david   	User Home Directories
		\\BENDER\IPC$           	IPC Service (Bender)
		\\BENDER\David's Public Folder	David's Public Folder
	\\7054EF000000   		MP620 series
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine 7054EF000000.  Error was ERRDOS - ERRbadfile (File not found.)
		\\7054EF000000\canon_memory   	MP620 series
		\\7054EF000000\IPC$           	
Bender:~ david$ 

```

running smbtree on the Ubuntu box produces no output...not even an error.

running smbtree -d3 on Ubuntu box
```

dave@dingo:/etc/mediatomb$ smbtree
Enter dave's password: 
dave@dingo:/etc/mediatomb$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::224:21ff:fe2c:9caf%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.101 bcast=192.168.1.255 netmask=255.255.255.0
Enter dave's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.8 ( 192.168.1.8 )
Connecting to host=192.168.1.8
Connecting to 192.168.1.8 at port 445
Connecting to 192.168.1.8 at port 139
Server requested LANMAN password (share-level security) but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
failed tcon_X with NT_STATUS_ACCESS_DENIED
Connecting to host=WDTVLIVE
Connecting to 192.168.1.8 at port 445
Connecting to 192.168.1.8 at port 139
Server requested LANMAN password (share-level security) but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
failed tcon_X with NT_STATUS_ACCESS_DENIED

```

Just for clarification, 192.168.1.8 is the WD Live's IP.

---

