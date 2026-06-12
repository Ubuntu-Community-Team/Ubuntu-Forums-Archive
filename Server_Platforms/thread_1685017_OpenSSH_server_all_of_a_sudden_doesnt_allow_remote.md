---
title: "OpenSSH server all of a sudden doesnt allow remote logins wtf"
date: 2011-02-10
forum: Server Platforms
---

### Post by thefix0r on 2011-02-10
Ive got a small server ive had running for months, all of a sudden it will not allow remote logins, I can login from my local network just fine, but the box will just say "Access Denied" when I try to login from across the internet, nothings changed on the box, at least I didnt change anything. And nothing on the lan has changed, port forwardings still properly setup, static ips, ect.

No idea why this is happening, I checked etc/hosts.deny and its clear, I do not have denyhosts installed.

Any help would be great, thank you!

---

### Post by rudelgurke on 2011-02-10
So it worked before and now it doesn't ?

Do your logfiles say anything ? And can you build a successful from the internet to your SSH server (e.g. by running telnet your_hostname your_ssh_port) ?

If the last fails, there's something wrong with the routing and it's impossible to access the server or at least the port where SSH is running from the internet.

---

### Post by jbrown96 on 2011-02-10
Post ```
ssh -v HOST
``` Your port forwarding rules probably aren't working on your router. 

Do you get a "Connection refused" error?

---

### Post by elico on 2011-02-10
is this box sitting behind a router/firewall?
try to telnet from the internet to the machine on the ssh port and see what you are getting.
you should get some openssh header on the telnet and if you dont that means its a network\firewall issu.

---

### Post by thefix0r on 2011-02-10
Ok guys, there is NO problem with the port, I can open ssh from a remote machine across the internet and I get the user login and password prompt, it just says Access Denied I dont know what happened, it was working fine until some time last week I guess, I have users that were complaining, I juse assumed they forgot their passwords or someone was trying to SE me to get me to change passwords, so I logged into an rdp and checked it out, sure enough, cannot login at all, 
"Access Denied"

Almost as if I had  put in the wrong password. 

Of course logging in from the lan is no problem, so, for some reason my box is basically not allowing internet computers to login. Once again, there is nothing wrong with my Nat configuration and the host is 100% reachable.

---

### Post by kkoffler on 2012-09-19
I'm having the same problem...any word on how to resolve this problem?

---

### Post by darkod on 2012-09-19
That thread is year and a half old, and since it doesn't include a solution anyway, it makes no sense to post there.

Create new thread with your issue.

Did you confirm you can see the ssh service listening with telnet?

---

### Post by kkoffler on 2012-09-19
Ok I will open a new request as you asked....yes I verified that ssh was installed and port 22 is open.

---

### Post by darkod on 2012-09-19
> **kkoffler said:**
> Ok I will open a new request as you asked....yes I verified that ssh was installed and port 22 is open.

That's not the same. The service running on the server has nothing to do with testing with telnet if you can see it from another location. We can continue the discussion in the new thread.

On linux, the telnet test would be something like:
telnet <server ip> 22

It should say something like Listening...

---

