---
title: "SSH through WAN problem"
date: 2012-06-24
forum: Server Platforms
---

### Post by george987 on 2012-06-24
Hey, I just installed my first linux (Ubuntu Server 12.04) on friday, so I'm a pretty big noob. It's installed on an old laptop I figured I'd use as a sort of development/testing server. Spent a whole day setting up wifi, which was a challenge, but I got it to work.

Now I got another problem, which I've read a lot of posts and tutorials about, but can't seem to get to work. So I figured I'd ask here :)

The server is running SSHD on port 9876. I can connect to it fine (using Putty) from any computer on the network, or locally. But when I try to connect through the internet I get: Connection Refused.

My first guess was the router. I can't find anything wrong. Port 80 and 9876 redirects to the server. The webserver shows up just fine through the internet. canyouseeme.org says both ports are open.

I then tried various options in the /etc/ssh/sshd_config file, but nothing seemed to make any difference. So I just set it back to what it was as default. (See below for contents.)

Then I figured it had to be some sort of local firewall or routing issue on the server. Can't really find anything here either. But when I stop the SSHD and run a netcat process instead I do get a similar connection refused.

What am I missing? Halp halp :P

```

~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372987 (372.9 KB)  TX bytes:372987 (372.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:bc:21:72
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:febc:2172/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6032 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1021 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1445108 (1.4 MB)  TX bytes:161053 (161.0 KB)
``````
~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
``````
~$ sudo ufw status
Status: inactive
``````

~$ sudo netstat -nlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1164/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      823/smbd
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1395/apache2
tcp        0      0 0.0.0.0:9876            0.0.0.0:*               LISTEN      3734/sshd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      862/cupsd
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN      1192/postgres
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      823/smbd
tcp6       0      0 :::139                  :::*                    LISTEN      823/smbd
tcp6       0      0 :::9876                 :::*                    LISTEN      3734/sshd
tcp6       0      0 ::1:631                 :::*                    LISTEN      862/cupsd
tcp6       0      0 :::445                  :::*                    LISTEN      823/smbd
udp        0      0 0.0.0.0:68              0.0.0.0:*                           955/dhclient3
udp        0      0 192.168.1.255:137       0.0.0.0:*                           1031/nmbd
udp        0      0 192.168.1.5:137         0.0.0.0:*                           1031/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1031/nmbd
udp        0      0 192.168.1.255:138       0.0.0.0:*                           1031/nmbd
udp        0      0 192.168.1.5:138         0.0.0.0:*                           1031/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1031/nmbd
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           847/avahi-daemon: r
udp        0      0 0.0.0.0:45419           0.0.0.0:*                           847/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                847/avahi-daemon: r
udp6       0      0 :::42258                :::*                                847/avahi-daemon: r
``````
~$ cat /etc/ssh/sshd_config
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 9876
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
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
#AuthorizedKeysFile     %h/.ssh/authorized_keys

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
```

---

### Post by Elfy on 2012-06-24
*Thread moved to **Server Platforms**.*

quotes changed to code

---

### Post by CharlesA on 2012-06-24
Are you trying to access the box using the external IP address from inside your network?

If canyoutseeme reports those ports open, it should work fine.

---

### Post by george987 on 2012-06-24
> **CharlesA said:**
> Are you trying to access the box using the external IP address from inside your network?

Yeah, that was the problem. :P Didn't even cross my mind that could be the problem. Thanks!

---

