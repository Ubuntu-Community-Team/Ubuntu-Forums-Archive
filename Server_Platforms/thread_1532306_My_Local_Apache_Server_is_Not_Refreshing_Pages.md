---
title: "My Local Apache Server is Not Refreshing Pages"
date: 2010-07-16
forum: Server Platforms
---

### Post by skrimpy on 2010-07-16
I own several websites and have always developed on my local Apache server.

I am in the middle of releasing a new product on one of my sites and have been making rapid changes to the site based on feedback from customers, etc. as my product has gone live...

My local server is NOT refreshing pages.  I make a change, click "refresh" in my browser and nothing happens.

I have tried clearing my browser cache and it makes no difference. Eventually (several minutes later) my changes happen.

Problem is, I need to be making these changes rapidly, and I really prefer to check my work on localhost before uploading it to a live server where I'm getting a lot of visitors right now.

This is a very recent problem as I have never had this occur before.  Running 10.04.

Any help?

---

### Post by cdenley on 2010-07-16
Try sending an HTTP request to your server directly, and see how it actually responds. This will narrow it down to either a client issue or a server issue.
```

echo -e "GET /path/to/changed/file HTTP/1.0\nHost: mydomain.com\n"|nc -q 1 127.0.0.1 80

```

---

### Post by skrimpy on 2010-07-16
Thanks for your reply cdenly,

Maybe I'm not getting something right with the syntax, because I'm getting a 404 Not Found error returned to me in the terminal.

My page is at the root of my domain.

So I have:

```
http://localhost.mydomain.com/nonupdatingpage.html
```

I've tried several different things in the syntax you gave me but I'm apparently not putting it in right.  Could you show how it should be using the example URL I gave above?

---

### Post by cdenley on 2010-07-16
I am assuming you are running the command on the server itself, so the request would be sent to 127.0.0.1.
```

echo -e "GET /nonupdatingpage.html HTTP/1.0\nHost: localhost.mydomain.com\n"|nc -q 1 127.0.0.1 80

```

---

### Post by skrimpy on 2010-07-16
well, that's one of the combinations I tried...  Here's my output:

```
me@my-desktop:/var/www$ echo -e "GET /first-bites-and-beyond.html HTTP/1.0\nHost: localhost.naturalbirthandbabycare.net\n"|nc -q 1 127.0.0.1 80
HTTP/1.1 404 Not Found
Date: Fri, 16 Jul 2010 14:52:15 GMT
Server: Apache/2.2.14 (Ubuntu)
Vary: Accept-Encoding
Content-Length: 328
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>404 Not Found</title>
</head><body>
<h1>Not Found</h1>
<p>The requested URL /first-bites-and-beyond.html was not found on this server.</p>
<hr>
<address>Apache/2.2.14 (Ubuntu) Server at localhost.naturalbirthandbabycare.net Port 80</address>
</body></html>
```

The page IS loading in Apache... it's just not updating...  

It's fine when I upload it to my live server so the problem isn't with something being messed up in my page's code.  Something is going on with my local server.

---

### Post by cdenley on 2010-07-16
Works fine for me.
```

echo -e "GET /first-bites-and-beyond.html HTTP/1.0\nHost: localhost.naturalbirthandbabycare.net\n"|nc -q 1 localhost.naturalbirthandbabycare.net 80

```

Your server where you are running that command responds with a 404 error when receiving requests for /first-bites-and-beyond.html with host localhost.naturalbirthandbabycare.net on interface 127.0.0.1. I couldn't tell you why exactly unless you post your server configuration. Perhaps you should try sending it to a different network interface.

---

### Post by skrimpy on 2010-07-16
I'm not sure how to go about sending it to a different network interface.  I can post any configuration files if you let me know what to post... otherwise I'm at a loss.  I cut and pasted the command into the terminal so I know there are no typos.

My server has *finally* updated the change I made close to 2 hours ago... really want to find out what's causing these delays :(

---

### Post by cdenley on 2010-07-16
```

echo -e "GET /first-bites-and-beyond.html HTTP/1.0\nHost: localhost.naturalbirthandbabycare.net\n"|nc -q 1 **xxx.xxx.xxx.xxx** 80

```
Replace "xxx.xxx.xxx.xxx" with the IP address of the server's interface you wish to send it on.

---

### Post by skrimpy on 2010-07-16
I tried sending it via the IP of the machine that I'm on now and got the same result :(  Is that what you meant?

---

### Post by skrimpy on 2010-07-16
ok I got this figured out... I needed to specify the path after the GET... so I had to put:

```
echo -e "GET /naturalbirthandbabycare.net/first-bites-and-beyond.html HTTP/1.0\nHost: localhost.naturalbirthandbabycare.net\n"|nc -q 1 127.0.0.1 80
```

This returned the page with these headers:

```
HTTP/1.1 200 OK

Date: Fri, 16 Jul 2010 17:39:28 GMT

Server: Apache/2.2.14 (Ubuntu)

Accept-Ranges: bytes

Vary: Accept-Encoding

Connection: close

Content-Type: text/html



<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>

...and so forth through my code...
```

The page still isn't updating properly.

---

### Post by cdenley on 2010-07-16
Are you sure the page which you updated is the same page which you are requesting? You didn't provide enough information for me to walk you through it.

Did you enable caching on the server?
```

sudo a2dismod disk_cache mem_cache cache
sudo /etc/init.d/apache2 restart

```

---

### Post by skrimpy on 2010-07-16
Hi cdenley - I gave you all the output I got from the command you gave me.

I'm sure it's the same page... I've second-guessed myself about 50x times, wondering if maybe I'm going crazy.  But it's definitely the same page... it has kind of a unique name :p

The output that returned to me with the HTTP request does reflect the change I made (I added bolded text with the strong tag) - it shows that syntax in the terminal output.

But the page in my browser (default Ubuntu Firefox) is still not updating... it's not updating on my other computer, either, when I use my server's IP address to access the page on that browser (that one is Firefox in Windows 7).  I've cleared the cache on both browsers to no avail, which is why I was thinking it's an Apache issue.

My Apache install is the default LAMP install one does with Ubuntu... the only thing I can think I've done to it is enable the x-bit hack for SSI.  

I don't recall enabling caching - should I do so?

---

### Post by cdenley on 2010-07-16
> **skrimpy said:**
> The output that returned to me with the HTTP request **does reflect the change I made** (I added bolded text with the strong tag) - it shows that syntax in the terminal output.

I'm confused. You said before when you posted the server's response "The page still isn't updating properly". When interacting directly with the server via the netcat command I gave, does apache serve the correct content?

Some sort of caching is the only thing I could think of which would cause what you describe, so I would not suggest enabling any caching at the moment.

Do you have a client computer with Linux on it? If not, can you run an ubuntu livecd on a client computer? Is there any kind of caching web proxy or content firewall your requests may pass through before they reach your web server?

---

### Post by skrimpy on 2010-07-16
> I'm confused. You said before when you posted the server's response "The page still isn't updating properly". When interacting directly with the server via the netcat command I gave, does apache serve the correct content?

Right... sorry for being confusing.  When I give the HTTP request via the command you gave me, I get the **correct** code in the terminal.

However the page is not updating in the **browser** - it's not updating on my server or on my laptop.  I have tried clearing the cache on both of those machines.  The only thing that seems to work is A. wait hours or B. reboot the server.

I thought it must be browser caching but clearing the cache doesn't seem to make any difference whatsoever.


> Do you have a client computer with Linux on it? If not, can you run an ubuntu livecd on a client computer? Is there any kind of caching web proxy or content firewall your requests may pass through before they reach your web server? 

My netbook runs UNR so I could try something on that.  

I don't think the requests are passing through anything - I develop on my server and I'm checking the pages on my server.  I'm definitely saving the HTML file, those changes are just not being reflected in the browser.

---

### Post by cdenley on 2010-07-16
Well, since you indicated the server gives correct responses when you use netcat, I doubt the problem is with apache. Are you sending the request to the same IP as your web browser is?
```

getent hosts localhost.naturalbirthandbabycare.net
echo -e "GET /naturalbirthandbabycare.net/first-bites-and-beyond.html HTTP/1.0\nHost: localhost.naturalbirthandbabycare.net\n"|nc -q 1 localhost.naturalbirthandbabycare.net 80

```
You can try to capture the HTTP responses the browser gets from apache using wireshark. Then we could determine if apache is actually serving old content, and what requests will give those results.

You know, when I send that request to the server that domain resolves to, it is served by a CentOS server. I assume that is because you are using the ubuntu server in a development environment, and are accessing the ubuntu server with your browser. You did say you tried browsing by IP with the same results.

---

### Post by skrimpy on 2010-07-16
Well the browser I'm mainly using is on my local server machine.  I am really a newbie about server issues and IP stuff.  The only thing I know for certain is that I am developing on a LAMP server installed on Ubuntu 10.04... we have assigned this machine a dedicated IP since it's my development server and I frequently check my pages from other computers to see how they look.  I don't think I'm being very helpful :/

I assume 

> You know, when I send that request to the server that domain resolves to, it is served by a CentOS server. I assume that is because you are using the ubuntu server in a development environment, and are accessing the ubuntu server with your browser. You did say you tried browsing by IP with the same results. 

Yeah, my Ubuntu server is here on my home computer.  I just use it to develop.  My live server is a CentOS sever (though I **wish** my hosting company had an Ubuntu server).

If I type [www.mydomain.net](www.mydomain.net) it's served by the CentOS server, and it shows the code changes correctly.

If I type localhost.mydomain.net it's served by my Ubuntu server, and the changes aren't there.

Like I said initially, this is very recent... I have been developing on a local Ubuntu server since Feisty and this is the first time I've ever had issues.  I haven't done anything with Apache recently, either.

Off to take a look at Wireshark...

---

### Post by cdenley on 2010-07-16
If you are sending a request for the same path and the same hostname to the same server on the same network interface, then apache should serve the same content regardless of whether it originates from a netcat command or a web browser. Your browser must either be displaying a cached page, sending the request to a different server or a different interface, or sending a GET request for a different path.

The firebug plugin for firefox should show HTTP requests as well, now that I think about it.
[http://getfirebug.com/](http://getfirebug.com/)
It would be displayed in the "net" section.

Google Chrome will show HTTP headers under "Resources" in their "developer tools" (ctrl+shift+I).

The status code is important. 200 means it wasn't cached, and content should have been served by apache. 304 means your browser is re-using its cached version.

---

