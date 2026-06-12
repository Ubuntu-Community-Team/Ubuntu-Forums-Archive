---
title: "[SOLVED] SSH problem when outside LAN"
date: 2007-10-11
forum: Server Platforms
---

### Post by piercleo on 2007-10-11
Hello all,

I have set up SSH on a desktop CPU at home. I have a netgear router on which I have forwarded port 22 to the desktop's local ip. I use dyndns. I have set up an authentication key for ssh.

I am able to SSH in and administer the server from my laptop if I'm on the same lan using both the desktop's local ip and the dyndns adress.

When I try to connect from outside the Lan (only tried from work), I get the following error message: **"ssh_exchange_identification: Connection closed by remote host".**

Since I can access internally, I don't think it's a firewall or a authentication key issue.

My goal is to be able to access the documents from my desktop CPU at all time when I am away (from anywhere) and to be able to launch and application from the remote desktop on my laptop.

I've read a lot about this so here are the complementary infos I can give you (FYI: I am new to Ubuntu and pretty new to computers in general, so I really don't know if what I give you will be of any use) :

1/ If i use the "ps -ef | grep sshd" command on the desktop CPU to see if the remote machine has a ssh seerver running I get the following:

root      5155     1  0 07:04 ?        00:00:00 /usr/sbin/sshd 
piercleo  7019  6997  0 12:20 pts/0    00:00:00 grep sshd 

2/ I checked /var/log/auth.log and couldn't find any« refused connect from localhost.localdomain ». This morning logs (when I tried to connect from work) are the following:

   Oct 11 07:04:10 piercleo-musique sshd[5155]: Server listening on :: port 22. 
   Oct 11 07:07:04 piercleo-musique gdm[4589]: (pam_unix) session opened for user piercleo by (uid=0) 
   Oct 11 07:07:07 piercleo-musique ssh-agent[5414]: error: Unknown message 252 
   Oct 11 07:07:08 piercleo-musique seahorse-agent[5426]: DNS-SD initialization failed: Daemon not running 
   Oct 11 07:09:46 piercleo-musique sudo: piercleo : TTY=unknown ; PWD=/home/piercleo ; USER=root ; COMMAND=/usr/sbin/synaptic
   --hide-main-window --non-interactive --parent-window-id 37748739
   --progress-str Veuillez patienter, cela peut prendre du temps.
   --finish-str La mise à jour est terminée --set-selections-file /tmp/tmpNRP0zT 
   Oct 11 07:17:01 piercleo-musique CRON[5912]: (pam_unix) session opened for user root by (uid=0) 
   Oct 11 07:17:01 piercleo-musique CRON[5912]: (pam_unix) session closed for user root 
   Oct 11 07:30:01 piercleo-musique CRON[6236]: (pam_unix) session opened for user root by (uid=0) 
   Oct 11 07:30:02 piercleo-musique CRON[6236]: (pam_unix) session closed for user root

3/ I couldn't find /etc/hosts.deny and /etc/hosts.allow
I have a /etc/hosts document: which has the following information:

   127.0.0.1 localhost
   127.0.1.1 piercleo-musique

   # The following lines are desirable for IPv6 capable hosts
   ::1 ip6-localhost ip6-loopback
   fe00::0 ip6-localnet
   ff00::0 ip6-mcastprefix
   ff02::1 ip6-allnodes
   ff02::2 ip6-allrouters
   ff02::3 ip6-allhosts

4/ When I try the « netstat -a | grep ssh » command on the desktop CPU I get this:
   
   tcp6       0      0 *:ssh                   *:*                     LISTEN     
   unix  2      [ ACC ]     STREAM     LISTENING     21828
   /tmp/ssh-NWAGiQ6440/agent.6440 
   unix  2      [ ACC ]     STREAM     LISTENING     21869
   /tmp/ssh-NWAGiQ6440/agent.6440.seahorse 

5/ I ran a Shieldsup test to determine the status of my system's first 1056 ports : all the ports are “stealth” (green)

6/ I used [http://www.canyouseeme.org/](http://www.canyouseeme.org/) and got the following result: Success: I can see your service on *mypublicip* on port (22)
Your ISP is not blocking port 22

I'm running out of ideas and of reading material.

Any help would be greatly appreciated.

Best regards,

Piercleo

PS (complementary remarks):

A/ I wasn't able to find an SSH troubleshooting guide, if anyone knows of one, I could use it :-)
B/ I've read that I shouldn't be using port 22 for security reasons, could that be the problem ?

---

### Post by cdenley on 2007-10-11
Is your laptop using Linux? I have problems connecting over the internet from Windows machines (putty or winscp), but not from Ubuntu. I'm guessing it's because my router blocks pings. Some routers will route connections over the LAN network if a LAN computer connects to the WAN IP, and bypass any firewall rules.

---

### Post by piercleo on 2007-10-11
Sorry about the missing information,

Yes both computers are on Feisty Fawn

piercleo

---

### Post by multi on 2007-10-11
When you are connecting from you laptop to you desktop pc are you using the desktop pc's LAN ip? If so try connecting again but this time using your router's external ip address or your dyndns name.

---

### Post by piercleo on 2007-10-11
I have tried both with the router's ip adress (but it changes so it is not convenient because i need to go on the dyndns webpage to have it) and with the dyndns host name.

Both work when i am on the lan.

---

### Post by dannyboy79 on 2007-10-11
few things to check.

the output of this: ls -la /var/run/ | grep sshd
drwxr-xr-x  2 root       root         40 2007-10-05 18:23 sshd
-rw-r--r--  1 root       root          5 2007-10-05 18:23 sshd.pid
should return exact as above. I am logged into my machine right now from work.

According to this sshd faq ([http://www.snailbook.com/faq/](http://www.snailbook.com/faq/)) it does say that this is mostly caused by tcpwrappers denying the connection. So can you double check that you don't have a /etc/hosts.allow anywhere? (ie locate hosts)

ALso,  I do see an error in the auth.log you posted:
piercleo-musique ssh-agent[5414]: error: Unknown message 252
This would leave me to believe that somethign isn't rright with /etc/ssh/sshd_config
I don't use ssh-agent so I am not sure how to troubleshoot it. You don't have any allow_users
lines within that config do you?

I use port 22 myself, as long as your using rsa or dsa key pairs, then people can pound at my port 22 all they want. Then again, that's why I setup a program called denyhosts, it parses auth.log for invalid ssh login attempts, if there is so many in a certain time, there ip gets added to hosts.deny file and that takes care of that!

---

### Post by piercleo on 2007-10-11
Hi, I am going back home now to try the le command.

Also, here is my sshd_config:

# Package generated configuration file
# See the sshd(8) manpage for details

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

UsePAM yes

---

### Post by HermanAB on 2007-10-11
Test connectivity from your LAN, using the public DynDNS address.  It should loop back and connect.  If it doesn't, then your port forwarding is suspect.  If it works and still doesn't work from the office, then the office firewall is blocking port 22, so select a different high port and change the forwarding and /etc/ssh/sshd-config to use that port, then restart sshd.

---

### Post by piercleo on 2007-10-11
Works perfectly from home even when i use the dnsdynserver.

Going back home straight away to try changing the port setting. Just for my information, how do i restart sshd ?

piercleo

ps to HermanAB: ty for being so helpful (not the first time your helping me out)..and ty to everyone of course :-)

---

### Post by piercleo on 2007-10-11
I just used shields up on the work ip and port 22 is opened !

It's driving me crazy. Is it really worth the shot that i go back home to change the port setting given the shields up results ?

By talking on #ubuntu-server, a nice ubuntero told me that i should go back home and disable ssh-agent. Any thoughts on that ?

---

### Post by eldragon on 2007-10-11
first thing to consider:

is your router / internet connection on a public ip? or are you on a isp WAN with a non routable ip (10.0.0.x, 192.168.x.x), you should be able to check that from your router. ive seen this happen in the past. some isps dont provide a public ip.

another problem: if your broadband modem is also working as a router. it might be filtering your connections. check if its own ip is a private ip too...

---

### Post by piercleo on 2007-10-11
The router ip is 86.206.xxx.xxx, but it changes because of dhcp, that's why i'm using dyndns

How do i check to see if the router's ip is a private one ?

piercleo

---

### Post by James79 on 2007-10-11
Have you tried connecting from elsewhere other than at work?

It sounds like all of the public internet can see your ssh server except for you while you are at work. Remember that firewalls can block both inbound *and outbound* traffic. Typical home routers do only the former, while in the workplace the latter is frequent as well (to prevent employees from using certain protocols).

At my work, they block *outbound* 22, which prevents people from SSH'ing from _work to outside addresses_.

My solution: find an outbound port that isn't blocked. We use yahoo instant messenger at work, so I know that we do not block outgoing connections to 5050. So I simply adjust my SSH server to listen on 5050, and adjusted my router to forward accordingly. 

Presto! ;)

> **piercleo said:**
> 
B/ I've read that I shouldn't be using port 22 for security reasons, could that be the problem ?

*_I highly recommend everyone change the port SSH listens on to something other than 22._* Nobody bothers to scan entire port ranges because it's too costly in terms of time. When scanning ranges of IPs for potential targets, hackers will only check for the easy targets such as 22,80, 135, 139, etc. If those are closed, they'll move on.

Anecdotal experience: On port 22, I would get **several** hack attempts on a **daily** basic. Eventually I changed it (for the reasons mentioned above), and I've since have had 0 failed attempts in 10+ months. This doesn't replace the need for a strong password of course...

---

### Post by piercleo on 2007-10-11
Hi and ty again for the answers,

How do I know which ports are opened outbound at work, is there a service on the internet that allows me to get this information ?

Piercleo

---

### Post by James79 on 2007-10-11
> **piercleo said:**
> How do I know which ports are opened outbound at work, is there a service on the internet that allows me to get this information ?


Unfortunately it's not that simple. Also, it's unlikely that the people who administer your firewall at work would be willing to divulge that information to you.

As an easy test, I would suggest going to a friend's house and trying from there. Or, bring a laptop to an internet café. If that works, then you can pretty much assume that the "fault" is with your work's firewall.

Then, like I was saying before, you can make some educated guesses as to which ports are open based on the protocols that are in use.

---

### Post by piercleo on 2007-10-11
VOUS ETES DES GENIES !!! (translation: you guys are geniouses).

I used the MSN messenger port and it worked ! I am soooo happy. It is a huge step for me in my computer life.

Thanks to all of you I have learned three essantial things:

1/ it's an external company who is managing the firewall of our company (scary, i am engaging someone as soon as possible to take care of all these things).

2/ People are using MSN at work...and a lot, lol, I have to do something about this.

3/ Linux is great. Someone with as little knowledge as me being able to do such a thing as setup a small SSH server... unbelievable if you ask me.

Again, thanks to all of you, 

Best regards,
Piercleo

---

### Post by dannyboy79 on 2007-10-11
when you are at home, you can issue 
nmap -P0 FQDN or nmap -P0 IP address
an example:
nmap -P0 [www.google.com](www.google.com)
or
nmap -P0 61.146.178.13
This should return the open ports.

---

### Post by James79 on 2007-10-11
> **dannyboy79 said:**
> when you are at home, you can issue 
nmap -P0 FQDN or nmap -P0 IP address
an example:
nmap -P0 [www.google.com](www.google.com)
or
nmap -P0 61.146.178.13
This should return the open ports.

Again, there is an important distinction between inbound and outbound ports. 

Issuing that nmap command from home against his work's ip address would only return which *inbound* ports his work's firewall is offering. And even there, only if there are services running. It would not indicate to him that MSN is being allowed from the inside going out.

> **piercleo said:**
> VOUS ETES DES GENIES !!! (translation: you guys are geniouses).


De rien ;)

---

### Post by dannyboy79 on 2007-10-11
any services that are allowing stuff through would be a port he could use. A service can't be "listening" on a certain port yet not allow outgoing traffic on that port. Can it?

---

### Post by James79 on 2007-10-11
> **dannyboy79 said:**
> any services that are allowing stuff through would be a port he could use. A service can't be "listening" on a certain port yet not allow outgoing traffic on that port. Can it?

Sure it can. You aren't going "thru" port 80 when you connect to a remote webserver.

You could run a webserver but deny websurfing to your users, for instance.

---

### Post by dannyboy79 on 2007-10-11
Good point, I stand corrected.

---

### Post by piercleo on 2007-10-11
:)

One tiny little last question maybe

:)

What is the command to tunnel VNC over SSH. Before I changed the port i used: vncviewer -via *dyndnsserver* *computername:0*

Now that command returns the following mistake:

VNC viewer version 3.3.7 - built Mar  8 2007 21:56:52
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
ssh: connect to host *dyndnsserver* **port 22: Connection refused**
vncviewer: Tunneling command failed: /usr/bin/ssh -f -L 5599:*computername*:5900 *dyndnsserver* sleep 20.

I'm sure it's no big thing, but I did man vncviewer and couldn't find it.

Thanks in advance already because I know you guys rock:guitar:

Piercleo

---

### Post by James79 on 2007-10-11
The "-via" command instructs vncviewer to quietly establish an ssh connection before attempting to connect to the vnc server. It does this by attempting to connect to the ssh on the default port of 22. Since you've just changed the default, it no longer works.

Unfortunately, I don't believe you can change the default port to connect to using the -via command. If I'm wrong hopefully someone  can correct me.

Instead, you'll have to establish the ssh connection manually and then your vnc connection in 2 seperate steps. Here's how I would do it (change 5555 to whatever you set your ssh server to listen to):

```
ssh dyndnsserver -p 5555 -L 9999:localhost:5900
```

Then in a* seperate shell window*:

```
vncviewer localhost:9999
```

These steps assume that your ssh server is the same computer that you are trying to VNC to. I hope that's clear :)

---

### Post by piercleo on 2007-10-12
Thank you James,

And yes your explanation was perfectly intelligible.

How do I log out cleanly of the ssh connection. I type exit after closing the application I am using and sometimes I get the following message: "logout" and then nothing happens. Is there another way to do it ?

For everyone's information, I have been in contact with the person who manages our internet connection here at work and he confirmed what I thought which is that port 22 is opened outbound !!! As a matter of fact, all outbound ports are opened !

It's ok now that it works perfectly well but still, i really don't understand why ssh would'nt work using port 22 when it works with other ports.

Just out of curiosity, I am going to change the server settings back to port 22 and go try connect from a friend's place this week-end. I really don't like not understanding something.

Anyway,

Have a good day (just starting for me in France),

piercleo

---

### Post by dannyboy79 on 2007-10-12
didi you check the things that I suggested?

---

### Post by James79 on 2007-10-12
> **piercleo said:**
> Thank you James,
How do I log out cleanly of the ssh connection. I type exit after closing the application I am using and sometimes I get the following message: "logout" and then nothing happens. 


"exit" is the correct command. If you see "logout" and the ssh connection appears to hang like it is, it's because you still have a connection that is active over your tunnel. If you close vnc, your ssh session should terminate properly.

> **piercleo said:**
> 
It's ok now that it works perfectly well but still, i really don't understand why ssh would'nt work using port 22 when it works with other ports.


Your admin is either mistaken, or your connection is being redirected somewhere else. *OR*, your ISP blocks incomming traffic on 22. Which is entirely possible. My internet provider blocks port 80 to prevent me from running a personal website (so I just host that on a different port too ;) )

> **piercleo said:**
> 
Just out of curiosity, I am going to change the server settings back to port 22 and go try connect from a friend's place this week-end. I really don't like not understanding something.


That would indeed eliminate some possibilities :)

If it makes your life any simpler, I believe you can instruct openssh to listen on multiple ports at the same time. In your /etc/ssh/sshd_config, you can have multiple Port statements:

```

Port 22
Port 5555

```

Test it first though :)

Bonne chance!

---

