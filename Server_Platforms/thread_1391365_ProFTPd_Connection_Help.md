---
title: "ProFTPd Connection Help"
date: 2010-01-26
forum: Server Platforms
---

### Post by jawsykilla on 2010-01-26
Hi, I'm no expert with Ubuntu but I have set up multiple FTP servers on windows and I have used Ubuntu for a while now so I thought i'd give it a shot. Now I am baffled. I have ProFTPd all set up in the proftpd.conf, i have set the port as 1969, passive ports of 60000 to 60100. I have 3 three user accounts on my ftp server and each when logged in only has permission to their specific directories. It is all working perfectly fine through LAN but when I connect using FTP in Terminal using my external IP it logs in fine but when I try to do anything I get this.

jawsykilla@Saturn-V:~$ ftp
ftp> open xx.xxx.xxx.xxx 1969
Connected to xx.xxx.xxx.xxx.
220 Welcome To Saturn-V, Please Authenticate!
Name (xx.xxx.xxx.xxx:jawsykilla): root
331 Password required for root
Password:
230 Access Granted To Saturn-V
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> dir
500 Illegal PORT command
ftp: bind: Address already in use
ftp> 

Now I have tried using Passive mode but it just hangs when i try to use a PORT command. I have tried using filezilla which lets me see the directories but then I cant do anything with the files. I have an Apple Airport Extreme Router. I have forwarded ports 20, 21, 1969 and 60000 - 60100. DHCP is enabled and it is using NAT.

Here is my proftpd.conf file.

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias root userftp
UserAlias koranzite rmacdonald
UserAlias aarondragon0 awilson

ServerName			"Saturn-V"
ServerType 			standalone
DeferWelcome			on

PassivePorts 60000 60100

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 30

RootLogin 			off

MasqueradeAddress	10.0.1.7      # using an IP address

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port				1969

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
AccessGrantMsg "Access Granted To Saturn-V"
# This message is displayed for each access good or not
ServerIdent                  on       "Welcome To Saturn-V, Please Authenticate!"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
AllowUser rmacdonald
AllowUser awilson
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/Aaron/>
AllowOverwrite On
	<Limit ALL>
		Order Allow,Deny
		AllowUser awilson
		AllowUser userftp
		Deny ALL
	</Limit>
</Directory>

<Directory /home/FTP-shared/Ryan/>
AllowOverwrite On
	<Limit ALL>
		Order Allow,Deny
		AllowUser rmacdonald
		AllowUser userftp
		Deny ALL
	</Limit>
</Directory>

<Directory /home/FTP-shared/Jawsykilla/>
AllowOverwrite On
	<Limit ALL>
		Order Allow,Deny
		AllowUser userftp
		Deny ALL
	</Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/upload/>
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

### Post by jawsykilla on 2010-01-27
Anyone?

---

### Post by Xianath on 2010-01-27
Looks like a client issue. You are either using passive mode or the PORT/EPRT command, you can't be using both for the same data connection -- see RFC 959. Since you're using PORT, you're not using passive mode. Try ftp -p <user@host>, or else in the ftp client shell, type the "passive" command. This should switch to passive mode and it should work, assuming your server and firewall(s) are configured correctly.

Regards,
Peter

---

### Post by jawsykilla on 2010-01-27
When i try passive mode it just hangs after i enable passive mode. If i use ftp -p when i use a PORT command it just hangs forever. Everything works fine when i am accessing the server from inside my LAN.

---

