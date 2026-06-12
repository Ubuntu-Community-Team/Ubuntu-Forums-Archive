---
title: "Permissions between owncloud and ubuntu users"
date: 2016-03-13
forum: Server Platforms
---

### Post by marta2 on 2016-03-13
Hi,
I'm new in Ubuntu and Owncloud. More or less I've got all configured and work everything fine.
But I've got some problems with the permissions.
I've got 2 servers, ubuntu 14.04.02 server and Windows Server 2008. I share an ubuntu folder with windows users. Till here everything ok.
Owncloud users can, also, access to this shared folder. And here is when my problem begins. To make possible the owncloud user's access to this folder, I have to do:
- add the owncloud user to ubuntu's user
- add the owncloud user to the group of the folder
- add the owncloud user to samba
I'm sure there is another way to make this easier and surer. I don't like the idea to have onwcloud users in ubuntu's users.

Does anybody have any idea?
Thanks

---

### Post by nerdtron on 2016-03-15
I've encountered this also. I have samba ad owncloud. And since management of samba is done manually, you have to do those sequence of commands manually too. Then again, I've moved on, why use samba of each user have their own owncloud accounts? So I removed samba altogether and switched to owncloud. The only samba share I've got is one that I use for an admin account.

Anyway, for your situation, you can try a quick and dirty solution using a script that will:
1. Scan the owncloud user database table if a new user is added:
2. Then process it to: 
- add the owncloud user to ubuntu's user
- add the owncloud user to the group of the folder
- add the owncloud user to samba
3. Run this script probably every hour. Depending on how often you add user accounts.

---

### Post by kambiz2 on 2016-03-15
Thanks nerdtron, I've decided to do another thing. All my Windows are added to samba. And from Owncloud I've decided to configurate every external folder with a username and a password, which I've added also to samba.
With this I can know if a file or folder is added from the owncloud user or windows user.
In the shared folder I've got a folder for every costumer (owncloud user), so, in this folder can only read, write, execute this costumer or windows users.
That's good for me, perhaps there is a better solution but I've not found it.

---

