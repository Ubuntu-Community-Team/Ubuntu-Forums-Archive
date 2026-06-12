---
title: "The Chinese have Taken an Interest in My Server"
date: 2006-12-18
forum: Server Platforms
---

### Post by cgCivie on 2006-12-18
I've been setting up a LAMP development server using Ubuntu 6.06. This server is for a project at work. The server is, thankfully, empty at the moment but it is connected to our outside network and it is configured for remote desktop logins. 

When I came in this morning, there were six windows stating "203.186.92.216 is attempting to login via remote desktop. Refuse | Allow" thankfully I hadn't set it to automatically allow that login. 

What I am wondering now is what can I do to see if he could have worked around that, what would he have had to know to get that far, and what can I do to prevent it? Our government has recently had some trouble with the Chinese trying to gain access to sensitive systems and, while this isn't a sensitive system, it pisses me off that someone is trying to break into it already (2 days old). 

Any ideas?

---

### Post by bmillsap on 2006-12-18
I doubt anyone was targeting you, I keep logs of my dropped packets and I probably get about 20-30 incoming attempts per day on port 5900, which is the default for VNC server and, I think, Ubuntu remote desktop.  That's just going to happen with any server exposed to the internet.  One thing to do would be to change the port the service runs on from the default; although some have the opinion that this doesn't do much, the fact is I never see any general port scanning attempts in my logs, it's always targeted attempts at certain services on their default ports.  Beyond that, if you need the service directly exposed, have a strong password.  If possible, instead use something like ssh or openvpn to establish the connection rather than exposing remote desktop directly to the internet.

---

### Post by cgCivie on 2006-12-18
Alright, I'll go ahead and try that. I don't know that anyone was trying their way in or not but with all the trouble we've had here lately, I wasn't to happy when that IP traced to Hong Kong.

Thank you.

---

### Post by fpois on 2006-12-19
> **cgCivie said:**
> Alright, I'll go ahead and try that. I don't know that anyone was trying their way in or not but with all the trouble we've had here lately, I wasn't to happy when that IP traced to Hong Kong.

Thank you.

Having the IP traced to Hong Kong doesn't really mean much, since real serious attacks are all done thru proxies, which means in this case could be someone anywhere in the world, either connecting to a hosted machine in Hong Kong or gaining control of a machine in Hong Kong, and launching the attack from there, just so that it won't be traced back to where he/she really is, so please don't be too quick to make any judgement on the attacker, especially in a racial way that you did.

I'm not Chinese but I still felt a little annoyed since your content didn't really justify your title.

---

### Post by Stephen_A on 2006-12-19
If you don't mind here is my 2 cents. I've lived in Hong Kong for some years and true, there are some freedom of expression issues in mainland China. Here though, things are still very free and the media openly criticizes the government, which is more than we can say for some countries in the 'free west.' ;-)

---

### Post by bahn on 2006-12-19
> **bmillsap said:**
> I doubt anyone was targeting you, I keep logs of my dropped packets and I probably get about 20-30 incoming attempts per day on port 5900, which is the default for VNC server and, I think, Ubuntu remote desktop.  That's just going to happen with any server exposed to the internet.  One thing to do would be to change the port the service runs on from the default; although some have the opinion that this doesn't do much, the fact is I never see any general port scanning attempts in my logs, it's always targeted attempts at certain services on their default ports.  Beyond that, if you need the service directly exposed, have a strong password.  If possible, instead use something like ssh or openvpn to establish the connection rather than exposing remote desktop directly to the internet.

I have done this both at home and at work. The number of attempt has vastly plumeted.

---

### Post by az on 2006-12-19
> **cgCivie said:**
> 
What I am wondering now is what can I do to see if he could have worked around that, what would he have had to know to get that far, and what can I do to prevent it??

Look in the auth.log to see if anyone successfuly logged in.

To prevent it?  Pick a strong password, use non-standard ports for services you absolutely need and dissable all services you don't.  Use a firewall to prevent any access you don't want.

> **cgCivie said:**
>  it pisses me off that someone is trying to break into it already (2 days old). 

Any ideas?

Get over it.  It's nothing personal.  The internet is big and it is trivial for someone to launch such an attack - it's gonna happen.

---

### Post by zipperback on 2007-01-15
> **azz said:**
> Look in the auth.log to see if anyone successfuly logged in.

To prevent it?  Pick a strong password, use non-standard ports for services you absolutely need and dissable all services you don't.  Use a firewall to prevent any access you don't want.



Get over it.  It's nothing personal.  The internet is big and it is trivial for someone to launch such an attack - it's gonna happen.



Look in your log files and determine the ip addresses of the offending boxes.

Then add them to your iptables configuration and reject the connection with the following:

sudo iptables -A INPUT -s ###.###.###.### -j REJECT


Replace ###.###.###.### with the actual ip address in question.

That will reject all traffic from  the ip address in question. ](*,)

---

### Post by MJN on 2007-01-17
Keep up at the back!
 
No need to do this manually, plenty of programs to automate the process... and in real-time too! (Fail2Ban comes highly recommended)
 
Mathew

---

### Post by Josh1 on 2007-01-17
Where I was working in 2005 they managed both the webserver, the windows 2003 box, the squid server, the mail server and another box or two.

Everything was routed through the linux box and when I checked the logs (and also the current "attacks"/attempted hacking attempts it was amazing.. every second or so it would show someone trying to connect remotely.

Let them be, there will always be some idiot trying to intrude your company network, but there will always be you stopping it. ;)

---

### Post by rolando2424 on 2007-01-18
That ip just tried to acess my remote desktop a few minutes ago...

Good thing I have the "Accept/Reject" Button...

---

### Post by FrankVdb on 2007-01-26
In that case, there is only one conclusion: your burglar is reading this very board. :D 
:guitar:

---

