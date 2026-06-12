---
title: "NFS Share Permissions"
date: 2009-03-22
forum: Security
---

### Post by bigbencg on 2009-03-22
Perhaps this is a better forum to post in, I am getting no answers in the networking forum.  [http://ubuntuforums.org/showthread.php?t=1102775]("http://ubuntuforums.org/showthread.php?t=1102775")

I have been playing around with NFS between my kubuntu boxes and a mac mini. I can set up the share and mount the share on the client computers. My issue is PERMISSIONS!!!!!

Permissions in linux are frustrating at best

When I create a folder in the root directory /thor, the default owner is root. Mounting this share on other systems gives me the ability to see the share, but no files or folders can be created in the share. Not even on the host computer with a sudo command. I made the share work by creating a new user on the host computer and using chown to change ownership of the folder. Presto, the share works.

Is there a built-in group or user that I can assign a shared folder to? One that would give a remote user the permissions I assign the share in exports.

P.S. I have another question about NFS [http://ubuntuforums.org/showthread.php?t=1102722](http://ubuntuforums.org/showthread.php?t=1102722)

---

### Post by cariboo on 2009-03-22
You could just give your mount point read/write permissions eg:

```
sudo chmod -R 777 /thor
```

This leaves the owner as root, but the share will be world read/writeable.

You can also set read/write permissions when exporting the share eg:

```
/home        192.168.0.1(rw) 192.168.0.2(rw)

```

Jim

---

### Post by HermanAB on 2009-03-22
You can do exactly what you want - force the accesses to be a specific user and group. Look at the NFS user_squash (or all_squash), anonuid and anongid mount options.

[http://www.troubleshooters.com/linux/nfs.htm](http://www.troubleshooters.com/linux/nfs.htm)

/etc/exports:
```

/home/data *(all_squash,anonuid=500,anongid=500,async,secure,no_subtree_check,rw)

```

Cheers,

Herman

---

### Post by bigbencg on 2009-03-22
I was stuck on user permissions rather than directory permissions.  Thank you for the tip cariboo907.  The share works and each computer and I can write to the share.  However I need to work on limiting access to the share.

Thank you for the help!

---

### Post by bigbencg on 2009-03-22
> etc/exports:
Code:

/home/data *(all_squash,anonuid=500,anongid=500,async,secure,no_subtree_check,rw)

Cheers,

Herman

This is what I need, examples!  Does the * designate any IP?  All examples I have seen are using IP's and netmasks to set access.

---

### Post by buntunub on 2009-05-06
First off, I use nfsv4 which is much easier to work with than older nfs versions. For that you use exports (/etc/exports) and you export the folders you wish to share via sudo exportfs -rv or -ra, and then simply setup your fstab on the clients and mount them and your done! The problem I think your having is that you need to set no_root_squash as an export option on your server files and that should in turn tell NFS to not worry about root permissions. Instead, NFS ties permissions to the user which in turn is granted root privledges over those specifically mounted/exported filesystems. Example nfs4 --

[Exported files]
/export/home  rw, async, no_root_squash, (more options as needed)
/export/whatever  rw, async, no_root_squash, (yada yada)

*bind your exports*

[server fstab entries]
/export/home  bind  0  0 
/export/whatever  bind  0  0 

Now export 

sudo exportfs -rv

Restart your nfs stuff

Then setup your client with fstab -

servername:serverIP /export/home  /your/mount/point  nfs4  rw, async, rs=8192, ws=8192, async, noint, hard, etc etc etc..

Restart nfs stuff on client and then mount -a and you should now see your NFS shares and they should be very fast, stable, and come up every time you reboot. NFS is an awesome network filesharing system that works very much like windows share mapping.

Forgot to add in here that this is a very rough example and going strictly off memory, although its pretty close. Follow the plethora of NFS how to's which abound the web. Google in all cases is, and always should remain, your bestest Linux buddy.

---

### Post by bigbencg on 2009-05-07
That is exactly what I was looking for, an explanation of some permissions.  I did not set up my share with chmod 777, my workaround was to create similar accounts on each comptuer and set the ID's to be identical.  I will adjust my shares with the steps you mentioned when I get a chance. 

Thank you for the reply!!!

---

