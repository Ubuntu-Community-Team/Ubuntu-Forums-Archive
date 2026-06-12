---
title: "Question about proftpd on 11.04 server"
date: 2011-10-29
forum: Server Platforms
---

### Post by kustomjs on 2011-10-29
Hey Guys
I have a question about proftpd and user directory's on 11.04 server the question is I have a directory called public_html and what I want to do is when customer ftp I want them go to the public_html directory directly and noting else how do I set that up?

---

### Post by Lars Noodén on 2011-10-29
That's easier to do with SFTP which can be chrooted easily.   

From /etc/ssh/sshd_config:
```

Subsystem sftp internal-sftp

Match Group webmasters
        ChrootDirectory %h/public_html/
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

```

SFTP clients are built into Nautilus, Dolphin and FileZilla. If you have SSH already then you have SFTP up and running and do not need [FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/) any more.

---

### Post by kustomjs on 2011-10-29
so the ssh port needs to be open correct on firewall to do this?

---

### Post by Lars Noodén on 2011-10-29
Yes, port 22.

---

### Post by kustomjs on 2011-10-29
now how secure is that to have port 22 open to the net?

---

### Post by Lars Noodén on 2011-10-29
It's fine, if you ensure that root log in is turned off and either the users have long passwords or, best, use keys for authentication.   What ever port you open to the net will get hammered, SSH is one of the safer services if the above advice is followed.

You can also use IP Tables to limit the rate at which new connections can be tried.

---

### Post by Dangertux on 2011-10-29
> **kustomjs said:**
> now how secure is that to have port 22 open to the net?

In addition to the other reply which explained some very good principles you can also use something like denyhosts or fail2ban to secure SSH. 

Also ultimately, the answer to the question is SSH is much more secure being exposed to the internet than FTP.

Hope this helps.

---

### Post by kustomjs on 2011-10-29
Well this server will be going behind either a smoothwall or pfsense firewall.

---

### Post by Lars Noodén on 2011-10-29
Smoothwall is linux based so it will have IP Tables, so you can limit the brute force attacks something like this:

```

   ip6tables -N SSH;    # create chain
   iptables  -N SSH;    # create chain

   # send all incoming SSH trafficc to SSH chain
   ip6tables -I INPUT -i eth0 -p tcp --destination-port 22 -m state --state NEW -j SSH;
   iptables  -I INPUT -i eth0 -p tcp --destination-port 22 -m state --state NEW -j SSH;

   # add host to "recent" list
   ip6tables -I SSH -m recent --set --name SSHLIMIT -j ACCEPT;
   iptables  -I SSH -m recent --set --name SSHLIMIT -j ACCEPT;

   # allow finite number of new connections per time limit
   ip6tables -I SSH -m recent --update --seconds 60 --hitcount 4 --name SSHLIMIT -j REJECT
   iptables  -I SSH -m recent --update --seconds 60 --hitcount 4 --name SSHLIMIT -j REJECT

```

PFSense uses [PF](http://home.nuug.no/~peter/pf/en/bruteforce.html) and rate limiting is also easy.

---

### Post by kustomjs on 2011-10-29
I also just tried that code and it does not go directly into the public_html

here is what I did to the code:

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

Match Group webmasters
        ChrootDirectory %h/public_html/
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

```

is that correct?

---

### Post by Lars Noodén on 2011-10-29
Do you have a group 'webmasters' and are the accounts to be chrooted members of it?

---

### Post by kustomjs on 2011-10-29
no I dont have any groups called webmasters or anything like that. But I do have a group called users.

---

### Post by Lars Noodén on 2011-10-30
The group in [Match Group](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) has to exist and contain the accounts you wish to chroot.  You can make the group and fill it with users if you need it.

---

### Post by kustomjs on 2011-10-30
Well I was able to get the user get into public_html but I want to fix this issue and the issue is the user can still see other other users directory how do I make this user only see his directory?

---

### Post by Lars Noodén on 2011-10-30
> **kustomjs said:**
> Well I was able to get the user get into public_html but I want to fix this issue and the issue is the user can still see other other users directory how do I make this user only see his directory?

If your sshd_config has a Match directive like in [#2](http://ubuntuforums.org/showpost.php?p=11406353&postcount=2) above, then it should just be a matter of 1) creating a group called 'webmasters' and then 2) adding the user to that group.

---

### Post by kustomjs on 2011-10-30
It really dont make any since if I take out this:

Match group webmasters
    ChrootDirectory %h/public_html/
    X11Forwarding no
    AllowTcpForwarding no
    ForceCommand internal-sftp

and restart it and try to connect its saying cant connect to server.

---

### Post by Lars Noodén on 2011-10-30
Here is an overview of the three main parts of the configuration. [sshd_config](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) will have more details.


Match group is needed, so that the changes apply only to a subset of users.  Otherwise you will lock yourself out.

ChrootDirectory specifies where the chroot jail shall be for the users.

ForceCommand internal-sftp forces the session into the sftp subsystem and prevents shell access.

---

### Post by kustomjs on 2011-10-30
Alright the user still as root and group as webmaster and I tried it again its still saying cant connect.

---

### Post by Lars Noodén on 2011-10-30
> **kustomjs said:**
> Alright the user still as root and group as webmaster and I tried it again its still saying cant connect.

Try it with a regular user.  Root should not be messed with.

---

### Post by kustomjs on 2011-10-30
Alright it works ok with group as users but it dont work as webmasters. Am I doing something wrong or what?

---

### Post by kustomjs on 2011-10-31
Lars Noodén or anybody else can help?

---

### Post by Lars Noodén on 2011-10-31
The only think I can think of is to repeat what  I wrote in [#2 above](http://ubuntuforums.org/showpost.php?p=11406353&postcount=2).  The directives shown there go at the end of your /etc/ssh/sshd_config file.  

From #10 above, you appear to have done that. 

For that to work, you need to have created a group "webmasters" and put the users to be chrooted into that group.

---

### Post by kustomjs on 2011-10-31
but see if I put the users in webmaster and then I try to connect it say cant connect to the server that is where I dont understand why its not working at all.

I mean I am willing to take a video of it and show you what I am talking about.

---

### Post by Lars Noodén on 2011-10-31
> **kustomjs said:**
> but see if I put the users in webmaster and then I try to connect it say cant connect to the server that is where I dont understand why its not working at all.

I mean I am willing to take a video of it and show you what I am talking about.

If you put the users in the group "webmasters" then they should only be able to connect using SFTP, not SSH anymore.

---

### Post by kustomjs on 2011-10-31
Alright here is what I will do I will create a video what I am talking about.

---

### Post by kustomjs on 2011-10-31
here is the videos:
[http://www.youtube.com/watch?v=Wngtyq9xoEg](http://www.youtube.com/watch?v=Wngtyq9xoEg)
[http://www.youtube.com/watch?v=CMhGvJd9stQ](http://www.youtube.com/watch?v=CMhGvJd9stQ)

---

### Post by Lars Noodén on 2011-10-31
The screen in the second video did not show the full list of groups that 'test9' was a member of.  What is the output of 
```

groups test9

```
when run in the shell?

Also what is the exact text of the error message when SFTP fails to connect?

---

### Post by kustomjs on 2011-10-31
here you go:

root@userpages:~# groups test9
test9 : users
root@userpages:~#

after making changes:

root@userpages:~# groups test9
test9 : webmasters
root@userpages:~#

while try to connect test9 while user is in group: webmasters:

Status:	Connecting to 192.168.0.198...
Response:	fzSftp started
Command:	open "test9@192.168.0.198" 22
Command:	Pass: ****
Error:	Network error: Software caused connection abort
Error:	Could not connect to server

after making switch to user test9 back to users group

Response:	fzSftp started
Command:	open "test9@192.168.0.198" 22
Command:	Pass: ****
Status:	Connected to 192.168.0.198
Status:	Retrieving directory listing...
Command:	pwd
Response:	Current directory is: "/home/test9/public_html"
Command:	ls
Status:	Listing directory /home/test9/public_html
Status:	Calculating timezone offset of server...
Command:	mtime ".bashrc"
Response:	1320073375
Status:	Timezone offsets: Server: -14400 seconds. Local: -14400 seconds. Difference: 0 seconds.
Status:	Directory listing successful

by the way I am using filezilla for my ftp client. So I am going try a different client like coreftp to see if it fixes the issue.

---

### Post by kustomjs on 2011-11-01
Alright I have tried it with core ftp lite while user is under webmasters group and getting this:

Welcome to Core FTP, release ver 2.2, build 1695 (U) -- © 2003-2011
WinSock 2.0
Mem -- 2,097,151 KB, Virt -- 2,097,024 KB
Started on Tuesday November 01, 2011 at 00:14:AM
Resolving 192.168.0.198...  
192.168.0.198 [22] connecting...  
SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3  
client -> aes128
server -> aes128
52:bb:d5:70:47:e0:a9:f6:65:23:0d:1a:1e:e6:cb:71
ssh-rsa
Sending password
SFTP connection error
Connection Failed

so I dont know whats going on.

---

### Post by kustomjs on 2011-11-01
Does anybody know whats going on with this?

---

### Post by kustomjs on 2011-11-01
Ok
I guess nobody got a clue how to fix this issue I guess I will just take the server down.

---

### Post by Lars Noodén on 2011-11-02
I've set up a machine like how you have yours described and looked at the possibilities.  The real error message only turns up in the server logs:  *bad ownership or modes for chroot directory "/home/test9"*  From [sshd_config](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) it turns out that the chroot directory has to be owned by root and no one else should be able to write to it.  

It was my notes that were unclear.

So instead of "ChrootDirectory %h/public_html/", "ChrootDirectory /home/" will work unless you want to change the permissions for the other directories.

---

### Post by kustomjs on 2011-11-02
Well I just dont want other users to see others directory's. So if I have to I will just place it as home and figure out some how make customers go into there own directory.

---

