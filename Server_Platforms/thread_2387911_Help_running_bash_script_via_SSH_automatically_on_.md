---
title: "Help running bash script via SSH automatically on second server"
date: 2018-03-25
forum: Server Platforms
---

### Post by alextostig on 2018-03-25
Hi,

I have a service running that uses a limited user account, and I want the service to kick off a bash script that connects to a second server to run a script there.

The problem is that I can run the the test.sh script as my usual, fully permitted username, so I know the test.sh script works. I just can't get the service to run the script.

The service is 'Motion' - I'm sure you've heard of it, and it has an on_event_start parameter that can run a bash script. I have it set to run test.sh, which is supposed to connect to the second server via SSH (Raspberry Pi) and run a script there - call it test2.sh. Since Motion is run by the motion user, I think that's the problem. 

I've tried using SSH keys - that works only for my user, so it fails for motion. I tried sshpass with the same results.

Any help is greatly appreciated.

Thanks!

Alex

---

### Post by wildmanne39 on 2018-03-25
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by volkswagner on 2018-03-26
On server1, you can [specify which ssh key to use]("https://www.cyberciti.biz/faq/force-ssh-client-to-use-given-private-key-identity-file/") in the connection command.

---

