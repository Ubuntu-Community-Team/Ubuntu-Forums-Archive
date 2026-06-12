---
title: "Can't start SSH Server"
date: 2007-02-13
forum: Server Platforms
---

### Post by tyeracj41 on 2007-02-13
Ok, this is driving me nuts.

I'm trying to get into SSH, just to play around with it. So I figured I would start out by just testing it on my own machine with localhost. So I go to start the server:
> /etc/init.d/sshd start
and I get:
> bash: /etc/init.d/sshd: No such file or directory


I know for sure I have SSH installed. I've apt-get'd the packages: ssh openssh-client openssh-server. I've installed them, removed them and installed them again. And I still get nothing. I've physically looked inside the init.d directory, and there is no sshd file. Only ssh. I've even "whereis sshd". It found it in /usr/sbin/sshd, I tried to copy that over to init.d, but to to avail.

Any help would be great as it is so so so frustrating to be stuck on the FIRST STEP!

---

### Post by highneko on 2007-02-13
Shouldn't it start automatically when you boot? Try something like this:
ssh username@192.168.0.10

---

### Post by PetePete on 2007-02-13
it should already be started. but if you want to restart it do this.
```

cd /etc/init.d
sudo ./ssh restart

```

this is presuming you are using the open-ssh-server , not sure about others

---

### Post by Brazen on 2007-02-13
> **tyeracj41 said:**
> Ok, this is driving me nuts.

I'm trying to get into SSH, just to play around with it. So I figured I would start out by just testing it on my own machine with localhost. So I go to start the server:

and I get:


I know for sure I have SSH installed. I've apt-get'd the packages: ssh openssh-client openssh-server. I've installed them, removed them and installed them again. And I still get nothing. I've physically looked inside the init.d directory, and there is no sshd file. Only ssh. I've even "whereis sshd". It found it in /usr/sbin/sshd, I tried to copy that over to init.d, but to to avail.

Any help would be great as it is so so so frustrating to be stuck on the FIRST STEP!

The command is "/etc/init.d/ssh" not "/etc/init.d/sshd"

---

### Post by icedogchi on 2007-02-25
I tried /etc/init.d/ssh restart and this doesn't work.  In fact, ssh is in my /usr/bin directory!

I'm brand spanking new to linux and Ubuntu, so I've no idea if this is where OpenSSH should be located, or if synaptic put it in the wrong location.

When I try sudo /usr/bin/ssh restart

ssh: restart: Name or service not known

When I try sudo /usr/bin/ssh -restart 
ssh: illegal option -- r
usage: blah blah blah

whereis ssh returned the following:
ssh: /usr/bin/ssh /etc/ssh /usr/bin/X11/ssh /usr/share/man/man1/ssh.1.gz

So what is going on?  

Thanks for any help!
-jt


EDIT:
Okay, turns out I had only installed the OpenSSH client.  Now I am really confused.  I can SSH from my windows XP machine using Putty to my linux box.  So how is that possible with only the OpenSSH client installed.  I thought that required the OpenSSH server.

Would someone be able to correct my brain so I know what is going on?  Thanks!

---

### Post by jtc on 2007-02-25
Do you have a ssh-server installed then? It doesn't come as standard when you install Ubuntu.

```
apt-get install openssh-server
```

(/usr/bin/ssh is simply the client)

---

### Post by icedogchi on 2007-02-25
I do not have the openssh server installed yet, but I plan on doing that.  But before I did, I wanted to make sure I understand what is going on.

I installed openSSH client on my linux box via synaptic.

I installed putty on my windows box.

Using putty on windows, I can SSH to my linux box and successfully log in.

My question, before I install openssh server, is how that is possible?  I thought that openssh server is *required* to remotely log in.  That is, the openssh client only allows me to SSH from my linux box to some other computer.

What am I confused on?  

Thanks!
-jt

EDIT:  Spending a bit more time searching around what is running on my computer, I finally found that I had installed lsh-client and lsh-server.  When I uninstalled these, I could no longer SSH to my machine.  Woot!

So, I figured out my own problem. . .sorry about the post, but hopefully some other linux noob might read this and not spend a few hours spinning his/her wheels!
-jt

---

### Post by mjv on 2008-06-18
By default ubuntu seems to install the gnu lsh server, which in turn puts a file in /etc/ssh/sshd_not_to_be_run which blocks openssh-server from running at the same time. I would advise removing lsh-server, or at least removing

1) /etc/ssh/sshd_not_to_be_run
and
2) /etc/init.d/lsh-server

then again, this may be a whole other problem.

ciao

Matthieu

---

