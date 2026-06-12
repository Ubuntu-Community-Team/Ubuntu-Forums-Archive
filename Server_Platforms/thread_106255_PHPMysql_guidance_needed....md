---
title: "PHP/Mysql guidance needed..."
date: 2005-12-20
forum: Server Platforms
---

### Post by mindwerks on 2005-12-20
I'm very new to the Linux/Ubuntu world and wanted to change that by creating a small webserver that I can learn PHP on. But I seem to be having some slight problems.

After I installed Ubuntu I installed Apache2,PHP5, PHP-mysql and got that working fine (ran a couple of test scripts). Then I installed Mysql and it seemed to work fine. I was unable to create connections to Mysql from PHP though. I kept getting a fatal PHP error that according to google and various other sites meant that my Mysql extentions were not compiled into the PHP. 

I thought PHP-mysql was used for that but figured that maybe since mysql wasn't installed when I installed PHP that it failed or isn't linked up right. In an attempt to remedy it I removed and reinstalled PHP5 and PHP5-mysql and now PHP doesn't work LOL. When I access the PHP pages it tries to download the script rather then execute it. I imagine the PHP service/daemon isn't started but I'm not really sure how to investigate that. 

I used synaptec for all of the installs and removals...

Anyone have some hints for a noob. :)

---

### Post by ad noiseam on 2005-12-20
Did you try this the [wiki articles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=php+mysql&titlesearch=Titles) about this?

---

### Post by localzuk on 2005-12-20
Take a look in /etc/apache/conf/httpd.conf and see if there is a line such as ```
AddHandler php5-script php
```

If there is, I would recommend removing all the components (php, apache2) and re-installing. Else if there isn't then add one.

Also, you need to be loading the php5 module so there should be a line that is similar to:

```
LoadModule php5_module        modules/libphp5.so
```

The easiest way to diagnose it is to post your httpd.conf file here.

---

### Post by mindwerks on 2005-12-20
Yeah, I'll post it when I get off work (don't have access to the machine right now) and give your suggestions a try. 

I remember looking around for the httpd.conf file and being unable to find it. I'll look in the directory you listed and hopefully I'll have better luck. 

If that fails I'll take your suggestion and just remove apache/PHP and reinstall them. 

Thanks for the help. I'll keep you posted.
:)

---

