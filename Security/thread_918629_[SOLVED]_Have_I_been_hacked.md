---
title: "[SOLVED] Have I been hacked ?"
date: 2008-09-13
forum: Security
---

### Post by Kevbert on 2008-09-13
I'm relatively new to network security and have been running 
```
netstat -pant 
```
on my Desktop (running Ubuntu Hardy 64 bit).  I get the following output:
```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:31416           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      -               
tcp        1      0 192.168.0.2:51624       138.37.50.115:80        CLOSE_WAIT  -               
tcp6       0      0 :::2500                 :::*                    LISTEN      -               
tcp6       0      0 :::110                  :::*                    LISTEN      
```
As you can see I get an IP 138.37.50.115.  This occurs continuously (if I run --continuous).  Is this a potential problem ?  I currently have the /etc/network/if-up.d/50firestarter exited with return code 2 bug (which ghas been reported).  I'm considering removing firestarter and [[COLOR="Red"]configuring UFW[/COLOR]]("http://ubuntuforums.org/showthread.php?t=914869") instead.  The IP is for the University of London (according to whois).

---

### Post by eentonig on 2008-09-13
Can't really consider this as being hacked. Seems like your machine is trying to open a webpage (:80) on server hepboinc.ph.qmul.ac.uk (138.37.50.115).

If it's not you doing so, than probably some program is trying to access that server.

---

### Post by Kevbert on 2008-09-13
Thanks for the quick reply.  I wasn't running Firefox or Evolution at the time.  The only thing that was running in the background was BOINC (Seti, Predictor, LHC, malariacontrol.net and rosetta) and Conky weather (XOAP).  When BOINC connects it is identified and uses
```
cp        0      0 127.0.0.1:35159         127.0.0.1:31416         ESTABLISHED 8112/boincmgr
```

---

### Post by The Cog on 2008-09-13
I think it's unlikely that you hvae been hacked, but I don't recognise all those port numbers. If you do **sudo netstat -pant** you will also see the program name and the pid of the process that opens the sockets. This might help figure out what is happening. You can then do **ps -f <pid>** to see the arguments given as the process was launched.

---

### Post by brian_p on 2008-09-13
> **Kevbert said:**
> 

As you can see I get an IP 138.37.50.115.  This occurs continuously (if I run --continuous).  Is this a potential problem ? 

```
man netstat
```

Search for 'CLOSE_WAIT'. Does that help you make up your mind?

---

### Post by EnGorDiaz on 2008-09-13
hmmmm looks like an update server of some kind its an apache server thats for sure

---

### Post by Kevbert on 2008-09-13
> **eentonig said:**
> Can't really consider this as being hacked. Seems like your machine is trying to open a webpage (:80) on server hepboinc.ph.qmul.ac.uk (138.37.50.115).

If it's not you doing so, than probably some program is trying to access that server.

Thanks, how did you get that info ?  I just used whois, in terminal, and it gave me University of London.  It must be one of my boinc projects (but not sure which one). 

> **The Cog said:**
> I think it's unlikely that you hvae been hacked, but I don't recognise all those port numbers. If you do **sudo netstat -pant** you will also see the program name and the pid of the process that opens the sockets. This might help figure out what is happening. You can then do **ps -f <pid>** to see the arguments given as the process was launched.

Thanks.  Sudo seems to give more info, I'll use this in future.

---

### Post by Kevbert on 2008-09-13
Found out what it was LHC@home.  One of their partners is University of London (so my work units must come through them).  Funnily enough there's been a story out today that LHC/CERN were hacked into by some Greek hackers who were trying to prove that the servers were insecure.
I think I can mark this thread as solved.  Thanks for everyone's help.

---

