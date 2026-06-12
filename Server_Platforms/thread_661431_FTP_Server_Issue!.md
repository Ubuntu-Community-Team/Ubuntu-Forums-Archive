---
title: "FTP Server Issue!"
date: 2008-01-07
forum: Server Platforms
---

### Post by Zeliwin on 2008-01-07
Well, I installed proftpd software onto my Ubuntu Server Edition 7.10 (I have a desktop enviroment) I went through the little tutorials people have, and still my question remains unanswered. I can't seem to link my IP address to the server.  It just uses the unusable one 192.168.0.2 which my router provides it. But not the real IP address. I even change the server name in the conf file to the Dynamic IP address ([www.mydomain.com](www.mydomain.com) w/e w/e) and still a no go. Any suggestions? It'll be helpful I run a game server etc etc and my other maintainers need to be able to upload there working progresses onto my server.

---

### Post by p_quarles on 2008-01-07
The address assigned by the router is far from useless: it's a LAN address, and that's the only kind that can be assigned to individual computers on a home network. 

To get your FTP and game servers working, you'll need to configure the router to "forward" the appropriate ports to the server's LAN IP address. You'll need to login to your router's configuration interface to set this up.

---

### Post by Zeliwin on 2008-01-07
Hehe, I did all this already. I forworded port 2008 (port I am using) to 192.168.0.2 which is the LAN address of my box. My game server is working fine, and so is my DNS name (pwmangband.game-host.org) My problem is my ftp won't use the address pwmangband.game-host.org, not even the raw IP address, I know and I've done lots of forwarding. 

I can connect to the ftp by connecting to 192.168.0.2 on my home Network, So I opened port 2008, (I even tryed 21) and set my ftp client to that port, reset it and then tryed it, still a no go pwmangband.game-host.org doesn't work only 192.168.0.2. Resulting in  my maintainers can't connect to upload, only people on my Network can. 

I receive this error when trying to connect to pwmangband.game-host.org

connected to pwmangband.game-host.org
connection closed by remote host
 
All ports are opened, no reason why it won't connect -shrugs-

---

### Post by p_quarles on 2008-01-08
The fact that you're getting a "connection closed by remote host" error (rather than a simple hangup) suggests that the connection itself is okay, and that the problem is with the server. 

I have more expertise with sftp than with proftpd, so I'm not sure how much I can help. Nonetheless, if you could post your config file, I and others here can try to look for solutions there.

---

### Post by Zeliwin on 2008-01-08
Yeah, no problem.

#To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias sauron userftp

ServerName			"pwmangband.game-host.org"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port				2008

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

---

### Post by Zeliwin on 2008-01-08
Any help?

---

### Post by koenn on 2008-01-08
> **p_quarles said:**
> The fact that you're getting a "connection closed by remote host" error (rather than a simple hangup) suggests that the connection itself is okay, and that the problem is with the server. 

I have more expertise with sftp than with proftpd, so I'm not sure how much I can help. Nonetheless, if you could post your config file, I and others here can try to look for solutions there.

could it not be one of these active vs. passive ftp things (I always forget which is which) and you need to choose the one where the server opens the datachannel i.s.o. the client, because the latter case won't work through NAT/firewall (but would usually  work when on the same LAN).

I can't find any option in that config file the set it to passive (or active) ftp - maybe you need to look that up

---

