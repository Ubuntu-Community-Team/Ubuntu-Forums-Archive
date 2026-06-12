---
title: "Ubuntu Server 12.04 - Group Permissions Not Working"
date: 2013-02-13
forum: Server Platforms
---

### Post by swift29 on 2013-02-13
Hi all,

I installed Ubuntu Server 12.04 to set up as a file server for my windows computers. Everything is going well except one function I would like to include that doesn't seem exsist, prevent deleting. I have spent days searching how to do this with no luck. What I wanted was my user to have full permissions and prevent the other users from deleting as I want them to be able to add to the share but not mess with the files.

Now I think I figured a way around it. I have two users, alex and izzie, alex (me) has all the root controls. I also added a group nodel which alex is part of.

What I can do is:
```
sudo mkdir /test
``` 
```
sudo chown alex:nodel /test
```
```
sudo chmod 2777 /test
```
Here is my samba conf
```

...
[Test]
comment = test
path = /test
browsable = yes
guest ok = no
writeable = yes
create mask = 0575
force create mode = 0575
directory mask = 0575
force directory mode = 0575
....

```
This then enables both users to write to the directory test, and prevents izzie from being able to delete any file. Now my theory was as alex is in the nodel group and it is set to group write only then I would be able to delete both files, annoyingly I cant delete izzie's.

Here are some potentially helpful outputs:
```
ls -l
drwxrwsrwx 4 alex nodel 4096 feb 12 21:31 test

ls -l /test
dr-xrwsr-x 2 alex nodel 4096 Feb 12 21:31 alex
dr-xrwsr-x 2 izzie nodel 4096 Feb 12 21:31 izzie

```

Also, I have tried sticky bit and this doesnt work how I want either.

Is this a screw up of permissions on my behalf, did I miss something to get group write working?

If not is there another way I can disable delete for all other users apart from myself when in a windows enviroment?

Thanks in advance, Alex

---

### Post by nothingspecial on 2013-02-14
*Thread moved to **Server Platforms**.*

---

