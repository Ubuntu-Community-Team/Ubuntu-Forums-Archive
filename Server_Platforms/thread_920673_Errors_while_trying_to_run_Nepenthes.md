---
title: "Errors while trying to run Nepenthes"
date: 2008-09-15
forum: Server Platforms
---

### Post by h3llh0l3 on 2008-09-15
Hello all,

I am trying to setup a Low Interaction Honeypot(Testing - its on the LAN) using Nepenthes. When I run the program I get the following errors about the ports being open and hence nepenthes is unable to bind them. I have blocked the ports using IP Tables but still I got the same errors:

[ spam net mgr ] bindTCPSocket 0 25 0 30 8083348
[ spam net handler ] <in virtual bool nepenthes::TCPSocket::bindPort()>
[ crit net handler ] Could not Bind Socket to Port 25
Address already in use
[ crit net handler ] ERROR Could not init Socket Address already in use
[ crit net mgr ] ERROR Binding :25 failed

And its not just the port 25 but it happens with other ports as well.

Please advice what I can do to fix it.

Thanks. :)

---

### Post by sprouty on 2008-09-15
Hi,  could you post the nepenthes log?

Just to give you heads up nepenthes is awesome at catching malware!

---

### Post by h3llh0l3 on 2008-09-15
Hi,

Attached is the log of nepenthes.log & thanks for the heads up :)

---

### Post by h3llh0l3 on 2008-09-15
I have attached the log as requested.

---

### Post by h3llh0l3 on 2008-09-15
Hello,

I was able to fix the issue. I am not sure how exactly this could cause the errors that I was getting and I would love to get an explanation, so this is what I did.

I saw that the nepenthes service was starting at the boot, so I stopped the service by "service nepenthes stop" and executed the following to start nepenthes:

```
nepenthes -u nep_test -g nepenthes
```

This started the nepenthes with no errors about "Error binding to port $$"..

Its currently logging every transaction that happens on any port.
I guess it was lucky shot, but still I would like to know how that could be a problem. 

Thanks. :)

---

### Post by pqrs541 on 2008-09-16
Threats: I'll slap you so hard, your clothes will be outtalk style.[wow gold](http://www.mmoinn.com) This'll jar your preserves. Don't you be making' me open a can o' whoop-*** on yaw! [buy wow gold](http://www.mmoinn.com)[World of warcraft Gold](http://www.mmoinn.com)[cheap wow gold](http://www.mmoinn.com)[power leveling](http://www.mmoinn.com)

---

### Post by sprouty on 2008-09-16
Great Glad to hear you got it up and running!!

Haven't got a clue why that would happen.
Just a quick two quick question wondering if you know the information?

In the log i see file with link:// and blink:// i was wondering if you know what type of vectors these attacks are?

Do you know how to run nepenthes on multiple ips? i think it can be done but have no idea?

Cheers,
Sprouty

---

### Post by h3llh0l3 on 2008-09-17
Ok, I am hit with another road block !!!

What's happening:
=================
When I run nepenthes it binds to all the ports with no errors. And when I try connecting to machine A(running nepenthes) from machine B, nepenthes logs all the details of the machine B.
But the problem is that I am unable to use any service on machine A, as all the ports are bind'd to nepenthes. So when I try accessing a website hosted on machine A from B the website won't load or if I try ftp/smtp, it would fail.

What I would like to do:
========================
I would like to have my servers(web, mail & ftp) running with nepenthes also binding to those ports. How it can be achieved?

I would really appreciate the help.

Thanks :)

---

