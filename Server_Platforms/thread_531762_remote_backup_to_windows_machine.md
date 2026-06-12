---
title: "remote backup to windows machine"
date: 2007-08-21
forum: Server Platforms
---

### Post by md5hash on 2007-08-21
how can i auto backup a directory to a windows machinne?

---

### Post by James79 on 2007-08-21
You will need to mount a folder from the windows drive on your ubuntu system. Then schedule the archiving to run every day.

Create a folder on your windows machine to house the archive, and share it. Make it accessible from your linux system like this:

```

sudo mkdir /mnt/mountpoint
sudo mount -t cifs -o username=xxx,password=xxx  //windows_ip/sharename /mnt/mountpoint

```

The username/password is a valid account on the windows drive. 

Create a cron job to archive a directory every morning at 6am. Be careful when editing the crontab! Add the following line to /etc/crontab :

```

 0 6    * * *   root    tar czvf /mnt/mountpoint/archive.tar.gz /directory_to_archive

```

Restart cron so that the changes will take effect:

```

sudo /etc/init.d/cron restart

```

Hope that is clear!

---

### Post by Viruk on 2007-08-22
Do you have to manually mount the windows location after any restart? Are the user details stored anywhere?

How would you edit the cron job to use the time/date of the backup as part of the archive filename?

---

### Post by James79 on 2007-08-22
> **Viruk said:**
> Do you have to manually mount the windows location after any restart? Are the user details stored anywhere?


Automounting is done by placing a command in the /etc/fstab file. I put the user details in a seperate file readable only by root to prevent others from being able to open it. Here's how I accomplished both:

I created a text file called /etc/credentials.windows. In there, I wrote:

```
username=xxxx
password=xxxx
```

Change that file's permissions to be readable only by root:

```

chmod 600 /etc/credentials.windows
sudo chown root /etc/credentials.windows

```

Before editing fstab, try mounting the directory manually to see if everything is working correctly:

```

sudo mount -t cifs -o credentials=/etc/credentials.windows //windows_ip/sharename /mnt/mountpoint
ls /mnt/mountpoint

```

If everything went well, you should see the contents of your shared windows folder. Once you are confident that everything works well, add it to fstab to be auto-mounted on startup. Add this to /etc/fstab:

```

 //windows_ip/sharename		/mnt/mountpoint	cifs	credentials=/etc/credentials.windows,mand	0	0

```



> **Viruk said:**
> 
How would you edit the cron job to use the time/date of the backup as part of the archive filename?


You can edit the tar command as follows to insert the date into the filename:

```
tar czvf /mnt/mountpoint/archive.`date +%F`.tar.gz /directory_to_archive
```


Be careful when editing any of these important files, always create backups beforehand!

---

### Post by Viruk on 2007-08-22
Thanks very much for a detailed response,  I'll have a go at this shortly :)

---

### Post by HermanAB on 2007-08-22
Over a LAN, the backup is best driven from Linux, by sharing a Windows directory.  The Windows File and Printer sharing daemon is called 'server'.  If it screws up, then you can restart it from a DOS box with 'net stop server' and 'net start server' without rebooting Windows.

Over the internet, it is best done by installing Cygwin and OpenSSH on Windows.  Install the SSH server to start automatically at boot-up.  Then you can treat the Windows machine the same as a Linux machine, but for the somewhat strage directory structure.  So then you can use 'rsync' over 'ssh' as with any other Unix machine.  I have found that with a setup like this, the Windows GUI can be crashed and the SSH daemon still works perfectly, so this is very reliable and secure, since the link is protected with strong encryption.

Hope that helps!

Herman

---

### Post by Viruk on 2007-10-26
It has taken me a while to get round to looking at this but I am now running into a problem...

I have set up the Windows share and I can do:
```
sudo mkdir /mnt/mountpoint
sudo mount -t cifs -o username=xxx,password=xxx  //windows_ip/sharename /mnt/mountpoint
```
When I do 
```
ls /mnt/mountpoint 
```
I can see the 2 test files I put there. 

So far so good...

I then create the file containing the credentials - I called my file details at first so did:
```
chmod 600 /etc/details 
chown root /etc/details 
```

Then when i try:
```
mount -t cifs -o credentials=/etc/details //[windows IP]/[share name] /mnt/mountpoint 
```

I get the following error:
```
root@SCwiki:~# mount -t cifs -o credentials=/etc/details //[windows IP]/[share name] /mnt/mountpoint
mount: wrong fs type, bad option, bad superblock on //[windows IP]/[share name],
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Then the output from dmesg | tail is:
```
root@SCwiki:~# dmesg | tail
[42949387.010000] cdrom: open failed.
[42949387.490000] kjournald starting.  Commit interval 5 seconds
[42949387.490000] EXT3 FS on hda5, internal journal
[42949387.490000] EXT3-fs: mounted filesystem with ordered data mode.
[42949390.380000] NET: Registered protocol family 10
[42949390.380000] lo: Disabled Privacy Extensions
[42949390.380000] IPv6 over IPv4 tunneling driver
[42949400.960000] eth0: no IPv6 routers present
[42949541.680000]  CIFS VFS: No username specified
[42949541.680000]  CIFS VFS: cifs_mount failed w/return code = -22
```


I then tried with the name credentials.windows instead of details but got the same error. I also tried changing the contents of the file to read:
username=xxx,password=xxx
Instead of 
username=xxx
password=xxx

And yes I am using real details not just xxx in case someone asks :lolflag:

Again I got the same error. Can anyone give me a push in the right direction?

One other question, what do I need to do to allow writing to the NTFS drive on the Windows 2003 server? 
I am using a standard Ubuntu 6.06.1 server install and I haven't manually installed SAMBA or similar.

---

### Post by HermanAB on 2007-10-26
Actually, I have found that the most reliable way to backup Windows machines is to install Cygwin and OpenSSH, then backup using rsync over SSH as is the usual method for Linux machines.

I have seen Windows machines crashed and unusable, then SSH still works, so I can log in through the net and restart it from SSH!

Cheers,

Herman

---

### Post by MJN on 2007-10-26
I thought I felt a sense of deju vu for a second thnen, but then I saw post #6! ;)

Mathew

---

### Post by James79 on 2007-11-05
Sorry I'm late. I've been away :)


> **Viruk said:**
> 
Again I got the same error. Can anyone give me a push in the right direction?


I believe[ this person]("http://ubuntuforums.org/showthread.php?t=79612") had a similar issue and found a solution to it.



> **Viruk said:**
> 
One other question, what do I need to do to allow writing to the NTFS drive on the Windows 2003 server? 


Ensure that the user you created on your windows machines has the permissions to write to your directory, and that the share itself permits writting. By default, if possible, I believe mount will permit reading and writting unless otherwise specified.

Hope that helps.

---

### Post by dennis_k85 on 2007-11-09
When I try to mount the windows file system I get this Error:
mount: block device //192.168.23.190/lbackup is write-protected, mounting read-only
mount: cannot mount block device //192.168.23.190/lbackup read-only

I use this mount command:
 mount -t cifs //192.168.23.190/lbackup -o username=oti/dennisk,password=xxxxxx /media/dak


I can mount the same windows share from a fedora box.

What am I doing wrong??

---

### Post by MJN on 2007-11-09
I've seen this sort of thing before when authentication fails (despite the error not intuitively referring to this) however you say you can access it okay from a Fedora, presumably the very same command/credentials?
 
Mathew

---

### Post by Viruk on 2007-11-16
> **James79 said:**
> Sorry I'm late. I've been away :)

I believe[ this person]("http://ubuntuforums.org/showthread.php?t=79612") had a similar issue and found a solution to it.

Ensure that the user you created on your windows machines has the permissions to write to your directory, and that the share itself permits writting. By default, if possible, I believe mount will permit reading and writting unless otherwise specified.

Hope that helps.

I checked out that issue and did 
apt-get install smbfs

That seemed to solve the connecting problem, however I am having issues writing to the share. 
I am connecting with credentials for an account that has full control over the windows share so I'm nto quite sure what to look for. 

I read another post showing the following command
//netbiosname/sharename    /media/sharename        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
Do I need to specify file_mode and dir_mode to make the share writable? 
If so how does that fit in to the slightly different command shown in this post?

---

### Post by Viruk on 2007-11-16
When doing ```
mount -t cifs -o credentials=/etc/details //server/share /mnt/mountpoint 
``` then doing ls on /mnt/mountpoint I can see the test files I put in the windows share, they shown in black text with a yellow background. 
(See attempt1.jpg)


I have now tried:
```
mount -t cifs //server/share /mnt/mountpoint -o iocharset=utf8,file_mode=0777,dir_mode=0777,credentials=/etc/details
```

doing ls on /mnt/mountpoint gives results in green - so i thought this may have solved my problem - but I still can't edit/create files!
(See attempt2.jpg)


Can anyone tell me what the different colour display means?

---

### Post by Viruk on 2007-11-20
I forgot to mention, I am using putty to connect to the server so I have not yet confirmed if these same colours are displayed when doing this direct from the server.

---

