---
title: "Switching my Consulting Firm to Linux"
date: 2007-10-02
forum: Testimonials &amp; Experiences
---

### Post by Go_Bucks on 2007-10-02
Several months ago I set out on an adventure. Having always been tired of Microshaft and their business practices, and having a need to speed up (yet again) a bloated Windows XP machine, I decided to start from scratch with this OS I heard of called Ubuntu. I had a few problems, sure, and I will not pretend that the install went easily, but I know computers well enough to expect that there may be some tweaking necessary with a third party operating system.

Well. months later, I have grown quite fond of Ubuntu. As shown in my previous posts, I have had the opportunity to install Ubuntu on one machine at my company's office (with no problems) and on my wife's old Compaq that was painfully slow until the day I installed Ubuntu on it. At our office, I will next week begin the process of replacing Windows XP Pro on our file server with Ubuntu Server Edition.

Now let me preface my next few statements with an explanation about my company. I work for a small environmental consulting firm that provides services to several very large homebuilders with projects throughout California and several adjoining states. Though my office is on the beach in Orange County, I work primarily out of my home in Los Angeles County. My computers at home are networked with the office system.

When I started working there as a biologist in 2003 it was basically a single guy with subcontractors. There was some fieldwork and reports. Technology was limited to word processing. I implemented GIS, data collection standards and databases and since then our company as expanded like mad. We have moved from a trailer on the beach sand to a $4 million office on Pacific Coast Highway. We are incorporated. We have employees, desks, workstations, a meeting area, a computerized phone system and an office manager.

My boss, who is technology averse, has made me his right hand man and pays me well for the job. Though I am primarily still a consultant, I also determine the workflow process that takes data from the point of collection in the field to integration in documents. Because of his aversion to change and technology, I have had to fight with him about every change that we have made to our processes, though as he has stated many times, every change I have asked for has turned out to be positive and growth-inducing for our company.

After some investigation, I decided that I didn't think it was a good idea to stay the course with Microsoft after XP disappears from the market. All well and good, except that we have a database in Access, produce reports in Office, and have a staff trained in ArcGIS/ArcInfo, etc. The GIS investment alone has cost us about $20,000 this year, but those are not single point in time expenses, as good GIS firms using an ESRI workflow have to pay thousands per year in maintenance fees.

So, my goal was to look at replacement software. In the process I have discovered a robust database system known as PostGIS, and have found many good GIS programs for Linux that will write to PostGIS layers. The clincher was discovering gvSIG, which allows us to produce the same quality maps from PostGIS layers that we are producing now in ArcMap. I have even found a plugin for free that will allow ArcMap to work with PostGIS. We also would have the opportunity to test placing maps on the web with open source Mapserver... a step we have wanted to take but have not because of the expense of ArcIMS. OpenOffice even allows us to continue writing documents for clients and save them as Word files, and it even has built-in PDF functionality. 

Well, yesterday I managed to impress my boss by putting together a 3D moving display of land cover change over time on a project using Linux-based software... this was something we could not do in our current $20,000 worth of software. I showed it to him from my Windows laptop logged into my Linux computer at home. He asked me about my email program, Evolution, which was up on a second screen at my desk as it runs on an Ubuntu virtualbox on my laptop. He liked how it had the ability to share calendars and contacts without the expense of Exchange as is required in Outlook.

That was enough for him. He asked me to assemble a new GIS and database infrastructure which will reside on our new Linux server and that will work cross-platform. Further, he wants me assist moving his computer to Linux, migrating documents to OpenOffice, and generally preparing the company for a possible move to an all-Linux environment. 

Now, I love this place but I am not a board junky. What I do intend to do from time to time is update this thread with information on the trials and tribulations of this process so to better inform others that may be in a similar situation. I am excited about it and look forward to the challenge.

---

### Post by conehead77 on 2007-10-02
Very interesting! I always wanted to know how much hassle it is for a company to switch from Windows to Linux.

---

### Post by tgalati4 on 2007-10-02
Take some of your older PC's and set them up with Ubuntu and place them around the work area as "backup machines".  It gives folks a chance to get some hand's-on experience.  After a year, there will be less resistance to using Ubuntu and Linux in general.

---

### Post by thiebaude on 2007-10-02
This was a very good choice.I now can say im 100% ubuntu 7.10.I had been switching back and forth between XP and 7.04.Last night I finally upgraded from 7.04 to 7.10.Installation was pefect.I didn't even have to install mplayer for firefox.there was one bug with opera not wanting to load,so a bug was filed with the devs and a few hours later when my wife and i got home, i was able to download the opera debi package file,I think it could of been dependencies, im not sure, but i love this version alot and i think many people will, i know its still in Beta, but i don't have any problems so far.


Good job again devs and community

---

### Post by w7kmc on 2007-10-02
I think I read  an article recently in one of the Ubuntu newsletters lamenting the fact the linux has gained such a little foothold in the business desktop world. This is a nice example of how that mentality may be changing.

---

### Post by matthew on 2007-10-02
Hey, this is a great contribution. Thank you. I'll be watching your progress with great interest as time passes. I have a business running on Linux, but I started it that way...no migration was necessary. Please continue to share everything from the successes to the potholes and difficulties.

---

### Post by zero244 on 2007-10-04
What you did was a smart move. You are fortunate you have a boss who is open to new ideas.
If I were running a business network I would definately be using a total Linux system.
Good Luck

---

### Post by wolfen69 on 2007-10-04
welcome.

---

### Post by adamorjames on 2007-10-05
That was a nice read. I hope everything keeps getting better, I can't wait for more. :)

---

### Post by Dropknee on 2007-10-05
Veeeeeerrryyy interesting, pls update us about this project and the impact in your work environment.

---

### Post by Go_Bucks on 2007-10-05
Wow... I wasn't expecting that many responses. I am glad to have so much support. FYI, this will take some time. The server reconfiguration is likely to take place early next week, though I was told it needs to wait until after an important document goes out on Monday evening. I am worried that my boss - who is convinced for some reason that something may go wrong and we will lose our files (I am referring here to the server's current primary purpose which is file serving) - may put it off until after I get back from vacation this month because of a fear that something will go wrong and I won't be there to fix it.

The other stuff awaits my ability to set up all aspects of a project in open source software solutions, including a full document in OpenOffice, a working database front end, and maps that look as good as our current ones. I have to work on this stuff in my free time and I do have a life which includes a wife, a kid, a dog, a cat, running, hiking, mountain biking and watching college football with a beer in my hand. Most of the work on this is on down-time late in the evening with my wife in front of the tube with a laptop on my lap that is logged into my desktop through VNC.

---

### Post by laptoppana on 2008-09-02
Nice talk, please update us some more news. My company is also a small GIS firm, that why I very interest in this. Thanks

---

