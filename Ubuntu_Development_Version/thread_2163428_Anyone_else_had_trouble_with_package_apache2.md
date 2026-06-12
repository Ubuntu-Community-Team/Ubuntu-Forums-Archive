---
title: "Anyone else had trouble with package apache2"
date: 2013-07-18
forum: Ubuntu Development Version
---

### Post by philinux on 2013-07-18
Apport caught this just now and it fired off a bug report.
[https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/1202653](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/1202653)

I tried to fix broken packages but it still errors.

```
Setting up apache2 (2.4.4-6ubuntu4) ...
Directory /etc/apache2/conf.d is not empty - leaving as is
Please note, that directory is considered obsolete and not read anymore by default
docvert
apache2: Syntax error on line 140 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/apache2/modules/libphp5.so: undefined symbol: unixd_config
 * Restarting web server apache2                                                             [fail] 
invoke-rc.d: initscript apache2, action "restart" failed.
dpkg: error processing apache2 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 apache2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm just having a look at the conf files.

---

### Post by dino99 on 2013-07-18
i've not got problem here on saucy i386, but the libphp5-embed package is not installed on my system.

---

### Post by philinux on 2013-07-18
> **dino99 said:**
> i've not got problem here on saucy i386, but the libphp5-embed package is not installed on my system.

This install is an upgrade from raring. It wont purge the above package either. This is 64 bit.

```
The following packages have unmet dependencies.
 apache2-mpm-prefork : Depends: apache2.2-common (= 2.2.22-6ubuntu5) but it is not installed
                       Depends: apache2.2-bin (= 2.2.22-6ubuntu5) but it is not installed
 libapache2-mod-php5 : Depends: apache2.2-common but it is not installed
 libphp5-embed : Depends: php5-common (= 5.5.0+dfsg-14ubuntu1) but 5.4.15-1ubuntu3 is installed
 php5-cli : Depends: php5-common (= 5.5.0+dfsg-14ubuntu1) but 5.4.15-1ubuntu3 is installed
 php5-gd : Depends: phpapi-20121212
           Depends: php5-common (= 5.5.0+dfsg-14ubuntu1) but 5.4.15-1ubuntu3 is installed
 php5-tidy : Depends: phpapi-20121212
             Depends: php5-common (= 5.5.0+dfsg-14ubuntu1) but 5.4.15-1ubuntu3 is installed
 php5-xsl : Depends: phpapi-20121212
            Depends: php5-common (= 5.5.0+dfsg-14ubuntu1) but 5.4.15-1ubuntu3 is installed
E: Unmet dependencies. Try using -f.
```

---

### Post by dino99 on 2013-07-18
are you also using uwsgi ? (dependent of libphp5-embed)

ore some ppas ?

---

### Post by philinux on 2013-07-18
> **dino99 said:**
> are you also using uwsgi ? (dependent of libphp5-embed)

ore some ppas ?

No. In fact i have no use for apache. Does the OS need it?

---

### Post by dino99 on 2013-07-18
i often check my rolling distro with gtkorphan, so i does not remember if libphp5-embed have been removed, or never been installed; by the way the stock saucy does not seems to need it.
I've glanced at the apache dependants, and the standard saucy does not need it, as i see

---

### Post by philinux on 2013-07-18
> **dino99 said:**
> i often check my rolling distro with gtkorphan, so i does not remember if libphp5-embed have been removed, or never been installed; by the way the stock saucy does not seems to need it.

It's not installed here either.

---

### Post by dino99 on 2013-07-18
> **philinux said:**
> It's not installed here either.

hm, some old settings inside the .local/.gconf,.gnome2,.config folders ?

---

### Post by philinux on 2013-07-18
> **dino99 said:**
> hm, some old settings inside the .local/.gconf,.gnome2,.config folders ?

Nothing changed at all. Because of these broken packages all other updates fail and a I cant remove them either.

---

### Post by dino99 on 2013-07-18
the next boot in recovery mode should solved that issue; or try with aptitude first

---

### Post by philinux on 2013-07-18
Someone's added a me too. So bug is now confirmed.

---

### Post by CAaronL on 2013-07-18
I just wanted to chip in to say that I too am experiencing this, and nothing I do seems to fix the problem.

---

### Post by philinux on 2013-07-19
> **CAaronL said:**
> I just wanted to chip in to say that I too am experiencing this, and nothing I do seems to fix the problem.

Bug now affects 11 people. These syntax errors are odd first one on line 140. Cant see anything obviously wrong

```
139  # Include module configuration:
140  IncludeOptional mods-enabled/*.load
141  IncludeOptional mods-enabled/*.conf
```

Second one only has one line in the file:

```
cat /etc/apache2/mods-enabled/php5.load
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
```

---

### Post by philinux on 2013-07-19
Well seeing as this laptop is not my main machine and for the sake of it here's what I did.

Opened synaptic and brought up the 5 broken packages and marked them for removal one by one starting at the bottom,

Then marked all upgrade and it's sorted now.

---

### Post by philinux on 2013-07-19
Wow. This bug got attention.  Triaged already and high. 

[https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/1202653](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/1202653)

What puzzles me is that only laptop got it amd not pc. Both of which are upgrades from raring. You'd think both would be affected.

---

