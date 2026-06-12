---
title: "Instance resource problem."
date: 2011-02-11
forum: Ubuntu Cloud and Juju
---

### Post by selvawithcommunity on 2011-02-11
hi friends finally i setup the priavate cloud using the 2 machines.

i ran instances with type m1.large and terminated andthen
ran instances with type m1.medium and terminaed

 so now no instances is running and i verified using the command
euca-describe-instances 
and this show no instances is running.
but when i am trying to run instances it shows the errors as

**FinishImageVerify:No enough resources available(--addressing priave).**

**what i have to do next? please reply soon.**

**mistakes i made:** [U]one time i shutdown the node controller system without shutdown the virtual instances. is this may be the problem?
[/U]
thank you friends.

---

### Post by raymdt on 2011-02-11
hi,
can you post the result of
```

euca-describe-availabilty-zone verbose

```

---

### Post by selvawithcommunity on 2011-02-12
now i can able to run the instances. but i am trying to connect the remote via ssh but it shows the error as follwos:

i run the instances using the command:
**$euca-run-instances emi-1F2115BB -k mykey -t m1.large**

and trying the following command to connect via ssh

**$sudo ssh -v -i mykey.priv user@10.1.7.105**

but it shows the error as follow:

OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 10.1.7.105 [10.1.7.105] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file mykey.priv type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu5
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu5 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
b6:93:90:14:a5:1c:31:4a:ef:65:99:70:34:7a:4d:a1.
Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending key in /root/.ssh/known_hosts:1
RSA host key for 10.1.7.105 has changed and you have requested strict checking.
Host key verification failed.

at the same time the above command without SUDO shows the output as

$**ssh -v -i mykey.priv user@10.1.7.105**
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 10.1.7.105 [10.1.7.105] port 22.
debug1: Connection established.
debug1: identity file mykey.priv type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu5
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu5 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '10.1.7.105' is known and matches the RSA host key.
debug1: Found key in /home/cladmin/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: cladmin@ubuntu-nc
debug1: Authentications that can continue: publickey
debug1: Offering public key: cladmin@ubuntu-nc
debug1: Authentications that can continue: publickey
debug1: Trying private key: mykey.priv
debug1: read PEM private key done: type RSA
debug1: Authentications that can continue: publickey
debug1: No more authentication methods to try.
Permission denied (publickey).

i really confused. 


please help me.
thank you.

---

### Post by kim0 on 2011-02-12
When you say user@ do you mean "ubuntu@" since the default username is ubuntu!

---

### Post by raymdt on 2011-02-12
Hi,
why  " sudo ssh " ?????
I asked you to post the result of 
 ```

euca-describe-availabilty-zone verbose
```

The following Commands should help
```

**rm  ~/.ssh/know_hosts**
**ssh -i mykey.priv ubuntu@10.1.7.105**

```

---

### Post by selvawithcommunity on 2011-02-16
thank you kim0 and raymdt. i login as the ubuntu user in my instances. thank you so much...
[URL="http://ubuntuforums.org/member.php?u=1203868"]
[/URL]

---

### Post by raymdt on 2011-02-18
Nice to hear it works :P

---

