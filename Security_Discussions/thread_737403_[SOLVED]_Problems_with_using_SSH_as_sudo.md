---
title: "[SOLVED] Problems with using SSH as sudo"
date: 2008-03-27
forum: Security Discussions
---

### Post by se2131 on 2008-03-27
So I've been trying to fix my problem over at [http://ubuntuforums.org/showthread.php?t=735726](http://ubuntuforums.org/showthread.php?t=735726) , and unfortunately cannot find a way to fix it that way. So here's another stab from a different direction (one that I'm still a bit clueless on).

I'm trying to set up my system so that I don't need to use a password to upload a specific file from my computer to a server via sftp. At the same time, I would like my computer to be accessible via VNC over SSH.

In other words, in the VNC situation, I would like my laptop at home to be the host, and the computer that I'm connecting from to be the client. This works fine

But in the uploading-file situation, I would like my laptop at home to be the client and the remote computer that I upload the file to to be the server. This doesn't work in the manner described in the link above (namely when I use 'sudo ssh...'. It does work when I do 'ssh ...' as a normal user).

I was hoping to accomplish this using only one set of private/public keys, and not a pair for when the laptop is the client and another pair for when the laptop is the server.

Here's what I've done so far:

1)  A la [http://ubuntuforums.org/showthread.php?t=383053&highlight=vnc](http://ubuntuforums.org/showthread.php?t=383053&highlight=vnc) :

```
ssh-keygen -t rsa
```

as a normal user. Generated a passphrase, stored the keys in my normal user home folder in an .ssh directory.

2) ```
cat id.pub >> authorized_keys;chmod 600 authorized_keys
```

3) Configured the /etc/ssh/sshd_config file based on the info in the link in step 1.

OK, so now I have my public and private keys. Public key info stays in /home/[myname]/.ssh/authorized_keys . Private key is on my person, and I'm successfully able to use VNC through this SSH tunnel from any computer w/ internet access. Now for configuring the uploading-specific-file-to-a-server situation...

4) So I have this pair of public/private keys. Public key stays on machine acting as server, and private key must be on the client machine, that much I know. I thought "why not just copy the public key that's on my laptop to the .ssh folder of the ftpserver? I already have the private key associated w/ it stored on my laptop's computer in the /home/[myname]/.ssh folder, so it should work."

And it does work. Somewhat. So I copied the authorized_keys file from my laptop computer to the ftpserver/.ssh directory. As a normal user (not root), I am successfully able to login using sftp without having to enter a password, a condition that I need because I want to update this specific-file on the ftp server every hour or so.

The problem comes when I try and establish this as a cron job. If you follow the link way at the top of this ridiculously long post, you'll see all the gory details. Basically I can't get the cronjob to run as my normal user, and cron runs as 'sudo'. Unfortunately, that screws up things a bit, because the private key is located in the normal user's .ssh directory.

After some searching of the ubuntu forums, I came across this link: [http://ubuntuforums.org/showthread.php?t=76103&highlight=sudo+ssh](http://ubuntuforums.org/showthread.php?t=76103&highlight=sudo+ssh) . Unfortunately, it's not clear whether any of those solutions resolved the OP's problem. I tried copying my private key into /root/.ssh/id_rsa , then making the /root/.ssh file a soft link to /home/[myname]/.ssh, then trying to generate a completely different set of public/private keys . Nothing seemed to work the way I intend it to, the server that I connect to always asks for my password when I do "sudo sftp [login]@[server]", but doesn't ask for it (which I want) when I do "sftp [login]@[server]"

I also stumbled across this, but I had no idea how to get it to work: [http://www.sudo.ws/pipermail/sudo-users/2003-April/001477.html](http://www.sudo.ws/pipermail/sudo-users/2003-April/001477.html) 

Well, I'm sorry for the extremely long post, I just wanted to put all the details in there from the get-go, and repitition to avoid ambiguity. I'm pretty new to ssh stuff, so I'm more considering this a learning experience I guess, so that I better understand how it all works. Thanks for taking the time to get this far, hopefully the solution is obvious to smarter ppl than I.

---

### Post by kevdog on 2008-03-27
Can you summarize the problem -- I kind of got lost in the details of the post.

---

### Post by p_quarles on 2008-03-27
> **se2131 said:**
> But in the uploading-file situation, I would like my laptop at home to be the client and the remote computer that I upload the file to to be the server. This doesn't work in the manner described in the link above (namely when I use 'sudo ssh...'. It does work when I do 'ssh ...' as a normal user).
This is the part I don't quite understand. sftp is a two-way protocol. Unlike some other types of connections, it shouldn't matter one bit which machine is running the server vs. which machine is running the client.

---

### Post by se2131 on 2008-03-27
> **kevdog said:**
> Can you summarize the problem -- I kind of got lost in the details of the post.

My apologies, here's the heart of the problem w/o the background:

I'm trying to use the SSH private key located on my laptop to associate w/ the public key on the remote server. This works fine when I do 'sftp [login]@[server]', basically running sftp as a normal user. The server doesn't ask me for a password, and I can upload a file using a simple script (the intention is to set up a cronjob to upload this specific file every hour, w/o having to enter in a password).

Unfortunately, I can't get cron to run as my normal user, so I'm forced to get this to work as the superuser. But when I do 'sudo sftp [login]@[server]', it always asks me for the password. I tried copying the private key to the /root/.ssh/ directory, copying everything from /home/[myname]/.ssh into that directory, and even creating a soft link that points /root/.ssh --> /home/[myname]/.ssh . Still, it always asks me for a password, which prevents me from running an hourly cron job.

---

### Post by se2131 on 2008-03-27
> **p_quarles said:**
> This is the part I don't quite understand. sftp is a two-way protocol. Unlike some other types of connections, it shouldn't matter one bit which machine is running the server vs. which machine is running the client.

Again, I don't really know too much about secure-protocols. However, the issue is the same whether I use 'sftp' or 'ssh'.

'ssh [login]@[server]' --> doesn't ask for password

'sftp [login]@[server]' --> doesn't ask for password

'sudo ssh [login]@[server]' --> asks for password

'sudo ssh [login]@[server]' --> asks for password

To clarify, the password that it's asking for is not for my sudo account, it's for the FTP server.

The answer may be here: [http://www.sudo.ws/pipermail/sudo-users/2003-April/001477.html](http://www.sudo.ws/pipermail/sudo-users/2003-April/001477.html) . But I can't figure out how to get this to work.

---

### Post by p_quarles on 2008-03-27
> **se2131 said:**
> My apologies, here's the heart of the problem w/o the background:

I'm trying to use the SSH private key located on my laptop to associate w/ the public key on the remote server. This works fine when I do 'sftp [login]@[server]', basically running sftp as a normal user. The server doesn't ask me for a password, and I can upload a file using a simple script (the intention is to set up a cronjob to upload this specific file every hour, w/o having to enter in a password).

Unfortunately, I can't get cron to run as my normal user, so I'm forced to get this to work as the superuser. But when I do 'sudo sftp [login]@[server]', it always asks me for the password. I tried copying the private key to the /root/.ssh/ directory, copying everything from /home/[myname]/.ssh into that directory, and even creating a soft link that points /root/.ssh --> /home/[myname]/.ssh . Still, it always asks me for a password, which prevents me from running an hourly cron job.
Try configuring the identity location in ssh_config. Instead of:
```
IdentityFile ~/.ssh/id_rsa
```
Change it to an absolute path, e.g.:
```
IdentityFile /home/your-username/.ssh/id_rsa
```

---

### Post by se2131 on 2008-03-27
> **p_quarles said:**
> Try configuring the identity location in ssh_config. Instead of:
```
IdentityFile ~/.ssh/id_rsa
```
Change it to an absolute path, e.g.:
```
IdentityFile /home/your-username/.ssh/id_rsa
```

Hey that did it! Thanks for your help, it would've taken me forever to come to that simple solution on my own.

---

### Post by p_quarles on 2008-03-27
> **se2131 said:**
> Hey that did it! Thanks for your help, it would've taken me forever to come to that simple solution on my own.
Glad to help. Just remember to mark this thread "solved" -- that helps make the forum search feature more useful. (it's under the "thread tools" menu at the top of the page).

---

