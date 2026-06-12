---
title: "Employee Training Tracking"
date: 2008-01-08
forum: The Cafe
---

### Post by timmy22 on 2008-01-08
Hi folks,

I've googled about, and searched in the forums, but am not having much luck. I'm looking for an employee training tracking database for a small business (less than 100 employees). The employees receive on-the-job training on various things (operation of heavy equipment, safety training, msds training, ad-hoc training). I need to be able to track which employee has taken what courses, on what date they passed (started would be nice if relevant), and if that training expires. Basic reporting on that is nice too.

I have considered tossing something together using asp.net with MS SQL as a back end, but if there is already a project/app that would run under Ubuntu (like some sort of bastardized LAMP project), this would be preferential from a "I could get hit by a bus and the company be clueless" standpoint.

Any suggestions? Most of what I have seen is related to classrooms which generate year end grades, etc. I just need a basic training application.

TIA,

-tim

---

### Post by UbuWu on 2008-01-09
A simple spreadsheet could do that...

---

### Post by rickyjones on 2008-01-09
If you really want something where anyone can administer it well after you are gone then I recommend looking into programming a simple web database application.

Off the top of my head all you need is a LAMP server. Make a simple database and table structure that will hold your information. The website will feature a form to enter the information which is then stored in the database.

Simple to use. Easy to put together.

If you don't wish to do something like that yourself I'm sure you can find people to do it. You could contract my company to do it :P. It'd take about a week off the top of my head to put it all together once you figure out exactly what data you need to record.

I hope this points you in the right direction!

-Richard

---

### Post by timmy22 on 2008-01-09
Thanks for the replies so far. A spreadsheet is an answer, but neither elegant nor easily secured. And as mentioned, I could easily program this myself using microsoft tech, but the issue is me being hit by a bus. If something like this *already exists* and is open source and is actively used and developed, that's what I'm looking for.

If not, that's OK, but then I'll be secure in the fact that I did make the effort at the time to find something rather than tossing together my own solution.

Any other suggestions out there?

Cheers,

---

### Post by mduaneh on 2008-07-17
Did you ever find an application that already exists.  I think I am repeating your search effort roughly six months later, and finding NOTHING.

I'm thinking of using the spreadsheet approach but using a Google spreadsheet to store the data, either learning something about the Google application creator or similar to make it more of a web application.

---

### Post by timmy22 on 2008-07-18
No I did not find anything suitable. I ended up creating an access front end to a SQL back end. Pretty simple, a handfull of tables, and a bunch of entry forms and reports. It's not ideal, but the HR folks could not be happier with it. I hate the idea that I've created this one off wierdo thing out there that will get orphaned when I move on. :)

Oh well...

-tim

---

### Post by Radyair on 2009-05-16
There is an open source CMS package, that they call a "Learning Content Management System":

[http://www.atutor.ca/atutor/](http://www.atutor.ca/atutor/)

You can serve the training modules here, develop them here or in another testing/training program, or just use it to track the training results and timelines.

---

### Post by tsali on 2009-05-16
Typically, academic "gradebook" software is wholly inadequate for industrial training management and certification tracking, but, unfortunately, a large portion of the available software is targeted towards managements of classes and grades rather than management of core knowledge.

I wrote an application like this in 2002 that ran from a LAMP server. In order to ensure speed and efficiency I used a text based user panel, but quickly discovered that potential customers wanted a "web based" solution, even though they couldn't explain to me why they wanted that solution.

In any event, software capable of performing this function is often quite expensive...and far more complex than a spreadsheet.

---

### Post by EBogdan on 2011-08-01
Anyone else found a solution for this in the two years that passed since the problem was risen? :P

I ask because far now the tools I tried - for example [Work Examiner]("http://www.workexaminer.com/") or [TrackWhen Employee Tracking]("http://www.trackwhen.com/") are way too advanced for what I need - basically they allow you to track what employers are working on / where they are, which is something I obviously don't need.

Wouldn't mind to pay some money for the right piece of software - something that helps keep track of employees courses without anything else fancy to distract me from the scope of the project.

---

### Post by plebgate on 2013-02-14
I am in the exact same position now. I'm guessing its fair to say that nothing really exists for this.

---

### Post by oldos2er on 2013-02-14
Ancient thread closed.

---

