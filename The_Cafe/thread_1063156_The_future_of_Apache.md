---
title: "The future of Apache?"
date: 2009-02-07
forum: The Cafe
---

### Post by hyperyoda on 2009-02-07
Since 2005 the market share of the Apache web server has fallen from 70% to 52%. 

Why did it fall so much? Do you think IIS will equal or overtake Apache? What can we do to get more sever admins running Apache?

[http://news.netcraft.com/archives/2009/01/16/january_2009_web_server_survey.html]("http://news.netcraft.com/archives/2009/01/16/january_2009_web_server_survey.html")
[http://www.edunetsys.com/blog/apache-or-iis-who-is-the-leader/]("http://www.edunetsys.com/blog/apache-or-iis-who-is-the-leader/")

Zach

---

### Post by Grant A. on 2009-02-07
Apache has more competitors in the FOSS world, IIS is not its only enemy.

---

### Post by kevin11951 on 2009-02-07
> **Grant A. said:**
> Apache has more competitors in the FOSS world, IIS is not its only enemy.

Here is one that is flying to the top! [http://www.lighttpd.net/](http://www.lighttpd.net/)

---

### Post by mrsteveman1 on 2009-02-07
Competition in the FOSS world is a bit different than in the proprietary world. When multiple FOSS projects compete, no matter what happens users win, and if the project managers are smart and efficient programmers they all win too.

---

### Post by Firestem4 on 2009-02-07
> **mrsteveman1 said:**
> Competition in the FOSS world is a bit different than in the proprietary world. When multiple FOSS projects compete, no matter what happens users win, and if the project managers are smart and efficient programmers they all win too.

+1

Thanks for saying that; it put it in perspective for me.

---

### Post by Johnsie on 2009-02-07
Alot of companies I know are moving to Windows servers because they are easier for their existing staff to maintain. Apache is ok on windows but unless you use Xampp for Windows it can be tricky for people to set up with php/cgi/asp etc. I should note that it has got easier in the last few years. Many Windows users prefer to have wizard based installers that make it easy to set up a server. It's the same on Linux. At first glance Apache can look tricky to setup with all the config files etc. Xampp made that easier but having Xampp meant that your apache was not up to date. One of the best things Ubuntu ever did was made it easy to do a Lampp install using either Ubuntu Server Edition or using Tasksel on Ubuntu desktop edition. Unfortunately most people don't use Ubuntu and not enough people know about the benefits of using Ubuntu Server. 

Apache is great, but people need to know how the easiest ways to set up (without compromising their security).

---

### Post by zmjjmz on 2009-02-07
> **Johnsie said:**
> Alot of companies I know are moving to Windows servers because they are easier for their existing staff to maintain. Apache is ok on windows but unless you use Xampp for Windows it can be tricky for people to set up with php/cgi/asp etc. I should note that it has got easier in the last few years. Many Windows users prefer to have wizard based installers that make it easy to set up a server. It's the same on Linux. At first glance Apache can look tricky to setup with all the config files etc. Xampp made that easier but having Xampp meant that your apache was not up to date. One of the best things Ubuntu ever did was made it easy to do a Lampp install using either Ubuntu Server Edition or using Tasksel on Ubuntu desktop edition. Unfortunately most people don't use Ubuntu and not enough people know about the benefits of using Ubuntu Server. 

Apache is great, but people need to know how the easiest ways to set up (without compromising their security).
Just wondering, but shouldn't professionals be operating servers? Why should a company pay the same amount for a sysadmin who's lazy/ignorant and wastes company money on expensive proprietary licenses?

---

### Post by Grant A. on 2009-02-07
> **zmjjmz said:**
> Just wondering, but shouldn't professionals be operating servers? Why should a company pay the same amount for a sysadmin who's lazy/ignorant and wastes company money on expensive proprietary licenses?

Exactly, the only server operating systems I could really see paying for would be Solaris, RHEL, or SLES. Windows licenses are just a waste of cash when it comes to servers, and you can't even modify the source of IIS to work around errors. You have to wait for Microsoft to repair them 5 months after they've been discovered.

---

### Post by Johnsie on 2009-02-07
I don't know about there, but most professionals here are trained in Windows. Pretty much all of my degree was based on Windows stuff. That's just the way it is. And most companies use Windows for their workstations. The alternatives are out there but  I guess the analysts/bosses are also trained in MS and want to stick with what they know. I'm  a programmer and the other day I installed Ubuntu on a workstation to run a stores management program I'm working on. It raised a few eyebrows. Alot of people still have the false impression that Linux is only for techies.

The people in the stores aren't IT literate, so I'm using them as guinea pigs to show the rest of the company that Linux can be easy to use and will save them money on licensing costs. I'm not pushing for a full Linux rollout across the company though, because we need to have compatibility with our clients, many of whom use Windows.

I also am using apache/php to do most of my data processing jobs. So when I leave the company the next person will need to have those skills or learn them as well as Ubuntu server. We have an MS server that an outside company maintains and an VMWare ESxi server which has an Ubuntu Lampp server as one of the main VM's on it.

---

### Post by Grant A. on 2009-02-07
> **Johnsie said:**
> I don't know about there, but most professionals here are trained in Windows.

That's a reason why Linux adoption is slow for some companies, because lazy IT guys will lobby and strike if they have to learn a new OS. A new OS for a company can mean the old IT guy is out of a job.

---

### Post by Johnsie on 2009-02-07
Well, I'm sure laziness if one reason for a lack of Linux adoption. There's also the problem that many specialised applications aren't available for Linux. When I am asked to install an OS for someone in the company I have to consider their needs and which operating system can support that.

For example, one of our staff is in charge of the drivers. He needs GPS tracking software on his PC so he can know where the vehicles are and record their movements. The best value local company provides Windows software for this so my decision has to be to install Windows on the machine.

In our data office the staff need to apply mailsort codes to data and fix postcoding errors. There was no Linux software available to do this so I had to install Windows so that they could run Matchit. I later wrote a php/apache based application that could do this but probably not as well as Matchit.

In our Downstream Access office our staff do alot of work using the Royal Mail EPRO and Dockethub website. EPRO will only work in Firefox (bad programming at Royal Mails end) and wont even work with the user agent switcher plugin for Firefox. This means that those people need to have Windows.


The point I'm getting at here is that rolling out Linux isn't as straight forward as one might think. You need to be able to make sure the staff can do their jobs properly,

How does this relate  to the use of apache? Well, if more people are using Windows then less it's less likely that they are going to want to learn apache because there are quite alot of other, easier to configure servers out for Windows.

---

### Post by tubezninja on 2009-02-07
Well, the graph showing market share doesn't tell the whole story.  Netcraft tallies server market share by domains, and during the period that MySpace, MS Live and Google's Blogger were exploding, those counted in Netcraft' statistics for "over 1 million sites" using IIS as their platform:

[http://news.netcraft.com/archives/2007/10/11/october_2007_web_server_survey.html](http://news.netcraft.com/archives/2007/10/11/october_2007_web_server_survey.html)

ENd result: you have some huge social networking powerhouses that recently came on the scene, and that is where your ISS market growth came in.


The effect is clearly starting to diminish though.   if you look at the current stats:

[http://news.netcraft.com/archives/2009/01/16/january_2009_web_server_survey.html](http://news.netcraft.com/archives/2009/01/16/january_2009_web_server_survey.html)

The trend is starting to reverse, which Apache share climbing again and IIS starting to level off.  The MySpace effect is starting to diminish.

---

### Post by hyperyoda on 2009-02-10
> **scaredpoet said:**
> Well, the graph showing market share doesn't tell the whole story.  Netcraft tallies server market share by domains, and during the period that MySpace, MS Live and Google's Blogger were exploding, those counted in Netcraft' statistics for "over 1 million sites" using IIS as their platform:

[http://news.netcraft.com/archives/2007/10/11/october_2007_web_server_survey.html](http://news.netcraft.com/archives/2007/10/11/october_2007_web_server_survey.html)

ENd result: you have some huge social networking powerhouses that recently came on the scene, and that is where your ISS market growth came in.


The effect is clearly starting to diminish though.   if you look at the current stats:

[http://news.netcraft.com/archives/2009/01/16/january_2009_web_server_survey.html](http://news.netcraft.com/archives/2009/01/16/january_2009_web_server_survey.html)

The trend is starting to reverse, which Apache share climbing again and IIS starting to level off.  The MySpace effect is starting to diminish.


Ah glad to hear that.

---

### Post by cardinals_fan on 2009-02-10
I use lighttpd, because it's lighter and (in my experiences) simpler.

---

### Post by dragos240 on 2009-03-12
apache for ever.

---

