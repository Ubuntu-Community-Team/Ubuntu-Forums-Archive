---
title: "cant ssh over internet"
date: 2011-05-11
forum: Server Platforms
---

### Post by wlraider70 on 2011-05-11
When I try to ssh into my server though the internet I get his error

ssh_exchange_identification: Connection closed by remote host


I can ssh just fine when I'm local.
I'm using a dyndns address for my server if it helps. 
The port id forwarding correctly, according to canyouseeme.org

---

### Post by stealth. on 2011-05-11
> **wlraider70 said:**
> When I try to ssh into my server though the internet I get his error

ssh_exchange_identification: Connection closed by remote host


I can ssh just fine when I'm local.
I'm using a dyndns address for my server if it helps. 
The port id forwarding correctly, according to canyouseeme.org

I've had that error before, but it was "denyhosts" blocking me (Had to TOR/proxychains into my server)

Add the verbose command to ssh, ie "ssh -v [email]user@domain.org[/email]" and post the output(**replace and IP addresses that show up, if any**). 

Also try to ssh into it with just the IP address, use nmap to scan your server ports (that should help you see what ports are open/closed) 

Here is a example "nmap [email]myserver@mydomain.org[/email]" install it with "sudo apt-get install nmap"

---

### Post by wlraider70 on 2011-05-11
nmap is awesome, way better then those website i was using.
22 is open.

my hosts.deny is empyt

I tried hosts allow 
I'm not sure if the syntax is correct
```

SSHD : ALL
SSH : ALL

```



heres my ip ssh

```


server@hyrule:~$ ssh -v server@72.134.49.174
OpenSSH_5.3p1 Debian-3ubuntu6, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 72.xxx... [] port 22.
debug1: Connection established.
debug1: identity file /home/server/.ssh/identity type -1
debug1: identity file /home/server/.ssh/id_rsa type -1
debug1: identity file /home/server/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host


```

-edit-
I have attempted to ssh from a ubuntu box that has never connected to the server in anyway before.
It has the same error.

---

### Post by spynappels on 2011-05-11
Are you using Public Key authentication or password authentication?

Could you share your sshd_config file so we can see what your settings are, it looks like the authentication may be failing somewhere.

---

### Post by wlraider70 on 2011-05-11
I was using password, when this started.
I have since setup pubkey. Both are working when I connect locally.

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
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication yes

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

### Post by stealth. on 2011-05-11
Sorry for taking forever to reply. You mentioned that you had a "hosts.deny", so I know you have denyhosts. 

Read this: [http://denyhosts.sourceforge.net/faq.html#3_19](http://denyhosts.sourceforge.net/faq.html#3_19) and follow the instructions. 

If you have TOR and proxychains installed, try to "proxychains ssh -v [EMAIL="user@domain.org"]user@domain.org[/EMAIL]" and see what happens.


Have you ever been blocked before by denyhosts?, check its log if you have a way.

---

### Post by wlraider70 on 2011-05-11
no logs. 

No tor, no proxy.
The only think abnormal is that I use dyndns, but nmap shows that its fine.

---

### Post by arrrghhh on 2011-05-11
> **wlraider70 said:**
> no logs. 

No tor, no proxy.
The only think abnormal is that I use dyndns, but nmap shows that its fine.

Have you tried connecting to the server's IP?

DynDNS is probably not your issue.  If you show 22 as open tho, there's gotta be some other reason - as I assume you've forwarded the port thru your router?

Also, you're not trying to use the DynDNS name from within your network, correct?  This is a complete separate network and you are indeed attempting to connect over a WAN?

I think it's ssh -v or -vvv, basically verbose - see what errors come out when you run ssh verbosely.

Also, check the logs on the server.  I think syslog is where you'll need to look.

---

### Post by wlraider70 on 2011-05-11
nmap. when I looked at nmap last night it showed all open
now it shows filtered. I'm assuming thats bad.
Port forwarding is correct.

```

luke@sempron:~$ nmap 724

Starting Nmap 5.21 ( http://nmap.org ) at 2011-05-11 08:51 PDT
Nmap scan report for cpe-72-134-49-174.socal.res.rr.com (72.14)
Host is up (0.034s latency).
Not shown: 994 closed ports
PORT     STATE    SERVICE
22/tcp   filtered ssh
53/tcp   filtered domain
80/tcp   filtered http
443/tcp  open     https
3000/tcp open     ppp
5900/tcp filtered vnc


```

edit

I am testing the connection while local, that is because the connection was failing from a different network.

---

### Post by arrrghhh on 2011-05-11
> **wlraider70 said:**
> I am testing the connection while local, that is because the connection was failing from a different network.

Testing locally will do you no good.  You can try thru a tethered phone cxn, perhaps ask a friend to help you out... but testing from within your LAN is useless if you're concerned about hitting your server from a true WAN connection.

Do you use UFW, or any sort of firewall on the box?

I don't have the most open of connections here at work, but I only see port 53 and 119 open from my end.  Could be my work's internet tho.

---

### Post by wlraider70 on 2011-05-11
ok so the problem is resolved, when my error changed to "connection timing out" I rebooted my router. That did it though I don't know why. Linksys e3000


As for testing localy, maybe I don't understand something. 

I'm on my home network laptop. 10.10.10.102 and I ssh to server@external ip. Isn't that traffic essentially coming from the internet?

---

### Post by arrrghhh on 2011-05-11
> **wlraider70 said:**
> I'm on my home network laptop. 10.10.10.102 and I ssh to server@external ip. Isn't that traffic essentially coming from the internet?

If you're on the same network as the server, how could the traffic be coming from the internet?  The traffic never leaves your network, despite you attempting to connect back to yourself...

Read how NAT works, perhaps it'll help you understand this concept more in-depth.

---

### Post by wlraider70 on 2011-05-11
I connected with my iphone to make sure. it works too.

what about when I ssh from my home network to [email]server@dyndns.org[/email]
When I check last login it says 10.10.10.1 my router. my router log shows an incoming connection for the dyndns ip. also the connection woundn't route through the router if it was only internal.

---

### Post by arrrghhh on 2011-05-11
> **wlraider70 said:**
> I connected with my iphone to make sure. it works too.

what about when I ssh from my home network to [email]server@dyndns.org[/email]
When I check last login it says 10.10.10.1 my router. my router log shows an incoming connection for the dyndns ip. also the connection woundn't route through the router if it was only internal.

Are you not grasping the loop here?  You are the WAN IP / DynDNS IP, unless you have multiple static IPs (based on what you've said, that's not the case).

So you're connecting from your DynDNS IP, to your DynDNS IP.  It's a loop, not a good test.  The test from your iPhone however (assuming it's not connected via wifi, using the phone's 3g data cxn) is a valid test as that's a completely different network.

---

### Post by wlraider70 on 2011-05-11
that makes sense and no the phone was not on wifi.

thanks for the help

---

