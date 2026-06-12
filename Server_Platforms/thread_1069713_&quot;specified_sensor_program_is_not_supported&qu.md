---
title: "&quot;specified sensor program is not supported&quot; after upgrade to 8.04 Hardy Heron"
date: 2009-02-14
forum: Server Platforms
---

### Post by cornell737 on 2009-02-14
I was using 7.10 server edition, and had phpysinfo and phpMyAdmin installed and working.  I upgraded to 8.04 Hardy Heron using (all commands were run with sudo):

apt-get update
apt-get install update-manager-core
do-release-upgrade

as indicated in [http://www.howtoforge.com/upgrade-ubuntu-7.10-server-to-8.04-lts](http://www.howtoforge.com/upgrade-ubuntu-7.10-server-to-8.04-lts)

When it asked about replacing modified configs, I kept the existing ones, as indicated in the above page.

After the upgrade, phpMyAdmin is still working, so apache2 and php are working.

But attempts to access phpsysinfo yields a page saying:

    **Huston, we got a problem.**

            **Oh, I'm sorry. Something seems to be wrong. **

        specified sensor program is not supported  ./xml.php on line 51 
bad configuration in config.php for $hddtemp_avail  ./xml.php on line 62 





After googling, I found a suggestion to chown -R root:www-data /usr/share/phpsysinfo


Checking the permissions, I found they weren't root:www-data, so I ran the chown, checked again and the permissions are now root:www-data.


I restarted apache2 with /etc/init.d/apache2 restart


I still got the same message.


For giggles and grins, I chowned /etc/phpsysinfo as well, restarted apache, still get the same message



Can anyone help?  Do you need more information?



TIA
Cornell

---

### Post by cornell737 on 2009-02-15
Resolved.

Found a config.php from another Hardy Heron machine, with the same version of phpsysinfo.  Copied it, restarted apache2, and it's working :-)

Thanks anyway, folks

---

### Post by xzibiz on 2009-02-28
i'm having same problem after updating like you had.
Can you post the config that works ?
i'm using phpSysInfo - 3.0-rc6.

---

### Post by comsciprof on 2009-05-02
Another fix here is to purge phpsysinfo, so that all previous configuration files are remove. Then, reinstall phpsysinfo.

To purge phpsysinfo:

[FONT="Courier New"]aptitude purge phpsysinfo[/FONT]

To re-install phpsysinfo:
[FONT="Courier New"]aptitude install phpsysinfo[/FONT]

---

