---
title: "Apache and file permissions"
date: 2012-06-20
forum: Server Platforms
---

### Post by mitchell2345 on 2012-06-20
Hi,

I created a web server that a user can upload files to via SMB to /var/www.  When doing so the user logs in as their Ubuntu account (user1) from their Windows PC.

When the files copy over the are owned by user1 with -rw-rw----

The problem is when Apache tries to read the files its access denied.

If i change the permissions to -rw-rw-r-- and change the owner to root:root it works.

How can I change it so that whenever the user copies a file over Apache and read the files as-is and I don't have to update anything?

Thanks,
Mitchell

---

### Post by rukiaEnix on 2012-06-20
You can run Apache or just a VirtualHost as root.
Or think of other way of uploading this files. Just tell me if you think will be a good idea to run Apache as root and I'll tell you how.
But it will be better to run only a VirtualHost as root.

---

### Post by kanikilu on 2012-06-20
Why do you need to chown the files to root:root for the webserver to be able to read them? I'd think the permissions change would be enough...

Also, to automatically set the permissions, look into setting a create mask for that samba share.

---

### Post by mitchell2345 on 2012-06-20
okay my mistake....all i need to do is chown +r and i can view it.  I do i make Samba give this access?

---

### Post by koenn on 2012-06-20
+1 for kanikilu
and don't even think of running apache as root;

if a create mask is insufficient, you may need to set a 'force group' in samba, or a setguid on the directory, or put the user accountsin the www-data group, that sort of thing.

---

### Post by mitchell2345 on 2012-06-20
i figured out the create mask in smb.conf.

I am just running apache how ever apt set it up.  is that okay?

---

### Post by rukiaEnix on 2012-06-20
Yes it will be better a mask for samba

---

### Post by kanikilu on 2012-06-20
> **mitchell2345 said:**
> I am just running apache how ever apt set it up.  is that okay? Should be fine running as www-data.

---

### Post by SeijiSensei on 2012-06-20
Another option is to use the "force user" and "force group" parameters in Samba like this:

```

[website]
path = /var/www
force user = www-data
force group = www-data
etc.

```

Now no matter who logs into the share with SMB, files they save will be owned by the www-data user and group.  If you don't care about auditing and knowing which user created which file, it's a very simple and robust solution.

---

### Post by bab1 on 2012-06-20
I'd like to add a few thoughts here.  Most of these methods mentioned it this thread are are kind of hackish in nature.  The EXT file system as it is implemented in Debian distros is really what needs to be configured.

This is very easily done (more later).  Additionally, Samba is a poor choice for what you are trying to do.  It only works in a LAN environment or over a VPN (more complexity).  Internet access to upload files, even if it's down the road should be  consideration.

That being said, I know nothing about Apache and which user/group runs it, so I would have questions of you also.  

In the end I believe you could configure the file system structure (/var/www) with group access and control with the SGID bit (Set Group ID) and use sshd with  SFTP clients to upload files.  This is scalable and extensible.

If you are interested let me know and I will be glad to explain more.

---

### Post by Habitual on 2012-06-20
> **koenn said:**
> ...don't even think of running apache as root...

What "he" said.

---

### Post by SeijiSensei on 2012-06-20
> **bab1 said:**
> Samba is a poor choice for what you are trying to do.

Did it cross your mind the OP might need to support Windows users posting files to the server?  Perhaps he's running a server on an office network.  Have you ever administered a mixed network with both *nix and Windows systems?  I have.  Samba is a fine choice if your user base is largely running Windows and simply needs to drop the occasional HTML file or other document into a web site.

> That being said, I know nothing about Apache and which user/group runs it, so I would have questions of you also.

Given this comment, your entire response seems a bit arrogant.  Do you really think none of us know about things like SGID bits, SFTP, and the like?  Before you stride in here and act like you're the only informed person here, perhaps a bit of humility is in order?

---

### Post by bab1 on 2012-06-20
> **SeijiSensei said:**
> Did it cross your mind the OP might need to support Windows users posting files to the server?  Have you ever administered a mixed network with both *nix and Windows systems?  I have.  Samba is a fine choice if your user base is largely running Windows and simply needs to drop the occasional HTML file or other document into a web site.
Sure I thought about it.  I've been maintaining heterogeneous networks for 20+ years now.  WinSCP works fine for Windows users who need to access via SFTP (SSH).  Samba is not the only way to access a Linux server by Windows clients.>  

Given this comment, your entire response seems a bit arrogant.  Do you really think none of us know about things like SGID bits and the like?  Before you stride in here and act like you're the only informed person here, perhaps a bit of humility is in order?

I'm not trying to be arrogant.  If the OP knew about it, he wouldn't have asked for help.  None of the other folks have mentioned the SGID configuration either.  As a matter of fact, I haven't seen anybody else in this thread advising setting up the file system using SGID.  

Using SGID is the proper way to do this and there are plenty of references to this via Google.  So I thought I would ask.  I'm not forcing anybody to follow what I say.  I'm only offering some thoughts about a solution.  If you feel offended I would say that would be *your problem* not mine.

---

