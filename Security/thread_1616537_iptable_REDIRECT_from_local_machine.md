---
title: "iptable REDIRECT from local machine"
date: 2010-11-08
forum: Security
---

### Post by douglas_slac on 2010-11-08
Ok, so I have a server that is on a high port number, and people want it on port 80.  For root exploit issues people say the server can not run as root.  So to solve things I want to redirect port 80 to a high port number, say 12345 on the machine.  This has been discussed all over the web, so I find I need to do this:

/sbin/iptables -t nat -A PREROUTING -p tcp -d 123.45.67.89 --dport 80 -j REDIRECT --to-ports 12345
/sbin/iptables-save > /etc/sysconfig/iptables

And I do this, an voila things work for the whole world.  All machines in the world can see the server on port 80 on the machine.

Except, on the machine itself.  On the machine 123.45.67.89, I try to get to the server on 123.45.67.89:80, I get a can't connect error.  On the machine if I try 123.45.67.89:12345 I can connect.

What am I doing wrong here?  I don't want localhost network really, I want the ip address and port, but I want the forwarding to work on the local machine.  But it doesn't... anyone have a good idea here?

---

### Post by SeijiSensei on 2010-11-08
Add the identical rule replacing 123.45.67.89 with 127.0.0.1.

---

### Post by douglas_slac on 2010-11-08
Yeah, I already tried that, and it didn't do anything.  Still the same error.

And anyway, I wasn't try to access the server using 127.0.0.1, I was
using 123.45.67.89:80 to access the server, but just on the same machine.

Not sure what I am doing wrong...

---

### Post by SeijiSensei on 2010-11-08
> **douglas_slac said:**
> Ok, so I have a server that is on a high port number, and people want it on port 80.  For root exploit issues people say the server can not run as root.

Apache never runs as the root user.  It starts as root so it can bind to port 80, but then switches to the user called "www-data".  This "user" has very limited privileges.  

I've run Apache for well over a decade on publicly-available servers and haven't had a root exploit in years.  (Even then it was because I hadn't installed a recent security patch.) Given that millions of web servers run Apache every day in this configuration, whatever those "people" might be saying about the possibility of root exploits has little basis in actual experience.

I'd just let Apache run on port 80 and be done with it.

---

### Post by douglas_slac on 2010-11-08
Thanks - but that doesn't help.  I said it is a server, but it is not an apache server.  I've already gone through 6-8 weeks of internal discussion on how I can't run this server as root, I can't go through that discussion again, thats a fight I've already lost...  I'm trying to find a way to win the next battle here... 

Not an apache server, a different server I need to run on port 80 but not have it run as root.

The question is on how to do port forwarding with iptables correctly.

---

### Post by SeijiSensei on 2010-11-08
I suspect the problem is that most firewall rulesets give blanket ACCEPT permissions to the localhost interface that occur prior to the REDIRECT you're trying to accomplish.  So if you're connecting locally, you'll never hit the REDIRECT rule.

Take a look at "sudo iptables -L -nv" and "sudo iptables -t nat -L -nv" and see where the rule(s) concerning the "lo" interface appear.  Perhaps you can move it below the REDIRECT rule.

You might also find some answers at [http://www.netfilter.org/](http://www.netfilter.org/).

---

### Post by bodhi.zazen on 2010-11-08
Add a rule to the OUTPUT chain

```
sudo iptables -t nat -A OUTPUT -d 123.45.6.789 -p tcp --dport 80 -j REDIRECT --to-port 12345
```

If that does not work, you will need to post all your rules for iptables (so we can review them).

I know you are frustrated, but, I suggest an alternate solution. As you are using port 80 I am guessing it is a web server of some kind. Most any web server can be configured to run as non-root.

IMO the security risk is that your server is running as root and, IMO, changing the port adds little to security You are redirecting traffic from port 80 anyways so what is really gained?  any security vulnerability, such a a mysql injection, or what have you, is simply passed to the new port.

What "server" are you running ? If it has to run as root, I would suggest there is very likely a better alternate and again Apache has a very strong security track.

If you need security, I would use Apache + mod_security.

---

### Post by douglas_slac on 2010-11-09
Ooo... thats an idea, thanks!  Good that gives me an idea on what to look for.  Ok, I'll look over the accepts and the order of things.

Yes, I know, I should just run the server as root, yes, I know I am just trying to patch another problem, and creating more problems for myself...  Like I said not a web server, not an apache server.  People have just told me they want it on port 80, and that it can't run as root.  I agree people are crazy, but like I said I lost that fight, and I'm just trying to give people what those people said they need...

Don't think I can post all the rules, those come from lots of other people also, that I can't control.

But, good, got some ideas to look for.  I was getting to the point where I thought I would have to read a book on iptables, and I'm not sure I've got that much time...

---

### Post by douglas_slac on 2010-11-10
Thanks for the help.  I implemented the "OUTPUT" redirect in the nat table, and that seems to have solved the problem.

---

