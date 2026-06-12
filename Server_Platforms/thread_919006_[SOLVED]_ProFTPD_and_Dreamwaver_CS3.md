---
title: "[SOLVED] ProFTPD and Dreamwaver CS3"
date: 2008-09-13
forum: Server Platforms
---

### Post by Keymaster on 2008-09-13
Even after following the instructions of other threads I am unable to get dreamweaver to save files to my FTP server.  Everything else works just fine though.  Even regular FTP from the same machine to the server.  Here is the ProFTPD config:

```

# This is a basic ProFTPD configuration file (rename it to 
# 'proftpd.conf' for actual use.  It establishes a single server
# and a single anonymous login.  It assumes that you have a user/group
# "nobody" and "ftp" for normal operation and anon.

ServerName			"FTP Server"
ServerType			standalone
DefaultServer			on

# Port 21 is the standard FTP port.
Port				21
# Umask 022 is a good standard umask to prevent new dirs and files
# from being group and world writable.
Umask				022

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				anonymous
#Group				nogroup
#<Anonymous /opt/ftpanony/>
#AnonRequirePassword off
#User anonymous
#Group anonymous
#RequireValidShell off
#<Directory /opt/ftpanony/*>
#<Limit WRITE>
#DenyAll
#</Limit>
#</Directory>
#</Anonymous>

# Normally, we want files to be overwriteable.
<Directory /opt/ftpanony/*>
#  AllowOverwrite		on
</Directory>

# only for the web servers content
DefaultRoot ~ !website
DefaultRoot /opt/www website

# nobody gets the password "lampp"
# commented out by lampp security
#UserPassword nobody wRPBu8u4YP0CY
#UserPassword nobody lF/bBdY9ikuzY

#Deny FTP Access to users in the group deniedftp
<Limit LOGIN>
AllowUser website
DenyALL
#DenyGroup deniedftp
</Limit>

# nobody is no normal user so we have to allow users with no real shell
RequireValidShell off

# nobody may be in /etc/ftpusers so we also have to ignore this file
#UseFtpUsers on
<Global>
RootLogin off
</Global>
RootLogin off

```

I use the user "website: to login, and it is the only user allowed to access the server.  I do not have anonymous users.  The ProFTPD server is provides by ApacheFriends Xampp For Linux.  I do not have the time to redo everything using regular installs at this time.  The directory is owned by website:website, and the file permissions are 755.  Many thanks to whoever helps me.

---

### Post by cariboo on 2008-09-13
You have two defaultroot directives:

> # only for the web servers content
DefaultRoot ~ !website
DefaultRoot /opt/www website


Neither of them are going to work the way they are. The first one makes no sense the is no such thing as ~ !website the second one should be something like this:

```
DefaultRoot /opt/www/website
```

So the directive should look something like this:

```
# only for the web servers content
#DefaultRoot ~ !website
DefaultRoot /opt/www/website
```

where website is the directory that the website files are in.

Jim

---

### Post by Keymaster on 2008-09-13
The way I understand it is !website means except for user website.  I will try it with one default root directory.  It's odd though, the current setup permits me to login viademweaver and view/download files, but not change/upload files.  It also lets me login via Windows Explorer or any normal FTP Client (ie: SmartFTP) and do everything I want correctly.  Any idea as to why?

---

### Post by Vegan on 2008-09-14
I found installing

sudo apt-get install sftp

allowed me to to use WinSCP to move files back and forth easily from Windows and my beheaded Linux server.

---

