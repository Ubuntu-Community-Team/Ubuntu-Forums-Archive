---
title: "Setting Up Co.CC Domain Name With Ubuntu?"
date: 2009-12-10
forum: Server Platforms
---

### Post by Tophats on 2009-12-10
Hi,

I'm a bit confused as to how I can point my domain name (tophatsgame.co.cc) to one of my Ubuntu servers on my network? How the heck would I set it up in 9.10?

The server will be running LAMP (Linux, Apache, MySQL)

Any help would be appreciated!

Edit: I would also like to send mail from my server, so that it reads something like: [email]noreply@tophatsgame.co.cc[/email]

Thanks again!


Cheers,

Tophats

---

### Post by munky99999 on 2009-12-10
Well you set it up with the co.cc people. As the ip address your box has. If it's nat'd you need to setup port forwarding at your router.

As for the mail list thing. You set that up with mailman.

---

### Post by Tophats on 2009-12-10
> **munky99999 said:**
> Well you set it up with the co.cc people. As the ip address your box has. If it's nat'd you need to setup port forwarding at your router.

As for the mail list thing. You set that up with mailman.

I'm sorry, but that isn't telling me a whole lot... :(

Can you be more detailed??

---

### Post by JonRohan on 2009-12-10
You'll need to change the DNS settings for your domain to point to your webserver internet IP address. In particular you will need to change the A record for your domain and the MX record. 

You will need to configure you routers NAT settings to allow requests form your internet IP address through to your server on port 80, so:

Internet IP of 80.80.80.80 on port 80 -> go to local IP 192.168.0.1 port 80

Your DNS provider can probably assist you in changing your DNS records. You will kill your domain if this is not setup correctly. 

On the server side you will need LAMP setup (as you've already figured out). See: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Tophats on 2009-12-11
> **JonRohan said:**
> You'll need to change the DNS settings for your domain to point to your webserver internet IP address. In particular you will need to change the A record for your domain and the MX record. 

You will need to configure you routers NAT settings to allow requests form your internet IP address through to your server on port 80, so:

Internet IP of 80.80.80.80 on port 80 -> go to local IP 192.168.0.1 port 80

Your DNS provider can probably assist you in changing your DNS records. You will kill your domain if this is not setup correctly. 

On the server side you will need LAMP setup (as you've already figured out). See: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Thanks a lot! Is there any detailed tutorials on how to do all of this?

---

### Post by erict43 on 2009-12-12
How to do it depends a lot on your ISP and your router.
 
First step, contact your ISP and ask them how to change their DNS records to point to your server.  So that when someone types [www.tophatsgame.co.cc]("http://www.tophatsgame.co.cc") in a web browser, their DNS server will send them to your IP address.  Or when someone sends a mail to [EMAIL="you@tophatsgame.co.cc"]you@tophatsgame.co.cc[/EMAIL], it will know to send email to your IP address.
 
After the DNS records have been changed, you need to configure your router to send traffic from your public IP address to your server on your internal network.  You'll want to look for PAT or Port Address Translation or Port Forwarding options on your router.  Then tell it that anything coming in on ports 80 (http), 443 (https), and 25 (smtp) should be directed to your server.  Usually you select the service or the port number, and then enter the internal IP (usually 192.168.x.x) of your server.
 
Those steps will get the traffic to your server.

---

