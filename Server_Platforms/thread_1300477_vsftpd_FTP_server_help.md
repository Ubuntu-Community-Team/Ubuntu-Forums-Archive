---
title: "vsftpd FTP server help"
date: 2009-10-25
forum: Server Platforms
---

### Post by wlraider70 on 2009-10-25
Im setting up a home server and the first thing im working on is FTP.

I used vsftpd from   [https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html)

My goal is to be able to get file from anywhere so i want to disable anon.

What i was trying to do was disable anon and set up a secure user.
so i made the user localy, and i disabled anon in the settings.
I set the user in the settings, but no Password, i ddint see the option.

Anyway the specific user does NOT work, when anon is enabled it DOES work.


so im sure my issue is in the settings for a user.

---

### Post by Lars Noodén on 2009-10-25
A) Do you want to get a file from your server from anywhere?
B) Do you mind if other people can read that file?
C) Do you want to upload from anywhere to your server?
D) Do you want to administer your server remotely?

If ( A && !B && !C ) 
[indent]then Anonymous FTP  (via vsftpd)
or HTTP (via Apache or Lighttpd or nginx)
[/indent]
If ( A && B && !C ) 
[indent]then SFTP (via openssh-server) or FTPS (via vsftpd) or HTTPS (via Apache or Lighttpd or nginx)
[/indent]
If ( A && ( B || C )) 
[indent]then SFTP (via openssh-server) or FTPS (via vsftpd)
[/indent]
If ( A && ( B || C ) && D ) 
[indent]then SFTP (via openssh-server)
[/indent]

---

### Post by wlraider70 on 2009-10-25
Big yes on A. The most likely situation being that I forgot a file and need to retrieve it from somewhere else. I would prefer it set up so that i could do it from any computer. 

B) YES i mind, I do not want them to read by anyone.

C) I probably won't need to upload. If adding that is easy I'm in, but its not really the purpose. 

D) I don't think i will need to do so. 



I'm not an expert, but i went for FTP over SSH because of the ability to access it from any internet browser.

---

### Post by Lars Noodén on 2009-10-25
> **wlraider70 said:**
> 
 i went for FTP over SSH because of the ability to access it from any internet browser.

Ok.  Then you want the HTTPS option, you'll be able to download from any file in your account's web folder.  If you use that as your document folder, you'll have remote read-only access from any web browser.

Install a webserver, then add SSL, user directories and password protection for the directories.  Here are the 

1) Apache
[list]
[*] [http://httpd.apache.org/docs/2.2/ssl/](http://httpd.apache.org/docs/2.2/ssl/)
[*] [http://httpd.apache.org/docs/2.2/howto/public_html.html](http://httpd.apache.org/docs/2.2/howto/public_html.html)
[*] [http://httpd.apache.org/docs/2.2/mod/mod_auth_basic.html](http://httpd.apache.org/docs/2.2/mod/mod_auth_basic.html)
[/list]

2) Lighttpd
[list]
[*] [http://redmine.lighttpd.net/projects/lighttpd/wiki/Docs:SSL](http://redmine.lighttpd.net/projects/lighttpd/wiki/Docs:SSL)
[*] [http://redmine.lighttpd.net/projects/lighttpd/wiki/Docs:ConfigurationOptions#mod_userdir-user-directories](http://redmine.lighttpd.net/projects/lighttpd/wiki/Docs:ConfigurationOptions#mod_userdir-user-directories)
[*] [http://redmine.lighttpd.net/projects/lighttpd/wiki/Docs:ModAuth](http://redmine.lighttpd.net/projects/lighttpd/wiki/Docs:ModAuth)
[/list]


3) Nginx
[list]
[*] [http://wiki.nginx.org/NginxHttpSslModule](http://wiki.nginx.org/NginxHttpSslModule)
[*] [http://wiki.nginx.org/NginxHttpRewriteModule](http://wiki.nginx.org/NginxHttpRewriteModule)
[*] [http://wiki.nginx.org/NginxHttpAuthBasicModule](http://wiki.nginx.org/NginxHttpAuthBasicModule)
[/list]


Later, if you want to have read-write access via the web broswer, then add WebDAV:

1b)
[http://httpd.apache.org/docs/2.2/mod/mod_dav.html](http://httpd.apache.org/docs/2.2/mod/mod_dav.html)

2b) 
[http://redmine.lighttpd.net/projects/lighttpd/wiki/Docs:ModWebDAV](http://redmine.lighttpd.net/projects/lighttpd/wiki/Docs:ModWebDAV)

3b)
[http://wiki.nginx.org/NginxHttpDavModule](http://wiki.nginx.org/NginxHttpDavModule)

---

### Post by wlraider70 on 2009-10-26
so should i give up on vsftpd.

is that a general consensus?


of the 3 options whats the best. 
Ive heard the most about Apache

---

### Post by Lars Noodén on 2009-10-26
vsftpd is a fine program and on such occasion that you need FTP or FTPS, then it would be a good choice.  OpenSSH would be a good choice if you need SFTP.  But from your requirements, it sounds like you are wanting HTTPS and neither OpenSSH nor vsftpd can provide either HTTPS or HTTP.  

Apache is then a good choice.  So are the others, they're the first real competition Apache has had since 1996.  If you're looking for a main-stream resume-builder, then Apache.   However, they are all used in the mainstream on high-traffic sites.

Regardless of which HTTP server you choose, I would encourage you, after you have accomplished your current project, to explore some of the modules.

---

### Post by Lars Noodén on 2009-10-26
Just for the archives, I'll add a postscript that the SFTP client problem on legacy platforms might be solved using a [portable application](http://portableapps.com/) like PuTTy Portable:
[http://portableapps.com/apps/internet/putty_portable](http://portableapps.com/apps/internet/putty_portable)

However, given the inherently insecure nature of the most common brand of legacy platforms, authentication should be handled by one-time passwords.  OPIE, S/Key, Donkey, and Yubikey are possible choices there.

---

