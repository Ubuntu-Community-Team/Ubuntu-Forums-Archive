---
title: "Help with HTTPS: files on ubuntu server"
date: 2010-11-05
forum: Server Platforms
---

### Post by mustava on 2010-11-05
Hello, Sorry if this Q has been placed before but I couldn't find and ref in the searches I did. I have ubuntu server 10.04 running on an old box, and followed the Ubuntu help enabling HTTPS: which seems to have worked ok.
The problem I have now is where do I put the web pages I need to be accessed only from a https url?
I read that it should be dne with a re-direct from a normal http page which is fine, but if I re-direct the "logon" link, where on the server do I place the "logon.php" page?
It's currently sitting at this location: /var/www/members and is linked from the index.php page sitting at /var/www/

Thanks in anticipation
Must!

---

### Post by Ryan Dwyer on 2010-11-05
Look at /etc/apache2/sites-available/default-ssl and see what the DocumentRoot is set to.

---

### Post by mustava on 2010-11-05
Hi Ryan, thanks, the doc/root is set to /var/www
so I suppose that means the pages go there, or I change the doc root in that file for another folder.
How do you stop a normal HTTP: url accessing the files then?
Does each page need something adding to only allow https: access?
This is new to me so please don't expect me to understand expert speak.
thanks
Must!

---

### Post by Ryan Dwyer on 2010-11-05
In PHP:

```

if (!isset($_SERVER['HTTPS'])) {
    header('Location: https://'.$_SERVER['HTTP_HOST'].$_SERVER['REQUEST_URI']);
    die;
}

```

---

### Post by mustava on 2010-11-07
Thanx Ryan,
I tried that, and realise that if you dont specify the https bit, it redirects you to the same page but prefixed by https:

Prob is that none of my pages will load if prefixed with the https bit.

response is "server is taking too long to respond"

Have you any idea why??

Must!

---

### Post by mustava on 2010-11-07
Ok, fixed that issue, it was due to my router not forwarding port 443.

prob is now I get:
SSL received a record that exceeded the maximum permissible length.

(Error code: ssl_error_rx_record_too_long)

Any advice please!!!!

Must.

---

### Post by James78 on 2010-11-08
You don't have a SSL certificate installed. You need to have one configured in Apache. You can either make your own (not recommended), or use a commercial one, or a free one by CaCert (not in all browsers/systems yet, and the only reasonable alternative to a payed one, as a self signed one is not reasonable)

[https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html)
[https://help.ubuntu.com/8.04/serverguide/C/httpd.html#https-configuration](https://help.ubuntu.com/8.04/serverguide/C/httpd.html#https-configuration)

---

### Post by mustava on 2010-11-08
Hi Guys,
Thanks for all the help so far, BUT I now seem to have broken my server, but not sure how.

I have restarted it, reloaded it and re-booted the PC, and although all seems ok, I cannot load any web pages at all.

I can still FTP to it and control it with puppy, but web server'ish looks dead.

When I restart the webserver I get the following msg:
* Restarting web server apache2
'98' Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
unable to open logs

Any help would be gratefully received.

Must!

---

### Post by James78 on 2010-11-09
Is there another instance of Apache running? One reason that it can't bind to a port is because another process (Apache) is already binded and using the port.

---

### Post by mustava on 2010-11-09
Hi mate,
Not sure, how do I find out??
I have re-booted the server several times, with the same result.
How would apache run more than once from boot??

Must

---

### Post by James78 on 2010-11-09
Just check all the processes, e.g. ps -fC apache2
Kill all apache2 processes, e.g. sudo killall apache2, and make sure there are none left over with the ps command above, then start apache2 up again by sudo service apache2 start. If you still get the error, then it's related to something else.

Well, if you rebooted several times, then it's likely another thing. What did you do before this happened? Please check your apache2 error log, it might show something useful. Also, post any configuration files, you might simply just have a configuration error.

---

### Post by mustava on 2010-11-09
Hi James,
Well, as regards what was I doing before it went bellyup, not really sure, but I was trying to follow the advice given in this thread.

As regards getting the logs....... you will have to advise which ones, and where I can find them, I don't know very much about linux yet, but trying my best.

UPDATE:
Ok, I have deleted the server.crt and server.key files, and edited the default-ssl removing the reference to the certificates, restarted apache2 and low and behold all web site is now working again.

All I wanted to do was to secure my logon page using https:, that's where it crashed.

Thanx for all the help, if you have any suggestions please feel free to add them...

Must!

---

### Post by James78 on 2010-11-10
I have an example SSL configuration in this topic. It's not too hard once you figure it out.
[http://ubuntuforums.org/showthread.php?p=10033065#post10033065](http://ubuntuforums.org/showthread.php?p=10033065#post10033065)

P.S. If you want to secure the login page, then it'll submit things encrypted, but if you go back to regular http anywhere else, then the users session and cookies are once again insecure and are easy to steal. In fact, I even know how to steal them. Facebook went wrong in this respect. The only way to keep users sessions and cookies secure is to stay on https.

I believe the default location of the error log is /var/log/apache2/error.log if you want to take a look at it (which would be a very good idea, as error logs hint to problems you may or may not know about, and help you fix the errors; thus always watching the system logs is a good idea.)

---

### Post by mustava on 2010-11-10
James,
Thanks a bunch, the info you have supplied is really appreciated, I'm gonna try to digest it all, then I will look at the error logs.

TVM
Must!

---

