---
title: "FTP server"
date: 2013-01-18
forum: Server Platforms
---

### Post by Soldier9221 on 2013-01-18
Hello Ubuntu forums,

This is my first post here, so I apologize if it is in the wrong category. I'm also quite new to server hosting, but I have some experience with Ubuntu and other linux distros.

So I am trying to set up an FTP server. I have tried vsFTPD and ProFTPD. I have done the following:

- Tried using different ports, 21, 2121, 2101 etc etc.

- Using an IP in the Marque option in the ProFTPD config.

- Tried various things in the vsFTPD config (Can't remember exactly what I did)

And finally, it seems I did manage to get one thing to work (to an extent): DMZ. I set the DMZ host to a virtual machine that I had ProFTPD running on, and I was able to login, but not browse to any directories. Here is a snippit of what happens when I try to connect without DMZ on:
```
Status:	Resolving address of arsonicsoldier.no-ip.org
Status:	Connecting to 68.96.99.113:21...
Status:	Connection established, waiting for welcome message...
Response:	220 ProFTPD 1.3.4a Server (Virtual Gaming) [68.96.99.113]
Command:	USER axe122
Response:	331 Password required for axe122
Command:	PASS *************
Response:	230 User axe122 logged in
Command:	OPTS UTF8 ON
Response:	200 UTF8 set to on
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is the current directory
Command:	TYPE I
Response:	200 Type set to I
Command:	PASV
Response:	227 Entering Passive Mode (68,96,99,113,210,170).
Command:	LIST
Error:	Connection timed out
Error:	Failed to retrieve directory listing
```

I'd also like to note that I get the same response from both FTP server programs.

Like I said, I'm new to this whole hosting thing, but I can figure out everything else. I've some servers set up for people, as well as SSH access. Sadly, too many people do not know how to use SSH, so I need for FTP to be working.

Thank you so much,
~Soldier9221

---

### Post by darkod on 2013-01-18
Don't forget that linux is very strict with permissions. For example, if you have a user misterx and the FTP home directory is /data/misterx, the user has to have permissions to read/write that folder so that it can use it.

Otherwise, with the correct username and password the FTP will accept the connection, but the OS will decline access to a folder where that username has no permissions.

Do you have the permissions set OK?

---

### Post by Soldier9221 on 2013-01-18
Yes, I have tried both just owner access, and 777. 

I also forgot to mention in the original post, here is my proftpd.conf:
```

#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes, reload proftpd after modWifications, if
# it runs in daemon mode. It is not required in inetd/xinetd mode.
#
 
# Includes DSO modules
Include /etc/proftpd/modules.conf
 
# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                         off
# If set on you can experience a longer connection delay in many cases.
IdentLookups                    off
 
ServerName                      "Virtual Gaming"
ServerType                      standalone
DeferWelcome                    off
 
MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    on
 
TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200
 
DisplayLogin                    welcome.msg
DisplayChdir                    .message true
ListOptions                     "-l"
 
DenyFilter                      \*.*/
 
# Use this to jail all users in their homes
DefaultRoot                     ~
 
# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell             off
 
# Port 21 is the standard FTP port.
Port                            21
 
# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534
 
# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
MasqueradeAddress               arsonicsoldier.no-ip.org
 
# This is useful for masquerading address with dynamic IPs:
# refresh any configured MasqueradeAddress directives every 8 hours
<IfModule mod_dynmasq.c>
# DynMasqRefresh 28800
</IfModule>
 
# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30
 
# Set the user and group that the server normally runs at.
User                            axe122
Group                           sudo
 
# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on
 
# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd              off
 
# This is required to use both PAM-based authentication and local passwords
# AuthOrder                     mod_auth_pam.c* mod_auth_unix.c
 
# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile                   off
 
TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log
 
# Logging onto /var/log/lastlog is enabled but set to off by default
#UseLastlog on
 
# In order to keep log file dates consistent after chroot, use timezone info
# from /etc/localtime.  If this is not set, and proftpd is configured to
# chroot (e.g. DefaultRoot or <Anonymous>), it will use the non-daylight
# savings timezone regardless of whether DST is in effect.
#SetEnv TZ :/etc/localtime
 
<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>
 
<IfModule mod_ratio.c>
Ratios off
</IfModule>
 
<ifModule mod_facts.c>
FactsAdvertise off
</ifModule>
 
 
# Delay engine reduces impact of the so-called Timing Attack described in
# http://www.securityfocus.com/bid/11430/discuss
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
 
#
# Alternative authentication frameworks
#
#Include /etc/proftpd/ldap.conf
#Include /etc/proftpd/sql.conf
 
#
# This is used for FTPS connections
#
#Include /etc/proftpd/tls.conf
 
#
# Useful to keep VirtualHost/VirtualRoot directives separated
#
#Include /etc/proftpd/virtuals.conf
 
# A basic anonymous configuration, no upload directories.
 
# <Anonymous ~ftp>
#   User                                ftp
#   Group                               nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias                   anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser on ftp
#   DirFakeGroup on ftp
#
#   RequireValidShell           off
#
#   # Limit the maximum number of anonymous logins
#   MaxClients                  10
#
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin                        welcome.msg
#   DisplayChdir                .message
#
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
#
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask                           022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
#
# </Anonymous>
 
# Include other custom configuration files
Include /etc/proftpd/conf.d/
<Limit LOGIN>
AllowUser axe122, soldier9221
DenyALL
</Limit>

```

---

### Post by sandyd on 2013-01-19
> **Soldier9221 said:**
> Hello Ubuntu forums,

This is my first post here, so I apologize if it is in the wrong category. I'm also quite new to server hosting, but I have some experience with Ubuntu and other linux distros.

So I am trying to set up an FTP server. I have tried vsFTPD and ProFTPD. I have done the following:

- Tried using different ports, 21, 2121, 2101 etc etc.

- Using an IP in the Marque option in the ProFTPD config.

- Tried various things in the vsFTPD config (Can't remember exactly what I did)

And finally, it seems I did manage to get one thing to work (to an extent): DMZ. **I set the DMZ host to a virtual machine that I had ProFTPD running on, and I was able to login, but not browse to any directories. Here is a snippit of what happens when I try to connect without DMZ on:**
```
Status:	Resolving address of arsonicsoldier.no-ip.org
Status:	Connecting to 68.96.99.113:21...
Status:	Connection established, waiting for welcome message...
Response:	220 ProFTPD 1.3.4a Server (Virtual Gaming) [68.96.99.113]
Command:	USER axe122
Response:	331 Password required for axe122
Command:	PASS *************
Response:	230 User axe122 logged in
Command:	OPTS UTF8 ON
Response:	200 UTF8 set to on
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is the current directory
Command:	TYPE I
Response:	200 Type set to I
Command:	PASV
Response:	227 Entering Passive Mode (68,96,99,113,210,170).
Command:	LIST
Error:	Connection timed out
Error:	Failed to retrieve directory listing
```

I'd also like to note that I get the same response from both FTP server programs.

Like I said, I'm new to this whole hosting thing, but I can figure out everything else. I've some servers set up for people, as well as SSH access. Sadly, too many people do not know how to use SSH, so I need for FTP to be working.

Thank you so much,
~Soldier9221
1. Is DMZ enabled or disabled?
You will need to forward the Passive FTP ports as well if you are using port forwarding. The ports are 49152-65534.

2. 
```

User                            axe122
Group                           sudo

```
is not correct - the FTP server should not be run as a sudo user.

I am not familiar with this ftp server, so I will offer something else instead...

Use PureFTPD instead - with puredb

```

sudo apt-get install pure-ftpd
cd /etc/pure-ftpd
nano conf/PAMAuthentication
#Replace 'yes' with 'no' and save
sudo ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/10puredb

```
Lets create some users
```

sudo pure-pw useradd <login name> -u <user uid> -g <group uid> -d <user home directory>
```
replace <login name> with the login name of the user, <user uid> with the user's UID, and <group uid> with the user's gid (which is not sudo's uid), and <user home directory> with the folder you want the user to be confined to. If you don't want them to be confined, replace -d with -D, but that is not reccomended. Each person must have their own account on the server, and they have to own the directory they are confined to. For example, if you want a root user, (not reccomended, and is disabled by default), you would have to use the uid of 0 and the gid of 0. You can find out the uid/gid by using the 'id' command.

so after you add all the users, run
```

sudo pure-pw mkdb
```
Restart pure-ftpd, and you should be all set.

---

### Post by Soldier9221 on 2013-01-19
/etc/pure-ftpd/auth/10puredb isn't a valid file/directory... What should I do? I'm really sorry, but you've been a great help so far.

---

### Post by thnewguy on 2013-01-19
I have a couple of suggestions:

1. If the LIST command is timing out that probably means the port is blocked. You connect to the FTP server on port 21, but the LIST data is sent over a different port. You will have to make sure all possible network ports on the host can be reached by the client. Or at least all the ports within the range your FTP service is allowed to access. It might be easiest, just for testing purposes, to make sure the firewall on the host computer is turned off and the host computer is in your DMZ.

2. Consider running a more simple FTP service. The ones you are using have a lot of features, but are more complex to set up. Something like Bftpd (bftpd.sf.net) will let you just install and go without adjusting the configuration.

---

### Post by sandyd on 2013-01-19
> **Soldier9221 said:**
> /etc/pure-ftpd/auth/10puredb isn't a valid file/directory... What should I do? I'm really sorry, but you've been a great help so far.

made typo
fixed

If it still doesn't work, what is the output of
```

ls /etc/pure-ftpd
ls /etc/pure-ftpd/auth
```

---

### Post by Soldier9221 on 2013-01-19
Sandyd, I'm having another issue. Thank you for being so kind as to keep helping me though.

Whenever I run the command: pure-pw useradd 1axe122 -u 1000 -g 1000 -d /home/axe122/

I get: Check that [1axe122] doesn't already exist,
and that [/etc/pure-ftpd/pureftpd.passwd.tmp] can be written.

However, I do not have a file by that name, in that directory. Do I have a bugged installation? Should I reinstall, or did I just miss a step?
Thanks.

---

### Post by Soldier9221 on 2013-01-21
Bumping, I'd really appreciate some more help.

Sorry if bumping is not allowed here.

---

### Post by sandyd on 2013-01-21
> **Soldier9221 said:**
> Sandyd, I'm having another issue. Thank you for being so kind as to keep helping me though.

Whenever I run the command: pure-pw useradd 1axe122 -u 1000 -g 1000 -d /home/axe122/

I get: Check that [1axe122] doesn't already exist,
and that [/etc/pure-ftpd/pureftpd.passwd.tmp] can be written.

However, I do not have a file by that name, in that directory. Do I have a bugged installation? Should I reinstall, or did I just miss a step?
Thanks.

sorry about the wait - a bit distracted by a stray DDOS attack hitting several of my servers...


Anyways, just add 'sudo' in front of pure-pw

Ive fixed it in the earlier post as well.

Oh, and make sure you uninstall the other FTP server as well.

---

### Post by Soldier9221 on 2013-01-21
Wow! Thank you! What a great community this is! However, I have another problem, and I'm very sorry to be such a bother. But, whenever I try to login using Filezilla, I get this:
```

Response:	220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Response:	220-You are user number 3 of 50 allowed.
Response:	220-Local time is now 19:36. Server port: 21.
Response:	220-This is a private system - No anonymous login
Response:	220-IPv6 connections are also welcome on this server.
Response:	220 You will be disconnected after 15 minutes of inactivity.
Command:	USER axe
Response:	331 User axe OK. Password required
Command:	PASS ********
Response:	530 Login authentication failed
Error:	Critical error
Error:	Could not connect to server

```

I've ensured that I'm using the correct credentials, I've even made more users to confirm. Did I do something wrong?

---

### Post by sandyd on 2013-01-22
> **Soldier9221 said:**
> Wow! Thank you! What a great community this is! However, I have another problem, and I'm very sorry to be such a bother. But, whenever I try to login using Filezilla, I get this:
```

Response:	220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Response:	220-You are user number 3 of 50 allowed.
Response:	220-Local time is now 19:36. Server port: 21.
Response:	220-This is a private system - No anonymous login
Response:	220-IPv6 connections are also welcome on this server.
Response:	220 You will be disconnected after 15 minutes of inactivity.
Command:	USER axe
Response:	331 User axe OK. Password required
Command:	PASS ********
Response:	530 Login authentication failed
Error:	Critical error
Error:	Could not connect to server

```

I've ensured that I'm using the correct credentials, I've even made more users to confirm. Did I do something wrong?
did you run
```

sudo pure-pw mkdb
```
after adding the user?

Also, the password for the FTP is the password it asked you for when you ran pure-pw to create the user.

---

### Post by Soldier9221 on 2013-01-22
I added yet another user, with a different home directory, and now I get this when trying to connect via Filezilla:
```

Response:	220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Response:	220-You are user number 2 of 50 allowed.
Response:	220-Local time is now 15:07. Server port: 21.
Response:	220-This is a private system - No anonymous login
Response:	220-IPv6 connections are also welcome on this server.
Response:	220 You will be disconnected after 15 minutes of inactivity.
Command:	USER soldier9221
Response:	331 User soldier9221 OK. Password required
Command:	PASS *************
Response:	230 OK. Current directory is /
Command:	OPTS UTF8 ON
Response:	200 OK, UTF-8 enabled
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is your current location
Command:	TYPE I
Response:	200 TYPE is now 8-bit binary
Command:	PASV
Response:	227 Entering Passive Mode (192,168,0,24,147,3)
Status:	Server sent passive reply with unroutable address. Using server address instead.
Command:	MLSD
Error:	Connection timed out
Error:	Failed to retrieve directory listing

```

---

### Post by sandyd on 2013-01-22
Using nat router...
```

sudo nano /etc/pure-ftpd/conf/ForcePassiveIP

```
Enter in
```

arsonicsoldier.no-ip.org
```
save and restart FTP.

That slows down FTP a *bit*, because it has to do DNS lookups, but I assume you have a dynamic ip address with ddclient or something enabled. In that case, this is the only fix

---

### Post by Soldier9221 on 2013-01-22
```

Response:	220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Response:	220-You are user number 1 of 50 allowed.
Response:	220-Local time is now 17:12. Server port: 21.
Response:	220-This is a private system - No anonymous login
Response:	220-IPv6 connections are also welcome on this server.
Response:	220 You will be disconnected after 15 minutes of inactivity.
Command:	USER soldier9221
Response:	331 User soldier9221 OK. Password required
Command:	PASS *************
Response:	230 OK. Current directory is /
Command:	OPTS UTF8 ON
Response:	200 OK, UTF-8 enabled
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is your current location
Command:	TYPE I
Response:	200 TYPE is now 8-bit binary
Command:	PASV
Response:	227 Entering Passive Mode (68,96,99,113,210,242)
Command:	MLSD
Error:	Connection timed out
Error:	Failed to retrieve directory listing

```

Still getting an error :s. I do apologize. If you're getting fed up, I understand.

---

### Post by sandyd on 2013-01-22
> **Soldier9221 said:**
> ```

Response:	220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Response:	220-You are user number 1 of 50 allowed.
Response:	220-Local time is now 17:12. Server port: 21.
Response:	220-This is a private system - No anonymous login
Response:	220-IPv6 connections are also welcome on this server.
Response:	220 You will be disconnected after 15 minutes of inactivity.
Command:	USER soldier9221
Response:	331 User soldier9221 OK. Password required
Command:	PASS *************
Response:	230 OK. Current directory is /
Command:	OPTS UTF8 ON
Response:	200 OK, UTF-8 enabled
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is your current location
Command:	TYPE I
Response:	200 TYPE is now 8-bit binary
Command:	PASV
Response:	227 Entering Passive Mode (68,96,99,113,210,242)
Command:	MLSD
Error:	Connection timed out
Error:	Failed to retrieve directory listing

```

Still getting an error :s. I do apologize. If you're getting fed up, I understand.

Not yet ;)

Are you sure there are _no_ firewalls blocking the passive FTP ports? Is your ISP blocking them?

---

### Post by Soldier9221 on 2013-01-22
Port 21 is open, which tells me that my ISP most likely isn't blocking it. Secondly, my gateway doesn't have any firewalls, nor dos the machine that FTP is running off of. I'll try another port, though.


EDIT:

I've followed the instructions located here: [https://help.ubuntu.com/community/PureFTP](https://help.ubuntu.com/community/PureFTP)

And this is now my result:
```
Response:	220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Response:	220-You are user number 1 of 50 allowed.
Response:	220-Local time is now 20:29. Server port: 21.
Response:	220-This is a private system - No anonymous login
Response:	220-IPv6 connections are also welcome on this server.
Response:	220 You will be disconnected after 15 minutes of inactivity.
Command:	USER axe122
Response:	331 User axe122 OK. Password required
Command:	PASS ********
Response:	421 Home directory not available - aborting
Error:	Could not connect to server

```

After using
```
sudo pure-pw show axe122
```
I get this:
```

Login              : axe122
Password           : <deleted for security>
UID                : 1000 (axe122)
GID                : 1000 (axe122)
Directory          : /home/ftpusers/axe122/minecraft/./
Full name          :
Download bandwidth : 0 Kb (unlimited)
Upload   bandwidth : 0 Kb (unlimited)
Max files          : 0 (unlimited)
Max size           : 0 Mb (unlimited)
Ratio              : 0:0 (unlimited:unlimited)
Allowed local  IPs :
Denied  local  IPs :
Allowed client IPs :
Denied  client IPs :
Time restrictions  : 0000-0000 (unlimited)
Max sim sessions   : 0 (unlimited)

```
No matter how many times I try, the home directory is somehow always set to end in /./ I'm not sure why.

---

### Post by sandyd on 2013-01-23
> **Soldier9221 said:**
> Port 21 is open, which tells me that my ISP most likely isn't blocking it. Secondly, my gateway doesn't have any firewalls, nor dos the machine that FTP is running off of. I'll try another port, though.


EDIT:

I've followed the instructions located here: [https://help.ubuntu.com/community/PureFTP](https://help.ubuntu.com/community/PureFTP)

And this is now my result:
```
Response:	220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Response:	220-You are user number 1 of 50 allowed.
Response:	220-Local time is now 20:29. Server port: 21.
Response:	220-This is a private system - No anonymous login
Response:	220-IPv6 connections are also welcome on this server.
Response:	220 You will be disconnected after 15 minutes of inactivity.
Command:	USER axe122
Response:	331 User axe122 OK. Password required
Command:	PASS ********
Response:	421 Home directory not available - aborting
Error:	Could not connect to server

```

After using
```
sudo pure-pw show axe122
```
I get this:
```

Login              : axe122
Password           : <deleted for security>
UID                : 1000 (axe122)
GID                : 1000 (axe122)
Directory          : /home/ftpusers/axe122/minecraft/./
Full name          :
Download bandwidth : 0 Kb (unlimited)
Upload   bandwidth : 0 Kb (unlimited)
Max files          : 0 (unlimited)
Max size           : 0 Mb (unlimited)
Ratio              : 0:0 (unlimited:unlimited)
Allowed local  IPs :
Denied  local  IPs :
Allowed client IPs :
Denied  client IPs :
Time restrictions  : 0000-0000 (unlimited)
Max sim sessions   : 0 (unlimited)

```
No matter how many times I try, the home directory is somehow always set to end in /./ I'm not sure why.

Port 21 is not your passive FTP port. Lemme see if I can find out exactly which ones they are...

---

### Post by Soldier9221 on 2013-01-23
Thank you so much, Sandyd.

---

### Post by sandyd on 2013-01-24
ok, so I don't know the defaults, but thats not a problem :)

Lets set them...
```

sudo nano /etc/pure-ftpd/conf/PassivePortRange
```
Enter in a range of ports, such as
```
30000 35000
```
Note that each user requires a passive FTP port - the above would serve 5000 users :o

---

### Post by JKyleOKC on 2013-01-24
> **Soldier9221 said:**
> ```

Command:	PASV
Response:	227 Entering Passive Mode (68,96,99,113,210,242)

```The last two values in the response list are the bytes of the assigned passive port number, in Motorola's highbyte-lowbyte sequence. The first four bytes are the host IP address which in this case would be 68.96.99.113. After responding to the PASV command, the server goes into a waiting condition expecting the client to send data to that address and port (in this case, if I've converted correctly, port 62,162). You have to configure the client to use passive transfer, and be sure that nothing is blocking that port. Most firewalls have a capability to leave a range open for passive transfers.

---

### Post by Soldier9221 on 2013-01-25
Why am I getting the home directory error though?

---

### Post by JKyleOKC on 2013-01-25
It's saying that the directory is not available, not that it doesn't exist or permission denied, so my best guess is that the owner and group for that directory don't match what the program expects. I use proftp rather than pure, and it's controlled rather differently, so sandyd can be more help than can I with this question...

---

### Post by Soldier9221 on 2013-01-26
Well thank you for your input anyways :)

---

### Post by sandyd on 2013-01-26
assuming your user's username(the one that corresponds to the UID/GID you entered in pure-pw is axe122,

```

#ignore errors of user/group already dxists
sudo groupadd ftpgroup
sudo useradd -g ftpgroup -d /dev/null -s /etc ftpuser
chown ftpuser:ftpgroup /home/ftpusers
sudo chown -R axel122:axel122 /home/ftpusers/axe122/
```

---

### Post by Soldier9221 on 2013-01-27
Still getting:
```

Response:	421 Home directory not available - aborting
Error:	Could not connect to server

```
Sandyd, I cannot thank you enough for your help so far.

---

