---
title: "gEcrit Python editor announcement!"
date: 2011-02-28
forum: The Cafe
---

### Post by cgroza on 2011-02-28
Hello, I have developed a python IDE for my own needs and I want to share it. 
It is build in wxPython and python. This is the list of features:


[LIST]
[*]Pyton indentation
[*]Line Numbers
[*]Code folding
[*]Syntax Highlight
[*]Shell Emulator
[*]Code Completion (ALPHA)
[*]Program runner
[*]Source Browser
[*]Indentation guides
[*]White space indicator
[*]Autosaving
[*]Edge Line
[*]Multitabing
[*]Printer
[*]Jump to line
[*]Word search
[*]Word replace
[*]Zooming
[*]Undo/Redo
[*]Pastebin.com code submit
[*]Python syntax checking (beta)
[*]Mass line indentation
[*]Mass line dedentation
[*]Autocompletiton
[*]Bad Brace Check
[*]Spell Checking
[*]Tree File Browser
[/LIST]
The editor is based on Scintilla, which provides a wide set of built in features.

So far I published it on:

[http://sourceforge.net/projects/gecrit/](http://sourceforge.net/projects/gecrit/)
[http://mac.softpedia.com/get/Word-Processing/gEcrit.shtml](http://mac.softpedia.com/get/Word-Processing/gEcrit.shtml)
[https://github.com/cgroza/gEcrit](https://github.com/cgroza/gEcrit)
[http://gnomefiles.org/content/show.php?content=139277](http://gnomefiles.org/content/show.php?content=139277)
[http://freshmeat.net/projects/gecrit](http://freshmeat.net/projects/gecrit)

If anyone has suggestions, I would be grateful.

The project is young (around 3 months).

The documentation is under way (been busy with coding and forgot about it).
So far it is just me supporting it.

Here is a main screenshot:

---

### Post by cgroza on 2011-03-01
bump

---

### Post by ErikNJ on 2011-03-01
That's pretty cool - thanks for sharing it.  I haven't done much in python.  I suppose if I were to ever attempt a larger project than isn't well-served by gedit, I'd have a look at some IDEs.  I like the concept of yours (it neatens up dealing with the fussy whitespace of python nicely).

---

### Post by Queue29 on 2011-03-02
> Error: Wrong architecture 'i386'

C'mon dude, it's written in python. Packaging for x64 is a 1 line change.


After using it for about 10 minutes, I took a few notes:

```


gEcrit

i386 ONLY

Icons suck (photographic, should be cartoon)

Source browser cuts off function name, more importantly does not display file name

Need explicit raw_input() at the end of __main__ to keep terminal window open

Syntax highlighting doesn't turn on until you click the "Syntax Highlight" 
option TWICE

Edge line doesn't appear anywhere
    Shows up only after opening a new file
    
Source Browser can be opened twice!
    Once in settings, then another parallel one can be opened with view->Source browser
    
Autoindentation width and tabwidth are two different things??

Very noisy terminal output:

gecrit 
<wx._gdi.Font; proxy of <Swig Object of type 'wxFont *' at 0x2958340> >
Traceback (most recent call last):
  File "editorClass.py", line 441, in <lambda>
    cur_doc.Bind(wx.EVT_KEY_UP, lambda event: AutoIndent(event,text_id))
  File "/usr/bin/gEcrit/bin/TinyFeatures.py", line 31, in AutoIndent
    if cur_doc.GetLine(line-1)[-2] == ":":
IndexError: string index out of range
Traceback (most recent call last):
  File "editorClass.py", line 441, in <lambda>
    cur_doc.Bind(wx.EVT_KEY_UP, lambda event: AutoIndent(event,text_id))
  File "/usr/bin/gEcrit/bin/TinyFeatures.py", line 31, in AutoIndent
    if cur_doc.GetLine(line-1)[-2] == ":":
IndexError: string index out of range
Traceback (most recent call last):
  File "editorClass.py", line 441, in <lambda>
    cur_doc.Bind(wx.EVT_KEY_UP, lambda event: AutoIndent(event,text_id))
  File "/usr/bin/gEcrit/bin/TinyFeatures.py", line 31, in AutoIndent
    if cur_doc.GetLine(line-1)[-2] == ":":
IndexError: string index out of range
Traceback (most recent call last):
  File "editorClass.py", line 441, in <lambda>
    cur_doc.Bind(wx.EVT_KEY_UP, lambda event: AutoIndent(event,text_id))
  File "/usr/bin/gEcrit/bin/TinyFeatures.py", line 31, in AutoIndent
    if cur_doc.GetLine(line-1)[-2] == ":":
IndexError: string index out of range
Child process pid 12196
Child process pid 12198
Unhandled escape sequence: [?12l
Unhandled escape sequence: [?25h
Unhandled escape sequence: [?1049h
Unhandled escape sequence: [1;24r
Unhandled escape sequence: [4l
Unhandled escape sequence: [?7h
Unhandled escape sequence: [?1h
Unhandled escape sequence: [?25l
Unhandled escape sequence: [?1000h
Unhandled escape sequence: [26X
Unhandled escape sequence: [26X
Unhandled escape sequence: [26X
Unhandled escape sequence: [25X
Unhandled escape sequence: [14;23r
Unhandled escape sequence: [2T
Unhandled escape sequence: [1;24r
Unhandled escape sequence: [?12l
Unhandled escape sequence: [?25h
Unhandled escape sequence: [?1000l
Unhandled escape sequence: [?1049l
Unhandled escape sequence: [?1l



Good:
    code folding works!
    python shell, os shell, 

```

---

### Post by cgroza on 2011-03-02
> **Queue29 said:**
> C'mon dude, it's written in python. Packaging for x64 is a 1 line change.


After using it for about 10 minutes, I took a few notes:

```


gEcrit

i386 ONLY

Icons suck (photographic, should be cartoon)

Source browser cuts off function name, more importantly does not display file name

Need explicit raw_input() at the end of __main__ to keep terminal window open

Syntax highlighting doesn't turn on until you click the "Syntax Highlight" 
option TWICE

Edge line doesn't appear anywhere
    Shows up only after opening a new file
    
Source Browser can be opened twice!
    Once in settings, then another parallel one can be opened with view->Source browser
    
Autoindentation width and tabwidth are two different things??

Very noisy terminal output:

gecrit 
<wx._gdi.Font; proxy of <Swig Object of type 'wxFont *' at 0x2958340> >
Traceback (most recent call last):
  File "editorClass.py", line 441, in <lambda>
    cur_doc.Bind(wx.EVT_KEY_UP, lambda event: AutoIndent(event,text_id))
  File "/usr/bin/gEcrit/bin/TinyFeatures.py", line 31, in AutoIndent
    if cur_doc.GetLine(line-1)[-2] == ":":
IndexError: string index out of range
Traceback (most recent call last):
  File "editorClass.py", line 441, in <lambda>
    cur_doc.Bind(wx.EVT_KEY_UP, lambda event: AutoIndent(event,text_id))
  File "/usr/bin/gEcrit/bin/TinyFeatures.py", line 31, in AutoIndent
    if cur_doc.GetLine(line-1)[-2] == ":":
IndexError: string index out of range
Traceback (most recent call last):
  File "editorClass.py", line 441, in <lambda>
    cur_doc.Bind(wx.EVT_KEY_UP, lambda event: AutoIndent(event,text_id))
  File "/usr/bin/gEcrit/bin/TinyFeatures.py", line 31, in AutoIndent
    if cur_doc.GetLine(line-1)[-2] == ":":
IndexError: string index out of range
Traceback (most recent call last):
  File "editorClass.py", line 441, in <lambda>
    cur_doc.Bind(wx.EVT_KEY_UP, lambda event: AutoIndent(event,text_id))
  File "/usr/bin/gEcrit/bin/TinyFeatures.py", line 31, in AutoIndent
    if cur_doc.GetLine(line-1)[-2] == ":":
IndexError: string index out of range
Child process pid 12196
Child process pid 12198
Unhandled escape sequence: [?12l
Unhandled escape sequence: [?25h
Unhandled escape sequence: [?1049h
Unhandled escape sequence: [1;24r
Unhandled escape sequence: [4l
Unhandled escape sequence: [?7h
Unhandled escape sequence: [?1h
Unhandled escape sequence: [?25l
Unhandled escape sequence: [?1000h
Unhandled escape sequence: [26X
Unhandled escape sequence: [26X
Unhandled escape sequence: [26X
Unhandled escape sequence: [25X
Unhandled escape sequence: [14;23r
Unhandled escape sequence: [2T
Unhandled escape sequence: [1;24r
Unhandled escape sequence: [?12l
Unhandled escape sequence: [?25h
Unhandled escape sequence: [?1000l
Unhandled escape sequence: [?1049l
Unhandled escape sequence: [?1l



Good:
    code folding works!
    python shell, os shell, 

```


You need to force the architecture:
sudo dpkg -i --force-architecture <file here>

Thank you for the critics, the project is still at the beginning. The syntax highlight turns on only on a python file. If it does not have a .py extension, it will not turn on.
Tab width is the size in spaces to display when using tabs.
The most of the terminal output is debugging info for me, you can ignore it.
Thanks, now I have things to fix! :D
EDIT: Fixed the syntax highlight bug.

---

### Post by cgroza on 2011-03-02
> **ErikNJ said:**
> That's pretty cool - thanks for sharing it.  I haven't done much in python.  I suppose if I were to ever attempt a larger project than isn't well-served by gedit, I'd have a look at some IDEs.  I like the concept of yours (it neatens up dealing with the fussy whitespace of python nicely).

Thank you, the project is still new and has many rough edges, but for the IDE part, you might want to try geany (I use it to develop this thing).

---

### Post by cgroza on 2011-03-02
The deb adds a menu launcher now, no icon though.

---

### Post by NightwishFan on 2011-03-02
It looks great to me. I will probably give it a go some time as I like python. :)

---

### Post by cgroza on 2011-03-02
> **NightwishFan said:**
> It looks great to me. I will probably give it a go some time as I like python. :)

Glad to have good impressions around here. Thank you.
Tomorrow a release will be out, with some bug fixes an a new feature.

---

### Post by cgroza on 2011-03-02
> **cood22 said:**
> [FONT=Verdana]The movies fans usually have a lot of DVDs, most of them may ask how to rip the DVD movies freely, now would recommend guys a iovSoft **[COLOR=#666666][DVD Ripper]("http://www.ainsofts.com/dvd-ripper-p.html"),[/COLOR]**[/FONT][FONT=Verdana]is a really fully featured DVD ripping and video conversion soft, such as ripping**[COLOR=#666666] [DVD to AVI]("http://www.ainsofts.com/dvd-to-avi-converter.html")[/COLOR]**, **[COLOR=#666666][DVD to MPEG]("http://www.ainsofts.com/dvd-ripper-p.html")[/COLOR]**, and DVD to WMV, MP4, DivX, XviD, FLV, 3GP, MOV, RM, it could also extract audio files from DVDs and convert**[COLOR=#666666] [DVD to MP3]("http://www.ainsofts.com/dvd-to-mp3-converter.html")[/COLOR]**, WMA WAV, OGG, RA audios. Besides, it supports convert DVD to most multimedia players, all the output formats are professionally optimized for best playing back, like converting **[COLOR=#666666][DVD to iPod]("http://www.ainsofts.com/dvd-to-ipod-converter.html")[/COLOR]**, iPhone, iPad, Apple TV, PSP, Xbox, Zune, NDS, Wii. Supplemented with iovSoft **[DVD Copy]("http://www.ainsofts.com/dvd-copy.html")**, enables you clone DVD movies to DVD 5 or DVD 9 quickly in higher quality.[/FONT]

I think you would have more benefits if you would create your own thread.
EDIT: Ignore, that post got deleted.

---

### Post by cgroza on 2011-03-03
Version 1.8.3 available, added support for "Recent Files" and fixed some bugs.

---

### Post by ukripper on 2011-03-04
Looks promising. I hope it matures enough to compete with pydev and komodo.

---

### Post by cgroza on 2011-03-04
> **ukripper said:**
> Looks promising. I hope it matures enough to compete with pydev and komodo.
I hope so too, :D, although it is a bit too optimistic.
I added auto brace completion. Will be included in the next release.

---

### Post by cgroza on 2011-03-05
New release available: 18.3.5

**Changes:** Added support for brace completion, now the  file dialogs will open in the last visited place and the editor will  open with the last file opened loaded. Remove trailing spaces option was added. Fixed some minor bugs.

---

### Post by cgroza on 2011-03-05
bump

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-03-05
In a nutshell, what does it do that I can't do in vim/emacs with existing macros and 20 lines of userscripts?

---

### Post by cgroza on 2011-03-05
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> In a nutshell, what does it do that I can't do in vim/emacs with existing macros and 20 lines of userscripts?
So far nothing special, but I am planning to get some regular expression support for this and a class hierarchy tree. One step at a time.

---

### Post by cgroza on 2011-03-09
> **Queue29 said:**
> 
```

Need explicit raw_input() at the end of __main__ to keep terminal window open

```
Fixed, will be available in next release which is 2 days away.

---

### Post by cgroza on 2011-03-10
Released 1.4.5: [https://sourceforge.net/projects/gecrit/](https://sourceforge.net/projects/gecrit/)
Freshmeat: [http://freshmeat.net/projects/gecrit](http://freshmeat.net/projects/gecrit)

---

### Post by cgroza on 2011-03-13
Just released 1.8.5:
[http://freshmeat.net/projects/gecrit](http://freshmeat.net/projects/gecrit)
Added some new features and bugfixes.

---

### Post by cgroza on 2011-03-20
Just released 1.8.7: [http://freshmeat.net/projects/gecrit](http://freshmeat.net/projects/gecrit)
Added new features.

---

### Post by cgroza on 2011-04-05
Just wanted to say that version 1.9 was released and it features plugin support. I am currently developing an interface to make the development faster via plugins.

Freshmeat page: [http://freshmeat.net/projects/gecrit](http://freshmeat.net/projects/gecrit)

---

### Post by ukripper on 2011-04-06
Can there be tool included to refactor code easily and unit test support (something like JUNIT for java)? Unit test module is good enough for it but thought  extra tool could help development.

---

### Post by cgroza on 2011-04-06
> **ukripper said:**
> Can there be tool included to refactor code easily and unit test support (something like JUNIT for java)? Unit test module is good enough for it but thought  extra tool could help development.
Hmm, this might be in the next release. I will look into other projects to see how code refactoring is done. Maybe I will get inspired by PythonTidy.
Thanks.

---

### Post by rudihawk on 2011-04-06
I don't do any coding but I admire what you are doing!

---

### Post by cgroza on 2011-04-06
> **rudihawk said:**
> I don't do any coding but I admire what you are doing!
This is by far the best thing anyone said to me.
Thank you!

---

### Post by ukripper on 2011-04-07
> **cgroza said:**
> Hmm, this might be in the next release. I will look into other projects to see how code refactoring is done. Maybe I will get inspired by PythonTidy.
Thanks.

Thanks mate.

Is it going to hit repos at some stage?

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-04-07
To this day, I fail to see the point of using a graphical interface and all the resource waste that entails, just to edit plaintext files. Please enlighten me.

---

### Post by ukripper on 2011-04-07
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> To this day, I fail to see the point of using a graphical interface and all the resource waste that entails, just to edit plaintext files. Please enlighten me.

Personal preference

---

### Post by cgroza on 2011-04-07
> **ukripper said:**
> Thanks mate.

Is it going to hit repos at some stage?

I hope so. I will do my best to package it so it will be accepted by Debian or Ubuntu.

---

### Post by ukripper on 2011-04-08
> **cgroza said:**
> I hope so. I will do my best to package it so it will be accepted by Debian or Ubuntu.

Thanks appreciate your work and i hope it hit repos soon.

---

### Post by gaokai on 2011-04-08
Good tool:lolflag:

---

### Post by cgroza on 2011-04-08
> **gaokai said:**
> Good tool:lolflag:
I do not know what to think, is that sarcasm?

---

### Post by cgroza on 2011-04-08
2.0 Released!
 [http://freshmeat.net/projects/gecrit](http://freshmeat.net/projects/gecrit)
2 new plugins and some serious bug was fixed.

---

### Post by ukripper on 2011-04-11
> **cgroza said:**
> 2.0 Released!
 [http://freshmeat.net/projects/gecrit](http://freshmeat.net/projects/gecrit)
2 new plugins and some serious bug was fixed.

Is there documentation for plugins I could use? thanks

---

### Post by cgroza on 2011-04-12
> **ukripper said:**
> Is there documentation for plugins I could use? thanks
Documentation, I have some pydoc files but they are outdated. I will generate the new ones tonight and post them on sourceforge.


Version 2.1 released.
Some GUI changes, new plugin(Abbreviation autocompletion), tree file browser improved and the source browser is now a plugin.

---

### Post by cgroza on 2011-04-12
> **ukripper said:**
> Is there documentation for plugins I could use? thanks
I uploaded the documentation in the Documentation folder on source forge.

---

### Post by ukripper on 2011-04-13
> **cgroza said:**
> I uploaded the documentation in the Documentation folder on source forge.

Thank you cgroza, will check it out!

Cheers

---

### Post by rudihawk on 2011-04-13
Any luck with getting it included into the repos?

---

### Post by cgroza on 2011-04-13
> **rudihawk said:**
> Any luck with getting it included into the repos?
I can do the package. This week I will submit it to revu.

---

### Post by ukripper on 2011-04-14
> **cgroza said:**
> I can do the package. This week I will submit it to revu.

Brilliant!! thanks

---

### Post by cgroza on 2011-04-14
I reached a dead end with the packaging, I can do a deb but not the source package. Maybe there is a volunteer somewhere with the right skills to help me.

Sorry.

---

### Post by cgroza on 2011-04-16
2.2 is out:
[http://freshmeat.net/projects/gecrit](http://freshmeat.net/projects/gecrit)

---

### Post by cgroza on 2011-04-20
2.3 is out!

Syntax highlight for C like languages, Java, and Ruby was added.
New plugin and bugfixes.

---

### Post by cgroza on 2011-04-25
Version 2.4 is out.

Support for window docking was added. Code completion is done via pyctags now.
Improved a plugin:

Freshmeat: [http://freshmeat.net/projects/gecrit](http://freshmeat.net/projects/gecrit)
SourceForge: [https://sourceforge.net/projects/gecrit/](https://sourceforge.net/projects/gecrit/)

---

### Post by cgroza on 2011-04-30
New version released: 2.5
**Changes:** This version adds session support for the  editor. It can save all the open tabs, window layout, selected document  and restore them at startup.  A plugin was added that allows you to have an unlimited number of  terminals for any shells. All it needs is a path to the shell  interpreter.  The spell checker was moved to a plugin and now it is possible to spell  check a text selection.  A document clone plugin was added.  The default text function was moved to a plugin called StampIt.
Link:
[http://freshmeat.net/projects/gecrit](http://freshmeat.net/projects/gecrit)

---

### Post by cgroza on 2011-07-16
Hello again.
Thanks to a Debian packager, there is a gEcrit PPA now.
PPA page:
[https://launchpad.net/~vincent-c/+archive/gecrit](https://launchpad.net/~vincent-c/+archive/gecrit)

---

### Post by NightwishFan on 2011-07-16
> **cgroza said:**
> Hello again.
Thanks to a Debian packager, there is a gEcrit PPA now.
PPA page:
[https://launchpad.net/~vincent-c/+archive/gecrit](https://launchpad.net/~vincent-c/+archive/gecrit)

Awesome! :) Any chance of it being maintained in debian?

---

### Post by cgroza on 2011-07-16
> **NightwishFan said:**
> Awesome! :) Any chance of it being maintained in debian?
Well the packager that helped me submitted it to the mentors. Too bad it's too late for it to get into Oneiric, maybe in 12.04.

---

### Post by cgroza on 2011-07-26
Just wanted to let you know that gEcrit made it into Debian Unstable and it is possible that Ubuntu 12.04 will pick it up.

---

### Post by NightwishFan on 2011-07-26
> **cgroza said:**
> Just wanted to let you know that gEcrit made it into Debian Unstable and it is possible that Ubuntu 12.04 will pick it up.

Seems it has. Great job! :)
```
user@debian-ghibli:~$ apt-cache policy gecrit 
gecrit:
  Installed: (none)
  Candidate: 2.7.1-1
  Version table:
     2.7.1-1 0
        600 http://debian.osuosl.org/debian/ unstable/main amd64 Packages
```

---

