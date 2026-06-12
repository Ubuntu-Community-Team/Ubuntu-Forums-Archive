---
title: "SAMBA in 8.10"
date: 2008-11-05
forum: Server Platforms
---

### Post by ingeva on 2008-11-05
First time I set up Samba (in 8.04) it took me 5 minutes.
All connections worked fine.
All I did was to follow the directions, and it worked the
first time I set it up.

Now, with 8.10, the only connection I can make is with Windows.
That is, Windows can see Linux and transfer files,
but I can't see the Windows shares from Linux.
That may not have anything to do with SAMBA.

I used exactly the same setup files for SAMBA in 8.10 and 8.04.

The real problem is that Linux can't see Linux, but
maybe it would be easier (and better?) to install nfs instead?

---

### Post by grep65535 on 2008-11-05
> **ingeva said:**
> First time I set up Samba (in 8.04) it took me 5 minutes.
All connections worked fine.
All I did was to follow the directions, and it worked the
first time I set it up.

Now, with 8.10, the only connection I can make is with Windows.
That is, Windows can see Linux and transfer files,
but I can't see the Windows shares from Linux.
That may not have anything to do with SAMBA.

I used exactly the same setup files for SAMBA in 8.10 and 8.04.

The real problem is that Linux can't see Linux, but
maybe it would be easier (and better?) to install nfs instead?

I'd like to see the solution to this also ...
:popcorn:

---

### Post by ercdvs on 2008-11-05
Post your smb.conf file.

I did notice in 3.2 that samab likes you to rename the smb.conf file to smb.conf.master, and run it through a process to cut down the smb.conf to its 'working' config.

I have needed to edit my vista workings for a proper sharing between 8.10 and vista.. and I can pull and push fine.

Connecting to my server from my intrepid laptop was a simple matter of using smb://servername/share

I do admittedly have yet to try and connect to anything *from* the server..   

How are your shares set up ?

---

### Post by williehowe on 2008-11-05
I'm having a slightly different problem, when I try and browse to the server, nothing ever shows up...

---

### Post by ingeva on 2008-11-05
> **ercdvs said:**
> I did notice in 3.2 that samab likes you to rename the smb.conf file to smb.conf.master, and run it through a process to cut down the smb.conf to its 'working' config.

You just gave me an idea. I used my old smb.conf file instead of making a new one based on the new installation. I think I'll try that first. But my existing smb.conf file lies at [http://paystation4.com/smb.conf](http://paystation4.com/smb.conf) if you want to look at it.

> **ercdvs said:**
> Connecting to my server from my intrepid laptop was a simple matter of using smb://servername/share
I do admittedly have yet to try and connect to anything *from* the server..   
How are your shares set up ?

These things have always worked before, and the setup is unchanged. But I wonder if I should remove samba altogether. I'm scrapping the old computer running Windows, but I can still use it to transfer the files over to the Ubuntu maschine.

---

### Post by ercdvs on 2008-11-06
> **ingeva said:**
> You just gave me an idea. I used my old smb.conf file instead of making a new one based on the new installation. I think I'll try that first. But my existing smb.conf file lies at [http://paystation4.com/smb.conf](http://paystation4.com/smb.conf) if you want to look at it.



These things have always worked before, and the setup is unchanged. But I wonder if I should remove samba altogether. I'm scrapping the old computer running Windows, but I can still use it to transfer the files over to the Ubuntu maschine.

Your conf is pretty wierd.  You have '/' mapped, but you have 'invalid user = root' .. so, unless you went and gave different permissions to /, only root has permissions to that directory, and root is unable to log in

here is my conf file :

[global]
        server string = %h server (Samba, Ubuntu)
        auth methods = sam, winbind
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        client NTLMv2 auth = Yes
        max log size = 1000
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

[photo]
        comment = Photos
        path = /home/master/photo
        read only = No

the original smb.conf has everything set to default, except for :

security = user    

is no longer commented out.   This config allows me to connect from any linux or windows machine in my house to my server.  The given username & password is the linux user..   all of my stuff is saved under /home/username

---

### Post by ingeva on 2008-11-06
> **ercdvs said:**
> Your conf is pretty wierd.  You have '/' mapped, but you have 'invalid user = root' .. so, unless you went and gave different permissions to /, only root has permissions to that directory, and root is unable to log in


OK, that can be removed. Don't know when I inserted that but it didn't affect my 8.04 configuration.

Thank you! I'll do it all over again. Took me 5 minutes the last time, and if the smb.conf requirements have changed I'll find out about it.

Anyway I think NFS would be better for the future. Windows is OUT, so I probably won't need SAMBA more than a day or two.

---

