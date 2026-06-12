---
title: "Weird Question"
date: 2010-02-25
forum: Server Platforms
---

### Post by Booher6194 on 2010-02-25
Hi, I have installed ubuntu server (I think 9.1) and I have it set up to ssh and I'm at my moms house and I can ssh into it from here, I'm repairing my girlfriends dads computer and the computer is at my house hocked up and has realVNC installed on it. My question is, is there anyway to putty in to the server, then vnc the computer. It sounds crazy and I'm not sure if it's possible. I've searched google and haven't found anything about this particular problem.
Thank You
Booher

---

### Post by 2hot6ft2 on 2010-02-25
Just re-read what you're trying to do. I'm not sure but it should be possible. But PuTTy is command line based and VNC is graphical (I believe) so I have my doubts unless there's a command line option for VNC.

---

### Post by noway2 on 2010-02-26
Does your server run a GUI?  If not, there is little point to use a remote desktop program like VNC and you should stay with SSH and Putty.  If you are running a GUI and want to have remove graphical desktops, do a search in the forums for freenx, vnc, ssh and you will find more than you want to know.

---

### Post by tlsarles on 2010-02-26
your question if poorly worded, but if you are saying its like this :

You ---- SSH Server --- VNC Server . Yes, you can use SSH to tunnel through to the VNC server much like a VPN. You'll need to google up a how to on SSH tunneling.

---

### Post by Booher6194 on 2010-02-26
Sorry. My question is, I want to ssh into my server and while in the server, vnc to the other computer on the network.

---

### Post by Booher6194 on 2010-02-26
Just found out how to do it. Thank you tlsarles for saying about tunneling.

Thank you
Booher

---

