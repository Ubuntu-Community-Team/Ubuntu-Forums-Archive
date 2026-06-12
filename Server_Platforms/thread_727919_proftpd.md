---
title: "proftpd"
date: 2008-03-18
forum: Server Platforms
---

### Post by chaichy on 2008-03-18
hello community,
some days ago i ordered a new virtual server, on which i recently installed ubtunu server ( 6.06.1). The installation included plesk. I used plesk on other servers without problems but now on the ubuntu one i tried to connect via ftp but wasn't able to do so. After discovering the ftp server being proftpd i tried to start it manually. By typing "proftpd" the only thing i get back is:
```
 - IPv6 getaddrinfo 'v31119.1blu.de' error: Name or service not known
v31119.1blu.de - fatal: Socket operation on non-socket

```
so i googled thist error and found much information[1] saying i should just add 
```
UseIPv6 off
```
in the /etc/[proftpd]/proftpd.conf .
Of course i tried that but the only thing it did was giving me another error 
```
root@v31119:~# proftpd 
 - Fatal: unknown configuration directive 'UseIPv6' on line 66 of '/etc/proftpd/proftpd.conf'
root@v31119:~# /etc/init.d/proftpd start
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.
```
So I hope someone knows how to fix this because I really need ftp access to my server

**thanks in advance chiachy**

[1] i.e. [http://mrfoo.de/archiv/305-IPv6-getaddrinfo-error-Name-or-service-not-known.html](http://mrfoo.de/archiv/305-IPv6-getaddrinfo-error-Name-or-service-not-known.html)

---

### Post by smileypaul on 2008-03-19
You may have an older version of proftpd that doesn't support the "UseIPV6" switch.

also, depending how it was installed .. try

sudo /etc/init.d/proftpd restart

Ive been using proftpd for a few years now, hopefully i can help you out a bit.

---

### Post by chaichy on 2008-03-19
i can need every help i can get 
so thank you for your answer and offer 

i executed the command ander eveything i got was :
```
 sudo /etc/init.d/proftpd restart
ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.

```
BTW. the server was configured by plesk so it is started in inetd mode.
but unforunately i not adavanced enough with linux to know whats the difference.

and i tried to update proftpd by apt-get, but it says it was the newest version..

---

### Post by smileypaul on 2008-03-19
At the top of your configuration file

do you have :

ServerType              standalone


?


It would help if you could post your config file.


To check this


cat /etc/proftpd/proftpd.conf


it will then show you the config file

---

### Post by chaichy on 2008-03-19
here it is
```

#
# Includes required DSO modules. This is mandatory in proftpd 1.3
#
Include /etc/proftpd/modules.conf

#
# To have more informations about Proftpd configuration
# look at : http://www.proftpd.org/
#

# This is a basic ProFTPD configuration file (rename it to 
# 'proftpd.conf' for actual use.  It establishes a single server
# and a single anonymous login.  It assumes that you have a user/group
# "nobody" and "ftp" for normal operation and anon.

ServerName                      "ProFTPD"
#ServerType                     standalone
ServerType                      inetd
DefaultServer                   on
<Global>
DefaultRoot     ~               psacln
AllowOverwrite          on
</Global>
DefaultTransferMode     binary
UseFtpUsers                     on

# Port 21 is the standard FTP port.
Port                            21
# Umask 022 is a good standard umask to prevent new dirs and files
# from being group and world writable.
Umask                           022

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

#Following part of this config file were generate by PSA automatically
#Any changes in this part will be overwritten by next manipulation 
#with Anonymous FTP feature in PSA control panel.

#Include directive should point to place where FTP Virtual Hosts configurations
#preserved

ScoreboardFile /var/run/proftpd/scoreboard

# Primary log file mest be outside of system logrotate province

TransferLog /opt/psa/var/log/xferlog

#Change default group for new files and directories in vhosts dir to psacln

<Directory /var/www/vhosts>
        GroupOwner      psacln
</Directory>

# Enable PAM authentication
AuthPAM on
AuthPAMConfig proftpd

IdentLookups off 
UseReverseDNS off


AuthGroupFile   /etc/group

Include /etc/proftpd.include


```

---

### Post by smileypaul on 2008-03-20
Hmmm..


you may have to ask over at ;

[http://forums.proftpd.org/smf/](http://forums.proftpd.org/smf/)

---

### Post by chaichy on 2008-03-20
well another time registering at a forum..
but i'll try it ;) 
thank you so far

---

