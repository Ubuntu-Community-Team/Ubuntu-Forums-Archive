---
title: "Server Load Capacity -- MySQL Server Question"
date: 2011-03-24
forum: Server Platforms
---

### Post by garfonzo on 2011-03-24
Hey Folks:

I have been approached by an organization to build a database for them to track membership turnouts. Basically, there are around 600 people in the organization and, these 600 people break off into small groups of about 10 people per group. Every group has a leader so there are about 60 groups and group leaders. This organization wants to track weekly group meeting attendance to report to the organization's board, as well as send out emails to group leaders etc. The organization is extremely cost-conscious and has a tiny budget to put towards this project. 

I have suggested using a Linux box with a MySQL database that leaders and the organization's staff can log into and produce various reports about attendance statistics. There will be probably about 40-80 people accessing this server at any given time and, the uses of this database may grow to include other uses than simple attendance tracking. 

My question is, given that the server isn't open to the world (ie: it isn't hosting a public website that could see hundreds of visitors a day) how much power do I really need in a server? I was thinking that a basic, top of the line desktop would easily handle the traffic and database processing. Am I correct?

---

### Post by Vegan on 2011-03-24
Do not worry about it, just make sure there is a regular backup in case of problems.

---

### Post by garfonzo on 2011-03-24
> **Vegan said:**
> Do not worry about it, just make sure there is a regular backup in case of problems.
So could I slap the database on an old tower I have kicking around (like Pentium II tower old)and still have a successful setup even with 80 or so people logging in?

---

### Post by freebeer on 2011-03-24
You should be fine with an old tower.  I don't think it's so much the quantity of users as it is the processing needed.  Input is typically not a CPU-intensive task.  It's when you need to run long and complicated reports will you see any real CPU use.

---

### Post by BkkBonanza on 2011-03-25
Even if all 60 groups were entering things at once you'd have a pretty small amount of actual hits/second here. Just about anything will work. You should probably just use a cheap low end VPS account and save the cost and hassle of hardware management. 

However, I could see if it's strictly internal on a LAN you would want to localize it to some machine. If it's going to be accessed from various places around the country/world then you're better off using a small VPS. More than enough power and only $10-15/mo. You won't barely cover electricity for that on hardware.

---

### Post by garfonzo on 2011-03-25
> **BkkBonanza said:**
> Even if all 60 groups were entering things at once you'd have a pretty small amount of actual hits/second here. Just about anything will work. You should probably just use a cheap low end VPS account and save the cost and hassle of hardware management. 

However, I could see if it's strictly internal on a LAN you would want to localize it to some machine. If it's going to be accessed from various places around the country/world then you're better off using a small VPS. More than enough power and only $10-15/mo. You won't barely cover electricity for that on hardware.

That's actually an interesting solution. I have an old tower that would probably suck $10-$15 in power alone, nevermind the possible hardware issues of an old system. 

Cool -- thanks for the help!

---

### Post by BkkBonanza on 2011-03-25
I was just posting in another question here about free vps servers, and it occurred to me that you may want to explore as well [Amazon EC2]("http://aws.amazon.com/ec2/pricing/") since they have a "first year free" deal for new signups. 

On a micro size instance (similar to a small vps) the normal cost would be between $5 and $15 a month and if you need more resources they are available instantly by moving to a bigger size with just a restart.

---

