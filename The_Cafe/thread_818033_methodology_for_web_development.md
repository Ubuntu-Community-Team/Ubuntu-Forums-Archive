---
title: "methodology for web development"
date: 2008-06-04
forum: The Cafe
---

### Post by dynamethod on 2008-06-04
Hey there, 


Just a project for tech, part of this project is to choose a suitable "methodology" for a e-commerce based website, im not looking for "The Answer", but just wondering if i could get a bit of feedback from anyone out there in the IT industry, what steps you take and why you choose that methodology? im kinda thinking either prototype or spiral, but im not sure, feed back much appreciated

---

### Post by Barrucadu on 2008-06-04
I'm not doing it professionally, but I make the occasional site, and use this method:
[list]
[*]Think of an idea.
[*]Create a prototype of pages out of just XHTML and CSS.
[*]Split the design into template files.
[*]Begin to write the most basic code to string it all together (eg: database, error handling).
[*]Flesh out the rest of the site and create more advanced functions to use the basic ones to get the job done (eg: user handling, template usage)
[*]Bug test
[/list]

I use this methodology because it seems to work best, and since I start with the very basic and work up, rather than the very complex and work down, errors tend to be fewer as it is more difficult to make a mistake with something really simple.

---

### Post by frrobert on 2008-06-04
With an e-commerce website the two things I look at first is what are the business requirements (product type, how many products do they want to sell, how do they want to ship, how do they want to charge for shipping, how do they want to process payments, etc) and the customer's target budget.

I find many people that want a site to sell a product don't realize the cost of website development, so often I will recommend that they use a cms such as Zen Cart if it meets the technical requirements.  Often it is the most cost effective way to provide a website for a small business.  If zen cart will work for them then it is a matter of creating a template to give them the look that they need and want.

If I do web development without a cms I often design the database first, code second, and the look last.  The reason being the majority of my work is on intranet sites that really are databases with web interfaces.  My customers are looking for a system to do a task such as process an order for a phone so I look at the task first and the look last.  Also years ago I started out as a database designer and branched out to web design so that may be the reason I look at the guts first.

---

