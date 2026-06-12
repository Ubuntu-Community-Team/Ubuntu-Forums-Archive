---
title: "Adding key manually"
date: 2011-04-13
forum: Server Platforms
---

### Post by Ceiber Boy on 2011-04-13
How do you manually add keys to a server (no GUI) so that an ssh connection can be made using key authentication?

---

### Post by rubylaser on 2011-04-13
You need to generate a new SSH keypair on the machine you want to start the ssh connection from
```
ssh-keygen -t rsa
```

Assuming that you wish to login to the machine called remote from your current host with the id_rsa and id_rsa.pub files you've just generated you should run the following command:

```
ssh-copy-id -i ~/.ssh/id_rsa.pub username@remote
```

This will prompt you for the login password for the host, then copy the keyfile for you, creating the correct directory and fixing the permissions as necessary.

Now you should be able to ssh into the host using the keys.

```
ssh username@remote uptime
```

If you want, you can make a config file so you don't have to type in username@remote, just host

```
nano ~/.ssh/config
```
Add this information to it

```
host remote
hostname ip_address or fqdn
user root (or whatever user you want to connect as)
identityfile ~/.ssh/id_rsa
```

This would allow you to ssh like this
```
ssh remote uptime
```
and see output like this...
```
09:52:50 up 96 days, 13:45,  0 users,  load average: 0.00, 0.00, 0.00
```

---

### Post by arrrghhh on 2011-04-13
rubylaser, awesome guide!

I'm curious tho, what about copying keys to another machine?  What is the recommended method for doing that?  I ended up blowing away key-based auth for the time being, but I'd like to re-enable it and not create new keys if necessary...

Perhaps just the ssh-copy-id step is all I need... I'll poke around.  Thanks again.

---

### Post by rubylaser on 2011-04-13
Glad to be of service :)  The ssh-copy-id will take care of copying your keys to the appropriate location on the other server.  If you follow these few simple steps, you'll have passwordless ssh working in no time.

---

### Post by Ceiber Boy on 2011-04-15
> **rubylaser said:**
> You need to generate a new SSH keypair on the machine you want to start the ssh connection from
```
ssh-keygen -t rsa
```Assuming that you wish to login to the machine called remote from your current host with the id_rsa and id_rsa.pub files you've just generated you should run the following command:

```
ssh-copy-id -i ~/.ssh/id_rsa.pub username@remote
```This will prompt you for the login password for the host, then copy the keyfile for you, creating the correct directory and fixing the permissions as necessary.

Now you should be able to ssh into the host using the keys.

```
ssh username@remote uptime
```If you want, you can make a config file so you don't have to type in username@remote, just host

```
nano ~/.ssh/config
```Add this information to it

```
host remote
hostname ip_address or fqdn
user root (or whatever user you want to connect as)
identityfile ~/.ssh/id_rsa
```This would allow you to ssh like this
```
ssh remote uptime
```and see output like this...
```
09:52:50 up 96 days, 13:45,  0 users,  load average: 0.00, 0.00, 0.00
```

Thank you excellent guide.

---

