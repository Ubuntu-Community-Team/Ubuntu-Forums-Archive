---
title: "Apache2 empty response in Ubuntu 12.04"
date: 2012-07-03
forum: Server Platforms
---

### Post by Killer Jacker on 2012-07-03
like title says, when i tried to connect to my configured domain, there's no content in response. For example, in Chromium the message says "Error 324 (net::ERR_EMPTY_RESPONSE)". Apache 2.2.22 is running with PHP 5.3.10 with Suhosin configured. The most rare thing is that in beginning, when mount the server and all services, all was working perfectly. 2 weeks later, begin problems. In logs all seems normal but some records like these:

```
91.200.156.95 - - [19/Jun/2012:13:09:03 -0400] "C\x863\xbf\xf4)\x91A\xce\xe8;S\x92X\xa0Ncz~\x88%$.\xaa\xe7\xc8\x01\x93\xe6\xd0\xaeW\x8fM" 501 321 "-" "-"

200.29.174.98 - - [19/Jun/2012:15:29:36 -0400] "\x9d!\x88d3\xfe\xd76p\xec\x18\x85\xc9\x0f\xeex\xec\x86\x11\xf3o94" 501 310 "-" "-"

27.255.64.36 - - [20/Jun/2012:13:17:58 -0400] "GET /user/soapCaller.bs HTTP/1.1" 404 471 "-" "Morfeus ******* Scanner"
```

i know that these are some kind of bot scanning for vulnerabilities, but for now, i need the site to show when i invoke the domain!! :(

i tried for a week in forums and Google, but can't find anything.

i'll be very grateful for your help

---

### Post by SeijiSensei on 2012-07-03
First question.  Can you see a simple HTML page on the server, but not use PHP applications?  Have you looked at the logs in /var/log/apache2 to see what the problem might be?  When a PHP script returns a completely blank page, it usually means there was a significant error at the beginning of the script which causes it to halt without an output.  PHP errors are logged to /var/log/apache2/error.log.

---

### Post by Killer Jacker on 2012-07-03
> **SeijiSensei said:**
> First question.  Can you see a simple HTML page on the server, but not use PHP applications?  Have you looked at the logs in /var/log/apache2 to see what the problem might be?  When a PHP script returns a completely blank page, it usually means there was a significant error at the beginning of the script which causes it to halt without an output.  PHP errors are logged to /var/log/apache2/error.log.

Hi SeijiSensei. First of all, thanks for your help. :)

Well, about your question, in fact i have PHP installed an running, but the page that i tried to open is an HTML simple page (a temporal page with only a image). I don't know if it's important but the page has headers for HTML5.

I was seeing the logs in /var/log/apache2. in fact, the lines that i've posted are from access.log. The error.log don't have any strange record... only the startings and stop of server.

---

### Post by SeijiSensei on 2012-07-03
Yes, but those lines are just random attacks against the server.  I was talking about log entries that correspond to your attempts to view the page that comes up blank.  Those 404 and 501 status codes indicate the attacker didn't get very far.

So, if you try to open a page with a browser, what do you see in access.log?

---

### Post by Killer Jacker on 2012-07-04
> **SeijiSensei said:**
> First question.  Can you see a simple HTML page on the server, but not use PHP applications?  Have you looked at the logs in /var/log/apache2 to see what the problem might be?  When a PHP script returns a completely blank page, it usually means there was a significant error at the beginning of the script which causes it to halt without an output.  PHP errors are logged to /var/log/apache2/error.log.

It's rare... today, there no records on access.log or access.log.1 of my connection attemps...
i tried to connect several times, but these don't appear in logs...
no errors in error.log or error.log.1
i'm very confused... :confused:
mainly because in past days logs was correctly saved in the files...
well... this are some old log records:
```

192.168.0.117 - - [27/Jun/2012:19:06:52 -0400] "GET /jqueryui.png HTTP/1.1" 200 3722 "http://192.168.0.111/" "Mozilla/5.0 (Linux; U; Android 2.3.4; es-cl; LG-P999 Build/GRJ22) AppleWebKit/533.1 (KHTML, like Gecko) Version/4.0 Mobile Safari/533.1 MMS/LG-Android-MMS-V1.0/1.2"
192.168.0.117 - - [27/Jun/2012:19:06:51 -0400] "GET /logo.png HTTP/1.1" 200 46696 "http://192.168.0.111/" "Mozilla/5.0 (Linux; U; Android 2.3.4; es-cl; LG-P999 Build/GRJ22) AppleWebKit/533.1 (KHTML, like Gecko) Version/4.0 Mobile Safari/533.1 MMS/LG-Android-MMS-V1.0/1.2"
192.168.0.117 - - [27/Jun/2012:19:06:53 -0400] "GET /favicon.ico HTTP/1.1" 404 447 "http://192.168.0.111/" "Mozilla/5.0 (Linux; U; Android 2.3.4; es-cl; LG-P999 Build/GRJ22) AppleWebKit/533.1 (KHTML, like Gecko) Version/4.0 Mobile Safari/533.1 MMS/LG-Android-MMS-V1.0/1.2"
127.0.0.1 - - [27/Jun/2012:19:07:01 -0400] "OPTIONS * HTTP/1.0" 200 126 "-" "Apache/2.2.22 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [27/Jun/2012:19:07:02 -0400] "OPTIONS * HTTP/1.0" 200 126 "-" "Apache/2.2.22 (Ubuntu) (internal dummy connection)"
190.8.120.139 - - [28/Jun/2012:11:55:50 -0400] "GET / HTTP/1.1" 200 941 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/536.5 (KHTML, like Gecko) Chrome/19.0.1084.56 Safari/536.5"
190.8.120.139 - - [28/Jun/2012:11:55:50 -0400] "GET /logo.png HTTP/1.1" 200 46751 "http://190.8.120.139/" "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/536.5 (KHTML, like Gecko) Chrome/19.0.1084.56 Safari/536.5"
190.8.120.139 - - [28/Jun/2012:11:55:50 -0400] "GET /jqueryui.png HTTP/1.1" 200 3778 "http://190.8.120.139/" "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/536.5 (KHTML, like Gecko) Chrome/19.0.1084.56 Safari/536.5"
190.8.120.139 - - [28/Jun/2012:11:55:50 -0400] "GET /valid-html5.png HTTP/1.1" 200 3374 "http://190.8.120.139/" "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/536.5 (KHTML, like Gecko) Chrome/19.0.1084.56 Safari/536.5"
190.8.120.139 - - [28/Jun/2012:11:55:50 -0400] "GET /html5.png HTTP/1.1" 200 2057 "http://190.8.120.139/" "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/536.5 (KHTML, like Gecko) Chrome/19.0.1084.56 Safari/536.5"
190.8.120.139 - - [28/Jun/2012:11:55:50 -0400] "GET /jquery.png HTTP/1.1" 200 3938 "http://190.8.120.139/" "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/536.5 (KHTML, like Gecko) Chrome/19.0.1084.56 Safari/536.5"
190.8.120.139 - - [28/Jun/2012:11:55:50 -0400] "GET /favicon.ico HTTP/1.1" 404 503 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/536.5 (KHTML, like Gecko) Chrome/19.0.1084.56 Safari/536.5"

```

thanks.

---

### Post by Killer Jacker on 2012-07-04
here are some screenshots of response in Chromium and Firefox and their Development tools analysis...

---

### Post by SeijiSensei on 2012-07-04
I take it you have one or more custom virtual host definitions in /sites-available/?  What if you delete the links to them in /sites-enabled/ and just leave the default link in place?  After restarting Apache, you should get the Ubuntu default "It Works!" page.

Another diagnostic is to connect to the server using telnet like this:
```

$ [color=blue]telnet yourserver 80[/color]
Trying [server ip address]...
Connected to yourserver.
Escape character is '^]'.
[color=blue]GET / HTTP/1.0
[enter][/color]

```

Material you type is in blue.  You need to hit enter twice after the GET request.  If you want to try this with virtual hosts use the following:

```
[color=blue]GET / HTTP/1.1
Host: name_of_virtualhost
[enter][/color]

```

---

### Post by Killer Jacker on 2012-07-06
Hello again SeijiSensei, very very thanks for your time and attention. Sorry for delay in the answer, but was have a busy and difficult day.

Well, in fact, the site that i have in the server it's only a temporal site, then i was not dedicate so much time in configuration. With a little bit of shame, tell to you that i was not edit the default available site; was only change the files in /var/www. In other words, the default cfg file was not edited. :lolflag:
This is the content of default:
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

relatively of diagnostics with telnet, can connect but passed some few seconds it desconnect me and says "Connection closed by foreign host."...

---

### Post by SeijiSensei on 2012-07-06
> **Killer Jacker said:**
> relatively of diagnostics with telnet, can connect but passed some few seconds it desconnect me and says "Connection closed by foreign host."...

If you don't see the HTML code of the page flash by, you're not connecting. 

This sounds more like a network problem than anything else.  What happens if you open a browser on the server itself and navigate to [noparse]http://localhost/[/noparse].  Do you see the page you expect?

---

### Post by Killer Jacker on 2012-07-07
> **SeijiSensei said:**
> If you don't see the HTML code of the page flash by, you're not connecting. 

This sounds more like a network problem than anything else.  What happens if you open a browser on the server itself and navigate to [noparse]http://localhost/[/noparse].  Do you see the page you expect?

Yes. From localhost and others local network machines the site open with no problem.

---

### Post by SeijiSensei on 2012-07-07
> **Killer Jacker said:**
> Yes. From localhost and others local network machines the site open with no problem.

If those other local machines share the same subnet addresses as you (i.e., they all fall into the same range like 192.168.1.1-254), then the problem pretty clearly is on your local machine.  What, if anything, differentiates your machine from the others that can connect?  If you can answer that problem, you've probably found the solution.

---

### Post by Killer Jacker on 2012-07-08
> **SeijiSensei said:**
> If those other local machines share the same subnet addresses as you (i.e., they all fall into the same range like 192.168.1.1-254), then the problem pretty clearly is on your local machine.  What, if anything, differentiates your machine from the others that can connect?  If you can answer that problem, you've probably found the solution.

The problem occurs when i try to connect from Internet, in other words, when i try to connect from a machine that is physically in other place than the server.
When setting up the server, was working with no problem, but passed 1 week, and show no more the website.

---

### Post by hardkxre on 2012-07-09
I follow this thread with great anticipation. I have the exact same issue but, alas, nothing to contribute. Please post, if you fix this. I will do the same.

---

### Post by SeijiSensei on 2012-07-09
To access the server from the Internet, are you forwarding port 80 through a router back to the server?  Are you sure the forwarding is correct?  Name service for the web site points to the router?  The router still has the same IP address as it did before?

---

### Post by hardkxre on 2012-07-09
Sorry, Killer Jacker, for interrupting your thread.
In my case, port 80 is correctly forwarded. Hypothetically, if it weren't it wouldn't serve a blank web page, would it? It would give some error message, right?

---

### Post by Killer Jacker on 2012-07-10
> **hardkxre said:**
> Sorry, Killer Jacker, for interrupting your thread.
In my case, port 80 is correctly forwarded. Hypothetically, if it weren't it wouldn't serve a blank web page, would it? It would give some error message, right?

Don't worry man. Any contribution is good received. 

Anyway, +1 to the post of hardkxre.

I'm forwarding port 80 through the router and IP is the same that when all was ok. I can connect using ssh.

This problem is really a headache. :(

---

### Post by Killer Jacker on 2012-07-26
Finally fixed... without any intervention o_O

would be a problem with DNS... i don't know

---

### Post by hardkxre on 2012-08-28
I still have the same issue :(
Did you ever realise what was wrong?

---

