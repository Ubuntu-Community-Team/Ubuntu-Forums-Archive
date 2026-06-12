---
title: "Vim rant"
date: 2006-06-09
forum: The Cafe
---

### Post by graigsmith on 2006-06-09
I don't understand why one of the most user friendly desktops has the default command line editor set to vim, which is way to complicated.  I just hate vim.  When i first started using linux, and i accidently got into vim, when i tried to access the manual on a certain command.  I couldn't do anything, but restart the computer.  I couldn't even figure out how to exit the program.  I attempted once to start learning vim.  But then i realised that i shouldn't have to learn something almost as complicated as a programming language to use a TEXT EDITOR.  Why do we include something like this as the default command line editor? isn't there something better we can use, so that noobies who type man ls, or man mount don't get confronted with something that only programmers should ever see.

---

### Post by grte on 2006-06-09
You can take vim from my cold dead hands.

You could always use nano.  It's installed by default, as well.

---

### Post by Sheinar on 2006-06-09
If for some reason my internet connection wasn't working after a fresh install and I had to edit some config files, I'd probably start pulling out my hair if I couldn't use vim.

---

### Post by benplaut on 2006-06-09
coming from a vi(m) user, the default really should be nano...

---

### Post by cormic on 2006-06-09
I found vi very difficult to get used to at the begining but I had to use it as it was the only editor on the systems I was using at the time.

I found this site really handy in those early days.

[http://www.lagmonster.org/docs/vi.html](http://www.lagmonster.org/docs/vi.html)

---

### Post by frenkel on 2006-06-09
[QUOTE=graigsmith]I don't understand why one of the most user friendly desktops has the default command line editor set to vim, which is way to complicated.  I just hate vim.  When i first started using linux, and i accidently got into vim, when i tried to access the manual on a certain command.  I couldn't do anything, but restart the computer.  I couldn't even figure out how to exit the program.  I attempted once to start learning vim.  But then i realised that i shouldn't have to learn something almost as complicated as a programming language to use a TEXT EDITOR.  Why do we include something like this as the default command line editor? isn't there something better we can use, so that noobies who type man ls, or man mount don't get confronted with something that only programmers should ever see.[/QUOTE]

Default is nano. Where did you read that the default is vi? Just run update-alternatives --all and see? It's nano. You can chose to make it vim.
(From the update-alternatives man page: "The current choice is marked with a ’*’ and the choice with the highest priority with a ’+’.")

---

### Post by ComplexNumber on 2006-06-09
i quickly developed a hatred of vi around 1997 when i had to use it.

---

### Post by angkor on 2006-06-09
[QUOTE=graigsmith]I don't understand why one of the most user friendly desktops has the default command line editor set to vim, which is way to complicated.  I just hate vim.  When i first started using linux, and i accidently got into vim, when i tried to access the manual on a certain command.  I couldn't do anything, but restart the computer.  I couldn't even figure out how to exit the program.  I attempted once to start learning vim.  But then i realised that i shouldn't have to learn something almost as complicated as a programming language to use a TEXT EDITOR.  Why do we include something like this as the default command line editor? isn't there something better we can use, so that noobies who type man ls, or man mount don't get confronted with something that only programmers should ever see.[/QUOTE]

*lol*

I agree, I love vim. ;). Once you get to know it it's fast and intuitive, I agree however the learning curve can be a showstopper for some.

Anyhow, why do you care, use nano or something.

---

### Post by B0rsuk on 2006-06-09
The point is not to remove vim, but to NOT make it the default editor. Let's face it, for someone who never used it, the interface is **awful.** It typically takes a few minutes for a person to go launch help and check what the quit hotkey is.
In case you didn't understand, this is **opposite** of what you want when you're just going to edit /etc/apt/sources.list right after install. Or some other quick config edit.

Nano should be default editor instead, it's much more userfriendly, works in console. It has the essential keys listed on screen all the time. Developers/programmers tend to know what they want to use and where to find it.  Besides, by default Ubuntu doesn't come with something as essential (for programming) like build-essential package, so any arguments that removing vim from default is harmful are lunacy.

to get rid of vim as default editor...
```

$ EDITOR=program_name
$ export $EDITOR

```
where program_name is for example, nano, mcedit (if you have mc installed), kate(requires KDE), gedit, emacs and so on.

I don't know for dapper, but in breezy, try to run texconfig and edit formats.... It's vim. setting up a variable fixes that.

---

### Post by cstudent on 2006-06-09
Use pencil and paper next time. Make it easy on yourself.


.

---

### Post by graigsmith on 2006-06-09
when i type editor, i get nano.  but when i type man mount, to get the manual, it opens it with vi.  kinda annoying.  why doesn't it open it with nano?

---

### Post by Hanj on 2006-06-09
> but when i type man mount, to get the manual, it opens it with viAre you sure about that? You must have made some weird change to some setting then, because man is its own text viewer, very similar to less. I've never seen man open up vi/vim, at least not by default. Not on Ubuntu or any other *nix system I've used.

---

### Post by Stormy Eyes on 2006-06-09
[QUOTE=benplaut]coming from a vi(m) user, the default really should be nano...[/QUOTE]

I agree, and I use Vim myself. Since I'm experienced, I can always change the default to Vim for myself, but less experienced users might appreciate a simpler editor. I also think we should put emacs in multiverse; it's evil.

---

### Post by Stormy Eyes on 2006-06-09
[QUOTE=B0rsuk]In case you didn't understand, this is **opposite** of what you want when you're just going to edit /etc/apt/sources.list right after install. Or some other quick config edit.[/QUOTE]

Newbies should be using gedit anyway, not vim.

---

### Post by frenkel on 2006-06-09
[QUOTE=graigsmith]when i type editor, i get nano.[/QUOTE]
Indeed, just like I said, nano is the default editor, unless _you_ change it with update-alternatives --all

---

### Post by angkor on 2006-06-09
[QUOTE=B0rsuk]The point is not to remove vim, but to NOT make it the default editor.[/QUOTE]

Read post #6 of this thread. The default **is** nano.

:confused:

---

### Post by tageiru on 2006-06-09
[QUOTE=graigsmith]when i type editor, i get nano.  but when i type man mount, to get the manual, it opens it with vi.  kinda annoying.  why doesn't it open it with nano?[/QUOTE]
That is impossible, man is a program that has nothing to do with editing text.

---

### Post by kabus on 2006-06-09
[QUOTE=tageiru]
That is impossible, man is a program that has nothing to do with editing text.[/QUOTE]

Man displays man pages using whatever program is specified in the MANPAGER environment variable, which can be set to vim.
It is much more likely that the original poster confuses less (the default pager used by man) with vim, though.

---

### Post by tseliot on 2006-06-09
[QUOTE=Stormy Eyes]I also think we should put emacs in multiverse; it's evil.[/QUOTE]
Oh, well I'm not a fan of Emacs or Vim but sometimes ago a kernel hacker told me that every time you use Vi, God kills a kitten :p 

Now which is the lesser of the two evils? :D 

No flamewar is meant, eh. I use Gedit and Nano but I look forward to learning both Emacs and Vim (so as to be able to say which I prefer)

---

### Post by Wallakoala on 2006-06-09
I personally really like vim. It seemed like a cool text editor even thought I had no clue how to use it. Through the use of google I learned how to use it. I mainly use gedit to write programs, but for editing config files and stuff, there is nothing like vim.

---

### Post by Stormy Eyes on 2006-06-09
[QUOTE=tseliot]Oh, well I'm not a fan of Emacs or Vim but sometimes ago a kernel hacker told me that every time you use Vi, God kills a kitten :p [/QUOTE]

Every time you use Emacs, Cthulhu eats a baby.

---

### Post by tseliot on 2006-06-09
[QUOTE=Stormy Eyes]Every time you use Emacs, Cthulhu eats a baby.[/QUOTE]
ok, I'll keep using Gedit and nano so as to prevent further murders. I like kittens though... :p

---

### Post by Sheinar on 2006-06-09
[QUOTE=Stormy Eyes]Every time you use Emacs, Cthulhu eats a baby.[/QUOTE]
I think it's time I learnt how to use Emacs then.

---

### Post by Stormy Eyes on 2006-06-09
[QUOTE=tseliot]ok, I'll keep using Gedit and nano so as to prevent further murders. I like kittens though... :p[/QUOTE]

Go ahead and use Vim; you'll help keep the feral cat population under control.

---

### Post by tseliot on 2006-06-11
[QUOTE=Stormy Eyes]Go ahead and use Vim; you'll help keep the feral cat population under control.[/QUOTE]
I have fallen in love with Vim. It's just too confortable and terribly addictive.

Poor kittens...

---

### Post by 3rdalbum on 2006-06-11
Vi(m): $0.
Emacs: $0
gEdit: Priceless.

---

### Post by halfvolle melk on 2006-06-11
What default? When you type 'vi' you get vim, when you type 'nano' you get nano. How is either default and where does it say that/do you change that?

---

### Post by fuscia on 2006-06-11
nano is where the money is.

---

### Post by hugmenot on 2006-06-11
Man pages are /not/ displayed with vi. Man uses your default pager, which is »less«. If you want nano try "man -P nano mount". It doesn&#8217;t completely make sense to use an editor for reading stuff however. Another nice pager is »most« which you can get with apt. It has a help line on the bottom for you. Just try to remember that the first and foremost key to exit stuff is a simple q¹. If that scares you, perhaps the command line is not for you.


¹then ctrl-c, ctrl-x, quit, bye, exit, \q, quit;, :q, et cetera

---

### Post by christhemonkey on 2006-06-11
For me i always if i need to do something quickly, use Vi(m)

:q! always helps in vi...


(My big brother laughed when he read man mount... o deary me.)

---

### Post by hugmenot on 2006-06-11
[QUOTE=christhemonkey]:q! always helps...[/QUOTE]

No, because he is not using vim at all.

---

### Post by IYY on 2006-06-11
> when i type editor, i get nano. but when i type man mount, to get the manual, it opens it with vi. kinda annoying. why doesn't it open it with nano?

You want to open the man page with nano? Why? A man page is not a text file you edit, it's a help file you scroll down and quit when you want to. For this, the default command is perfect (and it's not vim, it's 'less'). Down to move down, up to move down, page-down and page-up to scroll by pages, and q to quit. Not to mention that if you type a wrong key it actually prints out the keys you can use and what they do. What could possibly be friendlier for newbies?

---

### Post by Gtaylor on 2006-06-11
vim is definitely awesome. It does take a while to get used to it, but once you have a good idea of how to get around, you can run circles around emacs or gedit. I'm a very impatient programmer and I really hate when a bloated interface gets in my way. I find vim visually simple and the keyboard shortcuts become second nature after a while, once you get used to the keys for everything there isn't much getting in my way of codemongering.

For example, I strongly dislike having to interrupt my typing by picking up my mouse and clicking something. It takes time and sometimes using the keyboard alternative takes even longer. With vim, it's a keypress or two away.

But really, it isn't for the feint of heart, as mentioned. Vim has so many features that you'll never even come close to learning all of them, but you only need a set few to be productive.

---

### Post by euphemus on 2008-12-11
Couldn't agree more - I HATE VIM! HATE HATE HATE HATE HATE

The next time a program installs itself with vi as editor, I am going back to Windows - a hollow threat (but I HATE VIM that much). The most unfriendly editor there ever was.

---

### Post by mentallaxative on 2008-12-11
Thread necromancy + flamebait = pointless

---

### Post by Trail on 2008-12-11
Vim is actually pretty cool once you learn it. I have printed a cheatsheat with various vim commands and got it next to my seat.

It's very annoying, yet very powerful.

---

### Post by chucky chuckaluck on 2008-12-11
as a nano user, i can say that the one advantage to using something as anti-intuitive as vim is there's less chance you'll destroy your machine by accident.

---

### Post by EnGorDiaz on 2008-12-11
> **graigsmith said:**
> I don't understand why one of the most user friendly desktops has the default command line editor set to vim, which is way to complicated.  I just hate vim.  When i first started using linux, and i accidently got into vim, when i tried to access the manual on a certain command.  I couldn't do anything, but restart the computer.  I couldn't even figure out how to exit the program.  I attempted once to start learning vim.  But then i realised that i shouldn't have to learn something almost as complicated as a programming language to use a TEXT EDITOR.  Why do we include something like this as the default command line editor? isn't there something better we can use, so that noobies who type man ls, or man mount don't get confronted with something that only programmers should ever see.

vim *nightmare shudder* dnt get me started on vim

i was happily installing arch and boom it asked what text viewer/editor i should use i accidently hit it on vim 

and i was like errr...

---

### Post by EnGorDiaz on 2008-12-11
> **3rdalbum said:**
> Vi(m): $0.
Emacs: $0
gEdit: Priceless.

nanos way better :P

---

### Post by Bear Knuckle on 2008-12-11
The problem with *vi* is, it is as far from the modern users GUI experience as prossible. One of the widely accepted heristics of user interface design is:

> **Consistency and standards**
Users should not have to wonder whether different words, situations, or actions mean the same thing. Follow platform conventions. 

Since *vi* is nearly unchanged from times, where there was no mouse (at least not far from being developed and spread into the "real world"), it is not up to date, belonging to modern usability standards.

I like it and use it, but I bought a book to learn how to use it. In my first experience I also have not been able to quit it correctly. *vi* is the standard, because it's available on every system, except the one from Redmond. Is there a nano for Unix-Systems?

@graigsmith: Well, you complain about *vi* being the command line editor for one of the most user friendly desktop systems. Why do you use the command line, if the desktop is so friendly? And if you use the command line, you should be prepared to not have as much usability comfort as on a modern GUI system, but arguing about what is the best editor is like arguing if red whine is better than white one. It's not a matter of fact, it's a matter of taste.

Well, and don't let me forget to mention: **nano's for SISSIS!!!!** :D

---

### Post by bp1509 on 2008-12-11
> **graigsmith said:**
> I don't understand why one of the most user friendly desktops has the default command line editor set to vim, which is way to complicated.  I just hate vim.  When i first started using linux, and i accidently got into vim, when i tried to access the manual on a certain command.  I couldn't do anything, but restart the computer.  I couldn't even figure out how to exit the program.  I attempted once to start learning vim.  But then i realised that i shouldn't have to learn something almost as complicated as a programming language to use a TEXT EDITOR.  Why do we include something like this as the default command line editor? isn't there something better we can use, so that noobies who type man ls, or man mount don't get confronted with something that only programmers should ever see.

1. nano is the default text editor in Ubuntu's command line, except for man pages.. which you shouldn't be editing.
2. once one masters vi/vim you can do your text editing a lot faster than you can in nano or a gui editor. It's far more powerful.  Just wait until you have to search and replace globally. 
3. It's not that hard, i figured  it out in one week's worth of usage.  Look at vimtutor, it'll help. 
These tutorials may help: [http://ubuntuadministrator.com/?tag=vi](http://ubuntuadministrator.com/?tag=vi) as well
4. As to why vi is installed, is well, it's on every single linux system known to man.  vi is small enough to fit on a boot disk and is great for recovery purposes back in the day of floppies.  When you work with a large network of unix machines over ssh shells, you can count on the same text editor being on every single system, and that's vi or vim.  That's not the case with nano, pico, or others.
5. The man pages aren't full vi/vim.  You can drop into vim from them, I think, just as you can with less/more. But i don't get what's so complicated about man pages.  Press 'q' to quit and use your arrows to scroll.
6. If one was to consider themselves just a run of the mill desktop user, why aren't you using something like gedit, leafpad, mousepad,?

---

### Post by IllegalCharacter on 2008-12-12
> **chucky chuckaluck said:**
> as a nano user, i can say that the one advantage to using something as anti-intuitive as vim is there's less chance you'll destroy your machine by accident.

Probably because vim has proper undo support ;) From my experiences with nano (I used to use nano for programming before I switched to vim) the best undo support you get is ^U, which uncuts a line. Not really that helpful.

You're missing the point of vim. It's not designed to have an intuitive interface, it's designed to have a fast interface that stays out of the user's way - a lot of the time, these two goals are at odds with one another.

If you're going to be doing a lot of command-line stuff, I'd recommend learning vim as the time spent learning it will save much more time using it. For me, it took less than an hour to learn some basics and I was already more productive than I ever was with nano.

---

### Post by smartboyathome on 2008-12-12
> **bp1509 said:**
> 1. nano is the default text editor in Ubuntu's command line, except for man pages.. which you shouldn't be editing.
2. once one masters vi/vim you can do your text editing a lot faster than you can in nano or a gui editor. It's far more powerful.  Just wait until you have to search and replace globally. 
3. It's not that hard, i figured  it out in one week's worth of usage.  Look at vimtutor, it'll help. 
These tutorials may help: [http://ubuntuadministrator.com/?tag=vi](http://ubuntuadministrator.com/?tag=vi) as well
4. As to why vi is installed, is well, it's on every single linux system known to man.  vi is small enough to fit on a boot disk and is great for recovery purposes back in the day of floppies.  When you work with a large network of unix machines over ssh shells, you can count on the same text editor being on every single system, and that's vi or vim.  That's not the case with nano, pico, or others.
5. The man pages aren't full vi/vim.  You can drop into vim from them, I think, just as you can with less/more. But i don't get what's so complicated about man pages.  Press 'q' to quit and use your arrows to scroll.
6. If one was to consider themselves just a run of the mill desktop user, why aren't you using something like gedit, leafpad, mousepad,?

Note the date on the post you just replied to. I'm reporting for necromancy.

---

### Post by euphemus on 2009-04-28
> **mentallaxative said:**
> Thread necromancy + flamebait = pointless
What is "Thread necromancy"; and don't be patronizing! - I may be new to Ubuntu but I'm not so new as to tolerate rudeness! All too often techy-heads, and anyone else who gets involved substantially in a specialized subject, bully n00bs - its unnecessary and speaks volumes as to the nature of one's character.

---

### Post by frenkel on 2009-04-28
Why are you brining up this topic? You want to flame on?

---

### Post by euphemus on 2009-04-28
> **frenkel said:**
> Why are you brining up this topic? You want to flame on?
Is that directed at me? And can you speak a known language - what does"flame on" mean? Sounds agressive.

---

### Post by frenkel on 2009-04-28
Yes, it was directed at you. This thread was more like a flame-war (search that up on google, it means something like a war with words). Nobody posted to it for almost a year, and then you posted to it again, and people will get into fights again. Why did you do that?

---

### Post by euphemus on 2009-04-28
> **frenkel said:**
> Yes, it was directed at you. This thread was more like a flame-war (search that up on google, it means something like a war with words). Nobody posted to it for almost a year, and then you posted to it again, and people will get into fights again. Why did you do that?
Well - I was originally having some trouble with (god knows what) and that involved vim to an extent - so I was looking for posts about vim - I saw this thread and couldn't have agreed more with the original psot and gave my opinion.

This time around I was reviewing previous posts - seeing what has been added - is there anything useful? - I do this from time to time: I usually read the whole thread first time and its like catching up on a serial. I noted "necromancy" several times - not sure what that means - so I asked (I thought I was asking the original poster).

I now, after fending off accusations of aggression, am informed that it is posting to old threads (loving the dead). "Flaming on" is deliberately stiring up trouble. I meant not to do either.

As I think about this, I suspect that you along with others are viewing a new-post bulletin board, I never do this: I search for specific topics and post there. I don't think I've ever been to the main bulletin board here.

I will be more careful about the age of threads: in my ignorance I thought a thread that should not be used would be closed in some way.

Thank you for the answer &#8211; I'll avoid old threads and personal opions in future.

---

### Post by frenkel on 2009-04-28
Ok. Thanks. I wish everybody would be so smart as you :)

---

### Post by Perfect Storm on 2009-04-28
Thread closed.

---

