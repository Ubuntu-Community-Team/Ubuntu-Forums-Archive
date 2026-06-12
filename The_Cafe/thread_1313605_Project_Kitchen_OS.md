---
title: "Project: Kitchen OS"
date: 2009-11-03
forum: The Cafe
---

### Post by e30drift on 2009-11-03
Long story short, I am a widowed, single dad working in the IT industry (IT Director) and I have a unique knack for cooking.  

I moved into my new apartment a few months ago and have finally amassed a decent amount of kitchen gadgets and essentials. The one thing that I hate is a pile of recipes printed out from the web and put into a binder and scraps of paper with recipes scribbled on them.  Last week, I got fed up with having the binder around and scraps of paper after spilling a bunch of hot soup on my binder, I raged all day.  Needless to say, my 3 year old was mad dinner was late.:cry:

Being the IT nerd that I am, I figured I would create a database full of recipes and import them in from various websites like epicurious or foodnetwork.  That turned out to an epic failure.   I hate coding to parse text... failed that Computer Science course... miserably!

Seeings how I have a spare laptop and 20 inch LCD collecting dust, I knew that this would be a great alternative to the binder!

So, here is what I got and would love some input from you guys...
**Hardware**
[LIST]
[*]Mount the LCD in a Portrait layout to a new kitchen cabinet door (stupid apartment life)
[*]Run cables to top of the cabinet
[*]Mount laptop to the underside of the cabinet or on top (haven't decided)
[*]Wireless Networking
[*]Wireless keyboard/mouse
[/LIST]
**Software**
[LIST]
[*]Ubuntu 9.10 - bare-bones installation (Gnome or KDE)
[*]Gourmet Recipe Manager
[*]KRecipe
[*]Firefox 3.5
[/LIST]


I created a VM in Virtual Box to test different apps like Gourmet Recipe Manager and Krecipe and with different flavors of Ubuntu: Gnome, KDE, server, mini and netbook remix
All are 32bit (no need for 64bit) and based on 9.10

The laptop I want to put this on is an old Centrino Duo 1.6Ghz, 1GB and a 60GB 5400 RPM HDD (btw, that HDD is dog crap slooooow)  More than powerful to run what I want, but I want the bare minimum apps and services running. *yes, I could upgrade the RAM and HDD, but trying to keep costs to a minimum and inspire others to recycle old hardware!  SSD, maybe :p

Here is what I have tried so far:
[LIST]
Ubuntu Server w/ Gnome core (super bare-bones Gnome)
Ubuntu NBR  - epic failure... interface is nice, but Gourmet doesn't look right.
Ubuntu (Gnome)
[/LIST]
Installed Gourmet Recipe Manager(GRM) on all 3.  Each one seems to be ok, but I am torn on GMR's Pro's and Con's...
Pro
[LIST]
[*]Easy to Use
[*]Import Feature - URL is nice!
[*]Export to XML
[*]Timers (makes hyperlinks with in the instructions to builtin timer)
[*]Multiple Timer support - VERY IMPORTANT!
[/LIST]
Con[LIST]
[*]Comes with NO recipes
[*]Import feature not as good as you think - Must edit and tag everything
[*]Crashes when importing recipes from TXT files (encoding issues)
[/LIST]

Need to test:
Kubuntu (Krecipe)
Ubuntu Mini - seems like a dead end, but I'll try it.

I know I can run KDE apps in Gnome, but installing the KDE packages in with Gnome seriously increases disk space usage and I have heard of cross platform issues with some apps and performance issues.  Plus I am too lazy to test that out.

I am installing Kubuntu in a VM as I write this, so I do not have any hands-on experience with KRecipe.  From what I have found on the googles, it comes with a Recipe DB(?) or connects to an online one(?).  Didn't see anything about timers or like how GRM does it.

Any input would be welcomed!

---

### Post by Cuddles McKitten on 2009-11-03
My suggestion would be Puppy since it's lightweight and easy to set up.  Then, since booting would be relatively prohibitive when you just want a recipe, have it hibernate rather than shutting down.

---

### Post by e30drift on 2009-11-03
> **Cuddles McKitten said:**
> My suggestion would be Puppy since it's lightweight and easy to set up.  Then, since booting would be relatively prohibitive when you just want a recipe, have it hibernate rather than shutting down.

I thought about Puppy, but I like the challenge to mod Ubuntu to do what I want it to do.  

I even tried Xubuntu, but I couldn't get past the 90's interface, but I digress.  

I was thinking that this could be the best kitchen appliance out of my arsenal.:p

Plus, I thought it would be bad *** to roll a final product as an ISO and/or VM appliance for Virtual Box or VMWare for others to use.

---

### Post by synicalx on 2009-11-03
> **Cuddles McKitten said:**
> My suggestion would be Puppy since it's lightweight and easy to set up.  Then, since booting would be relatively prohibitive when you just want a recipe, have it hibernate rather than shutting down.


Agree, you'll want something small and fast - I'm sure you can set it to Hibernate whenever the laptop lib is closed and wake up when it's open? (Linux noob here :p).

Also, if your mounting the LCD on a door, be sure to reinforce that hinges or get new ones and make sure the door is made out of tough enough material so that the screw don't end up dragging and eventually coming loose. I've had problems screwing cutlery (yes cutlery) holders into flimsy doors - after a month or to of use, it started to wobble around and after a year it toppled out - leaving sizeable holes in the door where the screws had moved around and shot my cutlery across the room...

---

### Post by drawkcab on 2009-11-03
I really like this idea but you need a touchscreen interface, srsly.  Build that and you actually have a marketable product.  Quit your job and start selling the kitchencomp.

---

### Post by e30drift on 2009-11-03
> **synicalx said:**
> Agree, you'll want something small and fast - I'm sure you can set it to Hibernate whenever the laptop lib is closed and wake up when it's open? (Linux noob here :p).

Also, if your mounting the LCD on a door, be sure to reinforce that hinges or get new ones and make sure the door is made out of tough enough material so that the screw don't end up dragging and eventually coming loose. I've had problems screwing cutlery (yes cutlery) holders into flimsy doors - after a month or to of use, it started to wobble around and after a year it toppled out - leaving sizeable holes in the door where the screws had moved around and shot my cutlery across the room...

The cabinet doors are made of a very dense particle board so that plus washers should help keep it on the door.  as for the hinges, I rarely open that particular door, so it should be okay.  Also, the door is held on with 3 hinges, so that should keep the door on with the weight of the LCD.  

The laptop will be out of sight completely.  I plan on setting up a timer to put it on standby after 1 hour of inactivity.  that will save on power and will have instantaneous boot ups/downs.  and the best part is that the screen is dead, so I'll be removing it from the hinge to get easy access to the power button in case I need to power it up.

---

### Post by e30drift on 2009-11-03
> **drawkcab said:**
> I really like this idea but you need a touchscreen interface, srsly.  Build that and you actually have a marketable product.  Quit your job and start selling the kitchencomp.

Touchscreen?  why stop there?  multi-touch is where it's at!!

Seriously though, I did think about investing in a touchscreen later on, but imagine getting dirty kitchen hands on the screen... and the cost of a touchscreen is pretty high, too.

I plan on wrapping the monitor in plastic wrap (saran wrap) or flush mount a sheet of lexan or plexi glass in the inner bezel.  
I already got this: [http://www.adesso.com/products_detail.asp?productid=390#]("http://www.adesso.com/products_detail.asp?productid=390#")
and an old logitech wireless mouse
Those will be wrapped as well too.

---

### Post by Xzallion on 2009-11-03
Maybe look into the new wacom tablets that support multitouch once the drivers develop for them?

Mount the wacom with the lcd and you would have a really snazzy interface for your lcd.

Just a thought.

---

### Post by e30drift on 2009-11-04
> **Xzallion said:**
> Maybe look into the new wacom tablets that support multitouch once the drivers develop for them?

Mount the wacom with the lcd and you would have a really snazzy interface for your lcd.

Just a thought.

Thought of that too.  I was hoping for a good onscreen keyboard to use with a multi-touch or touchscreen, but that would be too awkward. 

The solution I have is to build a slide out tray under the cabinet and mount that there and put the keyboard on it, secured with velcro tape. 

The main objective is to increase usable counter space without having a keyboard or binder of recipes getting in the way.

BTW, I did try out KRecipe and was quite disappointed.  There was an online database coming along, but was abandoned.  The import feature is so-so and there are no built in timers.

I had a friend come over and check out the progress, she likes it and noted that since the laptop will be running Linux, the whole XKCD punchline: "Sudo make me a sandwich" adds to the hilarity and awesomeness of the project!
[IMG]http://imgs.xkcd.com/comics/sandwich.png[/IMG]

---

### Post by Xbehave on 2009-11-04
> **e30drift said:**
> The laptop I want to put this on is an old Centrino Duo 1.6Ghz, 1GB and a 60GB 5400 RPM HDD (btw, that HDD is dog crap slooooow)  More than powerful to run what I want, but I want the bare minimum apps and services running. *yes, I could upgrade the RAM and HDD, but trying to keep costs to a minimum and inspire others to recycle old hardware!  SSD, maybe :p
That system is good enough to run any ubuntu distro, kubuntu or gnome will both run fine (with no desktop effects), the best workaround for the slow HDD is to not shutdown and just suspend when possible.

---

### Post by Frak on 2009-11-04
A tad bit off topic, but I just found my next project for testing out the new multitouch API Microsoft just released with 2010.

If it works, hey, I'll shoot the code your way and someone can try to port it from there. Planning on the MIT or BSD license. You may not be able to port the touch interface, at first at least, but it should run reasonably within Mono.

EDIT
Also, you're thinking about a Screen Scraper for scraping the recipes off of a page. Be aware that there are legalities involves with this.

---

### Post by DeadSuperHero on 2009-11-04
Honestly, KRecipe is turning out to be pretty promising. You could always try a stripped down KDE desktop.

---

### Post by e30drift on 2009-11-05
> **Mr. Psychopath said:**
> Honestly, KRecipe is turning out to be pretty promising. You could always try a stripped down KDE desktop.

I had high hopes for Krecipe...  the fact that it does not have a timer function built into the app like Gourmet, was a nut kicker for me.

I tested both out last night making these: [http://www.recipezaar.com/Nikuman-Butaman-Pork-Bun-225697]("http://www.recipezaar.com/Nikuman-Butaman-Pork-Bun-225697")
I ended up making 2 batches so I used Gourmet first and then Krecipe for the next.

Importing in Gourmet via URL was a pain since I had to heavily edit and tag all the different sections.

Krecipe was easier, but not as robust... since it does not have a URL import, I copied and pasted the text from the site into Gedit, saved as a txt file and imported it that way.  mild annoyance.

I got spoiled with the timers in Gourmet, so minus points on Krecipe.  I did post a feature request on their sourceforge site.  

I will admit, not having a binder floating around, my netbook, or (shudders) my damn ipod touch to read recipe directions was very nice. 

speaking of stripped down KDE, I couldnt find the terminal code to do that.  with gnome it's just "gnome-core"
Any help would be nice!

---

### Post by e30drift on 2009-11-05
> **Frak said:**
> A tad bit off topic, but I just found my next project for testing out the new multitouch API Microsoft just released with 2010.

If it works, hey, I'll shoot the code your way and someone can try to port it from there. Planning on the MIT or BSD license. You may not be able to port the touch interface, at first at least, but it should run reasonably within Mono.

EDIT
Also, you're thinking about a Screen Scraper for scraping the recipes off of a page. Be aware that there are legalities involves with this.

I am excited for multi-touch!  I am hoping the Linux community will pull through and come up with their own API.  MS one looks very promising, hopefully it won't go by the way side like WinFS...

As for Screen Scrapper... :twisted:

---

### Post by Frak on 2009-11-05
> **e30drift said:**
> I am excited for multi-touch!  I am hoping the Linux community will pull through and come up with their own API.  MS one looks very promising, hopefully it won't go by the way side like WinFS...

As for Screen Scrapper... :twisted:
I have a development unit from HP with the technology ([you can buy the retail ACTUAL ONE here]("http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&a1=Brand&v1=HP+TouchSmart&series_name=tx2z_series&a1=Brand&v1=HP+TouchSmart")). I have access to a serial port to monitor activity. Looks solid from this end. More info about multitouch here:

1. [Demo]("http://channel9.msdn.com/pdc2008/PC03/")
2. Actual developing of applications
   | - [Part 1]("http://channel9.msdn.com/posts/yochay/Programming-Windows-7-Multi-Touch--Part-1/")
   | - [Part 2]("http://channel9.msdn.com/posts/yochay/Programming-Windows-7-Multi-Touch-Part-2/")

Now, somebody make me my Linux equivilent!

---

### Post by Firestem4 on 2009-11-05
To the OP, Many people have recommended a touch screen which I think would be a great idea. But you may be REALLy interested in this if you are interested in a touch screen.
[http://alwaysinnovating.com/home/index.htm](http://alwaysinnovating.com/home/index.htm)

It is a RISC based table/laptop. The display can detatch and be used as a tablet. It also has a magnetic back for attaching to (eg: ) refrigerators!

It is a very good price too (you can order just the tablet or tablet and keyboard/battery).

Good luck with your project!

---

### Post by Bungo Pony on 2009-11-05
I wanted to do something like this. I tried to use an old Telxon touchscreen PC with a detachable keyboard and a built in speaker. It also had wireless built right in. The only thing that sucked was the screen. It was dim black text on a gray background, so it was almost impossible to look at.

I'll wait and eventually find something right for my kitchen :)

---

### Post by drawkcab on 2009-11-06
Hey, remember that random post-modern essay generator from a few years back?

Maybe you could build in an application that randomly generates new recipes?

---

### Post by e30drift on 2009-11-06
Well, I did some more research on the touch screen LCD's, looks like $400+, $500 for a good USB one.

As far as I can tell the "capacitive" ones are the ones to go for.  Resistive is the next best.  "Acoustic Wave" seems to be the cheapest, but could be the worst of the types.
[NewEgg.com LCD Touch Screen's sorted by ascending price]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010190514+1287517665&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=514&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=")

---

### Post by markbuntu on 2009-11-06
Recipies, meh
You need to get beyond recipies unless you are making cakes or bread or stuff like that.

---

### Post by -grubby on 2009-11-06
> **drawkcab said:**
> 
Maybe you could build in an application that randomly generates new recipes?

Uhh... could you clarify? That doesn't seem to make much sense.

---

### Post by Thirtysixway on 2009-11-06
I'm planning on writing a web app called Kitchentory that can track recipees, kitchen stock, utensils etc.  Inventory built on barcodes, recipees can look up barcodes and tell you what you have or don't have.  When you use something, scan it out and it gets marked at used.  Then a grocery list can be built from all the products marked as empty.

I have yet to build it, but I've been planning it out.  It would be very cool to have :) good luck with your project.

---

### Post by e30drift on 2009-11-09
> **markbuntu said:**
> Recipies, meh
You need to get beyond recipies unless you are making cakes or bread or stuff like that.

Breads and cakes, yes there is a need for recipes, but even foods that require more than 4 or 5 ingredients need them too.  

I don't know how often you cook, but I'll be damned if I have to start memorizing measurements and ingredients for even a few recipes.

This is just a side project I came up with after having trouble organizing my kitchen.

Next step is to create a LAMP server that manages my food inventory :KS

---

### Post by e30drift on 2009-11-09
> **-grubby said:**
> Uhh... could you clarify? That doesn't seem to make much sense.

for example: 

10 lbs rib eye steak
4 cups chocolate powder
3 tsp of pomegranate juice, peeled, crushed, slivered
1 cup chicken, zested
2/3 lbs milk extract



come on!  you get the idea ;)

---

### Post by e30drift on 2009-11-09
> **Thirtysixway said:**
> I'm planning on writing a web app called Kitchentory that can track recipees, kitchen stock, utensils etc.  Inventory built on barcodes, recipees can look up barcodes and tell you what you have or don't have.  When you use something, scan it out and it gets marked at used.  Then a grocery list can be built from all the products marked as empty.

I have yet to build it, but I've been planning it out.  It would be very cool to have :) good luck with your project.

DO WANT!!  I have been tossing that idea around for years.  My brother is a developer and getting his lazy butt to hop aboard has been painful.

Perhaps we can build off the current Gourmet Recipe Manager code and fork the whole project.  

I also had an idea the RFID tagged food items would be kick *** too.  but alas I live in the US, so that won't happen for years (or when ever 'forever' comes around).

---

### Post by FuturePilot on 2009-11-09
> **e30drift said:**
> for example: 

10 lbs rib eye steak
4 cups chocolate powder
3 tsp of pomegranate juice, peeled, crushed, slivered
1 cup chicken, zested
2/3 lbs milk extract



come on!  you get the idea ;)

Yes, but would it be eatable? That sounds disgusting :shock:

---

### Post by The Real Dave on 2009-11-09
I see that plenty have people have beaten me to the touch screen idea, but one piece of advice, if you do use a touch screen, take some cling film, and cover the screen with it. It should still recognise your touch through it I think, and the reason is that if you attack a touch screen monitor with floury/oily/whatever kind of cooking you do hands, it ain't gonna last long :)

---

### Post by drawkcab on 2009-11-09
> **-grubby said:**
> Uhh... could you clarify? That doesn't seem to make much sense.

[http://www.elsewhere.org/pomo/](http://www.elsewhere.org/pomo/)

Just refresh a few times.

---

### Post by markbuntu on 2009-11-10
> **e30drift said:**
> Breads and cakes, yes there is a need for recipes, but even foods that require more than 4 or 5 ingredients need them too.  

I don't know how often you cook, but I'll be damned if I have to start memorizing measurements and ingredients for even a few recipes.

This is just a side project I came up with after having trouble organizing my kitchen.

Next step is to create a LAMP server that manages my food inventory :KS

I cook every day and do not use recipes except for bread and cakes etc. A can of this, a handful of that, chop, slice, saute, bake, broil, simmer for 3 weeks... season to taste. That sort of cooking. it is never exactly the same twice but is always good. When you cook often enough you get a feel for it.

btw, there are industrial touch screens that are pretty impervious to anything that could happen in a kitchen except for maybe a grade three grease fire.

Here is an old favorite recipe that I used to make occasionally when I was in Dutch Harbor Alaska and the seafood was free.

Stuffed baby halibut

1 whole baby halibut, (about 2 ft long) filleted with head and tail and skin attached
Combine in a large bowl
meat from 1-2 king crabs, 5-6 snow crabs, 30-40 medium shrimp, 2-3 lbs large sea scallops, some cleaned chopped squid and  whatever other seafood is at hand
1 bag bread crumbs, 4 eggs + 1 jar mayonnaise or some hollandaise or bechamel sauce or both
Mix together until it sort of holds together add more bread crumbs eggs fish etc as necessary

Lay bottom halibut fillet with head and tail attached (top of fish) on a large baking tray skin down
Spread contents of bowl evenly across fillet
Lay on top fillet

Bake at 350 for 1-1/2 hours.
 
Serve, enjoy.

I like the random recipe generator idea. I think a little artificial intelligence engine could prevent serious cooking errors and would probably come up with some really interesting unique food combinations that would work.

---

### Post by e30drift on 2009-11-10
> **markbuntu said:**
> 

Here is an old favorite recipe that I used to make occasionally when I was in Dutch Harbor Alaska and the seafood was free.

Stuffed baby halibut

1 whole baby halibut, (about 2 ft long) filleted with head and tail and skin attached
Combine in a large bowl
meat from 1-2 king crabs, 5-6 snow crabs, 30-40 medium shrimp, 2-3 lbs large sea scallops, some cleaned chopped squid and  whatever other seafood is at hand
1 bag bread crumbs, 4 eggs + 1 jar mayonnaise or some hollandaise or bechamel sauce or both
Mix together until it sort of holds together add more bread crumbs eggs fish etc as necessary

Lay bottom halibut fillet with head and tail attached (top of fish) on a large baking tray skin down
Spread contents of bowl evenly across fillet
Lay on top fillet

Bake at 350 for 1-1/2 hours.
 
Serve, enjoy.

I like the random recipe generator idea. I think a little artificial intelligence engine could prevent serious cooking errors and would probably come up with some really interesting unique food combinations that would work.

that sounds fantastic!!  too bad halibut around here (DC Metro) costs an arm and a leg /lbs!  

Random recipe generator would be awesome if it knew the kitchen's inventory.

---

### Post by e30drift on 2009-11-11
I found that awesome tablet mod for the Dell Mini 9 and the guy bought his own resistive touch screen kit and added it on.

That got me thinking that there had to be other kits available to add to existing monitors...

[http://www.touchscreens.com/products-addon.html]("http://www.touchscreens.com/products-addon.html")

Seems kinda expensive, but there are others for netbooks, but requires totally voiding the warranty.  
[http://www.mydigitaldiscount.com/CategoryProductList.jsp?cat=Browse+By+Brand%3AHoda+Technology]("http://www.mydigitaldiscount.com/CategoryProductList.jsp?cat=Browse+By+Brand%3AHoda+Technology")

I'm wondering if I can fix up my old netbook to have the touchscreen, make it a tablet and mount that to the cabinet door...:P

---

### Post by odog87 on 2009-11-24
I have been slowly working on something like what you are doing! But I am also learning parts of linux (or rather ubuntu) at the same time. [here (click here)]("http://projects.shadedviews.com/?cat=11") is my progress so far. I should have more pictures after the holidays

I just felt that it was good to know I am not the only one that thinks like this, and wanted to share!

:lol:

---

