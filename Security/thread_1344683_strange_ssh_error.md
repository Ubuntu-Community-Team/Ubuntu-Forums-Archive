---
title: "strange ssh error"
date: 2009-12-03
forum: Security
---

### Post by zak_neutron on 2009-12-03
Hi all

This is my 1st post in ubuntu forms (I'm a usual native of Fedoraforums). 

I seem to have a bizarre ssh connection problem between ubuntu and fedora. Let me explain:

I have 2 boxes on the same network PC 1 = Sneezy PC 2= Sleepy (sorry seven dwarves for names etc)

Sneezy is Fedora 12 running:

```
[richard@sneezy ~]$ uname -a
Linux sneezy.thejollies.com 2.6.31.5-127.fc12.i686.PAE #1 SMP Sat Nov 7 21:25:57 EST 2009 i686 i686 i386 GNU/Linux

[richard@sneezy ~]$ ssh -V
OpenSSH_5.2p1, OpenSSL 1.0.0-fips-beta4 10 Nov 2009


```Sleepy is Ubuntu 9.10 running:

```
richard@sleepy:~$ uname -a
Linux sleepy 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux

richard@sleepy:~$ ssh -V
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007


```I have setup the public key authentication between all my other machines and they work fine as does SNEEZY to SLEEPY (Fedora to Ubuntu) But......Ubuntu to Fedora seems to connect, but doesn't seem to connect. See the ssh -v output below:

```
richard@sleepy:~$ ssh -v richard@sneezy
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to sneezy [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/richard/.ssh/identity type -1
debug1: identity file /home/richard/.ssh/id_rsa type -1
debug1: identity file /home/richard/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
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
debug1: Host 'sneezy' is known and matches the RSA host key.
debug1: Found key in /home/richard/.ssh/known_hosts:7
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/richard/.ssh/id_dsa
debug1: Server accepts key: pkalg ssh-dss blen 433
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_GB.UTF-8
Linux sleepy 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

Last login: Thu Dec  3 12:22:26 2009 from sleepy.thejollies.com
richard@sleepy:~$ 

```The interesting point is the the prompt is still showing SLEEPY, but I am expecting the SNEEZY prompt. If I exit, it shows a closure of a connection?

```
richard@sleepy:~$ exitdebug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0

logout
debug1: channel 0: free: client-session, nchannels 1
Connection to sneezy closed.
Transferred: sent 2800, received 2920 bytes, in 137.5 seconds
Bytes per second: sent 20.4, received 21.2
debug1: Exit status 0
richard@sleepy:~$ 

```Interestingly if I connect from ubuntu to fedora using password authentication (see below use IP address it works!!!!)

```
richard@sleepy:~$ ssh -v richard@192.168.1.11
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.11 [192.168.1.11] port 22.
debug1: Connection established.
debug1: identity file /home/richard/.ssh/identity type -1
debug1: identity file /home/richard/.ssh/id_rsa type -1
debug1: identity file /home/richard/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.2
debug1: match: OpenSSH_5.2 pat OpenSSH*
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
debug1: Host '192.168.1.11' is known and matches the RSA host key.
debug1: Found key in /home/richard/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Next authentication method: gssapi-with-mic
debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug1: Unspecified GSS failure.  Minor code may provide more information


debug1: Next authentication method: publickey
debug1: Offering public key: /home/richard/.ssh/id_dsa
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Trying private key: /home/richard/.ssh/identity
debug1: Trying private key: /home/richard/.ssh/id_rsa
debug1: Next authentication method: password
richard@192.168.1.11's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_GB.UTF-8
Last login: Thu Dec  3 12:19:55 2009 from sleepy.thejollies.com
[richard@sneezy ~]$ 

```The command prompt is correct this time.

I'm guessing it has something to do with the public/private key relationship.

As I said at the begining to the connection from fedora into ubuntu is fine under both authentication methods.

Thoughts more than welcome!!!

---

### Post by The Cog on 2009-12-03
> **zak_neutron said:**
> Hi all

richard@sleepy:~$ ssh -v richard@sneezy
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: **Connecting to sneezy [127.0.0.1]** port 22.


There's your problem. Sleepy thinks sneezy is 127.0.0.1, which is its own loopback address. Check your DNS server if you have one, or more likely, your /etc/hosts file.

---

### Post by zak_neutron on 2009-12-03
Thanks for that -  I have checked the /etc/hosts file on both machines and I there was an error sleepy's hosts file still had an alias for 127.0.0.1 to sneezy - I think I caused it by copying a generic hosts file across all machine - obviously I didn't check it well enough!!!

However on connection I now get:

```
richard@sleepy:~$ ssh richard@sneezy
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@       WARNING: POSSIBLE DNS SPOOFING DETECTED!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
The RSA host key for sneezy has changed,
and the key for the corresponding IP address 192.168.1.11
is unchanged. This could either mean that
DNS SPOOFING is happening or the IP address for the host
and its host key have changed at the same time.
Offending key for IP in /home/richard/.ssh/known_hosts:2
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
ad:c6:2c:b0:10:c6:5f:86:ec:f2:73:3d:6f:d7:e1:d6.
Please contact your system administrator.
Add correct host key in /home/richard/.ssh/known_hosts to get rid of this message.
Offending key in /home/richard/.ssh/known_hosts:7
RSA host key for sneezy has changed and you have requested strict checking.
Host key verification failed.
```

How do I fix it?

---

### Post by The Cog on 2009-12-03
The problem is that sneezy has learned the wrong identity and thinks there is some impersonation going in. You need to delete the learned fingerprint. This is the line that tells you:> **zak_neutron said:**
> Offending key for IP in /home/richard/.ssh/known_hosts:2
So edit /home/richard/.ssh/known_hosts and delete line 2 (the first line being line 1).

---

### Post by zak_neutron on 2009-12-03
D'oh - thanks for that - All sorted - back to ssh-ing :p

Please marked as SOLVED!

---

### Post by The Cog on 2009-12-03
Glad to be of assistance.

Only the user who started the thread (you) can mark it solved. It's in the Thread Tools pull-down menu at the top of the page.

---

### Post by Lars Noodén on 2009-12-04
> **The Cog said:**
> The problem is that sneezy has learned the wrong identity and thinks there is some impersonation going in. You need to delete the learned fingerprint. This is the line that tells you:So edit /home/richard/.ssh/known_hosts and delete line 2 (the first line being line 1).

Another way to remove the key for a host would be to use ssh-keygen.

```

 ssh-keygen -R *xx.yy.zz.aa*

```

That way the old key is saved in a backup file in case a mistake was made and the is less chance of collateral damage than editing by hand.

---

