---
title: "SSH key authentication, passphase not accepted."
date: 2008-11-23
forum: Server Platforms
---

### Post by pksings on 2008-11-23
I have been trying to get my machine to back up some files to another automatically using rsync and trying to do it using key authentication.

ssh-keygen created the key, asked for my passphrase, I typed it in, successs, key is created. I copied it to the target machine, copied the file to "authorized_keys". 

When I SSH to the target machine it asks for my passphrase, but won't accept it. I have redone this process several times with different passphrases with the same result.

All of the HOWTO's I've found state show all the same steps I have done and that it should be working. Somehow I must have missed something.

Both machines are Ubuntu 8.04 by the way.

Any ideas anyone?

---

### Post by Dr Small on 2008-11-23
Please try this guide, and tell me if it works:
[http://php.8ez.com/drsmall/blog/?p=218](http://php.8ez.com/drsmall/blog/?p=218)

Be sure to remove your old keys for ~/.ssh and the authorized key from the remote server.

---

### Post by Lars Noodén on 2008-11-23
Double check to be sure that you put the **public** key in authorized_keys.  Also check to be sure the permissions for the .ssh directory are 700 and the files therein are 600 and owned by you.

---

### Post by roundhay on 2008-11-25
I've read a few how-tos on setting up keys but I'm still not certain how to set this up.

If I have a server and want to log in from my desktop where shoudl I run the command 

ssh-keygen -t dsa

Should I run this on the server and then copy the public key to the desktop or should it be the other way around?

It seems strange that you should create a key on the desktop and then copy it to the server?

---

### Post by volker48 on 2008-11-25
> **roundhay said:**
> I've read a few how-tos on setting up keys but I'm still not certain how to set this up.

If I have a server and want to log in from my desktop where shoudl I run the command 

ssh-keygen -t dsa

Should I run this on the server and then copy the public key to the desktop or should it be the other way around?

It seems strange that you should create a key on the desktop and then copy it to the server?

It doesn't really matter which system you make the keys on just be sure your secret key doesn't get out. The public key is used to encrypt messages and the private key is used to decrypt those messages. The server authenticates you by encrypting a random character with your public key then you decrypt it with your private key and confirm with the server that the character you received is the one it sent. 

The passphrase is used to encrypt the secret key that way even if it gets stolen hopefully it can't be used. The secret key is decrypted on the local machine so if you are having errors with that then maybe you are having some kind of key board issue like a numlock being on or a caps lock (I just had this problem the other day with someone trying to SSH). 

Basically, the public key goes to the server and needs to be added to the authorized_keys file. Once the public key is copied to the server you want to ```
cat id_dsa.pub >> ~/.ssh/authorized_keys
```

Check this out if you are still lost it helped me. [http://www.ibm.com/developerworks/library/l-keyc.html]("http://www.ibm.com/developerworks/library/l-keyc.html")

---

### Post by Philio on 2008-11-25
> **roundhay said:**
> I've read a few how-tos on setting up keys but I'm still not certain how to set this up.

If I have a server and want to log in from my desktop where shoudl I run the command 

ssh-keygen -t dsa

Should I run this on the server and then copy the public key to the desktop or should it be the other way around?

It seems strange that you should create a key on the desktop and then copy it to the server?

Generate the key on your desktop.
Then add it to the ~/.ssh/authorized_keys file on the server.

This should work :)

---

### Post by amac777 on 2008-11-25
> **Philio said:**
> Generate the key on your desktop.
Then add it to the ~/.ssh/authorized_keys file on the server.

This should work :)

When you put the pulic key on the server in that directory, make sure you put in the home directory for the user you are trying to ssh in as.

---

### Post by roundhay on 2008-11-26
Done thanks for the pointers can now access from my Ubuntu desktop to the server via key and have turned of password access.

Have also managed to install ssh on my puppy linux USB O/S can can access the server via mu work PC over my LAN!

---

