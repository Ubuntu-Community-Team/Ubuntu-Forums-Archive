---
title: "Installing X on a VDS"
date: 2008-12-31
forum: Server Platforms
---

### Post by Skyride on 2008-12-31
Hey guys.

Well Ive been using Ubuntu Server on my home servers and a VDS for a while now. However Ive now come across something I can't seem to find out with googling.

Essentially I would like to run a second game server on my VDS. Garrys mod, if you have ever dealt with source-engine servers then you probably know where Im going with this. The problem is that the games programmer was simply too lazy to write linux binaries (while EVERY other game based on the source engine does). However the upside is that it runs perfectly well in WINE. However to use wine, I obviously need X (even though this server is command line only).

The problem I am finding is that the company I rent my VDS from (linode) do not have virtual graphics hardware. I know that you can have X be rendered on CPU and sent via VNC so i would like some help with configuring this. The most tedious part is that I only need this for the initial configuration, the actual server runs entirely in command line. If its of any relevance, I have just had my VDS upgraded to 720MB of RAM to do this and it never went over 320MB previously (with the only significant things installed was another game server and apache with a phpBB forum.

Cheers in advance,
Adam

P.S. Happy New Year (also in advance).

---

### Post by windependence on 2009-01-01
X forwarding maybe? Over ssh? 

Dude, roll your own server. It's easy unless your ISP is a nasty b@st@rd like Comcast. I pay $5 US for a static IP above my normal net access.

-Tim

---

### Post by Skyride on 2009-01-02
Well I did get it to work forwarding over ssh (i presume you mean using the -Y command?).

I would ABSOLUTELY LOVE to be able to run a home server. But I live in the UK where our internet is crap. I have an 7928 d/rate and 448 u/rate. However where I live we will soon be the pilot of 100mbit fibre in the UK so it will depend on the uprate provided by that.

---

