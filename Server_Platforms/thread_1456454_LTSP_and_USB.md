---
title: "LTSP and USB"
date: 2010-04-17
forum: Server Platforms
---

### Post by kfleten on 2010-04-17
I have a Edubuntu 9.10 LTSP server. Some users can not access local medias like USB drives etc. If I add new users to the system, they DO have access to theese things, the problem is some older users. 

I have tried to remove a old user, and delete his home folder. Then I checked etc/passwd, etc/shadow, and etc/group to make shure he was totaly gone. Then I created the same user again with the same username and password, but with a different userID. The user IS member of the Fuse-group. The problem is still there :-o

What can be wrong ?

---

### Post by kiwicito22 on 2010-04-28
for access local media, the user must be on the group "fuse" just add then and try

[sudo addusser <username> fuse]("http://tuxxeando.blogspot.com/")

---

