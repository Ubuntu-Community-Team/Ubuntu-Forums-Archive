---
title: "mod_defensible"
date: 2010-08-21
forum: Security
---

### Post by MakOwner on 2010-08-21
Ubuntu LTS 10.4, LAMP and OpenSSH installaiton.

I'm looking into mod_defensible.
I have followed the how-to at [http://www.howtoforge.com/block-spammers-hackers-with-mod_defensible-on-apache2-debian-etch](http://www.howtoforge.com/block-spammers-hackers-with-mod_defensible-on-apache2-debian-etch) but apache fails to start after adding the changes to the apache2.conf file from the howto:

```

# Include generic snippets of statements
Include /etc/apache2/conf.d/

DnsblUse On
DnsblServers httpbl.abuse.ch sbl-xbl.spamhaus.org
DnsblNameserver 145.253.2.75

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

```

The error on startup failure is:
```

 * Restarting web server apache2                                                                                                                                                                               Syntax error on line 238 of /etc/apache2/apache2.conf:
Invalid command 'DnsblNameserver', perhaps misspelled or defined by a module not included in the server configuration

```

I have enabled the module with a2enmod.

Also, I have noted that sbl-xbl.spamhaus.org no longer responds and I can't find it in an nslookup.  

I have been searching for a bit but can't find any further documentation on the setup of this module.

---

### Post by unspawn on 2010-08-21
Wrt a2enmod: was mod_defensible present in the /etc/apache2/mods-available directory? Is it in the /etc/apache2/mods-enabled directory? Did you enable udns support and did you install libudns? Wrt spamhaus: zen.spamhaus.org replaces sbl-xbl ([http://www.spamhaus.org/zen/index.lasso](http://www.spamhaus.org/zen/index.lasso)). Wrt DnsblNameserver also see [http://www.docunext.com/wiki/Mod_defensible](http://www.docunext.com/wiki/Mod_defensible). Wrt mod_defensible itself note GIT ([http://git.naquadah.org/?p=mod_defensible.git;a=summary](http://git.naquadah.org/?p=mod_defensible.git;a=summary)) seems stale as of 2007. And finally also see mod_spamhaus: [http://www.lucaercoli.it/en/mod_spamhaus.html](http://www.lucaercoli.it/en/mod_spamhaus.html) ([http://www.howtoforge.com/how-to-block-spammers-with-apache2-mod_spamhaus-debian-etch](http://www.howtoforge.com/how-to-block-spammers-with-apache2-mod_spamhaus-debian-etch)).

HTH

---

### Post by MakOwner on 2010-08-21
> **unspawn said:**
> Wrt a2enmod: was mod_defensible present in the /etc/apache2/mods-available directory? Is it in the /etc/apache2/mods-enabled directory? Did you enable udns support and did you install libudns? Wrt spamhaus: zen.spamhaus.org replaces sbl-xbl ([http://www.spamhaus.org/zen/index.lasso](http://www.spamhaus.org/zen/index.lasso)). Wrt DnsblNameserver also see [http://www.docunext.com/wiki/Mod_defensible](http://www.docunext.com/wiki/Mod_defensible). Wrt mod_defensible itself note GIT ([http://git.naquadah.org/?p=mod_defensible.git;a=summary](http://git.naquadah.org/?p=mod_defensible.git;a=summary)) seems stale as of 2007. And finally also see mod_spamhaus: [http://www.lucaercoli.it/en/mod_spamhaus.html](http://www.lucaercoli.it/en/mod_spamhaus.html) ([http://www.howtoforge.com/how-to-block-spammers-with-apache2-mod_spamhaus-debian-etch](http://www.howtoforge.com/how-to-block-spammers-with-apache2-mod_spamhaus-debian-etch)).

HTH

Immensely.  Thank you.

---

