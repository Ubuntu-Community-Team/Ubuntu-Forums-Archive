---
title: "Can't login ssh from internet"
date: 2006-02-02
forum: Server Platforms
---

### Post by devilpaco on 2006-02-02
Well I've a Breezy Budger kernel k7 with ssh server enabled in a LAN with others computers, I can use ssh from the others computers in the local networkd to access the ssh one, but when I try to do it from internet using the public ip i cannot access, I've already the 22 port forwarded to my private ip in the lan, and i can ssh with the public ip through a lan computer, but from another computer with internet it says "connection timed out" or something like that.        
Computer A
/   /Computer B
Router D-LInk DI-604 -- Cablemodem Internet
\
Computer C (with ssh)

ABC are directly connected to the router, the router to the cablemodem and the cablemodem to internet

I have the 22 port forwarded to computer C and i can acces from A and B to C without problems.

I hope anyone can understand  what's happening :confused: and why i can't go into C from a computer that is not on my lan, thank you all from reading everything and for helping.

Thanks, devilpaco

---

### Post by MJN on 2006-02-02
Have you checked your firewall (on comp C) and sshd config for any restrictive host deny options?
 
Mathew

---

### Post by devilpaco on 2006-02-02
I've already checked sshd_config and I've not found anything wrong about it but I'm not quite sure about what I was looking for... about the firewall in computer C (the ubuntu one)I haven't configured any firewall... does ubuntu have a default one? how do I disable it?

just in case I paste here my sshd_config to see if you find anything wrong..
```

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
PermitRootLogin no
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


# To change Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#AFSTokenPassing no
#KerberosTicketCleanup no

# Kerberos TGT Passing does only work with the AFS kaserver
#KerberosTgtPassing yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
KeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```

thank you again

---

### Post by bjweeks on 2006-02-02
No, ubuntu does not come with a firewall but some isp's block port 22(ssh). You should run this [test]("https://www.grc.com/x/ne.dll?bh0bkyd2") from the box the ssh server is on.

---

### Post by devilpaco on 2006-02-02
[QUOTE=bjweeks]No, ubuntu does not come with a firewall but some isp's block port 22(ssh). You should run this [test]("https://www.grc.com/x/ne.dll?bh0bkyd2") from the box the ssh server is on.[/QUOTE]

Thanks about the idea... I had that port blocked because of my router, I made a mistake forwarding port22 to another private ip.. :-k I know... its a little stupid mistake... after changing that now my SSH 22 port appears open.. 

I'll try tomorrow to connect again from my school and see whats happens this time, thank you very much about helping, I'll post again tomorrow to say what happened. I had also seen that my Public IP is a dinamic one... so I've done a "no-ip" forward that autorefreshes to the actual IP every 5 minutes... hope this works.

devilpaco

---

### Post by devilpaco on 2006-02-03
I've just tried to connect now, and it continues saying "connect to host XX.XXX.X.XXX port 22: Connection timed out"

The computer responds to ping so I'ts on now, I've tried to found solutions about it but it seem that this problem affects only to me... maybe there's something wrong in the confiugration or something like that...

I've tried to access the lan configuration in the school to see if the port 22 is opened here, it's necessary to be like that? does it matters? thank you everyone for helping and wasting time here helping.

---

### Post by bjweeks on 2006-02-03
Yes, it does if your school blocks port 22 outbound it won't work. Have you run the port test on your computer yet?

---

### Post by devilpaco on 2006-02-03
Yes I've done it in the computer with the server ssh and 22 port is opened, the test says:
> 
Solicited TCP Packets: RECEIVED (FAILED) — As detailed in the port report below, one or more of your system's ports actively responded to our deliberate attempts to establish a connection. It is generally possible to increase your system's security by hiding it from the probes of potentially hostile hackers. Please see the details presented by the specific port links below, as well as the various resources on this site, and in our extremely helpful and active user community.

Unsolicited Packets: PASSED — No Internet packets of any sort were received from your system as a side-effect of our attempts to elicit some response from any of the ports listed above. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system remained wisely silent. (Except for the fact that not all of its ports are completely stealthed as shown below.)

Ping Reply: RECEIVED (FAILED) — Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.


So It means that I can receive packets on port 22 doesn't it?

I've searched a test to see if the port 22 is opened outbound to run it on the school computer and see if as you say thats the problem, but I've not found any, can anyone help me with a way to see it or something similar, the computer in school has winbugs XP SP2, I've disabled the firewall just in case.

Thank you very much

---

### Post by bjweeks on 2006-02-03
If you run the common ports test what color is port 22 come up?

---

### Post by devilpaco on 2006-02-04
In the Common Ports Test, port 22 appears red with the text "OPEN".

Thank you for your time.

Devilpaco

---

### Post by bjweeks on 2006-02-04
Then there is no issue on the server side.

---

### Post by devilpaco on 2006-02-05
thank you very much to solve my doubts, so in the end the conclusion is that is not a problem of computer C... so the problem is in the client computer? Does it need any requirement except to have the ssh client installed??, I've tried to search info about it but I didnt found anything

thankyou very much

devilpaco

---

### Post by diebels on 2006-02-05
Is the client computer that can't connect behind a proxy?

---

### Post by devilpaco on 2006-02-06
No it isn't... thankyou about helping I've searched some problems like this but I've no clue of what can it be...

---

