---
title: "trying to mount a nfs share from ubuntu onto windows 7"
date: 2011-02-12
forum: Server Platforms
---

### Post by slimjim1520 on 2011-02-12
I have a ubuntu server version 10.04 running a nfs server share. Im trying to mount this share on a windows 7 ultimate 64bit. The nfs client is installed and i can mount the drive however once its mounted it shows up in my computer but when i click it it hangs and then times out. 

This same share is mounted and viewed on an ubuntu desktop. so it works fine there.

Ive used another computer with windows 7 enterprise 32bit with the nfs client installed and it does the exact same thing.

The contents of my exports file
```

/storage/primary *(rw,async,no_root_squash,no_subtree_check,insecure)
/storage/secondary *(rw,async,no_root_squash,no_subtree_check,insecure)
/storage/files *(rw,async,no_root_squash,no_subtree_check,insecure)
/storage *(rw,async,no_root_squash,no_subtree_check,insecure)

```my mount command is the following
```

mount storage-1-ibm.XXXXXX.com:/storage Z:
``````
mount \\storage-1-ibm.xxxx.com\storage Z:
```ive even tried by IP... any suggestions.....btw all firewalls are turned off

Solution

> 
SOLVED!!!!!!!!!!!!!!!!!!!!

You were right it was a permission problem

No matter what I did the uid the mount in windows would use the uid=-2 and gid=-2

I changed the anon user _ON THE WINDOWS SIDE_ 

[LIST]
[*][FONT=Trebuchet MS]Start Registry Editor[/FONT]
[*][FONT=trebuchet ms,geneva]Locate ***HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ClientForNFS  \CurrentVersion\Default ***[/FONT]
[*][FONT=trebuchet ms,geneva]Create two DWORD values namely ***AnonymousUid ***and ***AnonymousGid***[/FONT]
[*][FONT=trebuchet ms,geneva]Set these values to the UID and GID you would like this NFS client to use[/FONT]
[*][FONT=trebuchet ms,geneva]Restart your Client for NFS service using the Microsoft Services for NFS MMC snap-in[/FONT]
[/LIST]
taken from [http://blogs.msdn.com/b/sfu/archive/...ows-vista.aspx]("http://blogs.msdn.com/b/sfu/archive/2009/03/27/can-i-set-up-user-name-mapping-in-windows-vista.aspx")

i then set the AnonymousUid and AnonymousGid to 0 for root. and BOOM it instantly worked.


---

### Post by Jose Catre-Vandis on 2011-02-12
Honestly its too much like hard work, and flaky.

Use samba instead

---

### Post by slimjim1520 on 2011-02-12
samba is not an option the virutalization software Im using requires nfs

---

### Post by elico on 2011-02-12
i have tried using nfs share on windows vista and 7 and both had and still has this specific problem.
the only was i got it to work is to use other software then the client comes with windows 7 and vista.
also dont ever use the * on nfs unless it's a very secure environment.

---

### Post by slimjim1520 on 2011-02-12
> **elico said:**
> i have tried using nfs share on windows vista and 7 and both had and still has this specific problem.
the only was i got it to work is to use other software then the client comes with windows 7 and vista.
also dont ever use the * on nfs unless it's a very secure environment.

is there a specific client you would recommend?

I would still perfer to use the windows client so if anyone has any other suggestions that would be splendid.
 
we will not put restriction on until the kinks are worked out. Till then this is a private network :KS

---

### Post by Jose Catre-Vandis on 2011-02-12
> **slimjim1520 said:**
> samba is not an option the virutalization software Im using requires nfs


More details then would be useful. You didn't mention virtual machines in your first post...

This might help?

[http://sagehacks.wordpress.com/2009/01/21/howto-mount-nfs-shares-under-windows-7/](http://sagehacks.wordpress.com/2009/01/21/howto-mount-nfs-shares-under-windows-7/)
and
[http://technet.microsoft.com/en-us/library/bb463214.aspx](http://technet.microsoft.com/en-us/library/bb463214.aspx)

---

### Post by slimjim1520 on 2011-02-12
> **Jose Catre-Vandis said:**
> More details then would be useful. You didn't mention virtual machines in your first post...

This might help?

[http://sagehacks.wordpress.com/2009/01/21/howto-mount-nfs-shares-under-windows-7/](http://sagehacks.wordpress.com/2009/01/21/howto-mount-nfs-shares-under-windows-7/)
and
[http://technet.microsoft.com/en-us/library/bb463214.aspx](http://technet.microsoft.com/en-us/library/bb463214.aspx)

The fact that there will be virtual machines are irrelevant since they are not the ones connecting directly to the nfs server the machines are physical. 

Thanks for the posts but i already looked at those posts. They bring me to the same point. thanks for

---

### Post by elico on 2011-02-13
did you tried to just use unc for nfs?
like \\server-ip\nfs_share
??
your settings is no root...
if it hangs 
for the sake of trying it again i tried now again and:
in the exports file i added this
/home/vm 192.168.10.100(async,anonuid=0,insecure,all_squash,anongid=0,rw,no_subtree_check)
and it work fine... as root user..
and also there are files there that doesn't work for root as for group \owner settings.
but i mounted the directory using 
mount \\192.168.10.1\home\vm R:

and i got drive r working just perfectly.

---

### Post by slimjim1520 on 2011-02-13
> **elico said:**
> did you tried to just use unc for nfs?
like \\server-ip\nfs_share
??
your settings is no root...
if it hangs 
for the sake of trying it again i tried now again and:
in the exports file i added this
/home/vm 192.168.10.100(async,anonuid=0,insecure,all_squash,anongid=0,rw,no_subtree_check)
and it work fine... as root user..
and also there are files there that doesn't work for root as for group \owner settings.
but i mounted the directory using 
mount \\192.168.10.1\home\vm R:

and i got drive r working just perfectly.

I added this to the exports
```

/storage *(async,anonuid=0,insecure,all_squash,anongid=0,rw,no_subtree_check)
```It does the same thing. When mounted it mounts but i open the drive and it comes up with the following message

```
R:\ is not accessible.

The semaphore timeout period has expired.
```

Mount Command

```
mount \\storage-1-ibm.XXXX.com\storage R:
```

ive even done by IP

---

### Post by elico on 2011-02-13
do an ls -l  /storage
on the server.

if you do want to try other thing and it help only to see one problem and that is:
use [http://j-ftp.sourceforge.net/](http://j-ftp.sourceforge.net/)
it's cifs\nfs\ftp client based on java and it must show you the directory.
it asks for user name and password for the share.

i think it's permissions settings on the server.

---

### Post by slimjim1520 on 2011-02-13
> **elico said:**
> do an ls -l  /storage
on the server.

if you do want to try other thing and it help only to see one problem and that is:
use [http://j-ftp.sourceforge.net/](http://j-ftp.sourceforge.net/)
it's cifs\nfs\ftp client based on java and it must show you the directory.
it asks for user name and password for the share.

i think it's permissions settings on the server.

```

slimjim1520@Storage-1-IBM:/$ ls -l /storage
total 28
drwxrwxrwx 5 root root  4096 2011-02-08 21:52 files
drwx------ 2 root root 16384 2011-02-06 17:06 lost+found
drwxr-xr-x 2 root root  4096 2011-02-11 21:34 primary
drwxrwxrwx 5 root root  4096 2011-02-07 14:34 secondary

```

is the results for that command

---

### Post by elico on 2011-02-14
did you tired with the j-FTP ?
it looks like or firewall problem on one of the machine\network problem.
or it can be users mapping between the windows machine and the nfs server.
try to use the command 
[FONT=courier new]**rpcinfo -p SERVER IP**
to get some information about the rpc connectivity.
also use the command
[/FONT][FONT=courier new]**showmount -e SERVER IP**
to get the list of mounts your computer can identify using the rpc.

also try to use the next  line to mount :
**mount -o casesensitive=yes -u:root -p: password server-ip:/storage r:** (no space between the ":" to the password)

and after you mounted the drive dont do anything just enter the command
**mount**
to get the list of the settings used with the nfs.

[/FONT]

---

### Post by slimjim1520 on 2011-02-14
I just now got Mac OS to mount using the following mount command.

```
mount -o nolock storage-1-ibm.xxxxx.com:/storage/files
```

Once i mounted this i was able to upload files and change things

---

### Post by slimjim1520 on 2011-02-14
> **elico said:**
> did you tired with the j-FTP ?
it looks like or firewall problem on one of the machine\network problem.
or it can be users mapping between the windows machine and the nfs server.
try to use the command 
[FONT=courier new]**rpcinfo -p SERVER IP**
to get some information about the rpc connectivity.
also use the command
[/FONT][FONT=courier new]**showmount -e SERVER IP**
to get the list of mounts your computer can identify using the rpc.

also try to use the next  line to mount :
**mount -o casesensitive=yes -u:root -p: password server-ip:/storage r:** (no space between the ":" to the password)

and after you mounted the drive dont do anything just enter the command
**mount**
to get the list of the settings used with the nfs.

[/FONT]

j-FTP ---- no not yet

```
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  58519  status
    100024    1   tcp  58005  status
    100021    1   udp  58126  nlockmgr
    100021    3   udp  58126  nlockmgr
    100021    4   udp  58126  nlockmgr
    100021    1   tcp  60209  nlockmgr
    100021    3   tcp  60209  nlockmgr
    100021    4   tcp  60209  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100227    2   tcp   2049
    100227    3   tcp   2049
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100227    2   udp   2049
    100227    3   udp   2049
    100005    1   udp  46257  mountd
    100005    1   tcp  57534  mountd
    100005    2   udp  46257  mountd
    100005    2   tcp  57534  mountd
    100005    3   udp  46257  mountd
    100005    3   tcp  57534  mountd

```

```
slimjim1520@Storage-1-IBM:~$ showmount -e 127.0.0.1
Export list for 127.0.0.1:
/storage           *
/storage/files     *
/storage/secondary *
/storage/primary   *

```

firewall is on accept all so it cant be firewall.

---

### Post by slimjim1520 on 2011-02-14
```
C:\Users\Administrator>mount

Local    Remote                                 Properties
-------------------------------------------------------------------------------
r:       \\192.168.0.29\storage                 UID=-2, GID=-2
                                                rsize=32768, wsize=32768
                                                mount=soft, timeout=20.0
                                                retry=1, locking=yes
                                                fileaccess=755, lang=ANSI
                                                casesensitive=no
                                                sec=sys

C:\Users\Administrator>
```

is the results of the mount command

---

### Post by slimjim1520 on 2011-02-14
SOLVED!!!!!!!!!!!!!!!!!!!!

You were right it was a permission problem

No matter what I did the uid the mount in windows would use the uid=-2 and gid=-2

I changed the anon user _ON THE WINDOWS SIDE_ 

[LIST]
[*][FONT=Trebuchet MS]Start Registry Editor[/FONT]
[*][FONT=trebuchet ms,geneva]Locate ***HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ClientForNFS\CurrentVersion\Default ***[/FONT]
[*][FONT=trebuchet ms,geneva]Create two DWORD values namely ***AnonymousUid ***and ***AnonymousGid***[/FONT]
[*][FONT=trebuchet ms,geneva]Set these values to the UID and GID you would like this NFS client to use[/FONT]
[*][FONT=trebuchet ms,geneva]Restart your Client for NFS service using the Microsoft Services for NFS MMC snap-in[/FONT]
[/LIST]
taken from [http://blogs.msdn.com/b/sfu/archive/2009/03/27/can-i-set-up-user-name-mapping-in-windows-vista.aspx](http://blogs.msdn.com/b/sfu/archive/2009/03/27/can-i-set-up-user-name-mapping-in-windows-vista.aspx)

i then set the AnonymousUid and AnonymousGid to 0 for root. and BOOM it instantly worked.

---

### Post by elico on 2011-02-14
im so happy cause this one of shortest posts on the same subject.
almost all the post was informative to solve the case.

---

### Post by slimjim1520 on 2011-02-14
> **elico said:**
> im so happy cause this one of shortest posts on the same subject.
almost all the post was informative to solve the case.
Well i hope this helps people in the future cause boy that was hell.

---

