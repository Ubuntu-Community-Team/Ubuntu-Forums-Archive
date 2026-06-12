---
title: "partitioning an 80gb hd for servers"
date: 2007-07-17
forum: Server Platforms
---

### Post by lunaz on 2007-07-17
just want to make sure this would work ok before i install:

10gb for ubuntu install
10gb for /var?
1gb for sweap
rest for /home

is that a good idea? i'm gonna start with the lamp intall & mess w web servers, then try mail, file servers as needed/wanted.

---

### Post by johng4 on 2007-07-17
Here's my layout for one of my servers which uses an 80GB and 200GB drive.

1GB for /boot - reiserfs
2GB for swap
10GB for / - xfs
40GB for /var - xfs
27GB for /home - xfs

And then...
200GB for /storage - xfs

Depending on what you're going to do with it, putting "all remaining" in /home may be pointless.  As in, if you're going to be the main user on the system, forget about your home folder and use /var instead (or /usr/share... whatever folder it is).  If you're going to have multiple users on the system, then giving each user about 3GB to play with is generally more than generous unless its a file server of some type.

My server above is an extranet server.  I host my groupware, web development, and intranet off of it.  User accounts aren't a high priority.  Most of their data is symlinked to the /var and /storage folders for personal blogs, and file storage.  I use their /home directories to store their rsync backups.  Eventually when my other server gets repaired, I'll have it push those backups in archive form to my cache server.

So...

/storage/public/user1 -> rsync -> /home/user1/backup/public
/storage/private/user1 -> rsync -> /home/user1/backup/private
/home/user1/public_html -> rsync -> /home/user1/backup/home



In this case, I'm not really even letting my users use their home directories outside of FTP, which even then, they'll most commonly follow a symlink to their /storage folder.

So.. basically, depending on your use of the server, you have many options.

---

### Post by lunaz on 2007-07-17
hm, thanks for the reply. i'm still trying to understand most of this stuff. :P

me & my roommate will have accounts on that computer but only i will be able to do admin stuff, if that makes a difference. she'll need to use it as a desk top & print things off it for school.

does this make a difference in how to partition stuff?

---

### Post by johng4 on 2007-07-17
significantly heh

I was assuming that the setup would be that of a server setup.  But this appears to be a home setup instead.

Ok.. in that case, try this...

1GB for /boot - reiserfs
1GB for swap
15GB for / - xfs
63GB for /home - xfs

Might be more for the / than others would recommend, but I always give my / enough room to expand beyond the needs I would push on it.

---

### Post by lunaz on 2007-07-17
this is gonna be a server; but will be used by roommate as desktop for a while

---

