---
title: "Is emacs still relevant?"
date: 2011-03-08
forum: The Cafe
---

### Post by Biddlesby on 2011-03-08
I have just started to explore emacs, and am reading up on the arguments for and against. I'm sure lots of people have views on emacs/vim, but I couldn't find anything recent searching the forum, so I've made a new topic.

My question is this: is emacs/vim still useful given today's software? I'm thinking mainly of C++ programming. For example, I can see why emacs would be useful in the past, and when accessing remote computers only using the terminal, but surely it cannot compare to modern software with bells and whistles and tab-completions and so on.

If you reply could you also answer: if you do alot of programming with C++, what editor do you use on Ubuntu?

Harry

---

### Post by Diametric on 2011-03-08
I don't use vim or emacs.  I use nano - tons more intuitive and easier to pick up quickly.  From time to time, I still look at vim commands to keep them fresh in my mind, because if a system goes down, I'm told you may only get the use of vim if you need to write script...but maybe someone else can chime in on that.

Does anyone know the file size difference between vim and nano?

BTW...the only thing I think emacs is good for is the built in text adventure game by Ron Schnell.  It's called Dunnet

---

### Post by Grenage on 2011-03-08
I've never used emacs, but I use vim every day; server administration calls for it.

It's a very powerful and useful editor, but don't use it on a normal desktop.

---

### Post by Spice Weasel on 2011-03-08
> **Diametric said:**
> Does anyone know the file size difference between vim and nano?


vim = 1.9mb
nvi = 400kb
nano = 191kb
mg = 140kb

(nvi = ultralight vi, mg = ultralight emacs)

---

### Post by aeiah on 2011-03-08
it used to be one of those old debates, emacs vs vim. i havent heard anything about emacs in ages though. vi / vim is still relevant for server admin etc, although like one of the posters above i usually use nano. nano is really just a text editor though. vim and emacs may be more useful for large projects but i dont know what you'd use for C++. eclipse maybe?

---

### Post by Diametric on 2011-03-08
> **Spice Weasel said:**
> vim = 1.9mb
nvi = 400kb
nano = 191kb
mg = 140kb

(nvi = ultralight vi, mg = ultralight emacs)

If that is correct, then nano is a fraction of the size of vim. Why wouldn't a sys-admin want nano as the default editor - if for nothing else then file size alone.

---

### Post by Sporkman on 2011-03-08
Emacs: A bloated OS that lacks a good text editor.
Vi: You need to know the secret codes before you can start typing anything.
Nano: Quick and intuitive.

---

### Post by crush304 on 2011-03-08
might ask the question in the programming forum, you'll probably get better responses. at least won't get anyone recommending nano. and not that nano is bad, it's easy when you don't know what you are doing. vi/emacs on the other hand are designed to be powerful when you know what you are doing.

i use emacs all the time although mostly for lisp - i don't do any c++ so i can't comment there

---

### Post by jerenept on 2011-03-08
Gedit is probably a good call. Personally, it's never given me any trouble, and, it has syntax highlighting...

---

### Post by Pogeymanz on 2011-03-08
I actually did quite a bit of C++ coding in Emacs.

It's wonderful. Emacs has shortcuts for auto-completion (and basically anything else you want a shortcut for) and has a built-in IDE.

I have been using Vim more lately, but I still find the search function (especially search-and-replace) to be WAY better in Emacs than Vim. Also, Emacs does way smarter indentation than Vim for C++, imo.

Just do a google search for "c++ emacs" and you'll find all kinds of great tips. Honestly, Emacs is a pain in the *** to use for anything but coding, but it is really helpful when coding.

---

### Post by Primefalcon on 2011-03-08
I have tried emacs and don't like it i, though I use VIM on a regular basis

---

### Post by Dustin2128 on 2011-03-08
I use emacs and vim for most of my editing, whatever pops into my head to use first. Also keep in mind that vim != vi. Vim is vi with loads more features (read: bloat), vi alone is incredibly lightweight being designed for computers of the '70s. But really, the size scale (well minus download size) is quite irrelevant with today's computers, or any computer really with more than 16 Mb RAM.

---

### Post by Pogeymanz on 2011-03-08
> **Dustin2128 said:**
> I use emacs and vim for most of my editing, whatever pops into my head to use first. Also keep in mind that vim != vi. Vim is vi with loads more features (read: bloat), vi alone is incredibly lightweight being designed for computers of the '70s. But really, the size scale (well minus download size) is quite irrelevant with today's computers, or any computer really with more than 16 Mb RAM.

Yes, vi is actually quite terrible to use.

---

### Post by NightwishFan on 2011-03-08
Its emacs! What could be more relevant. What repelled the million Persians from Thermopylae? Tactics and bravery? Pfft.. Emacs.

---

### Post by wojox on 2011-03-08
If your sporting a neckbeard, then yeah it's relevant. :p


> **Pogeymanz said:**
> Yes, vi is actually quite terrible to use.

+1 vi is evil. It does horrible things to your files. Vim FTW!!!

---

### Post by Dustin2128 on 2011-03-08
> **Pogeymanz said:**
> Yes, vi is actually quite terrible to use.
It's pretty decent actually, you just have to know how to use it before you start using it if you get my meaning.

---

### Post by jerenept on 2011-03-08
> **NightwishFan said:**
> Its emacs! What could be more relevant. What repelled the million Persians from Thermopile? Tactics and bravery? Pfft.. Emacs.

Thermopylae

---

### Post by jerenept on 2011-03-08
> **wojox said:**
> If your sporting a neckbeard, then yeah it's relevant. :p
+
Agreed :P

---

### Post by JDShu on 2011-03-08
I don't do much C++ these days but emacs is great for C, Java, and Python.

Also, in b4 xkcd.

---

### Post by NightwishFan on 2011-03-08
> **jerenept said:**
> Thermopylae

Normally I would be like pfft, but in this case thanks, the spelling eluded me and I was too busy to search it at the time. :D

---

### Post by 1clue on 2011-03-08
The guys who are recommending nano and gnome edit for software development don't know what they're talking about.

Emacs and vim are literally the same basic editor with a separate interface on it.  If you're a control key guy, then emacs is probably better for you.  I like vim.

Both of these editors are extremely pertinent for programming.  They were literally designed for that sort of thing.  If you're a keyboard oriented person, then these editors may offer what you need better than an IDE.

An IDE has a strong advantage with jumping to the function definition or to the references to it.

On the other hand, programmatic search and replace on vim/emacs is WORLDS better than any IDE.

I switch back and forth between vim, Eclipse and TextMate (a Mac app)

---

### Post by NightwishFan on 2011-03-08
I programmed my entire web browser using nano and gedit... :rolleyes: Its called choice. You've already made it, you just have to understand it.

---

### Post by 1clue on 2011-03-08
You can do that.  You can also walk from Anchorage Alaska to Lima Peru, but you might want to take an airplane for most of that.

---

### Post by Austin25 on 2011-03-08
> **JDShu said:**
> Also, in b4 xkcd.

Oh yeah.
[IMG]http://imgs.xkcd.com/comics/real_programmers.png[/IMG]
How come we didn't catch that sooner?

---

### Post by NightwishFan on 2011-03-08
> **1clue said:**
> You can do that.  You can also walk from Anchorage Alaska to Lima Peru, but you might want to take an airplane for most of that.

Hmm.. Over-dramatisation ftw. Please note I do not disagree with you, I just happen to like nano. :D

---

### Post by 1clue on 2011-03-08
LOL!

Nano is fine for the limited editing most Ubuntu users need a command line editor for.  It's got just about zero learning curve, and just about zero features that Notepad doesn't have on Windows.

Speaking as a programmer who makes his living based on how much actually gets done rather than how many hours I've been at it, if you're going to write real software you need a real software-oriented editor.

Vim and emacs both have a really steep learning curve, but they are both extremely powerful.  If you want the features, including a kick-*** search and replace that is unparalleled in any GUI editor, or the ability to use any UN*X command as an input or a filter, these editors are definitely worth the time.

I'm a vim guy, but I refuse to go into the vim-vs-emacs argument.  If emacs is your style then use it.  They're both the same editor underneath.

---

### Post by jpkotta on 2011-03-10
> **1clue said:**
> They're both the same editor underneath.

I disagree.  I see a big difference in philosophy behind Vim and Emacs, and they work very differently.  Just because they have many of the same capabilities doesn't mean they're at all similar.

---

### Post by lykwydchykyn on 2011-03-10
If your idea of a good IDE looks something like Visual Studio, then probably you aren't going to see the relevance of Emacs.  

Personally, I love it.  And I'm hardly a greybeard Unix guy -- I started using Emacs sometime around 2008.  I do mostly PHP/JS/HTML web development, Python development, or BASH scripts (though I use Emacs for a lot of non-coding tasks), but what makes it great IMHO transcends the particular language you use.

To me it's killer features are:
 
 - it can be easily and quickly customized or extended using the same language that it's (mostly) implemented in (eLisp).  It's really not hard to do, either; after using it just a couple months I was doing a lot of customization.
 - it never requires me to use the mouse, which I find far more ergonomic (I hate switching between mouse & keyboard)
 - the way modes work is very nice, in that the editor's behavior can be idiomatic to the type of file being edited; or how functionality can be easily enabled/disabled with a quick command.
 - having an "apropos" command sure beats digging through menus and dialog boxes looking for a feature you need but aren't quite sure exists.


There are all kinds of little things too, like the fact that it tiles windows automatically (always giving you the maximum space), or tramp mode for remote/root file editing, being able to have the same buffer open in two different windows (great for debugging large files), etc. etc.

Of course it has it's warts (printing comes to mind...), and learning the key shortcuts takes time.  But once you do, it pays off.  

(Some of the things (both good and bad) I've mentioned are probably true of vim as well, but vim vs emacs isn't the point here, is it?)

---

### Post by kpkeerthi on 2011-03-11
I use text editors for adhoc plain text editing. For hardcore programming and development (I program Java/JEE), I use IDEs (like Eclipse, Websphere Studio, Netbeans). IDEs can do things that simple text editors like Vi or emacs can't even think of.

---

### Post by 1clue on 2011-03-11
> **jpkotta said:**
> I disagree.  I see a big difference in philosophy behind Vim and Emacs, and they work very differently.  Just because they have many of the same capabilities doesn't mean they're at all similar.


There's no disagreeing to it.  Vi and emacs are both based on ed, which is a line editor.  Both have an 'ed' mode, and both are simply wrappers around ed.  Their user interface and behavior don't have anything to do with it.

---

### Post by jpkotta on 2011-03-11
> **1clue said:**
> There's no disagreeing to it.  Vi and emacs are both based on ed, which is a line editor.  Both have an 'ed' mode, and both are simply wrappers around ed.  Their user interface and behavior don't have anything to do with it.

"Simply wrappers around ed", as in they are just executing editing commands by calling ed?  Seriously?  You better be trolling.

---

### Post by 1clue on 2011-03-12
Not trolling at all, but in the effort of finding references I found out that emacs started out to be some macro scripts for the TECO editor, which was designed as a (paper) Tape Editor and COrrector.  TECO goes back to 1963.

Vim, on the other hand, comes from ed, which started as a line editor on a terminal and was first written in 1971.  That turned into ex, and then vi, and finally vim.

While they don't share the same code base as I thought, the definitely both grew from line editors.  There's nothing wrong with that, these editors have been around since the days when big computer manufacturers wouldn't have imagined a mainframe with as much memory as your cell phone has now.

Please do a bit of research before you get offended on principle.

---

### Post by ve4cib on 2011-03-12
Saying that vim and emacs are the same because they both evolved from line editors decades ago is rather much like saying chimpanzees and humans are the same because we share a common ancestor.  Yes, there are similarities in lineage, and function (in the case of editors)/appearance (in the case of primates), but they are in fact very, very different entities now.

I really have no preference in terms of emacs/vi.  I've never used either one sufficiently to really develop an opinion.  I do like Emacs on principle in that it has emacs lisp as part of it.  Anything involving lisp gets bonus points from me.

But really if I'm using a terminal and need to edit a file I'll usually use nano.  It doesn't do much other than open the file and let me edit it.  And most of the time that's all I really need.

If I'm writing code I'll be doing it in an X session where I can use much more useful editors.  Like Geany, Gedit, or even a full-blown IDE like MonoDevelop, Eclipse, or CodeBlocks.


To answer the OP's secondary question, I do a lot of C and C++ coding and generally use Geany.  It's just become my default text editor for pretty much everything.  I'm starting to play around with CodeBlocks and QtCreator for some of my larger projects though.  Haven't used them enough to really form an informed opinion yet, but they generally seem like decent IDEs.

---

### Post by matthew.ball on 2011-03-12
The real power of emacs comes from the plethora of available extensions available (this is most probably the same for vim, but I have never used it).

Most people associate emacs with a command-line editor, the reality is very few people actually use emacs-nox any more (from my searching online, I am one of a handful of people who has emacs-nox installed).

[This]("http://dev.pocoo.org/~gbrandl/emacs2.png") is the modern front-end for emacs (of course, this isn't vanilla emacs. There are a few extensions in action there, but they're all very easy to set-up). The only obvious thing I have found missing in emacs is an in-built form-builder. There is some amazing integration between emacs and development tools, but most people just don't look for it (or don't know how, not that it's very difficult to find). Projects like [CEDET]("http://cedet.sourceforge.net/") have attempted to bundle everything you would need to get the ultimate IDE experience out of emacs.

Really, I just think most people's analysis of emacs comes from the vanilla version, which while having a lot of abilities actually coupled with it, doesn't have the vast majority actually turned on, so without exploring the system a bit, you don't actually realise what you're missing out on. The project [emacs-starter-kit]("http://eschulte.github.com/emacs-starter-kit/") (which should come default with every version of emacs) turns on most useful things, and certainly gives a new user the ability to experience more of emacs to make an informed decision whether or not the editor is actually relevant.

Edit:

> **kpkeerthi said:**
> I use text editors for adhoc plain text editing. For hardcore programming and development (I program Java/JEE), I use IDEs (like Eclipse, Websphere Studio, Netbeans). IDEs can do things that simple text editors like Vi or emacs can't even think of.
I'd be interested to know (beyond my claim that emacs doesn't have an in-built form-builder) what an IDE does that emacs doesn't.

---

### Post by NightwishFan on 2011-03-12
^ This guy is the master.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-03-12
You have to keep in mind that both vim and emacs are designed for ease of use *once you learn to use them*, not ease of learning to use them. Knowing how to use both, trying to edit text with nano/gedit/geany is a real pain to me.

---

### Post by kevdog on 2011-03-12
Seriously -- if anyone has never crashed an install before and had to do some quick command line edits -- you gotta know some vim.  I'm not saying you have to know it inside and out, but its a necessity to know how to insert, edit, delete text and switch from navigation to text entry mode.  If that's all you know -- you'll be good for about 95% of cases you need a command line editor to save your borked system.

---

### Post by jerenept on 2011-03-12
> **kevdog said:**
> Seriously -- if anyone has never crashed an install before and had to do some quick command line edits -- you gotta know some vim.  I'm not saying you have to know it inside and out, but its a necessity to know how to insert, edit, delete text and switch from navigation to text entry mode.  If that's all you know -- you'll be good for about 95% of cases you need a command line editor to save your borked system.

Nano is the one I use.
Works for me, and there is no need to learn how to use it, it is just so nice and simple.

---

### Post by jwbrase on 2011-03-12
Emacs and vim are still relevant for things like server administration, where you may well never touch the physical machine and probably won't have the bandwidth to tunnel an X session. (And the server might not have X to begin with for that very reason).

For the average desktop user, gedit will probably do. I myself switch between gedit and vim situationally, and have some familiarity with Emacs. (I actually used it regularly for a while. There were some things I liked and others that drove me crazy...)

---

### Post by koenn on 2011-03-12
> **Diametric said:**
> If that is correct, then nano is a fraction of the size of vim. Why wouldn't a sys-admin want nano as the default editor - if for nothing else then file size alone.
it's partially tradition. you'd find vi installed on any unix since the 70s, and up to today, and since these old unixes tend to last, it's not uncommon to come across a 20 years old system even today.
So in case you have to work on one of those, you can either try to find and install a compatible version of nano and then get to work, or start vi and get to work. 

Essentially, knowing (at least a bare minimum of) vi makes your sysadmin skills transferable to pretty much every unix system out there. With nano, you can be an ubuntu admin, you pays your money and you takes your choice.

---

### Post by 1clue on 2011-03-12
> **ve4cib said:**
> Saying that vim and emacs are the same because they both evolved from line editors decades ago is rather much like saying chimpanzees and humans are the same because we share a common ancestor.  Yes, there are similarities in lineage, and function (in the case of editors)/appearance (in the case of primates), but they are in fact very, very different entities now.


We've gone way out of the context of my original point, which was that because (I thought) they shared a common heritage and still had that original functionality built in, all the rest is dressing.  Which negates the point of editor wars.

It turns out they don't share the common heritage, but both have an extremely similar line editor core, and my opinion is still that editor wars are stupid with two highly capable programming editors like that.

Vim still has an ex mode, where you are editing the file with ex.  Whether vim wraps ex or re-implements it I neither know nor care.  I'm not an emacs user but I assume you can get into a core line editor mode with that too.

> 
I do like Emacs on principle in that it has emacs lisp as part of it.  Anything involving lisp gets bonus points from me.


Really?  Lisp?  What would you use it for?  I learned a bit of it in the 80's and have never once had to solve a problem for which lisp was an appropriate tool.

> 
If I'm writing code I'll be doing it in an X session where I can use much more useful editors.  Like Geany, Gedit, or even a full-blown IDE like MonoDevelop, Eclipse, or CodeBlocks.


I DO use Eclipse.  I also use TextMate on a Mac.  When neither of those can do something particularly complex, I switch over to vim.  If I were oriented toward emacs, that would do everything vim can.

Modern IDE editors can handle some regex changes, but not nearly as conveniently as vim.  More yet, vim and emacs let you use any application on your system to edit your text file.  I use that a lot.

> 
To answer the OP's secondary question, I do a lot of C and C++ coding and generally use Geany.  It's just become my default text editor for pretty much everything.  I'm starting to play around with CodeBlocks and QtCreator for some of my larger projects though.  Haven't used them enough to really form an informed opinion yet, but they generally seem like decent IDEs.

I think there are a lot more -nox users out there than you think.  Most of the old-timers probably use the -nox version of emacs the same as they would use a -nox version of vim.  I use -nox because I don't see it adding anything to my experience.

> 
[This]("http://dev.pocoo.org/~gbrandl/emacs2.png") is the modern front-end for emacs (of course, this isn't vanilla emacs. There are a few extensions in action there, but they're all very easy to set-up). The only obvious thing I have found missing in emacs is an in-built form-builder. There is some amazing integration between emacs and development tools, but most people just don't look for it (or don't know how, not that it's very difficult to find). Projects like [CEDET]("http://cedet.sourceforge.net/") have attempted to bundle everything you would need to get the ultimate IDE experience out of emacs.

Really, I just think most people's analysis of emacs comes from the vanilla version, which while having a lot of abilities actually coupled with it, doesn't have the vast majority actually turned on, so without exploring the system a bit, you don't actually realise what you're missing out on. The project [emacs-starter-kit]("http://eschulte.github.com/emacs-starter-kit/") (which should come default with every version of emacs) turns on most useful things, and certainly gives a new user the ability to experience more of emacs to make an informed decision whether or not the editor is actually relevant.

Edit:


I'd be interested to know (beyond my claim that emacs doesn't have an in-built form-builder) what an IDE does that emacs doesn't.

One thing that vim/emacs don't do that well is jump to definitions or references of functions when multiple implementations of that name exist.  To highlight a call and say, "who calls this?" and only get the places where that particular implementation, with that particular parameter list are called.

That said, an IDE is a real pain in the rear to set up.  Eclipse often goes wonky on me and I spend hours getting it working again.  The intelligence tat comes with the code-aware editor just isn't worth it half the time.

---

### Post by jpkotta on 2011-03-13
> **1clue said:**
> Not trolling at all, but in the effort of finding references I found out that emacs started out to be some macro scripts for the TECO editor, which was designed as a (paper) Tape Editor and COrrector.  TECO goes back to 1963.

Vim, on the other hand, comes from ed, which started as a line editor on a terminal and was first written in 1971.  That turned into ex, and then vi, and finally vim.

While they don't share the same code base as I thought, the definitely both grew from line editors.  There's nothing wrong with that, these editors have been around since the days when big computer manufacturers wouldn't have imagined a mainframe with as much memory as your cell phone has now.

Please do a bit of research before you get offended on principle.

(Sorry that I implied that you were trolling.)

Yes, and the fact that they both have line editors as an ancestor was the only thing true in your post, if you allow 'ed' to stand for 'a line editor'.  To be fair, I never knew TECO was a line editor until I looked it up before replying.

> **1clue said:**
> We've gone way out of the context of my original point, which was that because (I thought) they shared a common heritage and still had that original functionality built in, all the rest is dressing.  Which negates the point of editor wars.

It turns out they don't share the common heritage, but both have an extremely similar line editor core, and my opinion is still that editor wars are stupid with two highly capable programming editors like that.


Emacs is **definitely not** a line editor at its core.  Emacs is a lisp interpeter, whose primary purpose is editing text.  It operates on *buffers*, which are fundamentally just arrays of characters (along with some local state and metadata).  I can't speak for Vim, but I'd guess it's similar.

I'd go on to say that the implementation details of an editor are completely irrelevant compared to the philosophy behind it.  That is why there are editor wars.  Not because Emacs people think Vim is not as capable as Emacs or vice versa; the debate continues because they do things differently, and have different mindsets.  That's why editors are religion: you can't objectively say that one is better than the other.  You just find one that **you** like and embrace it, then maybe evangelize and crusade against the nonbelievers.  

I like the big ideas behind Emacs, many others do too, and that's what (indirectly) keeps it relevant.  It stays relevant because enough people like Emacs to write extensions and improvements for it.  It's why Vim is also relevant.  Editors (or any piece of software, for that matter) that don't have people regularly improving them are doomed to die in obscurity (unless they fill a niche like sed or Notepad).

---

### Post by ve4cib on 2011-03-13
> **1clue said:**
> Really?  Lisp?  What would you use it for?  I learned a bit of it in the 80's and have never once had to solve a problem for which lisp was an appropriate tool.

Given that Emacs is essentially a text-editing-specific lisp interpreter you can use it for pretty much anything you want.  Need some kind of custom text-editing script?  Emacs Lisp.  Want games?  Emacs Lisp.  Want to play around with one of the weirdest, most fun-to-use programming languages?  Lisp of any flavour.

Is Lisp the be-all and end-all of programming languages?  Definitely not.  But I enjoy using it, and anything that supports it gets bonus points in my books.  But really that's just a personal opinion on the matter.  I don't expect anyone to agree with me.

____________

> Emacs and vim are still relevant for things like server administration, where you may well never touch the physical machine and probably won't have the bandwidth to tunnel an X session. (And the server might not have X to begin with for that very reason).

If you can SSH into the machine then in theory you could mount the other computer as an SSHFS drive and edit the files with your local X server and whatever GUI-oriented editors you wanted.  Less bandwidth than a tunneled X session, but still with the convenience of not having to use Vi nor Emacs.  You could also mount it as an FTP drive, provided the server has an FTP daemon running on it.

---

### Post by matthew.ball on 2011-03-13
> **1clue said:**
> Really?  Lisp?  What would you use it for?  I learned a bit of it in the 80's and have never once had to solve a problem for which lisp was an appropriate tool.
*Really* good configuration language for customising your emacs experience.

> **1clue said:**
> I think there are a lot more -nox users out there than you think.  Most of the old-timers probably use the -nox version of emacs the same as they would use a -nox version of vim.  I use -nox because I don't see it adding anything to my experience.

One thing that vim/emacs don't do that well is jump to definitions or references of functions when multiple implementations of that name exist.  To highlight a call and say, "who calls this?" and only get the places where that particular implementation, with that particular parameter list are called.
In my experience most people just have the default emacs installed (which comes with emacs-gtk) and call "emacs -nw" if they want to use the command-line version - it seems most development is focussed on the emacs version too, rather than emacs-nox, so that some things have been developed almost exclusively for the gtk version and those of us using the nox have to suffer.

I have a "psuedo-tags" function which takes a boost from ido, by default it just finds the point where a function is defined, but I'm sure you could extend it to all occurrences, that or just use [FONT="Courier New"]isearch-forward[/FONT] on some word and find the appropriate place - there's a useful extension to isearch (though I don't know the correct command, just the default key-binding) which searches for the word in front of the cursor, very convenient.

I mean, emacs' strength in search comes from it's use of regular expressions - they're *everywhere* - so I don't think it would be too difficult to script up a function which does what you're describing.

---

### Post by Shining Arcanine on 2011-03-13
> **Biddlesby said:**
> I have just started to explore emacs, and am reading up on the arguments for and against. I'm sure lots of people have views on emacs/vim, but I couldn't find anything recent searching the forum, so I've made a new topic.

My question is this: is emacs/vim still useful given today's software? I'm thinking mainly of C++ programming. For example, I can see why emacs would be useful in the past, and when accessing remote computers only using the terminal, but surely it cannot compare to modern software with bells and whistles and tab-completions and so on.

If you reply could you also answer: if you do alot of programming with C++, what editor do you use on Ubuntu?

Harry

Why did you decide to use emacs instead of xemacs?

---

### Post by 1clue on 2011-03-13
> **matthew.ball said:**
> *Really* good configuration language for customising your emacs experience.


In my experience most people just have the default emacs installed (which comes with emacs-gtk) and call "emacs -nw" if they want to use the command-line version - it seems most development is focussed on the emacs version too, rather than emacs-nox, so that some things have been developed almost exclusively for the gtk version and those of us using the nox have to suffer.

I have a "psuedo-tags" function which takes a boost from ido, by default it just finds the point where a function is defined, but I'm sure you could extend it to all occurrences, that or just use [FONT="Courier New"]isearch-forward[/FONT] on some word and find the appropriate place - there's a useful extension to isearch (though I don't know the correct command, just the default key-binding) which searches for the word in front of the cursor, very convenient.

I mean, emacs' strength in search comes from it's use of regular expressions - they're *everywhere* - so I don't think it would be too difficult to script up a function which does what you're describing.

Are you talking about *people* or *programmers?*

Random users who just want an editor, those guys will probably take the default installation and the default settings, try to figure out how to use the a few features and then give up after a day or a month.

I don't know any programmers at all who haven't done extensive re-installation of a dozen different apps to get things just right, and then spend a day or two experimenting with the settings.

Again not familiar with emacs, but with vim the gui version really doesn't get you much.  Anyone who started out with emacs or vim back before there was a GUI version would probably still be using the -nox one.



FWIW my original post on this thread was to say that emacs and vim are both still very relevant, and to address comments about which one is better by saying that it really doesn't matter one way or the other, each person will have a preference and that's as it should be.

Since then, I've been arguing with people who are arguing with me, apparently because I said it wasn't worth arguing about.  I'm tired of this.  You guys can carry on if you like but I'm done here.  Have fun.

---

### Post by matthew.ball on 2011-03-13
> **1clue said:**
> Are you talking about *people* or *programmers?*

Random users who just want an editor, those guys will probably take the default installation and the default settings, try to figure out how to use the a few features and then give up after a day or a month.

I don't know any programmers at all who haven't done extensive re-installation of a dozen different apps to get things just right, and then spend a day or two experimenting with the settings.

Again not familiar with emacs, but with vim the gui version really doesn't get you much.  Anyone who started out with emacs or vim back before there was a GUI version would probably still be using the -nox one.



FWIW my original post on this thread was to say that emacs and vim are both still very relevant, and to address comments about which one is better by saying that it really doesn't matter one way or the other, each person will have a preference and that's as it should be.

Since then, I've been arguing with people who are arguing with me, apparently because I said it wasn't worth arguing about.  I'm tired of this.  You guys can carry on if you like but I'm done here.  Have fun.
Just like my original post was directed to kpkeerthi, I asked for possible limitations - you gave one, and I just said that surely there would be a solution.

I am not a programmer, I'm just a casual user who uses Linux, and on the way discovered emacs. It has forced me to learn emacs lisp, but I am most certainly not a programmer.

---

### Post by jpkotta on 2011-03-14
> **Shining Arcanine said:**
> Why did you decide to use emacs instead of xemacs?

I started with GNU Emacs, then switched to XEmacs for about a year, then switched back.  The simple answer is GNU Emacs has more users, and thus most add ons will work with it a bit better (though 90% will work well with either), and at the time I stopped using it, XEmacs was more prone to crash (though it would regularly run for over a week with no issues).  I liked the tabs in XEmacs much better than tabbar for GNU Emacs, but since I started using ido, I don't miss them at all.  I still miss the horizontal scrollbar.

This sums it up pretty well: [http://steve-yegge.blogspot.com/2008/04/xemacs-is-dead-long-live-xemacs.html](http://steve-yegge.blogspot.com/2008/04/xemacs-is-dead-long-live-xemacs.html).

---

### Post by haziz on 2012-04-29
Yes.

Using emacs every day and love it. I find vi/vim however totally unintuitive.

---

### Post by perce on 2012-04-29
I use emacs every day to write in LaTeX. Together with the browser, it's the program I'm staring the longest at.

---

### Post by F.G. on 2012-04-29
hey everyone,
i use vim out of preference, though also spend alot of time using vi (apparently the only one available on some machines). at uni i tried to learn emacs once, found it so dull i initially learnt to program c with a pencil and paper. lots of people use emacs and love it, so it certainly isn't 'no longer relevant' but if you don't like use something else. for C++ programming i would probably use an IDE (unless the project was very small), probably Netbeans (which i would highly recommend if you are doing a large oo project in C++ or Java).

ps. other really nice editors, which i use if i want a GUI editor are Sublime and Cream (essentially a vim wrapper), both of which can be used without installation.

pps. and for the record, although i have to use vi all the time (literally for about half the editing i do) i really wish i didn't. vim is great, vi is a nightmare.

---

### Post by cloyd800 on 2012-04-29
Nano if it's available.  If not, then you always know vi(seeing as it's native to UNIX) is available which would be my second preference.

---

### Post by zombifier25 on 2012-04-30
I used Emacs some time ago, and it's really easy to use if you know the commands (which are also easy to remember) However, Emacs is f***ing heavy and is not installed by default on almost all UNIX systems (except for rms's personal computer I think), so I no longer use it.
Vim is hard to use, really hard to use, but if you managed to memorize the commands, editing complicated files on it will be really fast.
Nano is my preferred choice of command-line editing. It's easy and quick if you are not editing really big files (ideally a conky config)

---

### Post by josephmills on 2012-04-30
I like emacs a real lot and use it a bunch but it is a funny program to say the least

---

### Post by lykwydchykyn on 2012-04-30
> **josephmills said:**
> I like emacs a real lot and use it a bunch but it is a funny program to say the least


[center][img]http://imgs.xkcd.com/comics/real_programmers.png[/img][/center]

I know it's required by international Internet law to post that comic in any thread about Emacs, but twice is pushing it, isn't it?

(Hint: see post #24)

---

### Post by josephmills on 2012-04-30
> **lykwydchykyn said:**
> I know it's required by international Internet law to post that comic in any thread about Emacs, but twice is pushing it, isn't it?

(Hint: see post #24)


woops missed that

---

### Post by nothingspecial on 2012-04-30
> **lykwydchykyn said:**
> I know it's required by international Internet law to post that comic in any thread about Emacs, but twice is pushing it, isn't it?

(Hint: see post #24)

> **josephmills said:**
> woops missed that

The law is once per year, so it's ok :P

---

### Post by codemaniac on 2012-04-30
A die hard VIM fan .

---

### Post by Biddlesby on 2012-05-01
Since I first posted this threada year ago, I've taken up a programming role, and now I'm a die-hard emacs fan. I'm pretty sure it makes me rather odd in the head, but hey \\:D/

---

### Post by lykwydchykyn on 2012-05-01
> **Biddlesby said:**
> Since I first posted this threada year ago, I've taken up a programming role, and now I'm a die-hard emacs fan. I'm pretty sure it makes me rather odd in the head, but hey \\:D/

Welcome to the fold. We're all odd in the head here.

---

### Post by F.G. on 2012-05-01
> **lykwydchykyn said:**
> Welcome to the fold. We're all odd in the head here.
odd in the head? speak for yourself, i use vi for most of my editing.

---

### Post by 1clue on 2012-05-01
Vi users are definitely NOT odd in the head.

It must be an emacs thing.

<duck-and-run/>
:popcorn: :) :P :lolflag:

---

### Post by Erik1984 on 2012-05-02
> **matthew.ball said:**
> 
...
[This]("http://dev.pocoo.org/%7Egbrandl/emacs2.png") is the modern front-end for emacs (of course, this isn't vanilla emacs. There are a few extensions in action there, but they're all very easy to set-up). The only obvious thing I have found missing in emacs is an in-built form-builder. There is some amazing integration between emacs and development tools, but most people just don't look for it (or don't know how, not that it's very difficult to find). Projects like [CEDET]("http://cedet.sourceforge.net/") have attempted to bundle everything you would need to get the ultimate IDE experience out of emacs.
...


Which extensions are needed to make Emacs look like that? Seems like a very productive setup.

---

### Post by lykwydchykyn on 2012-05-02
> **Euroman said:**
> Which extensions are needed to make Emacs look like that? Seems like a very productive setup.

ECB (emacs code browser).  I believe it's still in the repositories.  I tried it for a while, but didn't really need it for what I do.

---

