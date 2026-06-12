---
title: "localhost works, can't see on wife's PC"
date: 2007-11-07
forum: Server Platforms
---

### Post by twist-throttle on 2007-11-07
I am trying to setup my development environment at home.

My PC is an 7.10 Ubuntu Linux box with Apache2, PHP5, MySQL, PHPMyadmin, Static IP behind my router/gateway to my cable modem & etc.

I have a local wordpress install for development, which seems to be working just fine on the Linux Dev PC, I can view my local wordpress site via [http://localhost](http://localhost) and/or 127.0.0.1, BUT my problem is that I can not see this same local site from my wife's PC, which is on the same network/workgroup.

From her Windows XP PC, when I type in the browser my Linux IP address of 192.168.2.200, I do see the wordpress directory listed, as well as the single test.php file that I have there. Still from my wife's PC, when I click on the test.php file that is on my Linux PC, this file displays in her browser as it should, displaying my Linux PHP info that the file is supposed to do.
But when I click on the wordpress directory from her PC (as well as enter the url of 192.168.2.200/wordpress), the browser pauses for a second or two, then just gives me the generic browser error: IE7 &#8211; &#8220;IE can not display the webpage&#8221; & Firefox says - &#8220;can't establish a connection to localhost&#8221;... wait! That might be something... the url now says localhost, instead of the Linux IP address... her PC has no localhost running, so of course that would error out... her browser should still keep the 192.168.2.200 IP address in the url.
Hmmm... IE7 doesn't say localhost in it's url after the error, it still says 192.168.2.200/wordpress.

Oh, my Apache Access Logs say that I'm getting a 301 error:
192.168.2.100 - - [07/Nov/2007:19:13:47 -0600] "GET /wordpress/index.php HTTP/1.1" 301 - "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; .NET CLR 2.0.50727; .NET CLR 3.0.04506.30; InfoPath.1)"
192.168.2.100 - - [07/Nov/2007:19:13:59 -0600] "GET /wordpress/index.php HTTP/1.1" 301 - "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.9) Gecko/20071025 Firefox/2.0.0.9"

So yea, on my Linux PC, I can view the test.php & wordpress site just fine. But from her PC, I can only display the test.php file in the browser & see the directory listing of the wordpress install... but clicking the wordpress directory in her browser... this doesn't work.

1. It seems that PHP is working fine on the Linux server
2. It seems that her Windows browser is not being blocked from the Linux apache server.
3. I can view the local wordpress site on the Linux PC, but not on her PC that is on the same network.

Finally, I am posting this both on the wordpress & Ubuntu forums... I appreciate any advice or directions for me to search further.

---

### Post by twist-throttle on 2007-11-07
I have been able to come up with a solution for this, if you are interested, you can see the forum posts that helped me out [http://wordpress.org/support/topic/142498?replies=6](http://wordpress.org/support/topic/142498?replies=6)

---

