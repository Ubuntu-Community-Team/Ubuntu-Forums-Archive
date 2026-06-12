---
title: "Test My Web Server - Round One"
date: 2007-05-04
forum: Server Platforms
---

### Post by nomb on 2007-05-04
I got rid of firestarter and used a great thread here on iptables to make my firewall.  I opened port 80 so there shouldn't have been any problems with web.  However at work I can't get to it and I'm thinking it is an actual problem with the web server and not the network I'm on.  In the process of trying to fix this problem, my request is if you have a few free seconds please see if it will load for you.  Then after a few seconds try to load it again.  Also, feel free to do an nmap scan of it if you would like.  (At least for now its ok... :lolflag: )  It would help me a lot to know what other people are seeing.  If you do an nmap scan post it up here and maybe we all could take a look at it.

[www.nombyte.com](www.nombyte.com)

Thanks,

nomb

---

### Post by u_kraze on 2007-05-04
the website is up and running i can see it fine. looks good so far i like the layout and the colours.

---

### Post by nomb on 2007-05-04
Thanks for the result.  We'll see how it goes for everyone else too. :D

---

### Post by useLinux, on 2007-05-04
> **nomb said:**
> I got rid of firestarter and used a great thread here on iptables to make my firewall.  I opened port 80 so there shouldn't have been any problems with web.  However at work I can't get to it and I'm thinking it is an actual problem with the web server and not the network I'm on.  In the process of trying to fix this problem, my request is if you have a few free seconds please see if it will load for you.  Then after a few seconds try to load it again.  Also, feel free to do an nmap scan of it if you would like.  (At least for now its ok... :lolflag: )  It would help me a lot to know what other people are seeing.  If you do an nmap scan post it up here and maybe we all could take a look at it.

[www.nombyte.com](www.nombyte.com)

Thanks,

nomb

Could you tell me this great thread? Please. xD I'm doing something similar to you. Dont want system DoS'ed.

---

### Post by rickyjones on 2007-05-04
Page wouldn't load for me @ 2:53PM Eastern time.

---

### Post by bcmiller on 2007-05-04
> **rickyjones said:**
> Page wouldn't load for me @ 2:53PM Eastern time.


same time here and it worked fine and it's very fast

I have my site hosted with GoDaddy and it takes a year to load...

Can you point me to a tutorial on how to do this using the Desktop install of feisty?

I'd love to start hosting from my home computer

Also, what did you use to make the site?

---

### Post by nomb on 2007-05-04
Thank you rickyjones.  Can anyone nmap it for me?

---

### Post by nomb on 2007-05-04
> **useLinux, said:**
> Could you tell me this great thread? Please. xD I'm doing something similar to you. Dont want system DoS'ed.

Here ya go:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

This is hosted on my howto forums as well lol but atm they are kinda worthless... :D

---

### Post by nomb on 2007-05-04
> **bcmiller said:**
> same time here and it worked fine and it's very fast

I have my site hosted with GoDaddy and it takes a year to load...

Can you point me to a tutorial on how to do this using the Desktop install of feisty?

I'd love to start hosting from my home computer

Also, what did you use to make the site?

Once I can get my firewall issue fixed, (if that is what it is) I will walk you step by step through the process...

---

### Post by u_kraze on 2007-10-27
thanks for the link nomb will look into this

---

### Post by The Tronyx on 2007-10-27
Nmap scan
> 

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-10-27 03:41 CDT
Insufficient responses for TCP sequencing (1), OS detection may be less accurate
Insufficient responses for TCP sequencing (0), OS detection may be less accurate
Insufficient responses for TCP sequencing (0), OS detection may be less accurate
Interesting ports on c-71-62-224-229.hsd1.va.comcast.net (71.62.224.229):
Not shown: 1693 filtered ports
PORT    STATE  SERVICE
21/tcp  open   ftp
22/tcp  open   ssh
80/tcp  open   http
113/tcp closed auth
Device type: broadband router|firewall
Running (JUST GUESSING) : Level One embedded (92%), Panasonic embedded (87%), Fortinet embedded (86%)
Aggressive OS guesses: LevelOne WBR-3403TX Wireless Broadband router (92%), Panasonic IP Technology Broadband Networking Gateway, KX-HGW200 (87%), Fortinet firewall Fortigate 50A (FortiOS V2.80) (86%), Fortinet firewall Fortigate 60 (86%)
No exact OS matches for host (test conditions non-ideal).
Nmap finished: 1 IP address (1 host up) scanned in 56.302 seconds


I'm not sure if I understand this post completely.  Were you looking for information on your security?  I might have some more info on that.  Let me know if you would like me to post it here or PM it to you.

---

