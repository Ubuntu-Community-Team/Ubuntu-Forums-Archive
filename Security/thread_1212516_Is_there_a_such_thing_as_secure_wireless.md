---
title: "Is there a such thing as secure wireless?"
date: 2009-07-13
forum: Security
---

### Post by Vunutus on 2009-07-13
Long story short, I'm the sys admin for a small business. I want to install a wireless network at work so that I can use my personal laptop to SSH into servers and such from anywhere in the office. Obviously, adding wireless to my network opens up a whole new can of worms security wise. Is there any way to have truly secure wireless?

I'm not so much worried about my activity being snooped since any interaction with servers will be via SSH (and therefor encrypted), but someone could cause some serious problems if they managed to connect to my wireless.

What I'm thinking of doing security wise:

[LIST]
[*]WPA encryption
[*]No SSID broadcasting
[*]Restricting MAC addresses to only the MAC of my laptop (yes I know it can be spoofed)
[*]No wireless connections outside of business hours
[*]Lowering signal broadcast strength to the point where it just barely encompasses the whole office
[/LIST]

I realize that many of those things on their own are not adequate security by any means, but if I implement all of the security measures on that list will I have a reasonable expectation that my wireless will be safe?

---

### Post by HermanAB on 2009-07-14
WPA2 is secure enough for small business purposes.  However, the paranoid method is to hook the WiFi modem *outside* your firewall.  You don't even need to encrypt it then and can leave it open for public access - the occasional road warrior will bless you.

To connect to your business LAN, you then need to use SSH or a VPN as usual, just the same as if you are coming in from anywhere else over the public internet.

---

### Post by slowth5 on 2009-07-14
Hi Vunutus, WPA alone is enough to secure the wireless network. There is a documented weakness with WPA TKIP, so use WPA AES or even better WPA2.

The other measures you listed offer no benefit over WPA2 with a very strong password of 63 characters. A determined intruder could easily defeat the other measures. There's nothing wrong with what you've listed, I just think it's overkill, and I'm paranoid.

---

### Post by bodhi.zazen on 2009-07-14
> **hermanab said:**
> wpa2 is secure enough for small business purposes.  However, the paranoid method is to hook the wifi modem *outside* your firewall.  You don't even need to encrypt it then and can leave it open for public access - the occasional road warrior will bless you.

To connect to your business lan, you then need to use ssh or a vpn as usual, just the same as if you are coming in from anywhere else over the public internet.

+1

---

### Post by wirelessmonkey on 2009-07-15
> **HermanAB said:**
> WPA2 is secure enough for small business purposes.  However, the paranoid method is to hook the WiFi modem *outside* your firewall.  You don't even need to encrypt it then and can leave it open for public access - the occasional road warrior will bless you.

To connect to your business LAN, you then need to use SSH or a VPN as usual, just the same as if you are coming in from anywhere else over the public internet.

Agreed.
Though there are more ways to secure your wireless net, if you are so inclined.

---

### Post by munky99999 on 2009-07-15
Security is like the pic.

The number of threats from #s of people are like a triangle... the most innane of security breaches... simply accidentally clicking on your AP and connecting. This can be done by ANYONE. It's also the EASIEST one to fight against. Use WEP stops this.

The higher up on the threats... the fewer people who can do it.

Inversely like the pic. The harder it is and the more money it takes to beat it.

> Long story short, I'm the sys admin for a small business.
Small business already says to me almost 99%

WPA2 + strong password and you're almost certain to do the job just fine.

> Is there any way to have truly secure wireless?
Radius server would do it.

> What I'm thinking of doing security wise:

    * WPA encryption
WPA2 with AES only encryption.

Also remember. STRONG PASSWORD.


> No SSID broadcasting
This one is a funny one. Yes you could do this and stop the ignorant people from messing with you. However this may also mean additional administrative work. As you have to insert the details.

The other hand. Crackers might see you not broadcasting... and wonder... I wonder what they are trying to hide? or see... Oooohhh challenge. FUN!

> Restricting MAC addresses to only the MAC of my laptop (yes I know it can be spoofed)
Yes but if they know your mac. They have to knock you off first. Which you can surely see if you got knocked off. Obviously the question is... is this really going to be JUST FOR YOU? Or will others want the mobility option eventually.

Mac filtering is definately a top notch way.

> No wireless connections outside of business hours
By unplugging it every night? That'll get tiresome. Might have to pay a few big $$ for that option softwarewise.



Implement a radius server. It's super easy to do. Make it a cheap 20$ ebay computer that's hardwired to the router. How can the beat that? They really cant.


The real question. What business are you in? Are you one of the [Stargate]("http://en.wikipedia.org/wiki/Stargate") small businesses?

Or are you really not holding that important of information where nobody cares.

Creating a fort knox for the price of cheese in china isnt exactly going to be that good.

---

### Post by kevdog on 2009-07-17
I love that comic -- its soo true!

---

### Post by HavocXphere on 2009-07-17
Most corporations go with a VPN. (Plus all the standard security  stuff of course).

---

