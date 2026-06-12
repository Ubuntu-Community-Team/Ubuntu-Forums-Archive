---
title: "Configure SSHD so it accesses authorized_keys as root"
date: 2014-08-01
forum: Security
---

### Post by Gr33nGapion on 2014-08-01
This is my first time setting up an SSH server so that it only accepts RSA keys for authentication. I noticed that when I run ssh in debug mode with this command:
```
$sudo /usr/sbin/sshd -ddd
```

I get these peculiar debug lines in the server just as the client is attempting to authenticate:
```

...
debug1: temporarily_use_uid: 1001/1001 (e=0/0)
debug1: trying public key file /home/public/.ssh/authorized_keys
debug1: fd 4 clearing O_NONBLOCK
debug1: matching key found: file /home/public/.ssh/authorized_keys, line 1
...

```

uid 1001 matches the user account which I am attempting to use to log in named "public."
The authorized_keys file is located in /home/public/.ssh/authorized_keys with permissions 600, owner=public.

HOWEVER. I plan on giving the credentials for this user account to several different people and I would prefer it if the authorized_keys file was owned by ROOT so that they can't just copy in a new public key and add access to a third party. When I simply make the file owned by the root user, the server prints this on a debug line:
```

Could not open authorized keys '/home/public/.ssh/authorized_keys': Permission denied

```

Is there something I can do in the sshd config file to make the server access the authorized_keys file as root?

Any help is appreciated.

---

### Post by SeijiSensei on 2014-08-02
Don't give multiple people the credentials for one account.  Give them separate accounts.  If there are files that need to be shared, put the users into a group and control access to the shared files that way.

---

### Post by Gr33nGapion on 2014-08-02
I understand that's the preferred way to do it, and in the long run I probably will end up doing that. This is mostly just for testing purposes at the moment. 

However, even in that case, I want to require each user to make a request to me to add a new public key to the authorized_users list. I don't want them to have the ability to add new keys whenever they want.

I should have also mentioned previously that I'm using OpenSSH_5.9p1 Debian-5ubuntu1.4, OpenSSL 1.0.1

---

### Post by Lars Noodén on 2014-08-02
Giving them separate accounts is definitely the way to go.  If they're all using one then it's too hard to figure out who is doing (or has done) what.  

However, if you still do not want them to be able to add, modify, or remove keys then you can change the [AuthorizedKeysFile](http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html) directive in /etc/ssh/sshd_config.  For example:

```

AuthorizedKeysFile /etc/ssh/authorized_keys/%u

```

That would need the directory /etc/ssh/authorized_keys/ to be mode 755 or 751 and then the files within it mode 644.  That way the files can still be owned by root but readable by the account logging in.  

Further, if you do not want those restrictions for all your users you can set *AuthorizedKeysFile* for just a group of users via *Match*.

---

### Post by Gr33nGapion on 2014-08-02
This is EXACTLY what I needed. Thank you so much!

For anyone else reading this solution, /etc/ssh/authorized_keys/%u is a directory with a file with all the authorized public keys for each username. e.g.
/etc/ssh/authorized_keys/user1
/etc/ssh/authorized_keys/user2
/etc/ssh/authorized_keys/user3

---

