---
title: "What is it about emacs and vi(m)?"
date: 2006-03-23
forum: The Cafe
---

### Post by commodore on 2006-03-23
I'm not a programmer or anything so I don't understand why people talk so much about emacs and vi or vim? What's so special about them? For me they are text editors with lots of unneeded features.

---

### Post by WelterPelter on 2006-03-23
It's one of those things: if you've already bothered to learn them -- which is hard -- they make a lot of stuff very quick and easy. 

Sort of like a computer. A pencil is much easier to use, but once you get the hang of a computer, there's a lot more you can do with it.

---

### Post by briancurtin on 2006-03-23
just to start it off: vi > emacs

---

### Post by oscar on 2006-03-23
emacs > vim

I prefer emacs mainly because it is modeless, I hate having to press Ins and Esc all the time in vim.

This article has a good summary:
[http://www.itworld.com/AppDev/575/swol-1095-software/](http://www.itworld.com/AppDev/575/swol-1095-software/)
(of my opinion)

---

### Post by stoeptegel on 2006-03-23
No please no emacs vs vi offtopic, although it might be hard let's stick to the question: 

They are advanced editor tools, and when you get your hands on using these advanges most people stick to it.

---

### Post by barthel on 2006-03-23
[QUOTE=commodore]I'm not a programmer or anything so I don't understand why people talk so much about emacs and vi or vim? What's so special about them? For me they are text editors with lots of unneeded features.[/QUOTE]

Back in the day when I was young and dinosaurs roamed the earth and the Dead Sea was still sick, most work on Unix systems was still done on the command line--and a lot of people were working on actual terminals. If you ever ran an MS-DOS based PC, you get the idea: you could only run one foreground program at a time.

RMS wrote emacs in lisp to handle basic text editing tasks, but it was extremely extensible and soon had a plethora of optional add-ins that would do nearly any task from within emacs. So even though you were only running emacs in the foreground, you could answer email, compile programs, play games, etc. without closing your emacs session.

There was another editor, ex, which was useful for batch processing edits to text files, but was rather a pain to use interactively (much like the MS-DOS edlin). Vi was a visual editor built upon the powerful ex command set that made interactive use far easier. Vim incorporates several new features to make vi even more useful for various editing tasks.

One other point to keep in mind is that a significant chunk of Unix text editing was related to programming, so one of the key goals of both emacs and vi was to make writing code easier. As a result, emacs and vi (and all their descendants) contain many features that are of little use to an end user.

However, those feature sets were more than adequate to inspire religious fervor among their devotees. (And I won't even delve into the inner schism of emacs vs. Xemacs. ;)  ).

Personally, I've been using vi and vim for years. I wouldn't dream of writing code in anything else. (I had tried emacs first, but the quadruple-bucky commands were too much to remember: Control-Alt-Meta-Shift-x and the like.)

The majority of users will have little need for either emacs or vim, so y'all can use gedit and ignore all us archaeologists playing with our fossils. :D

---

### Post by ComplexNumber on 2006-03-23
[quote=commodore]I'm not a programmer or anything so I don't understand why people talk so much about emacs and vi or vim? What's so special about them? For me they are text editors with lots of unneeded features.[/quote] i think its just personal preference really. i used vi for ages, but i never got used to it. after a while, i switched to a more 'logical' editor that didn't have modes and stuff. some people swear by emacs and vi, but i suppose those same people are the one's who know them and have crossed the 'barrier' in becoming comfortable with their way of doing things. such people, once they've made the transition, rarely go back to using any other editor because, although there is a lot to know and a lot to adjust to, what can be done afterwards using vi/emacs is quite a lot.
i never made that transition because it just doesn't tie in with my way of working. i work best with lots of small applications that get the job done rather than having a large and complex application that can do a multitude of tasks. maybe it suggests that i'm closed minded in that respect because anyone can get accustomed to anything if they really want to....it just seemed like more effort that its worth to do so.

---

### Post by eltaito on 2006-03-23
barthel- wow...that was a great explanation.  Didn't know a lot of that stuff.  But to get back on topic with the post....I use vi on occasion...it is absolutely wonderful to use once you get the hang of it (got one hell of a steep learning curve), but like everyone else is saying, emacs & vi aren't really necessary for most of us.  If I'm going to edit a text file, more often than not I'm using something simple like gedit instead of dealing with a heavier editor

---

### Post by taurus on 2006-03-23
When I first got into Unix, SunOS 4.1, long after the dinosaurs went kaput, there was only one text editor and it was vi.  Later, we have jove (smaller version of emacs) and emacs on the machine when we upgrade it to SunOS 4.3 but I always stayed with vi and have been vi since then...

---

### Post by ssam on 2006-03-23
when i edit files with gedit/nano they stop working.

but its probably because i leave
```
:wq
```
in them

:-)

when will i learn.

emacs is very much part of the gnu history. there was a good article in linux user and developer about it a few months ago. [http://www.linuxuser.co.uk/content/view/80/35/](http://www.linuxuser.co.uk/content/view/80/35/) . i still have not tried it though. its more like a desktop than a text editor, you can use it for email and everything.

---

### Post by mcduck on 2006-03-23
[QUOTE=barthel]...[/QUOTE]
That was great explanation.. And I had completely forgotten about edlin :D (Not so sure if remembering it again is a good thing)

---

### Post by Typhoon on 2006-03-24
Although emacs is usually thought of as a programmer's editor, I find it the best for my particular task: writing books. I write legal textbooks which have some requirements that are difficult to satisfy: there must be a table of cases, a table of statutes and a normal index as well. A high level of consistency in citing other works is required.

I have found nothing that does this better than using emacs together with the support software and Latex. Three indexes, consistent cross-referencing and citation. Nothing like it!

Typhoon

---

### Post by commodore on 2006-03-24
I don't think I am going to learn either of them if they are so big. Why does anyone have to type that much anyway to need such features? And if they do need then there's OpenOffice.org and Scribus. I think I'll just use gedit and nano.

---

### Post by dcraven on 2006-03-24
This applies to both Vim and Emacs, but Vim is my personal preference. What I like about it goes beyond the power featured out of the box. These things are almost infinitely extendable. I recently wrote a very small Vim script in Python that sends highlighted text to a pastebin of choice. Not only that, but it optionally sends the newly created URL to a Gajim contact of my choice or the currently focused IRC channel in xchat-gnome using DBus. All of this in just over 100 lines of code. This is a tribute to Python and the related programs mentioned above as much as it is to Vim though.

That's just one small example of the useful things that you can make these things do. It's not necessary, of course, since you can use the normal pastebin.com web interface, copy the URL and paste it into a Gajim/IRC conversation pretty easily as well. It sure does make things quicker and more convenient though.

Generally once learned, both of these editors are very powerful. If you just edit a simple config file or two once a week or something it's probably not worth the effort since you'll forget how to use them between sessions. However, Vim is easily my most used application and I almost always have at least one session of it open at a given time be it programming, document writing (LaTeX), or configuration files. In this case I would argue that it is worth the effort required to choose one and learn to use it properly. I promise it will pay off in the long run. I get asked this question a lot actually when people see me using it so much. The benefits are more difficult to explain than you would think because to most people, "It's just a bloody text editor.".

Cheers,
~djc

---

### Post by kabus on 2006-03-24
> I don't think I am going to learn either of them if they are so big.

You don't learn all the commands and you don't learn them all at once.
From Bram Moolenaar's (Vim developer) [Seven habits of effective text editing]("http://www.moolenaar.net/habits.html") :

> Learning to drive a car takes effort. Is that a reason to keep driving your bicycle? No, you realize you need to invest time to learn a skill. Text editing isn't different. You need to learn new commands and turn them into a habit.

On the other hand, you should not try to learn every command an editor offers. That would be a complete waste of time. Most people only need to learn 10 to 20 percent of the commands for their work. But it's a different set of commands for everybody. It requires that you lean back now and then, and wonder if there is some repetitive task that could be automated. If you do a task only once, and don't expect having to do it again, don't try to optimise it. But you probably realize you have been repeating something several times in the last hour. Then search the documentation for a command that can do it quicker. Or write a macro to do it.  When it's a larger task, like lining out a specific sort of text, you could look around in newsgroups or on the Internet to see if somebody already solved it for you.

The essential basic step is the last one. You can think of a repetitive task, find a nice solution for it and after the weekend you forgot how you did it. That doesn't work. You will have to repeat the solution until your fingers do it automatically. Only then will you reach the efficiency you need. Don't try to learn too many things at once. But doing a few at the same time will work well. For tricks you don't use often enough to get them in your fingers, you might want to write them down to be able to look them up later. Anyway, if you keep the goal in view, you will find ways to make your editing more and more effective.

---

### Post by IYY on 2006-03-24
> I don't think I am going to learn either of them if they are so big. Why does anyone have to type that much anyway to need such features? And if they do need then there's OpenOffice.org and Scribus. I think I'll just use gedit and nano.

The reason is simple: to use as few keystrokes as possible, to move your hands as little as possible, and to do things automatically without thinking about them. For example, in vi, you never have to use the arrow keys. This is a big plus since every time you use these keys (or even worse, the mouse), you make a motion of your hand. This is bad for your wrists and takes time.

---

### Post by commodore on 2006-03-25
Ok, I'm starting to understand now, thanks everyone.

---

### Post by jnoreiko on 2006-03-25
Some people are just masochists.

---

### Post by bogoliubov on 2006-03-25
Emacs is really a part of the GNU and Opensource history. Also both these programs have been around for very long but are still used. For instance Emacs on my iBook is version 22.0.5 !! 

Personally I use emacs for writing tex stuff. At work I use vi/vim alot, since I often have to use ssh to log in to different computers at work, and then a text-based editor is a bit faster.
Also, it really is good to know the basics of one of these, because at some point one is bound to crash the X-server :)

---

### Post by Stormy Eyes on 2006-03-25
[QUOTE=eltaito]If I'm going to edit a text file, more often than not I'm using something simple like gedit instead of dealing with a heavier editor[/QUOTE]

Believe it or not, vi is actually lighter in terms of resource consumption than Gedit. Also, it's handy to use when you need an editor but haven't got X configured, or have broken X by tinkering with the config files. I use it all the time both at work and a home, not just for programming, but for doing websites ([my site is done with Vim](http://www.starbreaker.net)) and writing as well. 

Believe it or not: all of the love letters I write to my wife were done with vi and formatted with LaTeX.

---

### Post by Stormy Eyes on 2006-03-25
[QUOTE=jnoreiko]Some people are just masochists.[/QUOTE]

Dude, if I was a masochist, I'd use Windows at home.

---

### Post by eltaito on 2006-03-25
haha....I definately see a few benefits to using vi or emacs....back when I first started using Linux (only about 7 months ago) i learned some vi basics just because......I still use it from time to time.....maybe I'll try to use it more, for some reason using vi just feels right....maybe because I see it as so very "un-windows-like" and you have the potential to get a lot done faster

---

### Post by commodore on 2006-03-25
One thing I don't like about both emacs and vim is that they don't have the regular text editing cursor. But that's probably because I'm too young :D. 

When prefering Vim over Emacs I feel sinned because Emacs is really a part of GNU :)

---

### Post by ow50 on 2006-03-25
The reason I actually started using Vim instead of Gedit in the first place was that I wanted to use different indentation for different filetypes and I got tired of changing the indentation setting in the Gedit prefrences dialog. Vim makes it very easy to define per-filetype settings, be it indentation, compiling, running, plugins or whatever else.

Vim and Emacs are both somewhat ancient console editors that have never quite well adapted to the modern GUI age. Vim is only now about to get tabs and Emacs is about to get text anti-aliasing. Both apps got their own weird ways of using a clipboard. Both are lacking good GUI design (just try to exit the Emacs GTK2 GUI with unsaved changes and note the dialogs.)

Luckily, at least Vim's (G)UI is very customizable. You can set up a bunch of "normal" keyboard combos, such as Ctrl+S and Ctrl+Q so that you don't have to switch between modes just save the file. You can configure Vim to use Ctrl+[XCV] for the global clipboard. You can choose not to load the default menu and just build your own. After a fair amount of work GVim is an excellent editor. It's a matter of opinion how much you'll want to customize, but at least some elementary annoyances you'll have to fix in your .vimrc if your local (debian) packager didn't already.
```
set nocompatible
syntax enable
filetype plugin indent on
```

---

### Post by majikstreet on 2006-03-25
Emacs can do everything...
Vi(m) is lighter and for me, get's the job done better. Probably because when I first used linux I did most stuff in the CLI.. and vi(m) came preinstalled so it was easy :D so now I'm used to it.. this thread made me go and try emacs gtk snapshot again... I did the tutorial.. I am too used to doing "ESC" then "ZZ" to save.. lol and "INSERT" to start typing - I actually tend to do insert when I work with nano lol.. but with vi(m) it is kinda easy to just do insert and do something else and forget that you are still in insert mode and hit it again and go into replace mode.. lol.

---

### Post by neoflight on 2006-03-25
[QUOTE=commodore]I'm not a programmer or anything so I don't understand why people talk so much about emacs and vi or vim? What's so special about them? For me they are text editors with lots of unneeded features.[/QUOTE]


glamor?  :mrgreen: 

astonish viewers using incredulous lightining key strokes? 

well... actually i heard vi is good when doing work remotely...dont know for sure.....

---

### Post by commodore on 2006-03-26
Can't vim save .txt files or something? Or .html? I saved them by typing the extension myself but the files contained the colon commands :D

---

### Post by commodore on 2006-03-26
Ok I learned vim and it's very interesting but I don't see why I should use it when I have GUI.

---

### Post by midwinter on 2006-03-26
[QUOTE=commodore]Ok I learned vim and it's very interesting but I don't see why I should use it when I have GUI.[/QUOTE]

vi/m is a text editor, as such it is not excluded from working in a gui..  hence gvim. 

But you don't have to use it so don't worry about it.  For programming, I find it invaluable.

---

### Post by Stormy Eyes on 2006-03-26
[QUOTE=neoflight]well... actually i heard vi is good when doing work remotely...dont know for sure.....[/QUOTE]

vi was *made* for remote work -- remote work over 300 baud modem, as a matter of fact.

---

### Post by commodore on 2006-03-26
[QUOTE=midwinter]vi/m is a text editor, as such it is not excluded from working in a gui..  hence gvim. 

But you don't have to use it so don't worry about it.  For programming, I find it invaluable.[/QUOTE]

But I want to program one day. And I allready code html and css. Now it feels like there's something wrong with me when I don't use Emacs or Vim :D

---

