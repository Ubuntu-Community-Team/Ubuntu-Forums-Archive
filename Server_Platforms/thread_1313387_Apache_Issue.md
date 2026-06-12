---
title: "Apache Issue"
date: 2009-11-03
forum: Server Platforms
---

### Post by paulfraser on 2009-11-03
Okies, i have this silly problem i have been working on for a while now, and im pretty sure it boils down to permissions, but cannot get it working at all :(

I have 2 domains;
1) paulOr.net
2) imghostr.net

if you go to both atm, you will see they both point to paulOr.net,

i have apache, php, mysql install.

in my home dir ( /home/paul/ ) i have a structure like this:
/home/paul/web/paulor/
/home/paul/web/paulor/mysql/ <-- sub domain
/home/paul/web/paulor/stats/ <-- sub domain
/home/paul/web/hosted/imghostr <-- hosted is just another dir to keep the dir list clean.

i have also played with the apache sites-available files to reflect such things;

```
NameVirtualHost 97.107.139.161
        <VirtualHost 97.107.139.161>
            DocumentRoot /home/paul/web/paulor/
            ServerName paulor.net
            ServerAlias www.paulor.net
            <Directory /home/paul/web/paulor/>
                Options FollowSymLinks MultiViews
                AllowOverride All
            </Directory>
        </VirtualHost>

```

```
NameVirtualHost *
        <VirtualHost *>
            DocumentRoot /home/paul/web/paulor/stats/
            ServerName stats.paulor.net
            ServerAlias stats.paulor.net
            <Directory /home/paul/web/paulor/stats/>
                Options FollowSymLinks MultiViews
                AllowOverride All
            </Directory>
        </VirtualHost>

```

```
NameVirtualHost *
        <VirtualHost *>
            DocumentRoot /home/paul/web/hosted/imghostr/
            ServerName imghostr.net
            ServerAlias www.imghostr.net
            <Directory /home/paul/web/hosted/imghostr/>
                Options FollowSymLinks MultiViews
                AllowOverride All
            </Directory>
        </VirtualHost>

```

These are all reflected in sites-enabled aswell.

First problem is all the sites are showing the index file that is in paulor dir and second problem is how to get them to show the index files in there own dirs?

Any help would be appreciated, as im ripping my hair out here!

(apache has been restarted a million times on each change, so its not that)

---

### Post by Vegan on 2009-11-03
See my site in the forum Linux/LAMP for how to run Apache properly.

---

