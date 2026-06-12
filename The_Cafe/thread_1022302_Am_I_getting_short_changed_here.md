---
title: "Am I getting short changed here?"
date: 2008-12-26
forum: The Cafe
---

### Post by Kernel Sanders on 2008-12-26
I have a Virtual Dedicated Server with GoDaddy.

256mb dedicated RAM, 1GB "Bursted"
10GB HDD
CentOS

I host a single blog on it, yet most of the time it takes 5 seconds to load the homepage, and can sometimes be as high as 15 seconds. In contrast subsequant pages load mostly in a second or two, yet sometimes even those can take up to 5 seconds.

Is this normal for a VDS, or should everything load instantly, and GoDaddy is being especially rubbish?

---

### Post by melojo on 2008-12-26
I don't have a virtual dedicated server and it loads instantly.  Seems like they are having problems on their end.

---

### Post by Lightstar on 2008-12-26
GoDaddy is an awesome registrar, and a not-so-good host.
Their control panel is way too complicated too.
I'm in charge of a company's web site that uses Godaddy, it's a pain in the neck.  My personal host is leadhoster.com.

I just thought I'd post a reply, but I can't help you there, the company's web site uses small pages, not much database and etc.  Their pages load really fast on a VDS.  The issue might have to do with scripts or database maybe?

---

### Post by pp. on 2008-12-26
> **Kernel Sanders said:**
> 256mb dedicated RAM, 1GB "Bursted"
10GB HDD
CentOS

The described behaviour would be perfectly consistent with your OS and application stack occupying more than 256MB RAM.

Of course, using 256mb would take even longer, that being 256 milli-bits or about one fourth of a bit.

---

### Post by -grubby on 2008-12-26
I've never heard good things about GoDaddy's hosting. I'd go with something else. I use Linode for my own VPS.

---

### Post by melojo on 2008-12-26
Have you tried to do a traceroute to see if it gets slowed down somewhere between you and the server?

---

### Post by ithanium on 2008-12-26
GoDaddy is doesn't offer that great of a hosting service but their domain registering is good

---

### Post by Kernel Sanders on 2008-12-26
To those saying I should go elsewhere, I pre-paid for 2 years worth of non-refundable VDS hosting just a few months ago. I got 30% off if I did that, but even with the discount I now regret it :(

So I have until Late Summer 2010 before my hosting expires :(

Btw, if I ping my site, these are the results (with personal info removed ;) )

---

### Post by -grubby on 2008-12-26
> **Kernel Sanders said:**
> To those saying I should go elsewhere, I pre-paid for 2 years worth of non-refundable VDS hosting just a few months ago. I got 30% off if I did that, but even with the discount I now regret it :(

So I have until Late Summer 2010 before my hosting expires :(

Btw, if I ping my site, these are the results (with personal info removed ;) )

No matter how much the added cost, I always do it on a month-by-month basis so if I need to cancel I'm not locked in.

---

### Post by pp. on 2008-12-26
Have you consulted the folks at goDaddy about your response times, and what did they say?

---

### Post by Kernel Sanders on 2008-12-26
> **pp. said:**
> Have you consulted the folks at goDaddy about your response times, and what did they say?

"No problems our end - you should have a VDS with more RAM. You can't upgrade VDS's though, just add bandwidth, so you'd need to order a whole new VDS from us with more RAM from the word go - and no, we won't refund your existing prepayment or transfer it as it's your fault for not selecting the RAM upgrade option when you ordered the VDS, not ours."

---

### Post by pp. on 2008-12-26
IOW, the ISP says that the problem lies with your machine using too much RAM. Where, then, does your RAM go? It's not that 256MB is very tight for a headless machine, I'd think.

---

### Post by melojo on 2008-12-26
> **Kernel Sanders said:**
> "No problems our end - you should have a VDS with more RAM. You can't upgrade VDS's though, just add bandwidth, so you'd need to order a whole new VDS from us with more RAM from the word go - and no, we won't refund your existing prepayment or transfer it as it's your fault for not selecting the RAM upgrade option when you ordered the VDS, not ours."

If they are going to be like that I am going to switch my hosting to another company.  I was thinking of getting a vds or a dedicated but not from them.

---

### Post by Kernel Sanders on 2008-12-26
> **melojo said:**
> If they are going to be like that I am going to switch my hosting to another company.  I was thinking of getting a vds or a dedicated but not from them.

Good decision. GoDaddy ALWAYS try to upsell you. I had shared hosting initially with one blog and one forum. It wasn't long before there were periods of ridiculous slowdowns so I asked what the problem was. They said my "heavy database usage" was to blame, and that I should get a VDS. Heavy database usage? TWO databases constitutes "heavy"? According to their advertised plan, shared hosting allows TEN databases, and they are calling my TWO "heavy"? 

I ended up buying the VDS, but not for that reason thankfully, but because I needed the extra capacity anyway. I'll  be honest though, GoDaddy's VDS's are the cheapest on the market, and I think i've found the reason. They're oversold. My uptime is 100%, yet accessing my server pretty much takes 5 seconds per request. The page always loads, but no quicker than 5 seconds and occasionally longer. I feel as though I am watching my VDS light blink when I click on something. It always works, it just takes a few seconds. I feel as though there are too many VDS's set up on a single server. I suppose you get what you pay for though? To get any better i'd have to pay almost double elsewhere, which I can't afford. So this is the best VDS I can afford, it just isn't particularly speedy.

So, if you are looking for cheap, working, yet 5 second page load times then go with GoDaddy. If however you don't mind paying almost double for instantanious load times, then go elsewhere.

Hope this helped :KS

---

### Post by Tipo on 2008-12-26
Just curious, what blogging software are you running? Sometimes if you are running larger apps (sometimes wordpress, or rails apps) they take longer to load.

---

### Post by Kernel Sanders on 2008-12-27
Wordpress 2.7

---

### Post by matthew on 2008-12-27
I moved six sites to GoDaddy last week, and I am completely underwhelmed. They are all considerably slower, and it appears that GoDaddy has customized Apache rules that make mod_rewrite work in unexpected ways, if at all.

I only paid for one month, and unless things change rapidly, I'll be moving on.

---

### Post by matthew on 2009-01-04
Update: I have canceled my GoDaddy hosting account for all the reasons I and others previously stated in this thread. I am still using them for domain name registration and am happy with them for that. I have now switched to slicehost ([non-spam link]("http://www.slicehost.com/")) ([referrer spam link here]("https://manage.slicehost.com/customers/new?referrer=da7ad2389c7ad34ea2a7aa6fbae376fa")), built my own Ubuntu server, and am hosting my sites, email, and dns there.

---

### Post by kevin11951 on 2009-01-04
i have a godaddy site here: [http://fjstech.com](http://fjstech.com) and it seems to load fine, its drupal and not some small html site too.

---

### Post by matthew on 2009-01-04
> **kevin11951 said:**
> i have a godaddy site here: [http://fjstech.com](http://fjstech.com) and it seems to load fine, its drupal and not some small html site too.
Hey, your site does load very quickly! I wonder if they have good servers and bad ones. Like with most shared hosts, it likely depends on who else is hosting on the same server, and what they are hosting.

I am glad to hear at least one good experience with them. Thanks for speaking up!

---

### Post by pp. on 2009-01-04
> **kevin11951 said:**
> i have a godaddy site here: [http://fjstech.com](http://fjstech.com) and it seems to load fine, its drupal and not some small html site too.

Is there anything more to the site than that single page I see? That page would fit nicely into the amount of RAM mentioned before in this thread, I presume.

---

