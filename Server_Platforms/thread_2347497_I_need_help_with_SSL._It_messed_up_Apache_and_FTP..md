---
title: "I need help with SSL. It messed up Apache and FTP."
date: 2016-12-25
forum: Server Platforms
---

### Post by deadlyfoez2 on 2016-12-25
I will try to give as many details as possible. If there is any more information or certain configs you would like to see in a file then please let me know. I have a very basic linux knowledge, although I have used kali and backtrack quite a bit so I know my way around not too bad in command line but still stumble on some things.

Ok. So I set up a machine to run Ubuntu Server 16.04 on my local network and serving to the web as well and I have been successful with setting up 3 virtual web hosts, ftp, plex media server. I am using a free domain name for my 3 virtual hosts. One is running wordpress, another basic html, and another that was still blank at the moment. Everything was working perfectly. The problem arose when I tried to set up SSL. I followed this [Digital Ocean Tutorial]("https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-apache-in-ubuntu-16-04") and everything broke except SSH. I have tried this many times over and reformatted my machine and tried again, wondering if I messed up somewhere so I would try again and it always breaks at this point.

I am doing my local work from my Win7 pc, using Chrome, PuTTY, and FIleZilla. I have my host file setup to direct the 3 site names directly to my server just for simplicity I can access my 3 sites locally using http, but when I try through https I get the generic apache page.  For testing from the internet I am using my phones cell connection. I can access my sites via http, but https gives me the generic page. I also get that warning about having a self signed certificate. If I try to goto [http://sitex.forwarder.com:443](http://sitex.forwarder.com:443) I get a "Bad Request" error, which is kind of expected.

I followed this [Digital Ocean Tutorial]("https://www.digitalocean.com/community/tutorials/how-to-configure-vsftpd-to-use-ssl-tls-on-an-ubuntu-vps") to at least get the SSL part working and FTP is broken now too. I had FTP working prior and I adjusted the file locations and such for my configuration. FileZilla times out while trying to connect.

After things didn't work so well I did try to see what some other tutorials had written and adjusted to my configuration, or lack thereof, and shockingly I got some things kinda working again.

Below is the general format of all of my sites .conf files.
```
<VirtualHost *:80>
        ServerName sitex.forwarder.net
        ServerAdmin my@email.com
        DocumentRoot /var/www/sitex/html
        ServerAlias www.sitex.forwarder.net
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

This is how my 000-default.conf file looks
```
<VirtualHost *:80>        ServerAdmin my@email.com
        DocumentRoot /var/www/html
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
        Redirect permanent "/" "https://10.0.0.101/"      #my local host IP
</VirtualHost>
```

This is my ssl-params.conf file
```
SSLCipherSuite EECDH+AESGCM:EDH+AESGCM:AES256+EECDH:AES256+EDHSSLProtocol All -SSLv2 -SSLv3
SSLHonorCipherOrder On
#Header always set Strict-Transport-Security "max-age=63072000; includeSubdomains; preload"
Header always set Strict-Transport-Security "max-age=63072000; includeSubdomains"
Header always set X-Frame-Options DENY
Header always set X-Content-Type-Options nosniff
SSLCompression off
SSLSessionTickets Off
SSLUseStapling on
SSLStaplingCache "shmcb:logs/stapling-cache(150000)"
SSLOpenSSLConfCmd DHParameters "/etc/ssl/certs/dhparam.pem"
```

My default-ssl.conf file
```
<VirtualHost _default_:443>                ServerAdmin my@email.com
                ServerName 10.0.0.101         #My local IP
                DocumentRoot /var/www/html
                ErrorLog ${APACHE_LOG_DIR}/error.log
                CustomLog ${APACHE_LOG_DIR}/access.log combined
                SSLEngine on
                SSLCertificateFile      /etc/apache2/ssl/apache.crt
                SSLCertificateKeyFile /etc/apache2/ssl/apache.key
                <FilesMatch "\.(cgi|shtml|phtml|php)$">
                                SSLOptions +StdEnvVars
                </FilesMatch>
                <Directory /usr/lib/cgi-bin>
                                SSLOptions +StdEnvVars
                </Directory>
                BrowserMatch "MSIE [2-6]" \
                               nokeepalive ssl-unclean-shutdown \
                               downgrade-1.0 force-response-1.0
</VirtualHost>
```


Does anyone know what my problem is? Thank you all for your time. I appreciate it.

---

### Post by TheFu on 2016-12-26
Welcome to the forums.

a) stop using plain FTP. Use sftp that is built into the ssh-server.  There is no good reason for plain FTP or FTPS to be used since ... 1995-ish. Google "stop using FTP" for more reasons why. Filezilla easily connects to sftp as does winscp. Every Unix has sftp:// support for URLs in their file managers. It just works, even better if you've setup ssh-keys. Putty has a pscp program, but I've only used it for automatic stuff and not in many years. Don't really use Windows much anymore. Plain FTP ports are dynamic, so most cheap routers have issues with that.

b) Double check your router settings for port forwards. Ensure the "server" is using a static IP and that IP is what you expect by the other clients and router port forwards.

c) I don't understand why you expect a port forwarder service to work with SSL.  It won't.  The client needs a direct connection to the SSL server.  Why use a self-signed cert too?  Use "let's encrypt" certs. They are trivial to setup for apache.

d) The copy/paste above seems screwed up. Line breaks matter. If that isn't just a copy/paste issue, then that is the 1st issue to be fixed.

e) You cannot expect the internet to use 10.x.x.x addresses. Review your IPv4 knowledge. 10.x.x.x IPs are not route-able over the internet. A redirect needs to point to an internet accessible location - public IP/Port.

I would use a reverse proxy and forward all traffic (HTTP/HTTPS) through it. It would terminate the SSL tunnel and forward non-encrypted GET/PUT stuff to the backend server. Pound, nginx, apache can do that. Your choice. Might be others, but those are the ones I've used.  Been using nginx the last 8-ish years, happily.

---

### Post by deadlyfoez2 on 2016-12-29
My knowledge of networking and linux is minimal, I will admit. I am using this whole thing as a hands on learning experience and I know I am making many mistakes in the process.

A. I was just starting to research sftp. Hopefully I can get that working.

B. All that stuff is correct.

C. I don't understand what you mean. I did not know that I had an option for other certs without paying for them or something. I will see about setting that up.
   So, if I am understanding you correctly, are you saying that SSL breaks once a port gets forwarded???
**EDIT** Oh, do you mean how I have "ServerName sitex.forwarder.net"? If so, the reason why I wrote it like that is I am using one of those free domain names. So my real domain is more like "mysite.no-ip.net". If that still breaks the SSL then I do not understand why it would.


D. Yeah, I cut out all the commented lines that weren't also variables to not take up so much space on this post. As far as the line breaks, if you are referring to the few mistakes in my post, yeah, that was just copy and paste error.

E. There are a few settings that I made that I was not sure if I needed to enter in my local ip address or my real ip. Could you point out which ones I messed up on please?

Thank you very much for your input.

---

### Post by howefield on 2016-12-29
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by TheFu on 2016-12-29
> **deadlyfoez2 said:**
> My knowledge of networking and linux is minimal, I will admit. I am using this whole thing as a hands on learning experience and I know I am making many mistakes in the process.

No better way to learn, just be certain that the rest of your network doesn't get taken over due to a noob-mistake. BTW, we've all made them. I've done some really baddies.

> **deadlyfoez2 said:**
> A. I was just starting to research sftp. Hopefully I can get that working. ssh/sftp/scp/rsync are all really easy. Easier than http, which is also easy for static files.  ssh is the swiss-army-knife of Unix connectivity. Don't use passwords, use ssh-keys for authentication. Only use a passphrase to unlock the ssh-keys. Best practice is long, complex, random, for the passphrase.

> **deadlyfoez2 said:**
> C. I don't understand what you mean. I did not know that I had an option for other certs without paying for them or something. I will see about setting that up.
   So, if I am understanding you correctly, are you saying that SSL breaks once a port gets forwarded???
**EDIT** Oh, do you mean how I have "ServerName sitex.forwarder.net"? If so, the reason why I wrote it like that is I am using one of those free domain names. So my real domain is more like "mysite.no-ip.net". If that still breaks the SSL then I do not understand why it would.

"Let's Encrypt" is an effort to make self-signed certs a thing of the past. Google it. Installing into apache is bonehead - like 4 steps. Now that I know how to do it, would take 30 sec to setup on a new server. Unless you are a Fortune 500 company, there really isn't much need for paid certs anymore.  The crypto isn't any different, stronger. Only the behind-the-scenes validations are stronger for expensive certs. Plus HTTPS has enough security problems due to the multi-layer trust requirements of CAs and DNS already, so it really isn't secure enough to be trusted for data, IMHO. Use a private cert and PKI to secure connections, not HTTPS.

> **deadlyfoez2 said:**
> D. Yeah, I cut out all the commented lines that weren't also variables to not take up so much space on this post. As far as the line breaks, if you are referring to the few mistakes in my post, yeah, that was just copy and paste error.
The first lines is wrong. Think you are missing line breaks before the ServerAdmin.  Details matter in Unix. Spacing can matter too. Be very careful and be extremely consistent with how you create text files.  Don't use Windows to open or maintain these files. Be careful about {tabs} and end-of-line characters too.  Some config files treat tabs VERY DIFFERENTLY than others. Sometimes tabs are mandatory in certain places (Makefiles). I don't know if it matters in Apache or not. Really don't use apache much the last decade.

> **deadlyfoez2 said:**
> E. There are a few settings that I made that I was not sure if I needed to enter in my local ip address or my real ip. Could you point out which ones I messed up on please? Nope. I'm not any apache expert, just have been running servers for 25+ yrs. Always have to look up the settings using the apache.org examples. Every major release, when they break things, I have to look up the changes and figure out what/why they changed. Sometimes there are very good reasons. Sometimes, not so much. I try to get help from the source, when possible.

> **deadlyfoez2 said:**
> Thank you very much for your input.  Everyone has an opinion, willing to share more than I know. ;)

As said before, just don't use plain FTP. ;)  That protocol should have been killed off around 1995.

---

### Post by deadlyfoez2 on 2017-01-01
Ok. I tried installing SFTP and lets encrypt and everything got worse, likely because all my other settings are completely borked as well. I think it is likely time for me to start over from scratch.

So what order should I be installing things?
My list of things that I need are; OpenVPN, Virtual Hosts, SFTP, Plex Media Server, Lets Encrypt.

---

### Post by TheFu on 2017-01-01
ssh is always first.

That removes the need for openvpn and sftp because ssh can be a VPN and sftp is built-into the ssh-server stuff.  ssh can connect any 2 systems in the world with a secure tunnel.  It is trivial to configure compared to openvpn. The only time openvpn makes sense is when non-technical people are the end-users and you want to ensure all their traffic uses the VPN.

Plex Media Server on a VPS? Really?  Uh ... I wouldn't for 50 different reasons. Mainly privacy.  You can connect to plex running inside your home, without a plex login, securely, using ssh.  I do this all the time.  The traffic is tunneled using the ssh port.

VirtualHosts isn't a package.

Start with ssh. Get that working. Learn about the 500 ways ssh can be used. It isn't just a remote terminal thing.

---

