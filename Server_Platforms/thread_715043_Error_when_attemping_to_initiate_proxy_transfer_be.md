---
title: "Error when attemping to initiate proxy transfer between two servers"
date: 2008-03-04
forum: Server Platforms
---

### Post by rockfx01 on 2008-03-04
Hello,

I am having a bit of a problem here with vsftpd which is over my head.

I have two servers set up, one is our server running the vsftpd service. The second server is a proprietary server running some form of linux/unix, but it's a proprietary box and I don't have any real control over it.

I am trying to synchronize between the two servers and have attempted using multiple different FTP clients to do so, to no avail.  Finally I tried doing it via command-line using the proxy FTP command, but that also did not work.  I can copy files from our server, running vsftpd and I can copy files to the other server(unknown service, allows anonymous login), but I cannot initiate a passive connection between the two it seems.  I am hoping someone might be able to help.

Here is a condensed version of my vsftpd.conf file:

```
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
#anon_upload_enable=YES
#anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
#chown_uploads=YES
#chown_username=whoever
#xferlog_file=/var/log/vsftpd.log
xferlog_std_format=YES
#idle_session_timeout=600
#data_connection_timeout=120
#nopriv_user=ftpsecure
async_abor_enable=YES #I enabled this b/c I thought it might help but it didn't.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#ftpd_banner=Welcome...
#banned_email_file=[file]
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
#ls_recurse_enable=YES
pam_service_name=vsftpd
userlist_enable=YES
userlist_deny=NO
listen=YES
tcp_wrappers=YES
```

Then in the command line from a third system (Ubuntu 7.10), I tried FTP'ing into the main server (x.x.x.1) and do a proxy transfer to the secondary server, (x.x.x.222).  Am I doing something wrong?

```
user@host:~$ ftp x.x.x.1
Connected to x.x.x.1.
220 (vsFTPd 2.0.1)
Name (172.16.0.1:user): ftpuser
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> cd Files
250 Directory successfully changed.
ftp> cd for.transfer
250 Directory successfully changed.
ftp> proxy open x.x.x.222
Connected to x.x.x.222.
220 
Name (x.x.x.222:user): anonymous
331 User name anonymous, need password
Password:
230 User anonymous logged in. There are currently 1 users.
Remote system type is Omneon.
ftp> proxy put "My File V0.mov" /fs0/backup
local: My File V0.mov remote: /fs0/backup
x.x.x.222:227 Entering Passive Mode (x,x,x,222,5,95)
x.x.x.1:500 Illegal PORT command.
ftp>
```

](*,)

If anyone is able to help, I would greatly appreciate it! 

Thanks!

---

### Post by faulkes on 2008-03-04
If either of the hosts is behind a firewall/router which does NAT, that is likely the cause
of your error when trying to use PASV (passive mode).

On the vsftpd side, you can configure it to explicitly return to the client the known
outside IP address of the firewall/router.  That may or may not solve the problem if
the issue is the remote end.  See the vsftpd.conf man page for information regarding
this.

The issue surrounds how the server returns what it thinks is it's IP address and what
the firewall/router originally gave to the client.  When that mismatch happens, PASV
breaks.

Faulkes

---

### Post by rockfx01 on 2008-03-04
faulkes, thank you for your help.

I did find that it was related to PASV, although I do not understand entirely why.

All of the computers are on the same internal network and at no point do they pass through a router of any sort.  The x.x.x.1 server acts as a DHCP server and file server, and the x.x.x.222 server is the one I am trying to push files to.  Then I have a third client with a dynamic IP, x.x.x.y, from which I am trying to initiate the proxy transfers.

After a bit of research I did find that adding the line:
```
pasv_promiscuous=YES
```
to the vsftpd.conf file on our server now allows the transfer to work one direction.  I.E.:

If I FTP into x.x.x.222 and then do a "proxy open" of the x.x.x.1 server, I can enter "proxy binary" mode and then perform "proxy put/get" operations.

I have not been able to make it work the other way; however, and I believe this may be causing problems with some proprietary synchronization software supplied to us by the vendor of the other server.  Unfortunately we need to get this specific software working (if possible) and using a different application to perform the file synchronization is not an option.


Is there anything else I can do to make the proxy transfer work the opposite direction? (i.e. "ftp x.x.x.1" and then "proxy open x.x.x.222")  I tried adding the following lines to the vsftpd.conf file as well, but they did not do any good.
```
dirlist_enable=YES
download_enable=YES
```

Thank you again for the help!

---

### Post by faulkes on 2008-03-04
It is something which has to be in effect on both servers IIRC.

So if you have a proprietary vendor solution on one side, I would say you're next
step would be to contact the vendor regarding it.  

Unfortunately it's a bit one sided here as I don't know the other server, 
so I can't offer any specifics on what may or may not work.

Faulkes

---

### Post by rockfx01 on 2008-03-04
The other server is running some custom linux/unix kernel and I have no root access to the box to change anything, so there's no reason to bother with it unfortunately.

I have been talking to them about the issues we have been having and perhaps they will have a solution, although nothing has been accomplished as of yet.  Hopefully I will not have ripped out all of my hair by the end of this week.

Thanks again for the help. Getting proxy transfers at least partially working is one small step in the right direction.

Cheers!

---

