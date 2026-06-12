---
title: "anon-proxy (JAP) Questions"
date: 2006-01-29
forum: Server Platforms
---

### Post by .t. on 2006-01-29
I had installed JAP on my Windows PC, and to me it looked quite stable, fast(-ish) and secure. I looked for the same thing in Ubuntu, and found it as the anon-proxy package. I installed it but it doesn't work. When I set the HTTP_PROXY env. variable, and point my browsers at localhost:4001, with the server daemon running, it just sits there waiting for a response or tells me that the proxy isn't working. I don't know why this is.

My other question is: is JAP really secure? I have heard many rumours telling me otherwise.

EDIT: OK, found the post regarding Tor and Privoxy. Looks like that's a better route to take; and JAP... well, who knows if it's spyware.

---

### Post by j-strap2 on 2006-01-29
JAP is not spyware - most of the source code for the JAP system is available - certainly for the JAP client and most of the mix-related stuff. Due to legal action, the JAP team were forced to add the facility to trace connections to certain sites. You can read all about it on the JAP site and on various forums. For most people, JAP is safe to use in this respect (I think the German authorities were trying to trace somebody using a child pornography site).

[http://anon.inf.tu-dresden.de/strafverfolgung/index_en.html](http://anon.inf.tu-dresden.de/strafverfolgung/index_en.html)

If you just want to prevent your ISP and the government seeing where you surf, and prevent the destination site from seeing your IP, JAP is fine.

I don't use the ubuntu package. I download the jar file:

[http://anon.inf.tu-dresden.de/others/jap_en.html](http://anon.inf.tu-dresden.de/others/jap_en.html)

and run the command

java -jar JAP.jar


I tend to use TOR because JAP got very slow for a while.

---

### Post by .t. on 2006-01-30
Yeah, I've moved to Tor/Privoxy.

Remember to always set your Tor to act as a server; it makes the system faster and more reliable for all of us.

---

### Post by chamonu on 2006-02-28
How  to stay anonymous with Java/Javascript/plug-ins/flash... enabled


1-method

 Install Firewall on your machine and restrict all the connections to the Internet (except for the anonymous proxy server) from a browser. It's also recommended to use port mapping for this free anonymous proxy server and define the browser's proxy as 127.0.0.1 with the local port from port mapping.

2-method

 Use socksification in your browser. This will enable relaying all the information your browser or any other software sends and transfers to the proxy server.

3º- THE Best Method

 You need to set up LAN, local IP addresses (192.168.1.x or alike). A corporate proxy server should forwards ALL requests to a free anonymous proxy server (you need to have skills and rights of a system administrator in order to do that). It's impossible to connect to the Internet bypassing a corporate proxy, as long as external IP address is not assigned to local machines. It's also impossible to scan local machine's settings: even if Java/ActiveX applets detects and gives out your local IP address (192.168.1.x) to the web server, your anonymity will remain unbroken. So, basically, you can rate this option as 100% anonymity.


greetings

---

### Post by majikstreet on 2006-02-28
tor is nice... but it's slow... and here in dapper I keep having to do sudo mkdir /var/run/tor ..

---

