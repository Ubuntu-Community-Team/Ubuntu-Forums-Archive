---
title: "What is the lightest .txt editor (what is a clone of windows notepad)"
date: 2021-10-17
forum: Ubuntu, Linux and OS Chat
---

### Post by skoggo on 2021-10-17
Windows notepad refuses to crash, and it refuses to lag. No matter how bogged down windows becomes, if you can open a notepad window than notepad will work perfectly fine.

I am searching for the Linux equivalent of windows notepad, the most light weight and lag proof text editor out there. Something that is a computerised type writer and nothing more.

---

### Post by The Cog on 2021-10-17
nano is often recommended for beginners. And is is part of the default install. Just open a terminal and type nano followed by the file name, e.g.
```
nano test.txt
```

---

### Post by vanadium on 2021-10-17
The default text editor, gedit, will satisfy your needs as a graphical text editor. mousepad, the default text editor of XFCE, is very lightweight.

---

### Post by Impavidus on 2021-10-17
Just checked with a 2.2MB plain text file. Nano needs 9MB to just open it (no editing yet), vim needs 14MB and mousepad needs 55MB (resident memory as reported by top). Nano and vim aren't exactly Windows Notepad clones, as they run in a terminal. Much of their lightness comes from not having to handle a window, font rendering and a mouse.

---

### Post by grahammechanical on 2021-10-17
If you are really serious about Windows Notepad then open Ubuntu software and search for Notepad3 (WINE). That is the notepad application that comes with an install of WINE. Someone has made a snap packaged version of it. So, there you have a Windows Notepad app running on Linux.

Regards

---

### Post by TheFu on 2021-10-17
There is only 1 editor for all platforms.  vi/vim.
Don't bother with any others.  Vim is infinitely extensible and 1000x more efficient than any others.  I've probably seen over 100 different editors in my career and use at least 20 extensively.  Vim is the most pervasive, available, and efficient of all of them.  I've never seen any editor beside vi on a router.  It is a stripped down version, but it is still vi.  

People who don't use vim have never seen vim in the hands of an expert.

Nano is a toy compared to every other editor, including notepad.  May as well use **cp file <** rather than nano.

---

### Post by GhX6GZMB on 2021-10-17
How about ed?


[tongue-in-cheek]

---

### Post by DuckHook on 2021-10-17
Others have answered you directly and given you some alternatives. I have nothing to add to those good suggestions. But let me try instead to address the context behind your question.

[list=1]
[*]While I can't say that notepad in and of itself has crashed on me, it has died and lost my unsaved work when Windows itself crashed.
[*]In the Windows world, when Windows crashes, all is lost. You have no choice but to reboot and mourn the work that is now just scattered electrons.
[*]In contrast, in the Linux world, the whole graphical environment is just a pretty dress that rests on top of a much more solid foundation. On the few occasions when my graphical environment has crashed, I have found that that foundation was still fine. I just had to relaunch the graphical environment without having to reboot or even logout/login.
[*]If you run graphical editors like gedit or mousepad, then in the event your GUI dies they will die just as completely as notepad does when Windows crashes.
[*]But if you first launch a command line multiplexer like *screen* or *tmux* and then run a purely command line editor like *nano* within it, then even if your graphical environment crashes, you can almost always reattach to the multiplexer session without losing your work. You could even kill your graphical session on purpose and not have your editing session compromised. Another example of superior Linux versatility, safety and power. 
[/list]
I use this strategy when I am working on critical system files. I don't want the file to be left in a corrupted state should the graphical environment go down. Mind you, nothing like this has happened for going on 10 years, but I'd rather be safe than sorry. Moreover, getting used to command line editors has further benefits: it has allowed me to remotely edit configuration files in distant servers that have no graphical user interface. Combined with the use of the aforementioned multiplexer and such delicate surgery can even be done quite safely.

The only point that I will contest is that of TheFu's. Vi/Vim is a beast. I consider myself a Linux power user and I cannot get used to it. Given that you are inquiring about a Windows notepad clone, I can confidently say that Vi/Vim is not in the running. Trying to use it will just send you screaming from your keyboard and running for the tranquilizers.

---

### Post by TheFu on 2021-10-18
> **DuckHook said:**
> 
<snip>
The only point that I will contest is that of TheFu's. Vi/Vim is a beast. I consider myself a Linux power user and I cannot get used to it. Given that you are inquiring about a Windows notepad clone, I can confidently say that Vi/Vim is not in the running. Trying to use it will just send you screaming from your keyboard and running for the tranquilizers.

All true.  But I've never seen notepad on any router. Not once.  I would call emacs a beast, not vim.  Vim is as tiny as you like or as huge as you like thanks to the addon capabilities.
But, someone who thinks they've been hacked might think vim was part of that hack if they didn't know any better.  The first time I used vi, I had to power off the computer to get out of it.  I had no Unix background at the time and the idea of a modal editor was completely foreign to me.  I had been programming on DOS, MS-Windows, OS/2, MacOS and TSO/ISPF for years ... but that didn't provide the background for using vi/vim. ;)

To the OP: There are GUI editors and terminal editors.  All GUI programs, including editors, have the same fatal flaw in that a GUI is required to use them.  Unix/Linux servers typically do not have any GUI, so for people who do server work, none of those are worth our time.  
GUI editors tend to become bloated as the development team decides to add one more menu or one more menu item to the feature list.  Look at VC or Netbeans.  Those are crazy bloated.  
Then there are the minimal GUI editors like GEdit, Kate xedit, pluma, ... that's about it. Those are a little like nano, but with a few more features, like spell checking.  Spell checking is a dangerous thing in config files, however.
There are a bunch of middle-of-the-road editors like Atom, Geany, and almost 1 for each major scripting language.
Which editor is "best" quickly becomes a personal choice based on the type of file editing you do.  If you edit python, Atom would be suggested. IF you edit a mix of different languages and want a little debugger and compile/link help, geany is not quite a full IDE, but more than a simple editor.  

Do you need syntax highlighting for different languages - XML, YAML, JSON, HTML, CSS, C, C++, C#, D#, perl, python, java, javascript, ruby, php, and more?  That's where extensible editors like vim are helpful.   [https://vimawesome.com/](https://vimawesome.com/) has nearly 1000 addons to handle almost anything you might need.  [http://www.drchip.org/astronaut/vim/index.html](http://www.drchip.org/astronaut/vim/index.html) has some interesting addons too. These are loaded only when needed.  It is the custom kitchen sink solution, infinitely extensible and easy for the end-user to create their own addons to accomplish almost anything using macros and both internal and external tools. Learning enough vi to get around takes 10 minutes. vimtutor will teach that.  But you can spend a lifetime learning more.  I try to add 1 new vim capability to my list of tricks every week.  52 tricks doesn't sound like many, but it explodes as you learn about addons and quickly your mind creates "modes of thought" to be efficient in vim in very smart ways.  Sorta like how mountain people learn practical ways to find and store food for long winters.  Every new vim capability that I learn is another can in my cellar for use later.

I get excited about vim, because it is so amazing, but it definitely takes time to get passed the beginner level, then the universe of editing becomes open to you. Before that, you are stuck on a 1 track line between 2 subway stops that goes just between those 2 stops and nowhere else.

But if nano works for you, great!


Whenever editing system files, be sure to use **sudoedit** - that is compatible with any editor you choose to use. Just set your EDITOR environment variable to the program you wish to use.

---

### Post by The Cog on 2021-10-18
I have to agree with both DuckHook and TheFu. 

The context of the question is a little obscure, which is probably why so many suggested answers. Mousepad is a lightweight editor that a beginner might feel very at home with. But it is a GUI editorm and therefore more susceptible to crashes than a console based editor such as nano. But why the stress on crash resistance?

vi/vim is a much more powerful editor than nano, but there is a steep learning curve. Maybe 30 years ago I was advised to learn the basics of vi - enough to do basic editing, because vi is always there on any *nix OS, not dependent on a working GUI. Knowing the real basics of vi will help you get out of many a hole. That's a true today as it was then and I only suggested nano because I suspect skoggo is likely to have a preference for graphical editors. I still only know the basics of vi, but it's surprising how much I use it. Almost every day.

---

### Post by DuckHook on 2021-10-18
> **The Cog said:**
> …why the stress on crash resistance?
More than fair comment. I overemphasized crash resistance at the expense of other things.

I have had my GUI crash on me. Not indiscriminately, but it did happen regularly when I was playing one specific Steam game. However, people won't be tweaking system config files while they are gaming, so I'm getting spooked by an edge case.

Editing system files with a CLI editor is mostly a matter of good habits for me. In prior Ubuntu flavours, editing such files with *sudo gedit* or *sudo mousepad* was just asking for trouble. Canonical has since changed their sudo structure so that this danger will be reduced going forward, but I still recommend CLI editors for this reason alone.

A further reason for getting comfortable with CLI editors is remote work. But many forum members have already chimed in on this advantage, so no point repeating their advice.

---

### Post by bonzini on 2021-10-19
> **skoggo said:**
> Windows notepad refuses to crash, and it refuses to lag. No matter how bogged down windows becomes, if you can open a notepad window than notepad will work perfectly fine.

I am searching for the Linux equivalent of windows notepad, the most light weight and lag proof text editor out there. Something that is a computerised type writer and nothing more.

I think you are looking for something that need not exist.  "no matter how bogged down windows becomes" - doesn't apply here.  Just use nano (easy to learn) vi (harder to learn but worth it) emacs (why Ctrl keys are down there next to the other stuff like Alt) and move on.

---

### Post by ajgreeny on 2021-10-19
My suspicion is, that if you must use a GUI text editor rather than nano (my default), and your GUI application keeps crashing, you must have problems a bit more general than simply the GUI text editor.

When I have used mousepad on my Xubuntu installation I don't think I have ever seen it crash; in fact I can't remember when i last had anything crash on this installation.

Perhaps I'm just lucky!

---

### Post by mastablasta on 2021-10-20
> **DuckHook said:**
> 
A further reason for getting comfortable with CLI editors is remote work. But many forum members have already chimed in on this advantage, so no point repeating their advice.

for remote server admin i use Ajenti which has a browser text editor - so GUI it is. :)

but only if i do more complex editing. for simple editing CLI editors are quite good. on old windows i used to use *edit *in CLI. i still remember *edlin *editor back in dos, which sucked.

---

### Post by zebra2 on 2021-10-20
Hard to say what the expectations are in this thread but I've never had a problem with Gedit, but I'm a straight out of the box Ubuntu user. If decided to go back to writing code my choice would be Atom which is a pure text point and click editor that is open source and supports Windows, Linux, and IOS. It has everything a compiler enthusiast could ask for.  I took a look at Mousepad just out of curiosity and it looks to have some versatile strengths also.    To each his choice I suppose.

---

### Post by vo-nguyen on 2021-10-22
Maybe vi, vim, or nano is your jam.

---

### Post by Tadaen_Sylvermane on 2021-10-25
> [COLOR=#000000]There is only 1 editor for all platforms. vi/vim.[/COLOR]
[COLOR=#000000]Don't bother with any others. Vim is infinitely extensible and 1000x more efficient than any others. I've probably seen over 100 different editors in my career and use at least 20 extensively. Vim is the most pervasive, available, and efficient of all of them. I've never seen any editor beside vi on a router. It is a stripped down version, but it is still vi.[/COLOR]

[COLOR=#000000]People who don't use vim have never seen vim in the hands of an expert.[/COLOR]

[COLOR=#000000]Nano is a toy compared to every other editor, including notepad. May as well use [/COLOR]**cp file < rather than nano.**It's extremely frustrating to see this said. While it may be an accurate statement it is far from the correct answer. When I was first learning linux and open source this was all anyone and even any guides said. However none of them mentioned that you needed months of hands on experience and a manual to remotely make any legitimate use of it. This exact answer was one of the things that kept me from diving into the open source world for quite awhile. For basic editing a manual shouldn't be required. It should be intuitive from the start. Vi(m) is not even remotely intuitive. Especially if it's a person coming from a Windows background.

---

### Post by vanadium on 2021-10-26
Basic editing with vim can be learned in 30 minutes, just like basic editing with notepad can be learned in 30 minutes for someone that never edited a file before.

---

### Post by ajgreeny on 2021-10-26
> **Tadaen_Sylvermane said:**
> It's extremely frustrating to see this said. While it may be an accurate statement it is far from the correct answer. When I was first learning linux and open source this was all anyone and even any guides said. However none of them mentioned that you needed months of hands on experience and a manual to remotely make any legitimate use of it. This exact answer was one of the things that kept me from diving into the open source world for quite awhile. For basic editing a manual shouldn't be required. It should be intuitive from the start. Vi(m) is not even remotely intuitive. Especially if it's a person coming from a Windows background.
Even after 16 years of using Ubuntu and Linux I agree totally with Tadaen_Sylvermane.

I have tried several times to deal with vi/vim and failed; it may be the best way for some users but it certainly has never been my experience that it is worth the hassle of learning it when there are other cli editors such as nano which are very simple to use without needing to remember, what to me were the most unlikely keyboard commands to edit, save, etc etc.

Perhaps all my uses are very simple text files and not coding etc, where maybe vi/vim have big advantages.
Not for me!

---

### Post by Tadaen_Sylvermane on 2021-10-26
I apologize. I exaggerated I admit. It's always been a sore point for me as there is nothing other than guessing until you find it. I still think a manual shouldn't be required just to save or exit, to say nothing of the insert vs option modes. That just isn't a thing windows users are aware of.

---

### Post by The Cog on 2021-10-26
There is very little you need to memorise to be able to use vi:
[INDENT]i - enter insert mode, to begin entering text (Use cursor keys to move, backspace or delete to remove text).
Esc - leave insert mode (you can still move with cursor keys)
:w - write (save) file.
:q - quit (:q! to quit without saving)[/INDENT]
That's enough to do a basic edit, and not much harder than nano. That's all I learned, all I knew for some years. This is **well worth learning** because vi is everywhere. Nano isn't. Nano is for those beginners who haven't learned the above four lines.
The first "fancy" one I learned was !wq - write and quit in one command.

---

### Post by DuckHook on 2021-10-26
> **The Cog said:**
> There is very little you need to memorise to be able to use vi…
This is **well worth learning** because vi is everywhere. Nano isn't. Nano is for those beginners who haven't learned the above four lines…
Sometimes, we (I hazard the presumption of including myself among the Linux acolytes) are so comfortable around the command line that we forget how *un*comfortable it makes newbies feel. While what you say is technically accurate, I think it misses the point that Tadaen_Sylvermane is trying to make: it's not so much the actual commands that make vi/m difficult to use, it's the general environment of obscurity and arcanery.

I get that modal editors are superpowered to their adepts. I also get that one can more or less find ones way around them without learning their more esoteric functions. But the whole idea of modal editing itself is entirely foreign to a non&#8209;geek. We must remain mindful of the OP's caveat, which is important enough to recap:> **skoggo said:**
> …Something that is a computerised typewriter and nothing more.*skoggo* is not only speaking for him/herself here; s/he is speaking for practically all newbies—and for more than a few oldies, including me (and Tadaen_Sylvermane and ajgreeny). Actually, I am very thankful that *skoggo* stated his/her requirements so baldly, which gets to the heart of the matter so succinctly that I'm going to borrow it for my own use.

Modal editors were created by programmers for programmers. Vi/m is capable of doing triple backward somersaults with four&#8209;and&#8209;a&#8209;half twists. But the vast majority of users have neither the time, patience, acumen nor even the inclination to become world class command line gymnasts. They just want a virtual typewriter. And anything that requires one to switch between edit mode vs command mode vs magic wand mode does not remotely act like a virtual typewriter.

The fact that *vi* is everywhere whereas *nano* is not is, again, true. But it is also a significant barrier to entry that keeps Linux obscure, keeps it arcane, discourages newcomers and turns off even seasoned users like me. The first thing I do after installing a bare bones OS (like OpenWRT) is to install *nano*.

The OP did ask about editors in the context of Ubuntu, where the availability of *nano* is not at issue.

---

### Post by T6&amp;sfpER35% on 2021-10-30
here's something i found that teaches to use the vim editor 
[https://www.makeuseof.com/master-vim-with-vimtutor/]("https://www.makeuseof.com/master-vim-with-vimtutor/")

---

### Post by vo-nguyen on 2021-10-30
You think nano is a toy? What about pico?

---

### Post by xinuzi on 2021-11-01
geany, definately (& better than Just Notepad)

---

### Post by TheFu on 2021-11-02
Just came back for a visit. I see the editor choice war is still going.  Enjoy it if you like.

An editor is NOT a word processor.  I get the feeling we need to be clear about that.  If the goal is a simple word processor, almost anything except an editor would be better. I wouldn't use my editor of choice for word processing more than 1-2 paragraphs.  

I do use it for taking notes, however.  There are a number of vim extensions just for note taking. I use vimwiki, but there are some heavier tools that are good for that - like gnote [https://wiki.gnome.org/Apps/Gnote](https://wiki.gnome.org/Apps/Gnote) and Basket-Note Pads [https://basket-notepads.github.io/](https://basket-notepads.github.io/) (very MS-OneNote like) and Zim [https://zim-wiki.org/](https://zim-wiki.org/) and if you have a Nextcloud server, there are 1-click modules for note taking for it.  I specifically don't want a GUI, so vimwiki fits my needs and can be accessed from anywhere in the world over an ssh connection.

I'll leave everyone to keep the editor-wars going now.

The right tool, for the right job and when it comes to text processing, there are probably hundreds of tools for any Unix-like OS. Just depends on the intended use.

---

### Post by KBar on 2022-01-03
Mousepad is super light and okay to use.

---

