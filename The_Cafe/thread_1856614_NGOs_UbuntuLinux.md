---
title: "NGOs Ubuntu/Linux"
date: 2011-10-08
forum: The Cafe
---

### Post by bonfire89 on 2011-10-08
Hi there,

I'm currently involved a project where I am studying an NGO whose purpose is to improve the nutrition of the worlds poor. I'm conducting an industry analysis which includes how Information Technology is used in the industry.

These uses could include things like: managing donations, managing project contracts, responding to RFPs, email, communications, tracking, supply chain management and more.

I just finished reading up on all the good things Microsoft can do for NGOs but I'd much rather finish this project by recommending something from the open-source world rather than something from Microsoft.

If anyone can hook me up with some links about using Ubuntu or Linux to help NGOs it would be a big help.

Preferably these links should be about the "as-is" state since I am at the moment conducting an industry analysis.

Many Thanks!

---

### Post by earthpigg on 2011-10-08
Wikimedia Foundation is an NGO non-profit: [http://www.canonical.com/about-canonical/resources/case-studies/wikimedia-chooses-ubuntu-all-its-servers](http://www.canonical.com/about-canonical/resources/case-studies/wikimedia-chooses-ubuntu-all-its-servers)

You'd need to get more specific about your NGO for really specific answers.

Some NGO non-profits are structured like a for-profit enterprise with "Community Outreach" and "Public Relations" replacing "Marketing" and everything else remaining nearly identical, while some aren't.

---

### Post by bonfire89 on 2011-10-08
I'm slightly limited in terms of confidentiality, (yes I know it is a non-profit but I'm airing on the side of caution) so I have to stay a bit general.

But, this organization helps people in local communities better grow food and partners with manufactures to manufacture food with the processes they develop and then further partners with others to distribute the food. This organization has offices all over the world, 1st world and 3rd world.

Looking at the IT in anything that is related to those sorts of activities would be useful. Another example might be that an organization could hypothetically get receive donated satellite internet to a rural location in Africa who could then use that connection to maybe connect to an Ubuntu LAMP server located at the headquarters of the organization I'm studying to access information.

Wikipedia would be a bit dissimilar in that they don't have to deal with rural poor areas that might cause issues in accessing infrastructure. They are also different in that there isn't really much of a supply chain or need for distribution of goods.

(ps this is a university project)

---

### Post by earthpigg on 2011-10-08
It sounds like maximum flexibility would be absolutely crucial for something like that.

-Wiki-style bottom-up documentation of farming approaches and results (as opposed to top-down 'thou shalt do this'), applying the scientific method. So at some point a web-server will be set up, and wiki software installed. You can say *poof* and turn any Ubuntu machine into a redundant webserver.

> an organization could hypothetically get receive donated satellite internet to a rural location in Africa 

-So it might be handy for computers to *poof* become a WiFi hotspot or router without any special equipment. The one laptop per child machines run linux, and do some automatic crazy chain range extenders - each one connected also serves as a router for systems farther away.

-And, because internet may be unreliable, Ubuntu offers the ability to *poof* become a software repository over a local intranet. I think the total size requirement for an Ubuntu computer to become a software repository is like 50 gb or something - fairly modest.

-Deploy-ability. TinyXP is illegal, but custom Ubuntu remixes specifically tailored to your needs and including software relevant to your project can be created and distributed on the cheap. You could make your custom remix automatically fetch and include the wiki page up-to-date as of when that USB/CD was burned (again, relevant if internet access isn't super reliable).

-Oh, and speaking of XP: Going the Windows route, you will either need to have all the machines on some old Windows version, or maintain/support separate versions for different hardware configurations. If you simply discount or fail to utilize all machines that wont run Win7, you will be throwing a lot of machines away. If you do the same thing with machines that wont run Ubuntu 11.10 you will still throw some away, but far fewer.


For a University project I'm sure you will have to turn each of those bullets into several pages, but thus is life.

---

### Post by koenn on 2011-10-08
lemme guess ... Oxfam ? 

There's np shortage on communication software - mail and web solutions should be trivially easy to find and are ready to use. I'm thinking, Zarafa, Zimbra, LAMP, web Frameworks s.a. Drupal, wiki engines,  ....

You probably also know the general purpose office software

For more specific software for typical NGO activities, I think Django in capable hands can go a long way.


I'd be interested to see what you found  Microsoft has to offer - it could shed some light on what sort of info you're looking for.

---

### Post by bonfire89 on 2011-10-08
these are definitely great ideas and the sort of thing I will be looking at next semester when I move from studying the "as-is" to the "to-be", But out of scope for the moment in time.

The school program I am in is a business program with a focus on IT. Next semester when we start coming up with solutions we will have to look at costs vs benefits, ways to implement, higher level matters and most important of all, a solution (which is where your suggestion come in). We will not particularly be coming up with our own solution but something that is already established that could be provided by a vendor.

It's a two semester project. Semester one is where we get all the information we may need to be able to make a well informed IT recommendation in semester 2.

Part of this current semester is establishing the importance of IT in the industry and that is what I'm doing now.

Thanks for the ideas! they will be useful a bit further down the line.

---

### Post by koenn on 2011-10-08
I misunderstood your OP then - and it's still not quite clear (maybe I don't fully grasp what "business analysis" means).

Are you looking for (NGO-like) cases where Open source software is being used ?

---

### Post by bonfire89 on 2011-10-08
getting to the point of why I'm here today I need to find cases where people have used technology that could also be used at the organization I'm studying.

The organization I'm studying is an NGO which can likely benefit from the open-source world. Which is awesome for me because I'm a linux geek and would love to suggest an open-source solution.



_The rest I have just typed up for perhaps your own curiosity_

But, in business a decision has have a sound foundation. I can't just say use Ubuntu because it can do cool stuff and it is free. I have to show:

* how it will be useful
* how using it will help them achieve their goals better
* that there is acceptable risk
* that the product will be accepted by people
* that people will be able to learn the software
* that the software will work well with the other people that are already in the industry
* that the product is inline with the company's vision
* that the product's functions are with in the scope of the company
* that doing something is better than doing nothing
* and more

Not so much in my exact situation, but in other situations where extremely large amounts of money are at stake investors/companies need to know that everything has been considered and that the system will work. 

What happens if there is a construction project expected to begin soon that will cause a lot of dust which ends up harming the new fancy computers. I need to know if something like that is going to happen. I need to know everything that might effect the situation.

I have to analyze it from every angle possible. If I told them to use Libre Office and they started receiving docx files that displayed malformed we'd have big issues. Staff will have difficulties dealing with the software, something they aren't experts in, and worst of all will cause them to be innefficient. Libre Office might be free, but if it means they help 10 less kids because a docx file wouldn't open right, then they'd be better off using MS Office.

One part of this section of my project is to do a "Porters 5 forces analysis" [http://en.wikipedia.org/wiki/Porter_five_forces_analysis](http://en.wikipedia.org/wiki/Porter_five_forces_analysis)

Or consider [http://en.wikipedia.org/wiki/Business_case](http://en.wikipedia.org/wiki/Business_case)

One way to study this is to see what others have done. And that's where I am now.




I hope all this makes sense, I'm in school learning about these topics, so, I'm not an expert either.

---

### Post by castrojo on 2011-10-08
[https://wiki.ubuntu.com/NGO](https://wiki.ubuntu.com/NGO)

---

