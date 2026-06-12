---
title: "Need help with guidance on school career path"
date: 2021-06-19
forum: The Cafe
---

### Post by issh on 2021-06-19
Hey everyone, 

I'm really hoping someone here who works in programming, software development, or anything to do with linux could help point me in the right direction to go in school. I'm 30 years old now, but I developed PTSD and I need to start a new career in a field that isn't so stressful. I'm familiar with computers and have been using linux since I was in high school so I figured something to do with computers would be ideal. I'm just clueless in where to start and it seems overwhelming. Is a linux systems engineer a career? I remember someone famous saying they studied for that.

Any guidance or maybe a mentor willing to talk with me would be great. Thank you so much. 

Regards.

---

### Post by TheFu on 2021-06-19
How to start depends on what your dream job might be.

Programming, administration, security, are big areas, each with specialization.  There are generalists in all of those as well, but often they've done 2 of the lower level jobs for years before their bag of mixed skills pays off as an architect. Architects aren't always hands-on, and usually happens 10-20 yrs after being a programmer or systems admin.

These jobs have stress, but nobody will be trying to kill you.  But your actions can cost millions or hundreds of millions to the company.  That's usually why the people involved are paid well, so they have a goal of not screwing stuff up, breaking things or causing downtime.

I know very few people who only work with Linux.  Even Redhat employees have to work other other OSes.  The world is integrated.

---

### Post by issh on 2021-06-20
> **TheFu said:**
> How to start depends on what your dream job might be.

Programming, administration, security, are big areas, each with specialization.  There are generalists in all of those as well, but often they've done 2 of the lower level jobs for years before their bag of mixed skills pays off as an architect. Architects aren't always hands-on, and usually happens 10-20 yrs after being a programmer or systems admin.

These jobs have stress, but nobody will be trying to kill you.  But your actions can cost millions or hundreds of millions to the company.  That's usually why the people involved are paid well, so they have a goal of not screwing stuff up, breaking things or causing downtime.

I know very few people who only work with Linux.  Even Redhat employees have to work other other OSes.  The world is integrated.

Let's say I would like to go into security and/or administration. Where would I start with school? Would you be willing to talk over voip? I guess my dream job would be working for a corp administrating over their netowork or devleloping software. I've been brainstorming ideas for copper electric turbines around car axles to recharge batteries as they travel down the road, utilizing opensource or free software on the automotive computer module.

---

### Post by TheFu on 2021-06-20
These sorts of question really need lots of different feedback from many different people. Everyone gets to a career point in different ways. There is no "right" way. There are lots and lots of exceptions, plus passion can overrule the most common path.

Trying to learn everything you've listed, even at a beginner level will take many years to barely be competent. People underestimate the effort all the time.  Life will probably get in the way. You already know that.

I'm old and a little opinionated, so many languages that I'd never use, never allow on my systems, and would never trust might become highly desired skills for someone younger.  The world is very different today than it was when I took my first programming job.

To become a competent programmer, barely intermediate level will take 2+ yrs of daily effort. To become an expert takes 5-10 yrs and real effort.  Perhaps less than 5% of all programmers are actually experts in their language of choice, regardless of time spent.  A few people with "a knack" can become expert in a much shorter time. I know a few like that - less than 10 out of hundreds of different programmers with whom I've worked directly.

There are lots of Linux groups meeting online the last year. Have you searched for those? Attended any meetings?  Same for programming and security groups.  Around 2012, I stopped going to the local Ruby group after attending about 3 yrs.  Decided that Perl was a better solution for my needs and I'd already been programming in perl for a few decades to get things done when a compiled language wasn't required.  Young people seem to avoid Perl over outdated ideas.  That's fine. I avoid Javascript and Java.

Inside an enterprise, systems admin is a separate job from programming.  They are in completely different groups. I doubt they talk much beyond the "I need X installed" on my development server.  The project dev lead would be responsible for packaging the working program to pass that onto QA.  In an enterprise, developers don't get access to integration or production systems.  This is a good thing. As a developer, you don't want any connect to production systems. 
Same goes for security. Completely different career paths.  Groups that meet tend to be separate for each of those areas too. 
For programming, the language is the split. 
For administration, the OS is the split and for security - well - just look for a local DefCon group.  

My metro area has 10 programming groups, 4+ security groups and I don't know how many OS-specific groups.  Some of those groups are end-users dealing with desktop stuff and others are enterprise admins.  My LUG has over 2K members and we have meetings in different parts of the metro area so people don't have to travel 1-2 hrs just to attend.  Each smaller group has a slightly different membership, so that drives the topics for each meeting.

To be an admin, go get a few RHEL certificates. Your location in the world and which industry you are part of will determine which OS is mostly used. Financial companies and huge enterprises are mostly RHEL.  Get the best book and start from chapter one, working through the book. Expect that to take 3-6 months.  When you think you are ready, pay for and take the exam.  Keep using RH-based distros daily so you don't lose those skills before you are done interviewing and land a position.  HR likes certs.  Technical leads should ignore them, since there are lots of people who can memorize books, but never actually do the work to learn it.  When I interviewed people, I would ask questions to determine where the other person's knowledge limit was. Nothing wrong with not knowing answers. "I don't know" is a valid answer. Be certain you look up the answer, so if there is a 2nd interview, you can answer it.  That was another test. About 80% of people didn't bother to keep learning. They didn't have the passion we wanted.

Debian doesn't have a cert, but LPI does. The LPI certs aren't as ... prestigious and don't seem to pay as much, IMHO. No admin certs teach scripting, but it is a key part of being an effective admin.  DevOps and virtualization are both key skills too.  Since around 2002, everywhere I worked mandated that all server deployments be onto virtual machines by default, so having experience with a few different hypervisors is useful.  After virtualization, if you can learn a few different Linux Container methods and automatic container build and deployment methods, you'll find an admin job very quickly.

I never wanted to be an admin for critical production systems.  I learned this in a class learning Netware long, long, ago.  That class was great!  It taught me that I never wanted a job like that.  However, it did make my night programming job a little easier, since at that time everyone was deploying software on netware servers.

All the areas you've listed are related and learning something in 1 will help in others too, but if you need a paycheck fast, then get a RHEL cert.  Certs teach about 1% of what an admin actually needs to know. Doesn't matter which cert in whatever field.  Every network is a little different from every other network.

Gotta go - sorry for the rambling.

---

