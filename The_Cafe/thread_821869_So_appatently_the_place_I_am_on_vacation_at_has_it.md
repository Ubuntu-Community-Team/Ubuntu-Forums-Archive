---
title: "So appatently the place I am on vacation at has its own proxy..."
date: 2008-06-07
forum: The Cafe
---

### Post by Lord Xeb on 2008-06-07
That isn't good because now they are tracking me... I am a paranoid person and I do not like my tracks being traced around. HELP ME!!!!

---

### Post by p_quarles on 2008-06-07
It's kind of difficult to avoid being tracked while using a network that you don't own. The only option that I know of would be Tor.

---

### Post by issih on 2008-06-07
Leave a computer on at home, set up a ddns system, then ssh into that box and do everything via vnc :)

Nicely encrypted all the way through the evil nasty proxy.

Obviously this requires another pc which is left on all the time (or at least has wake on lan working) a well configured router, ddns, patience in setting it all up and tolerance of the slowness of the whole thing.

I'd have thought you could also set up your box at home to act as a proxy, and then connect to it via ssh. I don't actually know how you'd do that though...I'd have to investigate.

---

### Post by diablo75 on 2008-06-07
> **issih said:**
> Leave a computer on at home, set up a ddns system, then ssh into that box and do everything via vnc :)

Nicely encrypted all the way through the evil nasty proxy.

Obviously this requires another pc which is left on all the time (or at least has wake on lan working) a well configured router, ddns, patience in setting it all up and tolerance of the slowness of the whole thing.

I'd have thought you could also set up your box at home to act as a proxy, and then connect to it via ssh. I don't actually know how you'd do that though...I'd have to investigate.
Where's a guide I can follow for doing this?

---

### Post by issih on 2008-06-07
Don't know of one off the top of my head.

Basic setup though is just to get ddns setup, e.g. go to:

[http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html?gclid=CPjSu--045MCFQpPQgodGGOvzA](http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html?gclid=CPjSu--045MCFQpPQgodGGOvzA)

and register for a free account and set that up as instructed there. They appear to have a linux client to make it all work.

You will probably need to then set up you router to forward incoming ssh traffic to the machine you are going to leave on, I'm not sure about that step though, as I've not played with ddns services myself yet.

Once that all works you should be able to log into the the machine at home from the remote box by typing:

ssh -l <username> <ddnsname>

from there kick off a vnc server on the box at home e.g.:

vncserver -depth 24 -geometry 1265x900

and record the number of the vnc desktop it gives you.

The number of the desktop then becomes the port used. desktop 01 becomes 5901, 23 becomes 5923 etc.

Now log out and ssh back in using port forwarding with something like:

ssh -L 5901:59xx -l <username> <ddnsname>

where the xx is the number of the desktop from above.

then run vncviewer pointing at port 5901 on localhost and enter your password on the remote box.....

Complicated I know.

ONce its up though, you can leave the vncserver running (this is actually pretty easy in hardy, as I believe there is an option to enable it under administration somewhere) and then just login with the final ssh line and fire up vncviewer on the laptop.

Hard to explain it without knowing what level you understand really, basically look into how ssh, vncviewer/server and ddns work and it should become apparent eventually

sorry if thats not much help

---

### Post by Dougie187 on 2008-07-17
I dont know if this is trackable, but you can always use socks 5 and ssh into another computer using
```
ssh -CD *portnumber* user@host
```

Then in the configuration for firefox, in Preferences->Advanced->Network->Settings, just specifiy as your socks 5 stuff 
localhost with port the same as in your ssh.

---

