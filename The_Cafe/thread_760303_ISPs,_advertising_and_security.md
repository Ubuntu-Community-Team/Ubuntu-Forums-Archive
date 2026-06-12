---
title: "ISPs, advertising and security"
date: 2008-04-20
forum: The Cafe
---

### Post by p_quarles on 2008-04-20
This was reported in several places over the past couple days, but I haven't noticed it being discussed here: ISPs injecting ads into error pages. In this one case, it introducted a huge vulnerability that was soon patched, but the basic problem with the practice is still there. 
[http://blog.wired.com/27bstroke6/2008/04/isps-error-page.html](http://blog.wired.com/27bstroke6/2008/04/isps-error-page.html)

Anyway, I find this pretty worrisome, particularly given how little attention many people pay to online security.

---

### Post by thisiam on 2008-04-20
I could see my ISP doing this, they have a cable and internet monopoly here so you see their commercials all the time, and  i just can't go back to dsl.

---

### Post by smoker on 2008-04-20
companies like this are only interested in getting their grubby hands on more internet advertising revenue, and as usual, masking it as 'a service to enrich the customers browsing experience' or some such crap. security will never be a priority over making a few quid!

---

### Post by Seisen on 2008-04-20
Wow companies will do anything to make money off of there users,I think I am glad I use Opendns rather than my ISP's DNS servers.

---

### Post by Dr Small on 2008-04-20
> **Seisen said:**
> Wow companies will do anything to make money off of there users,I think I am glad I use Opendns rather than my ISP's DNS servers.
+1
I use OpenDNS servers here, too.

---

### Post by SuperSon!c on 2008-04-20
what kind of speed increase/decrease do you see generally using opendns?

---

### Post by SuperSon!c on 2008-04-20
and from the article:

> "The entire security of the internet is now dependent on some random-*** server run by some British company," Kaminsky said.

lol

---

### Post by smartboyathome on 2008-04-20
I wonder, will I get this if I am behind a router?

---

### Post by Dr Small on 2008-04-20
> **smartboyathome said:**
> I wonder, will I get this if I am behind a router?
Most likely since all requests are passing through your ISP.

@SuperSon!c, I have seen no real change in DNS requests since using OpenDNS. No noticable difference either way.

---

### Post by SuperSon!c on 2008-04-20
thanks, doc

---

### Post by Mazza558 on 2008-04-20
Erm, OpenDNS also has ads on the error pages - except they're just Google ads.

---

### Post by Dr Small on 2008-04-20
> **Mazza558 said:**
> Erm, OpenDNS also has ads on the error pages - except they're just Google ads.
Rarely do I ever get an error page though :p
Also, I can meerly ban google in my /etc/hosts file anyhow.

---

### Post by p_quarles on 2008-04-20
Of course, I don't think it's security-conscious *nix users who are going to be the victims of junk like DNS poisoning. Even if we were, we'd probably realize what happened sooner rather than later.

It's the millions of people who don't know what a DNS is that are really vulnerable to the kinds of scams this could make possible. It's definitely worrisome.

EDIT: Just found [this summary](http://news.slashdot.org/article.pl?sid=08/04/20/1524246) on Slashdot, and thought it was an interesting corrolary. Scheier's insights are usually pretty right-on, so I imagine he's right about this trend. What's disturbing about the Wired report is that it seems some vendors want to bundle *exploits* into their software, and taking advantage of ignorance to get away with it.

---

