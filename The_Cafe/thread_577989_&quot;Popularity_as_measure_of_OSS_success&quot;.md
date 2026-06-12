---
title: "&quot;Popularity as measure of OSS success&quot;"
date: 2007-10-16
forum: The Cafe
---

### Post by 23meg on 2007-10-16
A bright article by our X maintainer [Bryce Harrington]("https://wiki.ubuntu.com/BryceHarrington"), from 2005. It deals with what can be an important issue for Ubuntu in the future: the ratio of contributors to "plain users".

[http://www.advogato.org/person/bwh/diary.html?start=38](http://www.advogato.org/person/bwh/diary.html?start=38)

> 
[SIZE="4"]**Popularity as measure of OSS success**[/SIZE]

A couple months ago we released Inkscape 0.42 and it got announced on Slashdot. Someone replied to one of my posts regarding Inkscape's goals.

[INDENT]*Third, building a huge userbase is not really among Inkscape's principle goals. We want to be a great application that helps make Open Source successful. *[/INDENT]

*...isn't popularity a rather large standard for judging success of a project? ...I guess I don't readily know the terms of "success" that Open Source has. If it's not to be reasonably widely accepted, easy to use, and able to help other open-source projects, I don't know what it is.*

I'm making a blog entry out of my reply because this is a common conception a lot of people have, and something we philosophized in great depth early on with Inkscape.

Sometimes you hear the advice with coding, "avoid premature optimization". Well, it's similarly important to "avoid premature popularity."

Now, for the vast majority of open source projects, popularity simply isn't an issue. I've easily had ten projects that never gained users for every one that did. For one reason or another, no matter how much you love your OSS project idea, it probably won't gain any users beyond yourself. Obviously, if the project meets your own particular needs, you can count it as a success.

But those aren't the type of projects I'm going to talk about here. I want to focus on the ones that *do* have the popularity problem; the ones that have the potential to have huge userbases.

**[SIZE="3"]Value Stream in Open Source[/SIZE]**

Let's start by defining success to be something which is "increasing in value". A company that has increased its profits by 100% is successful. A worker who has increased their net worth by 10% has succeeded. Value can be non-monetary; an environmentalist who saved 10 more forests from being cut down than last year is successful.

The fundamental misunderstanding regarding the importance to users in open source is that users in and of themselves are valuable. Users in OSS do not directly produce value. I think people get confused about this because in open source, users are not "customers", as occurs with commercial software.

With commercial software your value stream derives from users who purchase the software in a store. The user pays $50 or whatever for the software, which gets divvied out to the distributor, marketing folks, developers, and so on as salary to help them all continue producing software. The user is the source of the value that makes the system work, thus clearly in this case the user is the customer.

Now, in Open Source, users aren't paying that $50 per copy, and thus aren't covering the developers salaries. In some cases they do sponsor the developer to do work, but these situations are unfortunately rare, and we'll ignore them as the exception, not the rule. (Anecdotally, size of userbase does not seem to correlate with number of paying users; this seems to be driven more by the type of software and its criticality to the user's business model.)

So where *does* the value come from in the open source system? What enables the software itself to get better? In this case, it isn't money from users to cover developer salaries, but instead is the good souls who make contributions to the project in the form of patches, bug fixes, documentation, testing, marketing, and so forth. The value system for open source is much more direct than with commercial software - there isn't a transformation into monetary currency; the customer can directly contribute their value to the codebase.

Thus, I believe the customer for open source projects are the people who contribute back to those projects. This is a weird concept - the customer is not the consumer, but the _producer_.

From this line of thinking, we can define success a bit more accurately. A successful open source project is one that is increasing in value quickly, through the generation of improvements to the project.

Thus it can be seen that what you want to optimize for is number of contributors, not number of users. The number of users is still important, but indirectly; more users often (but not always) means more potential developers.

[SIZE="3"]**Signal to Noise**[/SIZE]

One of the main issues to having a large number of users is that they can unfortunately cause an increase in the amount of "noise" in a project. They ask questions that take time to answer, they can get into arguments, locate bugs that the developers are not prepared to fix, and otherwise increase the number of demands on the developers.

So long as the ratio of developers to users remains consistent, this is not an issue. If you can be sure that for every 100 users, say, you gain 1 new contributor, growth can be a good thing.

Unfortunately, in many situations it's a case of diminishing returns. For instance, producing a Windows version of your program can greatly swell your userbase, yet on Windows there is a much lower ratio of developers to users. Development tools are not as easily at hand as they are for Linux. The ideals of open source aren't nearly so prevalent among Windows users as they are for Linux. People are more accustomed to software that either "just works" or that has its lid welded shut so they can't contribute. The new users bring a whole host of new needs and demands on your time, but without the additional development assistance, this effectively *reduces* the value of the project since it must devote its existing developers to these new users.

[SIZE="3"]**Focus on Values**[/SIZE]

My final point is that even if users *were* valuable in an open source project, focusing on userbase size as a goal is the wrong approach.

In business school they tell you to focus not on "making money" but on "making the business". If you focus on making the business strong and good, the money has a tendancy to find a way to take care of itself.

Similarly for open source. Don't worry about your userbase. Focus on making your software as good as it can be. Think about what *you* want, or what your existing real users need, not some imagined "if only we had X we'd have more users". Focusing on real, present needs of real, present people ensures that your work will generate benefit in the near term, enabling you to build a feeling of momentum that will carry your project a lot further. If you do this and do it well, the userbase will take care of itself. 

---

### Post by euler_fan on 2007-10-16
It's definitely an interesting article. Thanks for posting it.

Given the author's exhortation for open source developers to stick to their core values, cue flame war over what Ubuntu devs should and should not value. (Please, no flame war, but it's a touchy issue nonetheless.)

---

### Post by Ireclan on 2007-10-16
I think the article has a good point, and I enjoyed reading it. Though, it DID seem to downplay the importance of users a bit. Users are useful because they have the potential to get you more developers.

---

### Post by 23meg on 2007-10-16
> **euler_fan said:**
> It's definitely an interesting article. Thanks for posting it.


Good to know someone is interested.

[QUOTE=Ireclan]I think the article has a good point, and I enjoyed reading it. Though, it DID seem to downplay the importance of users a bit. Users are useful because they have the potential to get you more developers.[/QUOTE]

Which is a point made in the article: if more users also means more contributors, that's fine. If it doesn't, problems arise after a while.

---

### Post by Wolki on 2007-10-17
Very interesting read, thanks for pointing it out.

One thing that's a bit underrepresented is motivation, having many users and getting interesting feedback from them can keep motivation from volunteers high. On the other hand, being treated like you killed their favorite pet because of a decision someone doesn't like, or because you can't spend 28 Hours each day working for free, probably kills just as much motivation. I wonder, as the userbase grows, which group grows faster...

---

### Post by Sporkman on 2008-04-08
> A large number of users...locate bugs that the developers are not prepared to fix...

Boo hoo! :lol:

---

