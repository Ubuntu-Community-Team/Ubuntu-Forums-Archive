---
title: "Change return path from www-data@domain.com"
date: 2008-05-23
forum: Server Platforms
---

### Post by jroc777 on 2008-05-23
Running 6.06.1 lts ,apache2,
Having issues with auto reply from website being blocked or classified as spam by gmail ,hotmail etc.

Would like to change the return path www-data to a valid email so it will match the from address.
In the example below I need From to match Return path.
I do not want to change the From

From: [email]me@domain.com[/email],
	"Content-type:text/html"@domain.com
Message-Id: <20080523152954.E0ECE3C92F2@domain.com>
Date: Fri, 23 May 2008 11:29:54 -0400 (EDT)
X-Barracuda-Connect: UNKNOWN[192.168.10.80]
X-Barracuda-Start-Time: 1211556741
X-Barracuda-Virus-Scanned: by Barracuda Spam Firewall at domain.com
Return-Path: [email]www-data@domain.com[/email]
X-OriginalArrivalTime: 23 May 2008 15:32:22.0682 (UTC) FILETIME=[31F8D7A0:01C8BCEA]

Can I set up an alias for www-data?
Where is the config that controls www-data ?
Thank You in advance

---

### Post by varkey on 2008-06-08
I also have the same question. Anybody?

---

### Post by quelx on 2008-06-08
Either **php** and/or **sendmail**/**postfix** needs configured

[http://ubuntuforums.org/showthread.php?t=598072&highlight=www-data+email](http://ubuntuforums.org/showthread.php?t=598072&highlight=www-data+email)

[http://php.net/mail](http://php.net/mail)

---

### Post by varkey on 2008-06-08
I got it working. I just set the return path when calling the mail function.

mail($to,$subject,$message,$headers,"-f [email]admin@domain.com[/email]");

Thank you!! :)

---

