---
title: "vsftpd -- how to stop it asking for username / pasword?"
date: 2010-03-19
forum: Server Platforms
---

### Post by SlugSlug on 2010-03-19
I have installed vsftpd and would like it to be completely accessible to the world, but each time I test connect it propts for username / password.

can anyone help  heres the config:


#
# Sample anonymous FTP server configuration
#
# Mandatory directives
#
listen=YES
local_enable=NO
anonymous_enable=YES
write_enable=NO
anon_root=/Downloads/ftp
#
# Optional directives
#
anon_max_rate=2048000
xferlog_enable=YES
#listen_address=192.168.0.100
listen_port=21

---

### Post by hessiess on 2010-03-19
Unless its only assessable on your private network, this is a very bad idea from a security point of view.

---

### Post by SlugSlug on 2010-03-19
is it really though?

I mean what can happen I want to share a folder (/Downloads/ftp) and just see if it gets used etc..

once someone has ftp access -- is it possible for them to do anything eles outside of /Downloads/ftp

?

---

### Post by cdenley on 2010-03-19
It is possible to configure vsftpd to not prompt for a password when the anonymous username is given (no_anon_password=YES), but I don't think it is possible to not prompt for a username. The username "anonymous" must be given for all anonymous ftp sessions, as far as I know.

[http://en.wikipedia.org/wiki/File_Transfer_Protocol#Anonymous_FTP](http://en.wikipedia.org/wiki/File_Transfer_Protocol#Anonymous_FTP)

---

### Post by SlugSlug on 2010-03-19
thanks,

do you know of a alternative ftp server that will do what i want ?

---

### Post by cdenley on 2010-03-19
> **SlugSlug said:**
> thanks,

do you know of a alternative ftp server that will do what i want ?

I don't think any FTP server will. It probably wouldn't be standards compliant, and clients wouldn't work with it.

[http://www.ietf.org/rfc/rfc0959.txt](http://www.ietf.org/rfc/rfc0959.txt)
> The argument field is a Telnet string identifying the user.
            [B]The user identification is that which is required by the
            server for access to its file system.  This command will
            normally be the first command transmitted by the user after
            the control connections are made (some servers may require
            this).  Additional identification information in the form of
            a password and/or an account command may also be required by
            some servers.[/B]  Servers may allow a new USER command to be
            entered at any point in order to change the access control
            and/or accounting information.  This has the effect of
            flushing any user, password, and account information already
            supplied and beginning the login sequence again.  All
            transfer parameters are unchanged and any file transfer in
            progress is completed under the old access control
            parameters.

If I read that correctly, it should be possible for the server not to require the client to send the USER command and just assume an anonymous connection, but since many servers require it, you probably won't find a client that doesn't prompt for the user so it can send the "USER" command before you can provide any "cd" or "dir" commands to the client. As a result, I doubt you will find any FTP server which assumes an anonymous connection until a user is specified.

---

### Post by SlugSlug on 2010-03-19
what about this for an example

_[ftp://adeskftp.autodesk.com/](ftp://adeskftp.autodesk.com/)_

---

### Post by cdenley on 2010-03-19
> **SlugSlug said:**
> what about this for an example

_[ftp://adeskftp.autodesk.com/](ftp://adeskftp.autodesk.com/)_

It requires you specify a username and password.
```

[COLOR="Silver"]cdenley@ubuntu:~$[/COLOR] nc adeskftp.autodesk.com 21
220 adeskftp01 Microsoft FTP Service (Version 5.0).
CWD /
530 Please login with USER and PASS.
QUIT
221  
[COLOR="Silver"]cdenley@ubuntu:~$[/COLOR] nc adeskftp.autodesk.com 21
220 adeskftp01 Microsoft FTP Service (Version 5.0).
USER anonymous 
331 Anonymous access allowed, send identity (e-mail name) as password.
PASS whatever
230-Welcome to the Autodesk FTP Server.
230 Anonymous user logged in.
CWD /
250 CWD command successful.
QUIT

```

---

### Post by SlugSlug on 2010-03-19
humm..

well using firefox I got straight through to the ftp listing  on that site - but on mine an prompted with a login box

---

### Post by cdenley on 2010-03-19
> **SlugSlug said:**
> humm..

well using firefox I got straight through to the ftp listing  on that site - but on mine an prompted with a login box

Did you read that wikipedia article I linked to? Many FTP client (such as firefox and most web browser) will initially attempt to use an anonymous login. If that fails, then the user is prompted for a login. Your server must not be configured for anonymous login, which is certainly possible with vsftpd. Did you restart vsftpd after reconfiguring it?

---

### Post by SlugSlug on 2010-03-19
I did restart yer,

I'll try a diff server another day, I was just curious as to weather an open ftp would get used and how much

---

### Post by cdenley on 2010-03-19
> **SlugSlug said:**
> I did restart yer,

I'll try a diff server another day, I was just curious as to weather an open ftp would get used and how much

Like I said, vsftpd can certainly be configured as an open/anonymous FTP. I'm currently running one right now. I never thought to track how many people establish anonymous connections, but I never received an anonymous upload we weren't expecting. I did set up an FTP honeypot once that wouldn't allow any username and password (anonymous or not), and plenty of people/bots took a crack at guessing the username/password.

my FTP honeypot:
[http://chrisdenley.com/ftp_honey/](http://chrisdenley.com/ftp_honey/)

---

### Post by SlugSlug on 2010-03-19
nice,
would you mind posting your vsftpd.conf?

quite surprised you never received an unexpected transfer

---

### Post by cdenley on 2010-03-19
> **SlugSlug said:**
> nice,
would you mind posting your vsftpd.conf?

quite surprised you never received an unexpected transfer

My setup is a little complicated as each connection uses it's own configuration file, but this is most of my configuration for anonymous users.
```

listen=NO
anonymous_enable=YES
write_enable=YES
anon_upload_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=MY BANNER
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
download_enable=NO
hide_ids=YES
no_anon_password=YES
ssl_enable=YES
allow_anon_ssl=YES
hide_file={MY HIDDEN DIRECTORY FOR BACKWARDS COMPATIBILITY}
pasv_address=MY WAN ADDRESS
pasv_min_port=33564
pasv_max_port=33584

```

You probably don't want to set "listen" to "NO", by the way.

I was also surprised I never received any unexpected uploads as well. It has been up for 3 years. I receive an e-mail for each anonymous upload. I'm pretty sure everything was legitimate, although I guess I can't say I'm 100% sure. Never received any windows executables or anything.

---

### Post by SlugSlug on 2010-03-19
> **cdenley said:**
> My setup is a little complicated as each connection uses it's own configuration file, but this is most of my configuration for anonymous users.
```

listen=NO
anonymous_enable=YES
write_enable=YES
anon_upload_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=MY BANNER
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
download_enable=NO
hide_ids=YES
no_anon_password=YES
ssl_enable=YES
allow_anon_ssl=YES
hide_file={MY HIDDEN DIRECTORY FOR BACKWARDS COMPATIBILITY}
pasv_address=MY WAN ADDRESS
pasv_min_port=33564
pasv_max_port=33584

```You probably don't want to set "listen" to "NO", by the way.

I was also surprised I never received any unexpected uploads as well. It has been up for 3 years. I receive an e-mail for each anonymous upload. I'm pretty sure everything was legitimate, although I guess I can't say I'm 100% sure. Never received any windows executables or anything.

Brill thanks! - no password box !! how do I make it go to /Downloads/ftp  and so no one can go outside of the ftp folder?

---

### Post by cdenley on 2010-03-19
> **SlugSlug said:**
> Brill thanks! - no password box !! how do I make it go to /Downloads/ftp  and so no one can go outside of the ftp folder?

That was part of my dynamic configuration, which is why it wasn't posted before. Every connection gets its own root directory on my server. Anyway, for anonymous connections
```

anon_root=/Downloads/ftp

```

There is a manpage with a comprehensive list of all supported configuration options, by the way.
```

man vsftpd.conf

```

---

### Post by SlugSlug on 2010-03-19
duplicated

---

