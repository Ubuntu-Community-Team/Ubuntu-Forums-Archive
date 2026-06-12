---
title: "MPI SSH without password?"
date: 2019-12-12
forum: Server Platforms
---

### Post by josephchrzempiec on 2019-12-12
Hello This question is way above my head. I'm helping a friend of mine Who needed 9 Virtual Machine each one is using ubuntu server and openssh. Well 1 master host  and 8 slave node. Systems  so the master node is ubuntu 18.04 desktop the 8 other virtual michanes are ubuntu server 18.04. I know nothing about programing I'm more of hardware. I just only recently figure out how to setup a Virtual system. 

So my question is as painless as i can get how can i setup a way for openssh server to be passwordless? here is his question from email.


[FONT=Arial]Hi Jay,[/FONT]

[FONT=Arial]The message passing software, MPI, needs to be able to ssh into the[/FONT]
[FONT=Arial]slave nodes without a password.  Currently the system is not configured[/FONT]
[FONT=Arial]to do that.  As a result, when I try to run my application, I get the[/FONT]
[FONT=Arial]following messages:[/FONT]

[FONT=Arial]johnb@johnbhost:~/terra$ mpiexec -n 8 -hostfile hostlist ./terra &[/FONT]
[FONT=Arial][3] 16334[/FONT]
[FONT=Arial]johnb@johnbhost:~/terra$ Permission denied, please try again.[/FONT]
[FONT=Arial]Permission denied, please try again.


Can someone please help me?



joseph[/FONT]

---

### Post by howefield on 2019-12-12
Thread moved to the "*Server Platforms*" forum.

---

### Post by josephchrzempiec on 2019-12-12
Hello thank you. Sorry still new to the fourms i wasn't sure where to post this at.

---

### Post by TheFu on 2019-12-12
For each client machine and userid, you must make an ssh-key. The command to do that is:
```
ssh-keygen -t ed25519
```

For each client-side userid -to- remote server, you need to push the public ssh-key (never the private), to the remote server.  The command to do that is:
```
ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote
```

The "username" is optional and not needed if the same between the client machine and remote server.
"remote" can be a DNS name, IP address, some manually setup lookup inside the /etc/hosts or configured in the ~/.ssh/config file.

This only needs to be done once between the username@client and username-whatever@server.  Don't screw with the ~/.ssh/ directory permissions or any file permissions inside.  ssh-copy-id does the right thing.  Test using **ssh username@remote**. No password should be requested.

These keys will work for ssh logins, scp, sftp, rsync, sshfs, x2go, and most backup tools.  There must be 50 other tools that support ssh connections.

To make your life easier, the client-side ~/.ssh/config file is really handy for using a different port, different userid, making ugly dns-names into something short and memorable.  The ssh_config manpage has all the settings possible.  These are client-side only.

---

