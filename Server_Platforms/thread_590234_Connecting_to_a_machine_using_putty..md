---
title: "Connecting to a machine using putty."
date: 2007-10-24
forum: Server Platforms
---

### Post by jusama14 on 2007-10-24
How can I connect to my computer at home via putty.
Well preferably a desktop connection but putty is a start. I have multiple computers on the same ip all running ubuntu but I only want to connect to 1 of them. 
How would I do this?

---

### Post by MJN on 2007-10-24
Presumably you're talking via SSH? If so, you need to set your router to forward port 22 to whichever machine you want to connect to. The destination machine will of course have to be running an SSH server.

If you require the ability to connect to one of several machines then you will need to set each machine's SSH service to listen on a different port - the router can then be set to forward each specific port to a specific machine. When connecting with Putty you would distinguish between machines by specifying its particular port.

Does that make sense? Have I understood your requirement properly?

Mathew

---

### Post by jusama14 on 2007-10-24
Is it possible to only change the port of the machine I'm trying to connect to or does it have to be port 22?
Right now if I type in the ip and port 22 into putty it works..asks for usernamd and password but the info I enter it says access denied.
Also how would I change the port?

---

### Post by codmate on 2007-10-25
> **jusama14 said:**
> Is it possible to only change the port of the machine I'm trying to connect to or does it have to be port 22?
Right now if I type in the ip and port 22 into putty it works..asks for usernamd and password but the info I enter it says access denied.
Also how would I change the port?

There should be a file in /etc called sshd.conf.
You can change the port in there.

Don't forget to update your iptables rules to the new port.

---

### Post by MJN on 2007-10-25
If you're connecting successfully (i.e. getting the username prompt, and then the password prompt) then it's likely you need to specifically allow your user to access SSH.
 
As above, look in /etc/ssh/sshd.conf and find the AllowUsers directive - add your user to this line. If you need further clarification post the contents of the file and we can take a look.
 
Mathew

---

### Post by timcredible on 2007-10-25
if what you really want is a desktop connection, just do that.  what you're wanting is an xdm connection, on the server (the machine you're connecting to) System -> Administration -> Login Windows, Remote tab -> change style to Same as local, then Security tab, and uncheck Deny TCP connections to Xserver, and then reboot.  Then on the client machines, install Xnest via synaptic. Then type in Xnest :30 -query <your server IP address> and you get the same exact desktop in that window that you get when you're on the console.

---

### Post by jusama14 on 2007-10-25
I'm trying to connect to the linux machine from a windows machine.
Here is my /etc/ssh/sshd_config file. I don't "AllowUsers" anywhere in the whole document.

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
AuthorizedKeysFile	%h/.ssh/authorized_keys2

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

### Post by MJN on 2007-10-25
First things first, from a security perspective change the **PermitRootLogin** from **yes** to **no**... (but that's not relevent here unless you're attempting to login as root).
 
The lack of an **AllowUsers** directive simply means it's not restricted (i.e. allow all) so it's not that...
 
So what is it then? Nothing jumps out at me as being wrong...
 
What does your **/etc/log/auth.log** file say when you attempt (yet fail) to login remotely? It should detail *why* access was denied.
 
Mathew

---

### Post by jusama14 on 2007-10-25
The file is blank.

---

### Post by lrhogusa on 2007-11-09
I read through here briefly and didn't see if you set up your putty connection to be ssh1 or ssh2. I remember using putty in the past and I had to set the connection type first on the putty side. The default on putty might be telnet or ftp and that stuff might be turned off on the Linux box side.

---

