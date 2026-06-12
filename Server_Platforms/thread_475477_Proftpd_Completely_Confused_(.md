---
title: "Proftpd: Completely Confused :("
date: 2007-06-16
forum: Server Platforms
---

### Post by Gruelius on 2007-06-16
Hey guys n gals,
Before i talk i will say ive read all the guides that i could find and i am quite unsure on how proftpd and its configuration file works. Instead of saying what ive tried ill just post what i want to do and then we might work something out ;)

I want to be able to give one passworded ftp user read/write access to /var/www/

I want to give another passworded ftp user browse only acces to /mnt/raid5/tv\ shows/.

I understand that i need the users in /etc/passwd however i have no idea about PAM or the actual config file itself :(

Anyway i hope i dont look like too much of an idiot when you guys solve this lol

Julius

---

### Post by OoooMatron on 2007-06-16
an easy way would be to create user accounts using "adduser" and then change their home directory with the "usermod" command and write the appropriate paths. you could then assign the users into groups and restrict access as necessary.

There are guides on the net for setting up mysql with proftpd so you can store logins and paths in a database instead of creating user accounts.

---

### Post by NumberOne on 2007-06-16
If you are not comfortable with the cmd line, Gproftpd if very good.  I use it and it is a snap to do what you are trying to do (Groftpd is a GUI for Proftpd).  Its in the repos.

---

### Post by Gruelius on 2007-06-16
> **OoooMatron said:**
> an easy way would be to create user accounts using "adduser" and then change their home directory with the "usermod" command and write the appropriate paths. you could then assign the users into groups and restrict access as necessary.

There are guides on the net for setting up mysql with proftpd so you can store logins and paths in a database instead of creating user accounts.

I figured it out after a while it was because i was doing useradd not adduser :p Ive tweaked my settings so they are secure but if i did need more users id probably use mysql.

---

### Post by Gruelius on 2007-06-17
Ok well i have gotten it working. There are two users, oxyrich and video.

oxyrich has its home directory as /var/www/ and has full read/write permissions and video has its home directory as /mnt/video/ and cannot read or write. This is my config

```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				off
AccessGrantMsg			"Harrow %u"
ServerName			"The treasure cove"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200
UseReverseDNS        off

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"
#<Directory ~>
#RateReadBPS	              10240
#RateWriteBPS			51200
#</Directory>
DenyFilter			\*.*/

# Use this to jail all users in their homes 
DefaultRoot			~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShells		off

# Port 21 is the standard FTP port.
Port				21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress		1.2.3.4

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				proftpd
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				775  775
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd		off

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile			off

# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend 
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
#<IfModule mod_sql.c>
# SQLBackend			mysql
#</IfModule>

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_tls.c>
TLSEngine off
</IfModule>

#Stop **** happening with tvshow
<Limit STOR RNFR DELE>
Denyuser tvshow
</Limit>


<IfModule mod_quota.c>
QuotaEngine on
</IfModule>

<IfModule mod_ratio.c>
Ratios on
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        on
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine on
</IfModule>

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
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
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

```

I want to be able to restrict the speed i upload at to 10kb/s and restrict the speed i download at to 50kb/s (server side). When i added
```
#<Directory ~>
#RateReadBPS	              10240
#RateWriteBPS			51200
#</Directory>
```
proftpd spat the dummy and crashed.

Also is the way i have it setup any good? and can someone explain to me what <anonymous> tags are and what <directory> tags are. Do they each create the directory for the users or do they just apply to that directory?

Thanks
Julius

---

### Post by Andrew Doades on 2007-06-24
try vsftpd!

---

### Post by nix4me on 2007-06-24
Proftpd is much better than vsftpd.  You have done a great job in your configuration.  Have a look at the following thread to learn more about proftpd setup:


[http://ubuntuforums.org/showthread.php?t=79588&highlight=proftpd](http://ubuntuforums.org/showthread.php?t=79588&highlight=proftpd)

nix4me

---

### Post by green-12 on 2007-06-26
I have created a user to proftp like the following

sudo useradd userftp -p your_password -d /home/FTP-shared -s /bin/false

Next I had to set the password again like this:

sudo passwd userftp
(then i entered the password twice)

After theses steps I was able to gain access but I can see all the files of my system(including all the root directories) and I was wondering if there is a way to only see the ftp folder and not be able to navigate around with certain users?

---

### Post by Wardazo on 2007-06-26
This should help:

[http://www.proftpd.org/docs/directives/linked/config_ref_DefaultRoot.html](http://www.proftpd.org/docs/directives/linked/config_ref_DefaultRoot.html)

---

