---
title: "Windows clients randomly disconnected from Samba shares"
date: 2014-09-17
forum: Server Platforms
---

### Post by freakalad on 2014-09-17
I have a hand-me-down server (upgraded over several LTS's) that's been running (mostly) stable for several years, but recently random clients of 2-dozen odd users are experiencing their mapped network drives getting randomly disconnected.

The windows users on on a NT domain, but the Samba server not & is set up to accept any & all connections unauthenticated form the LAN & treat them as chown nobody:nogroup

What bugs the hell out of me is why this issue is not consistent & widespread, but only happens intermittently & randomly.

I've checked the (very noisy log - what's with all the "../source3/"?) log & the only clue I'm seeing is this line:
"[2014/09/18 11:10:22.198697,  2] ../source3/auth/auth.c:288(auth_check_ntlm_password)
  check_ntlm_password:  Authentication for user [winuser] -> [winuser] FAILED with error NT_STATUS_NO_SUCH_USER"

This is a summary of the current smb.conf
(this is a fairly old box, so I've kept changes to the config minimal over the years)

```


[global]
        log file = /var/log/samba/log.%m
        log level = 2   
        max log size = 10240
        debug timestamp = yes

        load printers = no
        name resolve order = bcast host lmhosts wins
#name resolve order = lmhosts wins bcast host
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        aio read size = 1
        obey pam restrictions = yes
        wins server = $REDACTED
#deprecated     null passwords = yes
        encrypt passwords = true
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        aio write behind = false # true can cause corruption
        dns proxy = no
        netbios name = $REDACTED
        netbios aliases = fileserver
        server string = %h server (Samba, Ubuntu)
        unix password sync = yes
        aio write size = 1
        workgroup = $REDACTED
        os level = 20
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        max log size = 1000
        pam password change = yes

#max connections = 0
#deadtime = 0

#global shares rights & permissions
#        security = share
        usershare allow guests = yes

        guest ok = Yes
        guest account = nobody
#        map to guest = nobody

#https://wiki.archlinux.org/index.php/Samba/Tips_and_tricks
        map to guest = bad user
        security = user

#       admin users = nobody    #       ommitted: otherwise chown = root:nogroup
        force user = nobody
        force group = nogroup

        directory mask = 0775
        create mask = 0775
        force directory mode = 0775
#        force create mode = 0664
        force create mode = 0775

#kill stale/interrupted connections
        reset on zero vc = yes

#http://oreilly.com/catalog/samba/chapter/book/appb_02.html
        read raw = yes  
        write raw = yes 

#http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting
#bind interfaces only = Yes
        hosts deny = ALL
        hosts allow = 192.168.0.0/24  127.
#interfaces = eth0 eth1 lo

        load printers = no
        printing = bsd
        printcap name = /dev/null
        printcap cache time = 0
        disable spoolss = yes

#https://calomel.org/samba_optimize.html
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536 SO_KEEPALIVE


```

This server is a bit of a hand-me-down.
Since I don't deal with Samba servers all that often - I typically set them up & forget about messing around with an otherwise stable setup - this server's config has not been significantly altered over maybe 3 or more LTS's, but I believe Samba4 has now introduced issues that has not previously been present.

---

### Post by freakalad on 2014-09-18
I've dug around a little more, and found a suggestion to update the smb.conf to not use the deprecated "security= share" to "security = user" & "map to guest = Bad User".

Issue persists.

I've also wondered if it isn't some DNS or name-resolution issue, since I've seen the following.

In my /var/log/samba, I can see 2 logs for every connecting host: log.$HOSTNAME & log.$IPADDRESS

There seems to be a sort of hand-off between logs that seems to correspond to the aforementioned issues.

In the log.$IPADDRESS I see: (note the 30-minute gap)
```

[2014/09/19 10:04:00.618178,  2] ../source3/auth/auth.c:288(auth_check_ntlm_password)
  check_ntlm_password:  Authentication for user [$USER] -> [$USER] FAILED with error NT_STATUS_NO_SUCH_USER
[2014/09/19 11:46:58.979264,  2] ../source3/smbd/reply.c:592(reply_special)
  netbios connect: name1=DELL_FSERVER   0x20 name2=SN102185       0x0

```

The inverse/complement to the gap shows up in log.$HOSTNAME, leading me to believe that some sort of routing or name-resolution issue could be involved.

---

### Post by bab1 on 2014-09-18
> **freakalad said:**
> I've dug around a little more, and found a suggestion to update the smb.conf to not use the deprecated "security= share" to "security = user" & "map to guest = Bad User".

Issue persists.

I've also wondered if it isn't some DNS or name-resolution issue, since I've seen the following.

In my /var/log/samba, I can see 2 logs for every connecting host: log.$HOSTNAME & log.$IPADDRESS

There seems to be a sort of hand-off between logs that seems to correspond to the aforementioned issues.

In the log.$IPADDRESS I see: (note the 30-minute gap)
```

[2014/09/19 10:04:00.618178,  2] ../source3/auth/auth.c:288(auth_check_ntlm_password)
  check_ntlm_password:  Authentication for user [$USER] -> [$USER] FAILED with error NT_STATUS_NO_SUCH_USER
[2014/09/19 11:46:58.979264,  2] ../source3/smbd/reply.c:592(reply_special)
  netbios connect: name1=DELL_FSERVER   0x20 name2=SN102185       0x0

```

The inverse/complement to the gap shows up in log.$HOSTNAME, leading me to believe that some sort of routing or name-resolution issue could be involved.
You're right, you should only use "security = user" for recent versions of Samba (v3.6 and v4.1).  If you want to have guest access then you need "map to guest = Bad User" all versions of Samba (v3.6 and v4.1).  The parameter "map to guest = Bad User" causes Samba to allow access to a user that is not in the Samba database (smbpasswd -a).  You must define this as the default is map to guest = never"   The guest user is by default defined by this parameter "guest account = nobody".  You don't need to define it in the smb.conf file for it to be used.  In your original post you have defined this correctly.

I think the first error messages are pretty explicit.  The error "FAILED with error NT_STATUS_NO_SUCH_USER" means just that no such user.

The second message is information only.  The netbios name 1 ends in 0x20 which indicates that it is a file server.  The netbios name2 ends in 0x0.  This is the suffix for a workstation (the client).

My suggestion is that you try using a default (for the appropriate version of Samba) smb.conf file and adding only the shares at the bottom.   The latest versions of Samba will work perfectly this way.  If there are problems then we can diagnose them at that time.  Be careful; the default smb.conf file for Samba v3.6 is slightly different than the Samba v4.1 version.

---

### Post by freakalad on 2014-09-20
Thank you for taking the time to help me out with this issue

I've made some of the changes you pointed out, but
> **bab1 said:**
> You must define this as the default is map to guest = never"   The guest user is by default defined by this parameter "guest account = nobody".  
I don't quite understand what you're trying to say here - I think you have some unintended syntax or typo's here that makes the problem difficult to understand.

> **bab1 said:**
> My suggestion is that you try using a default (for the appropriate version of Samba) smb.conf file and adding only the shares at the bottom. The latest versions of Samba will work perfectly this way. If there are problems then we can diagnose them at that time. Be careful; the default smb.conf file for Samba v3.6 is slightly different than the Samba v4.1 version.

This has been my concern too - that there has been a whole lot of cruft collected over the years & versions, but SMB4 borks a bunch of stuff.

I've implemented a number of optimizations on the host that I want to preserve, but a cleaner slate seems a sensible approach.

I'll post my smb.conf here once I've made some changes

---

### Post by bab1 on 2014-09-21
> **freakalad said:**
> Thank you for taking the time to help me out with this issue

I've made some of the changes you pointed out, but I don't quite understand what you're trying to say here - I think you have some unintended syntax or typo's here that makes the problem difficult to understand.
> You must define this as the default is **[COLOR="#0000FF"]"map to guest = never"[/COLOR]** The guest user is by default defined by this parameter "guest account = nobody".  [COLOR="#0000FF"]Edit: I updated the typo error in bold blue above.[/COLOR]

I have just installed Samba v.1 on a Lubuntu 14.04 host and I see that my trusty man page for *smb.conf *is out of date on this issue.  The default parameters are already set as this```

map to guest = Bad User
guest account = nobody

```...this sets up the guest user by default. 
> 
This has been my concern too - that there has been a whole lot of cruft collected over the years & versions, but SMB4 borks a bunch of stuff.

I've implemented a number of optimizations on the host that I want to preserve, but a cleaner slate seems a sensible approach.

I'll post my smb.conf here once I've made some changes
The biggest change I have seen has been the change from Samba v3.6 to Samba v4.1.  I did notice you have a reference to a Samba v2 hack.  That's way out of date.

You don't have to delete your older smb.conf file.  Just rename and copy the default smb.conf file back.  Then see if you need to add back any of the old hacks.  I know that the Samba.org developers have created a completely new rewrite of the *smbd* daemon for Samba v4.  You might find you need no hacks at all.

---

### Post by freakalad on 2014-09-21
I've backed up my old config, pulled a fresh default copy, carried over some of my earlier work, and [referenced this guide]("https://wiki.samba.org/index.php/Public_Samba_Server")

My new smb.conf looks something like this:
```

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = DUMBVANILLAWORKGROUP

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
	wins server = 192.168.0.200

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

	netbios name = DELL_FSERVER
	netbios aliases = fileserver


#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0
#	interfaces = eth0 eth1 br0 lo

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes

#http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting
	hosts deny = ALL
	hosts allow = 192.168.0.0/24 172.16.0.0/16 127.



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 10240

#   syslog only = no
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

   server role = standalone server

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u   
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
;	encrypt passwords = true


# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes



########## Domains ###########
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#
;# - later...


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes



### OTHER COMMON SETTINGS FOR ALL SHARES & CUSTOMIZATION HACKS ###
#https://wiki.samba.org/index.php/Public_Samba_Server

#kill all printing
	load printers = no
	printing = bsd
	printcap name = /dev/null
	printcap cache time = 0
	disable spoolss = yes

#Asynchronous IO tweak
	aio read size = 1
	aio write size = 1
	aio write behind = false # true can cause corruption
#https://wiki.amahi.org/index.php/Make_Samba_Go_Faster - optionally
#	socket options=SO_RCVBUF=131072 SO_SNDBUF=131072 TCP_NODELAY
#	min receivefile size = 16384
#	use sendfile = true
#	aio read size = 16384
#	aio write size = 16384

#kill stale/interrupted connections
	reset on zero vc = yes

#http://oreilly.com/catalog/samba/chapter/book/appb_02.html
	read raw = yes  
	write raw = yes 

	force user = nobody
	force group = nogroup

#/me don't like this rather lax posture - risk is being mitigated elsewhere
	directory mask = 0775
	create mask = 0775
	force directory mode = 0775
	force create mode = 0775

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
	map to guest = bad user
	guest ok = yes
	read only = no
;	guest account = nobody
	

#======================= Share Definitions =======================
#http://oreilly.com/openbook/samba/book/ch05_05.html
#http://oreilly.com/openbook/samba/book/appc_01.html

[documents]
	comment = all documents
	path = /fileserver/docs

[CAD]
	comment = CAD files
	path = /fileserver/CAD
	
#deal with concurrent connections oplock issues
	level2 oplocks = No
	oplocks = False
	veto oplock files = /*.dw*/

[Temp]
	comment = Temporary Files
	path = /fileserver/temp

[Scans]
	comment = Scanned documents  & drawings
	path = /fileserver/docs/SCANS


```


I'll be keeping an eye on it, waiting for things to settle down, but early indications are, via `tail -n5 /var/log/samba/log.*`, that the problem still persist, despite effectively omitting the security portions.

I've kept as close to the original config & I've cautiously applied  info from the wiki, but I think I'm missing something crucial.

Mind taking a look & inform me where I went wrong, please?
(As I may have mentioned before), Samba is not something I mess around with regularly - it's typically something that I simply set&forget & don't touch once it's working, which this box has been doing remarkably well for a very long time - far longer than I would've like to have kept it in use.

---

### Post by freakalad on 2014-09-21
> **bab1 said:**
> 
```

map to guest = Bad User
guest account = nobody

``` 


I think I did have this in my original config, but omitted it for some reason - quite possibly due to bringing my config in line with the Samba wiki guide.

Will update, but doubt it'll make a huge difference.

What gets me is - why is this so intermittent? why now?
If there was an issue with the server, auth, permissions or anything ACL, then I would've expected it to show up & do so persistently & for all users.

But what I'm seeing is that this happens for some users some of the time, and for some more than others - and does not follow a predictable or reproducible script, which makes it exceedingly hard to troubleshoot.

The "FAILED with error NT_STATUS_NO_SUCH_USER" message in the logs, followed by a significant time-gap, is only a very strong correlation to the random disconnects the users are experiencing, and even then not all these "FAILED with error NT_STATUS_NO_SUCH_USER" errors are accompanied with a dropped client.

---

### Post by bab1 on 2014-09-21
> **freakalad said:**
> 

I'll be keeping an eye on it, waiting for things to settle down, but early indications are, via `tail -n5 /var/log/samba/log.*`, that the problem still persist, despite effectively omitting the security portions.

I've kept as close to the original config & I've cautiously applied  info from the wiki, but I think I'm missing something crucial.

Mind taking a look & inform me where I went wrong, please?
(As I may have mentioned before), Samba is not something I mess around with regularly - it's typically something that I simply set&forget & don't touch once it's working, which this box has been doing remarkably well for a very long time - far longer than I would've like to have kept it in use.

Yes I do mind.  I told you what I would start with and you have decided that it would be better to add a lot of variability with all the non-default settings.  Since we are just testing here I would urge you to start with a completely default smb.conf file and add only the settings that are easily verifiable such as```
workgroup = <yourworkgroup>

netbios name = <whatever>

```

Once again, since we are testing, I would advise you to add only global settings to the [global] section and add the share settings to the individual shares.  You have used share parameters in the global section.

After you have set the default smb.conf in place and restarted the *smbd *and *nmbd * daemons```
sudo service smbd restart 
sudo service nmbd restart
```... you can see all the default settings with this command```
testparm -sv
```...this is literally ALL the parameters as they are set by a combination of the internal *smbd* daemon settings and the changes set by the smb.conf.  Some of the parameters you have set are the defaults anyway.  I notice one parameter that is not valid at all.  Have you ever used *testparm* to verify the *smb.conf* file correctness?

Samba is better configured by starting with the defaults and configuring each share individually until everything is brought up to your liking.

---

### Post by freakalad on 2014-09-21
> **bab1 said:**
> Yes I do mind.  I told you what I would start with and you have decided that it would be better to add a lot of variability with all the non-default settings.[/CODE]
Fair enough, but I did need to preserve some of the the AIO & locking tweaks (will set per share where appropriate), as those are variables I've slogged through before to address other (rather serious) issues.

[QUOTE=bab1;13126560]
Since we are just testing here I would urge you to start with a completely default smb.conf file and add only the settings that are easily verifiable such as
```
workgroup = <yourworkgroup>
netbios name = <whatever>

```
roger...

[QUOTE=bab1;13126560]
After you have set the default smb.conf in place and restarted...
you can see all the default settings with this command```
testparm -sv
```...this is literally ALL the parameters as...
I notice one parameter that is not valid at all.  
Have you ever used *testparm* to verify the *smb.conf* file correctness?


Thanks for that. I actually did run the config through `testparam -v` to validate it & got the following result, indicating that it all seems copacetic, but I'll incorporate your above guidance, thanks:
```

# testparm -v /tmp/smb.conf.LGL
Load smb config files from /tmp/smb.conf.LGL
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[documents]"
Processing section "[CAD]"
Processing section "[Temp]"
Processing section "[Scans]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

```

---

