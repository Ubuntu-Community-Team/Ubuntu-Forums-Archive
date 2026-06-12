---
title: "text editor of choice for python?"
date: 2009-08-11
forum: The Cafe
---

### Post by bodyharvester on 2009-08-11
i just use gedit at the moment, are there any text editors made with python in mind?

im still a beginner, trying to sort out a ceaser cipher now, i dont mean a text editor which points out my mistakes just one which is more convenient

thanks

---

### Post by cmargolin on 2009-08-11
Try gvim, which has syntax coloring for many languages.

---

### Post by JT9161 on 2009-08-11
Make one in Python

---

### Post by BloGTK on 2009-08-11
I use gedit as well. It's not perfect, but I haven't really found anything that works better for my needs.

---

### Post by RiceMonster on 2009-08-11
> **cmargolin said:**
> Try gvim, which has syntax coloring for many languages.

If you're going to do that, you may as well learn regular vim (which I prefer).

---

### Post by hessiess on 2009-08-11
Learn Vi, Modal editing is way more effective.

---

### Post by bodyharvester on 2009-08-11
i think ill learn Vi, then make one ;)

EDIT: thanks, y'all

---

### Post by Barrucadu on 2009-08-11
The text editor which you are most comfortable with is the best one.

---

### Post by RiceMonster on 2009-08-11
> **bodyharvester said:**
> i think ill learn Vi, then make one ;)

EDIT: thanks, y'all

Before learning vi/vim I suggest typing vimtutor into a terminal and following it through. It'll help get you started.

---

### Post by bodyharvester on 2009-08-11
> **RiceMonster said:**
> Before learning vi/vim I suggest typing vimtutor into a terminal and following it through. It'll help get you started.
 
thanks, i couldnt find vi in the add/remove thing, silly me :p

---

### Post by RiceMonster on 2009-08-11
> **bodyharvester said:**
> thanks, i couldnt find vi in the add/remove thing, silly me :p

Vim is pretty much the version of vi used on most Linux distrobutions. I don't think you get the full version on Ubuntu by default, I think it's vim-tiny.

So, to be sure, you can install it:
```
sudo apt-get install vim
```

---

### Post by Viva on 2009-08-11
Try [geany]("apt:geany") or [drpython]("apt:drpython").

---

### Post by tc3000 on 2009-08-11
emacs. ;)

---

### Post by hessiess on 2009-08-11
install vim-full

then run

```

vim

```

or

```

gvim

```

---

### Post by dwanders on 2009-08-11
jedit from a thumb drive already configured to run on whatever PC I plug it into or Komodo Edit 5 (free version) for permanent editing of anything on a home or Work PC. 

I would also agree with whoever said the editor you like is the one to use ;)

---

### Post by bodyharvester on 2009-08-11
> **dwanders said:**
> jedit from a thumb drive already configured to run on whatever PC I plug it into or Komodo Edit 5 (free version) for permanent editing of anything on a home or Work PC. 

I would also agree with whoever said the editor you like is the one to use ;)

well im using the tutor of vim in the terminal and im feeling better about this one...

by thumb drive do you mean a usb stick? if i could put vim on a 128mb and store my .py files on there that would be cool. how did you install it on the drive?

---

### Post by lykwydchykyn on 2009-08-11
> **bodyharvester said:**
> i just use gedit at the moment, are there any text editors made with python in mind?

im still a beginner, trying to sort out a ceaser cipher now, i dont mean a text editor which points out my mistakes just one which is more convenient

thanks

Instead of just tossing out the name of my personal favorite text editor, can I ask what you feel gedit DOESN'T offer you in the way of python development?  

Knowing that would help us to give you useful advice in a new text editor, rather than just having everyone sound off about how awesome they think vim/emacs/whatever is.

There are editors aimed specifically at Python, like Eric, idle, or drpython.  Mostly they're only useful if you want or need some of the python-specific features they offer.

---

### Post by doas777 on 2009-08-11
geany in ubuntu, notepad++ in win.

Personally I despise anything even remotely related to vi.
when I first started learning it, we were ssh'ing into a unix box running ksh as the standard shell

lets say I wanted to go back one space, and add the letter 'a' before the one i just typed. I would have to enter these keys:
```

'esc' ':' 'k' 'i' 'a'
```all that, to accomplish 2 keystrokes worth of work.
in case you are wondering, Esc: puts you into nav mode, k says move one space left, and i incicates that i want to insert (versus replace, overwrite, and append ).

in order to backspace, we had to use ^H.

yet somehow VI is the most efficient editor in the world according to some folks.

---

### Post by dwanders on 2009-08-11
lykwydchykyn - is right on the money - that would be your best approach. 

As for the USB stick stuff, I wanted an editor that I could set up once and use anywhere (so I did not have to set it up again, and again at each PC I used it on). In fact I have found it very useful to do this with some of the App's I use often - which also drove my choice of Java based applications like jEdit, yEd, & jFig all on a 16gig Flash Voyager. 

jEdit is a very good editor but it is just that a general editor that can do many different Lang's, yEd is a wicked flow chart app, and jFig is the java version of Xfig. Because they are Java based, as long as there is a Java Runtime on the PC I am using I am good to go (most PC's these days). I tend to use Komodo when I am on a permanent PC cause I like its auto complete but it is kind of a hog - I still find myself using jEdit more than anything cause I can use it anywhere - only wish ddd was written in Java as well!

But I still agree with lykwydchykyn - (man thats a tough one to type) - determine your needs then go from there - mine was to be portable.:P If I was looking for something to edit config files when my servers was crashed - you cannot bean vi - but that is the only time I would torture myself with that editor :lolflag:

---

### Post by dwanders on 2009-08-11
Oh yea - and it does work in Windoze and Linux the same with this set up (another one of my deciders) - biggest problem I have had using jEdit between the two is going from C:\ to / which can cause it to error about the path not being available any more! Sweet!

---

### Post by jordilin on 2009-08-11
I use mostly vim or geany. Just grab one and be happy. :guitar:

---

### Post by donkyhotay on 2009-08-11
I use gedit with the extra plugins installed from the repos. It does everything I need for coding python.

---

### Post by CJ Master on 2009-08-11
> **donkyhotay said:**
> I use gedit with the extra plugins installed from the repos. It does everything I need for coding python.

+1. Gedit is the best python editor out there for me. Syntax highlighting and auto-indent. I only wish someone would extend it a bit more to including debugging.

---

### Post by Jimleko211 on 2009-08-11
Geany is a great app.  Kate is another great text editor, if you don't mind using KDE apps.

---

### Post by swoll1980 on 2009-08-11
I like Idle. Call me crazy.

---

### Post by Simian Man on 2009-08-11
> **doas777 said:**
> lets say I wanted to go back one space, and add the letter 'a' before the one i just typed. I would have to enter these keys:
```

'esc' ':' 'k' 'i' 'a'
```all that, to accomplish 2 keystrokes worth of work.
in case you are wondering, Esc: puts you into nav mode, k says move one space left, and i incicates that i want to insert (versus replace, overwrite, and append ).

in order to backspace, we had to use ^H.

yet somehow VI is the most efficient editor in the world according to some folks.

Have you used vim in the last 10 years??  You do not have to do all of that.  In order to add a before the letter you've just typed, just press the left arrow and then the 'a' key.  Same as you would for any other text editor.  Those more arcane key commands date back to when people used teletypewriters and vi couldn't assume a user would have arrow keys.  The arrows, insert/replace, backspace and delete keys all work as you'd expect.

The only time I really leave insert mode is when I want to do something slightly more complicated like copy/cut/paste sections of text, search and replace, save and quit or run shell commands.  Being able to use regular key combinations to do these things rather that Ctrl-Alt* type commands is what makes vim so efficient.

---

### Post by Daveski on 2009-08-11
> **CJ Master said:**
> +1. Gedit is the best python editor out there for me. Syntax highlighting and auto-indent. I only wish someone would extend it a bit more to including debugging.

I like gedit for Python coding - but I want code folding to simplify things. Anyone recommend something similar to gedit, or even if there is a plug-in or some setting I have missed?

---

### Post by lykwydchykyn on 2009-08-11
> **Daveski said:**
> I like gedit for Python coding - but I want code folding to simplify things. Anyone recommend something similar to gedit, or even if there is a plug-in or some setting I have missed?

kate and geany both have code folding.

---

### Post by Mateo on 2009-08-11
the lack of a good ide solution is one of the major reasons why i've never bothered with python.  that's my opinion, of course.

---

### Post by lykwydchykyn on 2009-08-11
> **Mateo said:**
> the lack of a good ide solution is one of the major reasons why i've never bothered with python.  that's my opinion, of course.

I learned python in spite of it, but I won't dispute the point.  I think I've tried about every python IDE out there, but they all either lacked the features I wanted, or were just buggy out the wazoo.  Eric came the closest, but half the time I can't even get it run (case in point, I just tried to run it after not using it a few weeks, and it's crashing with an import error).

It's a shame, really, because Python could be a lot more effective with a really killer IDE.

---

### Post by Mateo on 2009-08-11
The Wing IDE does seem pretty nice.  Check out it's videos on the site.  Looks pretty robust, I'm going to try it out.

---

### Post by Jimleko211 on 2009-08-11
> **lykwydchykyn said:**
> I learned python in spite of it, but I won't dispute the point.  I think I've tried about every python IDE out there, but they all either lacked the features I wanted, or were just buggy out the wazoo.  Eric came the closest, but half the time I can't even get it run (case in point, I just tried to run it after not using it a few weeks, and it's crashing with an import error).

It's a shame, really, because Python could be a lot more effective with a really killer IDE.
Did you try SPE?  I've tried it and it seems really cool..only thing I couldn't get was for my programs to accept input INSIDE of the IDE.  But I might try that again now that I have a new distro aside from Ubuntu.

---

### Post by CJ Master on 2009-08-11
> **Mateo said:**
> The Wing IDE does seem pretty nice.  Check out it's videos on the site.  Looks pretty robust, I'm going to try it out.

It's very nice, but I quit using it because it's propriety. Gedit is very nice as well, it just lacks a debugger..

---

### Post by days_of_ruin on 2009-08-11
> **bodyharvester said:**
> i think ill learn Vi, then make one ;)

EDIT: thanks, y'all

btw you should add this to your ~/.vimrc
```
set tabstop=4
set softtabstop=4
set expandtab    
set autoindent  
set shiftwidth=4    

```

This will allow you to have 4 space tabs that are not really tabs, they are spaces which is the python convention.

---

### Post by Firestem4 on 2009-08-11
> **Jimleko211 said:**
> Geany is a great app.  Kate is another great text editor, if you don't mind using KDE apps.

In my opinion Kate is an excellent (GUI) text editor. One of the nice features I like is shell integration, syntax highlighting (for literally dozens of popular programming languages.) One of my hardware buddies was surprised that KATE handles VHDL syntax. 

Block editing is also a nice feature that KATE handles.

---

### Post by lykwydchykyn on 2009-08-11
> **Mateo said:**
> The Wing IDE does seem pretty nice.  Check out it's videos on the site.  Looks pretty robust, I'm going to try it out.

I would hope so, for the price.  You don't even get code folding unless you pay for the $180 version.

@Jimleko221:  I tried SPE a while back.  I remember really liking it until it started crashing on me.  Can't remember if it caused KDE to die or X to lock hard, but it was one of the two and happened often.

Maybe that's fixed now...

---

### Post by Eviltechie on 2009-08-12
I prefer nano if I don't have a gui.

---

### Post by bodyharvester on 2009-08-12
Wow...there are so many text editors. Thanks for all the replies, i didn't know gedit had plugins!:confused:

well, im no closer to sorting out the ceaser cipher program i mentioned in my first post.

just so we're clear, i don't believe another text editor will make me better with python, just that there are so many its easier if everyone gives a comment about the one that they are most familiar with and find suit them best

thanks again

---

### Post by t0p on 2009-08-12
> **swoll1980 said:**
> I like Idle. Call me crazy.

+1. IDLE FTW, re Python.

---

### Post by moster on 2009-08-12
Sorry for bustin... How do I actually design window with buttons and usual stuff? I come from visual studio and that was easiest part there, here I just cannot figure that out.

---

### Post by lykwydchykyn on 2009-08-12
> **moster said:**
> Sorry for bustin... How do I actually design window with buttons and usual stuff? I come from visual studio and that was easiest part there, here I just cannot figure that out.

 1. Pick a toolkit that has a visual GUI editor
 2. Find a python editor with integration for said GUI editor
 3. Use and enjoy.

That said, I don't think python has anything quite as straightforward as Visual Studio, which is too bad because it would make python rock and roll over Visual Basic if it did.

I used Eric4 with my last GUI project, it has integration with QT designer.  It took a good bit of reading the manual to make it work right, though.

Stani's python editor has wxglade integration, I don't know if there's an editor with ordinary glade integration.

---

### Post by Eisenwinter on 2009-08-12
> **RiceMonster said:**
> If you're going to do that, you may as well learn regular vim (which I prefer).
+1, Vi(m) is good.

As far as a "Python specific" editor, I recommend SPE - Stani's Python Editor.

It's also written in Python itself.

To get it with subversion:
```
svn checkout svn://svn.berlios.de/python/spe/trunk/_spe
$ python SPE.py
```

---

### Post by Kazade on 2009-08-12
After trying Geany, GEdit, Kate, SPE, Eclipse+PyDev, Vim, Emacs, IDLE, Komodo I've finally settled on NetBeans + NBPython. It's not as resource hungry as Eclipse, and it has all the cool stuff like refactoring (variable/method renaming in Python, bliss!), hints, automatic code formatting (ALT+SHIFT+F formats the whole file), class browser, package browser, etc. etc.

Also, I do work with Java so I can switch between projects without changing the IDE :)

---

### Post by moster on 2009-08-12
> **lykwydchykyn said:**
> 1. Pick a toolkit that has a visual GUI editor
 2. Find a python editor with integration for said GUI editor
 3. Use and enjoy.

That said, I don't think python has anything quite as straightforward as Visual Studio, which is too bad because it would make python rock and roll over Visual Basic if it did.

I used Eric4 with my last GUI project, it has integration with QT designer.  It took a good bit of reading the manual to make it work right, though.

Stani's python editor has wxglade integration, I don't know if there's an editor with ordinary glade integration.
I was expecting something like visual studio from 1997-1998. It seems I expected way too much. Luckily, Python looks very good.

Ok, thanks. :)

---

### Post by Mateo on 2009-08-12
> **lykwydchykyn said:**
> I would hope so, for the price.  You don't even get code folding unless you pay for the $180 version.

Sounds like a pretty fair price, the debugger seems pretty robust.

---

### Post by bodyharvester on 2009-08-12
> **Mateo said:**
> Sounds like a pretty fair price, the debugger seems pretty robust.

from some other posts, a good debugger sounds like something some might be willing to pay for

---

### Post by thisllub on 2009-08-12
> **Kazade said:**
> After trying Geany, GEdit, Kate, SPE, Eclipse+PyDev, Vim, Emacs, IDLE, Komodo I've finally settled on NetBeans + NBPython. It's not as resource hungry as Eclipse, and it has all the cool stuff like refactoring (variable/method renaming in Python, bliss!), hints, automatic code formatting (ALT+SHIFT+F formats the whole file), class browser, package browser, etc. etc.

Also, I do work with Java so I can switch between projects without changing the IDE :)

You can get a vim plugin for NetBeans that gives you most of the editing power of vim in the netbeans ide.

I use NetBeans a little bit but it is a pig on resources.

---

### Post by jpkotta on 2009-08-12
> **tc3000 said:**
> emacs. ;)

I use Emacs, but there are [at least 2 python modes]("http://www.emacswiki.org/emacs/PythonMode").  Personally, I prefer [python-mode.el]("https://launchpad.net/python-mode").  I like how the indentation works, and it is pretty well-integrated with Emacs.

---

### Post by lykwydchykyn on 2009-08-12
> **Mateo said:**
> Sounds like a pretty fair price, the debugger seems pretty robust.

I suppose in some situations it might be worth it.  Personally, I rarely do much more than a few hundred lines of code in Python in any given project, so debugging rarely gets deep for me.

---

### Post by Mateo on 2009-08-12
If you use it for scripting then it's not worth the price, but if you're trying to develop something larger (a database backend project, a web application), I definitely can't live without a visual debugger.

---

