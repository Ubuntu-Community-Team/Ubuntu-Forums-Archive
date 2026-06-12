---
title: "[Help] HTTP Server available via lan IP/localhost, but not thru public IP -no/fwall"
date: 2006-08-09
forum: Server Platforms
---

### Post by barrmulio on 2006-08-09
All

I just purchased a domain on RegisterFly and trying to set it up.  I'm on a dynamic IP w/my ISP, and haven't yet dabbled in crontab'ing hitting the http site for auto-updates, so I'm forwarding my domain name to my dyndns site (autoupdated via my dlink di624) to hit my pc.

- On my Dapper pc, I can see my server with [http://localhost](http://localhost) and [http://127.0.0.1](http://127.0.0.1)   
- On other (windows) pcs connected to my router, I can see the server on 192.168.0.102 (so the virtual forwarding is correct)

however, in both cases, when I try to use my server.dyndns.com domain, purchased domain, or my public ip, it keeps trying to find it until a timeout (cannot be found error).

On both my windows and linux pcs, I can ping the domain.dyndns.com and public ip successfully, and everything is pointed in the right direction.

The behavior is typical of a firewall, but I have none.  It must be something I'm overlooking - 

I was starting on this Email Server guide:
[http://flurdy.com/docs/postfix/#ext_reply](http://flurdy.com/docs/postfix/#ext_reply)

(did all the apt-gets but never configured anything - other than php5, apache2 and mysql which I had configured per the ubuntuguide.org site) and then removed everything for a cleaner setup for the domain.  I'm wondering if maybe shorewall left remains after the apt-get remove

I don't have much on the server, so I wouldn't mind clearing all settings, dumping the tables, etc - but would prefer to not need to format my entire system

thanks in advance

---

### Post by chrisfay on 2006-08-09
What port are you running apache on? If 80 doesn't work, try using something else like 8080 as your ISP may be blocking it. I was helping someone else out and found that even 8080 had been blocked by the ISP. He used port 423 and it worked...??

If you change the ports, make sure and update the correct port in apache's ports.conf listen option, any router that you are using, and in your dynamic dns service or it won't route correctly. 

Then just type "yourdomain.com:8080" (or just "yourdomain.com" if you updated the port in your dynamic dns service) and it should work.

---

### Post by barrmulio on 2006-08-09
Thanks for the quick feedback

I'm running on 80, which isn't blocked by my ISP.  I've successfully run pubilic servers on this ISP and machine prior to a recent format to try out Windows SBS 2K3 and SLED, before coming back to Ubuntu. 

Nonetheless, I tried to the port changes, in both the router and ports.conf file through the public ip address (to aovid dns issues) to no avail

---

### Post by chrisfay on 2006-08-09
Are you sure your ports are actally open?

In a terminal prompt run:

```
nmap "ip"
```

To test and make sure your router is still opening them correctly. If you don't have nmap, just sudo apt-get install nmap will do it. 

If they are open, it sounds like maybe an issue in your apache config file; or /etc/hosts.

---

### Post by barrmulio on 2006-08-09
> **chrisfay said:**
> 
If they are open, it sounds like maybe an issue in your apache config file; or /etc/hosts.

I was getting errors with nmap, I dumped my apache config files and the hosts file, had them rebuilt from scratch and that solved it, must have been when toying with them for the email servers.

Thanks again for the help - issue resolved!

---

