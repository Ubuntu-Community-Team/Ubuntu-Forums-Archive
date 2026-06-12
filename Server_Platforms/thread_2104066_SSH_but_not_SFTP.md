---
title: "SSH but not SFTP"
date: 2013-01-12
forum: Server Platforms
---

### Post by ductiletoaster on 2013-01-12
Alright, I just setup a new Ubuntu 12.04 LTS server with a LAMP stack + Including OpenSSH server.

This users directory is located...
```

/var/www/vhosts/test.com/

```

Where the name of the user is test
I created this user via...
```

useradd test
passwd test

```

Now I also changed the users shell to bash after i realized that it was defaulted to sh.

Once I had setup ssh and the users home directory I then tried to sftp in with the users creds to no avail. (I have confirmed SFTP does work for root)

So my question is how can I activate sftp for this user?

I just checked the auth.log and found the following
```

Jan 12 00:44:26 TC1 sshd[4814]: error: Could not load host key: /etc/ssh/ssh_host_ecdsa_key
Jan 12 00:44:26 TC1 sshd[4814]: Accepted password for TEST from XX.XX.XXX.XXX port 60247 ssh2
Jan 12 00:44:26 TC1 sshd[4814]: pam_unix(sshd:session): session opened for user TEST by (uid=0)
Jan 12 00:44:27 TC1 sshd[4826]: subsystem request for sftp by user TEST
Jan 12 00:44:27 TC1 sshd[4814]: pam_unix(sshd:session): session closed for user TEST

```

Further research as uncovered the following thread on another site...
[http://www.unix.com/linux/161311-users-cant-sftp-into-my-server.html]("http://www.unix.com/linux/161311-users-cant-sftp-into-my-server.html")

After I too tried to manually run the sftp-server I get the following error
```

Couldn't open /dev/null: Permission denied

```

ls -l of /dev/null shows
```

crw------- 1 root root 1, 3 Jan  8 14:40 /dev/null

```

I am wary to change anything until i get confirmation that this indeed is the issue as the above link suggests

---

### Post by ductiletoaster on 2013-01-12
Alright sure enough this was the issue... I fixed it by changing the permissions on /dev/null
```

chmod 666 /dev/null

```

From what I can tell this is the correct action to take but if a better solution is found plz PM me. Thanks!

---

### Post by hawkmage on 2013-01-12
The /dev/null should have a permissions mask of 666 so what you did would be the correct solution.  

Do you have any idea how it got switched?

---

