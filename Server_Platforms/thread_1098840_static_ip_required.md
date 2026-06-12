---
title: "static ip required?"
date: 2009-03-17
forum: Server Platforms
---

### Post by blairm on 2009-03-17
Hi,

Looking at setting up a server - would anticipate it handling email along with files for computers in my home. Have a few years of experience with linux but I'm not an expert by any stretch of the imagination.
Most guides I've read have referred to static ip addresses - do I need to get one to set up a server?
And is this the sort of task that I could reasonably expect to complete in a weekend?

Cheers,

Blair

PS: Was unsure whether to post this in the absolute beginner or server forum; apologies if I have made the wrong choice.

---

### Post by primaxx on 2009-03-17
You don't really need a static ip, but it sure makes your life easier! :-)

The alternative is to get a free account by dyndns.org and make your router og server communicate with them.
What happens after you signed up for an account, and got a domain-name ala homeserver.dyndns.org, is that your router or server (after some configuration) allways report to dyndns.org what your ip-address is at the moment. Dyndns.org then again update the dns-servers according to your reports.
The consequense will be that homeserver.dyndns.org always points to your current ip-address.

Sorry for my terrible English...

---

### Post by TurboRush on 2009-03-17
As mentioned about, you do not need a static IP address facing the world necessarily (although it may make life easier).

For example, I have Comcast and in the 2 years I've had them my IP address has only changed once and that was probably because we had a massive ice storm that knocked out major sections of cable and electricity. Even when I lose power normally my IP remains the same.

Might be worth just periodically checking your IP to see if it changes over a couple of days.

---

### Post by blairm on 2009-03-17
Thanks primaxx and TurboRush

Might give it a go with the static ip, even though we get charged an extra $20 a month here in NZ if we want one - given my moderate skills anything that makes life easier is probably a good idea!

Cheers,

Blair

PS: primaxx, no need to apologise for your English; I've seen a lot worse on the net!

---

### Post by primaxx on 2009-03-17
Thanks about my English! :-)
For $20 a month for the Static ip, and you been playing with Linux for a couple of years I would really check out dyndns first. It's not *so *complicated. Good luck! :)

---

### Post by damis648 on 2009-03-17
It may just not be worth it. Try dyndns.org and set up an account. Click "Host Services" and add a new host name. That's it! Just fill in the box with the url you want and then click to use your current IP. Once you finish that, just get an updater for dyndns. Many will update your IP with the service once daily, my router does it automatically whenever my IP changes (many routers have DDNS features, see if yours does). :popcorn:

---

### Post by wkulecz on 2009-03-17
Before you get a static IP address or open up your home to the internet at large via dyndns, may I suggest you just run your file server behind a NAT firewall/router box to protect your local machines and then relay your Email thru your ISP.  This is doable in an afternoon if you know what you are doing, or a weekend if you are googling as you go to figure things out.

While a static IP makes some things easier, you take on a whole new level of responsibility when you expose your system to the internet at large.

Many ISP block incoming connects to well known service ports of their customer's machines -- insecure machines quickly become spam portals and eventualy lead to the provider's legitimate mail being caught in spam filter blacklists.

--wally.

---

### Post by schettj on 2009-03-17
> **wkulecz said:**
> 
While a static IP makes some things easier, you take on a whole new level of responsibility when you expose your system to the internet at large.

This is true, you want to get up to speed with firewalls, fail2ban, mod_secure for your web server, keep those patches up to date, make scanning the logwatch email over your morning coffee a "fun" activity, etc...

That said, its really not that hard to secure things. You just don't want to do anything stupid.

If your ISP gives you static IPs they likely don't firewall your ip for you.
-

---

### Post by volkswagner on 2009-03-17
Blair,

You did not mention a web server.  Do you plan to use the machine to host web sites?

To put things in perspective, my ISP would charge me an additional $100 for a static IP, where others only charge $5/month.

In my opinion a mail server needs a static IP due to other host's wont allow incoming mail from dynamic IP addresses (your friends with yahoo, gmail, MSN, etc. accounts wont get your mail).  The easiest work around is to use your ISP's SMTP server to send mail.

I would get your feet wet first with the server, before getting the static IP address.  There won't be much to change if you decide later.

Do your homework.  Make sure you can open the needed ports.  Verify if your ISP blocks outbound port 80, or 25, etc.  canyouseeme.org can tell you what ports are blocked.

It may be a long weekend if you roll your own mail server.  Many people recommend Citadel, Zimbra, or Kolab.  Check this [tread]("http://ubuntuforums.org/showthread.php?t=1062451&highlight=citadel") or search around for opinions.  I chose the roll your own via an excellent how to, Flurdy gives a comprehensive tutorial.  You may spend a whole day [here]("http://flurdy.com/docs/postfix/").

---

### Post by blairm on 2009-03-18
Thanks everyone,

Would probably look at hosting a website from the machine in the future but it's not a priority. 
But I would like the ability to do so because this is a bit of a learning experience for me - want to know more about how the net works, and figure one of the best ways is to do something like this.

As for the cost of the static ip - I can live with that, considering I get one free with a plan upgrade (which increases my data cap from 20gb to 40gb).

Having done more reading I can see that setting up a server is not the sort of thing I should attempt to complete in a weekend.
Think it could be done quite easily in that time -there are a lot of step by step tutorials out there - but I want to understand what I'm doing instead of simply cutting and pasting commands.

Cheers,

Blair

---

### Post by BkkBonanza on 2009-03-18
For $20/month you can rent a full VPS server in a data center and have full root access to a "machine" out there with full conectivity that can run a mailserver and much more. Also a great testbed for learning and you would be learning what you need for running a commercial server in a data center. There's heaps of vps servers available from $7.95 and up. Google.

---

### Post by hyper_ch on 2009-03-19
or you could relay outgoing email through a real existant email account at your ISP.

---

