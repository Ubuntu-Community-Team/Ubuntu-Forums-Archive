---
title: "Project Management / Scheduling?"
date: 2007-09-12
forum: The Cafe
---

### Post by rivalarrival on 2007-09-12
Before I go out and re-invent the wheel...

I'm looking for a project management solution for a LAMP server. The ones I've found would perform more than adequately, but the interfaces are WAY too clunky for my projects.

I expect I'll have to build something custom (which doesn't really scare me) but I would like some guidance on where to get started. I just got dotproject running, but I've got absolutely no qualms with killing it for another system. 

Here's what's going on:

I've got about a dozen clients, each one orders basically the same, simple project. (a drive-by property inspection) Each project consists of the same 6 tasks that must be completed in order.

I'll have several employees who should be able to select these tasks on a first come/first serve basis. For accounting purposes, I need to know who completed what task on what project. Note that I am NOT assigning these tasks, my employees will be accepting them one-by-one, so an interface typical of project management systems is perfectly suitable here.

I might get 5 orders in a day, I might get 100 orders in a day. I need an interface that is conducive to inputting at between 1 and 10  projects at a time without having to go back and forth between multiple pages/tabs/etc. 

Basically, I need to be able to enter an address, and due date, (the two of which would uniquely identify the project) a company name, and a dollar amount. It should automatically record the current user's name and the date/time the project was entered. 

Thanks in advance!

---

### Post by caseydk on 2007-09-12
Hi, core dotProject contributor here...

If you're not tracking time on the tasks and/or the tasks are either done or not done (eg. you're not concerned about a task being 50%), it sounds like dotProject might be overkill for you.... even if you turn off some of the extra modules, etc.

Something like Basecamp (or ActiveCollab?) might be a better fit for quick task sharing and updating.

Regardless, if you have any questions, let me know.

---

### Post by curuxz on 2007-09-12
have you looked at SugarCRM

since you are looking at orders as well as tasks and tracking the values of orders then it may be an idea, if a little complex at first :)

---

### Post by rivalarrival on 2007-09-13
The jobs this will manage are just one small fraction of all the work we do, and other projects will benefit greatly from the dotProject system. I'm not too worried about under-utilization.

Basecamp is too expensive, and I like doing things in-house wherever possible. 

SugarCRM looks like it suffers from the same "deficiencies" as dotProject - The one-at-a-time project handling that is going to kill our productivity.

Really, all I need is a better way of creating new projects - My clients are going to send me an e-mail or post orders on their sites - I need to have a window in the background while I check my e-mail or visit my client's websites, ready to accept multiple orders. When I'm done figuring out what my clients want me to do, I go back to the window, hit submit, and it drops all those projects into the database, along with their associated tasks.

All I'm familiar with is M$ Access - If I was doing it with that, I would build a form that was basically a datasheet view of the project table, so I could create several projects simultaneously, and have it auto-populate the tasks table with the 6 tasks for each project I entered. 

Anything pre-built? Anything that would be fairly easy to customize like this? Or should I just get off my lazy hind end and learn PHP? :)

Thank you for your advice and recommendations!  I really appreciate your response!

---

