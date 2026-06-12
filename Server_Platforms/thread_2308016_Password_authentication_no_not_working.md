---
title: "Password authentication no not working"
date: 2015-12-30
forum: Server Platforms
---

### Post by Vaindil on 2015-12-30
I have password authentication turned off for my server, I'm using keys now. My full sshd_config (sshd, not ssh) is below, I've removed most commented lines for brevity. Specifically, I'm asked for my username, then it says it's using keyboard-interactive authentication, then it asks for my password. I'm logging in as my user, not root. I fully rebooted the server after applying this change. I have another server with exactly the same config, just a different port, and password auth is properly disabled. This is Ubuntu Server 14.04. Why isn't password authentication properly turned off?
```
Port 612
Protocol 2
HostKey /etc/ssh/ssh_host_ed25519_key
HostKey /etc/ssh/ssh_host_rsa_key

KexAlgorithms curve25519-sha256@libssh.org,diffie-hellman-group-exchange-sha256,diffie-hellman-group1-sha1
Ciphers chacha20-poly1305@openssh.com,aes256-gcm@openssh.com,aes128-gcm@openssh.com,aes256-ctr,aes192-ctr,aes128-ctr
MACs hmac-sha2-512-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-ripemd160-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-512,hmac-sha2-256,hmac-ripemd160,umac-128@openssh.com

UsePrivilegeSeparation yes

KeyRegenerationInterval 3600
ServerKeyBits 1024

SyslogFacility AUTH
LogLevel INFO

LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile    %h/.ssh/authorized_keys

IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no

PermitEmptyPasswords no

PasswordAuthentication no

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes

AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
```

---

### Post by darkod on 2015-12-30
Why do you have AuthorizedKeysFile commented out? How is it supposed to confirm the key?

If it says it's trying to use a key and fails back to asking for the password that means it's not finding the correct key. In such case it will ask for password.

But I don't know if it has the same behavior when password auth is turned off. Maybe not finding a key defaults back to password auth even when it's disabled so that it still leaves you a way in.

---

### Post by Vaindil on 2015-12-30
That seemed odd to me too, but it's commented out on the other server where password auth is properly disabled, so I figured it wasn't a problem. I uncommented it and rebooted the server, still not working. (I know I don't have to reboot the whole server, I'm running updates at the same time.)

---

### Post by steeldriver on 2015-12-30
@darkod iirc the AuthorizedkeysFile entry is commented out by default - it's not necessary if you use the default keyfile location $HOME/.ssh

Of course the default location does need to be accessible before login - a common gotcha is if you are using home directory encryption: in that case the keysfile needs to be moved somewhere unencrypted such as /etc/ssh/*user*

---

### Post by Vaindil on 2015-12-30
@steeldriver I'm not using home directory encryption unless that's enabled by default on 14.04 and I've never heard about it. My other server doesn't give the option for password auth at all--it prompts for username, then throws an error and disconnects because it can't find my local keyfile (as expected, don't have this computer's key updated yet).

---

### Post by darkod on 2015-12-30
@steeldriver, thanks, didn't think of that. Haven't looked into my sshd_config for a while now... :)

The config looks correct and the server was rebooted after the modification of sshd_config. It's enough to restart the ssh service also.

Home directory encryption is never by default. It asks you during the install. If you haven't selected it, and it is not asking you for your pass during boot, then it's not encrypted... So right now I have no more ideas unfortunately...

---

### Post by steeldriver on 2015-12-30
I'm pretty much out of ideas as well - although iirc ssh is picky about overly-permissive permissions, you should check that they are correct i.e.

```

$ ls -ld ~/.ssh/{,authorized_keys}
drwx------ 2 user user 4096 Dec  9  2013 /home/user/.ssh/
-rw------- 1 user user  624 Jun 10  2015 /home/user/.ssh/authorized_keys

```

---

### Post by Vaindil on 2015-12-30
Permissions weren't set correctly though I could've sworn I did. Anyway, fixing them and rebooting did not solve the problem.

---

### Post by Vaindil on 2016-01-04
Bump. Anyone have any ideas?

---

