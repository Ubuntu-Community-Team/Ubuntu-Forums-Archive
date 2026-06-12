---
title: "virus affects linux routers"
date: 2009-03-25
forum: The Cafe
---

### Post by bryncoles on 2009-03-25
its happening folks...

[http://www.vnunet.com/vnunet/news/2239126/worm-turns-linux-routers-botnet](http://www.vnunet.com/vnunet/news/2239126/worm-turns-linux-routers-botnet)

choice quotes:

> Researchers are warning of a new worm that targets DSL routers running a distribution of Linux.
> The worm is believed to be the first of its kind, and the researchers at DroneBL estimate that it may have infiltrated as many as 100,000 routers.
> Once installed, psyb0t allows remote control of the router, and infected hardware has already been used to take part in botnet attacks

now, lets merge me with the other 100,000 threads on this topic, and bury me in recurring discussions!

---

### Post by smbm on 2009-03-25
Quotes from the article: [http://www.vnunet.com/vnunet/news/2239126/worm-turns-linux-routers-botnet](http://www.vnunet.com/vnunet/news/2239126/worm-turns-linux-routers-botnet)

"Psyb0t uses a brute force dictionary attack against the router to obtain username and passwords. This shows that the exploitation is not an attack on the flaw in the operating system itself, but against poor user security."

and

"Ninety per cent of the routers and modems participating in this botnet are participating due to user error"

Put it in perspective a little.

---

### Post by Sealbhach on 2009-03-25
I would iamgine it's easy to patch. Perhps that mips distro was abandoned - no longer maintained?


.

---

### Post by Icehuck on 2009-03-25
You are only vulnerable if:

* Your device is a mipsel device.
* Your device has telnet, SSH or web-based interfaces available to the WAN
* Your username and password combinations are weak, OR the daemons that your firmware uses are exploitable.

This also effects routers running DD-WRT

From here [http://www.dronebl.org/blog/8]("http://www.dronebl.org/blog/8")

---

### Post by bryncoles on 2009-03-25
> **smbm said:**
> "Ninety per cent of the routers and modems participating in this botnet are participating due to user error"

Put it in perspective a little.

yeah, i should have picked that one out too as i think about it. good catch!

---

### Post by Pogeymanz on 2009-03-25
So, if your username and password are dictionary words, you are in danger of being infected. OR if the daemons that your firmware uses are exploitable. There doesn't seem to be much one can do about that.

But you also have to have telnet, SSH or web-based interfaces available to the WAN. 

Do routers have those things by default? I've never tried to log in to my router from outside my LAN...

---

### Post by smbm on 2009-03-25
I checked over mine yesterday afternoon. 

I couldn't connect in from the WAN side but I rebooted and hardened up my password anyway.

---

### Post by Icehuck on 2009-03-25
> **Pogeymanz said:**
> 

Do routers have those things by default? I've never tried to log in to my router from outside my LAN...

These things are usually turned off by default on consumer routers.

---

### Post by SunnyRabbiera on 2009-03-25
> **Icehuck said:**
> You are only vulnerable if:

* Your device is a mipsel device.
* Your device has telnet, SSH or web-based interfaces available to the WAN
* Your username and password combinations are weak, OR the daemons that your firmware uses are exploitable.

This also effects routers running DD-WRT

From here [http://www.dronebl.org/blog/8]("http://www.dronebl.org/blog/8")

My router is a Linksys **WRT**54G, am I possibly in danger?

---

### Post by marco123 on 2009-03-25
It's started?  Oh no, we are doomed, it's the end of Linux.  I'd better re-install Windows to have a secure environment. :confused:

Seriously though, any Operating System can be cracked if the user is ignorant, even OpenBSD.

Cheers, Marco.

---

### Post by Giant Speck on 2009-03-25
I'm waiting for some uneducated person to say something along the lines of "that's not possible."

As I said in the other Psyb0t thread, I am glad I personally don't use a router.

---

### Post by marco123 on 2009-03-25
> **Giant Speck said:**
> I'm waiting for some uneducated person to say something along the lines of "that's not possible."

As I said in the other Psyb0t thread, I am glad I personally don't use a router.

Unfortunately that same lack of education is what actually makes it possible.:(

Cheers, Marco.

---

### Post by albandy on 2009-03-25
Using dictionary passwords is like if you carry your visa card with the pin number writed in it.
So this is not a linux security problem, is a user security problem.

---

### Post by Giant Speck on 2009-03-25
> **albandy said:**
> Using dictionary passwords is like if you carry your visa card with the pin number writed in it.
So this is not a linux security problem, is a user security problem.

That's what most security flaws are anymore.

I mean, you don't hear about normal viruses anymore, especially in Windows.  It's always trojans and social engineering schemes.

---

### Post by Icehuck on 2009-03-25
> **SunnyRabbiera said:**
> My router is a Linksys **WRT**54G, am I possibly in danger?

I don't really know if that particular model is in danger. I will say it is possible that it is at risk, but I don't know enough about that device to give you a real answer.

---

### Post by UbuntuNerd on 2009-03-25
> **albandy said:**
> Using dictionary passwords is like if you carry your visa card with the pin number writed in it.
So this is not a linux security problem, is a user security problem.

yep I believe this has more to do with the user than anything else.

---

### Post by SunnyRabbiera on 2009-03-25
> **marco123 said:**
> It's started?  Oh no, we are doomed, it's the end of Linux.  I'd better re-install Windows to have a secure environment. :confused:

Seriously though, any Operating System can be cracked if the user is ignorant, even OpenBSD.

Cheers, Marco.

Indeed, but hearing this does make me feel a little concerned with this being able to infect WRT routers and I have a WRT router staring me in the face (its right on top of my monitor)
Knowledge is power, I dont think I have anything to worry about but my Hubby is paranoid.


> **Icehuck said:**
> I don't really know if that particular model is in danger. I will say it is possible that it is at risk, but I don't know enough about that device to give you a real answer.


Detective work, ahoy!

---

### Post by Icehuck on 2009-03-25
> **SunnyRabbiera said:**
> Indeed, but hearing this does make me feel a little concerned with this being able to infect WRT routers and I have a WRT router staring me in the face (its right on top of my monitor)
Knowledge is power, I dont think I have anything to worry about but my Hubby is paranoid.

I wasn't absolutely sure that you were basing your possible risk on the WRT part of the router name in your last post.  However; now I am positive that you were referring to it this way. When I said DD-WRT I referring to the open source firmware project for routers called DD-WRT. It was originally intended as an alternative firmware for Linksys routers but it has spread to other brands and models. 

Now this doesn't mean your router is not at risk, because Linksys does use mipsel.  I just don't know which devices from Linksys are at risk.

---

### Post by SunnyRabbiera on 2009-03-25
> **Icehuck said:**
> I wasn't absolutely sure that you were basing your possible risk on the WRT part of the router name in your last post.  However; now I am positive that you were referring to it this way. When I said DD-WRT I referring to the open source firmware project for routers called DD-WRT. It was originally intended as an alternative firmware for Linksys routers but it has spread to other brands and models. 

Now this doesn't mean your router is not at risk, because Linksys does use mipsel.  I just don't know which devices from Linksys are at risk.

Aye, well I can play with stuff but I need to call my cable company too if I need to go that far into my router.
I remember setting it up ages ago on windows, but forget most of the steps.

---

### Post by sydbat on 2009-03-25
> **Giant Speck said:**
> I'm waiting for some uneducated person to say something along the lines of "that's not possible."

As I said in the other Psyb0t thread, I am glad I personally don't use a router.THATS NOT POSSIBLE!!11!!

Now that THAT is out of the way...my ADSL modem from the phone company has a built in router (Gigaset SE567). Anyone know if this is one of the mipsel type?

I do know that I have disabled things like wireless and made sure there is nothing "open" (ssh, telnet, etc).

Is there any way to find out if it has been compromised (although I do not believe it has)?

---

### Post by Icehuck on 2009-03-25
> **sydbat said:**
> THATS NOT POSSIBLE!!11!!

Now that THAT is out of the way...my ADSL modem from the phone company has a built in router (Gigaset SE567). Anyone know if this is one of the mipsel type?

I do know that I have disabled things like wireless and made sure there is nothing "open" (ssh, telnet, etc).

Is there any way to find out if it has been compromised (although I do not believe it has)?

If you can connect to it and make changes to your settings it's fine. Psybot closes the management ports when it runs on a router.

Edit - Fixed Typo

---

### Post by sydbat on 2009-03-25
> **Icehuck said:**
> If you can connect it and make changes to your settings it's fine. Psybot closes the management ports when it runs on a router.Thanks. Just checked and everything is good!

---

### Post by kaixi on 2009-03-25
> **Icehuck said:**
> If you can connect to it and make changes to your settings it's fine. Psybot closes the management ports when it runs on a router.

Edit - Fixed Typo
Does that mean that if my internet connection is very slow it's a problem of my ISP. My problems started about 3 weeks ago; I'm currently getting 1/6 of the speed I should get in normal conditions :(. I mean, I can actually connect to my router interface.

---

### Post by Sealbhach on 2009-03-25
> **kaixi said:**
> Does that mean that if my internet connection is very slow it's a problem of my ISP. My problems started about 3 weeks ago; I'm currently getting 1/6 of the speed I should get in normal conditions :(. I can actually connect to my router interface, though.


There's instructions to disinfect:

> To disinfect, simply powercycle your device and take appropriate action to lock it down, including the latest firmware updates, and using a secure password.

[http://dronebl.org/blog/8](http://dronebl.org/blog/8)

Does that mean switch it off and on again?


.

---

### Post by smbm on 2009-03-25
> **Sealbhach said:**
> There's instructions to disinfect:



[http://dronebl.org/blog/8](http://dronebl.org/blog/8)

Does that mean switch it off and on again?


.

In essence, yes.

Here's what I did though (being fairly paranoid about security):

I powered down my router, disconnected the WAN (phone) cable, powered the router back up again and changed the passwords, then I reconnected the WAN cable.

I then got a trusted mate to try and connect to my IP address via the web, telnet and ssh. When all his connections timed out I was satisfied I didn't have it and I had done everything in my power to prevent me getting it.

Hope yours turns out to be ok.

---

### Post by Rokurosv on 2009-03-25
[http://blogs.techrepublic.com.com/security/?p=1176](http://blogs.techrepublic.com.com/security/?p=1176)

Lesson: Don't use weak passwords

---

### Post by Icehuck on 2009-03-25
> **Rokurosv said:**
> 
Lesson: Don't use weak passwords

Or use hardware using MIPs architecture that runs an OS that has daemons that can be exploited regardless of password.

---

### Post by Rokurosv on 2009-03-25
> **Icehuck said:**
> Or use hardware using MIPs architecture that runs an OS that has daemons that can be exploited regardless of password.

I was referring to the 90% they mention are user-errors.

---

### Post by Icehuck on 2009-03-25
> **Rokurosv said:**
> I was referring to the 90% they mention are user-errors.

Oh, I probably interpreted that because the last thing I read on that link came off like they blamed the whole thing on bad passwords.

---

### Post by damis648 on 2009-03-25
:shock:
*Connects to router*
*Changes passwords*
*Disables WAN administration (only LAN)*
:-\"

This is some crazy stuff. The sad part is that 99% of the people I know have routers still using the default admin/password combination. *sigh*

---

### Post by oldsoundguy on 2009-03-25
I just posted this on a computer consulting board I work on .. it is mostly newbs and Windows users, but a few Mac and Linux users DO pop in now and then.
I know most here that read this have already taken the measures, but worth it to pass it on if we can help!

"The remedy:
FIRST: power down and then back up (a hard reset (using a paper clip) is NOT needed.) That pwrdn/pwrup will ERASE the bot if it is already in there!
THEN:
Access your router (using the set up info you have) and HARDEN your administrative password .. take it out of the dictionary or remove the "not required default password"! Make it alpha numeric (write it down and tape it to your router) ... a good way is take a two syllable word and put a number, then the first syllable, then a number, then the second syllable, and then a number.

IF this gets nipped in the bud, the damage will not be as severe if that thing gets launched.

A LOT of discussion about it on some of the security sites and the Linux sites (since the firmware is a crippled Linux program on some of the units.)

The REAL fix will be updated firmware, but do NOT hold your breath, especially for the OLDER routers."

---

### Post by bhishan on 2009-03-25
> **bryncoles said:**
> its happening folks...

[http://www.vnunet.com/vnunet/news/2239126/worm-turns-linux-routers-botnet](http://www.vnunet.com/vnunet/news/2239126/worm-turns-linux-routers-botnet)

choice quotes:





now, lets merge me with the other 100,000 threads on this topic, and bury me in recurring discussions!

i opened the link, and guess what, microsoft is advertising in that page. lol.

---

### Post by scottuss on 2009-03-25
So this is going to affect a stupidly small percentage of routers on the net then...

If people are running custom firmware you would think they would have the sense to use a good username / password. Or maybe not!

---

### Post by oldsoundguy on 2009-03-25
> **scottuss said:**
> So this is going to affect a stupidly small percentage of routers on the net then...

If people are running custom firmware you would think they would have the sense to use a good username / password. Or maybe not!


No,it is going to effect a LOT of routers .. since most of them use Linux (not Windows) based firmware.
BUT, having said that, not ALL manufacturers were lazy about their firmware and put in protection .. this piece of malware comes in as ROOT!  IF the proper precautions have not been taken, either by the manufacturer to PREVENT such or by the user to harden access to their router.

All one has to do to access many routers is put in the code:
[http://and](http://and) the ROUTER URL and you are IN to many of them from the OUTSIDE.  Good firmware does not allow such.  and if it has bad firmware, a good password will stop them from altering the programming.

---

### Post by gibxam on 2009-03-25
> 
and copies the file to the following location.

* /var/tmp/udhcpc.env

Does this mean that if we check this location and there is nothing there we are in the clear?

---

### Post by blastus on 2009-03-25
I have used DD-WRT for a long time. I have always done the following from day one:

1. Make sure Telnet is disabled
2. Make sure SSH is disabled
3. Make sure Remote Web GUI Management is disabled
4. Use HTTPS only for Web Access Protocol
5. Generate the longest possible password from GRC's *Perfect Passwords* and set the router password to that (the latest version of DD-WRT supports passwords at least up to 30 characters long because that's what I'm using)

---

### Post by scottuss on 2009-03-26
> **oldsoundguy said:**
> No,it is going to effect a LOT of routers .. since most of them use Linux (not Windows) based firmware.
BUT, having said that, not ALL manufacturers were lazy about their firmware and put in protection .. this piece of malware comes in as ROOT!  IF the proper precautions have not been taken, either by the manufacturer to PREVENT such or by the user to harden access to their router.

All one has to do to access many routers is put in the code:
[http://and](http://and) the ROUTER URL and you are IN to many of them from the OUTSIDE.  Good firmware does not allow such.  and if it has bad firmware, a good password will stop them from altering the programming.

If you read the article you will see that it applies to specific versions of Linux running on routers, standard Linux firmware that comes on consumer routers is not at risk.

---

