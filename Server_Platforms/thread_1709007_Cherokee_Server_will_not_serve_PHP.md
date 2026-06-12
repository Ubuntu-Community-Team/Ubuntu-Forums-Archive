---
title: "Cherokee Server will not serve PHP"
date: 2011-03-17
forum: Server Platforms
---

### Post by jnorthr on 2011-03-17
Hello world :)

Did a Cherokee server install using the instructions here [http://www.howtoforge.com/installing-cherokee-with-php5-and-mysql-support-on-ubuntu-9.04](http://www.howtoforge.com/installing-cherokee-with-php5-and-mysql-support-on-ubuntu-9.04)

have created a test php page as described called /var/www/info.php, did chmod a+x info.php and chmod 777 info.php just to avoid permission issues.

killed both apache and tomcat servers, then did:

/etc/init.d/cherokee start 

which worked ok and started Opera browser, then keyed [http://localhost](http://localhost) to confirm cherokee is running ok. Then when i try [http://localhost/info.php](http://localhost/info.php)
it does not send the php file thru the parser, but brings up a DOWNLOADING FILE dialog, to let me save the source. 

Think i may need to change a config table somewhere to make it happen, but where ???
ta

---

### Post by jnorthr on 2011-03-17
found the answer here: [http://www.cherokee-project.com/doc/cookbook_php.html](http://www.cherokee-project.com/doc/cookbook_php.html)

We need the cherokee-admin feature,  so from a terminal command line type:
cherokee-admin -b

then open a browser and in the address bar, type: [http://localhost:9090](http://localhost:9090) to bring up the cherokee admin feature.
The whole idea is simple once you see how, look across top for the VSERVER icon and click that. Down th eleft side is a list of your virtual servers, i only have one, so it's called default. Click that to see a set of tabs like BASIC, HOST MATCH, BEHAVIOR, etc. Click the BEHAVIOR choice then at the bottom is RULE MANAGEMENT button. Click that.

This will take you to a BEHAVIOR panel with a + sign which you click. This opens a dialog of different kinds of servers you could install. Click LANGUAGES to see choices of PHP and .NET, etc. Click PHP then click ADD button at bottom.

You may need to use a terminal session to find out if you have FAST CGI features. In terminal, type: php-cgi -v  to see your featureset. If you see (cgi-fcgi) then you have fast cgi processing available to you.

Back on the BEHAVIORS panel you should now see Extensions PHP on the left and on the right side, your handler can now be FAST-CGI

Finally be sure to click the SAVE button at top of admin panel. You can choose either  a graceful server restart. In a browser address type: [http://localhost/about](http://localhost/about)  just to see if things are running ok. 
Mine was not. So i tried stopping and restarting the server. From a terminal session, type: /etc/init.d/cherokee status   to review the server status, and since mine was still running, i had to key: /etc/init.d/cherokee stop
then: /etc/init.d/cherokee start
then from a browser address bar, typed: [http://localhost/info.php](http://localhost/info.php)
to bring up a full panel of cherokee server stats about PHP. :popcorn:

---

