---
title: "Large Capacity Server Planning"
date: 2006-12-27
forum: Server Platforms
---

### Post by dwessell on 2006-12-27
Hi all,

I have a bit of a server related question.. I'm in the beginning stages of putting together a business plan for a website.. And I'm stuck on planning for capacity questions. I've run a single server before (I'm a programmer), but never multiple servers handling one website..

Is there a general/basic curve that's followed? ie... For x number of hits, you'll need two servers handling the page requests, one handling the DB, etc....??

How is planning of this type usually handled? I know it's going to vary greatly on the type of site being implemented, but is there a guideline that I'm not finding?  ](*,) 

Any suggestions would be extremely welcome!!

Thanks
David

---

### Post by Brazen on 2006-12-27
This is going to vary greatly by the type of web apps or content on your site.  If this is an existing site, you will have to take benchmarks from the existing site.  If this is a new site, then starting out with one database server and one web server would be fine and your growth will depend on the popularity of the site.

---

### Post by dwessell on 2006-12-27
Brazen,

Thank you.. But what I'm hoping for is the existence of a generic guide, for future planning.. I know that one server will be fine at first, but what about on down the road? How can I plan hardware costs (At least a general idea) for when I'm seeing x number of hits?

Thanks
David

---

### Post by Brazen on 2006-12-27
How can you plan on how many hits you'll get, for that matter?  I know nothing about business plans.  I have an idea on budget planning here, but that's only going by previous data for this company.

I know my answer isn't a good one, I just didn't want to leave your thread hanging :)

edit:  You might go here: [http://www.anandtech.com/it/Default.aspx?start=46&qmaxrows=61&prevstart=31&sectionid=208&manu=&manukey=](http://www.anandtech.com/it/Default.aspx?start=46&qmaxrows=61&prevstart=31&sectionid=208&manu=&manukey=) and read some of the "Behind Anandtech" articles .  I read them years ago, and I seem to remember them talking a lot about number of hits and database access and how they handled their capacity expansion.  It might be helpful.  Also, I'm pretty sure there are performance guides out there on how many hits Apache can handle on such and such hardware and likewise for MySQL, but you'll have to Google around to find them (unless someone else knows of some).

---

### Post by PilotJLR on 2006-12-27
If bandwidth is not limiting, then the only reason to cluster is to handle server side scripts and database queries... so I'm not aware of any specific rules of thumb, since the variance from app to app to db is so great.

What type of WAN connection will this have? Why are you planning on multiple servers from the get-go?
And if you do need multiple web servers, then it's often best to implement an appliance based load balancer, like from Coyote Point or F5. You could also build your own load balancer with Squid or other services.

---

