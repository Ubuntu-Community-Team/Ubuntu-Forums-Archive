---
title: "Using DMZ for webserver with dyndns"
date: 2006-11-21
forum: Server Platforms
---

### Post by meyrd on 2006-11-21
Does everyone find that using the dmz port on the router works better or not using the following:
1. An account with dyndns to use your dynamic ip for a webserver.
2. An lamp installation webserver for http/https/ftp.

If yes, do I still have to forward my port 80/443/20 traffic to the internal ip of the server?
If yes, are there any other changes I should make to the server config because it's in the dmz?

If no, why not?  

Thanks for the help......

---

### Post by Eaglejazz on 2006-11-22
Have you tried using [www.zoneedit.com]("http://www.zoneedit.com")? I found this one of the best solutions, plus its free. If not any help disregard!

Eaglejazz

---

### Post by rickyjones on 2006-11-22
DMZ (De Militarized Zone) forwards all ports to that IP address. For safety, I recommend NOT using a DMZ and instead just forwarding the necessary ports to your internal IP. As for Dyndns functionality, all it does is provide domain services (me.ath.cx -> 1.2.3.4). That has nothing to do with what you router/server is doing.

For instance, I have a Dynamic DNS domain name of acrcdsl.ath.cx. This points to my DSL connection for my church. On my LAN, I only have a VPN port open for external connections. What happens from there is of no concern to Dyndns - it just translates names into addresses.

Did this clear it up for you?

---

### Post by meyrd on 2006-11-22
Well,
Actually I just was curious if everyone finds that using the dmz connection for an apache webserver works better than port forwarding. I'm having some issues with the prot forwarding working all the time.
I can configure my router to accept or deny any services even to the dmz so having the server on the dmz is not an issue.

So I guess from your post you feel that forwarding the port 80 traffic is better than just putting the server in the dmz?

Just trying to see how everyone else does it with the least problems.

---

### Post by Lucho77 on 2006-12-07
> **meyrd said:**
> Well,
Actually I just was curious if everyone finds that using the dmz connection for an apache webserver works better than port forwarding. I'm having some issues with the prot forwarding working all the time.
I can configure my router to accept or deny any services even to the dmz so having the server on the dmz is not an issue.

So I guess from your post you feel that forwarding the port 80 traffic is better than just putting the server in the dmz?

Just trying to see how everyone else does it with the least problems.

In my case, I use 'Virtual Server HTTP' in my router, and 'DynDns' domain name, it works just fine.

---

