---
title: "interview questions"
date: 2010-07-09
forum: The Cafe
---

### Post by jusbug on 2010-07-09
hi guyz, at the moment i'm updating my cv and i want to look for sys admin position, for this reason i would like to know what are
the daily tasks given to a junior or mid-level sysadmin, basicaly what do you do during the day (related to you job discription), and
can you tell me what kind of question i can expect during an interview.

thanks for your help.

---

### Post by Xianath on 2010-07-09
You shouldn't worry about the technical screening that might be part of the interview. If you're applying for a job then you've already weighed your technical knowledge against the requirements and have found it to match or exceed. It's the other questions that are much more interesting. Unless you luck out with a good interviewer, these might be just the standard set, such as:

* Where do you see yourself in 1/3/5 years
* Why did you choose this company / department / job
* What are some of your strengths / weaknesses
* Tell us something you're particularly proud / ashamed of
* How would you go about resolving a conflict with a subordinate / peer / manager
* What would you do if your manager asks you to do something you consider technically wrong?
* Would you rather do a so-so job on time or a good job late?

Be yourself, be respectful, be honest. Do your homework - find out about the company, what they do, what their products are, who their customers are, what other people in the local labor force market think about it, and how it measures up to other companies. Find out about dress code, ask if you have to. Have an idea about your requirements and what compromises you're willing to make with them. And finally, be on time for the interview!

I'd google around for some more tips but given that I just started here a month ago, I don't want to give the proxy the wrong impression :)

---

### Post by jusbug on 2010-07-09
what about the technical screening? that's what worries me. are the questions hard?

---

### Post by RiceMonster on 2010-07-09
> **Xianath said:**
> * Where do you see yourself in [s]1/3[/s]/5 years

Celebtrating the 5th year aniversery of you asking me this question!

---

### Post by stmiller on 2010-07-09
Basic sys admin stuff is to keep everything running and know how to fix something if it breaks. Also know how to patch or keep a system secure and updated.

Some basic sysadmin stuff is:

How do you start/stop services
How do you grep logs for problems 
How do you start in single user mode / why would you need to do this
How do you change run levels / why would you need to do this
How do you apply security updates / software updates in production environment

What ports are used for various protocols (http, https, imap, imaps, pop, pops, smtp, smtps, dns, etc).

What is the difference between tcp/udp packet

There is web stuff if applicable - managing apache:

What is a virtualhost? What situation would you need this?
How do you enable / disable apache modules?
How do you enable / disable sites?
.... 


Then there is email stuff - sendmail, postfix, etc:

How do you update the alias file / what is the alias file
How do you update the virtusertable
....

And also database stuff - mysql, postgres, oracle

The best thing to do is to just mess around with Linux at home, or pay for hosting where you have root access to have your own server. Then you can check it all out!

---

### Post by earthpigg on 2010-07-09
didn't i just see this exact same post in the San Francisco Linux User's Group mailing list? :P

---

### Post by jusbug on 2010-07-09
> didn't i just see this exact same post in the San Francisco Linux User's Group mailing list?

i dont know about this mailing list, a link would be helpful

---

### Post by earthpigg on 2010-07-09
> **jusbug said:**
> i dont know about this mailing list, a link would be helpful

nevermind, i must be hallucinating.

---

### Post by phrostbyte on 2010-07-09
Here is a sampling of questions I've had asked to me when I was a sysadmin.


Explain how to set up a mail server. What are some popular mail servers?

Write a command line directive that counts all the unique lines of all the files in the current working directory which end with .log

Where is Apache configured?

What protocol allows you to monitor network devices? Name a piece of software the aids in this task.

Explain the Linux boot process from when you click the power button on a computer to when you see the login screen.

Explain what happens in the Linux kernel when you execute a binary.

What are the layers of the OSI model and what does each do?

Write a regular expression that matches valid e-mail addresses.

How do you compile and install a Linux kernel?

---

### Post by Lucradia on 2010-07-09
I see someone forgot the question EVERY job place asks:

"Why should we hire you?"

---

### Post by Xianath on 2010-07-10
I would usually just mess up the network settings on my laptop, then turn it over to the candidate and ask them to figure it out. In IT most of what you do is troubleshooting in one form of another. That's a skill of its own as important as the actual technical knowledge. Observing how someone goes about solving a problem under pressure is very informative. Also, good beer laugh material if they end up being hired.

I would expect questions on troubleshooting a Linux system: networking, resource usage, package management and configuration, user management, etc. Here are some things I consider basic essential knowledge for a junior Linux IT:

* POSIX permissions (name a file that should have 400 permissions), including sticky and setgid/setuid
* CPU usage: user, system, idle, wait (what is id% and why is it always that high, should I be worried?)
* basic system monitoring: top, vmstat, free (I just booted this system, why does it only have 20MB free when it has 8GB?)
* disk space: df, du, mount
* package management (learn to use rpm as well since you probably will have to anyway)
* users and groups
* basic network configuration: ifconfig, route, ethtool
...

Take a look at the Absolute Beginner forum. You should be able to answer most questions asked there, or at least understand the answers. Move on to the General section. How are you faring there? Try the Server and Networking sections, too, this would give you a picture of what Linux admins do. Scale down to get to junior level. If you can handle some of this stuff, you should be fine.

---

### Post by koenn on 2010-07-10
> **Xianath said:**
> I would usually just mess up the network settings on my laptop, then turn it over to the candidate and ask them to figure it out. In IT most of what you do is troubleshooting in one form of another. 
I don't agree that "in IT most of what you do is troubleshooting in one form of another" - except maybe that lots of IT is about problems and solutions in a very broad sense (eg as in 'implement an email solution')

A seriously doubt that someone's ability to troubleshoot deliberately messed up network settings on a laptop gives any indication about a person's ability to manage user identification, authentication and authorization in a corporate IT environment, to design and implement a backup- and recovery strategy for a bunch of servers, and so on. 

Like the OP, I don't know really know what the term 'junior sysadmin' is supposed to cover (I'd have to see a job description of some sort), but if I had any say in the hiring, I'd be looking way beyond troubleshooting skills (or even the ability to work under pressure).

---

### Post by Xianath on 2010-07-10
> **koenn said:**
> I don't agree that "in IT most of what you do is troubleshooting in one form of another" - except maybe that lots of IT is about problems and solutions in a very broad sense (eg as in 'implement an email solution')

A seriously doubt that someone's ability to troubleshoot deliberately messed up network settings on a laptop gives any indication about a person's ability to manage user identification, authentication and authorization in a corporate IT environment, to design and implement a backup- and recovery strategy for a bunch of servers, and so on. 

Like the OP, I don't know really know what the term 'junior sysadmin' is supposed to cover (I'd have to see a job description of some sort), but if I had any say in the hiring, I'd be looking way beyond troubleshooting skills (or even the ability to work under pressure).

You're probably right, given that I worked in Support and not IT. For the record, in five years and over 200 interviews, we (myself, HR and my manager) have made only one hiring mistake (someone who we hired and had to fire). Most candidates came from some sort of IT position though, and in a lot of ways the job is similar -- only the end users are different. This is of course only one part of IT (more specifically, IT support). There's also networking, security, platform, application, storage, infrastructure, Unix, Windows, Exchange, database, firewall... you name it. Could be a couple of guys ("IT Crowd" style) or could be several dozen departments each the size and budget of a small company (like in the financial sector). It would help to know more about the position the OP is looking for, or looking at.

---

### Post by hambim336 on 2011-09-22
Hi
   
  I found that a member asked same question in this forum some months ago.
   
  Pls use search box to find this questions with comments

---

### Post by sffvba[e0rt on 2011-09-22
Back to sleep thread...

---

