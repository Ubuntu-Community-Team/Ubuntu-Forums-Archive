---
title: "Server upgrade path"
date: 2009-09-25
forum: Server Platforms
---

### Post by kayrune on 2009-09-25
Could someone please help me make the right choice for server?

Ok, first off, this is a private server, but it still needs to be stable and secure. Another thing, I'm lazy, I don't like to read and adjusting config files on a regular basis keeping the server running and up to date.

this is basically what I need that is available to the rest of the world:
- webserver (mysql, php)
- ssh
- ftp
- something that blocks brute force attacks

this is what I need for internal use:
- Windows file sharing (samba)
- email server, that basically is just a mirror of my provider account.

And I want it to be secure and low maintenance. I don't want the webserver to suddenly stop one day, because there was a php update that required everything to be "set up from scratch". But I don't want to be left behind either, unable to install new tools, just because of a strict upgrade path where I'm left with old and well tested applications.

So first glance tells me 10.04 would be nice - unfortunatly I need it now. As I've read, you can do 8.04 -} 10.04, but can you do 9.04 -} 10.04 ? How does the upgrade work ? Do you need go setup apache/php etc from scratch with updates ? Are there security patches ?

My current server is a rolling schema that requires maintenance with every update, I failed to do that. Even though it usually works, today I had problems with apache/php because of structural changes, and I got tired of it, I want something more simple. 

So what would be the smart choice? 8.04 or 9.04 - and how would that limit my upgrade cycle ?

Thank you for your input.

---

### Post by Iowan on 2009-09-25
If I read correctly, you can do LTS>LTS upgrades (8.04>10.04), but others should be release>release... 9.04>9.10>10.04.

---

### Post by cariboo on 2009-09-26
I'd suggest not setting up an ftp server, use sftp instead. Sftp is a part of the openssh-server package. Most ftp clients eg: Filezilla can do sftp.

---

### Post by KiLaHuRtZ on 2009-09-26
> **kayrune said:**
> - webserver (mysql, php)
apache2
mysql-server
php5

> **kayrune said:**
> - ssh
ssh (already installed)

> **kayrune said:**
> - ftp
vsftpd

> **kayrune said:**
> - something that blocks brute force attacks
fail2ban
iptables

> **kayrune said:**
> - Windows file sharing (samba)
samba

> **kayrune said:**
> - email server, that basically is just a mirror of my provider account.
postfix
mailx
courier-imap
courier-imap-ssl (optional)
squirrelmail (optional)
spamassassin (optional)

> **kayrune said:**
> And I want it to be secure and low maintenance. I don't want the webserver to suddenly stop one day, because there was a php update that required everything to be "set up from scratch". But I don't want to be left behind either, unable to install new tools, just because of a strict upgrade path where I'm left with old and well tested applications.

So first glance tells me 10.04 would be nice - unfortunatly I need it now. As I've read, you can do 8.04 -} 10.04, but can you do 9.04 -} 10.04 ? How does the upgrade work ? Do you need go setup apache/php etc from scratch with updates ? Are there security patches ?

My current server is a rolling schema that requires maintenance with every update, I failed to do that. Even though it usually works, today I had problems with apache/php because of structural changes, and I got tired of it, I want something more simple. 

So what would be the smart choice? 8.04 or 9.04 - and how would that limit my upgrade cycle ?

Thank you for your input.

Use 8.04 LTS and check this link out: [http://www.ubuntu.com/products/whatisubuntu/serveredition/benefits/lifecycle]("http://www.ubuntu.com/products/whatisubuntu/serveredition/benefits/lifecycle")

---

### Post by koenn on 2009-09-26
> **Iowan said:**
> If I read correctly, you can do LTS>LTS upgrades (8.04>10.04), but others should be release>release... 9.04>9.10>10.04.
yeah, that's about it. 
and you should be able to do the upgrades without having to install anything from scratch - unless you've done exotic customizations or installed software by hand in stead of using the repo system.

Even a better choice in this case would be Debian. Their stable releases usually last between 12 and 24 months (you get security updates but apart from that, nothing changes), and their release upgrades are painless.

---

### Post by kayrune on 2009-09-26
Thank you all for your comments, I believe I will have a look at 8.04 - I'm afraid I couldn't handle debian, I've tried it before a long time ago, and although their packages where well tested they where also dated, and gave me problems. This might have changed since it was a long time ago, it was at the time when everyone was using 2.6 and debian was still on 2.4 ... 

Just one more question for now, regarding upgrades. The folowing link describes version #  [http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs/8.04LTS](http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs/8.04LTS)

Am I correct to assume those are the versions until 10.04 - only with security patch ? Like php is 5.2 and not 5.3 in "current" 8.04 ?

---

