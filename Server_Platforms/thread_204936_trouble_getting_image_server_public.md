---
title: "trouble getting image server public"
date: 2006-06-27
forum: Server Platforms
---

### Post by SDREnate on 2006-06-27
I posted a similar thread a few days ago, but some new issues have arisen. Anyway, I made a WebGallery server following [these instructions]("http://doc.gwos.org/index.php/ServerGuide#WebGallery") 
Thanks to the advice of maggot, I then registered a domain at dyndns.org. So, the url should be look like [http://myhostname.dnsalias.net/gallery](http://myhostname.dnsalias.net/gallery) (but with the actual host name in place of "myhostname") This url works fine on my LAN. I also downloaded and configured ddclient on the server. 

A friend of mine told me that I also need to forward port 80 in my router configuration to the local IP of the server in order to access it from the internet. I'm using a Linksys WRT54G router. Here's a screenshot of what I did:

[IMG]http://i46.photobucket.com/albums/f110/SDREnate/ff67e04b.png[/IMG]

I also unchecked the "Block Anonymous Internet Requests" box on the router configuration page. I saved these settings, but my server is still not public. What am I doing wrong / what else do I need to do?

---

### Post by MJN on 2006-06-27
Does your ISP allow incoming port 80? And can you confirm if you can connect to your gallery using the public IP address from the Internet (I know you said the DNS was working but it can help to try and isolate the potential cause of the problem by ruling out the DNS).

What is your full domain name? There's really no point hiding it... the whole idea here is for the gallery to be publically visible under a public name.

Mathew

---

### Post by SDREnate on 2006-06-27
[QUOTE=MJN]Does your ISP allow incoming port 80? And can you confirm if you can connect to your gallery using the public IP address from the Internet (I know you said the DNS was working but it can help to try and isolate the potential cause of the problem by ruling out the DNS).

What is your full domain name? There's really no point hiding it... the whole idea here is for the gallery to be publically visible under a public name.

Mathew[/QUOTE]
the full domain name is sdrenate.dnsalias.net. I've asked a few friends on gaim to try the url, but they said it's not working. Here it is though: [http://sdrenate.dnsalias.net/gallery](http://sdrenate.dnsalias.net/gallery)
This one also works:
[http://sdrenate.dnsalias.net/gallery/view_album.php?set_albumName=album01](http://sdrenate.dnsalias.net/gallery/view_album.php?set_albumName=album01)

I'm working under the assumption that my ISP does allow incoming port 80, but I'm not sure. My ISP is Adelphia, if that helps.

---

### Post by MJN on 2006-06-28
You've configured your DNS to point to your private IP address on your LAN (192.168.1.101) whereas it needs to go to your *public *IP address i.e. the one that your ISP assigns you. Check your router to see what your public IP is or got to somewhere like [www.whatismyip.com]("http://www.whatismyip.com") (although the latter test is not guaranteed because of the potential for proxies to appear en route).
 
This is why it's working for *you* - you can route to 192.168.1.101 from your LAN clients whereas the rest of us on the Internet can't.
 
Mathew

---

### Post by Maggot on 2006-06-28
How did you configure your /etc/ddclient.conf ?

I found the easiest way was to use the "use=web".

Here is a sample of my /etc/ddclient.conf

pid=/var/run/ddclient.pid
protocol=dyndns2
custom=yes
#use=if, if=eth0
use=web
server=members.dyndns.org
login=username
password='password'
domain1,domain2

I believe you won't use the custom=yes line. Like I mentioned, I registered my own domainnames and have dyndns only as a DNS server.

Your router is setup correct BTW.

If you go to dyndns.org and login to your account, somewhere there is the setting that tells you what dyndns see's your comptuer IP as. You can manually modify it there too.

---

### Post by houstonbofh on 2006-06-29
Set up your dyndns account in the wrt54g.  It will automagically update you when it changes.  Then the incoming request goes to the WRT54g which forwards it to your server.

---

