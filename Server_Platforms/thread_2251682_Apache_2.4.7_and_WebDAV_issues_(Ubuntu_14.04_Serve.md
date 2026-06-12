---
title: "Apache 2.4.7 and WebDAV issues (Ubuntu 14.04 Server)"
date: 2014-11-06
forum: Server Platforms
---

### Post by TiredMan on 2014-11-06
Having a bit of a weird problem with WebDAV on a pair of Ubuntu 14.04 servers. I've been searching all over and can't seem to find any information about this aside from a thread at ServerFault from a few years ago, but the fix for that didn't work for me.

Basically, WebDAV works insofar as I can log into the server, and I can upload files. The problem is that the files do not upload in the specified directory. Instead, they are uploaded one level up, and renamed. If I upload, say, myfile.ext into /parentdir/mydir, instead of getting /parentdir/mydir/myfile.ext, I get, /parentdir/mydirmyfile.ext. This consistently happens across two servers, regardless of the client I'm using. I have tested so far with Cyberduck and Finder on Mac, and Cadaver on Linux, and all of them display this strange behaviour on both servers. Notably, this behaviour *didn't* occur on an older Debian server that was running Apache 2.2. I know the configuration options changed from Apache 2.2 to 2.4, but as far as I can tell, I have updated them correctly...

Additionally, subdirectories under the WebDAV-configured directory are inaccessible through WebDAV. I get a 404 error when accessing them through Cyberduck and Cadaver, and just empty directories when accessing the files after mounting the share in Finder. This is the error Cadaver throws:
```
dav:/> cd css
Could not access /css/ (not WebDAV-enabled?):
404 Not Found
```
Thinking that it might be trying to cd from the parent directory, I tried cd htdocs/css. Same error.

My config is as follows:

```

<VirtualHost *:80>
    ServerName webdav.domain.com
    ServerAlias webdav.domain.com
    ServerAdmin noc@domain.com
    DocumentRoot /var/www/sites/domain/htdocs/
    DavLockDB "/var/www/sites/domain/DavLock"

    <Location />
        DAV On
        AuthType Digest
        AuthName "DAV"
        AuthDigestProvider file
        AuthUserFile "/var/www/sites/domain/.dav_pw_digest"
        Require valid-user granted
        ForceType text/plain
    </Location>

    <Directory /var/www/sites/domain/htdocs/>
        Options Indexes FollowSymlinks MultiViews
        AllowOverride None
        Require all granted
    </Directory>

    Alias / /var/www/sites/domain/htdocs
    Alias /logs /var/www/sites/domain/logs
    php_flag engine off
</VirtualHost>

```

Options I've tried:
-For the 404 issue, I tried DavDepthInfinity On. I am aware that opens the possibility of DOS attacks, but it didn't work anyway, and has since been disabled.
-The final Alias line was, for a time, "Alias /htdocs/ /var/www/sites/domain/htdocs", but that didn't fix the error, all it meant was that I had to add htdocs to the URL when connecting. Notable about this, though, is that if I left the trailing slash off of /htdocs/, or excluded this line entirely, it would not allow me to connect at all. Adding or removing trailing slashes to other lines doesn't seem to do anything, and neither does adding or removing quotation marks.
-Related to that, I tried moving all of the configuration options in the <Location> section to the <Directory> section. Depending on which options I commented out or left active, I would either be unable to connect or I would be unable to upload a file at all.
-I've enabled and disabled pretty much every other option in this config. It either does nothing, or breaks it entirely.
-I've tried adding RewriteEngine Off, as mod_rewrite is active, but that didn't fix it either. This one is basically at the point where I'm just throwing stuff at it and seeing if it will stick.

All of the files in question are owned by www-data:www-data, though I've tried several different permission variations for everything. Files uploaded wind up owned by www-data:www-data with permissions of 644.

I also tried upgrading the server to 14.10, as I thought it may have been a bug in Apache 2.4.7, but it's not. The issue persisted after upgrading. So, I'm basically certain that this is an issue in a config file, but it appears to be beyond my ken.

---

### Post by SeijiSensei on 2014-11-06
> **TiredMan said:**
> If I upload, say, myfile.ext into /parentdir/mydir, instead of getting /parentdir/mydir/myfile.ext, I get, /parentdir/mydirmyfile.ext.

I know you said you tried various combinations of trailing slashes, but that still seems the likely explanation for the behavior you report.

I never include a trailing slash at the end of the DocumentRoot.  Did you try omitting that?

---

### Post by TiredMan on 2014-11-10
> **SeijiSensei said:**
> I know you said you tried various combinations of trailing slashes, but that still seems the likely explanation for the behavior you report.

I never include a trailing slash at the end of the DocumentRoot.  Did you try omitting that?

Yes. Just to be safe, I tested it again just now. Same issue.

---

