---
title: "Cannot SSH with Ubuntu, but can with Windows putty?"
date: 2011-03-04
forum: Server Platforms
---

### Post by garfonzo on 2011-03-04
Hey Folks:

I have a Ubuntu server running a website and some other stuff, and I regularly log into it remotely using the Window's program "Putty". I have the server setup to use an abnormal SSH port (not 22) for the "security by obscurity" idea. This login method has been working swimmingly. 

Now, enter Ubuntu desktop.

I installed Ubuntu desktop on one of my spare machines. I popped open a terminal window and tried to SSH into my server:

```
ssh garfonzo@123.456.789.213:1234
```

(obviously fake credentials for this post). 

the output I get is:

```
ssh: Could not resolve hostname 123.456.789.213:1234: Name or service not known
```

I also tried:
```
ssh -l garfonzo 123.456.789.213:1234
```
This produced the same result. 

I can ping my server from the terminal window, so I know it can see it (the Ubuntu desktop and the Ubuntu server are not on the same LAN)

Confused, I opened the "Connect to Server" application from within Ubuntu desktop. I entered the IP address, port, user name and selected "SSH". To my surprise, it connected no problem. 

So, why can't I connect through the terminal using SSH and, how do I get it to work?

---

### Post by HugoSerrano on 2011-03-04
try 

ssh garfonzo@123.456.789.213 -p1234

---

### Post by garfonzo on 2011-03-04
> **HugoSerrano said:**
> try 

ssh garfonzo@123.456.789.213 -p1234

And I'm in!

Thanks!

---

