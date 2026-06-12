---
title: "Apache2 hijacked?"
date: 2011-11-11
forum: Server Platforms
---

### Post by tehtide on 2011-11-11
Ok... I need some help on apache. I have just the default install of apache2 on Oneiric. Strictly the distribution setup. It is there just to server up a couple of status pages for my server for right now.

My issue comes when I startup apache2... once it is up and running my access log is filled with stuff like this:

```

***.***.***.*** - - [11/Nov/2011:14:33:32 -0500] "GET http://****** HTTP/1.1" 404 506 "https://****" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322)"
***.***.***.*** - - [11/Nov/2011:14:33:32 -0500] "GET http://**** HTTP/1.1" 200 428 "http://****" "mozilla/4.0 (compatible; MSIE 6.0; Windows 5.1;Windows 5.5;Windows 6.0)"

```

I assume that people are trying to use my server as a proxy pass through or something similar... I got that. I don't have mod_rewrite or mod_proxy enabled so I get the 404 errors. What bothers me are the status 200's. Those are requesting websites that don't exist on my server, but my server is returning a status of 200.

So I have 2 questions...
1. How the heck do I stop this? Or is this just something that I get to live with?
2. Why is Apache returning 200 when clearly it should be returning a 404 at the very minimum?

I have *** out the websites... but on the second line from the access log the first [http://***](http://***) request and the second [http://***](http://***) site are different addresses...

Any help would be appreciated.

---

### Post by Dangertux on 2011-11-11
Webserver's are scanned for open proxies constantly, as well as various vulnerabilities, which may have been what you are seeing. Since you didn't post what the GET request with the 200 reponse is for, I can't really tell you what it was.

If you want to tighten your apache security up I suggest installing mod-security. There is a procedure here : [http://dangertux.wordpress.com/tutorials/ubuntu-10-04-apache-current-mod-security/](http://dangertux.wordpress.com/tutorials/ubuntu-10-04-apache-current-mod-security/)

It should work for Ubuntu 11.10 just as well. 

Ultimately though, this is the nature of an internet facing server.

Hope this helps.

---

### Post by tehtide on 2011-11-11
This is the actual get response...

```

209.188.25.174 - - [11/Nov/2011:14:33:32 -0500] "GET http://www.chinaxindu.com HTTP/1.1" 200 428 "http://www.baidu.com" "mozilla/4.0 (compatible; MSIE 6.0; Windows 5.1;Windows 5.5;Windows 6.0)"

```

I understand the scanning part of it... I just didn't know what was/is normal and how I can doubly make sure that my server isn't doing something that it shouldn't be doing. I don't want to see my bandwidth get eaten up by this stuff.

I will look into the mod_security for sure.

---

### Post by lisati on 2011-11-11
Here's my $0.02: [http://www.baidu.com](http://www.baidu.com) is a provider based in China that includes a search engine which is probably crawling your site. I've seen it several times in my server's logs, and so far haven't had any major cause for concern. I'd only be worried if [http://www.chinaxindu.com](http://www.chinaxindu.com) isn't hosted on your machine.

The relevant Wikipedia article can be found [here]("http://en.wikipedia.org/wiki/Baidu").

---

### Post by tehtide on 2011-11-11
> **lisati said:**
> Here's my $0.02: [http://www.baidu.com](http://www.baidu.com) is a provider based in China that includes a search engine which is probably crawling your site. I've seen it several times in my server's logs, and so far haven't had any major cause for concern. I'd only be worried if [http://www.chinaxindu.com](http://www.chinaxindu.com) isn't hosted on your machine.

The relevant Wikipedia article can be found [here]("http://en.wikipedia.org/wiki/Baidu").

Thanks for the info... 

[http://www.chinaxindu.com](http://www.chinaxindu.com) isn't hosted on my site... hence my concern.

---

### Post by Dangertux on 2011-11-11
> **lisati said:**
> Here's my $0.02: [http://www.baidu.com](http://www.baidu.com) is a provider based in China that includes a search engine which is probably crawling your site. I've seen it several times in my server's logs, and so far haven't had any major cause for concern. I'd only be worried if [http://www.chinaxindu.com](http://www.chinaxindu.com) isn't hosted on your machine.

The relevant Wikipedia article can be found [here]("http://en.wikipedia.org/wiki/Baidu").

This pretty much covers it.

It's important to know that in its default configuration that Apache will respond to a GET request for anydomain.com/ so long as it is pointing at your IP address. So if for some reason the search crawler thought that WAS your domain. Then your webserver would have fulfilled the request hence 200 OK.

Hope thism akes sense

---

### Post by Vegan on 2011-11-11
I use a Cisco box to manage traffic. I only forward port 80 so nothing else gets in.

scanners see my firewall

---

### Post by tehtide on 2011-11-11
> **Vegan said:**
> I use a Cisco box to manage traffic. I only forward port 80 so nothing else gets in.

scanners see my firewall

I've got UFW on this box running... this is just a small home server for playing around and providing router/proxy cache/firewall/NAS for my home network. I was/am concerned why I am getting all these requests for websites that don't exist on my server.

---

### Post by Dangertux on 2011-11-11
Read what I said above if the Search crawler for some reason requests that domain from your servers ip and say it's looking for /index.HTML due to the initial configuration of apache it will fulfill the request

Here you can test it. 

Do something like this 

```

echo -e "GET http://google.com HTTP/1.1\n\n" | nc localhost 80 | less

```You will notice the same 200 Ok for your request to your server for google. Which you clearly aren't hosting either.

Now that I'm on a computer and not my phone I can explain why more clearly this happens.

If you look at your default apache install particularly your default site (/etc/sites-available/default)

you will notice that there is no servername so the vhost is 

VirtualHost *:80 - Or any host name on port 80. So if someone sends your server's ip a get request for google.com/index.html and you have an index.html you will respond, because you aren't paying attention to anything before /index.html.

Does that make more sense? As it stands right now your server doesn't know its domain, you may but it just knows it accepts GET requests on port 80.

---

### Post by tehtide on 2011-11-11
> **Dangertux said:**
> This pretty much covers it.

It's important to know that in its default configuration that Apache will respond to a GET request for anydomain.com/ so long as it is pointing at your IP address. So if for some reason the search crawler thought that WAS your domain. Then your webserver would have fulfilled the request hence 200 OK.

Hope thism akes sense

Sorry missed this part...


that does make total sense. So how do I configure apache2 to only respond to requests that match my server name? It is just setting a server name for the site? Or is there any other configuration that needs to be done?

---

### Post by Dangertux on 2011-11-11
If you look in thhout at file I mentioned /etc/apache2/sites-available/default

You will see something that looks like the below.

```
<VirtualHost *> 
```Add the following 
```

        ServerAdmin webmaster@example.com         
        ServerName  www.example.com                
        ServerAlias example.com 
```where example.com is the domain you want it to respond to. Note this should be a domain who's A record points to your IP address.  Save the file and restart apache2 .

Hope this helps.

---

### Post by tehtide on 2011-11-11
> **Dangertux said:**
> If you look in thhout at file I mentioned /etc/apache2/sites-available/default

You will see something that looks like the below.

```
<VirtualHost *> 
```

Add the following 
```

        ServerAdmin webmaster@example.com         ServerName  www.example.com         ServerAlias example.com 
```

where example.com is the domain you want it to respond to. Note this should be a domain who's A record points to your IP address.  Save the file and restart apache2 .

Hope this helps.

I appreciate your help... thanks for being patient with me on this one... :D

---

### Post by Dangertux on 2011-11-11
Make sure you look back at my edit, the code block wasn't spaced right in the first version those lines should be on NEW lines underneath eachother.

---

### Post by SeijiSensei on 2011-11-14
In answer to your original reply, the 200 response is sending back the default index page for the site, usually the "It Works!" page on an Ubuntu server.  You can see this by connecting to the server with telnet like this:

```

telnet www.example.com 80
Trying xxx.xxx.xxx.xxx...
Connected to www.example.com.
Escape character is '^]'.
GET / HTTP/1.1
Host: www.chinaxindu.com
[Hit enter a second time]

```

(Replace [www.example.com](www.example.com) with the name of your server.)  You'll see the contents of the file that is returned in response to your request.  It should be the default page for your server sent with the 200 response.  Any hostname put in the Host: parameter will be checked against the ServerName directives of your various virtual host definitions.  If it doesn't match any of them, the default response is sent.  On Ubuntu, the default is defined in /etc/apache2/sites-enabled/000-default.

---

