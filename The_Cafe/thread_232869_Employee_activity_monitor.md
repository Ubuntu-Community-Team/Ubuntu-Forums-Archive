---
title: "Employee activity monitor"
date: 2006-08-09
forum: The Cafe
---

### Post by Koobi on 2006-08-09
Hi,
I wasn't sure to post this so moderators, do move this thread to the appropriate section by all means if it belongs somewhere else.

At work, we want to implement an employee activity monitor. We'd like to use something that is open source.

I'm a project manager/systems analyst at my office which is a web dev firm and i have 6 programmers under me and we wanted to implement a system by which we can monitor what programs the computer has running and if it's a browser, what the URL is.

i'm running ubuntu/gentoo at work and the rest are all on windows so it would have to be cross platform.


anyone know of any good software?

---

### Post by ember on 2006-08-09
I do not know whether there is software that does this. Yet the solution should not be too tricky. What you do is programming a little skript that gathers all running processes (e.g. by running ps and parsing the output). I believe, to monitor the URLs you will have to modify the browser or write an extension.
Once this information is gathered, you can send it to a central station using either webservices or simple netcat.

Although all this can possibly be done, I allow my to raise the question whether you really want to do this. If I were one of your employees, I would rather cut down my productivity to a rather moderate level when I knew that my project manager uses that kind of surveillance measures.

---

### Post by Tomosaur on 2006-08-09
I find it incredibly ironic that you would use an OS specifically marketed towards fairness, freedom, and harmony, and then use it to monitor and control people.

Anyway, it's not my place to tell you how to do your job, so I can only agree with ember. I don't know of any actual programs out there, but if your server is set up right, you should be able to gather all the information you need very easily. You'd need a script which ran through, gathered, and collated all of the necessary information from logs.

---

### Post by Kernel Sanders on 2006-08-09
This is a terrible idea. I would never work for an organisation that does this... :(

---

### Post by Xzallion on 2006-08-09
I don't see why its such a bad thing.  It's a work computer, everything you do on it is theirs anyways, and there are needs for records in case of certain complaints or problems.  Like idiots browsing porn at work and another employee complaining about it.  You want records for that.  And theres a lot more, better arguments for it, I just can't think of them.

---

### Post by Koobi on 2006-08-09
> **ember said:**
> I do not know whether there is software that does this. Yet the solution should not be too tricky. What you do is programming a little skript that gathers all running processes (e.g. by running ps and parsing the output). I believe, to monitor the URLs you will have to modify the browser or write an extension.
Once this information is gathered, you can send it to a central station using either webservices or simple netcat.


Unfortunately, i'm the only one running on linux as i mentioned in my post but that's a very interesting idea :)
is there an equivalent of ps for Win?




Actually a lot of IT companies here do this sort of thing.
As far as i know, even Virtusa (Massachusetts) does this.


What we do is, we ask the programmers to turn it on themselves when they are working. Basically, we expect a certain number of hours of work per day and we just want to see who meets that quota so we can remunerate the best performers accordingly.
This was actually suggested by my boss.


What is the alternative? My problem is that the team works at a snail pace. What shouldn't take more than 30 minutes usually takes 4 hours or more and we are on a tight deadline. I have provided them with everything they need (tools, software, pseudo code, etc) but i'm not seeing any results.

---

### Post by hizaguchi on 2006-08-09
I think it's a pretty good idea, and it seems perfectly fair to me as long as they know they're being monitored.  One thing to keep in mind though is that a certain amount of messing around online or playing solitaire can actually increase productivity.  It's the equivalent of reading the paper or talking to co-workers about the weekend.

I know that when I'm doing something boring and repetative at work one of 2 things is bound to happen.  a) I'll take an occasional break to check email and talk on this forum.  or b) I'll eventually just space out and stare at the screen, followed by much slower work.

---

### Post by DoctorMO on 2006-08-09
Ah, couple of things to to face then, 1) trust, do they trust you 2) like, do they like you, 3) a job, do they consider it a clock job (waste as much time until you go home)?

The better solution would be to enforce the idea that they work the project not the clock, they're getting paid for producing work not for coming in at 9 and going home at 6. the advantage to the company is that it gets work done that may require overtime. the advantage to the employee is that they can achive greater flexability and where needs arise they don't feel guilty about comming in a bit late because of a doctors apointment ect.

Open source solutions, for the processes I would simply remove unwanted programs from the computers. for browsing you can moniter the http network traffic from the different ip addresses to find out what sites are being accessed when.

---

### Post by sapo on 2006-08-09
If you guys know any program that does this, please let me know, so i can kill the guy who wrote it.

---

### Post by ember on 2006-08-09
I believe you can do this with the Windows scripting language. Also there are commercial software products which do this (google brought up e.g. [http://www.protectcom.com/)](http://www.protectcom.com/)).

In Germany this kind of user monitoring is illegal in most cases, yet I know in many other parts of the world it is not. I generally question the success of these measures.

A possible alternative would be to adapt some points of extreme programming (only a rough sketch):

a) Identify the requirements and features for the software you are about to programm
b) Split everything up to packages that can be done in one week.
c) Start (or end) every week with a meeting in which you discuss what features have the highest priority and will be realized.
d) Do stand-up meetings where nothing is discussed but everybody can state where he is and what his problems are (a great opportunity for a cup of coffee while you listen). These meetings should be short.
e) Try to allocate only one project to one person. 
f) Think about programming in pairs.
g) Give your employees a chance to provide feedback (maybe anonymously)

If you believe that your employees spend much time with private surfing, just state your boss has asked you to remind them that private surfing is discouraged during working times.

My suspection is that your employees are overextended with the project or with the tools. That creates an atmosphere of unproductivity. Also it is a common case that many companies do not appreciate negative feedback. Think about asking your employees where they see the greatest risks and dangers in the project.

If you have concrete examples on work which takes too much time in your eyes, maybe you like to ask here in the forums. There is quite a lot of professional software developers here who can give their estimation on how long it would take them to complete that tasks.

---

### Post by djsroknrol on 2006-08-09
> This is a terrible idea. I would never work for an organisation that does this...


why not?...they pay you to work..not goof off...

> I think it's a pretty good idea, and it seems perfectly fair to me as long as they know they're being monitored. One thing to keep in mind though is that a certain amount of messing around online or playing solitaire can actually increase productivity. It's the equivalent of reading the paper or talking to co-workers about the weekend.

I know that when I'm doing something boring and repetative at work one of 2 things is bound to happen. a) I'll take an occasional break to check email and talk on this forum. or b) I'll eventually just space out and stare at the screen, followed by much slower work.

I agree with that to a point, as I do the same thing...like right now...I'm at lunch, on my time..but at times, I have to take a break (the old eyes you know)..my boss has come in and seen me in the fourms with no fallout...so he understands...

---

### Post by mips on 2006-08-09
> **Koobi said:**
> 
What we do is, we ask the programmers to turn it on themselves when they are working. Basically, we expect a certain number of hours of work per day and we just want to see who meets that quota so we can remunerate the best performers accordingly.
This was actually suggested by my boss.


What is the alternative? My problem is that the team works at a snail pace. What shouldn't take more than 30 minutes usually takes 4 hours or more and we are on a tight deadline. I have provided them with everything they need (tools, software, pseudo code, etc) but i'm not seeing any results.

I'm sorry to say this but programmers do not work towards a time clock. I've seen programmers code two days straight in a row but maybe for a week after that they do zip. It's one of those environments where creativity takes over. Did some network support for a local programming company and they could not give a rats *** if you are not at work by 10am. Some people only get in at like 6pm and stay there until 8am.

Sorry I degress but the programming environment is a weird one and trying to control people is not going to help you but instead maybe agrevate the coders.

---

### Post by codypumper on 2006-08-09
You could say you're now monitoring them, and see if progress improves at all...

---

### Post by Redcard on 2006-08-09
Couple of ideas for you.

First, don't limit people based on what they do.  If they're producing, don't worry about it.

Second, why do it this way?  How about another way?  Using DHCP and a proxy server, you can EASILY track who is going where and when and why and how.  You have the benefit of only seeing their browsers and URLs.  You can also limit online gaming and the like through strategic port usage controls.

I'll say this , though. Make certain that you don't eliminate browsing altogether.  People need their news, email, etc to feel connected to the world while at work.  It might hurt their productivity to take it away.

---

### Post by Abe Leno on 2012-05-25
> **Koobi said:**
> Hi,
I wasn't sure to post this so moderators, do move this thread to the appropriate section by all means if it belongs somewhere else.

At work, we want to implement an employee activity monitor. We'd like to use something that is open source.

I'm a project manager/systems analyst at my office which is a web dev firm and i have 6 programmers under me and we wanted to implement a system by which we can monitor what programs the computer has running and if it's a browser, what the URL is.

i'm running ubuntu/gentoo at work and the rest are all on windows so it would have to be cross platform.


anyone know of any good software?

The software I'm using runs on a cloud server on the employers part, and the employees' end of the program can run on Windows or Mac. As I understood, they have computers with Windows OS, so it should work if you are all connected by the internet. The name of the software is My Team Monitor, and you can register as an employer on their website: www.myteammonitor.com, and afterwards your employees will be able to download and install their part of the program from the same website. The software is free for both you and the employees, so you can try it and see if it works for your needs.

---

### Post by mörgæs on 2012-05-25
Old thread, closed.

---

