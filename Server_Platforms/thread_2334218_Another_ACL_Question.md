---
title: "Another ACL Question"
date: 2016-08-17
forum: Server Platforms
---

### Post by mcreef on 2016-08-17
Hey all,

From the volume of results searches return, I know this is a well covered subject, so I apologize in advance for the dead horse beating if that is how this reads. I think the overly thick nature of my skull is preventing something obvious from penetrating once again.

I am running a 14.04 server as a file server (to windows clients) with samba.

I have created a directory we will call "/srv/1/2" My intention is to use this as a place for temporary file placement. Anyone with access to it's parent directory "/srv/1" should be able to rwx any file or folder created within the "/srv/1/2" directory, regardless of author. I know I can just add every user to a common group, and be done with it, which I have already done out of frustration, but is there a way to use setfacl to force any new file or directory, created by anyone, to carry rwx permissions for the "others" group? Setting defaults for users and groups seem straight forward enough, but that last bit of the puzzle, getting the others permissions to inherit what I want continues to elude me.

Here is what I have so far...
```
ls -l /srv
drwxr-sr-x someuser somegroup 1

ls -l /srv/1
drwxrwsrwx+ someuser somegroup 2

getfacl /srv/1/2
#file: srv/1/2
#owner: someuser
#group: somegroup
#flags: -s-
user::rwx
group::rwx
other::rwx
default:user::rwx
default:group::rwx
default:group:test:rwx \\This is the group I created to get around problem
default:mask::rwx
default:other::rwx
```

If I create a file from any connected client (lets call it "test.txt") it looks like this...

```
ls -l /srv/1/2
-rwxrwxr--+ someuser somegroup test.txt
```

This works, so long as I create a group and put everyone in it, but this just feels like I've worked around the problem rather than solving it. What I really want, is to see this...

```
ls -l /srv/1/2
-rwxrwxrwx someuser somegroup test.txt
```

I am assuming that this can be done, because me adding 40 or so users, one at a time, to a group that is basically the equivalent of "others", just doesn't seem right. That is what the others group is for isn't it? I am just missing something obvious here right?

This isn't the first time I've run into problems trying to use the others group. It seems like I am throwing away an entire layer of permissions functionality sometimes because I can't get the behavior I want out of that bottom rung on the ladder...

Where am I going wrong?

---

### Post by howefield on 2016-08-17
Thread moved to the "*Server Platforms*" forum.

---

### Post by mcreef on 2016-08-17
Sorry about that. I suppose this would have been a more appropriate placement for my question.

---

