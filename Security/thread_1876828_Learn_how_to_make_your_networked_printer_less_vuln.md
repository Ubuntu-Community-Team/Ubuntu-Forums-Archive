---
title: "Learn how to make your networked printer less vulnerable"
date: 2011-11-06
forum: Security
---

### Post by WasMeHere on 2011-11-06
This thread is written in order to interact with the following wiki page
[[COLOR="RoyalBlue"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

**[SIZE="3"]Network printer[/SIZE]**

Use network printing only if you need it! It is safer with a printer attached directly to your computer.

The following shows how you can make your network printer less vulnerable to intruders. It is an example using a web browser (e.g. Firefox) to log in to your router and printer.

***Start by browsing through the manual for your printer.***

***Unless you already know it, find your printer's address.*** Log in to your router, usually at [http://192.168.0.1](http://192.168.0.1) or [http://192.168.1.1](http://192.168.1.1)

Look for 'Attached Devices' or something meaning the same. You may find the printer at
[http://192.168.0.3](http://192.168.0.3) (or a similar address),

or run an fping command like
[FONT="Courier New"]fping -ag 192.168.0.1 192.168.0.20 2>/dev/null |fping -ad[/FONT]
to find the printer (or at least what might be the printer).

***Then log in to your printer***, in this example at [http://192.168.0.3](http://192.168.0.3)

1. Change the default password(s) to something much better.

2. Browse the menus to find what protocols are enabled. Disable at least FTP, TFTP and Telnet, unless you are sure that you need them! Try to understand the other protocols too, and run only those necessary!

3. Save the changes and shut off the printer. Restart it and make sure that your printer settings really changed, that the settings are safer now (and that you can still use your printer from all computers).

4. If you cannot set the password(s) or disable FTP, TFTP and Telnet, please consider attaching the printer to your main computer, if you care about network security!

---

### Post by CharlesA on 2011-12-08
Very nice write up.

In my case, the two HP printers I have have mDNS installed (and running), with no way to disable it.

---

### Post by emiller12345 on 2011-12-08
Speaking of vulnerable printers, i read an interesting article...
[http://redtape.msnbc.msn.com/_news/2011/11/29/9076395-exclusive-millions-of-printers-open-to-devastating-hack-attack-researchers-say](http://redtape.msnbc.msn.com/_news/2011/11/29/9076395-exclusive-millions-of-printers-open-to-devastating-hack-attack-researchers-say)

---

### Post by kurt18947 on 2011-12-08
What is the risk of a bad guy getting printer access?  Could he/she get to the file system or /home via a printer system/CUPS/whatever?

---

### Post by Dangertux on 2011-12-08
First off great write up -- didn't see this one I've been super busy lately. Well done Olle :-)

Now to answer this question.

> **kurt18947 said:**
> What is the risk of a bad guy getting printer access?  Could he/she get to the file system or /home via a printer system/CUPS/whatever?

The risk on something like this is a little harder to calculate.  Look at it this way, if you're a corporation with network exposed printers the risk is considerably higher, the reason being printers are widely accessible from most clients (and vice versa) so they are a great way to move throughout the network. They are also often not regarded as a system which needs securing, tweaking or tightening in any way shape or form. Most people are just happy that their network printer works.

As a private individual the risk drops considerably, for a couple of reasons. One the average home printer you buy at a bigbox store like bestbuy isn't going to have the functionality of an enterprise class network printer, so automatically there is less to abuse. This does NOT mean that it's not vulnerable, it just means it's not "low hanging fruit" so to speak as it would be in an enterprise. You'd be more likely to have a poorly secured Linux box or Windows Box sitting on your network that would be easier to compromise than a printer. Also -- printer exploitation methods are often custom written due to the variation in models and technology so it's a sign of a very targeted attack, something most home users will never encounter.

Now once you start getting into CUPS and things of that nature, that's a different ballgame. Exploiting CUPS is the same as exploiting any other service (ftp , whatever) running on a system. This has nothing to do with the printer itself, more the service. Best preventitive measure here is keep CUPS updated if you need to use it, disable it if you don't.

```

sudo update-rc.d cupsd remove -f

```As far as exploiting a printer - gaining privileges on another machine in the network via a printer exploit is unlikely, probably could read data from the spooler service but that's about it. What would happen is the printer could be used as an attack platform to compromise additional machines and provide a pivot point within the network to do so.

 Exploiting CUPS however again is a different matter, exploiting a service will yield you privileges equal to that of the user running it. So here is where DAC and MAC come in. I believe CUPS has an Apparmor profile by default so it should be locked down fairly well, if not it should be trivial to generate one. IF it were unconfined and exploited it could yield r/w to home and r of /. However as I stated I believe it's confined.

Hope this is helpful.

---

### Post by bluexrider on 2011-12-08
this is GOOD information. Thanks

---

### Post by kurt18947 on 2011-12-08
Thanks Dangertux, that makes sense.  I know some enterprise-level document systems have hard drives built in.  I imagine that could be a fertile field for corporate espionage.

---

### Post by Dry Lips on 2011-12-08
From the article emiller12345 referred to:
[I]
"Could a hacker from half-way around the planet control your printer and  give it instructions so frantic that it could eventually catch fire?"[/I]

Sounds a bit like stuxnet 3.0, don't you think? I wonder what the next thing will be? Hackers gaining entrance to your toaster in order to... *pinky to lip* burn your toasts? Actually I suspect that's already happened ;)

---

### Post by CharlesA on 2011-12-08
> **Dry Lips said:**
> Hackers gaining entrance to your toaster in order to... *pinky to lip* burn your toasts? Actually I suspect that's already happened ;)

You made me think of [this]("http://ubergeek.tv/article.php?pid=53")...

---

### Post by Jive Turkey on 2011-12-08
> **kurt18947 said:**
> What is the risk of a bad guy getting printer access?  Could he/she get to the file system or /home via a printer system/CUPS/whatever?

I've heard claims that some printers, when misused can be caused to overheat and possibly ignited remotely.  Also, its always bad to have an exploited network aware gadget on your LAN for numerous reasons.

---

### Post by WasMeHere on 2011-12-09
> **CharlesA said:**
> Very nice write up.

In my case, the two HP printers I have have mDNS installed (and running), with no way to disable it.

> **Dangertux said:**
> First off great write up -- didn't see this one I've been super busy lately. Well done Olle :-)

Now to answer this question.
...

Thank you :-)

I'm no expert, so I'm glad that you posted such a comprehensive answer to kurt18947's question, DT. And it is good that the tread is getting an own life with several interesting posts.

---

