---
title: "apache2 not sending file size of downloads to browser with mod_include enabled"
date: 2009-05-19
forum: Server Platforms
---

### Post by Ichthyos on 2009-05-19
Hi everyone,

I've been using Apache HTTP Server 2.2 on Ubuntu Server (Intrepid) for a while, but just recently ran into the following issue. I enabled mod_include in a directory so that I could use SSI (server-side includes) in certain .shtml files there, but then noticed my web browser (Firefox 3) is not aware of the file sizes of large files I download from that directory. Disabling mod_include gets rid of this annoyance, but it'd be nice to have it enabled while preserving download time estimates in Firefox.

I apologize in advance if this has been asked before, but apparently my search skills are not up to par.

Below are all parts of my apache2 configuration that would apply to the directory in question:
```

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        <Directory /var/www/media/>
                #Options +Includes
                IndexOptions FancyIndexing
                HeaderName /media/HEADER.shtml
                IndexIgnore HEADER.shtml .htaccess
                AuthType Digest
                AuthName "Aquatica Media"
                AuthUserFile /etc/apache2/digest
                Require valid-user ichthyos
                #SetOutputFilter INCLUDES
        </Directory>

```Thanks in advance!

---

