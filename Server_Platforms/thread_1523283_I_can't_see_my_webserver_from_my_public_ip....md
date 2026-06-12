---
title: "I can't see my webserver from my public ip..."
date: 2010-07-03
forum: Server Platforms
---

### Post by redfox1160 on 2010-07-03
I am not sure if this is a problem with my server or my router (port forwarding). I have my server's local ip forwarded on my router on port 80 (UDP and TCP). When I type my public ip into a browser any system on my network, I cannot establish a connection to the server. Thanks for any help.

---

### Post by NullHead on 2010-07-03
It is possible your ISP is blocking port 80. Try connecting via the server's internal IP.

---

### Post by redfox1160 on 2010-07-03
> **NullHead said:**
> It is possible your ISP is blocking port 80. Try connecting via the server's internal IP.
I can connect to it from its local IP address. My ISP is Verizon, if that helps.

---

### Post by redfox1160 on 2010-07-03
> **redfox1160 said:**
> I can connect to it from its local IP address. My ISP is Verizon, if that helps.

Just found out Verizon blocks port 80 on residential lines... any ideas for what I can do with my server now???

---

### Post by NullHead on 2010-07-03
Well, I'd just change the port on apache to 8080 and you'll be good to go. Just point your domain at [http://yourdomain.com:8080](http://yourdomain.com:8080) and you'll be fine.

---

### Post by redfox1160 on 2010-07-03
> **NullHead said:**
> Well, I'd just change the port on apache to 8080 and you'll be good to go. Just point your domain at [http://yourdomain.com:8080](http://yourdomain.com:8080) and you'll be fine.
Am I allowed to do that? What I mean is, will Verizon slow my internet connection, or stop it, if they find out? Thanks.

---

### Post by NullHead on 2010-07-03
I wouldn't expect them to start cutting your service back. If anything they'll just send you a letter telling you to stop hosting a website.

---

### Post by SoFl W on 2010-07-03
If you are going to have several thousand users, and pull down a lot of bandwidth they might notice.
If you are showing pictures of your cat they might not notice.
Remember residential upload (from your server to an outside browser) is slow.

---

### Post by redfox1160 on 2010-07-03
> **NullHead said:**
> Well, I'd just change the port on apache to 8080 and you'll be good to go. Just point your domain at [http://yourdomain.com:8080](http://yourdomain.com:8080) and you'll be fine.

How do I change the port on apache? is that in the apache2.conf file?

---

### Post by NullHead on 2010-07-03
> **redfox1160 said:**
> How do I change the port on apache? is that in the apache2.conf file?

No, do this: ```
sudo nano /etc/apache2/ports.conf
```

Edit lines 8 and 9 to 8080 and restart apache: ```
sudo service apache2 restart
```

---

### Post by redfox1160 on 2010-07-03
> **NullHead said:**
> No, do this: ```
sudo nano /etc/apache2/ports.conf
```

Edit lines 8 and 9 to 8080 and restart apache: ```
sudo service apache2 restart
```

I edited lines 8 and 9 to
```
NameVirtualHost *:8080
Listen 8080
```
and I restarted apache. When I point my browser at my public ip, I still cannot connect.
I did a little bit more searching around and found that verizon blocks port 8080 as well...

---

### Post by NullHead on 2010-07-03
Well sounds like you have a problem there. Might I suggest a $5/mo [fivebean server](http://ubuntuforums.org/showpost.php?p=7088316&postcount=1), or you could change it to a different port of your choosing; like, say, 8800, 8088, 0880 etc. 

Really, it doesn't make a difference what port you use.

---

### Post by dfreer on 2010-07-04
> **redfox1160 said:**
> I am not sure if this is a problem with my server or my router (port forwarding). I have my server's local ip forwarded on my router on port 80 (UDP and TCP). When I type my public ip into a browser any system on my network, I cannot establish a connection to the server. Thanks for any help.

You need to check it from OUTSIDE of the local network. Don't know for sure if it applies here, but when I ran a server from inside my network everyone could see it fine, but I could only see it by using the internal IP and not the external domain name.

I ran my server on Verizon FiOS, and although I had issues with accessing it from port 80 (I actually hit the router IIRC every time even though I disabled remote administration on port 80), port 8080 worked fine.

---

### Post by DJYoshaBYD on 2010-07-04
fios residential service blocks port 80 coming into your network..

really, i have Comcast, and just set up my LAMP server, port forwarded, and its good..

changing the port on the LAN side will do nothing.. its the ISP..

It MAYBE could be blocked at the redback, but more than likely, its blocked using a Shasta type filter.. basically an ISP firewall.. 

hit up your ISP and ask them WTF..

This will tell you if your ISP is blocking port 80 (as long as you actually have port 80 forwarded in your router.. If you dont have the LAN configured for this, then this test will not be accurate.. verify LAN settings, then do this)

**also, port scan your network on port 80 from OUTSIDE THE ISPs NETWORK..If you have, say, verizon, for your ISP, use this command from a DIFFERENT ISP

```
nc -vv yourdomain.com 80
```

obviously, replace "yourdomain.com" with your IP or actual domain name.. it will tell you if it worked.. like so

> ~$ nc -vv yahoo.com 80
Connection to yahoo.com 80 port [tcp/www] succeeded!
^C
~$ 


---

