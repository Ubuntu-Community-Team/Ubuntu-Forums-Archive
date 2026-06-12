---
title: "Attention software developers everywhere!"
date: 2011-12-13
forum: The Cafe
---

### Post by ffej2ffej on 2011-12-13
Seriously, when creating software of any kind, do the authors EVER ask themselves, "What if people use this?  How should I make the experience for them?"  Instead, EVERYTHING EVERYWHERE is made as though the author and his close circle of friends are the only people who are ever going to use it.  
Everything I use nowadays from operating systems to the most novel of applications requires HOURS searching and reading of blogs, wikis, discussion groups, etc., etc. to find out why the damned thing doesn't work like it says it will in its own instructions!!!
My latest problem is with LAMP.  A decade or more ago, I made a fully functioning LAMP and WAMP computer in ONE FREAKING DAY!!  It was simply a matter of downloading and installing the software and it worked!!  Now, after several days of work, I have a LA_P computer that works, but I'm starting to think I'm going to have uninstall and recompile Apache to make it recognize MySQL.  Keep in mind that MySQL is already installed, working and has at least 1 database that I created that works as expected.
So let me say this to people who author software:  TRY IT BEFORE YOU RELEASE IT!!  Try it on your mother-in-law who cannot even plug in her coffee machine.  Try it on your 8 year old son.  Try it on other people who are NOT in your circle of nerdy friends (I'm not passing judgement as I'm a nerd myself!).  Lastly, if there is some configuration that needs to be done, INCLUDE IT IN THE INSTRUCTIONS!!  This means running the  configuration application before you try to run the software. This means TELLING THE USER how to configure the settings that are in a text file 30 folders deep that is nowhere near the folder where the application installed.  This means if you find a situation that only works with a workaround, INCLUDE IT IN THE INSTRUCTIONS!!
Please, please help!!

---

### Post by coffeecat on 2011-12-13
Not a technical support request.

*Thread moved to **The Community Cafe**.*

---

### Post by lykwydchykyn on 2011-12-13
So it turns out that every piece of software we need to make the free software desktop totally rock has actually been written, but it's not released yet because the authors are still testing it against every possible combination of hardware, software, and user to make sure there are never problems or misunderstandings.

Until they're finished, we're stuck with the software that's only been tested by the "nerdy circle of friends".  

They're almost done, but people keep releasing new hardware and software, and keep making new people, so it's hard to keep up.

;)

---

### Post by Dangertux on 2011-12-13
sudo apt-get install lamp-server^

Solved

---

### Post by juancarlospaco on 2011-12-13
[http://en.wikipedia.org/wiki/Paragraph](http://en.wikipedia.org/wiki/Paragraph) 

Apache recognize MySQL? &#10687;_&#10687;

Get [https://www.djangoproject.com](https://www.djangoproject.com) or [http://bottlepy.org](http://bottlepy.org) maybe...

---

### Post by rg4w on 2011-12-13
[Steve McConnell]("http://en.wikipedia.org/wiki/Steve_McConnell") describes the difference between a tool and a product kinda like this:

With a tool it need only be possible to use it correctly, but with a product it should be impossible to use it incorrectly.

I like that distinction, as it clarifies the order-of-magnitude greater work required to make a truly great product.

We often think of software as free because so many thousands of people have graciously donated their time to delivering free software.

But software is very expensive to create, and those who provide us with the gift of thousands of hours of their effort still need to eat and keep a roof over their head.

I produce commercial proprietary software for a living, and use a portion of the proceeds derived from that work to afford the luxury of also contributing to some modest FOSS projects.

Most of the commercial products I work on follow a process very much like you describe, thorough in both user testing and documentation.

But that's because we can afford to with those projects, paid for as they are with licensing fees.

The FOSS projects I work on are not nearly as well documented, do not provide the same level of affordance throughout the UI, and support is provided by an earnest group on a discussion list but not nearly as promptly or completely as we can afford to do with our commercial products.

Not all FOSS projects are as slackerly as the ones I work on, but that's often because some very large player has kicked in substantial funding to help things along.  Canonical, IBM, Google, even to some degree Apple, and many others have provided many millions to some of the larger FOSS projects, and the quality of those projects reflects that.

And now and then even smaller projects with modest funding exhibit the sort of thoroughness in their process that you describe.

But the economic reality of the expense of making software means that such projects are relatively few and far between.  Programmers have to eat too, so they can afford to spend only so much time giving away their work for free and need to spend much of their time doing other things to pay for it.

Often a free software will begin with a programmer who simply makes something she needs for herself, and having done that she may share it with the community but may not have the time to document it or refine its UI beyond what she needs for herself.

So this is where the community can step in to help:

Most free software is licensed in a way that encourages community participation. Dive in, the water's fine.  Got mad programming skills?  Consider adding a feature you need.  Have a background in design?  Perhaps you can donate icon or splash screen artwork.   Good with words?  You can write tutorials or references guides for the package.

Free software is a gift, paid for by the developers who created it.  We can help subsidize it by contributing to the work, to help turn good software into great software together.

---

### Post by JDShu on 2011-12-13
I'd be incredibly impressed if your mother-in-law who can't plug in a coffee machine and your 11 year old son knew what LAMP was and needed to set it up on their systems.

---

### Post by 3Miro on 2011-12-13
> **ffej2ffej said:**
> 
So let me say this to people who author software:  TRY IT BEFORE YOU RELEASE IT!!  Try it on your mother-in-law who cannot even plug in her coffee machine.  Try it on your 8 year old son.  Try it on other people who are NOT in your circle of nerdy friends (I'm not passing judgement as I'm a nerd myself!).  Lastly, if there is some configuration that needs to be done, INCLUDE IT IN THE INSTRUCTIONS!!  This means running the  configuration application before you try to run the software. This means TELLING THE USER how to configure the settings that are in a text file 30 folders deep that is nowhere near the folder where the application installed.  This means if you find a situation that only works with a workaround, INCLUDE IT IN THE INSTRUCTIONS!!
Please, please help!!

What makes you think that developers are actually not doing that? If you have 5 - 10 developers and they all try the software on 2 - 3 machines, then you get 15 - 30 configurations out of thousands if not millions. And LAMP isn't something that a computer illiterate mother-in-law would use.

---

### Post by Docaltmed on 2011-12-13
R.A.N.T Scale:

Readability: 3 points for judicious use of ALL CAPS
Accessibility: 1.4 points. What's LAMP?
Newsworthiness: 1 point. I have never, ever heard anyone complain that FOSS has too many bugs before. Ever.
Tanquaminity: 4 points. College level.

Total on the RANT scale: 9.5 out of 20. Sorry, try harder next time.

---

### Post by Copper Bezel on 2011-12-13
> tanquaminity
I like your word here. What does it mean?

---

### Post by Primefalcon on 2011-12-13
```
sudo apt-get install apache2 php5 mysql-server; sudo shutdown -r now
```

really that'll get you a working lamp server... the working directory will be /var/www/ now that's not too hard is it?

you could even do this graphically through the software center or synaptic

---

### Post by CharlesA on 2011-12-13
> **Copper Bezel said:**
> I like your word here. What does it mean?
It's a new word. I cannot find it in any dictionaries.

@OP: Configuring a LAMP server isn't really that hard. May I suggest reading this?

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by ffej2ffej on 2011-12-13
First, thank you Dangertux.  Your solution worked. However, on the 1st try, I assumed the carat (^) at the end was a typo.  The reason I bring up the carat is because I'll bet I could have searched for (insert time frame here) on Linux boards, Ubuntu boards, apt-get boards and a few others besides and NOT found that syntax.  I still don't know why the carat is required.  (_Teach_ a man to fish!)
rg4w, thank you for articulating as you did.  I wholeheartedly agree with every word you said.  I won't bore you with my history as a hobbyist programmer, but I want to say that recently I spent about a year with Google's Android SDK on several platforms. Before that, about 5 years on Apple's XCode and have ZERO to show for it.
Finally, let me conclude with this thought.  Whenever developing a program that runs from the command line (terminal window) with switches, make your program understand the switch -ddastnww.*



*(Don't Do Anything Stupid That Nobody Would Want)

---

### Post by Primefalcon on 2011-12-13
I've been using Linux since 2007 and have been installing lamp servers the way I said above.... and honestly... I hadn't seen that method with the caret either...

Kinda wondering why it does work, I di an apt-cache search for any meta package that contains lamp-server and nothing came back so....

---

### Post by Dangertux on 2011-12-13
The carat indicates that it is a tasksel task or group of packages. It includes the packages that Primefalcon mentioned.

Another example

```

sudo apt-get install dns-server^

```


It's kind of like yum groupinstall under RHEL/CentOS

```

su -c 'yum groupinstall "Web Server" "MySQL Database"'

```

Hope this helps.

---

### Post by haqking on 2011-12-13
edit: DT ninja'd me on tasksel

though i didnt think it was used much anymore on newer systems

---

### Post by Telengard C64 on 2011-12-13
[s]> **Dangertux said:**
> sudo apt-get install lamp-server^

I've seen the carat before, but I'm not sure what it might mean in this context.  Care to elaborate?[/s] (Note to self: start using CTE instead of spelling it out, just to be more obtuse.)

[http://ubuntuforums.org/showpost.php?p=11535846&postcount=15](http://ubuntuforums.org/showpost.php?p=11535846&postcount=15)

I can sympathize with OP a bit. I was recently battling against a bug in **e2fsck** which seemed inexplicable to someone unfamiliar with its correct use (me). The fix wasn't hard or anything, and I found a post in this very forum from the maintainer about it. I ended up working around the problem by using a newer version of the program.

So there you go. Community FTW!  :)

---

### Post by haqking on 2011-12-13
> **Telengard C64 said:**
> I've seen the carat before, but I'm not sure what it might mean in this context.  Care to elaborate? (Note to self: start using CTE instead of spelling it out, just to be more obtuse.)

I can sympathize with OP a bit. I was recently battling against a bug in **e2fsck** which seemed inexplicable to someone unfamiliar with its correct use (me). The fix wasn't hard or anything, and I found a post in this very forum from the maintainer about it. I ended up working around the problem by using a newer version of the program.

So there you go. Community FTW!  :)

he already mentioned it above, it is used for installing using tasksel

see here [https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

### Post by CharlesA on 2011-12-13
I thought the carat was a typo too. That's pretty cool, actually.

Thanks!

---

### Post by Primefalcon on 2011-12-13
Thx for the info dangertask and the link haqking, I never knew about task type installs..... damm and I and I thought was accomplished on the command line writing shell scripts and piping and such.... and I never heard of this simple thing....

<walks off to issue the command "apt-get moo">

---

### Post by Dangertux on 2011-12-13
Hmm.. Glad it was helpful. It's just one of those Debian things that comes along with Ubuntu Server for the ride, I guess alot of people probably don't use it, but it's definitely convenient.

---

### Post by CharlesA on 2011-12-13
> **Dangertux said:**
> Hmm.. Glad it was helpful. It's just one of those Debian things that comes along with Ubuntu Server for the ride, I guess alot of people probably don't use it, but it's definitely convenient.
I guess not. I usually just use tasksel directly.

Lol.

---

### Post by Docaltmed on 2011-12-13
> **CharlesA said:**
> It's a new word. I cannot find it in any dictionaries.

Kinda sorta.

tanquam = a person fit for college education

tanquaminity = the quality of being fit for a college education, i.e., smart.

The former word exists, if only in the hoarier cabinets of our vocabulary, and the latter word was created by me, released under CC. But if Apple even thinks about using it, I'm gonna sue them until their ears bleed.

---

### Post by stinkeye on 2011-12-13
> **Docaltmed said:**
> Kinda sorta.

tanquam = a person fit for college education

tanquaminity = the quality of being fit for a college education, i.e., smart.

The former word exists, if only in the hoarier cabinets of our vocabulary, and the latter word was created by me, released under CC. But if Apple even thinks about using it, I'm gonna sue them until their ears bleed.


Kinda sorta = make up your own words.

---

### Post by 3rdalbum on 2011-12-14
> **ffej2ffej said:**
> 
My latest problem is with LAMP.  A decade or more ago, I made a fully functioning LAMP and WAMP computer in ONE FREAKING DAY!!  It was simply a matter of downloading and installing the software and it worked!!  Now, after several days of work, I have a LA_P computer that works, but I'm starting to think I'm going to have uninstall and recompile Apache to make it recognize MySQL.  Keep in mind that MySQL is already installed, working and has at least 1 database that I created that works as expected.
So let me say this to people who author software:  TRY IT BEFORE YOU RELEASE IT!!  Try it on your mother-in-law who cannot even plug in her coffee machine.  Try it on your 8 year old son.  Try it on other people who are NOT in your circle of nerdy friends

Good luck getting an 8-year-old or computer-illiterate mother-in-law to even understand LAMP, much less install it.

This doesn't sound like a software development problem; it sounds more like a packaging issue. When you install PHP, Apache and MySQL on Ubuntu it should all Just Work due to the hard yards being done by the packaging team. If it doesn't work as expected, you should consider raising a bug report.

---

### Post by CharlesA on 2011-12-14
> **3rdalbum said:**
> Good luck getting an 8-year-old or computer-illiterate mother-in-law to even understand LAMP, much less install it.

Aye, I mean, you can install it via software center or apt-get, but it will work out of the box.

I've been running a LAMP server with very little configuration on a Lucid and CentOS box. I don't think it's a packaging issue tbh.

---

### Post by grahammechanical on 2011-12-14
It is my thinking that the paucity (I have a very large dictionary) of documentation was down to the developers being happy to develop but not happy to spend their time writing help documents. Surely the best people to write help documentation that actually helps people is those that use the program. Or, have we dropped the idea of Community from Open Source development?

Now, if we were talking about a commercial product we could pay a lot of money to get the right to complain about the poor quality of the documentation. And the answer that we would get back would be to pay for a training course to get certified for the product.

Paucity = smallness of number or amount; scarcity. It comes from Pauper, a person in straitened circumstances, one of small means; one who is regarded, or regards himself as poor.

It is also an old dictionary (50 years old) but younger than me.

Regards.

---

### Post by CharlesA on 2011-12-14
> **grahammechanical said:**
> It is my thinking that the paucity (I have a very large dictionary) of documentation was down to the developers being happy to develop but not happy to spend their time writing help documents. Surely the best people to write help documentation that actually helps people is those that use the program. Or, have we dropped the idea of Community from Open Source development?

Now, if we were talking about a commercial product we could pay a lot of money to get the right to complain about the poor quality of the documentation. And the answer that we would get back would be to pay for a training course to get certified for the product.

Paucity = smallness of number or amount; scarcity. It comes from Pauper, a person in straitened circumstances, one of small means; one who is regarded, or regards himself as poor.

It is also an old dictionary (50 years old) but younger than me.

Regards.

There is a metric ton of documentation about MySQL, Apache, and PHP. I even linked to some docs about the LAMP stack in an [earlier post]("http://ubuntuforums.org/showpost.php?p=11535590&postcount=12").

---

### Post by Telengard C64 on 2011-12-14
> **CharlesA said:**
> There is a metric ton of documentation about MySQL, Apache, and PHP.

[Have you measured that to be sure?](http://discovermagazine.com/2007/jun/how-much-does-the-internet-weigh)

I'd just say there's a *duck-ton*.

(oh look, there's an *f* key right next to the *d*)

:P

---

