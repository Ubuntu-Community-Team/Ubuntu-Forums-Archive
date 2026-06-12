---
title: "samba PDC problems"
date: 2007-11-27
forum: Server Platforms
---

### Post by cdenley on 2007-11-27
I'm having some problems with my samba PDC. When the client machines running Windows XP boot up, they can't login until after about a minute. It gives me an error saying the domain is not available. It uses a static IP, and it receives replies from the PDC, but it still says it is not available. There doesn't seem to be any network packets sent or received immediately before I can suddenly log in, but there is an hour glass for a split second on the client. There is nothing logged on the server until after the user succesfully logs in.

The other problem I have is that it occasionally seems to take unusually long to make a connection to the server. Sometimes, it takes longer than usual to log in. Sometimes, when browsing a network share, explorer will hang on the client.

Here are some messages in the samba logs which may be relevant:

log.winbindd
```

[2007/11/27 11:35:41, 0] libsmb/clientgen.c:cli_receive_smb(112)
  Receiving SMB: Server stopped responding
[2007/11/27 11:40:51, 0] libsmb/clientgen.c:cli_receive_smb(112)
  Receiving SMB: Server stopped responding
[2007/11/27 11:41:04, 0] libsmb/clientgen.c:cli_receive_smb(112)
  Receiving SMB: Server stopped responding
[2007/11/27 11:41:17, 0] libsmb/clientgen.c:cli_receive_smb(112)
  Receiving SMB: Server stopped responding

```

log.winbindd-idmap
```

[2007/11/27 11:43:30, 1] nsswitch/idmap_tdb.c:idmap_tdb_alloc_init(397)
  idmap uid range missing or invalid
  idmap will be unable to map foreign SIDs
[2007/11/27 11:43:30, 0] nsswitch/idmap.c:idmap_alloc_init(735)
  ERROR: Initialization failed for alloc backend, deferred!

```

log.client
```

[2007/11/27 11:08:50, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2007/11/27 11:08:50, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users

```

log.winbindd-dc-connect
```

[2007/11/07 16:57:08, 0] libsmb/nmblib.c:send_udp(791)
  Packet send failed to 192.168.1.255(137) ERRNO=Operation not permitted
[2007/11/07 17:01:38, 0] libsmb/nmblib.c:send_udp(791)
  Packet send failed to 192.168.1.255(137) ERRNO=Operation not permitted
[2007/11/07 17:02:09, 0] libsmb/nmblib.c:send_udp(791)
  Packet send failed to 192.168.1.255(137) ERRNO=Operation not permitted

```

log.nmbd
```

[2007/11/27 11:21:12, 0] libsmb/nmblib.c:send_udp(791)
  Packet send failed to 192.168.0.102(138) ERRNO=Operation not permitted
[2007/11/27 11:39:00, 0] libsmb/nmblib.c:send_udp(791)
  Packet send failed to 192.168.0.27(138) ERRNO=Operation not permitted

```

I used to get this in log.smbd before I firewalled TCP 445, but these problems exist with or without this port blocked.
```

[2007/11/26 07:47:26, 0] lib/util_sock.c:get_peer_addr(1232)
  getpeername failed. Error was Transport endpoint is not connected
[2007/11/26 07:47:26, 0] lib/util_sock.c:get_peer_addr(1232)
  getpeername failed. Error was Transport endpoint is not connected

```

Here is my smb.conf:
```

[global]
   netbios name = ubuntu
   store dos attributes = yes
   hide files = /desktop.ini/Desktop.ini/Thumbs.db/
   workgroup = MYPDC
   server string = %h server (Samba, Ubuntu)
   wins support = no
   dns proxy = no
   smb ports = 139
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = no
   domain logons = yes
   logon path = \\%N\profiles\%U
   logon drive = H:
   logon home = \\%N\%U
   logon script = logon.cmd
   add machine script = /usr/sbin/useradd -g machines -d /dev/null -s /bin/false %u
   socket options = TCP_NODELAY
   domain master = auto

#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = no
   valid users = %S
   writable = yes
   create mask = 0600
   directory mask = 0700

[netlogon]
   comment = Network Logon Service
   path = /samba/netlogon/%G
   guest ok = yes
   writable = yes
   browseable = no
   share modes = no

[profiles]
   comment = Users profiles
   path = /samba/profiles
   guest ok = no
   browseable = yes
   create mask = 0600
   directory mask = 0700
   writable = yes
   valid users = @ntusers @ntadmins
   csc policy = disable

###...more shares...###

```

---

### Post by roxlw on 2007-11-29
> The other problem I have is that it occasionally seems to take unusually long to make a connection to the server. Sometimes, it takes longer than usual to log in. Sometimes, when browsing a network share, explorer will hang on the client.

I have the exact same problem and have been banging my head against the wall trying to figure it out.  You probably got the same google search results I did--the same exact message list through 5,000 different URLs.  *sigh*

I'll be sure to post an update if I figure anything out.

---

### Post by cdenley on 2007-11-29
I think I figured out the login delay, where it would tell me the domain is unavailable. When I ran "pdbedit -Lv cdenley", I saw my user (the one I join the domain as) had the old domain name in the password database. I changed the domain name a long time ago, when I was still setting it up. I also noticed the old domain name was logged in netlogon.log several times after I enabled logging for it. I removed my samba user ("pdbedit -u cdenley -x"), re-created it ("smbpasswd -a cdenley"), re-joined the domain from the client, and I now seem to be able to login right away. I'm not sure if this fixed the occasional hang, but I haven't noticed any problems so far.

---

### Post by roxlw on 2007-11-29
Hmm, I think you're onto something.  I changed my workgroup name a while back.  I just checked pdbedit, and sure enough, the old workgroup name was in there.

UPDATE:

Unfortunately, I keep getting the "Receiving SMB: Server stopped responding" error.

UPDATE 2:

I can't figure out what I did, but I don't seem to get the "Receiving SMB: Server stopped responding" error anymore.  It might have something to do with the fact that I stopped the smbd/winbind daemons and "sudo rm -rf /var/lib/samba/*" to delete all of samba's info, then restarted the daemons.  Of course, this deletes samba's user/password database, so make backups.  Either way, I still get some of the other errors, so the battle isn't over.  What is interesting, though, is that even when I start from scratch, I get the "Failed to create Administrators/Users" errors.  I was scouring the internet and I found a tip from Michael Gasch -- "i guess it's "net sam createbuiltin" (requires winbindd running)" see: [http://lists.samba.org/archive/samba/2006-August/124261.html](http://lists.samba.org/archive/samba/2006-August/124261.html).  When I try this, I get:

```
$ sudo net sam createbuiltingroup Administrators
Creating Administrators failed with NT_STATUS_ACCESS_DENIED

$ sudo net sam createbuiltingroup Users
Creating Users failed with NT_STATUS_ACCESS_DENIED
```

So...who knows.  Good luck.

---

### Post by cdenley on 2007-12-10
My problem suddenly came back (login delay), so I don't seem to have fixed anything. When the problem goes away for a week for no reason, it is very difficult to troubleshoot. I'll try "sudo rm -rf /var/lib/samba/*" later. I think I made the error about creating builtin users go away by adding this to smb.conf.

```

winbind enum users = yes
winbind enum groups = yes

```

I think I read that it was disabled by default because it caused performance issues in large networks, though. I figured out that explorer hanging on the client machines corresponds to the "Receiving SMB: Server stopped responding" errors in log.winbindd. I guess the problem is with smbd hanging, but I don't know why.

UPDATE:

I tried "rm -rf /var/lib/samba/*", but it does not seem to help. If I turn off "domain logons", the problem goes away, but I need the domain functionality. I've tried changing all the options in smb.conf and switching to the smbpasswd backend.

---

### Post by cdenley on 2007-12-12
This seems to be a problem with any samba PDC, unless I'm doing something wrong. I did
```

sudo /etc/init.d/samba stop && sudo /etc/init.d/winbind stop
sudo rm -rf /var/cache/samba/*
sudo rm -rf /var/lib/samba/*
sudo /etc/init.d/samba start && sudo /etc/init.d/winbind start

```

I tried on two machines, AMD64 and x86. I tried changing all the relevant options I could find. I used the [smb.conf example]("http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html#fast-engoffice-global") in the official samba howto for a working PDC word-for-word. I disconnected the network cable, and the error still appeared about every five minutes. I changed to the hardy repository and upgraded samba. I did a fresh install of debian sid, installed samba and replaced smb.conf. I installed the experimental pre-release of samba 3.2. No matter what I do, this problem doesn't seem to go away. Is this a samba bug? Does anyone have a samba PDC that doesn't hang every five minutes?

I know this error in log.winbindd must be related to this problem, because explorer will hang on a client trying to browse a network drive 10 seconds before the error first appears, or until the errors stop. The errors usually happen three at a time, 10-15 seconds apart. I think this means that smbd hangs for about 30-40 seconds about every 5 minutes.

I think I also determined the pattern in not being allowed to log in to the domain. If I start the client, log myself in, then restart, I can log myself back in immediately, but anyone else will get the domain is not available error for about a minute. When someone logs out, anyone can log in immediately. I'm not sure if this problem is related, and I'm more concerned about the hangs.

---

### Post by freebeer on 2007-12-12
> **cdenley said:**
>  Does anyone have a samba PDC that doesn't hang every five minutes?


Mine seems stable... I've only had it up for ~2 weeks and I have less that 10 users, FWIW.  Are you using roaming profiles by any chance?  I had to turn that off as the network traffic was huge during login and log-off.  If you have profiles on, maybe the rush of data transfers is hanging the server? *shrugs*

---

### Post by cdenley on 2007-12-13
I am using roaming profiles, but that can't be the problem since it seems to hang without a network or a client. I prevented my profiles from getting too big by redirecting "My Documents" and their desktop to samba shares. I also changed the location of their outlook profile if they had a lot in there.

Are you running dapper? I set up a samba server running dapper yesterday, and there weren't any errors logged in log.winbindd last night. Now I will have to do some testing to  verify the problem does not exists in samba 3.0.22, then test to see if a downgrade will work in gutsy.

---

### Post by roxlw on 2008-01-09
> [2007/11/27 11:08:50, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2007/11/27 11:08:50, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users

I fixed this error by fixing my groupmaps.

See: [http://support.microsoft.com/kb/243330](http://support.microsoft.com/kb/243330)

The way my groupmapping was, I only set the rid=544/rid=545 for Administrators/Users.  This resulted in a long SID, when it appears that Users and Administrators are builtin groups with constant SIDs.  To fix this, I manually set the SIDs for the groupmapping and set the type to builtin.  I haven't seen the errors come back yet.

```
sudo net groupmap add sid=S-1-5-32-544 unixgroup=admin type=builtin ntgroup=Administrators
sudo net groupmap add sid=S-1-5-32-545 unixgroup=users type=builtin ntgroup=Users
```

Now, I am in the process of tackling these errors:

```
Jan  9 17:21:42 <host> winbindd[18622]: [2008/01/09 17:21:42, 0] nsswitch/idmap.c:idmap_init(687)
Jan  9 17:21:42 <host> winbindd[18622]:   ERROR: Initialization failed for alloc backend tdb, deferred!
Jan  9 17:21:42 <host> winbindd[18616]: [2008/01/09 17:21:42, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
Jan  9 17:21:42 <host> winbindd[18616]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend
Jan  9 17:21:42 <host> winbindd[18616]: [2008/01/09 17:21:42, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
Jan  9 17:21:42 <host> winbindd[18616]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend
Jan  9 17:21:42 <host> winbindd[18616]: [2008/01/09 17:21:42, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
Jan  9 17:21:42 <host> winbindd[18616]:   Possible deadlock: Trying to lookup SID S-1-5-11 with passdb backend
```

UPDATE: Well, the above errors were fixed by mapping more groups.  When I did the groupmapping, I specified the SIDs, but did not specify the "type".  I haven't seen any of the above errors return since the original timestamp of this post.

---

### Post by raphha on 2008-01-17
> **roxlw said:**
> 
Now, I am in the process of tackling these errors:

Jan  9 17:21:42 <host> winbindd[18616]: [2008/01/09 17:21:42, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
Jan  9 17:21:42 <host> winbindd[18616]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend

UPDATE: Well, the above errors were fixed by mapping more groups.  When I did the groupmapping, I specified the SIDs, but did not specify the "type".  I haven't seen any of the above errors return since the original timestamp of this post.

Hello,
first thank you for sharing your findings, it fixed the "Failed to create Users" stuff for me. But I had no luck with the above quoted "Possible deadlock" thing - did you fix this on your machine? If yes, did you also just add the SID group mappings and with which type setting?

Thank you and kind regards,
Raph

---

### Post by doudz on 2008-04-09
Hi !

I have the same problem with winbind
I always get "Receiving SMB: Server stopped responding" when samba run as PDC and the network "freeze" every 4 or 5 minutes.

To fix that, I stop the winbindd daemon and it works good but it's not a solution I think?

Do you have fixed the problem?

---

