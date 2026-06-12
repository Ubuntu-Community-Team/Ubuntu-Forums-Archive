---
title: "What goes into maintaining a website?"
date: 2015-11-11
forum: The Cafe
---

### Post by cody27 on 2015-11-11
I'm learning, well re-learning HTML, and learning CSS and JavaScript. It's the most excited I've been about "coding" in many years now. 

But I feel like I'm massively overthinking this.

Do you just check into your code every now and then? Is there anything you have to do a a front-end developer to help with the back-end?

I realized I've never thought about what is basically the business side of being a front-end developer. 

I had in my mind that you're a new, self-taught front-end developer that started working for a local small business, developing and designing their site. 
What's expected of you?
What do you do every day when you go into work?

What about freelancers? Do they write the code and then aren't expected to check up on it?

I hope these questions aren't too dumb :lolflag:

---

### Post by SeijiSensei on 2015-11-11
Many people rely on "content management systems" like Joomla, WordPress, or Drupal to build sites rather than writing everything from scratch.  I use WordPress for blogs and occasional other sites, but in general I write complete web applications from scratch with a combination of HTML, PHP, and a backend database, usually PostgreSQL.  In most cases the types of sites I'm developing don't lend themselves to a CMS.

For instance, I once wrote a web application to allow patients to request appointments with doctors at a community health center.  The site had to meet HIPAA privacy and security requirements, so I had to write routines to encrypt/decrypt all the transactions before storing them in a database.  Because the system was not tied directly to the health center's own databases, the patient's request had to be processed by a human and an email sent in reply. We could not include any of the details of the appointment in the email, so we included a specially encoded link in the email that the patient could click on and view the appointment after logging in with a username and password.  That meant I had to design a password-retrieval system as well.  In addition I wrote a separate administrative interface for the appointments staff to use.  All of this was so customized to the client's needs that it had to be developed from scratch.  However when the time came for the health center to build a new public website, it was written by a team that used Drupal.

A simple site can be quite static.  I host a site for a friend who is a psychotherapist.  It hasn't changed since it went public.  Other sites are "dynamic" and typically rely on an SQL database to handle logins, form data, and so forth.  Even then once the site is designed it may not need new content for quite some time.  I had to enable the staff at the health center to add or remove doctors from the physician list, but they weren't able to change any of the other content on the site.

In answer to your last question, I am a freelancer. While clients typically think buying a website is like buying office supplies, I usually try to negotiate an ongoing service contract to cover bug fixes and the like.  On simple sites like the one for my therapist friend, there isn't much need for that.  On a complex web application that plays an important role in the organization's functioning, a service contract makes more sense.  Clients typically have no understanding of the complexity that hides behind the pages that they view.  Even simple functions like logging in requires a database to hold the users' information and methods to collect the login information, authenticate users, retrieve forgotten passwords, and so forth.  Most clients think that happens "magically."

The most complicated site I've ever designed supports a game I and my friends play during the NCAA basketball tournament.  The actual page design wasn't that hard, but the backend database is complex.  It has many related tables with data on the teams, how they are bracketed, which ones each user selects, and the results of each round of the tournament.  I learned a lot of SQL designing the queries that link these tables together and produce the required reports.

---

### Post by grahammechanical on 2015-11-11
I have no experience about what is being discussed here but if we are examining supplying paid for services I think that should also include some form of user training even if it just a few printed pages in a binder.

You may get complaints the system is broken when it is the user that does not know how to do things. The oblivious things are not obvious to many people. Such as, always replenishing the printer paper tray when printing reports. I have fixed a number of "broken" computers by filling up the printer's paper tray. 

Regards.

---

### Post by Lars Noodén on 2015-11-11
I used to do that kind of work, but it is a while back so I don't remember the exact figures.  The ongoing maintenance was always a line item written into the initial contract and covered a specific period of time, with conditions for extending if needed.  The more familiar you are with the site's components the more accurate estimate you can make.  

If you're running a CMS, then you'll have to decide whether it is you or they who will do the obligatory updates.  The more complex it is, the more you'll have to work to maintain it.  So, keep it simple.  Avoid moving parts, including javascript.  For simple sites, XHTML+CSS+SSI is enough.  If you must have moving parts, including PHP, keep them to a minimum.  And if they don't need a CMS, don't saddle them with one, because if it's not there it can't break.  

CSS is great but, like with everything else, keep that simple too.  Some widely distributed CSS files get so big that they start imposing on a noticeable chunk of bandwidth.   Those are hard to detangle, especially if you spent some time away from them, costing a lot of time.  

Also, remember to focus on usability and accessibility during the initial design.  Focusing on both will future-proof the site a bit.

---

### Post by mastablasta on 2015-11-12
when you have it all setup up it practically maintains itself :P

---

### Post by Habitual on 2015-11-12
The term "Maintaining" needs refinement and I think you are massively over thinking this.

"The 'site' needs magic_quotes in php 5.2.xx" vs. "The homepage logo is 42 pixels too wide."

---

