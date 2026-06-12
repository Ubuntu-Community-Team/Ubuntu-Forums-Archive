---
title: "Problems mounting samba share"
date: 2011-02-02
forum: Server Platforms
---

### Post by stalemath on 2011-02-02
I am in the process of setting up a server on Xubuntu 10.04, using Samba. I am using these tutorials:

[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1)
and
[http://www.techrepublic.com/blog/opensource/how-do-i-connect-a-mac-os-x-machine-to-a-samba-share/173](http://www.techrepublic.com/blog/opensource/how-do-i-connect-a-mac-os-x-machine-to-a-samba-share/173) (to figure out how to connect via Mac)

and now that I have edited the smb.conf file, set up my samba username/password and everything, when I connect to my server IP and click "homes" to mount, I get an error message saying
```
The volume "homes" could not be mounted.
```

Does anyone know how I can fix this? I am new to Linux and trying to set up a server to host a few websites. Thanks

---

### Post by Weareblkflag on 2011-02-02
Well What kind of computers are you trying to setup? Windows and Mac to Linux?
 
I just set up something similar to what I think you are trying to do.
 
I have 2 Win boxes Vista(fail) Win 7(not so much fail) and 2 Ubuntu 10.10 boxs.
 
They all can see eachother and share files. So give some more info and Ill try to help out as much as I can. im a bit of a noob also.

---

### Post by stalemath on 2011-02-02
> **Weareblkflag said:**
> Well What kind of computers are you trying to setup? Windows and Mac to Linux?
 
I just set up something similar to what I think you are trying to do.
 
I have 2 Win boxes Vista(fail) Win 7(not so much fail) and 2 Ubuntu 10.10 boxs.
 
They all can see eachother and share files. So give some more info and Ill try to help out as much as I can. im a bit of a noob also.

I am using Linux (Xubuntu 10.04) on an old HP machine to run a server (for a few websites I manage), and I am trying to connect to it from a Mac (however, I just tried to connect from a Windows XP machine and I'm still unable). The server is recognized from both the Mac and Win computers, but I'm getting error messages when trying to connect to the "homes" or user directory of the server.

---

### Post by SeijiSensei on 2011-02-02
If you're not supporting Windows clients, then you should consider using NFS and not Samba.  That would enable you to export /home from the server and mount it into the OS X filesystem.

[http://www.techrepublic.com/blog/mac/mounting-nfs-volumes-in-os-x/430](http://www.techrepublic.com/blog/mac/mounting-nfs-volumes-in-os-x/430)

You can also use both NFS and Samba, the first to support *nix clients like Linux and OS X, and the latter to support Windows.

---

### Post by Morbius1 on 2011-02-02
Well, it's likely that I don't know what I'm talking about since one of the authors of the HowTo's you referenced claims to have 12 years experience at this sort of thing but ....

One doesn't "browse to" or "mount" homes because "homes" doesn't exist ( you will notice the [homes] section of smb.conf has no path ). It's a template used against the samba users on the server and it creates a share "on the fly" the moment the remote user asks for it. You have to access the share explicitly by using one of the following formats depending on the client OS:

```
smb://server/username
``````
\\server\username
```Perhaps OSX uses pixie dust to accomplish the same thing without passing a username at the moment of initial contact but I don't think it will work without it. In OSX's "Connect to server" use smb://server/username instead.

---

