---
title: "ssh tunneling and SOCKS5"
date: 2010-02-17
forum: Server Platforms
---

### Post by ja660k on 2010-02-17
hey guys,
while trying to install/configure cups... for the admin web interface i need to be the server, and as it is headless i thought id tunnel into it
```

ssh ja660k@192.168.0.100 -D 8080 -p 1025

```

where the tunnel i opened is on 8080

and i go to firefox->edit->preferences->advanced->network->connection settings.

and in the socks5 host i enter in localhost port 8080 
but it doesnt work, i cant connect to the servers admin web interface for cups, it says i dont have permission because only the server can access the web interface

so do i need any additional software to do this? i have ssh server 

thanks in advance

---

### Post by HermanAB on 2010-02-18
Howdy,

CUPS uses port 631, not 1025.

---

### Post by ja660k on 2010-02-18
> **HermanAB said:**
> 
CUPS uses port 631, not 1025.

yes, but 1025 is the ssh port...(which i have changed from 22)

this is not about cups
im trying to tunnel into my home server, then getting firefox to use SOCKS5 via the tunnel

---

### Post by Irosaki75 on 2010-03-12
> **ja660k said:**
> yes, but 1025 is the ssh port...(which i have changed from 22)

this is not about cups
im trying to tunnel into my home server, then getting firefox to use SOCKS5 via the tunnel

  
try:         ssh -D 1080 ja660k@192.168.0.100 -p 1025

I use 1080 instead of 8080 as it may be being used already, try that, i also set my ssh to listen on 443 because that port is always open + my server is currently not using it.



you will then get the "enter user's password" prompt and you're in, minimize the terminal keeping it open.

goto firefox and set the proxy to socks5 as localhost 1080
(if you have any other proxy type set it may mess it up.)

that should sort it, try surfing. (I use foxyproxy, its really nice for quickly switching between pre-saved proxies).

Hope this helps.

---

