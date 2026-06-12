---
title: "Setting up for passwordless ssh, but only allowed after logging in"
date: 2013-08-09
forum: Server Platforms
---

### Post by MFI-Spencer on 2013-08-09
I setup Ubuntu Server 12.04LTS for passwordless login by adding my public key to the authorized_keys file. However I am only able to login using the key after I have already logged in using the the password and it only works as long as I stay logged in.

---

### Post by hawkmage on 2013-08-09
This is something I have seen with the Desktop edition but not server.  It sounds list the Network Manager is installed and handling the network config.  On the desktop edition the network manager doesn't enable the network until a user logs in.  If the system is actually going to be a server and Network manager is installed I would recommend removing Network Manager and manually configuring the interfaces file.

---

### Post by MFI-Spencer on 2013-08-09
> **hawkmage said:**
> This is something I have seen with the Desktop edition but not server.  It sounds list the Network Manager is installed and handling the network config.  On the desktop edition the network manager doesn't enable the network until a user logs in.  If the system is actually going to be a server and Network manager is installed I would recommend removing Network Manager and manually configuring the interfaces file.

I attempted to run:

```
sudo apt-get purge network-manager
```

But got the message that:

```
Package network-manager is not installed, so not removed
```

---

### Post by cool110 on 2013-08-09
Do you have an encrypted home directory?

---

### Post by MFI-Spencer on 2013-08-09
I was searching around google to fix a problem I was having with FTP and while this did not fix my FTP problem it did fix my passwordless login problem. Running the command:

```
sudo chmod 0755 ~/
```

Now I can login using the key.
I hope that I didn't cause some permissions problem by doing that.

---

### Post by hawkmage on 2013-08-09
I am glad it is working but changing permissions really doesn't make sense, the permissions on a file usually don't change with a login unless there is something in your login profile or you somehow mount a remote or encrypted filesystem for your home.  

With OpenSSH, at leas for versions in the last 10 years, the default is for strict permissions on the ~/.ssh directory when doing key authentication that requires that your ~/.ssh directory is not writable by group or other and the authorized_keys is owned by the user and only the owner has access to it.  
The OpenSSH FAQ recoments the following:
```
chmod go-w $HOME $HOME/.ssh
chmod 600 $HOME/.ssh/authorized_keys
chown `whoami` $HOME/.ssh/authorized_keys
```

---

### Post by MFI-Spencer on 2013-08-21
I am not sure what has happened but it seems I must have used encryption.... 

I have in my notes:

```
User:...
Encrypted
Using LVM
No Proxy
...
```

#-o

The problem now is that it is asking for my passphrase. Is there some way to eliminate this home directory and start over with out actually starting all the way over with system install?

---

### Post by steeldriver on 2013-08-21
If you have an encrypted home directory, then the usual way to deal with that is to move your user's authorized_keys file from their home directory to an unencrypted system directory - usually /etc/ssh/*user*/authorized_keys - and make the corresponding change to /etc/ssh/sshd_config i.e.

```

-- AuthorizedKeysFile    %h/.ssh/authorized_keys
++ AuthorizedKeysFile    /etc/ssh/%u/authorized_keys

```

If you want to login without a password OR passphrase then the way to do that would be to replace you current key pair with one created using no passphrase - obviously that's less secure though.

---

