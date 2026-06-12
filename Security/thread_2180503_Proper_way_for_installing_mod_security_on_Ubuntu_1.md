---
title: "Proper way for installing mod_security on Ubuntu 12.04 LTS?"
date: 2013-10-13
forum: Security
---

### Post by 2smooth on 2013-10-13
When installing mod-security with apt-get, I see that the following is installed 

/etc/modsecurity/modsecurity.conf

and that in the directory /etc/apache2/mods-available

the config file 'mod-security.conf'  is installed, with the following comment:

        # Include all the *.conf files in /etc/modsecurity.
        # Keeping your local configuration in that directory
        # will allow for an easy upgrade of THIS file and
        # make your life easier
        Include "/etc/modsecurity/*.conf"


But...

Also the package modsecurity-crs is installed with it's own config file:

/usr/share/modsecurity-crs/modsecurity_crs_10_config.conf


and with a Readme file for Debian:

/usr/share/doc/modsecurity-crs/README.Debian

with the following instruction:


modsecurity-crs for Debian
--------------------------

If you want to use modsecurity's CRS rules just include the following
configuration snippet in your modsecurity configuration (usually under
/etc/modsecurity):

<IfModule security2_module>
        Include /usr/share/modsecurity-crs/*.conf
        Include /usr/share/modsecurity-crs/base_rules/*.conf
</IfModule>

Under /usr/share/modsecurity-crs/ you may also find other *_rules/ directories
with more experimental or "violent" rules.

 -- Alberto Gonzalez Iniesta <agi@inittab.org>  Thu, 31 Mar 2011 16:42:48 +0200



So now I'm a little bit confused. Hence my question.

---

### Post by sandyd on 2013-10-13
> **2smooth said:**
> When installing mod-security with apt-get, I see that the following is installed 

/etc/modsecurity/modsecurity.conf

and that in the directory /etc/apache2/mods-available

the config file 'mod-security.conf'  is installed, with the following comment:

        # Include all the *.conf files in /etc/modsecurity.
        # Keeping your local configuration in that directory
        # will allow for an easy upgrade of THIS file and
        # make your life easier
        Include "/etc/modsecurity/*.conf"


But...

Also the package modsecurity-crs is installed with it's own config file:

/usr/share/modsecurity-crs/modsecurity_crs_10_config.conf


and with a Readme file for Debian:

/usr/share/doc/modsecurity-crs/README.Debian

with the following instruction:


modsecurity-crs for Debian
--------------------------

If you want to use modsecurity's CRS rules just include the following
configuration snippet in your modsecurity configuration (usually under
/etc/modsecurity):

<IfModule security2_module>
        Include /usr/share/modsecurity-crs/*.conf
        Include /usr/share/modsecurity-crs/base_rules/*.conf
</IfModule>

Under /usr/share/modsecurity-crs/ you may also find other *_rules/ directories
with more experimental or "violent" rules.

 -- Alberto Gonzalez Iniesta <agi@inittab.org>  Thu, 31 Mar 2011 16:42:48 +0200



So now I'm a little bit confused. Hence my question.
Copy/link /usr/share/modsecurity-crs/modsecurity_crs_10_config.conf to /etc/modsecurity - modsecurity rules are not enabled by default

---

