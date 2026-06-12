---
title: "phpMyAdmin Ignores 'LoginCookieValidity'"
date: 2008-09-06
forum: Server Platforms
---

### Post by lightnb on 2008-09-06
phpMyAdmin automatically logs out after 30 minutes or so. When I'm actively developing on my own laptop, this isn't a very practical limitation.

I found a post suggesting that I could add a value to /etc/phpmyadmin/config.inc.php, called $cfg['LoginCookieValidity'], but this doesn't seem to have any effect.

The line I have reads:

[PHP]$cfg['LoginCookieValidity'] = 3600 * 24 * 365; // 1 year[/PHP]

Is there another way to disable or extremely retard auto-logout?

Thanks!

---

### Post by meshuggahner on 2008-09-15
This has been bugging me for a while now too - finally decided to venture into the phpmyadmin docs. This is by no means ideal for a production environment but works perfectly for a local development setup.

in your **/etc/phpmyadmin/config.inc.php** file edit / add the following
```

$cfg['Servers'][$i]['auth_type'] = 'config';
$cfg['Servers'][$i]['user'] = 'your_mysql_username';
$cfg['Servers'][$i]['password'] = 'your_mysql_password';

```

note: in my config I had to add the user and password lines - controluser / controlpass will not work.

This then removes the need to login altogether.

---

### Post by flowtron on 2008-09-20
> **meshuggahner said:**
> [...] This is by no means ideal for a production environment but works perfectly for a local development setup.
[...]
This then removes the need to login altogether.
As mentioned this _is not a secure way_ to handle the issue!
For one thing - even though phpmyadmin uses cookies to store some data - it needs to be configured to use cookies for authentication. To do this a line reading
```

$cfg['Servers'][$i]['auth_type'] = 'cookie';

```
needs to be activated. You might want to compare **/usr/share/doc/phpmyadmin/examples/config.sample.inc.php** too!
Because - for (additional) security - you should also have a line reading
```

$cfg['blowfish_secret'] = 'YOUR_big_SECRET'; /* YOU MUST FILL IN THIS FOR COOKIE AUTH! */

```
before any server lines (with appropriate **YOUR_big_SECRET**-string).
Then the line mentioned in the first post
```

$cfg['LoginCookieValidity'] = 3600 * 24 * 365; // 1 year

```
will work. For testing it might be prudent to enter something like **120** first though .. it's easier to wait for 2 minutes and see the **cookie**-session expired .. than waiting for one year ;-)
HTH

---

### Post by lightnb on 2008-09-23
Thanks flowtron,

That seems to have fixed the problem. (I'll let you know in a year if it worked ;) )

So if cookie logins aren't turned on, what does it use, PHP sessions?

---

### Post by MsTBWx2c on 2008-09-23
**[[color=red]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=red]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[size=3][color=red]Make money online,now![/color][/size]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

### Post by mariuss on 2008-10-04
Setting LoginCookieValidity did not do the trick in my case.

I don't think you have to set blowfish_secret, it should be set when phpMyAdmin is installed. Have a look at:
/usr/share/phpmyadmin/config.inc.php
/var/lib/phpmyadmin/blowfish_secret.inc.php

According to a debian bug report this is not working because LoginCookieValidity is overruled by a setting in php.ini: session.gc_maxlifetime

See: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=499399](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=499399)

Not sure what side effects to expect if I increase session.gc_maxlifetime.

Also wondering if it really worked for you guys by only setting LoginCookieValidity. Testing with shorter values, like 2 minutes, will of course work because session.gc_maxlifetime is set to 24 minutes by default (24*60=1440).

---

### Post by trtech on 2009-03-01
try putting 

ini_set('session.gc_maxlifetime', $cfg['LoginCookieValidity']);

after the line where you set $cfg['LoginCookieValidity']

---

### Post by nonanano on 2009-04-20
This solves the issue, cheers trtech!

I have the default setting set to 60 seconds on my live server, normally this is ok, but it seems phpmyadmin doesn't update the timeout on every request, so it will log out 60 seconds from the time you signed in, even if you have been using it during that 60 seconds.

This bug actually didn't exist in version 2.34.2.6, but it does in the most recent version of phpmyadmin.

---

### Post by williswatson on 2010-03-27
Please note that php         configuration option [session.gc_maxlifetime]("http://php.net/manual/en/session.configuration.php#ini.session.gc-maxlifetime")          might limit 
session validity and if session is lost, login cookie is         also invalidated.


plz google doc from the phpmyadmin.net

hope can help u some

---

### Post by Mark Rose on 2011-03-03
It's because of the debian way of doing things.

If /etc/php5/apache2/php.ini exists, edit the value session.gc_maxlifetime. Otherwise, the highest value in /etc/php5/*/php.ini will be used.

---

### Post by new_tolinux on 2011-03-09
Then maybe the "debian way of doing things" should be altered for Ubuntu.

There is a reason for values to be default, which is that the "default" as set works perfect most of the times.
Overrides are the exceptions. Just adjusting the defaults to fit the "needs" of phpmyadmin, will create the need to override the new defaults in every single other page on the webserver.
Therefore overrides should not just be ignored.

---

