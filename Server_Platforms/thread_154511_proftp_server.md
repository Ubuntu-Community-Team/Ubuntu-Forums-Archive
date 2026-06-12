---
title: "proftp server"
date: 2006-04-03
forum: Server Platforms
---

### Post by gymsmoke on 2006-04-03
I've got proftpd server installed on Ubuntu Server 5.10 ... seems to run fine, except that when I log into the server I am, be default, dropped into my /home directory (which is fine)... But I cannot change directories to anywhere...

I'm sure that this has to be a function of the proftpd.conf file, since the directory I want to change to is a web dir for publishing files, which is both owned and grouped as me ...

Any input on this would be greatly appreciated.

---

### Post by frodon on 2006-04-03
Could you post your proftpd.conf file please ? : ```
sudo gedit /etc/proftpd.conf
```Describe what you want to access exactly too (which directories ?), because it's really more secure to lock the user in a directory.

---

### Post by gymsmoke on 2006-04-03
frodon~
Sure.  Here's the file...

#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

ServerName                      "Debian"
ServerType                      standalone
DeferWelcome                    off

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    on

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                     "-l"

DenyFilter                      \*.*/

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd               off

# Uncomment this if you would use TLS module:
#TLSEngine                      on

# Uncomment this if you would use quota module:
#Quotas                         on

# Uncomment this if you would use ratio module:
#Ratios                         on
# Port 21 is the standard FTP port.
Port                            21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                            nobody
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default.
#DelayEngine                    off

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
#   DisplayFirstChdir           .message
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

DefaultRoot ~
IdentLookups off
ServerIdent on "FTP Server ready."

---

### Post by frodon on 2006-04-03
The **DefaultRoot ~** command lock the user in its home directory, if you remove this line you will be able to change directory but it's really unsecure because you will be able to access everything.
So there isn't a lot of solution : 
1- Remove the **DefaultRoot ~** command and access everything (unsecure)
2- a) if you just want to access one directory replace the **DefaultRoot ~** command by : ```
DefaultRoot the_directory_path_to_share
```
b) if you need more directories the easiest and secure way i know is as follow. First create a directory for the FTP called *myftp* under your /home for example. Use this command to lock all in the directory ```
DefaultRoot /home/*myftp*
```. Then create as many directories than you want to share, for example create a directory called *my_share* then mount whatever you want in with this command : ```
sudo mount -o bind the-directory-to-share /home/*myftp*/*my_share*
```
Using this way you can lock all in a directory and share what you want in a _secure_ way.

---

### Post by gymsmoke on 2006-04-03
frodon~
So, if my default dir is /home/gymsmoke , but I want to be able ftp onto the server and put files in /var/www/gymsmoke , I would:

Default_Root = /home/ftp_share

sudo mkdir /home/ftp_share
sudo mkdir /home/ftp_share/gymsmoke
sudo mount -o bind /var/www  /home/ftp/gymsmoke

if that's correct, then would this also work?
sudo mount -o bind /var/www /home/gymsmoke

---

### Post by frodon on 2006-04-04
if you use *Default_Root /home/ftp_share* you will not be able to access anything outside the ftp_share directory therfore you will not be able to access /home/gymsmoke.
However no problem with the rest, you will be locked into /home/ftp_share and you will see your /var/www/ directory in /home/ftp_share/gymsmoke.
You should have a look to my guide, i put a script in which allow you to start/stop, mount unmount the directory you want and all that with a GUI : [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

Let me know if you get other problems.

---

### Post by gymsmoke on 2006-04-04
frodon~
Thanks for the link!  I read through the threads... i'll walk this down later today and implement it.  If I have time, I may go through and clean up the text and such and submit it to you for a re-release under Breezy Badger (if that's ok)...

---

