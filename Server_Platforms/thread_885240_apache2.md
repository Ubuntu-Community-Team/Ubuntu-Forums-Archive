---
title: "apache2"
date: 2008-08-09
forum: Server Platforms
---

### Post by kennedy7 on 2008-08-09
Ok I have this website that I just posted about a month ago. People that have been on it say it is fast but when I try to get on it from my computer it is slow. Tell me if it fast for you [http://tyspage.doesntexist.com]("http://tyspage.doesntexist.com") . If so why is it faster for others and slow for me?

---

### Post by chickpea on 2008-08-10
it seems to take forever. i can never get your web page loaded. but when i do "nslookup tyspage.doesntexist.com" , i can get your web server's IP address(65.5.187.201). and "ping 65.5.187.201" works as well. so maybe there's something wrong in your apache configuration? how much is the value of "MaxClients" directive?

---

### Post by kennedy7 on 2008-08-10
Yeah I had My laptop off. Im running my webserver from my laptop. But soon ill have a server comp. Try now.

---

### Post by chickpea on 2008-08-10
is your laptop server now being ON? it hasn't responded to me yet...

---

### Post by MJN on 2008-08-10
It doesn't work at all from here...

---

### Post by chickpea on 2008-08-10
maybe your laptop is now turned back OFF. anyway i did visit your website 4 days ago when reading your "apache" thread that announced the launch of your site. i remember it didn't take a long time at that time.

---

### Post by linux_tech on 2008-08-10
I am not able to connect to your website 

nslookup shows 
Server:         68.87.74.162   (comcast)
Address:        68.87.74.162#53 

Non-authoritative answer:
Name:   tyspage.doesntexist.com        ([http://www.dyndns.com](http://www.dyndns.com))
Address: 65.5.187.201   (Bellsouth)

---

### Post by linux_tech on 2008-08-10
Did you deny icmp on any access list?

---

### Post by kennedy7 on 2008-08-10
Ok sorry My wif was disconnected. Now it works. [http://tyspage.doesntexist.com]("http://tyspage.doesntexist.com")
or try this [http://tysite.doesntexist.com]("http://tysite.doesntexist.com").

---

### Post by maxidrom11 on 2008-08-10
It's very slow from here - did you do smth to your htaccess?

---

### Post by MJN on 2008-08-10
> **kennedy7 said:**
> Ok sorry My wif was disconnected. Now it works. [http://tyspage.doesntexist.com](http://tyspage.doesntexist.com)
or try this [http://tysite.doesntexist.com](http://tysite.doesntexist.com).
They point to different IPs (65.5.187.201 and 63.208.196.110) - is this intentional?

Either way I cannot connect to either.

Looking at a packet trace suggests there is significant packet loss somewhere along the way.

Mathew

---

### Post by kennedy7 on 2008-09-10
Ok my server comp is working full time now it works. Thanks for your help.:popcorn:

---

