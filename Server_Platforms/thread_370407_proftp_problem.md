---
title: "proftp problem"
date: 2007-02-25
forum: Server Platforms
---

### Post by hratz on 2007-02-25
Hi,

I am unable to view my directory listing when logging into my proftp server remotely.  
If I log in to localhost there is no problem. (see below)

proftpd is listening on port 1980. (see below /etc/proftpd.conf)
I am using passive ports 60000-60100.
I suspected the problem was due to my router so I opened the above ports.  Now I think the problem is due to the fact that Ubuntu closes all ports by default.  
I have no firewall running and I haven't been able to find any information on how to open the needed ports in Ubuntu (if that is indeed the problem).

Any help on the matter would be greatly appreciated.  Thank you.

-----------------------------------------------------
gregory@thazserv1:~$ ftp localhost 1980
Connected to localhost.localdomain.
220 hello
Name (localhost:gregory): userftp
331 Password required for userftp.
Password:
230 welcome !!!
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful
150 Opening ASCII mode data connection for file list
drwxrwxrwx   2 (?)      (?)          4096 Feb 25 15:22 download
-rw-r--r--   1 (?)      (?)             0 Feb 25 15:58 ftproot
-rw-r--r--   1 (?)      (?)             0 Feb 25 15:22 one
drwxr-xr-x   2 (?)      (?)          4096 Feb 25 15:22 upload
-rw-r--r--   1 (?)      (?)           166 Feb 25 15:57 welcome.msg
226 Transfer complete.
ftp> quit
221 Goodbye.
gregory@thazserv1:~$ ftp xx.xx.xx.xx 1980
Connected to xx.xx.xx.xx.
220 hello
Name (xx.xx.xx.xx:gregory): userftp
331 Password required for userftp.
Password:
230 welcome !!!
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
500 Illegal PORT command
ftp: bind: Address already in use
ftp> quit
221 Goodbye.
-----------------------------------------------------------------------------

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
#AuthAliasOnly on

# Choose here the user alias you want !!!!
#UserAlias sauron userftp

ServerName			"Debian"
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

TimeoutLogin                    40

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
Port				1980

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
ServerIdent                  on       "hello"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

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

PassivePorts 60000 60100	# These ports should be safe...
IdentLookups off

---

### Post by towerofpower256 on 2007-09-17
I'm having a similar problem. I can access my server from the local network with no issues but when I try to access it by using the internet address, it jams on LIST.

---

### Post by hobojjr on 2007-09-29
me too. In fact I can connect the ftp from internet via command line like "ftp myhost" but when I try to execute ls or dir it die with the following

227 Entering passive mod(192,168,1,102,150,154)

Anyone knows whats going on and how to fix it?

---

### Post by hobojjr on 2007-09-29
if I don't do ls or dir then I am actualy able to mkdir and such...

---

### Post by Smartin on 2007-10-05
Hi,

I'm in the same spot...

I can access the ftp server from inside the LAN but not from outside.

Did anyone find a solution?

Am I right in thinking that only port 21 is incoming and so is the only one which needs forwarding from the router? Passive ports are outgoing, yes?

Simon

---

### Post by Smartin on 2007-10-06
Hi,

I made it work, to my amazement...

I have my router forwarding ports 20+21 to my server.

I have my firewall set to accept traffic on ports 20+21 and 60000-70000, which are my passive ports.

Worked for me.

Simon

---

