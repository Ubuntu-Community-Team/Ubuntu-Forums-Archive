---
title: "Samba File Server"
date: 2007-06-13
forum: Server Platforms
---

### Post by johng4 on 2007-06-13
I'm trying to get a file server with the following setup..

/storage/public
This will be a publically accessible folder on the network, that anyone (without a user name) can access the files/folders in this directory.

/storage/private
This will be only accessible to user on the network who have user accounts on the server.  As it stands I have a bind mount in each user's folder which points to this directory, where the users have full permissions on the folders within.


The problem I'm having so far, is that when I attempt to access the Public share, I get prompted for a login, and none of my logins work.  I've check permissions on the folder, and it is set to rwx for all (u/g/o).  

The second problem is that when I create the Private shares, I can't access the folders at all either.

Lastly, I have a subnet on my network, which I have isolated for different reasons.  It can not access my network shares at all.

---

### Post by dannyboy79 on 2007-06-13
here's for accessing the share without a password: [http://ubuntuforums.org/showthread.php?t=323046](http://ubuntuforums.org/showthread.php?t=323046)

as far as the different subnet thing, well you need to at least be in the same workgroup. also, if you want to know what to add to your smb.conf, just read the man pages: man smb.conf
and it will give you every option that's in there. i myself use usernames and password, the default smb.conf for security is "user" which means that whoever is trying to access secured share will have to be a user within yoru ubuntu system and you'll also have to add that same person to the smbpasswd database. I use "user" so I can't tell you how the other option work, "share" but I think it's way less secure and I don't think requires users to be on your system or be in the smbpasswd db but I could be wrong. if you don't want to create ton's of users on your ubuntu but still want to use the "user" security, then you can use a username.map file which maps the windows usernames to an ubuntu username. and password as well.

---

