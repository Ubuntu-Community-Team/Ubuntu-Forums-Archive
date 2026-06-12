---
title: "Tried hard, but giving up!"
date: 2007-05-27
forum: Testimonials &amp; Experiences
---

### Post by nmacjr on 2007-05-27
I've probably put 20 hours into this, read half of a beginners book, read the forums....I so wanted a good alternative to windows
But...
Internet access is terribly slow
I can't get to a number of internet sites.
Exact same hardware under windows, internet is blazing fast.  Under Ubuntu (Feisty) it is very slow.  There seems to be a lot of time where the status bar simply says "waiting for..."
The principal site that refuses to load is yahoo mail (not exactly an obscure site).  It will connect, but then with about 1/3rd of the progress bar complete, while it is "waiting for yahoo login" it never gets any farther.
So I'm going to reluctantly give up and order a fresh copy of windows from New Egg.  It's really too bad because I'm willing to put in the time and effort, but this is simply too frutstrating.
BTW, tried to get to launch.net as an alternative forum for info - same problem, Ubuntu simply won't load the site!

---

### Post by coffeecat on 2007-05-27
I'm prepared to bet £5 that this is the dreaded IPv6 issue.

20 hours! Pffft. Took me three months to solve this one when I was new to Linux. :wink: (Please don't take offence - only teasing.)

Try this:

Open firefox. Type 'about:config' into the address bar (not the quotes). Now 'ipv6' (again no quotes) in the filter. One line will appear starting 'network.dns.disableIPv6'. At the far right change the 'false' value to true by right or double-clicking. Now close down firefox and restart it. If you can browse the internet OK, we've identified the problem, but there will be more to do. Post back and we'll take it from there.

If this is the IPv6 problem, **do not blame Linux**. It is not a Linux problem. I'll explain more later if necessary.

Question: what type of internet connection are you using? Router? Type of modem?

By the way. If this is not down to IPv6, I'm keeping my £5. I'm not a betting man. :wink: :lol:

---

### Post by Sceptical on 2007-05-27
Quote:

[I]...Internet access is terribly slow
...under windows, internet is blazing fast. Under Ubuntu (Feisty) it is very slow...
... principal site that refuses to load is yahoo mail (not exactly an obscure site)... "waiting for yahoo login" it never gets any farther...[/I]

Well, that hasn't been my experience. And I am certainly a complete novice with any non-Dos/Windows OS.

I installed Feisty today on a spare machine (1 GHz Athlon, 768MB RAM) and connected it to my router. Bingo! So far, everything has worked like a dream.

I too use Yahoo webmail and it loads as fast - if not faster - on the Ubuntu machine as it is on the 'Doze one (W2K SP4; 2GHz P4, 1GB RAM). As, indeed, do the other sites I've visited.

My advice would be not to give up at the first hurdle: dig around, read a lot and enjoy the challenges and hiccups.

Sceptical

---

### Post by coffeecat on 2007-05-27
> **Sceptical said:**
> My advice would be not to give up at the first hurdle:

15 hours since he posted. Only one post. I rather think he might well have done - but I hope not.

---

### Post by jrusso2 on 2007-05-27
bah thats not even a major issue to quit over. Just some configuration issue probably IPV6 like people said.

Heck in the old days we had to write our own dial up script and configure it all be editing files

---

### Post by ryanVickers on 2007-05-27
I wouldn't give up quite yet, sounds like the Internet is your only problem, and there is help out there - you can even use windows drivers if you want!  I'm assuming it's a wireless connection, so look around in the iwconfig command under System > Help and Support, or if you haven't changed your panels, it's the blue circle at the top by evolution and firefox.

There are tons of people with this problem, but I got past it - you just have to be very specific in the configuration of everything - tell it your router name, key, channel/frequency, everything!  then wait about 20 mins for anything to happen :)

I would very much doubt it's a IPv6 thing - That's what I mistakenly thought also for a number of weeks before finding out that that didn't matter and I just had to be super specific in the config of the Internet connection.

---

### Post by Sceptical on 2007-05-28
> **coffeecat said:**
> 15 hours since he posted. Only one post. I rather think he might well have done - but I hope not.

Who? Me? Nah, I went to bed :)

I posted in another  thread but, to quote David Byrne, "When I've nothing to say / My lips are sealed / Say something once / Why say it again"

Sorry! Rather OT.

Scepical B*st*rd

---

### Post by 3rdalbum on 2007-05-28
It could be any number of things:

1. IPv6 is not compatible with his router. (Windows XP does not have support for IPv6.)

2. He is setting up his internet with DHCP, and the first DNS address being returned by the router is incorrect. This causes Linux to try and contact an invalid address every time an HTTP request is sent, then only after it times out does it contact the correct DNS server. (This did not happen on his Windows XP because the CD that came from his ISP set up the correct server addresses, which were hardcoded onto the CD's script).

---

### Post by nmacjr on 2007-05-29
Appreciate the responses.  Haven't quite given up completely.  I went to New Egg and was about to complete the order for WinXP - but I couldn't bring myself to hit the complete sale button.
Tried the IPv6 problem suggestion - it did not change anything.
Interesting thing is that most sites are fine - fast, no problem.  It's just the yahoo mail site - it directs to the site, but won't get as far as the login screen - it says it's waiting for login.yahoo.com.
I'm on vacation using a wireless service at the hotel.  When I tried Ubuntu at home before I left using a standard cable modem, yahoo mail worked fine.  So my install is fine, I'm NOT blaming Linux/Ubuntu itself, but there's something in its communication with the local router or security settings or something.
So I'll try again when I'm home and see if I can isolate the problem.

---

### Post by coffeecat on 2007-05-29
> **nmacjr said:**
> Interesting thing is that most sites are fine - fast, no problem.  It's just the yahoo mail site - it directs to the site, but won't get as far as the login screen - it says it's waiting for login.yahoo.com.

From your first post I didn't appreciate that some/most sites were fast. I thought it was everything - otherwise I wouldn't have suggested the IPv6 thing which is clearly now not relevant.

I use Yahoo mail and every so often the server goes out to lunch - a very long lunch. Sometimes I can't get the login page or sometimes I get hung up between the login page and my mailbox. The fact that I can browse other sites from another tab OK at such times means that it's clearly down to Yahoo.

Over what length of time were you stuck at the login.yahoo.com stage? There was an occasion some months ago when I couldn't get into Yahoo mail for more than a day. At the same time a neighbour who uses BT (that's British Telecom which contracts its email to Yahoo) and Apple Macs couldn't get into their mailbox either. 

Sorry to hear you've had such a frustrating time, and glad to hear you didn't buy another copy of Windoesn't. We don't want to weigh BG's pockets down with money any more than they are already, do we? :wink:

**Edit:** By the way, this business of servers suddenly slowing down for whatever reason can lead to [some very strange conclusions](http://ubuntuforums.org/showthread.php?t=454585). :)

---

