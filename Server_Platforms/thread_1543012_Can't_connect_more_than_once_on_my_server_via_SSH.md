---
title: "Can't connect more than once on my server via SSH"
date: 2010-07-31
forum: Server Platforms
---

### Post by jeromegn on 2010-07-31
Hello,

I've been having trouble with a newly configured server running on Ubuntu 10.04.1.

I can login fine via SSH the first them. Then if I want to open another session from another terminal tab, I kicks me right away. The server shows me the greeting message but then the connection immediately closes.

Any thoughts? I can't seem find any info on this.

---

### Post by inphektion on 2010-07-31
anything in /etc/security/limits.conf?

---

### Post by jeromegn on 2010-07-31
At the moment I'm running a little program that a lot of people rely on to use my application. So I can't really just stop it (it's not a daemon) to go check other files. I'll have to check at a less traffic-intense time.

I've added a screenshot to the original post, maybe that'll help.

---

### Post by jeromegn on 2010-07-31
I don't think it has anything to do with max logins in the light of that screenshot I posted. Also, I tried with different users and still the same thing happens.

---

### Post by CharlesA on 2010-07-31
Basically, you can connect, but it kicks you out before you get a shell prompt?

Can you post yer /etc/ssh/sshd_config?

I don't think it has to do with the config, but it is worth a look.

You could also try running ssh with the -vvv switch to add debug text to see what it says before it disconnects.

---

### Post by jeromegn on 2010-07-31
Thanks for replying!

Here's the output with -vvv at the end:
```
Last login: Sat Jul 31 12:31:39 2010 from x.x.x.x
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug2: channel 0: rcvd close
debug3: channel 0: will not send data after close
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t4 r0 i3/0 o3/0 fd -1/-1 cfd -1)

debug3: channel 0: close_fds r -1 w -1 e 7 c -1
Connection to x.com closed.
Transferred: sent 2000, received 2104 bytes, in 0.3 seconds
Bytes per second: sent 7876.6, received 8286.2
debug1: Exit status 254

```

And here's my ssh conf:
```
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes
UseDNS no
```

---

### Post by CharlesA on 2010-07-31
sshd_config looks ok.

There was [another thread like 3 years ago]("http://ubuntuforums.org/showthread.php?t=197072"), but no solution was posted.

Are you able to SSH in from a different terminal instead of using a new tab?

My suggestion would be to run this:

```
sudo apt-get purge ssh
```
```
sudo apt-get install ssh
```

Then see if it is still happening.

---

### Post by jeromegn on 2010-07-31
Will that kick me out if I do this while in SSH? This is a remote server and I wouldn't like losing connection during the weekend when there's less support at my hosting company.

---

### Post by CharlesA on 2010-07-31
I just tried it on my server at home and it didn't disconnect me.

Here's the script I used:

```
#!/bin/bash

apt-get purge ssh openssh-server --assume-yes && apt-get install ssh --assume-yes
```

I ran it using **sudo ./script.sh**

---

### Post by jeromegn on 2010-07-31
Same error sadly. I tried opening it in a new window too.

---

### Post by CharlesA on 2010-07-31
I would suggest booting off a livecd and trying to ssh in from there. It could be a problem with the client.

We've ruled out the server.

Also, do you have any firewall rules that limit connections?

---

### Post by jeromegn on 2010-07-31
It also failed on my other Macbook Pro and on my Ubuntu server I have home. So I don't think it's the client.

---

### Post by CharlesA on 2010-07-31
That's so strange. I am able to connect to my server at home multiple times with no problems.

Maybe try contacting the hosting company and asking them? It could be that they are limiting connections to 1 per IP or something.

---

### Post by jeromegn on 2010-08-03
Ok well now I had to reboot my computer so I lost the SSH connection and I can't connect anymore.

That's so weird.

---

### Post by CharlesA on 2010-08-03
That's so strange. I would definitely contact the hosting company and see what is going on.

---

### Post by jeromegn on 2010-08-03
I did... we'll see what happens. But it tells me the issue came after I got the server which is very strange because I haven't installed anything that could mess with SSH... at least I don't think so.

---

### Post by CharlesA on 2010-08-04
Where there any firewall rules in effect?

---

### Post by jeromegn on 2010-08-04
Probably not. Default configuration from the hosting company. I did login effortlessly the first time. Installed a bunch of web development stuff, but I don't think that could've caused the issue.

I found this thread which the guy seems to have found a solution, but I can't login to try it out: [http://www.mail-archive.com/linux-il@cs.huji.ac.il/msg43872.html](http://www.mail-archive.com/linux-il@cs.huji.ac.il/msg43872.html)

Still looking... Charles, I'd be willing to give you access to it if you think you can fix it. For some reason, my hosting company says they can log in without a problem.

---

### Post by CharlesA on 2010-08-04
I don't really know what the problem is tbh, since I've not run into this before, but I could see if it would even let me get a login prompt, if you want.

PM me the details and I'll see if I can connect.

That would probably help rule out if it's a problem on your end or on the hosting company's end.

---

### Post by ulfklose on 2010-08-04
Any further infos on that?

Charles, were you able to connect to this machine?

---

### Post by CharlesA on 2010-08-04
Dump of my attempt to connect:

```
ubuntu@sandboxub:~$ ssh xxx@xxx.xxx.xxx.xxx
xxx@xxx.xxx.xxx.xxx's password: 
Linux cl-t113-132cl 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.

Last login: Wed Aug  4 03:03:53 2010
Connection to xxx.xxx.xxx.xxx closed.
```

When I ran it with ssh -vvv it did the same thing that happened to you:

```
ubuntu@sandboxub:~$ ssh -vvv xxx@xxx.xxx.xxx.xxx
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to xxx.xxx.xxx.xxx [xxx.xxx.xxx.xxx] port 22.
debug1: Connection established.
debug1: identity file /home/ubuntu/.ssh/identity type -1
debug1: identity file /home/ubuntu/.ssh/id_rsa type -1
debug1: identity file /home/ubuntu/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu4
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug3: Wrote 792 bytes for a total of 831
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug3: Wrote 24 bytes for a total of 855
debug2: dh_gen_key: priv key bits set: 122/256
debug2: bits set: 544/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: Wrote 144 bytes for a total of 999
debug3: check_host_in_hostfile: filename /home/ubuntu/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 2
debug1: Host 'xxx.xxx.xxx.xxx' is known and matches the RSA host key.
debug1: Found key in /home/ubuntu/.ssh/known_hosts:2
debug2: bits set: 519/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: Wrote 16 bytes for a total of 1015
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug3: Wrote 48 bytes for a total of 1063
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/ubuntu/.ssh/identity ((nil))
debug2: key: /home/ubuntu/.ssh/id_rsa ((nil))
debug2: key: /home/ubuntu/.ssh/id_dsa ((nil))
debug3: Wrote 64 bytes for a total of 1127
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/ubuntu/.ssh/identity
debug3: no such identity: /home/ubuntu/.ssh/identity
debug1: Trying private key: /home/ubuntu/.ssh/id_rsa
debug3: no such identity: /home/ubuntu/.ssh/id_rsa
debug1: Trying private key: /home/ubuntu/.ssh/id_dsa
debug3: no such identity: /home/ubuntu/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
xxx@xxx.xxx.xxx.xxx's password: 
debug3: packet_send2: adding 48 (len 61 padlen 19 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug3: Wrote 144 bytes for a total of 1271
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug3: Wrote 128 bytes for a total of 1399
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.
debug3: Ignored env ORBIT_SOCKETDIR
debug3: Ignored env SSH_AGENT_PID
debug3: Ignored env TERM
debug3: Ignored env SHELL
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env WINDOWID
debug3: Ignored env GNOME_KEYRING_CONTROL
debug3: Ignored env GTK_MODULES
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env DEFAULTS_PATH
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env USERNAME
debug3: Ignored env XDG_CONFIG_DIRS
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env PATH
debug3: Ignored env PWD
debug3: Ignored env GDM_KEYBOARD_LAYOUT
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env MANDATORY_PATH
debug3: Ignored env GDM_LANG
debug3: Ignored env GDMSESSION
debug3: Ignored env SPEECHD_PORT
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env XAUTHORITY
debug3: Ignored env COLORTERM
debug3: Ignored env _
debug3: Ignored env OLDPWD
debug2: channel 0: request shell confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug3: Wrote 448 bytes for a total of 1847
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
debug2: channel 0: rcvd eow
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
Linux cl-t113-132cl 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.

Last login: Wed Aug  4 12:50:25 2010 from ip72-197-183-137.sd.sd.cox.net
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug2: channel 0: rcvd close
debug3: channel 0: will not send data after close
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t4 r0 i3/0 o3/0 fd -1/-1 cfd -1)

debug3: channel 0: close_fds r -1 w -1 e 6 c -1
debug3: Wrote 32 bytes for a total of 1879
debug3: Wrote 64 bytes for a total of 1943
Connection to xxx.xxx.xxx.xxx closed.
Transferred: sent 1744, received 2328 bytes, in 0.2 seconds
Bytes per second: sent 7532.4, received 10054.7
debug1: Exit status 254
ubuntu@sandboxub:~$ 

```

I don't know what exactly is the problem, since I've never encounted this kind of thing before. In my experience, it either connects fine or it doesn't connect at all.

Is there something set to run when a shell is started (.bashrc)  that is causing it to close to connection? **logout** and **exit** both do that.

What I can suggest is this: Create a new user and allow it to connect via SSH, then connect as that user and see if the same thing happens, that might help narrow it down to a problem with the profile or something.

[COLOR="Red"]EDIT: Here's the dump of me connecting successfully to a VM on my network via SSH (clean install of Ubuntu 10.04 x64 Server with only SSH installed:[/COLOR]

```
ubuntu@sandboxub:~$ ssh -vvv user@192.168.1.6
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.6 [192.168.1.6] port 22.
debug1: Connection established.
debug1: identity file /home/ubuntu/.ssh/identity type -1
debug1: identity file /home/ubuntu/.ssh/id_rsa type -1
debug1: identity file /home/ubuntu/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu4
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug3: Wrote 792 bytes for a total of 831
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug3: Wrote 24 bytes for a total of 855
debug2: dh_gen_key: priv key bits set: 130/256
debug2: bits set: 515/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: Wrote 144 bytes for a total of 999
debug3: check_host_in_hostfile: filename /home/ubuntu/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 3
debug1: Host '192.168.1.6' is known and matches the RSA host key.
debug1: Found key in /home/ubuntu/.ssh/known_hosts:3
debug2: bits set: 515/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: Wrote 16 bytes for a total of 1015
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug3: Wrote 48 bytes for a total of 1063
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/ubuntu/.ssh/identity ((nil))
debug2: key: /home/ubuntu/.ssh/id_rsa ((nil))
debug2: key: /home/ubuntu/.ssh/id_dsa ((nil))
debug3: Wrote 64 bytes for a total of 1127
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/ubuntu/.ssh/identity
debug3: no such identity: /home/ubuntu/.ssh/identity
debug1: Trying private key: /home/ubuntu/.ssh/id_rsa
debug3: no such identity: /home/ubuntu/.ssh/id_rsa
debug1: Trying private key: /home/ubuntu/.ssh/id_dsa
debug3: no such identity: /home/ubuntu/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
user@192.168.1.6's password: 
debug3: packet_send2: adding 48 (len 61 padlen 19 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug3: Wrote 144 bytes for a total of 1271
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug3: Wrote 128 bytes for a total of 1399
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.
debug3: Ignored env ORBIT_SOCKETDIR
debug3: Ignored env SSH_AGENT_PID
debug3: Ignored env TERM
debug3: Ignored env SHELL
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env WINDOWID
debug3: Ignored env GNOME_KEYRING_CONTROL
debug3: Ignored env GTK_MODULES
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env DEFAULTS_PATH
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env USERNAME
debug3: Ignored env XDG_CONFIG_DIRS
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env PATH
debug3: Ignored env PWD
debug3: Ignored env GDM_KEYBOARD_LAYOUT
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env MANDATORY_PATH
debug3: Ignored env GDM_LANG
debug3: Ignored env GDMSESSION
debug3: Ignored env SPEECHD_PORT
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env XAUTHORITY
debug3: Ignored env COLORTERM
debug3: Ignored env OLDPWD
debug3: Ignored env _
debug2: channel 0: request shell confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug3: Wrote 448 bytes for a total of 1847
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Linux atlantis 2.6.32-24-server #38-Ubuntu SMP Mon Jul 5 10:29:32 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Wed Aug  4 10:13:38 PDT 2010

  System load:  0.29              Processes:           81
  Usage of /:   14.2% of 7.49GB   Users logged in:     1
  Memory usage: 5%                IP address for lo:   127.0.0.1
  Swap usage:   0%                IP address for eth0: 192.168.1.6

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Wed Aug  4 10:12:48 2010 from sandboxub.asgard.lcl

```

---

### Post by BOK on 2010-08-04
Fascinating! My ostrich in Safari has it's head in the dirt now... ;)
Some thoughts / questions:

- is this a shared server or VPS/VM?
- any filesystems out of space (e.g. /tmp) ?
- what is /var/log/auth.log saying when a connection was closed?
- anything weird in $HOME/.ssh/config?
- anything out of the default in $HOME/.bashrc or .profile?
- any aged ssh-agents running?

---

### Post by LightningCrash on 2010-08-04
Sounds like a PAM maxlogins limit.

[http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_limits.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_limits.html)


If the account is locked out it will disconnect in the same manner.

ETA: If PAM doesn't have maxlogins, I'd force a reinstall of PAM. That's just me though.

---

### Post by CharlesA on 2010-08-04
Hrm, I wonder if it is the maxlogins in /etc/security/limits.conf. Mine only has examples that are commented out.

As for /var/logs/auth.log, that would probably tell you why it failed to login.

@LightningCrash: So if an account with SSH access is locked out, it will let you login, but then immediately disconnect?

That doesn't sound right.. since I tried it after locking "user" with sudo passwd -l user:

```
charles@thor:~$ ssh user@192.168.1.6
Enter passphrase for key '/home/charles/.ssh/id_rsa':
user@192.168.1.6's password:
Permission denied, please try again.
user@192.168.1.6's password:
Permission denied, please try again.
user@192.168.1.6's password:
Permission denied (publickey,password).
```

---

### Post by jeromegn on 2010-08-04
> **BOK said:**
> Fascinating! My ostrich in Safari has it's head in the dirt now... ;)
Some thoughts / questions:

- is this a shared server or VPS/VM?
- any filesystems out of space (e.g. /tmp) ?
- what is /var/log/auth.log saying when a connection was closed?
- anything weird in $HOME/.ssh/config?
- anything out of the default in $HOME/.bashrc or .profile?
- any aged ssh-agents running?

- It's a dedicated server and a power house at that!
- I doubt /tmp was out of space as I only have been using it for a few days. No way to tell anymore since no one can login.
- Can't tell.
- Can't tell, but probably not.
- I only modified the PATH to include a custom ruby installation at the beginning, but every utility still worked fine after sourcing it.
- Doubt it, but I can't tell.

As a general update to everyone interested in helping. My hosting company (iWeb) couldn't log in in any way on the server. They tried booting in "single mode" (don't know what that means) and with a KVM, still got the same issue.

They tried booting with a Knoppix Live CD and it said it couldn't read the system disk. Funny thing though, [http://dev.ostrichapp.com/](http://dev.ostrichapp.com/) is on that server and it's accessible.

That's a very weird issue. Luckily I had everything under source control and the information in my database is quite replaceable. Everyone will simply need to log in again. I fell back to the old server I had and pointed the DNS in the right way at around lunch time, should be up soon for everyone.

---

### Post by CharlesA on 2010-08-04
That's really strange. I wonder why it's having problem but Ostrich is working.

I would probably have them do a clean install of Ubuntu Server 10.04, since no one can connect, even locally (which is single user - boot into root shell from recovery mode).

---

### Post by LightningCrash on 2010-08-04
> **CharlesA said:**
> @LightningCrash: So if an account with SSH access is locked out, it will let you login, but then immediately disconnect?

That doesn't sound right.. since I tried it after locking "user" with sudo passwd -l user:

```
charles@thor:~$ ssh user@192.168.1.6
Enter passphrase for key '/home/charles/.ssh/id_rsa':
user@192.168.1.6's password:
Permission denied, please try again.
user@192.168.1.6's password:
Permission denied, please try again.
user@192.168.1.6's password:
Permission denied (publickey,password).
```

I have found two instances on this forum where people experienced what the OP has, and both of them were locked out accounts.
(There may also be some PAM misconfig in those two somewhere but I digress)
passwd -l changes the password line in /etc/shadow to *LK*, so you'll never get logged in. Some other pam lockout mechanisms don't do that.

---

### Post by CharlesA on 2010-08-04
> **LightningCrash said:**
> I have found two instances on this forum where people experienced what the OP has, and both of them were locked out accounts.
(There may also be some PAM misconfig in those two somewhere but I digress)
passwd -l changes the password line in /etc/shadow to *LK*, so you'll never get logged in. Some other pam lockout mechanisms don't do that.

I see. Interesting.

---

### Post by msandoy on 2010-08-05
Well, I have been following this thread with interest.
I have a virtual server, and I changed the setting in /etc/security/limits.conf, to give me only 2 instances. The result was quite similar to what the OP describes, BUT there is a slight difference. 
```

user@ASUS:$ ssh 192.168.1.190
user@192.168.1.190's password: 
Linux virtual 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

  System information as of Mon Aug  2 21:04:52 CEST 2010

  System load: 0.35              Memory usage: 10%   Processes:       78
  Usage of /:  8.3% of 14.58GB   Swap usage:   0%    Users logged in: 1

  Graph this data and manage this system at https://landscape.canonical.com/

Too many logins for 'user'.
Last login: Mon Aug  2 21:04:40 2010 from 192.168.1.6
Connection to 192.168.1.190 closed.

```
 It does say Too many logins just before it kicks me out.
I'm very interested to know how this works out, since I have a server running for two months at a time, when I can not reach it physically. Would be a disaster if I was blocked out of it.

---

### Post by CharlesA on 2010-08-05
> **msandoy said:**
> 
 It does say Too many logins just before it kicks me out.
I'm very interested to know how this works out, since I have a server running for two months at a time, when I can not reach it physically. Would be a disaster if I was blocked out of it.

That kind of makes sense, but it wouldn't prevent the user from logging in only once, would it?

---

### Post by msandoy on 2010-08-05
No, it does not. It just prevents me from loging in more than the set ammount of times at the same time. I can still log in and out with one instance of ssh.

---

### Post by CharlesA on 2010-08-05
Ok, thought so. I still wonder why they are having problems connecting now. It's so strange.

---

### Post by msandoy on 2010-08-05
I will do some more testing when I get off from work, in 9 hours time. I did try to lock myself out with Denyhosts, but that does not give any result even close to what he is experiencing here.

---

### Post by CharlesA on 2010-08-05
> **msandoy said:**
> I will do some more testing when I get off from work, in 9 hours time. I did try to lock myself out with Denyhosts, but that does not give any result even close to what he is experiencing here.

Thanks for trying to help. I am totally out of ideas here.

From what the OP said about the hosting company being unable to boot into "single user" mode, makes me think that the entire OS install is borked.

At the very least they should be able to get a root shell.

---

### Post by LightningCrash on 2010-08-05
OP is there any reason you need multiple SSH connections anyway? I usually just spawn more xterms when I need that...

---

### Post by msandoy on 2010-08-06
I have been surfing a bit, looking for similar problems. Found this on Linuxquestions.org
[http://www.linuxquestions.org/questions/linux-newbie-8/putty-ssh-to-ubuntu-server-9-10-a-799709/](http://www.linuxquestions.org/questions/linux-newbie-8/putty-ssh-to-ubuntu-server-9-10-a-799709/)
In that case, it was a faulty network card.

---

### Post by msandoy on 2010-08-06
I have tried, but I'm not able to replicate OP's login problem. I would start checking if there is a hw failure involved.

---

