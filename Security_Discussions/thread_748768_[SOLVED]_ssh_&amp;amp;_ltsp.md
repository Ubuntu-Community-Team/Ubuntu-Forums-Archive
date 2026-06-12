---
title: "[SOLVED] ssh &amp;amp; ltsp"
date: 2008-04-07
forum: Security Discussions
---

### Post by clarknova on 2008-04-07
So I have an Edubuntu/ltsp/thin-client network and I want to be able to manage the server remotely.

Normally I would enable port-forwarding in the router and use ssh, but leaving ssh open to the world is not really an option, because I don't consider my ltsp users's passwords to be secure.

I tried the AllowUsers option in the ssh config file but discovered that any ltsp user that is denied ssh access is also therefore denied ltsp access.

I tried running dropbear, but dropbear doesn't support the AllowUser option, so even though I can marginally increase security by running dropbear on an obscure random port, all my user logins are still exposed to the world.

Any suggestions?

db

---

### Post by kevdog on 2008-04-07
I take it from your conversation, key based authentication is not what you want.  You may want to put all your individual users in a linux jail to further protect your server, although this is not an absolute security measure.

---

### Post by clarknova on 2008-04-08
I'm not keen on key-based. If I understand it correctly, I would have to carry the key file with me, or on the machines that I connect from. It would never work for me in reality--I'm too mobile and not only would I forget to bring my key everywhere, I would also leave it everywhere I went.

I'm hoping more that somebody can tell me how to run a second instance of ssh server (or an alternative like dropbear) from a second config file to limit access by account.

db

---

### Post by HermanAB on 2008-04-09
You could try disallowing password access to ordinary users and allow it for root, then set a very strong root password of 16 or more characters.  Then you should be able to log in as root for administration, using a password.

---

### Post by clarknova on 2008-04-10
> try disallowing password access to ordinary users

Wouldn't that mean setting up a key for every user? Possible, I guess, just more work, as I have dozens of users, adding more weekly. Might be the only way though, judging by the lack of response.

db

---

### Post by HermanAB on 2008-04-10
Why do you want to give ordinary mortals SSH access?  Likely not a good idea.

---

### Post by clarknova on 2008-04-10
> Why do you want to give ordinary mortals SSH access? Likely not a good idea.

Agreed, but ltsp ("thin") clients connect to the server via ssh by default, via the individual user's account. I think there's a way to disable this security and then I could disable user access via ssh, but to do so without first altering the ltsp connect scheme would be to lock out my users from their computer access altogether.

db

---

### Post by netlogic on 2008-04-11
> **clarknova said:**
> I'm not keen on key-based. If I understand it correctly, I would have to carry the key file with me, or on the machines that I connect from. It would never work for me in reality--I'm too mobile and not only would I forget to bring my key everywhere, I would also leave it everywhere I went.

I'm hoping more that somebody can tell me how to run a second instance of ssh server (or an alternative like dropbear) from a second config file to limit access by account.

db

we have a server that holds ssh keys, things are heavily logged, firewalled, running IDS and maintain its own DNS information. All admins must logon to secure ssh server in order to work on other machines.

---

### Post by clarknova on 2008-04-12
Thanks. I think a dedicated ssh server or gateway is probably the best bet if I can't run two ssh servers on a single machine.

db

---

### Post by netlogic on 2008-04-12
> **clarknova said:**
> Thanks. I think a dedicated ssh server or gateway is probably the best bet if I can't run two ssh servers on a single machine.

db

The centralized security design or pushed configuration design are always a better idea.

---

### Post by HermanAB on 2008-04-12
Hmm, maybe you need a different approach:
You could make sshd listen on multiple ports (just add another one below the default in /etc/ssh/sshd_config and restart it).  Then you can use your firewall (iptables) to only allow the non-standard port for outside access.  You could also set it to only allow incoming connections from one or more specific IP addresses.  That would make things a much more secure without breaking things for the common users.

Cheers,

Herman

---

### Post by clarknova on 2008-04-17
This appears to be what I am looking for. I'll give it a try and post back.

[https://wiki.ubuntu.com/DedicatedLTSPSSH](https://wiki.ubuntu.com/DedicatedLTSPSSH)

---

### Post by clarknova on 2008-06-29
> **clarknova said:**
> This appears to be what I am looking for...
[https://wiki.ubuntu.com/DedicatedLTSPSSH](https://wiki.ubuntu.com/DedicatedLTSPSSH)

Well, it turns out that that link is just a proposal in abstract; basically saying what I said, that somebody should make this happen and package it. So no help there.

I did, however, find the solution on the ltsp mailing list. :)

It's a bit of a lengthy thread, but readable. I may boil it down to a howto when I have some more time.

[http://marc.info/?l=ltsp-discuss&m=120474267903826&w=2](http://marc.info/?l=ltsp-discuss&m=120474267903826&w=2)

db

---

