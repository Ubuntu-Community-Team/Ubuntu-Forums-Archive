---
title: "Changing apache default config directory"
date: 2010-09-25
forum: Server Platforms
---

### Post by iiz on 2010-09-25
Hello all. Is it possible to change the default configuration directory of an apache install. Not the web root folder but the directory which the config files are stored. I want to change from /etc/apache2 to /config/apache2. On compile you can change using --sysconfdir=DIR but after install I cannot figure it out.

Thank you

---

### Post by richardjh on 2010-09-25
The configuration directory is only really relevant when apache starts up and read the configuration files right?

If you look at the init script at /etc/init.d/apache2, look for the lines at the top of the script

```
if [ -n "$APACHE_CONFDIR" ] ; then
        if [ "${APACHE_CONFDIR##/etc/apache2-}" != "$APACHE_CONFDIR}" ] ; then
                DIR_SUFFIX="${APACHE_CONFDIR##/etc/apache2-}"
        else
                DIR_SUFFIX=
        fi
elif [ "${0##*/apache2-}" != "$0" ] ; then
        DIR_SUFFIX="-${0##*/apache2-}"
        APACHE_CONFDIR=/etc/apache2$DIR_SUFFIX
else
        DIR_SUFFIX=
        APACHE_CONFDIR=/etc/apache2
fi
```You can see it the variable $APACHE_CONFDIR is set it will use that, or you could just edit the line in the else bit

```

APACHE_CONFDIR=/etc/apache2
```and change it to
```

APACHE_CONFDIR=/config/apache2
```

---

