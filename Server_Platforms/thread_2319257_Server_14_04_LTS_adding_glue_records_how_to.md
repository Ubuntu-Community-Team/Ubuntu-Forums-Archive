---
title: "Server 14 04 LTS adding glue records how to"
date: 2016-04-02
forum: Server Platforms
---

### Post by Grupo_na_Hora on 2016-04-02
Hi,

i shifted from a regular vps with 2 ip's to a cloud vps with just one
i already added A records to point the ns1 and ns2 to the same IP
[FONT=Verdana]
On namecheap I added
ns1 | xx.xx.xxx.36 | A record[/FONT]
[FONT=Verdana]ns2 | xx.xx.xxx.36 | A record

Now they tell me i need to glue them in my server and i don't know the commands and how to
Sorry this is perhaps a very dumb question but i am a designer 

TIA for the help you can assist me with[/FONT]

---

### Post by darkod on 2016-04-02
Are you using the namecheap DNS or not?

I am confused. I thought you are saying that you are running your own DNS on one VPS, compared to running it on two VPSs earlier. But regardless of the number of VPSs, if you are running your own DNS you do not create A records on namecheap (which I assume is the registrar of the domain).

On the registrar you only set the primary and secondary DNS server to be used for that domain. I am not sure if their system will allow you using the same IP/server both as primary and secondary.

Then on your DNS you set up the zone file for the domain, and according to the definition of glue records here [https://www.howtoforge.com/troubleshooting-common-dns-misconfiguration-errors#i-glue-records](https://www.howtoforge.com/troubleshooting-common-dns-misconfiguration-errors#i-glue-records), that only means to create A records for the nameservers pointing to the IP. Like in their example having the A records for ns1 and ns2. That should be glueing them...

PS. If you have the option to use the DNS of namecheap better use that instead of your own single DNS. Namecheap will have more than one server which is complying with RFC directives to have at least two nameservers in case one goes down. You also save yourself from configuring and maintaining your own DNS setup especially if you are not too familiar with that.

---

### Post by Grupo_na_Hora on 2016-04-03
Hi Darko.

thanks first of all for replying

Yes i am yet in namecheap and contacted them to help me fix the dns on their side

[https://i.imgsafe.org/101a304.png](https://i.imgsafe.org/101a304.png)
[https://i.imgsafe.org/1303b67.png](https://i.imgsafe.org/1303b67.png)

@ Dig on google toolbox Dig all seems fine

Now i need to configure the dns on my side?

Here's the current config, yet no open ports
[https://i.imgsafe.org/15d7a79.png](https://i.imgsafe.org/15d7a79.png)

i am following a tut @ [https://deliciousbrains.com/hosting-wordpress-setup-secure-virtual-server/](https://deliciousbrains.com/hosting-wordpress-setup-secure-virtual-server/)
but i need to tweak it since i want to install and learn Plesk to manage it.

If you can share please your thoughts on the config.

You are right i am not familiar but now it's a undertaking &#8230; do what&#8230; i need to learn the basics...

Thanks
Humberto

---

### Post by darkod on 2016-04-03
Well, the DNS record look ok and you also say dig tests are successful. That part looks set up correctly.

Now you should be able to access the machine with something like 'ssh [email]root@cloud.mydomain.com[/email]' using your own domain name.

If you want to set up the full FQDN in /etc/hosts then you have to modify the line to something like:
```
89.x.x.36   cloud.mydomain.com   cloud
```

After that reboot the server. You can check the full FQDN with:
```
hostname -f
```

That should be all for the DNS and the hostname part.

---

### Post by Graham_Willis on 2016-04-05
There is something that I don't understand. Grupo_na_Hora, in the first screen where you chose the nameserver handling your domain (Namecheap BasicDNS) did you also put IP of your VPS? To me, what I see is confusing because as far as I can understand you delegated the domain xxxxxxxxxx.com to your own nameserver which runs on your VPS. If that is the case glue records had to be created at nameservers of .com domain in order to avoid circular dependency. But is Namecheap BasicDNS your VPS? I suppose that it is a nameserver of your hosting provider. Is 89.xxx.yyy.36 the address of your VPS?

---

