---
title: "Creating a backend that supports processing orders placed via the Internet"
date: 2019-11-10
forum: The Cafe
---

### Post by suomalainen on 2019-11-10
Hello Ubunteros!

I thought to post this question here as it seeks to find information on a subject I would like to learn more about.

When a framework is used to build/support backend development of a web site are there frameworks that can assist in creating the order processing that would be needed  in order to process incoming orders or does this need to be built from the ground up?

Thank you,

Suomalainen

---

### Post by jetsam on 2019-11-10
For open source solutions, it's MySQL databases for the most part, with the interfacing between the database and the client programs often provided by one of many many web frameworks.  That part is a bit of a maze to navigate, but you might find the Django, Drupal, or even Libre Office Base web sites of interest to research.

Word-press I believe has a prepackaged web store client solution that's almost certainly worth looking into.  The database management isn't very difficult and can usually be done by anyone with reasonable IT skills.  The middle-ware, though, is a bitch to create and debug.  It's probably better to start with a prepackaged solution to that part, at least at first.

---

### Post by mastablasta on 2019-11-11
for webshops there are plenty of opensoruce solutions. i am not sure why people always try and invent the wheel.

i recommend giving OpenCart a look. there are also Zen Cart and Magento and a few others.

as mentioned there are also ecommerce modules for website like Drupal, Wordpress, Joomla...

---

### Post by sdsurfer on 2019-11-11
> **mastablasta said:**
>  i am not sure why people always try and invent the wheel.

Precisely. I've been a developer for over 25 years, and therein lies "kinda sorta" an answer.

Mostly it's because they "can't get it to work," or "it's almost there but can't do that one thing that's important to us," or it's a matter of trust - believe me, I've seen code bases that would make your head explode. So they decide to do it themselves because they think they might be able to do better, or more efficient, or more specific to their needs.

The problem is, even as long as I've done this, there are hundreds, thousands of developers out there way smarter than I am. They work in open source or multi-developer environments where each method and class is examined by many eyes for vulnerabilities and they are routed out and corrected. When you do it yourself, you're in a silo and may be coding in super big mistakes you'd never thought of.

They've done most of the important stuff already - infrastructures, customization, many of them in compliant design patterns that are just plain beautiful (well to me, anyway.) And most importantly, they have addressed the really really huge thing - security of their apps (most of them.)

> are there frameworks that can assist in creating the order processing  that would be needed  in order to process incoming orders or does this  need to be built from the ground up?

See below - Yes, "strictly shopping cart solutions" have done the work to make payment integration/processing as painless as possible.

All that said, the shopping cart framework you choose should have the following attributes. I'm going to mention only open source PHP solutions simply because they have the widest reaching codebase and developer base for web apps. If you decide to go with a different language, it begins to get very specific as to your choices of developers and solutions (and often expensive.)

- **Complete, Current, and Correct Documentation**. This one is first on my list because as a developer it is really the **Most Important Thing.** If you find yourself searching a code base and trying to figure out what it's doing, you have already found why you shouldn't be using this framework.

- **Pluggable. **This word always brings Wordpress to mind, and with good reason (although out of the box, W.P. has other problems.) Wordpress has always been pluggable and hookable from the start, allowing you to add plugins and modules your users can enable or disable through admin. IMO the two problems with Wordpress are 1) out of the box it is very heavy and does too much. The first thing I do with a Wordpress install is remove a lot of the stuff a site will never need and go through the theme being used and kill a lot of the overhead. 2) Second is in most themes it tries to be everything to everyone, and this makes for a lot of overhead.

-** OOP/MVC based.** (Object oriented, Model/View/Controller.) This is by far the mechanism that enables the second item above. Wordpress didn't really start out this way, but it's moving in that direction. Coders who work in OOP are far more likely to respect standards and keep the code current with PSR's as they evolve. Even more important is that since we're all coding to a specific set of rules and design patterns, another developer can come in behind and grok exactly what it's doing, know where to look to add functionality, and get more done in less time.

**- Easy to Work With. **You shouldn't have to be a 25 year coding vet to install, configure, and work with a framework within a couple hours or less. If you try to run an install and wind up spending half a day figuring it out, it's probably not the framework for you.
[B]
- East of Payment Integration.[/B] Since you mentioned Ecommerce, this is a **HUGE** consideration.

**Some Popular Cart Solutions**

**- Wordpress -** this blogging platform is loved and hated mmm, pretty much equally. Personally I like it, once I use the hooks to remove a lot of stuff. Documentation is thorough and excellent for most usage. The real problems with WP lie in the themes and plugins users/developers install, not Wordpress itself. Don't go nuts with plugins, learn their ins and outs, learn to clean up themes, it's a pretty good solution that can be optimized and not so bloated. I personally use an extremely optimized WP install with the WooCommerce plugin and frankly, I never have to touch WooCommerce unless I'm updating templates. Saved me tons of time and headaches.

**- Magento **- because you mentioned Ecommerce, this is high on the list and one of the premiere Ecommerce solutions. There is a community edition and a paid edition, your mileage may vary.

**- Xcart -** I've messed with a few installs and didn't like it much, I recall "trying to do something" that was not supported directly by the software. But that doesn't make it bad, a lot of people use and love Xcart.

**- Zen Cart** - This is a popular one too, originally based on OsCommerce. Avoid osCommerce like the plague (IMO,) it is a hosted solution and in my experience a nightmare, dated, and poor support. Zen Cart does not suffer from this horror.

The deciding factor is, well, you're going to have to do the work and see what will work for you. :-D Do a search for PHP Ecommerce Solutions and start installing. :-D

---

### Post by jetsam on 2019-11-11
This is a bit speculative, but I think probably the business model or lack thereof of web development companies is responsible for the need to constantly reinvent the wheel...  

Nobody quite trusts anybody else's code, because literally everybody is trying to monetize their products without actually charging anybody any money for them...  
Thus hidden trackers, data gathering, and other ills of the modern internet get stuck in formerly benign objects like url addresses and tiny transparent gif files.  Since it's so easy to sneak junk like that into simple data, let alone into code... yeah...  

I think I'd reinvent the wheel, too...  If I ran a tire factory, I surely would.

BTW, great post, sdsurfer.  Thanks for sharing your experience.

---

### Post by mastablasta on 2019-11-12
> **jetsam said:**
> 
Nobody quite trusts anybody else's code, because literally everybody is trying to monetize their products without actually charging anybody any money for them...  
Thus hidden trackers, data gathering, and other ills of the modern internet get stuck in formerly benign objects like url addresses and tiny transparent gif files.  Since it's so easy to sneak junk like that into simple data, let alone into code... yeah...  


well ultimately you have to trust someone. otherwise life would be too expensive to live. or very and super modest (like Diogenes maybe).

imagine you have to make your own os, build your own car, your own appliances, your own TV, your own PC (i mean form scratch) and all apps on PC would be your own. just because someone might put something in there.

as mentioned above there is a solution with open code that many see an vet. with Ubuntu for, example, we know that someone from the forums jetsam might come along and post a bug saying why is this network data , IP address, flowing from my PC to Cannonical and Google servers. everyone would jump on it. if nothing else to see what is going on and identify the data.

anyway my frustration comes form my professional dealings with developers. we have this thing here that whenever possible they create their own apps. so what happens is the app we need urgently takes 7 years or more to develop (afterall they are also developing other stuff concurrently), and as a bonus it is missing the requested features in the production version. then i see FOSS app online - with all needed features. an app that is already used by large companies.  and we could have it up and running in max 1 month (2 weeks for the link to ERP database) and 2 more weeks of testing. at least for the features we need urgently.

i realise the risks but at least we could increase productivity instead of doing ridiculous jobs that computers could do a lot faster for us.

i mean if they doubt FOSS they should try the Oracle solution for example. and pay for it.

---

### Post by jetsam on 2019-11-12
Yep ;)

You might find this presentation interesting if you have an hour or so to spend:

It's the same subject, but the new hardware IOT side...
[URL="https://www.youtube.com/watch?v=cAHWXy12c54"]
Elliot Williams: Nexus Technologies, or How I Learned to Love WiFi[/URL]

> The only two things wrong with the internet of things:
1.) The Internet
and...
2.) The Things

The first 20 minutes or so is the most interesting unless you want to DIY automate your home without being spied on by Amazon, Facebook, Google, and/or the odd intelligence service...

...watch the whole thing.  The best parts are the demos and payoff at the end :)

---

