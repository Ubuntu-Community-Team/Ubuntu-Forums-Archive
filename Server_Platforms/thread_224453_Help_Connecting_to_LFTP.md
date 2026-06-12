---
title: "Help Connecting to LFTP"
date: 2006-07-28
forum: Server Platforms
---

### Post by stormblue on 2006-07-28
I'm trying to get lftp to work from the command line.  Unfortunately, I'm having some problems.  I can log into the server both through anon and get the public directory and I can login through gFTP through the account I'm trying to log in with. The username is [email]username@domain.com[/email] This is what I've done so far:
```

lftp username@domain.com ftp.domain.com
```

Then I type in the password and I get the prompt and I type ls and then I get this:

```
ls: Login failed: 530 Authentication failed, sorry
```

I then tried 

```
lftp -u username@domain.com ftp.domain.com
```

and then it just stalls when I issue the ls command with 

```
lftp username@domain.com@ftp.domain.com:~> ls
`ls' at 0 [Making data connection...]
```

Any ideas?  I've also tried playing around with passive mode settings, but to no avail.

Thanks

---

### Post by stormblue on 2006-07-28
Here's the output from the ls command with the debug switch:

```
---- Connecting to ftp.domain.com (xxx.xxx.xxx.xxx) port 21
<--- 220---------- Welcome to Pure-FTPd [TLS] ----------
<--- 220-You are user number 9 of 50 allowed.
<--- 220-Local time is now 10:54. Server port: 21.
<--- 220 You will be disconnected after 15 minutes of inactivity.
---> FEAT
<--- 211-Extensions supported:
<---  EPRT
<---  IDLE
<---  MDTM
<---  SIZE
<---  REST STREAM
<---  MLST type*;size*;sizd*;modify*;UNIX.mode*;UNIX.uid*;UNIX.gid*;unique*;
<---  MLSD
<---  ESTP
<---  PASV
<---  EPSV
<---  SPSV
<---  ESTA
<---  AUTH TLS
<---  PBSZ
<---  PROT
<--- 211 End.
---> AUTH TLS
<--- 234 AUTH TLS OK.
---> OPTS MLST type;size;modify;UNIX.mode;UNIX.uid;UNIX.gid;
Certificate: C=US,ST=Unknown,L=Unknown,O=Unknown,OU=Unknown,CN=superresellerza12347.servermatrix.host,EMAIL=ssl@cpanel.net
 Issued by: C=US,ST=Unknown,L=Unknown,O=Unknown,OU=Unknown,CN=superresellerza12347.servermatrix.host,EMAIL=ssl@cpanel.net
WARNING: Certificate verification: Not trusted
WARNING: Certificate verification: The certificate's owner does not match hostname 'ftp.domain.com'

<--- 530 You aren't logged in
---> USER username
<--- 331 User username OK. Password required
---> PASS password
<--- 230-User username has group access to:  group
<--- 230 OK. Current restricted directory is /
---> PWD
<--- 257 "/" is your current location
---> PBSZ 0
<--- 200 PBSZ=0
---> PROT P
<--- 534 Fallback to [C]
---> PASV
<--- 227 Entering Passive Mode (xxx,xxxx,xxx,xxx,7,197)
---- Connecting data socket to (xxx.xxx.xxx.xxx) port 1989
`ls' at 0 [Making data connection...]
```

this is where it hangs and the output from the debug switch

---

### Post by stormblue on 2006-07-31
For anyone that finds this later the fix includes the following on the server side for a pureFTP connect:

1. Force passive mode on server
2. Open specific ports in server firewall

---

