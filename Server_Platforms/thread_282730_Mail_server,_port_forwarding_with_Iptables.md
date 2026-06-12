---
title: "Mail server, port forwarding with Iptables"
date: 2006-10-23
forum: Server Platforms
---

### Post by twistedtwig on 2006-10-23
Hi guys and gals,

so i am thinking of setting up (trying to play with) a windows mail server.  never set up a mail server before.  I have a dapper box running dhcp, dns and net etc.  i have a windows 2003 server i am testing things on to get used to windows stuff, AD etc.  so i want to try and use exchange server.  

here comes the question..... how do i do that really???  yes i know i just asked about windows in an ubuntu forum :p... .what i mean is i know i will have to open up port 25 on the linux firewall.  i will have to port forward it to the windows server (no clue on that bit).  is there anything else that needs to be done on the networking / linux side of things or shoudl that send all traffic to the windows machine and allow all mail to be sent out from it?  as default all traffic is let OUT of the network at the mo.  

Also i use php to send automatic emails some times will this need to be changed / updated at all?

thx all

Twiggy


p.s..  I was just thinking on the way to lunch.  could this idea be extended to asp.net.  I want to get into understanding asp like i did with php so i thought maybe i could forward say port 7890 to bobby.  But then i thought this was a bit hacky and thought would a subdomain (virtual host i think its called) do the job?  could i create say windows.example.com and forward the windows subdomain to the other computer?  if so would all traffic then flow nicely between client and server?

thx again

---

### Post by twistedtwig on 2006-10-24
bump... any ideas please guys?

thx

---

### Post by harrysales on 2006-11-14
Put iptables tutorial into google and the top result is pretty comprehensive if a bit confusing. Also fwbuilder is an ubuntu app but I found it more confusing than writing the indiviual rules.

---

