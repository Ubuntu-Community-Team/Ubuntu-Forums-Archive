---
title: "How to Install an FTP over SSL Server (FTPS)"
date: 2012-10-26
forum: Server Platforms
---

### Post by LHammonds on 2012-10-26
Greetings and salutations,

I hope this thread will be helpful to those who follow in my foot steps as well as getting any advice based on what I have done / documented.

For the most current version of this thread, please use the source (original) thread here: [LHammonds Forums]("http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=197")

[SIZE=4]High-level overview[/SIZE]

This document will describe how to setup an FTP server which utilizes SSL (FTPS) encryption and local login IDs to allow users to login and upload files but cannot login to the console.

[SIZE=4]Tools utilized in this process[/SIZE]


[LIST]
[*][Ubuntu Server]("http://www.ubuntu.com/download/ubuntu/download") 12.04.1 LTS, 64-bit
[*][Portable PuTTY]("http://portableapps.com/apps/internet/putty_portable") 0.62
[*]vsftpd 2.3.5
[*]sendemail 1.56
[*]ftp-ssl (Linux client)
[*][SmartFTP]("http://www.smartftp.com/") 4.1.1278.0, 64-bit (Windows client)
[/LIST]


[SIZE=4]Helpful links[/SIZE]

The list below are sources of information that helped me configure this system.


[LIST]
[*][Ubuntu Help - FTP Server]("https://help.ubuntu.com/12.04/serverguide/ftp-server.html")
[*][Ubuntu Help - vsftpd.conf man page]("http://manpages.ubuntu.com/manpages/precise/en/man5/vsftpd.conf.5.html")
[*][vsftpd website (vsftp.conf)]("http://vsftpd.beasts.org/vsftpd_conf.html")
[*][Help Desk Screeds - Install FTP Server with vsftpd on Ubuntu 12.04 Precise Pangolin]("http://www.jonathanmoeller.com/screed/?p=3615")
[/LIST]


[SIZE=4]Assumptions[/SIZE]

This documentation will need to make use of some very-specific information that will most-likely be different for each person / location. This variable data will be noted in this section and highlighted in red throughout the document as a reminder that you should plug-in your own value rather than actually using these "place-holder" values.

Under no circumstance should you use the actual values listed below. They are place-holders for the real thing. This is just a checklist template you need to have answered before you start the install process.

Wherever you see [COLOR=red]RED[/COLOR] in this document, you need to substitute it for what your company uses.


[LIST]
[*]Minimum Passive Port: [COLOR=red]9000[/COLOR]
[*]Maximum Passive Port: [COLOR=red]9020[/COLOR]
[*]FTP User Account: [COLOR=red]myftp[/COLOR]
[*]FTP User Password: [COLOR=red]mypass123[/COLOR]
[/LIST]

---

### Post by LHammonds on 2012-10-26
[SIZE=4]Install Ubuntu Server[/SIZE]

The 1st thing to do is the installation of Ubuntu Server.  The following guide will describe how to setup a server for use in a production environment and this document assumes the guide was followed to setup Ubuntu.

The tutorial also contains an "Assumption" section with variables colored in RED, instead of using those values, this guide will instead use the following as replacements:

Ubuntu Server name: [COLOR=red]srv-ftps[/COLOR]
Ubuntu Server IP address: [COLOR=red]192.168.107.28[/COLOR]

[COLOR=red]**IMPORTANT**[/COLOR]: Keep in mind, these are typically different for each site/install.  Do not use these exact values yourself...make up your own that matches your environment, write them down and use them instead of the values in the guide.

NOTE: These are the sections you can skip in the install guide which are not necessary for this server (however, you might want them...it is up to you):


[LIST]
[*]Configure Ubuntu for File Sharing (Samba)
[*]Configure Windows Server as a Remote Mount Point
[*]SSH Public and Private Keys
[/LIST]

Follow the [How to Install Ubuntu Server]("http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=191") guide and come back when finished.

---

### Post by LHammonds on 2012-10-26
[SIZE=4]Install FTP Service[/SIZE]

At the login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR])

At the $ prompt, temporarily grant yourself super user privileges by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password ([COLOR=red]myadminpass[/COLOR]).

Install vsftpd and make a backup of the original config file.
```

aptitude -y install vsftpd
cp /etc/vsftpd.conf /etc/vsftpd.bak

```
[SIZE=4]Generate an SSL Certificate[/SIZE]

```

openssl req -x509 -nodes -days 730 -newkey rsa:2048 -keyout /etc/ssl/private/vsftpd.pem -out /etc/ssl/private/vsftpd.pem
chown root:ftp /etc/ssl/private/vsftpd.pem
chmod 644 /etc/ssl/private/vsftpd.pem

```
[SIZE=4]Configure vsftpd[/SIZE]

Edit /etc/vsftpd.conf and find/uncomment following lines:
```

local_enable=YES
write_enable=YES
local_umask=022
ftpd_banner=Welcome to our FTP server.
chroot_local_user=YES

```Find the following existing lines and change the values as follows:
```

anonymous_enable=NO
connect_from_port_20=NO
rsa_cert_file=/etc/ssl/certs/vsftpd.pem

```Add the following new lines (feel free to adjust values as desired):
```

listen_port=990

# Turn on SSL
ssl_enable=YES

# Allow anonymous users to use secured SSL connections
allow_anon_ssl=NO

# All non-anonymous logins are forced to use a secure SSL connection in order to
# send and receive data on data connections.
force_local_data_ssl=YES

# All non-anonymous logins are forced to use a secure SSL connection in order to send the password.
force_local_logins_ssl=YES

# Permit TLS v1 protocol connections. TLS v1 connections are preferred
ssl_tlsv1=YES

# Permit SSL v2 protocol connections. TLS v1 connections are preferred
ssl_sslv2=YES

# permit SSL v3 protocol connections. TLS v1 connections are preferred
ssl_sslv3=YES

# Hide the info about the owner (user and group) of the files.
hide_ids=YES

# Connection limit for each IP:
max_per_ip=10

# Maximum number of clients:
max_clients=10

# When port_enabled is YES, active mode connects are allowed.
port_enable=YES

# When pasv_enable is YES, passive mode connects are allowed.
pasv_enable=YES

# pasv_min_port specifies the lowest possible port sent to the FTP clients for passive mode connections. This setting is used to limit the port range so that firewall rules are easier to create. The value must not be lower than 1024.
pasv_min_port=[COLOR=red]9000[/COLOR]

# pasv_max_port specifies the highest possible port sent to the FTP clients for passive mode connections. This setting is used to limit the port range so that firewall rules are easier to create. The value must not exceed 65535.
pasv_max_port=[COLOR=red]9020[/COLOR]

# require_ssl_reuse, if YES, all SSL data connections are required to exhibit SSL session reuse.  Set to NO if your log shows failures to upload because of no session reuse.

require_ssl_reuse=NO

```

---

### Post by LHammonds on 2012-10-26
[SIZE=4]Configure User Accounts[/SIZE]

At the login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR])

At the $ prompt, temporarily grant yourself super user privileges by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password ([COLOR=red]myadminpass[/COLOR]).

Add an ftpusers group.
```

addgroup ftpusers

```Use the default ftp folder of /srv/ftp but move the home directory of the default "ftp" account underneath that folder.  The /srv/ftp folder will be become the base folder for all FTP user accounts but nobody will be able to access it directly.

```

mkdir -p /srv/ftp/ftp/public
usermod -d /srv/ftp/ftp ftp
chmod 555 /srv/ftp
chmod 555 /srv/ftp/ftp
chmod 755 /srv/ftp/ftp/public
chown -R ftp:ftpusers /srv/ftp/ftp

```Type this to add /usr/sbin/nologin to /etc/shells (* This allows users to login via FTP which cannot login directly on the server *)
```

echo "/usr/sbin/nologin" >> /etc/shells

```Now add a user called [COLOR=red]myftp[/COLOR] with a password of [COLOR=red]mypass123[/COLOR]

```

mkdir -p /srv/ftp/[COLOR=red]myftp[/COLOR]/public
chmod 555 /srv/ftp/[COLOR=red]myftp[/COLOR]
chmod 755 /srv/ftp/[COLOR=red]myftp[/COLOR]/public
useradd -g ftpusers -d /srv/ftp/[COLOR=red]myftp[/COLOR] -s /usr/sbin/nologin [COLOR=red]myftp[/COLOR]
chown -R [COLOR=red]myftp[/COLOR]:ftpusers /srv/ftp/[COLOR=red]myftp[/COLOR]
passwd [COLOR=red]myftp[/COLOR]
[COLOR=red]mypass123[/COLOR]

```

---

### Post by LHammonds on 2012-10-26
[SIZE=4]Configure Firewall/Router[/SIZE]

Configure your firewall/router to allow your external IP to route to your internal IP on port 990 and a port range of [COLOR=red]9000[/COLOR] to [COLOR=red]9020[/COLOR] (for passive mode connections)


[SIZE=4]Connect via FTP Clients[/SIZE]

It is recommended to test client connectivity from the local area network (LAN) to make sure everything is working before trying to test from outside the LAN.  This will help with troubleshooting if necessary.

If you have another Linux server on the LAN, login to that server and type the following to test out the FTP capability:
```

aptitude -y install ftp-ssl
ftp-ssl [COLOR=red]192.168.107.28[/COLOR] 990
[COLOR=red]myftp[/COLOR]
[COLOR=red]mypass123[/COLOR]
cd /public
pwd
lcd /etc
put hosts
dir
del hosts
dir
quit

```

To test from Windows over the LAN, use SmartFTP with the FTPS protocol and connect to the internal IP address.

Name: My FTPS Server
Protocol: FTPS (Explicit)
Host: [COLOR=red]192.168.107.28[/COLOR]
Port: 990
Path: /public
Timezone: Automatic
Login Type: Username & Password
Username: [COLOR=red]myftp[/COLOR]
Password: [COLOR=red]mypass123[/COLOR]

Once you verified that it works on your LAN, you can now test the connection from the outside through your firewall/router by connecting to the external IP from a PC/Server outside of your LAN.

---

