---
title: "Randomizing ports for services"
date: 2013-08-11
forum: Security
---

### Post by Hungry Man on 2013-08-11
For things like SSH and web services like Apache, how would one randomize the ports they listen on, if it's possible?

---

### Post by Velnias on 2013-08-11
And how you will connect to service with unknown port? by guessing?

And for what purposes?

---

### Post by The Cog on 2013-08-11
Both SSH and Apache are given their port numbers in configuration files. You could write something that re-writes those files before the service launches, but I don't see the point. As Velinas points out, if you don't know which port they're listening on, you're going to have trouble connecting to them.

Again, as Velinas asks, what are you trying to achieve by doing that?

---

### Post by Hungry Man on 2013-08-11
@Velnas,
> [COLOR=#000000]And how you will connect to service with unknown port? by guessing?[/COLOR]

[COLOR=#000000]And for what purposes?[/COLOR]
Well I would know the port, naturally. But an attacker would not, and they would have to scan.

@The Cog,

> [COLOR=#000000]Both SSH and Apache are given their port numbers in configuration files. You could write something that re-writes those files before the service launches, but I don't see the point. As Velinas points out, if you don't know which port they're listening on, you're going to have trouble connecting to them.[/COLOR]
Well for SSH I see no issue as long as I know the port. When I said randomize I worded it poorly, I just mean to change it to a random port, which I will know. Like I said above, it forces a port scan if someone wants to connect to the service.

So for SSH it isn't a problem, because I'm connecting. But if I were to do Apache and host a website would it be an issue? Would I need to do port forwarding at the router or something?

---

### Post by Cheesemill on 2013-08-11
To change the port that SSH listens on just edit the file /etc/ssh/sshd_config and uncomment and edit the Port line from this...
```
# Port 22
```
to this...
```
Port 22222
```

You can use whatever port you want but I find 22222 easy to remember.

For Apache if you change the port number but you would have to tell people what port to connect to, for example [http://example.com:8080](http://example.com:8080).

It is possible to run Apache on a different port and have your router do the forwarding but this would defat the purpose entirely as it would also forward an attackers packets to your non-default port as well.

At the end of the day none of this will make your system more secure. It's just security through obscurity which doesn't make your system harder to crack. The first thing a hacker will do is run a port scan on a machine if they're interested in it. Although there is an argument for changing the SSH port simply to stop your log files getting spammed with failed login attempts from scriptkiddies.

---

### Post by kevdog on 2013-08-11
You can psuedorandomize the port ssh is running on by putting a front end known as a port knocker (fwknop specifically).  Upon receiving a specific knocking sequence, its capable of opening a random port that will then redirect to port 22 for example.  The port it can open for redirection can be randomized.  I've used this method on one of my Linux installs for years, and frankly reviewing the logs have become so boring since I never see any more repeated port attempts on 22 anymore.

---

### Post by Velnias on 2013-08-11
Kevdog's advice is what you need. Still *less noise* related than security.

---

### Post by Hungry Man on 2013-08-11
Changing the port itself itself is security through obscurity, since it can be bruteforced quickly. But that's not the end goal - the end goal is to set up portspoof and an IDS, which will make a random port much for effective by slowing down port scans and detecting suspicious behaviors.

Thanks ofr the info how to do it. Unfortunately, that's what I had thought for Apache, and that's the one that matters. Still, I can make portspoof effective, just not the same way.

---

