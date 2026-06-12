---
title: "Automount NFS exports on a mac"
date: 2008-08-03
forum: Server Platforms
---

### Post by rossdub on 2008-08-03
I've set up an ubuntu 8.04.1 server on my home network.  Both Samba and NFS are configured and working properly.  I use linux and my wife uses a mac, so I would prefer to use the NFS exports as our primary file sharing system.  I can mount the exports on both machines, and I've configured my /etc/fstab file to make the exports automount on my linux laptop.  I'm looking for a way to make the same happen on my wife's Macbook.  It runs OS X leopard.  Anyone successful in setting up an automount on leopard? 

(Sorry if this is the wrong place for this...couldn't find much out information from google about automounting in leopard specifically and ubuntu forums are usually really helpful for everything).

---

### Post by windependence on 2008-08-03
I just let SAMBA do it on my Macbook pro. It just "works" like a Mac normally does, sees the share and mounts it after authenticating. Note that the Mac user and password must also exist in SAMBA and must be the same.

-Tim

---

### Post by rossdub on 2008-08-03
windependence-

Thanks...i didn't know I could get samba to mount automatically...I have the security option set to user so I thought we would have to sign in every time with a UN/password that exists on the server.  

Also, it seems to me that samba is a bit slower...especially when we are trying to play movies or music over the network.  That is why I would prefer to use NFS.  I just can't seem to find a way to automount the NFS export on the mac.  using the mount command works fine, but I don't want to have to do that every time my wife wants to access something from the server...I suppose i could just write a script, but it seems like I could use something already built in (like /etc/fstab in Linux).  Any suggestions?

---

### Post by windependence on 2008-08-03
Remember, this is a MAC. You should be able to do everything through the GUI. I never tried to see an NFS share on my Mac because SAMBA works fine (I don't think that is your slowness issue), but I can't see why the Mac wouldn't just see it as another network share in the finder. I'm thinking you don't want to mount it remotely, you  want to export it from the server, you know what I mean?

-Tim

---

### Post by rossdub on 2008-08-03
> **windependence said:**
> Remember, this is a MAC. You should be able to do everything through the GUI. I never tried to see an NFS share on my Mac because SAMBA works fine (I don't think that is your slowness issue), but I can't see why the Mac wouldn't just see it as another network share in the finder. I'm thinking you don't want to mount it remotely, you  want to export it from the server, you know what I mean?

-Tim

It doesn't mount automatically to show up in the finder.  Perhaps there is an nfs setting that I have overlooked which would work.  But I thought that the whole point NFS was to mount a file system locally. I'll keep digging and post here if I find anything

---

### Post by thefunnyman on 2008-08-03
I was in a similar situation that I actually resolved yesterday.  My hardy laptop found and mounted nfs shares automatically at system startup.  I figured I could just use the gui to configre nfs on my wife's mac, but that was not the case.  I eventually had to take the username that she created for herself and add her as a user on the server, then, I set up /etc/fstab for her to mount our shares on system startup.  Has worked perfectly ever since, and no samba....

The mac actually didn't have an fstab file, so I created one and the mount command uses it just like on a normal linux system. Here's an example row I put in her /etc/fstab file:
```

server:/full/path/to/share  /path/to/mount/dir     nfs    rw,hard,intr    0  0

```

Also, almost forgot...I read this on a forum somewhere and it seemed to make a difference as well.  I had to also add a directive (insecure) to my /etc/exports file on the server.  An example of that entry below:
```

/media/sdb1/Pictures      192.168.1.1/24(rw,insecure,no_subtree_check,sync)

```

Then, on the mac, u can run:
```

sudo mount /path/to/mount/dir

```
to test that fstab and nfs are playing nice without rebooting the mac.

I hope this helps.

thefunnyman

---

### Post by halocaridina on 2008-08-04
You might also look into the Directory Utility that comes with OS X 10.5.  It is located in Applications - Utilities.  I've used it to auto mount NFS shares on login.  Just google for some specific examples of how to use Directory Utility.

Here is a link to see how:

[http://www.dslreports.com/forum/r19564529-How-to-share-files-between-UbuntuLinux-Mint-and-OSX-](http://www.dslreports.com/forum/r19564529-How-to-share-files-between-UbuntuLinux-Mint-and-OSX-)

---

### Post by rossdub on 2008-08-04
Awesome...exactly what I was looking for.  Thanks!

---

### Post by rossdub on 2008-08-04
Halo - 

Thanks, I'll definitely look in to that as well.

---

### Post by thefunnyman on 2008-08-04
> **halocaridina said:**
> You might also look into the Directory Utility that comes with OS X 10.5.  It is located in Applications - Utilities.  I've used it to auto mount NFS shares on login.  Just google for some specific examples of how to use Directory Utility.

Here is a link to see how:

[http://www.dslreports.com/forum/r19564529-How-to-share-files-between-UbuntuLinux-Mint-and-OSX-](http://www.dslreports.com/forum/r19564529-How-to-share-files-between-UbuntuLinux-Mint-and-OSX-)

Well, that definitely works too, if u want to do it the non-nerdy, easier way.

Thanks man, tested on my wife's mac and works beautifully.

Thanks again,

thefunnyman

---

### Post by rossdub on 2008-08-07
I found this after following the link above.  It clearly spells out all of the options for automounting NFS shares on OS X 10.5.
[URL="http://xanana.ucsc.edu/~wgscott/xtal/wiki/index.php/NFS_on_OS_X_10.5#Auto-Mounting_remote_filesystems_with_NFS"]
http://xanana.ucsc.edu/~wgscott/xtal/wiki/index.php/NFS_on_OS_X_10.5#Auto-Mounting_remote_filesystems_with_NFS[/URL]

Hope that helps some one else looking to do the same things.

---

