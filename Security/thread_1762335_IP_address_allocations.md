---
title: "IP address allocations"
date: 2011-05-19
forum: Security
---

### Post by Noob2.0 on 2011-05-19
For a while now, I have been trying to reset my IP address in Ubuntu but I have had no luck. The reasons why I want to reset it and get a new one is because my service provider waits weeks to change it. I am concerned it has fallen into some unsavory hands.  Could anyone help me out with it? 

Also, can you be hacked if the would-be attacker is unaware of your IP address? Are there other means of locating your computer on the web without an IP address or webserver?

---

### Post by CandidMan on 2011-05-19
Hi,
What makes you think someone else has your IP address? As far as I know two devices can't have the same IP on the same network(internet in this case). It becomes meaningless to have an address at that point. Maybe someone is spoofing your address.

Check out [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) to see if you're visible to the internet

I suppose you could be hacked without an attacker 'knowing' your IP address, I've heard entire countries can be probed in and entire night.

Getting a new IP address for me is as easy as resetting my router

---

### Post by JKyleOKC on 2011-05-19
There seems to be a less than clear understanding of exactly what an IP address is; it's simply a number, although it's a very large number. Specifically, it's a 32-bit value that's broken up into four 8-bit segments for human convenience. That's why an address such as "300.400.500.600" is simply impossible to create; the maximum possible is "255.255.255.255" and even that isn't used. 

Theoretically, you could cycle through all four billion plus possible values to contact any possible IP address -- but that would take a few centuries to accomplish even with today's hardware if you used just one machine to do so. However, more limited scans are not only possible but ongoing every day, and you can be hit by any of them at any time.

As for changing your IP address without aid from your ISP, that's akin to changing your phone number without telling the phone company. The result would be that suddenly you would not be able to send or receive anything, because your ISP would still be using your old address for all your traffic, and would not recognize your new one to let you log in.

However, you CAN make such a change to prove my point. If your machine connects directly to your modem, not through a router, you can use Network Manager or the CLI command "ifconfig" to set your IP address to whatever you want it to be. If you use a router, change the router's configuration of its WAN (wide area network) address. However you won't be pleased with the results and may not be able to undo the damage!

Note that this description is for IPV4 addresses, the kind now in common use. The IPV6 format coming into use is similar but the number is much larger -- the same rules, however, apply.

---

### Post by uRock on 2011-05-19
Turn on your firewall and call it a day. **sudo ufw enable** in a terminal will start the firewall which is already installed. Once the command is entered it will deny all external connections that weren't established by you. If you prefer a user interface to control you firewall, then open Ubuntu Software Center, then search for and install GUFW.

With your firewall set to Deny your system will not respond to port scans, so the scanner will not know there is a host there to give necessity to probe further.

---

### Post by HermanAB on 2011-05-19
Hmm, to answer the actual question:
$ sudo killall dhclient
$ sudo dhclient eth0

Will restart dhclient which will get you a new address.

---

### Post by uRock on 2011-05-19
> **HermanAB said:**
> Hmm, to answer the actual question:

There was more than one quesetion. I hit the one which I felt most important. I know I can hit the renew button over and over(in my router's settings), but the ISP's DHCP server will keep giving me the same IP until their timer expires.

---

### Post by Noob2.0 on 2011-05-22
Thank you all so much. I found the comments to be informative and beyond the scope of this humble noob :) 

I will follow your advise and hope for the best. Again, thank you all.

---

