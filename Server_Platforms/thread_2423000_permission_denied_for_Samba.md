---
title: "permission denied for Samba"
date: 2019-07-16
forum: Server Platforms
---

### Post by fredy50 on 2019-07-16
Hello,

I'm trying to setup a Samba service on my ubuntu server.
But i can't access Samba it says permission denied for my users.

[free444you]
path = /media/16tb/007fred
writeable = yes
browseable = yes
public = no
writable = yes
create mask = 0644
directory mask = 0755
force user = sharedrev

photo:
[ATTACH=CONFIG]283629[/ATTACH]

Can someone help me with it, how can i access the samba for my user?

---

### Post by slickymaster on 2019-07-16
Thread moved to **Server Platforms** for a better fit.

Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by Morbius1 on 2019-07-16
There are two different sets of permissions here and I don't know which one is at play.

[1] You are trying to access the server share from your Mac as user sharedrev. 

** Does that user exists on the samba server?

** And did you add that user to the samba password database:
```
sudo smbpasswd -a sharedrev
```

[2] Linux permissions have to allow access to the entire path to the shared folder.

Does sharedrev have access to the entire path:
```
ls -al /media/16tb
```

---

### Post by fredy50 on 2019-07-16
Thanks @[**[COLOR=#000000]Morbius1[/COLOR]**]("https://ubuntuforums.org/member.php?u=982144")

It works now :)

---

### Post by slickymaster on 2019-07-16
> **fredy50 said:**
> Thanks @[**[COLOR=#000000]Morbius1[/COLOR]**]("https://ubuntuforums.org/member.php?u=982144")

It works now :)

Being so, please mark your thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

