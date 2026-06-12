---
title: "Multiple users"
date: 2016-02-27
forum: Server Platforms
---

### Post by kambiz2 on 2016-02-27
Hi,
I've got a shared folder in my Ubuntu 14.04 server. This folder is shared with windows user's, for this reason I've create everyone of these users in the server and added in the same group.
My question is: is there anyway that these users doesn't appear in the session login or ask for user and password?

Thanks very much

---

### Post by nerdtron on 2016-02-28
> This folder is shared with windows user's, for this reason I've create  everyone of these users in the server and added in the same group. 

I'm assuming the folder is shared using samba? When the users try to access a samba share from windows you can select the checkbox remember password so that they won't be asked for a username/password again.
Another option would be to make a "Map network drive" on the My Computer of windows computers so they can see the share when they open my computer. I believe this will save the username/password too.

---

### Post by kambiz2 on 2016-02-28
Thanks nedtron, but this is not what I exactly want. In fact, I want to avoid see al the users in the login screen. For this, the best solution I've found till now, has been to install lightdm and configurate it to ask for username and password, instead of listing all the users.
Sorry for my english and thanks again for helping me.

---

