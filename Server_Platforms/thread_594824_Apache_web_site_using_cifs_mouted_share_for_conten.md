---
title: "Apache web site using cifs mouted share for content"
date: 2007-10-28
forum: Server Platforms
---

### Post by swiftangelus on 2007-10-28
Hello all,

I am trying to get my apache server to view content in a cifs mount folder. The folder is mounted OK but Apache is not able to view the content. I am hoping tobe able to brose to my file store without having to copy all of the data onto the web server.

One thing that is bugging me is that the permissions on the mount point are drwxrws--- I suspect that Apache is requiring the "other" permission to enable access?

I am using LDAP for central user management and the cifs share is on a NAS.

Any help on this is appreciated.

Cheers

---

### Post by HermanAB on 2007-10-28
Using CIFS on a web server is not a good idea, since it is a horribly insecure and broken protocol.  You should be able to make it work, but your server won't remain un-hacked for very long...

You should rather try NFS (in TCP mode) over Stunnel.  You could also run CIFS over Stunnel, but it is slower.

There are millions of reason why not to do CIFS or plain NFS on a web server.  Some Googling will clue you in to the issues.

Cheers,

Herman

---

### Post by MJN on 2007-10-28
Perhaps it's me (quite likely!) but haven't you (HermanAB) got the wrong end of the stick here?

It sounds to me like the OP simply has a CIFS-mounted drive and wants to make its contents browsable via an existing web server. Presumably this mount is outside of the existing web root and so has symlinked the mount point to a point within the web tree?

In which case then, yes, it's a permissions issues (your Apache error log should tell you this) - the solution is to either mount the drive as world readable or make Apache (www-data) part of the same group as the mount point and hence accessible using the current permissions.

The underlying file/mount format should not matter as Apache is accessing it at a higher level.

Again, this erroneous stick holding could be mine so feel free to poke me with it! :)

Mathew

---

### Post by swiftangelus on 2007-10-28
Hello,

Thanks for the replies. Yes this is a remote mount to a NAS from the web server and yes it is symlinked to the mount point.

I am interested in two ideas you have both put forward, any chance of more info on how to perform the suggestions?

1. mount the drive as world readable - how do I do this?
2. use nfs over Stunnel - where do I start to read up on this?

Thanks again.

---

### Post by MJN on 2007-10-28
I've no experience of CIFS mounting but, from reading the mount.cifs man page, you could try using the **noperm** option _to prove the principle_. If this works then you ought to mount it exactly as required but someone else will have to step in and advise on what combination of options will suffice.

Mathew

---

### Post by sciurus on 2007-10-28
Why not just set the uid and gid arguments for mount.cifs to be the uid and gid that apache runs as?

Make sure you have smbfs installed and then read the manpage for mount.cifs.

---

### Post by swiftangelus on 2007-10-28
Hello all,

MJN has cracked my issue. the noperms works a treat. I believe that the uid and gid are ignored because the cifs extensions in ubuntu are known. I tried that hoping but they seemed to get ignored. Although when testingI was not trying the www_data user mentioned in this thread. I will try that as well and let you know.

Cheers

---

### Post by swiftangelus on 2007-10-28
OK, looks like the noperms has worked if mounting a folder in my web folder,if it is a symbollic link it still dones not allow teh access, permission denied.

As for th uid and gid, it does appear that they are ignored.

Any other ideas? I am looking into the ln -s command just in case there is a fix in there.

Ta

---

### Post by HermanAB on 2007-10-28
The problem is that if you are using a CIFS or NFS mount to another machine from a public web server, then it implies that the CIFS/NFS server (Windows or Linux) is on the public side of the firewall, which is not a good idea, since DCE and RPC are both hopelessly insecure.

It would be better to firewall the CIFS/NFS server and tunnel through it using Stunnel or SSH.

You can secure CIFS by tunneling the single port 445/TCP, or NFS, by tunneling port 2049 (provided that you set it to TCP in /etc/fstab).

Tunneling NFS is easy, just read the man pages on NFS and stunnel.

Cheers,

Herman

---

### Post by MJN on 2007-10-28
Why must the CIFS server (NAS device) be on the public side of the firewall?

If we've got a web server and a NAS device both sat on a LAN, and this LAN sits on the private side of a firewall/router, if that firewall/router only allows port 80 through (to the web server) then what's the threat?

Mathew

---

