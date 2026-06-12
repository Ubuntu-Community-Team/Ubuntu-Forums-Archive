---
title: "Webmin question"
date: 2005-05-01
forum: Server Platforms
---

### Post by andbert on 2005-05-01
Ive installed webmin 1200.
Im completely noob regarding this.

I want to access my home computer at work.
Have I undestand it correctly that if I use the link [https://domain:10000/](https://domain:10000/) i will have access when im at work?
Or is it another address?

In that case, do I have set up some kind of server in the webmin interface?
Any input is highly appreciated.

---

### Post by s0c0 on 2005-05-01
I think you are supposed to use [https://localhost:100000](https://localhost:100000) or https://<hostname here>.localhost:10000

Anyways, hope that helps.  Try reading the man page or the documentation that came with webmin.

---

### Post by nemin on 2005-05-03
[QUOTE=andbert]
Have I undestand it correctly that if I use the link [https://domain:10000/](https://domain:10000/) i will have access when im at work?
[/QUOTE]
First, find out wich port webmin is running. Usually this is 10000 indeed, but you can check that by running: ```
netstat -lant
```
Next, you have to find out your public IP address, or if you own a domain you can use that name instead.
When you use a router to access the internet, you usually have to setup "port forwarding" so access from the internet to your home network on a specific port (in case of webmin usually 10000) will be directed to  you webmin server.
Hope this helps:)

---

### Post by andbert on 2005-05-03
Ok. Thats sounds like it can solve my problem. Im behind a NAT router so i guess ill have to forward port 10000 to my computers IP. 

I will give it a try when i get home from work.
Thanks guys :)

---

### Post by s0c0 on 2005-05-03
[QUOTE=andbert]Ok. Thats sounds like it can solve my problem. Im behind a NAT router so i guess ill have to forward port 10000 to my computers IP. 

I will give it a try when i get home from work.
Thanks guys :)[/QUOTE]


Are there any security concerns doing remote administration this way?  I've always just used SSH for remote administration and webmin for local administration.

---

### Post by nemin on 2005-05-03
[QUOTE=s0c0]Are there any security concerns doing remote administration this way?[/QUOTE]When you use SSL encryption, not really in my opinion. Of course you sould use strong passwords and always install the latest versions with security fixes.

---

### Post by andbert on 2005-05-06
It seems like it is like you said, i have to forward some ports.
Have an issue with my ISP on this though, cant remember my username and password  ](*,) 

But thanks alot guys

---

### Post by bazh on 2005-05-06
Speaking as a Linux user of nearly 3 years, do not use webmin unless you are totally uncomfortable using the CLI.

You will have a much better understanding of linux by remote admin'ing it with ssh and cli.

I wasted 2 years using webmin, wish i had stuck to 'learning' linux .

---

### Post by nemin on 2005-05-06
[QUOTE=bazh]Speaking as a Linux user of nearly 3 years, do not use webmin unless you are totally uncomfortable using the CLI.

You will have a much better understanding of linux by remote admin'ing it with ssh and cli.[/QUOTE]Yeah, I agree with that. Though sometimes it's easier to use webmin, since you don't need additional sofware such as a ssh client, besides a web browser.

---

### Post by dewey on 2005-05-07
Compile webmin from source, the one in the repositories doesn't play well with Sudo, last I knew.

---

### Post by saltydog on 2005-05-10
Why do you need sudo for webmin?

---

### Post by nemin on 2005-05-10
[QUOTE=saltydog]Why do you need sudo for webmin?[/QUOTE]I know nothing about sudo&webmin, but I can imagine webmin needs root-access for some operation and can't handle sudo well then.

---

### Post by LordHunter317 on 2005-05-10
**Do NOT use webmin remotely if you're not using a HTTPS connection**

That's a good way to get your system owned.

I wouldn't use webmin at all, but that's just me.  But regardless, you must follow the above, or you will not like the consequences.

---

