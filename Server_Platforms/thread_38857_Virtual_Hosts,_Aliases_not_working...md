---
title: "Virtual Hosts, Aliases not working.."
date: 2005-06-02
forum: Server Platforms
---

### Post by CrustyDOD on 2005-06-02
Hey

I configured Virtual Host and now my aliases don't work anymore..

VH is configured like: [http://www.ubuntuforums.org/showthread.php?t=34238](http://www.ubuntuforums.org/showthread.php?t=34238)

I have router and server behind it, before i configured VH i could access my aliases using local ip of the server or using my outside ip address from another location, but now nothing works..

Can't try out if VH is working as domain DNS were changed (waiting min 24 hours.. :( )

So how can i get those aliases working again as that domain name is from my friend and i can't access phpmyadmin or even mine website (don't have domain name so i used alises for both things).

Oh if i just enter my local ip, it shows the default apache site.. but not anymore if i use [http://serverlocalip/some_name](http://serverlocalip/some_name)

what to do, what to do?


EDIT: nevermind, my apache crashed and if i start it, it just stops again...

FIXED..

---

### Post by LordHunter317 on 2005-06-02
Name-based VirtualHosting requires working DNS.  If you don't have DNS setup you will always get the default site.

---

### Post by CrustyDOD on 2005-06-02
OK, DNS server is already installed on default server ubuntu installation or not? Where is it located?

---

### Post by Beernut on 2005-06-04
[QUOTE=LordHunter317]Name-based VirtualHosting requires working DNS.  If you don't have DNS setup you will always get the default site.[/QUOTE]

I always thought that Apache used the HTTP headers to direct the browser to the correct site.  If you are using a dynamic dns service do you still need dns installed?

---

### Post by KRavEN on 2005-06-04
It does use HTTP headers and has nothing to do with DNS.

I have apache2 working fine without having bind installed.

There is a howto on apache2 debian style in the ubuntu wiki.  I found it searching google for apache2 virtual ubuntu on google.

you basically setup 2 files in /etc/apache2/sites-available one for http and one for https, the you use the a2ensite to enable them.

I can post my site files later if you still can't get it working

---

### Post by KRavEN on 2005-06-04
I just reread your post again.

If you add the name mappings to your /etc/hosts file it should get you going at least on the local box while you wait for DNS to converge.

I have to do something similar to test my virtual hosts out because I'm behind nat so the names can't locally map to the external ip like that would if I got them from DNS.

---

### Post by LordHunter317 on 2005-06-04
[QUOTE=Beernut]I always thought that Apache used the HTTP headers to direct the browser to the correct site. [/quote]It does.  And your clients need proper DNS to generate a HTTP Host header for name-based virtual hosting.  They can't do it without it.

>  If you are using a dynamic dns service do you still need dns installed?Your clients and servers need to be able to resolve that name to your server's IP address.  This generally doesn't mean you'll need to run your own DNS server, but it does mean they'll need access to a working DNS server.  Whether you have to run your own DNS server is dependent on your network, client, and server configurations.

> It does use HTTP headers and has nothing to do with DNS.That's simply not true.  You can't generate a correct HTTP Host header without working, correct DNS.  End of Story.

> I have apache2 working fine without having bind installed.Where did I ever say he need to install bind?  Or even that he needed to run a DNS server?

I said he needed working DNS.  Which he didn't have (or wasn't using).  Whether that requires him to setup a DNS server is a determination he has to make.

---

### Post by KRavEN on 2005-06-04
[QUOTE=LordHunter317]It does.  And your clients need proper DNS to generate a HTTP Host header for name-based virtual hosting.  They can't do it without it.

Your clients and servers need to be able to resolve that name to your server's IP address.  This generally doesn't mean you'll need to run your own DNS server, but it does mean they'll need access to a working DNS server.  Whether you have to run your own DNS server is dependent on your network, client, and server configurations.

That's simply not true.  You can't generate a correct HTTP Host header without working, correct DNS.  End of Story.

Where did I ever say he need to install bind?  Or even that he needed to run a DNS server?

I said he needed working DNS.  Which he didn't have (or wasn't using).  Whether that requires him to setup a DNS server is a determination he has to make.[/QUOTE]


Yeah, I misunderstood his first question.  I prob should have edited my first post.

---

