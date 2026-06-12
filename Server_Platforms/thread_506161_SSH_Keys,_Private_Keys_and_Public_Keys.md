---
title: "SSH Keys, Private Keys and Public Keys"
date: 2007-07-21
forum: Server Platforms
---

### Post by sefs on 2007-07-21
Hi all

Need some security guru explanations for the below...

What are all these keys (and support files) for and what do they mean and do i really need them....

I have ssh installed and NX Server which also uses ssh.

This question comes about because i was fiddling with putty-gen to see if i could just generate a private/public key not for anything in particular, but just so i can have a prv/pub key pair.

But somehow I think putty-gen automatically updated my keys somewhere without asking me because now when i log into ssh i have to enter a passphrase.  I had set a passphrase in the putty-gen request.  Before when I sshed i didnt have to enter a passphrase.  

Does putty-gen update your keys whereever they are stored without permission?

Now onwards with this question ...

This is all the stuff i have gathered from my computer what does each mean/represent

AuthorizedKeysFile     %h/.ssh/authorized_keys2   <--- this is in /etc/ssh/sshd_config file

 
/etc/ssh/ssh_host_dsa_key
/etc/ssh/ssh_host_dsa_key.pub
/etc/ssh/ssh_host_rsa_key
/etc/ssh/ssh_host_rsa_key.pub


/usr/NX/share/keys/server.id_dsa.key

/usr/NX/etc/keys/node.localhost.id_dsa
/usr/NX/etc/keys/node.localhost.id_dsa.pub

/home/<username>/.ssh/authorized_keys2
/home/<username>/.ssh/id_dsa
/home/<username>/.ssh/known_hosts


Why I am trying to find out about this is I want to be comfortable in setting up ssh and NX ect.  and be confident in generating a key public and private, and knowing where to put them.

For instance in the NX login screen options there is a key in there, not sure if its public or private, and what associates it self with in the above file listings.

Anyone care to give an indepth but understandable explanation? :)

---

### Post by elst on 2007-07-21
This document is technically a draft, but it covers how to use keys and agents:

[http://www.elsn.org/downloads/ssh/html/]("http://www.elsn.org/downloads/ssh/html/")

---

### Post by sefs on 2007-07-21
Based on reading the draft and some other post, I came to the conclusion that ones i had password auth and PAM auth on in the ssh config that I dont really need keys unless i want to specifically authenticate via a key so I deleted all my keys...

That is..

/etc/ssh/ssh_host_dsa_key
/etc/ssh/ssh_host_dsa_key.pub
/etc/ssh/ssh_host_rsa_key
/etc/ssh/ssh_host_rsa_key.pub

/home/<username>/.ssh/authorized_keys2
/home/<username>/.ssh/id_dsa
/home/<username>/.ssh/known_hosts

where username is the user i want to log into the machine which houses the ssh server.

Now when I try to log in I get...
Connection closed by UNKNOWN

Why is that.

Thanks.

---

### Post by sefs on 2007-07-21
Ok, so i should not have deleted the SSH host keys, which I presumed were generated on installation of the ssh server.  Once regenerated, its back in business again.

These host keys are located at

/etc/ssh/ssh_host_dsa_key
/etc/ssh/ssh_host_dsa_key.pub
/etc/ssh/ssh_host_rsa_key
/etc/ssh/ssh_host_rsa_key.pub

and can be regenerated using ...

```

sudo ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N ""
sudo ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key -N ""

```

I believe these are used to identify the server to the client ... to let the client know the server is authentic where by if the client has the public key of the server it can verify the server via the private key that is held by the server.

---

### Post by elst on 2007-07-21
I think that the easiest thing to do is probably to take a break, then reinstall openssh-server, because it looks like you are currently shooting in the dark a bit. The user private key was just the "id_dsa" file.

Key-based authentication is much more convenient and secure, but as you say, the default configuration uses PAM to authenticate with the main password for each user, so you probably don't need to modify any settings to use that method with NX. I don't use NX myself, so I can't advise on that.

EDIT: It looks like you've got it.

---

### Post by sefs on 2007-07-22
Description of keys above as far as i can gather...

AuthorizedKeysFile     %h/.ssh/authorized_keys2 
------------------------------------------------
Tells ssh server where to look for the file that contains 
public keys of clients who have the corresponding private keys which can then connect to it via 
public/private key session.  This is loacated in sshd_config.  For instance if you try to log in as foo
ssh server will look into /home/foo/.ssh/authorized_keys2.  If you try to log in as evil_doer, ssh server
will look into /home/evil_doer/.ssh/authorized_keys2 for the public half of the private key that evil_doer
should have. If not found, tough luck for Mr. Evil Doer.


/etc/ssh/ssh_host_dsa_key         
/etc/ssh/ssh_host_dsa_key.pub
/etc/ssh/ssh_host_rsa_key
/etc/ssh/ssh_host_rsa_key.pub
------------------------------------------------
Above are ssh host keys.  The first time a client connects the server passes one of the public keys to the client.
The client can accept this key permanently (it is then stored in its known_hosts file on ssh client machine for future use), 
OR it can accept the key for one time use, OR it can reject the key if it suspects the server is an evil doer :).  
sshd_config has values that instruct ssh server where these keys are located.

/usr/NX/etc/keys/node.localhost.id_dsa   <-- no idea what these are for
/usr/NX/etc/keys/node.localhost.id_dsa.pub <-- no idea what these are for


/usr/NX/share/keys/server.id_dsa.key
--------------------------------------
private key generated by nxserver for client use - a client must have this key in order to connect to the remote nxserver
by default this is generated on install.  Any nx client will have this private key set up to connect without too much hassle.
If this is a security concern you can generate your own pub/priv key pair and copy the priv key to any nx client that needs
access to the nxserver machine.
see more info at [http://www.nomachine.com/ar/view.php?ar_id=AR01C00126](http://www.nomachine.com/ar/view.php?ar_id=AR01C00126)
This is the private half of /usr/NX/home/nx/.ssh/default.id_dsa.pub below

/usr/NX/home/nx/.ssh/authorized_keys2  
----------------------------------------
public key used to authenticate remote nx client

/usr/NX/home/nx/.ssh/default.id_dsa.pub
---------------------------------------
public key used to authenticate remote nx client (imported into file /usr/NX/home/nx/.ssh/authorized_keys2 
above automatically on installation).  
This is the public half of /usr/NX/share/keys/server.id_dsa.key above.

/usr/NX/home/nx/.ssh/known_hosts 
--------------------------------
Known trusted nx servers. In actual fact just a list of the public keys of the known trusted ssh servers where an nx server resides.

/home/<username>/.ssh/authorized_keys2
---------------------------------------
This resides on the ssh server and contains the public key of the client that wishes to connect to the server 
via public/private key authentication.  Therefore you can have a multitude of clients that can generate 
Public/Private keys, and all these public keys can be for instance appended to /home/<username>/.ssh/authorized_keys2
whereby each client can now connect to the user "username" on the machine where the ssh server is running. Each using
its own seperate private key for authentication.  Of course this is provided the ssh server is set up for public/private
key authentication.  Question is if you don't trust a client any longer how do you remove this key from the authorized_keys2
file.


/home/<username>/.ssh/id_dsa  
---------------------------------------
private key on ssh client which is used to verify client to ssh server if public/private authenticaton is set up. This does
not neccessarily have to be in the /home/<username>/.ssh/ folder.  It can be anywhere on your file system. In that case you
would just need to specify the -i parameter in the ssh command to tell the client where to find the private key. like so,
ssh myserver -i /path/to/privatekey/id_dsa

/home/<username>/.ssh/known_hosts  
---------------------------------------
This file resides on ssh client machine and contains the public keys of all trusted SSH Servers the client is aware of.  
It uses these keys to verify that a ssh server being connected too is a trusted server and not an evil doer :).

---

### Post by elst on 2007-07-22
These look about right. Note that by default SSH tries to use key-based authentication, and then falls back to requesting a password (you may notice a slight pause). These means that you can use keys simply by adding the public key as a line in /home/<user>/authorized_keys2 on the server, but it also means that evildoers can still try to access your server by password cracking, unless you disable the option to fall back to password authentication as well.

---

