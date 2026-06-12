---
title: "having trouble with external access - apache n00b"
date: 2006-01-30
forum: Server Platforms
---

### Post by Daboo on 2006-01-30
I've googled and wikied, but I'm not sure what to do here..

I've got apache and subversion up and running locally. The problem is I don't know how to access my server from outside my network. I don't have a router, just a switch. 

ifconfig -a tells me my ip is 10.38.232.6, and I can get to my server fine via [http://10.38.232.6](http://10.38.232.6). First of all what is this ip if I don't have a router? [http://www.canyouseeme.org/](http://www.canyouseeme.org/) tells me my actual ip is  63.215.133.xx, and that port 80 is not blocked by my ISP. 

However trying [http://63.215.133.xx](http://63.215.133.xx) doesn't work. How do I configure apache so I can access this ip?

---

### Post by Daboo on 2006-01-31
Ok, I should also add that I have a broadband over powerline service. I guess the modem is assigning me that first IP?

---

### Post by herrpoon on 2006-01-31
[QUOTE=Daboo]I've googled and wikied, but I'm not sure what to do here..

I've got apache and subversion up and running locally. The problem is I don't know how to access my server from outside my network. I don't have a router, just a switch. 

ifconfig -a tells me my ip is 10.38.232.6, and I can get to my server fine via [http://10.38.232.6](http://10.38.232.6). First of all what is this ip if I don't have a router? [http://www.canyouseeme.org/](http://www.canyouseeme.org/) tells me my actual ip is  63.215.133.xx, and that port 80 is not blocked by my ISP. 

However trying [http://63.215.133.xx](http://63.215.133.xx) doesn't work. How do I configure apache so I can access this ip?[/QUOTE]

I think this is similar to a problem experienced by another user not too long ago, are you trying to access your external IP on your local machine?

If you are, then that's probably why it's not working for you, the chances are that your webserver is online to the rest of the world already, but to be sure, you need someone outside of your LAN to check, perhaps a friend or PM me with your IP and I can check for you (don't worry, I'm not going to hack your box - I wouldn't have the first idea how! :p).

---

### Post by Daboo on 2006-01-31
herrpoon: you're exactly right. I did see that post, but what got me is that I was testing it from work, which apparently wasn't working for some reason. However, my friends could access it. Any idea why I can't access it from work? No other websites at work are blocked. I've registed a name at dyndns, maybe it will work w/ that...

---

### Post by herrpoon on 2006-01-31
I can't see any reason why you wouldn't be able to access your website from work and for other people to be able to access it without any problems.  

The only thing I can think of is that (this actually happened to me over the weekend) perhaps you were assigned a different IP than the one you had written down or emailed to yourself, because of your computer/modem being restarted.  Suppose that's only possible though, if you have a dynamic IP.....

Do you think something like that could have happened?

Otherwise I'm stumped :-k.

---

### Post by captin_moor on 2007-03-07
> **herrpoon said:**
> I can't see any reason why you wouldn't be able to access your website from work and for other people to be able to access it without any problems.  

The only thing I can think of is that (this actually happened to me over the weekend) perhaps you were assigned a different IP than the one you had written down or emailed to yourself, because of your computer/modem being restarted.  Suppose that's only possible though, if you have a dynamic IP.....

Do you think something like that could have happened?

Otherwise I'm stumped :-k.

Hi there, Herrpoon, that sounds like a very valid options. However I am having the exact same problem and I have a static External IP address. I have run NMAP -P0 on my IP and it has come up that I have port 80 open. How ever when I also try and login from work all I get is the page taking ages and ages and ages to load. Its like its getting a response but cannot display anything. Finally it times out and says server cannot be found. Any ideas guys

---

### Post by Mr. C. on 2007-03-07
> **Daboo said:**
> I've got apache and subversion up and running locally. The problem is I don't know how to access my server from outside my network. I don't have a router, just a switch. 

ifconfig -a tells me my ip is 10.38.232.6, and I can get to my server fine via [http://10.38.232.6](http://10.38.232.6). First of all what is this ip if I don't have a router? [http://www.canyouseeme.org/](http://www.canyouseeme.org/) tells me my actual ip is  63.215.133.xx, and that port 80 is not blocked by my ISP. 

However trying [http://63.215.133.xx](http://63.215.133.xx) doesn't work. How do I configure apache so I can access this ip?

Your LAN IP address is the 10.x.x.x address.  This is a private address, not visible to the internet.

Your 63.xxx address is your WAN addresses, assigned by your ISP.

You will not reach your server via the 63 address internally, because its an external address.

Others must reach you via: 

[http://63.215.133.xx](http://63.215.133.xx) ( or by name if you have a name to go along with that address).

PM me your WAN IP address and I will tell you what I see.

MrC

---

