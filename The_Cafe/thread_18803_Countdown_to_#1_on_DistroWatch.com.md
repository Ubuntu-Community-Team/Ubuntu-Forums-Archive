---
title: "Countdown to #1 on DistroWatch.com"
date: 2005-03-08
forum: The Cafe
---

### Post by tkiesel on 2005-03-08
... specifically the 'Last 6 months' Page Hit Ranking that displays by default when visiting DistroWatch.com.  There's been talk of having a party the day that Ubuntu reaches #1 on the list, so I thought I'd start a thread to keep track of progress toward U#1.

Yes, I know that this is ultimately just numbers on a webpage. Since when do people need any more of a reason to have a party though?  :-D 

As a side-note, I've been collecting data on the 'Last 1 month' rankings as well. Ubuntu currently sits at #1 on that ranking, but MEPIS is fast ascending towards the top spot. Way to go MEPIS!

Now, the main event.  I've got 16 days of data so far, dating back to February 16. There are some holes at times when my wife and I were more than a little ill. Ubuntu and DistroWatch.com were far from my mind those days.  :shock: 

Ubuntu has been adding 9-10 points a day with stunning regularity. A linear curve fit on the data shows a slope between 9.5 and 9.9 with regularity, and with R-squared values in excess of 0.99 each day, the curve explains 99+% of the observed variation in the data.  I'm doubtful that it'll remain this way all the way to the top, but we'll see. :)

The current top dog, Mandrakelinux has been a bit harder to characterize, but over the last few days has settled in to where a linear curve fit explains about 90% of the variation in the data. The predicted slope has been increasing bit by bit each day, and currently stands at approximately 1.4 points each day.

Given these slopes, and the current point values of each distro, we can calculate the time in days till they intersect.

```
slope_ubuntu*time + current_score_ubuntu = slope_mandrake*time + current_score_mandrake
```

Solving for time, we get```
 time = (current_score_mandrake - current_score_ubuntu)/(slope_ubuntu - slope_mandrake)
```

DistroWatch.com updates once per day, meaning that if Ubuntu passes Mandrakelinux in the middle of a day, it won't show till the follwing day. For that reason, I take time and round up to the next whole number when predicting a date.

Current status:

curent_score_mandrake = 1517
curent_score_ubuntu = 1212
slope_mandrake = 1.3765
slope_ubuntu = 9.9849

time (days till U#1) = 35.43
_**Predicted date : April 13, 2005**_

If and when either distro displays significantly nonlinear behavior, I'll amend this estimate using different methodology. For a _really_ rough estimate though, this isn't too bad.

Now who's bringing chips to the party?

---

### Post by BWF89 on 2005-03-08
Your pretty good at math. Mabye you should be useing BSD instead of Linux :p .

---

### Post by tkiesel on 2005-03-08
[QUOTE=BWF89]Your pretty good at math. Mabye you should be useing BSD instead of Linux :p .[/QUOTE]Right over my head. I'm new to Linux/GNU/free-*nix territory. But, being a history buff, I've been reading up voraciously.  Currently burning through _*The Cathedral and the Bazaar*_ as the enchiladas warm up in the oven.  :)

My wife says she'll move to Ubuntu as soon as I can get FrontPage and Corel Photo Paint to work on it.

---

### Post by zenwhen on 2005-03-08
If Kubuntu and Ubuntu are listed separately on their site and the user base is somewhat split, your numbers will be severely destroyed. 

Not that these numbers really mean a great deal, but they could be watered down by the "brand split".

---

### Post by jdong on 2005-03-08
The other fallacy is the number of lurking variables we deal with: If Ubuntu announces a Preview Release for Hoary, then it's gonna get a surge of traffic.

If Mandrake makes AMD64 Mandrake free to download, it's gonna get a surge of traffic.


BTW, assuming linearity (or rough linearity), I suggest that you take a decently sized sample of slopes for each distro, and calculate a confidence interval.

---

### Post by jdong on 2005-03-08
Theoretically, though, a logistic curve should be a more accurate model. Oh well. Close enough :)

---

### Post by lordofkhemenu on 2005-03-08
[QUOTE=tkiesel]... specifically the 'Last 6 months' Page Hit Ranking that displays by default when visiting DistroWatch.com. There's been talk of having a party the day that Ubuntu reaches #1 on the list, so I thought I'd start a thread to keep track of progress toward U#1.

Yes, I know that this is ultimately just numbers on a webpage. Since when do people need any more of a reason to have a party though? :-D 

As a side-note, I've been collecting data on the 'Last 1 month' rankings as well. Ubuntu currently sits at #1 on that ranking, but MEPIS is fast ascending towards the top spot. Way to go MEPIS!

Now, the main event. I've got 16 days of data so far, dating back to February 16. There are some holes at times when my wife and I were more than a little ill. Ubuntu and DistroWatch.com were far from my mind those days. :shock: 

Ubuntu has been adding 9-10 points a day with stunning regularity. A linear curve fit on the data shows a slope between 9.5 and 9.9 with regularity, and with R-squared values in excess of 0.99 each day, the curve explains 99+% of the observed variation in the data. I'm doubtful that it'll remain this way all the way to the top, but we'll see. :)

The current top dog, Mandrakelinux has been a bit harder to characterize, but over the last few days has settled in to where a linear curve fit explains about 90% of the variation in the data. The predicted slope has been increasing bit by bit each day, and currently stands at approximately 1.4 points each day.

Given these slopes, and the current point values of each distro, we can calculate the time in days till they intersect.

```
slope_ubuntu*time + current_score_ubuntu = slope_mandrake*time + current_score_mandrake
```

Solving for time, we get```
 time = (current_score_mandrake - current_score_ubuntu)/(slope_ubuntu - slope_mandrake)
```

DistroWatch.com updates once per day, meaning that if Ubuntu passes Mandrakelinux in the middle of a day, it won't show till the follwing day. For that reason, I take time and round up to the next whole number when predicting a date.

Current status:

curent_score_mandrake = 1517
curent_score_ubuntu = 1212
slope_mandrake = 1.3765
slope_ubuntu = 9.9849

time (days till U#1) = 35.43
_**Predicted date : April 13, 2005**_

If and when either distro displays significantly nonlinear behavior, I'll amend this estimate using different methodology. For a _really_ rough estimate though, this isn't too bad.

Now who's bringing chips to the party?[/QUOTE]
/me stares blankly,nods head every few minutes and just says, "uh huh...okay. yes, continue..." where it seems appropriate. ;)

---

### Post by BWF89 on 2005-03-08
> Right over my head.
BSD and Un*x is an operating system for scientists. And scientists are good at math. I'm currently burning through Brave New World. Then I'll move onto 1984 and Snowball's Chance.

I think that Ubuntu should include both GNOME and KDE. Then we can crush those KUbuntu rebels! Muahahahaha!

---

### Post by tkiesel on 2005-03-08
[QUOTE=zenwhen]If Kubuntu and Ubuntu are listed separately on their site and the user base is somewhat split, your numbers will be severely destroyed. 

Not that these numbers really mean a great deal, but they could be watered down by the "brand split".[/QUOTE]

Hmmm. True. The issue then, is whether to attempt to consolidate related distros together into a mass count. Bringing in any related projects from Mandrake  would be needed for fairness. That would be predicting something different than the initial stated project though.

[QUOTE=jdong]The other fallacy is the number of lurking variables we deal with: If Ubuntu announces a Preview Release for Hoary, then it's gonna get a surge of traffic.[/QUOTE]

Yep. Fallacies abound here. As I stated, it's a _really_ rough estimate only. Ultimately, there are a freakish number of variables here, more variables than there are people visiting the DistroWatch site. To attempt to reduce the behavior to time being the single independant variable is by definition an exercise in futility to some degree or another. The question is... is it fun?

[QUOTE=jdong]Theoretically, though, a logistic curve should be a more accurate model. Oh well. Close enough [/QUOTE]

:wink: I can supply the acumulated data so far. Anyone willing to spend time on a more detailed analysis is more than welcome to do so if they desire something more than a rough guesstimate.  I'm just doing 'back-of-the envelope' style calculations here, and not even really considering the fitness of other regions of function space until I see (on a ho-hum eyeballing it level) significant non-linearity.

If I had the inclination, I could flex the ol' mental machinery from getting my physics degree, but I'm doing this more for fun than anything else.  I'm keeping a history of predicted dates for the current method (and any new ones I employ between now and then) though, to sate my curiosity.

---

### Post by TravisNewman on 2005-03-08
Actually I think we'd be JOINING them instead of crushing them, wouldn't we?

---

### Post by shimon on 2005-03-14
Ubuntu will go higher when it has something on the home page as it does many times

---

### Post by defkewl on 2005-03-14
Just click it every day. Or make a script to auto click the link. That number is based on clicks right?

---

### Post by bored2k on 2005-03-14
[QUOTE=defkewl]Just click it every day. Or make a script to auto click the link. That number is based on clicks right?[/QUOTE]
 Wouldn't that be cheating ?
We want it to be on top, but  not through those means right ? :-k

I wonder if other distro's fans are doing that :roll: though .

---

### Post by TravisNewman on 2005-03-14
Hmm, interesting point.

I would hope they wouldn't stoop to that level. And i'll be seriously disappointed if I find out any of us were doing that to get us bumped up. I'd love to be #1, but I want it to mean somehting other than "our users can click and click and click, and not even stop to pee!"

---

### Post by tkiesel on 2005-03-15
Yeah. Hopefully they just count hits from unique IP numbers each day, though that'd distort the picture with how many LANs are behind single IPs these days. I'd hope that no one's stuffing the ballot box though.  I click onto distros that sound interesting each day as the news scrolls by, giving them a decent boost, certainly. ;)

---

### Post by defkewl on 2005-03-15
[QUOTE=bored2k]Wouldn't that be cheating ?
We want it to be on top, but  not through those means right ? :-k

I wonder if other distro's fans are doing that :roll: though .[/QUOTE]
Of course. They even made a script for it.

---

### Post by Slapdash on 2005-03-15
wel I go to ubuntu.com before I go to the forums every day.
but we are 2 bhind one IP here.

---

### Post by bored2k on 2005-03-15
[QUOTE=Slapdash]wel I go to ubuntu.com before I go to the forums every day.
but we are 2 bhind one IP here.[/QUOTE]
 Maybe they should count the ubuntuforums visits ;) , that would make use #1.5 lol .

---

### Post by bored2k on 2005-03-15
[QUOTE=defkewl]Of course. They even made a script for it.[/QUOTE]
 Well that really sucks, but it's still no reason for us to cheat . If we like it so much, why would we cheat ? Or is it really not that good that its users need to cheat to make a fake #1 environment ? Tricky dilemma.

---

### Post by Burgundavia on 2005-03-15
Having read the FAQ on the counters, yes they count individual ips. In addition, only one hit per IP per day is allowed for each distro.

[http://distrowatch.com/dwres.php?resource=faq](http://distrowatch.com/dwres.php?resource=faq)
Scroll down to "What is this "Page Hit Ranking"?"

Corey

---

### Post by jsgotangco on 2005-03-15
But it's only about page hits, not users or adoptors! It would be nice if Ubuntu is tops on users and adoption instead of page hits!

But #1 on page hits is a good start :)

---

### Post by Buffalo Soldier on 2005-03-15
[QUOTE=BWF89]BSD and Un*x is an operating system for scientists. And scientists are good at math. I'm currently burning through Brave New World. Then I'll move onto 1984 and Snowball's Chance.

I think that Ubuntu should include both GNOME and KDE. Then we can crush those KUbuntu rebels! Muahahahaha![/QUOTE]
I'm sorry to say that you maybe be a little bit misguided about BSD and Unix there. Maybe a little bit more reading would do some good:[list]
[*] [What is FreeBSD](http://www.freebsd.org/doc/en_US.ISO8859-1/books/faq/introduction.html#WHAT-IS-FREEBSD) - a variant of BSD, but it should give the right general impression.
[*] [A Brief History of FreeBSD](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/history.html)
[/list]

I don't use KDE, but I have no problem with KDE or its users. And it's wrong to label Kubuntu users as rebels. Kubuntu **is** a part of Ubuntu. [Ubuntu Wiki page on Kubuntu](https://www.ubuntulinux.org/wiki/Kubuntu)> The Kubuntu project aims to be to KDE what Ubuntu is to Gnome: a great integrated distro with all the great features of Ubuntu, but based on the KDE desktop. Kubuntu is released regularly and predictably.

---

### Post by lao_V on 2005-03-18
Have a look at this [post]("http://www.ubuntuforums.org/showthread.php?t=15560&page=1&pp=10")

---

### Post by Buffalo Soldier on 2005-03-18
[QUOTE=lao_V]Have a look at this [post]("http://www.ubuntuforums.org/showthread.php?t=15560&page=1&pp=10")[/QUOTE]

But still there are currently for people who voted for Ubuntu will never be number 1.

---

### Post by poofyhairguy on 2005-03-21
[QUOTE=defkewl]Just click it every day. Or make a script to auto click the link. That number is based on clicks right?[/QUOTE]


I try to go to distowatch everyday....

---

### Post by HungSquirrel on 2005-03-21
Ubuntu is #2 on the 6-month list with 1536 hits per day.

---

