---
title: "[SOLVED] Passive FTP Problems"
date: 2008-08-01
forum: Server Platforms
---

### Post by computerwolf on 2008-08-01
I have searched all over the net and these forums, and no one seems to have an answer to my problem. I have a ubuntu server set up behind a router and have proftpd installed so I could transfer files. It has worked fine in the past. There is no firewall on the server and ports 21, 20, and the passive ports are all open on the router. Recently, however, the FTP connections start hanging when I attempt to get a directory listing after entering passive mode. On filezilla on my windows box, it will get to **Command:	LIST** and hang, and if I try from the command line on linux it gets to **227 Entering Passive Mode (x,x,x,x,53,213).** and hangs. I have even completely removed proftpd and installed pure-ftpd and vsftpd seperately and the same thing happens. I am thinking this could maybe be caused by some network setting on the server? I am a little lost when it comes to knowing the correct information that goes into files requiring hosts and hostnames and the like. I have even put the server in the DMZ and still nothing.

Here is my proftpd config for reference:

```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				off

ServerName			"ComputerWolf FTP"
ServerType standalone
DeferWelcome off

MultilineRFC2228 on
DefaultServer on
ShowSymlinks			on

TimeoutNoTransfer 600
TimeoutStalled 600
TimeoutIdle 1200

DisplayLogin                    welcome.msg
DisplayChdir               	.message true
ListOptions                	"-l"

DenyFilter			\*.*/

# Use this to jail all users in their homes 
# DefaultRoot			~
DefaultRoot /home/ftp ftpuser

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell		off
RequireValidShell		off

# Port 21 is the standard FTP port.
Port 21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534
PassivePorts 11000 14000

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
MasqueradeAddress X.X.X.X

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 30

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
#Umask				022  022
Umask				000  000

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>

<Limit LOGIN>
AllowGroup ftpuser
AllowUser josh
DenyALL
</Limit>

<Directory /home/ftp>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyGroup ftpuser
	</Limit>
</Directory>

<Directory /home/ftp/mp3s/*>
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyGroup ftpuser
	</Limit>
</Directory>

<Directory /home/ftp/uploads/*>
Umask 000 000
AllowOverwrite on
<Limit CWD MKD DELE RMD RETR STOR READ WRITE DIRS>
Allow all
</Limit>
</Directory>

<Directory /home/ftp/torrents/*>
Umask 000 000
<Limit CWD DELE RMD RETR READ DIRS LOGIN>
AllowAll
</Limit>
</Directory>

DirFakeGroup on
DirFakeUser on
AllowRetrieveRestart on
AllowStoreRestart on
UseReverseDNS off
IdentLookups off
```

---

### Post by computerwolf on 2008-08-03
*bump*

---

### Post by computerwolf on 2008-08-03
Almost 2 days and no one can help?

---

### Post by computerwolf on 2008-08-04
My problem was solved via help on the proftpd irc channel. It turns out that this was a router problem. Many Netgear routers have a feature enabled by default called "SPI Firewall". Disabling this feature allowed the server to be connected to as normal.

---

### Post by MJN on 2008-08-05
Great to hear you're up-and-running - it's a shame noone could help but I'm afraid that's the nature of FTP... full of little nuances waiting to trip you up at every corner. If possible, I would look towards more modern alternatives which have very much learnt from the 'mistakes' of FTP (particularly with regards to ports and security).
 
Mathew

---

