---
title: "Very serious looking security problem - think I've been hacked for online crime!!!"
date: 2010-01-05
forum: Security
---

### Post by cornburn on 2010-01-05
I've just got back from holiday to find some very worrying entries on the server. Things didn't seem right and the internet had also managed to break "itself" so I started looking around to see what was up. I noticed that in the internet history there are some very worrying pages that have been visited. Please help someone, I'll copy as much as I can below with times but am using a different machine so ill type out by hand.

20:06 Ubuntu start page visited, then signed up for a google mail account with various pages visited between 20:07 and 20:12. I have the email address registered which does have a name but I guess that it's fake.

2 minutes after signing up for the google email account he logs into paypal, then ebay a minute later, then for 15 minutes there are entries of pages visited at western union, logging in, going through an international money transfer then logging out again.

The installation is pretty new and there shouldn't be any personal information of my own on there. It's also behind a hardware router firewall that deson't seem to have helped. I'm not sure if someone's hacked in to set up this fake account, or whether some innocent person has followed a link or something and all this has been routed through my server.

I'm really concerned as it's obviously some sort of crime and I don't know what to do next about it or who to report it to (apart from my ISP) I don't want to get a knock at the door from the police thinking I'm involved in fraud of some sort! If anyone can tell me where to look for logs or anything to find what has happened please tell me - whoever it was didn't even clear the internet history so I guess they'll have left other traces.

---

### Post by BkkBonanza on 2010-01-05
Some things to clarify: 
What internet history are you taking about? Browsing history in Firefox? 
Do you have remote desktop enabled as server (allowing remote access)? 
If yes, how is it configured regarding passwords and options?
Any other remote access/ VNC apps running? 
While you were gone was physical access available to any other people?
Was the computer powered off or on when you left?

It appears someone did use your computer while gone but without more specifics we can't say yet how that may have occurred. What info is in the /var/log/messages log file during the time frame in question? Not everything but stuff "pam" related, eg.

grep pam /var/log/messages

---

### Post by cornburn on 2010-01-05
Thanks for the reply. var/log/messages doesn't have any info for the problem period at all, neither does messages.1 or older, that period is missing.

The internet history is the browsing history in firefox

Remote access is enabled using the included remote desktop package (which I connect to over VNC). When opening the preferences it says "Your desktop is only reachable over the local network. Others can access your computer using the address 10.0.0.41 or server.local. It's obviously wrong, I'm not sure how they managed to get through the firewall and onto my local network. The server only has an internal IP and the router has no port forwarding set up. Security only had the bottom box ticked (configure network automatically to accept connections), although I usually have to enter the password from the laptop.

There are no other remote apps running

There was definitely no physical access to the machine while we were away and it was turned off. The logs show that whoever it was did all of this the day before we went on holiday while the machine was still turned on, I just didn't notice. It's definitely remote though as it's under my stairs in the house and I can't see my girlfriend's into cybercrime.

I've installed firestarter and added an additional password to the remote desktop prefs on the server but am obviously worried about how they got onto my internal network in the first place - the other machines have far more sensitive data on them. I might have to put a second network card in the server so all internet traffic is routed through the software firewall as well as the hardware one in the router.

---

### Post by Jive Turkey on 2010-01-05
Do yu have WiFi enabled on your router?

---

### Post by BkkBonanza on 2010-01-05
You should test how it behaves when the remote desktop server is enabled and "automatically configure network to accept connections" is checked. I'm not a big user of VNC/Remote Desktop as I usually use ssh for admin work. But it could be that having that option checked causes Pnp to be used to configure a forwarded port on the router to that machine. This is often how it gets done. If you are able to connect to your machine using VNC from outside the LAN then this must be happening because a port has to be forwarded in order to get in.

Another thing is to use a port scanner to check your router from outside and verify that all ports are in fact closed when you think they should be. This place is a popular, well known one to try,

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

It sounds like VNC was used, but if so then the logs should indicate that it was accessed that way. There should be some kind of indicator of source IP address. The fact that the logs haven't been totally wiped for this info shows that whoever did it was likely not too experienced (or bright). You may be able to trace down more info in other logs.

As far as locking down VNC the best way would be to use VNC over top of ssh for security. You have to remember that VNC transfers data "in the clear" and someone listening in could capture login details very easily if they can see that traffic. If you have wifi (without WPA2 mode) on your LAN then that would be dead easy for any hacker. Even if these machines are hard wired any traffic could spill onto wifi if present and not configured optimally.

There are several tutorials around the net about using "ssh tunnels for VNC" - it would be good to get familiar with that. It's fairly easy to set up once you figure it out and it protects you from eavesdropping in most situations.

---

### Post by scottuss on 2010-01-05
Firstly, is the box password protected? If yes, was it a good password? If no to either question, well, you get the point!

Secondly, are you sure it couldn't have been accessed by someone with physical access? I know it looks slightly dodgy, but who is to say that the activity you noticed was illegal? Did you ask your girlfriend about it? It could be legitimate!

---

### Post by BkkBonanza on 2010-01-05
Another thing occurred to me - you might consider being proactive about the breach. If you can get some info together it may be worth notifying Paypal and eBay about the unauthorized use of your machine to register. It could allow them to track down and disable someone before they cause grief. Just because someone registered accounts doesn't mean they have already abused them. They may have done this as a "protective" measure to ensure later they don't get traced. I would be very sure that no one in your house or friends "innocently" used your machine before going this route. But being proactive may stop a problem before it happens and gets traced back to you. Just an idea to think about.

---

### Post by bodhi.zazen on 2010-01-05
> **cornburn said:**
> Thanks for the reply. var/log/messages doesn't have any info for the problem period at all, neither does messages.1 or older, that period is missing.

The internet history is the browsing history in firefox

Remote access is enabled using the included remote desktop package (which I connect to over VNC). When opening the preferences it says "Your desktop is only reachable over the local network. Others can access your computer using the address 10.0.0.41 or server.local. It's obviously wrong, I'm not sure how they managed to get through the firewall and onto my local network. The server only has an internal IP and the router has no port forwarding set up. Security only had the bottom box ticked (configure network automatically to accept connections), although I usually have to enter the password from the laptop.

There are no other remote apps running

There was definitely no physical access to the machine while we were away and it was turned off. The logs show that whoever it was did all of this the day before we went on holiday while the machine was still turned on, I just didn't notice. It's definitely remote though as it's under my stairs in the house and I can't see my girlfriend's into cybercrime.

I've installed firestarter and added an additional password to the remote desktop prefs on the server but am obviously worried about how they got onto my internal network in the first place - the other machines have far more sensitive data on them. I might have to put a second network card in the server so all internet traffic is routed through the software firewall as well as the hardware one in the router.

You were cracked via VNC. This is the most common crack seen on these forums and is due to either using weak or no password.

You can contact the authorities to see if they are interested in examining your system. You should also contact gmail, ebay, etc ...

When they are done I suggest you wipe the HD and re-install.

do not use VNC unless absolutely necessary, and if you use it be sure to use a strong password.

Use ssh and learn to secure your ssh server (you can forward graphical apps over ssh).

---

### Post by pricetech on 2010-01-05
You might want to start by reporting the incident to your ISP.  Their logs might be helpful as well in apprehending the perpetrator.  They should at least be able to suggest who to contact next.

As far as remote access, I suggest you look into NX from nomachine.com.  I use it here and it works like a charm.  It runs over SSH, so it's secure.

Good luck with it.

---

### Post by Lars Noodén on 2010-01-05
> **bodhi.zazen said:**
> 
do not use VNC unless absolutely necessary, and if you use it be sure to use a strong password.

And even then, tunnnel vnc over SSH since vnc's encryption is not as strong as it could be.

---

### Post by scottuss on 2010-01-05
The "authorities", including the ISP will most likely not be interested. There's little evidence of illegal activity with regard to the PayPal / Ebay activity, and if VNC was running and forwarded / allowed through a firewall with no password protection, the "authorities" won't take you seriously.

---

### Post by cornburn on 2010-01-07
Thanks for all the replies. Passwords were set on eveything, including the wireless. Physical security definitely isn't a problem, the server's in a cupboard uder the stairs and I'm sure my girlfriend would sooner use one of the 3 normal computers for internet than try to cram in there and work out how to use ubuntu :)
 
I've just taken everythin remote off the server for now, funny thing is shields up shows all ports stealth apart from 113 (closed) so there must a be a serious security vunerability with the remote software on ubuntu servers. This is the first time in 15 years on the internet I've ever had a problem like this! I'm really paranoid now in case they managed to put a back door of some sort on my XP machine or the server - any suggestions other than wiping both to check this out? I have firestarter running on the server, standard XP firewall and AVG on the XP box and hardware firewall on the router.
 
PS Reporting to ISP probably isn't worth the hassle as I'm with Virgin Media (formally NTL) and they wouldn't care.
 
PPS If anyone who's replied to the post wants my external IP to scan and put my mind at ease please let me know! :)

---

### Post by ld.4lpha on 2010-01-08
> **cornburn said:**
> If anyone who's replied to the post wants my external IP to scan and put my mind at ease please let me know! :)

You can do this at [http://nmap-online.com/](http://nmap-online.com/)

---

### Post by CharlesA on 2010-01-08
That's really handy!

---

### Post by HyperHacker on 2010-01-08
> **Lars Noodén said:**
> And even then, tunnnel vnc over SSH since vnc's encryption is not as strong as it could be.All the encryption in the world won't do you much good if you don't have a strong password (or really I should say passphrase).

---

### Post by lisati on 2010-01-08
> **cornburn said:**
> Thanks for all the replies. Passwords were set on eveything, including the wireless. 
I'd suggest making sure that the wireless password is WPA in preference to WEP, and possibly set some MAC access restrictions as well.

---

### Post by Project PWNED on 2010-01-09
> **scottuss said:**
> The "authorities", including the ISP will most likely not be interested. There's little evidence of illegal activity with regard to the PayPal / Ebay activity, and if VNC was running and forwarded / allowed through a firewall with no password protection, the "authorities" won't take you seriously.

If I approached my local police department I'd get a deer in the headlights look

---

### Post by euler_fan on 2010-01-09
> **lisati said:**
> I'd suggest making sure that the wireless password is WPA in preference to WEP, and possibly set some MAC access restrictions as well.

If and only if you are worried about denying access to your wifi connection and/or the `privacy' of your mobile browsing. Anything you send through an ssh tunnel will still be encrypted.

---

### Post by lisati on 2010-01-09
> **euler_fan said:**
> If and only if you are worried about denying access to your wifi connection and/or the `privacy' of your mobile browsing. Anything you send through an ssh tunnel will still be encrypted.

True......On their own, WEP and MAC filtering won't stop someone who is sufficiently determined to break in, but it will slow them down a little.

---

### Post by scottuss on 2010-01-09
> **Project PWNED said:**
> If I approached my local police department I'd get a deer in the headlights look

Absolutely, I suspect most would be like this!

---

