---
title: "[SOLVED] Can I connect via SSH to windows share?"
date: 2008-07-31
forum: Server Platforms
---

### Post by G1ZmO65 on 2008-07-31
Another newbie question lol

I have an SSH server running at home on Ubuntu 8.04 server and also have a Win2003Server running there.

I'm logged in to the ubuntu server via puTTY

Can I connect from there to a shared folder on the Windows box? (I know the login and pass)

Thanks

Paul

---

### Post by Dr Small on 2008-07-31
Yes, as long as you have SMBclient installed. You could do something like:
```
smbclient "\\\\ipaddress\\share name"
```

---

### Post by G1ZmO65 on 2008-07-31
Ah nice one!

I've managed to get onto the windows server and copy a file to the ubuntu server.

Is there any way I can copy it onto my local desktop? (at work)

---

### Post by MJN on 2008-07-31
A few ways...
 
My recommended suggestion, if you can install applications on your work PC, is to take advantage of your existing SSH service and use SFTP. A nice is client is [WinSCP]("http://winscp.net/eng/index.php") (ignore the naming discrepencies - it supports both SFTP and SCP) and you can even run a standalone executable if a full-blown installation is not acceptable.
 
There are many other ways besides, but I'd suggest going with this as a starter for ten as you'll be up-and-running in no time - it works out of the box.
 
Mathew
 
P.S. Putty also has an SFTP command-line client.... it is very short on features, particular if (unfairly) compared with a GUI client, but it might still be of interest.

---

### Post by G1ZmO65 on 2008-07-31
Spot on! 

Got the file on my work pc now :)

Not figured out yet how to use that program to get onto the Windows server directly but I'll keep trying

Thanks Matthew

Paul

---

### Post by G1ZmO65 on 2008-08-04
Just on this..

I'm connected to my remote win2003 server but am trying to search a folder for files created recently.

I saw from another thread that someone suggested the FIND command for this but it doesnt appear to be part of the 8.04 Server system.

How do I list files created after a certain date with LS? and/or install the FIND command?

Thanks

Paul

---

### Post by G1ZmO65 on 2008-08-04
also...

Can I map a network drive in the CLI so that I can then connect via WinSCP and view the files on the Win Server?

---

### Post by hyper_ch on 2008-08-04
you could install cygwin on the windows server as it also has a ssh server. You coudl then directly connect to it.

---

### Post by c2olen on 2008-08-04
> **G1ZmO65 said:**
> also...

Can I map a network drive in the CLI so that I can then connect via WinSCP and view the files on the Win Server?


Besides CYGWIN you can make a static mount from your ubuntu server to the windows share you performed yourself earlier. Then, through the ssh connection you could browse that mountpoint like any other filesystem.

Note:you say find isn't available on your ubuntu setup. That's really hard to believe. It is part of the base linux packages so it should most definately be on your box.

---

### Post by G1ZmO65 on 2008-08-04
Excuse my ignorance "Static mount"? I assume from that that I can do something that will make the smbclient link permanent? But how?

btw I've realised that its when I'm in the smbclient that the find command isnt there.

Thanks

Paul

---

### Post by c2olen on 2008-08-04
> **G1ZmO65 said:**
>  I assume from that that I can do something that will make the smbclient link permanent? But how?


You can put the smbmount options in the systems /etc/fstab. This file holds the partitions or network drives which are defined as mountpoints. Mostly, the entries in this file are mounted automatically, but you can also choose to mount them manually.

For starters, see 'man fstab' for documentation.

The quickstart is like this;
Add the following line to you /etc/fstab file, while subsituting servername and sharenames to mach your configuration.

```
//server/share /mnt/sambashare smbfs user,credentials=/etc/samba/cred-file,uid=your_userid,gid=users 0 0
```

Then fill the file /etc/samba/cred-file with your credentials like this.

```
username = <value>
password = <value> 

```
Now you should have the network share mounted at boot-time.
If you put noauto, in front of user, then the network mount is not done automatically, and you can mount it as a regular user (because of the user option).

---

### Post by G1ZmO65 on 2008-08-04
Ok I logged in as root and edited the fstab file and the cred-file then rebooted the server but unfortunately the server hasnt come up again lol

Need to have a look at it when I get home :)

Thanks for the help though, I'll try tonight

Cheers

Paul

---

### Post by c2olen on 2008-08-04
> **G1ZmO65 said:**
> Ok I logged in as root and edited the fstab file and the cred-file then rebooted the server but unfortunately the server hasnt come up again lol


Lesson learned: Never just reboot after making changes, test them first if possible.
This could have been tested simply by doing
```
mount /mnt/sambashare (or whatever your configuration was)
```

You would then have received an errormessage, which now probably sits on your console at home :-)

But don't worry, i've had these situations myself plenty of times. 
I once was logged in through VPN/ssh to my box at home, and ran a apt-get upgrade. Never checked what packages would be upgraded and completely missed the openvpn packages..... Yup, stopping openvpn was the last thing i saw, then connection dead....

---

### Post by G1ZmO65 on 2008-08-05
OK when I got home I found that my Samba server was not running and maybe that was because I used /mnt/sambashare

Here is my fstab now:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d26147e8-a6d0-4ccc-9732-5217a7d374ba /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d45b995a-a6cc-48c7-8bf3-c20447dc803f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//2003server/backup2 /mnt/2k3backup2 smbfs user,credentials=/etc/samba/cred-file,uid=paul,gid=users 0 0
```

And here is the error when I try to mount the folder:
```
paul@ubuntu:~$ mount /mnt/2k3backup2
mount error: could not find target server. TCP name 2003server/backup2 not found
No ip address specified and hostname not found
```

---

### Post by c2olen on 2008-08-05
> **G1ZmO65 said:**
> OK when I got home I found that my Samba server was not running and maybe that was because I used /mnt/sambashare
I don't think your samba server was not running due to this mountpoint. This mountpoint was to be used by the smbclient, and not the server. You should check your samba logfiles in /var/log/ to determine the error. Feel free to attach it to a post in this thread for us to help analyzing.


> **G1ZmO65 said:**
> mount error: could not find target server. TCP name 2003server/backup2 not found
No ip address specified and hostname not found

It appears that your linux host does not know how to find 2003server, because it neither in your available DNS, or in the hostfile /etc/hosts. You can do two things,

1. Put in the IP address instead of the hostname in your fstab,
or
2. Add the line ```
2003server    dotted.ip.address.here
``` to your /etc/hosts file.

---

### Post by G1ZmO65 on 2008-08-05
I'm not sure which logfile in /var/log/ is required.

Heres a snapshop of the logfiles with yesterdays date.

btw I can still connect to the server with 
```

smbclient \\\\2003server\backup2
```

---

### Post by G1ZmO65 on 2008-08-05
btw i am also getting these errors so I'm assuming there something wrong with my network settings somewhere.

```
paul@ubuntu:~$ sudo apt-get install tracert
sudo: unable to resolve host ubuntu
[sudo] password for paul:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

---

### Post by c2olen on 2008-08-05
nmbd and smbd are the samba daemons, so check these logfiles. Also I see a logfile with your 2003servers name. This might also be a good place to look.

---

### Post by c2olen on 2008-08-05
> **G1ZmO65 said:**
> btw i am also getting these errors so I'm assuming there something wrong with my network settings somewhere.

```
paul@ubuntu:~$ sudo apt-get install tracert
sudo: unable to resolve host ubuntu
[sudo] password for paul:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```


You seem to be unable to even resolve your localhost.
What does your /etc/hosts file look like?
Also show me you /etc/nsswitch.conf and /etc/resolv.conf files please.

---

### Post by G1ZmO65 on 2008-08-05
Hosts:

```
127.0.0.1 localhost
127.0.1.1	Ubuntu.Gizmonet

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

log.smbd```

[2008/08/03 07:39:33, 0] param/loadparm.c:map_parameter(2794)
  Unknown parameter encountered: "revalidate"
[2008/08/03 07:39:33, 0] param/loadparm.c:lp_do_parameter(3535)
  Ignoring unknown parameter "revalidate"
[2008/08/03 10:08:14, 0] lib/util_sock.c:get_peer_addr(1224)
  getpeername failed. Error was Transport endpoint is not connected
[2008/08/03 10:08:14, 0] lib/util_sock.c:get_peer_addr(1224)
  getpeername failed. Error was Transport endpoint is not connected
[2008/08/03 22:00:13, 0] lib/util_sock.c:get_peer_addr(1224)
  getpeername failed. Error was Transport endpoint is not connected
[2008/08/04 17:38:39, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/08/04 17:38:39, 0] param/loadparm.c:map_parameter(2794)
  Unknown parameter encountered: "revalidate"
[2008/08/04 17:38:39, 0] param/loadparm.c:lp_do_parameter(3535)
  Ignoring unknown parameter "revalidate"
[2008/08/04 22:53:07, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/08/04 22:53:07, 0] param/loadparm.c:map_parameter(2794)
  Unknown parameter encountered: "revalidate"
[2008/08/04 22:53:07, 0] param/loadparm.c:lp_do_parameter(3535)
  Ignoring unknown parameter "revalidate"
```

log.nmbd
```
[2008/08/04 17:38:39, 0] nmbd/nmbd.c:main(711)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/08/04 17:59:47, 0] nmbd/nmbd.c:terminate(58)
  Got SIGTERM: going down...
[2008/08/04 22:53:07, 0] nmbd/nmbd.c:main(711)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
```

log.2003server:
```

[2008/08/04 14:40:11, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/08/04 14:40:11, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2008/08/04 14:46:35, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/08/04 14:46:35, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2008/08/04 14:46:35, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/08/04 14:46:35, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
```

---

### Post by c2olen on 2008-08-05
Did you make sure you have no other package managers active, which lock-up your package manager database? Hence the lock error?

Change the second line in your host file to match this.
```
127.0.1.1	ubuntu Ubuntu.Gizmonet
```

You can mount your windows share from the command line you said, so the hostname resolve should work then (you have a dns entry with 2003server somewhere or you use the netbios name instead).
Your samba logs show nothin out of the ordinary here.

Then try the ip address in the fstab file instead of the hostname. 

Of course, only go through al this trouble if you really want to have your samba share mounted all of the time. Perhaps, only mounting it when needed is a better and safer option.

---

### Post by G1ZmO65 on 2008-08-05
> **c2olen said:**
> Did you make sure you have no other package managers active, which lock-up your package manager database? Hence the lock error?

Can I check this remotely?

> **c2olen said:**
> 
Change the second line in your host file to match this.
```
127.0.1.1	ubuntu Ubuntu.Gizmonet
```

Done that.

---

### Post by G1ZmO65 on 2008-08-05
ok my fstab now reads:
```
//192.168.1.3/backup2 /mnt/2k3backup2 smbfs user,credentials=/etc/samba/cred-file,uid=paul,gid=users 0 0
```

But I get:
```
root@ubuntu:/etc# mount /mnt/2k3backup2
mount error: can not change directory into mount target /mnt/2k3backup2
```

(same when I log in with user "paul" btw)

btw thanks for all the time you're taking over this!

Paul

---

### Post by c2olen on 2008-08-05
> **G1ZmO65 said:**
> root@ubuntu:/etc# mount /mnt/2k3backup2
mount error: can not change directory into mount target /mnt/2k3backup2

This is progress though. 
Does the directory /mnt/2k3backup2 exist?
Are you sure it isn't used for another (previous) samba or other mount?
You can use 'mount' or 'df' to see what is mounted.

> **G1ZmO65 said:**
> 
btw thanks for all the time you're taking over this!
Paul

Your welcome, always glad I can help and welcome new people to the community.

---

### Post by G1ZmO65 on 2008-08-05
> **c2olen said:**
> 
Does the directory /mnt/2k3backup2 exist?
Are you sure it isn't used for another (previous) samba or other mount?
You can use 'mount' or 'df' to see what is mounted.


ummm no the directory 2k3backup2 doesnt exist. Maybe I misunderstood the process. I thought this was a name I was giving to the alias of \\2003server\backup2 ?

---

### Post by G1ZmO65 on 2008-08-05
OK set fstab to:
```
//2003server/backup2 /mnt/sambashare smbfs user,credentials=/etc/samba/cred-file,uid=paul,gid=users 0 0
```

but get:
```
root@ubuntu:/etc# mount /mnt sambashare
mount: mount point sambashare does not exist
```

---

### Post by c2olen on 2008-08-05
No no, I definately wasn't clear enough on that.
Under normal circumstances before you can mount a filesystem or a network share, a local mountpoint needs to exist.  This means the path you wish to mount a filesystem or share on, needs to exist.

An example;
Let's assume we've made a whole new filesystem on a free partition or disk.
I'd like to mount this new filesystem (or network share) on /mnt/newfilesystem.

```

sudo mkdir /mnt/newfilesystem
mount /dev/sdb1 /mnt/newfilesystem

```

When you use installers or GUI's to create a new filesystem, a mountpoint could (sometimes) be created automatically.  In your case it isn't created automatically, so you need to do it yourselve.

```

sudo mkdir /mnt/sambashare
mount /mnt/sambashare

```

You need to change the path and sharename to match your wishes though.

---

### Post by G1ZmO65 on 2008-08-05
Does it have to be called sambashare?

reason I ask is that I might do it for some other shared folders on my windows boxes and would like to make it clear which machine the folder links to

eg 
shared resource //2003server/backup2 id like to name 2k3backup2
shared resource //2003server/docs id like to name 2k3docs 

etc

---

### Post by c2olen on 2008-08-05
> **G1ZmO65 said:**
> Does it have to be called sambashare?

no, see the end in my previous

> **c2olen said:**
> You need to change the path and sharename to match your wishes though.

---

### Post by G1ZmO65 on 2008-08-05
Gah!

Heres the line from the fstab:
```

//2003server/backup2 /mnt/2k3backup2 smbfs user,credentials=/etc/samba/cred-file,uid=paul,gid=users 0 0
```

But:
```
paul@ubuntu:~$ cd /mnt
paul@ubuntu:/mnt$ ls
2k3backup2  2k3docs
paul@ubuntu:/mnt$ sudo mount /mnt /2k3backup2
[sudo] password for paul:
mount: mount point /2k3backup2 does not exist

```

---

### Post by c2olen on 2008-08-05
> **G1ZmO65 said:**
> 
paul@ubuntu:/mnt$ sudo mount /mnt /2k3backup2
[sudo] password for paul:
mount: mount point /2k3backup2 does not exist


No spaces between /mnt and /2k3backup2.

The command you enteres actually means you are trying to mount /mnt onto /2k3backup2 as if /mnt was a device.

The command should be;
```
mount /mnt/2k3backup2
```

The sudo part is not really required, because you have the "user" option added in the fstab. Without it, sudo would be required. It doesn't hurt though.

---

### Post by G1ZmO65 on 2008-08-05
```
paul@ubuntu:/mnt$ sudo mount /mnt/2k3backup2
mount error: could not find target server. TCP name 2003server/backup2 not found
No ip address specified and hostname not found
paul@ubuntu:/mnt$ sudo vim /etc/fstab
```
[changed fstab line to //192.168.1.3/backup2 etc]

```
paul@ubuntu:/mnt$ sudo mount /mnt/2k3backup2
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

Tried without the sudo:```

paul@ubuntu:/mnt$ mount /mnt/2k3backup2
mount error: permission denied or not superuser and mount.cifs not installed SUID
```

It's frustrating not knowing what I'm doing lol

---

### Post by c2olen on 2008-08-05
> **G1ZmO65 said:**
> 
paul@ubuntu:/mnt$ sudo mount /mnt/2k3backup2
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)


So, is this a local (to linux) permission, or does your Windows box deny access??
That's what needs to checked. My understanding of errorcodes is not extensive enough to clearly state the cause of this errorcode, but have you made sure there are no spaces in your credentials file? This is somethimes the case and causes permissions problems.


> **G1ZmO65 said:**
> It's frustrating not knowing what I'm doing lol


You'll learn about this as you use your linux longer. This is something many of us struggle with at first. So did I, and many times I still do.

---

### Post by G1ZmO65 on 2008-08-05
the creds for the win2k3 server and the linux box are the same for my username (deliberately)

I've checked the /etc/samba/cred-file and the details are correct

username = paul
password = xxxxxx

should this have spaces or not?

If I don't specify the cred-file in fstab will I be asked for it?

---

### Post by c2olen on 2008-08-05
> **G1ZmO65 said:**
> the creds for the win2k3 server and the linux box are the same for my username (deliberately)

I've checked the /etc/samba/cred-file and the details are correct

username = paul
password = xxxxxx

should this have spaces or not?

If I don't specify the cred-file in fstab will I be asked for it?


No spaces!!

And you can try to see if you're asked for credentials, but my guess is NO. Just another access denied message.

---

### Post by G1ZmO65 on 2008-08-05
YAY!!! :)

Well done c2olen!

the mount (sudo mount /mnt/2k3backup2) worked and I can now see the files from the backup2 folder with WinSCP

many thanks for all your assistance c2olen

Think I've learned a thing or two also in the process :) :)

Cheers

Paul

btw I'm now going to document it for myself for reference!

---

### Post by c2olen on 2008-08-05
Glad I could help,
but you did most of the work yourself, I just pointed you in the right direction, so you too did a good job. 
Maybe you can remove one of the o's in looooooooong now :-D

---

### Post by G1ZmO65 on 2008-08-05
Sorry, another question on this :)

Now I can mount the network share \\2003server\backup2
how do I enter \\2003server\documents backup into fstab?

I've tried \\2003server\documents backup and \\2003server\"documents backup" but it keeps saying that the line in fstab is bad.

(need to avoid having spaces in folder names in future)

---

### Post by Dr Small on 2008-08-05
Try:
```
"\\2003server\documents backup"
```

---

### Post by G1ZmO65 on 2008-08-05
This is the fsatb line: (still says its bad though)
```
"//192.168.1.3/documents backup" /mnt/2k3docsbackup smbfs user,credentials=/etc/samba/cred-file,uid=paul,gid=users 0 0
```

I have tried:
//192.168.1.3/"documents backup" /mnt/2k3docsbackup .......
"//192.168.1.3/documents backup" /mnt/2k3docsbackup .......
'//192.168.1.3/documents backup' /mnt/2k3docsbackup .......

---

### Post by c2olen on 2008-08-05
Ok,

skip the " (quotes) and "escape the space".
In Unix, one can escape a character in order to make it litteraly.

Using a space in a mountpoint path would device it into two separate values.
When you escape it, like "\ " (the quotes are just to indicate beginning and end of example) the space is no longer interpreted as a value separator, but as a part of the first value.

```

//server/share\ name    /mnt/mount\ point    smbfs  and_so_on......

```Quotes are somewhat ignored in the fstab.

good luck

---

### Post by G1ZmO65 on 2008-08-05
hmm OK started again with this one:
The win2003 server folder is called "Test Folder" (put in a space deliberately)

The mount point is called 2k3test

```
paul@ubuntu:~$ sudo mkdir /mnt/2k3test
paul@ubuntu:~$ sudo vim /etc/fstab
[IN FSTAB] //192.168.1.3/Test\ Folder /mnt/2k3test smbfs user,credentials=/etc/samba/cred-file,uid=paul,gid=users 0 0
paul@ubuntu:~$ mount /mnt/2k3test
[mntent]: line 14 in /etc/fstab is bad
mount: can't find /mnt/2k3test in /etc/fstab or /etc/mtab
```

I know I can just rename the windows shares but I'll not always have the option of doing that so might as well find out how it can be done eh? :P

Oh btw, how do I get it to recognise the //2003server instead of having to put in the IP address?

Thanks

Paul

---

### Post by G1ZmO65 on 2008-08-05
Found on one of the other threads that you need to replace the space with \040 (the escape sequence for space)

Fstab:
```
//192.168.1.3/Test\040Folder /mnt/2k3test smbfs user,credentials=/etc/samba/cred-file,uid=paul,gid=users 0 0
```

which gave:
```
paul@ubuntu:~$ sudo mount /mnt/2k3test
mount error 11 = Resource temporarily unavailable
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

At least it's trying to mount it now!

---

### Post by c2olen on 2008-08-06
> **G1ZmO65 said:**
> 
Oh btw, how do I get it to recognise the //2003server instead of having to put in the IP address?

If you have a DNS server set up, you could add it there, but my guess is you don't have a DNS server. Then the next best thing is to put it in the host file.
Unix will look at DNS and hostfiles in a specific order. This order is determined in the file /etc/nsswitch.conf. By default it is first hostfile, then DNS (other methods can be added).

So, add your Windows host's IP address to /etc/hosts (below the two localhost lines).
```

dotted.ip.address.here [tab] hostname [tab] alias_for_this_host (add more if desired)

```

---

### Post by G1ZmO65 on 2008-08-06
Thanks again c2olen,

That works a treat.

btw 2k3test is mounting today also so it seems to be sorted by adding the \040 instead of a space :)

wow I got that bit myself! :)

Paul

---

### Post by c2olen on 2008-08-06
Good job. You can now remove another o.. :-D

It's addicting, isn't it?

---

### Post by c2olen on 2008-08-06
PS:

You might wanna mark this thread solved if you have no further questions in this matter.

Cheers.

---

### Post by andyfromtucson on 2008-08-06
Maybe I am missing something, but I think you should be able to just use bitVise Tunnelier installed on your Windows machine at work to SSH tunnel into your Ubuntu box and then directly map a drive on your work Windows box to your Windows 2003 server. No need to mount your Windows 2003 server on your Ubuntu box.

---

### Post by G1ZmO65 on 2008-08-07
I installed bitVise Tunnelier but cant see a way of doing what you suggested with it. :confused:

Paul

---

