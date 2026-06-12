---
title: "Edgy server to OS X WebDAV reliability - it's mega poo"
date: 2006-12-16
forum: Server Platforms
---

### Post by macgerhard on 2006-12-16
Hi,

I've set up a local dev box with Edgy Eft on it and configured WebDAV on it following this article [http://www.fatalistreview.com/?p=59]("http://www.fatalistreview.com/?p=59"). This is my /etc/apache2/sites-available/default file:

[PHP]NameVirtualHost *
<VirtualHost *>
        ServerAdmin my@email.com
        ServerName uby.local

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

    Alias /uby /var/www
    <Location /uby>
        DAV On
        AuthType Digest
        AuthName "webdav-pass"
        AuthDigestFile  /home/gerhard/webdav-password
        Require valid-user
     </Location>

</VirtualHost>[/PHP]

First of all, Apache takes ages to process digest...

[PHP][Sat Dec 16 13:40:58 2006] [notice] Digest: generating secret for digest authentication ...
[Sat Dec 16 13:43:23 2006] [notice] Digest: done
[Sat Dec 16 13:43:24 2006] [notice] Apache/2.0.55 (Ubuntu) DAV/2 PHP/5.1.6 mod_ssl/2.0.55 OpenSSL/0.9.8b configured -- resuming normal operations[/PHP]

As you can see from this log, it's almost 3 minutes... Is this normal?

As I started to say, WebDAV feels very flaky, keeps stalling and simply hanging up. A snippet from my OS X console.log:

[PHP]Dec 16 13:59:20 apalia kernel[0]: webdav server: http://uby.local/uby/: not responding
Dec 16 13:59:20 apalia webdavd[2947]: stream_transaction: CFStreamError: domain 1, error 60
Dec 16 13:59:20 apalia KernelEventAgent[36]: tid 00000000 received VQ_NOTRESP event (1)
Dec 16 13:59:20 apalia KernelEventAgent[36]: tid 00000000 type 'webdav', mounted on '/Volumes/uby', from 'http://uby.local/uby/', not responding[/PHP]

And this seems to be repeating itself. Any ideas what is going on? Does it have anything to do with 501 UID & GID?

Any Mac gurus out there? HEEEEEELP ](*,)

---

### Post by macgerhard on 2006-12-16
Nevermind guys, I've been tinkering with it and it seems to be fine now. Found myself disabling mod_auth_digest because it was stalling apache for a few mins upon almost each force-reload. Maybe some of you will have an idea in regards to this.

Cheers anyways, Gerhard.

---

### Post by Cruncher on 2007-06-02
A workaround to fix the stalled startup with Digest enabled is to install package "rng-tools". Note that this requires a builtin hardware number generator, which may not be available on all machines.
Another solution would be to recompile apache2 by passing "--with-devrandom=/dev/urandom" to ./configure
Note that some people believe /dev/urandom is unsafer than the default /dev/random.

---

