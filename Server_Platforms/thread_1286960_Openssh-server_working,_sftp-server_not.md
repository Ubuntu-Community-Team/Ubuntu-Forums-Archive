---
title: "Openssh-server working, sftp-server not"
date: 2009-10-09
forum: Server Platforms
---

### Post by Jive Turkey on 2009-10-09
I have a VPS account running ubuntu in OpenVZ.  I'm prepping it for use and I have sshd configured to allow either pubkey or password authentication for now.  Works great except for sftp.

For some reason I cannot get sftp-server working(part of openssh-server), ssh works well and I have the same configuration on a different server that works with sshd/sftp.  I think it might be something unique to the VM template from the host.



Attempting to connect using nautilus or sftp from the terminal throws this error message:

"Could not open location 'sftp://user@example:portnumber/directory/blah'

ssh program unexpectedly exited"



Using filezilla it just says "Error:	Could not connect to server."


trying to start sftp-server on the commandline from the host seems to result in a stopped instance of sftp-server when reviewed using top.


Thanks in advance for any help.

---

### Post by superc0w on 2009-10-09
I'm not sure how critical sftp is to you, maybe you can try using scp instead though! It's very similar sytax.

You'd have to look into filezilla docs, but from command line its:
scp -P22 [email]user@domain.com[/email]:/tmp/foo /local/directory

---

### Post by gombadi on 2009-10-09
> 
For some reason I cannot get sftp-server working(part of openssh-server), ssh works well and I have the same configuration on a different server that works with sshd/sftp.


If you can log in using ssh then have a look at the logs and see what the message is when you try and sftp to the VE.

Have a look at /var/log/auth.log and /var/log/syslog

---

### Post by Jive Turkey on 2009-10-10
> **superc0w said:**
> I'm not sure how critical sftp is to you, maybe you can try using scp instead though! It's very similar sytax.

You'd have to look into filezilla docs, but from command line its:
scp -P22 [email]user@domain.com[/email]:/tmp/foo /local/directory

scp won't work either, argh.  Curiously, I can use make an ill advised samba connection to the VPS.  Not sure why they chose to install samba on thier image template and not mysql.

[QUOTE=gombadi]
Quote:
For some reason I cannot get sftp-server working(part of openssh-server), ssh works well and I have the same configuration on a different server that works with sshd/sftp.
If you can log in using ssh then have a look at the logs and see what the message is when you try and sftp to the VE.

Have a look at /var/log/auth.log and /var/log/syslog [/QUOTE]

auth.log is empty, different problem, no mention of ssh or sftp or anything relevant in syslog either

---

### Post by superc0w on 2009-10-10
May you could paste in scp -v * so we can see the output of a failed connection?  I don't really know enough about sftp to troubleshoot that but if you're willing to try this route I'll see if I can help you.

---

### Post by Jive Turkey on 2009-10-11
> **superc0w said:**
> May you could paste in scp -v * so we can see the output of a failed connection?  I don't really know enough about sftp to troubleshoot that but if you're willing to try this route I'll see if I can help you.

That's a good idea.  I've determinied that the problem emerges after running updates.  The packages that apt wants to update from a fresh rebuild of the VE are:```
libperl5.10 (5.10.0-19ubuntu1.1)
cron (3.0pl1-105ubuntu1.1)
dhcp3-common (3.1.1-5ubuntu8.1)
dhcp3-client (3.1.1-5ubuntu8.1)
libmagic1 (4.26-2ubuntu4)
file (4.26-2ubuntu4)
libgnutls26 (2.4.2-6ubuntu0.1)
libnewt0.52 (0.52.2-11.3ubuntu3.1)
libssl0.9.8 (0.9.8g-15ubuntu3.3)
libsqlite3-0 (3.6.10-1ubuntu0.2)
lsb-release (4.0-0ubuntu0.9.04.1)
udev (141-1.2)
wget (1.11.4-2ubuntu1.1)
whiptail (0.52.2-11.3ubuntu3.1)
libxml2 (2.6.32.dfsg-5ubuntu4.2)
libisc45 (1:9.5.1.dfsg.P2-1ubuntu0.1)
libdns45 (1:9.5.1.dfsg.P2-1ubuntu0.1)
libisccc40 (1:9.5.1.dfsg.P2-1ubuntu0.1)
libisccfg40 (1:9.5.1.dfsg.P2-1ubuntu0.1)
libbind9-40 (1:9.5.1.dfsg.P2-1ubuntu0.1)
liblwres40 (1:9.5.1.dfsg.P2-1ubuntu0.1)
bind9-host (1:9.5.1.dfsg.P2-1ubuntu0.1)
bind9utils (1:9.5.1.dfsg.P2-1ubuntu0.1)
bind9 (1:9.5.1.dfsg.P2-1ubuntu0.1)
libapr1 (1.2.12-5ubuntu0.1)
mysql-common (5.1.30really5.0.75-0ubuntu10.2)
libmysqlclient15off (5.1.30really5.0.75-0ubuntu10.2)
libpq5 (8.3.8-0ubuntu9.04)
libaprutil1 (1.2.12+dfsg-8ubuntu0.3)
apache2-utils (2.2.11-2ubuntu2.3)
apache2-doc (2.2.11-2ubuntu2.3)
fetchmail (6.3.9~rc2-4ubuntu1.1)
libcups2 (1.3.9-17ubuntu3.2)
libcupsys2 (1.3.9-17ubuntu3.2)
libcurl3-gnutls (7.18.2-8ubuntu4.1)
libdbus-1-3 (1.2.12-0ubuntu2.1)
libglib2.0-0 (2.20.1-0ubuntu2.1)
libwbclient0 (2:3.3.2-1ubuntu3.2)
openssl (0.9.8g-15ubuntu3.3)
samba-common (2:3.3.2-1ubuntu3.2)
smbfs (2:3.3.2-1ubuntu3.2)
samba (2:3.3.2-1ubuntu3.2)
perl-modules (5.10.0-19ubuntu1.1)
libsasl2-modules (2.1.22.dfsg1-23ubuntu3.1)
libsasl2-2 (2.1.22.dfsg1-23ubuntu3.1)
sasl2-bin (2.1.22.dfsg1-23ubuntu3.1)
perl (5.10.0-19ubuntu1.1)
apache2.2-common (2.2.11-2ubuntu2.3)
apache2-mpm-prefork (2.2.11-2ubuntu2.3)
apache2 (2.2.11-2ubuntu2.3)
```

Currently its not broken since I reverted to a fresh build and haven't updated yet, I will shortly though.

---

### Post by Jive Turkey on 2009-10-11
ok here is the scp output (using key authentication):
```
user@client:~$ scp -v -P<<port-number.removed>> Desktop/file1 user@<<serverip.removed>>:/home/dir/
Executing: program /usr/bin/ssh host <<serverip.removed>>, user user, command scp -v -t /home/dir/
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /home/dir/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to <<serverip.removed>> [<<serverip.removed>>] port <<port-number.removed>>.
debug1: Connection established.
debug1: identity file /home/dir/.ssh/identity type -1
debug1: identity file /home/dir/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/dir/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '[<<serverip.removed>>]:<<port-number.removed>>' is known and matches the RSA host key.
debug1: Found key in /home/dir/.ssh/known_hosts:8
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/dir/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 277
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug1: Sending command: scp -v -t /home/dir/
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
Couldn't open /dev/null: Permission denieddebug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: fd 1 clearing O_NONBLOCK
Transferred: sent 2240, received 2328 bytes, in 0.2 seconds
Bytes per second: sent 10087.0, received 10483.3
debug1: Exit status 1
lost connection
```

I tried disabling Pubkey authentication on the server, similar results, password succeeds, file transfer fails.  
I'm curious, what are these calls to "Requesting [COLOR="Red"]no-more-sessions@openssh.com[/COLOR]," and "client_input_channel_req: channel 0 rtype [COLOR="Red"]eow@openssh.com[/COLOR] reply 0".

---

### Post by Lars Noodén on 2009-10-11
The client can only tell so much, especially when it looks like the problem might be on the server.  

You could look at the server logs to get some idea, e.g. /var/log/auth.log

However, you might get the most useful information looking at the output from the server itself:

```

# stop the server using the control script
sudo /etc/init.d/ssh stop
# run the ssh server, with extra debug messages and NOT in daemon mode 
sudo /usr/sbin/sshd -Dd

```

Then in another window, try to connect using SFTP.

---

### Post by Jive Turkey on 2009-10-11
> **Lars Noodén said:**
> The client can only tell so much, especially when it looks like the problem might be on the server.  

You could look at the server logs to get some idea, e.g. /var/log/auth.log

However, you might get the most useful information looking at the output from the server itself:

```

# stop the server using the control script
sudo /etc/init.d/ssh stop
# run the ssh server, with extra debug messages and NOT in daemon mode 
sudo /usr/sbin/sshd -Dd

```

Then in another window, try to connect using SFTP.

I think that will help.  I don't have physical access to the server though.  After running the first command, I wont be able to run the second command.  Is it possible to run sudo /etc/init.d/ssh restart with a setting for debug mode on configured elsewhere?  Maybe with a script or something to run the two commands.

---

### Post by Lars Noodén on 2009-10-12
> **Jive Turkey said:**
> I think that will help.  I don't have physical access to the server though.  After running the first {script}, I wont be able to run the second {program}.  Is it possible to run sudo /etc/init.d/ssh restart with a setting for debug mode on configured elsewhere?  ...

Good idea.  

If you have another port available, any port at all, then you can run a second instance of the sshd program and try connecting to that.  The examples below would be listening on port 3333:

```

# use the existing configuration, but override the port number
sudo /usr/sbin/sshd -Dd -p 3333

# use a completely different configuration,
sudo /usr/sbin/sshd -f /home/jiveturkey/test/sshd_config -Dd -p 3333

```

When you play with the configuration file, use the second option and test thoroughly.  Then let it sit.  Test it some more.

---

### Post by guitar_man on 2009-10-12
I had the same problem last week....

Try typing ssh://username@host/ in nautilus instead of sftp...it worked for me...

---

### Post by guitar_man on 2009-10-12
sorry double post..

---

### Post by dallasmayor on 2010-03-10
This is cause by an bad locale setting in /home/%user/.config/user-dirs.locale.

Open this file, and it should contain the value "en_US" or what is appropriate for your locale. If it contains the value "C", then it isn't going to work.

---

