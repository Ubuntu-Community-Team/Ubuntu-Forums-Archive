---
title: "firewalling..."
date: 2006-01-14
forum: Server Platforms
---

### Post by skaboss on 2006-01-14
Hello,

I have some strange issues with my firewall, hope someone will be able to help me :

My configuration : 
I have an ADSL connection, with a simple modem (no router).
I use firestarter.

1/  When i make a scanning at [shields up]("https://www.grc.com/x/ne.dll?bh0bkyd2"), it appears that all service ports are stealth, which seems to be ok, except for port 123 (NTP), which is closed. I don't understand why this port appears as closed, since i didn't make any special rule in firestarter ?

2/ While most are ok, i can't listen to some audio streams (web radios provided by streatuner) : i need to stop firestarter to be able to play them.

Can please somebody help me (i must tell that i'm total noob concerning networking)

Thanks a lot.

---

### Post by greenway on 2006-01-14
Hi there, 

I not quite suire about the first part of your post. What do you mean by "stealth"? Open or closed? Normally in Ubuntu all your ports will be closed unless you configure otherwise (editing IP tables directly or by using a frontend such as firestarter). So port 123 should be closed unless you have opened it by setting a rule in your firewall and letting a server listen on it.

As far as your streams go; this can be solved quite easily: when you notice a stream is being blocked, open firestarter and look at the events tab and find out which port is blocked and then add a policy so this stream can go through.

-mattijs

---

### Post by skaboss on 2006-01-14
> What do you mean by "stealth"? Open or closed
Actually, stealth ports are closed and invisible, for maximum security. AFAIK it means that they don't even respond to unsollicited requests.
Every good firewall will make ports stealth, so i don't understand why my port 123 appears closed.

> As far as your streams go; this can be solved quite easily: when you notice a stream is being blocked, open firestarter and look at the events tab and find out which port is blocked and then add a policy so this stream can go through.

Seems that web radios emitting on port 80 are (logically ) ok. Same for port 8000.
But i can't listen to a station on port 19322. Stations take various ports... Will i have to add one for every radio ? In windows (with kerio firewall), i was able to open every port or range of ports for a specific app. Is the same impossible on Ubuntu ?

By the way, here is the report from shields up : 
```

GRC Port Authority Report created on UTC: 2006-01-14 at 16:09:57

Results from scan of ports: 0-1055

    0 Ports Open
    1 Ports Closed
 1055 Ports Stealth
---------------------
 1056 Ports Tested

NO PORTS were found to be OPEN.

The port found to be CLOSED was: 123

Other than what is listed above, all ports are STEALTH.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.

```

Thanks for your answer.

---

### Post by LordHunter317 on 2006-01-14
> **skaboss]it appears that all service ports are stealth, which seems to be ok, except for port 123 (NTP), which is closed. I don't understand why this port appears as closed, since i didn't make any special rule in firestarter ?[/quote]It's probably intentionally left open by firestarter so things like ntpdate can function at bootup.  At any rate, it's irrelevant.

> 2/ While most are ok, i can't listen to some audio streams (web radios provided by streatuner) : i need to stop firestarter to be able to play them.Unless you're running servers on your machine and don't know how to write iptables rulesets (in which case you should learn) you don't need firestarter and simply should remove it.

[quote=skaboss]Actually, stealth ports are closed and invisible, for maximum security.[/quote]It adds no security.  One could argue it adds less, because then an attacker can clearly tell you're firewalled.  The reality of it is that the port response said:**
> Every good firewall will make ports stealth,No, they don't.

---

### Post by skaboss on 2006-01-14
> you don't need firestarter and simply should remove it
Do you really mean that every ubuntu home station can be ran securely without any firewall ?
I know Linux is supposed to be secure by nature, but i don't know if i should go to this point...:-k

---

### Post by LordHunter317 on 2006-01-14
[QUOTE=skaboss]Do you really mean that every ubuntu home station can be ran securely without any firewall ?[/quote]No.  If you install any sort of server, you *may* need a firewall, depending on what you do.

But out of the box, yes, you don't need one.

---

### Post by skaboss on 2006-01-14
Actually i installed apache2, not for a production site but because i'm doing some server side programming in java, and i also plan to set up a ftp server for friends.
So i'll probably need one.
The problem is that the simple ones (firestarter or guarddog) are messing, and iptables seems far too complicated for me. I also tried shorewall, but i don't even know what to put in zones or interfaces conf files....
Is there a mid solution (or at least a good tutorial *à la* "iptables for dumbers") ?

---

### Post by imagine on 2006-01-14
[QUOTE=skaboss]Actually, stealth ports are closed and invisible, for maximum security. AFAIK it means that they don't even respond to unsollicited requests.
Every good firewall will make ports stealth, so i don't understand why my port 123 appears closed.[/QUOTE]This is what some manufacturers of personal firewalls say, but it's not true.
I'm too lazy to explain, so I'll just post links : )

[http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)
[http://www.iks-jena.de/mitarb/lutz/usenet/Firewall.en.html#Verstecken](http://www.iks-jena.de/mitarb/lutz/usenet/Firewall.en.html#Verstecken)

---

### Post by skaboss on 2006-01-14
Thanks a lot for the links, that's exactly what i need to try and understang something about firewalls

---

### Post by Mr_Grieves on 2006-01-14
Here's a iptables generator, generate a iptables firewall and read thru the script. It helps you understand how it works.

[http://easyfwgen.morizot.net/gen/](http://easyfwgen.morizot.net/gen/)

---

### Post by skaboss on 2006-01-15
Thanks a lot, Mr Grieves !

Indeed that seems to be a great starting point for iptables.
I'm gonna try it !

---

### Post by airtonix on 2006-05-10
I was under the impression that firestarter is only a gui front end for iptables..

So by not having firestarter...it does not mean you have no firewall....only your gui has gone.

or ami under the wrong impression....?

---

### Post by RavenOfOdin on 2006-05-10
Routers work! Get yourself one if you haven't already, and run it with a software firewall.

---

