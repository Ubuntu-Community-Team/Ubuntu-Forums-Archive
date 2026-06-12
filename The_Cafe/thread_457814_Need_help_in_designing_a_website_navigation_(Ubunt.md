---
title: "Need help in designing a website navigation (Ubuntu/Linux related)"
date: 2007-05-29
forum: The Cafe
---

### Post by H.E. Pennypacker on 2007-05-29
I have been talking to DoctorMo about a new website that would help people in making the right hardware choices.  I explained to him that, currently, a Linux user has to go from one website to another to make sure that a piece of hardware is supported, and supported well.  If I want to know that a printer works well, I first have to go to linuxprinting.org, and then I have to switch back to Ubuntu's forums to see what other members have said.  This is a horrible system, and it is not helpful.  Many times, you will not find adequate and thorough reviews of hardware, either.

Now, at this point, DoctorMo and I (correct me if my usage is wrong) are talking about what type of navigation would be good for the website we have in mind.  For example, how would you go from the homepage to the hardware you're interested in.  What is the hierarchy?  

My idea follows newegg.com's navigation. Select hardware type > option 1 > option 2 > option 3, and view the hardware item. Of course, depending on the type of hardware, the options will vary (e.g. hard drive size, printer features, wireless card capabilities, etc.).  Newegg.com shows the hardware item, and the reviews to the right, all on the same page, with details on the hardware item too.  It is all very convenient.  

Since this website is directed at all of you, I would hope to receive suggestions and ideas.   What website navigation would work well here?  What real life websites (provide URL) do you like using?
[B][I]
Please keep this thread on topic[/I][/B].  Many threads go off topic.

---

### Post by aysiu on 2007-05-29
H.E. Pennypacker, this is an excellent idea, and I love the kind of feedback you're eliciting (or hoping to elicit).

I think the navigation should go at least one of two ways:

**1. Click on a major category** (printer, wireless card, etc.) and immediately get a list of all printers or wireless cards known to work with Linux--with the *most compatible* at the top of the list (works out of the box) and the more problematic ones at the bottom (works with some tweaking).

**2. Search for a particular model or manufacturer and see a rating** (6 - works perfectly, 5 - works perfectly with recent kernel versions, 4 - works perfectly after tweaking, 3 - works partially after tweaking, 2 - doesn't work at all, 1 - compatibility unknown).

I'd be interested to see how others respond.

---

### Post by macogw on 2007-05-29
I like the Newegg way, and Aysiu, I don't know if you've been on Newegg, but they do order the items that are found in the filters you've selected in order by how they've been reviewed by buyers.  So if you go Newegg-style and then have Aysiu's "prioritize by compatibility" for what's displayed for the items as you go through filters and once you've got all the filters in place, that'd be a good system, I think.

---

### Post by Tux Aubrey on 2007-05-29
I like your idea and would certainly use such a site.  I wouldn't know good web design from game fishing, but aysiu's suggestions sound right to me.

I'd like to also know:

a) whether the manufacture supports linux (ie. provides OS drivers or proprietary drivers); and

b) links to "mainstream" reviews that test Linux compatibility (I regularly lobby Australian magazines to get them to include Linux info in their hardware reviews and it would be good to see any that do being acknowledged by someone other than a middle-aged wanna-be geek)

Many of the Linux hardware sites are certainly difficult to use and confusing for average users - they appear to place a high priority on distro-specific comments.  I don't know how you can handle this without it becoming overloaded.

I assume DoctorMO's involvement means that Dohickey information will also be available through your site?

---

### Post by lyceum on 2007-05-29
I am currently working on a site to help new users chose the software they need. When they type a program/need into the search engine they will get a list FOSS programs that will do the job, ex. type PhotoShop and you would get GIMP, InkScape, Xara, CinePaint, etc... Click on one and there would be some info at the top from the product's website, some info from Wikipedia and links to both in case they want to read more. Under that would be what OS platforms the program runs on (Ubuntu/Mac/Windows). Below that will be a place for people to write reviews and rate with stars. The more starts a program gets, the higher on the list it will be when the search engine is used. There will also be links to how to install pages. 

I would recommend doing something similar for your site. You may want to skip the Wikipedia part, unless you want to tell the user what the part does (in case they are new to computers). I would love to have a site where I type Wifi info a search engine and the highest ranking just pops up.

---

### Post by Elijah on 2007-05-29
I'm thinking of doing the same hardware database site.. but only for our country. I had to filter out other hardware that won't be available from where I live. So I guess maybe a filter for location would be great for availability if one is shopping around and don't want to waste time checking if it's available on their stores.

---

### Post by seshomaru samma on 2007-05-29
I think if you want to make it very newbie friendly, you can also add which distro and which addition auto-detects the hardware.
for example i have a laptop dual booting debian etch and feisty. etch didn't pick up the wireles card (ipw2200) , feisty did.

---

### Post by lyceum on 2007-05-29
> **seshomaru samma said:**
> I think if you want to make it very newbie friendly, you can also add which distro and which addition auto-detects the hardware.
for example i have a laptop dual booting debian etch and feisty. etch didn't pick up the wireles card (ipw2200) , feisty did.

+1

This maybe a bit hard with so many distros, but it would be awesome to see. It may have to start with just the most popular ones from Distrowatch.

---

### Post by H.E. Pennypacker on 2007-05-29
> H.E. Pennypacker, this is an excellent idea, and I love the kind of feedback you're eliciting (or hoping to elicit).

Hopefully, it will gain pace, and others will help out in the making of this website.

> 1. Click on a major category (printer, wireless card, etc.) and immediately get a list of all printers or wireless cards known to work with Linux--with the most compatible at the top of the list (works out of the box) and the more problematic ones at the bottom (works with some tweaking).

This is certianly possible in that a rating system can take care of hardware item placement.  If you search eBay, you can have results organized by price.  It should be relatively easy to achieve. 

> 
2. Search for a particular model or manufacturer and see a rating (6 - works perfectly, 5 - works perfectly with recent kernel versions, 4 - works perfectly after tweaking, 3 - works partially after tweaking, 2 - doesn't work at all, 1 - compatibility unknown).

I prefer the star system.  You look up something, and you check out the number of stars it has.  Also, the kernel version is going to be a problem, because it would, from what I can tell, strain the website.  Not only must the website take into account all the hardware that is out there, but it also has to organize things by distributions.  If we start talking kernels, that would be a massive project.  It is fair to assume that most Linux users maintain fairly updated systems (recent kernel version), which would take care of this problem.  You don't really hear people saying they still use Hoary.

> a) whether the manufacture supports linux (ie. provides OS drivers or proprietary drivers); and

This gives me an idea of an entirely different section for the website: a place where people will be able to rate manufacturers.  For example, Intel will have much better placement than Broadcom.  Since manufacturers tend to be consistent in the level of Linux support they offer for their different hardware, it makes sense to rate them in general.

> b) links to "mainstream" reviews that test Linux compatibility (I regularly lobby Australian magazines to get them to include Linux info in their hardware reviews and it would be good to see any that do being acknowledged by someone other than a middle-aged wanna-be geek)

It may be easier to ask website visitors to provide those links, because I don't know how that would be integrated into the website.  Another problem is whether the external reviews you want linked to will still be available over time.  It is possible for this conceptual website we're talking about right now to link to external reviews (reviews from other websites), but who knows whether those reviews will be around or not in a few years.

Maintaining links to external reviews seems burdensome.  

> 
Many of the Linux hardware sites are certainly difficult to use and confusing for average users - they appear to place a high priority on distro-specific comments. I don't know how you can handle this without it becoming overloaded.

You're absolutely right about that.  We're talking a huge database with many filters (filters based on distro, ratings, etc.).  This type of project could not sustain itself without serious support from the community. 

> I'm thinking of doing the same hardware database site.. but only for our country.

Location is too much.  Besides, if HP offers a printer in New Zealand today, how do we know that printer won't be gone next year?  We can't possibly know what hardware is available in which country, and for how long that hardware is going to be available.  

> 
I think if you want to make it very newbie friendly, you can also add which distro and which addition auto-detects the hardware.

As a matter of necessity, distros would have to be included into this database.

Please keep offering ideas.  The more ideas, the better.

---

### Post by maniacmusician on 2007-05-29
> **H.E. Pennypacker said:**
> I have been talking to DoctorMo about a new website that would help people in making the right hardware choices.  I explained to him that, currently, a Linux user has to go from one website to another to make sure that a piece of hardware is supported, and supported well.  If I want to know that a printer works well, I first have to go to linuxprinting.org, and then I have to switch back to Ubuntu's forums to see what other members have said.  This is a horrible system, and it is not helpful.  Many times, you will not find adequate and thorough reviews of hardware, either.

Now, at this point, DoctorMo and I (correct me if my usage is wrong) are talking about what type of navigation would be good for the website we have in mind.  For example, how would you go from the homepage to the hardware you're interested in.  What is the hierarchy?  

My idea follows newegg.com's navigation. Select hardware type > option 1 > option 2 > option 3, and view the hardware item. Of course, depending on the type of hardware, the options will vary (e.g. hard drive size, printer features, wireless card capabilities, etc.).  Newegg.com shows the hardware item, and the reviews to the right, all on the same page, with details on the hardware item too.  It is all very convenient.  

Since this website is directed at all of you, I would hope to receive suggestions and ideas.   What website navigation would work well here?  What real life websites (provide URL) do you like using?
[B][I]
Please keep this thread on topic[/I][/B].  Many threads go off topic.
Is this going to be the interface for the Dohickey website?

I do like the idea of browsing by hardware, it's handy. I believe martin is also going to have search functionality for users searching for a specific model.

---

### Post by DoctorMO on 2007-05-29
Hello all,

Dohickey client is an application that allows you to review the hardware you have, rate your hardware and correct any hardware information; this information is then sent back to the dohickey server which contains the searching, browsing and general administration of all the hardware data collected from the users and web surfers. The idea is to prompt client users to have the interest in filling in the missing information about their hardware so that anyone else with that same hardware will also receive more detailed information that would ordinarily be available from plain detection.

We have 4 different ways to access hardware information and review information:

 1) Through the Dohickey client - Displays information on your current hardware
 2) Search - Search for a specific name, id, description etc
 3) Browse by Manufacturer > Model List
 4) Browse by Major Type > Manufacturer List + Model Lists (best first)

The idea of having a boolean for hardware vendor support is entirely possible, add a value to your dohickey client (edit any old hardware) and see how it looks and let me know if it looks good. I'll add it to the default fields for the next version. hopefully by then field changes will go to the server directly.

I'd really like for any interested parties who wish to be involved with creating the server side to join the dohickey-server mailing list so we can talk about the direction and with all your help I will be more sure of completing the server side faster.

Mailing lists: [http://sourceforge.net/mail/?group_id=177020](http://sourceforge.net/mail/?group_id=177020)

---

### Post by H.E. Pennypacker on 2007-05-29
> Is this going to be the interface for the Dohickey website?

I guess so.  It wouldn't make sense to have two separate websites.

> 
I do like the idea of browsing by hardware, it's handy. I believe martin is also going to have search functionality for users searching for a specific model.

In that case, why not have a general search feature?  A search feature that searches for anything (specific model, manufacturer, capabilities, etc.).

> 4) Browse by Major Type > Manufacturer List + Model Lists (best first)

I can understand that, for some people, selecting the right manufacturer is important, but for me, it is not.  I don't care what the manufacturer is as long as the hardware works.  I am not a brand name person either.  Since the results will produce the best compatibility anyway, why does anyone care about the manufacturer?  I don't get it.

---

### Post by DoctorMO on 2007-05-29
I edited my first post with some general dohickey info.

> I can understand that, for some people, selecting the right manufacturer is important, but for me, it is not. I don't care what the manufacturer is as long as the hardware works. I am not a brand name person either. Since the results will produce the best compatibility anyway, why does anyone care about the manufacturer? I don't get it.

A small list of manufacturers at the top as a small index and then a major list of  hardware sorted by rating NOT manufacturer. the list at the top is more a list of recommended hardware makers so they would have to have a general rating. i could set it so only makers that score above a certain amount would be visible or I could scrap it and just display the list of hardware in that category.

Do you think it's worth listing all types? because some types are 'Chipsets' it's not like you going to be able to choose a chipset unless your in the business of picking a motherboard.

---

### Post by maniacmusician on 2007-05-29
I think it would be good to have a combination of the newegg style browsing, and being able to narrow down your results with a search (or the other way around)

---

### Post by H.E. Pennypacker on 2007-05-30
> Do you think it's worth listing all types? because some types are 'Chipsets' it's not like you going to be able to choose a chipset unless your in the business of picking a motherboard.

I believe in having many different filters, but definitely no chipset categories.  You and I communicate referring to chipsets, but ordinary people don't.  People don't say "Hey Joe, I bought a 123 chipset XYZ."  Instead, you'd hear "Hey Joe, I bought a brand new Intel wireless card."  The website should not be that technical.

> I think it would be good to have a combination of the newegg style browsing, and being able to narrow down your results with a search (or the other way around)

I concur on having a highly flexible website with many search capabilities.

---

