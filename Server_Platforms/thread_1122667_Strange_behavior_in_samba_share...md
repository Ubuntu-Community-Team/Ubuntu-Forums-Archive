---
title: "Strange behavior in samba share.."
date: 2009-04-11
forum: Server Platforms
---

### Post by fanis on 2009-04-11
Hi all,

The fileserver runs centOS 5.2 x86_64( I am aware that this is the ubuntu forum, but still..) and mounts a 500GB share that all users on the network have access to(rwx access). So, a guy wanted a privete folder inside the share. Allthough I am actualy the webman there, I have a root pass so I tried to help him. 

I logged in as root though ssh and did the following(let's say he is user1)

# cd /home/user/share(the smb share location)
# mkdir user1_private_folder
# chown -R user1:user1 user1_private_folder/
# chmod 700 user1_private_folder/

Well it partially worked. Here starts the stange part;

There was a particular vista machine in the network that continued to have unlimited access to the folder! I logged to the server through ssh with the particular user credentials, and couldn't even read the files, but through the client machine I could do everything! All the other machines in the network(OSX 10.5 windows xp and windows vista clients) couldn't even read it... What do you guys think?

---

### Post by fanis on 2009-04-12
Anyone????

---

