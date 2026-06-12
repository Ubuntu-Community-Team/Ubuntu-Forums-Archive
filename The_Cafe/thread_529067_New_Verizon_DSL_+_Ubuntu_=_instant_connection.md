---
title: "New Verizon DSL + Ubuntu = instant connection"
date: 2007-08-18
forum: The Cafe
---

### Post by CSMatt on 2007-08-18
I just got Verizon DSL for my apartment, and decided to see what kind of error message would appear after not setting up my account with Windows first.  I was 95% sure that  Verizon would have zero GNU/Linux support until the account was set up under Windows or Mac OS X first.  Well, I booted up both Ubuntu and my wireless modem/router, started up the GNOME browser, and much to my surprise it worked immediately, without any redirects or error messages.  I was able to use other Ubuntu programs as well.  It seems that Verizon's DSL works as soon as they activate it, and they abuse the fact that the majority of users have Windows or Mac OS X with either IE or Firefox in order to coax them into running their proprietary software and attempt to trick the ignorant into installing useless junk after creating an e-mail.

Of course, there are some drawbacks.  The combined router/modem's authentication is the same as that for the e-mail for the master account holder, so it is impossible to change the router settings (not a problem for those who ordered just the modem and hooked it up to another router).  I also can't launch Firefox or Thunderbird, most likely because the modem was programmed to recognize those programs due to their popularity on the Windows front and disable them.  It should also be noted that I activated this service from another Internet connection with a separate e-mail address rather than by phone, so that might be a factor.

---

### Post by izanbardprince on 2007-08-18
Actually, the first thing I did when I got my DSL line was throw the setup disc in the trash, there's usually a setup address in the modem that will load in any web browser, 192.169..0.1 is mine, anyway all you have to do is type in your login information on the modem and then you're good to go, should work with any operating system, unfortunately most ISP's only support technical problems on Windows.

I was calling to report an outage and the first thing they did was tell me to run the connection diagnostic program from my task tray, I told them that may be a problem since I wasn't on Windows, actually I do dual boot Windows 2000 and Ubuntu but their crapplets aren't on my Windows partition anyway.

One of the most annoying things about Windows 2000 is that there is no MSCONFIG, and every Windows program likes to set itself to start up with Windows, whether there's a legitimate need to or not, I try to keep the list of running programs to a minimum because I don't like them sitting there gobbling up RAM.

---

### Post by Nessa on 2007-08-18
If you have a Westell modem, the ip address is usually 192.168.1.254. Most routers use 192.168.1.1.

---

### Post by CSMatt on 2007-08-18
I know what the address is (the Westell routers will also respond to [http://dslrouter/](http://dslrouter/)), I just can't get past the authentication because I don't have a user name and password set up yet with Verizon.

---

### Post by Warren Watts on 2007-08-20
go to activatemydsl.verizon.net to setup your username and password.

---

### Post by picpak on 2007-08-20
Not related to DSL, but I'm pretty sure the latest Verizon Fios commerical uses Linux in its desktop. The control center icon shown on the screen is the same one used in Gnome's icon set, and the theme looks like a purple variation of Clearlooks. It's also blazing fast :D

---

### Post by dca on 2007-08-20
In my experience, if your provider (whether DSL or broadband) does not require proxy servers than its as easy as giving them the MAC address of the modem to activate service...  Set network to obtain IP automatically and your there.

---

### Post by scott3091 on 2009-09-23
I just signed up for Verizon DSL.  I called their tech support number to have the service activated remotely.  The tech told me that they did not support Lee-nukes (Linux) and that they suggest I upgrade to Windows XP or Vista.  I politely told them 'No.' and found that some people have configured their connections manually.  Here are the steps I had to take:

1) Connect everything (wall jack to modem to computer)
2) Browse to [http://192.168.1.1/](http://192.168.1.1/) and enter your DSL username and password (for my Westell modem, I had to click on the word 'connect' to get to these settings
3) Disconnect and reconnect the PPP connection
* At this point, I was still being redirected to activate.verizon.net / or activatemydsl.verizon.net.
4) Browse to: [http://192.168.1.1/verizon/redirect.htm](http://192.168.1.1/verizon/redirect.htm)
5) Click on the Disable button to disable the redirect.

How shady!  Verizon puts a hidden 'feature' to force you to use their software unless you know about this page!

I asked the tech to hang on the line while I configured everything.  Once I completed step 2, she didn't have any problem walking me through the remaining steps.

Enjoy!

Scott

---

