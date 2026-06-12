---
title: "ProFTPd - wanting to make it as secure as possible"
date: 2006-10-17
forum: Server Platforms
---

### Post by feenster on 2006-10-17
Hi all,
I have a Ubuntu 6.06 LTS server that I am trying to setup ProFTPd on. I have a bunch of users setup (in the Ubuntu Users control panel) that transfer data across via SSH every night. I want these users to be able to access their data via FTP if necessary. 

To make sure their backed-up data does not get overwritten, I want to only allow them read access to their home directory and subfolders - they should not be able to upload, overwrite, delete or mangle any of their data, just download it. I also want to ban anonymous access of any kind, and if possible, deny root from logging in too. 

Could you have a look at my config file and just see if it is covering those things, and whether it could be improved to make it as secure as possible for my needs?

```

#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

ServerName			"FTP"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

DenyFilter			\*.*/

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd		off

# Uncomment this if you would use TLS module:
#TLSEngine 			on

# Uncomment this if you would use quota module:
#Quotas				on

# Uncomment this if you would use ratio module:
#Ratios				on

# Port 21 is the standard FTP port.
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				002
# Normally, we want files to be overwriteable.
AllowOverwrite			no

# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
#DelayEngine 			off

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



# Do not allow any uploading of files
<Limit WRITE>
	DenyAll
</Limit>

# Pretend hidden files (e.g. .ssh/) do not exist, and do not show them
<Limit DIRS LOGIN READ>
	AllowAll
	IgnoreHidden on
</Limit>

# Lock users into their home directory, so they cannot snoop into other users data
DefaultRoot ~

#IdentLookups off

# Decided what message to show when a user connects to the FTP server
ServerIdent on "FTP Server Ready"



# Disconnect client if idle for 2 minutes
#TimeoutIdle 120

# Disconnect client if not logged in successfully for 2 minutes
#TimeoutLogin 120

# Disconnect if client idle for 2 minutes without transfer
#TimeoutNoTransfer 120

# Set max number of connections per host and user
MaxClientsPerHost 5
MaxClientsPerUser 5

# Set max number of login attempts
MaxLoginAttempts 2

# Allow clients to continue broken downloads
AllowRetrieveRestart on
AllowStoreRestart on

# Set logging to file
ServerLog /var/log/proftpd.log

# Set transfer logging to file
TransferLog /var/log/proftpd_transfer.log

# Set Passive Ports range - to allow login from internet behind firewall
PassivePorts 49152 65534

```

Many thanks from a relatively newbie,
  Matt

---

### Post by gsdefender on 2006-10-17
Don't really know if this really helps you, but I suggest switching to vsftpd if possible. I've always sensed it as more secure.

---

### Post by feenster on 2006-10-17
Hi,
Thanks for the reply. I have actually tried it with **vsftpd** - it worked fine, but it seems that **proftpd** has a bit more flexibilty. Plus it has a GUI for less experienced users.

**proftpd** seems to be working fine - I just want to make sure there are no obvious security holes in my configuration.

Matt

---

### Post by nixios on 2006-10-17
If you want it to more secure, Allow only the IP
Addresses within your network.

---

### Post by feenster on 2006-10-17
> **nixios said:**
> If you want it to more secure, Allow only the IP
Addresses within your network.

Unfortunately, that is not possible, as the data is being transferred and downloaded from external sources.

What I am really after is making sure that there are no loopholes in my config that would allow a user to either view another users files, or overwrite/delete their own. My own testing seems to point to this being setup correctly, but i'm not all that familiar with **ProFTPd **at this point.

Matt

---

### Post by sonic2000gr on 2006-10-17
Your setup looks ok.
The two most critical things for security are:

DefaultRoot ~

to chroot a user into his own directory

and also to comment out the anonymous user so FTP only works with valid users.

I've been using proftpd for several months now, and I think it is secure and stable.

---

### Post by feenster on 2006-10-17
> **sonic2000gr said:**
> Your setup looks ok.
The two most critical things for security are:

DefaultRoot ~

to chroot a user into his own directory

and also to comment out the anonymous user so FTP only works with valid users.

I've been using proftpd for several months now, and I think it is secure and stable.

Hi,
Thanks for that - that was exactly what I needed to know :)

Matt

---

