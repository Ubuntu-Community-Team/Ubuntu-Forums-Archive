---
title: "problem with X server"
date: 2006-08-09
forum: Server Platforms
---

### Post by prani_bobby on 2006-08-09
hello.
its been very good using ubuntu except for one problem.
i generally login to my linux box using the Xwrapper protocol from my lab.
but with ubuntu im unable to do that, as the login screen fails to appear and 
keeps blinking without bringin up the login window.

can anyone help
thnx

---

### Post by scxtt on 2006-08-09
what OS does your lab PC use? -- i don't know anything about Xwrapper, but if it was me and i was stuck using Windows, i'd just d/l putty and realvnc viewer (both standalone, no installs) to connect ... of course if the lab PC uses Linux, you can use SSH/VNC right from them ...

---

### Post by prani_bobby on 2006-08-09
its a IBM thin client system connected to my room pc thru a 100Mbps LAN.
i used to run mandrake and it worked fine. i changed the config to give a text login for remote users. it now shows the text login. but when i enter the passowrd, nothin happens. it looks as if its goin to boot but ends up with the text screen again.

i use the command

Xwrapper -query <ip> :2


i tried this frm my box(but not outside) to check
Xnest -query 127.0.0.1 :2
and it works just fine.

this also works fine frm my box but not from outside
X -query 127.0.0.1 :2

please help!!!

---

### Post by scxtt on 2006-08-09
i don't know anything about Xnest/Xwrapper -- i've always used vncserver/vncviewer and ssh on both Windows and unix/linux ...

my recommendation would be to try and get them on your IBM thin-client ...

---

### Post by prani_bobby on 2006-08-10
cant do that. i dont have root permissions to install the vnc viewer there. 
any idea how to make my Xserver get connected to the client there?
thnx

---

### Post by prani_bobby on 2006-08-10
hi i found this but donno where to find the security/Disallow settings.
i think this is what preventing me from connection to my Xserver.

## Note:
# is your X server not listening to TCP requests?  Perhaps you should look at
# the security/DisallowTCP setting!

---

