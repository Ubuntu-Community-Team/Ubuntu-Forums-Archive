---
title: "Samba permissions issue"
date: 2012-01-19
forum: Server Platforms
---

### Post by rwslippey on 2012-01-19
Ok I'm working on a server for home/home office use...

I've got a folder called "dev" for which I plan to use as a web dev sandbox. I want to write and read protect it just because I'm paranoid lol.. So here is the setup

directory is /home/data/dev/   owned by nobody  group is developers

my username is a member of the group developers and permissions are set to 770

but I still can't access it.

Smb.conf has write list as @developers

any ideas?

---

### Post by rwslippey on 2012-01-19
This just proved that assumptions are a horrible thing.

I assumed because the group was on the write list it was included in the read list...

just added the read list = developers to smb.conf and it works now....

:popcorn:

---

