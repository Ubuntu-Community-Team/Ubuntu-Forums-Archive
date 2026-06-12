---
title: "Yoga - Program Idea"
date: 2014-03-12
forum: Ubuntu Application Development
---

### Post by Toliot on 2014-03-12
Hello great community of ubuntu!

I was just about to do some exercise(yoga in fact) when an idea came to my mind, a program that tells you to do yoga and lets you decide what yoga poses you want to do!
OK I know this has probably been done before(just remembering now I think it exists on the iOS app-market) but I quickly checked on Ubuntu Software Center and there doesn't seem to be anything of the like, so I'm thinking I would like to do this project, hopefully with others if there are other like-minded people here. I need to declare that I'm not very good at programming yet and thus this project will probably take quite awhile to actually finish but any supporting ideas/guides/frameworks that you guys can come up with I would gladly appreciate.

Working out is an important aspect of healthy living in my opinion, and me being a relatively lazy person, I like to do yoga, I recommend that everyone tries it, at any degree of strength because there are many poses of varying difficulty that even the most advanced will have difficulty doing and yet the progression is very light and you can easily build up the balance/core strength to do most of the poses within... I can't speak as a professional but i'd say about a month if your completely out of shape. To be honest I used to lift weights but now I'm too lazy so I'll just do yoga.

Basically what I'd like to gear this thread at it is how should I go about creating this program(because I frankly have no clue :( ), and hopefully in C, because I'm learning C.

Any help would be great! I look forward to your ideas guys :D

and if you guys know any similar programs already please don't hesitate to add a post of it please! :D

---

### Post by Dave_L on 2014-03-12
I found this by searching for "yoga software": [http://www.healthandyoga.com/html/yoga/yguide.aspx](http://www.healthandyoga.com/html/yoga/yguide.aspx)
Unfortunately, it's non-free and WIndows-only.

---

### Post by Toliot on 2014-03-12
> **Dave_L said:**
> I found this by searching for "yoga software": [http://www.healthandyoga.com/html/yoga/yguide.aspx](http://www.healthandyoga.com/html/yoga/yguide.aspx)
Unfortunately, it's non-free and WIndows-only.

Thanks a lot for looking into it!

Now we need to find a way to make it for linux :)

Any ideas at all about how I should go about this ?? :confused: 

regards,

---

### Post by Dave_L on 2014-03-13
One appproach is to start by writing a User Manual for the program. Pretend the program exists, and provide complete documentation that tells someone how to use it.

---

### Post by Toliot on 2014-03-13
> **Dave_L said:**
> One appproach is to start by writing a User Manual for the program. Pretend the program exists, and provide complete documentation that tells someone how to use it.

How about modelling it off the documentation from the windows-program above? Would that work? Or are there a lot of internal differences between OS's that would make this counter-intuitive? Furthermore would it thus make sense to look at the source of the program mentioned? (I don't know how to go about de-compiling) 
I know this sounds like a cop-out but I'm honestly just putting my toe into the ocean and think modelling an existing application would help me develop at least some kind of knowledge-base.

I've been thinking about a similar issue, does windows use .dll's the same way ubuntu does?(guessing that's a no because of the way repositories work)

Any help is greatly appreciated!

Thanks guys :D

---

### Post by Dave_L on 2014-03-14
De-compiling, even if successful, would be not be useful. Using the results would likely violate copyrights. And I doubt if the source code is available, since it's a commercial product.

Implementation details such as .dll's, or differences between the operating systems, are not relevant at this point.

Looking at that Window program's documentation could be helpful to get ideas, but even there you have to be careful about copying. Documentation is protected by copyright too.

*The first step is to decide exactly what you want the program to do, from the viewpoint of a user.*

A mind-mapping tool such as FreeMind, which is available in the Ubuntu repositories, is very handy for outlining a project such as this.

---

### Post by Archer920 on 2014-04-19
I'm interested, but I don't know anything about yoga. I do know quite a bit about programming :-) and can code in c++ or Java (i.e. we could use QT, Swing, or GTK-java?) I agree that a windows program should be back-compiled, but is there any reason why we couldn't clone it?

---

