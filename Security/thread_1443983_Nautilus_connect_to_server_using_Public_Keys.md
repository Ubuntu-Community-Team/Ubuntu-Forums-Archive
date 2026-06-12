---
title: "Nautilus: connect to server using Public Keys"
date: 2010-03-31
forum: Security
---

### Post by paulsp on 2010-03-31
Hello there,

I am using Nautilus to connect to an external server. Currently, I use password authentication, and all works fine. I just type sftp://SERVER and the connection is established after providing the login credentials. However, I changed the server to only accept Public Key Authentication and disabled password authentication, and as a consequence I could not login using Nautilus anymore. Is there some way to make this work? 

Regards,
Paul

---

### Post by cdenley on 2010-04-01
Did you generate the key pair on your client in ~/.ssh then install the public key on your server in the file ~/.ssh/authorized_keys?
```

ssh -v myuser@myserver

```

---

### Post by paulsp on 2010-04-03
Thanks for your reply. I used this tutorial:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

I can connect to the server through ssh without any problems. 

```
user@localhost:~$ ssh -v root@e
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to e [192.168.1.101] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug1: identity file /home/user/.ssh/id_rsa type -1
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'e' is known and matches the RSA host key.
debug1: Found key in /home/user/.ssh/known_hosts:9
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: user@localhost
debug1: Server accepts key: pkalg ssh-rsa blen 277
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Linux ubuntu #5 SMP Thu Jan 7 13:49:08 IST 2010 i686

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

3 packages can be updated.
0 updates are security updates.

Last login: Sat Apr  3 15:40:37 2010 from localhost.local
user@server:~# 

```

Is this a configuration issue you think? CAN I actually use Pub Keys with Nautilus?

---

### Post by FuturePilot on 2010-04-03
> **paulsp said:**
> 
Is this a configuration issue you think? CAN I actually use Pub Keys with Nautilus?

Yes, you can use key based authentication with Nautilus. I only accept key based auth on my server and can access it just fine with sftp and Nautilus.

---

### Post by paulsp on 2010-04-04
That is certainly good to hear. However, whenever I try to connect to the server when Password Authentication is disabled and Public Keys are the only allowed method, then I get an error in Nautilus that says:

COULD NOT DISPLAY "SFTP://SERVER"
Access was denied

I already tried moving the AuthorizedKeysFile file and changing the permissions (see TROUBLESHOOTING at [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)), but to no avail. Any other ideas?

Thanks,
Paul

---

### Post by cdenley on 2010-04-04
> **paulsp said:**
> 
COULD NOT DISPLAY "SFTP://SERVER"
Access was denied


Do you have permission to list the contents of the root directory on the server? Does it mount, but not display?
```

ssh media.local ls -ld /
gvfs-mount sftp://user@server
gvfs-mount -l

```

---

### Post by paulsp on 2010-04-04
First command gives this:
```
user@localhost:~$ ssh SERVER ls -ld /
Permission denied (publickey).
```

However, if I mount using the terminal with the command you provided, then the server IS mounted. In fact, it DOES APPEAR in Nautilus that way. However, I prefer to mount using Nautilus and not the terminal, if possible...

---

### Post by cdenley on 2010-04-04
So what user are you connecting as? What user is the public key installed on the server for? I'm guessing you are connecting as root, so the key is installed on the server at /root/.ssh/authorized_keys. This means if you attempt to authenticate without specifying you want to authenticate as the root user, you will connect as another user which you have not authorized with the public key. You will be prompted for a password if it fails to use a key for the default user. If you attempt to authenticate as root, that should work.

sftp://root@SERVER

Am I right?

---

### Post by FuturePilot on 2010-04-04
Perhaps just try the Places > Connect to Server. Choose SSH and fill in the details. Leave the password field blank though, it will prompt for your key passphrase once a connection is established.

---

### Post by paulsp on 2010-04-05
Thanks for your replies. Cdenley, you were right indeed!! By specifying root@ in the path, I can connect without any problems. So that was all, thanks a lot for all the help!

---

