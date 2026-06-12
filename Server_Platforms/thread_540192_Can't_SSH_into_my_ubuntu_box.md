---
title: "Can't SSH into my ubuntu box"
date: 2007-09-01
forum: Server Platforms
---

### Post by barnjo on 2007-09-01
I have my Ubuntu desktop in front of me, and my Apple MacBook next to that.

They are both on my LAN.

I can ssh from my ubuntu box into my OS X laptop no problem.

However, I can't ssh from my MacBook into my Ubuntu box.

~: ssh jonny@192.168.2.7

just times out, it doesn't even get a connection refused or dropped or anything.

I think the issue is the output of the command - sudo netstat -nlp | fgrep :22 is

```
jonny@jonny-ubuntu:/etc/ssh$ sudo netstat -nlp | fgrep :22
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     5059/hpiod          
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN     5062/python         
tcp6       0      0 :::22                   :::*                    LISTEN     12937/sshd
```

It appears ssh is only listening using ipv6 when im using ipv4.

Any help? thnx

---

### Post by NewbieNik on 2007-09-01
whats the content of your /etc/ssh/sshd_conf file?

---

### Post by barnjo on 2007-09-01
/etc/ssh/sshd_config:

```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
Port 7753
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
```

---

### Post by NewbieNik on 2007-09-01
OK, identical to mine apart from the ports. Only other difference is the MAC. Try changing your ports in the conf file to 22 only  and then
Sudo /etc/init.d/ssh restart
then try ssh from MAC to see if the mac is forcing that port.

also, dont use a name, just ssh into the ip address and it should ask for username and password
If that still does´t work, let us know and we shall look further...

---

### Post by barnjo on 2007-09-01
sticking the verbose flag into the command shows that the MacBook is trying to connect on port 22 and it still times out.

---

### Post by galeron on 2007-09-01
Does using port 7753 (the other port in your config file) help?

ssh -p 7753 username@<your ubuntu box ip>

---

### Post by barnjo on 2007-09-01
Nope, Ive booted up another laptop using a Ubuntu live cd and that can't ssh into my ubuntu box either.

---

### Post by wirelessmonkey on 2007-09-01
Have you been playing with IPTables or one of the firewall configuration utilities like FireStarter or GuardDog? Pull down nmap on your ubuntu machine.  (sudo apt-get install nmap) and run it against localhost. (nmap localhost) Then post the output here.  You may also want to try it from your Mac against your ubuntu machine.

---

### Post by barnjo on 2007-09-01
nmap returned

```
jonny@jonny-ubuntu:/etc/ssh$ nmap localhost

Starting Nmap 4.20 ( http://insecure.org ) at 2007-09-01 21:25 BST
Interesting ports on localhost (127.0.0.1):
Not shown: 1693 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
631/tcp  open  ipp
3306/tcp open  mysql

Nmap finished: 1 IP address (1 host up) scanned in 0.200 seconds
```

sudo iptables -L outputs:

```
jonny@jonny-ubuntu:/etc/ssh$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.2.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.2.1          anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  anywhere             192.168.2.255       
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.2.7          192.168.2.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.2.7          192.168.2.1         udp dpt:domain 
ACCEPT     0    --  anywhere             anywhere            
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
OUTBOUND   0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:8008 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:8008 
LSI        0    --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       0    --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere            

```

---

### Post by James79 on 2007-09-01
Post the results of using nmap against your ubuntu box from your mac.

Can you ssh to it from itself? ie: ssh localhost

---

### Post by lamnk on 2007-09-01
First check if ssh service is up and running ? Like James79 mentioned above, 'ssh localhost' to see ...

If yes then try to delete all your iptables rules with 'sudo iptables -F'. I've several times locked myself up outside my server because iptables blocked ssh port

If no then initialize ssh: 'sudo /etc/init.d/ssh start'

---

### Post by barnjo on 2007-09-01
Having finally got nmap installed on my MacBook, I ran it and I got the following message:

```
./nmap 192.168.2.7

Starting Nmap 4.20 ( http://insecure.org ) at 2007-09-01 23:16 BST
Note: Host seems down. If it is really up but blocking our ping probes, try -P0
Nmap finished: 1 IP address (o hosts up) scanned in 2.029 second
```

adding the -P0 it justs sits there, doing nothing, scrub that I tried again using the -v flag as well and its just taking a long time (5mins+)

having issued the command ./nmap 192.168.2.7 -P0 -v it repaorts that all 1697 ports scanned were filtered

---

### Post by James79 on 2007-09-02
Well then clearly there's a firewall dropping your packets. Did you try flushing your iptables as was suggested?

---

### Post by steve.horsley on 2007-09-02
Ad far as I can tell, the firewall is wide open. see this:
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.2.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.2.1          anywhere            
[COLOR="Red"]ACCEPT     0    --  anywhere             anywhere[/COLOR]    
...        

```
That line is allowing everything in - all the following lines are irrelevant.

If I've misread this, someone please correct me.

---

### Post by barnjo on 2007-09-02
Thanks guys, I can now ssh into my ubuntu box.

cleared iptables to read:

```
jonny@jonny-ubuntu:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

---

