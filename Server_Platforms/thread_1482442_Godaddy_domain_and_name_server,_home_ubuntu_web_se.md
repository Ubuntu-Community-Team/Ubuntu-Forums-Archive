---
title: "Godaddy domain and name server, home ubuntu web server"
date: 2010-05-13
forum: Server Platforms
---

### Post by Tlingit on 2010-05-13
I have everything set up for my web server i can connect to it from anywhere via it's external IP. So i go to godaddy set up custom name servers via my ip looks like this. NS1.mydomain.info.

I don't know what i'm doing wrong i set it up and waited a couple days.

Anyone know what i might be doing wrong?

Thank you.

---

### Post by johngreth on 2010-05-13
Is your server set up as a name server, and did you do anything fancy with the virtual hosts on apache?

---

### Post by cdenley on 2010-05-13
So are you running bind, then using your server as a nameserver? Why not use godaddy's nameserver? What is the domain? If it is mydomain.info, then telling godaddy to use NS1.mydomain.info won't work.

---

### Post by KnottyMars on 2010-05-13
a couple of network things to point out. 

Your domain is setup to use a set or a couple of nameservers, your domain needs to be told which name servers to use. (godaddy, netsol, etc....)

you want your nameserver (which is where the [www.domain.com](www.domain.com) translates to 123.123.123.123) to have the information on where to point to the IP address of your server.

You can use nslookup or some other tool (some are online) that will tell you where [www.domain.com](www.domain.com) is getting its nameserver info. 

You can also tracert the domain and see where it resolves to. If its anywhere other than your IP address for your server. The name server likely has the wrong information in it. 

So the fix would be to change the nameserver information to the correct IP, or point to another set of nameservers that do have the right information. 

Good luck

---

### Post by Tlingit on 2010-05-13
Nope just set it up open the ports allow DMZ through my router let my servers firewall control everything and it's open and looking good through the ip. 


Everything i did for godaddy.

Making name servers through domain manager with my ip address and added the name servers. waited a couple days.

---

### Post by cdenley on 2010-05-13
> **Tlingit said:**
> Everything i did for godaddy.

Making name servers through domain manager with my ip address and added the name servers. waited a couple days.

You're going to need to be a little more specific. What did you configure with godaddy? A records? What did godaddy call the input fields? This would be much easier if you could provide your actual domain.

---

### Post by KnottyMars on 2010-05-13
> **Tlingit said:**
> Nope just set it up open the ports allow DMZ through my router let my servers firewall control everything and it's open and looking good through the ip. 


Everything i did for godaddy.

Making name servers through domain manager with my ip address and added the name servers. waited a couple days.

I think what you did was designate a nameserver in your godaddy account and if you gave it the IP of your webserver, then name requests on your domain name are being checked at your name server for the translation. 

You would either need to install something that can act as a DNS server on that box (not sure if modding the host file would do it) or go into your godaddy account and use their servers and specify the IP address you are using.

EDIT: Sorry I hope Im not confusing this, cdenlys a pro and Ill let him take (hes helped me a few times before) sorry about that

---

### Post by Tlingit on 2010-05-13
> **cdenley said:**
> So are you running bind, then using your server as a nameserver? Why not use godaddy's nameserver? What is the domain? If it is mydomain.info, then telling godaddy to use NS1.mydomain.info won't work.

Okay Yes i have a (domain.info) and i'm using the NS1.domain.info and NS2.domain.info name server with my ip through godaddy. What or where would you suggest if find out about what to do?

I am not running a DNS server, just for what i know a simple apache2 http web server.

---

### Post by Tlingit on 2010-05-13
> **cdenley said:**
> You're going to need to be a little more specific. What did you configure with godaddy? A records? What did godaddy call the input fields? This would be much easier if you could provide your actual domain.

**For Godaddy**
went to domain manager selected provide domain servers and put my host address's in.
From my custom Host option i configured NS1.Charbytes.info and NS2.CharBytes.info with my external IP address.

My domain is [www.charbytes.info](www.charbytes.info).

---

### Post by cdenley on 2010-05-13
> **Tlingit said:**
> **For Godaddy**
went to domain manager selected provide domain servers and put my host address's in.
From my custom Host option i configured NS1.Charbytes.info and NS2.CharBytes.info with my external IP address.

My domain is [www.charbytes.info](www.charbytes.info).

That was not correct. When you select to "provide domain servers", you told it to use your own servers instead of godaddy's. Even if you had your own DNS servers, how is anyone supposed to resolve any of your domains if they can't connect to your DNS server without first resolving NS1.Charbytes.info or NS2.Charbytes.info.

---

### Post by Tlingit on 2010-05-13
> **cdenley said:**
> That was not correct. When you select to "provide domain servers", you told it to use your own servers instead of godaddy's.

Okay I understand, I thought i was just linking my ip address to godaddys domain.

Would you suggest anything?

---

### Post by johngreth on 2010-05-13
change the nameservers back to whatever they were, then go to "Total DNS Control" in the Domain manager and make the @ point to your IP. Then make sure the www host points to @

---

### Post by cdenley on 2010-05-13
> **johngreth said:**
> change the nameservers back to whatever they were

I think they probably were:
NS51.DOMAINCONTROL.COM
NS52.DOMAINCONTROL.COM

If not, and there is no "reset" or anything, call godaddy.

---

### Post by Tlingit on 2010-05-14
Thank All of you for helping my you have solved my problem! And taught me a lot.

---

