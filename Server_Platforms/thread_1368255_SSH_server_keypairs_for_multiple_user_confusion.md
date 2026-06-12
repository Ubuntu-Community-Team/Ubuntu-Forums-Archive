---
title: "SSH server keypairs for multiple user confusion"
date: 2009-12-30
forum: Server Platforms
---

### Post by getut on 2009-12-30
Out of the literally dozens of tutorials out there for configuring Ubuntu's SSH server for public/private key authentication, I haven't been able to find one that clearly explains how the SSH server handles this for multiple users and how keys are mapped to each user.

I have a working SSH server config right now using passwords on a server that is hosting 2 web sites. I have a relatively typical configuration with multiple users. An admin user and a severely limited user who, when logged in via SSH is only able to see their home folder, which is of course the root of their virtual web site.

I have the admin user working via keypairs but am totally lost on how to set up the remaining limited user for key based auth. How do I assign a key to that specific limited account so I can turn off password based auth?

BTW.. I used this tutorial to limit an SSH user to a single folder if that sheds any light on what I have done so far.
[http://www.minstrel.org.uk/papers/sftp/builtin/](http://www.minstrel.org.uk/papers/sftp/builtin/)

---

### Post by Lars Noodén on 2009-12-30
On the server, put the public key for the user in the file ~/.ssh/authorized_keys
That's the default location where sshd looks for the keys.  It can be changed

Normally the permissions for ~/.ssh should be 0700
The permissions for  ~/.ssh/authorized_keys should be 0600

```

#
sudo chown *user*:*user* ~/.ssh/
sudo chown *user*:*user* ~/.ssh/authorized_keys

#
sudo chmod u=rwx,g=,o= ~/.ssh/
sudo chmod u=rw,g=,o=  ~/.ssh/authorized_keys

```

~ is an abbreviation for the user's home directory, which may be anywhere, but the default is /home/*loginname*

The reference for changing the default location for the keys file is [sshd_config](http://linux.die.net/man/5/sshd_config) under **AuthorizedKeysFile**.  If you use encrypted home directories then you will need to customize **AuthorizedKeysFile**.

---

### Post by getut on 2009-12-30
Thanks Lars, but that is the part that still confuses me.

Where do I create the public/private key pairs for the non-admin users?

The user accounts don't exist on remote machines only on the SSH server, but they are limited accounts with no shell.

And another problem I am running into is that there still seems to be some tie to the remote user profile. I'll try to explain what I am seeing...

On the server I have Sadmin and Srestricted as users. On a remote PC I have only Rnormaluser. For testing purposes, I created a new user on the remote PC with the same name as Sadmin and created the public/private key pair from that signon on the remote PC. I moved the public key and restarted the SSH server.

Now, back on the remote PC, I moved a copy of the private key from Sadmins(Remote PC version) .ssh folder to the Rnormaluser .ssh folder. So now on the remote PC, I have the same private key in both the Sadmin and RNormaluser folders. I did some testing.

If I sign on to the Sadmin account on the remote PC and SSH to the server, it works properly!!! Key based authentication!

If I sign on the Rnormaluser account on the remote PC and use the SAME private key I did in the previous test, it fails.

What am I missing. If the key is truly providing the authentication AND the identification to the remote server, then the local user I am signed on to the remote PC with should be irrelevant right?

Wow, thats hard to explain.

---

### Post by BkkBonanza on 2009-12-30
You're getting a bit convoluted with users and keys. It actually is simpler then you describe...

For each user on a machine you generate a key pair and keep it only in that users home - don't copy the private key around. One user - one key pair.
eg. joey -> joey_key, mary -> mary_key

On the server you append the public key for any user you want to allow onto the authorized_keys file. This file can have many keys, one for each allowed user. There is an authorized_keys file in the home of each user on the server that determines who can login AS that user.
eg. 
joey_key >> /home/admin/.ssh/authorized_keys, 
mary_key >> /home/admin/.ssh/authorized_keys,
joey_key >> /home/bob/.ssh/authorized_keys

When you login to the server you don't have to use the name of the actual user on the home (remote/client) machine. You use the name of the account on the server that you want to login to. Whoever logs in obtains the rights of the user he logs in as, not who he is back on the client.
eg. 
server users are admin and bob

from joey machine use, ssh admin@server
will send joey_key which server will accept and login as admin

from mary machine use, ssh admin@server
will send mary_key which server will also accept and login as admin

from joey machine use, ssh bob@server
will send joey_key which server will also accept and login as bob

from mary machine use, ssh bob@server
will send mary_key which server will deny - mary not in bobs authorized_keys


You can have multiple user accounts on the server too, but it isn't required.

---

### Post by getut on 2009-12-30
I think I am getting that part since I have it working for a single user that I created.

The part that I am not getting is how to make this work if I generate the keypair FOR someone else or another machine.

In my case a windows box running winscp, but I also have had no luck generating the keypair from one useraccount and then using it from another account or another PC completely.

Take [server]admin and [server]bob server accounts. I have gotten key based auth to work if I create the key pair from an account named admin on the workstation and then also log in from that [workstation]admin account. If I try copying any parts of the keys that I generated there over to a [workstation]jerry user account in his .ssh folder and then try to log on as [server]admin from [workstation]jerry, I have not gotten it to work yet. And this is all still from linux. I haven't even started testing throwing windows or a second linux machine into the mix yet.

If I generate key pairs on [workstation1]tom, set the public key up on the server for [server]admin, and then copy the relevant keys to .ssh on [workstation2]tom and then try to log in to [server]admin I think I am going to get the same failure I am getting now.

I HAVE to generate these for the people and give them to them. These are not savvy people and generating their own will blow their mind... and in some cases they don't even have linux.

---

### Post by BkkBonanza on 2009-12-30
I believe what you are trying to do should work, althought it's not the intended way for it to work.

You shouldn't ever need to copy the keys from one user to another. The correct way is to generate a new key for each user on their account. Even on Windows I think putty and perhaps winscp have the function built in to generate keys.

The problem with copying the same key around is that it provides reduced authentication because you can't know who is actually logging in, nor keep an audit trail.

But even still I think it should work to just copy keys. You need to be sure to copy both the .ssh/id_dsa and .ssh/id_dsa.pub files. And most importantly you have to make sure the permissions are correct - check they match from a working system to a problem one. And finally you need to make sure the .ssh/id_dsa.pub file is the one you append to the authorized hosts file on the server account you want to access. 

There is a ready made automated script for this provided by ssh - called ssh-copy-id that will copy a key to the server authorized_keys file and set permissions (given that you have password access). See "man ssh-copy-id".

---

### Post by Lars Noodén on 2009-12-31
> **getut said:**
> 
Take [server]admin and [server]bob server accounts. I have gotten key based auth to work if I create the key pair from an account named admin on the workstation and then also log in from that [workstation]admin account. If I try copying any parts of the keys that I generated there over to a [workstation]jerry user account in his .ssh folder and then try to log on as [server]admin from [workstation]jerry, I have not gotten it to work yet. And this is all still from linux. I haven't even started testing throwing windows or a second linux machine into the mix yet.


Try to use key-naming conventions that will let you sort which key goes where.  

Here's one possible way.

Let's say you have three users (bob, joe, amy) with accounts on the server (s1) and on one or more workstations.  

```

+-----+
|  W1 |
| bob +---+
|     |   |
+-----+   |
          |   +-------+
+-----+   |   |  S1   |
|  W2 |   |   | sbob  |
| joe +---+---+ sjoe  |
|     |   |   | samy  |
+-----+   |   | admin |
          |   +-------+
+-----+   |
|  W3 |   |
| amy +---+
|     |
+-----+

```

Generate the keys so that you can keep them straight, making sure to choose good passphrases.

```

ssh-keygen -b 2048 -t rsa -f key_rsa_bob -C "Bob's Key"
ssh-keygen -b 2048 -t rsa -f key_rsa_joe -C "Joe's Key"
ssh-keygen -b 2048 -t rsa -f key_rsa_amy -C "Amy's Key"

```

That will generate a key pair per user, with their username in the file name. That's just one way of doing it.  

```

# public keys end in .pub, private keys don't
$ **ls** 
key_rsa_bob
key_rsa_bob.pub
key_rsa_joe
key_rsa_joe.pub
key_rsa_amy
key_rsa_amy.pub

```

Copy the private keys to the user's accounts on their workstation (W1 - W3) and put them in the .ssh under the user's home directory.  There's no harm in copying the public key. Make sure that the permissions are set correctly.

```

# for example
mkdir /home/bob/.ssh

chown bob:bob /home/bob/.ssh
chmod u=rwx,g=,o=  /home/bob/.ssh
chmod u=rw,g=,o=   /home/bob/.ssh/key_rsa_bob
chmod u=rw,g=r,o=r /home/bob/.ssh/key_rsa_bob.pub

```

Copy the public keys (and only the public keys) to the server and place each one inside the file **authorized_keys** inside the .ssh directory inside the user's home directory.

That should allow them to use their private key on their work station to log into their account on the server.

```

sftp -i /home/bob/.ssh/key_rsa_bob sbob@*S1.xx.yy.zz*

```

If you are using a version of ssh earlier than OpenSSH_5.3, the sftp client might have trouble finding the key, so use an agent first.

```

# if the agent is running, load a key with a passphrase
ssh-add /home/bob/.ssh/key_rsa_bob 

# connect
sftp sbob@*S1.xx.yy.zz*

```

---

### Post by getut on 2009-12-31
> **Lars Noodén said:**
> Try to use key-naming conventions that will let you sort which key goes where.  


Lars, that is a great set of instructions. Clear and concise, while also helping me understand the general concept of what I need rather than just blindly following instructions and not understanding what I'm doing... I thank you for taking the time to write that up!

I will post back with the results!

---

### Post by Gourgi on 2009-12-31
nice catch lars :popcorn:
clear indeed!

---

### Post by Lars Noodén on 2010-01-03
> **getut said:**
> I will post back with the results!

That would be awesome.  

Thinking about it, it is also possible to do host-based authentication.  For that the hosts authenticate to each other with their keys and then a list of approved groups are allowed to log in.  That's very different to set up, but if you have lots of users on the same machines, it may save you more work in the long run than making keys for each user.

---

