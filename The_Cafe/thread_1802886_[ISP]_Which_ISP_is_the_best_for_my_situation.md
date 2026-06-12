---
title: "[ISP] Which ISP is the best for my situation"
date: 2011-07-12
forum: The Cafe
---

### Post by ki4jgt on 2011-07-12
I just started a webserver. It's a game. The pages are merely bytes big (including the pictures) I have a domain. Now, I'm wondering what I should do about ISPs. Certain ISPs have problems with you using their service to host web content. Which ISP should I use? I have the site running through Tor. What type of hosting should I ask for? I live in the southern part of the US, Kentucky to be more exact.

---

### Post by Dry Lips on 2011-07-12
> **ki4jgt said:**
>  I have the site running through Tor. 

Hello mate! 

You have the site running through Tor? I didn't even know that
was possible... Out of curiosity, how do you do that? :-k

---

### Post by 8_Bit on 2011-07-12
Most of the bigger ISPs offer business packages that allow web servers.

Some ISPs don't condone web servers, but won't actually bother to check. My ISP for example blocks port 80, but you can just run the web server on port 81 instead and it works perfectly. I did this for several years and I never got "in trouble."

Anyway, if you have the money to pay for an ISP's business package you also have enough money for a dedicated host. Why not just pay for web hosting?

[EDIT] Just noticed the Tor part. You do know that this is really frowned upon, right? Running servers through Tor is just a plain abuse of the system. Tor is already really slow to begin with, and the people who provide their bandwidth for it are doing so voluntarily for free. You do not want your website's visitors to have to put up with really slow loading times anyway. I highly recommend ceasing the use of Tor for your server.

---

### Post by Dustin2128 on 2011-07-12
I run a forum from my server on my home ISP- just a simple tweak to give the machine an external IP and that's it. I agree that running it through TOR is not a good idea. Anyway, either get a business package that allows for a fixed IP or shared hosting. Both should cost about 20-40$ a month.

---

### Post by ki4jgt on 2011-07-12
I don't get why it is frowned upon. Wikileaks did it in it's early days, and Tor itself encourages it (as evident by their how to page)

[https://www.torproject.org/docs/tor-hidden-service.html.en](https://www.torproject.org/docs/tor-hidden-service.html.en)

This goes into detail of how to host a website/server through Tor. You get your own URL, which is what I was interested in. The URL stays the same even with a dynamic IP. I know DDNS does this too, but it's not the same. With Tor, I can change it on a whims notice.

EDIT: As for the lag. That's my only issue. However, I don't want a ddns b/c I will not have my own domain name. The lag will actually benefit the server though. The game relies on the fact that everyone isn't contacting it at once. The lag will allow this to happen. Although I'm moving to a domain name after I move the game out of BETA, the lag provides it's benefits. The game is a game of chance, and it text based.

---

### Post by Dustin2128 on 2011-07-12
I've got a dynamic IP, but I just update the domain (co.cc) every time it changes- I wrote a small script to alert me via email when it happens. Or rather, am writing. Bit trickier than I thought.

---

### Post by ki4jgt on 2011-07-12
> **Dustin2128 said:**
> I've got a dynamic IP, but I just update the domain (co.cc) every time it changes- I wrote a small script to alert me via email when it happens. Or rather, am writing. Bit trickier than I thought.

I'm going to move to a DDNS after BETA service is over, but currently, Tor works through firewalls. I can basically go to my dad's house with my netbook and run my server. I can go to my grandmother's house and run my server. I can go to the public library and have my server running. My apartment also will run it. I don't have to worry about adjusting the router's firewall settings each time. Until I get out of BETA, I don't want to offer it to just everyone. Plus, tor2web.org allows anyone to access it anyway. You simply type the domain name and instead of .onion you type .tor2web.org on the end. The pages are mearly bytes big, so the lag isn't that big of a deal, for a pro job (out of BETA) it will be, but not currently. I was considering IP2 which has pretty much cut the lag down substantially. No one knows about them though :-(.
Plus, I like the fact of having a virtual port, and a target port. The target port points at the server (all other ports have been blocked) and the virtual one points at port 80. It allows me to only have one port open for the entire system and it's only accessible via localhost.

---

