---
title: "Limiting applications to a single vhost"
date: 2008-07-15
forum: Server Platforms
---

### Post by DuronForever on 2008-07-15
I have an ubuntu server with, among other things, a webserver configuration. Runs apache2 and a couple of name-based vhosts.

I also have several web-applications installed, like squirrelmail/mrtg/phpmyadmin/etc. When you apt-get these, they usually have a /etc/mrtg/apache.conf, and a symlink to that in either /etc/apache2/sites-available/ or in /etc/apache2/conf.d/.

(Incidentally, the ones that did the latter, I moved to sites-available. Will that confuse apt-get on an upgrade?)

In these apache.confs, there's usually an Alias directive and a related <Directory> section, like so:
```
Alias /mrtg /var/www/mrtg
<Directory /var/www/mrtg>
        ...
</Directory>
```

This is neat as far as it goes, it allows you to a2ensite/a2dissite to enable/disable the (sub-)sites in the standard fashion. But what I would like would be for these Aliases to only be valid for a particular one of my vhosts, and preferably still fit into the overall scheme. This requires (as far as I can tell) that the Alias directive be inside the <VirtualHost> section.

Has anyone figured out a neat and standard way to do this that preserves the a2ensite/a2dissite functionality, or at least the "add/remove symlink to en/disable site" function?

The only one I can think of that's remotely neat is to mkdir a sites-available/vhost1, put the config files for these subsites in that one, then make a /etc/apache2/sites-enabled-vhost1/ (NOT a subdir of sites-enabled, because that'd go into the regular Include), and then Include the latter dir into vhost1's configuration snippet.

Can anyone think of something better, that still doesn't put application-specific commands into the vhost1 configuration?

---

