---
title: "Confusion around setting up vsftpd"
date: 2012-07-15
forum: Server Platforms
---

### Post by two00lbwaster on 2012-07-15
Hi there,

I have set up a LAMP stacked server for hosting a few Wordpress sites on a free tier EC2 instance.

However, Wordpress seems to want to update via FTP, so I'm looking to set up segregated(chrooted) FTP users that only have access to their own directory, which is where the website is; /home/user/www/user.com

I have been trying to set up the local users so that they can log into the server with the user account credentials.  Unfortunately, everything that I do just doesn't seem to want to work.  All the instructions seem to be written with a single user accessing a single folder (as if noone bothers setting webservers for multiple websites anymore and just use cpanel/plesk instead.)

---

### Post by Ji Ruo on 2012-07-16
My first thought is that you are using 12.04 (vsftpd version 2.3.5) and are getting this error:

[http://askubuntu.com/questions/128180/vsftpd-stopped-working-after-update](http://askubuntu.com/questions/128180/vsftpd-stopped-working-after-update)

Is this what's happening? If not could you be more specific about the problems you are getting.

---

### Post by two00lbwaster on 2012-07-17
> **Ji Ruo said:**
> My first thought is that you are using 12.04 (vsftpd version 2.3.5) and are getting this error:

[http://askubuntu.com/questions/128180/vsftpd-stopped-working-after-update](http://askubuntu.com/questions/128180/vsftpd-stopped-working-after-update)

Is this what's happening? If not could you be more specific about the problems you are getting.

I don't think that that is the issue.

Below is the log from WinSCP when it's trying to connect to my server using the local username:

```
. 2012-07-17 22:00:37.670 --------------------------------------------------------------------------
. 2012-07-17 22:00:37.670 WinSCP Version 4.3.8 (Build 1771) (OS 6.1.7601 Service Pack 1)
. 2012-07-17 22:00:37.670 Configuration: HKEY_CURRENT_USER\Software\Martin Prikryl\WinSCP 2\
. 2012-07-17 22:00:37.670 Local account: somename\somename
. 2012-07-17 22:00:37.670 Login time: 17 July 2012 22:00:37
. 2012-07-17 22:00:37.670 --------------------------------------------------------------------------
. 2012-07-17 22:00:37.670 Session name: somename@somename.co.uk (Stored session)
. 2012-07-17 22:00:37.670 Host name: somename.co.uk (Port: 21)
. 2012-07-17 22:00:37.671 User name: somename (Password: Yes, Key file: No)
. 2012-07-17 22:00:37.671 Tunnel: No
. 2012-07-17 22:00:37.671 Transfer Protocol: FTP
. 2012-07-17 22:00:37.671 Ping type: C, Ping interval: 30 sec; Timeout: 15 sec
. 2012-07-17 22:00:37.671 Proxy: none
. 2012-07-17 22:00:37.671 FTP: FTPS: None; Passive: Yes [Force IP: No]
. 2012-07-17 22:00:37.671 Local directory: default, Remote directory: home, Update: No, Cache: Yes
. 2012-07-17 22:00:37.671 Cache directory changes: Yes, Permanent: Yes
. 2012-07-17 22:00:37.671 DST mode: 1
. 2012-07-17 22:00:37.671 --------------------------------------------------------------------------
. 2012-07-17 22:00:37.722 Connecting to somename.co.uk ...
. 2012-07-17 22:00:37.752 Connected with somename.co.uk. Waiting for welcome message...
< 2012-07-17 22:00:37.806 220 Welcome to an FTP server.
> 2012-07-17 22:00:37.806 USER somename
< 2012-07-17 22:00:37.864 331 Please specify the password.
> 2012-07-17 22:00:37.865 PASS **************
< 2012-07-17 22:00:37.928 230 Login successful.
> 2012-07-17 22:00:37.928 SYST
< 2012-07-17 22:00:37.964 215 UNIX Type: L8
> 2012-07-17 22:00:37.964 FEAT
< 2012-07-17 22:00:38.022 211-Features:
< 2012-07-17 22:00:38.023  EPRT
< 2012-07-17 22:00:38.023  EPSV
< 2012-07-17 22:00:38.023  MDTM
< 2012-07-17 22:00:38.023  PASV
< 2012-07-17 22:00:38.023  REST STREAM
< 2012-07-17 22:00:38.023  SIZE
< 2012-07-17 22:00:38.023  TVFS
< 2012-07-17 22:00:38.023  UTF8
< 2012-07-17 22:00:38.023 211 End
> 2012-07-17 22:00:38.023 OPTS UTF8 ON
< 2012-07-17 22:00:38.141 200 Always in UTF8 mode.
. 2012-07-17 22:00:38.142 Connected
. 2012-07-17 22:00:38.142 --------------------------------------------------------------------------
. 2012-07-17 22:00:38.142 Using FTP protocol.
. 2012-07-17 22:00:38.142 Doing startup conversation with host.
> 2012-07-17 22:00:38.143 PWD
< 2012-07-17 22:00:38.190 257 "/home/somename"
. 2012-07-17 22:00:38.191 Getting current directory name.
. 2012-07-17 22:00:38.193 Retrieving directory listing...
> 2012-07-17 22:00:38.193 TYPE A
< 2012-07-17 22:00:38.227 200 Switching to ASCII mode.
> 2012-07-17 22:00:38.227 PASV
< 2012-07-17 22:00:38.292 227 Entering Passive Mode (10,250,203,13,154,75).
> 2012-07-17 22:00:38.292 LIST -a
. 2012-07-17 22:00:53.894 Timeout detected.
. 2012-07-17 22:00:53.894 Could not retrieve directory listing
. 2012-07-17 22:00:53.894 Connection was lost, asking what to do.
. 2012-07-17 22:00:53.894 Asking user:
. 2012-07-17 22:00:53.894 Lost connection. ("Timeout detected.","Could not retrieve directory listing","Entering Passive Mode (10,250,203,13,154,75).")
. 2012-07-17 22:00:58.968 Connecting to somename.co.uk ...
. 2012-07-17 22:00:58.992 Connected with somename.co.uk. Waiting for welcome message...
< 2012-07-17 22:00:59.032 220 Welcome to an FTP server.
> 2012-07-17 22:00:59.032 USER somename
< 2012-07-17 22:00:59.080 331 Please specify the password.
> 2012-07-17 22:00:59.080 PASS **************
< 2012-07-17 22:00:59.170 230 Login successful.
> 2012-07-17 22:00:59.170 SYST
< 2012-07-17 22:00:59.206 215 UNIX Type: L8
> 2012-07-17 22:00:59.206 FEAT
< 2012-07-17 22:00:59.230 211-Features:
< 2012-07-17 22:00:59.230  EPRT
< 2012-07-17 22:00:59.230  EPSV
< 2012-07-17 22:00:59.230  MDTM
< 2012-07-17 22:00:59.230  PASV
< 2012-07-17 22:00:59.230  REST STREAM
< 2012-07-17 22:00:59.230  SIZE
< 2012-07-17 22:00:59.230  TVFS
< 2012-07-17 22:00:59.230  UTF8
< 2012-07-17 22:00:59.230 211 End
> 2012-07-17 22:00:59.230 OPTS UTF8 ON
< 2012-07-17 22:00:59.280 200 Always in UTF8 mode.
. 2012-07-17 22:00:59.282 Connected
. 2012-07-17 22:00:59.282 Doing startup conversation with host.
> 2012-07-17 22:00:59.284 PWD
< 2012-07-17 22:00:59.306 257 "/home/somename"
. 2012-07-17 22:00:59.308 Changing directory to "/home/somename".
> 2012-07-17 22:00:59.308 CWD /home/somename
< 2012-07-17 22:00:59.359 250 Directory successfully changed.
. 2012-07-17 22:00:59.359 Getting current directory name.
> 2012-07-17 22:00:59.359 PWD
< 2012-07-17 22:00:59.414 257 "/home/somename"
. 2012-07-17 22:00:59.414 Startup conversation with host finished.
. 2012-07-17 22:00:59.420 Retrieving directory listing...
> 2012-07-17 22:00:59.420 TYPE A
< 2012-07-17 22:00:59.458 200 Switching to ASCII mode.
> 2012-07-17 22:00:59.458 PASV
< 2012-07-17 22:00:59.488 227 Entering Passive Mode (10,250,203,13,62,229).
> 2012-07-17 22:00:59.488 LIST
. 2012-07-17 22:01:14.175 Timeout detected.
. 2012-07-17 22:01:14.175 Could not retrieve directory listing
* 2012-07-17 22:01:14.175 (ESshFatal) Lost connection.
* 2012-07-17 22:01:14.175 Timeout detected.
* 2012-07-17 22:01:14.175 Could not retrieve directory listing
* 2012-07-17 22:01:14.175 Entering Passive Mode (10,250,203,13,62,229).
* 2012-07-17 22:01:14.175 Error listing directory '/home/somename'.
. 2012-07-17 22:01:19.275 Connecting to somename.co.uk ...
. 2012-07-17 22:01:19.296 Connected with somename.co.uk. Waiting for welcome message...
< 2012-07-17 22:01:19.320 220 Welcome to an FTP server.
> 2012-07-17 22:01:19.320 USER somename
< 2012-07-17 22:01:19.346 331 Please specify the password.
> 2012-07-17 22:01:19.346 PASS **************
< 2012-07-17 22:01:19.471 230 Login successful.
> 2012-07-17 22:01:19.471 SYST
< 2012-07-17 22:01:19.509 215 UNIX Type: L8
> 2012-07-17 22:01:19.509 FEAT
< 2012-07-17 22:01:19.563 211-Features:
< 2012-07-17 22:01:19.563  EPRT
< 2012-07-17 22:01:19.563  EPSV
< 2012-07-17 22:01:19.563  MDTM
< 2012-07-17 22:01:19.563  PASV
< 2012-07-17 22:01:19.563  REST STREAM
< 2012-07-17 22:01:19.563  SIZE
< 2012-07-17 22:01:19.563  TVFS
< 2012-07-17 22:01:19.563  UTF8
< 2012-07-17 22:01:19.563 211 End
> 2012-07-17 22:01:19.563 OPTS UTF8 ON
< 2012-07-17 22:01:19.599 200 Always in UTF8 mode.
. 2012-07-17 22:01:19.600 Connected
. 2012-07-17 22:01:19.600 Doing startup conversation with host.
> 2012-07-17 22:01:19.601 PWD
< 2012-07-17 22:01:19.637 257 "/home/somename"
. 2012-07-17 22:01:19.638 Getting current directory name.
. 2012-07-17 22:01:19.640 Retrieving directory listing...
> 2012-07-17 22:01:19.640 TYPE A
< 2012-07-17 22:01:19.678 200 Switching to ASCII mode.
> 2012-07-17 22:01:19.678 PASV
< 2012-07-17 22:01:19.715 227 Entering Passive Mode (10,250,203,13,58,134).
> 2012-07-17 22:01:19.715 LIST
. 2012-07-17 22:01:34.455 Timeout detected.
. 2012-07-17 22:01:34.455 Could not retrieve directory listing
* 2012-07-17 22:01:34.460 (ESshFatal) Lost connection.
* 2012-07-17 22:01:34.460 Timeout detected.
* 2012-07-17 22:01:34.460 Could not retrieve directory listing
* 2012-07-17 22:01:34.460 Entering Passive Mode (10,250,203,13,58,134).
* 2012-07-17 22:01:34.460 Error listing directory '/home/somename'.
. 2012-07-17 22:01:39.550 Connecting to somename.co.uk ...
. 2012-07-17 22:01:39.571 Connected with somename.co.uk. Waiting for welcome message...
< 2012-07-17 22:01:39.596 220 Welcome to an FTP server.
> 2012-07-17 22:01:39.596 USER somename
< 2012-07-17 22:01:39.642 331 Please specify the password.
> 2012-07-17 22:01:39.643 PASS **************
< 2012-07-17 22:01:39.684 230 Login successful.
> 2012-07-17 22:01:39.684 SYST
< 2012-07-17 22:01:39.734 215 UNIX Type: L8
> 2012-07-17 22:01:39.734 FEAT
< 2012-07-17 22:01:39.757 211-Features:
< 2012-07-17 22:01:39.757  EPRT
< 2012-07-17 22:01:39.757  EPSV
< 2012-07-17 22:01:39.757  MDTM
< 2012-07-17 22:01:39.757  PASV
< 2012-07-17 22:01:39.757  REST STREAM
< 2012-07-17 22:01:39.757  SIZE
< 2012-07-17 22:01:39.757  TVFS
< 2012-07-17 22:01:39.757  UTF8
< 2012-07-17 22:01:39.757 211 End
> 2012-07-17 22:01:39.757 OPTS UTF8 ON
< 2012-07-17 22:01:39.799 200 Always in UTF8 mode.
. 2012-07-17 22:01:39.800 Connected
. 2012-07-17 22:01:39.800 Doing startup conversation with host.
> 2012-07-17 22:01:39.801 PWD
< 2012-07-17 22:01:39.859 257 "/home/somename"
. 2012-07-17 22:01:39.860 Getting current directory name.
. 2012-07-17 22:01:39.864 Retrieving directory listing...
> 2012-07-17 22:01:39.864 TYPE A
< 2012-07-17 22:01:39.902 200 Switching to ASCII mode.
> 2012-07-17 22:01:39.902 PASV
< 2012-07-17 22:01:39.961 227 Entering Passive Mode (10,250,203,13,248,239).
> 2012-07-17 22:01:39.961 LIST
. 2012-07-17 22:01:54.735 Timeout detected.
. 2012-07-17 22:01:54.735 Could not retrieve directory listing
* 2012-07-17 22:01:54.738 (ESshFatal) Lost connection.
* 2012-07-17 22:01:54.738 Timeout detected.
* 2012-07-17 22:01:54.739 Could not retrieve directory listing
* 2012-07-17 22:01:54.739 Entering Passive Mode (10,250,203,13,248,239).
* 2012-07-17 22:01:54.739 Error listing directory '/home/somename'.
. 2012-07-17 22:01:59.830 Connecting to somename.co.uk ...
. 2012-07-17 22:01:59.861 Connected with somename.co.uk. Waiting for welcome message...
< 2012-07-17 22:01:59.884 220 Welcome to an FTP server.
> 2012-07-17 22:01:59.884 USER somename
< 2012-07-17 22:02:00.002 331 Please specify the password.
> 2012-07-17 22:02:00.002 PASS **************
< 2012-07-17 22:02:00.085 230 Login successful.
> 2012-07-17 22:02:00.085 SYST
< 2012-07-17 22:02:00.110 215 UNIX Type: L8
> 2012-07-17 22:02:00.110 FEAT
< 2012-07-17 22:02:00.230 211-Features:
< 2012-07-17 22:02:00.230  EPRT
< 2012-07-17 22:02:00.230  EPSV
< 2012-07-17 22:02:00.230  MDTM
< 2012-07-17 22:02:00.230  PASV
< 2012-07-17 22:02:00.230  REST STREAM
< 2012-07-17 22:02:00.230  SIZE
< 2012-07-17 22:02:00.231  TVFS
< 2012-07-17 22:02:00.231  UTF8
< 2012-07-17 22:02:00.231 211 End
> 2012-07-17 22:02:00.231 OPTS UTF8 ON
< 2012-07-17 22:02:00.303 200 Always in UTF8 mode.
. 2012-07-17 22:02:00.304 Connected
. 2012-07-17 22:02:00.304 Doing startup conversation with host.
> 2012-07-17 22:02:00.305 PWD
< 2012-07-17 22:02:00.347 257 "/home/somename"
. 2012-07-17 22:02:00.349 Getting current directory name.
. 2012-07-17 22:02:00.350 Retrieving directory listing...
> 2012-07-17 22:02:00.350 TYPE A
< 2012-07-17 22:02:00.371 200 Switching to ASCII mode.
> 2012-07-17 22:02:00.371 PASV
< 2012-07-17 22:02:00.395 227 Entering Passive Mode (10,250,203,13,88,144).
> 2012-07-17 22:02:00.395 LIST
. 2012-07-17 22:02:15.016 Timeout detected.
. 2012-07-17 22:02:15.016 Could not retrieve directory listing
* 2012-07-17 22:02:15.019 (ESshFatal) Lost connection.
* 2012-07-17 22:02:15.019 Timeout detected.
* 2012-07-17 22:02:15.019 Could not retrieve directory listing
* 2012-07-17 22:02:15.019 Entering Passive Mode (10,250,203,13,88,144).
* 2012-07-17 22:02:15.019 Error listing directory '/home/somename'.
. 2012-07-17 22:02:20.109 Connecting to somename.co.uk ...
. 2012-07-17 22:02:20.134 Connected with somename.co.uk. Waiting for welcome message...
< 2012-07-17 22:02:20.158 220 Welcome to an FTP server.
> 2012-07-17 22:02:20.158 USER somename
< 2012-07-17 22:02:20.180 331 Please specify the password.
> 2012-07-17 22:02:20.180 PASS **************
< 2012-07-17 22:02:20.245 230 Login successful.
> 2012-07-17 22:02:20.245 SYST
< 2012-07-17 22:02:20.282 215 UNIX Type: L8
> 2012-07-17 22:02:20.282 FEAT
< 2012-07-17 22:02:20.344 211-Features:
< 2012-07-17 22:02:20.344  EPRT
< 2012-07-17 22:02:20.344  EPSV
< 2012-07-17 22:02:20.344  MDTM
< 2012-07-17 22:02:20.344  PASV
< 2012-07-17 22:02:20.344  REST STREAM
< 2012-07-17 22:02:20.344  SIZE
< 2012-07-17 22:02:20.344  TVFS
< 2012-07-17 22:02:20.344  UTF8
< 2012-07-17 22:02:20.344 211 End
> 2012-07-17 22:02:20.344 OPTS UTF8 ON
< 2012-07-17 22:02:20.389 200 Always in UTF8 mode.
. 2012-07-17 22:02:20.390 Connected
. 2012-07-17 22:02:20.390 Doing startup conversation with host.
> 2012-07-17 22:02:20.391 PWD
< 2012-07-17 22:02:20.460 257 "/home/somename"
. 2012-07-17 22:02:20.461 Getting current directory name.
. 2012-07-17 22:02:20.463 Retrieving directory listing...
> 2012-07-17 22:02:20.463 TYPE A
< 2012-07-17 22:02:20.524 200 Switching to ASCII mode.
> 2012-07-17 22:02:20.525 PASV
< 2012-07-17 22:02:20.576 227 Entering Passive Mode (10,250,203,13,243,236).
> 2012-07-17 22:02:20.576 LIST
. 2012-07-17 22:02:35.296 Timeout detected.
. 2012-07-17 22:02:35.296 Could not retrieve directory listing
* 2012-07-17 22:02:35.298 (ESshFatal) Lost connection.
* 2012-07-17 22:02:35.298 Timeout detected.
* 2012-07-17 22:02:35.298 Could not retrieve directory listing
* 2012-07-17 22:02:35.298 Entering Passive Mode (10,250,203,13,243,236).
* 2012-07-17 22:02:35.298 Error listing directory '/home/somename'.
. 2012-07-17 22:02:40.390 Connecting to somename.co.uk ...
. 2012-07-17 22:02:40.400 Connected with somename.co.uk. Waiting for welcome message...
< 2012-07-17 22:02:40.433 220 Welcome to an FTP server.
> 2012-07-17 22:02:40.433 USER somename
< 2012-07-17 22:02:40.476 331 Please specify the password.
> 2012-07-17 22:02:40.476 PASS **************
< 2012-07-17 22:02:40.568 230 Login successful.
> 2012-07-17 22:02:40.568 SYST
< 2012-07-17 22:02:40.599 215 UNIX Type: L8
> 2012-07-17 22:02:40.600 FEAT
< 2012-07-17 22:02:40.635 211-Features:
< 2012-07-17 22:02:40.635  EPRT
< 2012-07-17 22:02:40.636  EPSV
< 2012-07-17 22:02:40.636  MDTM
< 2012-07-17 22:02:40.636  PASV
< 2012-07-17 22:02:40.636  REST STREAM
< 2012-07-17 22:02:40.636  SIZE
< 2012-07-17 22:02:40.636  TVFS
< 2012-07-17 22:02:40.636  UTF8
< 2012-07-17 22:02:40.636 211 End
> 2012-07-17 22:02:40.636 OPTS UTF8 ON
< 2012-07-17 22:02:40.694 200 Always in UTF8 mode.
. 2012-07-17 22:02:40.695 Connected
. 2012-07-17 22:02:40.695 Doing startup conversation with host.
> 2012-07-17 22:02:40.696 PWD
< 2012-07-17 22:02:40.717 257 "/home/somename"
. 2012-07-17 22:02:40.718 Getting current directory name.
. 2012-07-17 22:02:40.720 Retrieving directory listing...
> 2012-07-17 22:02:40.720 TYPE A
< 2012-07-17 22:02:40.788 200 Switching to ASCII mode.
> 2012-07-17 22:02:40.789 PASV
< 2012-07-17 22:02:40.811 227 Entering Passive Mode (10,250,203,13,44,128).
> 2012-07-17 22:02:40.812 LIST
. 2012-07-17 22:02:55.575 Timeout detected.
. 2012-07-17 22:02:55.576 Could not retrieve directory listing
* 2012-07-17 22:02:55.578 (ESshFatal) Lost connection.
* 2012-07-17 22:02:55.578 Timeout detected.
* 2012-07-17 22:02:55.578 Could not retrieve directory listing
* 2012-07-17 22:02:55.578 Entering Passive Mode (10,250,203,13,44,128).
* 2012-07-17 22:02:55.578 Error listing directory '/home/somename'.
. 2012-07-17 22:03:00.670 Connecting to somename.co.uk ...
. 2012-07-17 22:03:00.691 Connected with somename.co.uk. Waiting for welcome message...
< 2012-07-17 22:03:00.725 220 Welcome to an FTP server.
> 2012-07-17 22:03:00.725 USER somename
< 2012-07-17 22:03:00.750 331 Please specify the password.
> 2012-07-17 22:03:00.750 PASS **************
< 2012-07-17 22:03:00.811 230 Login successful.
> 2012-07-17 22:03:00.811 SYST
< 2012-07-17 22:03:00.839 215 UNIX Type: L8
> 2012-07-17 22:03:00.839 FEAT
< 2012-07-17 22:03:00.885 211-Features:
< 2012-07-17 22:03:00.885  EPRT
< 2012-07-17 22:03:00.885  EPSV
< 2012-07-17 22:03:00.885  MDTM
< 2012-07-17 22:03:00.885  PASV
< 2012-07-17 22:03:00.885  REST STREAM
< 2012-07-17 22:03:00.885  SIZE
< 2012-07-17 22:03:00.885  TVFS
< 2012-07-17 22:03:00.885  UTF8
< 2012-07-17 22:03:00.885 211 End
> 2012-07-17 22:03:00.885 OPTS UTF8 ON
< 2012-07-17 22:03:00.910 200 Always in UTF8 mode.
. 2012-07-17 22:03:00.911 Connected
. 2012-07-17 22:03:00.911 Doing startup conversation with host.
> 2012-07-17 22:03:00.912 PWD
< 2012-07-17 22:03:00.943 257 "/home/somename"
. 2012-07-17 22:03:00.944 Getting current directory name.
. 2012-07-17 22:03:00.945 Retrieving directory listing...
> 2012-07-17 22:03:00.945 TYPE A
< 2012-07-17 22:03:00.992 200 Switching to ASCII mode.
> 2012-07-17 22:03:00.993 PASV
< 2012-07-17 22:03:01.027 227 Entering Passive Mode (10,250,203,13,39,247).
> 2012-07-17 22:03:01.027 LIST
. 2012-07-17 22:03:16.870 Timeout detected.
. 2012-07-17 22:03:16.870 Could not retrieve directory listing
* 2012-07-17 22:03:16.877 (ESshFatal) Lost connection.
* 2012-07-17 22:03:16.877 Timeout detected.
* 2012-07-17 22:03:16.877 Could not retrieve directory listing
* 2012-07-17 22:03:16.877 Entering Passive Mode (10,250,203,13,39,247).
* 2012-07-17 22:03:16.877 Error listing directory '/home/somename'.

```

---

### Post by two00lbwaster on 2012-07-21
Okay, this was absolutely ridiculous to set up and get working as I would expect it to.

[URL="http://serverfault.com/questions/222906/vsftpd-local-root-var-www-sites-user-doesnt-get-interpreted"]
**[COLOR="DarkOrange"]_This link_[/COLOR]**[/URL] helped with getting vsftpd set up so that my users would arrive in the correct directory.  And I only found that post thanks to Wolter Hellmund's comment in [[COLOR="DarkOrange"]_**this post**_[/COLOR]]("http://askubuntu.com/questions/73323/how-to-setup-vsftpd-for-multiple-users-including-adding-specific-directories").

I then had to remove write privileges from the root directory set down in the vsftp config file as below
```
chmod a-w /home/user/www
```

The final piece of the jigsaw was getting passive ftp to work, which is needed for updating, downloading and deleting plugins in Wordpress.  That I found from this following post:
[[COLOR="DarkOrange"]_**http://www.adrianworlddesign.com/Knowledge-Base/Web-Hosting/Amazon-Web-Services/Enable-FTP-in-EC2**_[/COLOR]]("http://www.adrianworlddesign.com/Knowledge-Base/Web-Hosting/Amazon-Web-Services/Enable-FTP-in-EC2")

That was a little more specific to AWS, although, I have rules in place so that I have full port access from my specific IP address.

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
local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
anon_upload_enable=NO
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
ftpd_banner=Welcome to an FTP server.
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
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that
# the user does not have write access to the top level directory within the
# chroot)
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
# Customization
#
# Some of vsftpd's settings don't fit the filesystem layout by
# default.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/private/vsftpd.pem
#
# My Mods
user_config_dir=/etc/vsftpd/users
listen_port=21
# PASV - passive settings for FTP
pasv_enable=YES
# external address of the server
pasv_address=123.123.123.123 
pasv_min_port=3200
pasv_max_port=3300

```

---

