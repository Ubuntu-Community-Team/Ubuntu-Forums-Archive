---
title: "Kubuntu Kfrb connections"
date: 2007-03-13
forum: Server Platforms
---

### Post by jonez34 on 2007-03-13
Good day:

I have Kubuntu Edgy installed with Kfrb running so that I can connect to the machine remotley.  I have it setup to allow uninvited connections, not to announce on the network, not to ask before allowing the connection and I have a password on all connections.  I was just surfing when the message "The remote user has closed the connection".  I get this when I disconnect from VNC but I was not connected and I thought that no one else was either.  Should I be worried.  Has anyone else ever heard of this happening?  Is it a bug, I didn't see the connection message that pops up when someone connects but I wasn't sitting in front of the machine the whole time and I didn't take a close look when I returned to the machine to see if the tray icon was there to signifiy that someone was connected.  Is the password for krfb hard to break ( I realize that if I use a sucky password then it will be easier).  It gives me the creeps knowing that someone was watching me surf the internet.

Thanks in advance.

---

### Post by nyvalbanat on 2007-03-13
I'm by no means an expert but I happily use the KDE remote desktop daily. Some thoughts:

   - I think the error message probably just confirms that you disconnected; what can I say, use a good password and be security-concious
   - sometimes I lose the connection with krfb still running and not allowing new connections; I ssh into the box and kill krfb
   - krfb is very cpu-hungry; I get much better performance through vnc; run x11vnc -usepw -forever in an active KDE session, and you won't see the difference (except, of course, better performance); x11vnc may come up on a different port if the KDE one is still running - check startup messages; the password will be the same due to -usepw

Have fun!

---

### Post by frafu on 2007-03-14
Hello, 

I have moved this thread to the "Severs & Security" forum, where it is more appropriate.

Have a nice day. 

Francesco

---

### Post by GliderMike on 2007-03-31
I have the same issue on mine.  I was concerned and have started running some sniffs to see if I could glean any info.  It seemed unlikely that these are actual connections, I think it is a bug.  None the less, I'm going to keep sniffing until I see it again and see if anything comes up.

---

