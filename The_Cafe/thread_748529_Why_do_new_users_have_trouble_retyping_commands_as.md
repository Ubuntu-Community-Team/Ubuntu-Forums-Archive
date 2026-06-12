---
title: "Why do new users have trouble retyping commands as they see them?"
date: 2008-04-07
forum: The Cafe
---

### Post by aysiu on 2008-04-07
I'm not trying to be elitist here, since I was a new user once, and when I was a new user, I also had difficulty retyping commands at that time. It's this difficulty that has had me recommending people copy and paste instead of retype commands.

You might have seen it happen before. Someone says > Just type ```
cat /etc/apt/sources.list
``` in the terminal and then the user gets an error for typing ```
cat/etc/apt/sources.list
``` or ```
cat /etc/apt/source.list
``` I might think to be outraged ("Can't these people read?!") except that, as I said before, I also had trouble retyping commands when I first started on Linux.

So my question is why do new users have trouble retyping commands? Why did I? I don't know. It's a mystery to me why aysiu in 2008 has no trouble retyping commands (even ones I haven't seen before) but aysiu in 2005 did have trouble.

Ideas?

---

### Post by bapoumba on 2008-04-07
May be because the syntax and most of the words and signs make sense now, when they did not mean anything before?

---

### Post by Npl on 2008-04-07
> **aysiu said:**
> I'm not trying to be elitist here, since I was a new user once, and when I was a new user, I also had difficulty retyping commands at that time. It's this difficulty that has had me recommending people copy and paste instead of retype commands.

You might have seen it happen before. Someone says  and then the user gets an error for typing ```
cat/etc/apt/sources.list
``` or ```
cat /etc/apt/source.list
``` I might think to be outraged ("Can't these people read?!") except that, as I said before, I also had trouble retyping commands when I first started on Linux.

So my question is why do new users have trouble retyping commands? Why did I? I don't know. It's a mystery to me why aysiu in 2008 has no trouble retyping commands (even ones I haven't seen before) but aysiu in 2005 did have trouble.

Ideas?simple: you learned the grammar of the shell

---

### Post by aysiu on 2008-04-07
That might explain a lot of it, but on a very basic level, shouldn't someone who knows English (someone like me of three years ago) be able to tell the difference between two words that have a space in between them and two words without a space? Or the word *source* and the word *sources*?

---

### Post by popch on 2008-04-07
Two ways of thinking about that.

One: 

To a new user, those commands are just gibberish, i.e. strings of letters, numbers and others characters without rhyme or reason. A new user has no conception of whether white space is meaningful or not, and under what conditions. Truth to be told, there's no 'canonical' answer to that. Not only does a new use not know the syntax of the command you have him type, he is not even aware of the very concept of a syntax for 'character soups'. You can recapture a tiny bit of that feeling by trying to enter a line of random characters with a liberal sprinkling of white space and some characters you did not even know your keyboard had (if, in fact, it does have them).

Two: 

The new user might think computers are intelligent. They then might go on to presume that altering the case of what they are entering to something more adequate, altering word order or entering a synonym for another term was quite all right. 

In German, for instance, we capitalize the first word of a sentence and all nouns and proper names. That greatly improves the legibility of some computer statements.

You can now stop laughing. That's what I did in my very first program, and I could not understand for the life of me why the bloody box insisted that a term was undefined when the manual clearly said to use a term with the very same meaning.

---

### Post by BDNiner on 2008-04-07
Yes all the typing takes some getting used to. I for one use a lot of auto complete on Word so that when i miss type words they are automatically corrected. I have added several words like changing colour to color and centre to center, because that is the way i learned the words and spelling them the correct way annoys most Americans. So i had a lot of trouble in linux because i wouldn't think about the autocomplete and just assumed the words i was typing would get corrected.

I will say that linux has made me a better typer. I don't look down at the keyboard anymore and make far fewer mistakes when typing. And i correct mistakes a lot quicker now, it helps to look at the screen when typing.

---

### Post by odiseo77 on 2008-04-07
Maybe they don't know useful things like copying and pasting with a middle click or some key combination (which I wouldn't suggest to do all the time without thinking but in some cases) and the magic of tab completion (it took me like 6 months of using the terminal to discover the tab completion trick, I think).But probably the most important factor is they're not familiar with the file system structure and the most commonly used commands.

---

### Post by aimran on 2008-04-07
What I'm more worried is that they don't even understand copy/paste! Highlight, right-click, select copy, go to terminal, right click, paste.

Saves having to learn shell grammar :P

---

### Post by BDNiner on 2008-04-07
My begining experience with linux was command line only. It took me a week to understand how to correctly install the nvidia drivers and get X started. It wasn't until about a month ago that i discovered the middle click.

---

### Post by hsweet on 2008-04-07
Most humans are not used to looking at what is there.  

This is true if you want to learn how to draw as much as for learning bash.  Forget about CLI.  How many folks have missed a gui hint that is right there on the screen screaming "click me!!!!!" Instead, they think clicking randomly as fast as possible(preferably with eyes closed) will solve the problem.

So, looking at an unfamiliar command thingie, most folks miss a critical detail or 2 and the thing does not work.

There is a lot to be said for cut and paste!

---

### Post by Bruce M. on 2008-04-07
[CENTER]
[[IMG]http://img392.imageshack.us/img392/6922/pic18584yx0.th.gif[/IMG]](http://img392.imageshack.us/my.php?image=pic18584yx0.gif)
[SIZE="5"]**is worth two in the hand!**[/SIZE]
[/CENTER]

Do you know that a person "reading" his/her native language does NOT see every word? The mind steps in and predicts certain words. Prepositions are a biggie here.

Now add that to a **"new OS"** with a **"mindset for the old OS"** and you're an error looking for a place to happen.

For example it took me a bit to see the difference between your original code and the third code.  HEY! Who put that **s** in there?

Nice subject.







How many saw: "A bird in **the *the*** bush is worth two in the hand" at first glance?

---

### Post by Het Irv on 2008-04-07
I know I would type the command aysiu gave above:
```
cat /ect/apt/sources.list
```
I do it everytime,  I think the other roadblock is the keyboard command for Copy and Paste in the terminal is "Shift+Ctrl+C" and "Shift+Ctrl+V".  That might trip up some new users.

EDIT: and some old users as well it seems:lolflag:

---

### Post by aysiu on 2008-04-07
Yeah, I definitely didn't know about case-sensitivity, copying and pasting, or autocomplete when I started out. But even with all that aside, I still mistyped what should amount to transcription.

I guess it goes back to what popch said earlier about it appearing to be gibberish. I read *Misquoting Jesus* recently, and I thought it was interesting how some errors in copied manuscripts were done by scribes who didn't even know the language they were copying! Probably similar to this situation.

---

### Post by Bruce M. on 2008-04-07
> **Het Irv said:**
> I think the other roadblock is the keyboard command for Copy and Paste in the terminal is "Shift+Ctrl+C" and "Shift+Ctrl+V".  That might trip up some new users.

Ahhhhhhhh, so that's how! I've been wondering why [Ctrl]+c and [Ctrl]+v didn't work.

Learned a new thing today.

me = \\:D/
Bruce

---

### Post by BDNiner on 2008-04-07
+1, i had no clue why ctrl+c and ctrl+v didn't work.

---

### Post by aysiu on 2008-04-07
> **Bruce M. said:**
> 
How many saw: "A bird in **the *the*** bush is worth two in the hand" at first glance? Good point. I didn't catch that at all.

---

### Post by FranMichaels on 2008-04-07
> **Het Irv said:**
> I know I would type the command aysiu gave above:
```
cat /ect/apt/sources.list
```
I do it everytime,  I think the other roadblock is the keyboard command for Copy and Paste in the terminal is "Shift+Ctrl+C" and "Shift+Ctrl+V".  That might trip up some new users.

EDIT: and some old users as well it seems:lolflag:

Let's be glad there is no folder named "the"

cd /teh does not exist!

I think it is just nervousness or rushing.
I'm sure the same errors can happen when dealing with a touch tone phone or calculator. 
Enter even the smallest thing wrong, it's likely you won't get what you want out of the device :)

---

### Post by Bruce M. on 2008-04-07
> **aysiu said:**
> Good point. I didn't catch that at all.

And the real phrase is:
> A bird in the hand is worth two in the bush.

---

### Post by BDNiner on 2008-04-07
Yeah great test Bruce M. Did you ever get a similar chain e-mail where the first and last letters of the words are correct but all the others are in the wrong order? your brain fills in the rest of the words even with only 2 letters being correct so you can still read the message. very interesting.

---

### Post by Bruce M. on 2008-04-07
> **BDNiner said:**
> Yeah great test Bruce M. Did you ever get a similar chain e-mail where the first and last letters of the words are correct but all the others are in the wrong order? your brain fills in the rest of the words even with only 2 letters being correct so you can still read the message. very interesting.

Yes, I still have that here.

I should post it here if it's OK with aysiu.  I don't want to go off topic but in some respects it does fit the question, because it certainly displays the fact that the "mind" plays a BIG role when reading something.

aysiu, any thoughts?

---

### Post by Irihapeti on 2008-04-07
I think that stress is a big factor. I know I've misread and/or misinterpreted many things (not just commands!) when I've been under pressure.

Many (most?) beginners posting problems are stressed in some way: anxious, angry, afraid, maybe feeling stupid/ashamed that they have their problem.

I've noticed also that even when I'm not stressed, I can have some difficulty deciding whether there's a space in a line of type, or whether it's just the way the typeface happens to display.

Just my $0.02

---

### Post by aysiu on 2008-04-07
Thanks to all who've answered so far. I've gained a lot of insight into this phenomenon. I think Irihapeti is right that stress has a lot to do with it. It may be a lot harder to type cryptic commands if you're frustrated that "nothing" is working.

---

### Post by retrow on 2008-04-07
> **aysiu said:**
>  Someone says  and then the user gets an error for typing ```
cat/etc/apt/sources.list
``` or ```
cat /etc/apt/source.list
```
Be glad you don't get people who reply with:

Why cat? I don't like cats. Can I use a different animal instead?

---

### Post by kutjara on 2008-04-07
whut da hill r yoo takkin boot? Ah neevah haf trubbal tiping kammands.

---

### Post by Dr Small on 2008-04-07
I think that maybe around the first week, I may have begun typing in commands, rather than pasting them, but I came from Windows and knew how to use command prompt, and spoof emails from hotmail :)

I understood sytax and that things had to be spelt correctly. So typing really wasn't a big issue for me in the beginning. As time progressed, I began pasting the commands in the terminal. Of course now, I completely understand what each command does, and can usually type it out by just glancing at it.

But as to the question, I think new users have this paranoid, creepy, scary feeling of the terminal, and they become nerveous when they have to open it. Thus the pressure and typos when they type.

Dr Small

---

### Post by ubuntu-freak on 2008-04-07
It just goes over your head at first, bit of an overload and some frustration mixed in. That's why I recommend cutting and pasting, and I think most new users naturally think to do that anyway.
 
Nathan

---

### Post by forrestcupp on 2008-04-07
The command line typos don't irritate me half as much as when people get an error that tells them right there in the output what command to enter to fix the problem, and yet they still come on the forums asking what to do.  Someone always asks if they tried doing what the output says to do, and when they try it, it magically works!

> **Het Irv said:**
> I think the other roadblock is the keyboard command for Copy and Paste in the terminal is "Shift+Ctrl+C" and "Shift+Ctrl+V".  That might trip up some new users.

That messed me up for a while.  I usually use Shift+Insert to paste in the terminal.

---

### Post by aysiu on 2008-04-07
> **forrestcupp said:**
> The command line typos don't irritate me half as much as when people get an error that tells them right there in the output what command to enter to fix the problem, and yet they still come on the forums asking what to do.  Someone always asks if they tried doing what the output says to do, and when they try it, it magically works!


That messed me up for a while.  I usually use Shift+Insert to paste in the terminal.
Depending on the error message, I can be understanding about it. For example, Ubuntu really shouldn't tell you to run ```
dpkg --configure -a
``` if you're really supposed to run ```
sudo dpkg --configure -a
```

---

### Post by forrestcupp on 2008-04-07
> **aysiu said:**
> Depending on the error message, I can be understanding about it. For example, Ubuntu really shouldn't tell you to run ```
dpkg --configure -a
``` if you're really supposed to run ```
sudo dpkg --configure -a
```

True.  I've had to guide someone through that one before.

---

### Post by hvac3901 on 2008-04-07
For me, and this might sound funny to ya'll, I have a hard time telling spaces sometimes, i have good vision so thats not the issue, but if "l" is after anything there is a pretty convincing space left.

I just hate not knowing the commands, and then wondering why i can't remember them when i need them.

---

### Post by kevdog on 2008-04-07
I just wish Cntl-C and Cntl-V were used for copy and paste rather than the addition of the Shift.  I'm not asking MS to define a standard but it seems that it already is an unwritten standard.  Anyway that I can set something up for me to do this?  Alter some config file perhaps?

---

### Post by Boelcke on 2008-04-07
Someone said it best already, you get used to the context.  Even now when you type a command you don't know, you've got the basic format down.

For someone who has only known windows, /etc/apt looks silly.  Their brain is only used to seeing filenames as C:\WINDOWS\stuff.

The same trick happens when you learn to fly airplanes and talk to air traffic control.  It's the same English you know, only it isn't.  At first, you can't make out what anyone is saying on the radio.  Later, at some point, it becomes obvious and routine.  In fact, folks only use a limited vocabulary of words and always say things in a similar way to help avoid confusion.

You've done the same thing with linux commands.  I have too, as I've switched over to Linux.

It reminds me of the trick where you can read something even when much of the words are messed up.  > Aoccdrnig to rscheearch at Cmabrigde Uinervtisy, it deosn't mttaer in waht oredr the ltteers in a wrod are, the olny iprmoetnt tihng is taht the frist and lsat ltteer be at the rghit pclae. The rset can be a toatl mses and you can sitll raed it wouthit a porbelm. Tihs is bcuseae the huamn mnid deos not raed ervey lteter by istlef, but the wrod as a wlohe. That's a great example of how much you're NOT reading the text.  I believe the same is true of linux commands.

---

### Post by jflaker on 2008-04-07
What is MORE interesting is trying to support a remote user and asking them to describe then read the ENTIRE SCREEN to you.....Unless I have had already spoken to the user in a previous session, I never was able to get them to describe and read the entire screen.......they would pick a spot somewhere in the center of the screen and start reading........

When speaking to remote users and having them type a command, I read the command character for character and then have them read it back..........Usually it is wrong then too.

Users are generally scared of more than GUI and they panic.  When panicked, they skip the details and type what, in the spoken language, looks like it may be correct.

---

### Post by master5o1 on 2008-04-07
Would it be possible to add a plugin to terminal to make it easier where when a user mistypes something, instead of erroring out, the terminal instead tries to give options of possible commands?

example

cd/ect/x11/xorg.conf

terminal instead of erroring shoud say

do you mean cd /etc/X11/xorg.conf (y/n)

or something like that.

---

### Post by yatt on 2008-04-08
> **aysiu said:**
> I'm not trying to be elitist here, since I was a new user once, and when I was a new user, I also had difficulty retyping commands at that time. It's this difficulty that has had me recommending people copy and paste instead of retype commands.

You might have seen it happen before. Someone says  and then the user gets an error for typing ```
cat/etc/apt/sources.list
``` or ```
cat /etc/apt/source.list
``` I might think to be outraged ("Can't these people read?!") except that, as I said before, I also had trouble retyping commands when I first started on Linux.

So my question is why do new users have trouble retyping commands? Why did I? I don't know. It's a mystery to me why aysiu in 2008 has no trouble retyping commands (even ones I haven't seen before) but aysiu in 2005 did have trouble.

Ideas?Perhaps they do not realize that Linux is capable of advanced features such as copy and paste.

---

### Post by HangukMiguk on 2008-04-08
> **aimran said:**
> What I'm more worried is that they don't even understand copy/paste! Highlight, right-click, select copy, go to terminal, right click, paste.

Saves having to learn shell grammar :P

Do that in xterm or aterm and see what happens ;)

I always got more frustrated doing that as a newb because Ctrl+V didn't work.  Now, Shift+Insert is like breathing to me.

---

### Post by popch on 2008-04-08
> **yatt said:**
> Perhaps they do not realize that Linux is capable of advanced features such as copy and paste.

But then, how is someone going to learn about commands and syntax and stuff when they just copy and them? Some people learn better by typing stuff.

---

### Post by ubuntu-freak on 2008-04-08
> **aysiu said:**
> Depending on the error message, I can be understanding about it. For example, Ubuntu really shouldn't tell you to run ```
dpkg --configure -a
``` if you're really supposed to run ```
sudo dpkg --configure -a
```

 
That catches quite a few people out and makes them feel rather silly. Obviously it's written that way because we are using Debian, and that message presumes you are in super user (admin) mode already, "su". Are there any plans to change how the commands are displayed in the Ubuntu family distros? It would mean less support questions and red faces.
 
Nathan
 
P.S. Doesn't anyone else use the right-click context menu to copy/paste into the Terminal? I never use the keyboard method.

---

### Post by 3rdalbum on 2008-04-08
I like it when a new user asks something like "I tried to install blender from the command-line, but it didn't work!" and then they post the contents of their terminal; and their terminal always begins with this:

```

ubuntu@ubuntu: ~$ sudo apt-get blender
Password: 
Sorry, try again.
Password:
Sorry, try again.
Password:
dpkg: The action "blender" is unknown

```

I guess some people are just quite bad at typing. It's not just the commands themselves that they have trouble with; their own passwords can trip them up (especially when they can't see what they're typing or how many characters they've typed)

---

### Post by Irihapeti on 2008-04-08
> **3rdalbum said:**
> 

```

ubuntu@ubuntu: ~$ sudo apt-get blender
Password: 
Sorry, try again.
Password:
Sorry, try again.
Password:
dpkg: The action "blender" is unknown

```



I've seen this in *advice* given to people! Maybe because the "-get" in "apt-get" already presupposes getting and installing? And, no, I can't say that I wouldn't be guilty myself - I know I've frustrated myself a few times by forgetting the magic word "install":oops:

---

### Post by koenn on 2008-04-08
> **master5o1 said:**
> Would it be possible to add a plugin to terminal to make it easier where when a user mistypes something, instead of erroring out, the terminal instead tries to give options of possible commands?

example

cd/ect/x11/xorg.conf

terminal instead of erroring shoud say

do you mean cd /etc/X11/xorg.conf (y/n)

or something like that.

actually, tab completion does that already - if you hit tab every few characters it would catch the missing space and the non-existing ect and x11, catch mistakes in paths in the process,  and write 70 % of the statement for you - garantueed correct.

---

### Post by Het Irv on 2008-04-09
[http://ubuntuforums.org/showthread.php?goto=newpost&t=750592](http://ubuntuforums.org/showthread.php?goto=newpost&t=750592)

An example you need?  Here look you should.

---

### Post by fissionmailed on 2008-04-09
I was clumsy, I have gotten better with my typing skills since then.  Plus I've learned how the shell works, that helps a lot IMO.

---

### Post by tamoneya on 2008-04-09
until recently i thought that it was just tab auto complete and the lack of copy paste usage but recently I have run into some users who run into more trouble that would be expected.  I have had people not been able to run ```
ls -l
``` Even after saying "those are lower case Ls" they told me that the command was not found.  What do you guys think could be the source of this and more importantly how can we work to fix this miscommunication.

---

### Post by aysiu on 2008-04-09
> **tamoneya said:**
> until recently i thought that it was just tab auto complete and the lack of copy paste usage but recently I have run into some users who run into more trouble that would be expected.  I have had people not been able to run ```
ls -l
``` Even after saying "those are lower case Ls" they told me that the command was not found.  What do you guys think could be the source of this and more importantly how can we work to fix this miscommunication.
The l's can sometimes look like 1's. The best way to fix this miscommunication is to say > Copy and paste this command instead of > Type this command

---

### Post by NightwishFan on 2008-04-09
Yes, asking to copy/paste would help some beginners.

The main thing users want other than no problems, is having a popup say "This problem has been fixed automatically."

---

### Post by Barrucadu on 2008-04-09
I've often wondered that myself, I've never gone through a period like that. I started using Ubuntu, and BAM, I could use the shell and knew all the basic commands.
How? I don't know. I had never seen a ls, cd, or apt-get before, but I somehow just knew them. I didn't actually discover Synaptic and Add/Remove Programs until a few weeks after I had installed everything.

---

