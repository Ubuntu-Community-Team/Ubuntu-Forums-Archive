---
title: "wanna be attacked !"
date: 2009-03-18
forum: Server Platforms
---

### Post by fabianus on 2009-03-18
Hello all !

I just finished to setup my first ubuntu server. It runs a magento webstore. I use apache, php5, openssh and the ufw firewall. Now I would like to check if the server is secure as I tuned it. Do you know any tool or website the provides a check ? Meaning that it tries to attack my server and tells me where I have security holes. 

Thanks a lot for any suggestion !


Regards, 
Fabianus

---

### Post by khelben1979 on 2009-03-18
I found [this]("http://reviews.cnet.com/Labs/4520-6603_7-6227252-1.html") from CNet.

---

### Post by Johnsie on 2009-03-18
shieldsup is a good website for checking your ports

---

### Post by uberlinux on 2009-03-18
I'd like to take a second to point out that ISPs monitor for some of the more egregious scan/attack patterns and may pull the plug on the 'attacker' if they see it.  Permission or no.

---

### Post by fabianus on 2009-03-18
Thank you Johnsie, 

that site is a good start. 

Regards, 
Fabianus

---

### Post by MrWES on 2009-03-18
+1 on Shields Up

[http://www.grc.com/intro.htm]("http://www.grc.com/intro.htm")

Follow the link to Shields Up under the 'Services' menu tab.

---

### Post by fabianus on 2009-03-19
MrWES, yes, that's the site Johnsie proposed ... or did I miss something?

---

### Post by windependence on 2009-03-19
This site will give you a good start in understanding what is available:

[http://insecure.org/](http://insecure.org/)

Also here:

[http://sectools.org/vuln-scanners.html](http://sectools.org/vuln-scanners.html)

There are tools that the credit card companies use to verify your site IF you are storing CC information, which most sites don't do.

-Tim

---

### Post by Johnsie on 2009-03-19
Personally if I was going to exploit someones site  I would look for holes in any php code used by the webmaster. The reason being that the webmaster usually doesn't have the same technical/security skills as the team of people who develop the webserver software.

If the site allows uploads, which type of file can it upload? Is there any way I can trick it into letting me upload a php script? Using file permissions is a good way to stop an uploaded script from being able to delete files or cause any serious damage. Restricting which folders scripts can be run from is good too. Ban scripts from being able to be run from the upload folder.

If it's listing a folder, is there any way I can make it list a different folder? Like by putting a ../../ in the url somewhere? If so then someone might get something they weren't mean to see.

How does the website interact with the database? Is it open to SQL Injection ? (certainly something worth googling)

Does the server output the name and version of  the webserver or any other software when there is an error message? If so then a potential attacker could look for vulnerabilties in that specific piece of software. 

Try to avoid putting password files in folders that are visible in your web browser.

Another way people have exploited sites in the past is by tricking the domain hosts into sending them the passwords instead of he genuine owner. Unfortunately there's not much you can do about that until it happens. It doesn't happen to most people.


I've had to learn my of these things through experience because I run a gaming site that was targeted by trolls. So far they haven't managed to do any damage but they attacked another guys site and defaced it. They've tried to exploit anything that can posted to on at my site, so I've minimised the interactive features until I implement a secure username/password based system. Spammers will also target every posting thing that they can find and even sign up as members to sites using their bots, so I recommend using re-captcha as a way of preventing that. Captchas suck for the user but they really do help prevent spam.

---

### Post by fabianus on 2009-03-19
Hi Johnsie, 

thanks a lot for this valuable recap !

Regards, 
Fabianus

---

### Post by fabianus on 2009-03-20
I tried [www.alertsite.com](www.alertsite.com), which gives the possibility to test it for 30 days. Here is a report result : 


Synopsis :

It is possible to obtain information about the remote host. 

Description :

The remote service understands the Bonjour (also known as ZeroConf or
mDNS) protocol, which allows anyone to uncover information from the
remote host such as its operating system type and exact version, its
hostname, and the list of services it is running. 

Solution :

Filter incoming traffic to UDP port 5353 if desired. 

Risk factor :

Medium / CVSS Base Score : 5.0
(CVSS2#AV:N/AC:L/Au:N/C:P/I:N/A:N)

Plugin output :

Nessus was able to extract the following information :

  - Computer name    : fabianus-desktop.local.
  - Ethernet addr    : 00:12:3f:b4:0a:0e
  - Computer Type    : I686
  - Operating System : LINUX





Do you have any idea how I could solve this problem ?

A second problem was shown : 




Debugging functions are enabled on the remote web server. 

Description :

The remote webserver supports the TRACE and/or TRACK methods.  TRACE
and TRACK are HTTP methods which are used to debug web server
connections. 

In addition, it has been shown that servers supporting the TRACE
method are subject to cross-site scripting attacks, dubbed XST for
'Cross-Site Tracing', when used in conjunction with various weaknesses
in browsers.  An attacker may use this flaw to trick your legitimate
web users to give him their credentials. 

See also :

[http://www.cgisecurity.com/whitehat-mirror/WH-WhitePaper_XST_ebook.pdf](http://www.cgisecurity.com/whitehat-mirror/WH-WhitePaper_XST_ebook.pdf)
[http://www.apacheweek.com/issues/03-01-24](http://www.apacheweek.com/issues/03-01-24)
[http://www.kb.cert.org/vuls/id/867593](http://www.kb.cert.org/vuls/id/867593)

Solution :

Disable these methods.

Risk factor :

Medium / CVSS Base Score : 5.0
(CVSS2#AV:N/AC:L/Au:N/C:P/I:N/A:N)
Solution : 

Add the following lines for each virtual host in your configuration file :

    RewriteEngine on
    RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
    RewriteRule .* - [F]

Alternatively, note that Apache versions 1.3.34, 2.0.55, and 2.2
support disabling the TRACE method natively via the 'TraceEnable'
directive.

Plugin output :

Nessus sent the following TRACE request : 

------------------------------ snip ------------------------------
TRACE /Nessus1511477366.html HTTP/1.1
Connection: Close
Host: store.fabianus.com
Pragma: no-cache
User-Agent: Mozilla/4.0 (compatible
 MSIE 6.0
 Windows NT 5.0)
Accept: image/gif, image/x-xbitmap, image/jpeg, image/pjpeg, image/png, */*
Accept-Language: en
Accept-Charset: iso-8859-1,*,utf-8

------------------------------ snip ------------------------------

and received the following response from the remote server :

------------------------------ snip ------------------------------
HTTP/1.1 200 OK
Date: Thu, 19 Mar 2009 17:47:53 GMT
Server: Apache/2.2.9 (Ubuntu) mod_fastcgi/2.4.6 PHP/5.2.6-2ubuntu4.1 with
Suhosin-Patch mod_ssl/2.2.9 OpenSSL/0.9.8g
Keep-Alive: timeout=15, max=100
Connection: Keep-Alive
Transfer-Encoding: chunked
Content-Type: message/http


TRACE /Nessus1511477366.html HTTP/1.1
Connection: Keep-Alive
Host: store.fabianus.com
Pragma: no-cache
User-Agent: Mozilla/4.0 (compatible
 MSIE 6.0
 Windows NT 5.0)
Accept: image/gif, image/x-xbitmap, image/jpeg, image/pjpeg, image/png, */*
Accept-Language: en
Accept-Charset: iso-8859-1,*,utf-8

------------------------------ snip ------------------------------

CVE : CVE-2004-2320
BID : 9506, 9561, 11604
Other references : OSVDB:877, OSVDB:3726



Could somebody tell me how to disable 'TraceEnable' ?

Thanks a lot for any suggestion !

Regards, 
Fabianus

---

