---
title: "[SOLVED] automount samba in /etc/fstab"
date: 2007-07-26
forum: Server Platforms
---

### Post by a_posse_ad_esse on 2007-07-26
Hey all, just a quick and probably simple fstab configuration question:

I am trying to automount samba shares (nfs is too insecure in this case) in order to do automatic backups of local machines.  I get a "SMB connection failed" error with the following configuration:

```

//192.168.2.5:/share /share smbfs username=xxx,password=xxx,auto,user,rw 0 0

```

I am able to access the appropriate folders in konqueror, so permissions and the server itself is configured correctly.  Any suggestions?  Thanks.

---

### Post by Koybe on 2007-07-26
Maybe you do not have smbfs package instaled.
```
sudo apt-get install smbfs
```

And you should not put the ":" after the ip.

---

### Post by a_posse_ad_esse on 2007-07-26
Reconfiguring fstab and removing the ":" after the IP yields

```

5727: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

```

when I try to mount the share.  

Smbfs is installed as well.

Any suggestions?  Thanks.

---

### Post by Koybe on 2007-07-26
Try using the name instead of the IP.

Here's what i have :
```
//server/public /mnt/public smbfs rw,codepage=cp850,iocharset=utf8,credentials=/etc/samba/user 0 1
```

---

### Post by a_posse_ad_esse on 2007-07-26
I get the same results.  I wonder if this is a larger configuration issue?

Here are my relevant configs:

/etc/hosts
```

192.168.2.5     server

```

/etc/fstab
```

//server:/share /share smbfs username=xxx,password=xxx,auto,user,rw 0 0

```

The resulting mount attempt yields

```

6707: Connection to server: failed
SMB connection failed

```

The same is true with the IP defined.  I am not sure why it wants the colon after the IP or hostname, but it doesn't recognize it as a valid share without it.

---

### Post by Koybe on 2007-07-27
I don't get it.

What if you type 
```
sudo mount -t smbfs -o username=xxx,rw //server:/share /share
```And then
```
sudo mount -t smbfs -o username=xxx,rw //server/share /share
```and
```
sudo mount -t smbfs -o username=xxx,rw //192.168.2.5:/share /share
```and 
```
sudo mount -t smbfs -o username=xxx,rw //192.168.2.5/share /share
```Give us all outputs so we can see the difference.


Could you indicate you samba configuration too? 
```
testparm
```

---

### Post by arsenic23 on 2007-07-27
Ok, I think I remember someone telling me that mounting things with smbfs was not the best way to do this.  Something about smbfs not being maintained or some such thing.  I was told, and have had much better luck mounting things using cifs.  I've also never heard of adding anything other then source, destination, and username/password.  Here's a sample of what works for me.

```
//192.168.1.101/t       /home/ending/DL cifs    username=******,password=******
```

---

### Post by Koybe on 2007-07-27
cifs is for Windows 2003 shares as far as I know?

---

### Post by arsenic23 on 2007-07-27
> **Koybe said:**
> cifs is for Windows 2003 shares as far as I know?

Has worked for me with XP, 2000, and Vista shares.

------
In fact I've only ever been able to get proper write suport with my shared XP folders using cifs.

---

### Post by a_posse_ad_esse on 2007-07-27
```

sudo mount -t smbfs -o username=xxx,password=xxx,rw //server:/share /share
6306: Connection to server: failed
SMB connection failed

```

```

sudo mount -t smbfs -o username=xxx,password=xxx.rw //server/share /share
6313: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

```

```

sudo mount -t smbfs -o username=xxx,password=xxx,rw //192.168.2.5:/share /share
6333: Connection to 192.168.2.5: failed
SMB connection failed

```

```

sudo mount -t smbfs -o username=xxx,password=xxx,rw //192.168.2.5/share /share
6339: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

```

server testparm
```

testparmLoad smb config files from /etc/samba/smb.conf
(bla bla bla)
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

```


As for cifs, I am connecting to my home ubuntu server.  I would use nfs, but it is not secure enough for what I am trying to accomplish.  Plus, I would like to be able to allow guests to view recorded shows, etc, on their laptops when they come over.  We don't have any Windows machines in our household anymore, thank goodness, but there are others who are less fortunate...

---

### Post by arsenic23 on 2007-07-27
Sorry for the misunderstanding, I was reading several things at once and got confused as to what your problem was.

---

### Post by a_posse_ad_esse on 2007-07-27
Hey, aren't we all? :-P

I appreciate your efforts in trying to solve this.  There isn't any need to apologize.

---

### Post by Koybe on 2007-07-27
What I would like about testparm is the dump coming after the 'enter' it asks you ;) (or post your smb.conf)

And excuse me for asking again but do you got smbfs installed?
```
dpkg -l smbfs
```

---

### Post by a_posse_ad_esse on 2007-07-27
```

dpkg -l smbfs
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                          Version                       Description
+++-=============================-=============================-==========================================================================
ii  smbfs                         3.0.24-2ubuntu1.2             mount and umount commands for the smbfs (for kernels >= than 2.2.x)

```

Here is my smb.conf:

```

[global]
	workgroup = Server
	server string =	Server
	netbios name = Server
#	smb ports = 139
	log level = 2
	invalid users = root
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0
	encrypt passwords = true
	socket options = TCP_NODELAY
	dns proxy = no
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
	username map = /etc/samba/usermap.txt
	unix extensions = yes
	security = user
        wins support = yes
        preferred master = yes

[printers]
	comment = All printers
	path = /var/spool/samba
	printable = yes
	guest ok = yes
	browsable = no

[shared]
	comment = Tim & Kristen's shared folder
	browseable = no
	writable = yes
	create mask = 0777
	directory mask = 0777
	path = /shared
	public = no
	valid users = tim,kristen
	guest ok = no

[Tim's folder]
	comment = Tim's files
	browseable = no
	writable = yes
	create mask = 0777
	directory mask = 0777
	path = /home/tim
	public = no
	valid users = tim
	guest ok = no

[Kristen's folder]
	comment = Kristen's files
	browseable = no
	writable = yes
	create mask = 0777
	directory mask = 0777
	path = /home/kristen
	public = no
	valid users = kristen
	guest ok = no

[Public files]
	comment = Public files
	browseable = yes
	writable = no
	create mask = 0755
	directory mask = 0755
	path = /public
	public = yes

[Public media]
	comment = Public media folder
	browseable = yes
	writable = no
	create mask = 0755
 	directory mask = 0755
	path = /storage
	public = yes

```

---

### Post by Koybe on 2007-07-27
You try to mount a share named 'share' and there is non in your config file. There is one named 'shared'. Are you usere you are using the right name?

Also it's better not having space in share names.

So what if you do this :
```
sudo mount -t smbfs -o username=xxx,password=xxx,rw //server/shared /share
```

---

### Post by a_posse_ad_esse on 2007-07-28
Ah, sorry to confuse.  I was just using a generic version of the mount because I have been playing with the configuration as my ideas have been evolving about what I want to accomplish.  I've made sure that the shares are mountable, etc, through konqueror and the like.

Here is what I have ATM:

/etc/fstab
```

//server:/shared/backups /backups smbfs username=bla,password=bla,auto,user 0 0

```

and mounting:
```

mount /backups
7215: Connection to server: failed
SMB connection failed

```

---

### Post by h3lmut on 2007-07-28
> **a_posse_ad_esse said:**
> 
```

//server**:**/shared/backups /backups smbfs username=bla,password=bla,auto,user 0 0

```

That colon shouldn't be there.

---

### Post by Koybe on 2007-07-28
I still think as h3lmut, no colon.
And I'm not sure you can mount a directory in a share.
```
//server/shared /backups smbfs username=bla,password=bla,auto,user 0 0

```

To mount all your fstab you can also use
```
sudo mount -a
```

---

### Post by a_posse_ad_esse on 2007-07-29
I wonder if the server is blocking my client somehow.  Maybe the "ERRnosuchshare" error is due to a door being slammed shut.  I can mount using konqueror as I've said, but this could be due to the program being more pushy than I can be on the command line a single command at a time.  I wonder if there is something wrong with the server's smb.conf?

---

### Post by Koybe on 2007-07-29
To me, preferred master is not needed. And I would avoid space in share names as I already told before. But well, everything else just look ok.
Another think : I wouldn't give execute permission to files. This is not needed.

But these are speculation, it shouldn't block you from accessing your samba shares.

---

### Post by a_posse_ad_esse on 2007-07-30
I suppose that since we are against a wall in this case, and, after doing some thinking, I have concluded that maybe my best option would be using nfs.  My only concern with this is security...   Is there a "best" way to secure it?

My scenario would be as such:

The network will be consisting of 2 laptops (which are used for taking notes at my grad classes and for my wife to take notes at her teaching block, etc... essentially meaning that they are on non-native networks a lot) and a workstation.  I was thinking that I would simply have a symlink from the /home directory to /backups, which would be mounted on the server when the machine would be on our home network.  However, a problem that arises with the laptops in this scenario, should I understand the workings of symlinks correctly, is that materials that are updated while on a non-native network would not necessarily update when remounted on the server.  We could certainly just have a usbstick forever plugged into the back of the machines, but then we would have to upload the newer file to the server, which would then reflect onto the workstation, etc, etc.  

As always, having the process done automagically is better.  Does anyone have any ideas about how to do this?

---

### Post by droopy1129 on 2007-07-30
Don't give up so fast... Try using an fstab line like this:

//server/share  /mountpoint       smbfs rw,user,noauto,username=XXX,password=XXX,umask=0777,fmask=0777               0  0

and adding:
 mount /mountpoint 
to your /etc/rc.local file

this is what works for my systems

---

### Post by a_posse_ad_esse on 2007-07-30
Hmm...  no good.

By the way, using the "auto" option would do the same thing I believe.

---

### Post by droopy1129 on 2007-07-30
No go huh?  Sorry man.  Did you use the smbpasswd command on the server to create the samba account?  I had a bunch of problems with samba when I started using linux too.  Also, another thing to try would be to setting security to "share" in the smb.conf file and see if that works.

BTW, I had some problems using the "auto" option.  My mounted drives would no longer connect and I couldn't reboot without my system hanging.  Just a heads up in case this happens to anyone else... changing it to "noauto" and adding the entries to rc.local fixed the problem.

---

### Post by a_posse_ad_esse on 2007-07-31
I appreciate the input.  I suppose I am getting vexed because I have been using Linux exclusively for about 5 years now, yet am being thwarted by a simple matter of mounting a network share :-P.  The nature of the beast I suppose.

Does anyone know if the updated material would update on the server upon re-mounting in the nfs scenario that I put forth before?  I did some looking, and restricting nfs root access, IP range, etc, would be almost as good as samba.

Thanks

---

### Post by chele on 2007-07-31
What happens if "smbfs" is replaced with "cifs" in the fstab line?

---

### Post by a_posse_ad_esse on 2007-08-01
The server in question is a linux samba server.

---

### Post by a_posse_ad_esse on 2007-08-05
I removed and re-installed smbfs after this last update, and now the mounts are working fine.  How or why it works I don't know, but this is the final working result:

```

//192.168.2.5/shared /shared smbfs username=xxx,password=xxx,auto,user 0 0

```

Thank you all for your input.

---

### Post by Mongo5000 on 2007-11-18
I almost got it, but can't get write permission.

I can browse the files, but no write access unless I use sudo.

Im using a mybook world edition and confused as to the .credentials information.

My NAS doesn't require authentication to access it or even write to it.

What am I doing wrong?

---

