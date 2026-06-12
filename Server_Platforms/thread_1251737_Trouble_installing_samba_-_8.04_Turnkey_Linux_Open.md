---
title: "Trouble installing samba - 8.04 Turnkey Linux OpenVZ container"
date: 2009-08-28
forum: Server Platforms
---

### Post by JedMeister on 2009-08-28
I wasn't sure where the best place to post this issue would be but I decided to post here and see how we go. If I don't have any joy here I'll try elsewhere and post back with my progress. I am currently having trouble installing samba on a container running under OpenVZ (Proxmox).

I have spent a heap of time searching the net and I can't find anyone with a problem just like mine (probably because I have a unique hacked together setup).

Firstly a bit of background:
Basically I am a Linux noob but fairly tech savy and a bit of PC admin experience (although mostly on Windows).
My hardware OS is [Proxmox]("http://pve.proxmox.com/wiki/Main_Page") 1.3 (a virtualisation environment based on Debian Lenny running KVM-86 and OpenVZ).
My VM is a [hacked together template that I made myself]("http://wiki.turnkeylinux.org/Whiteboard/OpenVZ_Template_-_TKL_Core") (from [Turnkey Linux Core]("http://www.turnkeylinux.org/appliances/core/updates") - based Ubuntu 8.04LTS) running in an [OpenVZ]("http://wiki.openvz.org/Main_Page") container.

As I was saying a pretty unique hacked together setup!

I have done a fair bit of testing and haven't had any problems like this (that I haven't been able to fix). I have installed lots of packages and have many many running fine. But this one has me stumped.

I am running as root (I know I know!) and when I install (using apt-get install samba) I get the following:
```
Unpacking samba (from .../samba_3.0.28a-1ubuntu4.8_i386.deb) ...
Setting up samba (3.0.28a-1ubuntu4.8) ...
Generating /etc/default/samba...
tdbsam_open: Converting version 0 database to version 3.
account_policy_get: tdb_fetch_uint32 failed for field 1 (min password length), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 2 (password history), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 3 (user must logon to change password), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 4 (maximum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 5 (minimum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 6 (lockout duration), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 7 (reset count minutes), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 8 (bad lockout attempt), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 9 (disconnect time), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 10 (refuse machine password change), returning 0
Importing account for nobody...ok
* Starting Samba daemons                                                             [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure): 
	subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
	samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
From my understanding of the error(s) it seems to be a user account problem of some sort. As I said above I am running as root, This is for another purpose (not just a samba server) and so I have only defined one user. As far as I know I do not have an account 'nobody' (unless that a default Ubuntu user account?)

I have tried most of the common advice that I have read re samba problems (eg apt-get --purge remove samba / samba-common, reinstall) to no effect.

Anybody got any ideas for me please. I'm sure its something I've broken when I converted the TKL appliance to an OpenVZ container but I've got no idea what. Or perhaps its just something simple I've overlooked.

Thanks!

---

### Post by JedMeister on 2009-08-31
I'm going to continue troubleshooting this over on the [Turnkey Linux forums]("http://www.turnkeylinux.org/forum/general/20090813/plans-tkl-openvz-templates"). If you think you have something useful to offer please feel free to come over there and post (or just post here). 

If/when I find a solution I will endeavor to post back here.

---

### Post by JedMeister on 2009-09-01
Solved! The problem was that I neglected to create the /dev/random file and as such samba was unable to generate random numbers on intial install. The reason why other apps were working fine is that most use /dev/urandom to generate random nos. It still has the (above) permission errors on install but it will run. Apparently the way to resolve these errors is to use the command```
dpkg-reconfigure samba

```

---

### Post by brian.hussey on 2009-10-02
> **JedMeister said:**
> Solved! The problem was that I neglected to create the /dev/random file and as such samba was unable to generate random numbers on intial install. The reason why other apps were working fine is that most use /dev/urandom to generate random nos. It still has the (above) permission errors on install but it will run. Apparently the way to resolve these errors is to use the command```
dpkg-reconfigure samba

```

Hi,
I had this same problem, and solving it came down to the reconfig as well, but "dpkg-reconfigure" samba gave me similar issues.

I solved it by 
```
sudo apt-get remove samba
sudo apt-get remove samba-commons
sudo apt-get purge samba
sudo apt-get purge samba-commons

``` 
the purges were to be sure to be sure...

```

sudo apt-get install samba-commons

```
At which point I got error:
```
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba-common
```

To fix this :
```

sudo cp /usr/share/samba/smb.conf /etc/samba/smb.conf
sudo dpkg --configure -a

```

Then "sudo apt-get install samba" worked like a charm.

Hope this helps, someone save a few hours of their lives :D

Brian

---

