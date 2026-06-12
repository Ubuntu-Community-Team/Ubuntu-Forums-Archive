---
title: "proftpd - CreateHome"
date: 2005-12-09
forum: Server Platforms
---

### Post by gotcha on 2005-12-09
I've been trying to add some kind of homedirectory using CreateHome for ftp users on my server.

My server is running proftpd with mysql and MyftpAdmin and apache2.

The thing is, I use MyftpAdmin to add users and to add some of them to a group I call "Web". I want users of the group "Web" to be able to set up their own homepage on my server. 

So I have my proftpd root pointed to /srv/ftp/ and inside that directory I have two folders, one called upload (unlimited access to all my ftp users) and http (users of the group "Web" should get access to this one). Inside the http folder I want users of the group "Web" to have their own folder (homedirectory) that only they have access to change things in (they should not be able to do changes in http, but only inside their homedirectory). 

My proftpd.conf so far :P 

```

# 'proftpd.conf' for actual use.  It establishes a single server
# and a single anonymous login.  It assumes that you have a user/group
# "nobody" and "ftp" for normal operation and anon.

ServerName   "- Welcome to xxx ProFTPD Server -"
#ServerType   standalone
ServerType      inetd
DefaultServer   on
DefaultRoot /srv/ftp/

Port 30
PassivePorts 51000 51999
MasqueradeAddress       xxx.xxx.com
Umask 022
MaxInstances 30
MaxClientsPerHost 8

AllowStoreRestart on

User ftp
Group ftp

#SSL -----
#AccessGrantMsg "If your FTP client supports TLS/SSL use it"
#TLSEngine on
#TLSLog /var/log/proftpd/proftpdtls.log
#TLSRequired off
#TLSOptions NoCertRequest
#TLSVerifyClient off
#TLSProtocol TLSv1
#TLSProtocol SSLv23
#TLSRSACertificateFile /etc/proftpd/ca/host.cert
#TLSRSACertificateKeyFile /etc/proftpd/crl/host.key
#TLSRSACertificateFile /etc/proftpd/certs/host.pem
# End SSL

SQLAuthTypes xxx
SQLAuthenticate xxx
SQLConnectInfo xxx
SQLUserInfo xxx
SQLGroupInfo xxx
SQLUserWhereClause xxx
SQLDefaultGID xxx
SQLDefaultUID xxx
SQLHomedirOnDemand xxx
RequireValidShell xxx
SQLLog xxx
SQLNamedQuery xxx

### Log trafic (STOR, RETR commands)
SQLLog STOR,RETR,ERR_STOR,ERR_RETR logtrafic
SQLNamedQuery logtrafic FREEFORM "INSERT INTO history (username, filename, transfertype, transfersize, transferhost, transfertime, transferdate) VALUES('%u'

### Log user error events (ERR_* commands)
SQLLog ERR_* logevents
SQLNamedQuery logevents FREEFORM "INSERT INTO userevents (username, eventtype, description, eventdate) VALUES ('%u', '%m', '%r', NOW())"

CreateHome on 755 skel /srv/ftp/http/ dirmode 755

#<Directory /*>
#       AllowOverwrite          off
#       <Limit WRITE>
#               DenyAll
#               AllowGroup admin
#       </Limit>
#</Directory>

<Directory /srv/ftp>
        <Limit READ DIRS>
                AllowAll
        </Limit>
        <Limit WRITE>
        </Limit>
</Directory>

<Directory /srv/ftp/upload>
        AllowOverwrite on

        <Limit READ DIRS>
                AllowAll
        </Limit>
        <Limit STOR MKD XMKD>
                AllowAll
        </Limit>

        <Limit WRITE>
                AllowAll
        </Limit>
        <Limit DELE>
                DenyAll
        </Limit>
</Directory>

<Directory /srv/ftp/http>
        AllowOverwrite on

        <Limit READ DIRS>
                DenyAll
                AllowGroup web
        </Limit>
        <Limit STOR MKD XMKD>
                DenyAll
        </Limit>

        <Limit WRITE>
                DenyAll
        </Limit>
        <Limit DELE>
                DenyAll
        </Limit>
</Directory>

AllowOverwrite off
RootLogin off

```
CreateHome is not working

and in my apache2 sites-enable I have added

```

Alias /http "/srv/ftp/http/"
    <Directory "/srv/ftp/http/">
        Options Indexes FollowSymlinks MultiViews
        AllowOverride None
        Order allow,deny
        Allow from all
    </Directory>

```
But I would rather have something like this: "my.server.com/user" instead of "my.server.com/http/user". Dunno how to do this tho :P

But since Im not that good at Linux and I don't know what I do wrong, I would appriciate some help :) 

I have read the miniHOWTO on createhome but, cant manage to do it right anyway :razz:

---

