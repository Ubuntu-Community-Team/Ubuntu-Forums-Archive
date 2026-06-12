---
title: "Lots of Hits on 1433"
date: 2007-08-01
forum: Server Platforms
---

### Post by Raptor45 on 2007-08-01
I've been using Firestarter for some time, and I'm used to seeing the random hit on it blocking something every now and then. However suddenly I've started receiving a whole string of blocked messages, all from the same IP, on port 1433, once every second or two. Should I care? Why might this be?

---

### Post by p_quarles on 2007-08-01
According to Wikipedia, 1433 is the default for Microsoft SQL access, so it doesn't make a lot of sense that someone/thing would be repeatedly trying to access it on a Linux system. 

A couple things: run nmap on your system to make sure that port is actually closed. If it's not, I'd get worried.

Also, I tend to think it's a bad idea to use Firestarter to monitor your network. It runs as root, and has the ability to change firewall rules, so it can be a security risk. Better, imo, to use something like Wireshark or Etherape.

---

### Post by Raptor45 on 2007-08-01
nmap says its closed.

---

### Post by p_quarles on 2007-08-01
Then you should be safe. 

I'm no expert, but I'm guessing this is either a script probing your system, or a MS client that got the wrong IP address for its server somehow. 

If I were you, though, I would also check my router/gateway, just to make sure that this 1433 is closed on those as well.

---

