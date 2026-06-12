---
title: "Samba Configuration for basic 18.04 &lt;-&gt; Win10 share"
date: 2018-12-30
forum: Server Platforms
---

### Post by JusticeEmpire on 2018-12-30
Hi guys,
I'm in the process of trying to setup a new server, and I'm having some trouble with SAMBA.

I've previously built a server ([https://ubuntuforums.org/showthread.php?t=2339981&page=1](https://ubuntuforums.org/showthread.php?t=2339981&page=1)) and I've been using that as reference material for this build. However, I can't seem to get a basic Samba share to work.

As per the thread, it's probably down to a novice error, but from what I can see, the server should be visible from my windows pc, but it's not showing up so nor is the share.

This is at the end of the /etc/samba/smb.conf

```
[public]
   comment = public anonymous access
   path = /MusketBreweryData
   browseable = yes
   writeable = yes
   read only = no
   guest ok = yes
   public = yes
   create mask = 0777
   directory mask = 0777

```
The workgroup is correct, I have wins support = yes and commented out wins server, I've added netbios name.

What am I doing wrong or what have I missed?

TIA

---

### Post by Morbius1 on 2018-12-30
> but from what I can see, the server should be visible from my windows pc
Not if SMBv1 has been disabled on the client side of the Win10 machine. Network netbios browsing and smbv1 are linked.

What you an do however is access the server explicitly ... as in:
```
\\servername
```
OR
```
\\servername.local
```
OR even:
```
\\server-ip-address
```
You might want to ppost the outoput of the following commands if the above doesn't work:
```
hostname
```
```
testparm -s
```

---

### Post by JusticeEmpire on 2018-12-30
Thanks for the response.

Interestingly, although I tried before with no luck and have rebooted since, I can access the share from explicitly typing the server name in the address bar as you mentioned. 

I didn't have that problem when I built the last one using 16.04, the server appeared on the network without a fuss.

I should probably edit the question, as what you have mentioned did solve my problem, although I would like the server to appear on the Win10 network list. 

Is it just a case of finding & enabling SMBv1 on the windows machine, or is there something else I need to do server side?

---

### Post by Morbius1 on 2018-12-30
Funny you should ask that question on this particular day.

[1] You could change it on the WIn10 systems just make sure you do it on the client side not the server side of Win10.

Control Panel > Programs and Features > Turn Windows features on or off:
[ATTACH=CONFIG]282040[/ATTACH]

[2] OR ... if you are a bit more adventurous you could try what was posted a few hours ago here: [https://ubuntuforums.org/showthread.php?t=2409183](https://ubuntuforums.org/showthread.php?t=2409183)

---

### Post by JusticeEmpire on 2018-12-30
That's odd indeed....

I've turned in on client side, rebooted and it's still not shown up. Still don't understand why the other server was showing up, yet this one isn't. I don't remember stating a netbios name on the previous server, could that be causing the issue?

---

### Post by Morbius1 on 2018-12-30
Well the normal things that would prevent you from browsing ( aside from the smbv1 thing ) for hosts:

** Firewall in the way
** Host / Netbios name longer than 15 characters
** nmbd service not running
** smbd service not running

 would be the same things that would prevent you from accessing the host explicitly by name so that is perplexing.

---

