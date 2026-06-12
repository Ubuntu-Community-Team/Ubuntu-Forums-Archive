---
title: "Looking for FTP server software"
date: 2007-12-07
forum: Server Platforms
---

### Post by couzin2000 on 2007-12-07
I wanted to find out from everybody what your experience is in regards to finding, downloading, installing, setting up and turning on an FTP server software on Ubuntu.
I currently have Gutsy, but I can't really find much as far as an appreciation of FTP software.
Way back when I was using Windows (XP), I was using Bulletproof FTP and FileZilla FTP servers (not together). Both worked great for my limited needs.

What's your take on this -- what should I get? Any thread I should refer to?

Thanks

---

### Post by mouseboyx on 2007-12-07
proftpd is the easiest when combined with gproftpd both available in the repositories, but i still can't figure out how to make users and passwords for it from the cli

---

### Post by couzin2000 on 2007-12-08
And here I thought I was getting something easy.
Well, thanks, I downloaded proftpd and gproftpd, both are installed, now I have a S***load of problems to solve. 

[LIST=1]
[*]First, I've put together the config from gproftpd. However, I'm using a free dynamic dns locator (from [http://dyndns.org/]("http://dyndns.org/")) and now I have to configure the dyndns deamon running, because otherwise I will never know my IP.
So before I actually get to the dyndns config, I've put in the domain name.
[*]I own a DLink router with running firewall, so I'm using NAT as well. When I was using Windows I never had to enter the outside-world addy, but this asks me to. Do I really have to? I thought the router would do that job?
[*]Most of the config is ok and easy to do, except for maybe the directories, which I was reading in the Help file that they all need to be below the root ftp folder? So let's say I'm setting this up for myself, I need complete access to my pc, do I have to use a mount command, or can't I just specify "/" as my "default home directory"? (note: I understand the security implications, but this is just for the example -- I'm not really gonna do that)
[*]**USERS.** Ahh, now we get to it. I can't seem to "Add" a user to the list, even though when I use the import function in the Servers tab, I can see both the users I just created. Plus, there should be a scrollable list at the top of the Users tab, but this list is jammed solid and doesn't display *jack*. So how do I fix this? It almost seems as though the system is trying to look up users in a folder which is not described in the program. Help me with this!!
[*]Plus, when I DO manage to fill in the entire user config for 1 user, including the folder permissions, I hit either "apply" buttons and I get an error message. If I hit "Add", then it works - but the user automatically disappears and I can't see him in the list.
[/LIST]

This is *MUCH* more complicated than you said, mouseboyx.

---

### Post by freebeer on 2007-12-09
Verdun, eh?  I used to live there many moons ago.  :D

Ok, let's tackle some of your issues.  I'm using proftp and gproftp as well as with a dynamic ip service (DynDNS). So our set-ups are going to be similar.

With regards to the router, the only thing I had to do was tell the router to forward ports to the ftp server.  The router should take care of the Network Addressing Translation issue.

One other thing I've found (and backed up by other posts that I've read)... **passive** ftp doesn't always work well.  (Might be a router issue. *shrugs*)  So I use proftp in standalone (not daemon mode) and connections are configured for **active** mode only.

Post up your config file so we can have a look at it.

One question I have: You mentioned that you need complete access to your file system.  I'm not sure why that is -- maybe ftp isn't the right answer for what you're trying to accomplish.  Shell access might be what you really want.

---

### Post by couzin2000 on 2007-12-10
Shell access isn't what I really want. I use the FTP to share some of my stuff with other friends, instead of using P2P which would share WAY too fast. My upload busts everytime!
I'd rather have some sort of php/MySQL db running out of an Apache website, which when accessed (obviously you would need a password acces to the site hosted on my pc) would open an interactive list of all my files. I would even LOVE to have a built-in music and video player (probably Flash-based) so no one would need anything but a Firefox and Flash to see my stuff. But for now, let's, stick with FTP.
Here's a look at my proftpd.conf file (from /etc/proftpd):
```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# Includes DSO modules
Include /etc/proftpd/modules.conf
# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				on
ServerName "couzin2000.homedns.org"
ServerType			inetd
DeferWelcome			off
MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on
TimeoutNoTransfer 600
TimeoutStalled			600
TimeoutIdle 600
DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"
DenyFilter			\*.*/
# Use this to jail all users in their homes 
# DefaultRoot			~
# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell		off
# Port 21 is the standard FTP port.
Port				21
# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
PassivePorts 5500 49152
# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
#MasqueradeAddress MasqueradeAddress
# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 30
# Set the user and group that the server normally runs at.
User				proftpd
Group				nogroup
# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on
# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd		off
# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
# UseSendFile			off
# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend 
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#<IfModule mod_sql.c>
# SQLBackend			mysql
#</IfModule>
TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log
<IfModule mod_tls.c>
TLSEngine off
</IfModule>
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

Also, here's gprotls.conf from /etc/gproftpd:
```
[ req ]
default_bits       = 1024
default_days       = 730
distinguished_name = req_distinguished_name
prompt             = no
output_password    = 

[ req_distinguished_name ]
C            =
ST           = State or province
L            = City or town
O            = Organization
OU           = Organizational unit
CN           = 127.0.0.1
emailAddress = bogusmail@bogusdomain.com

[ req_attributes ]
challengePassword =
```
I've set the router the way it used to be (which was port forwarding, simple as what you explained). Passive FTP ports haven't been setup yet, but I am running proftpd as a daemon. I,d rather have it like that because it's just simpler that way - it has to be there. 

Hope this helps!

---

### Post by umattu on 2007-12-11
I dealt with proftpd when I was first setting up a simple FTP server for, like you, my friends and myself to share files. It took all of about a day before I was uninstalling proftpd and installing vsftpd. 

Vsftpd IME, is fast, secure, and super simple to set up.  

Be sure to forward ports 21 and 22 on your router to the ftp servers local IP.

If your not set with proftpd yet, give it a try.

I would also suggest installing fail2ban, if running an ftp server at your home. This will ban any IP failing to login after a pre-determined amount of attempts, for a pre-determined amount of time, or permanantly.

---

### Post by dj_lightning on 2007-12-11
I am running pure-ftpd-mysql and really like it over Pro or VS which I have been using for years now.  All my FTP users are sitting in a MySQL DB now which I find a bit more (could be less if not done right) secure.  It was super easy to configure and runs well.

Not to sure if I will use Pro or VS again after this.

---

### Post by freebeer on 2007-12-12
Nothing in your config jumps out at me right at the moment.  Have you tried testing (from the server) to see if your port(s) are open?  Some ISPs block ports.  You can give shields up a try at [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) to confirm that your ports are actually open to the outside world.

---

### Post by couzin2000 on 2007-12-14
Nah the ports are opne, and my ISP doesn't affect me directly. I've used this router setup in the past with WinXP, and it has worked fine. No, for some reason, the proftpd gui doesn't seem to respond properly.

---

### Post by kevmaster on 2007-12-15
We're very pleased with vsftpd:

```
aptitude install vsftpd
```

Very secure by default, very fast & lightweight, and (as far as I know) it's never had a vulnerability.

By default the config file is set up to make the server accept anonymous read only connctions. We always replace the config file like this:

```
cp -af /etc/vsftpd.conf /etc/vsftpd.conf.bak
echo "listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=YES
ascii_upload_enable=YES
ascii_download_enable=YES
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd
use_localtime=YES
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key" > /etc/vsftpd.conf

```

.. to enable write access for local users, but only in their caged home directory (UNIX home directory is their 'root')

---

### Post by bproven on 2007-12-15
I chose vsftpd.  Simple setup, very secure, small footprint, reliable (IME), supports TLS/SSL...  No problems recommending it.  The only reason I would hesitate would be if you need quotas, virtual users, or access to a nice gui as these features are lacking.  Other than that is does what its supposed to do really well - FTP.

---

### Post by couzin2000 on 2008-02-12
After having layed down the arms for quite awhile, I've decided to start up again on trying to find the best FTP server software. I've now come to the conclusion that VSFTPD is the software for me - however I'm quite tired of having to look for the darn thing in my PC, even AFTER it's been installed!

I ran ```
sudo apt-get install vsftpd
``` and everything went well... even started vsftpd.

Now I'm looking for it. I've found vsftpd.conf in my /etc/ folder, but how do I change its ports, users, etc? I'm looking for info on [http://vsftpd.beasts.org/]("http://vsftpd.beasts.org/"), but I'm barely finding anything. Is there anyone who knows of a HOWTO thread somehwere in Ubuntuforums?

Sure would like this to work.

Also, as a side note, I'd like to run DynDNS and be able to connect from the outside world so I can share with my friends. I saw this thread ([http://ubuntuforums.org/showthread.php?t=692355&highlight=vsftpd]("http://ubuntuforums.org/showthread.php?t=692355&highlight=vsftpd")), but I don't understand half of what my Canadian buddy explains. Anyone care to explain to me what I'm supposed to be doing? I come from WindowWorld, so to me, installing DynDNS was running an install program, and installing an FTP server was cracking Bulletproof FTP.

How do I get out of this predicament?

---

### Post by lespaul_rentals on 2008-02-12
> **couzin2000]
Also, as a side note, I'd like to run DynDNS and be able to connect from the outside world so I can share with my friends. I saw this thread ([http://ubuntuforums.org/showthread.php?t=692355&highlight=vsftpd]("http://ubuntuforums.org/showthread.php?t=692355&highlight=vsftpd")), but I don't understand half of what my Canadian buddy explains. Anyone care to explain to me what I'm supposed to be doing? I come from WindowWorld, so to me, installing DynDNS was running an install program, and installing an FTP server was cracking Bulletproof FTP.

How do I get out of this predicament?[/QUOTE]

You said your router was a D-Link.  The newer D-Links have an IP log function in the firmware.  You can have it submit its information to [www.dyndns.org](www.dyndns.org) for you.  You just supply the username, password, and hostname and it update whenever you have an IP change.

I have a D-Link myself but I don't use that function because the D-Link is my internal router.  I just login to the DynDNS website, go to" My Services,"  select the hostname I use for myself, and select "Use Automatically Detected IP Address."  I just do that whenever I have a power outage or restart my router.

[QUOTE=couzin2000 said:**
> After having layed down the arms for quite awhile, I've decided to start up again on trying to find the best FTP server software. I've now come to the conclusion that VSFTPD is the software for me - however I'm quite tired of having to look for the darn thing in my PC, even AFTER it's been installed!

I ran ```
sudo apt-get install vsftpd
``` and everything went well... even started vsftpd.

Now I'm looking for it. I've found vsftpd.conf in my /etc/ folder, but how do I change its ports, users, etc? I'm looking for info on [http://vsftpd.beasts.org/]("http://vsftpd.beasts.org/"), but I'm barely finding anything. Is there anyone who knows of a HOWTO thread somehwere in Ubuntuforums?

Google is your friend.  First result:

> NAME
vsftpd.conf - config file for vsftpd   
DESCRIPTION
vsftpd.conf may be used to control various aspects of vsftpd's behaviour. By default, vsftpd looks for this file at the location /etc/vsftpd.conf. However, you may override this by specifying a command line argument to vsftpd. The command line argument is the pathname of the configuration file for vsftpd. This behaviour is useful because you may wish to use an advanced inetd such as xinetd to launch vsftpd with different configuration files on a per virtual host basis. 

  
FORMAT
The format of vsftpd.conf is very simple. Each line is either a comment or a directive. Comment lines start with a # and are ignored. A directive line has the format: 

option=value 

It is important to note that it is an error to put any space between the option, = and value. 

Each setting has a compiled in default which may be modified in the configuration file. 

  
BOOLEAN OPTIONS
Below is a list of boolean options. The value for a boolean option may be set to YES or NO. 

allow_anon_ssl 
Only applies if ssl_enable is active. If set to YES, anonymous users will be allowed to use secured SSL connections. 

Default: NO 
anon_mkdir_write_enable 
If set to YES, anonymous users will be permitted to create new directories under certain conditions. For this to work, the option write_enable must be activated, and the anonymous ftp user must have write permission on the parent directory. 

Default: NO 
anon_other_write_enable 
If set to YES, anonymous users will be permitted to perform write operations other than upload and create directory, such as deletion and renaming. This is generally not recommended but included for completeness. 

Default: NO 
anon_upload_enable 
If set to YES, anonymous users will be permitted to upload files under certain conditions. For this to work, the option write_enable must be activated, and the anonymous ftp user must have write permission on desired upload locations. 

Default: NO 
anon_world_readable_only 
When enabled, anonymous users will only be allowed to download files which are world readable. This is recognising that the ftp user may own files, especially in the presence of uploads. 

Default: YES 
anonymous_enable 
Controls whether anonymous logins are permitted or not. If enabled, both the usernames ftp and anonymous are recognised as anonymous logins. 

Default: YES 
ascii_download_enable 
When enabled, ASCII mode data transfers will be honoured on downloads. 

Default: NO 
ascii_upload_enable 
When enabled, ASCII mode data transfers will be honoured on uploads. 

Default: NO 
async_abor_enable 
When enabled, a special FTP command known as "async ABOR" will be enabled. Only ill advised FTP clients will use this feature. Additionally, this feature is awkward to handle, so it is disabled by default. Unfortunately, some FTP clients will hang when cancelling a transfer unless this feature is available, so you may wish to enable it. 

Default: NO 
background 
When enabled, and vsftpd is started in "listen" mode, vsftpd will background the listener process. i.e. control will immediately be returned to the shell which launched vsftpd. 

Default: NO 
check_shell 
Note! This option only has an effect for non-PAM builds of vsftpd. If disabled, vsftpd will not check /etc/shells for a valid user shell for local logins. 

Default: YES 
chmod_enable 
When enables, allows use of the SITE CHMOD command. NOTE! This only applies to local users. Anonymous users never get to use SITE CHMOD. 

Default: YES 
chown_uploads 
If enabled, all anonymously uploaded files will have the ownership changed to the user specified in the setting chown_username. This is useful from an administrative, and perhaps security, standpoint. 

Default: NO 
chroot_list_enable 
If activated, you may provide a list of local users who are placed in a chroot() jail in their home directory upon login. The meaning is slightly different if chroot_local_user is set to YES. In this case, the list becomes a list of users which are NOT to be placed in a chroot() jail. By default, the file containing this list is /etc/vsftpd.chroot_list, but you may override this with the chroot_list_file setting. 

Default: NO 
chroot_local_user 
If set to YES, local users will be (by default) placed in a chroot() jail in their home directory after login. Warning: This option has security implications, especially if the users have upload permission, or shell access. Only enable if you know what you are doing. Note that these security implications are not vsftpd specific. They apply to all FTP daemons which offer to put local users in chroot() jails. 

Default: NO 
connect_from_port_20 
This controls whether PORT style data connections use port 20 (ftp-data) on the server machine. For security reasons, some clients may insist that this is the case. Conversely, disabling this option enables vsftpd to run with slightly less privilege. 

Default: NO (but the sample config file enables it) 
deny_email_enable 
If activated, you may provide a list of anonymous password e-mail responses which cause login to be denied. By default, the file containing this list is /etc/vsftpd.banned_emails, but you may override this with the banned_email_file setting. 

Default: NO 
dirlist_enable 
If set to NO, all directory list commands will give permission denied. 

Default: YES 
dirmessage_enable 
If enabled, users of the FTP server can be shown messages when they first enter a new directory. By default, a directory is scanned for the file .message, but that may be overridden with the configuration setting message_file. 

Default: NO (but the sample config file enables it) 
download_enable 
If set to NO, all download requests will give permission denied. 

Default: YES 
dual_log_enable 
If enabled, two log files are generated in parallel, going by default to /var/log/xferlog and /var/log/vsftpd.log. The former is a wu-ftpd style transfer log, parseable by standard tools. The latter is vsftpd's own style log. 

Default: NO 
force_dot_files 
If activated, files and directories starting with . will be shown in directory listings even if the "a" flag was not used by the client. This override excludes the "." and ".." entries. 

Default: NO 
force_local_data_ssl 
Only applies if ssl_enable is activated. If activated, all non-anonymous logins are forced to use a secure SSL connection in order to send and receive data on data connections. 

Default: YES 
force_local_logins_ssl 
Only applies if ssl_enable is activated. If activated, all non-anonymous logins are forced to use a secure SSL connection in order to send the password. 

Default: YES 
guest_enable 
If enabled, all non-anonymous logins are classed as "guest" logins. A guest login is remapped to the user specified in the guest_username setting. 

Default: NO 
hide_ids 
If enabled, all user and group information in directory listings will be displayed as "ftp". 

Default: NO 
listen 
If enabled, vsftpd will run in standalone mode. This means that vsftpd must not be run from an inetd of some kind. Instead, the vsftpd executable is run once directly. vsftpd itself will then take care of listening for and handling incoming connections. 

Default: NO 
listen_ipv6 
Like the listen parameter, except vsftpd will listen on an IPv6 socket instead of an IPv4 one. This parameter and the listen parameter are mutually exclusive. 

Default: NO 
local_enable 
Controls whether local logins are permitted or not. If enabled, normal user accounts in /etc/passwd may be used to log in. 

Default: NO 
log_ftp_protocol 
When enabled, all FTP requests and responses are logged, providing the option xferlog_std_format is not enabled. Useful for debugging. 

Default: NO 
ls_recurse_enable 
When enabled, this setting will allow the use of "ls -R". This is a minor security risk, because a ls -R at the top level of a large site may consume a lot of resources. 

Default: NO 
no_anon_password 
When enabled, this prevents vsftpd from asking for an anonymous password - the anonymous user will log straight in. 

Default: NO 
no_log_lock 
When enabled, this prevents vsftpd from taking a file lock when writing to log files. This option should generally not be enabled. It exists to workaround operating system bugs such as the Solaris / Veritas filesystem combination which has been observed to sometimes exhibit hangs trying to lock log files. 

Default: NO 
one_process_model 
If you have a Linux 2.4 kernel, it is possible to use a different security model which only uses one process per connection. It is a less pure security model, but gains you performance. You really don't want to enable this unless you know what you are doing, and your site supports huge numbers of simultaneously connected users. 

Default: NO 
passwd_chroot_enable 
If enabled, along with chroot_local_user , then a chroot() jail location may be specified on a per-user basis. Each user's jail is derived from their home directory string in /etc/passwd. The occurrence of /./ in the home directory string denotes that the jail is at that particular location in the path. 

Default: NO 
pasv_enable 
Set to NO if you want to disallow the PASV method of obtaining a data connection. 

Default: YES 
pasv_promiscuous 
Set to YES if you want to disable the PASV security check that ensures the data connection originates from the same IP address as the control connection. Only enable if you know what you are doing! The only legitimate use for this is in some form of secure tunnelling scheme, or perhaps to facilitate FXP support. 

Default: NO 
port_enable 
Set to NO if you want to disallow the PORT method of obtaining a data connection. 

Default: YES 
port_promiscuous 
Set to YES if you want to disable the PORT security check that ensures that outgoing data connections can only connect to the client. Only enable if you know what you are doing! 

Default: NO 
run_as_launching_user 
Set to YES if you want vsftpd to run as the user which launched vsftpd. This is useful where root access is not available. MASSIVE WARNING! Do NOT enable this option unless you totally know what you are doing, as naive use of this option can create massive security problems. Specifically, vsftpd does not / cannot use chroot technology to restrict file access when this option is set (even if launched by root). A poor substitute could be to use a deny_file setting such as {/*,*..*}, but the reliability of this cannot compare to chroot, and should not be relied on. If using this option, many restrictions on other options apply. For example, options requiring privilege such as non-anonymous logins, upload ownership changing, connecting from port 20 and listen ports less than 1024 are not expected to work. Other options may be impacted. 

Default: NO 
secure_email_list_enable 
Set to YES if you want only a specified list of e-mail passwords for anonymous logins to be accepted. This is useful as a low-hassle way of restricting access to low-security content without needing virtual users. When enabled, anonymous logins are prevented unless the password provided is listed in the file specified by the email_password_file setting. The file format is one password per line, no extra whitespace. The default filename is /etc/vsftpd.email_passwords. 

Default: NO 
session_support 
This controls whether vsftpd attempts to maintain sessions for logins. If vsftpd is maintaining sessions, it will try and update utmp and wtmp. It will also open a pam_session if using PAM to authenticate, and only close this upon logout. You may wish to disable this if you do not need session logging, and you wish to give vsftpd more opportunity to run with less processes and / or less privilege. NOTE - utmp and wtmp support is only provided with PAM enabled builds. 

Default: NO 
setproctitle_enable 
If enabled, vsftpd will try and show session status information in the system process listing. In other words, the reported name of the process will change to reflect what a vsftpd session is doing (idle, downloading etc). You probably want to leave this off for security purposes. 

Default: NO 
ssl_enable 
If enabled, and vsftpd was compiled against OpenSSL, vsftpd will support secure connections via SSL. This applies to the control connection (including login) and also data connections. You'll need a client with SSL support too. NOTE!! Beware enabling this option. Only enable it if you need it. vsftpd can make no guarantees about the security of the OpenSSL libraries. By enabling this option, you are declaring that you trust the security of your installed OpenSSL library. 

Default: NO 
ssl_sslv2 
Only applies if ssl_enable is activated. If enabled, this option will permit SSL v2 protocol connections. TLS v1 connections are preferred. 

Default: NO 
ssl_sslv3 
Only applies if ssl_enable is activated. If enabled, this option will permit SSL v3 protocol connections. TLS v1 connections are preferred. 

Default: NO 
ssl_tlsv1 
Only applies if ssl_enable is activated. If enabled, this option will permit TLS v1 protocol connections. TLS v1 connections are preferred. 

Default: YES 
syslog_enable 
If enabled, then any log output which would have gone to /var/log/vsftpd.log goes to the system log instead. Logging is done under the FTPD facility. 

Default: NO 
tcp_wrappers 
If enabled, and vsftpd was compiled with tcp_wrappers support, incoming connections will be fed through tcp_wrappers access control. Furthermore, there is a mechanism for per-IP based configuration. If tcp_wrappers sets the VSFTPD_LOAD_CONF environment variable, then the vsftpd session will try and load the vsftpd configuration file specified in this variable. 

Default: NO 
text_userdb_names 
By default, numeric IDs are shown in the user and group fields of directory listings. You can get textual names by enabling this parameter. It is off by default for performance reasons. 

Default: NO 
tilde_user_enable 
If enabled, vsftpd will try and resolve pathnames such as ~chris/pics, i.e. a tilde followed by a username. Note that vsftpd will always resolve the pathnames ~ and ~/something (in this case the ~ resolves to the initial login directory). Note that ~user paths will only resolve if the file /etc/passwd may be found within the _current_ chroot() jail. 

Default: NO 
use_localtime 
If enabled, vsftpd will display directory listings with the time in your local time zone. The default is to display GMT. The times returned by the MDTM FTP command are also affected by this option. 

Default: NO 
use_sendfile 
An internal setting used for testing the relative benefit of using the sendfile() system call on your platform. 

Default: YES 
userlist_deny 
This option is examined if userlist_enable is activated. If you set this setting to NO, then users will be denied login unless they are explicitly listed in the file specified by userlist_file. When login is denied, the denial is issued before the user is asked for a password. 

Default: YES 
userlist_enable 
If enabled, vsftpd will load a list of usernames, from the filename given by userlist_file. If a user tries to log in using a name in this file, they will be denied before they are asked for a password. This may be useful in preventing cleartext passwords being transmitted. See also userlist_deny. 

Default: NO 
virtual_use_local_privs 
If enabled, virtual users will use the same privileges as local users. By default, virtual users will use the same privileges as anonymous users, which tends to be more restrictive (especially in terms of write access). 

Default: NO 
write_enable 
This controls whether any FTP commands which change the filesystem are allowed or not. These commands are: STOR, DELE, RNFR, RNTO, MKD, RMD, APPE and SITE. 

Default: NO 
xferlog_enable 
If enabled, a log file will be maintained detailling uploads and downloads. By default, this file will be placed at /var/log/vsftpd.log, but this location may be overridden using the configuration setting vsftpd_log_file. 

Default: NO (but the sample config file enables it) 
xferlog_std_format 
If enabled, the transfer log file will be written in standard xferlog format, as used by wu-ftpd. This is useful because you can reuse existing transfer statistics generators. The default format is more readable, however. The default location for this style of log file is /var/log/xferlog, but you may change it with the setting xferlog_file. 

Default: NO 

  
NUMERIC OPTIONS
Below is a list of numeric options. A numeric option must be set to a non negative integer. Octal numbers are supported, for convenience of the umask options. To specify an octal number, use 0 as the first digit of the number. 

accept_timeout 
The timeout, in seconds, for a remote client to establish connection with a PASV style data connection. 

Default: 60 
anon_max_rate 
The maximum data transfer rate permitted, in bytes per second, for anonymous clients. 

Default: 0 (unlimited) 
anon_umask 
The value that the umask for file creation is set to for anonymous users. NOTE! If you want to specify octal values, remember the "0" prefix otherwise the value will be treated as a base 10 integer! 

Default: 077 
connect_timeout 
The timeout, in seconds, for a remote client to respond to our PORT style data connection. 

Default: 60 
data_connection_timeout 
The timeout, in seconds, which is roughly the maximum time we permit data transfers to stall for with no progress. If the timeout triggers, the remote client is kicked off. 

Default: 300 
file_open_mode 
The permissions with which uploaded files are created. Umasks are applied on top of this value. You may wish to change to 0777 if you want uploaded files to be executable. 

Default: 0666 
ftp_data_port 
The port from which PORT style connections originate (as long as the poorly named connect_from_port_20 is enabled). 

Default: 20 
idle_session_timeout 
The timeout, in seconds, which is the maximum time a remote client may spend between FTP commands. If the timeout triggers, the remote client is kicked off. 

Default: 300 
listen_port 
If vsftpd is in standalone mode, this is the port it will listen on for incoming FTP connections. 

Default: 21 
local_max_rate 
The maximum data transfer rate permitted, in bytes per second, for local authenticated users. 

Default: 0 (unlimited) 
local_umask 
The value that the umask for file creation is set to for local users. NOTE! If you want to specify octal values, remember the "0" prefix otherwise the value will be treated as a base 10 integer! 

Default: 077 
max_clients 
If vsftpd is in standalone mode, this is the maximum number of clients which may be connected. Any additional clients connecting will get an error message. 

Default: 0 (unlimited) 
max_per_ip 
If vsftpd is in standalone mode, this is the maximum number of clients which may be connected from the same source internet address. A client will get an error message if they go over this limit. 

Default: 0 (unlimited) 
pasv_max_port 
The maximum port to allocate for PASV style data connections. Can be used to specify a narrow port range to assist firewalling. 

Default: 0 (use any port) 
pasv_min_port 
The minimum port to allocate for PASV style data connections. Can be used to specify a narrow port range to assist firewalling. 

Default: 0 (use any port) 
trans_chunk_size 
You probably don't want to change this, but try setting it to something like 8192 for a much smoother bandwidth limiter. 

Default: 0 (let vsftpd pick a sensible setting) 

  
STRING OPTIONS
Below is a list of string options. 

anon_root 
This option represents a directory which vsftpd will try to change into after an anonymous login. Failure is silently ignored. 

Default: (none) 
banned_email_file 
This option is the name of a file containing a list of anonymous e-mail passwords which are not permitted. This file is consulted if the option deny_email_enable is enabled. 

Default: /etc/vsftpd.banned_emails 
banner_file 
This option is the name of a file containing text to display when someone connects to the server. If set, it overrides the banner string provided by the ftpd_banner option. 

Default: (none) 
chown_username 
This is the name of the user who is given ownership of anonymously uploaded files. This option is only relevant if another option, chown_uploads, is set. 

Default: root 
chroot_list_file 
The option is the name of a file containing a list of local users which will be placed in a chroot() jail in their home directory. This option is only relevant if the option chroot_list_enable is enabled. If the option chroot_local_user is enabled, then the list file becomes a list of users to NOT place in a chroot() jail. 

Default: /etc/vsftpd.chroot_list 
cmds_allowed 
This options specifies a comma separated list of allowed FTP commands (post login. USER, PASS and QUIT are always allowed pre-login). Other commands are rejected. This is a powerful method of really locking down an FTP server. Example: cmds_allowed=PASV,RETR,QUIT 

Default: (none) 
deny_file 
This option can be used to set a pattern for filenames (and directory names etc.) which should not be accessible in any way. The affected items are not hidden, but any attempt to do anything to them (download, change into directory, affect something within directory etc.) will be denied. This option is very simple, and should not be used for serious access control - the filesystem's permissions should be used in preference. However, this option may be useful in certain virtual user setups. In particular aware that if a filename is accessible by a variety of names (perhaps due to symbolic links or hard links), then care must be taken to deny access to all the names. Access will be denied to items if their name contains the string given by hide_file, or if they match the regular expression specified by hide_file. Note that vsftpd's regular expression matching code is a simple implementation which is a subset of full regular expression functionality. Because of this, you will need to carefully and exhaustively test any application of this option. And you are recommended to use filesystem permissions for any important security policies due to their greater reliability. Example: deny_file={*.mp3,*.mov,.private} 

Default: (none) 
dsa_cert_file 
This option specifies the location of the DSA certificate to use for SSL encrypted connections. 

Default: (none - an RSA certificate suffices) 
email_password_file 
This option can be used to provide an alternate file for usage by the secure_email_list_enable setting. 

Default: /etc/vsftpd.email_passwords 
ftp_username 
This is the name of the user we use for handling anonymous FTP. The home directory of this user is the root of the anonymous FTP area. 

Default: ftp 
ftpd_banner 
This string option allows you to override the greeting banner displayed by vsftpd when a connection first comes in. 

Default: (none - default vsftpd banner is displayed) 
guest_username 
See the boolean setting guest_enable for a description of what constitutes a guest login. This setting is the real username which guest users are mapped to. 

Default: ftp 
hide_file 
This option can be used to set a pattern for filenames (and directory names etc.) which should be hidden from directory listings. Despite being hidden, the files / directories etc. are fully accessible to clients who know what names to actually use. Items will be hidden if their names contain the string given by hide_file, or if they match the regular expression specified by hide_file. Note that vsftpd's regular expression matching code is a simple implementation which is a subset of full regular expression functionality. Example: hide_file={*.mp3,.hidden,hide*,h?} 

Default: (none) 
listen_address 
If vsftpd is in standalone mode, the default listen address (of all local interfaces) may be overridden by this setting. Provide a numeric IP address. 

Default: (none) 
listen_address6 
Like listen_address, but specifies a default listen address for the IPv6 listener (which is used if listen_ipv6 is set). Format is standard IPv6 address format. 

Default: (none) 
local_root 
This option represents a directory which vsftpd will try to change into after a local (i.e. non-anonymous) login. Failure is silently ignored. 

Default: (none) 
message_file 
This option is the name of the file we look for when a new directory is entered. The contents are displayed to the remote user. This option is only relevant if the option dirmessage_enable is enabled. 

Default: .message 
nopriv_user 
This is the name of the user that is used by vsftpd when it wants to be totally unprivileged. Note that this should be a dedicated user, rather than nobody. The user nobody tends to be used for rather a lot of important things on most machines. 

Default: nobody 
pam_service_name 
This string is the name of the PAM service vsftpd will use. 

Default: ftp 
pasv_address 
Use this option to override the IP address that vsftpd will advertise in response to the PASV command. Provide a numeric IP address. 

Default: (none - the address is taken from the incoming connected socket) 
rsa_cert_file 
This option specifies the location of the RSA certificate to use for SSL encrypted connections. 

Default: /usr/share/ssl/certs/vsftpd.pem 
secure_chroot_dir 
This option should be the name of a directory which is empty. Also, the directory should not be writable by the ftp user. This directory is used as a secure chroot() jail at times vsftpd does not require filesystem access. 

Default: /usr/share/empty 
ssl_ciphers 
This option can be used to select which SSL ciphers vsftpd will allow for encrpyted SSL connections. See the ciphers man page for further details. Note that restricting ciphers can be a useful security precaution as it prevents malicious remote parties forcing a cipher which they have found problems with. 

Default: DES-CBC3-SHA 
user_config_dir 
This powerful option allows the override of any config option specified in the manual page, on a per-user basis. Usage is simple, and is best illustrated with an example. If you set user_config_dir to be /etc/vsftpd_user_conf and then log on as the user "chris", then vsftpd will apply the settings in the file /etc/vsftpd_user_conf/chris for the duration of the session. The format of this file is as detailed in this manual page! PLEASE NOTE that not all settings are effective on a per-user basis. For example, many settings only prior to the user's session being started. Examples of settings which will not affect any behviour on a per-user basis include listen_address, banner_file, max_per_ip, max_clients, xferlog_file, etc. 

Default: (none) 
user_sub_token 
This option is useful is conjunction with virtual users. It is used to automatically generate a home directory for each virtual user, based on a template. For example, if the home directory of the real user specified via guest_username is /home/virtual/$USER, and user_sub_token is set to $USER, then when virtual user fred logs in, he will end up (usually chroot()'ed) in the directory /home/virtual/fred. This option also takes affect if local_root contains user_sub_token. 

Default: (none) 
userlist_file 
This option is the name of the file loaded when the userlist_enable option is active. 

Default: /etc/vsftpd.user_list 
vsftpd_log_file 
This option is the name of the file to which we write the vsftpd style log file. This log is only written if the option xferlog_enable is set, and xferlog_std_format is NOT set. Alternatively, it is written if you have set the option dual_log_enable. One further complication - if you have set syslog_enable, then this file is not written and output is sent to the system log instead. 

Default: /var/log/vsftpd.log 
xferlog_file 
This option is the name of the file to which we write the wu-ftpd style transfer log. The transfer log is only written if the option xferlog_enable is set, along with xferlog_std_format. Alternatively, it is written if you have set the option dual_log_enable. 

Default: /var/log/xferlog

---

### Post by couzin2000 on 2008-02-12
> **lespaul_rentals said:**
> You said your router was a D-Link.  The newer D-Links have an IP log function in the firmware.  You can have it submit its information to [www.dyndns.org](www.dyndns.org) for you.  You just supply the username, password, and hostname and it update whenever you have an IP change.
Found that, but I didn't know **at ALL** that it would be used INSTEAD of the software downloaded from DynDNS.org. Guess that means I'll be using that option from now on instead of a downloaded locator executable... thanks!

> **lespaul_rentals said:**
> I have a D-Link myself but I don't use that function because the D-Link is my internal router.  I just login to the DynDNS website, go to" My Services,"  select the hostname I use for myself, and select "Use Automatically Detected IP Address."  I just do that whenever I have a power outage or restart my router.
Will keep that in mind _for sure_.

> **lespaul_rentals said:**
> Google is your friend.  First result:
Well, I just went through the whole entire file, and wrote down every possible option one by one in my vsftpd.conf file... but I'm no further on than I was before.

Specifically, I want to do this:
[LIST]
[*]define all my users and passwords for each;
[*]define what each of them can do (i.e., go into which folder and download what);
[*]make sure that vsftpd is currently running with these settings;
[*]test the system to make sure it is running and reliable.
[/LIST]
I need to know how to do this, but there are no forums for vsftpd, and no well written manual. For a beginner, using Apache is tricky... this is the same. You have to know what you're looking for - so I need a newbie-friendly manual, or a newbie-friendly guide (as in a real person) to help me out here, because I don't know what I'm looking for nor where to look for it.

---

### Post by freebeer on 2008-02-13
I haven't played with vsftpd, so I'm probably unable to help much.  It looks line the default config file is self-documenting.  It sounds to me that your best approach would be to start small (using defaults) then tweak the configuration file one or two settings at a time until you've got it working the way you want.  The config file describes some of the things you were looking for (such as port, etc.)

---

### Post by couzin2000 on 2008-02-13
Well, I would if it were possible, but I can't seem to be able to log in from another computer. I'm looking to figure out where I define who the users are and how thye log in - so far, the config file only sets a general setting for any user - unless I don't know what I'm doing.

Anyone else?

---

### Post by freebeer on 2008-02-13
Well, let's look at the connection from another computer first.  Where is this other computer in relation to your server?  Is it local (LAN) or remote (Internet)?

---

### Post by lespaul_rentals on 2008-02-13
The way you configure *vsftpd.conf* is through modifying the values that are already in there.  There should be a long list of options.  Some of them maybe commented out using the "#" character.  If you wish to set the option, remove the "#" from the line, like so:

```
// This is what a line from the vsftpd.conf file might look like.
// Notice the "#" symbol; if left there it will not set the option.
// So, if you want to set anonymous login YES/NO, you need to find
// the following line and remove the comment tag.

#anonymous_enable YES

// This should become:

anonymous_enable YES

// This assumes you want anonymous logins enabled.  If not:

anonymous_enable NO
```

If you want your FTP server to require authentication (might be a good idea if you don't like the idea of just anyone being able to gain access), start by disabling anonymous access.  Then, add users for the server.  Because vsftpd is a daemon, it is not like an FTP server on Windows, where the users and privileges are set by the software.  vsftpd reads the actual system for eligible users and privileges.  You can add new users with the following command:

```
adduser
```

Follow the prompts and it will create a new user with the information you provide.

To restrict what they can access, I would recommend enabling chroot_local_user.  There is a line in the *vsftp.conf* file to enable chroot_local_user.  This will keep anyone who is logged in as a local user locked in their /home directory.

For example, say I create a user called "foo" and want him to only have access to certain files, not the whole computer.  I would go into *vsftp.conf* and set chroot_local_user to "YES" to limit him (and all the rest of the FTP users) to his own home directory.  Then, say I want to give Mr. Foo Bar access to a video file I have on my computer, *The Bourne Ultimatum* (not condoning piracy ;)).  I could either copy or move it to his home directory, **/home/foo**, or create what is called a "symbolic link."

```
ln -s <path to source file> <path to link>
```

For the following example, assume I keep my movies in my home directory in a folder called "Movies":

```
ln -s /home/myself/Movies/The_Bourne_Ultimatum_XVID.avi /home/foo/The_Bourne_Ultimatum_XVID.avi
```

Now, whenever foo logs in, he will see what appears to be the movie file, and can then download it.  You are not wasting space by having the movie file twice on your hard drive, but to the end user, there is no apparent difference.  The symbolic link works perfectly for this situation.  Just make symbolic links for all files and folders you want to share, and put the symbolic links in the desired user's folder.  Now my buddy foo can download his movie, and I don't have to worry about him stumbling across any of my personal files.  ;)

To start/stop/restart the vsftpd daemon, please run the following:

```
sudo /etc/init.d/vsftpd <command>
```

So, to restart it (say after editing a configuration file to run it with the new settings:

```
sudo /etc/init.d/vsftpd restart
```

To test the server, find out your IP address.  Run

```
ifconfig
```

...and look for your main network device.  You should see your private IP address there.  If you have a second computer, you can use your private IP address and try to access the server that way.  If it works, you're good to go.  All you have to do after that is forward port 21 from your router to your private IP.

In your D-Link, go into "Advanced," and look for "Virtual Servers."  Add a rule to forward public port 21 and private port 21 to your private IP address, the one you found when running **ifconfig**.  Save the changes, and you should be good to go!  Have a friend try to access it, or use an online FTP test ([http://www.g6ftpserver.com/en/ftptest](http://www.g6ftpserver.com/en/ftptest)) to make sure it's accessible to the outside world.

---

### Post by couzin2000 on 2008-02-14
> **lespaul_rentals said:**
> If you want your FTP server to require authentication (might be a good idea if you don't like the idea of just anyone being able to gain access), start by disabling anonymous access.  Then, add users for the server.  Because vsftpd is a daemon, it is not like an FTP server on Windows, where the users and privileges are set by the software.  vsftpd reads the actual system for eligible users and privileges.  You can add new users with the following command
So the way I understand this is that the users in vsftpd are *actual* users in my pc - like when I log on physically to the pc? Had I known that, it would have made everything a whole lot easier. I guess it's my misdunderstanding of the word 'daemon', then, which is a 'service' in Windows.

I read something about symlinks, something to do with the fact that if I restrict chroot_local_user, they wouldn't work. Am I wrong? If it works, then it'll be pretty easy to setup.

From Gnome's GUI, can I mass create symlinks, and just copy them to another folder? I assume I'd have to have root privileges to copy them from one user to the other, but... assuming I can mass create the symlinks, it'd make everything easier than typing every link.

As far as the DLink goes, I've had that figured out for a while. However, I'm assuming the problem I have connecting by FTP comes from the fact that I'm using my own user -- I'm logged in to the pc, sitting in front of it, and I open my FTP client, try to connect to the DynDNS address, punch in a port, user and pass, but it still doesn't work. I gues this is because I'm using the user, so it's busy and can't be logged in twice? I'll have to try it out from work or something...

Thank you so much for the help, this makes so much more sense now!

---

### Post by freebeer on 2008-02-15
As users on your system, they receive the rights and privileges that you grant them (and is enforced by the OS).

I've never used symlinks myself (the ones I have were set up through the install process) but you should be able to just copy them to each user's home folder.

As for the logging in problem: it's not because you're using your own user account (that's permitted, provided, of course, it's not overridden in your ftp config).  It's because from within your lan you cannot reference yourself using the external domain name.  So instead of "mydomain.com" you reference it with 127.0.0.1 (the loopback address of your machine) or, if on another machine within your local network, the internal IP address of the ftp server machine (something like 192.168.1.104 of whatever it is).

If you want to be able to access it through your external domain name, you need to make an entry in your /etc/hosts file.  A line that looks like this:

```

127.0.0.1 mydomain.com

```

What that does is it tells your machine to substitute "mydomain.com" with the local IP address.  That's how the Domain Name system works, basically.  When you type "google.com" your machine looks at the hosts file.  If it can't find a match, it then goes out and asks your (usually ISP's) Domain Name Server to find "google.com".  If found, it returns Google's IP address.

---

### Post by hyper_ch on 2008-02-15
depending on what you want to do, why not using SSH and chrooted user accounts?

---

### Post by lespaul_rentals on 2008-02-18
**-------THE INFORMATION CONTAINED IN THIS POST REFERRING TO SYMBOLIC LINKS WORKING IN CHROOT JAIL IS INCORRECT.  Please refer to post #24 for a working solution.-------**

> **couzin2000 said:**
> So the way I understand this is that the users in vsftpd are *actual* users in my pc - like when I log on physically to the pc?

Indeed.

> I read something about symlinks, something to do with the fact that if I restrict chroot_local_user, they wouldn't work. Am I wrong? If it works, then it'll be pretty easy to setup.

It should work fine.  Worked fine for me.  You may have to give the symbolic links world-readable permissions:

```
chmod 644 <symbolic link>
```

Or, to perform the permission modification on a directory and all its contents:

```
chmod -R 644 <folder>
```


> From Gnome's GUI, can I mass create symlinks, and just copy them to another folder? I assume I'd have to have root privileges to copy them from one user to the other, but... assuming I can mass create the symlinks, it'd make everything easier than typing every link.

Should be able to.

> Thank you so much for the help, this makes so much more sense now!

No problem, let me know if you need any more help.

---

### Post by Holmes89 on 2008-02-18
Ok I'm new at this. I have installed vsftpd on my server. What I want to be able to do is to share files on a public level, meaning people can connect and share files. Also though I want to be able to upload webpages and files to the server through windows (on a local network) how do I do this? I'm kind of confused and can't find a good guide. Thanks in advance.

Oh and I know this may sound stupid but what port do I need open on my router to share?

---

### Post by lespaul_rentals on 2008-02-19
Hey, couzin2000, I spoke too soon.  You are right in that symbolic links will not function in a chroot jail.  I apologize!  #-o

Instead, use the mount function.  Any recent kernel supports mounting files, folders, and partitions on multiple mountpoints.  It will also work in a chroot jail.

Say I wanted to mount my Music folder in someone else's home directory, so he or she could access it using FTP:

```
mount --bind /home/myself/Music /home/myfriend/Music
```

That'll do the trick!  :)

---

### Post by lespaul_rentals on 2008-02-19
> **Holmes89 said:**
> Ok I'm new at this. I have installed vsftpd on my server. What I want to be able to do is to share files on a public level, meaning people can connect and share files.

Share on a public level as in allow anyone to connect and upload?  You will need to enable anonymous access and anonymous uploads.  First though, consider the risks of this:

[LIST]
[*]Warez/cracker gangs will often upload their cracks and pirated products to anonymous FTP servers.  You might be fine for a while, but eventually your FTP server will be found and taken advantage of.  If you keep an eye on your server, you should be okay, but just remember that this is a problem with allowing anonymous access.
[*]What if someone uploads CP to your server?  Sure, you might not go to prison for possession but there's nothing like a good conversation with the F.B.I. on why there was CP on your computer.  Keep that in mind as well.
[*]Some ISP's block port 21 as standard practice, but still others allow their users to open FTP servers.  If they catch you with an anonymous FTP server they may tell you to stop.
[/LIST]

If you still decide you want to go ahead and do it, edit your */etc/vsftpd.conf* file to reflect it (I can help you do this if you need help).

> **Holmes89 said:**
> Also though I want to be able to upload webpages and files to the server through windows (on a local network) how do I do this? I'm kind of confused and can't find a good guide. Thanks in advance.

I would recommend you use FTP to upload the files you want on your website to your home directory, then use SSH to copy the files to the */var/www* directory.  If you configure your FTP server to allow access to the */var/www* directory, it would be a possible security risk.

Or, you could always edit your Apache configuration to use */home/yourself/public_html* as your website directory, then upload the files to the web directory directly.

> **Holmes89 said:**
> Oh and I know this may sound stupid but what port do I need open on my router to share?

21.  And you shouldn't *open* it, you should *forward* it.

---

### Post by zecora on 2008-02-19
Just wondering if you guys would recommend a howto on a FTP server/Mysql.

---

### Post by leroy_30 on 2008-02-19
I haven't noticed anyone mentioning this so here's my attempt at helping :)

I setup an ftpserver zFTPServer on Windoze (I'm working on moving to linux) about a year ago, and had issues where I could connect fine from my local network but external connections just didn't work.

This wasn't a major issue to me until a few days ago when a client needed to upload a 7GIG data file and couldn't connect.

After searching long & hard I discovered that (when using Passive connections at least) the ftp server upon recieving a connection request returns the IP & Port that It (for the lack of a better term) wants to talk over. However, when using port forwarding on a router the server replies with it's own local ip address(eg 192.168.x.x) not the ip address visible to the rest of the world. Therefore the ftp client can't resolve it and drops the connection. In zFTPServer there is a Passive connections area where you enter the IP address(i used [www.myhost.com](www.myhost.com)) and port range for passive connections. Problem solved.

I don't know if this will help at all but it was very useful info for me.

---

### Post by couzin2000 on 2008-02-19
> **lespaul_rentals said:**
> Hey, couzin2000, I spoke too soon.  You are right in that symbolic links will not function in a chroot jail.  I apologize!  #-o

Instead, use the mount function.  Any recent kernel supports mounting files, folders, and partitions on multiple mountpoints.  It will also work in a chroot jail.

Say I wanted to mount my Music folder in someone else's home directory, so he or she could access it using FTP:

```
mount --bind /home/myself/Music /home/myfriend/Music
```

That'll do the trick!  :)
Thanks... I've been reading up a lot on this stuff, but I hardly know the **mount** function. I know I should just go **mount --help**, but for the benefit of everyone...

I assume the *bind* argument is passed so that the mounting will occur and reoccur every single time the user logs on. Which path is the source and which is the target path? For example,```
mount --bind /home/myself/Music /home/myfriend/Music
``` mean that I'm opening my "myself" folder to my friend's "myfriend" folder, so that if he is in a chroot jail he can access the music folder in MY profile from his jail? This would mean the first path is the source, the second one would be the target... right?

---

### Post by lespaul_rentals on 2008-02-20
> **couzin2000 said:**
> Thanks... I've been reading up a lot on this stuff, but I hardly know the **mount** function. I know I should just go **mount --help**, but for the benefit of everyone...

I assume the *bind* argument is passed so that the mounting will occur and reoccur every single time the user logs on. Which path is the source and which is the target path? For example,```
mount --bind /home/myself/Music /home/myfriend/Music
``` mean that I'm opening my "myself" folder to my friend's "myfriend" folder, so that if he is in a chroot jail he can access the music folder in MY profile from his jail? This would mean the first path is the source, the second one would be the target... right?

I don't think that *bind* makes it so that the partition is mounted automatically at boot.  You may have to re-mount it, but I could be wrong.

And yes, it's the source path, and the destination mount point.

---

### Post by Holmes89 on 2008-02-20
> **lespaul_rentals said:**
> Share on a public level as in allow anyone to connect and upload?  You will need to enable anonymous access and anonymous uploads.  First though, consider the risks of this:


No I want to make a list of users so they can connect so we can share files. I don't want it public but I do want to share with people outside my network so I would like to create users.


> 
21.  And you shouldn't *open* it, you should *forward* it.

I know, dumb comment. Should I change the port on my server to something other than 21 because you said that some ISPs block it?

And is there a way to limit the number of people connecting, the size of the files, the maximum capacity for storing sharing things on the server. Really I don't want it to fill up to much so is there a way to set a lifespan for a file on the server, like if the file has not been downloaded for x amount of days it gets deleted?

And finally, I only want a specific part of the server to be seen, how do I change where this is an ensure that people can't move around in the server folders?

Thanks for all of the help

---

### Post by norha_king on 2008-03-04
Hi, I use AnyClient when I need file transfer. It is a free platform independent file transfer application that supports all major file transfer protocols including FTP/S, SFTP and WebDAV/S. [ AnyClient ](http://www.anyclient.com) is available both as a web based service requiring no software installation, and as a downloadable application that you can install locally.  Hope this will help you.
All the best!

---

### Post by norha_king on 2008-03-04
..

---

