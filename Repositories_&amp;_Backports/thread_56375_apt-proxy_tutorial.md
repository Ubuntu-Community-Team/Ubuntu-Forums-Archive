---
title: "apt-proxy tutorial"
date: 2005-08-12
forum: Repositories &amp; Backports
---

### Post by hazza96 on 2005-08-12
I am not sure if I need apt-cacher or apt-proxy.

What I have is a Hoary server and several Hoary workstations. I want the server to keep a copy of any package that any workstation requests.

So the first time a workstation requires a package (game, security update, whatever) the server will look in it's cache see it's not there and goes and gets it. The next workstation that wants the same package will have it feed from the local cache.

I read it a while ago but I can no longer find it on how to configure the server, import the packages that have already been downloaded and configure the workstation so that the only source they have listed is the server.

Does anyone know where to find those instructions?

---

### Post by heimo on 2005-08-12
Is this helpful?
[https://wiki.ubuntu.com/AptProxyHowTo](https://wiki.ubuntu.com/AptProxyHowTo)

---

### Post by hazza96 on 2005-08-12
[QUOTE=heimo]Is this helpful?
[https://wiki.ubuntu.com/AptProxyHowTo](https://wiki.ubuntu.com/AptProxyHowTo)[/QUOTE]
ahhhhh yes that is what I had read before, I just could not find it, I did search honestly I did, I just kept going round in circles.

The wiki search function must not work very well, I searched for both apt-proxy and apt-cacher and it returned 0 results.

umm I just tried again and noticed that there are two search buttons on the wiki, one for title and the other for text, duh  ](*,)

Thank you very much.

---

### Post by hazza96 on 2005-08-13
I followed those instructions and got an error message when I tried to import the packages I had already downloaded. Searching for the error message I found this:
[http://sourceforge.net/mailarchive/message.php?msg_id=11817120](http://sourceforge.net/mailarchive/message.php?msg_id=11817120)

In it the maintainer says that they broke the import function and it was fixed in 1.9.30. I have 1.9.28 installed so I went looking for a version that is at least 1.9.30 and found 1.9.31 on this page:
[http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=apt-proxy](http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=apt-proxy)

The problem is that package is for Debian and it requires Python to be less than 2.4.

Does anyone have a apt-proxy package that is at least 1.9.30 and it can be installed on Hoary with it's 2.4.1 version of Python?

---

### Post by hazza96 on 2005-08-14
Well I am not going to bother with the importing of the old packages,

Apt-proxy works great, I have a server and 3 other Hoary workstations, it certainly saves on the downloading. I get the server to automatically update itself at night and the workstations when they startup.

---

### Post by Brad wilkinson on 2005-08-24
ok, well I've read the howtos and the Debian manual and all sorts, but I've still got some questions.

1. on my apt-proxy "server" I've installed the apt-proxy package via synaptic. do I now need to edit any of the lines in apt-proxy-v2.conf? I was thinking this one might need uncommenting and changing to the address of my router, i.e.

> 
;; Server IP to listen on
;address = 192.168.0.254   

should be

> 
;; Server IP to listen on
address = 192.168.1.254   

2. on my "clients" i need to edit the sources.list file to add a proxy lookup, the howto shows this

> 
# apt-proxy entries for standard modules
deb [http://localhost:9999/ubuntu](http://localhost:9999/ubuntu) hoary main restricted universe multiverse
deb-src [http://localhost:9999/ubuntu](http://localhost:9999/ubuntu) hoary main restricted universe multiverse   


but my server is not localhost, as the server is just 1 of 4 machines hanging from a broadband modem/router. So should I replace localhost with the IP of the machine that will act as the "server"? i.e.

> 
# apt-proxy entries for standard modules
deb [http://192.168.1.19:9999/ubuntu](http://192.168.1.19:9999/ubuntu) hoary main restricted universe multiverse
deb-src [http://192.168.1.19:9999/ubuntu](http://192.168.1.19:9999/ubuntu) hoary main restricted universe multiverse   

where 198.168.1.19 is the stable IP of my "server"

hope this is clear enough. 

cheers,

Brad

---

### Post by hazza96 on 2005-08-24
[QUOTE=Brad wilkinson]1. on my apt-proxy "server" I've installed the apt-proxy package via synaptic. do I now need to edit any of the lines in apt-proxy-v2.conf? I was thinking this one might need uncommenting and changing to the address of my router, i.e.[/QUOTE]
I think that is only need if you want to restrict the ability to connect to it, the default with the entry commented out lets any IP on any interface connect to the apt-proxy. I haven't tested it because I restricted the access to the internal IP's on eth0.
 
[QUOTE=Brad wilkinson]but my server is not localhost, as the server is just 1 of 4 machines hanging from a broadband modem/router. So should I replace localhost with the IP of the machine that will act as the "server"? i.e.[/QUOTE]
Yes, the client's need to have the IP (or name) of the apt-proxy server there instead of localhost.

---

### Post by LordMerlin on 2006-04-14
[quote=hazza96]I think that is only need if you want to restrict the ability to connect to it, the default with the entry commented out lets any IP on any interface connect to the apt-proxy. I haven't tested it because I restricted the access to the internal IP's on eth0.
 

Yes, the client's need to have the IP (or name) of the apt-proxy server there instead of localhost.[/quote]

I setup apt-proxy, as per thise links, but when I start apt-proxy (/etc/init.d/apt-proxy start) I can't connect to it on port 9999? Any suggestions? I tried to use either the machine name, or the IP address. This is my setup:

```

[DEFAULT]
;; All times are in seconds, but you can add a suffix
;; for minutes(m), hours(h) or days(d)

;; Server IP to listen on
address = 192.168.10.1

;; Server port to listen on
port = 9999


```

---

