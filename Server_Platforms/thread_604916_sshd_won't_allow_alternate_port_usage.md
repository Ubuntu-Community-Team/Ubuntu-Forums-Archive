---
title: "sshd won't allow alternate port usage"
date: 2007-11-06
forum: Server Platforms
---

### Post by jhetrick62 on 2007-11-06
I installed sshd in Gutsy 7.1.  I also opened the port in Firestarter to "anyone" for now.

I can access just fine.

When I changed the port statement in sshd_config to
***port 12022 (rather than port 22)***
I can't access the system but I get the follow error messages when I invoke ssh with the -v option.

>>
M0295:~ # ssh -v -l rhonda -p 12022 192.168.1.95
OpenSSH_3.8p1, SSH protocols 1.5/2.0, OpenSSL 0.9.7d 17 Mar 2004
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.95 [192.168.1.95] port 12022.
debug1: Connection established.
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.6p1 Debian-5build1
debug1: match: OpenSSH_4.6p1 Debian-5build1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_3.8p1
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer
<<

I also opened up port 12022 in Firestarter and as you can see it established the connection, but fails to receive the SSH2_MSG_KEXINIT back and crashes.

Has anyone had this experience and can you explain how to rectify this issue?

Thanks,
Jeff

---

### Post by scorp123 on 2007-11-06
Did you check the syntax? Also: You are trying SSH as "root" (guessing from your shell prompt ... '#' ...) ... Are you sure you enabled the "root" account for SSH logins? Did you try as normal user? And can you try e.g. to leave firestarter away for starters, just to narrow down the problem?

Also ... is there anything in config files such as /etc/hosts.allow and /etc/hosts.deny ... ? Those files may not exist, but if they do it would be worth to check the content because you can block unwanted SSH connections too via those two files.

---

### Post by jhetrick62 on 2007-11-06
Thanks for your reply.  Firestarter is not the issue.  I did turn it off and still the same result.  No, I'm not using the root user, I'm using the user "rhonda", an authorized user on the box and the same user that works when it is set to listen to port 22.  The user is set in the ssh statement with the -l flag, thus "ssh -v [COLOR="Red"]-l rhonda[/COLOR] -p 12022 192.168.1.95" from the linux command line.

The only change I made was changing the listening port to 12022 and restarting the ssh service.

The error occurs after making this one change, otherwise it works.

Thanks,
Jeff

---

### Post by scorp123 on 2007-11-06
Can you post your sshd_config please?

---

### Post by HermanAB on 2007-11-06
Did you remember to restart sshd after changing the port?

You can see if it is listening with telnet:
$ telnet localhost 12022

Cheers,

Herman

---

### Post by jhetrick62 on 2007-11-06
Yes HermanAB, it is listening when I do that.

My sshd_config file is:

>>
rhonda@linuxserver:/$ cat /etc/ssh/sshd_config
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 12022
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

UsePAM yes
<<

Goodluck.  I will eliminate root permissions once I get this thing to work on the port 12022.  Currently, KISS principle and as I said above, it I change the 1 line back to "port 22", it works.  So I won't make it more secure until I get it to work on port 12022.

Thanks to all,
Jeff

---

### Post by MJN on 2007-11-06
Have you tried accessing SSH on the new port **from the server**? (e.g. **ssh -v -l rhonda -p 12022 localhost**)

You need to be eliminating potential alternative sources of the problem, the most obvious of which is the firewall.

Mathew

---

### Post by jhetrick62 on 2007-11-06
Yep, here it is:

>>
rhonda@linuxserver:/$ ssh -v -l rhonda -p 12022 localhost
OpenSSH_4.6p1 Debian-5build1, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 12022.
debug1: Connection established.
debug1: identity file /home/rhonda/.ssh/identity type -1
debug1: identity file /home/rhonda/.ssh/id_rsa type -1
debug1: identity file /home/rhonda/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.6p1 Debian-5build1
debug1: match: OpenSSH_4.6p1 Debian-5build1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.6p1 Debian-5build1
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer
<<

As I said, I can turn the firewall off and I get the same result.  It isn't effecting it and when it's on, Firestarter doesn't show any reject logs either.

---

### Post by MJN on 2007-11-06
Ah, okay - that's interesting[1].

The reason I asked you to double-check it is that I've lost count of the number of times someone has said (quite genuinely) that their firewall is turned off when after several hours scratching our heads it's turned out to be on! Hence now I always ensure it's ruled out by performing local connections just to make sure!

I wish I could offer some advice but as things stand I'd just be guessing...

Mathew

[1] 'Interesting' meaning 'I aint got a clue then'!

---

### Post by HermanAB on 2007-11-06
OK, if SSHD responds to a telnet query to localhost, then SSHD is fine and dandy.  The problem then lies elsewhere.

If this works:
$ telnet localhost 12022

then this must also work:
$ ssh username@localhost

If this doesnt work:
$ telnet youripaddress 12022
$ ssh username@youripaddress

then the problem is with iptables dropping the packets (or you are using the wrong ipaddress).

Cheers,

Herman

---

### Post by jhetrick62 on 2007-11-06
Herman,

I really do not believe that you are correct.  I ran your test and here are the results:

rhonda@linuxserver:~$ ssh -p 12022 rhonda@localhost
Read from socket failed: Connection reset by peer
rhonda@linuxserver:~$ telnet localhost 12022
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
SSH-2.0-OpenSSH_4.6p1 Debian-5build1


As you can see, same result and I have the firewall turned off.  It will not actually connect through on telnet but it attempts to.

As I said above, the only change from it working to not working is the listen port.

We will keep searching.... endlessly maybe.

Jeff

---

### Post by MJN on 2007-11-06
The telnet test is not testing the complete connection as it cannot establish a SSL/TLS tunnel hence whilst it shows an initial connection so does the SSH debugging output - the problem appears later on in response to the KEXINIT stage (I don't know what that is - key exchange of some sort I assume).

And he's tried connecting with SSH to localhost thus ruling out any firewall...

I must admit, I'm completely stumped!

Mathew

---

### Post by MJN on 2007-11-06
Here's a thought - try increasing the server log level (from INFO to VERBOSE or even DEBUG1, DEBUG2 etc) and see how the server sees things...

(it is afterall the server that's hosing the connection so the logs should hopefully say why)

Mathew

---

### Post by jhetrick62 on 2007-11-06
[SIZE="3"][COLOR="Red"]**Fixed !!!**[/COLOR][/SIZE]

Get this, I upped the error levels to VERBOSE and then read the logs.  It would say that it was not binding to the address that it was already in use??  It would not show up as an open port though in a portscan!

>>
Nov  6 18:54:42 linuxserver sshd[26496]: error: Bind to port 12022 on :: failed: Address already in use.
Nov  6 18:54:42 linuxserver sshd[26496]: error: Bind to port 12022 on 0.0.0.0 failed: Address already in use.
Nov  6 18:54:42 linuxserver sshd[26496]: fatal: Cannot bind any address.
<<

Then as a lark, I switched the port to 11022 and as you can see below, IT WORKED!

>>
Nov  6 19:09:29 linuxserver sshd[27133]: Server listening on 0.0.0.0 port 11022.
Nov  6 19:09:34 linuxserver sshd[27138]: Connection from 127.0.0.1 port 60193
Nov  6 19:09:34 linuxserver sshd[27138]: Failed none for rhonda from 127.0.0.1 port 60193 ssh2
Nov  6 19:09:38 linuxserver sshd[27138]: Accepted password for rhonda from 127.0.0.1 port 60193 ssh2
Nov  6 19:09:38 linuxserver sshd[27140]: pam_unix(ssh:session): session opened for user rhonda by (uid=0)
Nov  6 19:09:41 linuxserver sshd[27140]: Connection closed by 127.0.0.1
Nov  6 19:09:41 linuxserver sshd[27140]: pam_unix(ssh:session): session closed for user rhonda
Nov  6 19:09:41 linuxserver sshd[27140]: Closing connection to 127.0.0.1
Nov  6 19:10:10 linuxserver sshd[27159]: Connection from 192.168.1.220 port 33806
Nov  6 19:10:15 linuxserver sshd[27159]: Failed none for rhonda from 192.168.1.220 port 33806 ssh2
Nov  6 19:10:18 linuxserver sshd[27159]: Accepted password for rhonda from 192.168.1.220 port 33806 ssh2
Nov  6 19:10:18 linuxserver sshd[27161]: pam_unix(ssh:session): session opened for user rhonda by (uid=0)
Nov  6 19:10:20 linuxserver sshd[27161]: Connection closed by 192.168.1.220
Nov  6 19:10:20 linuxserver sshd[27161]: pam_unix(ssh:session): session closed for user rhonda
Nov  6 19:10:20 linuxserver sshd[27161]: Closing connection to 192.168.1.220
<<

The catch is that I have been using port 12022 on many Fedora systems for 3 years and had port forwarding set to that for ever!!

I guess I'm adapting, but it seems strange that it complains of another address already attached to that.

Thanks for your thoughts & the advice to up the error levels.

Jeff

---

