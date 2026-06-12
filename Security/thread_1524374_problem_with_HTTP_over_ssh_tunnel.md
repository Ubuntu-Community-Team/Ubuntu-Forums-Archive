---
title: "problem with HTTP over ssh tunnel"
date: 2010-07-05
forum: Security
---

### Post by kasans on 2010-07-05
Hello, all.

I've got a problem with sending http traffic over ssh tunnel. It makes to reboot to win(
So the topology of my connection is like this:
____________...................._____________________.....___________
|***********|...................|******************|........| customer's   |
|*laptop*****|-->[ip-sec]->| GW to customer net |---->   | Apache srv  |
|10.33.251.7*|.....[cisco ]....| 83.206.87.68 ******|........| 10.84.18.65 |
|_Ubuntu____|....................|___FreeBSD________|........|_Red-Hat___|

I'm trying to open web interface which is on "customer's Apache server" from my "laptop". I have to go through "gateway to cust. net". Besides, this last connection is over cisco ip-sec, but I can successfully open http recourses within this ip-sec tunnel, so I suppose ip-sec has no impact on http and we can forget about it (for now at least).
So to reach Appache srv I make SSH port forwarding for port 80 (and 22), connecting to the "gateway to cust. net", by this:
```
user@user-laptop:~$ sudo ssh -vvv -L 10.33.251.7:22:10.84.18.65:22 -L 10.33.251.7:80:10.84.18.65:80 login@83.206.87.68 -N
```This forwarding gives me reliable SSH connection to the Appache srv (it's linux) that's I can login and use console, but unless I try to use http.
Regardless I connect to console prior or connect to http -the connection behaves weird - web-interface loads particularly and browser "waiting", console works only for output (I can see "top" updates, but can't stop it, even bu ctlr-c).
Please see detailed log in the attachment.

I do hope that someone can help me to make http over ssh works...

---

### Post by teejaybee on 2010-07-05
Possible MTU issue?

---

### Post by kasans on 2010-07-24
sorry, wasn't able to log here this time(
How to check peer settings for MTU?

---

