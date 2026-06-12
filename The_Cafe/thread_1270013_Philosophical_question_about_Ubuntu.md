---
title: "Philosophical question about Ubuntu"
date: 2009-09-19
forum: The Cafe
---

### Post by mjp29 on 2009-09-19
Personally, I have a lot of experience using computers as a hobby (goes back to the one Apple II in our elementary school, having a Timex Sinclair as first computer at home which was quickly replaced with a Commodore Vic-20).  I could write many pages about my childhood computer hobby and reading computer magazines and such but I won't bore you.

But somewhere along the line I chose not to be indoctrinated and use a Microsoft Windows system. I have used a Mac (a rebel) since early releases of the Apple and even now I use an old G4 cube running an older version of os X.

My older Uncle, on the other hand, I have been unable to convince not to use a Windows operating system.  My many conversations with him and emails to him telling him how the Mac o.s. is something he must try ... never stuck with him.  He just kept buying and still keeps buying laptop Windows laptop systems even in his retirement.

The Irony of all this is that a few years back my Uncle (who actually reads a lot about computers on the net like I do) started talking about something called Ubuntu and asked me if I would help him install it on his old desktop to try it out.  I looked it up on the net and it was Unix based too like my Mac and decided sure let's try it (anything to get him to try something besides Microsoft Windows).

The Irony is that I helped him install it and we both used it and we both loved it better than what we were using - the Irony is obvious.

And now I've just installed Ubuntu on a Pentium 4 box (that was given to me)tonight and showed it to an old female friend that has never seen it and really likes it a lot (she has used Windows at work for years but really really likes Ubuntu).

The philosphical question that comes to mind is this.  Is Ubuntu for linux people that know code (know a lot about how to program with command lines and such) or is it a bridge for we users that don't know code but really like how it looks and how it feels (to use).  Those that know the code love it and there seems to be (to me) an increasing amount of users that can't decipher or understand a line of lynix code that also like it.  

The philosophical question is this:  Is Ubuntu still more for lynix expert programmer users or is Ubuntu now more for users like me (me, my uncle, my friend) who know nothing about programming code.

The only reason I bring this topic to the community is because it seems to me that questions I ask for help are answered about 50% by users that know how to program code and answer with code commands on how to fix a problem and the other 50% of users answer with where we dummies should click and get things to work for us dummies - lol.

Or perhaps Ubuntu really does means "I am what I am because of who we all are"

Perhaps we all meet together somewhere - ?

---

### Post by earthpigg on 2009-09-19
there is a pretty grey line between "knowing how to program code" and "not knowing how to program code".

for example, i dont know a damn thing about C or java or perl...

...but i can write simple shell scripts.

and now, so can you:

```
#!/bin/bash
echo "each line is a command."
echo "i can string commands back to back."
echo "rawr is dinosaur for i love you"
```

save that text file as rawricanprogram.sh. to run it:

```
sh rawricanprogram.sh
```

you are now capable of *programming code*, as you put it.

and if someone wanted to know how to write a program that would display "Hello World!" when ran, you would now know how.

---

### Post by fluxlizard on 2009-09-19
Hey- my first computer was a vic20! (still have it with a modern made 32k ram expander and a cable that hooks it up to an old pentium 1 running dos with a nifty little program that makes the pentium act as a hard drive for the vic)

 Anyway- I don't code, but I've used linux since around 2001 and ubuntu for a few years now.

 The commands people use at the command line to solve problems are just commands- remember this one from commodore days?- load"program name",8

The commands used to solve problems are more like that than actual coding. They just tell the computer to do one thing- it's like a dos command.

Easy to learn or to copy and paste commands from the forum into a terminal window.

But a "normal" user of most popular linux distros these days like ubuntu can probably get away with never using the terminal. It's faster for some things though if they want to learn the commands.

---

### Post by squenson on 2009-09-19
Interesting question...

For me, Ubuntu is for both populations. A computer is such a marvelous device that absolute beginners and experts can get many things done out of it. Of course, you need to adapt and accept that tasks can be done differently. You have to move out of your 'comfort zone' and explore unknown territories.

But if Ubuntu is great in itself, it is just an Operating System and it should make itself as invisible as possible. What is important to develop the 'beginners' population are the software, their intuitiveness and openess.

What I like personnally the most with the development of Ubuntu and other OSes is that it brings more competition and when there is more competition, the consumer gets better products and it will ultimately benefit the Windows, Mac and Ubuntu users.

---

### Post by earthpigg on 2009-09-19
also, tell me which is easier to explain to a newbie asking for help on the forums from the point of view of a forum volunteer (ie: anyone with more than roughly 200 'beans'):

option 1:
```
sudo apt-get install ubuntu-restricted-extras
```

option 2:
click applications -> click add/remove programs -> click on the search box -> type in 'ubuntu restricted extras' -> click the check box -> select apply.


people concerned with efficiency quickly realize that the time investment in learning to do #1 will pay itself back hundreds of times over when compared to using option #2 for the rest of your life.


and, option 2 will [very likely change in future releases of ubuntu]("https://wiki.ubuntu.com/SoftwareStore"). meaning the knowledge can become obsolete.

would anyone care to delve back into the history books and tell me how long ago it was that "apt-get install ($packagename)" did not work?

someone could have learned that command **a decade ago**, and it still works *exactly the same* on Debian and Debian-based systems such as Ubuntu.

i predict that in ubuntu 15.10, apt-get install ($packagename) will still work peachy keen.... i do not think add/remove will look the same as it does today. if it is even still maintained at all.

to be even more extreme, consider some of these commands that have probably been around for 2 or 3 decades harking back to the days of AT&T Unix (development for that project began in 1969) waaaaaaay before some Finn named Linus ever even thought about running Unix on his Intel 386 system in the early 90s:

[dd]("http://en.wikipedia.org/wiki/Dd_%28Unix%29")
[ls]("http://en.wikipedia.org/wiki/Ls")
[cp]("http://en.wikipedia.org/wiki/Cp_%28Unix%29")
[uname]("http://en.wikipedia.org/wiki/Uname")

learning how to use dd will serve me for 50 years to come, if i wish.

learning how to point and click around in John's Proprietary Disk Imaging Program or Ubuntu's Graphical Tool to Accomplish _________? not a chance in hell.

---

### Post by stderr on 2009-09-19
There's no easy answer to that. I have friends and colleagues on both (extreme) sides of the spectrum you paint who all use Ubuntu very happily. My personal viewpoint is the more of a Linux (btw, it's pronounced l-in-ucks ;)) geek one is, the more likely one would be to run a (in my mind) more serious distro, such as Debian/Gentoo/Slack etc. Having said that, more by coincidence than anything else, I actually moved from Debian as my main distro to Ubuntu, some years back. 

At the end of the day, the particular distro doesn't make much difference. Well, it does, but not in so much as a Debian/Ubuntu distinction. A Slackware/Ubuntu distinction would be more noticeable ;) Ultimately, we're talking about a GUI of sorts, sitting on top of standard Linux shells and GNU tools. The precise default layout of the GUI and default applications don't bother me too much; I change much of it anyway, and disable most of the Windoze-like additions. 

To a recent Windoze convert, Ubuntu and the like are far more sensible inital choices for a distro, but conversely Linux geeks can take any distro, including Ubuntu, pull up a terminal, and weave gold :)

---

### Post by earthpigg on 2009-09-19
> **stderr said:**
> 
...conversely Linux geeks can take any distro, including Ubuntu, pull up a terminal, and weave gold :)

i love how you put that.

---

### Post by arinlares on 2009-09-19
Linux is moving into an era now where you don't have to be a big computer geek to use it.  I can only write a few lines of useful Python, but have settled into Ubuntu just fine.  I'm not a convert, I like Linux and Windows for different reasons.  I find the command line a little easier to use than the graphical methods for installing packages.  You don't even need to know a programming language to compile a program, I'm living evidence of that.

For all of the stuff I hear about "Linux and Windows are not the same," they are startlingly similar, providing you're in a graphical environment.  I came into Ubuntu the first time ever, and was like "This is here, this is there.  Okay, 'sudo apt-get install packagename...  SWEET!  Like a command line Windows installer!"  It's just that easy and simple, provided you are willing to think, and maybe ask for help.  Best of all, with maybe an hour of learning, I could probably jump into something like SUSE or Fedora with no issues, and vice versa, with my same skill level, and still use it.

I think stderr has the best point, by the way, with his last comment.

---

### Post by stderr on 2009-09-19
> **earthpigg said:**
> i love how you put that.

It does have a certain ring to it, eh :)

> **earthpigg said:**
> 
for example, i dont know a damn thing about C or java or perl...


```

ace@ace1:~/scripts$ cat > test.pl
#!/bin/perl
print "Hello Bash\n"                         
^C
ace@ace1:~/scripts$ perl test.pl
Hello Bash

```

You do now.

---

### Post by jocheem67 on 2009-09-19
It all depends on the complexity of the commands. Where using a GUI is  imo also considered as "commanding"

I prefer avidemux over mencoder, because it's quicker for me. There's too much chance of typo's in creating an avi or whatever using the CLI only ( try using say like 3/4/5 filters ).
Avidemux does the same, graphically, without any chance of not knowing what you want from it.
The CLI does.

---

### Post by gnudoc on 2009-09-19
I have a friend who routinely confuses the terms "processor" and "peripheral".

I have another friend who's been a "power user" of windows for the last 10 years or so, who is happy enough fiddling with the registry but is glad he doesn't often have to type at the command line.

I've been using various distros of linux for over ten years, and often write shell/python/perl scripts, and very occasionally dabble with c.

I know there are *loads* of people on these fora far more experienced than me.

The great thing about ubuntu is that, because of its solid unix, linux, gnu, debian, X.... underpinnings, and its excellent set of user tools and usability, all of these people can and do happily use it every day.

gnudoc

---

### Post by Tibuda on 2009-09-19
Ubuntu is presented as "Linux for human beings". I think this answer your question.

> **earthpigg said:**
> also, tell me which is easier to explain to a newbie asking for help on the forums from the point of view of a forum volunteer (ie: anyone with more than roughly 200 'beans'):

option 1:
```
sudo apt-get install ubuntu-restricted-extras
```

option 2:
click applications -> click add/remove programs -> click on the search box -> type in 'ubuntu restricted extras' -> click the check box -> select apply.


option 3:
[click here]("apt:ubuntu-restricted-extras")

easier for both the volunteer and the beginner.

---

### Post by davo11 on 2009-09-19
was ubuntu not created for that exact purpose? so that people who knew little or nothing about coding could use linux? thats the point of ubuntu to me

---

### Post by Murrquan on 2009-09-19
> **davo11 said:**
> was ubuntu not created for that exact purpose? so that people who knew little or nothing about coding could use linux? thats the point of ubuntu to me

As near as I can tell, if you *have* to do something complicated to get something to run in Ubuntu, the community treats it as a bug. Until it's solved, though, they'll tell you how to do it.

---

### Post by praveesh on 2009-09-19
It is possible  to do EVERYTHING in UBUNTU without using a terminal . A user can optionally study the terminal to do SOME tasks more efficiently and fast . For some highly advanced tasks(too advanced so that a user won't do that in windows or mac) the terminal is needed. The reason why most of the answers to the queries in this forum are terminal commands is that the people here are lazy to give instructions for the gui(graphical user interface) which consume more time . More over, most of the people think that just  copying and pasting in the terminal is very easy fast. The problem is that a new user will think the linux is only for tech people who know terminal commands. When I switched from OpenSUSE to Ubuntu, I have thought that the Ubuntu needs the knowledge in terminal ( I have not visited the OpenSUSE forum) .  In my experience, for everything, there is a gui way and a terminal way in Ubuntu. In kUbuntu, a user might need to use terminal , because the graphical package management tool really sucks in kUbuntu(it's just my opinion). More over, kUbuntu lacks some work that the Ubuntu team have done on Ubuntu to make it a wonderful experience in gui.

---

### Post by stwschool on 2009-09-19
> **praveesh said:**
> It is possible  to do EVERYTHING in UBUNTU without using a terminal . A user can optionally study the terminal to do SOME tasks more efficiently and fast . For some highly advanced tasks(too advanced so that a user won't do that in windows or mac) the terminal is needed. The reason why most of the answers to the queries in this forum are terminal commands is that the people here are lazy to give instructions for the gui(graphical user interface) which consume more time . More over, most of the people think that just  copying and pasting in the terminal is very easy fast. The problem is that a new user will think the linux is only for tech people who know terminal commands. When I switched from OpenSUSE to Ubuntu, I have thought that the Ubuntu needs the knowledge in terminal ( I have not visited the OpenSUSE forum) .  In my experience, for everything, there is a gui way and a terminal way in Ubuntu. In kUbuntu, a user might need to use terminal , because the graphical package management tool really sucks in kUbuntu(it's just my opinion). More over, kUbuntu lacks some work that the Ubuntu team have done on Ubuntu to make it a wonderful experience in gui.
Wrong. Terminal commands are precise. Give GUI commands and people can misinterpret, things can be in the wrong place (customisation). Give terminal commands and they copy+paste. No interpretation needed. No errors. Problem fixed quickly and without fuss.

---

### Post by praveesh on 2009-09-19
> **stwschool said:**
> Wrong. Terminal commands are precise. Give GUI commands and people can misinterpret, things can be in the wrong place (customisation). Give terminal commands and they copy+paste. No interpretation needed. No errors. Problem fixed quickly and without fuss.

I agree about the precision . But the people don't understand what  the command x does and doesn't know the stuff after the - are options and doesn't know what these options do . Without knowing these , it would be difficult to remember the command for future use. If a gui way is told, it would be very easy for a new user to remember ,  because, if s/he just look around in the app, s/he will see a button s/he has pressed earlier and will recall everything easily .

---

### Post by MasterNetra on 2009-09-19
> **mjp29 said:**
> 
...
The philosophical question is this:  Is Ubuntu still more for lynix expert programmer users or is Ubuntu now more for users like me (me, my uncle, my friend) who know nothing about programming code.

...

Its for both. Ubuntu is great for coders and non-coders a like and seems to cater to both.

---

### Post by MikeTheC on 2009-09-19
I consider myself a very tech savvy person with tons of experiences in the tech industry stretching back over 23 years.

I prefer Ubuntu because, frankly, of all the different distros I've tried over the years, well...

"It just works!"

---

### Post by keiichidono on 2009-09-19
> **MikeTheC said:**
> "It just works!"TM

Fixed.

---

### Post by tgalati4 on 2009-09-19
I give terminal commands because it is faster to respond than to look up what the mouse-click sequence is to perform a given action.

Besides, the GUI's change with each release and are different between XFCE, KDE, and Gnome.  Most new users don't specify what they are running in the first place.

The terminal commands work with any release and with any desktop environment.

So yes it does scare new users. It's like speaking a foreign language to them.  But when their sound card doesn't work, they tend to pay attention, and that's a teachable moment.

Many manufacturer support websites have a worthless popup that says:  "Was this answer helpful to you?".  Perhaps these forums should have a similar worthless popup.  If the answer is NO 50% of the time, then that would be indicative.

---

