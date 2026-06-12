---
title: "ssh connection with putty from xp wont work ..."
date: 2009-03-17
forum: Server Platforms
---

### Post by fabianus on 2009-03-17
Hello all !

I installed the openssh server :

sudo apt-get install openssh-server


then I installed the putty client : 

sudo apt-get install putty putty-tools



And I may connect well from local (either user localhost or the machine's IP). 

Now if I use putty from my Windows XP machine I always get the same error once I type in the password : 
Access denied

Thanks a lot for any hint on this !

Regards, 
Fabianus

---

### Post by hictio on 2009-03-17
**Tests**:

_On the Server itself_:

Do you have an internal firewall running on the Ubuntu Server?
On the Server, type this:

```

sudo ufw status ENTER

```

And see if there any active rules.
Other place to check is the '/etc/hosts.allow' & '/etc/hosts.deny' files.

_From the Windows box_:

Can you ping the Ubuntu Server?
Are both boxes on the same network? (Could it be that there is a firewall blocking SSH access before it even reaches the Ubunut Server?)
Are you trying to access the Ubuntu Server from the Internet? 

Try the very basic network test:

```

telnet ip.address.Ubuntu.Server 22 ENTER

```

Do you connect to the server?

---

### Post by fabianus on 2009-03-17
Hello hictio, 

thanks a lot for your suggestions !

I did a telnet from my WinXP machine and I could connect to the server. 

And here are the answers to your questions : 

Can you ping the Ubuntu Server?
> yes ! (I can for example browse a website that I run on the ubuntu server from the XP machine)

Are both boxes on the same network?
> Yes!

Could it be that there is a firewall blocking SSH access before it even reaches the Ubunut Server?
> There is no firewall between them and no firewall active on the Ubuntu 8.10 server.

Are you trying to access the Ubuntu Server from the Internet?
> no, from the local network. 

Do you have an internal firewall running on the Ubuntu Server?
> Status: not loaded

Thanks a lot for any feedback !

Regards, 
Fabianus

---

### Post by uberlinux on 2009-03-17
> **fabianus said:**
> Hello hictio, 

thanks a lot for your suggestions !

I did a telnet from my WinXP machine and I could connect to the server. 

And here are the answers to your questions : 

Can you ping the Ubuntu Server?
> yes ! (I can for example browse a website that I run on the ubuntu server from the XP machine)

Are both boxes on the same network?
> Yes!

Could it be that there is a firewall blocking SSH access before it even reaches the Ubunut Server?
> There is no firewall between them and no firewall active on the Ubuntu 8.10 server.

Are you trying to access the Ubuntu Server from the Internet?
> no, from the local network. 

Do you have an internal firewall running on the Ubuntu Server?
> Status: not loaded

Thanks a lot for any feedback !

Regards, 
Fabianus

Fabian, could you try restarting the sshd service?
> sudo /etc/init.d/sshd restart

Maybe you could post your sshd_config file from /etc/sshd?

---

### Post by fabianus on 2009-03-17
Hello uberlinux,

thanks for participating :-)

Yes, I did restart dozents of times. 


Here is my config : 

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

UsePAM yes



Thanks a lot for any further suggestion !

Regards, 
Fabianus

---

### Post by uberlinux on 2009-03-17
> **fabianus said:**
> Hello uberlinux,

thanks for participating :-)

Yes, I did restart dozents of times. 


Here is my config : 
khgkhgshs



Thanks a lot for any further suggestion !

Regards, 
Fabianus

I just diff'd yours and mine, and the only thing that's different on yours is:
< PasswordAuthentication yes

Mine's commented out.  I don't know if it's that much of a lead, but maybe you can comment your out and see if it changes anything.  (after you restart the service, of course)

---

### Post by fabianus on 2009-03-17
uberlinux, 

thanks for the quick feedback - that's speedy support :-)

I commented it out (as it was before), but still have the same problem. 

Do you have any other idea ?

Regards, 
Fabianus

---

### Post by lordadi on 2009-03-17
I dont know about others, but I always ensure that I have this line in there:

```
AllowUsers <username on server here>
```

This I do mainly from a security perspective and *perhaps by doing this your login will work as I suspect that it will force your server to deny other logins and see just one. Be sure to restart your server before attempting a connect!

Also try to ssh into your server FROM your server using ```
ssh localhost
``` if you can login then the problem is with your xp box or xp firewall or network, probably not your server.

Let me know how goes, 


Lordadi.

---

### Post by fabianus on 2009-03-17
Hi Lordadi, 

thanks for joining !

I already tried this (and did it again now), but no success. 
Don't forget : I may connect through putty if I do it from the local machine (putty installed on ubuntu server), but not through putty from WinXP ...

Hope this helps for any further suggestion :-)

Regards, 
Fabianus

---

### Post by lordadi on 2009-03-17
can you show us what your putty settings look like? (a screenshot maybe?) I think the problem is with putty.

---

### Post by uberlinux on 2009-03-17
> **fabianus said:**
> Hi Lordadi, 

thanks for joining !

I already tried this (and did it again now), but no success. 
Don't forget : I may connect through putty if I do it from the local machine (putty installed on ubuntu server), but not through putty from WinXP ...

Hope this helps for any further suggestion :-)

Regards, 
Fabianus

ooo.  I wonder if it's a username problem then.  I always use the command line from my mac to ssh into the ubuntu server.  I'm wondering if putty is feeding something stupid as the username from the XP box.  Does your logon in XP differ at all from your username in Ubuntu?  I'm wondering if putty is somehow feeding: ssh -p22 XPusername@ubuntubox rather than ssh -p22 ubuntuusername@ubuntubox???


Maybe this part of putty:
# Plink (a command-line interface to the PuTTY back ends) 
will allow more verbose interaction with your ubuntu box?

Can you go to Start | Run:  type: cmd, [ENTER]
then try to execute plink?

---

### Post by fabianus on 2009-03-17
Guys, it's all ok. Following the suggestion of uberlinux to try plink I discovered that for some reason when I do : 

c:\plink myuser@myhost
it still askes me for the login 
and the writes : 
myuser@myWinXPip password:

So in fact it does not take into account the correct host ...

So I tried putty on another XP machine ... and everything went fine !

So thanks a lot to you all, this is a great community !

Regards, 
Fabianus

---

### Post by lordadi on 2009-03-17
that would do it, glad to hear you got it working!!:D

---

### Post by lvleph on 2009-03-17
If you don't mind trying something else, I would suggest using cygwin and just straigh ssh. Cygwin is nice because it gives you close to the power of bash in windows.

---

### Post by Alex Yeh on 2009-03-18
> **lvleph said:**
> If you don't mind trying something else, I would suggest using cygwin and just straigh ssh. Cygwin is nice because it gives you close to the power of bash in windows.

I second this. When I need to ssh to another system from within Windows, I prefer to use openssh on cygwin (I usually compile the latest portable, but cygwin's version is fine for most folks). Another cool thing about having openssh on cygwin is, it makes it possible to ssh into your windows computer (provided you have added a batch script to run sshd on startup).

---

