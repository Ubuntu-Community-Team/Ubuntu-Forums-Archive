---
title: "rsa keys"
date: 2009-11-11
forum: Security
---

### Post by kpholmes on 2009-11-11
im looking to lock down my server after some "wierd" looking failed log in attempts noticed in the auth.log and ive been looking over some of the documentation on making rsa keys, but i have one question.

do i make the keys on the client then upload the public key to the server, and make a key for every computer i log in from?

or

do i make the key on the server and then pass the private key to all of my client computers?

thanks

---

### Post by FuturePilot on 2009-11-11
I assume you're talking about SSH keys. You want to create the key on the client. It will create 2 keys, one private key and one public key. The private key always stays with you on the client side. You put the public key on the server. Even then it probably won't eliminate people trying to brute force their way in. You probably will want to completely disable password authentication and go strictly with key based authentication and even change the ssh daemon to a non-standard port.

---

### Post by kpholmes on 2009-11-12
awesome!

thanks.

---

### Post by kpholmes on 2009-11-12
so can i take that private key from the original client, and give it to another client to connect to the server? or do i have to make a key for each individual computer connecting to the server?

---

### Post by FuturePilot on 2009-11-12
> **kpholmes said:**
> so can i take that private key from the original client, and give it to another client to connect to the server? or do i have to make a key for each individual computer connecting to the server?

Yes, you can use the same private key on every client.

---

### Post by Lars Noodén on 2009-11-12
When you put the key pair on a new client make sure that the .ssh directory and the keys have the right permissions.

chmod u=rwx,g=,o= ~/.ssh
chmod u=rw,g=,o= ~/.ssh/key
chmod u=rw,g=,o= ~/.ssh/key.pub

They should be viewable by your account only.

---

### Post by kevdog on 2009-11-14
> **Lars Noodén said:**
> When you put the key pair on a new client make sure that the .ssh directory and the keys have the right permissions.

chmod u=rwx,g=,o= ~/.ssh
chmod u=rw,g=,o= ~/.ssh/key
chmod u=rw,g=,o= ~/.ssh/key.pub

They should be viewable by your account only.

Wouldn't the above really be simplied by just using:

chmod 700 ~/.ssh ~/.ssh/id_rsa ~/.ssh/id_rsa.pub

---

### Post by falconindy on 2009-11-14
> **kevdog said:**
> Wouldn't the above really be simplied by just using:

chmod 700 ~/.ssh ~/.ssh/id_rsa ~/.ssh/id_rsa.pub

```
chmod 700 ~/.ssh/{,id_rsa,id_rsa.pub}
```
If you really wanna save keystrokes. However, it's wrong. Your public key needs to be readable by the world. Hence, public. It needs 644 permissions.

---

### Post by Lars Noodén on 2009-11-16
> **falconindy said:**
> ```
chmod 700 ~/.ssh/{,id_rsa,id_rsa.pub}
```
If you really wanna save keystrokes. However, it's wrong. Your public key needs to be readable by the world. Hence, public. It needs 644 permissions.

The public key *can* be world-readable, but it doesn't have to be.  IMHO, that translates as should not be readable unless there is a specific reason to make it readable.  When it's in your own .ssh directory, it shouldn't be.  

Roll down to the section "Files" in the manual for ssh-keygen:
  [http://linux.die.net/man/1/ssh-keygen](http://linux.die.net/man/1/ssh-keygen)

---

### Post by Trebaruna on 2009-11-16
> **Lars Noodén said:**
>  IMHO, that translates as should not be readable unless there is a specific reason to make it readable.
There's zero security risk in having it be world readable, because it's a public key. It can safely be distributed to whomever you'd like, even Mallory.
Besides, in this case it's sitting in your home folder which is only user readable anyway...

Also, wouldn't ```
chmod -R 700 ~/.ssh/
``` work? Even though it leaves the key user readable only...

---

