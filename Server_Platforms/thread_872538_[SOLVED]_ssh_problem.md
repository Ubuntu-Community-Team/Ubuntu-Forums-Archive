---
title: "[SOLVED] ssh problem"
date: 2008-07-28
forum: Server Platforms
---

### Post by boblemur on 2008-07-28
hey all, what im trying to achieve is an ssh tunnel from my computer to a server:

my computer >(ssh) > server >(http proxy)> internet proxy server > [www.google.com](www.google.com)

i have setup the link between me and the server

```
ssh -D 8080 user@server
``` 

and i have setup the firefox proxy so that SOCKS goes through the tunnel, however im unsure of how i should go about making it use the http proxy on the other side of the tunnel

---

### Post by boblemur on 2008-07-28
bump... help please

---

### Post by dmizer on 2008-07-28
part of your problem may be that the port your trying to tunnel across (8080) is http (socks), so you may be running into a conflict with that.

You'll need to use a port that's not assigned.  Try something high.  Anything above 9999 should be open and safe.

Also, the general rule of thumb for bumping a thread is at least 24 hours.  There are a number of reasons for this but most importantly because there is a team (of which I am a member) dedicated to answering posts with no replies.  And, as soon as you bump your thread, you have a reply and it is no longer searchable as a zero reply post.

Just because your post falls off the first page does not mean that it will not get an answer.

---

### Post by Sef on 2008-07-28
Moved to server platforms.

---

### Post by boblemur on 2008-07-28
im getting the following error:

```
-bash-3.2$ channel 3: open failed: connect failed: Connection refused
```

its inside the ssh terminal...

and if i run 

```
ls -l
```

i see whats inside my home dir on the server... so i have sucessfuly connected to the server...

however i dont know what the channel 3: means? or who/what is refusing my connection is there a way i can find out


also, sorry about the early bump... thanks for the move


ps i changed the port to 12345 is their a prob with that?

---

### Post by dmizer on 2008-07-28
here's a good post that may help: [http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/](http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/)

shouldn't be a problem with using port 12345 as far as i know.

---

### Post by boblemur on 2008-07-28
thanks for that, however thats where i got the original command from...


my problem is specificly... i have a tunnel through SOCKS to the server...

and now i am trying to find a way to point it at the web proxy...



basicly... i have my home computer, im ssh'ing into the server... however the server sits behind a web proxy... and i need to get my traffic to go from my computer... to the server and then out through their proxy, as though the connection was comming from within the network the server is on

---

### Post by dmizer on 2008-07-28
I see.

Open firefox:
Edit > Preferences > Advanced > Network (tab) > Settings.

Select "Manual proxy configuration"

In the blank next to "SOCKS host", type
```
localhost
```
and in the blank next to "port", type: 12345

Click "OK" > "Close"

You should now be using your proxy server.

---

### Post by ChumleyEX on 2008-07-28
Hey man I had a lot of trouble with this too. I had to install squid to get it working. Tunneling is very powerful. Just install squid and webmin (to help configure the caching) and your good to go. 


I could never get it to work without squid.

---

### Post by boblemur on 2008-07-28
as in install squid on the server??

because its not my server... its my uni server...

---

### Post by dmizer on 2008-07-29
take a look here: [http://www.debuntu.org/port-forwarding-and-channel-3-open-failed-connect-failed-Connection-refused](http://www.debuntu.org/port-forwarding-and-channel-3-open-failed-connect-failed-Connection-refused)

By the way, I just used this technique to proxy through my home server from work.  I was surprised to learn that it even worked in Windows using [cygwin](http://www.cygwin.com/).

---

### Post by cariboo on 2008-07-29
Seeing as this isn't your server you may want to contact your university IT staff before trying this.

JIm

---

### Post by boblemur on 2008-07-29
yeh i know this works, i used too  use it to tunnel past my schools web filter so i could play games :)

but my problem is maybe the uni is blocking it? however putty/ssh report successfully forwarding of the ports... and i can access the uni intranet, so i can get it to go through to the uni just having problems getting the server to then forward it to the web server at uni..

---

### Post by boblemur on 2008-07-29
> **cariboo907 said:**
> Seeing as this isn't your server you may want to contact your university IT staff before trying this.

JIm

true, although i dont think they would mind... they just wouldn't help me...

---

### Post by Thund3rstruck on 2008-08-29
Did you ever solve this? I'm running an SSH server as well and all works well when I telnet in but firefox always replies 'Proxy Server Connection Refused'. I have tried every guide out there and none of them work. The SSH server runs just fine but the SOCKS proxy feature just doesn't work.

---

### Post by dmizer on 2008-08-29
> **Thund3rstruck said:**
> Did you ever solve this? I'm running an SSH server as well and all works well when I telnet in but firefox always replies 'Proxy Server Connection Refused'. I have tried every guide out there and none of them work. The SSH server runs just fine but the SOCKS proxy feature just doesn't work.

What version of ubuntu are you using for your ssh server? How are you configuring your proxy in firefox?

---

### Post by boblemur on 2008-08-31
yes i did solve this problem

i use:

```
ssh -L 9999:proxy.domain.com:8000 me@uni_ssh_server

```

where 8000 is the port the proxy accepts connections on 9999 can be chosen to be any value (if less than 1000 you will need sudo) proxy.domain.com is the address of the proxy or computer u want to forward to (from the perspective of uni_ssh_server

so say the proxy isnt available to address directly (hence the problem in the first place) ssh to the uni_ssh_server and then run nslookup proxy.domain.com and use that ip address

then you can just use the proxy:

localhost:9999 and that will connect to the proxy and let you get to the internet.

---

