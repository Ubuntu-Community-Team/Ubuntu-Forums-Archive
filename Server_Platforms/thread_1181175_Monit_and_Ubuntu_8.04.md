---
title: "Monit and Ubuntu 8.04"
date: 2009-06-07
forum: Server Platforms
---

### Post by wattaman on 2009-06-07
So, I'd like to know what I must enter in the monit's config. file (etc/monit/monitrc) so it will restart closed processed. I have a lot of problems with mysql stopping (again) and monit looks like a nice tool to start particular processes; unfortunatelly, they Udon't have an easy documentation or an example of config file for Ubuntu.
For example, they say this:>  check process apache with pidfile /var/run/httpd.pid
       start "/etc/init.d/httpd start"
       stop  "/etc/init.d/httpd stop"
       if failed host 127.0.0.1 port 80
          protocol apache-status loglimit > 60% 
       then restart
 should start the apache if is not running, but I don't have the /var/run/httpd.pid file no matter if apache is running or not... must be somewhere else, probably.

An example of monit config file for Ubuntu 8.04 would be much apreciated. I must say I have mysql v.5 and apache 2 I want to monitor.
Thank you!

---

### Post by LepeKaname on 2009-06-07
It is not /var/run/httpd.pid it is: /var/run/apache2.pid

Use this:
```
  check process apache2 with pidfile /var/run/apache2.pid
    start program = "/etc/init.d/apache2 start"
    stop program  = "/etc/init.d/apache2 stop"
#    if cpu > 60% for 2 cycles then alert
     if cpu > 90% for 5 cycles then restart
#    if totalmem > 200.0 MB for 5 cycles then restart
#    if children > 250 then restart
#    if loadavg(5min) greater than 10 for 8 cycles then stop
    if failed host localhost port 80 protocol http
#       and request "/monit/token"
       then restart
#    if failed port 443 type tcpssl protocol http
#       with timeout 15 seconds
#       then restart
    if 3 restarts within 5 cycles then timeout
```


For mysql:
```

check process mysql with pidfile /var/run/mysqld/mysqld.pid
   group mysql
   start program = "/etc/init.d/mysql start"
   stop program = "/etc/init.d/mysql stop"
   if failed host 192.168.0.1 port 3306 then restart
   if 5 restarts within 5 cycles then timeout
```

Use 192.168.0.1 if your mysql is listening to that IP, if not, you can use localhost or 127.0.0.1

---

### Post by wattaman on 2009-06-08
Thank you! I've made the changes.
One more thing, though: Is there a weay to see if monit is running, from within Webmin? I don't have internet at home yet and I'm using a public wireless point with the ssh port blocked and in Webmin>System>Running Processes I don't see it.

---

### Post by LepeKaname on 2009-06-08
Depending on your monit settings:

```
set httpd port 2812 and
     use address yourhost.com  # only accept connection from localhost
     allow  monitadmin:(mypassword)
```

You can "nmap" your host and see if port 2812 is there. Also check your firewall settings. 

If you set your mail settings (inside monit config file) correctly, then you will receive an email specifying that monit is running.

---

### Post by wattaman on 2009-06-09
I don't know how to configure the mail settings. I only entered my email at *set alert*; dunno what I must enter at *set mailserver*.
I've tried the name of the server, the IP and names of domains hosted there,but didn't work... so I haven't received any email from the monit script yet :)

---

### Post by LepeKaname on 2009-06-09
If your mailserver is in the same server, usually specifying your mail server like this, will work:

```
set mailserver mail.myserver.com
```

For a more detailed setup (user/password/etc), look at here:

[http://mmonit.com/monit/documentation/monit.html#setting_a_mail_server_for_alert_messages](http://mmonit.com/monit/documentation/monit.html#setting_a_mail_server_for_alert_messages)

For example:

```
 set mailserver mail.tildeslash.com, mail.foo.bar port 10025
     username "Rabbi" password "Loewe" using tlsv1, localhost
     with timeout 15 seconds
```

---

### Post by wattaman on 2009-06-10
I'm trying to use gmail and I have:
> set mailserver smtp.gmail.com port 465
     username "gmail-username" password "gmail-password" using sslv3, localhost
     with timeout 15 seconds
- Is it right? cause I haven't received any email yet

---

### Post by LepeKaname on 2009-06-10
Check your spam folder... nothing?

It seems fine to me. 

Don't forget to specify the email account, and to restart monit.

```
set alert user@gmail.com
```

---

### Post by wattaman on 2009-07-03
It doesn't send anything. I keep trying the *monit -t* command in putty but all I get is
> 
/etc/monit/monitrc:35: Error: hostname did not resolve 'username'
/etc/monit/monitrc:35: Error: hostname did not resolve 'mail@gmail.com'
/etc/monit/monitrc:35: Error: hostname did not resolve 'password'
/etc/monit/monitrc:36: Error: syntax error 'tlsv1'


Now the mailserver looks like this:
> set mailserver smtp.gmail.com port 465
    username "mail@gmail.com" password "pass"
    using tlsv1
    with timeout 20 seconds

---

### Post by thibs on 2009-07-23
The problem is that the monit package on Ubuntu 8.04 is in version 4.8.1 and the "username" and "password" options are not supported in this version (requires at least monit 4.10.1). I have rebuild a package of monit 4.10 (available on jaunty) for Ubuntu 8.04 to be able to benefit from these features on my server. I'll make this package available on my blog as soon as I have some time... I'll keep you posted!

---

### Post by wattaman on 2009-07-24
Thanks for clarifying this issue.
I'll keep watching this thread for the solution you have. Or, write the address of your blog so I'll look directly there.
Thanks!

---

