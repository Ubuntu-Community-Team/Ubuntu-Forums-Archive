---
title: "SSH questions"
date: 2010-03-16
forum: Server Platforms
---

### Post by jfmanamtr on 2010-03-16
I have a few qustions about SSH & wanted to see if you guys could help me answer them. I am thinking about setting up ssh keys at my house (trying to automate a backup using rsync). I am just curious about a few things. 
 
Is it possible to do a ssh key & use it off a usb thumbdrive with putty? I remote into my server from work a lot, but I don't want to leave the key on the work computers (they are shared pcs). So I would need to be able to take it with me once I leave. 
 
If I can't do this, then is it possible to only allow the ssh keys to be used on the local subnet & force external address to use user\pass authentication? Thanks for all your help!
 
~John

---

### Post by bodhi.zazen on 2010-03-16
> **jfmanamtr said:**
> I have a few qustions about SSH & wanted to see if you guys could help me answer them. I am thinking about setting up ssh keys at my house (trying to automate a backup using rsync). I am just curious about a few things. 
 
Is it possible to do a ssh key & use it off a usb thumbdrive with putty? I remote into my server from work a lot, but I don't want to leave the key on the work computers (they are shared pcs). So I would need to be able to take it with me once I leave. 
 
If I can't do this, then is it possible to only allow the ssh keys to be used on the local subnet & force external address to use user\pass authentication? Thanks for all your help!
 
~John

Yes you can do this, although putty will need to import your openssh keys with keygen.

[http://linux-sxs.org/networking/openssh.putty.html](http://linux-sxs.org/networking/openssh.putty.html)

---

### Post by jfmanamtr on 2010-03-16
Ok. So, then the ssh keys that I generate are specific to the users & not the machines themselves?
 
~John

---

### Post by bodhi.zazen on 2010-03-16
Yes and no.

A key will be specific to a user on the server, but from the client multiple people can use the same key to log into the server as the user on the server.

Likewise, you may use the same key across servers and users on a server.

In general , one key per user per server.

---

### Post by jfmanamtr on 2010-03-16
Ok. So if I am understanding you right, there is one key per user per server, but I can use the client key on multiple client PCs, So server has UserA & there are 4 PCs. I can generate an ssh key for UserA on the server, but distribute the client key for all 4 of the other PCs, right?

~John

---

### Post by KB1JWQ on 2010-03-16
You can ALSO have multiple keys per user, just append to ~/.ssh/authorized_keys, one per line.

---

### Post by jfmanamtr on 2010-03-21
Ok, had another question in regards to SSH. On my server, I am trying to create a user for these automated backups. I want to be able to chroot this user into it's home directory & disable this user from being able to log in directly to the server (kinda like making the user an ssh-only user). Is this possible?
 
~John

---

### Post by KB1JWQ on 2010-03-21
Not really. Not sure what you're trying to do, but look into scponly.

---

### Post by jfmanamtr on 2010-03-21
I am trying to backup config files from one machine to another using RSYNC. I want to setup a seperate user for the SSH from one machine to another, but I want this user to only be able to be used through the SSH only.
 
~John

---

### Post by KB1JWQ on 2010-03-21
No worries then. Scponly supports rsync.

You owe the oracle a cookie.

---

### Post by jfmanamtr on 2010-03-21
Ok, so scponly is another shell for *nix? 
 
Here is your cookie oh great oracle:
 
[http://www.codeismylife.com/ascii_cookie/48150.html](http://www.codeismylife.com/ascii_cookie/48150.html)
 
~John

---

### Post by bodhi.zazen on 2010-03-21
> **jfmanamtr said:**
> Ok, had another question in regards to SSH. On my server, I am trying to create a user for these automated backups. I want to be able to chroot this user into it's home directory & disable this user from being able to log in directly to the server (kinda like making the user an ssh-only user). Is this possible?
 
~John

Yes this is possible. Make a new user. Give the user a ssh key (so they may ssh in using the key), then disable (lock) the account and disable (ssh) password logins.

---

### Post by jfmanamtr on 2010-03-22
And I am assuming by disable, you mean passwd -l 'username'?
 
~John

---

### Post by kemra on 2010-03-22
> **jfmanamtr said:**
> And I am assuming by disable, you mean passwd -l 'username'?
 
~John

Yes **passwd -l username** to lock/disable the account.

---

### Post by jfmanamtr on 2010-03-25
Ok. I am having issues getting this to work right. I have 2 computers, the server & the laptop. On the server I have userA. On the laptop I have userB. While logged into the laptop as userB, I want to be able to log onto the server as userA by going to the terminal & typing ssh userA@serverIP. 

I go to the terminal on the laptop as userB & issue:

```
ssh-keygen -t rsa
```

I then create .ssh under userA's home folder on the server:

```
ssh userA@serverIP mkdir -p .ssh
```

I then put id_rsa.pub in userB's .ssh folder on the laptop into userA's .ssh folder in the authorized keys file:

```
cat ,ssh/id_rsa.pub | ssh userA@serverIP 'cat >> authorized_keys'
```

Then I try to ssh into the server as userA (ssh userA@serverIP), but nothing happens & eventually the server kills the connection (due to the timeout restrictions I setup). I am not sure what I did wrong. Any ideas on what I can do to make this work?

~John

---

### Post by KB1JWQ on 2010-03-25
Likely a perms issue.

Rather than copying the pubkey to the remote server by hand, why not use:

ssh-copy-id REMOTEHOST

---

### Post by jfmanamtr on 2010-03-25
Ok. I always get confused by this. When you say remote host, are you referring to the computer that I am using ssh to access or the computer that I am at? Which computer should i be generating the ssh-keys on, The computer being access or the computer that I am sitting at? This may help some of my confusion about all this.

~John

---

### Post by KB1JWQ on 2010-03-26
Let's discuss this in the context of a laptop and a server.

I'm on my laptop, all typing is done on said laptop.

I want to generate a new keypair.

ssh-keygen

(I wait while it generates a key)

ssh-copy-id SERVER
It prompts me for a password, I grant it one, and it does the rest for me.

ssh SERVER
And I'm in.

Make sense?

---

### Post by jfmanamtr on 2010-03-26
Yes. Perfect sense. Sorry, I am a little easy to confuse & that was where I was getting to. Thanks for the clarification. I will try this out when I get back to the house tonight. Thanks for all your help!
 
~John

---

### Post by KB1JWQ on 2010-03-26
No worries.  It makes it a LOT easier when you've got many servers.  Past a certain point, it's all about scale.

---

### Post by jfmanamtr on 2010-03-28
Ok. I used the ssh-copy-id 'user@serverIP -p nonstandardport' to copy the id_rsa.pub to the server, but it still doesn't work. When I try to ssh, I get the following:

```
Agent admitted failure to sign using the key
```

Then it gives me a password prompt. I checked & the id_rsa.pub was copied verbatium to the server. Only thing is that the user at the end of the key is the user for my laptop & the laptop's hostname. Is that correct?

~John

---

### Post by jfmanamtr on 2010-03-28
Ok. So, I changed the user in the key & it all looks good now. Thanks for all the help.

~John

---

