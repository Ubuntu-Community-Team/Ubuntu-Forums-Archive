---
title: "How'd you get so &quot;command line&quot; savy?"
date: 2005-10-21
forum: The Cafe
---

### Post by mojogil on 2005-10-21
This is as basic as a question can get but I really want to know how best to start learning Linux.
Is the command line operation in linux a "programming language"?  
I guess I'm wondering if someone like me who has only worked with graphical interfaces would benefit from learning a certain programming language that would make command line operation a lot simpler.  
I think that I represent a growing number of users who are trying to switch but are really confused by the terminal and command lines.  What does the / or \ mean etc?
Thank you,
Gil

---

### Post by migueljacq on 2005-10-21
I guess you could say that it's a programming language - it recognises Unix commands.
Whilst distributions like Ubuntu certainly push the GUI, I certainly consider the command line to be important. Sometimes you might find yourself in need of doing some modifying of files or whatever that is frankly easier to do in the command line in terms of speed etc.

some basic commands are as follows:

cd (same as windows, open a folder)
the / relates to folders in a tree sequence i.e

cd /home/joe/music

will open the music folder in joe's directory

cp = copy, i.e

cp /home/joe/music /home/bill/music

will copy the entire music folder from joe and make a new directory 'music' for bill and copy the data in there.

rm is remove or delete

mkdir creates a directory i.e

mkdir /home/joe/music/new_music

rmdir removes directories

there are some more advanced commands like permission changing (chmod, chown etc). I don't want to say 'google it' but I know that there are pages on the net devoted to glossary of linux commands.

---

### Post by aysiu on 2005-10-21
I don't in the least bit consider myself "savvy" when it comes to the command line, but what little I do know, I know from cutting and pasting commands and seeing what those commands do. It's not a programming language, as far as I know. It's like DOS but different.

---

### Post by matthew on 2005-10-22
Some things that will help from a current learner (been using linux since April 2005).

1. Lots of practice. Don't let yourself be intimidated or fear the command line, embrace it and try to conquer it.

2. [https://wiki.ubuntu.com/BasicCommands](https://wiki.ubuntu.com/BasicCommands)

3. [Learning the Bash Shell]("http://www.amazon.com/exec/obidos/tg/detail/-/1565923472/qid=1129953720/sr=8-2/ref=pd_bbs_2/002-5332088-0067241?v=glance&s=books&n=507846")

4. [http://www.ss64.com/bash/](http://www.ss64.com/bash/)

5. [GNU Bash]("http://www.gnu.org/software/bash/bash.html")

6. [Bash Reference Manual]("http://www.gnu.org/software/bash/manual/bashref.html")

I have not mastered all of these, but they are a great way to get started. There is also a great [Debian quick reference card]("http://people.debian.org/%7Edebacle/refcard/") in pdf format that you can print out with a list of commands available that I recommend highly.

---

### Post by Manny C on 2005-10-22
I'm with Matthew. Practise. And I don't consider myself command line savvy yet.

---

### Post by Dr. Nick on 2005-10-22
Im not very savy either, learned alot from copy/paste and the terminal(bash) history of previous typed commands. Knowing  basic command line is nice if you break Xorg and are stuck in a command line to get it fixed, it also comes in handy if you use other distros of linux that are not as gui oriented or just rearranged making it a bit confusing, Gui changes some between distros, Basic command line doesnt :)

The best approach may be to learn some basics now then learn specifics as you need them

---

### Post by Brunellus on 2005-10-22
practice, practice, practice.  Also, read a good book-- I got "How Linux Works:  What Every Superuser Should Know" (No Starch Press).  

The links mentioned in matthew's post, above, are all excellent resources.   The most important ingredient, however, is your commitment.  

I'm a big believer in the "leap into the deep end and learn to swim" method for this.  Hit CTRL+ALT+F1.  That will get you to a text mode console--no gui!  Learn to work there.  If you chicken out, you can always hit CTRL+ALT+F7 to bring you back to your graphical environment.

I use the virtual consoles to do nearly all of my commandline work, rather than opening up gterm windows in gnome.  it's just as handy, and the console font is a lot bigger & more legible than the tiny gterm window.  And I can still listen to my music (by running rhythmbox in the graphical session, and working in the text one...so long as I don't mess with the sound outputs, the music still plays while I tinker in textmode)

Good luck and have fun!

---

### Post by bored2k on 2005-10-22
I'm not savvy, but I do know that reading forums and websites helps like nothing else.

---

### Post by phen on 2005-10-22
i think the posts above say everything! just practise, and work in the commandline instead of drag and drop things in gnome. imagine now desktop environment would exist :-)

some tips:

using "|" with "grep" is like searching for something. example:

lspci | grep Audio

executes 2 commands: lspci lists all pci devices, grep finds the lines with "Audio".
type lscpi to see the difference.

lspci >> output.txt pipes the output of the command into a file. you can also pipe it to a printer. you can pipe it everywhere you want

use "man <command>"

to get help for the command.

have fun!

---

### Post by Riverside on 2005-10-22
The real fun of Linux comes when one becomes familiar with the command line.  Aside from Firefox, I don't really use any graphical applications at all, and I came from a Windows background having only started using Linux in 2002.  Now, I run the world's most powerful email client (Mutt), which helps me to deal quickly and effectively with between 300-3000 emails per day (really!) at work, the slrn newsreader which makes reading text Usenet a pleasure (a graphical Usenet client such as Pan is more useful for binary Usenet admittedly), and all my system administration and configuration is done at the command line.  Both Mutt and slrn are console applications, which I typically run in an xterm window.

O'Reilly books are good to help one learn, such as Running Linux, Linux In A Nutshell etc.

Really though, there is no substitute for practice and experimentation.  Don't be afraid to get things wrong, it will help if you can install Linux on a spare system perhaps where it doesn't matter too much if you hose the wrong set of files etc.  The web is an excellent resource too, there are megabytes of information online concerning Linux command line usage etc.

---

### Post by GreyFox503 on 2005-10-22
try this thread:

[http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)

and this site:

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by doclivingston on 2005-10-22
While knowing lots of commands is okay, the real power of the command line is knowing how to put them together.

[QUOTE=phen]using "|" with "grep" is like searching for something. example:
lspci | grep Audio[/QUOTE]

I'll give a more detailed explanation of what that actually means.

* The "lspci" command prints out the PCI devices on your computer, you can read about it with "man lspci"
* The "grep" command belongs to a large group of commands, called filters, what take some input, and then output something else (based on the input). In particular "grep X" only outputs the lines of the input which have "X" in them.
* The "|" symbol is called a pipe. What it does is connect the output of one command to the input of the next.


Putting all of those, what happens is:
1) the "lspci" command outputs a list of PCI devices
2) that output is send into "grep Audio", which removes any lines not containing "Audio"
3) the output from grep hasn't been told where to go, so it gets printed out.

The result is that you get a list of all your pci audio devices.


If someone given you a complex command, with pipes and everything, the best way of understanding it is to break it into pieces and see what they do individually.

---

### Post by PatrickMay16 on 2005-10-22
I only know a few commands, which I learned by reading around the forums and the man pages.

---

### Post by Kvark on 2005-10-22
The 3 built in help functions come in handy when you are confused about a specific command. For example if you are wondering about the command "grep":

Small: grep --help
A quick reminder for those who already know the command.

Medium: man grep
A manual page that provides an overview of the command. This can serve as a more detailed reminder or as a general introduction to a new command.

Large: info grep
A lot of info broken down into several pages. This is what you will want to read to learn a command.

---

### Post by Master Shake on 2005-10-22
[QUOTE=GreyFox503]

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)[/QUOTE]


I Definitely heartily second this site!

It has an excellent tutorial that covers the commands and file system organization, has a section on bash programming, and an excellent refrence section!

---

### Post by Stormy Eyes on 2005-10-22
[QUOTE=mojogil]This is as basic as a question can get but I really want to know how best to start learning Linux.
Is the command line operation in linux a "programming language"?  [/QUOTE]

The shell can be used as a programming language to write "shell scripts" (think of 'em as batch files if you're used to batch files on Windows or DOS). It's primarily a command interpreter.

Here is a tutorial for [using the command line.](http://www.hypexr.org/bash_tutorial.php)

Here is an [Introductory shell programming HOWTO.](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

As to your question about how I got so savvy with the command line: years of practice. I ran Gentoo for a couple of years, FreeBSD for several months, and Slackware for half a year. I had no choice but to learn to love the shell.

---

### Post by mojogil on 2005-10-24
WOW!  Thank you all for the great advice and examples.  I do read this and other forums and have a couple of books, "Linux For Dummies" and "Linux In A Nutshell". I'm in the process of making sense of it all.  I'm really excited to learn how to work with command line!
Thanks,
Gil

---

### Post by brentoboy on 2005-10-24
I would welcome a "C" or "php" or "javascript" syntax for the shell at least then, if you learn one, you have a headstart on the other.

copy("/home/me/some-file", "/home/me/some-other-file");

I realize that there are lots of command line switches that are available that would be hard to implement in this way, but if program functions can limit themselves to predicable parameters, certainly a command line could handle it.

Even if php commands were executable from the command line

echo gethostbyname('www.ubuntu.com');

not that php is easier than the command line, but both are technically just different syntaxs (language layouts) for doing things, and why not learn both at the same time.  Then, The more you know the command line, the more you would know about programming.

just an idea - havnt had time to really think on it.

apt_get_install("build-essential");
apt_get_dist_upgrade("breezy");

call me a diehard developer, but that would be really sweet.

---

### Post by Ride Jib on 2005-10-24
I learned from a couple of different methods. 

1. I went to college. All of the department computer were solaris machines, so I was forced to learn it.

2. I read the book "Unix in a Nutshell" which was fantastic, and I still use it as a reference book 5 years later.

3. Search University websites. Many schools have a class using unix, and frequently post their class notes online. 

4. Try doing everything with the command line first. If you really can't figure it out, then go to the GUI applications.

---

### Post by matthew on 2005-10-24
[quote=brentoboy]I would welcome a "C" or "php" or "javascript" syntax for the shell at least then, if you learn one, you have a headstart on the other.
[/quote] Have you looked at tcsh as a shell? I have heard it has much more of a C type syntax. I hae never used it, but I took a look and it is in the repos:
```
sudo apt-get install tcsh
``` Here's an introduction...I'm sure a quick Google search would elicit more
[http://www.tcsh.org/Welcome]("http://www.tcsh.org/Welcome")

---

### Post by Brunellus on 2005-10-24
if I'm not mistaken, shells of this nature are available, if you want them.

It's been enough for me to learn bash, lately, though, without having to worry about different shells.  apparently, Microsoft's monad (windowless, get it? haahahaa! yeah.  ahem.) shell, MSH, has syntax like this.

---

### Post by brentoboy on 2005-10-25
[QUOTE=matthew]Have you looked at tcsh as a shell? I have heard it has much more of a C type syntax. I hae never used it, but I took a look and it is in the repos:
```
sudo apt-get install tcsh
``` Here's an introduction...I'm sure a quick Google search would elicit more
[http://www.tcsh.org/Welcome]("http://www.tcsh.org/Welcome")[/QUOTE]

I'll check it out, that is quite interesting actually.  But the more I thought about it, the more I would really like it to be like PHP becuase PHP is more flexible, and strings are "normal" things in php instead of closely watched memory leak hazards - and command lines are mostly strings.

I'll have to look, it is a very compelling idea.
If you are going to learn one cryptic language, why not make it one you can use elsewhere?

---

### Post by Mr_J_ on 2005-10-25
Actually from many places, but the reason to learn those commands is breaking stuff.
Most Learning Linux manuals are pretty nice to start learning.
Mainly as a crutch, but not really in depth. Usually I find them lacking.
Have 2 myself, and the best book I have fits in my pocket and it's from O'Reilly.
"Linux in a Nutshell" is a good place to learn command line, and a good place to fall back on.

Breaking X is also nice to learn.
Sometimes instead of opening a console in X you could use those outside it.
Restricts some stuff and is accessible threw Ctrl+Alt+F1-F8.
F1 to F6 are system consoles, F7 is Xorg, F8 is the boot screen.

I'm not very "savvy", but I'm not frightend of the console either.

---

### Post by dbw on 2005-10-25
I have been learning some Linux over the past 3 months.  I would recommend:
 [http://www.mhpcc.edu/training/vitecbids/UnixIntro/UnixIntro.html](http://www.mhpcc.edu/training/vitecbids/UnixIntro/UnixIntro.html)
Especially the summary of basic commands.  I feel like this + man + google should get you fairly proficient in a short while.

 oh actually.  I forgot the most important bit:
   Type some junk into that command line, and see what pops out.

---

