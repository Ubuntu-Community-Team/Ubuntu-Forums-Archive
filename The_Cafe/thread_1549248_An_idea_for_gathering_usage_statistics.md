---
title: "An idea for gathering usage statistics"
date: 2010-08-09
forum: The Cafe
---

### Post by MasterNetra on 2010-08-09
Rather simple really why not just add all hardware product id's which are unique to each piece of hardware (e.g. two Intel Celeron processors that are identical physically are gonna have different product ids still) and add them together to form a Statistic ID? (well mostly unique, you may occasionally get the same sum between different machines but that would be rare or at least very uncommon I would think) and this would be limited to hardware you don't change too often (CPU, GPU, ram, etc)

This Statistic ID by nature couldn't be broken down so no way someone could take the number and figure out what you have, with exception that they have all your product ids except one already and just need to figure out that last one. (Not a issue obviously plus what would be the point, they wouldn't figure out anything that would be useful to them).

Now as for operation, after install by default the system would attempt compile and send this Statistic ID, that is worthless except for helping determining how many people use the OS, to ... Canonical's server lets just say where it compares it to the list of existing numbers and if the ID doesn't exist in that list it adds it. This would be done probably first time you connect for a system update.

As for new hardware additions, once Ubuntu (or whatever) detects new hardware it would toggle the update variable telling the system it will have to recompile and send again, but of course to help prevent multiple entries the system would have to have had saved that original ID and tell the server its old id and provide the new one so that the server can remove the old entry and replace it with the new.

And to be clear the ID number wouldn't be accessible by other programs, and if someone managed to take control of your system to get this number (again though such effort for next to no reward so this is highly unlikely) but of course in such a case you would have much bigger problems then a worthless number being obtain by someone...

---

### Post by Simian Man on 2010-08-09
Microsoft and Apple already know how many units they sell.  And nobody else cares about this except for Linux fanboys who don't have the resources to implement anything like this in the first place.

---

### Post by MasterNetra on 2010-08-09
> **Simian Man said:**
> Microsoft and Apple already know how many units they sell.  And nobody else cares about this except for Linux fanboys who don't have the resources to implement anything like this in the first place.

On the contrary it is extremely important to linux, if of course you want commercial software to be made available as well as bringing more users and developers in. Right now there is really only that 1% - 2% market share showing companies how many people use a linux distro, which isn't a accurate representation of the user base. All market share tells is how many people PURCHASE something. And last i checked Ubuntu, Fedora, and regular open-suse is free of charge. The more we can show that use linux the more companies will be encouraged to port/develop for linux which in turn brings more people and more developers.

---

### Post by RiceMonster on 2010-08-09
Somehow I doubt software vendors are closely watching OS market share stats thinking "if linux hits 5.7%, THEN we're gonna port our app!"

[quote=MasterNetra]All market share tells is how many people PURCHASE something[/quote]

No, it doesn't.

---

### Post by Simian Man on 2010-08-09
> **MasterNetra said:**
> Right now there is really only that 1% - 2% market share showing companies how many people use a linux distro, which isn't a accurate representation of the user base. All market share tells is how many people PURCHASE something. And last i checked Ubuntu, Fedora, and regular open-suse is free of charge. The more we can show that use linux the more companies with port/develop for linux which in turn brings more people and more developers.

Wow you are extremely confused!  The 1% number comes from online web browsing data which *does* count free distros.  Those numbers aren't terribly precise, but they do give a good indication of desktop Linux usage.  Whether you like it or not that number IS around 1%.

---

### Post by MasterNetra on 2010-08-09
Will either way, if we can show the number of people who use linux in say the millions, that will be more attractive then the 1% market share number.

millions of people vs 1% which looks more enticing?

---

### Post by Bachstelze on 2010-08-09
> **MasterNetra said:**
> Will either way, if we can show the number of people who use linux in say the millions, that will be more attractive then the 1% market share number.

millions of people vs 1% which looks more enticing?

Depends to whom you're speaking.

---

### Post by RiceMonster on 2010-08-09
> **MasterNetra said:**
> Will either way, if we can show the number of people who use linux in say the millions, that will be more attractive then the 1% market share number.

millions of people vs 1% which looks more enticing?

How many of these users are going to buy their software?
How many of them will still buy their software and use it with Windows if there is no Linux version?

---

### Post by Simian Man on 2010-08-09
> **MasterNetra said:**
> Will either way, if we can show the number of people who use linux in say the millions, that will be more attractive then the 1% market share number.

millions of people vs 1% which looks more enticing?

Software companies pay people to make informed decisions about things like this.  It's not your job to convince anybody.

---

### Post by MasterNetra on 2010-08-09
> **Bachstelze said:**
> Depends to whom you're speaking.

A company more likely, I dunno about you but I'd be more entice to developing for a OS that has Millions of potential customers, oppose to hearing it just has only 1% of the market share.

---

### Post by Bachstelze on 2010-08-09
> **MasterNetra said:**
> A company more likely, I dunno about you but I'd be more entice to developing for a OS that has Millions of potential customers, oppose to hearing it just has only 1% of the market share.

You are obviously not a company.

---

### Post by MasterNetra on 2010-08-09
Regardless folks, the system is a harmless way of figuring out how many people use Linux which (in theory anyway) is more efficient then using IP addresses.

> **Bachstelze said:**
> You are obviously not a company.

Actually I do own my own business, but only sense April so granted i am still new to the game.

---

### Post by MasterNetra on 2010-08-09
Actually I am correct about what market share actually is. (essentially, I was more simple about it but still) Or at least the original version of it.

[http://www.businessdictionary.com/definition/market-share.html](http://www.businessdictionary.com/definition/market-share.html)
[http://en.wikipedia.org/wiki/Market_share](http://en.wikipedia.org/wiki/Market_share)
[http://www.investopedia.com/terms/m/marketshare.asp](http://www.investopedia.com/terms/m/marketshare.asp)
[http://www.wisegeek.com/what-is-market-share.htm](http://www.wisegeek.com/what-is-market-share.htm)

---

### Post by whiskeylover on 2010-08-09
> **MasterNetra said:**
> A company more likely, I dunno about you but I'd be more entice to developing for a OS that has Millions of potential customers, oppose to hearing it just has only 1% of the market share.

I'm sure the companies have a bunch of statisticians and tools worth thousands of dollars dedicated to doing exactly this type of research. I'm sure they haven't overlooked the 1%/1 million users relation.

---

### Post by MasterNetra on 2010-08-09
> **whiskeylover said:**
> I'm sure the companies have a bunch of statisticians and tools worth thousands of dollars dedicated to doing exactly this type of research. I'm sure they haven't overlooked the 1%/1 million users relation.

lol not us startups or small companies.

At any rate fedora along apparently has in the neighborhood of 23.5 million users and it isn't even the most popular (or at least its not believed to be the most popular).

Source: [http://fedoraproject.org/wiki/Statistics](http://fedoraproject.org/wiki/Statistics)

---

### Post by cariboo on 2010-08-09
Most Linux distribution makers use unique ip adresses connecting to their repositories as a metric for counting the number of installs. The last I heard Ubuntu had approximately 12 million users.

---

### Post by MasterNetra on 2010-08-09
> **cariboo907 said:**
> Most Linux distribution makers use unique ip adresses connecting to their repositories as a metric for counting the number of installs. The last I heard Ubuntu had approximately 12 million users.

Wish canonical would make a statistics page like fedora... Also it might be possible that its just from those who check the submit statistical data option in software sources... which isn't checked by default (should be though, let those who don't want to uncheck it before updating.) get a bigger number that's for sure.

Any way, the method i propose could (in theory, haven't heard of it tested) provide more accurate numbers and without the concerns brought up from using IP addresses. Granted it MAY mean more work to make it operational though, i mean you have dynamic address and computers concealed in a corporation network that throw the numbers off with IP addresses which makes it harder to get a reasonable accurate number.

---

### Post by handy on 2010-08-09
It is really easy to get an idea of how many people are using Linux. You just need to spend a little time talking to a variety of people (a cross section) & you will see that it is a very small number compared to the run of the mill option(s).  

We have Mac hardware (amongst other stuff) in our house & I know how few people I talk to (covering quite a range of types of people) use Macs. 

For me to talk to someone face to face who uses Linux is extremely unusual & BSD, Haiku & such has never happened in 25 years.

---

