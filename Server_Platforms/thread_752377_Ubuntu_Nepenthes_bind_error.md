---
title: "Ubuntu Nepenthes bind error"
date: 2008-04-11
forum: Server Platforms
---

### Post by damd79 on 2008-04-11
Hi,
I'm trying to set up Nepenthes honeypot in a VM Ubuntu installation as a way of getting to know Linux. Everything seems to have installed ok and I've altered the nepenthes.conf to bind to 192.168.1.30. However, when I try to sudo nepethes i get the following error:-

[crit net handler] Could not bind socket to Port 25 Address already in use
[crit net handler] Could not init Socket Address already in use
{crit net mgr] Error binding :25 failed

This error occurs around 30 times as it tries to bind to each port (110, 143, 465, etc ,etc)

I've nothing else running. Would you guys have any idea where I've gone wrong?

Thanks in advance for your help.

---

### Post by G4slight$ on 2008-05-07
Did you ever get an answer on this?  I get the same errors --
Thanks -

---

### Post by bryanstein on 2008-05-07
It's from the exim4 MTU running on port 25...if you'd do a portscan(nmap)  you'd see that. Either:

/etc/init.d/exim4 stop

or

apt-get remove exim4

The previous method will work for now, but it might not allow nepenthes to load on startup.

You can also install sysv-rc-conf (apt-get install sysv-rc-conf) to stop exim4 from running the easy way.:guitar:

---

### Post by G4slight$ on 2008-05-30
That exim4 action doesn't work down here in texas -- 
It's gonzo from my ubuntu box and Nepenthes is still punking me with
binding errors:

 spam net handler ] <in virtual bool nepenthes::TCPSocket::bindPort()>
[ crit net handler ] Could not Bind Socket to Port 3372
Address already in use
[ crit net handler ] ERROR Could not init Socket Address already in use
[ crit net mgr ] ERROR Binding :3372 failed

any other ideas?
Thanks from the crispy state -
tk

---

### Post by bryanstein on 2008-05-30
Well hombre...that method should work anywhere in the Great 48...unless there is something else running on the same port. Did you scan with nmap or run a netsta -an to see what is listening on the same port?

I canned nepenthes because the ssh module is broken in it...you need to run the older versions to get it working. I ran it for a few days and got NO hits...seems the malware could detect it...I didn't even get failed login in attempts.

---

### Post by bryanstein on 2008-05-30
Oh that is something else not exim4...exim runs on 25. 3327 is something totally different...scan with nmap...see what it is, then stop it or configure it to run on a different port while you "play" with nepenthes.

Tell me if you get any results with nepenthes:lolflag:

---

