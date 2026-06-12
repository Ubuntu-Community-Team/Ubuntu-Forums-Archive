---
title: "What is *the* way to have a secure /home mounted from server?"
date: 2011-03-07
forum: Security
---

### Post by DizzyCoder on 2011-03-07
The only similar topic regarding my query is this: [http://ubuntuforums.org/showthread.php?t=1145890](http://ubuntuforums.org/showthread.php?t=1145890)

Poster wanted to ensure server did NOT have access to decrypted data.. my query is different in that I'd like to be able to SSH into the server box and have access to my /home/%user data.

So, my question: **What's the acceptable way to have your data (/home folder) securely stored on the server but accessible via remote login and even mounted as /home on a remote machine? **

From my research, I figure it could work if 
[LIST]
[*]user /home folders are encrypted using EncryptFS on server
[*]use PAM to unlock (that's automatically handled I guess?) on login via ssh to server
[*]use NFS to export the EncryptFS file itself for decrypting by remote machine (client)
[/LIST]

I guess the trick is using PAM on the local machine to mount //nfsserver/homeshare/%users_home_file as /home/%user on login

of course.. what do you do if the server is inaccessible? then you can't login.

and what happens if you're logged in via ssh, and then you login with gui and try to mount EncryptedFS again?

Really open to any ideas or pointers in the right direction, can't find any relevant, recent info on exactly this.

---

