---
title: "proftpd config for a web server"
date: 2009-04-02
forum: Server Platforms
---

### Post by skidz on 2009-04-02
Hi all...

proftpd.. I can't figure out... 

I am just trying to set up a user to login for ftp to goto /var/www directory. Sounds simple enough... but I am having all kinds of issues. 

ok, so I have created a user skidzftp2, and I have my default login of skidz.

Issue one: skidzftp2 can never login, always tells me login is incorrect, and I have tried changing the password.

Issue two: skidz can log in, but, he does not go to the /var/www directory. Instead its a directory with .bash_history as the first file.

Any advice would be helpful, I am new to linux, and admit I have done great up until now.

Here is my config:
```

ServerName	SkidzFPT1
ServerIdent	on
ServerAdmin	ftpadmin@localhost
ServerType	standalone
Port	21
DefaultServer	on
IdentLookups	off
UseReverseDNS	off
User	nobody
Group	nogroup
Umask	022
#DefaultRoot	~
ListOptions	"-a"
AllowOverwrite	on
MaxClients	9 
MaxClientsPerHost	3 
MaxInstances	30
MaxLoginAttempts	3
TimeoutIdle	320
TimeoutNoTransfer	320
TimeoutStalled	320
TimesGMT	off
TransferLog	/var/log/xferlog

DefaultRoot	/var/www

<Limit LOGIN>
	AllowUser skidz
	Allowuser skidzftp2
	DenyALL
</Limit>

<Global>
	AllowForeignAddress	on
	AllowOverwrite	on
	AllowRetrieveRestart	on
	PassivePorts	59000 60050
	RequireValidShell	on
	RootLogin	off
	ShowSymlinks	off
</Global>

<VirtualHost 192.168.1.160>
  ServerAdmin	admin@localhost.com
  ServerName	localhost server
  TransferLog	/var/spool/syslog/xfer/localhost
  MaxLoginAttempts	5
  DefaultRoot	/var/www
  User	skidz
  Group	nogroup
  AllowOverwrite	on
</VirtualHost>


```

---

### Post by skidz on 2009-04-02
NM, I got it... 

in my config, I had:
Allowuser skidzftp2

and it should have been:
AllowUser skidzftp2

:) Thanks anyways...

---

