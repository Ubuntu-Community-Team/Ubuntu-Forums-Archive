---
title: "Can't get domain logons working with samba as PDC"
date: 2011-12-28
forum: Server Platforms
---

### Post by ssorj on 2011-12-28
Hello.  I'm having trouble getting samba to work as a PDC.  I've been  following tutorials digging through logs for nearly a week.  I guess it  is time to post for help.  Anyone up for some super-fun troubleshooting? :)

Environment is as follows:
ubuntu server 10.04 LTS, fully upgraded as of this morning running samba 3.4.7
mixed workstations of mostly win7 pro and a few xp pro.  

Failure message is: "The specified network name is no longer available" when attempting to join the domain. 

Some errors from the logs:

[2011/12/28 18:18:16,  2] smbd/uid.c:276(change_to_user)
  change_to_user: SMB user nobody (unix user nobody, vuid 100) not permitted access to share IPC$.
[2011/12/28 18:18:16,  0] smbd/service.c:942(make_connection_snum)
  Can't become connected user!

I am sure I was completely logged out of everything before submitting credentials, so I'm not sure why I'm getting this error or why it is trying to sign on as "nobody".

However, the worst of it is winbind.  From its log, I get:

```

[2011/12/28 18:17:13,  1] lib/server_mutex.c:71(grab_named_mutex)
  Could not get the lock for AUTH
[2011/12/28 18:17:13,  0] winbindd/winbindd_cm.c:782(cm_prepare_connection)
  cm_prepare_connection: mutex grab failed for AUTH
[2011/12/28 18:17:41,  1] winbindd/winbindd_cm.c:977(cm_prepare_connection)
  failed tcon_X with NT_STATUS_LOGON_FAILURE
[2011/12/28 18:17:41,  0] winbindd/winbindd.c:190(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=0)
[2011/12/28 18:17:41,  0] libsmb/namequery.c:75(saf_store)
  saf_store: refusing to store 0 length domain or servername!
[2011/12/28 18:18:16,  1] winbindd/winbindd_cm.c:977(cm_prepare_connection)
  failed tcon_X with NT_STATUS_LOGON_FAILURE
[2011/12/28 18:20:13,  0] libsmb/namequery.c:75(saf_store)
  saf_store: refusing to store 0 length domain or servername!
[2011/12/28 18:20:13,  1] winbindd/winbindd_cm.c:977(cm_prepare_connection)
  failed tcon_X with NT_STATUS_END_OF_FILE
[2011/12/28 18:21:06,  1] lib/util_tdb.c:521(tdb_wrap_log)
  tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 85 ltype=1 (Interrupted system call)
[2011/12/28 18:21:06,  0] lib/util_tdb.c:69(tdb_chainlock_with_timeout_internal)
  tdb_chainlock_with_timeout_internal: alarm (40) timed out for key AUTH in tdb /var/run/samba/mutex.tdb
[2011/12/28 18:21:06,  1] lib/server_mutex.c:71(grab_named_mutex)
  Could not get the lock for AUTH
[2011/12/28 18:21:06,  0] winbindd/winbindd_cm.c:782(cm_prepare_connection)
  cm_prepare_connection: mutex grab failed for AUTH
[2011/12/28 18:22:26,  1] lib/util_tdb.c:521(tdb_wrap_log)
  tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 85 ltype=1 (Interrupted system call)
[2011/12/28 18:22:26,  0] lib/util_tdb.c:69(tdb_chainlock_with_timeout_internal)
  tdb_chainlock_with_timeout_internal: alarm (40) timed out for key AUTH in tdb /var/run/samba/mutex.tdb
[2011/12/28 18:22:26,  1] lib/server_mutex.c:71(grab_named_mutex)
  Could not get the lock for AUTH
[2011/12/28 18:22:26,  0] winbindd/winbindd_cm.c:782(cm_prepare_connection)
  cm_prepare_connection: mutex grab failed for AUTH

```Here is my testparm of /etc/samba/smb.conf
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[profile]"
Processing section "[netlogon]"
Loaded services file OK.
Server role: ROLE_DOMAIN_PDC

```Here is my smb.conf (redacted)
```

[global]
   workgroup = RPS
   netbios name = AUTH
   wins support = yes
   name resolve order = hosts wins bcast
   socket options = SO_KEEPALIVE TCP_NODELAY SO_SNDBUF=8192 SO_RCVBUF=8192
   domain logons = yes
   domain master = yes
   preferred master = yes
   local master = yes
   os level = 33
   security = user
   encrypt passwords = yes
   valid users = @rpsusers
   admin users = @rpsadmins
   add user script = /usr/sbin/useradd %u
   add group script = /usr/sbin/groupadd %g
   add machine script = /usr/sbin/adduser -n -g machines -c Machine -d /dev/nul$
   delete user script = /usr/sbin/userdel %u
   delete user from group script = /usr/sbin/deluser %u %g
   delete group script = /usr/sbin/groupdel %g
   logon path = \\%L\profile\%U
#  logon script = %U.bat
   hide files = /desktop.ini/ntuser.ini/NTUSER.*/Thumbs.db/
   log level = 2
   map to guest = bad user
   template shell = /bin/bash
   template homedir = /home/%D/%U
   idmap uid = 10000-20000
   idmap gid = 10000-20000


[homes]
   comment = Home Directories
   browseable = no
   writeable = yes
   valid users = @rpsusers

[profile]
   comment = Profiles
   path = /home/samba/profile
   guest ok = yes
   browseable = no
   create mask = 0600
   directory mask = 0700
   writeable = yes
   profile acls = yes

[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   guest ok = yes
   writeable = no


```

---

### Post by collisionystm on 2011-12-28
First of all, why are you using winbind? You only need winbind to integrate the system with an existing active directory.

2nd.

You need to set your DHCP or manually conigure your NICS on windows to point their WINS / Netbios resolution to your Ubuntu box. A domain depends on Wins / Netbios.

Oh and 3rd. If you want to save yourself headaches. Try Zentyal.

---

### Post by ssorj on 2011-12-28
Ok. total noob here.  I was browsing through /etc/log/samba and found that.  I never told anything to use winbind.  I would imagine that if it weren't needed and I never specified it to be used that nothing would use it, but the log is there and it is full of errors.  

I can ping both machines by hostname and fqdn.  I can nslookup both machines from eachother.  DNS is provided by a router using DD-WRT and it has always been reliable in the past.  

I'm fairly sure the machines are able to communicate -- I think it is authentication that is the problem and I'm not sure where that problem is...

Also, I'm fairly committed to Ubuntu server as I have 5 others that serve different samba shares and backup networked pcs.  They have all been working fine for a long time.  This is the first time I've ever tried to make one a PDC and I'm stuck.  :(  I'm sure it's me and not Ubuntu.

EDIT:  I forgot to mention that I specified the ubuntu server's ip as the WINS server.  It shows properly in the ipconfig /all from both windows machines.  WINS points in the right direction.  Netbios over TCP/IP is enabled on both the win 7 and xp machines.  The netbios name in smb.conf is the same as the hostname of the ubuntu server.  This is correct, isn't it?

---

### Post by collisionystm on 2011-12-28
Here are some settings from my working PDC that i found different.

 enable privileges = yes
 interfaces = lo,eth0
 bind interfaces only = Yes 

 smb ports = 137 138 139 445
 name resolve order = wins bcast hosts
 os level = 65

---

### Post by collisionystm on 2011-12-28
also, do this.

sudo apt-get install nmap

nmap localhost

post output

---

### Post by ssorj on 2011-12-28
added your suggestions to smb.conf.  Restarted smbd, nmbd, and networking.  Same error when trying to join the domain.  "The specified network name is no longer available".  

NMAP output: 

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-12-28 19:46 CST
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 992 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
53/tcp    open  domain
80/tcp    open  http
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
631/tcp   open  ipp
3306/tcp  open  mysql
10000/tcp open  snet-sensor-mgmt

Nmap done: 1 IP address (1 host up) scanned in 0.33 seconds

Also, while attempting to join the domain, netstat on both windows machines shows me:
TCP     10.6.0.130:49164     auth:microsoft-ds     ESTABLISHED
right up until the error message -- then I see no active connections.  At no point does it show a failure in communication between the two machines which leads me to believe it is a config error on my part on the ubuntu server.  

Success and error messages from the most recent login with the suggested smb.conf changes:

```

[2011/12/28 19:53:14,  2] auth/auth.c:310(check_ntlm_password)
  check_ntlm_password:  authentication for user [kbrown] -> [kbrown] -> [kbrown] succeeded
[2011/12/28 19:53:16,  2] smbd/uid.c:276(change_to_user)
  change_to_user: SMB user nobody (unix user nobody, vuid 100) not permitted access to share IPC$.
[2011/12/28 19:53:16,  0] smbd/service.c:942(make_connection_snum)
  Can't become connected user!
[2011/12/28 19:53:16,  2] smbd/process.c:1979(deadtime_fn)
  Closing idle connection

```
So, I was authenticated as the user kbrown, but somehow it switched to nobody and was rejected as a connected user?  

Then after several log entries about closing an idle connection, these are the last few lines:

```

[2011/12/28 19:55:55,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
[2011/12/28 19:55:55,  0] lib/util_sock.c:743(write_data)
[2011/12/28 19:55:55,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2011/12/28 19:55:55,  0] smbd/process.c:62(srv_send_smb)
  Error writing 98 bytes to client. -1. (Transport endpoint is not connected)

```

---

### Post by collisionystm on 2011-12-28
okay try this smb.conf



[global]
   workgroup = RPS
   netbios name = AUTH
   wins support = yes
   name resolve order = wins bcast hosts
   domain logons = yes
   domain master = yes
   preferred master = yes
   local master = yes
   os level = 65
   security = user
   enable privileges = yes
   interfaces = lo,eth0
   bind interfaces only = Yes 
   smb ports = 137 138 139 445
   encrypt passwords = yes
   add user script = /usr/sbin/useradd %u
   add group script = /usr/sbin/groupadd %g
   add machine script = /usr/sbin/adduser -n -g machines -c Machine -d /dev/nul$
   delete user script = /usr/sbin/userdel %u
   delete user from group script = /usr/sbin/deluser %u %g
   delete group script = /usr/sbin/groupdel %g
   logon path = \\%L\profile\%U
#  logon script = %U.bat
   log level = 2
   map to guest = bad user
   template shell = /bin/bash
   template homedir = /home/%D/%U
   idmap uid = 10000-20000
   idmap gid = 10000-20000


[homes]
   comment = Home Directories
   browseable = no
   read only = No
   writeable = yes
   valid users = %U

[netlogon]
 path = /home/samba/netlogon/
 browseable = No
 read only = yes

[profiles]
 path = /home/samba/profiles
 read only = no
 create mask = 0600
 directory mask = 0700
 browseable = No
 guest ok = Yes
 profile acls = yes
 csc policy = disable
 valid users = %U
 admin users = @rpsadmins
 hide files = /desktop.ini/outlook*.lnk/*Briefcase*/

---

### Post by ssorj on 2011-12-28
No joy.  Copy/paste smb.conf, testparm to ensure no syntax errors, returns good.  Turned off all machines.  Rebooted router.  Brought up the server then the two other machines.  Ping and nslookup all return successfully as expected.  Same error on xp and 7 when trying to join the domain.  Same errors in log.smbd as posted previously.  I can still see the communication with netstat as "ESTABLISHED" right up until it fails.  

Strange, though.  My login to the ubuntu server took about 2 minutes.  Same thing happened when I tried to use sudo from the terminal.  It worked, just took a long time.  A little searching shows that it is likely due to networking issues, but everything else seems to be working fine.  Below are my networking settings...

cat /etc/hosts
```

127.0.0.1    localhost
10.6.1.1        auth

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

cat /etc/resolv.conf
```

nameserver 10.6.0.1
domain dallas.lan
search dallas.lan

```

cat /etc/nsswitch.conf
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal dns mdns4 wins [NOTFOUND=return]
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

---

