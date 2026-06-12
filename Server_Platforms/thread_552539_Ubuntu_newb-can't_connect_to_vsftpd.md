---
title: "Ubuntu newb-can't connect to vsftpd"
date: 2007-09-16
forum: Server Platforms
---

### Post by Rhcd67 on 2007-09-16
I recently built a Ubuntu server(7.10) with vsftpd and my FTP connections are getting refused.  I am trying to use SecureFX and I get a message saying 

Discarding invalid state change from STATE_NOT_CONNECTED to STATE_CLOSED

I have tried other FTP programs and I get the same result.  Here are some of the options I have enabled in vsftpd.conf based on the tutorial in the Ubuntu Server Guide:

write_enable=YES
enable_ssl=YES
anonymous_enable=NO
local_enable=YES
secure_chroot_dir=/var/vsftpd

Any help would be greatly appreciated.  Thanks.

---

### Post by ruibernardo on 2007-09-16
Hi rhcd67,

maybe your problem is related to the option "enable_ssl=YES". Try to comment it out and then restart the vsfptd service to use the FTP service:

```
 sudo /etc/init.d/vsftpd restart
```If you do want to to use SSL on FTP, I think you have to enable some other options (add the options that aren't on vsftpd.conf):

```
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
```And restart the vsftpd service again. Please note that not all the FTP clients work with SSL.

Take a look [here]("http://ubuntuforums.org/showthread.php?t=518293") to see more details.

---

### Post by Rhcd67 on 2007-09-17
Hello.

Disabling SSL worked, although it still does not work under SSL even with those configuration changes.  I know my client works with SSL since I've used it to connect to other servers with it.  

Is there anywhere else that you know of where SSL has to be enabled?

Thanks for the help.

---

### Post by Wim Sturkenboom on 2007-09-17
Did you create a certificate? And do you use the correct protocol on the client side? Please be aware that a number of clients simply don't support secure ftp.

Example for configuration and some suggested clients: [http://www.brennan.id.au/14-FTP_Server.html](http://www.brennan.id.au/14-FTP_Server.html)

---

### Post by ruibernardo on 2007-09-17
You can create a SSL certificate, but by default VSFTPD uses the one that is created when you install Ubuntu. You can find the reference to it in the end of /etc/vsftpd.conf:

```
 #This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
```With all the SSL/TLS options and the "snake-oil" certificate (or a newly created one), SSL should work with SFTP clients.

---

### Post by Rhcd67 on 2007-09-17
The certificate options are as epimeteo says.  I also checked the directory to make sure they were there, and I was told I did not have permissions to the 'private" directory where ssl-cert-snakeoil.key is stored, and I am logged in as the admin user I created upon installation.  Could this be the problem, and if so how do I get to that file?

---

### Post by ruibernardo on 2007-09-17
That directory is only accessible to the root user (run "sudo -i" to that), but this should not be a problem to run VSFTPD with ssl. Enable the options, restart VSFTPD and login with a FTP client that works with a TLS/SSL enabled FTP clients.

Some of the TLS/SSL enabled FTP clients are on the page that Wim Sturkenboom posted (in the end of the page).

You can confirm if SFTP is really running by installing the package **ftp-ssl** and then execute:

```
 ftp-ssl 127.0.0.1
```and then type your user and password to login. If this works, then VSFTPD is running with SSL.

---

### Post by Rhcd67 on 2007-09-17
ftp: connect: Connection refused

Is there somewhere else I need enable SFTP?

---

### Post by ruibernardo on 2007-09-18
> **Rhcd67 said:**
> ftp: connect: Connection refused

Is there somewhere else I need enable SFTP?

What client are you using?

If you have SSL enabled, you can't login with ftp command or with a normal ftp client. IE or Firefox don't work with FTP/SSL. Please install the ftp-ssl package, or check the compatible clients list in the page posted by Wim Sturkenboom.

---

### Post by Brazen on 2007-09-18
enabling ssl in vsftpd is not the same thing as sftp.  The protocol vsftpd implements is called ftps or ftp/ssl.  This is entirely different than sftp.  If you enable ssl in vsftpd than your client must support the protocol ftps (aka ftp/ssl).  If your client supports sftp but does not support ftps than it will not connect to vsftpd with ssl enabled, no matter what you do.

---

### Post by Rhcd67 on 2007-09-18
> **epimeteo said:**
> What client are you using?

If you have SSL enabled, you can't login with ftp command or with a normal ftp client. IE or Firefox don't work with FTP/SSL. Please install the ftp-ssl package, or check the compatible clients list in the page posted by Wim Sturkenboom.

I'm using SecureFX, and I used it with my old ubuntu server under the same conditions using SFTP with vsftpd.  I have tried SmartFTP from Wim's list and that didn't work either.  Both SecureFX and SmartFTP support FTP/SSL (implicit & explicit) and neither has worked-the machine refuses the connection every time.    

> **Brazen said:**
> enabling ssl in vsftpd is not the same thing as sftp. The protocol vsftpd implements is called ftps or ftp/ssl. This is entirely different than sftp. If you enable ssl in vsftpd than your client must support the protocol ftps (aka ftp/ssl). If your client supports sftp but does not support ftps than it will not connect to vsftpd with ssl enabled, no matter what you do.

I'm confused now-what is the difference between SFTP and FTP/SSL?  


Again, thanks to everyone who has tried to help.

---

### Post by ruibernardo on 2007-09-18
FTPS is FTP/SSL, the FTP protocol with SSL encryption. ([Wikipedia - FPTS]("http://en.wikipedia.org/wiki/Ftps"))

SFTP is FTP over a SSH shell, which needs a SSH server. ([Wikipedia - SFTP]("http://en.wikipedia.org/wiki/Sftp"))

Please check if the ftp-ssl client runs without problems. I suggest you to install the ftp-ssl package and then test it. This client works perfectly with me, so it is a working FTPS client for sure. To test it:

```
 ftp-ssl 127.0.0.1
```Please confirm if that work for you too. If this client works, then you can begin to look with other clients. Check the FTPS page in wikipedia to see more clients that work with FTPS.

NOTE: the ftp-ssl package will uninstall the package ftp. After the test you can reinstall the package ftp if you want.

---

### Post by Rhcd67 on 2007-09-18
> **epimeteo said:**
> FTPS is FTP/SSL, the FTP protocol with SSL encryption. ([Wikipedia - FPTS]("http://en.wikipedia.org/wiki/Ftps"))

SFTP is FTP over a SSH shell, which needs a SSH server. ([Wikipedia - SFTP]("http://en.wikipedia.org/wiki/Sftp"))

Please check if the ftp-ssl client runs without problems. I suggest you to install the ftp-ssl package and then test it. This client works perfectly with me, so it is a working FTPS client for sure. To test it:

```
 ftp-ssl 127.0.0.1
```Please confirm if that work for you too. If this client works, then you can begin to look with other clients. Check the FTPS page in wikipedia to see more clients that work with FTPS.

NOTE: the ftp-ssl package will uninstall the package ftp. After the test you can reinstall the package ftp if you want.

The connection is still refused.  Although I installed the OpenSSH server and now I can get in that way.  

Although now I'm confused a little bit more, because at [http://ubuntuforums.org/showthread.php?t=518293](http://ubuntuforums.org/showthread.php?t=518293) you say that FTPS and SFTP are the same thing-is this right or am I missing something?

---

### Post by ruibernardo on 2007-09-18
Sorry for misleading you with that. :oops:

When I said "also known as" on that thread, it was because that many people call it SFTP too, although it isn't (it is FTPS only).

Just be careful with SSH server, if the users use a SSH shell, they will have more capabilities than just transferring files...

I'm going to remove the SFTP comment on that thread.

By the way Rhcd67, what FTP client you use with SSH (SFTP)?

---

### Post by Rhcd67 on 2007-09-18
> **epimeteo said:**
> Sorry for misleading you with that. :oops:

When I said "also known as" on that thread, it was because that many people call it SFTP too, although it isn't (it is FTPS only).

Just be careful with SSH server, if the users use a SSH shell, they will have more capabilities than just transferring files...

I'm going to remove the SFTP comment on that thread.

By the way Rhcd67, what FTP client you use with SSH (SFTP)?

Not a problem.  I have been using SecureFX the whole time.

Once again, thank you for all your help.

---

### Post by ruibernardo on 2007-09-19
Well, I've tried to run a FTP/SSL client in windows (coreFTP Lite) and I could connect to both SSH and VSFTPD servers, both running at the same time on the same computer, just by selecting FTPS and SFTP in the coreFTP connect options, with no problems at all. 

Then I've tried SecureFX. It did connect to the SSH server, but when I've tried to connect to VSFTPD server, using "**FTP/SSL (explicit)**", it just disconnected saying:

```
i Control connection successfully established.
< 220 (vsFTPd 2.0.5)
> AUTH TLS
< 234 Proceed with negotiation.
i Control connection could not be protected. 
i (0x80090325) The certificate chain was issued by an authority that is not trusted.

```I've let it end all the connection retrys, clicked again on the toolbar, on the "Connect" button and selected the VSFTPD server IP, then I've clicked on the "Proprieties" button and then on "SSL Options". Then I've the **checked** the box "*Disable certificate validation*", and gave another try. Surprise:

```
i Session 00005 established for session 192.168.235.129
i Control connection successfully established.
< 220 (vsFTPd 2.0.5)
> AUTH TLS
< 234 Proceed with negotiation.
i Time zone of server could not be determined.
> USER user
i Control connection is protected (SSL Explicit). 
< 331 Please specify the password.
> PASS <password>
< 230 Login successful.
> SYST
< 215 UNIX Type: L8
i Remote operating system type is UNIX.
> PWD
< 257 "/"
> TYPE A
< 200 Switching to ASCII mode.
> PBSZ 0
< 200 PBSZ set to 0.
> PROT P
< 200 PROT now Private.
> PASV
< 227 Entering Passive Mode (192,168,235,129,250,38)
> LIST
< 150 Here comes the directory listing.
i Data connection 71AB3B91 connected.
< drwxr-xr-x    2 1000     1000         4096 May 30 21:23 Desktop
< lrwxrwxrwx    1 1000     1000           26 May 15 08:35 Examples -> /usr/share/example-content
< -rw-r--r--    1 1000     1000      4655788 Sep 18 21:01 out.ogg
i Data connection 71AB3B91 closed normally.
< 226 Directory send OK.

```It worked :guitar:

Hope it works for you too, if you still want to use VSFTPD.

---

