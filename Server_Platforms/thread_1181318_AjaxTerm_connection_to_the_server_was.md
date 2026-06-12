---
title: "AjaxTerm: connection to the server was"
date: 2009-06-07
forum: Server Platforms
---

### Post by mewbie on 2009-06-07
Hello :D I post here as I saw a previous post about AjaxTerm (though different problem).
Sorry if long post; want to be complete. Thank you for your time :D

   [FONT=&quot]I'm running: Linux Debian / apache2-mpm-prefork 2.2.9-10+lenny2 
Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_ssl/2.2.9 OpenSSL/0.9.8g mod_perl/2.0.4 Perl/v5.10.0 Server at ********* Port 80[/FONT]
  
  [FONT=&quot]I just can not get this to work via browser:
"The connection to the server was reset while the page was loading.[/FONT]
  [FONT=&quot]The network link was interrupted while negotiating a connection. Please try again."[/FONT]
  
  [FONT=&quot]Please if you can help or point to a place that can, thank you. Two days trying my best to solve this and just can't figure it out. I followed this [https://help.ubuntu.com/community/AjaxTerm](https://help.ubuntu.com/community/AjaxTerm) plus all sorts of other fixes I have read. I first tried the wget method using readme.txt and that was even more unsuccessful.[/FONT]
  
  _[FONT=&quot]These are the steps I have done:[/FONT]_
  **a2enmod proxy_http**  **[FONT=&quot]apt-get install ajaxterm[/FONT]**
  **[FONT=&quot]/etc/init.d/ajaxterm start[/FONT]**
  [FONT=&quot]It replied: Starting web based terminal: ajaxterm[/FONT]
  **pico /etc/ssh/ssh_config**//uncomment: PasswordAuthentication yes  **[FONT=&quot]cd /[/FONT]**
  **[FONT=&quot]mkdir /srv/ajaxterm[/FONT]**
  **[FONT=&quot]cd /srv/ajaxterm[/FONT]**
  **[FONT=&quot]htpasswd -cm /srv/ajaxterm/.htpasswd MyName[/FONT]**
  **[FONT=&quot]typed in pass…[/FONT]**
  
  **[FONT=&quot]pico /etc/apache2/sites-enabled/ssl[/FONT]**
  [FONT=&quot]This section had this:[/FONT]
  [FONT=&quot]<VirtualHost *:443>[/FONT]
  [FONT=&quot]        ServerAdmin webmaster@localhost[/FONT]
  
  [FONT=&quot]        DocumentRoot /var/www/[/FONT]
  [FONT=&quot]        SSLEngine On[/FONT]
  [FONT=&quot]        SSLCertificateFile /etc/apache2/ssl/apache.pem[/FONT]
  
  [FONT=&quot]        <Directory />[/FONT]
  
  [FONT=&quot]Changed it to:[/FONT]
  **[FONT=&quot]<VirtualHost *:443>[/FONT]**
  **[FONT=&quot]        ServerAdmin webmaster@localhost[/FONT]**
  
  **[FONT=&quot]        DocumentRoot /var/www/[/FONT]**
  **[FONT=&quot]        SSLEngine On[/FONT]**
  **[FONT=&quot]        SSLCertificateFile /etc/apache2/ssl/apache.pem[/FONT]**
  **[FONT=&quot]        SetEnvIf Request_URI "^/u" dontlog[/FONT]**
  **[FONT=&quot]        ErrorLog /var/log/apache2/error.log[/FONT]**
  **[FONT=&quot]        Loglevel warn[/FONT]**
  
  **[FONT=&quot]        ProxyRequests Off[/FONT]**
  **[FONT=&quot]        <Proxy *>[/FONT]**
  **[FONT=&quot]                AuthUserFile /srv/ajaxterm/.htpasswd[/FONT]**
  **[FONT=&quot]                AuthName EnterPassword[/FONT]**
  **[FONT=&quot]                AuthType Basic[/FONT]**
  **[FONT=&quot]                require valid-user[/FONT]**
  
  **[FONT=&quot]                Order Deny,allow[/FONT]**
  **[FONT=&quot]                Allow from all[/FONT]**
  **[FONT=&quot]        </Proxy>[/FONT]**
  **[FONT=&quot]        ProxyPass / [http://localhost:8022/](http://localhost:8022/)[/FONT]**
  **[FONT=&quot]        ProxyPassReverse / [http://localhost:8022/](http://localhost:8022/)[/FONT]**
  
  **[FONT=&quot]        <Directory />[/FONT]**
  
  **[FONT=&quot]/etc/init.d/apache2 reload [/FONT]**
  **[FONT=&quot]loaded fine…[/FONT]**
  **[FONT=&quot]/etc/init.d/ajaxterm start[/FONT]**
  
  I try going to: [https://mysite.com:8022](https://mysite.com:8022) and get error: The connection to the server was reset while the page was loading.  
  [FONT=&quot]I do this: **netstat -antp**[/FONT]
  [FONT=&quot]I think this is the ajaxterm that on the list**: **[/FONT]
  **[FONT=&quot]tcp        0      0 127.0.0.1:8022          0.0.0.0:*               LISTEN      25926/python  [/FONT]**
  
  [FONT=&quot]When I do cmd**: ps x **, I don't see it on the list of processes running, but I see many of these nmbd things that I don't think I saw before:[/FONT]
  
  **[FONT=&quot]13587 ?        Ss     0:07 /usr/sbin/nmbd -D[/FONT]**
  **[FONT=&quot]13589 ?        Ss     0:08 /usr/sbin/smbd -D[/FONT]**
  **[FONT=&quot]13590 ?        S      0:00 /usr/sbin/smbd -D[/FONT]**
  **[FONT=&quot] 5333 ?        S      0:00 [pdflush][/FONT]**
  **[FONT=&quot]14779 ?        S      0:00 /usr/sbin/smbd -D[/FONT]**
  **[FONT=&quot]25819 ?        S      0:00 /usr/sbin/smbd -D[/FONT]**
  **[FONT=&quot]26146 ?        S      0:00 /usr/sbin/smbd -D[/FONT]**
  **[FONT=&quot]26344 ?        S      0:00 /usr/sbin/smbd -D[/FONT]**
  
  [FONT=&quot]When I issue the cmd: [/FONT]
  **[FONT=&quot]ajaxterm[/FONT]**
  [FONT=&quot]Reply I get is: [/FONT]
  **[FONT=&quot]AjaxTerm at [http://localhost:8022/](http://localhost:8022/)[/FONT]**
  **[FONT=&quot]Traceback (most recent call last):[/FONT]**
  **[FONT=&quot]  File "/usr/share/ajaxterm/ajaxterm.py", line 571, in <module>[/FONT]**
  **[FONT=&quot]    main()[/FONT]**
  **[FONT=&quot]  File "/usr/share/ajaxterm/ajaxterm.py", line 565, in main[/FONT]**
  **[FONT=&quot]    qweb.QWebWSGIServer(at,ip='localhost',port=int(o.port),threaded=0,log=o.log).serve_forever()[/FONT]**
  **[FONT=&quot]  File "/usr/share/ajaxterm/qweb.py", line 1309, in __init__[/FONT]**
  **[FONT=&quot]    BaseHTTPServer.HTTPServer.__init__(self, (ip, port), QWebWSGIHandler)[/FONT]**
  **[FONT=&quot]  File "/usr/lib/python2.5/SocketServer.py", line 330, in __init__[/FONT]**
  **[FONT=&quot]    self.server_bind()[/FONT]**
  **[FONT=&quot]  File "/usr/lib/python2.5/BaseHTTPServer.py", line 101, in server_bind[/FONT]**
  **[FONT=&quot]    SocketServer.TCPServer.server_bind(self)[/FONT]**
  **[FONT=&quot]  File "/usr/lib/python2.5/SocketServer.py", line 341, in server_bind[/FONT]**
  **[FONT=&quot]    self.socket.bind(self.server_address)[/FONT]**
  **[FONT=&quot]  File "<string>", line 1, in bind[/FONT]**
  **[FONT=&quot]socket.error: (98, 'Address already in use')[/FONT]**
  
  [FONT=&quot]And then I'm just left in this blank window… that I don't know how to quit.[/FONT]
  [FONT=&quot]----------[/FONT]
  [FONT=&quot]I read to do this: **wget -O- -np  [https://localhost:8022](https://localhost:8022)**[/FONT]
  [FONT=&quot]The reply I got was:[/FONT]
  **[FONT=&quot]--2009-06-07 [/FONT]****[FONT=&quot]18:34:03[/FONT]****[FONT=&quot]--  [https://localhost:8022/](https://localhost:8022/)[/FONT]**
  **[FONT=&quot]Resolving localhost... 127.0.0.1[/FONT]**
  **[FONT=&quot]Connecting to localhost|127.0.0.1|:8022... connected.[/FONT]**
  **[FONT=&quot]OpenSSL: error:140770FC:SSL routines:SSL23_GET_SERVER_HELLO:unknown protocol[/FONT]**
  **[FONT=&quot]Unable to establish SSL connection.[/FONT]**
  
  
  I see in my /var/log/apache2/error.log  [FONT=&quot][Sun Jun 07 [/FONT][FONT=&quot]18:16:44[/FONT][FONT=&quot] 2009] [notice] mod_python: Creating 8 session mutexes based on 50 max processes and 0 max threads.[/FONT]
  [FONT=&quot][Sun Jun 07 [/FONT][FONT=&quot]18:16:44[/FONT][FONT=&quot] 2009] [notice] mod_python: using mutex_directory /tmp [/FONT]
  [FONT=&quot][Sun Jun 07 [/FONT][FONT=&quot]18:16:45[/FONT][FONT=&quot] 2009] [notice] Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_ssl/2.2.9 OpenSSL/0.9.8g mod_perl/2.0.4 Perl/v5.10.0 configured -- resuming normal operations[/FONT]

---

### Post by mewbie on 2009-06-07
Even more strange I just noticed!: 
1.) That when I go to any URL on my site it brings me to the AjaxTerm login page! It seems the entire site has been redirected to the AjaxTerm.
2.) Furthermore I only got that to load when after several attempts of trying my normal name/pass for the site didn't work I thought to try the pass I set for AjaxTerm in steps above.. that worked!
   3.) And when I do try to login to the AjaxTerm window I type in name, hit enter, it returns back to Login. Never ask for pass.. as if login name isn't correct..
   4.) when I do: netstat -antp Instead of just one listing on port 8022 there are now many:
  tcp        0      0 127.0.0.1:8022          0.0.0.0:*               LISTEN      25926/python    
  tcp        0      0 127.0.0.1:8022          127.0.0.1:4991          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:8022          127.0.0.1:4990          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:8022          127.0.0.1:4989          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:8022          127.0.0.1:4988          TIME_WAIT   -                  
  tcp        0      0 127.0.0.1:8022          127.0.0.1:4987          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:4992          127.0.0.1:8022          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:8022          127.0.0.1:1032          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:8022          127.0.0.1:1031          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:8022          127.0.0.1:1030          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:8022          127.0.0.1:4998          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:8022          127.0.0.1:1029          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:8022          127.0.0.1:4997          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:8022          127.0.0.1:1028          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:8022          127.0.0.1:4996          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:8022          127.0.0.1:1027          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:8022          127.0.0.1:4995          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:8022          127.0.0.1:1026          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:8022          127.0.0.1:4994          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:8022          127.0.0.1:1025          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:8022          127.0.0.1:4993          TIME_WAIT   -               
  tcp        0      0 127.0.0.1:8022          127.0.0.1:1024          TIME_WAIT   -  
   
  And a many with server ip on port 443
  
   5.) I do this: /etc/init.d/ajaxterm stop
  It replied: Stopping web based terminal: ajaxterm.
& then:   /etc/init.d/apache2 reload   
  Entire site is still redirected to the AjaxTerm page
Though I still have error when I try to go [https://mysite.com:8022]("https://mysite.com:8022/")

I've commented the new entries on pico /etc/apache2/sites-enabled/ssl
and site is working again. (still a ton of strange entries under netstat -antp)
  
  
So now question is not only to get that to work but to get it stop redirecting entire site to it.

Thank you!

---

