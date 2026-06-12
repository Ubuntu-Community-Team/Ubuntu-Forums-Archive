---
title: "Need help with configuring OpenSSH (+ FreeNX)"
date: 2011-07-07
forum: Server Platforms
---

### Post by gunnarflax on 2011-07-07
Hello! I'm trying to set up FreeNX with OpenSSH and as always when I do this I get stuck somewhere. I have installed OpenSSH by [this guide]("https://help.ubuntu.com/community/SSH?action=show&redirect=SSHHowto") and installed FreeNX with [this guide]("http://notepad2.blogspot.com/2011/05/install-freenx-server-on-ubuntu-1004.html").

In /etc/ssh/sshd_config I have changed the default port to 228822 and disabled passwords so that I force keys. I have generated rsa keys instead of the default dsa keys. But when I installed FreeNX it generated keys of it own, but it was after that I generated the [new RSA keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys"), I don't know if it matter but I thought I should bring it up at least.

I can't restart the Daemon with:
```
/etc/init.d/ssh restart
```

I get the error that it is an upstart service and must be restarted with:
```
service sshd restart
```

But that doesn't work either. If I remember correctly I used something like...
```
sshd restart
```
...on my previous install.

When I try to connect I get "bad port: 228822" error so I've read up on some problems related to using an encrypted home directory (can't find the link but it's something close to [this one]("http://ubuntuforums.org/showthread.php?t=1677786")) and I've moved my id_rsa keys to **/etc/ssh/server/id_rsa**. I've also done the appropriate changes in the config but the thing is that all tutorials talk about a file called **authorized_logins** which I don't have. I only have the **id_rsa** files.

Any ideas?
(I'm running Ubuntu 11.04 x64 Desktop edition)

---

### Post by brighty22 on 2011-07-07
I'll start by saying I've never used FreeNX, however I have just set up keys on a new server so I'll walk you through what I did for that. It sounds like you're not specifying a port when connecting - and so it's trying 22 and failing, or there's a file permission issue - but I might be wrong. First, change sshd_config so you can use passwords to login to your server. Next, as you've generated keys and don't quite know what's what, I'd suggest wiping the contents of *~/.ssh/* on the client, as well as */etc/ssh/server/id_rsa* and *~/.ssh/authorized_keys* on the server, if the latter is there - but it shouldn't be in your case as your home dir is encrypted.

To restart ssh, use

```
sudo service ssh restart
```

The encrypted directory link you're looking for is, I imagine, [this]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Troubleshooting"). Create this authorized_keys file with all the correct permissions, and change */etc/ssh/sshd_config* before doing what's below - just follow the steps in the link. Restart ssh on the server using the command above when you're done.

I'll refer to the machine running freenx and openssh as the server, and a computer connecting to it as the client.

So. On the client:
1. To generate a new rsa key:

```
ssh-keygen -t rsa
```

Accept the default save location, and enter a passphrase if you wish.

2. To add the key:

```
ssh-add
```

Type in the passphrase when prompted if you used one.

3. To move the key to the server (include the double quotes):

```
ssh-copy-id "<your_username_on_server>@<server_ip> -p 228822"
```

4. That should be it; try logging in with

```
ssh -p 228822 <server_ip>
```

and you shouldn't be asked for a password.

I don't have an authorized_logins file on my server.. if the steps above don't work, I'll look into it a bit more.

Good luck :)

---

### Post by gunnarflax on 2011-07-08
Thank you! I will try this as soon as I get the time! You are great! :)

---

### Post by gunnarflax on 2011-07-12
I tried again and this time I get the connection but it denies the authentication:

```
NX> 203 NXSSH running with pid: 2152
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.0.64 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.
```

I've reinstalled the whole system so that I don't use an encrypted home directory any longer, since it seemed to only cause problems. What should I do next?

---

### Post by brighty22 on 2011-07-12
Make sure you've installed your public key properly, and NX is configured to use it (rather than a password). I'd try figuring out why it's 'Enabling skip of SSH config files' first.

---

