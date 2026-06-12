---
title: "Apache error"
date: 2010-11-02
forum: Server Platforms
---

### Post by Sav1 on 2010-11-02
I have Zonemnder 1.24.2 running on Ubuntu 10.10 server (had same issue before on Ubuntu Desktop 10.04)

Everything works except for event replays, it shows one frame and then locks up. I have to close the browser and open it again before I can access Zoneminder, just closing the tabs doesn't help.

I have tested from several different computers with different browsers and I get the same result.

I get the following in my apache error log on the server as I click the replay button.

Any advice would be appreciated.

> [Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 808, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 813, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 818, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 823, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 828, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 808, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 813, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 818, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 823, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 828, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 808, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 813, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 818, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 823, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 828, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 808, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 813, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 818, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 823, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:53 2010] [error] [client **.***.***.***] PHP Deprecated:  Function ereg() is deprecated in /usr/share/zoneminder/includes/functions.php on line 828, referer: [http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter](http://*******.dvrdns.org/zm/index.php?view=events&page=1&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1

[Mon Nov 01 11:23:57 2010] [error] [client **.***.***.***] socket_sendto( /tmp/zms-816036s.sock ) failed: No such file or directory, referer: [http://*******.dvrdns.org/zm/index.php?view=event&eid=19&filter](http://*******.dvrdns.org/zm/index.php?view=event&eid=19&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1&sort_field=StartTime&sort_asc=1&page=1

[Mon Nov 01 11:23:57 2010] [error] [client **.***.***.***] array (\n  0 => \n  array (\n    'file' => '/usr/share/zoneminder/ajax/stream.php',\n    'line' => 55,\n    'function' => 'ajaxError',\n    'args' => \n    array (\n      0 => 'socket_sendto( /tmp/zms-816036s.sock ) failed: No such file or directory',\n    ),\n  ),\n  1 => \n  array (\n    'file' => '/usr/share/zoneminder/index.php',\n    'line' => 116,\n    'args' => \n    array (\n      0 => '/usr/share/zoneminder/ajax/stream.php',\n    ),\n    'function' => 'require_once',\n  ),\n), referer: [http://*******.dvrdns.org/zm/index.php?view=event&eid=19&filter](http://*******.dvrdns.org/zm/index.php?view=event&eid=19&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1&sort_field=StartTime&sort_asc=1&page=1


5min later
> [Mon Nov 01 11:28:54 2010] [warn] [client xx.xxx.xxx.xxx] Timeout waiting for output from CGI script /usr/lib/cgi-bin/nph-zms, referer: [http://xxxxx.dvrdns.org/zm/index.php?view=event&eid=19&filter](http://xxxxx.dvrdns.org/zm/index.php?view=event&eid=19&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1&sort_field=StartTime&sort_asc=1&page=1

---

### Post by Ryan Dwyer on 2010-11-02
The ereg() function in PHP is deprecated in PHP 5.3 and above, which is what Ubuntu 10.10 uses. It means the function is going to be removed in an upcoming version of PHP and shouldn't be used any more. Although you're getting warnings in the error log, that function should still work.

I've never used Zoneminder so I don't know what it's trying to do or where the problem lies. Maybe ask their support forum if they have one.

---

### Post by Sav1 on 2010-11-02
> **Ryan Dwyer said:**
> The ereg() function in PHP is deprecated in PHP 5.3 and above, which is what Ubuntu 10.10 uses. It means the function is going to be removed in an upcoming version of PHP and shouldn't be used any more. Although you're getting warnings in the error log, that function should still work.

I've never used Zoneminder so I don't know what it's trying to do or where the problem lies. Maybe ask their support forum if they have one.

Thanks for the reply, I figured out that was not the problem as I get the same issue on another machine that is working correctly.

It is trying playback an event which is stored as a series of images, I can view the images one at a time but can't play them back as a stream.

I have posted on their forum but have not received a reply.

The problem must be with the following.
> 
[Mon Nov 01 11:23:57 2010] [error] [client **.***.***.***] socket_sendto( /tmp/zms-816036s.sock ) failed: No such file or directory, referer: [http://*******.dvrdns.org/zm/index.php?view=event&eid=19&filter](http://*******.dvrdns.org/zm/index.php?view=event&eid=19&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1&sort_field=StartTime&sort_asc=1&page=1

[Mon Nov 01 11:23:57 2010] [error] [client **.***.***.***] array (\n  0 => \n  array (\n    'file' => '/usr/share/zoneminder/ajax/stream.php',\n    'line' => 55,\n    'function' => 'ajaxError',\n    'args' => \n    array (\n      0 => 'socket_sendto( /tmp/zms-816036s.sock ) failed: No such file or directory',\n    ),\n  ),\n  1 => \n  array (\n    'file' => '/usr/share/zoneminder/index.php',\n    'line' => 116,\n    'args' => \n    array (\n      0 => '/usr/share/zoneminder/ajax/stream.php',\n    ),\n    'function' => 'require_once',\n  ),\n), referer: [http://*******.dvrdns.org/zm/index.php?view=event&eid=19&filter](http://*******.dvrdns.org/zm/index.php?view=event&eid=19&filter)[terms][0][attr]=MonitorId&filter[terms][0][op]=%3D&filter[terms][0][val]=1&sort_field=StartTime&sort_asc=1&page=1


---

### Post by Rattle1 on 2010-11-21
Perhaps is worth checking this out: [http://www.zoneminder.com/wiki/index.php/ZoneMinder_1.24.2_Bugfixes](http://www.zoneminder.com/wiki/index.php/ZoneMinder_1.24.2_Bugfixes)

---

### Post by wongo888 on 2010-11-22
Does this post help?

[http://www.zoneminder.com/forums/viewtopic.php?p=51097&sid=608e4ea6d01dc43d33807b515685afd2](http://www.zoneminder.com/forums/viewtopic.php?p=51097&sid=608e4ea6d01dc43d33807b515685afd2)

---

### Post by Sav1 on 2010-11-22
Thanks for the replies, but I had solved this issue.

"Pre event image count" must be set lower than "Image buffer size"

---

### Post by aaronLund on 2012-12-01
Where did you change the configuration?

I'm having the same issue.

---

### Post by ryan28 on 2013-09-04
I know this post is aged, however I have run across this problem as well.  Seeing as I was using presets for the most part and had a 40-10 buffer ratio as mentioned previously I looked for other anomolies.  On one of my Camera's I had set the "Alarm Frame" to 5 in hopes that it would trigger fewer alarms.  Once I set this back to1 it seems that the errors have stopped.

Just something else to look at since this seems to be an on going issue,

---

