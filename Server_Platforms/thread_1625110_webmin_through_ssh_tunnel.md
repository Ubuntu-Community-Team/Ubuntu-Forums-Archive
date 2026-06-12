---
title: "webmin through ssh tunnel"
date: 2010-11-18
forum: Server Platforms
---

### Post by corkscrew on 2010-11-18
I'm real new at servers and remote access so please bear with me.

I have installed ubuntu server on a spare box and installed it in my home network which is behind a router.

So far on the LAN i have managed to set up freeNX server on the server and tested access to it from separate machines inside my LAN with nomachine all good.

I can also access to the server with webmin again from inside my LAN. 

I want to be able to access webmin from outside the LAN through a ssh tunnel which I have read is quite secure. I have followed a how to I found on the web on how to do this here 

[http://http://groups.google.com/group/ubuntu-user-community/web/ssh-tunnel-setup-and-configuration-guide]("http://http://groups.google.com/group/ubuntu-user-community/web/ssh-tunnel-setup-and-configuration-guide")

I start a puTTY session log in to the server ok but now what do I do?
If i point browser to webmin ie port 10000 all it does is start webmin on my client pc?

---

### Post by Vegan on 2010-11-18
You will need to allow access from remote to port 10000 so that you can achieve complete remote access.

Make sure your passwords are very strong.

---

### Post by corkscrew on 2010-11-19
sorry I am pretty green at this, how do i do this? at the moment I have my router set to forward port 22 to allow the ssh tunnel

---

### Post by HermanAB on 2010-11-19
Howdy,

You may be re-inventing the wheel there:
[http://www.webmin.com/ssl.html](http://www.webmin.com/ssl.html)

---

### Post by corkscrew on 2010-11-20
Thanks for thst herman, so I guess you are saying dont use ssh tunnel for webmin.

---

### Post by CharlesA on 2010-11-20
> **HermanAB said:**
> Howdy,

You may be re-inventing the wheel there:
[http://www.webmin.com/ssl.html](http://www.webmin.com/ssl.html)

I thought Webmin used SSL by default? I could be wrong, since it's been a while since I've actually used it.

> **corkscrew said:**
> Thanks for thst herman, so I guess you are saying dont use ssh tunnel for webmin.

When I used webmin, I accessed it via an SSH tunnel so I wouldn't have it open to the internet.

Check this page [here]("http://realprogrammers.com/how_to/set_up_an_ssh_tunnel_with_putty.html"), just ignore the part about mysql and point yer browser to localhost:10000

---

### Post by James78 on 2010-11-20
> **CharlesA said:**
> I thought Webmin used SSL by default? I could be wrong, since it's been a while since I've actually used it.
You're right, it does use SSL by default.

Corkskrew: If you're using the default self generated webmin SSL certificate, you should get a non-self signed certificate for your website, and use that instead. Real certificates > self-signed. If you don't want to pay lots of money, you could consider CaCert. They're not in every browser or OS, but they're free, and it's as close as you can get without using a self-signed certificate. Of course, if it's just for a server, and not really a website, you don't really need to bother with a real certificate.

---

### Post by corkscrew on 2010-11-20
> **CharlesA said:**
> I thought Webmin used SSL by default? I could be wrong, since it's been a while since I've actually used it.



When I used webmin, I accessed it via an SSH tunnel so I wouldn't have it open to the internet.

Check this page [here]("http://realprogrammers.com/how_to/set_up_an_ssh_tunnel_with_putty.html"), just ignore the part about mysql and point yer browser to localhost:10000

hi Charles thanks for that I followed the instructions on the link to set up the puTTY session. No problem started session get a cli and manage to log in to my server. Next I open my firefox browser and enter localhost:10000 but the only webmin I get is my local machine not the server. What am i doing wrong?

---

### Post by CharlesA on 2010-11-20
> **corkscrew said:**
> hi Charles thanks for that I followed the instructions on the link to set up the puTTY session. No problem started session get a cli and manage to log in to my server. Next I open my firefox browser and enter localhost:10000 but the only webmin I get is my local machine not the server. What am i doing wrong?
So you are running webmin on the local machine as well?

Change the local port in the SSH tunnel to something like 10001 and try to connect that way.

---

### Post by corkscrew on 2010-11-21
> **CharlesA said:**
> So you are running webmin on the local machine as well?

Change the local port in the SSH tunnel to something like 10001 and try to connect that way.

yes I am running locally as well.

tried changing local port 10 10001, think i'm getting closer, now when i enter this in my browser [HTML]https://localhost:10001[/HTML] i get security cert warnings i accept all of those and then i get this in the browser window [HTML] Error - Access denied for 127.0.0.1[/HTML]

---

### Post by CharlesA on 2010-11-21
What are yer settings for the tunnel, can you post a screenshot?

It should have worked.

---

### Post by corkscrew on 2010-11-21
> **CharlesA said:**
> What are yer settings for the tunnel, can you post a screenshot?

It should have worked.
 here you go

---

### Post by CharlesA on 2010-11-21
That should work, but I'm not sure if running webmin on the localhost of yer local machine is causing a problem.

Use the ip address of the machine that is running webmin instead of 127.0.0.1.

---

### Post by corkscrew on 2010-11-21
> **CharlesA said:**
> So you are running webmin on the local machine as well?

Change the local port in the SSH tunnel to something like 10001 and try to connect that way.

Success!!! thanks very much, i decided to re install my server from scratch had been messing around with too many settings so started with clean slate.

Installed server updated everything then installed webmin.

Set up ssh tunnel with puTTY and used 10001 as local port worked straight away. many many thanks.

The next step is remote desktop I've been messing around with various without a lot of success.

What do you recomend for vnc server and client which I can put thorough ssh tunnel?

---

### Post by CharlesA on 2010-11-21
If you have a GUI on the server, I'd recomment using [NX]("http://www.nomachine.com/select-package.php?os=linux&id=1") to access it.

Otherwise, it's easier to forward X over SSH by running this:

```
ssh -X user@host
```

---

