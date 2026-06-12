---
title: "Automount single NFS share/export"
date: 2009-06-27
forum: Server Platforms
---

### Post by Lucky. on 2009-06-27
Gah, frustration growing!

Using both Ubuntu 9.04 server and client.

BACKSTORY:

1.  Got Samba working on the server, and my Windows client connects to it very well.  A certain user on the Windows client has a mapped drive to a public share on the server.  Very nice.

2.  For my Ubuntu client, I want to have a mapped drive to the public share just like my Windows client does.  I use "Connect to Server" in Gnome, and save it as a bookmark.  The samba share isn't mounted at login, but clicking the bookmark mounts and works just fine afterwards.  That's reasonable enough.

3.  I decide that "Samba is nice for Windows, but for my Ubuntu client I want to use NFS.  I need to learn it anyway."

4.  I get NFS working fine on the server.  I'm able to mount the public share manually from my Ubuntu client using the following:

```
sudo mount 192.168.1.202:/srv/music /mnt/music
```

(Of course 192.168.1.202 is the address of the server.)

5.  Manually mounting is nice, but I want my mapped drive behavior.  How to do it?  Gnome's "Connect to server" feature doesn't seem to support NFS.

I want to simply automount my single public share, but not have it mapped universally (every user should not have it mapped).  

In my searches, I've found two types of tutorials/forum posts:

1.  People editing their fstab file.  This seems like it will mount the share for everybody...not just certain people.  That's no good.

2.  People automounting a networked home folder using autofs.  This is more on track, but a little too dynamic.  I like my home folder where it's at.  I simply want to mount a single folder...not have users automounting home folders based on their names.  I would really like to see an example of this working with something other than home folders.

Anybody with experience on the subject?  This seems like such a trivial simple thing...an automounted share for an individual user.

---

### Post by TwiceOver on 2009-06-27
I've never done this but couldn't you mount it using fstab and then change the permissions on the mount point?

---

