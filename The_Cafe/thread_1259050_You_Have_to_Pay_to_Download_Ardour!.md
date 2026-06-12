---
title: "You Have to Pay to Download Ardour?!"
date: 2009-09-05
forum: The Cafe
---

### Post by Joseph Schwenker on 2009-09-05
I have been interesting in downloading Ardour to fool around with, seeing as it is open source, but was shocked when I went to the download page and was not able to download it for free.  Wait, isn't Ardour supposed to be open source?!  I thought that if something is open source, that the BEST version of it should be available to EVERYONE regardless of whether they have a credit card that they want to empty!  Was this not what the open source license was supposed to help eliminate?  Anyway, is there a way that I could download Ardour (any of the versions) for free, or would that be called, "pirating open source software"?  ](*,)

---

### Post by dmizer on 2009-09-05
From the [download]("http://ardour.org/download") page:
> You are not required to pay anything for Ardour.
So if you do not wish to pay anything, just change the "I choose to pay US$ ..." to zero.

Also, it might interest you to know that Ardour is in the Ubuntu repositories, so you don't even have to download it directly from the site. You just need to search for it in Synaptic or run this command:
```
sudo apt-get install ardour
```

And finally, if you want a more recent build than what's available in the repositories, here's a PPA with a current build: [https://launchpad.net/~khashayar/+archive/ppa](https://launchpad.net/~khashayar/+archive/ppa)

Finally, if you read the information in the download site, it says:
> You are not required to pay anything for Ardour. But in general less than 3% of you do pay. That is why, for several months, the project has not even met its goal of paying just one full time developer a salary of US$54,000/yr. With the current level of financial support it is hard to justify continuing fulltime work on the project. So please consider paying something for your download.

So, it's not about "piracy" because the source is indeed open. It's about being able to pay a developer to work on the project.

---

### Post by Joseph Schwenker on 2009-09-05
> **dmizer said:**
> From the [download]("http://ardour.org/download") page:

So if you do not wish to pay anything, just change the "I choose to pay US$ ..." to zero.

Also, it might interest you to know that Ardour is in the Ubuntu repositories, so you don't even have to download it directly from the site. You just need to search for it in Synaptic or run this command:
```
sudo apt-get install ardour
```And finally, if you want a more recent build than what's available in the repositories, here's a PPA with a current build: [https://launchpad.net/~khashayar/+archive/ppa]("https://launchpad.net/%7Ekhashayar/+archive/ppa")

Finally, if you read the information in the download site, it says:


So, it's not about "piracy" because the source is indeed open. It's about being able to pay a developer to work on the project.

If you set the I choose to pay __ for this software to zero, then you get a "trial" version that doesn't save or load AU plugin settings.

---

### Post by dmizer on 2009-09-05
> **Joseph Schwenker said:**
> If you set the I choose to pay __ for this software to zero, then you get a "trial" version that doesn't save or load AU plugin settings.

Then use the version from the Ubuntu repositories, or from the PPA I listed above.

---

### Post by Exodist on 2009-09-05
> You are not required to pay anything for Ardour. But in general less than 3% of you do pay. That is why, for several months, the project has not even met its goal of paying just one full time developer a salary of US$54,000/yr. With the current level of financial support it is hard to justify continuing fulltime work on the project. So please consider paying something for your download

Now I dont mind making donations when I can afford them. And right now isnt a good time due to the economy going to complete crap around here. But I was shocked they complained they couldnt pay a full time programmer there yearly salary of $54K.. HOLY CRAP.. I am a full time machinist and I only make about half that.. $54,000 is a bit much.. half that would be understandable.

---

### Post by Monkey.feets on 2009-09-05
Open source doesn't necessarily mean free...

> Computing Dictionary

open source philosophy, legal
A method and philosophy for software licensing and distribution designed to encourage use and improvement of software written by volunteers by ensuring that anyone can copy the source code and modify it freely.
The term "open source" is now more widely used than the earlier term "free software" (promoted by the Free Software Foundation) but has broadly the same meaning - free of distribution restrictions, not necessarily free of charge.
There are various open source licenses available. Programmers can choose an appropriate license to use when distributing their programs.
The Open Source Initiative promotes the Open Source Definition.
The Cathedral and the Bazaar. was a seminal paper describing the open source phenomenon.
Open Sources - O'Reilly book with full text online.
Articles from ZDNet.
(1999-12-29)

---

### Post by Regenweald on 2009-09-05
Greedy programmers...... coding all this cutting edge stuff for free, then wanting to pay bills and eat! the rank audacity!
don't they realize that FOSS is just one big free for all ?

---

### Post by ChrT on 2009-09-05
You're implying that "open source" = "free as in price". That's not the case. Free open source software can be commercial.

---

### Post by Keyper7 on 2009-09-05
> **Joseph Schwenker said:**
> I have been interesting in downloading Ardour to fool around with, seeing as it is open source, but was shocked when I went to the download page and was not able to download it for free.  Wait, isn't Ardour supposed to be open source?!  I thought that if something is open source, that the BEST version of it should be available to EVERYONE regardless of whether they have a credit card that they want to empty!  Was this not what the open source license was supposed to help eliminate?  Anyway, is there a way that I could download Ardour (any of the versions) for free, or would that be called, "pirating open source software"?  ](*,)

1) There's no such thing as "the open source license". There are *distribution licenses* and Ardour in particular uses GPL, which is a *free software* license.

2) The concept of free software has nothing to do with being free of charge.

---

### Post by niteshifter on 2009-09-06
> **Exodist said:**
> Now I dont mind making donations when I can afford them. And right now isnt a good time due to the economy going to complete crap around here. But I was shocked they complained they couldnt pay a full time programmer there yearly salary of $54K.. HOLY CRAP.. I am a full time machinist and I only make about half that.. $54,000 is a bit much.. half that would be understandable.

As one who free-lances as a developer let me point out something: You don't get to keep all $54K: Uncle Sam wants his cut (FWT + FICA). Insurance is the big ticket item, that can run a grand or two / month for a couple with kids. So that $54K can wind up being under $30K net.

Also depends a lot on where you are. Your area (Mississippi) historically pays low. Where I work (Tennessee) a mechanic / millwright gets $54K with benefits. An Electronics / Automation tech gets $72K. Yes, it's a Union shop. Non-union "tech" jobs around here go for around $16 - $22 / hour.

The last part-time gig I landed as a developer they paid $32K for 6 months and were happy to get off "that cheap" (their words, not mine).

---

### Post by shadylookin on 2009-09-06
> **Exodist said:**
> Now I dont mind making donations when I can afford them. And right now isnt a good time due to the economy going to complete crap around here. But I was shocked they complained they couldnt pay a full time programmer there yearly salary of $54K.. HOLY CRAP.. I am a full time machinist and I only make about half that.. $54,000 is a bit much.. half that would be understandable.

54k for a developer is a rather modest salary.

---

### Post by Exodist on 2009-09-06
> **shadylookin said:**
> 54k for a developer is a rather modest salary.

Well. TBH, it would also depend on where you live. In SanDiego where I lived that is chump change because pc techs at Frys got paid almost $25 per hour. But here in MS no one gets 25 per hour for anything.. 
I work my butt off and wish I had something close to 50k a year.. /cry

---

### Post by Warpnow on 2009-09-06
There are a good many non-free open source software. You want it free? Compile it from source, or find a ppa, or do some legwork. You pay for the convenience of them having packaged it usually.

Edit: Just checked, only the OSX packages require a payment.

---

### Post by Firestem4 on 2009-09-06
> **Exodist said:**
> Well. TBH, it would also depend on where you live. In SanDiego where I lived that is chump change because pc techs at Frys got paid almost $25 per hour. But here in MS no one gets 25 per hour for anything.. 
I work my butt off and wish I had something close to 50k a year.. /cry

One thing to note is salaries can vary by region. In California the cost-of-living is on average higher. An 800,000 dollar house in San Diego is a 300,000 dollars in Alabama.

---

### Post by Exodist on 2009-09-06
> **Firestem4 said:**
> One thing to note is salaries can vary by region. In California the cost-of-living is on average higher. An 800,000 dollar house in San Diego is a 300,000 dollars in Alabama.
Very true..  Started to buy one. Glad I didnt now.. hehe

---

### Post by jocheem67 on 2009-09-06
My Aussie girlfriend who is doing a high-level producing job in LA at the moment really got a raise for being able to live in LA with the same standard as living in Sydney....seems only fair to me.

I live in Holland, rates/wages here are just a tiny bit lower than in the States..I guess it just depends on where one resides when talking small or big wages...

---

### Post by Viva on 2009-09-06
free as in freedom

---

### Post by Joseph Schwenker on 2009-09-06
> **dmizer said:**
> Then use the version from the Ubuntu repositories, or from the PPA I listed above.

So then what abut the Mac version?

---

### Post by madjr on 2009-09-06
> **shadylookin said:**
> 54k for a developer is a rather modest salary.

**54k** per year in my country is being **rich** and can get you anything you want

anyway, my cousin is a open heart surgeon in **New York** and only gets **66k** a year ... 

God dang am sure they can get a full time developer even for **$20k** from a different country. 

I can sustain a family of 4 with **15k** and live normally

In my country some work for that amount or less and it's even easier to get one as how the economy is NOW and how hard it's to get a **JOB** , they don't have much choice.

Now i know why companies **outsource** so much. There's a nice, intelligent and hard working **Asian** guy that would do this job for pocket change (as most do now anyway), heck they would be even more polite and less ****upthight than most **** "westerns"

Am sure they haven't looked or **don't want to** so they invent these excuses, but is their project so i could care less how they manage it

---

### Post by gnomeuser on 2009-09-06
If you like the application throw the guys a few bucks, it's only fair.. honestly what is the problem?

They gives you:
1) the source code and all the rights to do pretty much whatever you please with it.
2) their time and skill in developing and maintaining said application. Skills they probably had to pay a hefty round of college fees to get and time they could spend with their loved ones instead.
3) They don't require payment but request it.

Please don't forget exactly how good a deal Open Source offers you and forget your sense of entitlement for a second. Not only do you get excellent software, you get a means to fix it and improve it, knowledge of what it does on your machine. You get freedoms to cherish, no questions asked. Surely if you are pleased with their application they earned a couple of dollars.

---

### Post by shadylookin on 2009-09-06
> **madjr said:**
> **54k** per year in my country is being **rich** and can get you anything you want

Well I'm sure in some places the cost we pay for internet for a year will be more than they'll ever see in their entire life. 

> 
anyway, my cousin is a open heart surgeon in **New York** and only gets **66k** a year ... 

Well I don't know much about open heart surgery, but I do know the average software developer will make ~70k. Even adjusted for living expenses in various regions of developed countries 54k is not a number to be shocked at. 

> 
God dang am sure they can get a full time developer even for **$20k** from a different country. 

Perhaps, but there are issues to consider like will he be as high quality? Will the other contributors be willing to work with him instead? How do you ensure he doesn't just take your cash and run? Will the extra hassle justify the drop in price? 

> 
I can sustain a family of 4 with **15k** and live normally

In my country some work for that amount or less and it's even easier to get one as how the economy is NOW and how hard it's to get a **JOB** , they don't have much choice.

Are you talking United States dollars here? If the average wage is that low then the odds are that there aren't many software developers around.

---

### Post by Warpnow on 2009-09-07
I would be unlikely to hire a programmer not living near me for anything but contracted work. How would I know he wouldn't up and move, find a new job, and disappear, ect, ect, ect. There's not much accountability when you live in an entirely different country.

I also would not hire a coder unless he fluently spoke the language most users will be using.

---

### Post by madjr on 2009-09-07
> **shadylookin said:**
> > I can sustain a family of 4 with **15k** and live normally


Are you talking United States dollars here? If the average wage is that low then the odds are that there aren't many software developers around.

not only many software devs, but **many Doctors, lawyers, etc**.

**15k** salary gives you a normal life.

and yes some people retire **from other countries** (or come back) and move over here because their retirement funds gives them a better life for the same amount of money (probably **3x**) and they have all the services they need (yes, McDonalds and chips included). 

oh and banks can pay up to **15%** / year on certificates. Life is pretty good

am sure all this might be even better in some other parts

> **shadylookin said:**
> Well I'm sure in some places the cost we pay for internet for a year will be more than they'll ever see in their entire life.

yes, so true and they manage to live 70+ years (sometimes happily in a good social environment or living peacefully with nature)

i would love to imitate that, but i love technology too much... The closest I might get is getting a house near the beach and using solar/wind power for most of my needs. Either that or getting my own farm.

---

### Post by Warpnow on 2009-09-07
Your location says DR...is that Dominican Republic? Sorry, I know nothing of Geography.

---

### Post by koshatnik on 2009-09-07
There's no such thing as free. Everything costs, and everything has a chargeable price.

Makes me laugh when people get indignant about having to pay for something they want... ok, don't pay and watch the project collapse, then have nothing to use.  Your choice. Whats a couple of dollars to anyone, anyway?

---

### Post by Warpnow on 2009-09-07
> **koshatnik said:**
> There's no such thing as free. Everything costs, and everything has a chargeable price.

Makes me laugh when people get indignant about having to pay for something they want... ok, don't pay and watch the project collapse, then have nothing to use.  Your choice. Whats a couple of dollars to anyone, anyway?

Cost comes in more forms than money. Time is a considerible cost as well. It is also not always the consumer who pays the cost. It might be the developer, or a third party like an advertiser, or large corporations who run servers and need support for the software, because the time cost of self-support is too high.

---

### Post by koshatnik on 2009-09-07
> **Warpnow said:**
> Cost comes in more forms than money. 

That's why I said there is no such thing as free.

---

### Post by Skripka on 2009-09-07
> **madjr said:**
> not only many software devs, but **many Doctors, lawyers, etc**.

**15k** salary gives you a normal life.


I don't know where you live, or what currency you're using, but in the US, $15,000USD will barely afford you a box to live in on the street, forget about medical care, food, transit, insurance.  IIRC $15k USD, in the US is just above what is classified by the government as "poverty level".

---

### Post by koshatnik on 2009-09-07
> **Skripka said:**
> I don't know where you live, or what currency you're using, but in the US, $15,000USD will barely afford you a box to live in on the street, forget about medical care, food, transit, insurance.  IIRC $15k USD, in the US is just above what is classified by the government as "poverty level".

£15k in the Uk is nothing either. Maybe ifyou live rent free at home with your parents with no debts, £15k is a decent salary, but its not if you have to pay bills, rent, mortgage or support a family. £25k is about acceptable.

---

### Post by Swagman on 2009-09-07
> **madjr said:**
> **54k** per year in my country is being **rich** and can get you anything you want

anyway, my cousin is a open heart surgeon in **New York** and only gets **66k** a year ... 

God dang am sure they can get a full time developer even for **$20k** from a different country. 

I can sustain a family of 4 with **15k** and live normally

In my country some work for that amount or less and it's even easier to get one as how the economy is NOW and how hard it's to get a **JOB** , they don't have much choice.

Now i know why companies **outsource** so much. There's a nice, intelligent and hard working **Asian** guy that would do this job for pocket change (as most do now anyway), heck they would be even more polite and less ****upthight than most **** "westerns"

Am sure they haven't looked or **don't want to** so they invent these excuses, but is their project so i could care less how they manage it

But do they have they Mortgage costs equivalent to location ?
If your going to live rough besides the river like the Eastern Europeans do in my city then you can undercut everyone.

But...

How crap a life do you want to live ?

---

### Post by Drunky on 2009-09-07
> **madjr said:**
> Now i know why companies **outsource** so much. There's a nice, intelligent and hard working **Asian** guy that would do this job for pocket change (as most do now anyway), heck they would be even more polite and less ****upthight than most **** "westerns"

Am sure they haven't looked or **don't want to** so they invent these excuses, but is their project so i could care less how they manage it

You make it sound like a crime, something abhorrent.

This isn't some large company.  It's a few people who actually conceived this software and *shock* **enjoy** coding it and would like to make a living doing it.  

Sounds like capitalism to me.

And why should they hire someone else to do what they want to do?  So you don't have to pay or pay less?  

If you disagree with the process or are offended by them charging, then voice your opinion by not paying or contributing.

Of course, this may already be happening.

---

### Post by dmizer on 2009-09-08
> **Joseph Schwenker said:**
> So then what abut the Mac version?

1) Download the open source and compile a Mac package yourself.
-- and/or --
2) Go to a Mac forum and complain about it there rather than on an Ubuntu forum where the program is actually open source and free.

---

### Post by hanzomon4 on 2009-09-08
Dude you can still get a version for free that does not support apples AU plugins AND you can pay as little as a dollar for the Ardour+AU. Really?!?! You complain! It cost more to make an iPhone fart!!!

---

### Post by misfitpierce on 2009-09-08
Just use ubuntu repo version as said... works fine and everything saves fine for me and has not asked me to pay anything.

---

### Post by Joseph Schwenker on 2009-09-08
> **Viva said:**
> free as in freedom

Free as in freedom... and FREE AS IN FREE BEER!  Wait, if you can distribute it freely, then doesn't that defeat the purpose of having it be commercial?  :lolflag:

---

### Post by Joseph Schwenker on 2009-09-08
> **dmizer said:**
> 1) Download the open source and compile a Mac package yourself.
-- and/or --
2) Go to a Mac forum and complain about it there rather than on an Ubuntu forum where the program is actually open source and free.

First off, the reason that I asked that question was because I wanted someone to help me SOLVE THE PROBLEM.  Telling me to "download the open source" and "compile a Mac package" helps me as much as Windows did when it said, "Error #498098: The memory at location 9283730x could not be read.  The instruction 19274u5920x will now be terminated.".  As I am beginning with Linux, I honestly have NO IDEA how to compile anything.  Also, as Ardour is an open source program, I wanted to ask it on an open source forum.  Not in some mac forum where they will say, "ardour is $[-}17 use gargebandlol".

---

### Post by Joseph Schwenker on 2009-09-08
> **hanzomon4 said:**
> Dude you can still get a version for free that does not support apples AU plugins AND you can pay as little as a dollar for the Ardour+AU. Really?!?! You complain! It cost more to make an iPhone fart!!!

Does not support apples?  Well, if I pay the one dollar for it, then there is always the possibility of the download failing, and then, since there is no licensing, I will have to pay AGAIN for something that I don't know even works.  Open source software is supposed to be freely distributed.  There is no purpose to open source if it is not free as in free beer.

---

### Post by Joseph Schwenker on 2009-09-08
> **koshatnik said:**
> There's no such thing as free. Everything costs, and everything has a chargeable price.

Makes me laugh when people get indignant about having to pay for something they want... ok, don't pay and watch the project collapse, then have nothing to use.  Your choice. Whats a couple of dollars to anyone, anyway?

What is a couple of dollars to a thirteen year old who will have to spend time convincing his mom to enter her credit card number on some weird website to download something that SHOULD BE FREE, as in terms of currency.

---

### Post by .Maleficus. on 2009-09-08
> **Joseph Schwenker said:**
> First off, the reason that I asked that question was because I wanted someone to help me SOLVE THE PROBLEM.  Telling me to "download the open source" and "compile a Mac package" helps me as much as Windows did when it said, "Error #498098: The memory at location 9283730x could not be read.  The instruction 19274u5920x will now be terminated.".  As I am beginning with Linux, I honestly have NO IDEA how to compile anything.  Also, as Ardour is an open source program, I wanted to ask it on an open source forum.  Not in some mac forum where they will say, "ardour is $[-}17 use gargebandlol".
Because you'll need to learn it eventually...

1.  Go to Ardour downloads page and click Source Code.
2.  Click Download button.
3.  Extract the archive.  Right click > Extract here.
4.  Open terminal.
5.  'cd path/to/newly/created/folder'
6.  './configure'
7.  'make'
8.  'sudo make install'
9.  ????????
10. PROFIT

No quotes on the commands.
> **Joseph Schwenker said:**
> Does not support apples?  Well, if I pay the one dollar for it, then there is always the possibility of the download failing, and then, since there is no licensing, I will have to pay AGAIN for something that I don't know even works.  Open source software is supposed to be freely distributed.  There is no purpose to open source if it is not free as in free beer.
Yes, there absolutely is.  "Free as in beer" is not why the open source movement started.  Free as in speech is why.  And either way, you don't have to pay to get it for a Mac.
> **Joseph Schwenker said:**
> What is a couple of dollars to a thirteen year old who will have to spend time convincing his mom to enter her credit card number on some weird website to download something that SHOULD BE FREE, as in terms of currency.
Again, open source does not mean free as in currency.  It means "do what you want with my program, when you want, because I said you can".  Also, Paypal.

---

### Post by modmadmike on 2009-09-08
[http://forums.macrumors.com/showthread.php?t=352977]("http://forums.macrumors.com/showthread.php?t=352977")

HOW TO COMPILE LINUX SOFTWARE FOR YOUR MAC ^^^^^    :lolflag:

---

### Post by modmadmike on 2009-09-08
> **.Maleficus. said:**
> Because you'll need to learn it eventually...

1.  Go to Ardour downloads page and click Source Code.
2.  Click Download button.
3.  Extract the archive.  Right click > Extract here.
4.  Open terminal.
5.  'cd path/to/newly/created/folder'
6.  './configure'
7.  'make'
8.  'sudo make install'
9.  ????????
10. PROFIT

No quotes on the commands.

Yes, there absolutely is.  "Free as in beer" is not why the open source movement started.  Free as in speech is why.  And either way, you don't have to pay to get it for a Mac.

Again, open source does not mean free as in currency.  It means "do what you want with my program, when you want, because I said you can".  Also, Paypal.

Since when was this 4chan /b/ lol

---

### Post by .Maleficus. on 2009-09-08
> **modmadmike said:**
> Since when was this 4chan /b/ lol
Since I made it /b/ a few minutes ago :D.

---

### Post by modmadmike on 2009-09-08
> **.Maleficus. said:**
> Since I made it /b/ a few minutes ago :D.

orly? lulz

---

### Post by bfc on 2009-09-08
> **madjr said:**
> **54k** per year in my country is being **rich** and can get you anything you want

anyway, my cousin is a open heart surgeon in **New York** and only gets **66k** a year ... 

I don't want to call you or your cousin a liar... but the only way he/she is making 66k a year as a heart surgeon is if he/she is working illegally in a back alley.

The average salary for a General Surgeon in the US is $330,000

Back on Topic, I get a little concerned regarding larger Open source projects that are not supported/sponsored by large corporations.

The reality is developers need to eat, put a roof over their heads, etc....  Working on a project "part-time" could result in long development cycles, poor code and might lead to project stagnation.  However, working part-time, is usually the only option as open-source developers are unlikely to make much, if any money off the code they produce.  

I do not think it is unreasonable for the developers of Ardour to ask for a donation. If you benefit from the project, why not contribute.

---

### Post by dmizer on 2009-09-08
> **Joseph Schwenker said:**
> First off, the reason that I asked that question was because I wanted someone to help me SOLVE THE PROBLEM. Telling me to "download the open source" and "compile a Mac package" helps me as much as Windows did when it said, "Error #498098: The memory at location 9283730x could not be read. The instruction 19274u5920x will now be terminated.". As I am beginning with Linux, I honestly have NO IDEA how to compile anything. Also, as Ardour is an open source program, I wanted to ask it on an open source forum. Not in some mac forum where they will say, "ardour is $[-}17 use gargebandlol".
As I said before. Since your problem is Mac specific, you should present your issue before an audience of peers who understand Mac. Not an audience of peers who understand that the GPL means that the code is open, not that the code is free of cost.

So, as many other people have pointed out, your problem (believing that open source should be free of cost) isn't really a problem because nowhere does it say that open source = free of cost. The GPL does, however, say that [you are allowed]("http://www.gnu.org/licenses/gpl-faq.html#DoesTheGPLAllowMoney") [charge money]("http://www.gnu.org/licenses/gpl-faq.html#DoesTheGPLAllowMoney") [for your code]("http://www.gnu.org/philosophy/selling.html").

Finally, Ardour is an open source program. Due to the nature of open source, if your platform (in this case OSX) does not have a prepackaged download available, you must compile your own (or in this case, pay money for the packaged download).

---

### Post by RiceMonster on 2009-09-08
> **modmadmike said:**
> Since when was this 4chan /b/ lol

this is /uf/ didn't you know?

---

### Post by Mistrblank on 2009-09-08
> **Exodist said:**
> Now I dont mind making donations when I can afford them. And right now isnt a good time due to the economy going to complete crap around here. But I was shocked they complained they couldnt pay a full time programmer there yearly salary of $54K.. HOLY CRAP.. I am a full time machinist and I only make about half that.. $54,000 is a bit much.. half that would be understandable.

Sorry for you then.  I make more than that where I am and that's being UNDERPAID.  Fact of the matter is that cost of living is different in different areas of the world and even varies across a single country in some cases.

Does it make you feel better if I said they haven't met the goal of paying 2 developers a fulltime salary of $27k?  I'm pretty sure even two full time developers isn't quite enough to support advancement of the software in addition to website and distribution costs (bandwidth is NOT free either).

---

### Post by t0p on 2009-09-08
> **Joseph Schwenker said:**
> So then what abut the Mac version?

Yeah right, what about the Mac version?  Does anyone care?  Only other Mac users.  Does anyone care about them?  Only other Mac users...

:p

---

### Post by hanzomon4 on 2009-09-09
Ok... this person has been ripped anew, I think he's had enough now. I hope there's no hard feelings...

---

### Post by FunkyRes on 2009-09-09
> **shadylookin said:**
> 54k for a developer is a rather modest salary.

No kidding - a decade ago I was making 60K as a first year developer.

---

### Post by Viva on 2009-09-09
> **hanzomon4 said:**
> Ok... this person has been ripped anew, I think he's had enough now. I hope there's no hard feelings...

+1

The mob mentality is the biggest evil on the internet, but you can't help but be a part of the mob.

---

### Post by Joseph Schwenker on 2009-09-09
> **.Maleficus. said:**
> Because you'll need to learn it eventually...

1.  Go to Ardour downloads page and click Source Code.
2.  Click Download button.
3.  Extract the archive.  Right click > Extract here.
4.  Open terminal.
5.  'cd path/to/newly/created/folder'
6.  './configure'
7.  'make'
8.  'sudo make install'
9.  ????????
10. PROFIT

No quotes on the commands.

Yes, there absolutely is.  "Free as in beer" is not why the open source movement started.  Free as in speech is why.  And either way, you don't have to pay to get it for a Mac.

Again, open source does not mean free as in currency.  It means "do what you want with my program, when you want, because I said you can".  Also, Paypal.

./configure does nothing.  Make returns an error message.  Sudo make install returns an error message.  And, with Paypal, you still have to enter your credit card on a site.

---

### Post by hanzomon4 on 2009-09-10
> **Joseph Schwenker said:**
> ./configure does nothing.  Make returns an error message.  Sudo make install returns an error message.  And, with Paypal, you still have to enter your credit card on a site.

Ok whenever you compile something from source you need certain dev packages.. One way to get them is 

sudo apt-get build-dep ardour

Are you on Ubuntu or OSX?

[The Directions from the Ardour site]("http://ardour.org/building") on building from source. I'll try to walk you through it. It's much easier then it looks. Just let me know the first thing you don't understand and we will go from there. 

By the way Ardour uses scons, so instead of ./configure make make install it's scons(configure and make) scons install(make install)

---

