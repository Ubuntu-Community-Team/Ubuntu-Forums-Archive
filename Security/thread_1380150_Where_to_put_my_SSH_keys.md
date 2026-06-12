---
title: "Where to put my SSH keys?"
date: 2010-01-13
forum: Security
---

### Post by pstein on 2010-01-13
I have generated SSH *.pub and *.ppk keys.
 
Where should I put them so that they are automatically used and available when e.g. issuing an
 
ssh ....
 
command in Terminal?
 
Peter

---

### Post by cdenley on 2010-01-13
Are you connecting from putty to ubuntu? If so, public keys which can authenticate are stored in ~/.ssh/authorized_keys, one per line.

---

### Post by cariboo on 2010-01-13
If you follow this [howto]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys"), the keys are automagically put in the correct place.

---

### Post by cdenley on 2010-01-13
> **cariboo907 said:**
> If you follow this [howto]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys"), the keys are automagically put in the correct place.

Except they seem to be using a putty client, since they have a thier private key in a .ppk file.

---

### Post by bodhi.zazen on 2010-01-13
> **cdenley said:**
> Except they seem to be using a putty client, since they have a thier private key in a .ppk file.

Server side it is the same, putty or no, the .pub key goes in ~/.ssh/authorized keys (or alternate location if you change).

client side, it does not matter , you can keep the keys anywhere you wish with putty and store your preferences. With ssh you have to specify the key or add it to RAM with ssh-add.

---

### Post by pstein on 2010-01-14
> **cdenley said:**
> Are you connecting from putty to ubuntu? If so, public keys which can authenticate are stored in ~/.ssh/authorized_keys, one per line.
 
I want to connect from Ubuntu to a remote Solaris machine.
 
Folder ~/.ssh  exists but not /authorized_keys
 
The keys are already generated. Do I have to create manually the subdir /authorized_keys and put the keys into?
 
Again: I don't want to connect from another remote machine to local Ubuntu but the other way round: I want to connect through SSH comand line command to remote machine. E.g. for setting up a SSH tunnel
 
Peter

---

### Post by cdenley on 2010-01-14
> **pstein said:**
> I want to connect from Ubuntu to a remote Solaris machine.
 
Folder ~/.ssh  exists but not /authorized_keys
 
The keys are already generated. Do I have to create manually the subdir /authorized_keys and put the keys into?
 
Again: I don't want to connect from another remote machine to local Ubuntu but the other way round: I want to connect through SSH comand line command to remote machine. E.g. for setting up a SSH tunnel
 
Peter

Openssh in ubuntu does not use putty's private key format. Generate new keys with ubuntu as described in the howto linked to previously.

authorized_keys is a FILE on the SERVER which tells sshd which public keys are allowed to connect. You need to add the public key generated in ubuntu to the authorized_keys file in your user's home directory (~/.ssh/authorized_keys) on the Solaris server you are connecting to. The private and public key generated in ubuntu should then be placed in your ~/.ssh directory in ubuntu.

---

### Post by bodhi.zazen on 2010-01-14
Generate the keys on the CLIENT (ubuntu)

On the SERVER ~/.ssh is a DIRECTORY and ~/.ssh/authorized keys is a file containing a list of public keys, one per line, allowed to access the server.

On the CLIENT (Ubuntu) use the command

```
ssh-copy-id -i ~/.ssh/key_name user@server
```

[http://linux.die.net/man/1/ssh-copy-id](http://linux.die.net/man/1/ssh-copy-id)

---

### Post by pstein on 2010-01-14
> **bodhi.zazen said:**
> Generate the keys on the CLIENT (ubuntu)
 
On the SERVER ~/.ssh is a DIRECTORY and ~/.ssh/authorized keys is a file containing a list of public keys, one per line, allowed to access the server.
 
On the CLIENT (Ubuntu) use the command
 
```
ssh-copy-id -i ~/.ssh/key_name user@server
```
 
[http://linux.die.net/man/1/ssh-copy-id](http://linux.die.net/man/1/ssh-copy-id)
 
Ok, thank you.
From what have read "ssh-copy-id" is used to copy my pub ssh key to the remote server. Is the command usable if the remote OS is NOT Linux/Ubuntu but Solaris?
 
Do I have to put both - my private and my public OpenSSH key into my ~/.ssh folder?
 
Peter

---

### Post by bodhi.zazen on 2010-01-14
> **pstein said:**
> Ok, thank you.
From what have read "ssh-copy-id" is used to copy my pub ssh key to the remote server. Is the command usable if the remote OS is NOT Linux/Ubuntu but Solaris?

I would assume so, but I do not run a Solaris server, but you can answer the question for us very fast by giving it a try ;)
 
> Do I have to put both - my private and my public OpenSSH key into my ~/.ssh folder?
 
Peter

You may keep these files wherever you wish. The default location is ~/.ssh

As has been explained several times on this thread, the .pub key goes to the server, into ~/.ssh/authorized_keys, one key per line. Once the file is on the server you do not need it on the client, you can delete it if you wish.

You can change the location on the Server by editing /etc/ssh/sshd_config on the server.

You can change the location of the key on the client to wherever you wish, you simply specify the location in the command.

ssh -i ~/.ssh/key user@server

or, if you prefer

ssh -i /full/path/to/some/alternate/location/wherever/you/like/your/key user@server

---

