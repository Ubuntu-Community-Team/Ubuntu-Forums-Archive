---
title: "No error output from php"
date: 2011-08-10
forum: Server Platforms
---

### Post by ingeva on 2011-08-10
After I "upgraded" to 11.04 php does not give any error output.
It's quite frustrating when a script produced absolutely nothing and
there's nothing to indicate the error.

I checked the error log settings in /etc/php5/apache2/php.ini, but that didn't help.
I removed apache and php and re-installed, but that didn't help.
I re-installed the complete system from scratch, but that didn't help.

I booted 9.10 which I still have in another partition, and the errors come out nice.
Basically the same install scripts are used for both versions.
I always install the server first, then get the updated version of all
programs including LAMP and the desktop.

I just ran the script from terminal (not from the browser). Errors
come out just fine.

Does anyone have the same experience or a clue about what to do?

---

### Post by SeijiSensei on 2011-08-12
Try /var/log/apache2/error.log.

Writing errors to the generated web page is considered poor security as it can be used to expose internals of your site to potential attackers.  You can change this behavior with "[display_errors]("http://www.php.net/manual/en/errorfunc.configuration.php#ini.display-errors")," but make sure you disable it when you put the site into production.

---

### Post by ingeva on 2011-08-13
> **SeijiSensei said:**
> Try /var/log/apache2/error.log.

Writing errors to the generated web page is considered poor security as it can be used to expose internals of your site to potential attackers.  You can change this behavior with "[display_errors]("http://www.php.net/manual/en/errorfunc.configuration.php#ini.display-errors")," but make sure you disable it when you put the site into production.
I thought I had done that, but it still didn't show errors.
Obviously I need the error messages. There's no way I can develop a website without them. The production system is on a remote host and I use their settings.
Checking the Apache log file I see that the errors have been logged there.
I thought I had checked the php.ini file and found the settings to be correct,
but when I checked again (after I re-installed the complete system) I see
that they are not. The documentation states that the default value is
display_errors = On,
but it was incorrectly set to Off. I'll reboot and check if my changes have done the trick.

Yes, it did. I must have made a mistake the first time,
but anyway it's annoying to see that the defaults are incorrectly set.

Thanks for the input!

---

