---
title: "Security Concern."
date: 2013-01-05
forum: Security
---

### Post by themanwithshoes on 2013-01-05
Hi,

I currently own a gaming server (MInecraft). Someone else hosts it for me. What information could they get or what risk am i at when i connect to the servers control panel externally?

If you need any more information let me know

Thank you

---

### Post by arpanaut on 2013-01-05
If you log on to your control panel with username and a good password you should be fine there.
If you do not trust your hosting provider, move elsewhere.

---

### Post by themanwithshoes on 2013-01-05
> **arpanaut said:**
> If you log on to your control panel with username and a good password you should be fine there.
If you do not trust your hosting provider, move elsewhere.


Ok tell me.. Say if the server hosting company was malicious. what could they get?

Thank you so much for your help

---

### Post by mlentink on 2013-01-05
Don't know much about Minecraft, but probably saved games, additions and that sort of stuff. What's more important: do you use the same username and password anywhere else?

---

### Post by 1clue on 2013-01-05
It's really pretty simple:  They can get what goes through the wire from your box to their box.

They already have your credit card because you pay them for hosting your system, and probably bought whatever box it is with it too.  Since it's a gaming server I doubt there's much more on there to interest them.  If they haven't been sucking extra money out of your account then you're probably fine from the perspective of the hosting company.

IMO you're not at much of a risk.  I would be more worried about an intruder compromising the box with malware, and then attacking your home network from there.

How is your home firewall?  I recommend an appliance-type firewall/router, with everything turned off, and then run your computers inside as though they're unprotected.  I do more than that, but IMO that's the place to start.

---

### Post by arpanaut on 2013-01-05
> Say if the server hosting company was malicious. what could they get?

Actually they would have access to everything, but if they operated in that manner they would not be in business for very long.  Know who you are doing business with.

Most hosting companies are too busy running their business to be nosing into their clients affairs. Plus at a reputable company  it is unethical and grounds for termination for employees to be delving into the clients data. Check the reputation and track record for your provider, if not satisfied, move elsewhere.

---

### Post by themanwithshoes on 2013-01-05
> **arpanaut said:**
> Actually they would have access to everything, but if they operated in that manner they would not be in business for very long.  Know who you are doing business with.

Most hosting companies are too busy running their business to be nosing into their clients affairs. Plus at a reputable company  it is unethical and grounds for termination for employees to be delving into the clients data. Check the reputation and track record for your provider, if not satisfied, move elsewhere.

How would they have access to everything? How would they get passed the 'wire' between me and the server... Another question.. obviously because i am connecting to the server they have my public ip.. I Know that they can get your general location but apparently illegally they can get your full address ?

---

### Post by mlentink on 2013-01-05
> **themanwithshoes said:**
> How would they have access to everything? How would they get passed the 'wire' between me and the server... Another question.. obviously because i am connecting to the server they have my public ip.. I Know that they can get your general location but apparently illegally they can get your full address ?

As was said, they already have your payment details, and I don't know anything about the law in your location, but in most cases that would include your address as well.
What it boils down to: How have you secured your router? With the same username/password as you use to login on your hosted server? If so, better change it immediately. If you have taken the usual precautions, there's not much to worry about.

---

### Post by 1clue on 2013-01-05
What do you mean by "full address?"  Your public IP they can get from the log files, your credit card they have because you pay them, your billing address they have because they use your credit card and you have a contract.  Your money they get because you pay them and they have a contract.  All of that is legal.

If your game requires clients to open a port on a public IP, then you might have a problem if there is an exploit for that game.

The safest way I know is to have multiple firewalls in your home.  One allows access to your "demilitarized zone" which contains your gaming box and anything else you want exposed, and another to a private network which gets access strictly limited.

---

### Post by themanwithshoes on 2013-01-05
Thank you for all your replies. They have no payment info so please dont worry about any of that. The user name and password are totally different and random to anything else. They have no details about me at all (Its hard to explain but just thats how it is :P) Anyway.. if they had my public ip could they find out your home address? Could they have any access to your network info and or files etc...

---

### Post by mlentink on 2013-01-05
> **themanwithshoes said:**
> Thank you for all your replies. They have no payment info so please dont worry about any of that. The user name and password are totally different and random to anything else. They have no details about me at all (Its hard to explain but just thats how it is :P) Anyway.. if they had my public ip could they find out your home address? Could they have any access to your network info and or files etc...

Assuming your external IP-address is one out of the pool of your ISP, they would need to break in at your ISP (literally or digitally) and look up your details. Or if "they" are a government agency with a warrant, your ISP would need to provide them with those details. And then they would need to break through your NAT-firewall to get to your internal network, or, with a second warrant, do a search.

All an extremely hypothetical case, I would say, so don't worry.

---

### Post by 1clue on 2013-01-05
Just to make some of that clearer:
Your ISP DOES have your address, and they log it.  Even if your IP address changes, they keep records based on the mac address of the device (e.g. cable modem) connected, and that was registered to your physical address when you set up the service.  For mobile devices it's the same thing, only it's a specific cellular device. If you leave your wifi unprotected you're legally responsible for anything a "guest" does with it.

Legally, people can't get your physical address from your ISP without a search warrant.  However, that applies to the USA but a significant part of the world cares not one bit for that, and will do what they can to break into your ISP if they have a reason to do so.

I can't imagine a company who would let you host your hardware without money, but whatever.

SOHO (small office, home office) networking gear is not especially good at keeping the bad guys out.  The advantage with them is that they're cheap, and there's not much in the way of utilities to use against the network if they break in.

Best defense is to turn off any feature you're not using, limit configuration to internal physically connected boxes on the same subnet (not through another router) and use really good passwords on every device.  Not the same passwords.  :)

---

### Post by themanwithshoes on 2013-01-05
> **1clue said:**
> Just to make some of that clearer:
Your ISP DOES have your address, and they log it.  Even if your IP address changes, they keep records based on the mac address of the device (e.g. cable modem) connected, and that was registered to your physical address when you set up the service.  For mobile devices it's the same thing, only it's a specific cellular device. If you leave your wifi unprotected you're legally responsible for anything a "guest" does with it.

Legally, people can't get your physical address from your ISP without a search warrant.  However, that applies to the USA but a significant part of the world cares not one bit for that, and will do what they can to break into your ISP if they have a reason to do so.

I can't imagine a company who would let you host your hardware without money, but whatever.

SOHO (small office, home office) networking gear is not especially good at keeping the bad guys out.  The advantage with them is that they're cheap, and there's not much in the way of utilities to use against the network if they break in.

Best defense is to turn off any feature you're not using, limit configuration to internal physically connected boxes on the same subnet (not through another router) and use really good passwords on every device.  Not the same passwords.  :)

Thank you both for your replies you have been so much help. I just have a few more questions and i hope you dont mind.. 

So depending on the 'pool' side of things we have gathered that if someone has your Public iP they cannot get your full address without having authorisation. 

Now.. I connect to the server.. it has a built in control panel GUI. I connect to this panel regularly. As long as i dont download any files am i under any more risk than the others connecting to the server just to play on it.. not control.. Sorry if that doesn't make sense :s

Secondly i connected to the FTP Server a few times using Filezilla. My concern was that by doing this.. even after disconnecting the person would have access to all my files? Is this true.. Or is that just me being stupidly anxious. Is there any risk (As long ,again, as im not downloading any files) of me connecting to the FTP Server.

Thank you so much for your help

---

### Post by uRock on 2013-01-05
Moved to Security Discussions sub-forum.

---

### Post by arpanaut on 2013-01-05
> How would they have access to everything?
I was referring to everything on your hosted server.
Now as far as your personal files on your own computer, pay heed to what the others here are posting.

I guess I misunderstood your original question.

---

