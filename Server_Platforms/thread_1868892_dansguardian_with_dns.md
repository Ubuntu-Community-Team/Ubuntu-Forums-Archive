---
title: "dansguardian with dns"
date: 2011-10-25
forum: Server Platforms
---

### Post by Rakeshvijayan on 2011-10-25
Hi am new in using dansguardian .I need to learn first ,I am not installed dansguardian  on my server.I  am using 11.04 ubutnu is  my server .I have some questions 
1) Is it possible to install  and configuring dansguardian on my flavor of ubuntu ?
2) Dns Is working on this server ,and have only one lan card ,do it possible   to implement the filtering though this dns server ,all my client system  depends on the dns  server for Internet 

your valuable information can help me to implement filtering on my server ,please post your suggestions 


Thanks have nine day

---

### Post by a2j on 2011-10-25
last year I have setup squid/dansguardian/dns/dhcp on 10.04LTS server. still works great.

---

### Post by vasile002 on 2011-10-25
yes, dansguardian is available for ubuntu:
```

root@izghitu:~# apt-cache search dansguardian
dansguardian - Web content filtering

```

the filtering can rely on any dns server that is set up in /etc/resolv.conf as long as it is working fine.

---

### Post by Rakeshvijayan on 2011-10-26
> **vasile002 said:**
> 
the filtering can rely on any dns server that is set up in /etc/resolv.conf as long as it is working fine.

great will u explain it how to install and configure ,this is  an urgent requirement for me:)

---

### Post by collisionystm on 2011-10-26
How many computers are you trying to filter with DansGuardian?

---

### Post by Rakeshvijayan on 2011-10-27
> **collisionystm said:**
> How many computers are you trying to filter with DansGuardian?

14 systems are under on my dns server .I need to filter all client pc .dansguardian installation on each pc is difficult ,thats y am asking to you my friends .....

---

### Post by LtPitt on 2011-10-27
If you want to do things right, add more security and learn a little linux you should setup a proxy server and dansguardian.

I'd suggest to put the proxy server between your lan and the internet and force all clients to pass through it to get on the internet.

Another (very simple) way to filter traffic - which you can add to your proxy and dansguardian configuration too but it'll work even on its own - would be to use as only dns for your network opendns (search it on google, open an account and live happy) :)

---

### Post by Rakeshvijayan on 2011-10-27
> **LtPitt said:**
> If you want to do things right, add more security and learn a little linux you should setup a proxy server and dansguardian.




I want to learn, you are right I dont know linux if you know this topic please give me a configuration note here , currently I setup dansguardian on server and tested on same system works fine . I need  to know how its works on client system..?

---

### Post by koenn on 2011-10-27
if you have dansguardian working fine, as you say you have, 
als you have to do is
set up the clients to use your dansguardian as a proxy (browser proxy, system proxy, etc).
The address is the name or address of the server, the port is 8080 by default, iirc

---

### Post by Rakeshvijayan on 2011-10-28
thanks for good advice .

I have a one doubt remaining is it  possible to configure dansguardian with dns port on my server

---

### Post by LtPitt on 2011-10-28
If you find things difficult I can also suggest to use Webmin to manage your server easily from a web interface (there you can find easy and comfortable graphical tools to change things in your text config files).

Once done your job can dig into the command line and check the config file and see what webmin did for you.
Comment it, modify it and keep on learning :)


If I was in your shoes I'd setup squid (proxy server) on port 3128 and point all your clients' proxy (you can find it in network preferences of any browser: firefox, chrome, explorer) to youserverip and port 3128.
If you need help to do squid configuration (check your squid.conf file: it's very well commented and maybe you can do on your own) there is a LOT of good documentation online ([http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html](http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html))

If you still have problems please wait for me to get back to work on monday and I'll send you my config :)

---

### Post by Rakeshvijayan on 2011-10-28
> **LtPitt said:**
> 
If you still have problems please wait for me to get back to work on monday and I'll send you my config :)

Thanks for this words ,yes I need it because its a new thing for me and other bigners ,now my dansguardin works fine ,,,,,I will post all of my configuration here on Monday .I did only simple steps for configuring but I don't know how it make log and where i can  see the log.?.

---

### Post by Rakeshvijayan on 2011-10-31
hi friends I need your guide please , How can i log all hit on dansguardian 
Thanks

---

### Post by Rakeshvijayan on 2011-11-02
[QUOTE=Rakeshvijayan];11412040, How can i log all hit on dansguardian 
Thanks[/QUOTE]
do it possible to log

---

### Post by Rakeshvijayan on 2011-11-05
I can able to view the log using webmin. how can i see logs through the terminal

---

