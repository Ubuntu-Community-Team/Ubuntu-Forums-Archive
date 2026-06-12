---
title: "Want to set a simple FTP server with user account,  need help with proftpd.conf"
date: 2005-06-10
forum: Server Platforms
---

### Post by frodon on 2005-06-10
First, my goal is to set simple Ftp server sharing few files with friends, it will not running all the time.
For that i want connections using user account and password.

In the fisrt time I install proftpd and read a lot of doc, configure proftpd.conf file but it still not work. But i really want to do it.

Did someone can show me his proftpd.conf file using users account, locking user in his home directory and allowing only read and download.

However, vsftpd is perhaps better for my use, lot of people say that it is mor secure and fast than proftpd. But I don't know for the moment how it work, is it like configuring proftpd ?

Thanks a lot for showing me config files or just helping me.

If someone have this knowledge, it would be interresting to write an HOW TO because many of us want to have a simple ftp server with users account and never do it by lack of information or knowledge.

---

### Post by LordHunter317 on 2005-06-10
You know, it's eaiser to tell you what's wrong with your configuration if you post your configuration.

Asking for other people's is not always a good idea.  Unless your hang up is small, learning configuration by example is a PITA, and you may not figure it out.    If you post your configuration, someone more knowledgeable can tell you what's wrong.

---

### Post by frodon on 2005-06-10
this is my proftpd.conf file :


ServerName			"Frodon's server "
ServerType			standalone
DeferWelcome			on

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutNoTransfer 		20
TimeoutStalled 			10
TimeoutLogin 			20
TimeoutIdle 			1200

RootLogin 			off

ExtendedLog 			/var/log/ftp.log auth,all


#DenyFilter			\*.*/

UseFtpUsers off

AllowStoreRestart		on

# Port 21 is the standard FTP port.
Port				21

MaxInstances			3

# Set the user and group that the server normally runs at.
User                  ftpin
Group                 ftpin

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022

PersistentPasswd		off

MaxClients 3

MaxClientsPerHost 1

AccessGrantMsg "Connexion reussie pour %u - Bienvenue !"

ServerIdent                  on       "hello"

DefaultRoot /ftproot

DefaultRoot ~

MaxLoginAttempts    5

UserAlias	ftpin		sauron

<Directory />
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory ~/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> ~/upload>
Umask 022 022
AllowOverwrite on
	<Limit MKD XMKD RNRF RNTO DELE RMD XRMD STOR>
	AllowAll
	</Limit>
</Directory>

---

### Post by LordHunter317 on 2005-06-11
The reason it isn't working is your ServerName is invalid.  This isn't an arbitrary parameter.  It must be a valid, resolvable hostname for your server.

Also, why aren't you using nobody/nogroup for the proftpd account?

---

### Post by Beernut on 2005-06-12
Here is how I got ProFTPD to work.  I am not sure about the permissions you need maybe somebody can help you out with that.  If your server is running behind a router using NAT you have to set a Masquerade Address.  Use a service like DynDNS.org for your server name.

[Ubuntu HowTo:  ProFTPD behind NAT](http://tsb.blogdns.org/?p=27)

---

### Post by frodon on 2005-06-13
[QUOTE=LordHunter317]The reason it isn't working is your ServerName is invalid.  This isn't an arbitrary parameter.  It must be a valid, resolvable hostname for your server.

Also, why aren't you using nobody/nogroup for the proftpd account?[/QUOTE]


ok

I'm not using nobody/nogroup for the proftpd account because i don't want to allow anonimous access, but maybe it's possible to have only user access using nobody/nogroup for the proftpd account, but I'm not sure about that. Can you enlighten me with that ?

I change the server name but users can't access my FTP server and I really don't know why, any ideas ?

---

### Post by frodon on 2005-06-18
:razz: I find the solution !

I modify a little bit my proftpd.conf file :

I use now nobody/nogroup for the proftpd account, and I add some lines in order to restrict user access :            

#VALID LOGINS
<Limit LOGIN>
AllowUser ftpin
DenyALL
</Limit>

I also remove useralias and modify the path of my directories

First time I created users account like that : [http://www.frankandjacq.com/ubuntuguide/5.04/index.html](http://www.frankandjacq.com/ubuntuguide/5.04/index.html) but my password was never recognized and I don't know why. So, I create user account in a terminal : useradd -p password -d /home/name name  and now the password is well recognized.
note :  A wrong path of directory will produce the same result

In conclusion my problem was more to create a good user account with a well recognized password and verify the good path of directories than configure proftpd itself. 

also the command "proftpd -td5" is really usefull to check the good syntax of the proftpd.conf file

Thanks for your help, I'm happy to have my FTP server working  :razz:

---

