---
title: "Ubuntu as a NAS"
date: 2010-05-07
forum: Server Platforms
---

### Post by comatosed on 2010-05-07
Hi 

i'm setting up a NAS using samba for local LAN and a secure ftp for remote access with the following users, groups, folders and access restrictions.

users - Lee, Hafsa, John, Dave, Frank
Groups (members)- Accounts (John, Lee), Management (Lee, Hafsa), Everyone (Lee, Hafsa, John, Dave, Frank)
Folders (group access)- Sales (Accounts, Management), Projects (Everyone), Business(Management)

obviously this is not the total structure, but from this i will be able to workout the rest of the setup.

i've already created the users and groups in Ubuntu

Should i be using smaba 3 or 4?

which secure ftp server should i use. i need ftp to be disabled. ive already setup ssh.

Thaks

---

### Post by powerofpi on 2010-05-07
For this kind of application I would highly recommend FreeNAS... even though what you are asking is doable with Ubuntu, Ubuntu is a general purpose OS with far more functionality than you need.

---

### Post by sylvester_0 on 2010-05-07
That's great - I came in here to recommend FreeNAS as well. Give it a try!

---

### Post by comatosed on 2010-05-07
Thanks for the heads up on the freeNas. But i'm after settup info using ubuntu 10.4.

Thanks

---

### Post by badman35 on 2010-05-07
> **comatosed said:**
> Thanks for the heads up on the freeNas. But i'm after settup info using ubuntu 10.4.

Thanks


I tried the ubuntu home server thing and I always got somthing wrong in the setup. 

I have been a happy freeNAS user for bout 7 years now. I don't like the fact that it is bsd (would like an all DEB house) mixing commands is not good.

---

### Post by arrrghhh on 2010-05-07
Sounds like the OP really wants to stick with Ubuntu.  Which, if they ever want their server to do more than just NAS, it can.

To the OP: I'd use samba3, just because samba4 is not nearly ready for production.  You said your users/groups are already setup, I use Webmin to manage those + samba, NFS, all the goodies - makes it very easy.  If you have ssh setup, you already have sftp setup mate :D

---

### Post by DaF1oh1 on 2010-05-07
I like to use Samba, its relatively easy to install once you know how to do it :P I'll quickly show you:

edit /etc/samba/smb.conf
And to add a share put to the bottom of the file:

 [Sharename] (Thats the share name of the file, so when you open it in windows explorer, it will say whatever you write there
        comment = Share on fileserver (Any comment will do)
        path = /data (the path of the share on the linux box)
        valid users = chuckn (The users who are authorized to access the file
        public = no
        writeable = yes
        create mask = 0765

After you have done that, you need to create an Samba password so that your user can log in so for example:
smbpasswd -a chuck n
And then it will prompt you to type the password for your user

Last but not least, make sure the permissions are set on the directory so that your user has access on the Linux box, if he doesn't have access there, then he definitely won't have access remotely so change ownership and/or permissions:
chown chuckn /data
chmod 700 /data

then it restart the smb service:
/etc/init.d/samba restart


Then it should all work, I hope this helps :)

---

### Post by CharlesA on 2010-05-07
Ubuntu as well as FreeNAS will do the job.

If you want to use Ubuntu to configure Samba and whatnot, it would probably be simpler to use Webmin or something similar to do the configuration, since it's GUI-based and editing .conf files just sucks.

Just my $0.02

---

### Post by DaF1oh1 on 2010-05-08
> **CharlesA said:**
> it would probably be simpler to use Webmin or something similar to do the configuration, since it's GUI-based and editing .conf files just sucks.

Simpler, But, I do say, learn how to use the conf files to learn how it works in the background imo, that way you can be more technical with it.

---

### Post by comatosed on 2010-05-08
Guys
 
thanks for all your help so far. here's where i'm at.
 
since the last post i did, i downloaded the freenas. i managed to set up multiple users and multiple groups, but not multiple access when using the additional group thingy. i also set up the ssh & ftp (sftp) so i could putty & filezilla in. i just have probs with the multiple user in multiple group access. ultimately, i like the interface and the software but still nto what the thread is all about. i may start another thread on the freenas thingy. But here, lets focus on the SAMBA please
 
everywhere i go i get info of how to set up a single user to a single share. this is not what i want. i have multiple users, groups and folders. entering the users name one by one is not really an option as there are alot of employees, my original request was as a pointer.
 
i've not managed to use the web admin interface yet, but will give it a go later today or tomorrow. i've used SWAT, back in the day and i really don't mind the command line. i didn't think it would be this difficult. i figured it would be a few simple commands!?!?!
 
 i've used Linksys NAS drives before and are very simple and easy to use. they've lacked the group membership feature, but the point & click folder permissions for each user is a breeze. i'm not a computer scientist, just a tinkerer who doesn't mind getting his hands dirty.
 
all help so far greatly appreciated. but the original question still stands. pls help
Thanks

---

### Post by CharlesA on 2010-05-08
You can set permissions for each share to different users/groups in smb.conf or just use linux file permissions to do that.

```
[Bob]
        comment = Share Folder
        create mode = 660
        invalid users = clone,htpc
        path = /array/bob
        write list = charles,bob
        directory mode = 770

```

The file permissions are set like so:
```
rwxrwx--- 14 bob bob 4096 2010-05-03 21:01 /array/bob
```

My user is added to the 'bob' group.

---

### Post by memilanuk on 2010-05-08
Turnkey Linux has a Fileserver appliance install that might be just what you're looking for... still using 8.04.3 LTS though, haven't migrated to 10.04 yet.

---

