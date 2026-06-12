---
title: "Samba and Directory Security help?"
date: 2008-04-17
forum: Server Platforms
---

### Post by garfonzo on 2008-04-17
Hiya,

I have a question about using Samba, sort of. I have a server (currently test server until I figure all the bugs out) which will be serving media files to a few computers on a LAN. The computers will be WinXP, Vista and Ubuntu boxes. 

Here's my problem/question. I set up a share for a directory through Samba which is defined as follows:
```

[Music]
  path = /Documents/Music
  read only = No
  guest ok = Yes
  public = Yes
  browseable = Yes
  create mask = 0666
  directory mask = 0777

```

Now, I've realized that in order for people on the LAN to be able to actually create and save files in that directory, the permissions on the directory itself needed to be changed. So I set the permissions on the directory to this:

```

drwxrwxrwx  4 root root 4096 2008-04-14 21:09 Music

```

Now, this makes me concerned about security having this directory, basically, open to public use like this. Am I setting this up right? Is this how a directory shares its contents on a LAN? Are there any security tips to make this tight, or is this good?


Thanks for your help!

Garfonzo

---

### Post by lintoolman on 2008-04-18
If you want every one on the LAN to be able to read and write, your file permissions are correct.

But I'll give you something to consider.  

My wife takes ton's of pictures and our home network they are the "crown jewels" to be protected no matter what.  So I created a group called "pictures" and only placed my wife's account in it.  Next, I set the ownership and group such that my wife owns the files and the group is "pictures" with r/w/x.  Users not allow to write.  This takes care of the filesystem side.  

I configured Samba to force the group "pictures" and set the create masks to ensure new files are created with the proper owner/group and permissions.

Maybe if you have a need to control the music being placed on your LAN, this setup might be better.

---

