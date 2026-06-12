---
title: "Virtual hosts don't work with any web server"
date: 2010-01-21
forum: Server Platforms
---

### Post by Phoenixheart on 2010-01-21
Hello,

I don't know if I'm posting in the right box - I'm new to both Ubuntu and this forum so please bear with me. 

Thing is, I spent almost 2 days trying to find a web server that meets my likes. I tried like almost every well known web server, be it Apache, Lighttpd, Nginx, and Cherokee, one by one. For each I was successfully in getting PHP up and running, but was never able to configure the virtual hosts.

I'm 99.99% sure that I - for multiple times - followed correctly the online how-to's. Especially Cherokee, I did exactly the screencast (which is just 2 steps, as Cherokee has a GUI for virtual server setups). Strange enough, with each web server the virtual hosts thing never worked for me. I always received "Server not found" error.

I tried with Firefox and Google Chrome. Currently I'm on an Ubuntu 9.10 (32bit) box - I reinstalled this one over the 64bit, to vain.

Don't know if it's a problem with my DNS, but I have another machine running Windows 7 with the same DHCP settings (means same DNS and IP range). Virtual hosts work fine there on an XAMPP installation.

I'm totally clueless. Any help would be much, much appreciated.

---

### Post by steven.jones on 2010-01-21
> **Phoenixheart said:**
> Hello,

I don't know if I'm posting in the right box - I'm new to both Ubuntu and this forum so please bear with me. 

Thing is, I spent almost 2 days trying to find a web server that meets my likes. I tried like almost every well known web server, be it Apache, Lighttpd, Nginx, and Cherokee, one by one. For each I was successfully in getting PHP up and running, but was never able to configure the virtual hosts.

I'm 99.99% sure that I - for multiple times - followed correctly the online how-to's. Especially Cherokee, I did exactly the screencast (which is just 2 steps, as Cherokee has a GUI for virtual server setups). Strange enough, with each web server the virtual hosts thing never worked for me. I always received "Server not found" error.

I tried with Firefox and Google Chrome. Currently I'm on an Ubuntu 9.10 (32bit) box - I reinstalled this one over the 64bit, to vain.

Don't know if it's a problem with my DNS, but I have another machine running Windows 7 with the same DHCP settings (means same DNS and IP range). Virtual hosts work fine there on an XAMPP installation.

I'm totally clueless. Any help would be much, much appreciated.

Apache I have always found is a pig to set up for virtual hosts so you are not alone...I have so far only done Debian and its not std in terms of standard online docs for apache2 so I needed Debian specific ones and even then I had issues due to changes/errors. I have now switched to ubuntu 9.10 so this is my next job!

:/

I did a temp new virtual (Debian) server while I switch the hardware to Ubuntu and made some brief notes...

[http://graywitch.co.nz/debian/apache2.htm](http://graywitch.co.nz/debian/apache2.htm)

These might help....I will do better and ubuntu specific ones once I get to it, which will be in a few days.

If you post back any gotchas you find that would probably help me.

regards

---

### Post by Phoenixheart on 2010-01-21
Thanks Steven,

Actually I don't think that I did the configuration wrong - in the end I'm not that bad in copy and paste :) And how could it be all web servers? This is definitely something weird (maybe I'm just dumb).

---

### Post by cdenley on 2010-01-21
> **Phoenixheart said:**
> Thanks Steven,

Actually I don't think that I did the configuration wrong - in the end I'm not that bad in copy and paste :) And how could it be all web servers? This is definitely something weird (maybe I'm just dumb).

If you can't get any server to work, then it must not be a server issue. Are you sure your requests are actually reaching the server? You should test it with a command like this:
```

echo -e "GET / HTTP/1.0\nHost: mydomain.com\n"|nc 127.0.0.1 80

```

How are your hostnames being resolved?
```

host mydomain.com

```

---

### Post by thefunnyman on 2010-01-21
Also, show us your apache virtualhost config if you don't mind.

---

### Post by Phoenixheart on 2010-01-21
Hi,

Doing an echo returns nothing in my terminal.
The host command returns: Host test.dev not found: 3(NXDOMAIN)
Currently I'm using lighttpd. The virtual host configuration is as simple as follow: 

```

# other that these lines at the bottom of /etc/lighttpd/lighttpd.conf
# I don't have any changes
$HTTP["host"] =~ "(^|\.)test\.dev$" {
  server.document-root = "/home/phoenixheart/www/wordpress"
}
```

Thanks for your help.

---

### Post by cdenley on 2010-01-22
> **Phoenixheart said:**
> 
Doing an echo returns nothing in my terminal.

What is the full command you tried? Are you sure it finished? I don't think netcat will return with no output. You did substitute the correct domain, right?
> **Phoenixheart said:**
> 
The host command returns: Host test.dev not found: 3(NXDOMAIN)

So your domain is "test.dev", and your website is "http://test.dev/"? How is the hostname supposed to get resolved? Do you have it configured in the /etc/hosts file of every computer you try to connect with?
```

ping -c 1 test.dev

```
> **Phoenixheart said:**
> 
Currently I'm using lighttpd. The virtual host configuration is as simple as follow:

If you want help with web server configuration, you might want to switch back to apache.

---

### Post by Phoenixheart on 2010-01-22
Hi,

/etc/hosts file did the trick! I've no idea why I didn't even think of it - I did it hundreds of time on Windows with XAMPP. How stupid I was!

Now it's not server not found error anymore... but 403 Forbidden.

I checked and verified that:

- The /wordpress folder is in place.
- The host entry is there (127.0.0.1 test.dev)
- The folder and its content's owner is www-data
- lighttpd has been restarted.

Am I still missing something here? Thanks in advance!

---

### Post by cdenley on 2010-01-22
> **Phoenixheart said:**
> Hi,

/etc/hosts file did the trick! I've no idea why I didn't even think of it - I did it hundreds of time on Windows with XAMPP. How stupid I was!

Now it's not server not found error anymore... but 403 Forbidden.

I checked and verified that:

- The /wordpress folder is in place.
- The host entry is there (127.0.0.1 test.dev)
- The folder and its content's owner is www-data
- lighttpd has been restarted.

Am I still missing something here? Thanks in advance!

Does lighttpd run as www-data? Once again, if want support with a web server, you would have better luck with apache. I've never used lighttpd before.

---

### Post by Phoenixheart on 2010-01-22
You have been a life-saver cdenley - I'm really, really appreciate for that.
Now that I know the problem came from /etc/hosts, I think I'll go for nginx (which I intended to go with from the beginning). Let's see how it goes.

Cheers,
An

---

### Post by R.Bucky on 2010-01-23
I am currently operating around 12 domains with my server using Apache Virutal Hosts. Read this [http://buckycomputing.net/blog/hosting-2-domains-with-1-server/]("http://buckycomputing.net/blog/hosting-2-domains-with-1-server/")

---

### Post by zereshk on 2010-02-05
Actually it is very easy to set up virtual hosts in Apache2. You can follow [this noog-friendly instructions ]("http://www.debian-administration.org/articles/412")and you'll be fine. 
[Here]("http://jblevins.org/computing/internet/ubuntu-vps") also there is a very comprehensive article for insallaton and fine-tuning of apache.

In addition, you can even finde some scripts[ like this]("http://www.commandlineidiot.com/blog/2007/plate-up-bash-script-for-apache-vhost-setup/"), that automate adding virtual hosts for you.

---

