---
title: "A Free MS-Exchange ?"
date: 2012-02-01
forum: The Cafe
---

### Post by honeybear on 2012-02-01
Hi, 

I would like to know whether you know an website provider of sort of MS-Exchange (free) / eventually opensource. Have you eventually heard about somthg? 

MS-Exchange offer: 
- mobile service to login
- webmail

a way to link evolution/kmail to its onlien remote free:
- contacts
- emails
- tasks

Preferably a Linux Ubuntu solution would be great... !

Let me know. 
thanks

---

### Post by CharlesA on 2012-02-01
As far as I know there is no single open source or otherwise solution that integrates everything that Exchange offers.

---

### Post by Lars Noodén on 2012-02-01
The place to start would be with [Citadel](http://www.citadel.org/) and [Kolab](http://kolab.org/).  That will get you most of the features that MS Exchange claims to advertise.  To lose the same amount of mail, you can probably whip up a quick recipe in Procmail.  Both Citadel and Kolab are modular.

---

### Post by Dry Lips on 2012-02-01
I don't know if this software does everything Ms Exchange do, but at least it
does some of these things:

[http://www.zarafa.com/](http://www.zarafa.com/)

According to their Website:

*"Zarafa&#8217;s open source groupware is regarded by its customers and partners as the only real replacement for Microsoft Exchange." *

---

### Post by mlentink on 2012-02-01
> **Dry Lips said:**
> I don't know if this software does everything Ms Exchange do, but at least it
does some of these things:

[http://www.zarafa.com/](http://www.zarafa.com/)

According to their Website:

*"Zarafa’s open source groupware is regarded by its customers and partners as the only real replacement for Microsoft Exchange." *, 

+1 Zarafa (but hey, I'm Dutch...)

---

### Post by honeybear on 2012-02-01
Citadell looks more LINUX and also evolution and kmail can connect to it

[http://www.citadel.org/doku.php?id=screenshots](http://www.citadel.org/doku.php?id=screenshots)

does I really think that it is free and linux based? really like MS_exchange? I may dream. there should be some drawbacks ... somehow

edit: 
I saw. It is linux baseed, so you have to install it onto your server ubuntu and open some ports onto your router. and it leaves you risks for open ports. I dont like this to leave a server on the net or any access :( no ssh, nothing

edit2:
is it compatible with CLI. such as abook, or mutt, or any cli stuffs?

---

### Post by Lars Noodén on 2012-02-01
It's available in the package [citadel-server](apt://citadel-server)

You'll probably need to leave open SSH (for your maintenance), IMAPS and SMTP.  The documentation will go into that in detail. Without leaving ports open, there can be no access for your clients.  

Whether a mail client is text or gui makes no difference.  What is important is that it can use IMAP/IMAPS.  Mutt, at least, can do that.

---

### Post by e79 on 2012-02-01
Give a try to [Zimbra Collaboration Suite - Open Source Edition]("http://www.zimbra.com/downloads/os-downloads.html").

---

### Post by honeybear on 2012-02-01
Let's check the citadel... stuff 

a light weight way...

```
# apt-get install citadel-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  db4.6-util libcitadel2 libdb4.6 libical0 libsieve2-1
The following NEW packages will be installed:
  citadel-server db4.6-util libcitadel2 libdb4.6 libical0 libsieve2-1
0 upgraded, 6 newly installed, 0 to remove and 48 not upgraded.
Need to get 1,426 kB of archives.
After this operation, 5,067 kB of additional disk space will be used.
Do you want to continue [Y/n]? y

```

```

 Please specify the IP address which the server should be listening to. If you specify 0.0.0.0, the server will listen on all   &#9474;      
      &#9474; addresses.                                                                                                                     &#9474;      
      &#9474;                                                                                                                                &#9474;      
      &#9474; This can usually be left to the default unless multiple instances of Citadel are running on the same computer.                 &#9474;      
      &#9474;                                                                                                                                &#9474;      
      &#9474; Listening address for the Citadel server:                                                                                      &#9474;      
      &#9474;                                                                                                                                &#9474;      
      &#9474; 0.0.0.0_______________________________________________________________________________________________________________________ &#9474;      
      &#9474;         
```

then?


not good... 

```
low this faq item:#012http://www.citadel.org/doku.php/faq:mastering_your_os:net#netstat

Message from syslogd@ubuntu at Feb  1 21:28:53 ...
 citadel: Startup Problems
[/QUOTE]


[QUOTE]
# lsof -n -i tcp
COMMAND     PID    USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
portmap     984  daemon    5u  IPv4   3911      0t0  TCP *:sunrpc (LISTEN)
rpc.statd   996   statd    7u  IPv4   3949      0t0  TCP *:57924 (LISTEN)
cupsd      1428    root    5u  IPv6   4728      0t0  TCP [::1]:ipp (LISTEN)
cupsd      1428    root    6u  IPv4   4729      0t0  TCP 127.0.0.1:ipp (LISTEN)
sendmail-  1440    root    4u  IPv4   4690      0t0  TCP 127.0.0.1:smtp (LISTEN)
sendmail-  1440    root    5u  IPv4   4691      0t0  TCP 127.0.0.1:submission (LISTEN)
citserver 32464 citadel   21u  IPv4 817776      0t0  TCP *:504 (LISTEN)
citserver 32464 citadel   22u  IPv4 817777      0t0  TCP *:imap2 (LISTEN)
citserver 32464 citadel   23u  IPv4 817779      0t0  TCP *:imaps (LISTEN)
citserver 32464 citadel   24u  IPv4 817781      0t0  TCP *:2020 (LISTEN)
citserver 32464 citadel   25u  IPv4 817782      0t0  TCP *:pop3 (LISTEN)
citserver 32464 citadel   26u  IPv4 817783      0t0  TCP *:pop3s (LISTEN)
citserver 32464 citadel   27u  IPv4 817785      0t0  TCP *:ssmtp (LISTEN)
citserver 32464 citadel   30u  IPv4 817791      0t0  TCP *:xmpp-client (LISTEN)

```

Do you know another solution that works well? Buggy is citadel. Even a fresh install does not make it work

---

### Post by Lars Noodén on 2012-02-01
With Kolab, there are companies that can provide installation and/or support.  There might be similar options for Citadel.

---

### Post by honeybear on 2012-02-01
> **Lars Noodén said:**
> With Kolab, there are companies that can provide installation and/or support.  There might be similar options for Citadel.

thanks. I hope that kobab is better... I let you know
```
apt-get remove citadel-server --purge ; apt-get install kolab-webadmin kolabd  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libical0 db4.6-util libcitadel2 libdb4.6 libsieve2-1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  citadel-server*
0 upgraded, 0 newly installed, 1 to remove and 48 not upgraded.
After this operation, 2,417 kB disk space will be freed.
Do you want to continue [Y/n]? 
```



Nope: kolab requires too much.... I can not all this flood of pacakges, unnecessary into a simple box.
```

dpkg: warning: while removing citadel-server, directory '/var/lib/citadel/data' not empty so not removed.
dpkg: warning: while removing citadel-server, directory '/var/lib/citadel' not empty so not removed.
dpkg: warning: while removing citadel-server, directory '/var/spool/citadel/network' not empty so not removed.
dpkg: warning: while removing citadel-server, directory '/var/spool/citadel' not empty so not removed.
Processing triggers for man-db ...
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libical0 db4.6-util libcitadel2 libdb4.6 libsieve2-1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-mpm-prefork apache2-utils apache2.2-bin apache2.2-common db4.8-util fckeditor gawk horde3 kolab-cyrus-admin kolab-cyrus-clients
  kolab-cyrus-common kolab-cyrus-imapd kolab-cyrus-pop3d kolab-libcyrus-imap-perl ldap-utils libapache2-mod-php5 libapr1 libaprutil1
  libaprutil1-dbd-sqlite3 libaprutil1-ldap libasn1-8-heimdal libc-client2007e libconvert-asn1-perl libconvert-binhex-perl
  libdigest-hmac-perl libdigest-sha1-perl libfile-remove-perl libgd2-xpm libgssapi2-heimdal libheimntlm0-heimdal libhx509-5-heimdal
  libio-socket-ssl-perl libio-stringy-perl libjs-prototype libjs-scriptaculous libkolab-perl libkrb5-26-heimdal libmail-box-perl
  libmail-imapclient-perl libmcrypt4 libmime-tools-perl libmime-types-perl libnet-ldap-perl libnet-libidn-perl libnet-netmask-perl
  libnet-ssleay-perl libobject-realize-later-perl libonig2 libparse-recdescent-perl libqdbm14 libroken18-heimdal libterm-readkey-perl
  libterm-readline-gnu-perl libtest-pod-perl libuser-identity-perl libwind0-heimdal libzephyr4 mlock odbcinst odbcinst1debian2 php-auth
  php-auth-sasl php-cache php-date php-db php-file php-http-request php-kolab-filter php-kolab-freebusy php-log php-mail php-mail-mime
  php-mail-mimedecode php-mdb2 php-mdb2-driver-mysql php-net-dime php-net-ftp php-net-imap php-net-ldap php-net-ldap2 php-net-lmtp
  php-net-sieve php-net-smtp php-net-socket php-net-url php-pear php-services-weather php-soap php-xml-parser php-xml-serializer php5
  php5-cli php5-common php5-gd php5-imap php5-ldap php5-mcrypt php5-mysql php5-suhosin postfix postfix-ldap sasl2-bin slapd smarty tinymce2
  unixodbc
Suggested packages:
  apache2-doc apache2-suexec apache2-suexec-custom imp4 turba2 gollem chora2 kronolith2 mnemo2 webcpp xlhtml ppthtml wv source-highlight
  enscript php5-mhash gettext libgeoip1 unrtf libwpd-tools php5-auth-pam apt-listchanges db4.2-util amavisd-new clamav clamav-daemon
  spamassassin uw-mailutils libgd-tools libio-socket-inet6-perl libauthen-sasl-perl libmcrypt-dev mcrypt libxml-parser-perl libxml-sax-perl
  phpunit php5-sqlite php5-dev procmail postfix-mysql postfix-pgsql postfix-pcre resolvconf postfix-cdb ufw libmyodbc odbc-postgresql
  tdsodbc unixodbc-bin
The following packages will be REMOVED:
  libgd2-noxpm sendmail-bin
The following NEW packages will be installed:
  apache2-mpm-prefork apache2-utils apache2.2-bin apache2.2-common db4.8-util fckeditor gawk horde3 kolab-cyrus-admin kolab-cyrus-clients
  kolab-cyrus-common kolab-cyrus-imapd kolab-cyrus-pop3d kolab-libcyrus-imap-perl kolab-webadmin kolabd ldap-utils libapache2-mod-php5
  libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap libasn1-8-heimdal libc-client2007e libconvert-asn1-perl
  libconvert-binhex-perl libdigest-hmac-perl libdigest-sha1-perl libfile-remove-perl libgd2-xpm libgssapi2-heimdal libheimntlm0-heimdal
  libhx509-5-heimdal libio-socket-ssl-perl libio-stringy-perl libjs-prototype libjs-scriptaculous libkolab-perl libkrb5-26-heimdal
  libmail-box-perl libmail-imapclient-perl libmcrypt4 libmime-tools-perl libmime-types-perl libnet-ldap-perl libnet-libidn-perl
  libnet-netmask-perl libnet-ssleay-perl libobject-realize-later-perl libonig2 libparse-recdescent-perl libqdbm14 libroken18-heimdal
  libterm-readkey-perl libterm-readline-gnu-perl libtest-pod-perl libuser-identity-perl libwind0-heimdal libzephyr4 mlock odbcinst
  odbcinst1debian2 php-auth php-auth-sasl php-cache php-date php-db php-file php-http-request php-kolab-filter php-kolab-freebusy php-log
  php-mail php-mail-mime php-mail-mimedecode php-mdb2 php-mdb2-driver-mysql php-net-dime php-net-ftp php-net-imap php-net-ldap php-net-ldap2
  php-net-lmtp php-net-sieve php-net-smtp php-net-socket php-net-url php-pear php-services-weather php-soap php-xml-parser
  php-xml-serializer php5 php5-cli php5-common php5-gd php5-imap php5-ldap php5-mcrypt php5-mysql php5-suhosin postfix postfix-ldap
  sasl2-bin slapd smarty tinymce2 unixodbc
0 upgraded, 108 newly installed, 2 to remove and 48 not upgraded.
Need to get 37.2 MB of archives.
After this operation, 124 MB of additional disk space will be used.
Do you want to continue [Y/n]? n



```

---

### Post by honeybear on 2012-02-01
**[COLOR="Red"]L O V E   IT !![/COLOR]**

I have followed this howto ... 

[http://postfixmail.com/blog/index.php/install-citadel-groupware-on-ubuntu-810/](http://postfixmail.com/blog/index.php/install-citadel-groupware-on-ubuntu-810/)

So it works !!  apt-get install citadel-suite

and you press ENTER... and you get it. 

After : 

MYIP=`ifconfig eth0 | grep addr | grep inet | awk -F "r:" ' { print $2 } '  | awk ' { print $1 } ' | head -n 1 | awk ' { print $1 } '`

firefox "${MYIP}:80"
and you get this !  [http://postfixmail.com/blog/wp-content/uploads/2009/01/cit4.png](http://postfixmail.com/blog/wp-content/uploads/2009/01/cit4.png)

[http://imageshack.us/photo/my-images/9/citj.png/](http://imageshack.us/photo/my-images/9/citj.png/)

LOVE IT 

it is simple for ubuntu newbies


and I can use simply another high number port... for its web-interface correct? Could I use a port like 6677348934 ?

---

### Post by TheFu on 2012-02-02
Zimbra replaces Ms-Exchange nicely. I've been running it for 3 companies about 4 years.  It has been solid for us.  There are paid clients for some portable devices, but pretty much everything can be accomplished through the web interface on those devices too.  It works really well with thunderbird.

Zimbra has enterprise calendaring, which most of the other systems lack. It also has delegation and sharing of pretty much everything (contacts, todo lists, email folders, ...).

---

### Post by Bodsda on 2012-02-02
> **honeybear said:**
> **[COLOR=Red][/COLOR]**
and I can use simply another high number port... for its web-interface correct? Could I use a port like 6677348934 ?

Sort of, yes you can use a high number, but not that one. The highest possible IPv4 port number is 65535, and it is recommended to pick something between 1024–49151

Bodsda

---

### Post by honeybear on 2012-02-02
> **Bodsda said:**
> Sort of, yes you can use a high number, but not that one. The highest possible IPv4 port number is 65535, and it is recommended to pick something between 1024–49151

Bodsda

Pitty but Zimbra is not into the repositories.

Anyhow, citabel-suite is very simple to install. Is it hacker secured? 

regarding ports: 
wow sounds cool. then I could set a high number and I could log onto my contact book, like being on the intranet.

another thing. Do you know if from a port 80/https behind a corporate router/firewall (all ports closed but regular internet), I could log onto citadel such as : firefox [http://myip:65535?](http://myip:65535?)

greetings

---

### Post by Lars Noodén on 2012-02-02
> **honeybear said:**
> 
Anyhow, citabel-suite is very simple to install. Is it hacker secured? 

Perhaps you meant *cracker* instead of [hacker](http://catb.org/jargon/html/H/hacker.html)?  Linux is for hackers. :)

About the groupware, Kolab was initially developed for the German Federal Office for Information Security (BSI)

---

### Post by honeybear on 2012-02-02
> **Lars Noodén said:**
> Perhaps you meant *cracker* instead of [hacker](http://catb.org/jargon/html/H/hacker.html)?  Linux is for hackers. :)

About the groupware, Kolab was initially developed for the German Federal Office for Information Security (BSI)

I dont know the name. In practice, the one that enters and breaks a system. 

So Kolab might be secured. I wish it is the same for citadel, like a fortress ;)

---

