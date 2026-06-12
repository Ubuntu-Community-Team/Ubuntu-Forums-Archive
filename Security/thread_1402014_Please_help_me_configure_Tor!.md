---
title: "Please help me configure Tor!"
date: 2010-02-08
forum: Security
---

### Post by miggerish on 2010-02-08
Okay, so I am trying to figure out how to use Tor in order to have the ultimate secure browsing experience.  

I am using this info:

Running the Tor client on Linux/BSD/Unix
[http://www.torproject.org/docs/tor-doc-unix.html.en]("http://www.torproject.org/docs/tor-doc-unix.html.en")

And I am using this page to keep testing if and when Tor is running:
[https://check.torproject.org/]("https://check.torproject.org/")

So my question is, do I have to follow all the steps mentioned in the first link?  Or can I just simply install the Tor add-on to my firefox and expect it to work?

Also, it mentions "toggling Tor".  How do I toggle it on and off?  


I am using this version of Linux Ubuntu and Mozilla Firefox:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.7) Gecko/20100106 Ubuntu/9.10 (karmic) Firefox/3.5.7

version 3.5.7 of firefox and "Mozilla Firefox for Ubuntu canonical - 1.0" are the details

Also, is this information important for me to follow:
[http://www.torproject.org/docs/tor-doc-web.html.en]("http://www.torproject.org/docs/tor-doc-web.html.en")   ???

I have very little experience in the terminal, and when it gives instructions in the first link, I get confused.

Thanks

---

### Post by rookcifer on 2010-02-08
1) Add these lines to /etc/apt/sources.list:

```
deb http://deb.torproject.org/torproject.org karmic main
deb-src http://deb.torproject.org/torproject.org karmic main

```

2) Import the keys:

```
gpg --keyserver subkeys.pgp.net --recv 886DDD89
gpg --fingerprint 886DDD89
gpg --export 886DDD89| sudo apt-key add -
```

3) Install tor 

```
sudo apt-get update && sudo apt-get install tor privoxy
```

4) Configure privoxy:

```
sudo nano /etc/privoxy/config/
```

At the end of the file, add this line exactly as listed:

```
forward-socks4a / localhost:9050 .
```

5) Start Tor:

```
sudo /etc/init.d/tor start
sudo /etc/init.d/privoxy start
```

6) Install the firefox add-on "tor button."

7) Click on the tor button to start browsing through tor.  First thing you should do is go test it at "whatsmyip" or some other such site.  

**Important:**  Do not to send personal info out while on tor -- that is, do not give your login credentials to websites that require them **unless the website uses SSL**.  Why?  Because the tor exit node can sniff all traffic, which means they can steal your username and passwords if they are used on sites that don't have secure logins (and most sites do not use secure logins).  Remember, tor is for anonymity and *not privacy*; you should **always assume** the guy at the exit node is watching your traffic.

---

