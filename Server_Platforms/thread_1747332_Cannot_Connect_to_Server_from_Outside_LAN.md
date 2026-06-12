---
title: "Cannot Connect to Server from Outside LAN"
date: 2011-05-02
forum: Server Platforms
---

### Post by flyingsuperhigh on 2011-05-02
Hello,

This problem has been bothering me for a while now. Basically I am trying to set up my own server so that I can ssh into it from anywhere. I am able to SSH into my server when I use the LAN IP of my server but I am not able to SSH into it if I use the public IP address. I have read many threads and in my opinion I've tried almost all of the common fixes suggested. One possibility may be that my ISP has blocked port 22. I have taken this into consideration and sent them an email and I'm presently waiting for a reply. However, I highly doubt that my ISP has restricted acess to port 22. I would really like to be able to SSH into my server from anywhere. Hence, I will post a detailed outline of the procedure I followed and I'm hoping someone can find a solution.

1)I installed openssh client/server using the following commands:
```
sudo apt-get install openssh-client
sudo apt-get install openssh-client
```

2)I forwarded port 22 on my router. (see attachment for the settings)

3)I modified /etc/ssh/sshd_config such that my server has a static LAN address.

contents of sshd_config file:
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

I then entered the command: 
```
sudo /etc/init.d/ssh restart
```

4.I turned off the firewall using the command:
```
sudo ufw disable
```

5.Here is the output of the IP tables:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

---

### Post by Demented ZA on 2011-05-02
Can you connect to your server with ssh from inside your network (on the same subnet and interface as your server)?

Your config file has SSH set to accept connections on all interfaces as is the default. 

If you can connect to your server from within the lan, I can guarantee you the problem is not with ssh or the way your server is set up, thus meaning its a routing problem: router configuration or isp blocking ports. 

Also, are you sure you are connecting to the right external IP address? You can verify by getting into your router's remote administration page from outside your network.

---

### Post by flyingsuperhigh on 2011-05-02
Firstly, I just want to make a correction. To make my server have a static IP I modified the etc/network/interfaces file and not the etc/ssh/sshd_config file like I mentioned in my original post.

Here are the contents of the interfaces file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

iface eth0 inet static
        address 192.168.0.108
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.0.1
 
```

I am able to connect from LAN which probably means I have something wrong in my router configuration or my ISP may be blocking port 22. In addition to forwarding port 22 in the router configuration, is there anything else in particular which must be done?

---

### Post by volkswagner on 2011-05-02
> **flyingsuperhigh said:**
> 
I am able to connect from LAN which probably means I have something wrong in my router configuration or my ISP may be blocking port 22. In addition to forwarding port 22 in the router configuration, is there anything else in particular which must be done?

You can verify if port 22 is open by navigating to [canyouseeme.org]("http://canyouseeme.org") and check port 22.  Do this from inside your LAN from any PC on the same network as your server.  You can do this rather than waiting to hear back from your isp, which may give you inaccurate results.... LOL

To clarify:  Have you tried this from physically outside of you LAN?  There can be a second issue when trying your public ip from inside your LAN, called NAT redirection or reflection, which may be enabled or disabled on your router.

---

### Post by flyingsuperhigh on 2011-05-02
When I go to canyouseeme.org I get a connection timed out message. I called my ISP and they said that they don't block port 22. Thus, this probably means that I didn't configure my router's settings properly.

For your second comment, I've tried SSH'ing into my server while being connected to my school's network via a VPN connection and still being connected to my home network. Thus, I guess I may be affected by NAT redirection/reflection. 

Nonetheless, I believe the real issue is related to my router being improperly configured. Since, my ISP is not blocking port 22, when I go to canyouseeme.org, port 22 should be opened but it's giving a connection timed out message. I can upload more screen shots of my router's settings if you feel that the problem does lie in the router's configuration.

---

### Post by volkswagner on 2011-05-02
I'm not familiar with your router's virutal server settings.  Your information looks correct to me.

Have you tried, or can you try directly adding the port 22 forward at the "Port Forwarding" section for the router web interface.  Since you are using public port 22 and private port 22, I don't think you are using the "Virtual" portion anyway.

---

### Post by hawk2010 on 2011-05-03
My question is that are you using a static IP address for the server? If so please change the listen directive and set that static IP address there so it will listen to that.

Also you have a pretty bad security issue.

Set the PermitRootLogin to no ( otherwise you server will get pwned[hacked] pretty soon)
Also it is not a wise idea to disable the firewall when you can set a rule to simply allow ssh like

ufw allow 22                                                              


> **flyingsuperhigh said:**
> Hello,

This problem has been bothering me for a while now. Basically I am trying to set up my own server so that I can ssh into it from anywhere. I am able to SSH into my server when I use the LAN IP of my server but I am not able to SSH into it if I use the public IP address. I have read many threads and in my opinion I've tried almost all of the common fixes suggested. One possibility may be that my ISP has blocked port 22. I have taken this into consideration and sent them an email and I'm presently waiting for a reply. However, I highly doubt that my ISP has restricted acess to port 22. I would really like to be able to SSH into my server from anywhere. Hence, I will post a detailed outline of the procedure I followed and I'm hoping someone can find a solution.

1)I installed openssh client/server using the following commands:
```
sudo apt-get install openssh-client
sudo apt-get install openssh-client
```2)I forwarded port 22 on my router. (see attachment for the settings)

3)I modified /etc/ssh/sshd_config such that my server has a static LAN address.

contents of sshd_config file:
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
```I then entered the command: 
```
sudo /etc/init.d/ssh restart
```4.I turned off the firewall using the command:
```
sudo ufw disable
```5.Here is the output of the IP tables:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

---

### Post by flyingsuperhigh on 2011-05-03
Okay so my router is being really annoying to me. As a result, I am thinking of connecting my server directly to my modem. If I do this, will I be able to ssh into it from outside (not on LAN)? Also, if this does work what files would I have to change and what would I have to change in them? I'm guessing that I definitely would have to change the /etc/network/interfaces file but I'm not sure what to put in there. Assume for now that I have a static public IP.

---

### Post by flyingsuperhigh on 2011-05-03
nvm. Please ignore my previous post.

---

### Post by usatonycuba on 2011-05-03
I'm going to remark @hawk2010 previous post... you might wanna take care of thus security issues... So

Change 

Make enable your firewall, then simply allow it ssh in ufw like [COLOR=DarkRed]ufw allow 22 [/COLOR]

Wondering.... after making changes did you [COLOR=DarkRed]/etc/init.d/networking restart[/COLOR] ?.... Do you have [COLOR=DarkRed]apparmor [/COLOR]enable..?, Since it does give me erratic behavior on my server, I always do:
```

 /etc/init.d/apparmor stop
 update-rc.d -f apparmor remove
 aptitude remove apparmor apparmor-utils

```> **volkswagner said:**
> I'm not familiar with your router's virutal server settings.  Your information looks correct to me.

Have you tried, or can you try directly adding the port 22 forward at   the "Port Forwarding" section for the router web interface.  Since you   are using public port 22 and private port 22, I don't think you are   using the "Virtual" portion anyway.
+1  lo

@flyingsuperhigh in order to connect to a private ip address.. you have  to allow the network traffic  connection  from your router via port  forwarding...Take a look to [http://portforward.com/help/pfprogression.htm](http://portforward.com/help/pfprogression.htm)

---

