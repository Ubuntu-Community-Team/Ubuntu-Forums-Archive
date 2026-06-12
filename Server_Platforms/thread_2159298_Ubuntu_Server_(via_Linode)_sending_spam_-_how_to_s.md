---
title: "Ubuntu Server (via Linode) sending spam - how to stop it?"
date: 2013-07-02
forum: Server Platforms
---

### Post by MadMonkMike on 2013-07-02
Hello gents, 

So today our server was shut down by Linode due to the quantity of spam mail it was sending out. We have many WordPress dev sites up on this server along with one client site and I know that WordPress can be an attack vector. 

I checked mailq and I see tons of stuff trying to go out and constantly getting "temporarily suspended"- I presume this is, in fact, the spam script. 

Seen here:

```
E097F5A77BA     8721 Mon Jul  1 23:42:45  MAILER-DAEMON(delivery temporarily suspended: connect to madmonkdev.com[50.116.40.178]:25: Connection refused)
                                         "apache2@no-reply"@madmonkdev.com


E21905A5E1F     8977 Mon Jul  1 14:17:36  MAILER-DAEMON
(delivery temporarily suspended: connect to madmonkdev.com[50.116.40.178]:25: Connection refused)
                                         "apache2@no-reply"@madmonkdev.com


E44EB5A76D9     8725 Mon Jul  1 18:52:34  MAILER-DAEMON
(delivery temporarily suspended: connect to madmonkdev.com[50.116.40.178]:25: Connection refused)
                                         "apache2@no-reply"@madmonkdev.com


ECFD95A7022     8625 Mon Jul  1 14:27:49  MAILER-DAEMON
(delivery temporarily suspended: connect to madmonkdev.com[50.116.40.178]:25: Connection refused)
                                         "apache2@no-reply"@madmonkdev.com


EA8F65A64E0     4167 Mon Jul  1 18:47:27  MAILER-DAEMON
(delivery temporarily suspended: connect to madmonkdev.com[50.116.40.178]:25: Connection refused)
                                         "apache2@no-reply"@madmonkdev.com


E0FCB5A6E65     4151 Mon Jul  1 14:17:51  MAILER-DAEMON
(delivery temporarily suspended: connect to madmonkdev.com[50.116.40.178]:25: Connection refused)
                                         "apache2@no-reply"@madmonkdev.com


E71C95B7D41     8592 Mon Jul  1 22:33:54  MAILER-DAEMON
(delivery temporarily suspended: connect to madmonkdev.com[50.116.40.178]:25: Connection refused)
                                         "apache2@no-reply"@madmonkdev.com


EB38E5A7691     8671 Mon Jul  1 15:10:06  MAILER-DAEMON
(delivery temporarily suspended: connect to madmonkdev.com[50.116.40.178]:25: Connection refused)
                                         "apache2@no-reply"@madmonkdev.com


E22125A7B52     8684 Mon Jul  1 18:47:28  MAILER-DAEMON
(delivery temporarily suspended: connect to madmonkdev.com[50.116.40.178]:25: Connection refused)
                                         "apache2@no-reply"@madmonkdev.com


EC2D05B541A     8609 Mon Jul  1 19:52:41  MAILER-DAEMON
(delivery temporarily suspended: connect to madmonkdev.com[50.116.40.178]:25: Connection refused)
                                         "apache2@no-reply"@madmonkdev.com


EAC785A809C     8692 Mon Jul  1 23:42:41  MAILER-DAEMON
(delivery temporarily suspended: connect to madmonkdev.com[50.116.40.178]:25: Connection refused)
                                         "apache2@no-reply"@madmonkdev.com


E4A4A5B56BF     8567 Mon Jul  1 20:34:27  MAILER-DAEMON
(delivery temporarily suspended: connect to madmonkdev.com[50.116.40.178]:25: Connection refused)
                                         "apache2@no-reply"@madmonkdev.com


EDA0B5B5955     8504 Mon Jul  1 21:24:05  MAILER-DAEMON
(delivery temporarily suspended: connect to madmonkdev.com[50.116.40.178]:25: Connection refused)
                                         "apache2@no-reply"@madmonkdev.com



```


A few things I should tell you guys. I've only been working at this place 3 days, the lead developer quit on a dime just before I got here, and I'm the only person here (entry level front end web dev, 22) who is even remotely qualified to deal with this so the owner gave this to me to fix. I have had -some- experience with Linux, I had Ubuntu on my desktop in a separate partition for awhile and I had academic training in college with linux CLI. 

So I'm not totally unexposed, but please treat me like a novice here so that I don't screw anything up. 


..So how would I go about zeroing in on the spam source and  terminating it? Afterwards... How would I go about hardening our security?

---

### Post by MadMonkMike on 2013-07-02
I should add, I nuked the mail queue and purged almost 60k emails. I checked on it just now after having done that 10 min ago and nothing new was added in..  

I also did the following:

netstat -pant |grep LISTEN

tcp        0      0 0.0.0.0:10081           0.0.0.0:*               LISTEN      2767/lighttpd   
tcp        0      0 0.0.0.0:10082           0.0.0.0:*               LISTEN      2767/lighttpd   
tcp        0      0 127.0.0.1:10083         0.0.0.0:*               LISTEN      2711/apache2    
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      2255/mysqld     
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      2150/vsftpd     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2190/sshd       
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      2446/master     
tcp6       0      0 :::80                   :::*                    LISTEN      2711/apache2    
tcp6       0      0 :::22                   :::*                    LISTEN      2190/sshd       
tcp6       0      0 ::1:25                  :::*                    LISTEN      2446/master 

cat access.log | awk '{print $1}' | sort | uniq -c | sort -n | tail

5 38.106.123.131
      5 98.71.134.179
      6 119.63.193.130
      6 208.58.193.52
      6 74.134.233.131
      7 71.196.107.52
      9 157.55.32.54
      9 76.6.10.248
     11 65.66.254.129
     20 212.58.108.178

---

### Post by Habitual on 2013-07-02
_I suspect_ insecure WP _plugins_.
Are they current versions of WP at least?
any .htaccess files being used in those WP "DocumentRoot" directories?

if yes, any directives such as ...
deny from all
allow from spe.cif.ic.ip
?

Insecure WP plugins combined with improper directory permissions can be an issue.

Please see and read [http://codex.wordpress.org/Hardening_WordPress](http://codex.wordpress.org/Hardening_WordPress)

---

### Post by MadMonkMike on 2013-07-02
You're probably correct is my guess. And no,  these are not 'up to date' versions, many of them at least are not.

Is there any way I can be sure that our server isn't rooted? That is my chief concern.

---

### Post by Habitual on 2013-07-02
you could and should install, update and then run rkhunter.
guide is at [https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter)

---

### Post by SeijiSensei on 2013-07-02
There are two types of situations that can put you in this position.  One is when your server can be turned into an "open relay."  In that situation you should see lots of messages arriving with random From addresses and destination addresses outside the domains you control.  If this server is not designed to accept inbound mail, then I would make sure that whatever mail exchanger you are using, like Postfix or sendmail, is configured to bind only to the localhost address, 127.0.0.1.  Then web applications like WP can still send mail out, but you cannot be turned into an open relay.

Upgrading WP an absolute must.  Anyone with access to the Dashboard for a WP site can update simply by clicking on Update entry in the left-hand Dashboard column then clicking on the Update button.  Just before writing this I checked my blog and noticed I needed to upgrade from 3.5.1 to 3.5.2.  Any site not running 3.5.2 should be updated immediately.

One possibility in your case may be that some of your WP users are letting people create accounts without proper vetting.  If so, that's an open invitation for spammers to exploit your site.  I would explore whether you can require that blog owners moderate requests for accounts.  I've disabled all the contact stuff on my site and do not allow anyone to register.  All the content posted there is mine; that limits the damage outsiders can do.

I would most certainly disable any kind of user-created content on a development site.  If you must allow users to create content which could result in the generation of email, it should only take place on the production site which you can lock down.

In fact you should consider forcing the developers' sites to be located at an entirely different domain name or IP address from the one being used in production.  Don't advertise the name in DNS either.  Force the developers to use IP-based URLs like [http://10.10.10.10/devsite1](http://10.10.10.10/devsite1) and keep the IP private.  Buying another IP from Linode isn't that expensive.

---

