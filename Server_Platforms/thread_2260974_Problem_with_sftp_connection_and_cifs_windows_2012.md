---
title: "Problem with sftp connection and cifs windows 2012 share"
date: 2015-01-15
forum: Server Platforms
---

### Post by berteipc2 on 2015-01-15
Hi all!

I've this problem:

I've config a SFTP server 3 days ago on my ubuntu last server version.

this is the configuration file sshd_config:
Subsystem sftp internal-sftp

Match group sftponly
ForceCommand internal-sftp
ChrootDirectory /var/sftp
X11Forwarding no
AllowTcpForwarding no

(I use this guide ***[http://devtidbits.com/2011/06/29/implement-a-sftp-service-for-ubuntudebian-with-a-chrooted-isolated-file-directory](http://devtidbits.com/2011/06/29/implement-a-sftp-service-for-ubuntudebian-with-a-chrooted-isolated-file-directory)***/)

on /var/sftp I mount trought fstab the follow windows 2012 server share:

//xxx.xxx.xxx.xxx/edi  /var/sftp/  cifs  username=administrator,password=xxx,iocharset=utf8,file_mode=0755,dir_mode=0755,gid=1001 0 0

gid=1001 is the group "sftponly" and I created a user in this group namely edi

after i launch mount -a I see this:

drwxr-xr-x  2 root sftponly    0 Jan 14 16:47 sftp

and If i use my filezilla with user edi to connect to ftp server all the thing is ok: I see all but I can't write and modify nothing


After, I change my fstab connecting line to: //xxx.xxx.xxx.xxx/edi  /var/sftp/  cifs  username=administrator,password=xxx,iocharset=utf8,file_mode=0775,dir_mode=0775,gid=1001 0 0

after i launch mount -a I see this:

drwxrwxr-x  2 root sftponly    0 Jan 15 16:59 sftp

and If i use my filezilla with user edi to connect to ftp server all the thing I recived an error:

Error:	Network error: Software caused connection abort
Error:	Impossibile collegarsi al server

and if i use sftp from terminal i recived this error:

Write failed: Broken pipe
Couldn't read packet: Connection reset by peer


I try for days and nights but I can't find a way to solve my problem...

Do you have any idea?

thanks a lot

---

### Post by TheFu on 2015-01-15
You can't write because the directory and file permissions for the group at mount are wrong.
775 is what you want for both.

---

### Post by Lars Noodén on 2015-01-15
It might be a permissions problem.  One detail, which necessitates a bit of fiddling sometimes, is that the chroot directory has to be owned by root and group root and not writeable by anyone else.  So you might make a subdirectory to /var/sftp and mount your CIFS system there.

So if you have the directory /var/sftp with root:root and 775 (or 755) and the subdirectory /var/sftp/cifs mounted from the remote machine with the permissions you have above,

```

Match group sftponly
  ChrootDirectory /var/sftp
  ForceCommand internal-sftp *-d cifs*
  X11Forwarding no
  AllowTcpForwarding no

```

The -d tells the SFTP server to start in that directory within the chroot.

---

### Post by berteipc2 on 2015-01-15
Thanks i'll try, but i've sftp directory with root:sftponly permission....and the user that i use called edi is in the group sftponly....

---

### Post by TheFu on 2015-01-15
> **berteipc2 said:**
> Thanks i'll try, but i've sftp directory with root:sftponly permission....and the user that i use called edi is in the group sftponly....

That is exactly why you need 775 permissions for this to work.
Might be useful to work through a permissions tutorial to better understand this stuff.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by berteipc2 on 2015-01-15
I know permission in linux thanks anyway!

But the problem is that is all correct but dosen't work.

No one have expirience about this situatio with a share win 2012 that is the roor of a ftp server? :*(

---

### Post by TheFu on 2015-01-15
My apologies. I missed the 775 settings in the 2nd part of your post.

We don't have any Windows Servers here, but I do mount from win7 and group sharing is working with Win7 as the initial source, provided the gid maps correctly.  I did find that using the IP address was required - using the hostname (which can be pinged by that name anywhere on the network) didn't work.

Here's my auto.Data line for one:
```
K       -fstype=cifs,rw,iocharset=utf8,gid=1000,file_mode=0664,dir_mode=0775,credentials=/etc/samba/win7lap-D.credentials  ://172.22.22.14/K

```

The put works:
```
sftp> put t
Uploading t to /Data/K
t                                             100%    0     0.0KB/s   00:00    
sftp>
```

BTW, did you rename "Administrator" to "administrator" on Windows? I don't think Windows cares, but ....  I'm reaching here. ;)

---

### Post by berteipc2 on 2015-01-15
Thanks for your post!
I see windows share trought ftp when is 755.
When is 775 i can't connect to ftp... is very strange...
It will be interesting undestrand why

---

### Post by TheFu on 2015-01-15
FTP is not the same as sftp. Please confirm you are using sftp.

Is the Win server on AD?  Kerberos?

---

### Post by Lars Noodén on 2015-01-16
> **berteipc2 said:**
> Thanks for your post!
I see windows share trought ftp when is 755.
When is 775 i can't connect to ftp... is very strange...
It will be interesting undestrand why

With root:sftponly, it should work when 755 and not work when 775 because in the former only root can write to the chroot and in the latter more than root can write to the chroot.  SSH / SFTP won't chroot unless *only* root has write access to the directory.  Check the manual page for [sshd_config](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html) for the paragraphs on ChrootDirectory as they are the authoritative source on the matter.  However, they don't go into their motivations for such a decision there in the man page, so I am equally curious.

So I would put the CFS mount inside a subdirectory like in #3 above.

---

### Post by berteipc2 on 2015-01-16
Yes is SFTP and is a windows server R2 2012 and its user is in Domain (in a AD)

---

### Post by berteipc2 on 2015-01-16
Ciao!
I don't modify anything in my config sftp file.

I umount windows share,
and I set 755 to the directory that is in chroot.

Than I create subdirectory editest with 775 under the chroot directory.

Than I connect to SFTP server without problem.

If i enter into the subdirectory I can write and modify.

So now i'm going to repeat the same operation on windows share and after that I'll post here the result.




> **Lars Noodén said:**
> With root:sftponly, it should work when 755 and not work when 775 because in the former only root can write to the chroot and in the latter more than root can write to the chroot.  SSH / SFTP won't chroot unless *only* root has write access to the directory.  Check the manual page for [sshd_config]("http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html") for the paragraphs on ChrootDirectory as they are the authoritative source on the matter.  However, they don't go into their motivations for such a decision there in the man page, so I am equally curious.

So I would put the CFS mount inside a subdirectory like in #3 above.

---

### Post by berteipc2 on 2015-01-16
so i mount windows share with 755 permission and correct uid:gid on /var/sftp, I can connect with filezilla.
By terminal i create subfolder under /var/sftp namely editest, and the persmission is 755 with the same user and group of the top directory.

So i do chmod 775 to the editest subfolder, I don't recive any errors but the permission remain 755.... Now I think that the problem is this....

---

### Post by Lars Noodén on 2015-01-16
> **berteipc2 said:**
> so i mount windows share with 755 permission and correct uid:gid on /var/sftp, .

You would need to mount the CIFS share under /var/sftp/edittest with permissions 775 but leaving /var/sftp itself as 755.  Chroot on SSH / SFTP is a little fiddly.

---

### Post by berteipc2 on 2015-01-16
Yes lars!
 the problem is how I can mount sftp with 755 and have possibility to change permission on folder inside... 

> **Lars Noodén said:**
> You would need to mount the CIFS share under /var/sftp/edittest with permissions 775 but leaving /var/sftp itself as 755.  Chroot on SSH / SFTP is a little fiddly.

---

### Post by darkod on 2015-01-16
Folder permissions do not depend strictly on the up level folder. Even in Windows you have that option. You can have /folder1 with 755 (more restricted), but folder /folder1/folder2 with 775. Depending what you need.

Simply set 775 to /var/sftp/edi and that's it.

---

### Post by Lars Noodén on 2015-01-16
> **berteipc2 said:**
> Yes lars!
 the problem is how I can mount sftp with 755 and have possibility to change permission on folder inside...

Don't mount anything on /var/sftp itself.  Make the directory /var/sftp mode 755 and leave it at that.  Then make a subdirectory /var/sftp/editest.  Then mount your CIFS on /var/sftp/editest with permissions [s]755[/s] 775  That should do it.

---

### Post by darkod on 2015-01-16
> **Lars Noodén said:**
> Don't mount anything on /var/sftp itself.  Make the directory /var/sftp mode 755 and leave it at that.  Then make a subdirectory /var/sftp/editest.  Then mount your CIFS one /var/sftp/editest with permissions [COLOR=#ff0000]755[/COLOR]  That should do it.

I made the same mistake typing and then edited it. The second one should be 775 right?

---

### Post by Lars Noodén on 2015-01-16
Yes. The second one should be 775.  Sorry for the typo

---

### Post by berteipc2 on 2015-01-16
i'm trying now... THANKS!

---

### Post by berteipc2 on 2015-01-16
OK!!!

I've mount the windows share on editest with 775 and I left /var/sftp with 755 and all works!!!!

THANKS!!!!!!

---

### Post by Lars Noodén on 2015-01-16
Great!

Also, if you use the [-d option for internal-sftp](http://manpages.ubuntu.com/manpages/trusty/en/man8/sftp-server.8.html) you can set the starting directory to be within the mount itself.

```

Match group sftponly
  ChrootDirectory /var/sftp
  ForceCommand internal-sftp -d editest

```

---

### Post by berteipc2 on 2015-01-16
THANKS A LOT!!!!!! how i can put solved on this post?

---

### Post by slickymaster on 2015-01-16
> **berteipc2 said:**
> THANKS A LOT!!!!!! how i can put solved on this post?

[How to mark your thread as SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

