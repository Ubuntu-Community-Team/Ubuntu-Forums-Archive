---
title: "What do you think about an &quot;Is Ubuntu for You?&quot; quiz?"
date: 2007-04-25
forum: The Cafe
---

### Post by aysiu on 2007-04-25
I love the [Linux Distribution Chooser Quiz](http://www.zegeniestudios.net/ldc/). It's quite handy for a lot of newcomers wondering, "Which distro do I pick?" While the distro the quiz recommends may not be the one a new user ultimately sticks with, it's usually a good starting place.

Well, we do get a lot of people in here asking "Is Ubuntu for Me?" I wrote up a narrative response:
[Is Ubuntu for You?](http://ubuntuforums.org/showthread.php?t=63315)

But wouldn't it be neat to have an online quiz people could take, too?

Basically, it'd ask a lot of questions like what you primarily use your computer for, what Windows and Mac applications you currently use, what the specs of your computer are (processor, RAM, etc.), what model wireless card or video card you have (if applicable... and if known by the user). It can even ask how much time the person plans to spend learning a new operating system. The question possibilities are limitless.

In the end, they can get some kind of score and a recommendation (Ubuntu, Kubuntu, Xubuntu, stay with Windows, use Damn Small Linux, etc.).

What do people think?

---

### Post by ronocdh on 2007-04-25
This is a great idea. I have met several new but moderately competent Linux users (Ubuntu only) who were dumbfounded at the difference between Ubuntu and Kubuntu. "If it's just a desk environment, why change the name of the distro?" I think the quiz should try very hard to determine not only whether Ubuntu suits the user, but also *which* version is right for them.

---

### Post by igknighted on 2007-04-25
I think its an awesome idea, and I wish I could help... but at the moment I am stretched so thin I don't have the time.

---

### Post by lepz on 2007-04-25
What can we win? ;)

---

### Post by aysiu on 2007-04-25
Well I'm thinking there are several categories of questions the quiz could have:

1. Attitude / time investment (Ready to try something new? Do you have time to troubleshoot?)
2. Hardware compatibility (Intel or Broadcomm? ATI? Nvidia?)
3. Hardware capability (128 MB of RAM or 2 GB of RAM?)
4. Software needs (AutoCAD... or just Thunderbird?)
5. Previous experience (Windows? Mac? *nix?)

---

### Post by der_joachim on 2007-04-26
> **aysiu said:**
> Well I'm thinking there are several categories of questions the quiz could have:

1. Attitude / time investment (Ready to try something new? Do you have time to troubleshoot?)
2. Hardware compatibility (Intel or Broadcomm? ATI? Nvidia?)
3. Hardware capability (128 MB of RAM or 2 GB of RAM?)
4. Software needs (AutoCAD... or just Thunderbird?)
5. Previous experience (Windows? Mac? *nix?)

Although I like the idea, I think that the questions asked above are not really *buntu specific. These questions, put in a different context, could be equally applicable to a 'which Windows version' quiz (2000 vs Vista). No offense. ;)

The question is pretty straightforward, but the intended audience can make quite a difference. Having read some of your articles, I gather that the intetded audience is primarily the prospective beginner, but I am making an assumption now.Of course, the questions can be altered, dependent of earlier quostions. If a user has been using linux for a few years already (question #5 above), it will be quite safe to assume that question #1 will be a bit redundant.

Of course, some of the questions should be *buntu-specific ('Do you think that all software on your computer should be free?' or 'Do you like easily configurable Vista-like effects on your desktop?').

---

### Post by aysiu on 2007-04-26
Yeah, the examples I gave are quite generic, but we can also put in some Ubuntu-specific stuff.

If people want proprietary stuff out of the box and don't care about free software, then Mepis might be a better choice, for example.

---

### Post by Bloch on 2007-04-26
I had the same idea some time ago - I thought of adapting a basic multi-choice IT quiz to test if people had enough knowledge to move to ubuntu.
Points would be added at the end (there could be an automatic version and a downloadable pdf) to give score ranges from "You are already at geek-level, I don't believe you've never tried linux" to "only move if you have a more computer-knowledgeable person always a call away."

Questions would be fun and pretty basic:

A photograph straight from a digital camera would be approximately:
A) 1GB    B)1000GB     C) 1MB     D) 1KB 

The boss's computer is running slow. You tell him he needs more memory. He shouts that he threw out all the junk on the hard drive only yesterday. Do you
A)  Calmly explain what you mean, open his control panel and see what type and how much he needs
B)  Say "I'm only saying what I read in a magazine this morning"
C)  Say: "Well my friend tried that and it worked for him, so it might work for you too"
D)  Say: "How many sugars in your coffee?"

I think it's fair to say that potential ubuntu users/self-administrators  should have basic IT knowledge, the right attitude to be able to seek help in the forums. Aysiu's "Is ubuntu for you" is spot on in warning/encouraging people, and it would be nice to have a quiz.

But I don't think it should take itself too seriously or try to be too comprehensive. It should serve to give a little confidence boost to those who have a basic knowledge but have heard you have to be a geek, and also as a warning to those who have been falsly informed it's just like windows except there are no viruses. 
People who use computers for work purposes will be making informed decisions at a much higher level, to keep the quiz focussed we should assume a general reader.  

I won't have time to work on this until after May 1 - let me know if you would like me to brainstorm a few multi-choice questions.

---

### Post by aysiu on 2007-04-26
I started up a Wiki page for this.

If you have more questions or can help out in any way, please feel free to edit the page (or post in this thread):
[https://wiki.ubuntu.com/IsUbuntuForYouQuiz](https://wiki.ubuntu.com/IsUbuntuForYouQuiz)

---

### Post by ubuntu27 on 2007-04-26
Great idea. :guitar:

---

### Post by jeffathehutt on 2007-04-27
Take a look at [this.]("http://jeffmizzell.com/ubuntuquiz")

Right now, it doesn't have much of an interface, but I think it works for the most part.

The program uses a seperate question file, where you can easily add new questions or edit existing ones.  Each question can have any number of responses, from 2 to however many you need.  Each response has a point value, starting with 0 for the most inexperienced answer, and going up to however many responses are possible.  For instance, if there are 3 possible responses, the point values would be 0, 1, and 2.

After the user has submitted the answers, they will be given a percent score of how well they did.  If the user selected all the most advanced answers in each question, they will get 100%.  If they answer the least experienced response for each question, they will get 0%.

Now comes the fun part: converting the score into something a little more usable.  Obviously if they get 100%, then it is safe to assume Ubuntu is for them.  I'm not sure what each score range should mean, but that is easy enough to change later.  The good thing about using percents instead of a number is that the quiz can adapt and grow as needed, but the percents will stay the same.  That way, we wouldn't have to update the ranges every time a new question was added, as the percent will always be 0%-100%.

Also, the quiz is coded to be multilingual, it just needs a new language file for each language supported.

Let me know if this is on the right track of what you were thinking. :)

---

### Post by aysiu on 2007-04-27
That's awesome, jeffathehutt!

That's exactly what I'm thinking, and I like the idea of percentages better than raw points.

---

### Post by earobinson on 2007-04-27
Its going to be way to hard to caputre all the possibilites in a quiz

---

### Post by aysiu on 2007-04-27
> **earobinson said:**
> Its going to be way to hard to caputre all the possibilites in a quiz
Yeah, but people could still get a general idea, right?

---

### Post by earobinson on 2007-04-27
> **aysiu said:**
> Yeah, but people could still get a general idea, right?
I would just worrie that we would be discourging a lot of people. When people ask me the question I usualy tell them to pop in a live cd and find out, after warning that live cds are slower of cource

---

### Post by aysiu on 2007-04-27
> **earobinson said:**
> I would just worrie that we would be discourging a lot of people. When people ask me the question I usualy tell them to pop in a live cd and find out, after warning that live cds are slower of cource
I do the same, too, but another resource may fill a certain niche.

Also, the results don't have to be like "Loser! Go back to Windows!"

It could have certain recommendations like:

* It doesn't sound as if moving to Ubuntu would be the best move for you right now, but when you're feeling the crunch of upgrading to Vista, you may want to come back and give Ubuntu a try then.

* Ubuntu may be a bit too intense for your current hardware specs, but you can still give Linux a shot. Try Damn Small Linux or Puppy Linux.

* Linux is in your future, but it's not going to be Ubuntu. Mepis will be a better choice for you to start with, and it's based on Ubuntu.

---

### Post by jeffathehutt on 2007-04-27
The only problem with my current setup is that it doesn't distinguish between different types of questions.  However, this can be easily resolved by having more than one section to the quiz.  For example, it would start with "General Linux questions" that would determine if the user could use linux in general.  Then, "Hardware requirements" would be a seperate section to determine which distribution would work best on their hardware.

At least from the coding point of view, that isn't hard to do.  I would just have a seperate file that does each section, and link from one to the next while the user takes the quiz.  Once the user is done with one section, they will immediately get results about that section, and then they can choose to go to the next section if they are satisfied with the results.

Edit:  The hardest part in that setup is converting a percent to useful information.  If there was a section about different distributions, I'm not sure how to make a percent mean anything.  How does 10% mean any particular distribution?  That's just an example, but I will have to think of a way to do that.  It might be as easy as carefully wording the questions and answers.

---

### Post by aysiu on 2007-04-27
I appreciate that.

Now I guess the tough part would be figuring out what questions to ask and paring it down to something digestible (instead of 200 questions).

---

### Post by Iceni on 2007-04-27
We should probably have a question about gaming. hardcore gamers don't want linux period, so that would rule out those right away. For example:

Do you play games on your computer? 
1. Yes, I play every day or almost every day.
2. I like to play a game now and then, but nothing serious.
3. No.

Answer 1 would lead to something like "With the current lack of support for windows-based games in Ubuntu and linux in general, we feel that linux is not for you. Still, we encourage you to test a live cd, if only to show you the great, free alternative os that is Ubuntu"

Answer 2 would propose a dual-boot setup, like many of us run for that odd hour of gaming fun now and then, also take other questions into consideration.

Answer 3 could either dismiss the value of the question or better, take into consideration that this is a prime candidate, because games are a big reason today's youth are bound to windows.

---

### Post by aysiu on 2007-04-27
I agree, but we should probably make a distinction in the answers between games (Tetris) and gaming (World of Warcraft).

---

### Post by Oki on 2007-04-27
I think this is a very good idea:) 

Linux doesn&#8217;t get much advertisment (compared to ms crap-ware). This idea will take advantage of the internet and give it more free attention, and  I believe it that also people that normaly dont care about the word "Linux" would listen. The reason for this is that most people think it&#8217;s funny to answer surveys(if they are good made). There are lots of sites that has &#8220;surveys&#8221; about everything &#8211; and many think that is funny. I was thinking about this for a week ago when I was answering the KDE icon survey ([http://85.10.193.9/UCCASS/index.php)](http://85.10.193.9/UCCASS/index.php)). You could &#8220;use&#8221; sites like dig to make it known. 

&#8220;*what model wireless card or video card you*&#8221;: if it doesn&#8217;t work you could tell them about one that dos work, and with a low price. I mean, there are very cheap USB wireless cards in the store now, and perhaps many don&#8217;t know about them(much more cheaper to buy a usb wireless and get a free OS then buying slow vista). 

Perhaps you could make a &#8220;find the Linux application that can replace my ms programs for me&#8221;, perhaps they could click in a list(like ms office then openoffice would be suggested), more or less like these sites but just automaticly:
[http://www.in.redhat.com/AppComparisonList.php3](http://www.in.redhat.com/AppComparisonList.php3)
[http://linuxeq.com/](http://linuxeq.com/)
As you said; &#8220;*The question possibilities are limitless.*&#8221;	

Even if you cant recommend them to try Linux, they would have learned about the it. 

And if it is not vice to recommend Linux you could advice them to try open and free software that can work on both platforms, like Firefox, thunderbird, openoffice and so on &#8211; witch will make it easyer for them if they later tryes to shift.

If the person is a hardcore gamer you could advice him to dual boot, keep all his important thing with Linux and games in windows(safe from virus, spyware and so on). Gamers like to hear that they could have a &#8220;clean and fast&#8221; xp &#8211; witch is good for games, and a at the same time have a nice Linux desktop with free applications.
But let them know that games can be made for Linux(not all know that), and that there are some; 
[http://www.enemyterritory.com/](http://www.enemyterritory.com/)
[http://savage2.s2games.com/](http://savage2.s2games.com/)
[http://www.unrealtournament2007.com/](http://www.unrealtournament2007.com/)
[http://doc.gwos.org/index.php/Non_Native_Game](http://doc.gwos.org/index.php/Non_Native_Game)
[http://doc.gwos.org/index.php/Native_Games](http://doc.gwos.org/index.php/Native_Games)
and so on&#8230;

Sorry my English...

---

### Post by jeffathehutt on 2007-04-27
[Check the updated version.]("http://jeffmizzell.com/ubuntuquiz")

I split it into sections, so now each section can have its own score.  Also, on the Main section, I went ahead and added some result text just to see how it will work.  If you score < 20% on the main section, it will say something different than if you score higher.

Eventually, once we work out the questions, it will be pretty easy to add more sections as needed.

---

### Post by jeffathehutt on 2007-04-27
You can now check the response to a particular question.  For example, you might ask a question about hardware:

What video card do you have?
- nVidia
- ati
- Intel

In a situation like that, percents don't really mean anything.  Now you can respond according to the user's response:
Choice 1:  Your card is supported
Choice 2:  You might have to do some tweaking to get it to work
Choice 3:  You need to install the driver for your card
etc.

---

### Post by Mazza558 on 2007-04-28
Just found this:

[http://commons.wikimedia.org/wiki/Crystal_Clear]("http://commons.wikimedia.org/wiki/Crystal_Clear")

Loads of free to use icons licenced under the Creative Commons Licence. Enjoy!

Alternatively, for tango icons:

[http://commons.wikimedia.org/wiki/Category:Tango_project]("http://commons.wikimedia.org/wiki/Category:Tango_project")

---

### Post by der_joachim on 2007-04-28
> **aysiu said:**
> I appreciate that.

Now I guess the tough part would be figuring out what questions to ask and paring it down to something digestible (instead of 200 questions).

2 suggestions: 
1) Try working with a tree-like question structure and allow it to branch according to previous answers. Modelling this decision tree should be easy. (I know one modelling method, but It's not very widespread).
2) About older computers: do not forget a recommendation for Xubuntu. ;)

---

### Post by maniacmusician on 2007-04-28
> **jeffathehutt said:**
> [Check the updated version.]("http://jeffmizzell.com/ubuntuquiz")

I split it into sections, so now each section can have its own score.  Also, on the Main section, I went ahead and added some result text just to see how it will work.  If you score < 20% on the main section, it will say something different than if you score higher.

Eventually, once we work out the questions, it will be pretty easy to add more sections as needed.
Free games:

Sauerbraten  [http://sauerbraten.org](http://sauerbraten.org)
Alien Arena    [http://red.planetarena.org/#](http://red.planetarena.org/#)

---

