---
title: "Apache from localhost can't reach internet"
date: 2011-07-11
forum: Server Platforms
---

### Post by oysteigr on 2011-07-11
I've installed apache2 on ubuntu 10.04 and everything works fine, but when I use functions that needs to connect to internet, it doesn't work. Is there a simple setup I've forgot? I've been searching and looking for a solution, but I'm stuck! If someone knows anything, please tell me!

Thank you in advance! :)

---

### Post by Lars Noodén on 2011-07-11
We'll need a little more detail.  Describe a little more what you are trying that does not work.

---

### Post by spynappels on 2011-07-11
Can you ping [www.google.com?](www.google.com?)
Can you ping 8.8.8.8?
What does ifconfig eth0 give?

(all from the commandline of your server)

---

### Post by oysteigr on 2011-07-11
You see, I'm, as an example, connecting facebook together with wordpress. I now have to upload to my webserver each time I want to check if it works. If I don't use any functions that needs interaction with the rest of the internet, everything works fine on localhost! Do you understand my problem now?

---

### Post by spynappels on 2011-07-11
I'm still not sure what you are trying to do exactly, but if you can do what I suggested, it can at least rule out a networking issue....

---

### Post by oysteigr on 2011-07-11
the ping and ifconfig are fine and looks just like it should. I'm sorry for not making myself clear! I'll try again;

I'm working on my computer where I put up apache2 so I can run my php-pages locally. That works just fine as long as my pages is independent and no need of the internet. But now I need to connect through facebook connector and here's when things stop working. If I upload my webpages to my webserver everything works fine! So are there some settings on my computer that blocks apache2 from connecting to internet? There is no problems with my network-connection :p

---

### Post by karlson on 2011-07-11
> **oysteigr said:**
> the ping and ifconfig are fine and looks just like it should. I'm sorry for not making myself clear! I'll try again;

I'm working on my computer where I put up apache2 so I can run my php-pages locally. That works just fine as long as my pages is independent and no need of the internet. But now I need to connect through facebook connector and here's when things stop working. If I upload my webpages to my webserver everything works fine! So are there some settings on my computer that blocks apache2 from connecting to internet? There is no problems with my network-connection :p

You are still not making yourself clear and not providing enough information to help.

1.  Can you get out to the internet using a web browser?
2.  Can you get out to the internet using telnet (telnet [www.facebook.com](www.facebook.com) 80)?
3.  Have you looked at what apache reports in the logs?
4.  Are you running a firewall on this machine?

---

### Post by spynappels on 2011-07-11
Are you trying to get content from Facebook onto your site, or trying to get content from your site on to Facebook?

I suspect the former, in which case you need to look at write permissions for Wordpress etc. I'm afraid I can't help with that, I have no clue about Wordpress and don't use Facebook and have never needed to connect the two.

Networking is fine though.

---

### Post by oysteigr on 2011-07-11
> **karlson said:**
> You are still not making yourself clear and not providing enough information to help.

1.  Can you get out to the internet using a web browser?
2.  Can you get out to the internet using telnet (telnet [www.facebook.com]("http://www.facebook.com") 80)?
3.  Have you looked at what apache reports in the logs?
4.  Are you running a firewall on this machine?


1, 2. It's the same computer i'm writing on now. I can get out to facebook and all other pages without problems.

3. This is what I found in the errorlog:
[Mon Jul 11 10:44:46 2011] [error] [client 127.0.0.1] PHP Warning:   fopen([http://api.facebook.com/restserver.php?method=facebook.admin.getAppProperties&session_key=&api_key=xxxxxxxxxx&v=1.0):](http://api.facebook.com/restserver.php?method=facebook.admin.getAppProperties&session_key=&api_key=xxxxxxxxxx&v=1.0):)  failed to open stream: HTTP request failed!  in  /home/xxxx/facebook-platform/facebookapi_php5_restlib.php on line 3391,  referer: [http://localhost/wp_test/wp-admin/profile.php](http://localhost/wp_test/wp-admin/profile.php)

4. I'm not running any firewall as I know of. 

> **spynappels said:**
> Are you trying to get content from Facebook  onto your site, or trying to get content from your site on to Facebook?

I suspect the former, in which case you need to look at write  permissions for Wordpress etc. I'm afraid I can't help with that, I have  no clue about Wordpress and don't use Facebook and have never needed to  connect the two.

Networking is fine though.

I'm trying to get content from facebook, and I manage it with the same code on a server when I upload it, but I can't run it locally from localhost with a browser. I don't think it has anything to do with WP. It runs just fine with WP when I don't try to reach the FB-content.

---

### Post by karlson on 2011-07-11
> **oysteigr said:**
> 
3. This is what I found in the errorlog:
[Mon Jul 11 10:44:46 2011] [error] [client 127.0.0.1] PHP Warning:   fopen([http://api.facebook.com/restserver.php?method=facebook.admin.getAppProperties&session_key=&api_key=xxxxxxxxxx&v=1.0):](http://api.facebook.com/restserver.php?method=facebook.admin.getAppProperties&session_key=&api_key=xxxxxxxxxx&v=1.0):)  failed to open stream: HTTP request failed!  in  /home/xxxx/facebook-platform/facebookapi_php5_restlib.php on line 3391,  referer: [http://localhost/wp_test/wp-admin/profile.php](http://localhost/wp_test/wp-admin/profile.php)


Have you tried opening the URL in the browser directly?
Have you tried going to the same server from another machine on the network?

---

### Post by oysteigr on 2011-07-11
> **karlson said:**
> Have you tried opening the URL in the browser directly?

Yeah, and that works fine.

> **karlson said:**
> Have you tried going to the same server from another machine on the network?

Jup! And it's just the same. Is there some settings anywhere that 'localhost' are not allowed to access the network, or something like that?

---

### Post by smurphy_it on 2011-07-11
```
This is what I found in the errorlog:
[Mon Jul 11 10:44:46 2011] [error] [client 127.0.0.1] PHP Warning: fopen(http://api.facebook.com/restserver.p...xxxxxx&v=1.0): failed to open stream: HTTP request failed! in /home/xxxx/facebook-platform/facebookapi_php5_restlib.php on line 3391, referer: http://localhost/wp_test/wp-admin/profile.php
```

I'd suggest looking at your profile.  I would suspect that profile doesn't have the permissions for what you are attempting to do.

---

