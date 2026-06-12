---
title: "Apache - one site from several servers"
date: 2013-03-01
forum: Server Platforms
---

### Post by Grobbendonk on 2013-03-01
This is a bit of a newbie question - I'm trying to do something, I'm sure Apache can do it, but I'm stuck.  The power of Apache and my inexperience has left me a) lost and b) totally unsure I've even got the right idea.

The problem - I've got a small network with a handful of servers running different web-services.  These need to be combined into one web-site.  To keep it simple, let's say that internally [http://192.168.1.10](http://192.168.1.10) throws up an application "foo" and [http://192.168.1.20](http://192.168.1.20) serves up "bar".  On a third server, we've got Apache on the Ubuntu server, on the internet as [http://oursite.net/](http://oursite.net/) , where it's happily throwing up the contents of /var/www/ exactly as documented.

What I'd like is [http://oursite.net/](http://oursite.net/) to serve as it is, but be able to insert the other servers underneath it.  So a hit on [http://oursite.net/foo](http://oursite.net/foo) from the outside serves up what lives at [http://192.168.1.10](http://192.168.1.10), and [http://192.168.1.20](http://192.168.1.20) looks like [http://oursite.net/bar](http://oursite.net/bar)

From the reading I've done, I think I might need proxypass and/or rewrite, but they can do so much, I'm a bit lost!  I guess this is where my question is - can I do it with either of them? Both? Something else?  

TIA, Nic

---

### Post by GordThompson on 2013-03-02
You want to set up a reverse proxy. I found a blog posting here that should get you started:

[http://whitehat.williamlee.org/2011/05/apache2-modproxy-as-reverse-proxy-on.html](http://whitehat.williamlee.org/2011/05/apache2-modproxy-as-reverse-proxy-on.html)

---

### Post by Grobbendonk on 2013-03-02
Great, thank you, that implies I'm starting in the right place :-)  

But I am still stuck.   I need [http://oursite.net/foo](http://oursite.net/foo) to proxy [http://192.168.1.10/](http://192.168.1.10/)

So I think the line is "ProxyPass /foo http://192.168.1.10/" - this does part of the job, I can see the main page that the service provides under /foo, but none of the images, css, javascript, or any pages within the application.  All the links and references are wrong, referring back to the root, instead of the proxied pages.  For example, the service provides [http://192.168.1.10/cgi-bin/browse.jim](http://192.168.1.10/cgi-bin/browse.jim), but when I look at the link under [http://oursite.net/foo](http://oursite.net/foo) , it says [http://oursite.net/cgi-bin/browse.jim](http://oursite.net/cgi-bin/browse.jim) - should that not be [http://oursite.net/foo/cgi-bin/browse.jim](http://oursite.net/foo/cgi-bin/browse.jim)

Is there a setting for proxies to proxy all the locations below foo?  Or do I need to dive into rewrites?  (Or something else?)

TIA, again!

---

### Post by GordThompson on 2013-03-02
There might be some way to map the requests back and forth, and rewrites seem a likely candidate. However, it might be easier to just move the web application from 192.168.1.10/ to 192.168.1.10/foo/ so you don't need to re-map anything. 

I wrote several web apps behind a reverse proxy for a client, and their IT people insisted that the sites on the machines behind the proxy have the same path as the proxied application name. So if I was setting up an app that would be accessed from the outside via...

[http://theirproxy.example.com/gordApp/](http://theirproxy.example.com/gordApp/)

...I was required to set it up on the host server as...

[http://192.168.1.10/gordApp/](http://192.168.1.10/gordApp/)

...and not in the server root, even if there was only one web application on that server.

I don't know if that was because they were unwilling (or unable) to go through the mapping exercise, or whether that's just the way reverse-proxied apps are normally set up.

---

### Post by Grobbendonk on 2013-03-02
Hmm, that makes sense.  It works for the app I can relocate.

Problem is that a couple of the applications are on embedded systems.  You give the boxes an IP address, and they throw up a web-interface there.  There's no configuration options or access to the OS, so relocation is not an option.

Any ideas?

---

### Post by GordThompson on 2013-03-03
> **Grobbendonk said:**
> Hmm, that makes sense.  It works for the app I can relocate.

Problem is that a couple of the applications are on embedded systems.  You give the boxes an IP address, and they throw up a web-interface there.  There's no configuration options or access to the OS, so relocation is not an option.

Any ideas?
I found a Stack Overflow article [here]("http://stackoverflow.com/questions/1393706/how-to-use-a-different-path-name-in-proxypass-than-the-tomcat-context-name") which suggests that a solution without moving the app(s) might be as simple as using both ProxyPass and ProxyPassReverse, as in

```
ProxyPass /foo/ http://192.168.1.10/
ProxyPassReverse /foo/ http://192.168.1.10/
```
(Note that a comment in that article seems to indicate that the trailing slashes are important.)

---

### Post by Grobbendonk on 2013-03-04
Thank you for trying, but that does exactly the same (I've tried every combination of trailing slashes just in case).  The main page comes out, but all the links are relative to the server root and not below /foo

I think I'll have another look at rewrites next, as that sounds like it might do it.

---

### Post by GordThompson on 2013-03-04
After a bit more searching I found another suggestion [here]("http://ubuntuforums.org/showthread.php?t=1320324&p=8288374#post8288374"). Does that help? (It looks like mod_proxy_html is in the mix, too.)

---

### Post by GordThompson on 2013-03-05
I started feeling guilty after sending you on a bit of a wild goose chase with the results of my Google searches, so I thought I'd try it myself. I created a site in the root of my 64-bit test server, which lives at 192.168.1.103. Then I went to my 32-bit dev server, which is at 192.168.1.3, and did the following:

First I installed the package

```
sudo apt-get install libapache2-mod-proxy-html
```
Then I enabled the three (3) mods

```
sudo a2enmod proxy proxy_html proxy_http
```
Then I edited the '/etc/apache2/sites-available/default' file and added the following two (2) lines immediately after the DocumentRoot directive

```
ProxyPass /u64/ http://192.168.1.103/
ProxyPassReverse /u64/ http://192.168.1.103/
```
Then I restarted apache2

```
sudo service apache2 restart
```
Now when I browse to...

[http://192.168.1.3/u64/](http://192.168.1.3/u64/)

...I get exactly the same site as if I browse to...

[http://192.168.1.103/](http://192.168.1.103/)

The links are all mapped and everything seems to be working as it should.

---

### Post by koenn on 2013-03-06
It's all about mapping one URL to another with as little effort as possible - but there are severall things at play here

1- you need ProxyPass and ProxyPassReverse to map URLs as they appear in HTTP requests (GET, ...), and in the HTTP headers that are part if the replies
2- you (usually) need mod_proxy_html because that handles URLs in the content of the replies (i.e. if a page contains a hyperlink, it'll need to be modified so it points to the proxy server). mod_proxy_html does that on the fly while that page is being send to the browser

If you can get away with just this, you're golden, and that's probably the reason that IT-department insisted on the symmetry between the proxy and the actual web apps

You **may** need more  ProxyPass/ ProxyPassReverse pairs than you initially anticipated - eg if the proxied webapp/website uses more than one path, as in the /foo and /cgi example. You could map "/cgi" to one of the servers, but that is obviously not a solution if "/cig" is needed in more than 1 site or server. 
In that case, you have a choice between reorganizing the websites/webapplication's directory tree, or go to the next mechanism:

3- 
If you've exhausted the possibilities  above, and you still have certain URL's that don't work, you'll need an additional mechanism - possibly redirects or URL rewrites, and you probably want to try redirects before you fall back on rewrites, to avoid the processing overhead.  

Also, rewrites and the associated pattern matching is more complicated and therefore more error prone  and less maintenance free than simply "reverse poxy" mappings as in 1- and 2-

---

