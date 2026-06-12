---
title: "APC UPS (apcupsd) Questions"
date: 2015-09-07
forum: Server Platforms
---

### Post by Marc-NJ on 2015-09-07
I currently have an APC UPS hooked up to by Ubuntu server 12.04 (running on HP desktop hardware I believe) and have the apcupsd software installed on the Ubuntu server (and also the Apache and Webmin plugins for monitoring via a website and via Webmin).  

Earlier today, the location where this server is lost power, and by the time I had arrived power had been restored but it was apparent that power had been off long enough that the APC UPS had run out of battery and the server had shut off.  However, I'm not sure if the apcupsd also has the ability to gracefully shut down a connected Ubuntu server when it detects it will run out of battery power.  Is this something that it can do?  And if so, how can I check if this did happen and my Ubuntu server was gracefully shut down, or just had a hard shut off when the UPS ran out of battery power?

(Also - if it did have a hard shut off because potentially apcupsd wasn't configured correctly to do a graceful shutdown, how can I configure this?)

Thanks so much for any help!

---

### Post by tgalati4 on 2015-09-08
Yes, there is a [configuration]("https://help.ubuntu.com/community/apcupsd") setting to set both server shutdown after hitting a battery % remaining or a time-on-battery.  Then there is also a setting to turn the UPS off, so that it remains off when the power comes back on--to reduce the power surge damage that typically happens.  Of course this requires a manual reset of the UPS, but that is better than damaged equipment.

To get all of these elements to work correctly, you need to run tests.  Some APC UPS's have switches in the back or front panel settings to set the shutdown/restart-on-power settings.  Your server's BIOS has some restart behavior settings.  

You need to extensively [test]("http://www.apcupsd.org/manual/manual.html#testing-apcupsd") your configuration so that you understand how it works.  This is important for a remote server.  Simply installing *acpupsd* and hooking an UPS is only 20% of the effort required to make sure it works under various scenarios.  The default settings may not work for your Use Case.

Check the timestamps on your log files in /var/log.  They get created/rotated after each boot.  Check *syslog* and its previous version:

```
more /var/log/syslog
```

It has timestamps for each entry.  From that you should be able to determine how your machine behaved.  Acpupsd also sends email to root and puts power event files in /var/log.

---

### Post by SeijiSensei on 2015-09-08
Look at the MINUTES parameter in /etc/apcupsd/apcupsd.conf.  The default is to tell the system to shut itself down with three minutes runtime remaining on the battery.

---

### Post by tgalati4 on 2015-09-08
Yes, and 3 minutes is not useful for an old UPS with old batteries.  It should be set to 20 minutes, so that you get a clean shutdown, even with old batteries.  Batteries that have 3 to 5 years of use are considered "old".

---

