---
title: "Being disconnected from wireless internet"
date: 2010-06-07
forum: Server Platforms
---

### Post by cliftonbazaar on 2010-06-07
This problem has occurred three times now (I thought it was just me).

My Ubuntu web server is left on all the time, sometimes I notice that it is disconnected from the network so I have to goto the server and re-enter the password in the network connections, this allows me back onto the network.

Why is the server being disconnected? (The computer is running all the time because if it re-starts the terminal window is open on the screen).
And how can I stop it from happening?  It's got to the point where I need to check it every hour which really defeats the purpose of having it!

EDIT: It has happened again 30 minutes after I started this thread.

---

### Post by BobVila on 2010-06-08
What wireless card are you using? I had a similar problem with my RT2860-based wireless card on my desktop. 

Run ```
lspci
``` on the box and post the relevant Network Controller portion. If it turns out that you've got the same card I do, I'll post a walkthrough to build your own drivers from Ralink. 

Aside from drivers, you might also be on a crowded channel - if you're on 6, try moving to 1 or 11... You can use netstumbler or something like that to see what other channels are in use near you if necessary.

---

