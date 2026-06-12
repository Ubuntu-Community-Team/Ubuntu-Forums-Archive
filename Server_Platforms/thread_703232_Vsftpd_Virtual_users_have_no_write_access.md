---
title: "Vsftpd Virtual users have no write access"
date: 2008-02-21
forum: Server Platforms
---

### Post by ricketick on 2008-02-21
Hi there,

I have setup vsftpd following this post ([http://ubuntuforums.org/showthread.php?p=2313197](http://ubuntuforums.org/showthread.php?p=2313197)) and vsftpds own manual for virtual users ([ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.3/EXAMPLE/VIRTUAL_USERS/README](ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.3/EXAMPLE/VIRTUAL_USERS/README)).

Everything works except "write_enable=YES". I can login to the ftp, read files, but I can't upload.

I've made a virtual user with the** home dir /var/www and chown the www to virtual:virtual and chmodded it to 777.**

This is my current vsftpd.conf:
```
anonymous_enable=NO
local_enable=YES
write_enable=YES
anon_upload_enable=YES
#anon_world_readable_only=NO
local_umask=022
virtual_use_local_privs=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
chroot_local_user=YES
guest_enable=YES
guest_username=virtual
listen=YES
listen_port=10021
pasv_min_port=30000
pasv_max_port=30999

```
As you can see I've enabled most priviliges, however shouldn't "write_enable=YES" alone do the trick nicely?

Also I tried to change guest_username to my admin account (created at server installation) however vsftpd just ignored it and when i logged in on the ftp I still came to the virtuals home dir, even though the admin accounts was set as guest and it had a different home dir.

Thanks.

---

### Post by ricketick on 2008-02-22
Any suggestions as to what might have gone wrong?

Thinking of installing proftpd and give it a try. Read it's easy however not as secure as vstpd. Does anyone have any tips how to procede with proftpd, to avoid the situation I am in now?

---

### Post by gameplayer2011 on 2008-02-22
It seems that you have done what I am trying to do.

I can't get to the vsftpd.conf file
how do you get to it to edit it?

thank you very much

---

### Post by ricketick on 2008-02-23
Vstpfd normaly recides at /etc/vsftpd.conf.

e.g: sudo pico /etc/vsftpd.conf

Of course you would have to install vsftp first. See the links in my first post for more information.

---

### Post by blx_286 on 2008-02-23
I don't know if this will help, but I followed the how-to at [http://ubuntuforums.org/showthread.php?t=518293](http://ubuntuforums.org/showthread.php?t=518293) and I have the virtual users working.

I can upload and download, but I can't get the setup exactly like I want. This is the setup I am trying to accomplish.

ProjectFolder1 - download only folder for multiple client group access
ProjectFolder2 - download only folder for multiple client group access
ClientFolder1 - upload/down folder for specific client
ClientFolder2 - upload/down folder for specific client
Uploads - an uploads only folder for authorized users

I would also like to give upload/download access to another user in our company to access all of these folders. I am still trying to figure out how to give the correct access for myself and this other user.

Let me know if that how-to works for you.

Tim

---

### Post by ricketick on 2008-02-25
Thanks for posting that guide, I had completely missed it.

I commented guest_enable and guest_username to try and loging with a normal account. However it didn't work, not even anonynomous worked, however I could still login with the user and pass I had made in the pam database!

Something smelled fishy so I deleted the virtual user and then I got this message when I tried to login via ftp.
"Could not find 'guest_username':virtuel user."

So somehow some settings in vsftpd were never updated at restart.
I restart vsftpd with intd: /etc/init.d/vsftpd restart

When I try to start in standalone ./vsftpd att /usr/sbin/ I get this:
"500 OOPS: could not bind listening IPv4 socket"

I decided to restart the server and things started working, I managed to setup a normal user account, added the usernamne to vsftpd.allowed_users so only that user may login, and it works fine. I also disabled the shell login, so that use can't login on the shell.

A few questions:
Why did my vsftpd behave like this and what can I do to fix it? 
Why can't I start it in standalone and should it run standalone or with inetd?
Do I have a secure setup (I intend to useenable ssl) or should I consider trying to get virtual users work, now that I know my previous attemtps might have been ignored by vsftpd?

---

### Post by blx_286 on 2008-02-27
Sorry, I don't think I will be much help at answering your questions as to why vsftpd is working like it is.

I thought I had my virtual users working right and I have been trying to get this setup for a week and still don't have it yet. Somehow the accounts I did have working are no longer working. I'm about ready to give up on this.

On the secure stuff, I think that using SSL and virtual users would be the  better way to go.

---

### Post by Mr. C. on 2008-02-27
What directory do you end up in when you've logged in as a virtual user?
What is the error message you receive when you attempt to upload?

MrC

---

### Post by ricketick on 2008-02-28
I've got my server up and running now without virtual users. Made a local account and set userlist_enable=YES  and added the user account, so now all other accounts are denied. Then I disabled the ftp local accounts shell login, so the user can't login to ssh. I think I'll give virtual users another try in a week or two, need the ftpserver at the moment. Thinking of writing a server guide with all the problems I've encountered ;)

blx_286, I don't know how you have setup the server or what problems you have encoutered. Does none of the accounts work anymore? can you login at all? try enabling the anonymous setting to just try and se if the ftp works at all.

If the ftp users suddenly stopped working my suggestion is to restart the server, my vsftpd started acting strange and stopped updating it's settings, however it worked again after I restarted the server.

---

### Post by blx_286 on 2008-02-28
Ok, I found I had a couple of problems. I now have everything set as I mentioned previously and it's working well. The first problem I had was that I was using a copy of the original vsftpd.conf file and trying to modify it as needed. I was referring to several different threads and that was part of my problem. The other problem I had was that on one of my pam database loads, I had specified the wrong directory to build the database so vsftpd was looking at the wrong spot.

I cleaned up my previous mess and started again from the beginning. I kept the original vsftpd.conf and erased everything in the copy and started over. I followed the tutorial from [http://ubuntuforums.org/showthread.php?t=570717](http://ubuntuforums.org/showthread.php?t=570717) which was modified from this tutorial [http://www.debiansec.com/linux/services/ftp.html#introduction](http://www.debiansec.com/linux/services/ftp.html#introduction) and this last tutorial addresses standalone vs. xinetd.

I documented my steps so I would have them for future reference and I made some changes to the tutorials I used. Most of this is a copy of the original link from above, but I though I would post what worked for me.

```
# install and config base ubuntu server with ssh and vsftpd services
# -------------------------------------------------------------------------

# update software archives with
sudo aptitude update

# install openssh
sudo aptitude install openssh-server

# change the openssh listening port from the standard of 22 to something else
# you can then connect to this ssh port using putty
# make a copy of original ssh config file first
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.original
sudo chmod a-w /etc/ssh/sshd_config.original
sudo nano /etc/ssh/sshd_config

# restart the ssh service
sudo /etc/init.d/ssh restart

# install vsftp service
sudo aptitude install vsftpd
```

```
# -------------------------------------------------------------------------
# configure the vsftpd services making a copy of the original first
sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.original
sudo nano /etc/vsftpd.conf

# Since I had a copy of the original I started with a blank vsftpd.conf
# file and added the following code -

# == beginning of code ====================================================
# base configuration
# -------------------------------------------------------------------------
anon_world_readable_only=NO
anonymous_enable=NO
chroot_local_user=YES
guest_enable=YES
guest_username=ftp
hide_ids=YES
listen=YES
# I commented this out from the original tutorial
#listen_address=192.168.0.1
local_enable=YES
max_clients=100
max_per_ip=1
nopriv_user=ftp
pam_service_name=ftp
pasv_max_port=65535
pasv_min_port=64000
session_support=NO
use_localtime=YES
user_config_dir=/etc/vsftpd/users
userlist_enable=YES
userlist_file=/etc/vsftpd/denied_users
xferlog_enable=YES

# -------------------------------------------------------------------------
# ftp settings
# -------------------------------------------------------------------------
anon_umask=0027
async_abor_enable=YES
connect_from_port_20=YES
dirlist_enable=NO
download_enable=NO

# -------------------------------------------------------------------
# ssl settings
# -------------------------------------------------------------------
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
listen_port=1984
# == end of code ==========================================================

```

```
# -------------------------------------------------------------------------
# create the ftp directories

sudo -i
cd /home/ftp
mkdir directory1 directory2 directory3
chown ftp directory1 directory2 directory3
exit

# you can verify that user ftp owns the directories with
ls -ld *
# which should show something similar to this
drwxr-xr-x 2 ftp root 4096 2008-02-28 20:45 directory1
drwxr-xr-x 2 ftp root 4096 2008-02-28 20:45 directory2
drwxr-xr-x 2 ftp root 4096 2008-02-28 20:45 directory3

```

```
# -------------------------------------------------------------------------
# create the vsftpd directory for config files
sudo mkdir /etc/vsftpd
sudo mkdir /etc/vsftpd/users

# create a config file for every virtual user and add the following code
sudo nano /etc/vsftpd/users/user1

# == beginning of code ====================================================
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
dirlist_enable=YES
download_enable=YES
local_root=/home/ftp/directory1
write_enable=YES
# == end of code ==========================================================

# this can be copied for additional users and modified as needed
sudo cp /etc/vsftpd/users/user1 /etc/vsftpd/users/user2
sudo nano /etc/vsftpd/users/user2
```

```
# -------------------------------------------------------------------------
# create a denied local user list - only virtual users can login
sudo -i
cat /etc/passwd | cut -d ":" -f 1 | sort >/etc/vsftpd/denied_users
exit
```

```
# -------------------------------------------------------------------------
# update the pam service for login authentification
sudo nano /etc/pam.d/ftp

# add the following code to the file
# == beginning of code ====================================================
auth required /lib/security/pam_userdb.so db=/etc/vsftpd/accounts
account required /lib/security/pam_userdb.so db=/etc/vsftpd/accounts
# == end of code ==========================================================

```

```
# -------------------------------------------------------------------------
# create the vitual user name and password file, below is the format
sudo nano /etc/vsftpd/accounts.tmp

# == beginning of code ====================================================
user1
password for user1
user2
password for user2
# == end of code ==========================================================

```

```
# load the password file into the pam database
sudo db3_load -T -t hash -f /etc/vsftpd/accounts.tmp /etc/vsftpd/accounts.db
chmod 600 /etc/vsftpd/accounts.tmp
chmod 600 /etc/vsftpd/accounts.db

```

```
# -------------------------------------------------------------------------
# restart the vsftpd service
sudo /etc/init.d/vsftpd restart

# -------------------------------------------------------------------------
# verify what ports your server is listening on. there should only be two
# the ssh port and the ftps port that were assigned earlier

netstat -tulp
```

That seems to be working for secure logins and only using vitual users. I hope that helps and sorry for the long post.

Tim

---

### Post by blx_286 on 2008-02-28
I thought I might also mention that I initially had problems with virtual users because of the way I was trying to set them up. I originally had several users that were both local users and virtual ftp users. I have since ditched this approach.

I set this server up on my network, but will be moving it to the DMZ. I don't really want my network users to have local accounts to this box, they can just ftp into it. So now I have 2 local admins that can login with ssh to manage the box and all other users are virtual ftp users (with different names). Using separate login names for local and ftp users has helped me keep things straight.

Tim

---

### Post by Mr. C. on 2008-02-28
> **blx_286 said:**
> That seems to be working for secure logins and only using vitual users. I hope that helps and sorry for the long post.

The important thing is that you discovered your misconfiguration and have it resolved.  There are too many posts and beliefs that these tried and true,very stable software services mysteriously stop working or randomly or magically change themselves.   Nice work.

MrC

---

### Post by ricketick on 2008-02-29
Thank you blx_286, skimmed through your post and I wil make sure to consult it when I try to setup my server with virtual hosts.

> **Mr. C. said:**
> The important thing is that you discovered your misconfiguration and have it resolved.  There are too many posts and beliefs that these tried and true,very stable software services mysteriously stop working or randomly or magically change themselves.   Nice work.

MrC

I have however not discovered why my vsftpd stopped updating its settings when vsftpd.conf was edited and vsftpd was restarted via int.d. and I havn't managed to figure out why I can't start vsftpd in standalone mode. If you have any theories please let me know.

---

### Post by Mr. C. on 2008-02-29
> **ricketick said:**
> I have however not discovered why my vsftpd stopped updating its settings when vsftpd.conf was edited and vsftpd was restarted via int.d. I havn't figured out why I can't start with vsftpd in standalone mode either. If you have any theories please let me know.

This is most assuredly a problem with multiple configuration files - you are editing one, but another, or default settings, are used for startup.

vsftpd is passive in reading the configuration files - you tell it which one, and it only reads the file.

Create a copy of the configuration file you want somewhere.  Set 

```
listen=YES
```

in the file.  Start vsftpd from the command line as:

```
sudo vsftpd /path/to/conf/file/you/copied
```

It should sit there in listen (standalone) mode, and will allow you to attach via FTP elsewhere.

Examine your init.d/vsftpd file to see *which* vsftpd.conf file is being used.  Find all vsftpd.conf files on your system.

---

### Post by ricketick on 2008-03-01
Hm interesting there are multiple configuration files on my system, however could really any of them be responsible?

These are all the vsftpd config files on my system:
```
/etc/vsftpd.conf
/etc/vsftpd.conf.bak
/usr/share/doc/vsftpd/EXAMPLE/INTERNET_SITE_NOINETD/vsftpd.conf
/usr/share/doc/vsftpd/EXAMPLE/INTERNET_SITE/vsftpd.conf
/usr/share/doc/vsftpd/EXAMPLE/VIRTUAL_USERS/vsftpd.conf
/usr/share/man/man5/vsftpd.conf.5.gz
/var/lib/dpkg/info/vsftpd.conffiles
```
I find it unlikely that vsftpd has started using the doc files or my vsftpd.conf.bak

After looking through /etc/init.d/vsftpd I found two interesting lines:

if [ -f /etc/vsftpd.conf ] && ! egrep -iq "^ *listen(_ipv6)? *= *yes" /etc/vsftpd.conf; then  exit 0

This was the only line I could find that seems to do something with /etc/vsftpd.conf, and only seems to check for the listen directive.

# Exit if vsftpd.conf doesn't have listen=yes or listen_ipv6=yes

Sounds like I need listen=yes to start vsftpd with inet.d, I thought it was used for standalone mode only? Perhaps vsftpd read from the pid file and never updated it with the conf file? I only restarted, and that used to work, but suddenly it didn't anymore, should I have fore reloaded?

---

### Post by Mr. C. on 2008-03-01
Agreed; there is nothing interesting with the found configuration files.

Confirm for yourself that by default vsftpd is using the config file you expect:

```
strings /usr/local/sbin/vsftpd |grep '\.conf'
```

Change the path to vsftpd as necessary above.


if [ -f /etc/vsftpd.conf ] && ! egrep -iq "^ *listen(_ipv6)? *= *yes" /etc/vsftpd.conf; then exit 0

This line exits the startup script if there is no conf file in the standard place, or if listen != yes, as the comment suggests.

> 
Sounds like I need listen=yes to start vsftpd with inet.d, I thought it was used for standalone mode only? 

Unfortunately, the typos in your writings what should have been either "init.d" or "inetd" ("nt.d." and "inet.d" : two different, but relevant things!) have created some confusion.  I suppose you mean "init.d" and never have mean "inetd" or "inet.d" (which are part of the UCB inetd master daemon that starts up programs like vsftpd in the background upon connection!).

If you want vsftpd to run in standalone mode (which means "not controlled by a super networking daemon such as xinetd or inetd), then you set LISTEN=yes and it must be manually started or started via the "init.d/vsftpd" script.

> 
Perhaps vsftpd read from the pid file and never updated it with the conf file? I only restarted, and that used to work, but suddenly it didn't anymore, should I have fore reloaded?

No, the PID file is just a housekeeping file to assist in starting and stopping; it is not read by vsftpd.  Ignore that for now.

Restarting vsftpd via /etc/init.d/vsftpd is the same as using start followed by stop.  Reload (if supported) would do what is necessary for vsftpd to reload its configuration - if that means start/stop, it will do that, if it can just reload, it will do that.

Mind you - you must disconnect all your ftp connections before you restart the vsftpd; this ensures all the connections are closed so that the master re-reads the configuration file and new connections obtain the settings.

Please don't get tripped up believe that vsftpd does not pay attention to its configuration file - it does.  It is an outstanding piece of software.  If it is not working as you expect, consider it user misunderstanding or error, and focus on trying to figure out what that misunderstanding is.

---

### Post by blx_286 on 2008-03-02
I'm glad that Mr.C was able to jump in and work with you on your probs because I don't know enough to help in that area.

Mr.C, my victory was bittersweet because I can't access vsftpd in my DMZ. It works fine locally but once moved into the DMZ I cannot connect to it from the Net. Here is what I found on my vendors support page.

```
SSL FTP is very similar to standard FTP, but adds SSL encryption negotiation to the data and control connections. It uses dynamic port negotiation in exactly the same way that normal FTP does.

This is a problem because the FTP control connection specifies which ports will be opened for the FTP data channel. When the control connection is encrypted, there is no way that any firewall or NAT device can successfully examine (for opening the ports) or rewrite (for NAT) the contents of the control connection. This makes it difficult to pass SSL FTP through any other NAT or firewall device.

If you need secure file transfer, consider looking into SFTP or SCP. These protocols do not use dynamic port negotiation and work fine through any firewall without sacrificing security.
```

I don't know the difference between SFTP and SCP, but I guess I will be looking into one of those options.

Tim

---

### Post by Mr. C. on 2008-03-02
Have you tried:

Q) Help! Can I restrict vsftpd data connections to a specific range of ports?
A) Yes. See the config settings "pasv_min_port" and "pasv_max_port".

[http://en.wikipedia.org/wiki/SFTP](http://en.wikipedia.org/wiki/SFTP)
[http://en.wikipedia.org/wiki/Secure_copy](http://en.wikipedia.org/wiki/Secure_copy)

---

### Post by blx_286 on 2008-03-02
I'll check out those port settings.

Thanks

---

### Post by blx_286 on 2008-03-04
MrC can you point me in the right direction? Before I read your last post about the PASV ports, I had hastily uninstall vsftpd with

```
sudo aptitude remove vsftpd
```

I then removed the vsftpd.conf file and the vsftpd directories that I had previously created.

After reading your post, I reinstalled it and was going to walk through the setup again. The first thing I noticed was that the vsftpd.conf file was not created. I configured everything based on my notes and restarted vsftpd. I received the follow message:

```
* Stopping FTP server: vsftpd No /usr/sbin/vsftpd found running; none killed.
```

When it restarted, I found that it wasn't listening, when I used netstat. When searching for that message, I found that I could restart vsftpd manually with:

```
/usr/sbin/vsftpd &
```

I did that and received the following message:

```
vsftp 500 OOPS: SSL: cannot load RSA key
```

I remembered that the vsftp.conf file from the original install had a reference to RSA keys, so I added the following to vsftpd.conf:

```
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
```

Now, I can restart vsftpd using the init.d restart and do not get the "No /usr/sbin/vsftpd found running", but when I connect with an ftp client I get the following:

```
Status:	Connecting to 192.168.x.x:ssl_port ...
Status:	Connected with 192.168.x.x:ssl_port, negotiating SSL connection...
Response:	220 (vsFTPd 2.0.4)
Command:	AUTH SSL
Response:	234 Proceed with negotiation.
Status:	SSL connection established. Waiting for welcome message...
Command:	PBSZ 0
Response:	200 PBSZ set to 0.
Command:	PROT P
Response:	200 PROT now Private.
Command:	USER client1
Response:	331 Please specify the password.
Command:	PASS **********
Response:	230 Login successful.
Command:	FEAT
Response:	211-Features:
Response:	 AUTH SSL
Response:	 AUTH TLS
Response:	 EPRT
Response:	 EPSV
Response:	 MDTM
Response:	 PASV
Response:	 PBSZ
Response:	 PROT
Response:	 REST STREAM
Response:	 SIZE
Response:	 TVFS
Response:	211 End
Command:	SYST
Response:	215 UNIX Type: L8
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/"
Command:	PORT 10,0,0,60,4,149
Response:	200 PORT command successful. Consider using PASV.
Command:	TYPE A
Response:	200 Switching to ASCII mode.
Command:	LIST
Response:	150 Here comes the directory listing.
Error:	Unknown error in SSL layer
Error:	Disconnected from server
Error:	Could not retrieve directory listing
Error:	Timeout detected!
```

Any help would be greatly appreciated.

---

### Post by ricketick on 2008-03-04
> **blx_286]
The first thing I noticed was that the vsftpd.conf file was not created.[/QUOTE]
I've noticed this as well. If you remove the vsftpd package and install it again it does not make a new vsftpd.conf. I assume apt-get does not perfrom a "true" uninstall by removing the package.

Thanks for your help and patience MrC

Not sure this is relevant but I thought I should mention that when i first stopped the server via init.d and then ran sudo vsftpd /etc/vsftpd.conf my ssh client crashed (the pointer just fell of the prompt) however my ftp server was started successfully.

[QUOTE=Mr. C. said:**
> Confirm for yourself that by default vsftpd is using the config file you expect:

```
strings /usr/local/sbin/vsftpd |grep '\.conf'
```

It returned /etc/vsftpd.conf so seems to be correct.

> **Mr. C. said:**
> 
Unfortunately, the typos in your writings what should have been either "init.d" or "inetd" ("nt.d." and "inet.d" : two different, but relevant things!) have created some confusion.  I suppose you mean "init.d" and never have mean "inetd" or "inet.d" (which are part of the UCB inetd master daemon that starts up programs like vsftpd in the background upon connection!).

Thank you for pointing this out, this explains a thing or two :)

> **Mr. C. said:**
> 
Please don't get tripped up believe that vsftpd does not pay attention to its configuration file - it does.  It is an outstanding piece of software.  If it is not working as you expect, consider it user misunderstanding or error, and focus on trying to figure out what that misunderstanding is.
Couldn't agree anymore, my knowledge in this area is pretty limited, I'll keep an eye open the next time this happens, and perhaps I'll see a pattern.

---

### Post by blx_286 on 2008-03-05
> **ricketick said:**
> I've noticed this as well. If you remove the vsftpd package and install it again it does not make a new vsftpd.conf. I assume apt-get does not perfrom a "true" uninstall by removing the package.

I did find there is a purge option for apt-get and aptitude that is supposed to uninstall and clean things up better. I ran the following:

```
sudo aptitude purge vsftpd
sudo aptitude autoclean
```

I then reinstalled vsftpd and the vsftpd.conf file was created. Unfortunately, I walked through the setup again and it won't work. It works as an anonymous server, but once I configure it for SSL, it stops working. Guess I will scour the threads some more and see if I can find my problem.

---

### Post by Mr. C. on 2008-03-08
Sorry for the delay - do either / both of you still need help with this ?

---

### Post by blx_286 on 2008-03-09
I got mine working again, but the only way I could do it was to reinstall the entire server and go through my notes again. I then enabled the passive ports option that you mentioned.

Do you know of a way that I can create a recovery CD where I could plug in a CD and restore my server to the way I have it configured now?

I did start another thread on vsftpd because it's not really a write access issue, but I am still having a connection problem. I can connect from the Internet using a public IP and the pasv_address option, but I cannot connect to the public IP (or the private IP) from inside my network. I can then comment out the pasv_address option and connect to the local IP from inside my network. But when I do this, I cannot connect to the public address from the Internet.

Thanks,
Tim

---

### Post by Mr. C. on 2008-03-09
> **blx_286 said:**
> I got mine working again, but the only way I could do it was to reinstall the entire server and go through my notes again. I then enabled the passive ports option that you mentioned.
Sometimes that's the best way... a fresh start.

> **blx_286 said:**
> 
Do you know of a way that I can create a recovery CD where I could plug in a CD and restore my server to the way I have it configured now?
No, I'm not familiar with any tools that might do this.  I'm in the camp that prefers to maintain and track my own configurations, and backup the necessary files I know I need.  There are lots of options; you can track which configuration files you create when you install and configure a service, you can create timestamp lists and compare before / after to see which files you want to backup, or you can use dd or similar tools to backup the entire file system.

> **blx_286 said:**
> 
I did start another thread on vsftpd because it's not really a write access issue, but I am still having a connection problem. I can connect from the Internet using a public IP and the pasv_address option, but I cannot connect to the public IP (or the private IP) from inside my network. I can then comment out the pasv_address option and connect to the local IP from inside my network. But when I do this, I cannot connect to the public address from the Internet.


Many home or commodity routers do not provide NAT loopback (allows you to use your WAN IP on the LAN).  Yours sounds like it does not.  Access your LAN services when on the LAN via a LAN IP, not a WAN IP.  And vice versa, of course.

---

### Post by blx_286 on 2008-03-09
> **Mr. C. said:**
>  I'm in the camp that prefers to maintain and track my own configurations, and backup the necessary files I know I need. .

I am real big on documentation, so I imagine I will end up in this camp also.

>  There are lots of options; you can track which configuration files you create when you install and configure a service, you can create timestamp lists and compare before / after to see which files you want to backup, or you can use dd or similar tools to backup the entire file system

I'm an old DOS guy and not up to speed on all of the Linux commands yet, but I'll get there. Thanks for your help with my virtual user problem.

---

### Post by ricketick on 2008-03-10
> **Mr. C. said:**
> Sorry for the delay - do either / both of you still need help with this ?
Not at the moment :) Thanks for your help.

---

