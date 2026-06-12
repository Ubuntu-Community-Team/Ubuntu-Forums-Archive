---
title: "Nginx responds to http requests only when addressed to IP, not domain"
date: 2014-05-14
forum: Server Platforms
---

### Post by Learningmore on 2014-05-14
I've checked the Server Wiki, searched for other posts related to DNS and Nginx and also checked the server and desktop guides related to web serving but didn't see an answer.

Issue: Web requests for my domain foo.tk (undisclosed to protect the innocent) do not resolve- my browser just spins and spins. I have Ubuntu 14 running NGinx (apache and lighthttpd removed) behind my router with forwarded ports and DNS for my domain pointing to my public IP. I know my ISP probably blocks port 80 so I'm also forwarding 8080.

Requests get to my house: I verified traceroutes from outside my home network correctly resolve to my home's public IP.
```
**TraceRoute from Network-Tools.com to xx.xx.xx.xx [www.domain.tk]**
[TABLE="width: 100%"]
[TR]
[TD="width: 22, align: right"]**Hop**[/TD]
[TD="width: 65, align: right"]**(ms)**[/TD]
[TD="width: 65, align: right"]**(ms)**[/TD]
[TD="width: 65, align: right"]**(ms)**[/TD]
[TD="width: 4"][/TD]
[TD="width: 130"]**     IP Address**[/TD]
[TD]**Host name**[/TD]
[/TR]
[/TABLE]
[TABLE="width: 100%"]
[TR]
[TD="width: 22, align: right"] 1 [/TD]
[TD="width: 65, align: right"]  Timed out [/TD]
[TD="width: 65, align: right"]  305 [/TD]
[TD="width: 65, align: right"]  647 [/TD]
[TD="width: 130"]     8.9.232.73[/TD]
[TD]  xx.xx.xx.ear1.dallas1.level3.net  
[/TD]
[/TR]
[/TABLE]
[TABLE="width: 100%"]
[TR]
[TD="width: 22, align: right"] 2 [/TD]
[TD="width: 65, align: right"]  3 [/TD]
[TD="width: 65, align: right"]  3 [/TD]
[TD="width: 65, align: right"]  4 [/TD]
[TD="width: 130"]     4.68.63.50[/TD]
[TD]  centurylink-level3.dallas3.level3.net  [/TD]
[/TR]
[/TABLE]
[TABLE="width: 100%"]
[TR]
[TD="width: 22, align: right"] 3 [/TD]
[TD="width: 65, align: right"]  Timed out [/TD]
[TD="width: 65, align: right"]  Timed out [/TD]
[TD="width: 65, align: right"]  Timed out [/TD]
[TD="width: 130"]     [/TD]
[TD]   -   [/TD]
[/TR]
[/TABLE]
[TABLE="width: 100%"]
[TR]
[TD="width: 22, align: right"] 4 [/TD]
[TD="width: 65, align: right"]  71 [/TD]
[TD="width: 65, align: right"]  66 [/TD]
[TD="width: 65, align: right"]  64 [/TD]
[TD="width: 130"]     184.99.65.114[/TD]
[TD]  184-99-65-114.boid.qwest.net  [/TD]
[/TR]
[/TABLE]
[TABLE="width: 100%"]
[TR]
[TD="width: 22, align: right"] 5 [/TD]
[TD="width: 65, align: right"]  88 [/TD]
[TD="width: 65, align: right"]  91 [/TD]
[TD="width: 65, align: right"]  92 [/TD]
[TD="width: 130"]     71.209.24.56[/TD]
[TD]  xx.xx.xx.xx.bois.qwest.net  
[/TD]
[/TR]
[/TABLE]
Trace complete


```

I can ping my house: I've verified my public / WAN IP responds to a ping.

NGINX Web Server correctly responds to requests to the assigned IP. Also, on my home network I can browse to 192.168.0.2 and receive a webpage.
```
curl 192.158.0.2
[webpage is correctly displayed]
```

NGINX Web Server does not respond to requests at 2wilson.tk or [www.2wilson.tk:](www.2wilson.tk:)
```
curl domain.tk
response: blank- nothing shows. process just spins.
```

My nginx.conf is as follows:
```
  # LISTEN DIRECTIVES
        listen     127.0.0.1:80;
        listen     localhost:80;

        listen     127.0.0.1:8080;
        listen     localhost:8080;

        #Listen on LAN IP
        listen     192.168.0.2:80;
        listen     192.168.0.2:8080;

      # Listen on WAN IP
        listen     71.209.24.56

        #Listen ports
        listen     80;
        listen     *:80;
        listen     8080;
        listen     *:8080;

        # SERVER NAME DIRECTIVES
        server_name   foo.tk www.foo.tk;

        server_name   *.foo.tk;
        server_name   .foo.tk;

        #No server name listed, so Nginx will serve from IP address
        server_name   "";

```

I've confirmed both ports 80 and 8080 are forwarded from my router to the box's correct IP. 

Are there any tools to see what is happening and pages are not being served when requested on my domain?

---

