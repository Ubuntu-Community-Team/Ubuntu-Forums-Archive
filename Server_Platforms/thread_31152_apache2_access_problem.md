---
title: "apache2 access problem"
date: 2005-05-02
forum: Server Platforms
---

### Post by cavalier67 on 2005-05-02
Hello ... I'm a linux/Ubuntu noobie ... however ... I love how easy Ubuntu was to install and am learning ...

Here is my problem ... I have installed apache2, mysql 4.1, and php4 on my server using the Lamp for Hoary install tutorial ... and it is running fine when accessed from the server itself ... from the physical server machine I can access the apache server by: localhost, 192.168.2.102, or the machine name gremlin ... however ... from any other system on my network I can only access the apache server with 192.168.2.102 (and it works fine this way) ... anything else gives me "page cannot be displayed" ...

At first I thought it was a ServerName problem ... until I tried accessing it by "gremlin" at the machine itself ... so I think this is not the issue ... could be wrong ...

I have opened port 80 on my router to no avail ... 

Also ... It isn't an issue with hardware outside of the server itself ... I used to run an apache2 server on windows 2003 from this same box ... 

All other configs are the defaults ... I made sure to return everything to normal as I tested changes that didn't fix the problem ...

Any help would be most appreciated ...

Thanks in advance ...

KP

---

### Post by cavalier67 on 2005-05-02
Looks like it is DNS ... meaning that I need a DNS server ... never realized that windows ... specifically Netbios workied as a small semi-DNS server ... 

Anyway ,,, gotta learn linux DNS :) ... 

Will post here again when the problem is solved ...

Now if I am way off base here ... and someone notices ... please let me know ... 

Thanks ...
KP

---

### Post by Gandalf on 2005-05-02
well ok here's a thought, reinstall ubuntu to erase all your custom changes (or just apt-get --purge remove all the packeges you installed to run the server)
than install VHCS control panel by following [HOWTO: install VHCS on ubuntu (SERVER)](http://ubuntuforums.org/showthread.php?t=25722) , i run one server, installed MANY if you need help or maybe remote install just tell me!!! i'll be happy to help you out

---

### Post by cavalier67 on 2005-05-02
Thanks for the info ... got a question though ... well maybe two of them ...

Does VHCS take the place of apache2, mysql, and php?

It looks as if VHCS either installs apache2 (the tutorial requires manipulation of the apache2.conf file) or that it requires it to be installed ...

I have not actually changed any settings or config files ... just have the default installs for apache2, mysql, and php ... so ... Do I really need to wipe this thing out and start over in order to use VHCS?

---

### Post by Gandalf on 2005-05-03
[QUOTE=cavalier67]Thanks for the info ... got a question though ... well maybe two of them ...

Does VHCS take the place of apache2, mysql, and php?

It looks as if VHCS either installs apache2 (the tutorial requires manipulation of the apache2.conf file) or that it requires it to be installed ...

I have not actually changed any settings or config files ... just have the default installs for apache2, mysql, and php ... so ... Do I really need to wipe this thing out and start over in order to use VHCS?[/QUOTE]
 well VHCS does not take place of apache2 etc... it's just if you want, an automatic configuration of apache and mails etc... in a god looking web page, all the modules (as you noticed in the tuto) are installed manually,

in the case you didn't changed anything then yes you can install without wiping anything just follow the TUTO the apt-get will not touch the already installed modules, if you need help just contact me

---

### Post by bartokk on 2005-05-04
I'm also having similiar issues (running Warty).  I installed apache2, php, and mysql.  I can access index.html (from comp running web server) using localhost, private IP address, AND public IP address, as well as a DNS name I registered with dyndns.org.

I can even do all that from a second computer on my network (using global/WAN IP, DDNS name).  However, I'm unable to access from outside of my network.  I first thought that it was a problem with my router (NAT based) even though it is configured to forward requests to proper IP.  I know the router does work, since I was able to SSH form an external source, as well as test other port forwarding apps I configured.

I am willing to try VHCS, but I was wondering what I was missing with my current setup.  Trying VHCS may solve my problem, but I would like to know why it's not working.

---

### Post by Gandalf on 2005-05-04
[QUOTE=bartokk]I'm also having similiar issues (running Warty).  I installed apache2, php, and mysql.  I can access index.html (from comp running web server) using localhost, private IP address, AND public IP address, as well as a DNS name I registered with dyndns.org.

I can even do all that from a second computer on my network (using global/WAN IP, DDNS name).  However, I'm unable to access from outside of my network.  I first thought that it was a problem with my router (NAT based) even though it is configured to forward requests to proper IP.  I know the router does work, since I was able to SSH form an external source, as well as test other port forwarding apps I configured.

I am willing to try VHCS, but I was wondering what I was missing with my current setup.  Trying VHCS may solve my problem, but I would like to know why it's not working.[/QUOTE]
 maybe verify your apache2.conf that is listening to 80 and not to an ip:80, like
Listen 80, maybe this is what keeping it away from public IPs

---

### Post by bartokk on 2005-05-05
The apache2.conf file is pointed to ports.conf for port listening.  I checked ports.conf and the only line it has is ```
Listen 80
```.  I'm sorry if I misunderstood your post, but were you saying that it should say 'Listen 80' or that it should have something else?

---

### Post by cavalier67 on 2005-05-09
I have gotten as far as the second step ...

sudo sh vhcs.sh

And it has sat on removing unneeded packages all night long (actually it says "undeeded")... the system is not frozen as I am using it now to post ... 

Should it take this long or is something wrong ... this is the second time it has done this ... the first I stopped after 4 hours ... I then did a complete format and reinstall of Ubuntu and started the process over ... so this is a clean install ...

Any advise would be great ...

Thanks,
KP

---

### Post by Gandalf on 2005-05-09
[QUOTE=cavalier67]I have gotten as far as the second step ...

sudo sh vhcs.sh

And it has sat on removing unneeded packages all night long (actually it says "undeeded")... the system is not frozen as I am using it now to post ... 

Should it take this long or is something wrong ... this is the second time it has done this ... the first I stopped after 4 hours ... I then did a complete format and reinstall of Ubuntu and started the process over ... so this is a clean install ...

Any advise would be great ...

Thanks,
KP[/QUOTE]
 well tell me about your connection? because actually at this step it will download about 400Mb from repository which is all needed packages (i will correct the typo mistake),
from another session check the file /root/vhcs_log.txt look to the end, what it says??

//EDIT: i corrected the typo mistake, and added one more comment where it will begin packages installation to know where it really hangs... please also attach the /root/vhcs_log.txt file so i can expect what really going on

P.S: you don't have to format, the script will replace any existing vhcs system already installed (not apache or proftpd or... only the vhcs which is in the directory /var/www/vhcs2 and /etc/vhcs2

---

### Post by cavalier67 on 2005-05-09
Here is the log file ...

 +-----------------------------------------------------------------------------$ | Wael Nasreddine (Gandalf) / [email]gandalf@siemens-mobiles.org[/email]                     $ | Purpose of this script is to install VHCS                                   $ |                                                                             $ | This script is distributed without any warrenty use it at your own risk.    $ | If this script blows up your installation it's not my fault :)              $ |                                                                             $ | This script has been tested on ubuntu Hoary Hedgehog 5.04 and on debian sarg$ | ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++$ | You can modify this script and/or redestribute it as long as this text stay $ | on the TOP and displayed to the user when he run the script.                $ | Whatever you change, this license must always be displayed to the user...   $ |                                                                             $ | any suggestion are welcomed...                                              $ +-----------------------------------------------------------------------------$
Ubuntu selected
adding ubuntu repository


My connection is a 1.5mb DSL ... bellsouth fastaccess to be more specific ... 

The only reason I formatted was that I thought the problem might have been from the previous install of apache2, mysql, and php ... 

Just so you know ... it is still sitting on "removing unneeded packages" ... been 10 hours total ... and there appears to be no constant hard drive activity ... only the occational blip as I am sending or opening posts ...

Thanks again,
KP

---

### Post by Gandalf on 2005-05-09
it's weird, the log does not contain your step *-)
can you verify if there's internet activity?

QUICK fix,
cancel the script,
open the script with gedit
replace
```

${apt} -y remove ${remove_packages} >> /root/vhcs_log.txt 2>&1

```
with
```

${apt} -y remove ${remove_packages}

```

and
```

${apt} install -y ${install_packages} >> /root/vhcs_log.txt 2>&1

```
with
```

${apt} install -y ${install_packages}

```

this will allow you to see the apt-get progress

---

### Post by LordHunter317 on 2005-05-09
[QUOTE=Gandalf]than install VHCS control panel by following [HOWTO: install VHCS on ubuntu (SERVER)]("http://ubuntuforums.org/showthread.php?t=25722") , [/quote]The problem with this is he doesn't need a VHCS, or anything resembling it.
 
 He just needs to setup DNS.  And from what scant information is on the VHCS webpage, their DNS administration sucks.
 
 So you just gave bad advice.  You killed a fly using a double-barrel 12-guage, I'm afraid.
 
And instead of telling him to hack up the script, you could have just told him to view the logfile. The output would be there, you know.

**cavailer67**:
I'm going to give you a very strong recommendation to abandon the VHCS crap and start over clean. Follow the LAMP guide and get back to the point you were at. You got there once so I know you can do it again :)

Then, start a new thread asking for help setting up DNS for your local LAN and someone will help you through it, if you need it.

VHCS is obviously going to be a PITA and a waste of your time, so don't bother.

It's intended to give front-end to users at web hosting providers that host thousands of sites. It's not intended for single-site administration, and shouldn't be used as such.

Besides, learning to do it outside of VHCS is a valuable and useful skill, and you'll have much more appreciation for the people who run the 'Net afterwards ;)

---

### Post by Gandalf on 2005-05-09
[QUOTE=LordHunter317]The problem with this is he doesn't need a VHCS, or anything resembling it.
 
 He just needs to setup DNS.  And from what scant information is on the VHCS webpage, their DNS administration sucks.
 
 So you just gave bad advice.  You killed a fly using a double-barrel 12-guage, I'm afraid.
[/QUOTE]well who says it sucks, you just edit the template manually, it's so easy and everything done automatic from there,
 
[QUOTE=LordHunter317]
And instead of telling him to hack up the script, you could have just told him to view the logfile. The output would be there, you know.
[/QUOTE]well here you either invented the cold water, or you aren't wearing your glasses, read the posts above!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


[QUOTE=LordHunter317]
**cavailer67**:
I'm going to give you a very strong recommendation to abandon the VHCS crap and start over clean. Follow the LAMP guide and get back to the point you were at. You got there once so I know you can do it again :)

Then, start a new thread asking for help setting up DNS for your local LAN and someone will help you through it, if you need it.

VHCS is obviously going to be a PITA and a waste of your time, so don't bother.

It's intended to give front-end to users at web hosting providers that host thousands of sites. It's not intended for single-site administration, and shouldn't be used as such.

Besides, learning to do it outside of VHCS is a valuable and useful skill, and you'll have much more appreciation for the people who run the 'Net afterwards ;)[/QUOTE]
well i used it for one site, but instead of creating mails, manually, ftp accounts and worry about security, VHCS do everything for me :D

---

### Post by LordHunter317 on 2005-05-09
[QUOTE=Gandalf]well who says it sucks, you just edit the template manually, it's so easy and everything done automatic from there,[/quote][This implies that their DNS is inadequate]("http://vhcs.net/new/modules/newbb/viewtopic.php?topic_id=2227&forum=2&post_id=11014#forumpost11014") for the needs of people using VHCS.

 > well here you either invented the cold water, or you aren't wearing your glasses, read the posts above!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!No, your recommendation still doesn't make any sense. If the commands aren't writing to the log, the commands aren't being run. Telling him to remove the output to the log isn't going to help anything, it's only going to waste his time.

> well i used it for one site, but instead of creating mails, manually, ftp accounts and worry about security, VHCS do everything for me :DBut does it really do it correctly and securely? I don't know, I've never used it, but generally, getting applications like that to do the right thing requires a lot of work, moreso than is worth taking for a single-user site. 

There's no such thing as "drop and go" on a server.  There just isn't, and you're dellusion if you think there is.

---

### Post by Gandalf on 2005-05-09
well actually, the DNS template isn't that hard, it's hard to replace {IP} with your IP, that's it,
about the log, i just want him to see make it asks him about failure authentification and needs to press Y that's why i asked him to remove the log

for the security wel i used it for 5 months with 1 site, now i have 3, 2 are mine and till now i've never had a problem, the system for ftp is quite secure, try it before writing bad comments,

anyway sorry being a bit rude in my last post, i apologise i was a bit nervous (NOT FROM YOUR POST) and i apologise again :)

---

### Post by bnutting on 2005-05-09
I agree with the post above I would not do the VHCS stuff either.
Let me see if I understand your original problem:
1. You could access your 'home page' bye going to localhost on the server itself.
2. You could access your 'home page' bye going to 192.168.2.102 on the server itself.
3. You could access your 'home page' bye going to gremlin on the server. This works because it is resolving bye the /etc/hosts file on the box.
4. You could access your 'home page' bye 192.168.2.102 from other systems on your private network.
5. Anything else gives you "page cannot be displayed".

This sounds like a simple issue. Are you trying to access the site from the real world?
If not and all you want to do is access it by your local private network, you could just simply put an entry in the hosts file on each box. This way you do not need DNS.
If you are trying to access from the real world then you would need to setup port forwarding on your firewall to your web server.

Allways remember K.I.S.S (Keep It Simple Stupid)  ;-)

Let us know how you make out.
Bryan

---

### Post by bnutting on 2005-05-09
[QUOTE=bartokk]I'm also having similiar issues (running Warty).  I installed apache2, php, and mysql.  I can access index.html (from comp running web server) using localhost, private IP address, AND public IP address, as well as a DNS name I registered with dyndns.org.

I can even do all that from a second computer on my network (using global/WAN IP, DDNS name).  However, I'm unable to access from outside of my network.  I first thought that it was a problem with my router (NAT based) even though it is configured to forward requests to proper IP.  I know the router does work, since I was able to SSH form an external source, as well as test other port forwarding apps I configured.

I am willing to try VHCS, but I was wondering what I was missing with my current setup.  Trying VHCS may solve my problem, but I would like to know why it's not working.[/QUOTE]

Do you see any entries in the access.log file for apache when you try to access it from the outside world? I would still question the firewall/router.

---

### Post by cavalier67 on 2005-05-10
Hello Again,

I want to at least give VHCS a shot and see what it can do ... besides I am thinking about hosting a couple sites ... maybe more ...

I managed to get past the "removing unneeded packages" point ... 

It is now hanging on "Installing New Packages" ... below is the last part of the vhcs_log.txt file ... everything prior to this looks good ... 



removing unneeded packages...
Reading package lists...
Building dependency tree...
Package lpr is not installed, so not removed
Package nfs-common is not installed, so not removed
Package portmap is not installed, so not removed
Package pidentd is not installed, so not removed
Package pcmcia-cs is not installed, so not removed
Package pppoe is not installed, so not removed
Package pppoeconf is not installed, so not removed
Package ppp is not installed, so not removed
Package pppconfig is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

updateinetd

installing new packages...
Reading package lists...
Building dependency tree...
postfix is already the newest version.
postfix-tls is already the newest version.
Note, selecting perl instead of libmime-base64-perl
perl is already the newest version.
libperl5.8 is already the newest version.
perl is already the newest version.
perl-base is already the newest version.
perl-modules is already the newest version.
diff is already the newest version.
gzip is already the newest version.
iptables is already the newest version.
mysql-common is already the newest version.
patch is already the newest version.
procmail is already the newest version.
tar is already the newest version.
libsasl2-modules is already the newest version.
libsasl2 is already the newest version.
bzip2 is already the newest version.
The following extra packages will be installed:
  apache2-utils libapr0 libasn1-6-heimdal libbit-vector-perl libcarp-clan-perl
  libdb4.1 libdigest-hmac-perl libdigest-sha1-perl libgssapi1-heimdal libisccc0
  libisccfg0 libkrb-1-kerberos4kth libkrb5-17-heimdal libltdl3
  libnet-daemon-perl libpcre3 libplrpc-perl libroken16-kerberos4kth
  openssh-server openssl php4-cli php4-common php4-universe-common
  proftpd-common ssl-cert
Suggested packages:
  apache2-doc lynx www-browser bind9-doc courier-doc courier-imap-ssl
  courier-pop-ssl dbishell libmail-audit-perl libmcrypt-dev mcrypt
  libcompress-zlib-perl mysql-doc ca-certificates php4-dev proftpd-doc
Recommended packages:
  libnet-ph-perl libnet-snpp-perl libnet-telnet-perl libsocket6-perl
  libio-socket-inet6-perl
The following NEW packages will be installed:
  apache2 apache2-common apache2-mpm-prefork apache2-utils bind9
  courier-authdaemon courier-base courier-imap courier-maildrop courier-pop
  libapache2-mod-php4 libapr0 libasn1-6-heimdal libberkeleydb-perl
  libbit-vector-perl libcarp-clan-perl libcrypt-blowfish-perl libcrypt-cbc-perl
  libcrypt-passwdmd5-perl libdate-calc-perl libdate-manip-perl libdb4.1
  libdbd-mysql-perl libdbi-perl libdigest-hmac-perl libdigest-sha1-perl
  libgssapi1-heimdal libio-stringy-perl libisccc0 libisccfg0
  libkrb-1-kerberos4kth libkrb5-17-heimdal libltdl3 libmail-sendmail-perl
  libmailtools-perl libmcrypt4 libmd5-perl libmime-perl libnet-daemon-perl
  libkrb-1-kerberos4kth libkrb5-17-heimdal libltdl3 libmail-sendmail-perl
  libmailtools-perl libmcrypt4 libmd5-perl libmime-perl libnet-daemon-perl
  libnet-dns-perl libnet-netmask-perl libnet-perl libnet-smtp-server-perl
  libpcre3 libplrpc-perl libroken16-kerberos4kth libsnmp-session-perl
  libterm-readkey-perl libterm-readpassword-perl libtimedate-perl mysql-client
  mysql-server openssh-server openssl original-awk php4 php4-cli php4-common
  php4-mcrypt php4-mysql php4-pear php4-universe-common proftpd-common
  proftpd-mysql sasl2-bin ssh ssl-cert

Extracting templates from packages: 1%
Extracting templates from packages: 2%
Extracting templates from packages: 4%
Extracting templates from packages: 5%
Extracting templates from packages: 7%
Extracting templates from packages: 8%
Extracting templates from packages: 10%
Extracting templates from packages: 11%
Extracting templates from packages: 13%
Extracting templates from packages: 14%
Extracting templates from packages: 16%
Extracting templates from packages: 17%


etc ... etc ... etc ...

Extracting templates from packages: 100%
Preconfiguring packages ...
^[[?1049h^[[1;24r^[[4l^[(B^[)0^[[?25l^[[m^O^[[37m^[[40m^[[1;24r^[[H^[[2J^[[1;1H^[[1m^[[37m^[[44m
                                                     ^[[2;1H
                 ^[[3;1H                                                                                ^[[4;1H
                                                                    ^[[5;1H

^[[6;1H                                                         -                       ^[[7;1H
                                                    ^[[8;1H
                ^[[9;1H                                                                                ^[[10;1H
                                                                    ^[[11;1H

^[[12;1H                                                                                ^[[13;1H
                                                     ^[[14;1H
                  ^[[15;1H                                                                                ^[[16;1H
                                                                       ^[[17;1H
                                    ^[[18;1H
 ^[[19;1H                                                                                ^[[20;1H
                                                      ^[[21;1H
                   ^[[22;1H                                                                                ^[[23;1H
                                                                        ^[[24;1H
                                    ^[[24;79H ^H^[[4h ^[[4l^[[1;1H^[[33mUbuntu Configuration^[[4;2H^[[m^O^[[30m^[[47m\uffff^\uffff^\uffff
^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\u0524 ^[[3
1mConfiguring courier-base^[[30m \uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^
\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff^[[5;2H\uffff^\uffff^
    \uffff^\uffff^\uffff^[[1m^[[37m^[[40m ^[[6;2H^[[m^O^[[30m^[[47m\uffff^\uffff^\uffff Courier uses several configuration files which are located in
         \uffff^\uffff^\uffff^[[1m^[[37m^[[40m ^[[7;2H^[[m^O^[[30m^[[47m\uffff^\uffff^\uffff /etc/courier. Some configuration files can be replaced by a
subdirectory  \uffff^\uffff^\uffff^[[1m^[[37m^[[40m ^[[8;2H^[[m^O^[[30m^[[47m\uffff^\uffff^\uffff where all files insides this directory are concatenated
 and considered    \uffff^\uffff^\uffff^[[1m^[[37m^[[40m ^[[9;2H^[[m^O^[[30m^[[47m\uffff^\uffff^\uffff to be a single, consolidated, configuration file.
                        \uffff^\uffff^\uffff^[[1m^[[37m^[[40m ^[[10;2H^[[m^O^[[30m^[[47m\uffff^\uffff^
                              \uffff^\uffff^\uffff^[[1m^[[37m^[[40m ^[[11;2H^[[m^O^[[30m^[[47m\uffff^\uffff^\uffff The web-based administration provided
by the courier-webadmin package     \uffff^\uffff^\uffff^[[1m^[[37m^[[40m ^[[12;2H^[[m^O^[[30m^[[47m\uffff^\uffff^\uffff relies on configuration director
ies instead of configuration files. If    \uffff^\uffff^\uffff^[[1m^[[37m^[[40m ^[[13;2H^[[m^O^[[30m^[[47m\uffff^\uffff^\uffff you agree, any directories
 needed for the web-based administration tool   \uffff^\uffff^\uffff^[[1m^[[37m^[[40m ^[[14;2H^[[m^O^[[30m^[[47m\uffff^\uffff^\uffff will be created unle
ss there is already a plain file in place.            \uffff^\uffff^\uffff^[[1m^[[37m^[[40m ^[[15;2H^[[m^O^[[30m^[[47m\uffff^\uffff^
                                                            \uffff^\uffff^\uffff^[[1m^[[37m^[[40m ^[[16;2H^[[m^O^[[30m^[[47m\uffff^\uffff^\uffff Create d
irectories for web-based administration ?                         \uffff^\uffff^\uffff^[[1m^[[37m^[[40m ^[[17;2H^[[m^O^[[30m^[[47m\uffff^\uffff^
                                                                        \uffff^\uffff^\uffff^[[1m^[[37m^[[40m ^[[18;2H^[[m^O^[[30m^[[47m
^\uffff^                     <Yes>                       ^[[37m^[[41m<No>^[[30m^[[47m                       \uffff^\uffff^\uffff^[[1m^[[37m^[[4
0m ^[[19;2H^[[m^O^[[30m^[[47m\uffff^\uffff^                                                                            \uffff^\uffff^\uffff^[[1m^[[3
7m^[[40m ^[[20;2H^[[m^O^[[30m^[[47m\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^
^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff
^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^
^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff
^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^
^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff\uffff^\uffff^\uffff^[[1m^[[37m^[[40m ^[[21;3H
                                 ^[[18;55H^[[18;23H^[[m^O^[[37m^[[41m<Yes>^[[23C^[[30m^[[47m<No>^[[18;28H


Oh ... and just in case your wondering ... I had a bad drive that I was using as /home ... where I had been downloading vhcs.sh ... replacing it is what solved the last issue ...


Thanks again,
KP

---

### Post by Gandalf on 2005-05-11
so i guess you are running VHCS now... ok np

---

### Post by cavalier67 on 2005-05-11
Gandalf,

Ummm ... no ... unfortunately it isn't running yet ... the problem that I got past by changing the drive was where it got stuck at "removing unneeded packages" ... now it is stuck on "Installing New Packages" ... sorry for the confusion ... see above for the log file ...

Any help is most appreciated ...

Thanks,
KP

---

### Post by Gandalf on 2005-05-11
[QUOTE=cavalier67]Gandalf,

Ummm ... no ... unfortunately it isn't running yet ... the problem that I got past by changing the drive was where it got stuck at "removing unneeded packages" ... now it is stuck on "Installing New Packages" ... sorry for the confusion ... see above for the log file ...

Any help is most appreciated ...

Thanks,
KP[/QUOTE]
 i really don't know what's going on on your box, till now i used the script on almost 30 servers (debian sarge and ubuntu) not even one hanged,
try the manual method

---

### Post by bartokk on 2005-05-13
> Originally Posted by **bnutting** 
*Do you see any entries in the access.log file for apache when you try to access it from the outside world? I would still question the firewall/router.* 

Only reason I'm not questioning the router is because it worked with a Windows 2003 Server.  :-$   Same IP, same DDNS.

I had to reinstall (big screw up on my part) so I dont have any logs to check.  I'm reinstalling and I'll post if I find anything.  I was told by a friend that I needed to allow access to outsiders, ie allow 0.0.0.0/255.0.0.0  I looked through the default *.conf files but couldnt find anything that was set to deny.  I did see where the path to the manuals were set to only allow from 127.0.0.0.  There was also some info on allowing access to server status reports and remote server configuration reports, but they are currently edited out.  Do I need to add some info to allow access to the index.html (in home folder)?  Or can I assume that since it is not set to deny it should allow incoming connections?

---

### Post by cavalier67 on 2005-05-13
Gandalf,
Could the problem be caused by my having a separate drive for /home ... This is where I have been downloading the script ... into /home/username and then installing from that location ...

KP

---

### Post by Gandalf on 2005-05-13
[QUOTE=cavalier67]Gandalf,
Could the problem be caused by my having a separate drive for /home ... This is where I have been downloading the script ... into /home/username and then installing from that location ...

KP[/QUOTE]
 no the script wil create /root/vhc_tmp and will work there, it will download/untar everything there, and then make install VHCS to /tmp/vhcs and then cp -r /tmp/vhcs to /

---

### Post by cavalier67 on 2005-05-13
Trying to narrow it down ... so ...

One more question ... I am running it from within a root terminal inside gnome ... is this a problem?

---

### Post by Gandalf on 2005-05-13
[QUOTE=cavalier67]Trying to narrow it down ... so ...

One more question ... I am running it from within a root terminal inside gnome ... is this a problem?[/QUOTE]
 no  not at all, it suppose to be ran with a root!

---

### Post by cavalier67 on 2005-05-13
Well ... I'm stumped ... Guess I'll try the manual method ...

Is there anything that you would like me to send you from my install before I blow it off of here?

Thanks for all the help,
KP

---

### Post by Gandalf on 2005-05-13
[QUOTE=cavalier67]Well ... I'm stumped ... Guess I'll try the manual method ...

Is there anything that you would like me to send you from my install before I blow it off of here?

Thanks for all the help,
KP[/QUOTE]
 no it's ok
try the manual method, i don't know what the problem with yours, i tried it already on many servers everything went smooth! :o

---

### Post by Beernut on 2005-05-13
I had the same problem with it hanging at the same point.  I just commented out that part of the script and did the remove on my own.  VHCS seemed OK wasn't really thrilled with the how it configured things and decided it was more than I needed.  I would probably give it try again if I was going to provide paid hosting.

On a side note I just setup the server for mail using  [http://hula-project.org](http://hula-project.org) based on Novells Netmail works like a charm if your looking for mail and calendaring.

---

