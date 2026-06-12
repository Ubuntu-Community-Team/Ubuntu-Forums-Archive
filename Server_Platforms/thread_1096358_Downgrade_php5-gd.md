---
title: "Downgrade php5-gd"
date: 2009-03-14
forum: Server Platforms
---

### Post by ChrisTek on 2009-03-14
I have an Ubuntu server (8.04 LTS) running a LAMP setup, PHP 5. I need to add php5-gd to it to get the GD library support.

Right now, it wants to install php5-gd=5.2.4-2ubuntu5.5 when I install it (which is the package that comes with 8.04), however, that comes with libfreetype6 version 2.3.5. My main problem is that one of my scripts relies on libfreetype6 version 2.1.10. So I figured hey, I'll just go add the old repositories and use aptitude to downgrade it.

I added the dapper repositories and tried this:

```
apt-get --purge remove libfreetype6
apt-get autoremove
apt-get install libfreetype6=2.1.10-1ubuntu2.5
```

It installed fine, so I restarted Apache2... Just to find out that I no longer have freetype support at all from PHP. So I removed that and reinstalled php5-gd so the original setup would come back.

```
apt-get --purge remove libfreetype6
apt-get autoremove
apt-get install php5-gd
```

Alright, so now I'm back to square one. I have one last thought, I'll just install the entire php5-gd package from dapper! So I run...

```
apt-get --purge remove php5-gd
apt-get autoremove
apt-get install php5-gd=5.1.2-1ubuntu3.13
```

When I run the last bit there, I get an error:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-gd: Depends: phpapi-20051025
           Depends: php5-common (= 5.1.2-1ubuntu3.13) but 5.2.4-2ubuntu5.5 is to be installed
E: Broken packages
```

So now I'm stuck. Can anyone tell me how to downgrade at least libfreetype6 from 2.3.5 => 2.1.10, or if needed downgrade php5-gd from 5.2.4 => 5.1.2 so I can get the older version of freetype? Thanks! :D

---

### Post by askreet on 2009-03-17
When you say you have a script the requires libfreetype 2.1.10, what kind of script is it?  PHP?

It sounds like you want to have two copies of libfreetype installed, one that will allow you to keep php5-gd up to date, and the specific one needed for your script.  If this is a PHP script, that'll make it more difficult.

I'm surpised you have a script that won't work with an updated version of the library, any chance of updating it?

---

### Post by ChrisTek on 2009-03-18
> **askreet said:**
> When you say you have a script the requires libfreetype 2.1.10, what kind of script is it?  PHP?

It sounds like you want to have two copies of libfreetype installed, one that will allow you to keep php5-gd up to date, and the specific one needed for your script.  If this is a PHP script, that'll make it more difficult.

I'm surpised you have a script that won't work with an updated version of the library, any chance of updating it?
It is PHP. I solved the problem in the meantime by switching my webserver to CentOS, which I've been meaning to do for awhile.

I researched further, and apparently the debian-based libfreetype renders fonts quite differently, the kerning is terrible and the antialiasing is quite bad as well. It's running happily now that I installed CentOS.

---

