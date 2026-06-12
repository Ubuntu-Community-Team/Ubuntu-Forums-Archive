---
title: "How to learn programming?"
date: 2012-09-01
forum: The Cafe
---

### Post by 3v3rgr33n on 2012-09-01
Hi

I'm currently doing my sophomore year. I've been programming in Java for over 3 semesters now but I don't feel like I can build anything very useful. Before Java, I did python for six months but I only know the basics.

I've been highly interested in developing an app that let's you view videos via the terminal. I've recently realised that cvlc does that but it's not particularly good.

I really want to get involved and code but I don't think any company can ever need me. What do you think is a great of way of learning? What should I be doing?

I've been looking at the stories of people like Mark Zukkerberg, apperently he made facebook during he's sophomore year. I cannot even build a single website (I don't even know what's the difference between a processor and a core).

What am i not doing right?

---

### Post by JDShu on 2012-09-01
Still relevant:

[http://norvig.com/21-days.html](http://norvig.com/21-days.html)

---

### Post by Roque Lmnz on 2012-09-01
I also recommend [this]("http://lifehacker.com/5939374/a-better-way-to-practice?tag=motivation") as a complementary text.

---

### Post by lykeion on 2012-09-01
It takes time, love and dedication. If you know Java, why don't you try Android development? At least that's what companies might be looking for right now...

---

### Post by effenberg0x0 on 2012-09-01
Everyone is different, so it's hard to say what will work for you. 

IMO, the only real way to learn something is to have a curiosity within you. When you have that you automatically want to know more about things, even if there's no real goal and it's not something that will make you money or a career. 

I can only learn things that are interesting to me. When something is interesting, I can't avoid Googling it, reading and participating in forums and discussions about it, buying books, investing time in it. I probably Google stuff about politics, biology, astronomy, economics, whatever a thousand times a day. Technology and computers are a huge part of that. Sometimes I'm in bed watching TV at 2AM, I see something in a movie, and I just have to get my smartphone and Google it to learn more - no matter the time, how tired I am, or if I have to wake up early. I got to a point in which I can't keep up with the amount of stuff I bookmarked to read later. 

When I'm researching, writing, talking about computers and technology stuff it doesn't feel like work or a task. It's fun and effortless. On the other hand, all the times I tried to learn things that I had no real interest, I failed miserably. I've learned I can't force myself to like and be interested in something. It's doesn't work like that.

What works for a lot of people is to join an online programming community (focused on the language you choose) and try to become active in this group: contribute to their forums and documentation, get to know the other members activities and projects, participate in the discussions, eventually join one or more projects so that you will naturally have to discuss problems with others and evaluate alternatives and solutions. 

About your own projects: I'd try to start small, create working modules that can be used later in larger projects. You're talking about Facebook and working with video. I would begin by writing a module to read and write settings from a config file in my $home directory. You will probably reuse that 100 times every year so it's not wasted time. Once that is working, move on to another basic task/module. Do that until you get to the core functionality/module. You will be learning all the basics and common tricks when working on this reusable modules, and you will be much more prepared and fluent in the programming language when you get to the core functionality. If you feel like this is boring and eventually drop it, it's because you had no real interest in it.

Again, everyone is different. That's what works for me.

Regards,
Effenberg

---

### Post by 3v3rgr33n on 2012-09-01
Thank you very much for the reply. I've been learning android.  I was just panicking, I just thought I was the only one who's had such feelings or thoughts.

I would like to work with some people. I feel like I wont know if I can fly not unless I jump from a cliff. I need to part of group who can make a difference in software development. I fear that I will fade away in a suit after next year.

---

### Post by V for Vincent on 2012-09-01
Not too long ago, I felt the same way. It's true that if you just settle for what comes your way on its own, progress is going to be slow. My advice is to think of a project that seems doable but which still requires you to learn new stuff. Start working on it and write daily or weekly progress reports on a blog somewhere. Stick with it. If you don't have time on a certain day, *make* time. (You could also see if there are existing open source projects that need help, of course.)

If you get stuck, ask for help. This is crucial. Some people are hesitant about it, but you can learn a tremendous amount just by asking questions.

Also, actively explore new material. If you need to do something for a project and you find a shortcut you don't understand, don't be tempted to take it. Learn what it does or find another solution. Subscribe to a weekly newsletter related to the language of your choice. Dig deeper. Instead of relying on techniques you already know now, learn about alternative approaches. A good way to do that is to make the exercises at [Programming Praxis]("http://www.programmingpraxis.com") and to compare your own solutions with those of others.

---

### Post by 3v3rgr33n on 2012-09-01
I'm really thankful for these forums. I've just started my blog now and my first project is to develop a top down shooter game in Java. I've never built a game in java. I found a game engine along with it's documentation.

Hopefully I'll have a fully functioning game by Monday.

Thanks a lot guys.

---

### Post by 3v3rgr33n on 2012-09-01
> **effenberg0x0 said:**
> 
 ...I would begin by writing a module to read and write settings from a config file in my $home directory. You will probably reuse that 100 times every year so it's not wasted time ...

I don't think I understand what you mean by this? Mind explaining

---

### Post by effenberg0x0 on 2012-09-01
> **3v3rgr33n said:**
> I don't think I understand what you mean by this? Mind explaining

I meant that just about any program you write will need to have settings stored somewhere. In windows that is sometimes done by reading / writing to the registry. In Linux you can do that in many different ways too, but you will generally end up using config files stored withing the user directory. 

So, just to get started with something easy (yet usable in the future), you can write a killer "read/write (load/save) settings" function - something that is fast, well-designed, uses as little resources as possible, reliable, extensible, maybe portable. Of course you could just adopt some API and have a working function in minutes but if you code that from scratch it would be a good exercise to get you involved and a step towards higher complexity tasks in your program. 

It's just an example anyway: you can think of other small program functionality/tasks in your program and dive into them to get you started in your project. I find easier to work in big projects when I can divide them into many small functionalities and code them separately, from the easiest to the hardest. 

When you create your own set of libs to do these small tasks, and optimize them as best as you can, it's not wasted time because you can easily reuse them in future projects. Sometimes when we just follow a book or tutorial we create stuff that isn't really reusable in the future.

Just my two cents :)

Regards,
Effenberg

---

### Post by johnb820 on 2012-09-01
In my personal experience, I have learned a lot more from working with other people's code than my own coding projects. I say this because you get a much more fundamental view of the overall picture of how you want to build your code and what techniques can work. Starting from a blank text editor is just about the most daunting thing for a programmer, and unless you know where you want to go with it in terms of design and organization, getting there will be too large of a challenge.

Imo this is also why so many people fail at learning to program from just fragments of code in a book.

---

### Post by vexorian on 2012-09-01
> **3v3rgr33n said:**
> Hi

I'm currently doing my sophomore year. I've been programming in Java for over 3 semesters now but I don't feel like I can build anything very useful. Before Java, I did python for six months but I only know the basics.

I've been highly interested in developing an app that let's you view videos via the terminal. I've recently realised that cvlc does that but it's not particularly good.

I really want to get involved and code but I don't think any company can ever need me. What do you think is a great of way of learning? What should I be doing?

I've been looking at the stories of people like Mark Zukkerberg, apperently he made facebook during he's sophomore year. I cannot even build a single website (I don't even know what's the difference between a processor and a core).

What am i not doing right?
You ask to learn programming when you are actually asking to learn application development.

It is different.

Let me try to explain... Programming is a lot like making a man-shaped sculpture out of a rock. Whilst app development is more like buying already-made sculptures of body parts and putting them together with glue. The problem becomes less about how well you can make the sculpture with your own hands, but more about how well you choose the body parts and the glue and that you make sure that you are building a sculpture of the right person.

So, learn about libraries, APIs and that stuff. Mike Zuckurberg didn't build facebook  from his bare hands. What is more important about what he did was to have the idea (to steal someone else's idea but with better direction) and he got some guys to build the core stuff like the db servers. And reusing some web libraries



If you don't know the difference between processor and core, go to wikipedia for a second and fix that. It is not a biggie.

---

### Post by 3v3rgr33n on 2012-09-01
> **effenberg0x0 said:**
> I meant that just about any program you write will need to have settings stored somewhere. In windows that is sometimes done by reading / writing to the registry. In Linux you can do that in many different ways too, but you will generally end up using config files stored withing the user directory...

What you are saying makes sense but it's starting to scare me. I've never written software that needed to store settings. Doesn't that apply for large scale software or am i misunderstanding you (or what I've been doing is bad practice)?

---

### Post by 3v3rgr33n on 2012-09-01
> **vexorian said:**
> You ask to learn programming when you are actually asking to learn application development.

It is different.
  [/QOUTE]
I didn't write the title, it was changed as mine was perhaps inappropriate.

[QUOTE=vexorian;12211223]
If you don't know the difference between processor and core, go to wikipedia for a second and fix that. It is not a biggie.
That line was meant purely as a figure of expression, I figured some slight exaggeration might help.

Mark Zukkerberg is being used in some sort of comparison test here. It is not about how did what he did. All I'm trying to say he managed to drop out of varsity, and still not starve. I love code, I breathe this stuff. Some people may not see that, I just fear that I may not be different from any other coder out there. People are making things which were never imagined by most, I just want to be part of that. 

In a cliche line: I wana be part of the group that changes the world.

---

### Post by V for Vincent on 2012-09-01
Some of this stuff sounds daunting, but if you love programming, you'll be fine. Just code. Learn and code. If you do that because you enjoy it, you'll set yourself apart without even trying too much.

Also, maybe one approach is better than another. Joining a project probably is more educational than building something on your own. But do what inspires you. Be patient about it, monitor your own achievements and byte off bits (heh.) you can chew. Wanting to make something revolutionary is an admirable goal, but give that some time. Get comfortable coding.

Incidentally, what is your blog's address?

---

### Post by 3v3rgr33n on 2012-09-01
Lol I'm fairly new in the world of blogging so don't judge harshly.

adeebnqo.blogspot.com

One of the reasons why I've been panicking is that I entered the Google Code Jam this year, I managed to through the Qualifying round but I never made through Round 1C, I never tried round1A and round1B. The times were ridiculous, I think they started at 3 in the morning here.

So you should understand where I'm coming from.

---

### Post by BrokenKingpin on 2012-09-01
If you know the basics pick a project and start working on it, learning what you need to along the way. If you are still learning the basics, just grab a book on whatever language you want to use and start going through it.

Also, find a programming forum where you can post some of your project code for review. Having feedback from people with more experience is very helpful early on to improve the way you design your applications.

---

### Post by forrestcupp on 2012-09-01
> **3v3rgr33n said:**
> What you are saying makes sense but it's starting to scare me. I've never written software that needed to store settings. Doesn't that apply for large scale software or am i misunderstanding you (or what I've been doing is bad practice)?

Even a simple top-down shooter might use a config file, even if it's only something as small as saving high scores, or maybe saved games or saving simple settings. Reading and writing simple data from a file is not hard at all. Just because you have never done it doesn't mean that it's going to be hard when you actually try. The only time that type of thing gets hard is if you need to compress or encrypt your files and you are writing your own algorithms to do that. That's usually not something you have to worry about with a simple config file.

But to be blunt, if you really just can't get the concept of programming, maybe you should look into changing your major so you don't spend the rest of your life miserable. If it's really your desire and interest, though, just keep working at it and persevere. Not everyone is a Mark Zuckerberg, but that doesn't mean you can't be successful.

---

### Post by JDShu on 2012-09-01
> **3v3rgr33n said:**
> 
One of the reasons why I've been panicking is that I entered the Google Code Jam this year, I managed to through the Qualifying round but I never made through Round 1C, I never tried round1A and round1B. The times were ridiculous, I think they started at 3 in the morning here.


:) those things have a way of making you feel really stupid. Don't worry, the people who compete there are on the upper echelons of programming skill. Remember that there are always people who are way better than you are and people who are worse. What's important is that you're improving yourself.

Also, if you search for "how to become a better programmer" you'll find a lot of good suggestions about how to do it.

---

### Post by JDShu on 2012-09-01
> **forrestcupp said:**
> 
But to be blunt, if you really just can't get the concept of programming, maybe you should look into changing your major so you don't spend the rest of your life miserable. If it's really your desire and interest, though, just keep working at it and persevere. Not everyone is a Mark Zuckerberg, but that doesn't mean you can't be successful.

Mark Zuckerberg isn't even known for being an amazing programmer.

---

### Post by 3v3rgr33n on 2012-09-01
> **forrestcupp said:**
> Even a simple top-down shooter might use a config file, even if it's only something as small as saving high scores, or maybe saved games or saving simple settings. Reading and writing simple data from a file is not hard at all. Just because you have never done it doesn't mean that it's going to be hard when you actually try. The only time that type of thing gets hard is if you need to compress or encrypt your files and you are writing your own algorithms to do that. That's usually not something you have to worry about with a simple config file.

Quit programming? That's like saying I should say I should quick Breathing. Oh Now I understand the whole point of the config files and it's actually a great idea. Thank you very much to everyone who gave input.

Some people just read too much to the Mark Zukkerberg thing, Nonetheless keep on doing what you are doing.THANX):P
<I'm closing this thread>

---

### Post by trent.josephsen on 2012-09-02
> **3v3rgr33n said:**
> I've been looking at the stories of people like Mark Zukkerberg, apperently he made facebook during he's sophomore year. I cannot even build a single website (I don't even know what's the difference between a processor and a core).

They say that Julius Caesar considered himself a failure compared to Alexander.

Although, it didn't take an expert to build facebook. You could learn enough PHP and stuff to build your own crappy clone in a month or two. Mark Zuckerberg wasn't a genius or anything, he just happened to come upon the right idea at the right time. It could have happened to anyone, but it didn't. That's the way it happens.

(There's really no difference between processors and cores. Cores are what you call multiple processors on a single physical chip. "Processor" can also be used to refer to the physical chip, though, so there's some semantic confusion.)

---

### Post by Mikeb85 on 2012-09-02
If you want to simply build useful programs on your own, maybe revisit Python or another interpreted language like Ruby...  

Java is notorious for being slightly difficult and not necessarily very productive, however it is used in industry alot because of it's benefits.  

If you simply want to be able to build things quickly, Ruby, Python, PHP, etc.., are very productive and easy, if you want to work for a large software company, just keep at it, I'm sure things will come together eventually.

---

### Post by forrestcupp on 2012-09-03
> **JDShu said:**
> Mark Zuckerberg isn't even known for being an amazing programmer.

I brought that up because the OP was comparing himself to what Zuck was doing when he was the same age. Not everyone is going to end up as successful as Zuckerberg.

---

