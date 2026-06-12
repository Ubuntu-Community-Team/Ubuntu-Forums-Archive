---
title: "changing ports.. a good security measure?"
date: 2009-02-02
forum: Security
---

### Post by tednumber8 on 2009-02-02
I've noticed that 1 port needs to be open for me to connect to internet.

Is there a way for me to chnage this port very now and then or is it a safe port?

---

### Post by brian_p on 2009-02-02
> **tednumber8 said:**
> I've noticed that 1 port needs to be open for me to connect to internet.

How did you get to notice this? Detail, please.

---

### Post by kevdog on 2009-02-02
Do they need you to go through a proxy server?

---

### Post by HermanAB on 2009-02-02
You actually need at least two ports: DNS and HTTP.

Most people would want HTTPS too.

Cheers,

Herman

---

### Post by jerome1232 on 2009-02-02
> **tednumber8 said:**
> I've noticed that 1 port needs to be open for me to connect to internet.

Is there a way for me to chnage this port very now and then or is it a safe port?

Are you talking about incoming connections or outgoing, if incoming you shouldn't need any ports open, if outgoing your going to need more than one port.

---

### Post by cjacobsen on 2009-02-02
If you don't run a server you don't need opening any ports.

But if you run some kind of server services and want to allow external connections you need to open ports and in some cases changing from a default port could be one of your security measures. Like changing the SSH port from the default port 22 to lets say 23532 or what ever. 

However you should not use different ports for HTTP and HTTPS.

---

### Post by Nepherte on 2009-02-02
To connect to the internet you need a couple of ports opened for *outgoing* connections. The minimum ports you need to open are 53 (dns) and http (80) as HermanAB pointed out. On ubuntu, all outgoing ports are opened so no need to do something here. You can't change these ports, you simply have to use the ones the internet serves.

If you are running a web server yourself and you would like it to be accessible for others, you need to open the http port (80) or https (443) for *incoming* connections. You might have to forward these ports from your router if you have one to your server. Again, on ubuntu all ports for incoming connections will be allowed as long as the service is running. No changes are required. The ports your services are using can be changed if you really want to.

In both cases no change should be made.

---

