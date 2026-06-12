---
title: "Howto: Easy FTP with vsftpd"
date: 2007-08-05
forum: Tutorials
---

### Post by ruibernardo on 2007-08-05
I like [vsftpd]("http://freshmeat.net/projects/vsftpd/"). It's very very simple to configure.

Now let's get to the point.

[SIZE=4]Installation[/SIZE]
```
sudo apt-get install vsftpd

```This installs ssl-cert, openssl and vsftpd, only with anonymous login and just for downloads from a jailed /home/ftp/.

[SIZE=4]Configuration[/SIZE]

Make a copy of the original configuration file. It is very well commented. Keep a copy to have the original settings and comments, just in case.
```
sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.original
```Now edit the file /etc/vsftpd.conf and change it's settings as follows.

[SIZE=4]Basic Setup[/SIZE]

To disable anonymous login and to enable local users login and give them write permissions:
```
# No anonymous login
anonymous_enable=NO
# Let local users login
# If you connect from the internet with local users, you should enable TLS/SSL/FTPS
local_enable=YES

# Write permissions
write_enable=YES
```NOTE: It is not advisable to use FTP without TLS/SSL/FTPS over the internet because the FTP protocol does not encrypt passwords. If you do need to transfer files over FTP, consider the use of virtual users (same system users but with non system passwords) or TLS/SSL/FTPS (see below).

[SIZE=4]To chroot users

[/SIZE] To jail/chroot users (not the vsftpd service), there are three choices. Search for "chroot_local_users" on the file and consider one of the following:
```
# 1. All users are jailed by default:
chroot_local_user=YES
chroot_list_enable=NO

# 2. Just some users are jailed:
chroot_local_user=NO
chroot_list_enable=YES
# Create the file /etc/vsftpd.chroot_list with a list of the jailed users.

# 3. Just some users are "free":
chroot_local_user=YES
chroot_list_enable=YES
# Create the file /etc/vsftpd.chroot_list with a list of the "free" users.
```[SIZE=4]To deny (or allow) just some users to login[/SIZE]

To deny some users to login, add the following options in the end of the file:
```
userlist_deny=YES
userlist_file=/etc/vsftpd.denied_users

```In the file /etc/vsftpd.denied_users add the username of the users that **can't** login. One username per line.

To allow just some users to login:```
userlist_deny=NO
userlist_enable=YES
userlist_file=/etc/vsftpd.allowed_users
```In the file /etc/vsftpd.allowed_users add the username of the users that **can** login.

The not allowed users will get an error that they can't login before they type their password.

[SIZE=4]TLS/SSL/FTPS

[/SIZE]NOTE: you definitely have to use this if you connect from the Internet.

To use vsftpd with encryption (it's safer), change or add the following options (some options aren't on the original config file, so add them):
```
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
# Filezilla uses port 21 if you don't set any port
# in Servertype "FTPES - FTP over explicit TLS/SSL"
# Port 990 is the default used for FTPS protocol.
# Uncomment it if you want/have to use port 990.
#listen_port=990

```No need to create a certificate. vstfpd uses the certificate Ubuntu creates upon it's installation, the "snake-oil" certificate (openssl package, installed by default). Please don't be afraid of it's name! :)

Install Filezilla (on the repositories), and use the Servertype "FTPES - FTP over explicit TLS/SSL" option to connect to the server with TLS/SSL/FTPS.

[SIZE=4]Additional Options

[/SIZE] Here are some other available options. The values are examples:
```
# Show hidden files and the "." and ".." folders.
# Useful to not write over hidden files:
force_dot_files=YES

# Hide the info about the owner (user and group) of the files.
hide_ids=YES

# Connection limit for each IP:
max_per_ip=2

# Maximum number of clients:
max_clients=20
```[SIZE=4]
Apply new configuration settings

[/SIZE] Don't forget that to apply new configurations, you must restart the vsftpd service.
```
sudo /etc/init.d/vsftpd restart

```[SIZE=4]Webmin Module

[/SIZE] For those who use webadmin, there is a module for VSFTPD here [http://www.webmin.com/third.html](http://www.webmin.com/third.html).

[SIZE=4]Firewall Problems[/SIZE]

If you find problems when connecting, set pasv_min_port and pasv_max_port in /etc/vsftpd.conf and allow outbound connections in the ports you set in your firewall.
```
pasv_min_port=12000
pasv_max_port=12100
```[SIZE=4]Virtual users with TLS/SSL/FTPS and a common upload directory - Complicated vsftpd

[/SIZE] Virtual users are users that do not exist on the system - they are not in /etc/passwd, do not have a home directory on the system, can not login but in vsftpd - or if they do exist, they can login in vsftpd with a non system password - security.

You can set different definitions to each virtual user, granting to each of these users different permissions. If TLS/SSL/FTPS and virtual users are enabled, the level of security of your vsftpd server is increased: encrypted passwords, with passwords that are not used on the system, and users that can't access directly to their home directory (if you want).

The following example is based and adapted on the [example]("ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.5/EXAMPLE/VIRTUAL_USERS/README") for virtual users in vsftpd site, on documentation and the very good examples in this forum that can be found [here]("http://ubuntuforums.org/showpost.php?p=3497743&postcount=1") and [here]("http://ubuntuforums.org/showpost.php?p=867795&postcount=9").

From the [FAQ]("ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.5/FAQ") in vsftpd site:
> Note - currently there is a restriction that with guest_enable enabled, local
users also get mapped to guest_username.This is a polite way to say that if the default vsftpd PAM file is used, the system users will be guests too. To avoid confusions change the PAM file used by vsftpd to authenticate only virtual users, make all vsftpd users as virtual users and set their passwords, home and permissions based on this example.

[SIZE=3]The workshop[/SIZE]

This is an example for a work directory where various virtual users can save (upload) their work - in this case it will be /home/work, that must be owned by the guest_username (workers). 

Create the system user (workers) and the work directory (/home/work) to be used by the virtual users in vsftpd where they will upload their work in it:
```
# Don't use -m (--create-home) option. This avoids creating a home
# directory based on /etc/skel (.bash* and .profile files).
sudo useradd -d /home/work workers
sudo mkdir /home/work
sudo chown workers /home/work

```Create directories to save the virtual users definitions.
```
sudo mkdir /etc/vsftpd
sudo mkdir /etc/vsftpd/vusers
```Change the PAM authentication in vsftpd.conf and create a new PAM file that uses the pam_userdb module to provide authentication for the virtual users.

If you still didn't do it, make a backup copy of your vsftpd.conf or make a backup copy of the default one (it is a very good starting point and it is very well commented, as I previously wrote).

Edit the default /etc/vsftpd.conf:
```
sudo nano /etc/vsftpd.conf
```Change the line anonymous=YES, uncomment local_enable=YES and change pam_service_name=vsftpd:
```
# Disable anonymous_enable is optional.
anonymous_enable=NO
...
local_enable=YES
...
pam_service_name=ftp

```Then add the TLS/SSL/FTPS definitions (from above) in the end of the file and after it also add:
```
# Enable (only) guests.
guest_enable=YES
# This is not needed, it's the default. Just here for clarity.
guest_username=ftp
# Where the guests (virtual) usernames are set.
user_config_dir=/etc/vsftpd/vusers
```The default settings in vsftpd.conf are restricted just for anonymous user that can download from /home/ftp, are chrooted there and can't upload nor create directories. Virtual users are treated as anonymous users by vsftpd. We have disabled anonymous logins, enabled local_users (virtual users in this case, authenticated by the PAM file we will create) and enabled guests (local users - guests - will be virtual users).

The rest of the options are the default ones, so nobody can upload and because we set guest_enable=YES, if a username exists and have an empty username file, it will be treated as an anonymous user ("ftp" user). We added the TLS/SSL/FTPS so no cleartext passwords are used in the connections.

Now you will override the vsftpd.conf settings for each username individually with files in the directory /etc/vsftpd/vusers wich was set in "user_config_dir=" option. Lets continue.

Create the new file /etc/pam.d/ftp for the new authentication system:
```
sudo nano /etc/pam.d/ftp
```And add the following content:
```
auth required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login
account required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login
```Create a file with the virtual usernames and passwords that can login (one line for username, one line for password and so on for all the users) and call it "logins.txt":
```
mike
password1
sarah
password2
```Install libdb3-util, create the login database with the file logins.txt and restrict permissions to the database:
```
sudo apt-get install libdb3-util
sudo db3_load -T -t hash -f logins.txt /etc/vsftpd/vsftpd_login.db
sudo chmod 600 /etc/vsftpd/vsftpd_login.db
# This is not safe, you should delete this file.
sudo chmod 600 logins.txt
```Create a file for the workers settings (mike and sarah on logins.txt): 
```
sudo nano /etc/vsftpd/workers
```Add the new definitions for this users (remember that virtual users are treated as anonymous users by default on vsftpd, default anonymous settings are set on /etc/vsftpd.conf):
```
write_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
local_root=/home/work
chroot_local_user=YES
dirlist_enable=YES
download_enable=YES
guest_username=workers
```Link this file to the workers usernames in /etc/vsftpd/vusers/, so that any change made at /etc/vsftpd/workers is applied to all workers (after you restart vsftpd).
```
sudo ln -s /etc/vsftpd/workers /etc/vsftpd/vusers/mike
sudo ln -s /etc/vsftpd/workers /etc/vsftpd/vusers/sarah
```If this was suppose to be for web development, you would add this directory in apache, make it an available site and enable it as an enabled website.

Restart vsftpd.

[SIZE=3]System users as a virtual user with non-system password
[/SIZE]
The next example file for one user, like a system user. Add his username and a password - not the system one please, just to be a little bit safer - in logins.txt and repeat the db3_load command. Create a file named after his username inside /etc/vsftpd/vusers/:
```
sudo nano /etc/vsftpd/vusers/user
```And save the following in it:
```
write_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
chroot_local_user=YES
# change /home/user to the actual user home directory.
local_root=/home/user
dirlist_enable=YES
download_enable=YES
guest_username=user
```As you can see, guest_username is important because it will be the user that owns the uploaded files on the directories owned by the guest_username and only files owned by this guest_username can be deleted by him (if you allow it). If you don't set a guest_username, then the "ftp" user will be the used (default in /etc/vsftpd.conf). If you create an empty file of a username present in /etc/vsftpd/vsftpd_login.db (logins.txt), this user will only have the permissions set to anonymous users in /etc/vsftpd.conf, his default home directory will be /home/ftp/ and the owner of the files he uploads (if you allow him and the directory is owned by ftp) will be "ftp".

Only usernames in both /etc/vsftpd/vsftpd_login.db (logins.txt) AND with a file in /etc/vsftpd/vusers/ can login. So, the username can't login if:[INDENT] - If a file exist in /etc/vsftpd/vusers/ but the username is not in /etc/vsftpd/vsftpd_login.db (logins.txt) - you can add filenames that aren't on the database, no harm done.
- If the username is in /etc/vsftpd/vsftpd_login.db (logins.txt) but do not exist in /etc/vsftpd/vusers/ - you can disable logins, just (re)move/rename the file(s) and/or link(s).
[/INDENT]Restart vsftpd.

EDIT1: removed SFTP reference in TLS/SSL/FTPS section
EDIT2: added virtual users configuration.
EDIT3: added allow/deny userlist.

---

### Post by frodon on 2007-08-06
Here is the link of the outdated vsftpd tutorial just for the record :
[http://ubuntuforums.org/showthread.php?t=91887](http://ubuntuforums.org/showthread.php?t=91887)

Thanks for this up to date guide ;)

---

### Post by chadlewis on 2007-08-06
Oh awesome. I spent about two hours yesterday trying to get FTP working on my new vonbox/ubuntu server, with no luck. I'll have to give this a shot tonight and post the results. Thanks!

---

### Post by KubuntuKilledMe on 2007-08-07
I've used vsftpd for 2 years and never had a problem.

---

### Post by motionsiren on 2007-08-07
I enjoy vsftpd but i've been having one hell of time getting it to work with accounts through NIS. Can someone please add to these wonderfully straight forward directions; setting up vsftpd with NIS? I understand it's more about PAM talking to NIS in general but vsftpd is the only app that requires this (for me) as sshd works just fine for me, right out of the box. This is a total bummer. My NIS Master is FreeBSD 6, if that makes any difference.

---

### Post by ruibernardo on 2007-08-08
Thank you all for finding this howto useful. 

I've made it some months ago (in portuguese) just to make the installation of a FTP server for common use in Ubuntu the painless as it can be.

Motionsiren, I've never used PAM and NIS. On vsftpd [FAQ]("ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.5/FAQ") it says:

"If you are not using PAM, then vsftpd will do its own check for a valid user shell in /etc/shells. You may need to disable this if you use an invalid shell to disable logins other than FTP logins. Put check_shell=NO in your /etc/vsftpd.conf."

Don't know if this is helps you in any way. 

I'll be glad to had your findings to the howto. 

The howto is very simple (it was it's objective) and it could be improved with some more functions.

Cheers.

---

### Post by ungluun on 2007-08-09
My vsftpd is running but I can't figure out how I can share specific folders...

I'd like to share these folders:

/media/hda1/HL
/media/sda1/#MP3

How can I do this?

Thanks!

---

### Post by ungluun on 2007-08-09
Is this even possible with vsftpd

---

### Post by ruibernardo on 2007-08-09
> **ungluun said:**
> 
I'd like to share these folders:

/media/hda1/HL
/media/sda1/#MP3

How can I do this?



Hi ungluun,

I suppose you want a "mp3" user for this. If it is, the simplest way to do it is to create a user which its home folder in /media/sda1/MP3:

```
sudo groupadd mp3
sudo useradd -c "FTP mp3" -d /media/sda1/MP3 -g mp3 mp3
```Set his password:

```
sudo passwd mp3
```And restart vsftpd:

```
sudo /etc/init.d/vsftpd restart
```If you have all users chrooted, it will work with no more changes.

Hope this works for you. :)

---

### Post by ungluun on 2007-08-11
Hi,

That solution works only for one folder..

Windows has many ftp servers. In almost all of them you can simply add folders you'd like to share. How is this done in vsftpd?



I'd like to create virtual paths to those folders. So that every user on my ftp can access those directories.
I think I could do this by mounting the dirs (with fstab) under my ftp folder, but that's a weird solution, no? :(

---

### Post by ruibernardo on 2007-08-11
It not *that* odd, I think.

Check the [vsftpd FAQ]("ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.5/FAQ") (2nd question).

It's how vsftpd works with folders outside chroot users folders. As an example here is how to do it:

[http://www.ducea.com/2006/07/27/allowing-ftp-access-to-files-outside-the-home-directory-chroot/](http://www.ducea.com/2006/07/27/allowing-ftp-access-to-files-outside-the-home-directory-chroot/)

I don't know any other way to do it, sorry.

---

### Post by ungluun on 2007-08-12
That approach did the trick :), thanks!

But it leads me to another problem: file permissions

My ftp users are able to upload (write).
But they should only be able to read these folders:
/home/ftp/HL
/home/ftp/#MP3

With my current configuration they are able to delete and write files in the those folders.

I don't won't to chmod 755 these folders because I want still to be able to write in these folders as pc user (not ftp).

How do I solve this problem :confused:

---

### Post by ungluun on 2007-08-12
Or how do I create a user that can only read:
/home/ftp/HL
/home/ftp/#mp3

And another user that can only upload in /home/ftp/upload

:confused:

---

### Post by ruibernardo on 2007-08-12
That should be simple to do. You should enable write permissions to users (all) with:

```
 write_enable=YES
```but disable write permission to anonymous with:

```
 anon_upload_enable=NO
```NOTE: if you DO enable anonymous to write/upload files, you should change the default owner of those files (for security reasons) with:

```
chown_upload=YES
chown_username=some_username_with_write_permission_on_the_directory
```

---

### Post by ruibernardo on 2007-08-12
Another note:

If you want to add certain setting to individual users, create a directory that will have the settings of those users:

```
 sudo mkdir /etc/vsftpd_user_conf
```Edit vsftp configuration file to read that directory:

```
 sudo nano /etc/vsftpd.conf
```and set the user_config_dir variable (non-existent in the default configuration file) to read that directory:

```
 user_config_dir=/etc/vsftpd_user_conf
```Inside the /etc/vsftpd_user_conf directory, create a file named with the username of the "exception" user and set the variables/options that you want him/them to have as exceptions to the default configuration. For various users, various files, each one with different settings if you want.

Don't forget to restart vsftp each time you change its configuration

```
 sudo /etc/init.d/vsftpd restart
```

---

### Post by moon2js on 2007-09-25
Does anyone know a easy way to keep track of your vsftpd, so that I know when people have uploaded files (or connected). Ideally, I'd just like a terminal window showing ftp activity.

---

### Post by ruibernardo on 2007-09-27
Hi moojs,

you can track vsftpd activity on the usual place, in the /var/log/ directory in the vsftpd.log file.

---

### Post by ghostlines on 2008-02-15
i get this error when i try to log in:

ftp: SSL_connect error error:140943FC:SSL routines:SSL3_READ_BYTES:sslv3 alert bad record mac

When i try to connect to from a pc on my lan to my server that's also on my lan it works fine with ssl. I'm using filezilla too. But from outside my lan i get that error.

can anyone help me with this plz?

---

### Post by Mike V on 2008-02-15
I have a problem too, I have like three days trying to set up vsftpd with no little or no success at all, Im trying to do the following:

user anonymous: read several folders, but dont write anything, I will mount the folders like you explained earlier.
my local user: full access to /home/user name

I reached this configuration so far:
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=NO
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=mike
idle_session_timeout=300
data_connection_timeout=120
ftpd_banner=Welcome to Mike's FTP server
chroot_local_user=YES
chroot_list_enable=NO
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
local_root=/home/mike
force_dot_files=YES
hide_ids=YES
max_per_ip=1
max_clients=6
pasv_min_port=1025
pasv_max_port=1125

with this I can connect locally, (ftp localhost) and it works, but right now Im not in my home and I cant access the server,it says connection refused, the connection is working because I can see my page and access to my box via ssh and scp, any advice? Im I doing something wrong?

Thnx in advance folks

---

### Post by stock1232 on 2008-02-17
epimeteo

I followed your howto ftp with vsftpd. When i use filezilla i can log in until i get this 
Response: 425 security: Bad IP Connecting
Error: Failed to retrieve directory listings

Assuming a followed your directions, why would I get this error?

Thanks

---

### Post by blx_286 on 2008-02-22
Thank you for the tutorial. I was wanting to know if you could help further with my setup. I am trying to setup a corporate ftp for project collaboration and this server will not use anonymous logins. I have followed your tutorial and I chose the option to chroot all users and setup virtual users.

This is what I was considering:

ProjectFolder1 - download only folder for multiple client group access
ProjectFolder2 - download only folder for multiple client group access
ClientFolder1 - upload/down folder for specific client
ClientFolder2 - upload/down folder for specific client
Uploads - an uploads only folder for any authorized users

I would like to create 2 system users to administer this box. I would like to know how to give users Admin1 and Admin2 upload/download and add/delete file access to all of these folders?
Also Is there a way to restrict the uploads folder to uploading only without viewing the contents of the folder?

Thanks,
Tim

---

### Post by jdawson on 2008-04-23
Hello, I have followed this tutorial and managed to get vsftpd up and running using FTP over explicit TLS/SSL, however, the third party connecting to it have demanded we use implicit! I cannot find any howtos on the Internet. Could someone please advise? Thank you

---

### Post by ruibernardo on 2008-04-25
Hi jdawson,

did you try

```
listen_port=990
```

in your vsftpd.conf? (I can't test it at the moment)

---

### Post by clayton@a-k-a.net on 2008-04-29
I am fairly new to Linux, though I am computer savvy and technically inclined. I have a lot of experience working with Windows, and have set up many other FTP servers.

Having said that, spending 16-20 hours working to set up "the best" ftp server available for this system is getting ridiculous. To answer the first question, yes I've restarted the service.

I primarily use web browsers to access ftp sites, but I've also installed Filezilla.

For starters, with the initial setup it is my understanding that an anon user can connect to the site to download files only. I have included a file in the directory /home/ftp, but I cannot see it when I access the site via a web browser (FF, IE6, IE7).

Do a little digging, I get told I need to share that folder. So I share it... no success.

Then I decide  it doesn't matter what an anon user can see because I need to secure this site. So I tailor the config file appropriately:
> # Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
# Filezilla uses port 21 if you don't set any port
# in Servertype "FTPES - FTP over explicit TLS/SSL"
# Port 990 is the default used for FTPS protocol.
# Uncomment it if you want/have to use port 990.
listen_port=990
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=yoda
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
ftpd_banner=Welcome to the AKA FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
chroot_list_enable=NO
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
ls_recurse_enable=YES
#
#
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

So I'm at the point now where Filezilla is trying to connect. I have everything set up in there right, server type is ftps, UN/PW etc. The error I'm seeing here is it says the connection is established, initializing TLS, and then it tells me it cannot connect. In the web browser I get the authorization screen to enter a UN/PW combo but it does not recognize ANY users I have on the system.

I'm starting to get the overwhelming feeling the issue is with either the TLS/SSL or it's with the users. It's unfortunate there isn't a simple interface to add and remove users, and designate their home folders. I've added the users to the system, I've shared their /home/(user) folder, I've configured the file (to the best of my ability and knowledge) to allow these users to connect, and yet they cannot.

Any help is appreciated! All I want is an FTP server which I can log into, download and upload files. As a forewarning, in order to help me you cannot just say "create xxxxxx.xxx and then add a user to it" I really need the HOW. A step by step, this is how you configure your server, this is what you type into Terminal, to allow this user to connect from a web browser, without any of the overhead technical jargon.

THANK YOU!

---

### Post by rd341p on 2008-05-02
Hi epimeteo,
To start off, thank you for such a great and well written how-to.
I have followed every step of it and have implemented it as per the how-to, so that I could run a ftp server with vsftpd, ssl and virtual users (also with local users).

I have succeeded to a extent that vsftpd+ssl+localuser work, but with ssl enabled, the virtual users are unable to login :( . If I disable SSL, the same virtual users are able to login in with the password :confused:. I really have no clue :confused: as to why this is happening. The only clue I got from the logs that pam_unix is unable process the username. Here is the error

========= /var/log/auth.log ====================================
May 1 21:46:09 sshd[22941]: Invalid user foobar from 192.168.2.1
May 1 21:46:09 sshd[22941]: Failed none for invalid user foobar from 192.168.2.1 port 1261 ssh2
May 1 21:46:15 i-softwareproducts sshd[22941]: (pam_unix) check pass; user unknown
May 1 21:46:15 i-softwareproducts sshd[22941]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=localhost
================================================== =================

Here is a more info on my install and config:
OS: Ubuntu 7.04
vsftpd: version 2.0.5
installed openssl, ssl-cert and db3-utils

/etc/vsftpd.conf
================
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
#connect_from_port_20=YES
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=YES
idle_session_timeout=600
data_connection_timeout=120
chroot_local_user=YES
ls_recurse_enable=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=ftp
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
force_dot_files=YES
hide_ids=YES
guest_enable=YES
guest_username=virtual
user_config_dir=/etc/vsftpd/vusers

/etc/pam.d/ftp
==============
uth required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login
account required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login

/etc/vsftpd/vusers/foobar
=========================
rite_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
local_root=/home/ftpusers
chroot_local_user=YES
dirlist_enable=YES
download_enable=YES
guest_username=virtual


Please help me resolve this.

Thank You

---

### Post by d.j.schroeder on 2008-05-02
I am in the exact same spot with respect to getting FileZilla to work, that it is it won't with SSL enabled.  GoFTP (another client) will work if I use explicit SSL, if I try and use implicit SSL (regardless of which port the vsftpd server listens to) it will not connect.  I think FileZilla is expecting implicit to work, frankly so was I.  After a few hours of searching I'm thinking that it is not a problem with misconfiguration it is simply that vsftpd doesn't support implicit SSL.

I hope that I'm wrong here and someone can tell me what directives need to be turned on for this to happen.

---

### Post by MAO on 2008-05-30
how to compile [http://workaround.org/articles/ispmail-etch/](http://workaround.org/articles/ispmail-etch/) together and VSFTPd!!!
How to do this:
virtual_users must have access to they folders in virtual_domains>
for excample:
user1
user2
user3
....

domain1
domain2
domain3
....

[ftp://user1.domain1.com](ftp://user1.domain1.com)
[ftp://user1.domain2.com](ftp://user1.domain2.com)
[ftp://user2.domain3.com](ftp://user2.domain3.com)
.....

Like this is this possible? if Yes plz help me how ?

---

### Post by lordfkiller on 2008-06-10
I want only /media/disk-1/FTP to be available over FTP.
I used ```
sudo useradd -d /media/disk-1/FTP ftpuser

``` but after logging in with ftpuser, again many more folders are shown(from / )

Any help is appreciated.

---

### Post by DeaDWiZ on 2008-08-30
Hello, First of all the tutorial is great..It helped me a lot :)

But i have a problem.When i go to download files from another computer i get this error:
```
&#65279;Could not read from transfer socket: ENOBUFS - Out of memory
```

I have free ram so i do not think that is a ram problem..
> $free -m
             total       used       free     shared    buffers     cached
Mem:           503        380        123          0          2         74
-/+ buffers/cache:        303        200
Swap:          321         78        243


---

### Post by devill on 2008-09-16
I've tried to set up vsftpd with a single virtual user, called transfer. It's working almost perfectly: user can upload files, delete files, create directories, delete directories, **BUT** it **can't** *download* files, or *chmod*. Funny, uhh? one would expect problems to happen the other way around :) Although if I chmod the file as a root to have 666 privileges (instead of 600, which is default) than user can download.

I also checked that the file owner is ftp and group is ftp, and the daemon is listening as root, and opens 2 new threads for ftp connection as ftp user.

So... below are my config files, can you tell me what could be the problem?

/etc/vsftpd.conf
```

listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
nopriv_user=ftp
secure_chroot_dir=/var/run/vsftpd
pam_service_name=ftp
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
force_dot_files=YES
guest_enable=YES
guest_username=ftp

```

/etc/vsftpd/vusers/transfer 
```

write_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
local_root=/var/www/ftp.transfer
chroot_local_user=YES
dirlist_enable=YES
download_enable=YES

```

/etc/pam.d/ftp
```

auth required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login
account required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login

```

also 
```
$ls -ld /var/www/ftp.transfer
drwxrwxrwx 3 ftp ftp 4096 Sep 16 16:54 /var/www/ftp.transfer
```

FTP error when downloading is:
550 Failed to open file

distro is Hardy, and so I had to instal version 4.2 instead of libdb3-util.. but I doubt that this could be the problem!

---

### Post by Sid1980 on 2008-10-08
sudo apt-get install libdb3-util  not working :(

any idea Why ??

hardy-heron 

2.6.24-19-server

---

### Post by rickyrockrat on 2008-10-09
It use db4.6-util
I kept getting "unknown user" until I changed my vsftpd.conf file:

pam_service_name=vsftpd
Which has to match the name used in /etc/pam.d. I was migrating my config to a new server and didn't catch that.

Sheesh.

---

### Post by devill on 2008-10-09
> **Sid1980 said:**
> sudo apt-get install libdb3-util  not working :(

any idea Why ??

hardy-heron 

2.6.24-19-server

In Hardy libdb3 is replaced by version 4... search for it in aptitude.

---

### Post by shankhs on 2008-10-10
I am using vsftpd in my PC and use it as a backup place of all my college works(projects , pics etc) everything is running fine but I want to automate the backup process using a shell script...
Does anybody know the detail of the commands that vsftpd prom[t "ftp>"(w/o quotes) take???
Any help would be appreciated.
Thankyou

---

### Post by banditti on 2008-10-10
The libdb doesn't work for me either and I did a search with no results for libdb(anything)-util


Thoughts?

---

### Post by jwg188 on 2008-10-13
Try db4.6-util

---

### Post by WilliamThrilliam on 2009-02-04
I see alot of you are having the same problem I have been having.  I could connect internally, but I could not connect externally.  So, add this nice little piece to your /etc/vsftpd.conf file: 

pasv_enable=YES
pasv_promiscuous=YES
pasv_min_port=50000
pasv_max_port=50100
pasv_address=[your external ip here]

Make sure you foward those pasv_min and max ports from your router.
Make sure you foward ports 20 and 21 from your router.
Make sure "connect_from_port_20=YES" is uncommented (no #).
You don't need "#listen_port=990" so leave it commented.

---

### Post by ralph1973 on 2009-02-08
Hello, thanks for your efforts writing this tutorial. I stuck at certain moment: sudo apt-get install libdb3-util 
This package isn't available in Hardy LTS. Libdb4 has been installed, but there is no /usr/bin/db* executable. How can I solve this? 
Thanks and regards,
Ralph

---

### Post by mahela007 on 2009-03-09
HI. I read the first howto in this thread. 
I connect to the internet via a router. Anything special I have to do because of this? I'm a newbie to this kind of stuff so I'm pretty clueless at this point

---

### Post by solveit on 2009-03-16
I am trying to setup vsftpd as an ftp server to eventually move off-site to make backups to, for additional redundancy.

I am having the some problems connecting using TLSv1. Filezilla connects fine with standard FTP and gives directory listing correctly. Using FTPES it connects and is authenticated but cannot display directory listing. My setup is as follows:

Virgin Media ISP
Motorola surfboard cable modem
Draytek Vigor 2820
Ubuntu Server 8.1 Intrepid Ibex with vsftpd installed and hopefully configured correctly (standard ftp working fine), currently listening on port 21, but I have also tried changing that to 990, with identical results.
XP Pro PC using Filezilla ftp client

I am connecting to the ftp server using a dyndns address and am forwarding ports 21 and 990 to the local IP of the server.

If someone could point me to what I might be doing wrong, opening additional ports on the router maybe? I would be grateful.

Many Thanks in advance for any assistance!
J

LOG:

Status: Resolving address of ftp.XXX.dnsalias.com
Status: Connecting to 82.43.57.XX:21...
Status: Connection established, waiting for welcome message...
Response: 220 WELCOME TO SOLVE-REMOTE1 FTP SERVER
Command: AUTH TLS
Response: 234 Proceed with negotiation.
Status: Initializing TLS...
Status: Verifying certificate...
Command: USER XXXXXXX
Status: TLS/SSL connection established.
Response: 331 Please specify the password.
Command: PASS **********
Response: 230 Login successful.
Command: SYST
Response: 215 UNIX Type: L8
Command: FEAT
Response: 211-Features:
Response: AUTH SSL
Response: AUTH TLS
Response: EPRT
Response: EPSV
Response: MDTM
Response: PASV
Response: PBSZ
Response: PROT
Response: REST STREAM
Response: SIZE
Response: TVFS
Response: UTF8
Response: 211 End
Command: OPTS UTF8 ON
Response: 200 Always in UTF8 mode.
Command: PBSZ 0
Response: 200 PBSZ set to 0.
Command: PROT P
Response: 200 PROT now Private.
Status: Connected
Status: Retrieving directory listing...
Command: PWD
Response: 257 "/data/REMOTE_BACKUPS"
Command: TYPE I
Response: 200 Switching to Binary mode.
Command: PASV
Response: 227 Entering Passive Mode (192,168,0,103,48,124)
Status: Server sent passive reply with unroutable address. Using server address instead.
Command: LIST

---

### Post by ipggi on 2009-04-03
> **ralph1973 said:**
> Hello, thanks for your efforts writing this tutorial. I stuck at certain moment: sudo apt-get install libdb3-util 
This package isn't available in Hardy LTS. Libdb4 has been installed, but there is no /usr/bin/db* executable. How can I solve this? 
Thanks and regards,
Ralph

Try this ...

sudo apt-get install db4.3-util

then ...

sudo db4.3_load etc instead of db3_load

---

### Post by tsultana on 2009-04-22
devill, I have the same problem with the chmod 600 and not being able to download.  I have come up with a workaround for it.  Use the anon_world_readable_only=NO instruction to allow all files to be readable.

I prefer changing the 600 permissions to 660 but this worked for the moment.

Tony

---

### Post by LiQuidAiR on 2009-04-25
This download is for Intel x86 processor Ubuntu computers.

if you wish to use the db3_load you have to download and run the sudo dpkg -i package-name.deb command.

First - go to and download, [http://packages.ubuntu.com/dapper/i386/libdb3/download](http://packages.ubuntu.com/dapper/i386/libdb3/download)

go to the directory where the new file is residing and run sudo dpkg -i libdb3_3.2.9-23_i386.deb.

Follow the on screen instructions.  This should install the necessary library files for the next step.  

Send - go to and download, [http://packages.ubuntu.com/dapper/i386/libdb3-util/download](http://packages.ubuntu.com/dapper/i386/libdb3-util/download)

go to the directory where the new file is residing and run sudo dpkg -i libdb3-util_3.2.9-23_i386.deb

Follow the on screen instructions.  If everything went okay, you now have db3_load.

[B]Note:  Other machine types/versions exist that may suit your needs at [http://packages.ubuntu.com/search?keywords=libdb3](http://packages.ubuntu.com/search?keywords=libdb3)

The above link will provide you a more detailed list and selection of which package types to install.[/B]

---

### Post by robbyburmeister on 2009-04-28
Working with Ubuntu and vsftpd for the first time. Found it easy to configure with system users but that doesn't sound like a secure method. Our users and clients will share the same username and password to access a common directory. Tried setting up a single virtual user but get access denied errors when connecting. Didn't setup TLS/SSL/FTPS because I had problems getting it to work with IE and Windows Explorer. Looking for a secure and easy way to setup users. Please let me know what other information would be useful. Have a deadline of May 1st.

---

### Post by Victormd on 2009-04-29
I've been trying to get vsftpd to work and this is what I've run into... I can access the folder I've setup using FileZilla but when I try to download a file, this is the error I get:
> Status:	Starting download of /myfile
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PASV
Response:	227 Entering Passive Mode (XX,XXX,XXX,XX,XXX,XX - ***this is my server IP address***)
Command:	RETR myfile
Response:	550 Failed to open file.
Error:	Critical error
I used chown to assure the download folder is owned by the user but still no luck. Any suggestions?

---

### Post by robbyburmeister on 2009-04-30
I was able to get vsftp working.  The following document helped in addition to this thread.
[http://linuxforfun.net/2008/04/05/vsftpd-virtual-users/](http://linuxforfun.net/2008/04/05/vsftpd-virtual-users/)

---

### Post by Victormd on 2009-04-30
Thanks! I'll try that later today...

---

### Post by ktritty on 2009-05-06
I am still very new.  I am trying to set up Ubuntu 9.04 server.  I'm stuck at step 1.  I do sudo apt-get install vsftpd and it gives error message "Couldn't find package vsftpd".  Perhaps there is already another ftp package? Perhaps already installed?  All I am trying to do is make it possible for me to get a file from my MacBook onto my server using ftp.  I am clueless how to get files to and from my server as of yet.  I am committed to learning terminal-only administration!  I am also up for hekp setting up samba.  I have bought a few ubuntu books but it is slow to digest.

***
Appended:

Was able to use scp command to do local transfers to/from my MacBook.  Still want to setup ftp though.

Local transfer syntax:
ktritty@macbook$ scp /path/filename [email]serveruser@ip.address.of.server[/email]:/outputpath/filename

This works great; must have ssh services active and proper ssh port open

---

### Post by jmeggers on 2009-05-08
I'm having the same problem.  I checked resolv.conf and I can ping by name, so DNS resolution isn't the issue.  Any suggestions?  I'm relatively new to this, trying to set up server for the first time.

Thanks,
John

---

### Post by LiQuidAiR on 2009-05-10
Most of the serious issues will be because there is something wrong with the vsftpd.conf file and firewall tunneling.  Tunneling simply means, telling the router to let certain ports cross thru or bypass the firewall.  Heck, most routers are even firewalls, they simple hide private addresses from public, but, that's a different story.

ktritty, how did you install Ubuntu Server?  Is it actually on a physical hard drive with dedicated components like motherboard and network card, or is it running with VMWare software?

jmeggers, please post your config file and tell me what type of network setup you have.  DNS shouldn't be the problem.  If you have an IP address to your system you should be able to use that.

I personally ran into several differences in each how to or tutorial I read.  In fact, I haven't found one that actual worked the way they said it should.  This one included.  I figured mine out by using the trial by error method. Sucks :)

---

### Post by kooldino on 2009-07-22
Is there a way to set it up so that you can use the same username as an account on the machine with a different password?

---

### Post by babola on 2009-10-30
Very nice tutorial, thanks!

However...  I want to give real users the ability to log in via ftp AND create some virtual users at the same time. The additional lines in the /etc/pam.d/vsftpd config file...

auth required /lib/security/pam_userdb.so db=/etc/vsftpd_login
account required /lib/security/pam_userdb.so db=/etc/vsftpd_login

...causes access for normal users (those with entries in /etc/passwd) to no longer work. So how can I do both?

Thanks,
B.

---

### Post by roundhay on 2009-11-16
I have tried following this tutorial on 9.10 but I can't get access to the ftp-files folder I created or access using ftp localhost.

I have posted the terminal session from the install and configuration and my /etc/vsftp.conf file, I would be grateful if someone could look at these and let me know what i have done wrong?

Terminal session info:

```
home@server:~$ sudo apt-get install vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  vsftpd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/144kB of archives.
After this operation, 475kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package vsftpd.
(Reading database ... 64489 files and directories currently installed.)
Unpacking vsftpd (from .../vsftpd_2.2.0-1ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up vsftpd (2.2.0-1ubuntu1) ...
update-rc.d: warning: vsftpd stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)
 * Starting FTP server: vsftpd                                                                       [ OK ] 

home@server:~$ sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.original
home@server:~$ sudo nano /etc/vsftpd.conf
home@server:~$ sudo /etc/init.d/vsftpd restart
 * Stopping FTP server: vsftpd                                                                                                                 [ OK ] 
 * Starting FTP server: vsftpd                                                                                                                 [ OK ] 
home@server:~$ sudo useradd -d /home/ftp-files ftp-users
home@server:~$ sudo mkdir /home/ftp-files
home@server:~$ sudo chown ftp-users /home/ftp-files
home@server:~$ sudo mkdir /etc/vsftpd
home@server:~$ sudo mkdir /etc/vsftpd/vusers
home@server:~$ sudo nano /etc/vsftpd.conf
home@server:~$ sudo nano /etc/pam.d/ftp
home@server:~$ sudo nano logins.txt
home@server:~$ sudo apt-get install db4.2-util
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdb4.2
The following NEW packages will be installed
  db4.2-util libdb4.2
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 486kB of archives.
After this operation, 1,266kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com karmic/main libdb4.2 4.2.52+dfsg-5 [416kB]
Get: 2 http://gb.archive.ubuntu.com karmic/universe db4.2-util 4.2.52+dfsg-5 [70.7kB]
Fetched 486kB in 0s (607kB/s)    
Selecting previously deselected package libdb4.2.
(Reading database ... 64542 files and directories currently installed.)
Unpacking libdb4.2 (from .../libdb4.2_4.2.52+dfsg-5_amd64.deb) ...
Selecting previously deselected package db4.2-util.
Unpacking db4.2-util (from .../db4.2-util_4.2.52+dfsg-5_amd64.deb) ...
Setting up libdb4.2 (4.2.52+dfsg-5) ...
Setting up db4.2-util (4.2.52+dfsg-5) ...
home@server:~$ sudo db4.2_load -T -t hash -f logins.txt /etc/vsftpd/vsftpd_login.db
home@server:~$ sudo chmod 600 /etc/vsftpd/vsftpd_login.db
home@server:~$ sudo chmod 600 logins.txt
home@server:~$ sudo nano /etc/vsftpd/ftp-users
home@server:~$ sudo ln -s /etc/vsftpd/workers /etc/vsftpd/vusers/user1
home@server:~$ sudo ln -s /etc/vsftpd/workers /etc/vsftpd/vusers/user2
home@server:~$ sudo ln -s /etc/vsftpd/workers /etc/vsftpd/vusers/user3
home@server:~$ sudo ln -s /etc/vsftpd/workers /etc/vsftpd/vusers/user4
home@server:~$ sudo ln -s /etc/vsftpd/workers /etc/vsftpd/vusers/user5
home@server:~$ sudo ln -s /etc/vsftpd/workers /etc/vsftpd/vusers/user6
home@server:~$ sudo ln -s /etc/vsftpd/workers /etc/vsftpd/vusers/user7
home@server:~$ sudo /etc/init.d/vsftpd restart
 * Stopping FTP server: vsftpd                                                                                                                        No /usr/sbin/vsftpd found running; none killed.
                                                                                                                                               [ OK ]
 * Starting FTP server: vsftpd                                                                                                                 [ OK ] 
home@server:~$ ftp localhost
ftp: connect to address 127.0.0.1: Connection refused
Trying 127.0.0.1...
ftp: connect: Connection refused
ftp> 

``` 

/etc/vsftp.conf file

```
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
#local_umask=022
#anon_upload_enable=YES
#anon_mkdir_write_enable=YES
#dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
#chown_uploads=YES
#chown_username=whoever
#xferlog_file=/var/log/vsftpd.log
#xferlog_std_format=YES
#idle_session_timeout=600
#data_connection_timeout=120
#nopriv_user=ftpsecure
#ftpd_banner=Welcome to blah FTP service.
#deny_email_enable=YES
#banned_email_file=/etc/vsftpd.banned_emails
# chroot_list_enable below.
# chroot_local_user=YES
chroot_local_user=YES
chroot_list_enable=NO
#chroot_list_file=/etc/vsftpd.chroot_list
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
# Filezilla uses port 21 if you don't set any port
# in Servertype "FTPES - FTP over explicit TLS/SSL"
# Port 990 is the default used for FTPS protocol.
# Uncomment it if you want/have to use port 990.
#listen_port=990
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=ftp
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
max_clients=2
hide_ids=YES
guest_enable=YES
guest_username=ftp
user_config_dir=/etc/vsftpd/vusers

```

---

### Post by benkoburger on 2009-11-19
> **roundhay said:**
> I have tried following this tutorial on 9.10 but I can't get access to the ftp-files folder I created or access using ftp localhost.



I've got the same problem here... Any suggestions?

B

---

### Post by DVDPSR on 2009-12-26
Hi guys. I am getting the same problem when I upgraded from 9.04. The server seemed to be running fine before now I don't have access to the ftp folder.:confused:

---

### Post by LiQuidAiR on 2009-12-26
> **DVDPSR said:**
> Hi guys. I am getting the same problem when I upgraded from 9.04. The server seemed to be running fine before now I don't have access to the ftp folder.:confused:

What type of error msgs are you receiving?  What ftp client are you using to connect to vsftpd?

Did you check your log files for errors?  If so, what do they say about the connection attempt?

---

### Post by LiQuidAiR on 2009-12-26
> **roundhay said:**
> I have tried following this tutorial on 9.10 but I can't get access to the ftp-files folder I created or access using ftp localhost.

I have posted the terminal session from the install and configuration and my /etc/vsftp.conf file, I would be grateful if someone could look at these and let me know what i have done wrong?

Terminal session info:

```
home@server:~$ sudo apt-get install vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  vsftpd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/144kB of archives.
After this operation, 475kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package vsftpd.
(Reading database ... 64489 files and directories currently installed.)
Unpacking vsftpd (from .../vsftpd_2.2.0-1ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up vsftpd (2.2.0-1ubuntu1) ...
update-rc.d: warning: vsftpd stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)
 * Starting FTP server: vsftpd                                                                       [ OK ] 

home@server:~$ sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.original
home@server:~$ sudo nano /etc/vsftpd.conf
home@server:~$ sudo /etc/init.d/vsftpd restart
 * Stopping FTP server: vsftpd                                                                                                                 [ OK ] 
 * Starting FTP server: vsftpd                                                                                                                 [ OK ] 
home@server:~$ sudo useradd -d /home/ftp-files ftp-users
home@server:~$ sudo mkdir /home/ftp-files
home@server:~$ sudo chown ftp-users /home/ftp-files
home@server:~$ sudo mkdir /etc/vsftpd
home@server:~$ sudo mkdir /etc/vsftpd/vusers
home@server:~$ sudo nano /etc/vsftpd.conf
home@server:~$ sudo nano /etc/pam.d/ftp
home@server:~$ sudo nano logins.txt
home@server:~$ sudo apt-get install db4.2-util
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdb4.2
The following NEW packages will be installed
  db4.2-util libdb4.2
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 486kB of archives.
After this operation, 1,266kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com karmic/main libdb4.2 4.2.52+dfsg-5 [416kB]
Get: 2 http://gb.archive.ubuntu.com karmic/universe db4.2-util 4.2.52+dfsg-5 [70.7kB]
Fetched 486kB in 0s (607kB/s)    
Selecting previously deselected package libdb4.2.
(Reading database ... 64542 files and directories currently installed.)
Unpacking libdb4.2 (from .../libdb4.2_4.2.52+dfsg-5_amd64.deb) ...
Selecting previously deselected package db4.2-util.
Unpacking db4.2-util (from .../db4.2-util_4.2.52+dfsg-5_amd64.deb) ...
Setting up libdb4.2 (4.2.52+dfsg-5) ...
Setting up db4.2-util (4.2.52+dfsg-5) ...
home@server:~$ sudo db4.2_load -T -t hash -f logins.txt /etc/vsftpd/vsftpd_login.db
home@server:~$ sudo chmod 600 /etc/vsftpd/vsftpd_login.db
home@server:~$ sudo chmod 600 logins.txt
home@server:~$ sudo nano /etc/vsftpd/ftp-users
home@server:~$ sudo ln -s /etc/vsftpd/workers /etc/vsftpd/vusers/user1
home@server:~$ sudo ln -s /etc/vsftpd/workers /etc/vsftpd/vusers/user2
home@server:~$ sudo ln -s /etc/vsftpd/workers /etc/vsftpd/vusers/user3
home@server:~$ sudo ln -s /etc/vsftpd/workers /etc/vsftpd/vusers/user4
home@server:~$ sudo ln -s /etc/vsftpd/workers /etc/vsftpd/vusers/user5
home@server:~$ sudo ln -s /etc/vsftpd/workers /etc/vsftpd/vusers/user6
home@server:~$ sudo ln -s /etc/vsftpd/workers /etc/vsftpd/vusers/user7
home@server:~$ sudo /etc/init.d/vsftpd restart
 * Stopping FTP server: vsftpd                                                                                                                        No /usr/sbin/vsftpd found running; none killed.
                                                                                                                                               [ OK ]
 * Starting FTP server: vsftpd                                                                                                                 [ OK ] 
home@server:~$ ftp localhost
ftp: connect to address 127.0.0.1: Connection refused
Trying 127.0.0.1...
ftp: connect: Connection refused
ftp> 

``` 

/etc/vsftp.conf file

```
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
#local_umask=022
#anon_upload_enable=YES
#anon_mkdir_write_enable=YES
#dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
#chown_uploads=YES
#chown_username=whoever
#xferlog_file=/var/log/vsftpd.log
#xferlog_std_format=YES
#idle_session_timeout=600
#data_connection_timeout=120
#nopriv_user=ftpsecure
#ftpd_banner=Welcome to blah FTP service.
#deny_email_enable=YES
#banned_email_file=/etc/vsftpd.banned_emails
# chroot_list_enable below.
# chroot_local_user=YES
chroot_local_user=YES
chroot_list_enable=NO
#chroot_list_file=/etc/vsftpd.chroot_list
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
# Filezilla uses port 21 if you don't set any port
# in Servertype "FTPES - FTP over explicit TLS/SSL"
# Port 990 is the default used for FTPS protocol.
# Uncomment it if you want/have to use port 990.
#listen_port=990
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=ftp
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
max_clients=2
hide_ids=YES
guest_enable=YES
guest_username=ftp
user_config_dir=/etc/vsftpd/vusers

```

I see one item of concern.  Maybe two...

1. You have SSL enabled.  If you have this type of connection then you have to supply that to using your ftp program.  Doing a simple ftp o 127.0.0.1 to your server is a standard connection protocol (without ssl).

I would make sure the server can accept connections before turning on SSL.

2.  It looks like, once you disable ssl, you will make the connection, but then you won't be able to modify or upload items to the ftp server directory.  I believe this will occur because you are using the guest login type within your .conf file.   The folders where each user has their items stored must be chown VSFTPD USER  (replace VSFTPD USER with actual guest user, ftp in this case).


There is an easier way to assign new users without having to create them in vsftpd virtual user space.  I can help you with that once we figure the first two things out.

---

### Post by tmade on 2010-01-26
Hello,

I´m searching since quite a while for a solution for my vsftp-server.

I´m looking for a way to enable write access just for _one_particualar shared ftp folder, but afterwards the user is not allowed to delete his uploaded file.
So the requirements are:
1. permission to upload
2. no permission to delete uploaded files.

It looks like here are some vsftp-cracks around whith a solution!?

Edit: Also a common linux solution could help to solve my problem!

Thanks
Tom

---

### Post by srynonick on 2010-02-21
hello,

i installed ubuntu 9.10 server, but there's no libdb3-util that I could install? can someone please help me with this? thanks!
(there's no libdbXXX-util, no matter which libdb version)

---

### Post by philavia on 2010-04-26
On Ubuntu 9.10, use db4.7-util instead of libdb3-util.

---

### Post by Happosade on 2010-06-28
Hello and thanks for tutorial.

I've installed and configured vsftpd. It works in localhost, but when I try connect from another server, it just says "connection time out" I belive that my iptables are configured right, but if not, please tell what I have done wrong.

I would like to have also one user, that have access to all others dirs. And other just have their dirs. And dirs should be on RAID (md0) 

VSFTPD config
```
# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
#ftpd_banner=Welcome to blah FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
#
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/vsftpd.pem


# Added, not in default config:

# To get stuff on RAID
user_sub_token=$USER
local_root=/I/don't/yet/know/where/I/should/mount/my/raid/$USER
```IPTABLES
```
# Generated by iptables-save v1.4.2 on Mon Jun 28 11:17:02 2010
*mangle
:PREROUTING ACCEPT [316760:129808118]
:INPUT ACCEPT [265205:125666820]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [129794:34322757]
:POSTROUTING ACCEPT [135197:34641445]
COMMIT
# Completed on Mon Jun 28 11:17:02 2010
# Generated by iptables-save v1.4.2 on Mon Jun 28 11:17:02 2010
*filter
:INPUT ACCEPT [10837:8458197]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [143979:35689269]
:fail2ban-courierauth - [0:0]
:fail2ban-couriersmtp - [0:0]
:fail2ban-postfix - [0:0]
:fail2ban-proftpd - [0:0]
:fail2ban-sasl - [0:0]
:fail2ban-ssh - [0:0]
:fail2ban-ssh-ddos - [0:0]
-A INPUT -p tcp -m multiport --dports 21,20,990,989 -j fail2ban-proftpd 
-A INPUT -p tcp -m multiport --dports 25,465,143,220,993,110,995 -j fail2ban-courierauth 
-A INPUT -p tcp -m multiport --dports 25,465,143,220,993,110,995 -j fail2ban-sasl 
-A INPUT -p tcp -m multiport --dports 25,465 -j fail2ban-postfix 
-A INPUT -p tcp -m multiport --dports 22 -j fail2ban-ssh 
-A INPUT -p tcp -m multiport --dports 25,465 -j fail2ban-couriersmtp 
-A INPUT -p tcp -m multiport --dports 22 -j fail2ban-ssh-ddos 
-A INPUT -s 192.168.101.0/24 -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 21 -j ACCEPT 
-A INPUT -i eth0 -j ACCEPT 
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT 
-A INPUT -p 21 -m conntrack --ctstate NEW -j ACCEPT 
-A INPUT -p tcp -m conntrack --ctstate NEW -m tcp --dport 21 -j ACCEPT 
-A INPUT -p tcp -m conntrack --ctstate NEW -m tcp --dport 22 -j ACCEPT 
-A fail2ban-courierauth -j RETURN 
-A fail2ban-couriersmtp -j RETURN 
-A fail2ban-postfix -j RETURN 
-A fail2ban-proftpd -j RETURN 
-A fail2ban-sasl -j RETURN 
-A fail2ban-ssh -j RETURN 
-A fail2ban-ssh-ddos -j RETURN 
COMMIT
# Completed on Mon Jun 28 11:17:02 2010

```Amn... It seems like fail2ban have left some rules from proftpd testing. Should clean them up. :P

---

### Post by nebileix on 2010-07-25
thks. very nice guide.

---

### Post by duceduc on 2010-08-04
Upon installing vsftpd, I got a unknown instance error when I try to restart the program. I haven't even edit the vsftpd.conf yet.

Where can I check the log for this error? I've looked in the /var/log/vsftpd.log but I don't see any errors.

edited:
I rebooted the server and checked my boot.log. This is the error for vsftpd.
```
init: vsftpd main process (716) terminated with status 1

init: vsftpd main process ended, respawning

init: vsftpd main process (763) terminated with status 1

init: vsftpd main process ended, respawning

init: vsftpd main process (766) terminated with status 1

init: vsftpd main process ended, respawning

init: vsftpd main process (769) terminated with status 1

init: vsftpd main process ended, respawning

init: vsftpd main process (772) terminated with status 1

init: vsftpd main process ended, respawning

init: vsftpd main process (776) terminated with status 1

init: vsftpd main process ended, respawning

init: vsftpd main process (779) terminated with status 1

init: vsftpd main process ended, respawning

init: vsftpd main process (782) terminated with status 1

init: vsftpd main process ended, respawning

init: vsftpd main process (785) terminated with status 1

init: vsftpd main process ended, respawning

init: vsftpd main process (788) terminated with status 1

init: vsftpd main process ended, respawning

init: vsftpd main process (791) terminated with status 1

init: vsftpd respawning too fast, stopped
```

When I try to start vsftpd with this cmd.
```
sudo service vsftpd start
```
I get this error.
```
start: unknown instance
```
If I try with this cmd.
```
start vsftpd
```
I get this error.
```
start: Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory.
```

I have been troubleshooting this for a couple of days now; I still can't figure out why the dbus error. I need to get this working as I have several websites I wished to make changes to when I am out of my network. Help please.

---

### Post by duceduc on 2010-08-06
I finally got the vsftpd connected. I am able to connect, log in, browse the folders. I followed the howto using the exact permission for the users as shown in the fist post.
```
write_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
local_root=/home/work
chroot_local_user=YES
dirlist_enable=YES
download_enable=YES
guest_username=workers
```

Here is what I can do:
rename files 
upload files
upload empty folders
delete files

Here is what I cannot do:
delete folders
upload folders with files inside.

How can I grant these permissions? The code above seems to be correct but I can't do what I want it to do.

Thanks for your help.

---

### Post by duceduc on 2010-08-23
Anyone reading this can help with my problem above this post? I don't know what else to look for for my permission deny error.
Here is my vsftpd.conf
```
# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Disabled by default)
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# If enabled, vsftpd will display directory listings with the time
# in  your  local  time  zone.  The default is to display GMT. The
# times returned by the MDTM FTP command are also affected by this
# option.
use_localtime=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
ftpd_banner=Welcome FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=ftp
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/private/vsftpd.pem
#
#
ssl_enable=NO
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
#
# Enable (only) guests.
guest_enable=YES
# This is not needed, it's the default.
guest_username=ftp
# Where the guests (virtual) username are set.
user_config_dir=/etc/vsftpd/vusers

```

---

### Post by duceduc on 2010-09-03
I finally got vsftpd to work. I am able to log in and edit files. My issue was that I needed to add this line to vsftpd.conf
> virtual_use_local_privs=YES

I have another question. I use Filezilla client to transfer files. I also have several subdomains I host on this server. Right now, I can use any one of my domains to connect to vsftp by fixing ftpes://. How can I just have one ftp address setup to login to the vsftp server?

---

### Post by 19657 on 2010-09-11
Hi,
I am trying to build here a media server.
Ubuntu 10.4
installed vsftpd as explained. I was using dual boot, but removed completely windows, so I have installed Storage Device manager to map the ntfs data I had already, where vsftpd has one link to the folder in use.
I installed also nfs-server.

Now, Id like to move this desktop to a non monitor/keyb configuration, so I was trying the RealVNC, but I need to be logged on to be able to run this.

So the other way was, ok so I will have the machine with auto-login.. but for some reason the default user is not possible to do this... so I created another user.. it logs in auto, but now my ftp service seems not to be running...  so I tried to login to ftp server while in the login screen and I found out that I can not log in to ftp. So I really need to login with a special user (admin) to be able to run ftp etc..?

The message I get when login (and ubuntu in login screen) ftp connects asks password.. I provide password and it freezes...

Ideas? I am rookie with Linux but for years I am trying to give it a try... several attempts done but I always run through minor problems that I can not overcome....

Help needed please....

What I need is: have this machine working no monitor/keyb.. be able to loging remotely for maintenance etc... and have ftp server and nfs server running... IS THIS POSSIBLE???

Thx

---

### Post by echelon-iv on 2010-09-11
hi,
i set up vsftpd on an ubuntu 10.04 server. i have edited the config file to allow anonymous users. they should be able to transfer files and create directories. 
i have tried connecting to the server with multiple ftp clients. it takes using active mode, and then it connects. but once connecting there are errors when i try to send files.

can anyone help?

---

### Post by dragao-azul on 2010-10-01
Hey,

I'm having 2 problems here:
1 - When I enable ssl I can't login to the server (I'm using fireftp to connect, a firefox add on and I choose an encryption connection). Does anyone know why this happens?

2 - When I create a folder or files with a virtual user that is not also a system user I can't see it's contents although I can upload stuff in it. (This is a permissions problem, how do I make it right?)

I've also created [this]("http://ubuntuforums.org/showthread.php?p=9912111") topic but have had no luck so far.

thz in advance

;)

---

### Post by Glandoux on 2010-10-24
> **duceduc said:**
> Upon installing vsftpd, I got a unknown instance error when I try to restart the program. I haven't even edit the vsftpd.conf yet.
 
Where can I check the log for this error? I've looked in the /var/log/vsftpd.log but I don't see any errors.
 
edited:
I rebooted the server and checked my boot.log. This is the error for vsftpd.
```
init: vsftpd main process (716) terminated with status 1
 
init: vsftpd main process ended, respawning
 
init: vsftpd main process (763) terminated with status 1
 
init: vsftpd main process ended, respawning
 
init: vsftpd main process (766) terminated with status 1
 
init: vsftpd main process ended, respawning
 
init: vsftpd main process (769) terminated with status 1
 
init: vsftpd main process ended, respawning
 
init: vsftpd main process (772) terminated with status 1
 
init: vsftpd main process ended, respawning
 
init: vsftpd main process (776) terminated with status 1
 
init: vsftpd main process ended, respawning
 
init: vsftpd main process (779) terminated with status 1
 
init: vsftpd main process ended, respawning
 
init: vsftpd main process (782) terminated with status 1
 
init: vsftpd main process ended, respawning
 
init: vsftpd main process (785) terminated with status 1
 
init: vsftpd main process ended, respawning
 
init: vsftpd main process (788) terminated with status 1
 
init: vsftpd main process ended, respawning
 
init: vsftpd main process (791) terminated with status 1
 
init: vsftpd respawning too fast, stopped
```
 
When I try to start vsftpd with this cmd.
```
sudo service vsftpd start
```
I get this error.
```
start: unknown instance
```
If I try with this cmd.
```
start vsftpd
```
I get this error.
```
start: Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory.
```
 
I have been troubleshooting this for a couple of days now; I still can't figure out why the dbus error. I need to get this working as I have several websites I wished to make changes to when I am out of my network. Help please.
 
What did you do to fix this error?? I have the same error and i can't find a solution...
thanks,

---

### Post by Glandoux on 2010-10-24
Ok, i found the problem.
Now my ftp works with virtual users.
 
Why it wasn't working? It's because i was trying to use SSL.
So if i set this option in vsftpd.conf : ssl_enable=YES, my ftp server won't start, and i get this error :  init: vsftpd main process (2692) terminated with status 1
                       init: vsftpd respawning too fast, stopped
 
So now i have a new problem, can't work with ssl.
 
Any idea?
 
thanks,

---

### Post by wconstantine on 2010-10-25
I've set up virtual users. The home dir for them should be /media/truecrypt1. I've mounted an encrypted partition that I want the FTP users to gain access to. I've added my own system user to the workers group and I'm now trying to change the group permissions on /media/truecrypt1.

Anything I throw at it doesn't work. E.g:

> wh1sk3yj4ck@valkyrie:/media$ ls -l
total 44
drwx------ 1 wh1sk3yj4ck wh1sk3yj4ck 40960 2010-10-21 20:38 truecrypt1
drwxr-xr-x 6 wh1sk3yj4ck workers      4096 2010-10-21 20:32 truecrypt2
wh1sk3yj4ck@valkyrie:/media$ sudo chgrp -R workers truecrypt1
wh1sk3yj4ck@valkyrie:/media$ ls -l
total 44
drwx------ 1 wh1sk3yj4ck wh1sk3yj4ck 40960 2010-10-21 20:38 truecrypt1
drwxr-xr-x 6 wh1sk3yj4ck workers      4096 2010-10-21 20:32 truecrypt2
wh1sk3yj4ck@valkyrie:/media$ 


Wth? The other volume worked just fine.

---

### Post by live4fun on 2010-11-11
I am new to vsftp. Thanks for the guidance this howto provides.

But as life is never that easy i have some questions :)

The FTPS setup in the first post mentions those options for the vsftpd.conf
```

ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES

```

I was looking at the man page in parallel to verify what i am doing and couldn't find those listed. (Perhaps those changed over time?)

There is an option ssl_ciphers which seems like an adequate replacement to choose allowed encryption algorithms.

But I am not a 100% confident which are considered to be safe these days. I found a post on another forum [here]("http://www.linuxquestions.org/questions/linux-security-4/openssl-certificate-generation-question-aes-670297/#post3284594") suggesting this setup

```
ssl_ciphers=ADH-AES256-SHA:DHE-RSA-AES256-SHA:DHE-DSS-AES256-SHA:AES256-SHA
```

Could anybody with a profound security background tell me if it is wise/safe to choose those options?

Thanks guys for the effort you put into this forum!

---

### Post by al_mic on 2010-11-29
Hi,

Is it possible to have in VSFTPD same username for login to more that one domain?

Example: I want to create the user "test" for domain mydomain.com
And then I what to create the user "test" for domain yourdomain.com

And both mydomain.com and yourdomain.com point to the same VSFTPD server that has only one public IP address.

Is it possible to make VSFTPD know which user tries to log in from the two and place it in his correct home directory?

For example if I try to user for login the username: [email]test@mydomain.com[/email]
And for a different login to use [email]test@yourdomain.com[/email]

How can I do this in VSFTPD?

Can you please tell me.

Thank you.

---

### Post by mordriel on 2010-12-03
Hi there.  
     So, I've got vsftpd working.  ...  Mostly.  When I try to connect through FileZilla using ServerType and FTPES, I get "PASS" for my connection with the password and whatnot... but then it spits this out:  

GnuTLS error -8: A record packet with illegal version was received.

Has anyone ever had a similar issue, or know what it's about?  I'm rather lost...

Thanks!

---

### Post by nebileix on 2010-12-20
> **mordriel said:**
> Hi there.  
     So, I've got vsftpd working.  ...  Mostly.  When I try to connect through FileZilla using ServerType and FTPES, I get "PASS" for my connection with the password and whatnot... but then it spits this out:  

GnuTLS error -8: A record packet with illegal version was received.

Has anyone ever had a similar issue, or know what it's about?  I'm rather lost...

Thanks!

Got that error sometime back too. Cant recall how i fixed it.

Maybe u can start with those customized setting that u had on ur vsftpd.conf so as to troubleshoot easier.

Start by commenting out those customized settings... Thats how I solve the issue.

PS: Remember not to post sensitive information.

---

### Post by karthick87 on 2010-12-24
These are my settings,how ever when i type [ftp://127.0.0.1](ftp://127.0.0.1) in browser i am taken to /home/karthick instead of /srv/ftp why??
```
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=karthick
ftpd_banner=Welcome to FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/srv/ftp
```

---

### Post by nebileix on 2010-12-26
if im not wrong, karthick is a user in the system right? and when u log, do u see something like [SSL Cipher ##########]?

---

### Post by karthick87 on 2010-12-26
No i dont see such things.

---

### Post by nebileix on 2010-12-27
> **nebileix said:**
> if im not wrong, [COLOR="Blue"]karthick is a user in the system right?[/COLOR] and when u log, do u see something like [SSL Cipher ##########]?

How about that above?

---

### Post by karthick87 on 2010-12-27
Yes i am the user..

---

### Post by nebileix on 2010-12-27
That is why u are at ur home directory once u are log into the ftp. Pls refer to the option on how to configure vsftpd from here.

[http://vsftpd.beasts.org/vsftpd_conf.html]("http://vsftpd.beasts.org/vsftpd_conf.html")

---

### Post by duceduc on 2010-12-31
I've got vstpd setup it is working fairly well. I am using filezilla to upload files. I would also like to use Dreamweaver to connect to my server. What are the settings for that?

In Filezilla, my login info is

ftpes://domain.com
username: *****
password: *****

When I input those lines in dreamweaver's settings, it throws out an error. Am I suppose to configure something else in the server to be able to connect via dreamweaver?

---

### Post by dkozhukhar on 2011-01-14
It was pretty hard to tackle out all setups, but it works. Thanks for guide! :popcorn:

---

### Post by alfamuzjak on 2011-01-23
Can someone help me with firewalling vsftpd with iptables?(ports 21,20;anonymous upload,download..).
How i can cover all that???

---

### Post by alfamuzjak on 2011-01-24
> **alfamuzjak said:**
> can someone help me with firewalling vsftpd with iptables?(ports 21,20;anonymous upload,download..).
How i can cover all that???

any idea?!

---

### Post by czerdrill on 2011-03-30
I'm trying to chroot my users, and my conf settings seem to be correct, however in Filezilla they are able to navigate all the way to the root folder, so clearly I'm missing some configuration option somehwere.  Can anyone help me with this?

---

### Post by skaramanger on 2011-10-12
First off thanks for this howto.
I have gotten to the point of trying to create database files:

I have Maverick 10.10 installed and have libdb4.8 libraries but no libdb4.8-utils and not dbxx_load command.  I get a command not found error and my searches for the command dbxxx_load come up empty.  This must have been changed.  What pkg do I need to down load or is there a different command used?

Thanks

---

### Post by alfamuzjak on 2011-10-13
In my case...previous month i used db4.7-util or 4,8 on ubuntu 10.10, use:
```
sudo apt-get install db4.7-util
``` for instaling and
```
sudo db4.7_load -T -t hash -f ...
``` for loading, generating...

---

### Post by skaramanger on 2011-10-13
alfamuzjak

Thanks for your reply.

> **alfamuzjak said:**
> In my case...previous month i used db4.7-util or 4,8 on ubuntu 10.10, use:
```
sudo apt-get install db4.7-util
``` for instaling and
```
sudo db4.7_load -T -t hash -f ...
``` for loading, generating...

Yes I did find and install db4.8-util.  I have the vsftpd up but my virtual users can't log in. I'm going to make a complete post of my config in momentarily.

Regards,

---

### Post by skaramanger on 2011-10-13
I am now testing vsftpd.  I have done this by either running it as a service or from the command line:

```
sudo vsftpd
```

I can connect to the host, but am unable to log in using my virtual user.  I have included my configuration files below:
/etc/vsftpd
```
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd.virtual
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/vsftpd/vsftpd.pem
# This option specifies the location of the RSA key file to use for SSL
# encrypted connections.
# rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
# 
# Mods from: http://ubuntuforums.org/showthread.php?p=3138955
#
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
# Filezilla uses port 21 if you don't set any port
# in Servertype "FTPES - FTP over explicit TLS/SSL"
# Port 990 is the default used for FTPS protocol.
# Uncomment it if you want/have to use port 990.
# listen_port=990
# Show hidden files and the "." and ".." folders.
# Useful to not write over hidden files:
force_dot_files=YES
# Hide the info about the owner (user and group) of the files.
hide_ids=YES
# Connection limit for each IP:
max_per_ip=2
# Maximum number of clients:
max_clients=2
#
# Enable (only) guests.
guest_enable=YES
# This is not needed, it's the default. Just here for clarity.
guest_username=ftp
# Where the guests (virtual) usernames are set.
user_config_dir=/etc/vsftpd/vusers
pasv_min_port=12000
pasv_max_port=12100
#check_shell=NO

```

Now for the vsftpd.pem file that I created using:

```

# cd /etc/vsftpd/
# /usr/bin/openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout vsftpd.pem -out vsftpd.pem

```

Apparently, under maverick there is no snakeoil.pem file just a key file:

```

#sudo ls -l /etc/ssl/private/
total 4
-rw-r----- 1 root ssl-cert 887 2009-12-16 10:21 ssl-cert-snakeoil.key

```

/etc/pam.d/vsftpd.virtual (it didn't work named ftp either)

```

auth required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login
account required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login
# session    required     /lib/security/pam_loginuid.so

```

/etc/vsftpd/workers:

```
write_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
local_root=/home/work/$USER
chroot_local_user=YES
dirlist_enable=YES
download_enable=YES
guest_username=workers

```

/etc/vsftpd/vusers/BossHog
```
write_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
chroot_local_user=YES
# change /home/user to the actual user home directory.
local_root=/home/work/BossHog
dirlist_enable=YES
download_enable=YES
guest_username=user

```

```
ls -lR /etc/vsftpd
/etc/vsftpd:
total 24
-rw------- 1 root root 12288 2011-10-12 21:53 vsftpd_login.db
-rw-r--r-- 1 root root  2319 2011-10-12 23:07 vsftpd.pem
drwxr-xr-x 2 root root  4096 2011-10-13 13:34 vusers
-rw-r--r-- 1 root root   208 2011-10-13 12:29 workers

/etc/vsftpd/vusers:
total 4
-rw-r--r-- 1 root root 262 2011-10-13 01:00 BossHog
lrwxrwxrwx 1 root root  19 2011-10-12 21:06 Brian -> /etc/vsftpd/workers

```

```

ls -l /etc/pam.d/vsftpd*
-rw-r--r-- 1 root root 321 2011-10-12 23:52 /etc/pam.d/vsftpd
-rw-r--r-- 1 root root 143 2011-10-13 13:56 /etc/pam.d/vsftpd.virtual

```

Currently, I get this ssl error message when try to connect:

ssl_getc: SSL_read failed -1 = 0
421 service not available, removte server has closed connection
login failed

---

### Post by skaramanger on 2011-10-13
I am now testing vsftpd.  I have done this by either running it as a service or from the command line:

```
sudo vsftpd
```

I can connect to the host, but am unable to log in using my virtual user.  I have included my configuration files below:
/etc/vsftpd
```
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd.virtual
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/vsftpd/vsftpd.pem
# This option specifies the location of the RSA key file to use for SSL
# encrypted connections.
# rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
# 
# Mods from: http://ubuntuforums.org/showthread.php?p=3138955
#
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
# Filezilla uses port 21 if you don't set any port
# in Servertype "FTPES - FTP over explicit TLS/SSL"
# Port 990 is the default used for FTPS protocol.
# Uncomment it if you want/have to use port 990.
# listen_port=990
# Show hidden files and the "." and ".." folders.
# Useful to not write over hidden files:
force_dot_files=YES
# Hide the info about the owner (user and group) of the files.
hide_ids=YES
# Connection limit for each IP:
max_per_ip=2
# Maximum number of clients:
max_clients=2
#
# Enable (only) guests.
guest_enable=YES
# This is not needed, it's the default. Just here for clarity.
guest_username=ftp
# Where the guests (virtual) usernames are set.
user_config_dir=/etc/vsftpd/vusers
pasv_min_port=12000
pasv_max_port=12100
#check_shell=NO

```

Now for the vsftpd.pem file that I created using:

```

# cd /etc/vsftpd/
# /usr/bin/openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout vsftpd.pem -out vsftpd.pem

```

Apparently, under maverick there is no snakeoil.pem file just a key file:

```

#sudo ls -l /etc/ssl/private/
total 4
-rw-r----- 1 root ssl-cert 887 2009-12-16 10:21 ssl-cert-snakeoil.key

```

/etc/pam.d/vsftpd.virtual (it didn't work named ftp either)

```

auth required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login
account required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login
# session    required     /lib/security/pam_loginuid.so

```

/etc/vsftpd/workers:

```
write_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
local_root=/home/work/$USER
chroot_local_user=YES
dirlist_enable=YES
download_enable=YES
guest_username=workers

```

I removed $USER.  Now I login with user Brian! yeah. and mkdir now time to work on other bugaboos

/etc/vsftpd/vusers/BossHog
```
write_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
chroot_local_user=YES
# change /home/user to the actual user home directory.
local_root=/home/work/BossHog
dirlist_enable=YES
download_enable=YES
guest_username=user

```

oops above needs corrected.

```
ls -lR /etc/vsftpd
/etc/vsftpd:
total 24
-rw------- 1 root root 12288 2011-10-12 21:53 vsftpd_login.db
-rw-r--r-- 1 root root  2319 2011-10-12 23:07 vsftpd.pem
drwxr-xr-x 2 root root  4096 2011-10-13 13:34 vusers
-rw-r--r-- 1 root root   208 2011-10-13 12:29 workers

/etc/vsftpd/vusers:
total 4
-rw-r--r-- 1 root root 262 2011-10-13 01:00 BossHog
lrwxrwxrwx 1 root root  19 2011-10-12 21:06 Brian -> /etc/vsftpd/workers

```

```

ls -l /etc/pam.d/vsftpd*
-rw-r--r-- 1 root root 321 2011-10-12 23:52 /etc/pam.d/vsftpd
-rw-r--r-- 1 root root 143 2011-10-13 13:56 /etc/pam.d/vsftpd.virtual

```

Currently, I get this ssl error message when try to connect:

ssl_getc: SSL_read failed -1 = 0
421 service not available, removte server has closed connection
login failed

---

### Post by alfamuzjak on 2011-10-14
Hi, i can help you with virtual users by posting my whole steps of configuring... 
I had same problems, and most of all are because of outdated and in most cases not complete quides. I also had problem with snakeoil and ssl, so i didnt do that because i had little time and i had to finish it because that was part of my specialization work for school.

I can't remebmer where i was stucked with snakeoil and ssl, but if u succeed with that part pls let me how u do that.

---

### Post by skaramanger on 2011-10-14
alfamuzjak,

I currently have a semi working setup. However, I can connect from my dyndns domain name, but get error messages regarding a bad (local) ip address being passed back or a failed to get certificate message especially in passive mode.  So I'm curious as to how you got your setup to work from the internet?  What should I change in the vsftpd.conf file?  I'll include the latest below:

```
# Current config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Disabled by default)
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
virtual_use_local_privs=YES
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# If enabled, vsftpd will display directory listings with the time
# in  your  local  time  zone.  The default is to display GMT. The
# times returned by the MDTM FTP command are also affected by this
# option.
use_localtime=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
# xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
ftpd_banner=Welcome to Tz FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
#chroot_local_user=YES
#chroot_list_enable=NO
##
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd.virtual
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/vsftpd/vsftpd.pem
# This option specifies the location of the RSA key file to use for SSL
# encrypted connections.
# rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
# 
# Mods from: http://ubuntuforums.org/showthread.php?p=3138955
#
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
# Filezilla uses port 21 if you don't set any port
# in Servertype "FTPES - FTP over explicit TLS/SSL"
# Port 990 is the default used for FTPS protocol.
# Uncomment it if you want/have to use port 990.
# listen_port=990
listen_port=10021
# Show hidden files and the "." and ".." folders.
# Useful to not write over hidden files:
force_dot_files=YES
# Hide the info about the owner (user and group) of the files.
hide_ids=YES
# Connection limit for each IP:
max_per_ip=2
# Maximum number of clients:
max_clients=10
#
# Enable (only) guests.
guest_enable=YES
# This is not needed, it's the default. Just here for clarity.
guest_username=ftp
# Where the guests (virtual) usernames are set.
user_config_dir=/etc/vsftpd/vusers
pasv_min_port=12000
pasv_max_port=12100
#check_shell=NO
debug_ssl=YES
log_ftp_protocol=YES


```

Regards

---

### Post by skaramanger on 2011-10-14
alfamuzjak,

I got it working now.  I added:
```
pasv_promiscuous=YES
```
to the vsftpd.conf file.  Connected my virtual user and
```

ftp> binary
ftp> passive

```
and was able to do what I needed to do. Whew! :D

Thanks again for your replies.

Regards


> **alfamuzjak said:**
> Hi, i can help you with virtual users by posting my whole steps of configuring... 
I had same problems, and most of all are because of outdated and in most cases not complete quides. I also had problem with snakeoil and ssl, so i didnt do that because i had little time and i had to finish it because that was part of my specialization work for school.

I can't remebmer where i was stucked with snakeoil and ssl, but if u succeed with that part pls let me how u do that.

---

### Post by Flerpje on 2011-10-28
I've tried everything to set up my own vsftpd server as well, but i can't get SSL to work. Which is imperative, because some users will prbably be logging in over the internet.

When i try to connect to my server i get an ECONNREFUSED error. Disabling SSL entirely in my config file resolves the problem, so it's definitely SSL related. 

I'm using the latest (windows) Filezilla to connect to my server (locally) and my ports are all forwarded.

Here is my .conf file: (note that SSL is currently disabled)
```
listen=YES
#listen_ipv6=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
#local_umask=022
#anon_upload_enable=YES
#anon_mkdir_write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
#chown_uploads=YES
#chown_username=whoever
vsftpd_log_file=/var/log/vsftpd.log
log_ftp_protocol=YES
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=YES
#idle_session_timeout=600
#data_connection_timeout=120
#nopriv_user=ftpsecure
#async_abor_enable=YES
#ascii_upload_enable=YES
#ascii_download_enable=YES

ftpd_banner=GOOD LORD IT'S A CHEESEBURGER! A DOUBLE!

#deny_email_enable=YES
#banned_email_file=/etc/vsftpd.banned_emails

chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list

userlist_deny=NO
userlist_enable=YES
userlist_file=/etc/vsftpd.allowed_users

#ssl_enable=YES
#allow_anon_ssl=NO
#force_local_data_ssl=YES
#force_local_logins_ssl=YES
#ssl_tlsv1=YES
#ssl_sslv2=YES
#ssl_sslv3=YES
#rsa_cert_file=/etc/ssl/private/ssl-cert-snakeoil.key
#rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

# Filezilla uses port 21 if you don't set any port
# in Servertype "FTPES - FTP over explicit TLS/SSL"
# Port 990 is the default used for FTPS protocol.
# Uncomment it if you want/have to use port 990.
#listen_port=990

# Show hidden files and the "." and ".." folders.
# Useful to not write over hidden files:
force_dot_files=YES

# Hide the info about the owner (user and group) of the files.
hide_ids=YES

# Connection limit for each IP:
max_per_ip=4

# Maximum number of clients:
max_clients=10

#ls_recurse_enable=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem

pasv_min_port=15000
pasv_max_port=15000

```

Can anyone help me with this? I've tried looking up my log files, but they all appear to be either empty, are just not reporting something useful. Can anyone help? Thanks in advance!

---

### Post by nhutto on 2011-11-03
I have set up basic vsftpd servers with ubuntu plenty in the past however I can not get it running on my system after i upgraded from 11.04 to 11.10 my log shows successful logins on the day before I upgraded then the next day nothing I can't get in. I have removed vsftpd and conf and reinstalled it but I still can't login. i get a 530 error. any Idea I am not using ssl. what could have changed in the upgrade that would cause this?

---

### Post by chrismyers on 2011-11-06
I apologize for being off-topic but it makes me smile that the title for this thread is "Easy FTP with vsftpd" & we have 10 pages of responses so far :-k

P.S. I'm not knocking anyone. I do love the Ubuntu community. :P

---

### Post by whoop on 2011-11-15
Is this possible: vsftpd+virtual users+ssl?

This works for me: vsftpd+virtual users
This wprks for me: vsftpd+ssl+normal users
I can't seem to combine them...

So has anybody got vsftpd+virtual users+ssl running?

---

### Post by duceduc on 2012-02-14
I have setup ubuntu server (11.10) which differs in regards to installing vsftpd as compared to 10.4. I copied all the settings from my 10.4 to 11.10 but was having connection issue when I use Filezilla. 

If you are getting this error
> GnuTLS error -12: A TLS fatal alert has been received. Could not connect to server

Add this line to your vsftpd.conf file. restart. It should connect.
> ssl_ciphers=AES128-SHA or ssl_ciphers=HIGH

---

### Post by duceduc on 2012-02-14
I thought I had it fix since my last post above, but I still can't log in via vsftpd. It says 'login incorrect'. Either the password or username is not set correctly. I am using filezilla.

I have rerun the db4.7_load to create another vsftpd_login.db. It still say the login is not correct. It has to be some setting within vsftpd. Need help.

---

### Post by duceduc on 2012-02-14
Ok. I got it to semi-work now. I can log in ftp but not ftpes. It seems now I cannot log in via ssl connection. The connection times out.

I would also like to add that, ssl connection works if I disable shorewall. I have open ports 20,21 in shorewall but it still doesn't work unless I disable it.

---

### Post by duceduc on 2012-02-15
> **duceduc said:**
> Ok. I got it to semi-work now. I can log in ftp but not ftpes. It seems now I cannot log in via ssl connection. The connection times out.

I would also like to add that, ssl connection works if I disable shorewall. I have open ports 20,21 in shorewall but it still doesn't work unless I disable it.

I got it working now. See [this thread](http://ubuntuforums.org/showthread.php?t=1925301).

---

### Post by gadelkareem on 2012-03-17
Another way to do that: [Configuring vsFTPd on CentOS with different port]("http://gadelkareem.com/2012/02/27/configuring-vsftpd-on-centos-with-different-port/")

---

### Post by Shutterstrom on 2012-05-01
Hi, this is my first attempt to Linux and I'm trying to set up VSFTPD on my Ubuntu 11.10 server (64 bit)

What I'm looking for is a way to have an ftp user that can only view and download files from my folder called download under /share/download

I would like to have a named user (username and password) to access this folder and this folder only. Going higher in the treeview (/share) should not be possible.

However this should only affect the ftp user. If I log on via ssh to my server I should be able to go where I want to.

I have dissabled upload.
I have dissabled annonumus login.
I have set the local_root to /share/upload

Since I'm a bit new I used this guide if you have any more questions on how I did: [http://cviorel.easyblog.ro/2009/03/05/how-to-setup-vsftpd-ftp-on-ubuntu-linux/](http://cviorel.easyblog.ro/2009/03/05/how-to-setup-vsftpd-ftp-on-ubuntu-linux/)

But user can still brows arround on the ftp server and see all my files. How do I restrict them to this folder only? (/share/download)

BR
/Henrik

---

### Post by resting on 2012-05-07
```
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
# Filezilla uses port 21 if you don't set any port
# in Servertype "FTPES - FTP over explicit TLS/SSL"
# Port 990 is the default used for FTPS protocol.
# Uncomment it if you want/have to use port 990.
#listen_port=990
```

Are these necessary if I configure my client (Filezilla) to connect using SFTP instead?
Because apparently I could still connect even when I stopped VSFTPD service.
I'm assuming Ubuntu SSH is by default encrypted with snake oil certificate?

---

### Post by teosbpl on 2012-05-08
Most probably you have an error in config file. Comment all and start adding line by line.

---

### Post by Return Privacy on 2012-06-04
epimeteo,
I'm new to ftp servers, and Ubuntu. I got vsftpd to install and setup with your tutorial. I am just a little confused on how to configure the users part. All I need to do is setup 2 specific users that I want to allow to login and send (upload) files to vsftpd. These will be from 2 computers on my home network only, nothing from outside the home. And I need to specify 1 particular folder for both to send the files to vsftpd on the Ubuntu computer. Actually, I want the folder to be on the 2nd drive in the Ubuntu computer, it is: /media/Drive2/FTP. I want to restrict the 2 specified users that can login and send files to vsftpd on Ubuntu to only be able to see or connect to this second drive, and the folder named FTP. I don't want to allow anonymous users to login. 
Can you please explain how to do this? I'm thinking that you mean that I have to create a new file to list the new users and their passwords, and the specific drive/folder they can upload to?
Thanks in advance for anyone who can help?

---

### Post by Redsandro on 2012-06-14
Is it possible to have virtual users, but to have certain user use a different local system user?

For virtual users, we have: 
***/etc/vsftpd/vsftpd.conf***
```
# Required for virtual users
local_enable=YES
guest_enable=YES
guest_username=ftp

# Home
local_root=/home/virtual/$USER

# User specific settings
user_config_dir=/etc/vsftpd/users

```

For individual users, we have, for example: 
***/etc/vsftpd/users/admin***
```
dirlist_enable=YES
download_enable=YES
write_enable=YES
local_root=/home/admins
guest_username=admin ### this does not work

```

How can we make certain users be a different 'real' username on the system?

---

### Post by Redsandro on 2012-06-15
On second thought, I think it actually does work. With a catch.

If you have the **global** *guest_username=ftp* but the **user-specific** *guest_username=admin*, your ftp client will show all permissions being owned by user and group *ftp*, but in reality you only have the permissions for *admin* on the real system.

Confusing, but it works.

---

### Post by Return Privacy on 2012-06-18
What? I don't understand what a virtual user is at all. I just need to setup this to allow 2 specific users on 2 other computers on my home network, to Upload files to the FTP server.
Right now I am just having them log in to the FTP server as the Admin user of the FTP Ubuntu computer. I know that can't be safe at all, as it gives them full access to the Ubuntu FTP computer.

---

### Post by Redsandro on 2012-06-18
That's where virtual users come in handy. They are users that are not real users on the system.

For example, you can have 'bob' and 'clara' log into your ftp server, while in reality they log in as user 'ftp'.

[http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/](http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/)

---

### Post by skaramanger on 2012-08-10
I'm trying to get vsftpd working again for me.  Last year, I had a crash and lost all my configuration for vsftpd.  Recently, I decided to give it a try again.  I'm currently running Kubuntu 12.04 kernel 3.2.0-27-generic. I installed vsftpd from the repos and commenced to duplicate my previous configuration gleened from my posts here in this thread.

I've gotten to a point that vsftpd starts and doesn't crash :/.  I cannot login I get the old 530 error regarding non-anonymous users must use encryption.

```
~$ ftp localhost
Connected to localhost.
220 Welcome to Tz FTP service.
Name (localhost:me): Mr_T
530 Non-anonymous sessions must use encryption.
Login failed.
ftp>
```

```
# Current config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive. 
#listen_ipv6=YES
#
# Allow anonymous FTP? (Disabled by default)
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
virtual_use_local_privs=YES
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# If enabled, vsftpd will display directory listings with the time
# in  your  local  time  zone.  The default is to display GMT. The
# times returned by the MDTM FTP command are also affected by this
# option.
use_localtime=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by 
# a different user. Note! Using "root" for uploaded files is not
# recommended!
# chown_uploads=YES
# chown_username=terryg
#
# You may override where the log file goes if you like. The default is shown
# below.
xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
# nopriv_user=ftp
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reportin g the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
ftpd_banner=Welcome to Tz FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
#chroot_local_user=YES
#chroot_list_enable=NO
##
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd.virtual
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/vsftpd/vsftpd.pem
# This option specifies the location of the RSA key file to use for SSL
# encrypted connections.
# rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
# 
# If I uncomment the above, ftp denies connection out right.

# Mods from: http://ubuntuforums.org/showthread.php?p=3138955
#
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
# Filezilla uses port 21 if you don't set any port
# in Servertype "FTPES - FTP over explicit TLS/SSL"
# Port 990 is the default used for FTPS protocol.
# Uncomment it if you want/have to use port 990.
# listen_port=990
listen_port=21
# Show hidden files and the "." and ".." folders.
# Useful to not write over hidden files:
force_dot_files=YES
# Hide the info about the owner (user and group) of the files.
hide_ids=YES
# Connection limit for each IP:
max_per_ip=2
# Maximum number of clients:
max_clients=2
#
# Enable (only) guests.
guest_enable=YES
# This is not needed, it's the default. Just here for clarity.
guest_username=ftp
# Where the guests (virtual) usernames are set.
user_config_dir=/etc/vsftpd/vusers
pasv_min_port=12000
pasv_max_port=12100
#check_shell=NO
debug_ssl=YES
log_ftp_protocol=YES
pasv_address=192.168.1.120
pasv_promiscuous=YES
pasv_enable=YES

```

The above is virtually the same as last years.

```
$ cat /etc/pam.d/ftp
auth required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login
account required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login
$ 

```

```
~$ cat /etc/vsftpd/workers
write_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
local_root=/home/work/$USER
chroot_local_user=YES
dirlist_enable=YES
download_enable=YES
guest_username=workers
~$
```


I've got ports 21 and 20 forwarded on my router to my local ip address. I opened ports on my local firewall 20,21,12000-12100.  So if some kind fellow user might assist me with this issue I would be ubunturnally grateful.

---

### Post by sunnytuladhar on 2012-11-07
Hi,

I have one problem regarding vsftpd. Suppose if I upload a file name "abc.txt" and I edited that file and again reupload the same file it will ask "do you want to overwrite the same file"

I dont want this message to come. if an user uploads file that exist in server, he should be able to upload the file without any notification. 

what should I change at server end?

Note: want to change at server end only.

Thanks in advance...

---

### Post by ikester8 on 2012-11-10
I've got the oddest problem. vsftpd will let me see most directories, but not all. Here is an example of a successful and an unsuccessful dirlist:

```
Command:	CWD /Pictures
Response:	250 Directory successfully changed.
Command:	PWD
Response:	257 "/Pictures"
Command:	PASV
Response:	227 Entering Passive Mode (67,191,236,175,103,178).
Command:	LIST -a
Response:	150 Here comes the directory listing.
Response:	226 Directory send OK.
Status:	Directory listing successful
Status:	Retrieving directory listing...
Command:	CWD /Documents
Response:	250 Directory successfully changed.
Command:	PASV
Response:	227 Entering Passive Mode (67,191,236,175,98,227).
Command:	LIST -a
Response:	150 Here comes the directory listing.
Error:	Connection timed out
Error:	Failed to retrieve directory listing
```

Here is my vsftpd.conf:
```
# Put in /etc/vsftpd.conf
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
ftpd_banner=Welcome to Ike's FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/home/ftp
chroot_local_user=YES
```

Any thoughts? I really need to see my Documents folder when I'm out of town.

Thanks!

---

### Post by jumbarger on 2013-02-21
There is nothing"easy" or "simple" about setting up this FTP server.  

12 pages of discussion on setup, no GUI, the necessity of customizing code...  After hours and hours of trying to solve the problem of how to access my files remotely (VPN, VNC, FTP, etc.), I am ready to give up.

Does anyone know of a genuinely "simple" FTP server.  By "simple" I mean GUI, no custom coding, intuitive setup requiring little/no help, server smart enough to figure some things out on its own and let me use buttons and toggles for the rest.

I want it on Ubuntu, I want open source, and I want it for free.

---

### Post by RaHorakhty on 2013-03-14
I hear ya! Check out the following sites...

[https://www.digitalocean.com/community/articles/how-to-set-up-vsftpd-on-ubuntu-12-04](https://www.digitalocean.com/community/articles/how-to-set-up-vsftpd-on-ubuntu-12-04)

[http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/](http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/)

[http://www.hosting.com/support/linux/adding-ftp-users-for-vsftp](http://www.hosting.com/support/linux/adding-ftp-users-for-vsftp)

Hrs of head scratching and I'm still stuck....

---

### Post by tulong211 on 2013-03-24
Hi Everybody!

I can't install [COLOR=#000000][FONT=Ubuntu Mono]libdb3-util package with : [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install libdb3-util. I try research for libdb3-util but It's no available. I can't continue install FTP
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
My OS : Ubuntu 12.04 Lts 64bit.
[/FONT][/COLOR]

---

### Post by Birdman2010 on 2013-03-28
> **jumbarger said:**
> There is nothing"easy" or "simple" about setting up this FTP server.  

12 pages of discussion on setup, no GUI, the necessity of customizing code...  After hours and hours of trying to solve the problem of how to access my files remotely (VPN, VNC, FTP, etc.), I am ready to give up.

Does anyone know of a genuinely "simple" FTP server.  By "simple" I mean GUI, no custom coding, intuitive setup requiring little/no help, server smart enough to figure some things out on its own and let me use buttons and toggles for the rest.

I want it on Ubuntu, I want open source, and I want it for free.

I found this website:  [http://systembash.com/content/evaluating-ftp-servers-proftpd-vs-pureftpd-vs-vsftpd/](http://systembash.com/content/evaluating-ftp-servers-proftpd-vs-pureftpd-vs-vsftpd/)

According to this website, you should only use vsftpd if you have many servers to manage.  In addition, the author recommends ProFTPd for someone who wants a simple GUI solution.  I haven't tried ProFTPd.  I'm still trying to get vsftpd to work.  However, I feel your frustration with vsftpd.  I'm there too.  Since I am on Page 12 of a "Easy FTP with vsftpd" thread, I think that my next step is to use ProFTPd.

Here is wishing us good luck with ProFTPd!

---

### Post by ssaththiyan on 2014-01-01
Hi, 
I have to  configure a FTP server using VSFTPD as like this, There will be multiple ftp users and each ftp users should see only their home directory, Other directories should not visible , may be they can see another public directory which is shared to all ftp users. How do i do this in ubuntu/linux with vsftpd? 

Please help me,

---

### Post by Votlon on 2014-01-04
> **tulong211 said:**
> 

I can't install [COLOR=#000000][FONT=Ubuntu Mono]libdb3-util package with : [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install libdb3-util. I try research for libdb3-util but It's no available. I can't continue install FTP
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
My OS : Ubuntu 12.04 Lts 64bit.
[/FONT][/COLOR]

Dude im having same exact issue WTF

---

### Post by grahammickle on 2014-01-10
> **dallen2 said:**
> Dude im having same exact issue WTF

Same issue.

Ubuntu version:

Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise

---

### Post by nwilson5 on 2014-01-14
> **grahammickle said:**
> Same issue.

Ubuntu version:

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise
db5.1-util - Berkeley v5.1 Database Utilities
db4.7-util - Berkeley v4.7 Database Utilities
db4.8-util - Berkeley v4.8 Database Utilities

Newer versions of said package. No guarantee it will fix everything you're trying to do though :).

---

### Post by chris2kari on 2014-01-18
It's ricidulous I agree.
Networking is the last bastion of the autistic savant geeks who love to make everything as difficult and time consuming as possible.
Not everyone is a sysadmin being paid to do nothing but sit & type long cryptic case sensitive command strings all day long..

Install & make it insecure (easy to access in a trusted LAN:
[http://www.liberiangeek.net/2012/06/install-and-setup-ftp-server-vsftpd-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/06/install-and-setup-ftp-server-vsftpd-in-ubuntu-12-04-precise-pangolin/)

Install & make it very secure in an enterprise environment:
[http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/](http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/)

Adding 'virtual' users:
[http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/](http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/)

[http://www.hosting.com/support/linux/adding-ftp-users-for-vsftp/](http://www.hosting.com/support/linux/adding-ftp-users-for-vsftp/)

---

### Post by Votlon on 2014-01-30
still no fix?

---

### Post by fred.sauze on 2014-04-25
> **epimeteo said:**
> 
Create the new file /etc/pam.d/ftp for the new authentication system:
```
sudo nano /etc/pam.d/ftp
```And add the following content:
```
auth required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login
account required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login
```


It seems the location of 'pam_userdb.so' has changed (I'm using Ubuntu 13.10).
```
$ locate pam_userdb.so
/lib/x86_64-linux-gnu/security/pam_userdb.so
```
So after the following command:
```
sudo nano /etc/pam.d/ftp
```
the content might need to change to:
```
auth required /lib/x86_64-linux-gnu/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login
account required /lib/x86_64-linux-gnu/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login
```
And again, check the location of 'pam_userdb.so', the location might be different in 32-bit or other Ubuntu versions.

> **tulong211 said:**
> Hi Everybody!

I can't install [COLOR=#000000][FONT=Ubuntu Mono]libdb3-util package with : [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install libdb3-util. I try research for libdb3-util but It's no available. I can't continue install FTP
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
My OS : Ubuntu 12.04 Lts 64bit.
[/FONT][/COLOR]
Hope this helps
```
sudo apt-get install db-util
```
Sometimes when you type the command, Ubuntu might suggest the package needed.
For example in this scenario
```

$ db_load
The program 'db_load' is currently not installed. You can install it by typing:
sudo apt-get install db-util
```

---

### Post by netrix-g on 2014-05-19
So I have Ubuntu 14.04 on an HP Microserver N54L
I'm tech-savvie to a degree, working on Windows mainly, but got an iMac a couple of years back, and never really got into OSX.

After probably a week i managed to get the mac to user the server for Time Machine backups but, although I can "see" my server in Finder on the Mac I cannot browse or see any folders let alone copy "stuff" to it. (and I mean a week solid pulling my hair out !!)

So I now desperately want to set up ftp so an iPhone user can use a free ftp client to upload a (rather long) video of a recently deceased relative.
I have no more hair to pull out but I despair t the title of these thread "Easy ftp with VSFTPD" the 13 pages of problems bear out my despair.

Can someone please tell me if it will work with my setup ? and possibly point me to a tutorial that works ?

I'd probably need some good pointers on how to remove all the "bad programming" that I've ended up with, taking tips and hints from various threads/tutorials is not a good idea in my opinion.

Thanks in advance for any help - I realise this thread has been dormant for some three weeks.

Please be kind !!

Regards,

Netrix

---

### Post by Lars Noodén on 2014-05-19
> **netrix-g said:**
> So I have Ubuntu 14.04 on an HP Microserver N54L
I'm tech-savvie to a degree, working on Windows mainly, but got an iMac a couple of years back, and never really got into OSX.

After probably a week i managed to get the mac to user the server for Time Machine backups but, although I can "see" my server in Finder on the Mac I cannot browse or see any folders let alone copy "stuff" to it. (and I mean a week solid pulling my hair out !!)

So I now desperately want to set up ftp so an iPhone user can use a free ftp client to upload a (rather long) video of a recently deceased relative.
I have no more hair to pull out but I despair t the title of these thread "Easy ftp with VSFTPD" the 13 pages of problems bear out my despair.

Can someone please tell me if it will work with my setup ? and possibly point me to a tutorial that works ?

I'd probably need some good pointers on how to remove all the "bad programming" that I've ended up with, taking tips and hints from various threads/tutorials is not a good idea in my opinion.

Thanks in advance for any help - I realise this thread has been dormant for some three weeks.

Please be kind !!

Regards,

Netrix

[Please don't use FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) for that.  It's 2014, not 1994 ;)  For a simple file transfer with an iMac, if you are using OS X or Ubuntu, SFTP is the way to go.  It's part of the system in OS X and it can be turned on by going to System Preferences -> Internet & Networking -> Sharing -> Remote Login.  Or something like that, it's been a while.  If you are running Ubuntu on your iMac, then just install the package openssh-server.  

Either way, **S**FTP clients will then be able to connect to the machine securely and easily.  Is your [S](https://www.google.fi/search?q=stop+using+ftp)FTP client on the iPhone Cyberduck?

---

### Post by netrix-g on 2014-05-19
Hi Lars, thank you for the speedy reply !

The iMax is OSX Mountain Lion, the HP server has Ubuntu 14.04 installed. Going forward, I would like to be able to connect remotely to the Ubuntu server (securely !!)

I thought the "VS" of vsftpd would be adequate, but I'll have to look at SFTP now.
In the short term, if I can get the video from the iPhone to the mac (we live 90 miles apart !) via SFTP that will suffice for now but as mentioned I would like colleagues at work and family to connect/upload and download to the HP server at some point in the near future !
Her iPhone currently has no ftp client and I wanted to use a free app as they are not related to me etc and are doing me a favour by allowing me to see the video. so I chose FTP Sprite (it's free) and I've used that on my iPhone  to ftp to a colleague's ftp server .

I'm off to Google SFTP and OS X

Thanks again for your input

Regards

Netrix

---

### Post by helseth2 on 2014-06-23
Trying to set up vsftpd on Ubuntu server 14.04 . Everything works aslong as SSL is not enabled.

Filezilla:
```
Status:    Connecting to 192.168.1.67:990...
Status:    Connection established, initializing TLS...
Error:    GnuTLS error -15: An unexpected TLS packet was received.
Error:    Could not connect to server

```

vsftpd.conf
```
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
listen_port=990
ssl_ciphers=HIGH
debug_ssl=YES

```

There's nothing about SSL in /var/log/vsftpd.log even though debug_ssl is enabled.

```

Mon Jun 23 14:32:51 2014 [pid 1905] CONNECT: Client "192.168.1.66"
Mon Jun 23 14:32:56 2014 [pid 1909] CONNECT: Client "192.168.1.66"
Mon Jun 23 14:37:22 2014 [pid 1913] CONNECT: Client "192.168.1.66"
Mon Jun 23 14:37:36 2014 [pid 1917] CONNECT: Client "192.168.1.66"
Mon Jun 23 14:37:41 2014 [pid 1921] CONNECT: Client "192.168.1.66"

```



Any ideas?



E: Figured it out - I was trying to implicit FTP over TLS, when implicit_ssl was disabled.

---

### Post by Justin_Slay on 2014-08-12
So how would one go about changing how the page is displayed when accessing a site via web browser [ftp://domain.com](ftp://domain.com), is there anyway to dress it up to make it look nicer than an apache directory listing?

---

### Post by chase7 on 2014-08-17
> **epimeteo said:**
> Hi ungluun,

I suppose you want a "mp3" user for this. If it is, the simplest way to do it is to create a user which its home folder in /media/sda1/MP3:

```
sudo groupadd mp3
sudo useradd -c "FTP mp3" -d /media/sda1/MP3 -g mp3 mp3
```Set his password:

```
sudo passwd mp3
```And restart vsftpd:

```
sudo /etc/init.d/vsftpd restart
```If you have all users chrooted, it will work with no more changes.

Hope this works for you. :)

I am trying to accomplish the same thing as this but my info is below
Group: Officer
User: Chaser

Directory
/home/field1/field2/field3

I added the group using
#sudo groupadd Officers

and added the user using
# sudo useradd -d /home/field1/field2/field3 -g Officers Chaser

I then set Chasers Password using
# sudo passwd Chaser

I then restarted the vsftpd service using
# service vsftpd restart

I tried connecting to my FTP (Filezilla) using the IP and port I set (I'm already using port 21) and this is what i have returned to me.
"Connection attempt failed with "ECONNREFUSED - Connection refused by server"."

What might i be doing wrong?

---

### Post by Justin_Slay on 2014-08-19
> **chase7 said:**
> I am trying to accomplish the same thing as this but my info is below
Group: Officer
User: Chaser

Directory
/home/field1/field2/field3

I added the group using
#sudo groupadd Officers

and added the user using
# sudo useradd -d /home/field1/field2/field3 -g Officers Chaser

I then set Chasers Password using
# sudo passwd Chaser

I then restarted the vsftpd service using
# service vsftpd restart

I tried connecting to my FTP (Filezilla) using the IP and port I set (I'm already using port 21) and this is what i have returned to me.
"Connection attempt failed with "ECONNREFUSED - Connection refused by server"."

What might i be doing wrong?

When you add a user, it is always good to do a reboot before attempting an ftp or other login. 

First, verify the server has stayed running after restart
```

j@jslay:~$ sudo service vsftpd restart
[sudo] password for j:
vsftpd stop/waiting
vsftpd start/running, process **9767**
jjslay:~$ sudo service vsftpd status
vsftpd start/running, process **9767**



```
Make sure it has the same PID # as it did when you issued a restart.

Verify it is listening on your given port #
```

sudo netstat -lnptu | grep vsftpd
tcp        0      0 0.0.0.0:**21**              0.0.0.0:*               LISTEN      **9767/vsftpd**

```


Check to make sure that user has a shell assigned. Even if it is /bin/dummy 
```

getent passwd Chaser | cut -d: -f7

```


If no shell has been defined, define one.
```

sudo vim /etc/shells

```

Add this line to the end
```

/bin/dummy

```
Save.

Mod the user's shell
```

sudo usermod -s /bin/dummy Chaser

```

Reboot the box and try again.

---

### Post by Flauschie on 2014-08-21
followed your tutorial, but receiving "GnuTLS Error -15" ...
I tried to disable ssl_enable and found out whats happening... the server can't handle the user configs!

```
write_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
local_root=/home/work
chroot_local_user=YES
dirlist_enable=YES
download_enable=YES
guest_username=workers
```

I have to remove everything except for local_root and guest_username .... So what now? How to handle the user rights from here? Seems like either your tutorial is way too outdated or sth is still wrong on my side...

EDIT: Looks like that the specific virtual user configs are not allowed to overwrite the vsftpd.conf ... thats why I am receiving errors like
500 OOPS: bad bool value in config file for: write_enable
500 OOPS: bad bool value in config file for: chroot_local_user
.....


EDIT2: Resolved the problem by removing trailing spaces after each line :-) :-)

---

### Post by jerchmungo on 2015-02-13
thank you epimeteo!

---

### Post by keith_stone2 on 2015-02-24
is there a way to limit specific commands such as mkdir or rm?

i see cmds_allowed and cmds_deny for vsftpd.conf, however they look ftp command related.

is there away to disable the subsystem commands that are avail with sftp ?

sftp> ?
Available commands:
bye Quit sftp
cd path Change remote directory to 'path'
chgrp grp path Change group of file 'path' to 'grp'
chmod mode path Change permissions of file 'path' to 'mode'
chown own path Change owner of file 'path' to 'own'
df [-hi] [path] Display statistics for current directory or
filesystem containing 'path'
exit Quit sftp
get [-P] remote-path [local-path] Download file
help Display this help text
lcd path Change local directory to 'path'
lls [ls-options [path]] Display local directory listing
lmkdir path Create local directory
ln oldpath newpath Symlink remote file
lpwd Print local working directory
ls [-1aflnrSt] [path] Display remote directory listing
lumask umask Set local umask to 'umask'
mkdir path Create remote directory
progress Toggle display of progress meter
put [-P] local-path [remote-path] Upload file
pwd Display remote working directory
quit Quit sftp
rename oldpath newpath Rename remote file
rm path Delete remote file
rmdir path Remove remote directory
symlink oldpath newpath Symlink remote file
version Show SFTP version
!command Execute 'command' in local shell
! Escape to local shell
? Synonym for help
sftp>

---

### Post by Lars Noodén on 2015-02-24
Edit: never mind, wrong package...

> **keith_stone2 said:**
> is there away to disable the subsystem commands that are avail with sftp ?

Yes, but it's more technical and depends on which version of OpenSSH server you are running, it's only in 6.5 and later.  You can see a list of the requests which you can allow or block using [-Q with the stand-alone sftp-server](http://manpages.ubuntu.com/manpages/trusty/en/man8/sftp-server.8.html):

```

 /usr/lib/sftp-server -Q requests

```

Then use -p or -P to whitelist or blacklist them in [sshd_config](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html) with the Subsystem directive.  It will take a bit of verbose log watching to work out what is allowed. 
```

Subsystem sftp internal-sftp -p *foo,bar* -l VERBOSE

```

---

### Post by keith_stone2 on 2015-02-27
> **Lars Noodén said:**
> Edit: never mind, wrong package...



Yes, but it's more technical and depends on which version of OpenSSH server you are running, it's only in 6.5 and later.  You can see a list of the requests which you can allow or block using [-Q with the stand-alone sftp-server]("http://manpages.ubuntu.com/manpages/trusty/en/man8/sftp-server.8.html"):

```

 /usr/lib/sftp-server -Q requests

```

Then use -p or -P to whitelist or blacklist them in [sshd_config]("http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html") with the Subsystem directive.  It will take a bit of verbose log watching to work out what is allowed. 
```

Subsystem sftp internal-sftp -p *foo,bar* -l VERBOSE

```


**** :(

openssh-server-5.3p1-104.el6_6.1.x86_64.  this is redhats version.. so im not sure how to determine if this is equivalent to 6.5

---

