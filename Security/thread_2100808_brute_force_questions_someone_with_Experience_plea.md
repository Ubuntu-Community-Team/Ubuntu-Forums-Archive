---
title: "brute force questions someone with Experience please"
date: 2013-01-02
forum: Security
---

### Post by chadk5utc on 2013-01-02
Ok heres the issue I may be bothered for nothing but, I have been getting hits all day from this guy. I have running Apache,ssh,dns with rules and logging for all. fail2ban is not working I believe because I do use keybased login? but real question is, Should I be concerned at all about this? Is this guy wasting his time? I have so far not lost/been down or had any service issues in years. No evidence of breach. I do watch all logs daily.
> 
messages:Jan  2 17:15:24 sshd[23114]: Invalid user 69696969 from 190.24.10.11
messages:Jan  2 17:27:38 sshd[24522]: Invalid user kukuku from 190.24.10.11
messages:Jan  2 17:39:54 sshd[25949]: Invalid user 43021211 from 190.24.10.11
messages:Jan  2 17:52:24 sshd[27498]: Invalid user 2526111 from 190.24.10.11
messages:Jan  2 18:04:54 sshd[28930]: Invalid user r5554r from 190.24.10.11
messages:Jan  2 18:17:34 sshd[30489]: Invalid user 4602079263 from 190.24.10.11
messages:Jan  2 18:30:14 sshd[32050]: Invalid user 1245 from 190.24.10.11
messages:Jan  2 18:42:52 sshd[1050]: Invalid user kingkong from 190.24.10.11
messages:Jan  2 18:55:48 sshd[2731]: Invalid user 0849906062 from 190.24.10.11
messages:Jan  2 19:08:46 sshd[4281]: Invalid user 100186 from 190.24.10.11
I have set iptables rules
> 
BYTEME:/var/log # iptables -L -n | grep 190.24.10.11
DROP       all  --  190.24.10.11         0.0.0.0/0
BYTEME:/var/log # iptables -L -n | grep 190.24.10.8/29
DROP       all  --  190.24.10.8/29       0.0.0.0/0

sshd requires rather large(4096bit)key-based login which requires a passwd and another for su functions. upper/lower/alpha/numeric etc. etc.
whois returns
> 
e-mail:      [email]maria.rodriguezs.proveedor@ETB.COM.CO[/email]
address:     AVENIDA CARACAS, 37-63, ED. ADMINIST
address:     9999 - BOGOTA - CU
 Of course the email bounces(didnt think it would be good)

---

### Post by samiux on 2013-01-02
> **chadk5utc said:**
> Ok heres the issue I may be bothered for nothing but, I have been getting hits all day from this guy. I have running Apache,ssh,dns with rules and logging for all. fail2ban is not working I believe because I do use keybased login? but real question is, Should I be concerned at all about this? Is this guy wasting his time? I have so far not lost/been down or had any service issues in years. No evidence of breach. I do watch all logs daily.

I have set iptables rules

sshd requires rather large(4096bit)key-based login which requires a passwd and another for su functions. upper/lower/alpha/numeric etc. etc.
whois returns
 Of course the email bounces(didnt think it would be good)

Congrats, you are his target!

Be keep in mind that the IP address that he is currently using may not be his real IP address.

He will try his best to break into your system unless he give up.

There may be another way he can get into your system, for example, Apache or the web application.  Please make sure they are safe too.

Samiux

---

### Post by chadk5utc on 2013-01-02
> **samiux said:**
> Congrats, you are his target!

Samiux
Thanks for the reply
I dont mind being chosen once in a while it keeps me on top of things. No other logs showing anything out of the normal traffic. Im guessing a script or something as I know I wouldnt sit that long for nothing.

---

### Post by dodo3773 on 2013-01-02
I would be surprised if this wasn't a bot. Are you using the default ssh port? Change it to something else if you are and restart sshd.

---

### Post by chadk5utc on 2013-01-02
> **dodo3773 said:**
> I would be surprised if this wasn't a bot. Are you using the default ssh port? Change it to something else if you are and restart sshd.

Hi
 Yes I am I did think about changing it some time ago but until now its been unnoticed, if this continues I will go back to my usual port choice which is out of the normal range. I have to say that this is the longest single ip event I think I have found and just raised my concerns making sure I did all I could do if you know what I mean.

---

### Post by dodo3773 on 2013-01-02
> **chadk5utc said:**
> Hi
 Yes I am I did think about changing it some time ago but until now its been unnoticed, if this continues I will go back to my usual port choice which is out of the normal range. I have to say that this is the longest single ip event I think I have found and just raised my concerns making sure I did all I could do if you know what I mean.

Yeah, I figured it was something like this. I am more surprised that it took so long for the bots to start attacking. I remember back within a day of setting up an ssh server login attempts would be around the clock haha. Another thing you can do (just an idea) is use blocklists (pgl, iplist, moblock, etc..). If you are the only one that needs to ssh into this machine you can go as far as block entire countries / the world except your area and just whitelist the ports you don't want to be filtered. Should be as simple as that. I would still change the port though seriously.

---

### Post by chadk5utc on 2013-01-02
> **dodo3773 said:**
> Yeah, I figured it was something like this. I am more surprised that it took so long for the bots to start attacking. I remember back within a day of setting up an ssh server login attempts would be around the clock haha. Another thing you can do (just an idea) is use blocklists (pgl, iplist, moblock, etc..). If you are the only one that needs to ssh into this machine you can go as far as block entire countries / the world except your area and just whitelist the ports you don't want to be filtered. Should be as simple as that. I would still change the port though seriously.

Yes I am the only one that logs in with ssh. Key-based with long username/longer password all the usual for that.In fact the system wont take username/password logins at all. I also have a script that I use when I update my country blocks. When I find a range that I have not previously blocked it gets added and updated. I was a little disappointed that I couldn't get fail2ban running on this box as I have on others.  Default port likely to get changed first thing in the morning.

---

### Post by chadk5utc on 2013-01-02
Thanks all

---

### Post by Ms. Daisy on 2013-01-03
FWIW, I had a ssh honeypot running on a high port for months and got absolutely zero bruteforce attempts. A wise man suggested that if you see attempts on your ssh service running on a random high port, then at least you know you're actually being targeted.

---

### Post by chadk5utc on 2013-01-03
Good advise, just changed my port to high, adjusted firewall. restarted service and viola locked out to funny means I have to go across the room now lol....must have missed something

---

### Post by dodo3773 on 2013-01-03
> **chadk5utc said:**
> Good advise, just changed my port to high, adjusted firewall. restarted service and viola locked out to funny means I have to go across the room now lol....must have missed something

Hahaha. Sounds pretty safe. You can't even get in!

---

### Post by chadk5utc on 2013-01-03
ok that was fun back in now, I think this will be much quieter up hear Thanks again all

---

