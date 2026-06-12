---
title: "Mount error 6"
date: 2011-11-07
forum: Server Platforms
---

### Post by brand1068 on 2011-11-07
I'm new to this...
 
So I'm trying to setup a ubuntu server for testing.
 
Named Ubuntu
 
Need to setup a file share - no security
 
The folder I want to share is in /mnt/ called share so lives /mnt/share
 
I want to call it sage 
 
So the line in fstab I have is
 
//Ubuntu/sage /mnt/share cifs user=USERNAME,password=PASSWORD,UID=1000,iocharset-tuf8,codepage=unicode 0 0
 
the user name and password are my current admin account
 
but when I sudo mount -a I get the 
 
Retrying with upper case share name
mount error (6) : No such device or address
 
I can ping the server name and get the correct IP 
 
Now I'm stuck..
 
Chris

---

### Post by papibe on 2011-11-07
In order to mount samba shares you need to install an additional package (besides samba):
```
sudo apt-get install smbfs
```
Hope it helps. Tell how it goes.
Regards.

---

### Post by brand1068 on 2011-11-07
Hi - thanks for the help.
 
Yes have installed smbfs - same issue.
 
Best,
 
Chris

---

### Post by papibe on 2011-11-07
Wait a minute...

You want to share it? So it is not shared yet? At first I thought the mount was in the client side, but now I have my doubts.

Just to make sure:
[LIST]
[*]You share a folder using samba by creating a new entry in /etc/samba/smb.conf. See [this]("http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html") example.
[*]On the client side you could both just browse the network and double click the share, or mount the share as I think you were doing.
[/LIST]
Also, Could you post the result of this command on the server?
```
testparm
```
Regards.

---

### Post by brand1068 on 2011-11-07
DOH !
 
I feel a total numpty now...
 
Yes I was trying to mount the share on the ubuntu server for the windows clients to see....
 
I see know I've been doing it the wrong way round.... flibbty gibbets
 
Now that works but asks for a user name and pwd when you connect.
 
Any way around this ?
 
Chris

---

### Post by papibe on 2011-11-07
Great!

You can use the user and password on the server to connect. If don't really want passwords, change the security to "share" in your smb.conf:
```

   security = share

```
Try that and let us know how it goes.
Regards.

---

