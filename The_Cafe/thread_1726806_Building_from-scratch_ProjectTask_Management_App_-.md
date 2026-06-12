---
title: "Building from-scratch Project/Task Management App -- suggestions please"
date: 2011-04-11
forum: The Cafe
---

### Post by samalex on 2011-04-11
I'm developing a Project/Task Management system from scratch, and for anyone who uses such an application I'm curious to know which product you use, what features do you find most or least important, and what features do most such apps you've used lack the most?

I'm still drafting out the basics of what this app will do so I'm not even to the point of coding anything yet -- not even sure what language I'll use though I do want it to be a web-based application.

Thanks for any insight...

Sam

---

### Post by Tony221268 on 2011-04-12
I think you are doing a good thing since I just looked for one and found nothing of any real worth from the following installed project tools:

Planner - limited. Doesn't do enough reviews or reports. Defaults are odd (so when you add a task it defaults to a scheduling type rather than just being obedient to your start and end date)
Projity - great looking but it has annoying constraints. I.e. by default it also has strange scheduling defaults. Seemed to have it's own business rules which I didn't want. In particular it seemed to worry about the start date of the project as being some sort of reason to override my inputs. I am meant to be in charge...not you stupid programme! So I did what I think most would do; I gave up in annoyance. The import also failed causing me to waste another 30 minutes.
Xplan - downloaded the binaries and it failed to "make" so gave up.
Gantt Project - couldn't create an app launcher without lots of effort and bash knowledge so gave up. Importer also poor since it has no guide.

Personally I would concentrate on:

1. Ease of set-up including basic help to get you going
2. Ease of importing from MS Project/ TXT. 
3. Lots of views
4. Plan to provide good support when things don't work.
5. If you are going web then you need to make data entry fast. Not click add>type details>click save>screen refresh. People want to type fast.

I would avoid:

1. Complex constraints
2. Business rules
3. Worrying about being able to run before you can walk. Just a set of heirarchical tasks with user friendly inputting would be cool.

PS - of the four, I reluctantly chose planner but only after being irritated by it enough to evaluate the others.

---

### Post by samalex on 2011-04-12
> **Tony221268 said:**
> I think you are doing a good thing since I just looked for one and found nothing of any real worth from the following installed project tools.  <SNIP>

Thanks for the feedback.  I've also spent some time reviewing different project/task managers, and none really had what I was looking for either.

Here is a short list of features in my product backlog:
- Web-based
- AJAX to prevent screen refresh so often
- Project Management using SCRUM Development for larger projects
- Task Management for smaller/quick tasks
- Document/File Library for meeting notes, screen shots, white board snapshots, prototyping, etc
- Task scheduling for reoccurring tasks
- Task creation through text-based emails and files so tasks can be generated through any application that can write a text file to the filesystem or email
- Charts/Reports

I have about a 4 pages of features on my wish list plus some very rough drawings of layout, so we'll see how well it works.  Either way it'll take some time to setup, possibly 6 months or more, but I'll post updates as I go.

---

