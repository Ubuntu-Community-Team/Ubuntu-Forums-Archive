---
title: "This is why I always have given up on Linux!!!"
date: 2010-08-28
forum: Testimonials &amp; Experiences
---

### Post by markjs on 2010-08-28
The simplest (or should be) operation requires arcane commands and files I am supposed to know the name and location of and I'm also supposed to be able to understand the terribly incomplete instructions!

It all started when my panel just started changing itself for no apparent reason.  The shutdown button got crowded off the end to where I could not access it.  Then, I don't know if it was related or not, all of a sudden my screen was so big I could not see any of the panels.  After much RAGE I figured out how to get the screen back with the nVidia-xconfig tool.

So then I am just trying to get the damn panel back to some default state but I accidentally deleted it.  So I try to look it up and I get supposed instructions:

> To
restore the default preference values for a user, run the following command:

gconftool-2 --direct \
  --config-source user-configuration-source \
  --recursive-unset

Replace user-configuration-source with the
configuration source in the .gconf directory in the home
directory of the user. 

This command resets the values of all preference keys, in all subdirectories,
from the user setting to the setting in the default configuration source.

What the hell does this mean:  

[B][I]Replace user-configuration-source with the
configuration source in the .gconf directory in the home
directory of the user. [/I][/B] ?!?

I go to /home/me/.gconf and inside that is just two folders nothing else, no files, nothing?!?  

What are the back slashes?  Aren't there supposed to be no back slashes?

Worse still why is this stuff changing by itself through no action of my own?  Why in the hell is there not some simple GUI tool to reset defaults?  I am ready to re-install the whole damn OS just to get back to where it started, but then what would I have learned?    

I am bound and determined to learn this stuff so I can try and get friends interested in Ubuntu, but to a virtual Windoze expert so much of it is just so damned counter-intuitive!  Why does it have to assume you know things?  That has always been the problem for me in all of this is it says things like that and was written obviously by someone who expects you to have some knowledge to start with. It is EXTREMELY poorly explained for novice level users!  It has gotten a lot better over the years for sure, but then I run into something like this and sometimes it is just maddening!

Sorry for the frustration but for some reason this was NOT the night for it!  At this point my nerves are so fried I just can't even read more tonight, just walk away and hope someone can make this easy to understand for me.

"A TV may insult your intelligence, but nothing rubs it in like a computer" -(not sure who?)

Thanks in advance....

---

### Post by hawthornso23 on 2010-08-28
This isn't a linux only problem. I remember back in my windows days having exactly the same problem with games crashing out and leaving me in an unusable screen resolution unable to reach any of the useful buttons in the GUI and change the display resolution back. It is the kind of problem which you learn how to solve and then it never bugs you again. Switching operating systems means meeting and learning how to solve all these minor annoyances all over again. Fortunately solving this kind of thing is easier in ubuntu than in windows.

There are MANY ways to do it via the command line. But if this problem happens to you regularly you might want to look into doing what I've done, which is to set up a couple of keyboard shortcuts so that you can fix the problem instantly and don't have to remember all those commandline commands.

System-preferences-keyboard shortcuts is the place to set this up.

Click to add. I have the following set up
```

ctrl alt end     ==>   metacity --replace
``````

ctrl alt home   ==>   compiz --replace ccp
``````

ctrl alt backspace  ==>  xrandr -s 1280x1024
```The first two switch window manager between compiz and metacity. This is useful for turning compiz off and on quickly in order to run certain games. Reinitialising your window manager is also a quick fix for pretty much any kind of display issue and will usually fix the problem you mention. 

The last one explicitly resets the screen resolution to 1280x1024. Adjust the values to the defaults you like, but make sure it is a resolution that works with your hardware. 

With this set up, if a game crashes out and leaves you in a bizarre screen resolution, you can fix it instantly with a simple key combination.

---

### Post by markjs on 2010-08-28
LoL, I finally got my breath (and more importantly my mind) back!

Before I got your reply I found [this]("http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html"):  

> Open up a Terminal window, by clicking on Applications \ Accessories \ Terminal. Or, if you deleted the top panel and cannot access the menus, just press ALT+F2 and in the run dialog box, type gnome-terminal then click on Run.

You can also browse for applications, such as Terminal from the Run window, by clicking on the arrow icon next to 'Show list of known applications" and browse for Terminal.



Once the Terminal window opens, enter the following command at the prompt:

gconftool-2 – -shutdown

(Note: There should be no spaces between the two dashes before shutdown.)

EDIT – Reader nickrud has suggested a better method instead of shutting down gconfd. Instead use the following command (thanks nickrud!)

gconftool – -recursive-unset /apps/panel

(Remember: There should be no spaces between the two dashes before shutdown.)

Then enter the next command:

rm -rf ~/.gconf/apps/panel

And enter one more command:

pkill gnome-panel

That's it!

See this is what I needed because it actually is written for a novice!

Thanks though I will look into implementing that info too!

---

### Post by DeMus on 2010-08-28
There are many interesting internet sites and there lots of books to read so you learn more about Linux and/or Ubuntu.
Don't forget you also had to learn how to handle Windows, maybe at school, maybe at work, maybe just at home. It's the same for Linux, you have to learn how to operate and control it and when you do, you will love it.

---

### Post by markjs on 2010-08-28
You're right about it not being Linux only.  But still, Windoze was always aimed at novices and now that I am so trained in it it can be hard to switch gears.  Add to that that some of the guys who write for Linux in the past have just been either too technically proficient to write good instructions, or maybe just evil little coders who like to mess with you.  It has gotten much better but still with Windows it is easier to find simple instructions sometimes just because it wasn't written by so many different people.

---

### Post by DeMus on 2010-08-28
> **markjs said:**
> You're right about it not being Linux only.  But still, Windoze was always aimed at novices and now that I am so trained in it it can be hard to switch gears.  Add to that that some of the guys who write for Linux in the past have just been either too technically proficient to write good instructions, or maybe just evil little coders who like to mess with you.  It has gotten much better but still with Windows it is easier to find simple instructions sometimes just because it wasn't written by so many different people.

Okay, it is not as easy as Windows, but is that a reason to quit? Think not. Put your teeth into it, do one thing at a time, read a lot and it will come to you. I use it for 2 1/2 years now and I am still learning, especially here on the forum. I write my problems here and get answers, when possible I help others. I read books and websites and get better and better. You can do the same. Don't let it discourage you right from the start. It takes time, that's true, but it's a great system and it is worth to put in the extra mile.

---

### Post by markjs on 2010-08-28
Oh there is no doubt that this is the best and most friendly Linux site I have ever been to and who said anything about giving up?  I said this is why I have given up, past tense.  I am going to learn it, and not give up this time, but you must admit there can be times and sometimes weeding through bad info to find good is a pain too.

I remember 10 years ago if you asked Linux geeks anything online they would make fun of you, insult you then tell you to read the man page.  It has indeed come a long way.

---

### Post by XubuRoxMySox on 2010-08-28
Alot of the time, people who help others here offer command-line solutions because it's alot faster and easier - not just for you, but for them! It's easier to type

```
sudo aptitude clean
```

for example, than it is for them to write a whole paragraph on how to get the same thing done using a graphical interface. They want to help as many people out as they can, in between the stuff in their own hectic lives. 

I think it's awesome that so many people come here just to help others! Maybe some are better at putting things in terms that you or I can understand, but they're all just being sweet to help us out, dontchyathink?

Use Google, search the forums, and don't try the very first solution that is offered if you can't understand it. Wait a bit for one that is spelled out in a way that makes sense. It rarely takes longer than just a few hours for a "perfectly put" solution to appear on this wonderful support site!

I think you'll learn in spite of yourself, and it'll be fun!

Enjoying it,
Robin

---

### Post by Dayofswords on 2010-08-28
> I remember back in my windows days having exactly the same problem with games crashing out and leaving me in an unusable screen resolution unable to reach any of the useful buttons in the GUI and change the display resolution back.

i remember having that problem too in the days of win98

---

### Post by rollin on 2010-08-28
> **dixiedancer said:**
> Alot of the time, people who help others here offer command-line solutions because it's alot faster and easier - not just for you, but for them! It's easier to type

```
sudo aptitude clean
```for example, than it is for them to write a whole paragraph on how to get the same thing done using a graphical interface. They want to help as many people out as they can, in between the stuff in their own hectic lives. 

I think it's awesome that so many people come here just to help others! Maybe some are better at putting things in terms that you or I can understand, but they're all just being sweet to help us out, dontchyathink?

Use Google, search the forums, and don't try the very first solution that is offered if you can't understand it. Wait a bit for one that is spelled out in a way that makes sense. It rarely takes longer than just a few hours for a "perfectly put" solution to appear on this wonderful support site!

I think you'll learn in spite of yourself, and it'll be fun!

Enjoying it,
Robin

Well said!

OP: DeMus and dixiedancer are right! You have to start with some kind of reference it's unlikely you will succeed without some form of guidance at first. Same with any kind of lessons / lectures you need some reference material to help. I'd suggest having a look around on Google Books for Linux stuff. 
I actually fully agree with a point you made "walk away" which is a great idea if your converting to Linux from something like Windows. Run Linux as Wubi or on a seperate PC to begin with so it doesn't affect your normally day PC activities, that way you can take some time here and there to work on your knowledge and the system you have. Ultimately the harder you are trying the more you will learn. You seem fairly passionate about it which is great, I'm sure that energy will help you master it soon enough.

---

### Post by cariboo on 2010-08-29
It seems to me that many users ignore the fact that they've used Windows exclusively for most of their lives. They forget how hard Windows was to use when they first started using computers. If they used a linux variant exclusively for as long as they have used Windows, all problems would be pretty trivial.

That being said, there are so many good resources available now, then when I started using Linux, that solving most problems doesn't take much effort.

---

### Post by 3Miro on 2010-08-30
When I first read this, I realized that I don't know how to restore default settings for the panels in Windows, then I realized that last time I was using windows full time was windows XP and the only customization this one had, was which side of the screen you want it on.

There are many different explanations on how to do things. There are official HowTo's that are very good and very noob oriented and I don't think the first example given was from such a HowTo. If you ask a question on the forum and you don't understand the answer, ask for clarification. If you see someone else's post, then maybe the answer was good enough for them.

One big realization about Linux settings: there is no common registry or any kind of a database that all apps reference for their individual settings. Everything is written in a plain text file somewhere. If something breaks down, it can always be fixed by manually editing some files.

---

