---
title: "mounting files from NFS server on clients"
date: 2012-06-19
forum: Server Platforms
---

### Post by Ms. Daisy on 2012-06-19
I'm trying to set up a NFS file server (on Ubuntu server 12.04) to share files with several Ubuntu clients.  They all live on a host-only network in virtualbox if it makes any difference.

I found this tutorial 

[http://jeff.robbins.ws/articles/nfs-tutorial](http://jeff.robbins.ws/articles/nfs-tutorial)

Which seemed to be pretty simple to follow.  I can see the shared folder using ```
mount -l
``` so I know the server & client are communicating.

I want to mount the file /home/sharedfiles (which lives on the server)  permanently on the client in  /home.  I want the file to appear  in the GUI home folder for the client if that's possible, too.  To modify /etc/fstab I did this on the client:```
gksudo gedit /etc/fstab
``` Do I need to be root instead?

I modified the /etc/fstab file to say this: ```
192.168.56.101:[COLOR=#000000]**/**[/COLOR]home/sharedfiles    [COLOR=#000000]**/**[/COLOR]home       nfs         rw           [COLOR=#000000]0[/COLOR]    [COLOR=#000000]0[/COLOR]
``` And the next time I booted the client, it couldn't mount anything including home.  So obviously something is horribly wrong.  Can anyone point out the grievous error?

Obviously I'm new to servers, mounting, nfs, linux, editing /etc/fstab, and the planet.  So if you know of any good guides for noobs such as myself please share.

---

### Post by CharlesA on 2012-06-19
I haven't really done any NFS mounting, but can you post your entire /etc/fstab file?

EDIT: Check out the info on nfs mounting via fstab here too:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by SeijiSensei on 2012-06-20
I'd start by figuring out how to get the share mounted to some temporary mountpoint other than /home.  Create a directory called something like /mnt/test and try mounting it there.

Unless /home/sharedfiles on the server actually contains the users' home directories on the server, you'll almost certainly have problems.  If you want a user on the client to see /home/user as her local home directory, then you need to export /home from the server.

What do you have in the server's /etc/exports?  In particular, do you have "no_root_squash" as an option?  If you want to mount the share on the client in a root-owned directory like /home, you need to use "no_root_squash".  Otherwise the share will be owned by the "nobody" user.  See "man exports" for details.  

I export the /home from a server and mount it to /media/something.  In /etc/exports I have:

```
/home 192.168.0.0/16(rw,no_root_squash,async,insecure)
```

I use async because I write to the server only rarely and thus am not worried about losing cached writes in the event of a crash.  The server also has a UPS and remains up pretty much 24/7.  The "insecure" option allows the client to connect on ports < 1024.  I don't recall if I needed it or not the last time I set things up.  I'm pretty sure I've run NFS servers without that option.

---

### Post by Ms. Daisy on 2012-06-21
Very helpful, thanks SeijiSensei!

---

### Post by SeijiSensei on 2012-06-23
How are things progressing, Daisy?

I thought I should amplify my remarks about the "async" option.  If all the clients are on a wired LAN, then I wouldn't use async.  If you have some wifi clients, then it will improve their peformance considerably with only a limited risk of data loss.  If the wifi clients are in a different subnet from the wired clients, you can export the same share twice, once with the wired subnet specification and sync, and again with the wifi subnet and async.

Also, for testing purposes, just to see if you make the connection and mount the share, you can use:

```
sudo mount server:/share /mnt/point
```

and not deal with /etc/fstab.  You don't need to include "-t nfs" for mount; it recognizes the form server:/path as an NFS filesystem.

---

### Post by Ms. Daisy on 2012-06-23
Thanks again.  I decided to mount the shared folder in /mnt and things went much better.  I've got three files in my shared folder: user, user12, and test. 
[ATTACH]220142[/ATTACH]

---

