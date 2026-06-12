---
title: "Samba with POSIX Permissions"
date: 2010-09-13
forum: Server Platforms
---

### Post by wiz561 on 2010-09-13
Hi,

Please help because I'm tearing my hear out!  I'm sure I'm making this more of an issue than it really is, but I can't get these samba shares for the life of me.

OK, I have an ubuntu 'server' with a the directory "/data/public/".  In my smb.conf, I have this...

---
[public]
path = /data/public/
browseable = yes
comment = share
writable = yes
public = yes
guest ok = yes
---

On my box, my public directory looks like this...


root@snoopy:/data# ls -l
total 20
drwx------ 2 root root 16384 2010-09-12 20:45 lost+found
drwxrwxrwx 2 root root  4096 2010-09-12 21:56 public
root@snoopy:/data# 


==========
On another linux box, as root, I mkdir 'public' in /mnt so it looks like this.


root@XBMCLive:/mnt# ls -l
total 4
drwxr-xr-x 2 root root 4096 2010-09-13 07:55 public
root@XBMCLive:/mnt# 

I think mount the share...

root@XBMCLive:/mnt# smbmount //10.0.1.3/public /mnt/public/ -o guest
Warning: mapping 'guest' to 'guest,sec=none'
root@XBMCLive:/mnt# 

After that, I try to create a file, but get a 'permission denied' as a regular user of the system, but it still creates the file.

xbmc@XBMCLive:/mnt/public$ pwd
/mnt/public
xbmc@XBMCLive:/mnt/public$ ls -l
total 0
xbmc@XBMCLive:/mnt/public$ touch foobar
touch: cannot touch `foobar': Permission denied
xbmc@XBMCLive:/mnt/public$ ls -l
total 0
-rw-r--r-- 1 nobody nogroup 0 2010-09-13 08:23 foobar
xbmc@XBMCLive:/mnt/public$ 

But then as 'root', it works fine.

xbmc@XBMCLive:/mnt/public$ sudo su
[sudo] password for xbmc: 
root@XBMCLive:/mnt/public# touch root-foobar
root@XBMCLive:/mnt/public# ls -l
total 0
-rw-r--r-- 1 nobody nogroup 0 2010-09-13 08:23 foobar
-rw-r--r-- 1 nobody nogroup 0 2010-09-13 08:25 root-foobar
root@XBMCLive:/mnt/public# 

===========================

It seems like I can never get samba just right to where it works.  I've tried to set it up a dozen of times, and I continue to get issues with permissions.  Can anybody help make a suggestion to where this works?  

Thanks in advance...

---

### Post by wiz561 on 2010-09-13
FYI...I got it to work by doing something funk in fstab.


//10.0.1.3/video	/media/samba/video	cifs	guest,rw,mand,nosuid,nodev,relatime,uid=1000,forceuid,gid=1000,forcegid,addr=10.0.1.3,posixpaths,serverino,acl,rsize=16384,wsize=57344 0 0

Don't ask me what it all means.  I just kept running into one problem after the other, but this seems to fix it.

---

