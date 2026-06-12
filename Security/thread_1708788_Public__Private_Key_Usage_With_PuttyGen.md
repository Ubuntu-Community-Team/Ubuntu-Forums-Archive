---
title: "Public / Private Key Usage With PuttyGen"
date: 2011-03-17
forum: Security
---

### Post by 980045 on 2011-03-17
Hi,

I've been trying to get public / private keys working with SSH / Putty and had mixed the results.  Finally I got it working fine with a public / private key but when I've done that it breaks my installation with NX.

I think its down to one using RSA and the other using DSA.  Can anyone confirm this is the case and if so how can I get both working at the same time...

Regards

Dave.

---

### Post by mimor on 2011-03-17
I don't understand the question.
So you've created a DSA or RSA keypair.
You've included your public key on the server ~/.ssh/authorized_keys file?

What are you doing and what do you get in return?

---

### Post by 980045 on 2011-03-17
Hi,

Sorry for not making myself clear...

With puttygen I created a RSA key and got Ubuntu working with that but then I notice my NX stops working.

I think it's because NX uses's DSA keys...

I'll try and generate the NX error again.

---

### Post by bodhi.zazen on 2011-03-17
> **980045 said:**
> Hi,

Sorry for not making myself clear...

With puttygen I created a RSA key and got Ubuntu working with that but then I notice my NX stops working.

I think it's because NX uses's DSA keys...

I'll try and generate the NX error again.

Yes, Nx uses keys. 

I do not know the "solution" as I do not use NX because of this issue.

If you use ssh , I highly advise you simply use ssh -X rather then NX.

There is a discussion of some of the issues here:

[http://alandoyle.com/tutorials/setup-freenx-under-ubuntu/](http://alandoyle.com/tutorials/setup-freenx-under-ubuntu/)

I do not know how up to date it is, but it claims you can not disable password authentication, which would be another big disadvantage IMO.

See also this thread :

[http://ubuntuforums.org/showthread.php?t=1062942](http://ubuntuforums.org/showthread.php?t=1062942)

You can list multiple keys in the key file, one per line, rather then using two separate files.

Post back if you do not understand that concept ^^

---

### Post by 980045 on 2011-03-17
Ok I'm really struggling now! :-(

I've followed this post and really cant get public / private keys working at all under 10.10 and I've followed quite a few articles...

The most recent is [http://www.wowtutorial.org/tutorial/22.html](http://www.wowtutorial.org/tutorial/22.html)

Can someone please give me a step by step guide on how to get this working.

I'd like to create the keys using PuttyGen on Windows and then use those keys on my Ubuntu server.

Regards

Dave.

---

### Post by bodhi.zazen on 2011-03-17
You can generate the keys any way you wish.

You put the contents of the public key in ~/.ssh/authorized_keys on the server, one key per line.

See: 

[http://bodhizazen.net/Tutorials/SSH_keys](http://bodhizazen.net/Tutorials/SSH_keys)

[http://bodhizazen.net/Tutorials/SSH_keys#Manual](http://bodhizazen.net/Tutorials/SSH_keys#Manual)

Using the manual method, put the public putty key on the server, you can do this with winscp or a flash drive.

Then

```
cat <your_public_putty_key> >> ~/.ssh/authorized_keys
```

If it is not working it could be any number of problems, the two most common are:

1. You need to forward the port from your router to your ssh server.

2. Permissions of the key file (make them 400).

---

### Post by 980045 on 2011-03-17
To be able to run this I need to sudo before cat which takes me to the %h of root, am I right?

cat <your_public_putty_key> >> ~/.ssh/authorized_keys

---

### Post by 980045 on 2011-03-17
Also what is the command to restar the sshd on Ubuntu...

---

### Post by bodhi.zazen on 2011-03-17
> **980045 said:**
> To be able to run this I need to sudo before cat which takes me to the %h of root, am I right?

cat <your_public_putty_key> >> ~/.ssh/authorized_keys

No, you do NOT run that command as root (sudo). You run it as the user you log in with via ssh.

Of course if you are ssh in as root, that is not the best practice, keys or otherwise, but it can be done. In that event make sure you disable password authentication.

> **980045 said:**
> Also what is the command to restar the sshd on Ubuntu...

```
sudo service ssh restart
```

---

### Post by cariboo on 2011-03-17
If you want to start the server, just type:

```
sudo service ssh restart
```

the client doesn't need to be restarted.

---

### Post by 980045 on 2011-03-17
when I do ssh-key gen

It says generating public/private rsa key pair
enter file so it shows /home/david/.ssh/id_rsa:
enter passphrase
enter same passphrase
open /home/david/.ssh/id_rsa failed: permission denied

what should the permissions be on my /home/david/.ssh directory

---

### Post by bodhi.zazen on 2011-03-17
> **980045 said:**
> when I do ssh-key gen

It says generating public/private rsa key pair
enter file so it shows /home/david/.ssh/id_rsa:
enter passphrase
enter same passphrase
open /home/david/.ssh/id_rsa failed: permission denied

what should the permissions be on my /home/david/.ssh directory

Well, now you are running in circles. You started with puttygen and now you are using ssh-keygen.

I doing so, you are making this more complicated then it really is.

See the page I gave you or stay with puttygen. Personally I make the keys with openssh (ssh-keygen), give them a name, and import them to putty.

[http://bodhizazen.net/Tutorials/SSH_keys](http://bodhizazen.net/Tutorials/SSH_keys)

Permissions are another topic, and if you need I suggest you take a look at :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

For ssh you need to tighten permissions a bit, again see the link I gave you.

[http://bodhizazen.net/Tutorials/SSH_keys#Login](http://bodhizazen.net/Tutorials/SSH_keys#Login)

I discussed permissions there =)

~/.ssh needs rwx permissions from your user, and so, use 700.

~/.ssh/authorized_keys needs rw (600) and once it is working you can change it to ro (400) , although other permissions will work.

---

