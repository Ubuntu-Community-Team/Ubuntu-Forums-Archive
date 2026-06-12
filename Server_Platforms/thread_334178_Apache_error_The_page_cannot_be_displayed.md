---
title: "Apache error: The page cannot be displayed"
date: 2007-01-08
forum: Server Platforms
---

### Post by cocotu on 2007-01-08
Here at work a set up a apache server using Xubuntu. When I type the machine IP address I get this:

**The page cannot be displayed**
There is a problem with the page you are trying to reach and it cannot be displayed.

Please try the following:

    * Click the Refresh button, or try again later.
    * Open the Web site home page, and then look for links to the information you want.
    * If you believe you should be able to view this directory or page, please contact the Web site administrator by using the e-mail address or phone number listed on the Web site home page. 

10060 - Connection timeout
Internet Security and Acceleration Server

Technical Information (for support personnel)

    * Background:
      The gateway could not receive a timely response from the Web site you are trying to access. This might indicate that the network is congested, or that the Web site is experiencing technical difficulties.

    * ISA Server: isagatewayiii.exchange.goodwillny.org
      Via:

      Time: 1/8/2007 7:46:01 PM GMT 

But when I type: **[http://127.0.0.1/apache2-default/](http://127.0.0.1/apache2-default/)** I get the default apache page and everything is fine.  What is the problem? This the output of *netstat -plant*:

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     4749/mysqld 
tcp        0      0 127.0.0.1:3402          0.0.0.0:*               LISTEN     4167/hpiod 
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     4858/smbd 
tcp        0      0 127.0.1.1:631           0.0.0.0:*               LISTEN     5588/cupsd 
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     4858/smbd 
tcp        0      1 10.0.3.238:4749         72.21.63.182:80         SYN_SENT   4303/freshclam 
tcp6       0      0 :::80                   :::*                    LISTEN     5486/apache2 
tcp6       0      0 :::22                   :::*                    LISTEN     4876/sshd 

Thanks...

---

### Post by hal10000 on 2007-01-08
Maybe per default apache block other ip addresses than from localhost, so you might have to edit your httpd.conf file.

---

### Post by cocotu on 2007-01-08
Before I installed a LAMP server I didn't have these problems. Now I'm using Xubuntu, is it different from the one you get in the LAMP version? I will check httpd.conf file in the morning.

Thanks

---

### Post by cocotu on 2007-01-09
This is the httpd.conf file, I don't see any IP blocked.  Thanks

This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

---

### Post by hal10000 on 2007-01-09
you may also look into your .htaccess files.

---

### Post by Biggus on 2007-01-09
Dude, isn't it that the default directory to serve up pages is /var/www/ , and you just don't have a file called index.html in it?

---

### Post by cocotu on 2007-01-09
It was only a firewall problem. I had firestarter installed a few week ago and it was blocking port 80 for HTTP. Everything is fine now...

Thanks for your help!!

---

### Post by hal10000 on 2007-01-09
@Biggus:
No, this can't be the reason, because when doing a http:127.0.0.1 he gets the default apache page.

I guess you have to create a directive that points to the machine's IP address.

---

