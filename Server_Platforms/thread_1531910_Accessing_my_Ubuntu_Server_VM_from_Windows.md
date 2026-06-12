---
title: "Accessing my Ubuntu Server VM from Windows"
date: 2010-07-15
forum: Server Platforms
---

### Post by HittingSmoke on 2010-07-15
I recently set up a local test server for my site using Ubuntu server in VMWare Player on a Windows 7 host.

I'm wondering how to go about easily accessing files on my test server.

First I tried Samba then gave up after reading how complicated it is to set up. I opted for FTP.

After some trial and error I settled on proftpd. It was the first one that would let me successfully connect. I thought everything was OK.

Today I tried to copy over my current web site via FTP and I get *550 index.html: Permission denied* across the entire virtual drive. Even in the Home directory of the user I'm logged in as. The permissions on the drive are all 755 as far as I can tell. As far as I know everything is set up properly in proftpd.conf also.


After all of this I tried Samba again. I got it to show up in my networked computer list and logged in but when I open the network drive nothing shows up. As if it's an empty folder.

Can anyone give me any ideas on how to get either or both of these systems to work? I just need a way to easily move files to my VM from the host. Preferably with full drive access.

---

### Post by brettg on 2010-07-15
By far the easiest way is to use samba. The default config should pretty much "just work". 

From there you need to add a user;

```
sudo smbpasswd -a *username*
```

and configure a share in /etc/samba/smb.conf

```
[myshare]
path = /path/to/dir
directory mask = 755
create mask = 755
browseable = yes
```

This is a basic, not terribly secure config but it will be enough for a start.

Alternatively you could use winscp which is part of putty (I think). It copies files using ssh.

---

### Post by HittingSmoke on 2010-07-15
> **brettg said:**
> By far the easiest way is to use samba. The default config should pretty much "just work". 

From there you need to add a user;

```
sudo smbpasswd -a *username*
```

and configure a share in /etc/samba/smb.conf

```
[myshare]
path = /path/to/dir
directory mask = 755
create mask = 755
browseable = yes
```

This is a basic, not terribly secure config but it will be enough for a start.

Alternatively you could use winscp which is part of putty (I think). It copies files using ssh.

Awesome thanks!

I got that all set up and now I can see files, but it won't let me write. I try to move files and I get an error in Windows saying I need permission to do this.

I've tried setting the permissions on my public_html directory to relaxed settings and it still doesn't help.

Security isn't really an issue with me. It's in a virtual machine so it's only up for short periods of time to test web code changes. I just need access to the file system.

*EDIT*

More specifically I get:

> Destination Folder Access Denied
You need permission to perform this action
public_html

I've tried adding "read only = no" to the settings as well.

I've done chmod 755 on the public_html directory with no results.

---

### Post by brettg on 2010-07-15
Make sure that the unix ownership/permissions on the samba folder allow your user to write to the directory.

While logged into the console using your samba user account do a 

```
cd /path/to/share
``` 

and try to write a file;

```
touch testfile
```

If that works then your samba config needs tweaking, if you cant write to the directory even in unix then it is a filesystem permission problem.

---

### Post by HittingSmoke on 2010-07-16
> **brettg said:**
> Make sure that the unix ownership/permissions on the samba folder allow your user to write to the directory.

While logged into the console using your samba user account do a 

```
cd /path/to/share
``` 

and try to write a file;

```
touch testfile
```

If that works then your samba config needs tweaking, if you cant write to the directory even in unix then it is a filesystem permission problem.

I get *permission denied* unless I use sudo

For reference it was tried in /home/user/public_html. My Samba share is set to root so I have access to the full drive since the server is all command line.

---

### Post by brettg on 2010-07-16
OK, assuming your username is "username" you need to assign ownership of the directory to your user;

```
sudo chown username /path/to/dir
```

If there are already files and directories in there then you will need to do the same for them.

```
cd /path/to/dir/

sudo find . -exec chown username {} \;
```

---

### Post by HittingSmoke on 2010-07-16
> **brettg said:**
> OK, assuming your username is "username" you need to assign ownership of the directory to your user;

```
sudo chown username /path/to/dir
```

If there are already files and directories in there then you will need to do the same for them.

```
cd /path/to/dir/

sudo find . -exec chown username {} \;
```

Thank you! Since security isn't much of an issue would it be ok to just use:
```
sudo chown username /*
```
So I can control the entire VM file system from my host machine?

Thanks

---

### Post by brettg on 2010-07-16
No, don't do that, you will break you box!

Whether you are concerned about security or not is irrelevant. 

A lot of files and dirs need to be owned by specific users to work and if you mess with that you will FUBAR your machine. Besides, you can't, say, edit a config file in windows without breaking it because windows uses a weird LF+CR combination and attempting to do so will also break stuff, just in a different way.

---

### Post by HittingSmoke on 2010-07-16
> **brettg said:**
> No, don't do that, you will break you box!

Whether you are concerned about security or not is irrelevant. 

A lot of files and dirs need to be owned by specific users to work and if you mess with that you will FUBAR your machine. Besides, you can't, say, edit a config file in windows without breaking it because windows uses a weird LF+CR combination and attempting to do so will also break stuff, just in a different way.

Ahh ok, so to be safe I shouldn't chown anything outside of my home directory?

---

