---
title: "Learning Unix, how much is too much?"
date: 2010-07-01
forum: The Cafe
---

### Post by imgx64 on 2010-07-01
A little more than half a year ago, I installed Ubuntu on my computer. The method I used for learning to use it was '*Try out all menus, if all fails, Google it*.' It generally worked fine, especially with the GUI and all, and there are plenty of help sites online. However, the more I use it, the more I get interested in it. And sometimes, solutions on some websites make me feel left out; Even though they worked, I didn't really understand what they did. And these little cryptic one-liner sh/sed/awk/perl/etc commands have some kind of magic in them; Magic I couldn't fully appreciate, and couldn't modify to suit my needs.

So, at some point, I decided to learn the Unix part of Ubuntu (Yes, I know Linux isn't *real* UNIX™. But for my intents and purposes, it's Unix enough.) But before I start learning, I needed to know *what* and *how* to learn. After some extensive (well, sort of) research, I decided to start from the bottom; I would learn Unix the way it was meant to be, Version 7 Unix! I got two books, *The Unix Programming Environment* by Brian W. Kernighan and Rob Pike, and *Unix Programmer's Manual*, the manual for Version 7 Unix. The latter contains two volumes, the first is the man pages of V7 and the second is a collection of papers, essays, and tutorials. It's also [available for free online]("http://cm.bell-labs.com/7thEdMan/"). I also found a [PDP-11 emulator and a running copy of Unix V7]("http://simh.trailing-edge.com/").

Now, I started reading the books and learning, and it has been an enjoyable experience. Suprisingly, not much has changed in over 30 years; Most commands work just like they did on V7. However, while almost nothing was removed, a lot has been added, some as standard additions (added to POSIX,) and some as non-standard extensions. As an example, the sh man page in V7 contains about 3000 words (the biggest man page in V7), the bash man page has 41025. That's over 13 times bigger, and that's without counting the texinfo manual of bash! What's more, I found out that zsh is even more advanced than bash, and has even more features. That is just one example, other commands also had their share of additions and there are also many new commands.

I am facing a dilemma here, I don't know what to learn or where to stop. I have two solutions (plus the gray area in between.) The first solution is to stick with just the basics. The problem with that approach is that I will miss many features that could make my life much easier. Also, I risk not understanding some commands/scripts that other people write, which is the reason I started learning in the first place.

The other solution is knowing no limit, learning every command, reading about every option, trying every feature, exploring every nook and cranny, and maybe even learning perl(which, if the Internet is any indication, is simultaneously the best AND worst solution of any problem.) This is obviously impossible, as it will take an unlimited amount of time. I will also have a problem if I ever had to use a system that doesn't have some of these extensions. Also, if I ever try to help someone, they might not have them (for example, giving a command that works in zsh and not in bash.)

Naturally, a reasonable person would suggest starting with the basic set, and learning the extras gradually as I need them. But even that has problems. First, if I don't know something exists, how can I learn to use it? And second, no manual page or book tells you "this feature is available in bash but not in dash, and zsh does it but using different syntax." Which is really the same problem as with the previous appraoch; When helping others or trying to write portable code, how do I know what works where?

I understand this problem is universal, and it would happen even if I picked up a 'modern' book about Unix in general, Linux, or Ubuntu. So, I am hoping you share your own experiences, how do you manage it? How do you learn about these features? How do you know when to stop learning about one command and its extensions and move on to the next one? And do you have any other suggestions for me? Maybe recommend a good book or website?

Note: in case I wasn't clear enough, I'm not just talking about  the different shells. Even though my examples were mainly about shells, I also have problems with additions to other programs, awk has been extended, sed has been extended, ed has been extended, even cat has been extended, and the list goes on and on.

---

### Post by ubunterooster on 2010-07-01
Suggestion? Seeing OSX _]is_ UNIX, you *might* want to try reading on the Apple OSX's CLI.

---

### Post by lostinxlation on 2010-07-01
it depends on what you do with Unix. Unless you are making living with deeply dealing with Unix, knowing basic stuffs is enough. I have been on Unix for 20 years, but I have never bothered to learn all the commands or features. As long as I know enough of it, learning the rest on the occasion when I need is easy.
Regarding the difference in shell, stick to the shell you like. I ditched Bourne Shell long time ago and I only know csh/tcsh variants and have no problem.

---

### Post by kaldor on 2010-07-01
> **ubunterooster said:**
> Suggestion? Seeing OSX _]is_ UNIX, you *might* want to try reading on the Apple OSX's CLI.

I use OS X. It uses "GNU Bash". Exact same as Linux.

I wouldn't call it "true UNIX". OpenSolaris or *BSD are closer imo.

---

### Post by NMFTM on 2010-07-01
> **lostinxlation said:**
> Regarding the difference in shell, stick to the shell you like. I ditched Bourne Shell long time ago and I only know csh/tcsh variants and have no problem.
I only use Bash and haven't dabbled in other shells out of the fear that if I'm on a computer that's not my own and am asked to do something and installing my preferred shell isn't' an option. I'll have to know Bash anyway, since that's what almost every Unix-like OS ships with.

Of course, you could make that same argument as to why someone should never learn anything except Windows. I don't use 95% of the things that Bash offers though. But I may in the future since I'm going to school to learn about network administration.

---

### Post by Penguin Guy on 2010-07-01
Learn one programming language at a time (good starting languages are [bash]("http://linuxcommand.org/") or [python]("http://docs.python.org/tutorial/")) and once you've got the hang of that, move to another. The more languages you already know, the easier it will be to learn another one.

---

### Post by chessnerd on 2010-07-01
In college this year, in a computer science class on Java programming, we had to learn the Unix/Linux command line (on Fedora Linux). A lot of people in the class didn't like it. I thought it was great.

If you are looking for a place to start, you can start with this -

Attached are the notes that I took in that class. Not all of these are "commands" per-say, for example "^C" (Ctrl-C) is simply entered and it executes.

My note-taking skills are terrible, so I'd suggest you Google the command and/or check the man page for a better understanding. However, if you learn this list you will have a start on learning the Unix/Linux command line. 

Don't forget to learn about the power of [piping]("http://en.wikipedia.org/wiki/Pipeline_(Unix)") as well...

EDIT: Ugh, I forgot how bad I was at taking notes. I just read this over for the first time in a few months and I have no idea how I used this to study! My apologies...

---

### Post by imgx64 on 2010-07-01
> **lostinxlation said:**
> it depends on what you do with Unix. Unless you are making living with deeply dealing with Unix, knowing basic stuffs is enough. I have been on Unix for 20 years, but I have never bothered to learn all the commands or features. As long as I know enough of it, learning the rest on the occasion when I need is easy.

I agree. And since I'm learning it mostly for my own use, I suppose the basics are enough. But there is still the problem, how do I know what to learn if I don't know it exists? :-?


> **NMFTM said:**
> I only use Bash and haven't dabbled in other shells out of the fear that if I'm on a computer that's not my own and am asked to do something and installing my preferred shell isn't' an option. I'll have to know Bash anyway, since that's what almost every Unix-like OS ships with.

I do have the same fear. I think that after learning the basics, I will only learn the extensions that I can live without. For example, use Bash's ctrl-r history search, which is a great convenience but not really necessary. But not use Bash's arrays, which are not supported by simpler shells.


> **Penguin Guy said:**
> Learn one programming language at a time (good starting languages are [bash]("http://linuxcommand.org/") or [python]("http://docs.python.org/tutorial/")) and once you've got the hang of that, move to another. The more languages you already know, the easier it will be to learn another one.

Well, I know some programming, mainly in Java. But this whole *out-of-IDE experience*(excuse the bad pun :roll:) and the dynamic/scripting nature of the shell is somewhat foreign to me.


> **chessnerd said:**
> If you are looking for a place to start, you can start with this -

Attached are the notes that I took in that class. Not all of these are "commands" per-say, for example "^C" (Ctrl-C) is simply entered and it executes.

That list would've been useful when I just started. But now I know quite a bit after reading the books I got (Even though I haven't finished them yet.) But thanks anyway. :)

Also, the last one is wrong.
```
(command; command)      runs two commands at once
```
should be
```
command & command
```

---

### Post by eriktheblu on 2010-07-01
My advice:
Learn the basic syntax of the commands you will use frequently.(cd, cp, rm, chmod)
Learn directory structure, and environmental variables (~,.,..)
**Know how to reference the things you don't use often.**

No expert worth his salt tries to commit everything to memory.

---

### Post by Bachstelze on 2010-07-01
> **kaldor said:**
> I use OS X. It uses "GNU Bash". Exact same as Linux.

I wouldn't call it "true UNIX". OpenSolaris or *BSD are closer imo.

Well, the fact that *you* wouldn't call it UNIX is irrelevant, as is your opinion. The Open Group knows better than you, and has certified Leopard and Snow Leopard as UNIX.

---

### Post by koenn on 2010-07-01
> I agree. And since I'm learning it mostly for my own use, I suppose the basics are enough. But there is still the problem, how do I know what to learn if I don't know it exists?
this is where it gets interesting. 
You've formally learned the basics. What you need next is to develop a 'feel' for the operating system. Reading a bit about design principles and history of unix may help here.

What will happen then is you're able to make leaps, such as

in a point and click environment, I sometimes do such and so operation. It's something those old unix guys probably also needed to do sometimes, but they did not have these GUI proghams  -> how did they do it back then -> google -> learn something new

program bb can be used for a, b, c ... so it would make sense it can also be used to do d and e ... -> so you go check, experiment a bit, and find out  that indeed it can do d and e (and even f, provided  you combine it with some other program). 

You consider: I can send output of a program to my monitor, to a file, to another program. Assuming these are all variations on the same mechanism (which, given the design of unix, would not be unexpected), what would it take to send this output across a network cable, a serial cable, a parrallel cable, an infrared link, USB, ... . 
And, if you really want/need to know, you'll go find out, and you learn something. 

and so on.
So, without explicitly knowing or formally learning, you'll be able to make assumptions (about programs, options, features, ways to accomplish things,...)  and find that those assumptions are true (most of the time).

---

### Post by imgx64 on 2010-07-02
> **eriktheblu said:**
> **Know how to reference the things you don't use often.**

Sometimes, the most simple advice is the most useful. Thanks. :D


> **koenn said:**
> this is where it gets interesting. 
You've formally learned the basics. What you need next is to develop a 'feel' for the operating system. Reading a bit about design principles and history of unix may help here.

What will happen then is you're able to make leaps, such as

in a point and click environment, I sometimes do such and so operation. It's something those old unix guys probably also needed to do sometimes, but they did not have these GUI proghams  -> how did they do it back then -> google -> learn something new

program bb can be used for a, b, c ... so it would make sense it can also be used to do d and e ... -> so you go check, experiment a bit, and find out  that indeed it can do d and e (and even f, provided  you combine it with some other program). 

You consider: I can send output of a program to my monitor, to a file, to another program. Assuming these are all variations on the same mechanism (which, given the design of unix, would not be unexpected), what would it take to send this output across a network cable, a serial cable, a parrallel cable, an infrared link, USB, ... . 
And, if you really want/need to know, you'll go find out, and you learn something. 

and so on.
So, without explicitly knowing or formally learning, you'll be able to make assumptions (about programs, options, features, ways to accomplish things,...)  and find that those assumptions are true (most of the time).

Yep, I think I'm already beginning to see some common patterns.

---

### Post by slooksterpsv on 2010-07-02
Hey I just wanted to say thank you for this post, I've now found my new terminal, tcsh - where it's so much like C/C++ scripts make more sense, I didn't get the:
if

fi

thing, but the tcsh, I've actually been doing fun things like:
```

foreach i ( */*/* )
echo $i >> temp.txt
end

```

so I can see 3 directories deep =D. This is fun =D.

---

