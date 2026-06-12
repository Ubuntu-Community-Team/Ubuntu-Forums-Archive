---
title: "Should I go Open Source?"
date: 2010-03-08
forum: The Cafe
---

### Post by BuffaloX on 2010-03-08
I'm developing a midi device like this with my wife:
[http://www.megadrum.info/]("http://www.megadrum.info/")

We started building one ourselves just for fun, it's partly based on our own designs, partly on designs from other open source projects, and it's turning out pretty good.

So we have decided to try to sell it, as there seems to be a lack of such devices that have good quality and features and are reasonably priced.

We have half decided to go full blown open source with it.
The advantages would be:
1: People can do with it what they want, like hack it to do unexpected things.
2: When out of warranty, owners can have it repaired most any place.
3: We may get constructive ideas for improvements from customers.
4: We show that we are an open and honest company, and may gain customer trust quicker.

The danger is:
Any person or company with more resources than us, or access to cheap parts or labor could build an identical or maybe even improved unit cheaper than we can, and cut us out of the market entirely.

We could replace the open source parts, and go old fashioned proprietary, but none of us would like that.

What license would be best for this project?

We are considering a clause that requires prominent display of the project name on any product based on the design or code.

What are your thoughts?

---

### Post by Kdar on 2010-03-08
Those drums look great.

I am not very technical about Open Source licence, maybe someone else can help you much more with this. But I think it would be good if you did do it this way. 

If I ever get to this stage (where I will develop something, software or hardware), I think I would put it out as Open Source.

---

### Post by foxmulder881 on 2010-03-08
It becomes personal choice when you get to the stage you are at. So basically it comes down to this:
--If you think it's good enough to sell and make $$ off, do it.
--If you open-source it, I'd say there's very little chance anyone is going to steal your idea and profit from it before you do. There's more chance if you open-source it that it will improve drastically through other peoples/developers ideas/concepts and input.

---

### Post by Kdar on 2010-03-08
If someone Open-Source something, the people who improve it are still responsible before the main author (or at least they have to reference him), right?

---

### Post by foxmulder881 on 2010-03-08
I guess that depends on what licence you release the code under.

---

### Post by BuffaloX on 2010-03-09
> **Kdar said:**
> If someone Open-Source something, the people who improve it are still responsible before the main author (or at least they have to reference him), right?

> **foxmulder881 said:**
> I guess that depends on what licence you release the code under.

I think chances are 99% that we will use either GPL 2 or 3.
With a small modification about the project name.
Kind of a reverse Firefox clause about name and logo. :p

We have actually been considering this from many angles, and I think it's pretty safe to say it will be a full blown open source project.
I will post here when we have the finished product. :D

---

### Post by ssam on 2010-03-09
> **BuffaloX said:**
> 
We started building one ourselves just for fun, it's partly based on our own designs, partly on designs from other open source projects, and it's turning out pretty good.

if it is derived from other opensource projects you need to check their licences. If they have GPL/share-a-like style clauses then your derivative will need to be open source.

as with any project, the most interesting use of it will probably be though of by somebody else. making it open source makes their life easier.

---

### Post by yoasif on 2010-03-09
[http://www.arduino.cc/](http://www.arduino.cc/)
[http://www.wired.com/print/techbiz/startups/magazine/16-11/ff_openmanufacturing](http://www.wired.com/print/techbiz/startups/magazine/16-11/ff_openmanufacturing)
[http://en.wikipedia.org/wiki/Arduino](http://en.wikipedia.org/wiki/Arduino)

---

### Post by dearingj on 2010-03-09
Perhaps you should try to register a patent on its design, then donate the patent to something like the [Open Invention Network]("http://www.openinventionnetwork.com/").

---

### Post by earthpigg on 2010-03-09
GPLv3, specifically, may be best for this project. your setup looks like it could potentially become a future victim of [tivoisation]("http://en.wikipedia.org/wiki/Tivoization").

> Any person or company with more resources than us, or access to cheap parts or labor could build an identical or maybe even improved unit cheaper than we can, and cut us out of the market entirely.

you could still sell support - in this case, maybe preformed rhythms.

> We are considering a clause that requires prominent display of the project name on any product based on the design or code.

considered bad form -- the old BSD license did that.


what about this: dual license, like virtualbox. Release it under the GPLv3 and a proprietary license. MySQL does this. Google does this with chrome.

maybe the GPLv3 version of the software has all of the technical stuff going for it (and includes all of the open source code you got from wherever you got it from, and will still benefit from the FOSS dev model), but the proprietary version has pretty bells and whistles? like rhythms you made, or a fully featured GUI, or whatnot.

you would have to look into details about which parts of code you used are LGPL, which are GPL, etc... and then look at the exact requirements to be or not to be considered a 'derivative work' - i imagine the FSF website can give you guidance on that. 

dual licensing something you create like that means that *you* can release proprietary, but no one else can.


edit: and to protect yourself from some company releasing a similar product (think guitar hero 6, or whatever the next version is), and then coming after you for patent infringement... take a look at these guys: [http://www.openinventionnetwork.com/](http://www.openinventionnetwork.com/) ... not only will none of them file suit against you if you join, but if someone else does then they (Sony, Red Hat, Phillips, Novell, etc) will provide your legal team.

question i have: can they release the 'art' aspects of this software under a restrictive [creative commons attribution and non-commercial license]("http://creativecommons.org/licenses/by-nc-nd/3.0/us/"), while keeping the software GPL'd? if what sets your product apart from all others is the art, and not the software, then that could very well be enough.

---

### Post by BuffaloX on 2010-03-11
Thanks for the valuable input guys. :D

> **ssam said:**
> if it is derived from other opensource projects you need to check their licences. If they have GPL/share-a-like style clauses then your derivative will need to be open source.

as with any project, the most interesting use of it will probably be though of by somebody else. making it open source makes their life easier.

1: You are absolutely right, and we will fully respect any license of any part hardware or software we use in the final product, which is why a proprietary version would take longer to develop.

2: We think that too.

> **yoasif said:**
> [http://www.arduino.cc/](http://www.arduino.cc/)
[http://www.wired.com/print/techbiz/startups/magazine/16-11/ff_openmanufacturing](http://www.wired.com/print/techbiz/startups/magazine/16-11/ff_openmanufacturing)
[http://en.wikipedia.org/wiki/Arduino](http://en.wikipedia.org/wiki/Arduino)

Thanks fgor the links, We are already using the Arduino for our  prototype, but we have made our own design for the production version.
Arduino is an awesome development platform which has sped up the design process immensely.
The second link was a very interesting read. If we could have half thei success we would be very happy. ;)

> **dearingj said:**
> Perhaps you should try to register a patent on its design, then donate the patent to something like the [Open Invention Network]("http://www.openinventionnetwork.com/").

Isn't that expensive? Maybe if we make loads of money...

**********************

> **earthpigg said:**
> GPLv3, specifically, may be best for this project. your setup looks like it could potentially become a future victim of [tivoisation]("http://en.wikipedia.org/wiki/Tivoization").


I think GPL3 is only good for software, not so good for hardware.
I don't think Tivoization is a serious danger for such a small project.
But still I would hate if it happened.

> **earthpigg said:**
> 
you could still sell support - in this case, maybe preformed rhythms.


Are you kidding? I don't think that is very likely.

> **earthpigg said:**
> 
considered bad form -- the old BSD license did that.


This is interesting, Why is it bad form?
Could this requirement be implemented in a way that is not bad form?
Sort of the reverse of Firefox.
The idea is to prevent "theft" and to promote the project.

> **earthpigg said:**
> 
what about this: dual license, like virtualbox. Release it under the GPLv3 and a proprietary license. MySQL does this. Google does this with chrome.


We have been talking about this, and we will probably do that, but we're not quite sure how it works for content contributed by the community?

> **earthpigg said:**
> 
maybe the GPLv3 version of the software has all of the technical stuff going for it (and includes all of the open source code you got from wherever you got it from, and will still benefit from the FOSS dev model), but the proprietary version has pretty bells and whistles? like rhythms you made, or a fully featured GUI, or whatnot.


We are considering supplying an Ubuntu Studio DVD, modified to include a complete sampled drumkit, we might copyright the drumkit samples, because we don't want the competition to just copy it.
But there is a serious lack of good free drumkits, so maybe we "copy left" that too, it could be good advertising.

> **earthpigg said:**
> 
you would have to look into details about which parts of code you used are LGPL, which are GPL, etc... and then look at the exact requirements to be or not to be considered a 'derivative work' - i imagine the FSF website can give you guidance on that. 


Yes really boring. Not looking so much forward to that part.
But unless some weird licenses or clauses are used, I don't foresee any real problems. It's very likely we will end up only using a library for Serial, USB and LCD communications, the rest is already mostly rewritten.
Still we plan to include a lot of other stuff in our credit notice, because it has helped us in the beginning.

> **earthpigg said:**
> 
dual licensing something you create like that means that *you* can release proprietary, but no one else can.

Unless we allow it, one beer per license. :p

> **earthpigg said:**
> 
edit: and to protect yourself from some company releasing a similar product (think guitar hero 6, or whatever the next version is), and then coming after you for patent infringement... take a look at these guys: [http://www.openinventionnetwork.com/](http://www.openinventionnetwork.com/) ... not only will none of them file suit against you if you join, but if someone else does then they (Sony, Red Hat, Phillips, Novell, etc) will provide your legal team.


Seems they only defend the use of Linux. We intend to supply a Linux DVD, but I think we will be covered by whatever covers the Distro.

> **earthpigg said:**
> 
question i have: can they release the 'art' aspects of this software under a restrictive [creative commons attribution and non-commercial license]("http://creativecommons.org/licenses/by-nc-nd/3.0/us/"), while keeping the software GPL'd? if what sets your product apart from all others is the art, and not the software, then that could very well be enough.

I think that for now that would be grasping for straws.

Again thank you all for the valuable input. :D

UPDATE:
We just tested the prototype. The results are very encouraging.
There is no perceptible lag or latency, and the reading is so fast it registers even if you hit the same drum with two sticks almost simultaneously (the hardest possible test to pass for most E-drums). The sensitivity settings are perfect, and we haven't even optimized that part yet, it's based solely on theoretical estimates.
There are no accidental triggings. (noise) 

I'm a little proud, because we have made huge improvements compared to the algorithms used by another project, I estimate 18 times faster! and with better precession.
This was our first real test run, and already it works much better than the "pro" one my wife is using now.

---

### Post by pizza-is-good on 2010-03-11
You can Open Source it but still make people pay for it, and still have a trademark, copyright and patent on it. Open Source just means that you are willing to give people the source so that they can fully edit their program. It's all about how much you want to 'open source'(if it can be used as a verb..) it

~pizza

---

### Post by earthpigg on 2010-03-12
> [QUOTE][a required advertising clause is] considered bad form -- the old BSD license did that.
This is interesting, Why is it bad form?
Could this requirement be implemented in a way that is not bad form?[/QUOTE]

your project says forks have to say "based on BuffaloX's stuff" somewhere.

the fork adds a "must say based on fork1's stuff" part.

next fork adds "fork2"

pretty soon you can't distribute the project without 500 "based on" lines. Berkeley wanted Berkeley to be advertised in any fork of BSD, but eventually abandoned the requirement. they realized that for those that are interested or care, they will soon realize that OS X and FreeBSD have stuff in it that came from UC Berkeley **_with or without_** the mandatory advertising clause. 

the old BSD license was abandoned by Berkeley in 1999, iirc.

> [QUOTE]what about this: dual license, like virtualbox. Release it under the GPLv3 and a proprietary license. MySQL does this. Google does this with chrome.
We have been talking about this, and we will probably do that, but we're not quite sure how it works for content contributed by the community?[/QUOTE]

go dig around the Google Chrome open source page. for code to be accepted into Google Chrome, you first must transfer all copyright ownership of it to Google. since google owns it, they can then re-release it as proprietary. GNU stuff does the same thing. Lot's of open source projects do, dual license or no.

> We are considering supplying an Ubuntu Studio DVD, modified to include a complete sampled drumkit, we might copyright the drumkit samples, because we don't want the competition to just copy it.
But there is a serious lack of good free drumkits, so maybe we "copy left" that too, it could be good advertising.

you own the copyright by default to anything you (you the person, you the company, doesn't matter) create. maybe copyleft ***some*** of the drumkit samples? Nine Inch Nails released an album under the Creative Commons license. so ***some*** of their music can be copied, modified, etc, freely, but ***some*** of it must still be purchased. the free stuff advertises the non-free stuff.




something else you could consider, that could work as long as most people are windows users:

Linux version == fully GPL, traditional Free Software.
Windows and Mac version == proprietary only.

sooo Windows users could pop in the Ubuntu LiveCD with your software preinstalled and use it there, but if they want to use it in windows then they have to pay.

see: [http://en.wikipedia.org/wiki/GCompris](http://en.wikipedia.org/wiki/GCompris)

> It is available for Linux, Mac OS X and other systems. Binaries compiled for Microsoft Windows version are distributed as crippleware with a restricted number of activities; it is possible to access all the activities in Windows for a fee.

[http://gcompris.net/-Download-](http://gcompris.net/-Download-)

it kinda means Microsoft Windows users pay for the development of Free Software in order for it to be freely available to all GNU/Linux users.

---

