---
title: "IPAC-NG help"
date: 2006-07-06
forum: Server Platforms
---

### Post by dccool879 on 2006-07-06
I want to use IPAC-NG to create a graph of my server's bandwidth usage, and put it on my website. I've been using this. So far, i've installed ipac-ng. Now it is time for me to set up rules. (look at defining rules in that link i posted.) I am confused, because i am not forwarding. I am trying to track the servers usage, which is behind a router. It is being forwarded to. So how would i do the rules? Also, i keep iptables alone right?

---

### Post by dccool879 on 2006-07-06
nvm i solved that other stuff, but now i am confused about

Note that ipac-ng needs to be (re-)initialised each time your linux box, or each time you restart iptables.
To achieve this, I added the following lines into the start section of my iptables script:

# initialise ip accounting
/usr/local/sbin/fetchipac -Sv

what is my iptable script?

---

