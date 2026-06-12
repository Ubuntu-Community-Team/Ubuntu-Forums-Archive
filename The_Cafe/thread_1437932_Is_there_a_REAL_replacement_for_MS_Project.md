---
title: "Is there a REAL replacement for MS Project?"
date: 2010-03-24
forum: The Cafe
---

### Post by hambone79 on 2010-03-24
I'm working on a 2 year long project that currently has about 180 tasks. The project involves several engineers and we are trying to keep our spending to a minimum by avoiding the purchase of MS Project licenses (it would cost us in the neiborhood of $10,000). Because of this I have been looking at several open source PM programs, but all of them have serious issues. Here is a list of the ones I've tried:

1. GanttProject
2. OpenProj
3. OpenWorkbench

Here are the problems I have had:
1. Critical path is calculated incorrectly.
2. Problems with the tasks suddenly moving forward several days.
3. Problems with earliest start date.
4. Problems with weekends and vacation days being ignored.
5. Various resource management issues.

Does anyone know of any program that is a true replacement for MS Project? In other words, something that can calculate task logic and critical paths correctly?

---

### Post by fatality_uk on 2010-03-24
In a word no. I tried gnome planner [http://live.gnome.org/Planner](http://live.gnome.org/Planner) but it had many problems. Engineers don't need a copy Project. They need to know what they are doing, but ultimately the PM has to do the planning. In that case, you should really only need at most two Project licenses for a team of several engineers, one for PM and one possibly for team head.

---

### Post by juancarlospaco on 2010-03-24
Planner ?

---

### Post by fatality_uk on 2010-03-24
> **juancarlospaco said:**
> Planner ?

I did post a link to planner, at least for the OP to try, but honestly, for day to day work, as much as I don't like saying it, MS Project is still the top app for PM.

---

### Post by whiskeylover on 2010-03-24
dotProject. 

Pretty close to the real thing. Its a pain to enter tasks in it though.

---

### Post by hambone79 on 2010-03-24
All of the ones listed so far are ok for small project with 20 or so tasks but they seem to crumble when you get to around 60 tasks. I guess we will have to bite the bullet and get MS Project.

---

### Post by whiskeylover on 2010-03-24
You only have to buy licenses for project managers, not for everybody else.

---

### Post by IoanLucian on 2010-03-25
Have you tried RationalPlan? It computes correctly the critical path, it respects calendar working hours, works well for a reasonable number of tasks (hundreds or more), comes with a free viewer and it is much more cheaper than MS Project. But hey it is not free... Check it out at:
[http://www.rationalplan.com/](http://www.rationalplan.com/)

---

### Post by hambone79 on 2010-03-25
RationalPlan looks good except for the fact that it doesn't handle PERT charts.

---

### Post by HermanAB on 2010-03-25
Primavera is commonly used for very large projects and is popular in the Oil and Gas industry.  It is probably not cheap either, but it is a real alternative!

---

### Post by madjr on 2010-03-25
so what really do people using exclusive linux or mac have done all these years? purchase MS project?

what do real devs "really" use

---

### Post by IoanLucian on 2010-03-25
> **hambone79 said:**
> RationalPlan looks good except for the fact that it doesn't handle PERT charts.
And do you really need PERT charts? Doesn't Gantt chart give you enough information? I mean what is it missing from a Gantt that you need in a PERT?

---

### Post by hambone79 on 2010-03-25
> **IoanLucian said:**
> And do you really need PERT charts? Doesn't Gantt chart give you enough information? I mean what is it missing from a Gantt that you need in a PERT?

To me the PERT chart is essential. I enter all of my tasks in the Gantt chart then use the PERT chart to organize the logic. Also, I find the PERT chart easier to understand than the Gantt for large projects.

---

### Post by fatality_uk on 2010-03-25
What I tend to find is my PM's usually issue PERT charts to management team as a nice visual overview of a project. They can also work with logic of task progression

---

### Post by tgalati4 on 2010-03-25
You can manage projects with web-based tools:

planner publishes to html.
[http://getontracks.org](http://getontracks.org)
[http://37signals.com](http://37signals.com)
[http://www.simile-widgets.org/timeline/](http://www.simile-widgets.org/timeline/)
google calendar (create a master project calendar, then share with participants--updated in realtime)
Also check out the google labs plug-ins for gmail and calendar.  Lots of interesting tools.
[http://jnintegration.sourceforge.net/integration-main/user-guide/planner-to-ics.html](http://jnintegration.sourceforge.net/integration-main/user-guide/planner-to-ics.html)

Anyone with web browser can see project status.  PM's and Team Leaders can be granted edit priviledges.  Run a script once a day to update the various pieces, send out status emails/sms, etc.

It requires a different mindset from 1990's (really 1960's)-style project management.

MS Proj is nice, but expensive to set up for entire workgroup.

---

### Post by Sporkman on 2010-03-25
Re critical patch calculations, I have such a calculator on my website:

[http://sporkforge.com/sched/critical_path.php](http://sporkforge.com/sched/critical_path.php)

You have to compose a text file to specify the tasks, but it's been in use for a couple of years without any complaints re accuracy.

---

### Post by tgalati4 on 2010-03-25
Large stickies for the PERT chart.  Quicker than using a program.  Use the above tool to find the critical path.  (Very cool tool by the way, Sporkman)

Once the PERT and critical path are initially done, then you can layout the tasks in planner for execution.

I'm not sure of the value of PERT during execution.  Except for viewgraph engineering.

---

### Post by phrostbyte on 2010-03-25
> **madjr said:**
> so what really do people using exclusive linux or mac have done all these years? purchase MS project?

what do real devs "really" use

Project management is way overrated. Most FOSS projects don't do planning. No, I'm not kidding. :) This is even true for very large FOSS projects like the Linux kernel, with thousands of developers.

The few that do tend to use wikis. Or wiki/bug tracker/source control combinations like Trac.

---

### Post by fatality_uk on 2010-03-26
> **phrostbyte said:**
> Project management is way overrated. Most FOSS projects don't do planning. No, I'm not kidding. :) This is even true for very large FOSS projects like the Linux kernel, with thousands of developers.

The few that do tend to use wikis. Or wiki/bug tracker/source control combinations like Trac.

Care to provide details of how you "*know*" this?

I have been involved in software development, some FOSS, for over 20 years and I can tell that, WITHOUT exception, all had a level of planning involved. Might be a spreadsheet with task to complete but that **IS **planning.

> This is even true for very large FOSS projects like the Linux kernel, with thousands of developers.

Now you _REALLY_ need to cite where this little gem comes from?

---

### Post by Mark Phelps on 2010-03-26
Can't comment on FOSS projects.  Have spent all of my career working in closed-source projects.  But in those, EVERY project did formal Project Management.

OK, so we're generally talking hundreds of team members, about 1/2 of which are developers, and the rest other engineers and PM personnel.

But without PM tools, it would be virtually impossible to keep track of progress (or more generally, the lack thereof).

And before anyone throws in their gold-plated Agile wrench, yes, we have those projects and we use PM tools on them, too.

---

### Post by pbenerjee on 2010-06-26
I think OpenProj is pretty good for small projects as someone pointed out.
Has anyone tried taskjugglar ?? It is available in Ubuntu repository too and it has the latest stable version.

Here is the site for the app and [B]user manual :
[/B]
[http://www.taskjuggler.org/](http://www.taskjuggler.org/)

Here is wiki :

[http://en.wikipedia.org/wiki/TaskJuggler](http://en.wikipedia.org/wiki/TaskJuggler)

It has a learning curve but thankfully, they gave a manual on their site (ignore first 25 pages or so).
Most important "milestone" is getting started with taskjugglar. However, once you get started, it does act as a true management aid for you. As opposed to other products, which are cakewalk to begin with, slowly become cumbersome as the projects moves forward in real life.

Taskjuglar is not a product to "document" your plan, but helps you make the plan after you give its basic input like tasks, estimated man-days etc. It fulfils moderm requirements like global time zone support and is also better suited for agile style management. Despite that, its still very conventional and rock solid. Its scalable. Earlier it was KDE only but now good for all unix/Linux thanks to Ruby

I am amazed that I took long time to discover it (google crawlers??) and am not surprised that none mentioned about it here too.

However, as I said there is a learning curve at the beginning but its not much difficult. It really is a management aid rather than a documentation tool for your plan.

No worries, it does churn out Gantts/PERTS's and few others too. Its not perfect though, but if it suits your need, then its a candidate for MS project replacement. for free as in $$ and liberty

---

### Post by Xianath on 2010-06-26
Agile is no silver bullet or gold-plated wrench but it does give you flexibility and visibility. Contrary to what people who've never used it think, it does NOT mean no planning -- there's actually more going on than with some of the other project management methods. You basically HAVE to have proper tools. On the bright side, since it's all the hype, competition in Agile project management tools is much more multiple-sided than it is in MS Project vs. nobody. I'd go with either the Atlassian suite (Jira+Greenhopper, optionally FishEye, Crucible and/or Bamboo) or Rally, and I've also heard good things about VersionOne but haven't used it personally. It really depends on headcount, MS Project might actually work best for you.

On my previous job, I've had endless embarrassment trying to do even simple PM tasks in either openProj or OWB. I ended up writing my own little Agile tools in OO.o Calc, crude but good enough to give me a backlog, iteration planning and burndown. At least that way I re-gained some of the respect of the engineers that way :)

---

### Post by pbenerjee on 2010-06-26
> **Xianath said:**
> Agile is no silver bullet or gold-plated wrench but it does give you flexibility and visibility. Contrary to what people who've never used it think, it does NOT mean no planning -- there's actually more going on than with some of the other project management methods. You basically HAVE to have proper tools. On the bright side, since it's all the hype, competition in Agile project management tools is much more multiple-sided than it is in MS Project vs. nobody. I'd go with either the Atlassian suite (Jira+Greenhopper, optionally FishEye, Crucible and/or Bamboo) or Rally, and I've also heard good things about VersionOne but haven't used it personally. It really depends on headcount, MS Project might actually work best for you.

On my previous job, I've had endless embarrassment trying to do even simple PM tasks in either openProj or OWB. I ended up writing my own little Agile tools in OO.o Calc, crude but good enough to give me a backlog, iteration planning and burndown. At least that way I re-gained some of the respect of the engineers that way :)

I agree Agile is no silver bullet. However, I never made it out to be one. I made a reference to it as it could be an important factor for many. The tool I spoke about is suited for Agile though as I mentioned it is still very conventional tool. Its the flexibility aspect that I tried to highlight

I think PM tools is an area where Linux attention hasn't gone enough in recent times. We have options available though nothing like say OpenOffice, FireFox, GIMP, Inkscape, mutimedia, emails etc. Just like GIMP is an excellent alternative to Photoshop for professionals, we need an equivalent of M$ Project as OpenProj has a long way to go as far as scalability is concerned. But it has the potential for sure.

---

### Post by chrisjsmith on 2010-06-27
MS project is a symptom of a problem, not a tool to manage products.

---

### Post by Old Marcus on 2010-06-27
> **chrisjsmith said:**
> MS project is a symptom of a problem, not a tool to manage products.
Doth speak the FUD-monger.

---

### Post by pbenerjee on 2010-06-30
> **chrisjsmith said:**
> MS project is a symptom of a problem, not a tool to manage products.

Agree, MS Project, the way its commonly used, is a way to document a plan at its best. If you want to track project performance using it, you have to forget that "ghost % completion" of task. You have to use "other" performance measurement criteria. For example, Earned Value analysis. 
Same goes true of open source counterparts GanttProject, OpenProj etc. These can become management aid IF we forget that "ghost completion" of tasks.

Else, they just remain programs to document your schedule/effort/budget plan, not anything more.

---

### Post by fatality_uk on 2010-07-01
So I found out yesterday that the Lazarus (Free Pascal) project was alive. Was so nice to see a "friendly face" As a former Delphi lead developer, I am now working on refreshing my coding skills. So anyway, I have decided to start a project to create a project planner. Don't get too excited. It's totally an idea so far. I would imagine 6-9 months before anything comes of it.

---

### Post by Sporkman on 2010-07-01
> **Sporkman said:**
> Re critical patch calculations, I have such a calculator on my website:

[http://sporkforge.com/sched/critical_path.php](http://sporkforge.com/sched/critical_path.php)

You have to compose a text file to specify the tasks, but it's been in use for a couple of years without any complaints re accuracy.

I've recently made an expanded tool called the "Project Scheduler". Besides sporting a unique & inspired name, it will schedule tasks while taking into account resource usage.

There's a link to it from the critical path calculator.

But, as usual for my stuff, it's basic text in / text out - no fancy charts or anything.

---

### Post by bad_cables on 2011-05-31
just a comment... most companies that do work for an engineering firm have to use Primavera or MS Project by contract.

---

