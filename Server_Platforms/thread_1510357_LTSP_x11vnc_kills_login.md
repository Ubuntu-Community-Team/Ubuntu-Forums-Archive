---
title: "LTSP x11vnc kills login"
date: 2010-06-15
forum: Server Platforms
---

### Post by Devilheart on 2010-06-15
Hi
the issue is simple: i have a pc which is booting up from network, acts as a ltsp thin client. i can login successfully but when i try to launch x11vnc on boot (so i can use the related feature of thin client manager) I cannot login anymore. after writing the password, the login screen hangs and reloads.

what can i do?

---

### Post by krunge on 2010-06-15
Check /var/log/Xorg.N.log and /var/log/Xorg.N.log.old to see if the X server is crashing (replace "N" with the thin client X DISPLAY number.)

---

### Post by Devilheart on 2010-06-18
there is no crash reported in xorg's logs. it is like if the client does not communicate with the server. there are no useful lines in messages or auth.log and the client first stuck on "verifying password" and then "no response form server". i've followed this guide [https://wiki.edubuntu.org/InstallX11VncOnLtspClients](https://wiki.edubuntu.org/InstallX11VncOnLtspClients)

one more info: it seems that x11vnc is not starting because it cannot open display :6

---

### Post by krunge on 2010-06-18
> **Devilheart said:**
> 
one more info: it seems that x11vnc is not starting because it cannot open display :6
Is the DISPLAY really :6 ?  (sorry I don't use ltsp)

If you add -o /tmp/x11vnc.log to the x11vnc cmdline it will print everything to that log file.  I suggest reproducing the problem and attaching the logfile to this thread.

---

### Post by Devilheart on 2010-06-18
> **krunge said:**
> Is the DISPLAY really :6 ?  (sorry I don't use ltsp)display number is hardcoded in the init script provided on that page

> If you add -o /tmp/x11vnc.log to the x11vnc cmdline it will print everything to that log file.  I suggest reproducing the problem and attaching the logfile to this thread.very well, i'll try

---

### Post by Devilheart on 2010-06-21
partially solved

1)using -o option solved login problem. i guess x11vnc was constantly writing something and blocking login process

2)i've managed to run x11vnc using xinetd. it works, i can connect using vncviewer but it is not what i wanted. edubuntu howtos show that i can connect via thin client manager but i see no options for this. i guess i need to find a way to start x11vnc in advance and not when an explicit connection attempt is made

---

