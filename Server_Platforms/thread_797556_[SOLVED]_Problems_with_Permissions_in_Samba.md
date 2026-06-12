---
title: "[SOLVED] Problems with Permissions in Samba"
date: 2008-05-17
forum: Server Platforms
---

### Post by dash86no on 2008-05-17
Evening,

I have set up SAMBA file sharing on Hardy server edition today. Everything is working great, and I can copy files from both my Hardy desktop box and my windows xp box.

My problem, is that although I am able to create new files and folders, the permission settings of these files and folders seem to be getting set to "root" by default. When I create a file or folder, an orange padlock appears in the corner and it says something about the user being "nobody" and the group "nogroup".

Interestingly, there is no such problems when I create files and folders from my windows box. this leads me to think it might be a problem with the way i'm mounting the share with my fstab file. 

Anyway, it's a little annoying because I can't copy folders over to the shared drive, because it will create the new folder then immediately deny the files being copied and say there is no permission. 

I would appreciate any advice.

---

### Post by koenn on 2008-05-17
> **dash86no said:**
>  ... this leads me to think it might be a problem with the way i'm mounting the share with my fstab file

post the relevant entry from your fstab then.

---

### Post by dash86no on 2008-05-17
Here is is:

# Ubuntu Share
//192.168.0.22/public /media/ubuntushare cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

---

### Post by fmartinez on 2008-05-17
> **dash86no said:**
> Here is is:

# Ubuntu Share
//192.168.0.22/public /media/ubuntushare cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

This should be the normal response when you mount a file system as "guest". 
Try using share instead so you can login and get full access that filesystem.

---

### Post by dash86no on 2008-05-17
> **fmartinez said:**
> This should be the normal response when you mount a file system as "guest". 
Try using share instead so you can login and get full access that filesystem.



I modified my fstab to: 

# Ubuntu Share
//192.168.0.22/public /media/ubuntushare cifs share,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 

I then remounted. However, I am still getting the same problem. The orange padlock still appears in the top corner of any folder I make and I can't copy files into these folders.

---

### Post by koenn on 2008-05-18
there's a space in your dir_mode=07 77 that probably shouldn't be there

also, try mounting that share from the command line until you got it working as it should, then create a corresponding entry in fstab

the problem might have something to do with the user account you use to access that share. Look at these examples for ways to pass credentials to samba when mounting a share : [http://wiki.linuxquestions.org/wiki/Samba](http://wiki.linuxquestions.org/wiki/Samba)

---

### Post by dash86no on 2008-05-24
Koenn,

Cheers for the tip. Actually, there is no space in my "dir_mode=07 77 " but it appeared that way when I copied and pasted into this forum. Weird eh?

If I "mount" the shared file through the network menu option, i can copy folders no problem. 

however, if I mount using fstab I have the problem. I wonder if anyone could point me towards a page detailing mounting file systems and related permissions issues. 

The difficult thing here is that this is NOT a mounted windows directory. It is a mounted Ubuntu server shared folder. A lot of the web pages out there (including the one Koenn pasted) have instructions for accessing a windows shared drive, which is not quite what I want. 

On a lighter note, I've successfully got my web/ftp server set up with Ubuntu. It was really easy and is working amazingly well. I really can't get over how awesome Ubuntu is....

---

### Post by koenn on 2008-05-24
Windows File Sharing and Samba behave identically, so it doesn't really matter that you find Windows examples. The same mechanisms apply to a Samba server.

When I say mount, I mean mount, as in 'attach storage to a mount point in your filesystem'. What you see in Nautilus when you do 'connect to network server', isn't a mount. It's a gui representation of a network protocol. 
What i meant is : once you figure out how to use the mount command to get what you want, it's trivial to write the corresponding entry in fstab.
So experiment with 'mount' until you have something that works.

Seeing that you can access the network share through smb (Windows File sharing protocol, what you use when you use Places:Network -> Windows server) but not trough mount, suggests your samba config on the server is OK (for now) but your mount command isn't. 

try leaving out some or all of the options. I'd keep rw, but get rid of the masks, share, charset, or add them one by one,  until you have something that works.
mounts in fstab are executed by root, the mount command is executed with sudo, so probably you have root@client trying to access files that belong to user@server. You probably get readonly access to files that have others:read. So you may need to add a username & pass for the account that owns the files on the server to your mount statement. 
Look in the samba manual for the exact syntax.

---

### Post by dash86no on 2008-05-25
koenn,

Many thanks for your advice.

I've read through the man mount and man mount.cifs and tried various options (Such as -t cifs, -o noman -o default etc.etc.) but I cant get anything to work. I also tried creating a folder in my /home area and mounting to that, but I haven't had any luck. 

I've searched google to death with "new directory read only, new dir ro, new dir permission problem, samba create new directory, etc. etc. and I just can't find anyone out there who has had the same problem (Which seems bizarre)

I'm sure this problem is due to my lack of understanding the linux file system, including concepts such as "groups" and "ownership of files/folders" 

I did not quite follow what you wrote about adding username and pass of user account that owns files on the server. I would have thought that should be kept transparent from client machines.

---

### Post by koenn on 2008-05-25
> **dash86no said:**
> 
I did not quite follow what you wrote about adding username and pass of user account that owns files on the server. I would have thought that should be kept transparent from client machines.

```
mount -t smbfs //server/share /mnt -o rw,**username=joe,password=bloggs**

```
this is actually the 2nd line in the wiki page I linked to. 
note that the account 'joe' is a user account on the server. It's the same name and pass that you use to connect to the share via Places:Network

it's simple : if the directory that is shared as //server/share is owned by user joe, and no-one else has access to it , then the server is going to want you to authenticate as user joe (with password 'bloggs') before you're allowed access to that share. It wouldn't be very secure if by mere sharing a directory, the whole world would get access to your files, would it ? Microsoft used to do it that way, and even they changed their minds about it somewhat. 

If you want it transparent, you have to make it transparent. Usually this is done by some form of centralised authentication (Microsoft Active directory, LDAP, Kerberos, ...) ; however, you still need to authenticate. 
In the examples from that wiki page, it's made transparent to the _user_ (not to the client) by adding credentials to the mount command or the fstab entry.

---

### Post by dash86no on 2008-05-25
> **koenn said:**
>  It's the same name and pass that you use to connect to the share via Places:Network



Hmmm, actually I do not need to enter a user name and password when I connect via Places:Network. I've set up my Samba so that anyone on the network can access the folder without any authentication. This is how I would like at the moment. 

I'm actually migrating from Windows 2000 server to Ubuntu so I've whacked my AD and was not intending to replace it for a while (As central authentication is not so useful in a home network as far as I can tell). 

However, maybe what you are suggesting is that without this central authentication (Via. LDAP or whatever) I’m not going to be able to get this working correctly?

It's pretty frustrating; because other than new folders being created in RO mode, EVERYTHING else about this mounted share works perfectly. I can create files, delete files to my heart’s content. That got me thinking that the issue could be one of new folders inheriting some kind of permissions from somewhere, but I can't for the life of me work out where. (Since the parent folder (my shared directory itself) allows full rw permissions.

---

### Post by molotov00 on 2008-05-25
One thing comes to MY mind that hasn't been mentioned yet. In /etc/samba/smb.conf there's a line:

directory mask = 0700

Since you are opening your server up to everyone anyway, you should be able to change this to 0777 or 0775, then everyone should be able to modify any folders that Samba creates. Hope that helps!

Edit: directory mask is the security/permission assigned to a folder created under Samba. Remember to restart Samba after editing the config.

Let us know if you get it working.

M

---

### Post by koenn on 2008-05-26
> **dash86no said:**
> 
However, maybe what you are suggesting is that without this central authentication (Via. LDAP or whatever) I’m not going to be able to get this working correctly?
That's not what I said. My mention of LDAP etc. what just a side note in reply to your 'transparent'. LDAP is one way to do that. Abandoning all authentication is another.

> **molotov00 said:**
> One thing comes to MY mind that hasn't been mentioned yet. In /etc/samba/smb.conf there's a line:

directory mask = 0700

Since you are opening your server up to everyone anyway, you should be able to change this to 0777 or 0775, then everyone should be able to modify any folders that Samba creates. Hope that helps!

I think it's worth a shot, It crossed my mind but I ruled it out because accessing the shares through Places:Network works, but changing the dir mask might actueally help to circumvent the permission/ownership issue.

> **dash86no said:**
> 
It's pretty frustrating; because other than new folders being created in RO mode, EVERYTHING else about this mounted share works perfectly. I can create files, delete files to my heart’s content. That got me thinking that the issue could be one of new folders inheriting some kind of permissions from somewhere, but I can't for the life of me work out where. (Since the parent folder (my shared directory itself) allows full rw permissions.

your wording is confusing. you can have ro and rw for mounting filesystems etc, but this has nothing to do with the actual permissions. 'rw permissions' is meaningless unless you specify who's permissions you're talking about : the owner, the group, or all others. 
Hence the importance of
a/ knowing the permissions
b/ knowing wich account you authenticate with when accessing a remote filesystem

Maybe it helps if you show the filesystem permissions (_on the server_) of the shared directory, and some files in it (both files that you can modify and files that you can't modify)
you can do this with 'ls' eg
```
ls -dal /home/username
ls -al /home/username/some_file
```

---

### Post by dash86no on 2008-05-27
> **molotov00 said:**
> One thing comes to MY mind that hasn't been mentioned yet. In /etc/samba/smb.conf there's a line:

directory mask = 0700

Since you are opening your server up to everyone anyway, you should be able to change this to 0777 or 0775, then everyone should be able to modify any folders that Samba creates. Hope that helps!

Edit: directory mask is the security/permission assigned to a folder created under Samba. Remember to restart Samba after editing the config.

Let us know if you get it working.

M

Molotov,

you're a legend. I edited the line directory mask = 0700 to directory mask = 0775 and restarted SAMBA, as you directed, and my share is now working a treat.

Many many thanks for the help.

---

### Post by dash86no on 2008-05-27
i'm trying to edit the thread title to make it clearer for people who may have the same problem in the future.

Hmm not sure how to do this. Can anyone tell me how to edit a thread title?

---

