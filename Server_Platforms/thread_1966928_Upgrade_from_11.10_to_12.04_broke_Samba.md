---
title: "Upgrade from 11.10 to 12.04 broke Samba"
date: 2012-04-27
forum: Server Platforms
---

### Post by benkuhn on 2012-04-27
Hello,

I recently upgraded my file server from 11.10 to 12.04.  Since the upgrade, Samba has not allowed access to shares from windows or other samba clients.  This configuration was running correctly before the upgrade.

Windows clients give the error "Windows cannot access \\Servername\share check the spelling..."  Under details the error is "Error code 0x80070043 The network name cannot be found."

Mounting the share on other Samba clients I get the error "Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)"

I have checked all the usual stuff.  I have verified the samba user has read/write/execute permissions to the share.  The user account does exist when I do a pdbedit -L.  I can't even mount the share through loopback on the server.

The following is my smb.conf.  I NEED the dfree command and vfs objects directives in each of the shares in order for greyhole to work.


[global]
        workgroup = MAINFRAME
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        unix extensions = No
        wins support = Yes
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb
        wide links = Yes

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        print ok = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
        write list = root, frosty

[Backup]
        path = /storage/.logical/Backup
        read only = No
        create mask = 0777
        directory mask = 0777
        dfree command = /usr/bin/greyhole-dfree
        vfs objects = greyhole

[Books]
        path = /storage/.logical/Books
        read only = No
        create mask = 0777
        directory mask = 0777
        dfree command = /usr/bin/greyhole-dfree
        vfs objects = greyhole

[Homework]
        path = /storage/.logical/Homework
        read only = No
        create mask = 0777
        directory mask = 0777
        dfree command = /usr/bin/greyhole-dfree
        vfs objects = greyhole

[Music]
        path = /storage/.logical/Music
        read only = No
        create mask = 0777
        directory mask = 0777
        dfree command = /usr/bin/greyhole-dfree
        vfs objects = greyhole

[TV]
        path = /storage/.logical/TV
        read only = No
        create mask = 0777
        directory mask = 0777
        dfree command = /usr/bin/greyhole-dfree
        vfs objects = greyhole

[Photos]
        path = /storage/.logical/Photos
        read only = No
        create mask = 0777
        directory mask = 0777
        dfree command = /usr/bin/greyhole-dfree
        vfs objects = greyhole

[Software]
        path = /storage/.logical/Software
        read only = No
        create mask = 0777
        directory mask = 0777
        dfree command = /usr/bin/greyhole-dfree
        vfs objects = greyhole

[Movies]
        path = /storage/.logical/Movies
        read only = No
        create mask = 0777
        directory mask = 0777
        dfree command = /usr/bin/greyhole-dfree
        vfs objects = greyhole

[OS]
        path = /storage/.logical/OS
        read only = No
        create mask = 0777
        directory mask = 0777
        dfree command = /usr/bin/greyhole-dfree
        vfs objects = greyhole

[Projects]
        path = /storage/.logical/Projects
        read only = No
        create mask = 0777
        directory mask = 0777
        dfree command = /usr/bin/greyhole-dfree
        vfs objects = greyhole

---

### Post by bab1 on 2012-04-27
I don't think this is a Samba "problem".  Ubuntu 12.04 does handle DNS configuration differently when Network-Manager is in control of the interfaces.  A slightly different set up of DNSmasq is now being used.

Since you get this > "Error code 0x80070043 The network name cannot be found."


I'll bet this is a desktop install with Network-Manager; right?

Try adding this to your [global] section of the smb.conf file```
resolve order = bcast
```

[COLOR="Blue"]Edit:[/COLOR] This could also indicate that name resolution is not working> Mounting the share on other Samba clients I get the error "Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs( manual page (e.g. man mount.cifs)"

---

### Post by benkuhn on 2012-04-27
It's ubuntu server without NetworkManager :)

This happens when trying to connect either by IP or Hostname.

---

### Post by bab1 on 2012-04-27
> **benkuhn said:**
> It's ubuntu server without NetworkManager :)

This happens when trying to connect either by IP or Hostname.

Can you ping this host from the Windows host?

---

### Post by benkuhn on 2012-04-27
Yes.  I can ping by hostname and by IP.  I an list the shares on the server as well.

---

### Post by bab1 on 2012-04-27
> **benkuhn said:**
> Yes.  I can ping by hostname and by IP.  I an list the shares on the server as well.

From the Ubuntu host, what do you get with```
smbtree -d3
```Please post this between the [code] tags (this is the # icon).

---

### Post by benkuhn on 2012-04-27
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::207:e9ff:fe10:9c21%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=10.10.0.2 bcast=10.10.0.255 netmask=255.255.255.0

---

### Post by bab1 on 2012-04-27
> **benkuhn said:**
> ```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::207:e9ff:fe10:9c21%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=10.10.0.2 bcast=10.10.0.255 netmask=255.255.255.0
```

Two things here: 1. Put it between the code tags (like above) and 2. use your password and get the rest of the output.  The password won't be shown.  The debug date is in the part you have not shown.  :D

---

### Post by benkuhn on 2012-04-27
Sorry about that... Forgot about code tags.

Here's the rest of the output:
```
Deleted because I don't like the internal details of my network where everyone can see them.
Sorry for the paranoia :P
```

---

### Post by bab1 on 2012-04-27
It sure looks like you have name resolution from the Ubuntu side.  I'm not sure why you are using a WINS server on a single subnet (you don't need a WINS server at all).

If you are using 127.0.0.0/8 network for the WINS server how do the Windows hosts find it.  You can only have 1 WINS server per subnet (or network).

---

### Post by benkuhn on 2012-04-27
I haven't fully configured the WINS server yet.  Originally the idea was to use wins for name resolution so I didn't have to use the fqdn when accessing other hosts on the lan via hostname rather than IP.  I ended up setting up a proper DNS server instead so it's basically old cruft laying around now.

---

### Post by bab1 on 2012-04-27
> **benkuhn said:**
> I haven't fully configured the WINS server yet.  Originally the idea was to use wins for name resolution so I didn't have to use the fqdn when accessing other hosts on the lan via hostname rather than IP.  I ended up setting up a proper DNS server instead so it's basically old cruft laying around now.
It's not just cruft.  Your Ubuntu host is configured as a WINS server.```
wins support = Yes
```

I'm surprised that you are having problems with IPaddress connectivity.  If Samba is working then //IP_address/SHARE should work.  Is the Samba daemon running?
 ```
pgrep mbd
```

Are you aware that both Windows and Samba shares are ultimately ID'd by NETBIOS NAME for the host?  Samba converts the hostname or DNS FQDN with the daemon *nmbd*.  It's //NETBIOS_NAME/SHARE, not //DNS or Hostname/SHARE.

The default is to look to LMHOST and hosts and wins.  It is easier to just broadcast all this info (bcast).  If you look at you output from smbtree you will see that only the broadcast is successful. This is NETBIOS not hosts or DNS.

I'm not familiar with Windows other than to say that Windows workstations are set up as NETBIOS <b-node>.  This also is broadcast.  Even the hybrid mode is NETBIOS.

I would use Wireshark to see what the Windows hosts are looking for and adjust accordingly.

[COLOR="Blue"]Edit:[/COLOR] > I haven't fully configured the WINS server yet.  There is no configuration of a WINS server.  It's entirely dynamic.  It is is working or it's not.  Your one line has turned it on.

---

### Post by SeijiSensei on 2012-04-27
This looks problematic:

```
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
```

On my 12.04 machine that file is owned by root as is /var/run (a symlink to /run) and /var/run/samba.

---

### Post by bab1 on 2012-04-27
> **SeijiSensei said:**
> This looks problematic:

```
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
```

On my 12.04 machine that file is owned by root as is /var/run (a symlink to /run) and /var/run/samba.

I believe this is normal.  

[COLOR="Blue"]Edit: [/COLOR]These are binary blobs.  Those files are for Samba's use only.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://wiki.samba.org/index.php/Frequently_Asked_Questions").

See my```
smbtree -d3 |grep tdb
Enter bab1's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory

```
The no such file means they haven't been created yet.

---

### Post by gboudreau on 2012-04-27
I have yet to upgrade to 12.04 myself, but you should check that your Greyhole VFS library is still where it should be, otherwise Samba will let you see your shares, but you won't be able to connect to any Greyhole-enabled share until the VFS is there is should be.

On 11.10, it's here:

```
$ ls -l /usr/lib/samba/vfs/greyhole.so
lrwxrwxrwx 1 root root 39 2012-04-01 08:58 /usr/lib/samba/vfs/greyhole.so -> /usr/lib64/greyhole/greyhole-samba35.so

```
On 12.04, I'd guess it should be at the same location, but didn't check myself yet.

If you're missing that symlink, simply re-install the latest Greyhole .deb, either using dpkg or using apt: ```
apt-get install --reinstall greyhole
```

---

### Post by benkuhn on 2012-04-27
> **gboudreau said:**
> I have yet to upgrade to 12.04 myself, but you should check that your Greyhole VFS library is still where it should be, otherwise Samba will let you see your shares, but you won't be able to connect to any Greyhole-enabled share until the VFS is there is should be.

On 11.10, it's here:

```
$ ls -l /usr/lib/samba/vfs/greyhole.so
lrwxrwxrwx 1 root root 39 2012-04-01 08:58 /usr/lib/samba/vfs/greyhole.so -> /usr/lib64/greyhole/greyhole-samba35.so

```
On 12.04, I'd guess it should be at the same location, but didn't check myself yet.

If you're missing that symlink, simply re-install the latest Greyhole .deb, either using dpkg or using apt: ```
apt-get install --reinstall greyhole
```

Good catch.  My symlink was pointed to /usr/lib64/greyhole/greyhole-samba35.so.  12.04 upgraded Samba to 3.6 so I recreated the symlink and pointed it to greyhole-samba36.so and it's working again.

---

### Post by benkuhn on 2012-04-27
> **bab1 said:**
> It's not just cruft.  Your Ubuntu host is configured as a WINS server.```
wins support = Yes
```

I'm surprised that you are having problems with IPaddress connectivity.  If Samba is working then //IP_address/SHARE should work.  Is the Samba daemon running?
 ```
pgrep mbd
```

Are you aware that both Windows and Samba shares are ultimately ID'd by NETBIOS NAME for the host?  Samba converts the hostname or DNS FQDN with the daemon *nmbd*.  It's //NETBIOS_NAME/SHARE, not //DNS or Hostname/SHARE.

The default is to look to LMHOST and hosts and wins.  It is easier to just broadcast all this info (bcast).  If you look at you output from smbtree you will see that only the broadcast is successful. This is NETBIOS not hosts or DNS.

I'm not familiar with Windows other than to say that Windows workstations are set up as NETBIOS <b-node>.  This also is broadcast.  Even the hybrid mode is NETBIOS.

I would use Wireshark to see what the Windows hosts are looking for and adjust accordingly.

[COLOR="Blue"]Edit:[/COLOR]   There is no configuration of a WINS server.  It's entirely dynamic.  It is is working or it's not.  Your one line has turned it on.

Thanks for the info.  I'm honestly not a huge Windows guy so I never really looked in to how WINS works.  Now you have me curious.  That's always a good thing :)

---

### Post by bab1 on 2012-04-27
> **benkuhn said:**
> Thanks for the info.  I'm honestly not a huge Windows guy so I never really looked in to how WINS works.  Now you have me curious.  That's always a good thing :)

[COLOR="Blue"]**Edit: So many afterthoughts:** We can discuss WINS vs no WINS but first we should get the system working.[/COLOR]

Here is what I would do.[LIST]
[*] [COLOR="Red"]**Remove**[/COLOR] the *wins support = Yes* from the [global] section of smb.conf
[*][COLOR="Green"]**Add**[/COLOR] the line *name resolve order = bcast* to the [global] section of smb.conf
[*] Restart the smbd and nmbd daemons (sudo restart smbd (and then nmbd))
[*] Check that the daemons are running (pgrep mbd (2 smbd and 1 nmbd)
[/LIST]

If you want you can explicitly add the netbios name in the [global] section with ```
netbios name = SOME_NAME
```

To see if the netbios name is at least implied you can do this```
testparm -sv|grep netbios
```

Now try browsing for the Samba server.  If this is a Windows client it should be easy in Network Neighborhood.  If you are using a Linux client first try ```
smbtree
```

---

### Post by benkuhn on 2012-04-27
Actually, gboudreau's suggestion fixed it.  The symlink to the greyhole vfs library was pointing to the wrong version.  Thanks for your assistance.

---

### Post by bab1 on 2012-04-27
> **benkuhn said:**
> Actually, gboudreau's suggestion fixed it.  The symlink to the greyhole vfs library was pointing to the wrong version.  Thanks for your assistance.

I don't use that VFS.  I did a little reading.  I have to guess that the location of the share on whatever disk is what was the problem, rather than the hostname resolution, eh?

---

### Post by gboudreau on 2012-04-27
> **bab1 said:**
> I don't use that VFS.  I did a little reading.  I have to guess that the location of the share on whatever disk is what was the problem, rather than the hostname resolution, eh?
The problem was that he installed Greyhole on 11.10, and that installed the Greyhole VFS for Samba 3.5. When he upgraded to 12.04 (and thus Samba 3.6), Greyhole didn't update, and he was left with a Samba 3.5 VFS. HE switched that VFS for the Samba 3.6 one and it fixed his problems.

I should probably have the Greyhole daemon check for those incompatibilities, and fix them by itself.

---

### Post by ddewaleffe on 2012-05-06
I am having a similar problem after upgrading to 12.04...
I see the ubuntu machine from my windows (win 7, 32b and 64b) pc's but cannot get to the shares using the advertised netbios name. 

I get the [Network name cannot be found] error...

I can however see the shares and access them if I use the IP address of the ubuntu machine...

The mentionned fix did not work (not using greyhole)...

On the ubuntu side, smbtree displayed the expected view of my net/shares.

Any idea welcome...

D.

---

### Post by bab1 on 2012-05-06
> **ddewaleffe said:**
> I am having a similar problem after upgrading to 12.04...
I see the ubuntu machine from my windows (win 7, 32b and 64b) pc's but cannot get to the shares using the advertised netbios name. 

I get the [Network name cannot be found] error...

I can however see the shares and access them if I use the IP address of the ubuntu machine...

The mentionned fix did not work (not using greyhole)...

On the ubuntu side, smbtree displayed the expected view of my net/shares.

Any idea welcome...

D.

If you are not using *greyhole* then you problem is NOT the same as the OP's problem.  I would start a new thread that describes your specific problem.  Maybe post the exact errors.  Describe your configuration.

---

### Post by ddewaleffe on 2012-05-06
1. similar != same
2. problem solved: disable IPV6 on 12.04
    as described in [http://blog.dannysauer.com/?p=239](http://blog.dannysauer.com/?p=239)

---

