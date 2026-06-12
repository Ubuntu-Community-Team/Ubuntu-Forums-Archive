---
title: "Scribes: A Text Editor for GNOME"
date: 2006-10-16
forum: The Cafe
---

### Post by Mystilleef on 2006-10-16
Hello,

Scribes 0.3.1 has been released.

Release Note:  [http://scribes.sourceforge.net/release-note-0-3-1.html](http://scribes.sourceforge.net/release-note-0-3-1.html)

Flash Demo: [http://scribes.sf.net/demo.htm](http://scribes.sf.net/demo.htm)

website: [http://scribes.sf.net/](http://scribes.sf.net/)

download: [http://scribes.sf.net/download.html](http://scribes.sf.net/download.html)

templates: [http://scribes.sf.net/templates.tar.bz2](http://scribes.sf.net/templates.tar.bz2) 

Thanks

---

### Post by IYY on 2006-10-16
I'm a vi user so I won't be using this, but it certainly looks like a neat little tool for programmers.

---

### Post by _lynX on 2006-10-16
> **Mystilleef said:**
> Hello,

Apologies if I'm posting in the wrong forum. I need your help testing Scribes before I make a public release. I appreciate any feedback you have.

Flash Demo: [http://scribes.sf.net/demo.htm](http://scribes.sf.net/demo.htm)

website: [http://scribes.sf.net/](http://scribes.sf.net/)

download: [http://scribes.sf.net/download.html](http://scribes.sf.net/download.html)

templates: [http://scribes.sf.net/templates.tar.bz2](http://scribes.sf.net/templates.tar.bz2) 

I'll upload a deb file immediately the maintainer provides one.

Thanks

Very cool. I'll definitely give it a try.

---

### Post by PriceChild on 2006-10-16
Just thought i'd point out [http://scribes.sourceforge.net/demo.htm](http://scribes.sourceforge.net/demo.htm) doesnt' work for me....

I had a problem with flash earlier on youtube... maybe its just me.

Edgy's flash won't reinstall for me....

---

### Post by _lynX on 2006-10-16
This requires Gtk 2.10.0, and the latest Gtk version in the repositories is 2.8.20. Just thought you might like to know that.

---

### Post by Mystilleef on 2006-10-17
> **IYY said:**
> I'm a vi user so I won't be using this, but it certainly looks like a neat little tool for programmers.

I was a VIM power user for years. I've become impatient with it over time. Now I only use it to edit configuration files in non-GUI mode. What made me like VIM is its powerful text processing capabilities. Many of which I implemented in Scribes. I can't say I miss VIM. :-)

---

### Post by Mystilleef on 2006-10-17
> **PriceChild said:**
> Just thought i'd point out [http://scribes.sourceforge.net/demo.htm](http://scribes.sourceforge.net/demo.htm) doesnt' work for me....

I had a problem with flash earlier on youtube... maybe its just me.

Edgy's flash won't reinstall for me....

That's unfortunate. I know AMD64 users have problems with Flash. Are you one by chance? 

Here is an old GIF demo.

[http://www.minds.may.ie/~dez/images/blog/scribes.html](http://www.minds.may.ie/~dez/images/blog/scribes.html)

---

### Post by Mystilleef on 2006-10-17
> **_lynX said:**
> This requires Gtk 2.10.0, and the latest Gtk version in the repositories is 2.8.20. Just thought you might like to know that.

This release is targetted at testers, not users. I assume most testers are already on Edgy. It's unfortunate Ubuntu hasn't upgraded to GTK 2.10. Almost all other major distros have I believe. I'm still new to Ubuntu so I don't understand how the upgrade process works. I come from Gentoo were an upstream upgrade also means an upgrade for users. Plus GTK 2.10 has been out for months now. Does anyone know why it's not in Ubuntu? I have it here on Edgy, however.

---

### Post by Wolki on 2006-10-17
> **Mystilleef said:**
> Plus GTK 2.10 has been out for months now. Does anyone know why it's not in Ubuntu? I have it here on Edgy, however.

Stable releases only get security fixes and critical bug fixes. This reduces the load on the maintainers and reduces the possibility of upgrades within a release breaking working functionality.

Anyway, I've been plaing with scribes 2.something some time ago, and the new release seems to work well. I've noticed that the document browser feels a bit jumpy though, hiding/closing the window and restarting it again.

I'm really looking forward to scribes future, its interface often feels like a fresh breath of air and is sometimes annoying, a good sign I'd say. :) gedit has some nice features though (mostly through plugins), and i don'T want to switch text editors all the time :-/

Oh, and please consider implementing the standart gnome toolbar options (like text beside/below icons). Having icons only is fine on lower resolutions; but on higher resolutions, especially with a small screen, it's a pain to hit them with the mouse.

[edit] Oh, and making a change to a document, then undoing will not remove the * from the titlebar, though there are no unsaved changes.

[edit2] Yet another thing I noticed: If you import templates that exist, they will be added again with a number added to their name. It would be nice for collaboration on templates if that would only happen if the templates were not identical - I could import someone else's templates and not have to remove all the duplicates.
And it would be especially great if templates could be shared between scribes and gedit snippets - easy migration or even a unified default template set between GNOME text editors would rock.

And before I forget it, thank you for such a nice program. :)

[edit3] yay for another edit! I noticed that the bookmark functions from the right-click menu don't seem to work, using the keyboard shortcuts works though.
The manual lists the keybinding for go to line twice. And shouldn't "Rename a File" be called "Save under a different name", since the original file will still be there?

---

### Post by chaosgeisterchen on 2006-10-17
Seems to be VERY cool. But only THAT great for Python? Or does it support all those features for other languages too..

---

### Post by Wolki on 2006-10-17
> **chaosgeisterchen said:**
> Seems to be VERY cool. But only THAT great for Python? Or does it support all those features for other languages too..

It will work for all languages gtksourceview supports (a lot), and you can do general stuff that will work everywhere. Not all languages have exhaustive templates by default, though :)

---

### Post by chaosgeisterchen on 2006-10-17
Hmh.. what about PHP and Ruby :) ?

---

### Post by punkforpez on 2006-10-17
just compiled it.  i really see a lot of potential in scribes.  it already feels polished and i love the minimalistic approach it takes.  i really hate big rows of icons getting in the way.  excellent work so far!

some things i'd like to see implemented:

the ability to switch syntax highlighting on the fly.  i could only get the colors rolling when i loaded a preexisting source file.  i'd like to be able to start with a clean slate and set the colors right away based on my environment.

a full-screen option would be great too.  sometimes it's nice to just have the code and nothing else in the way. 

and a screen-splitting option, ala emacs.  i must admit i'm an emacs junkie and i like the idea of working on multiple files on the same screen.

please don't judge me because i'm pro-emacs and you're vim.  your editor is great and i really am looking forward to future releases!

---

### Post by Wolki on 2006-10-17
I'm not sure there is a template library for ruby or php somewhere, at least it's not included in the template collection from the scribes homepage. It's not that bad, however, since you can create one yourself and then easily share it with other people. Creating them is easy too.

punkforpez: metacity can force windows to fullscreen. Simply define a keyboard shortcut in System > Preferences > Keyboard Shortcuts, press that shortcut and scribes will be fullscreen.

---

### Post by punkforpez on 2006-10-17
> **Wolki said:**
> I'm not sure there is a template library for ruby or php somewhere, at least it's not included in the template collection from the scribes homepage. It's not that bad, however, since you can create one yourself and then easily share it with other people. Creating them is easy too.

punkforpez: metacity can force windows to fullscreen. Simply define a keyboard shortcut in System > Preferences > Keyboard Shortcuts, press that shortcut and scribes will be fullscreen.

oh how did i ever not know that?!?! thank you! ^-^

---

### Post by Mystilleef on 2006-10-17
> **Wolki said:**
> Stable releases only get security fixes and critical bug fixes. This reduces the load on the maintainers and reduces the possibility of upgrades within a release breaking working functionality.


Coming from Gentoo, I'm a bit dissapointed, but oh well. Thanks for the explanation.

> **Wolki said:**
> 
Anyway, I've been plaing with scribes 2.something some time ago, and the new release seems to work well. I've noticed that the document browser feels a bit jumpy though, hiding/closing the window and restarting it again.


Can you explain further? Do you mean it doesn't show quickly?

> **Wolki said:**
> 
I'm really looking forward to scribes future, its interface often feels like a fresh breath of air and is sometimes annoying, a good sign I'd say. :) gedit has some nice features though (mostly through plugins), and i don'T want to switch text editors all the time :-/

Oh, and please consider implementing the standart gnome toolbar options (like text beside/below icons). Having icons only is fine on lower resolutions; but on higher resolutions, especially with a small screen, it's a pain to hit them with the mouse.


That was possible in the past. But they looked ugly, and the names were confusing people that initially tested Scribes. So I removed them. They don't serve any purpose.

> **Wolki said:**
> 
[edit] Oh, and making a change to a document, then undoing will not remove the * from the titlebar, though there are no unsaved changes.


The * signifies a document has been modified. Even undoing a document is a form of modification.

> **Wolki said:**
> 
[edit2] Yet another thing I noticed: If you import templates that exist, they will be added again with a number added to their name. It would be nice for collaboration on templates if that would only happen if the templates were not identical - I could import someone else's templates and not have to remove all the duplicates.

Template triggers have to have unique names. It's less confusing on my part and the part of users.

> **Wolki said:**
> 
And it would be especially great if templates could be shared between scribes and gedit snippets - easy migration or even a unified default template set between GNOME text editors would rock.

Scribes had Templates before Gedit. Our implementations differ. And I don't like Gedit's implementation. Maybe in the future someone will write a plug-in to convert Gedit's to Scribes and vice-versa.

> **Wolki said:**
> 
[edit3] yay for another edit! I noticed that the bookmark functions from the right-click menu don't seem to work, using the keyboard shortcuts works though.

Ah yes, thanks.  ](*,)

> **Wolki said:**
> 
The manual lists the keybinding for go to line twice. 

Thanks !    ](*,)

> **Wolki said:**
> 
And shouldn't "Rename a File" be called "Save under a different name", since the original file will still be there?

Or better yet, "Create a new file, give it a name, while doing nothing to the old file". :-D I hope you get my drift. We don't have to be too pedantic with the interface. And the user doesn't really have to know all that.

Thanks for your feedback, it's really appreciated. Look forward to more.

---

### Post by TheMono on 2006-10-17
"Create a new file, give it a name, while doing nothing to the old file" and "Rename a File" are radically different things - mainly because the second implies altering the original...

Possibly borrow from Photoshop - "Save a copy"?

---

### Post by Mystilleef on 2006-10-17
> **punkforpez said:**
> just compiled it.  i really see a lot of potential in scribes.  it already feels polished and i love the minimalistic approach it takes.  i really hate big rows of icons getting in the way.  excellent work so far!

some things i'd like to see implemented:

the ability to switch syntax highlighting on the fly.  i could only get the colors rolling when i loaded a preexisting source file.  i'd like to be able to start with a clean slate and set the colors right away based on my environment.

How about renaming a file before editing it? :-D
That way you wouldn't need to manually set syntax colors. The editor will do it for you.

> **punkforpez said:**
> 
a full-screen option would be great too.  sometimes it's nice to just have the code and nothing else in the way. 


Press F11 for full-screen mode. See the manual for other operations the you can perform with the editor.

> **punkforpez said:**
> 
and a screen-splitting option, ala emacs.  i must admit i'm an emacs junkie and i like the idea of working on multiple files on the same screen.


Ewww, split screen! Kidding! :-D Scribes was not designed to be an MDI. More details on this and Tabs on [my blog]("http://mystilleef.blogspot.com/2006/10/no-tabs-why.html")

> **punkforpez said:**
> 
please don't judge me because i'm pro-emacs and you're vim.  your editor is great and i really am looking forward to future releases!

Ah you're an emacs lover. Die EMACS Die.
Long live VIM! Kidding! :-D

---

### Post by Mystilleef on 2006-10-17
> **chaosgeisterchen said:**
> Hmh.. what about PHP and Ruby :) ?

It supports both.

---

### Post by asimon on 2006-10-17
Compiles and works fine on current Kubuntu Edgy.

Looks spiffy and friendly.

A minor bug I encountered: all editor windows created by CTRL+N are not shown in the document switcher (F9). They appear in the switcher not until they are saved.

I think it should be possible to set the tab stop options differently for different file types. For example for Ruby the common tab-width is 2, whereas most C/C++ projects use 4 or 8. This would be convenient if you work for example on Ruby/Python and C files at the same time, which is not uncommon.

Another thing: I found no way to quickly change the language of the spell checking between different documents. Not all documents I work on use the language of my desktop.

---

### Post by Mystilleef on 2006-10-17
> **asimon said:**
> Compiles and works fine on current Kubuntu Edgy.

Looks spiffy and friendly.

A minor bug I encountered: all editor windows created by CTRL+N are not shown in the document switcher (F9). They appear in the switcher not until they are saved.

The document switcher only shows windows containing documents. If you have several empty windows the document switcher ignores them. The point of the switcher is to switch to open documents not empty windows.

> **asimon said:**
> 
I think it should be possible to set the tab stop options differently for different file types. For example for Ruby the common tab-width is 2, whereas most C/C++ projects use 4 or 8. This would be convenient if you work for example on Ruby/Python and C files at the same time, which is not uncommon.

This is tough to do because GNOME apps use the same configuration deamon, GConf. I'd have to write my own configuration system and create a database that keeps track of each file to implement this. It seems to be a lot of work for little gain. I've have plans to implement something like VIM/EMACS/KATE modes however. Maybe that could solve this problem.

> **asimon said:**
> 
Another thing: I found no way to quickly change the language of the spell checking between different documents. Not all documents I work on use the language of my desktop.


Yes, I'll look into this for the next major release. 

Thanks for your feedback. Look forward to more.

---

### Post by asimon on 2006-10-17
> **Mystilleef said:**
> The document switcher only shows windows containing documents. If you have several empty windows the document switcher ignores them. The point of the switcher is to switch to open documents not empty windows.
But if I create a new window and enter something it's not empty anymore. In this case, shouldn't it appear in the switcher, i.e. unsaved non-empty documents? I first have to save it to make it reachable through the switcher (it's no big issue, just feels strange to me).

> **Mystilleef said:**
> 
This is tough to do because GNOME apps use the same configuration deamon, GConf. I'd have to write my own configuration system and create a database that keeps track of each file to implement this. It seems to be a lot of work for little gain. I've have plans to implement something like VIM/EMACS/KATE modes however. Maybe that could solve this problem.
Yes, that would definitely be cool, mode-lines solve the issue fine.

---

### Post by Mystilleef on 2006-10-17
> **asimon said:**
> But if I create a new window and enter something it's not empty anymore. In this case, shouldn't it appear in the switcher, i.e. unsaved non-empty documents? I first have to save it to make it reachable through the switcher (it's no big issue, just feels strange to me).

As far as Scribes is concerned a document is a reference to a file saved on your computer. If the window you're are working on does not refer to a file on your computer, Scribes does not treat is as a document.

---

### Post by chaosgeisterchen on 2006-10-17
> **Mystilleef said:**
> It supports both.

Fine that it supports both PHP and Ruby. If there is any certain support in languages missing I could also do some work to support this editor.

As I am a KDE-User I will be not target group for your programme, but I will certainly try it out. Thanks ;)

---

### Post by Mystilleef on 2006-10-17
> **chaosgeisterchen said:**
> Fine that it supports both PHP and Ruby. If there is any certain support in languages missing I could also do some work to support this editor.

As I am a KDE-User I will be not target group for your programme, but I will certainly try it out. Thanks ;)

I'd appreciate testing and feedback regardless of your favorite desktop environment or editor. :-)

Thanks

---

### Post by asimon on 2006-10-17
I am curious. Is there a special reason why scribes, when called from the command line, needs the '-n' option to create a new file? Most editors automatically create a new file if the file you specify on the command line does not already exist.

Another thing, the [feature page](http://scribes.sourceforge.net/features.html) lists among others 'Automatic indentation'. But this is not yet implemented or am I missing something? For example, when typing in python mode something like 'def foo():' and press 'Enter' the next line is not automatically intended.

---

### Post by mostwanted on 2006-10-17
Very neat editor. I like it.

I made a deb if anyone is interested. I have no idea what the dependencies are though, you figure it out :)

---

### Post by Wolki on 2006-10-17
> **Mystilleef said:**
> Coming from Gentoo, I'm a bit dissapointed, but oh well. Thanks for the explanation.

I see what you mean, but it has advantages. Plus, Ubuntu releases fast, so for people who like new stuff, they can just upgrade to the new release.

> 
Can you explain further? Do you mean it doesn't show quickly?

Exactly. I see the window disappearing and reappearing, if it already is visible on screen.

> That was possible in the past. But they looked ugly, and the names were confusing people that initially tested Scribes. So I removed them. They don't serve any purpose.

Well, they do serve te purpose of making the individual items larger. :) It's a big pain to hit the icons on my laptop.

> The * signifies a document has been modified. Even undoing a document is a form of modification.


But is this in any way relevant to the user, if the only real modification is that it was not modified? I noticed myself hitting ctrl-z repeatedly despite the message that there was nothing left to undo, because there was a star and it looked like I made some changes and would save them  (which I didn't want to, only view the document)

I guess it's a more philosophical question - If I rotate a picture 90° left four times, is it now in the same position or in a different one?

> Template triggers have to have unique names. It's less confusing on my part and the part of users.

What I meant is that the import shouldn't create a new template if the one to be imported is exactly the same as one I already have. If it's different, they should obviosly be imported, and if necessary with a different name. If a friend and I both have the . => self. python template, and I want to merge mine with my firends to use both, what benefit will a .-1 => self. template give me?

> Scribes had Templates before Gedit. Our implementations differ. And I don't like Gedit's implementation. Maybe in the future someone will write a plug-in to convert Gedit's to Scribes and vice-versa.

I know. Thanks for at least considering it.

> Or better yet, "Create a new file, give it a name, while doing nothing to the old file". :-D I hope you get my drift. We don't have to be too pedantic with the interface. And the user doesn't really have to know all that.

Yeah, but it would be sad if users feared to use it because they assume it would remove their original file, or assume it would end end up with a lot of copies they don't need. Maybe as TheMono suggests "Save a copy" or the old "Save As"?

> Thanks for your feedback, it's really appreciated. Look forward to more.

I will try my best. :)

One thing I thought of, and this might be complete crack, was that it would be nice to have a functionality that opens the parent folder in $filemanager. Such a function would make it very easy to open files that are in the same directory without a file sidebar (just press the combination, first few letters of the name, and return), and further enhance the spatial nature (strengthen link between folder and contents, and spatial nautilus has this nice "open parent folder" too. The good shortcut (alt-up) is already taken, however :-/

---

### Post by Buffalo Soldier on 2006-10-17
so far I like what I see :) I hope you will stay the course and keep on doing things your way. It would be nice to see where this project would end up.

---

### Post by skymt on 2006-10-17
I love it! I may even switch from Vim (stupid, no-templates-without-clunky-plugins Vim)!

---

### Post by Mystilleef on 2006-10-17
> **asimon said:**
> I am curious. Is there a special reason why scribes, when called from the command line, needs the '-n' option to create a new file? Most editors automatically create a new file if the file you specify on the command line does not already exist.

I follow the "explicit is better than implicit" rule when implementing behavior. If a user wants to open the file "foot.txt" and accidentally types "foo.txt", it would be rather annoying if Scribes created the file foo.txt and then opened it. It may even confuse the user. The right thing to do is to tell the user foo.txt does not exist.

> **asimon said:**
> 
Another thing, the [feature page]("http://scribes.sourceforge.net/features.html") lists among others 'Automatic indentation'. But this is not yet implemented or am I missing something? For example, when typing in python mode something like 'def foo():' and press 'Enter' the next line is not automatically intended.

There's a difference between automatic indentation and intelligent indentation. Automatic indentation indents based on the indentation level of the previous line. Intelligent indentation indents based on the source code type. Scribes currently only implements automatic indentation, not intelligent indentation. Intelligent indentation will be implemented as a language plug-in.

---

### Post by castrojo on 2006-10-17
I've been using this as my main text editor for a while and I really dig it, keep it up!

---

### Post by Mystilleef on 2006-10-17
> **Wolki said:**
> I see what you mean, but it has advantages. Plus, Ubuntu releases fast, so for people who like new stuff, they can just upgrade to the new release.



Exactly. I see the window disappearing and reappearing, if it already is visible on screen.

Perhaps you are experience redraw issues with GTK+? The document switcher shows up almost instantly for me. Maybe I used to GTK+ redraw problems. A lot people complain about it, so it's not unusual. I'm I getting the problem, right? Or have I derailed.? :-)

> **Wolki said:**
> 
But is this in any way relevant to the user, if the only real modification is that it was not modified? I noticed myself hitting ctrl-z repeatedly despite the message that there was nothing left to undo, because there was a star and it looked like I made some changes and would save them  (which I didn't want to, only view the document)

Well, the rule is if you see the *, then you have certainly modified the document. So what is a modified document? The moment you add, remove, or change text in the editing area, then the document is modified. How can you prevent modification? You can press F3 to toggle readonly mode. Readonly mode prevents you  from modifying the document.

 > **Wolki said:**
> 
I guess it's a more philosophical question - If I rotate a picture 90° left four times, is it now in the same position or in a different one?


Yes, it may well be. But most importantly it is a question of consistency. When a user sees *, the user should automatically know the document has be modified. In the next release I'm going to work of making the state of the document more explicit in the statusbar.

  > **Wolki said:**
> 
What I meant is that the import shouldn't create a new template if the one to be imported is exactly the same as one I already have. If it's different, they should obviosly be imported, and if necessary with a different name. If a friend and I both have the . => self. python template, and I want to merge mine with my firends to use both, what benefit will a .-1 => self. template give me?


Ah, I understand now. That's a pretty smart way to handle it. I never thought about it. The only problem I see is how does one determine the difference between templates? If the difference between templates is just one space or tab character at the end of the template, then we are back to square one. :-D

 > **Wolki said:**
> 
Yeah, but it would be sad if users feared to use it because they assume it would remove their original file, or assume it would end end up with a lot of copies they don't need. Maybe as TheMono suggests "Save a copy" or the old "Save As"?


I think most people who want to change the name of a file don't care what happens to the old file. Maybe I'm being presumptious.
  
> **Wolki said:**
> 
One thing I thought of, and this might be complete crack, was that it would be nice to have a functionality that opens the parent folder in $filemanager. Such a function would make it very easy to open files that are in the same directory without a file sidebar (just press the combination, first few letters of the name, and return), and further enhance the spatial nature (strengthen link between folder and contents, and spatial nautilus has this nice "open parent folder" too. The good shortcut (alt-up) is already taken, however :-/

Well, the open dialog already allows you to open files in the same folder. Scribes' implementation even remembers the last state of the open dialog. In fact, I encourage user to use open dialog as a file manager. You can even bookmark folders in open dialog. However, your idea is something that could be experimented with a plug-in.

Thanks for your feedback.

Cheers.

---

### Post by Mystilleef on 2006-10-17
> **mostwanted said:**
> Very neat editor. I like it.

I made a deb if anyone is interested. I have no idea what the dependencies are though, you figure it out :)

Ah thank you! :-)

But the dependency checking is important. Otherwise, I'll get hoards of bug reports related to deps. I imagine it will be troublesome for KUbuntu and XUbuntu users who don't have some the gnome libs installed.

Deps:
dbus-python 0.6 or later
pygtk-2.10
gnome-python-desktop 2.12
gnome-python-extras 2.12

---

### Post by chaosgeisterchen on 2006-10-17
Thank you for your answer, Mystilleef *smile*

It's written Python, ain't it? Man, the lanuage is great!
Stop me if I am overextending, but will it get support for plugins or is that already implemented in some special way?

---

### Post by Mystilleef on 2006-10-17
> **chaosgeisterchen said:**
> Thank you for your answer, Mystilleef *smile*

It's written Python, ain't it? Man, the lanuage is great!
Stop me if I am overextending, but will it get support for plugins or is that already implemented in some special way?

Yes, it is written in Python. The Plug-in system has already been implemented. It will be exposed officially for version 0.4. Prior to that, I need to "dog-food" it (convert features/services to plug-ins) and write a GUI that will allow users to install/remove, enable/disable plug-ins. By version 0.3.1, brave souls should be able to write plug-ins for Scribes. However, the next major release, version 0.3 will __not__ ship with the plug-in system enabled. Sorry :-(

---

### Post by chaosgeisterchen on 2006-10-17
We have time and it's still many times faster developed than propietary and non-free coding editors which are inferior compared to **Scribes** so do not hurry more than you have to :)

Must be an interesting feeling to do further programming of a programme in the programme itself ;)

---

### Post by Corbelius on 2006-10-17
Good apps :)

---

### Post by NoWhereMan on 2006-10-17
i love devs talking directly to their users :)

---

### Post by chaosgeisterchen on 2006-10-17
> **NoWhereMan said:**
> i love devs talking directly to their users :)

So, that's the spirit of ubuntu ;)

---

### Post by punkforpez on 2006-10-17
> **Mystilleef said:**
> Yes, it is written in Python. The Plug-in system has already been implemented. It will be exposed officially for version 0.4. Prior to that, I need to "dog-food" it (convert features/services to plug-ins) and write a GUI that will allow users to install/remove, enable/disable plug-ins. By version 0.3.1, brave souls should be able to write plug-ins for Scribes. However, the next major release, version 0.3 will __not__ ship with the plug-in system enabled. Sorry :-(

plugins! oh can't wait...

---

### Post by Wolki on 2006-10-17
> **Mystilleef said:**
> Perhaps you are experience redraw issues with GTK+? The document switcher shows up almost instantly for me. Maybe I used to GTK+ redraw problems. A lot people complain about it, so it's not unusual. I'm I getting the problem, right? Or have I derailed.? :-)

The document switcher more or less shows up instantly for me, too. It's the windows I switch to that flicker.  Say I have two scribes windows open and visible, and use the document switcher to switch between them. After choosing a window, it will briefly disappear, showing the desktop background, then come back again.
It seems the effect is a bit stronger when more windows are open, but I did not thoroughly test it and I might be wrong.

> Well, the rule is if you see the *, then you have certainly modified the document. So what is a modified document? The moment you add, remove, or change text in the editing area, then the document is modified. 

Maybe it's a bit of a consistency thing, I'm used to programs using the * to signal "unsaved changes", and not displaying it after they detect that no actual modifications have taken place.
Maybe a different symbol could be used?

On a similar note, if I start an empty scribes window, change somthing then remove or undo it again, the empty document will be saved. Now, there are no doubt some valid circumstances where a user wants to create an empty file, but I can't think of one where an empty file with a default name is wanted. Maybe scribes could save unnamed documents only if they actually contain someting?

> Ah, I understand now. That's a pretty smart way to handle it. I never thought about it. The only problem I see is how does one determine the difference between templates? If the difference between templates is just one space or tab character at the end of the template, then we are back to square one. :-D

Yeah, but than they're at least actually different templates, and even whitespace might change meaning sometimes. (for example, if someone's programming in whitespace [http://compsoc.dur.ac.uk/whitespace/](http://compsoc.dur.ac.uk/whitespace/) ;))

> I think most people who want to change the name of a file don't care what happens to the old file. Maybe I'm being presumptious.
  

I'd say a consistent naming scheme between applictions is worth a lot, and rename in one Application should work as in others. You're the developer though.

> Well, the open dialog already allows you to open files in the same folder. Scribes' implementation even remembers the last state of the open dialog. In fact, I encourage user to use open dialog as a file manager. You can even bookmark folders in open dialog.

Well, I have a personal dislike for open dialogs, since they largely duplicate functionality already in my file manager of choice, only much worse. A plugin would be a fine solution though, as it's just a bonus feature. :)

---

### Post by chaosgeisterchen on 2006-10-17
> **Wolki said:**
> Well, I have a personal dislike for open dialogs, since they largely duplicate functionality already in my file manager of choice, only much worse. A plugin would be a fine solution though, as it's just a bonus feature. :)

I would very much appreciate if, for instance, KDE would use Konqueror as open file dialog, as the open file dialog of KDE is great but it lacks options to perform - for instance copy/pase and file deletion.

---

### Post by Mystilleef on 2006-10-17
> **Wolki said:**
> The document switcher more or less shows up instantly for me, too. It's the windows I switch to that flicker.  Say I have two scribes windows open and visible, and use the document switcher to switch between them. After choosing a window, it will briefly disappear, showing the desktop background, then come back again.
It seems the effect is a bit stronger when more windows are open, but I did not thoroughly test it and I might be wrong.

The window you focus is initially hidden before shown. The effect is intentional. It is a form of visual feedback to signal to the user that something has happened.

> **Wolki said:**
> 
Maybe it's a bit of a consistency thing, I'm used to programs using the * to signal "unsaved changes", and not displaying it after they detect that no actual modifications have taken place.

Maybe a different symbol could be used?

That's exactly how Scribes works. * indicates that the buffer has been modified and the document has not yet been saved. This is also the behavior suggested by the GNOME Human Interface Guide.

> **Wolki said:**
> 
On a similar note, if I start an empty scribes window, change somthing then remove or undo it again, the empty document will be saved. Now, there are no doubt some valid circumstances where a user wants to create an empty file, but I can't think of one where an empty file with a default name is wanted. Maybe scribes could save unnamed documents only if they actually contain someting?

I follow a consistent rule. If a document is modified, it will be saved. Press (Control - Shift - w) to prevent a modified "Unsaved Document" window from saving on exiting. Editing is the process of adding, removing and changing data. Because a user removes data associated with a document doesn't mean I should make an assumption that may lead to permanent data loss. This is the reason buffer modification and not the content of the editing area is the most robust means for determining whether or not to save intelligently.

> **Wolki said:**
> 
Yeah, but than they're at least actually different templates, and even whitespace might change meaning sometimes. (for example, if someone's programming in whitespace [http://compsoc.dur.ac.uk/whitespace/](http://compsoc.dur.ac.uk/whitespace/) ;))

I like the idea a lot. I'll see how feasible it is to implement.

  
> **Wolki said:**
> 
I'd say a consistent naming scheme between applictions is worth a lot, and rename in one Application should work as in others. You're the developer though.

There are no naming scheme for tooltips. Just recommendation by the GNOME HIG. Half the applications I have don't even follow the HIG when labelling tooltips. I'm certainly not going to label the tooltip "Save as.." because most other applications label it that way. :-D I think most users will understand what the process of renaming a file entails. And if they are unsure of the action, they can always backup and test it. :-)

---

### Post by skymt on 2006-10-17
> **Mystilleef said:**
> I'm certainly not going to label the tooltip "Save as.." because most other applications label it that way.

That's exactly why you should call it that. It's called a convention. People expect the Save As functionality to be called "Save As". Just like people expect a menu when they right-click (a convention Scribes follows) and they expect ^C to copy the selected text (ditto). Unless you have something significantly better than the convention, please stick to it. Don't change things like that just to be contrary.

It's even worse when the change conflicts with another convention. Users are used to files being renamed in-place. When you right click a file in Nautilus and choose Rename, it doesn't make another copy, does it? Then why would Scribes?

---

### Post by Mystilleef on 2006-10-17
> **skymt said:**
> That's exactly why you should call it that. It's called a convention. People expect the Save As functionality to be called "Save As". Just like people expect a menu when they right-click (a convention Scribes follows) and they expect ^C to copy the selected text (ditto). Unless you have something significantly better than the convention, please stick to it. Don't change things like that just to be contrary.

It's even worse when the change conflicts with another convention. Users are used to files being renamed in-place. When you right click a file in Nautilus and choose Rename, it doesn't make another copy, does it? Then why would Scribes?

You are not paying attention. Naming a tooltip "Save as.." violates the GNOME HIG. I don't know what's more silly following convention blindly or following convention that is __WRONG__. Renaming also overwrites existing files. If you have a file foo.txt. And you change the name of a file bar.txt to foo.txt, foot.txt is overwritten. So your example is moot. Let me repeat myself, you can't name a tooltip "Save as..." Tooltips are supposed to be descriptive. "Save as..." is a meaningless phrase.

---

### Post by Buffalo Soldier on 2006-10-17
Changing from using Gedit to Scribes is not unlike changing from Windows to Linux. It involves a paradigm shift (I hope it's the correct word). 

First time using it I can feel a sense of shock to my system, which is used to Gedit and Nano. But now after several hours of using Scribes I think I'm *getting it*.

Rock on Mystilleef. Scribes and your vision is quite refreshing :)

---

### Post by spockrock on 2006-10-18
sorry I am trying out scribes, and well, I am wondering when I try to edit files such as xorg.conf, it doesn't like me running scribes as the the root user via sudo?  Is this intentional??  I am just wondering.....

---

### Post by NoWhereMan on 2006-10-18
> **chaosgeisterchen said:**
> So, that's the spirit of ubuntu ;)

[img]http://forums.igray.ru/html/emoticons/beer.gif[/img]

---

### Post by Spif on 2006-10-18
Wow, this application looks very promising. I'm going to try it out later today.

---

### Post by NoWhereMan on 2006-10-18
well... feature request... regex's ;D maybe for 5.0 :p
"about" window buttons: has this already reported?

---

### Post by Mystilleef on 2006-10-18
> **spockrock said:**
> sorry I am trying out scribes, and well, I am wondering when I try to edit files such as xorg.conf, it doesn't like me running scribes as the the root user via sudo?  Is this intentional??  I am just wondering.....

This is a problem/bug with D-Bus, I'm working on a solution. Thanks for your feedback.

Thanks

---

### Post by NoWhereMan on 2006-10-18
another thing; on first open, mru menu is not displayed, but the button stays pushed... it looks strange to me, as if the program was stuck (in fact it's not, just click anywhere else, ok)... maybe would be better showing a menu with only "no documents in the list" or something... or you won't have feedback

---

### Post by Mystilleef on 2006-10-18
> **NoWhereMan said:**
> well... feature request... regex's ;D maybe for 5.0 :p
"about" window buttons: has this already reported?

I already implemented regex, but it was too unreliable that I disabled it. I'll resume work on it within one of the 0.3.X releases. The about dialog problem is noted. Thanks

---

### Post by Mystilleef on 2006-10-18
> **Buffalo Soldier said:**
> Changing from using Gedit to Scribes is not unlike changing from Windows to Linux. It involves a paradigm shift (I hope it's the correct word). 

First time using it I can feel a sense of shock to my system, which is used to Gedit and Nano. But now after several hours of using Scribes I think I'm *getting it*.

Rock on Mystilleef. Scribes and your vision is quite refreshing :)

Thanks for the feedback. Yes, Scribes provides a unique text editing experience unlike any other editor I've used. But I'm biased, don't take my word for it. :-D

---

### Post by Mystilleef on 2006-10-18
> **NoWhereMan said:**
> another thing; on first open, mru menu is not displayed, but the button stays pushed... it looks strange to me, as if the program was stuck (in fact it's not, just click anywhere else, ok)... maybe would be better showing a menu with only "no documents in the list" or something... or you won't have feedback

If it's not too much trouble, can you provide a screenshot?

---

### Post by NoWhereMan on 2006-10-18
> **Mystilleef said:**
> If it's not too much trouble, can you provide a screenshot?

it won't if you tell me how i clear mru's now :p

---

### Post by Spif on 2006-10-18
Alright, I tried it out. Will be my text editor of choice when programming, no doubt about that! Maybe we could create a category dedicated to this project on these forums?

Here's my wishlist:

* Tabs
* Templates installed by default
* A close button for the "Search and Replace"
* About menu (has already been mentioned I think)
* The Scribus name should appear next to the document name, like all other applications 
* Tabs. Please... :)

---

### Post by NoWhereMan on 2006-10-18
> **Spif said:**
> Here's my wishlist:

* Tabs
[...]
* Tabs. Please... :)

he's gonna kill you, I've told you :D :D :D
[http://mystilleef.blogspot.com/2006/10/no-tabs-why.html](http://mystilleef.blogspot.com/2006/10/no-tabs-why.html)

---

### Post by Spif on 2006-10-18
> **NoWhereMan said:**
> he's gonna kill you, I've told you :D :D :D
[http://mystilleef.blogspot.com/2006/10/no-tabs-why.html](http://mystilleef.blogspot.com/2006/10/no-tabs-why.html)

Hehe :P

Tabs > All. It is a must have feature, especially when working with multiple modules at once.

I really like the GUI in general. I hate how most programs use the "File, Edit, View..." and so on, it is really not user-friendly at all. Nice to see one that doesn't use this.

---

### Post by ago on 2006-10-18
I have used only for a little but I am VERY impressed. I will certainly use it more soon and come back to you with suggestions.

---

### Post by chaosgeisterchen on 2006-10-18
I am also pro Tabs.

---

### Post by Mystilleef on 2006-10-18
> **NoWhereMan said:**
> it won't if you tell me how i clear mru's now :p

It involves tampering with a file that maybe in use by other applications so it's not a good idea.

Cheers

---

### Post by NoWhereMan on 2006-10-18
> **Mystilleef said:**
> It involves tampering with a file that maybe in use by other applications so it's not a good idea.

Cheers

then i'm sorry but you'll have to figure it out yourself :(

---

### Post by neoflight on 2006-10-18
Excellent application. I haven't tested it thoroughly. But i am planning to use it as my latex editor. Is there any way I can integrate the latex commands with scribes? There are several people who might be interested.
THanks

edit: plus...

A menu which quickly gives the main shortcuts would be nice. So you dont have to remember it all the time + dont have to open the help browser a lot.

It doesnt ask to save the file while closing it... how frequently does it save the document? 

pardon me if all these have already been answered

---

### Post by Mystilleef on 2006-10-18
> **Spif said:**
> Alright, I tried it out. Will be my text editor of choice when programming, no doubt about that! Maybe we could create a category dedicated to this project on these forums?

Here's my wishlist:

* Tabs
* Templates installed by default
* A close button for the "Search and Replace"
* About menu (has already been mentioned I think)
* The Scribus name should appear next to the document name, like all other applications 
* Tabs. Please... :)

Thanks for the feedback. 

1). I've discussed the Tabs issue elsewhere, see the link provided above.

2). I'd like to have a complete set of templates before thinking about
installing them by default. Plus most users don't need all templates
installed by default. It's better for them to select which ones they want to install.

3). It's unusual to place a close button on a bar. Close button are
better suited for dialogs

4). I guess those applications don't follows any HIGs, especially not
the GNOME one.
[http://developer.gnome.org/projects/gup/hig/2.0/windows.html#window-props-titles](http://developer.gnome.org/projects/gup/hig/2.0/windows.html#window-props-titles)

Thanks for your feedback once again.

Cheers

---

### Post by Mystilleef on 2006-10-18
> **neoflight said:**
> Excellent application. I haven't tested it thoroughly. But i am planning to use it as my latex editor. Is there any way I can integrate the latex commands with scribes? There are several people who might be interested.
THanks


When the plug-in system is enabled, you'll be able extend the Scribes however you wish. The plug-in system will be officially unvieled by version 0.4. But it will be used unofficially by 0.3.1

> **neoflight said:**
> 
edit: plus...

A menu which quickly gives the main shortcuts would be nice. So you dont have to remember it all the time + dont have to open the help browser a lot.

Leave the help browser open. :-D

> **neoflight said:**
> 
It doesnt ask to save the file while closing it... how frequently does it save the document? 

pardon me if all these have already been answered

 Documents are saved a few seconds after they are modified and also at other special occassions.

Thanks for the feedback.

Cheers

---

### Post by Raavea on 2006-10-20
I'm sorry if this query has arisen before, but I don't have time to read through as I gotta go or I'll miss my bus.

 It looks (I watched the gif demo) a lot like how I have my gedit set up, even with the html snippets and all. I had to add so many snippets - perhaps there are a better range in scribes, or is the uber thing that people won't have to faff about with setting up the plugins and preferences? 
 I use gedit for php programming, but I'm intending to learn ruby at some point, or python. I know gedit has a basic set of snippets for all these, to which I will obviously have to add - what makes scribe better?

 I don't mean any of this in a bad way, I'm really interested. :)

 Will check when I get home! :D
[I][SIZE="1"]
PS: Forgive me any errors, got a dark theme with a light font, which doesn't show good against the forum edit boxes. :roll: and no time to preview or try highlighting it all with this stupid little touchpad thing...[/SIZE][/I]

---

### Post by NoWhereMan on 2006-10-20
> **Mystilleef said:**
> Leave the help browser open. :-D
may I suggest to put the keyboard shortcuts in the buttons tooltips? :)

> Documents are saved a few seconds after they are modified and also at other special occassions.

I must admit this is sometimes annoying, for instance if you type something in a new document, then decide you want to discard it, you close it, and still a file is saved on your desktop...

however this is my point of view... feel free to ignore it :)

a little thing (a behaviour you didn't expect from the user ;)) about the template insertion.
If you mess a little around with your mouse while in "template insertion mode", Scribes will get a little puzzled; I'd suggest that clicking with the mouse while inserting a template quits the insertion mode.

To reproduce what I'm talking about, insert a template trigger and press tab; click somewhere else in the template, or even delete the whole inserted text. syntax highlighter will get "confused" :)

HTH

---

### Post by Wolki on 2006-10-20
> **NoWhereMan said:**
> I must admit this is sometimes annoying, for instance if you type something in a new document, then decide you want to discard it, you close it, and still a file is saved on your desktop...

It probably takes some time getting used to... I don't know yet. What I'm wondering right now is usb flash sticks... since they have a limited number of writes, wouldn't scribes wear them out really fast?

Mystilleef, I'm using scribes right now to write a paper, and one thing I noted is that the autocompletion stays around if you move the cursor. I happened to me a couple of times that I inserted a word somewhere, them moved the cursor to another place, and the suggested autocompletions  stayed around until I entered a new character somewhere. It's just a minor annoyance, but I think it should disappear if you move the cursor, or at least if you move it to another word.

---

### Post by Mystilleef on 2006-10-20
> **NoWhereMan said:**
> may I suggest to put the keyboard shortcuts in the buttons tooltips? :)

The buttons on the toolbar have tooltips with keyboard shortcuts. Are you suggesting I add tooltips to the popup menu?

> **NoWhereMan said:**
> 
I must admit this is sometimes annoying, for instance if you type something in a new document, then decide you want to discard it, you close it, and still a file is saved on your desktop...

however this is my point of view... feel free to ignore it :)


Press (Control - Shift - W) to prevent that from happening.

> **NoWhereMan said:**
> 
a little thing (a behaviour you didn't expect from the user ;)) about the template insertion.
If you mess a little around with your mouse while in "template insertion mode", Scribes will get a little puzzled; I'd suggest that clicking with the mouse while inserting a template quits the insertion mode.

To reproduce what I'm talking about, insert a template trigger and press tab; click somewhere else in the template, or even delete the whole inserted text. syntax highlighter will get "confused" :)

HTH

Can you provide detailed steps on how I can reproduce the problem with examples?

There are two ways to exit template mode. One is to click outside the template area, the other is to press Tab until the statusbar informs you that template mode is exited. Clicking inside the template should not exit template mode because users may want to edit other aspects of the templates that may not be placeholders.

Thanks for your feedback. :-)

Cheers

---

### Post by Mystilleef on 2006-10-20
> **Wolki said:**
> It probably takes some time getting used to... I don't know yet. What I'm wondering right now is usb flash sticks... since they have a limited number of writes, wouldn't scribes wear them out really fast?

Mystilleef, I'm using scribes right now to write a paper, and one thing I noted is that the autocompletion stays around if you move the cursor. I happened to me a couple of times that I inserted a word somewhere, them moved the cursor to another place, and the suggested autocompletions  stayed around until I entered a new character somewhere. It's just a minor annoyance, but I think it should disappear if you move the cursor, or at least if you move it to another word.

I'm confirming this problem. For now, you can press Esc to hide the completion window at any time.

Thanks for your feedback.

Cheers.

---

### Post by Mystilleef on 2006-10-20
> **Raavea said:**
> I'm sorry if this query has arisen before, but I don't have time to read through as I gotta go or I'll miss my bus.

 It looks (I watched the gif demo) a lot like how I have my gedit set up, even with the html snippets and all. I had to add so many snippets - perhaps there are a better range in scribes, or is the uber thing that people won't have to faff about with setting up the plugins and preferences? 
 I use gedit for php programming, but I'm intending to learn ruby at some point, or python. I know gedit has a basic set of snippets for all these, to which I will obviously have to add - what makes scribe better?

 I don't mean any of this in a bad way, I'm really interested. :)

 Will check when I get home! :D
[I][SIZE=1]
PS: Forgive me any errors, got a dark theme with a light font, which doesn't show good against the forum edit boxes. :roll: and no time to preview or try highlighting it all with this stupid little touchpad thing...[/SIZE][/I]

This question is tough because differrent people will give differrent responses. I'm biased. My brain is programmed to tell you Scribes looks, behaves and feels better than any other text editor. It's the best application in the world. On occassions I've been known to say it does your dishes, cleans up after you and massages your girlfriend. I have more hype material, but I won't bore you.

My point is, I'll say whatever you want to hear. So you shouldn't listen to me or anyone. You should install Scribes, evaluate it and see if it meets your needs or has potential. If it does you should contribute by providing feedback, [donating]("http://scribes.sf.net/donate.html") or whatever to help make the application better.

Now back to your question. Yes, Scribes does everything better than Gedit. :-D

Cheers

---

### Post by NoWhereMan on 2006-10-20
> **Mystilleef said:**
> The buttons on the toolbar have tooltips with keyboard shortcuts. Are you suggesting I add tooltips to the popup menu?
I didn't remember they were there :p but I'll then suggest to show shortcuts on the left click menu too :D:D
(ps i think the gnome guidelines would put in the tooltips the name of the button *together* with the shortcut key... i know that would be boring to do, just as a future suggestion ;))


> Press (Control - Shift - W) to prevent that from happening.
cool! I'll try :)


> Can you provide detailed steps on how I can reproduce the problem with examples?

new file.c add a template e.g. func[tab], then ctrl+a and delete all by [canc]

...

as another suggestion: could you add the ability to choose syntax directly, so that you can switch to (say...) c while you still haven't saved... or to switch to javascript mode while editing an html file :)

TextMate can do that (*cough*) :mrgreen: ;)

---

### Post by Raavea on 2006-10-20
Your logic is, indeed, infalliable.

 I shall test your baby out later, when I get to the less vital part of my current project. :)

---

### Post by Mystilleef on 2006-10-21
> **NoWhereMan said:**
> I didn't remember they were there :p but I'll then suggest to show shortcuts on the left click menu too :D:D
(ps i think the gnome guidelines would put in the tooltips the name of the button *together* with the shortcut key... i know that would be boring to do, just as a future suggestion ;))


I don't think that's done with popup menus. I'll have to read the HIG again.

> **NoWhereMan said:**
> 
new file.c add a template e.g. func[tab], then ctrl+a and delete all by [canc]


I can reproduce the problem. It should be fixed for the next release.

> **NoWhereMan said:**
> 
as another suggestion: could you add the ability to choose syntax directly, so that you can switch to (say...) c while you still haven't saved... or to switch to javascript mode while editing an html file :)

TextMate can do that (*cough*) :mrgreen: ;)

I'll implement this for version 0.3.1 or 0.3.2

Thanks for the feedback

Cheers

---

### Post by NoWhereMan on 2006-10-21
> **Mystilleef said:**
> Thanks for the feedback

you're welcome ;) :cool: =D>

---

### Post by ruimoura on 2006-10-21
The download link doesn't work for me .. Is it broken on sourceforge?

---

### Post by Mystilleef on 2006-10-22
> **ruimoura said:**
> The download link doesn't work for me .. Is it broken on sourceforge?

Sourceforge is having problems. Try again later.

Cheers

---

### Post by Anonii on 2006-10-22
Tried it out today. A really clean look for my desktop, and I'm using it as the default GUI text editor, now.

I'd love it more, if it had Emacs-ish shortcuts <: (like ^k and ^n/p/a/f)

Anyway, great work.

---

### Post by NoWhereMan on 2006-10-22
shhht, he's a vim guy :D

---

### Post by chaosgeisterchen on 2006-10-22
As there will be plugin-support in upcoming releases you could distribute a emacs-hotkey-plugin to Scribes to make it fit your needs.

---

### Post by ago on 2006-10-22
The more I use it, the more I like it. I think I will keep it as default text editor. PS Are there templates available?

---

### Post by Wolki on 2006-10-22
> **ago said:**
> The more I use it, the more I like it. I think I will keep it as default text editor. PS Are there templates available?

There are some, see the FAQ on the website: [http://scribes.sourceforge.net/docs_faq.html](http://scribes.sourceforge.net/docs_faq.html)

If someone creates more, feel free to post them :)

---

### Post by NoWhereMan on 2006-10-22
> **ago said:**
> The more I use it, the more I like it. I think I will keep it as default text editor. PS Are there templates available?

see first post

---

### Post by paul6 on 2006-10-22
> **Mystilleef said:**
> Ah thank you! :-)

But the dependency checking is important. Otherwise, I'll get hoards of bug reports related to deps. I imagine it will be troublesome for KUbuntu and XUbuntu users who don't have some the gnome libs installed.

Deps:
dbus-python 0.6 or later
pygtk-2.10
gnome-python-desktop 2.12
gnome-python-extras 2.12


Would you mind posting the exact name of the dependencies, as they exist in the package repositories? For example, "sudo aptitude search dbus-python" brings up no results, so I assume it is named differently.

Also, I get an error when I try to ./configure this:
```
paul@ubuntu:~/scribes-0.2.9.88$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.35.0... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
paul@ubuntu:~/scribes-0.2.9.88$
```

But this will be fixed once I install the dependencies, right?

---

### Post by ago on 2006-10-22
> **Wolki said:**
> There are some, see the FAQ on the website: [http://scribes.sourceforge.net/docs_faq.html](http://scribes.sourceforge.net/docs_faq.html)

If someone creates more, feel free to post them :)

Thx I have them up now.

---

### Post by Buffalo Soldier on 2006-10-22
I manage to cram all the shortcuts into 1 piece of A4-sized paper. I've attached it to a separate thread. [http://ubuntuforums.org/showthread.php?t=282481](http://ubuntuforums.org/showthread.php?t=282481)

---

### Post by Wolki on 2006-10-23
That's cool, thanks!

---

### Post by LinuxKid on 2006-10-23
This editor reminds me of [Textmate]("http://www.macromates.com") alot. I believe that this is a great text editor. 

[SIZE="1"]Any chance for a port to windows? (Please don't flame me)[/SIZE]

---

### Post by ago on 2006-10-23
Some suggestions

TOGGLES:

I would recommend to use toggle switches whenever possible. Toggles can be used whenever you can loop through a small set of states, provided the original state is part of the looped states. It is generally easier to use a single toggle button/key combination rather than having separate commands, because:

1) fewer shortcuts to memorize
2) "undo" can be built-in: by repeating the same operation until you come back to the original state
3) given the above, they give a "physical" feeling to the action, like a switch
4) repeating the same key combination is relatively fast since your fingers do not move around the keyboard (not as fast as having separate key combinations but a good second best)
5) it is not mutually exclusive, you can keep toggle switches and individual commands (but I personally do not see the point). Or have hybrid commands, so that each act as an individual command, but if you press it again you toggle through the remaining states.

Some examples:

* toggle bookmark on/off
* toggle block comment/uncomment
* toggle text direction LTR/RTL
* toggle tabs/spaces indentation (3rd click returns to current state ~ undo)
* toggle lower/upper/title case (4th click returns to current state ~ undo)
* toggle join/split line (3rd click returns to current state ~ undo)
...

FIND:

IMO, the search should start at the current cursor position. Now it starts from beginning of the document. Sometimes you want to search for a word in order to act on some other parts of the sentence, and then go to the next match.

It would be nice if search in files (all open files) could be implemented. In the simplest form, you could add a single button in the search bar. When you press it (or CTRL+Shift+F), a dialog similar to the switcher is shown, with all the matches in the open files. If you select one of them, you go to the equivalent file/line and with its searchbar open. 

SWITCHER:

I am not going to advocate tabs, quite the opposite, I like the switcher, in fact I think that for many people the switcher is enough, and it would be nice to have an option to hide the other documents, so that only one page is shown at any one time and you use the switcher to change documents without cluttering the desktop/taskbar.

---

### Post by Mystilleef on 2006-10-23
> **paul6 said:**
> Would you mind posting the exact name of the dependencies, as they exist in the package repositories? For example, "sudo aptitude search dbus-python" brings up no results, so I assume it is named differently.

Also, I get an error when I try to ./configure this:
```
paul@ubuntu:~/scribes-0.2.9.88$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.35.0... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
paul@ubuntu:~/scribes-0.2.9.88$
```But this will be fixed once I install the dependencies, right?

I think on Ubuntu it's called python-dbus. I'm not on Ubuntu at the moment. You can do a search for dbus in Synaptic. I don't know why you are getting the above error however. Looks like you don't have a perl package installed.

Cheers

---

### Post by Mystilleef on 2006-10-23
> **LinuxKid said:**
> This editor reminds me of [Textmate]("http://www.macromates.com") alot. I believe that this is a great text editor. 

[SIZE=1]Any chance for a port to windows? (Please don't flame me)[/SIZE]

Unfortunately not. I barely have the resources to maintain Scribes on Linux talk little of a port to windows. :-D

---

### Post by ago on 2006-10-23
not on ubuntu machine but you can use the following to search for packages:

apt-cache search  dbus | grep python*

[http://packages.ubuntu.com/dapper/python/python2.4-dbus](http://packages.ubuntu.com/dapper/python/python2.4-dbus)

---

### Post by Mystilleef on 2006-10-23
> **ago said:**
> Some suggestions

TOGGLES:

I would recommend to use toggle switches whenever possible. Toggles can be used whenever you can loop through a small set of states, provided the original state is part of the looped states. It is generally easier to use a single toggle button/key combination rather than having separate commands, because:

1) fewer shortcuts to memorize
2) "undo" can be built-in: by repeating the same operation until you come back to the original state
3) given the above, they give a "physical" feeling to the action, like a switch
4) repeating the same key combination is relatively fast since your fingers do not move around the keyboard (not as fast as having separate key combinations but a good second best)
5) it is not mutually exclusive, you can keep toggle switches and individual commands (but I personally do not see the point). Or have hybrid commands, so that each act as an individual command, but if you press it again you toggle through the remaining states.

Some examples:

* toggle bookmark on/off
* toggle block comment/uncomment
* toggle text direction LTR/RTL
* toggle tabs/spaces indentation (3rd click returns to current state ~ undo)
* toggle lower/upper/title case (4th click returns to current state ~ undo)
* toggle join/split line (3rd click returns to current state ~ undo)
...


This is interesting food for thought. The GNOME HIG talks extensively about how to formulate shortcut keys. By and large I use the HIG as a basis for the formulation of shortcut keys. I'll take your input into consideration, however, when formulating shortcut keys in the future. Thanks

> **ago said:**
> 
FIND:

IMO, the search should start at the current cursor position. Now it starts from beginning of the document. Sometimes you want to search for a word in order to act on some other parts of the sentence, and then go to the next match.

Press (Control - K) for the incremental search bar.

> **ago said:**
> 
It would be nice if search in files (all open files) could be implemented. In the simplest form, you could add a single button in the search bar. When you press it (or CTRL+Shift+F), a dialog similar to the switcher is shown, with all the matches in the open files. If you select one of them, you go to the equivalent file/line and with its searchbar open. 

Sounds complicated. I wouldn't add that to Scribes. It could be implemented as a third party plug-in however. 


> **ago said:**
> 
SWITCHER:

I am not going to advocate tabs, quite the opposite, I like the switcher, in fact I think that for many people the switcher is enough, and it would be nice to have an option to hide the other documents, so that only one page is shown at any one time and you use the switcher to change documents without cluttering the desktop/taskbar.

I fear this will lead to confusion and inconsistency. It also breaks the spatial paradigm Scribes follows.

---

### Post by ago on 2006-10-23
> **Mystilleef said:**
> Sounds complicated. I wouldn't add that to Scribes. It could be implemented as a third party plug-in however.
I am not sure. Say you press the button "Search in open files", that will repeat the search in any open file, gather the results and present them using a dialog very similar to the switcher. Other than a new dialog (which is almost identical to the switcher) there should not be much else to do. I might be wrong though and I trust your instinct on this better than mine.

> I fear this will lead to confusion and inconsistency. It also breaks the spatial paradigm Scribes follows.
It would be like having all the sheets in a single stack as opposed to having them spread all over the desk. It is still a paradigm... but feel free to ignore it. 

PS Thanks for the work so far, if I can think of anything else I will drop a line.

---

### Post by Anonii on 2006-10-23
> **chaosgeisterchen said:**
> As there will be plugin-support in upcoming releases you could distribute a emacs-hotkey-plugin to Scribes to make it fit your needs.
Actually, I'd love to do that, if I knew how ... ehm... well... to do that.

My programming experience and skills are really limited, and I could only do this, if someone explains me where to find the shortcuts, how to change them, and how to save them as a plugin.

(I guess its not really hard, eh? They are all stored in the source code, and I just have to edit their lines, eh? Let me live in my Utopia, eh?)

---

### Post by chaosgeisterchen on 2006-10-23
Python is in fact really easy to learn - try it out, you won't be dissatisfied ( I hope at least :) )

---

### Post by Anonii on 2006-10-23
> **chaosgeisterchen said:**
> Python is in fact really easy to learn - try it out, you won't be dissatisfied ( I hope at least :) )
Yeah, I have some basic knoweledge in Python, till the dictionaries etc. But most programming, at least in Python, is using modules that I'm unaware of their uses and existence :/

So, how hard would it be to edit these shorcuts? ^_^

---

### Post by chaosgeisterchen on 2006-10-23
Do not ask me. I am very aware of the fact that you're certainly more skilled in programming Python than I am, I am afraid.

(School imposes Microsoft C#.NET on us. I would rather learn Python instead.)

---

### Post by Anonii on 2006-10-23
> **chaosgeisterchen said:**
> Do not ask me. I am very aware of the fact that you're certainly more skilled in programming Python than I am, I am afraid.

(School imposes Microsoft C#.NET on us. I would rather learn Python instead.)
Okie dokie, thanks for answering my questions.
If anyone else knows something moar, please tell me.


(Mystilleef, Scribes wins so hard! Thanks!)

---

### Post by omns on 2006-10-23
.

---

### Post by Wolki on 2006-10-23
> **Anonii said:**
> 
If anyone else knows something moar, please tell me.

If you globally enable emacs shortcuts in gnome (/desktop/gnome/interface/gtk_key_theme), you can use a few of the keys they suport( [http://developer.gnome.org/projects/gup/hig/2.0/input-keyboard.html#additional-widget-navigation](http://developer.gnome.org/projects/gup/hig/2.0/input-keyboard.html#additional-widget-navigation) )in scribes. It will not work for things that scribes itself implements, though.

I guess it should be possible to implement more , but I didn't really take a look at the source yet...

[edit] Anonii, take a look at actions.py...

---

### Post by zachtib on 2006-10-23
is this gnome-specific, or will it run on say, XFCE?  I'm thinking of moving to XFCE, but would miss gedit's syntax highlighting, to the point that I spent the day writing a simple python editor with syntax highlighting that uses pure gtk

---

### Post by Wolki on 2006-10-23
> **zachtib said:**
> is this gnome-specific, or will it run on say, XFCE?

It uses gtksourceview's python bindings, which as far as I know is part of python-gnome-desktop.

---

### Post by Mystilleef on 2006-10-24
> **ago said:**
> I am not sure. Say you press the button "Search in open files", that will repeat the search in any open file, gather the results and present them using a dialog very similar to the switcher. Other than a new dialog (which is almost identical to the switcher) there should not be much else to do. I might be wrong though and I trust your instinct on this better than mine.

It is very complicated. But that's the lesser problem. The larger problem is the fact that you are now crossing boundaries with regards to document-centric metaphors. For example, it feels wrong to search for strings in other documents from another document. Scribes is document-centric. That means each document/window is autonomous of other documents and windows. Document A does not care about the contents of document B and vice versa. In fact, document A does not even know document B exists. This is why a third part plug-in that allows you to search for strings in all documents is more sensible. 

> **ago said:**
> 
It would be like having all the sheets in a single stack as opposed to having them spread all over the desk. It is still a paradigm... but feel free to ignore it.

That analogy is mistaken. If we are relating a window to a sheet of paper, you are suggesting I hide all other windows except the one. That's the same as hiding all sheets with the exception of one. Hiding windows is not the same thing as stacking them. Cool window managers (VISTA's, Compiz(?)) can performing stacking operations. Hiding is a bad idea. Why? Well what happens to hidden windows when the user closes the visible one?

> **ago said:**
> 
PS Thanks for the work so far, if I can think of anything else I will drop a line.

Look forward to more feedback.

Thanks

---

### Post by Mystilleef on 2006-10-24
> **GrantG said:**
> This looks like a great project.:D Have you thought about asking for a third party forum here to handle the traffic and increase the efficiency of the feedback?... this thread is getting quite lengthy.

I purposefully created the thread to get feedback here. I doubt another third party forums provides any benefit.

---

### Post by Mystilleef on 2006-10-24
> **zachtib said:**
> is this gnome-specific, or will it run on say, XFCE?  I'm thinking of moving to XFCE, but would miss gedit's syntax highlighting, to the point that I spent the day writing a simple python editor with syntax highlighting that uses pure gtk

Scribes will run on any *nix DE as long as you have the deps installed.

Cheers

---

### Post by Anonii on 2006-10-24
> **Wolki said:**
> If you globally enable emacs shortcuts in gnome (/desktop/gnome/interface/gtk_key_theme), you can use a few of the keys they suport( [http://developer.gnome.org/projects/gup/hig/2.0/input-keyboard.html#additional-widget-navigation](http://developer.gnome.org/projects/gup/hig/2.0/input-keyboard.html#additional-widget-navigation) )in scribes. It will not work for things that scribes itself implements, though.

I guess it should be possible to implement more , but I didn't really take a look at the source yet...

[edit] Anonii, take a look at actions.py...
Thank you very much.

I took a look on the actions.py code. From what I understood, he is defining some functions and then he is assigning them to keyboard shortcuts. Unfortunately there were no functions like "Go to the start of the line" or "Delete everything before the cursor" or "Go down one line", do I have to create the myself?

Thanks, again!

---

### Post by Mystilleef on 2006-10-24
> **Anonii said:**
> Thank you very much.

I took a look on the actions.py code. From what I understood, he is defining some functions and then he is assigning them to keyboard shortcuts. Unfortunately there were no functions like "Go to the start of the line" or "Delete everything before the cursor" or "Go down one line", do I have to create the myself?

Thanks, again!

Hello, it's a good idea to wait for me to enable the plug-in system. The plug-in system will be enabled in version 0.3.1. I'll be more than willing to guide you through the process of extending Scribes then.

Cheers

---

### Post by Anonii on 2006-10-24
> **Mystilleef said:**
> Hello, it's a good idea to wait for me to enable the plug-in system. The plug-in system will be enabled in version 0.3.1. I'll be more than willing to guide you through the process of extending Scribes then.

Cheers
Thats great!

Thank you very much, and good luck with your project!

---

### Post by Wolki on 2006-10-24
There is a function for deleting to the end of the line, see delete_cursor_to_line_end_trigger. The cursor movement is not there, but it should not be too difficult to do... but it's likely better to wait for proper plugin support.

I'm by far no expert programmer, but what I've seen of the code looks well-structured and readable, so rock on, Mystilleef :)

One thing I'm missing especially are smart tabs like the gedit extension...  meaning that when doing spaces instead of tabs, you can remove one tabstop worth of spaces by pressing backspace. Probably best to wait for the plugins, though...

---

### Post by ago on 2006-10-24
Some ideas on shortcuts

* Alt + Left/Right now moves to next previous/bookmark, but if I move to the previous/bookmark the document scrolls vertically, it seems unnatural to associate horizontal buttons to a vertical movement. I can understand the concepts of "next and previous" go well along with left/right but the visual feedback is more important than the label and in this case it does not match. Moreover bookmark navigation should mimic cursor navigation, in this spirit Alt+Ctrl+Home should move to first bookmark.

* I would use ctrl+b to toggle a bookmark, ctrl+shift+b to delete all bookmarks. FX to show bookamrk navigator.

* I would use a toggle switch for capitalization as explained previously or alternatively letters like ctrl+u, ctrl+l... The cursor keys are important ones, using them for capitalization is a bit of a waste. They should be used for navigation and/or selection.

* Indention should be governed by Tab/Shift+Tab. Tab is "natural", since tab's job is basically to indent and it requires 1 key (or 2 for de-indenation) as opposed to 2 (or 3). Also if I select a block of code and hit tab, it is highly unlikely that I want to replace it with a tab, so the meaning is unique. And if I am at the beginning of a line and hit tab, I obviously want to indent. The only reason not to use the tab I can think of is that the cursor has to be before a non whitespace char or a block of code has to be selected for the keypress to be interpreted as an indentation, while with CTRL+T you can use it also if you are in the middle of a line. But I do not see that as restrictive at all.

* There is no block comment/uncomment (I would recommend using a toggle for that) unless I missed it. ctrl+#?

* I do not see why Home does not go to beginning of line (in my setup it goes before to first non-whitespace char), I do not think this is consistent.

---

### Post by Wolki on 2006-10-24
> **ago said:**
> 
* Alt + Left/Right now moves to next previous/bookmark, but if I move to the previous/bookmark the document scrolls vertically, it seems unnatural to associate horizontal buttons to a vertical movement. I can understand the concepts of "next and previous" go well along with left/right but the visual feedback is more important than the label and in this case it does not match. Moreover bookmark navigation should mimic cursor navigation, in this spirit Alt+Ctrl+Home should move to first bookmark.

I'm against stuff using ctrl-alt shortcuts, as these always feel like global shortcuts to me... that direction stuff is interesting.

> * I would use ctrl+b to toggle a bookmark, ctrl+shift+b to delete all bookmarks. FX to show bookamrk navigator.


I'd agree on the toggle, since it's so easily visible whether something is bookmarked or not. I'd say it should stay as ctrl-d though, as that's what every other application uses to bookmark something... iirc it's what the HIG recommends too,

> The cursor keys are important ones, using them for capitalization is a bit of a waste. They should be used for navigation and/or selection.


Sounds resonable to me.

> * There is no block comment/uncomment (I would recommend using a toggle for that) unless I missed it. ctrl+#?

Commenting is language-specific, so it would probably come as part of language plugins

> * I do not see why Home does not go to beginning of line (in my setup it goes before to first non-whitespace char), I do not think this is consistent.

I thought so too... but it can be convenient. It's a toggle though, I'd have guessed you like it ;)

---

### Post by ago on 2006-10-24
> I thought so too... but it can be convenient. It's a toggle though, I'd have guessed you like it ;)
did not even notice that... :D  
(I still think is inconsistent with other situations in which "home" is used, so I will have to raise an exception to my toggle theory...)

---

### Post by Mystilleef on 2006-10-24
> **ago said:**
> Some ideas on shortcuts

* Alt + Left/Right now moves to next previous/bookmark, but if I move to the previous/bookmark the document scrolls vertically, it seems unnatural to associate horizontal buttons to a vertical movement. I can understand the concepts of "next and previous" go well along with left/right but the visual feedback is more important than the label and in this case it does not match. Moreover bookmark navigation should mimic cursor navigation, in this spirit Alt+Ctrl+Home should move to first bookmark.

That's an excellent point. However, what keyboard shortcut do you 
suggest for moving to next/previous bookmarks? I like alt-left/right
because it's efficient and least cumbersome. I do like your idea about using alt-ctrl-Home(end) for navigating to the first(last) bookmark.

> **ago said:**
> 
* I would use ctrl+b to toggle a bookmark, 

All GNOME applications should use ctrl-d to bookmark lines at least
according to the GNOME HIG. See Table 10.8.

[http://developer.gnome.org/projects/gup/hig/2.0/input-keyboard.html#standard-shortcuts](http://developer.gnome.org/projects/gup/hig/2.0/input-keyboard.html#standard-shortcuts)

> **ago said:**
> 
ctrl+shift+b to delete all bookmarks. FX to show bookamrk navigator.

From the GNOME HIG:

[I]
Note that you cannot use Shift-Ctrl-A-thru-F or Shift-Ctrl-0-thru-9 for your own purposes, as these combinations are used to enter unicode characters in text fields.[/I]

See the guidelines section:
[http://developer.gnome.org/projects/gup/hig/2.0/input-keyboard.html](http://developer.gnome.org/projects/gup/hig/2.0/input-keyboard.html)

> **ago said:**
> 
* I would use a toggle switch for capitalization as explained previously or alternatively letters like ctrl+u, ctrl+l... The cursor keys are important ones, using them for capitalization is a bit of a waste. They should be used for navigation and/or selection.

ctrl-u is used in word processors to underline words. I'm reluctant to
use it in Scribes to avoid confusion. ctrl-l is used in GNOME to show 
the a dialog that allows you to open files. See Table 10.10.
[http://developer.gnome.org/projects/gup/hig/2.0/input-keyboard.html](http://developer.gnome.org/projects/gup/hig/2.0/input-keyboard.html)

I like the idea of using the cursor keys primarily for navigation, it make a lot of sense.

> **ago said:**
> 
* Indention should be governed by Tab/Shift+Tab. Tab is "natural", since tab's job is basically to indent and it requires 1 key (or 2 for de-indenation) as opposed to 2 (or 3). Also if I select a block of code and hit tab, it is highly unlikely that I want to replace it with a tab, so the meaning is unique. And if I am at the beginning of a line and hit tab, I obviously want to indent. The only reason not to use the tab I can think of is that the cursor has to be before a non whitespace char or a block of code has to be selected for the keypress to be interpreted as an indentation, while with CTRL+T you can use it also if you are in the middle of a line. But I do not see that as restrictive at all.

In Scribes "ctrl-t" is used exclusively for indentation. "Tab" key does not perform indentation. It only inserts a "\t"(Tab) character into the buffer. This is very different from indentation. Thus using the "Tab" key to represent character insertion and indentation leads to inconsistency. "\t" is a character just like "a", "b" or "c". When you select a word and type "a", what happens? The selection gets replaced by "a." Why should we make exceptions for the "\t" character. I know some editors use the "\t" exclusively for indentation, but I think they are wrong! Maybe I'm being too pedantic here?

> **ago said:**
> 
* There is no block comment/uncomment (I would recommend using a toggle for that) unless I missed it. ctrl+#?

This is a source code specific funtion that I'll implement as a language plug-in.


> **ago said:**
> 
* I do not see why Home does not go to beginning of line (in my setup it goes before to first non-whitespace char), I do not think this is consistent.

What is inconsistent about it? What behavior do you expect when you type the "End" key? Do you expect to be taken to the end of the line, or the end of the last character in a line?

---

### Post by Mystilleef on 2006-10-24
> **ago said:**
> Some ideas on shortcuts

* I would use ctrl+b to toggle a bookmark, ctrl+shift+b to delete all bookmarks. FX to show bookamrk navigator.

I forgot to mention I like the toggle theory. So, ctrl-d would be used to toggle bookmarks. I'm still not so sure about navigation, I like (alt-left/right) :-). We also can't use ctrl-shift-d to remove all bookmarks. What other instances is the toggle theory applicable?

---

### Post by Mystilleef on 2006-10-24
> **Mystilleef said:**
> That's an excellent point. However, In Scribes "ctrl-t" is used exclusively for indentation. "Tab" key does not perform indentation. It only inserts a "\t"(Tab) character into the buffer. This is very different from indentation. Thus using the "Tab" key to represent character insertion and indentation leads to inconsistency. "\t" is a character just like "a", "b" or "c". When you select a word and type "a", what happens? The selection gets replaced by "a." Why should we make exceptions for the "\t" character. I know some editors use the "\t" exclusively for indentation, but I think they are wrong! Maybe I'm being too pedantic here?


I just realized this argument is flawed. Because there are many instances were Scribes overrides expected behavior in the interest of being smart. So yes, ago, while "Tab" is technically a character, 90% of people don't know this and use it for indentation purposes. So I'll implement your behavior.

---

### Post by Mystilleef on 2006-10-24
> **Wolki said:**
> 
One thing I'm missing especially are smart tabs like the gedit extension...  meaning that when doing spaces instead of tabs, you can remove one tabstop worth of spaces by pressing backspace. Probably best to wait for the plugins, though...

I almost missed this. Yes, that will certainly be implemented as a plug-in.

---

### Post by ago on 2006-10-24
> **Mystilleef said:**
> That's an excellent point. However, what keyboard shortcut do you 
suggest for moving to next/previous bookmarks?
I was thinking alt+up/down.

> All GNOME applications should use ctrl-d to bookmark lines at least
according to the GNOME HIG. See Table 10.8.
Well I do not understand what d has to do with b-o-o-k-m-a-r-k, but I do not always agree with HIG...

"Choose access keys to be as easy to remember as possible. Normally, this means using the first letter of the label." :rolleyes: 

They use CTRL+B for the "bookmark navigator", but in scribbles, shouldn't FKeys be used for that to be consistent say with F9 for the "window navigator"?

> Note that you cannot use Shift-Ctrl-A-thru-F or Shift-Ctrl-0-thru-9 for your own purposes, as these combinations are used to enter unicode characters in text fields.
I guess that rules out ctrl+shift+d to delete all bookmarks. Maybe ctrl+m for bookMark? Even better, what about alt+left (pointing toward the sidebar where the bookmark will appear) for a toggle? Alt+right will cancel all bookmark, and alt+up/down alt+ctrl+home/end to navigate. So alt becomes the "bookmark" modifier... Only problem with this approach is that now alt+home/end becomes confusing...

> ctrl-u is used in word processors to underline words.
Just an example, I still prefer a single toggle... 

> In Scribes "ctrl-t" is used exclusively for indentation. "Tab" key does not perform indentation. It only inserts a "\t"(Tab) character into the buffer. This is very different from indentation.
But according to the circumstances tab means unequivocally indentation. If I am at the beginning of the line (or before the first non-white-space char) and hit tab I surely want to indent. If I select a block and hit tab, again, it means I want to indent. In the middle of a line tab will mean just "\t". I do not think there is any risk for confusion. And I also like that when I hit backspace at the first non-whitespace char, it de-indents. 

Basically, in code, when at the beginning of a line, indentation should be strongly enforced, it should be difficult to accidentally insert an odd number of white spaces.

> What is inconsistent about it?
If I press alt+home for instance it deletes since beginning of line, not since indentation. Bust shift+home will select since indentation.

---

### Post by Wolki on 2006-10-24
> **ago said:**
> "Choose access keys to be as easy to remember as possible. Normally, this means using the first letter of the label." :rolleyes: 

Access keys != shortcuts. Access keys are the underlined stuff you use with alt.

I guess ctrl-d was chosen because windows uses the same and the mac uses command-d. 
Shortcuts are language-independant, while access keys aren't... so for most people, the mnemonic wouldn't help.

> Even better, what about alt+left (pointing toward the sidebar where the bookmark will appear) for a toggle? Alt+right will cancel all bookmark, and alt+up/down alt+ctrl+home/end to navigate. So alt becomes the "bookmark" modifier... Only problem with this approach is that now alt+home/end becomes confusing...


hm... wouldn't it be a bit dangerous to have such a destructive action so easily accessed? Especially with crappy laptop keyboards...

---

### Post by Mystilleef on 2006-10-24
> **ago said:**
> I was thinking alt+up/down.

I like this. Now, I need to figure out what to use for the case operations.

> **ago said:**
> 
Well I do not understand what d has to do with b-o-o-k-m-a-r-k, but I do not always agree with HIG...

"Choose access keys to be as easy to remember as possible. Normally, this means using the first letter of the label." :rolleyes: 


The purpose of the HIG is to enforce consistency among application. If every GNOME application uses (ctrl-d) for bookmarks and I don't, it means users have a relearn an interface.

> **ago said:**
> 
They use CTRL+B for the "bookmark navigator", but in scribbles,


shouldn't FKeys be used for that to be consistent say with F9 for the "window navigator"?

GNOME applications use (ctrl-b) to show bookmark browsers. I don't see how it benefits users to break with this tradition.

> **ago said:**
> 
I guess that rules out ctrl+shift+d to delete all bookmarks. Maybe ctrl+m for bookMark?

I'm sticking with the HIG for bookmarking.

> **ago said:**
> 
 Even better, what about alt+left (pointing toward the sidebar where the bookmark will appear) for a toggle? Alt+right will cancel all bookmark,

This contradicts your suggestion to use the cursor keys for navigation.

> **ago said:**
> 
and alt+up/down alt+ctrl+home/end to navigate.


I like this. It will be implemented as soon as I can figure out what to use for the case operations.

> **ago said:**
> 
Just an example, I still prefer a single toggle... 


Yes, I appreciate the toggle theory.

> **ago said:**
> 
But according to the circumstances tab means unequivocally indentation. If I am at the beginning of the line (or before the first non-white-space char) and hit tab I surely want to indent.

I'm not sure I agree. "Tab" should be used to insert the "\t" character, not to indent. Indentation, in Scribes, is based on tab stops. Inserting characters is not. Let me give an example. Lets assume the first character in a line starts at column 3. When the user indents the line, the first character should be moved to column 4. This is assuming the user has a tab with of 4. However, if the user presses the "Tab" character, indentation should not occur. Instead, the "\t" character should be inserted, thus moving the first character in the line to column 7. 

> **ago said:**
> 
If I select a block and hit tab, again, it means I want to indent. In the middle of a line tab will mean just "\t". I do not think there is any risk for confusion. And I also like that when I hit backspace at the first non-whitespace char, it de-indents. 


This goes back to the same argument. Backspace should not be used for indentation, it should be used to remove characters. Same goes for the "Delete" character. Using for (un)indentation is inconsistent and wrong.

The reason most developers use these characters wrongly and inconsistently is because some of them use spaces instead of tabs for indentation. Thus they see "Tab" and "Backspace" as indentation functions are opposed to what they really are.


> **ago said:**
> 
Basically, in code, when at the beginning of a line, indentation should be strongly enforced, it should be difficult to accidentally insert an odd number of white spaces.

In Scribes you can enforce formating consistency by pressing (alt-t) if you use tabs as indentation characters and (alt-shift-t) if you use spaces as indentation characters. This performs a kind of automatic indentation for all lines in the buffer.

> **ago said:**
> 
If I press alt+home for instance it deletes since beginning of line, not since indentation. Bust shift+home will select since indentation.

That's a bug, it should be fixed.

---

### Post by ago on 2006-10-25
> **Mystilleef said:**
> 
Let me give an example. Lets assume the first character in a line starts at column 3. When the user indents the line, the first character should be moved to column 4. This is assuming the user has a tab with of 4. However, if the user presses the "Tab" character, indentation should not occur. Instead, the "\t" character should be inserted, thus moving the first character in the line to column 7.
I disagree on this. This will break indentation. Breaking indentation is extremely annoying in code (and particularly so in python, where it can even lead to situations hard to debug) and it should be difficult. If you are writing code with an indent of 4, there is no point at all in going to column 7. If you _really_ want to go to column 7, indent once and press 3 spaces, breaking indentation should not be easy. Moreover, since you mentioned consistency with gnome apps, that is what gedit does... 

> This goes back to the same argument. Backspace should not be used for indentation, it should be used to remove characters.
That depends on how you think of indentation. I think of it as a meta-char (not necessarily a "tab"), even when it is made of white spaces. When you hit backspace before an indentation, you remove the indentation meta-char. If you deleted a single whitespace (assuming you are using whitespaces for indentation) you would be break indentation, again that should be difficult in a code editor. If you _really_wanted that you could still use del and whitespace to do the damage.

> Thus they see "Tab" and "Backspace" as indentation functions are opposed to what they really are.
My suggested compromise is simple: before the first non-whitespace or when a block of code is selected, interpret tab and backspace as indentation commands, otherwise interpret them as normal. That has several advantages:

1) it is far safer if you are writing code since it will make it harder for people to break indentation.
2) Even if you have inconsistent behaviour of the same key (different action according to the situation), you will meet expactations of most users in most cases, since most users do use tab to indent
3) At the beginning of the line the difference between indentation and tab is a subtle one. When using tabs most people rely on visual feedback for the correct alignment, they can easily adjust for any difference using whitespace.


Another suggestion. What about transforming the template editor into a more generic "code profile" editor? What I mean is that you could use the same interface to specify:

1) code substitution
2) code-specific parameters (like single line comment and block comments, indentation width...)
3) actions (using shell)

In case 2 and 3 the token will be a predetermined word e.g. @SINGLE_LINE_COMMENT@, or @CTRL_1_ACTION@

---

### Post by alejandrops on 2006-10-25
hi! congrats for your app! 
I've been lloking for a nice clean editor like this!
I like the idea of no tabs, but I have 2 suggestions (not mine really, textmate made me love those tricks)

1) code folding: just a little icon can make code much more readable when editing big files.

[http://macromates.com/textmate/manual/navigation_overview#collapsing_text_blocks_foldings](http://macromates.com/textmate/manual/navigation_overview#collapsing_text_blocks_foldings)

2) a project drawer that let access to files with just one click, easier for editing huge projects with multiple directory levels.

great program! loving it right now

---

### Post by Mystilleef on 2006-10-25
> **ago said:**
> I disagree on this. This will break indentation.
It does not break anything. "Tab" **IS NOT** an indentation function. "Tab" is represented the by "\t" and "\t" **IS A** character. When you type a character into the buffer that character should be inserted into the buffer. Doing any other thing is inconsistent, wrong and annoying.

> **ago said:**
> 
 Breaking indentation is extremely annoying in code (and particularly so in python, where it can even lead to situations hard to debug) and it should be difficult.

Scribes already provides automatic indentation, errors like this are almost non-existent. Also remember that Scribes is not a Python editor, it is a general purpose editor. So your expectations in Python can break in other languages.

> **ago said:**
> 
If you are writing code with an indent of 4, there is no point at all in going to column 7.


There is! When users insert a character in the buffer, they expect the character to be inserted! The fact that you expect something else to happen is subjective, not objective. When a user inserts "a" in the buffer, they don't expect an editor to do any other thing but insert "a". If you expect the editor to do something else then that's just you personal preference.
> **ago said:**
> 
 If you _really_ want to go to column 7, indent once and press 3 spaces, 
This is wrong. What if the user really wants to insert "\t" in the buffer? You are in essence telling me that Scribes should prevent users from inserting "\t" in the buffer because you want to use "\t" as an indentation function instead of a character. So in order words, Scribes because unusable for a category of users who use "\t" as they are supposed to be used.

> **ago said:**
> 
breaking indentation should not be easy.

I agree. And that's why Scribes provides both automatic indentation and smart indentation. You have to put in some effort to break indentation.

> **ago said:**
> 
Moreover, since you mentioned consistency with gnome apps, that is what gedit does...

First of all Gedit does not do that. Second of all your logic is flawed. If some gnome apps do the "WRONG" thing, that doesn't mean I should blindly follow them.

> **ago said:**
> 
That depends on how you think of indentation. I think of it as a meta-char (not necessarily a "tab"),

Stop thinking like that. "\t" is a character, not a function or meta-character. Do you think of "a", "&", "8", "*" as meta-characters too? They are characters. Lets treat them like what they are not what we want them to be.

> **ago said:**
> 
 even when it is made of white spaces. When you hit backspace before an indentation, you remove the indentation meta-char. If you deleted a single whitespace (assuming you are using whitespaces for indentation) you would be break indentation, again that should be difficult in a code editor. Ifyou _really_wanted that you could still use del and whitespace to do the damage.


Yes, and this is reason why you shouldn't use whitespace for indentation. (ooops! :-D) I agree. Scribes is not smart about indentation if you use whitespace as indentation characters. This needs to be worked on. But there are functions to reformat your code properly.

> **ago said:**
> 
My suggested compromise is simple: before the first non-whitespace or when a block of code is selected, interpret tab and backspace as indentation commands, otherwise interpret them as normal. 

This rule is arbitrary, inconsistent and broken. Why don't we do the "RIGHT" thing? That is, threat "Tab" as "\t" and backspace as what it is. Why do we have to introduce new and inconsistent semantics to fit our needs. [/quote]


> **ago said:**
> 
That has several advantages:

1) it is far safer if you are writing code since it will make it harder for people to break indentation.

I don't see how it is easy for people to break indentation now. Scribes is over 40000 lines of code written in an indentation strict language, Python. I have never had broken indentations. So, I'd like to know how you are breaking indentation given all the function Scribes provides to prevent just that.

> **ago said:**
> 
2) Even if you have inconsistent behaviour of the same key (different action according to the situation), you will meet expactations of most users in most cases, since most users do use tab to indent

They use "Tab" as an indentation character yes. But that is different from indenting. Using "Tab" for smart indentation and character insertion will introduce inconsistencies and confusion. Because there may be times when user may really want to insert a "Tab" characters at the begining of a line, as opposed to indenting the line. With your suggestion they'll have no way to do that. That's like saying everytime a user types "a" I should replace it with "Aaaa". This is nice if the user expects this 90% of the time, but what happens when the user really wants to type "a"?


> **ago said:**
> 
3) At the beginning of the line the difference between indentation and tab is a subtle one. When using tabs most people rely on visual feedback for the correct alignment, they can easily adjust for any difference using whitespace.

Let me tell you why this is broken. Assuming a user want to insert a space and "\t" character at the beginning of a line, with your suggestion, Scribes makes it impossible for him to do that. Why should Scribes prevent people from inserting whatever character they want into the buffer?

Yesterday, I had a change of heart regarding the Tab for indentation issue, but now I'm entirely convinced that using Tab as an indentation function is semantically wrong and inconsistent. The good news is that a plug-in system will allow someone to implement this behavior. In Scribes there's one clear what to indent line(s).

    (ctrl - t) - for indentation
    (ctrl - shift - t) - for unindentation

This is clear, unambigious and simple. And this actually does smart indentation unlike most other editors.

> **ago said:**
> 
Another suggestion. What about transforming the template editor into a more generic "code profile" editor? What I mean is that you could use the same interface to specify:

1) code substitution
2) code-specific parameters (like single line comment and block comments, indentation width...)


I don't understand this. Can you give concrete examples and how it will benefit most users.

> **ago said:**
> 
3) actions (using shell)

In case 2 and 3 the token will be a predetermined word e.g. @SINGLE_LINE_COMMENT@, or @CTRL_1_ACTION@

  Isn't arbitrarily running shell scripts from the buffer a security vulnerability? Or maybe this not what you are saying?


I welcome more feedback. 

Cheers

---

### Post by Mystilleef on 2006-10-25
> **alejandrops said:**
> hi! congrats for your app! 
I've been lloking for a nice clean editor like this!
I like the idea of no tabs, but I have 2 suggestions (not mine really, textmate made me love those tricks)

1) code folding: just a little icon can make code much more readable when editing big files.

[http://macromates.com/textmate/manual/navigation_overview#collapsing_text_blocks_foldings](http://macromates.com/textmate/manual/navigation_overview#collapsing_text_blocks_foldings)


Code folding will be implemented by a third party library, gtksourceview. They plan to unveil it for version 2.0. 

> **alejandrops said:**
> 
2) a project drawer that let access to files with just one click, easier for editing huge projects with multiple directory levels.

great program! loving it right now

I've argued against this in the past. I've argued that the open dialog in GNOME serves as project drawer, and recreating  a TM-like drawer is duplicative effor and reinventing the wheel. However, the purpose of the plug-in system is to allow developers extend Scribes however they wish if they don't agree with my point of view. It looks like something that'll be implemented as a plug-in.

Cheers

---

### Post by alejandrops on 2006-10-25
thanks for the answer!
good to know that code folding will be implemented. this is looking so good.

about the drawer> well, I know that reinventing the weel is bad, so maybe we can find a more creative way to access files quickly :)
meanwhile: how can I develop a plugin for the drawer? in phyton? guidelines?

By the way, I love the webpage design.

---

### Post by Mystilleef on 2006-10-25
> **alejandrops said:**
> 
about the drawer> well, I know that reinventing the weel is bad, so maybe we can find a more creative way to access files quickly :)
meanwhile: how can I develop a plugin for the drawer? in phyton? guidelines?

The plug-in system has been developed but will not be enabled until 0.3.1. It will be officially released to the public by version 0.4. By then there will be extensive documentation on how to write plug-ins. However, if after version 0.3.1 you are still eager to write plug-ins you can get in touch with me via IRC/email/Jabber and I'll be glad to help you with any questions.

> **alejandrops said:**
> 
By the way, I love the webpage design.

Thanks

Cheers

---

### Post by NoWhereMan on 2006-10-25
> **alejandrops said:**
> meanwhile: how can I develop a plugin for the drawer? in phyton? guidelines?


there's not yet an open interface for plugins, he will implement it in the next releases (read the older posts)

---

### Post by ago on 2006-10-25
> **Mystilleef said:**
> What if the user really wants to insert "\t" in the buffer?
Well I cannot think of many cases in any programming language where you want anything else than correct indentation at beginning of the line. And that does not only mean having the right number of chars for each indent but also the same types of chars for each indent. Python requires good indentation, but in all other languages it is a good practice anyway. I believe that in a coding editor good indentation should be strongly enforced, particularly when users press the most common key used for indentation, which happens to be 'tab' key. 

In practice, inserting "\t" should be treated as an exception because: 

1) The chances that you "really want to insert '\t' in the buffer" are slim, particularly when programming

2) there are 2 possible mistakes: inserting "indent" when you mean "\t", and inserting "\t" when you mean "indent"; you need to minimize the most common error and the most dangerous one... The second case is more common by a few orders of magnitude.

3) inserting "\t" when you mean "indent" can lead to problems (more so than the other way around) since it can create wrong indentation both in terms of indentation lengh and in terms of characters used (by mixing spaces and tabs). If you mix tabs and spaces other people will not have the same indentation that you see. In some programming languages having the wrong indentation can create errors, often difficult to debug. 

Therefore if a user really wants to have "\t" at the beginning of the line, he should make such will VERY explicit e.g. by using ctrl+t (or any other combination). I would:

* assign '\t' to a key cobination (ctrl+t?)
* assign tab stop (possibly represented by whitespaces) to the tab key
* assign indentation to the tab key when used before first nonwhitespace char (which is fairly similar to tab stop)
* assign indentation to the tab key when used on a multi-line selection
* assign deindent to backspace when used before first nonwhitespace char, i.e. no change in behaviour when tabs are used to indent, but slightly different behaviour (read safer) when whitespaces are used.
* assign deindent to backspace when used on a multi-line selection

With the above keybindings it should be fairly difficult to break indentation.

> I don't see how it is easy for people to break indentation now.
Simple: if you use spaces for indentation (indent=4) your cursor is at col 3 (you think is at 4) and you hit tab, you break indentation. If you are at col 8 and hit backspace deleting 1 white space, you break indentation. If the first 4 chars are white spaces and you insert a "\t" and you start coding at col 8, you break indentation, since you are mixing characters (you do not know how long "\t" is going to be when someone else opens the file). All of the above should be difficult.

> That's like saying everytime a user types "a" I should replace it with "Aaaa".
The difference is that when people press "a" they mean "a". When people press "Tab", in the vast majority of cases, they mean "indent", not "\t". And differently from "a", when you use "\t" for the wrong reason: 1) you will not be able to spot it, since "\t" is not visible, 2) as explained, it may create problems, sometimes extremely difficult to debug.  

> I don't understand this. Can you give concrete examples and how it will benefit most users.

I have an editor (scite) that uses "#~" for commenting a line in python, another that uses "#". The behaviour is different when uncommenting. In the second case, when toggling the comment, I will also toggle lines that where manually commented (e.g. real comment lines), in the first case I can only uncomment lines that were previously comment by the toggle. Another example: I may want to block comment C++ code with "//" as opposed to "/* ... */", so that I can uncomment individual lines. So it is nice to be able to tell you what is the preferred commenting style for individual lines and code blocks. Also because you need this info anyway... I might also want to use different tabbing styles in different languages. And so forth. Basically this gives a way to override general settings for each language, and to provide information about the language (what is the comment char?), all without changing the interface.

> Isn't arbitrarily running shell scripts from the buffer a security vulnerability? Or maybe this not what you are saying?
I might want to conveniently run the code through pylint for instance or to save the code and pass the file to "ipython -d" or run a regex testing application... 

Ciao,

Ago

---

### Post by Mystilleef on 2006-10-25
> **ago said:**
> Well I cannot think of many cases in any programming language where you want anything else than correct indentation at beginning of the line. And that does not only mean having the right number of chars for each indent but also the same types of chars for each indent. Python requires good indentation, but in all other languages it is a good practice anyway. I believe that in a coding editor good indentation should be strongly enforced, particularly when users press the most common key used for indentation, which happens to be 'tab' key. 

In practice, inserting "\t" for anything other than indenting is the exception because: 

I'm not going to make assumptions about how people use indentation. In my experience, some people use "\t", some use spaces and some use a combination of both. If you have a look at many Java, C, C++ and GTK+ projects, many use a combination of both for indentation and alignment. The fact that Python enforces strict indentation does not mean we should impose Python's linguistic syntax on non-Python users.


> **ago said:**
> 
1) it is not common (using "indent" when you mean "\t" is far less common than using "\t" when you mean "indent", particularly in programming)

I have evidence to prove it is common. Take a lot at any GNOME project and you'll see people use a combination of "\t" and space for alignment. Heck, take a look at the GTK+ source code, you'll see the function parameters are aligned in a combination of "\t" and spaces.

> **ago said:**
> 
2) it can lead to problems when you misuse it, creating wrong indentation both in terms of indentation lengh and in terms of characters used (by mixing spaces and tabs). In some programming languages this can create errors, often difficult to debug. If you mix tabs and spaces other people will not have the same indentation that you see.


Scribes provides functions to prevent this. Do you have problems with them?

> **ago said:**
> 
Therefore if a user really wants to have "\t" at the beginning of the line, he should make such will VERY explicit e.g. by using ctrl+t (or any other combination). I would:

* assign '\t' to a key cobination (ctrl+t?)
* assign tab stop (possibly represented by whitespaces) to the tab key
* assign indentation to the tab key when used before first nonwhitespace char (which is fairly similar to tab stop)
* assign indentation to the tab key when used on a multi-line selection
* assign deindent to backspace when used before first nonwhitespace char, i.e. no change in behaviour when tabs are used to indent, but slightly different behaviour (read safer) when whitespaces are used.
* assign deindent to backspace when used on a multi-line selection

I am not going to override established standard Tab and Backspace behavior to adhere to Python semantics. Not everyone uses Python. Pressing Tab should insert "\t" in the buffer. Pressing Backspace should remove a single character from the buffer. It's simple, clear and consistent. The exception is when people  (wrongly, IMO) use spaces for indentation.

> **ago said:**
> 
With the above keybindings it should be fairly difficult to break indentation.

Why I don't like the above solution:

1). It is inconsistent
2). It is heavily influenced by the semantics of a single language, Python. Scribes is a general purpose editor.
3). It is wrong. When users type a character, the character should be inserted, nothing more nothing less.
4). It leads to confusion. Pressing Tab should behave the same way regardless of where it is pressed in the buffer.
5). Overriding the default behavior keys violates usability principles.
6). Coding overhead and complexity for little gain.

> **ago said:**
> 
Simple: if you use spaces for indentation (indent=4) your cursor is at col 3 (you think is at 4) and you hit tab, you break indentation. 
If you are at col 8 and hit backspace deleting 1 white space, you break indentation. If the first 4 chars are white spaces and you insert a "\t" and you start coding at col 8, you break indentation, since you are mixing characters
 and you do not know how long "\t" is going to be when someone else opens the file. All of the above should be difficult.


Sure, if you intentionally go out of your way to break indentation, there's nothing an editor can do about it. And an editor should never prevent you from doing that if you want to. In addition, Scribes provides functions to convert spaces to tabs and vice-versa. These functions do automatic indentation.

> **ago said:**
> 
The difference is that when people press "a" they mean "a". When people press "Tab", in the vast majority of cases, they mean "indent", not "\t". 

That's not accurate. People also press "\t" for formating purposes.  You can't speak for everyone, just for yourself unless you have usability data to validate your beliefs.

> **ago said:**
> 
And differently from "a", when you use "\t" for the wrong reason: 1) you will not be able to spot it, since "\t" is not visible, 2) as explained, it may create problems, sometimes extremely difficult to debug.  


And as stated, Scribes provides functions to eliminate these problems and even prevent them.

> **ago said:**
> 
I have an editor (scite) that uses "#~" for commenting a line in python, another that uses "#". The behaviour is different when uncommenting. In the second case, when toggling the comment, I will also toggle lines that where manually commented (e.g. real comment lines), in the first case I can only uncomment lines that were previously comment by the toggle. Another example: I may want to block comment C++ code with "//" as opposed to "/* ... */", so that I can uncomment individual lines. So it is nice to be able to tell you what is the preferred commenting style for individual lines and code blocks.

There should be command to allow users to use different commenting styles that the source code supports. I don't like the idea of having users meddle with configuration to establish behavior like that. Or better yet the editor should use an algorithm that figures out when which commenting style is appropriate. I have a "zero-configuration", "full-automation" principle with Scribes.

> **ago said:**
> 
Also because you need this info anyway... I might also want to use different tabbing styles in different languages. And so forth. Basically this gives a way to override general settings for each language, and to provide information about the language (what is the comment char?), all without changing the interface.


Yes, a modes plug-in should be implemented for this, like how VIM, Emacs, Kate do it.

> **ago said:**
> 
I might want to conveniently run the code through pylint for instance or to save the code and pass the file to "ipython -d" or run a regex testing application... 

My opinion is that the function of a text editor is to modify, process and manipulate text, not launch third party programs or what not. You can install an IDE or a terminal for that. Of course you are welcome to implement this as plug-ins to suit your needs.

I enjoy your insights. I welcome more feedback.

Cheers

---

### Post by ago on 2006-10-25
> The fact that Python enforces strict indentation does not mean we should impose Python's linguistic syntax on non-Python users.
It is a good practice in ANY language, including plain text. Python has nothing to do with it. C code will well work without any indentation at all, but you cannot read code without indentation, and code you cannot read you cannot maintain... Code with wrong indentation is even worse than code with no indentation since you can easily misinterpret it. Making it easy for users to do crap indentation does not make their life any better, quite the opposite... 

> I have evidence to prove it is common. Take a lot at any GNOME project and you'll see people use a combination of "\t" and space for alignment.

Exactly my point...

A line with 2 tabs and a line with 8 spaces may look completely different according to the tab settings of each user. If you have tab of 2 the first line will look as a "parent", it will look the other way around if you have tabs of 8, and the lines will look as siblings if you have tabs of 4... The code will run just the same in many languages, but it will be difficult to read and maintain. The result is a mess. And it is a mess whether you are using python, C, or even "formatted" plain text.

What you should ask is: "did the developers did that on purpose?" Clearly not. What you see is the result of using a poor editor that did not encourage proper indentation, coupled with lack of attention to details... Second question: "would have it been better if indentation had been consistent across the document?" Third question: "would have been better if the editor had helped the users to keep consistent indentation?" 

> Scribes provides functions to prevent this. Do you have problems with them?
I think it is an excellent idea. I just happen to think that to prevent the situations like the ones you just mentioned, even more should be done and strict indentation should be encouraged by the editor. Not enforced, but strongly encouraged. The keybindings I suggested move in that direction.

> The exception is when people  (wrongly, IMO) use spaces for indentation.
There is nothing wrong with spaces, the problem is when people mix tabs and spaces or change indentation settings within a file, or use the wrong indentation alltogether... Which unfortunately happens a lot, and part of the blame has to be on the editors.

> Sure, if you intentionally go out of your way to break indentation, there's nothing an editor can do about it.
Wrong. Take your own example. Did GNOME developers INTENTIONALLY want to mix tabs and spaces? No they didn't. Then, if they did so UNINTENTIONALLY, don't you think that a good code editor should have helped preventing that?

> And an editor should never prevent you from doing that if you want to.
Wrong. It should prevent to make UNINTENTIONAL mistakes. As mentioned you can still intentionally mess it up using del, whitespace and ctrl+t to insert and delete individual "\t" and spaces to your heart content. But the editor should make it clear that it is your INTENTION to mess it up...

> People also press "\t" for formating purposes.
Not in code, whatever the language. If you use "\t" in code in order to format, it is always within quoted text where in most cases you will have to escape it. And even in plain text most of the use of "\t" is to align stuff. If stuff is properly indented, it is also properly aligned. If stuff is not properly indented or with mixed tabs and spaces, it will not be properly aligned. It may look aligned on your screen, but not on someone else's screen, and that is certainly not what users want. Therefore proper indentation will be beneficial ALSO when editing plain text and formatting documents. There are very few cases where you require exactly a "\t" char in the buffer instead of proper indentation/alignment. In those few cases you can use ctrl+t. Every time you hit tab key ask yourself: "do I want text to be properly indented/aligned or do I want to insert the '\t' char?" 

Ciao Ago

---

### Post by Mystilleef on 2006-10-25
> **ago said:**
> It is a good practice in ANY language, Python has nothing to do with it. C code will well work without any indentation at all, but you cannot read code without indentation, and code you cannot read you cannot maintain... Code with wrong indentation is even worse than code with no indentation since you can easily misinterpret it. Making it easy for users to do crap indentation does not make their life any better, quite the opposite... 

I am not arguing about whether or not indentation is bad. I think indentation is good. My argument is that overriding the semantic behavior of the Tab ("\t") character is wrong. It's simple. When a user types a character into the buffer, the character should be inserted. You are telling me to override this fundamental expectation.

> **ago said:**
> 
Exactly my point...

A line with 2 tabs and a line with 8 spaces may look completely different according to the tab settings of each user. 


This is why tabs should be used for indentation, not spaces. Tabs allow editors to display documents with correct indentation regardless of tab width people use. This is not the case with spaces.

> **ago said:**
> 
If you have tab of 2 the first line will look as a "parent", it will look the other way around if you have tabs of 8, and the lines will look as siblings if you have tabs of 4... The code will run just the same in many languages, but it will be difficult to read and maintain. The result is a mess. 

Assuming you are using tabs for indentation __not__ spaces, the document should display exactly as you expect in your editor. If I use a tab width of 20 and you use one of 4, the document I edited will open in your editor as if I used a tab width of 4. This is not the case with spaces, however.

> **ago said:**
> 
What you should ask is: "did the developers did that on purpose?" Clearly not. 

Yes. They do it to align arguments of functions in different lines to aid readability. If tabs performed indentation instead of inserting the "\t" alignment will rapidly become a nuisance.

> **ago said:**
> 
What you see is the result of using a poor editor that did not encourage proper indentation, coupled with lack of attention to details... Second question: "would have it been better if indentation had been consistent across the document?" You answer...

If people do not indent their code properly, there's nothing an editor can do about it. Scribes provides functions to perform indentation. Heck it does automatic indentation by default. So, I can't force anyone to use indentation if they don't want to. And there's no reason why I should impose my indentation ideology on anybody.

> **ago said:**
> 
I think it is an excellent idea. I just happen to think that to prevent the situations like the ones you just mentioned, even more should be done and strict indentation should be encouraged by the editor. Not enforced, but strongly encouraged. The keybindings I suggested move in that direction.

I disagree. Users should take the initiative to indent/format their code as they see fit. Editors should provide them with the facilities to do so easily.

> **ago said:**
> 
There is nothing wrong with spaces, the problem is when people mix tabs and spaces or change indentation settings within a file, or use the wrong indentation alltogether... Which unfortunately happens a lot, and part of the blame has to be on the editors.


There's a lot wrong with spaces. The most annoying is that if a user uses 7 spaces for indentation, then all editors have to display those 7 spaces. It doesn't matter that my editor is set to indent lines at 4 spaces. There's also an element of torture  on the part of text editor developers associated with catering for instances where people use spaces for indentation intead of tabs. But I digress.

> **ago said:**
> 
Wrong. Take your own example. Did GNOME developers INTENTIONALLY want to mix tabs and spaces? No they didn't.


Yes, they did, see above.

> **ago said:**
> 
Then, if they did so UNINTENTIONALLY, don't you think that a good code editor should have helped preventing that?


No! The editor should not make such assumptions. In this case making such assumptions would have irritated users who wanted alignment, not indentation.

> **ago said:**
> 
Wrong. It should prevent to make UNINTENTIONAL mistakes. As mentioned you can still intentionally mess it up using del, whitespace and ctrl+t to insert "\t", spaces as much as you like. But the editor should make it clear that it is your INTENTION to mess it up...


Yeap and Scribes provides facilities to prevent such mistakes.

> **ago said:**
> 
Not in code, whatever the language. If you use "\t" in code to format, it is always within quoted text where you will have to escape it. And even in plain text most of the use of "\t" is to align stuff. If stuff is properly indented, it is also properly aligned. If stuff is not properly indented or with mixed tabs and spaces, it will not be properly aligned. It may look aligned on your screen, but not on someone else's screen, and that is certainly not what users want. Therefore proper indentation will be beneficial also when editing plain text. There are very few cases where you require exactly a "\t" char in the buffer instead of proper indentation. In those few cases you can use ctrl+t.

Ciao Ago

People use tab for alignment all the time. Today I was editing a gtkrc theme file were I saw code like this
```
    xthickness                        = 2 # default 0
    ythickness                        = 2 # default 0
    bg_pixmap[NORMAL]                = "Panel/panel-bg.png"
    bg_pixmap[SELECTED]                = "Panel/panel-bg.png"
    bg_pixmap[INSENSITIVE]            = "Panel/panel-bg.png"
    bg_pixmap[PRELIGHT]                = "Panel/panel-bg.png"

```The code was aligned in a way were all the equal signs were properly aligned via tabs. I've seen this is  C/C++/Java/Haskell/Basic code too.

Cheers

---

### Post by ago on 2006-10-26
> **Mystilleef said:**
> Assuming you are using tabs for indentation __not__ spaces, the document should display exactly as you expect

You simply cannot assume that. Particularly when different people work on the same document. Or even if you open the document with a different editor. If one editor uses tabs and one editor uses spaces and you mix the two your alignment/indentation is gone for good. And the worse part is that you will not even notice that, since things may look ok on your screen. Did you have ever received a mail or text file with a table aligned with tabs and spaces that was all over the place? I bet you did. Take your gtkrc table above, if a new developer adds a line to the table and he is using spaces for tab, the alignment in the table will become inconsistent.

I can summarize it like that: people hit tab because they want their text to be indented or aligned. The fact that the tab key inserts "\t" is completely instrumental, and unfortunately "\t" mixed with spaces will screw up alignment and indentation far more often than it will get it right. Even worse, it will screw things up in subtle ways, such that text that looks aligned/indented on your screen will not look the same with different set-ups. And if that is a problem in text files, it is even worse in source code, and particularly in python where you can even introduce errors. But it is by no means a python-only problem. You can either help people consistently indent/align text they way they want. or you can help them consistently insert "\t". You can pick only one of the two. Your choice.

---

### Post by Mystilleef on 2006-10-26
> **ago said:**
> You simply cannot assume that. Particularly when different people work on the same document. Or even if you open the document with a different editor. If one editor uses tabs and one editor uses spaces and you mix the two your alignment/indentation is gone for good. And the worse part is that you will not even notice that, since things may look ok on your screen. Did you have ever received a mail or text file with a table aligned with tabs and spaces that was all over the place? I bet you did. Take your gtkrc table above, if a new developer adds a line to the table and he is using spaces for tab, the alignment in the table will become inconsistent.

This is why people should use Tabs for indentation. :-) And if you are worried about mixing Tabs with spaces, Scribes provides a function to take care of such discrepancies.

> **ago said:**
> 
I can summarize it like that: people hit tab because they want their text to be indented or aligned. The fact that the tab key inserts "\t" is completely instrumental, and unfortunately "\t" mixed with spaces will screw up alignment and indentation far more often than it will get it right. Even worse, it will screw things up in subtle ways, such that text that looks aligned/indented on your screen will not look the same with different set-ups. And if that is a problem in text files, it is even worse in source code, and particularly in python where you can even introduce errors. But it is by no means a python-only problem. You can either help people consistently indent/align text they way they want. or you can help them consistently insert "\t". You can pick only one of the two. Your choice.

Here's the thing, Scribes goes above and beyond most editors to provide mechanisms to indent your code or text properly and perform various formatting operations. If people ignore or fail to use these functions, neither I nor Scribes can be blamed for their decisions.

---

### Post by Mystilleef on 2006-10-26
Hello,

 Yet another release. Many small tweaks, bug fixes and enhancements based on your feedbacks. In particular, the keyboard shortcuts for bookmark and case operations have changed. Sorry for the inconvenience. Added French translation. New templates for Ruby and ROR, and some more.

Your feedbacks have made Scribes better. You all ROCK! :cool:

Flash Demo: [http://scribes.sf.net/demo.htm](http://scribes.sf.net/demo.htm)

website: [http://scribes.sf.net/](http://scribes.sf.net/)

download: [http://scribes.sf.net/download.html](http://scribes.sf.net/download.html)

templates: [http://scribes.sf.net/templates.tar.bz2](http://scribes.sf.net/templates.tar.bz2) 

Thanks

---

### Post by Buffalo Soldier on 2006-10-26
> **Mystilleef said:**
> Hello,

 Yet another release. Many small tweaks, bug fixes and enhancements based on your feedbacks. In particular, the keyboard shortcuts for bookmark and case operations have changed. Sorry for the inconvenience. Added French translation. New templates for Ruby and ROR, and some more.

Your feedbacks have made Scribes better. You all ROCK! :cool:

Flash Demo: [http://scribes.sf.net/demo.htm](http://scribes.sf.net/demo.htm)

website: [http://scribes.sf.net/](http://scribes.sf.net/)

download: [http://scribes.sf.net/download.html](http://scribes.sf.net/download.html)

templates: [http://scribes.sf.net/templates.tar.bz2](http://scribes.sf.net/templates.tar.bz2) 

ThanksDoes the previous version needs to be uninstalled first before installing this new one?

---

### Post by Mystilleef on 2006-10-26
> **Buffalo Soldier said:**
> Does the previous version needs to be uninstalled first before installing this new one?

No it doesn't.

Cheers

---

### Post by Buffalo Soldier on 2006-10-26
> **Mystilleef said:**
> No it doesn't.

CheersThanks Mystilleef,

Scribes rocks. I think the song "My Way" by Frank Sinatra should be the official song of Scribes :)

---

### Post by Anonii on 2006-10-26
The first thing I do in new releases on any program is search for a .deb in the same thread. Probably a bad habbit since many of them are created wrongly with checkinstall. If someone is like me, and wants to install it from a .deb, instead of a source, download the .deb I created **using checkinstall** *(which is not the correct way on turning source to debs)*

[http://rapidshare.com/files/759389/scribes_0.2.9.89-1_i386.deb.html](http://rapidshare.com/files/759389/scribes_0.2.9.89-1_i386.deb.html)

(Thanks for the great release once again Mystileef!)

---

### Post by ago on 2006-10-26
Thank you Mystilleef. I really think this editor will become a star. I will install the new version tonight!

---

### Post by NoWhereMan on 2006-10-27
> **Anonii said:**
>  download the .deb I created **using checkinstall** *(which is not the correct way on turning source to debs)*

OOOOOT: I'm very sorry to ask, but why? I'm really curious I was wondering myself some days ago about that

---

### Post by Mystilleef on 2006-10-31
Hello Folks,

New release. This is most likely going to be the last release before 0.3. You can now change scope highlight colors via gconf. Plenty bug fixes.

Cheers

[http://scribes.sf.net/download.html](http://scribes.sf.net/download.html)

---

### Post by ruimoura on 2006-10-31
Scribes 0.2.9.90 debian file here - [http://ruimoura.net/software/scribes/](http://ruimoura.net/software/scribes/)

Done with checkinstall :rolleyes:

---

### Post by chaosgeisterchen on 2006-11-01
> **ruimoura said:**
> Scribes 0.2.9.90 debian file here - [http://ruimoura.net/software/scribes/](http://ruimoura.net/software/scribes/)

Done with checkinstall :rolleyes:

As far as I know checkinstall-created debs are not capable of running anywhere as they are adapted to the system they were created with. 

I once tried to create a package this way and to distribute it but I was told not to do it as it would not run on another machine without issues...

---

### Post by ruimoura on 2006-11-01
> **chaosgeisterchen said:**
> As far as I know checkinstall-created debs are not capable of running anywhere as they are adapted to the system they were created with. 

I once tried to create a package this way and to distribute it but I was told not to do it as it would not run on another machine without issues...

Yes, i know it can work or not. But did you try it? I'm new at creating .deb packages and this is the easy way ...

---

### Post by dr_kabuto on 2006-11-02
I've upload a native deb package for edgy here:
[http://digilander.libero.it/dr_kabuto/](http://digilander.libero.it/dr_kabuto/)

---

### Post by zachtib on 2006-11-02
Just a suggestion, and if I should post this elsewhere, tell me and I will:

But for the next release, I guess 0.4, you should implement a tabbed interface for editing multiple files at the same time.
Also, when using tabs, you should be able to display two tabs side by side.  This would certainly come in handy for coding.

I'm using 0.2.90 right now... I think you just replaced gedit for me

great work :)

---

### Post by ruimoura on 2006-11-02
Dude, i recommend you to read this - [http://mystilleef.blogspot.com/2006/10/no-tabs-why.html](http://mystilleef.blogspot.com/2006/10/no-tabs-why.html)

:-k

---

### Post by zachtib on 2006-11-02
> **ruimoura said:**
> Dude, i recommend you to read this - [http://mystilleef.blogspot.com/2006/10/no-tabs-why.html](http://mystilleef.blogspot.com/2006/10/no-tabs-why.html)

:-k

either way, it's his project and he's welcome to do with it what he likes.

I'll use it regardless

---

### Post by ruimoura on 2006-11-02
> **zachtib said:**
> either way, it's his project and he's welcome to do with it what he likes.

I'll use it regardless

Me too :)

---

### Post by NoWhereMan on 2006-11-02
a little suggestion (maybe)
adding some kind of visual feedback when indenting lines would be useful expecially when editing a language such as python where indententation is important

something like a thin grey line (as seen in SciTE/Scintilla)

```

def myfunc()
 | # <--- this is a indenting line
 | # here goes my code
 | f()

```

this should help with inner loops or conditional tests
```

def myfunc()
 | if (something) :
    |  # let's do something
    |  do_something()
 | # outside the if

```

etc...

and... still the language chooser thingy :D

---

### Post by Mystilleef on 2006-11-04
Hello,

I am pleased to announce the release of version 0.3 of Scribes. Thanks for your feedback and contributions. :-)

Cheers

Download: [http://scribes.sf.net/download.html](http://scribes.sf.net/download.html)

Templates: [http://scribes.sf.net/templates.tar.bz2](http://scribes.sf.net/templates.tar.bz2)

Release Notes: [http://scribes.sf.net/release-note-0-3.html](http://scribes.sf.net/release-note-0-3.html)

---

### Post by ummo on 2006-11-04
First of all Scribes is looking to be a great program, and i thank you for your work!

i am wondering if there is any progress on getting scribes to work with sudo?   With edgy the version of the python D-Bus bindings is 0.71-2ububtu1 and i see that your website lists D-Bus version 0.6 as a dependency.  Should that cause any problems?
this is the error i receive when i run:  
```
sudo scribes

Traceback (most recent call last):
  File "/usr/local/bin/scribes", line 39, in ?
    main(argv[1:])
  File "/usr/local/lib/python2.4/site-packages/SCRIBES/dbusmain.py", line 53, in main
    from info import dbus_iface
  File "/usr/local/lib/python2.4/site-packages/SCRIBES/info.py", line 32, in ?
    session_bus = SessionBus()
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 266, in __new__
    return Bus.__new__(cls, Bus.TYPE_SESSION, use_default_mainloop, private)
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 99, in __new__
    bus._connection = dbus_bindings.bus_get(bus_type, private)
  File "dbus_bindings.pyx", line 1692, in dbus_bindings.bus_get
dbus_bindings.DBusException: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```
dunno if this information helps at all

---

### Post by Mystilleef on 2006-11-04
> **ummo said:**
> First of all Scribes is looking to be a great program, and i thank you for your work!

i am wondering if there is any progress on getting scribes to work with sudo?   With edgy the version of the python D-Bus bindings is 0.71-2ububtu1 and i see that your website lists D-Bus version 0.6 as a dependency.  Should that cause any problems?
this is the error i receive when i run:  
```
sudo scribes

Traceback (most recent call last):
  File "/usr/local/bin/scribes", line 39, in ?
    main(argv[1:])
  File "/usr/local/lib/python2.4/site-packages/SCRIBES/dbusmain.py", line 53, in main
    from info import dbus_iface
  File "/usr/local/lib/python2.4/site-packages/SCRIBES/info.py", line 32, in ?
    session_bus = SessionBus()
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 266, in __new__
    return Bus.__new__(cls, Bus.TYPE_SESSION, use_default_mainloop, private)
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 99, in __new__
    bus._connection = dbus_bindings.bus_get(bus_type, private)
  File "dbus_bindings.pyx", line 1692, in dbus_bindings.bus_get
dbus_bindings.DBusException: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```dunno if this information helps at all

This is a known problem. I hope to fix it by 0.3.1.

Cheers

---

### Post by raublekick on 2006-11-04
hi. i made a deb for this using checkinstall. hopefully it works for others as well.

[http://jaraub.good-evil.net/jaraub/debs/scribes_0.3-1_i386.deb](http://jaraub.good-evil.net/jaraub/debs/scribes_0.3-1_i386.deb)

scribes seems pretty neat, but i dunno if it will be replacing emacs :)

---

### Post by nandasunu on 2006-11-05
> **raublekick said:**
> hi. i made a deb for this using checkinstall. hopefully it works for others as well.

[http://jaraub.good-evil.net/jaraub/debs/scribes_0.3-1_i386.deb](http://jaraub.good-evil.net/jaraub/debs/scribes_0.3-1_i386.deb)

Thanks.

---

### Post by CrippledCanary on 2006-11-05
I'm working with a "proper" .deb package built with pbuilder on edgy.
Will hopefully be ready tonight.

---

### Post by CrippledCanary on 2006-11-05
Here you have it... a "proper" built .deb for Edgy.
It might still have some messy dependencies but it works for me.

[scribes_0.3-0ubuntu1_i386.deb]("http://ubuntu.crippledcanary.se/scribes_0.3-0ubuntu1_i386.deb")

If you check at [http://ubuntu.crippledcanary.se](http://ubuntu.crippledcanary.se) you will be able to download the diff.gz and dsc files as well.
Please report any package errors to me by email.

crippledcanary(at-location)remove-me(dot)gmail(dot)com

---

### Post by [h2o] on 2006-11-05
I really, really want to like this editor. But no tabs means lots of open windows, and I don't like that. The document switcher is neat, but superfluos  to me since I can already ALT-Tab, and does not solve problem of having lots of windows open.
So sorry, I really like it, but I'll just stick to gedit with tabs.

---

### Post by CrippledCanary on 2006-11-06
I uploaded the latest .deb to REVU. If we are lucky it might be included in universe some day.

---

### Post by Wolki on 2006-11-06
> **CrippledCanary said:**
> I uploaded the latest .deb to REVU.

You rock.

I'll likely still install it manually to get newer versions, but good job.

---

### Post by altonbr on 2006-11-08
Things I find missing:

-multiple line tabs (A.K.A. selecting 5 lines and indenting all of them at the same time simply by pressing 'tab')
-embedded syntax highlighting for JavaScript or CSS _inside_ an HTML file.
**documentation on how to install the program in Ubuntu and it's templates. I'm fairly new to Linux in general so I don't know how to install a .deb or run your install.sh inside scribes-0.3.tar.bz2 (so in general, better documentation for Laymens :D)

I LOVE the minimalism though. I'm a big fan (Y)

---

### Post by Mystilleef on 2006-11-08
> **altonbr said:**
> Things I find missing:

-multiple line tabs (A.K.A. selecting 5 lines and indenting all of them at the same time simply by pressing 'tab')
-embedded syntax highlighting for JavaScript or CSS _inside_ an HTML file.
**documentation on how to install the program in Ubuntu and it's templates. I'm fairly new to Linux in general so I don't know how to install a .deb or run your install.sh inside scribes-0.3.tar.bz2 (so in general, better documentation for Laymens :D)

I LOVE the minimalism though. I'm a big fan (Y)

Hello,

Thanks for your feedback.

- You can press (ctrl - t) to indent a line or selected lines.

- This will be provided by the gtksourceview library in the nearest future.

- The README file has instructions on how to install Scribes on Linux.
You'll have to see Ubuntu's guide on how to install application's on it.
I found this:
    [http://ubuntuforums.org/archive/index.php/t-6365.html](http://ubuntuforums.org/archive/index.php/t-6365.html)
    [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

You can install new templates by downloading the templates tarball,
unpacking it and dragging and dropping each xml file to the templates
editor (alt - F12).

    [http://scribes.sf.net/templates.tar.bz2](http://scribes.sf.net/templates.tar.bz2)

Cheers

---

### Post by zachtib on 2006-11-08
one thing, and i may have mentioned this before, would it be possible to run this without all the gnome libs?  its minimalism seems like it would fit nicely in XFCE

---

### Post by Mystilleef on 2006-11-09
> **zachtib said:**
> one thing, and i may have mentioned this before, would it be possible to run this without all the gnome libs?  its minimalism seems like it would fit nicely in XFCE

The GNOME libraries are essential for Scribes to function. Without them, there'll be no Scribes. However, you don't need to run GNOME to run Scribes. Scribes runs well in XFCE, KDE and any other *nix DE or WM.

Cheers

---

### Post by zachtib on 2006-11-09
I know, I've installed it, I was just looking for a good editor that doesn't involve pulling down all the gnome libs

---

### Post by Mystilleef on 2006-11-09
> **zachtib said:**
> I know, I've installed it, I was just looking for a good editor that doesn't involve pulling down all the gnome libs

Leafpad?

[http://tarot.freeshell.org/leafpad/](http://tarot.freeshell.org/leafpad/)

---

### Post by Anonii on 2006-11-10
```
$ gksudo scribes
Traceback (most recent call last):
  File "/usr/bin/scribes", line 39, in ?
    main(argv[1:])
  File "/usr/lib/python2.4/site-packages/SCRIBES/dbusmain.py", line 53, in main
    from info import dbus_iface
  File "/usr/lib/python2.4/site-packages/SCRIBES/info.py", line 32, in ?
    session_bus = SessionBus()
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 266, in __new__
    return Bus.__new__(cls, Bus.TYPE_SESSION, use_default_mainloop, private)
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 99, in __new__
    bus._connection = dbus_bindings.bus_get(bus_type, private)
  File "dbus_bindings.pyx", line 1692, in dbus_bindings.bus_get
dbus_bindings.DBusException: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```
And there it ends, without any scribes popping up.
;_;

---

### Post by NoWhereMan on 2006-11-10
> **Anonii said:**
> 
And there it ends, without any scribes popping up.
;_;

known issue; it depends on python-dbus

---

### Post by Anonii on 2006-11-10
> **NoWhereMan said:**
> known issue; it depends on python-dbus
Is it fixable, yet?

Thanks for the fast reply.

---

### Post by NoWhereMan on 2006-11-10
> **Anonii said:**
> Is it fixable, yet?

I don't think so. It depends on that dbus lib; it won't be fixed until the library itself it's fixed byt the ubuntu team :)

> Thanks for the fast reply.

;)

---

### Post by AgenT on 2006-11-10
> **Mystilleef said:**
> This is why tabs should be used for indentation, not spaces. Tabs allow editors to display documents with correct indentation regardless of tab width people use. This is not the case with spaces.
....
There's a lot wrong with spaces. The most annoying is that if a user uses 7 spaces for indentation, then all editors have to display those 7 spaces. It doesn't matter that my editor is set to indent lines at 4 spaces. There's also an element of torture  on the part of text editor developers associated with catering for instances where people use spaces for indentation intead of tabs. But I digress.

RIGHT, so why does Scribes have "Use spaces instead of tabs" enabled by default? That is a major disappointment after reading this thread and then trying out Scribes. Not because this option is hard to change, but because this was not expected. There is the thought of "I wonder what else will this editor break in my already existing files". And having spaces as default results in horrible code in Scribes due to the auto indentation of templates being tabs (at least in the Python template). Therefore with default settings one ends up with some lines using spaces, some tabs. Glad I did not use this on my existing files, but instead played around with it using a temporary file (see where the "I wonder what else...") comes in?

A few disadvantages of Scribes to vim:[LIST]
[*]GUI-based. The "one editor to rule them all" idea goes out the window as it cannot be used for everything and in every situation. Meaning you cannot just know Scribes, but Scribes and some other editor. But this cannot be fixed.
[*]Learning curve. Yes, it probably is small compared to full-blown vi/emacs, but it is still there. And actually, the learning curve of "basic" vim is very small. There are very few shortcuts that are really needed in vim to zip around a buffer in no time. Switching means learning shortcuts all over again.
[*]No regular expressions: this will no doubt be a deal breaker for a lot of users. Maybe incorporate sed itself into the editor? Even if you plan on having sed like regular expressions incorporated directly within the editor, for now embedding sed would be fine (and a quicker way of enabling regex).
[*]Home-row keys ideology is broken. Scribes feels "all over the place" and slow.
[*]While this may sound strange: major features, like templates, require learning a lot of shortcuts (ex. svdef in Python template) and requires a lot of configuration to make it powerful (creating custom templates). With vim, my config file consists of two options and it has been like that for years.[/LIST]There is a major problem with most of the points above: they are vim-centric (and very biased, of course). I wrote them to as an aid to understand former advanced editor (like vim) users. As an ex-vim user, maybe you could compile a vim-to-scribes document to help wean vim users to Scribes.

Another small gripe: looking through the Python template, there seem to be some very odd shortcuts like cmt. What is the purpose of writing "cmd" to get "#"? Maybe I am missing a feature.

And the demo is a great idea. It does show some nice things about Scribes. And it is refreshing to see an editor like Scribes. May you have great success with this (because you already deserve it)!

---

### Post by Mystilleef on 2006-11-10
> **AgenT said:**
> RIGHT, so why does Scribes have "Use spaces instead of tabs" enabled by default?

It isn't enabled by default. Maybe the GConf schema was not properly installed on your system. 

> **AgenT said:**
> 
 That is a major disappointment after reading this thread and then trying out Scribes. Not because this option is hard to change, but because this was not expected. There is the thought of "I wonder what else will this editor break in my already existing files". And having spaces as default results in horrible code in Scribes due to the auto indentation of templates being tabs (at least in the Python template). Therefore with default settings one ends up with some lines using spaces, some tabs. Glad I did not use this on my existing files, but instead played around with it using a temporary file (see where the "I wonder what else...") comes in?


There's a command to convert spaces to tabs. The undo function is also useful.

> **AgenT said:**
> 
GUI-based. The "one editor to rule them all" idea goes out the window as it cannot be used for everything and in every situation. Meaning you cannot just know Scribes, but Scribes and some other editor. But this cannot be fixed.

If you use a non-GUI environment, it's time to upgrade to the 21st century. :-D Even server environments these days have GUI panels and control. I'm sure I didn't understand this gripe.

> **AgenT said:**
> 
Learning curve. Yes, it probably is small compared to full-blown vi/emacs, but it is still there. And actually, the learning curve of "basic" vim is very small. There are very few shortcuts that are really needed in vim to zip around a buffer in no time. Switching means learning shortcuts all over again.

Are you really comparing the learning curve of VIM/Emacs to Scribes? :-D At least you don't have to read a manual to learn how to quit Scribes. If you have a non-Geek member of your family. Sit the person before Scribes and VIM. Allow them to use it for a while. Give absolutely no instructions. Then ask then which they found easier to use, learn and navigate around. I've done this tests myself, but I'd be pleased to hear the result of your experiment.

> **AgenT said:**
> 
No regular expressions: this will no doubt be a deal breaker for a lot of users. 


Good point! I don't agree it is a deal breaker for many users, maybe a few. It's one of the things I hope to work on before 0.4. 

> **AgenT said:**
> 
Home-row keys ideology is broken. Scribes feels "all over the place" and slow.

You lost me here. Can you expatiate?

> **AgenT said:**
> 
While this may sound strange: major features, like templates, require learning a lot of shortcuts (ex. svdef in Python template)

You can modify template trigger to something you can remember. You don't have to learn all the template triggers, just the ones you use frequently.

> **AgenT said:**
> 
 and requires a lot of configuration to make it powerful (creating custom templates).

So does VIM. :-D Pray tell me how would you get templates working on VIM? You need to go to the InterWeb, download some  *.vim file, install the it, read the manual, install the templates, learn the templates shortcut keys, and pray it works. Oh, and I'm simplifying things here. Took me 2 hours to get templates working on VIM. And what's worse, it didn't work well. :-D

> **AgenT said:**
> 
 With vim, my config file consists of two options and it has been like that for years.

You are not real VIM user. :-D When I was VIM user I spent months crafting my vimrc. So much so that when I lost it, I became depressed for days. Ah the good old days. :-D

> **AgenT said:**
> 

There is a major problem with most of the points above: they are vim-centric (and very biased, of course). I wrote them to as an aid to understand former advanced editor (like vim) users. As an ex-vim user, maybe you could compile a vim-to-scribes document to help wean vim users to Scribes.

Tutorial for VIM users:

1). Scribes is not VIM.
2). Scribes does not try to be VIM.
3). Scribes will never be VIM.
4). Scribes uses keyboard shortcuts that follow GNOME and widely used Desktop conventions, not VIM.
5). See the manual for all operations you can perform via shortcut keys. Do not attempt to learn them all in one day.
6). Did I mention Scribes is not VIM?

> **AgenT said:**
> 
Another small gripe: looking through the Python template, there seem to be some very odd shortcuts like cmt. What is the purpose of writing "cmd" to get "#"? Maybe I am missing a feature.


If you don't like any of the templates, you can change them or remove them completely.

Thanks for your feedback.

Cheers

---

### Post by AgenT on 2006-11-10
Before responding further, a misunderstanding needs to be addressed. Everything that was posted before was not meant as an attack on you or Scribes. In fact, nothing (except my question at the end) was meant as a personal criticism of mine. As I stated somewhere in the post: "There is a major problem with most of the points above: they are vim-centric (and very biased, of course). *I wrote them as an aid to understand former advanced editor (like vim) users*." I meant this as a usability observation from a(nother) vim users' perspective (not including yourself, of course - since obviously you had your reasons for quitting vim and writing Scribes). 

> **Mystilleef said:**
> It isn't enabled by default. Maybe the GConf schema was not properly installed on your system. I used the deb file from the website without any prior use of Scribes, making my install a "fresh install". scribes.schemas was installed on my system. Maybe there is something wrong with how the schema file is loaded the first time (wild guess)? Here is the original (taken from the deb) schema file (truncated):
```
        <schema>
            <key>/schemas/apps/scribes/tab</key>
            <applyto>/apps/scribes/tab</applyto>
            <owner>Scribes</owner>
            <type>int</type>
            <default>4</default>
            <locale name="C">
                <short>Tab width</short>
                <long>Sets the width of tab stops within the editor</long>
            </locale>
        </schema>

        <schema>
            <key>/schemas/apps/scribes/use_tabs</key>
            <applyto>/apps/scribes/use_tabs</applyto>
            <owner>Scribes</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short>Use Tabs instead of spaces</short>
                <long>
                    True to use tabs instead of spaces, false otherwise.
                </long>
            </locale>
```The schema file seems to be okay. No idea why it did not load. It was installed to:
```
etc/gconf/schemas/scribes.schemas
```> **Mystilleef said:**
>  Are you really comparing the learning curve of VIM/Emacs to Scribes? :-D At least you don't have to read a manual to learn how to quit Scribes. If you have a non-Geek member of your family. Sit the person before Scribes and VIM. Allow them to use it for a while. Give absolutely no instructions. Then ask then which they found easier to use, learn and navigate around. I've done this tests myself, but I'd be pleased to hear the result of your experiment.You subjected your family members to vim?! :twisted: In all seriousness, this is what showed me that there was a misunderstanding. I meant this from a <enter a powerful text editor/emacs> user's perspective.

OK, so my previous post was a bad attempt and I did not explain myself well enough. (this is why I am skipping a lot of things in this response)

Do realize that even though it may not have sounded like it, I was trying to help.

> **Mystilleef said:**
>  Good point! I don't agree it is a deal breaker for many users, maybe a few. It's one of the things I hope to work on before 0.4.Nice!

> **Mystilleef said:**
>  You are not real VIM user. :-D Maybe. However, a long time ago I did have a nice and long vimrc file. After some time I realized that it was not really all that helpful due to my text editing habits.

> **Mystilleef said:**
> If you don't like any of the templates, you can change them or remove them completely.I actually like the templates and they are a very good way of learning the template system. I was just confused by some of the entries in the Python template. To quote myself, "What is the purpose of writing "cmd" to get "#"? *Maybe I am missing a feature*." I take your response to mean that I was not missing a feature. ;)

> **Mystilleef said:**
>  Thanks for your feedback. Thank you for the nice editor! Hopefully this post is more understandable than my previous one. And for all it is worth, think of my previous post as a (rather long) free bump. :rolleyes:

Again, good luck with your work. It looks very promising.

---

### Post by Mystilleef on 2006-11-10
> **AgenT said:**
> Before responding further, a misunderstanding needs to be addressed. Everything that was posted before was not meant as an attack on you or Scribes. In fact, nothing (except my question at the end) was meant as a personal criticism of mine. As I stated somewhere in the post: "There is a major problem with most of the points above: they are vim-centric (and very biased, of course). *I wrote them as an aid to understand former advanced editor (like vim) users*." I meant this as a usability observation from a(nother) vim users' perspective (not including yourself, of course - since obviously you had your reasons for quitting vim and writing Scribes). 

I actually want you to attack and criticize Scribes. How else will
it get better? How I take your feedback is irrelevant. What is relevant
is your subtle influence on the future of the project. I encourage more
feedback/opinions/suggestions/criticisms/comparisons regardless of how
gentle or acrimonious they may be.  I've stopped trying to gauge
emotions when interacting on the Internet. :-)

> **AgenT said:**
> 
I used the deb file from the website without any prior use of Scribes, making my install a "fresh install". scribes.schemas was installed on my system. Maybe there is something wrong with how the schema file is loaded the first time (wild guess)? 

GConf's cache needs to be updated after the schema files are installed.
Package managers are supposed to take care of this but many of them 
don't. Gconf has many other annoying attributes that may be responsible
for your problem, but that's a story for another day. :-D

> **AgenT said:**
> 
You subjected your family members to vim?! :twisted: In all seriousness, this is what showed me that there was a misunderstanding. I meant this from a <enter a powerful text editor/emacs> user's perspective. OK, so my previous post was a bad attempt and I did not explain myself well enough. (this is why I am skipping a lot of things in this response)
 

Believe it or not, much of Scribes text manipulation functions is
influenced by VIM, the line operations in particular. But I'm positive
I misunderstood your point. I thought your were saying VIM/Emacs is
easier to use than Scribes. More powerful? Maybe. Easier to use? Not
so sure. :-D

> **AgenT said:**
> 
Do realize that even though it may not have sounded like it, I was trying to help.

Thank you. I appreciate all the help I can get. I encourage you to be do
more however you can.

> **AgenT said:**
> 
Maybe. However, a long time ago I did have a nice and long vimrc file. After some time I realized that it was not really all that helpful due to my text editing habits.

That was partially a joke. I didn't mean to say you are an inferior VIM user. It may have sounded like that, but that wasn't my intention. The point I was trying to get accross was that to do anything meaningful in VIM, you have to spend days/weeks/months configuring it and reading manuals. That was fun when I was a young geek. But I've grown older, colder and impatient. Any application that requires extensive configuration, unnecessary tampering, time wastage, sacrifice to the Unix gods, and manual reading will be ignored by me. Hence the reason I started Scribes. In the time it takes you to be productive with Scribes, you'd still be learning how save and quit VIM. Okay, I'm biased. :-D

 
> **AgenT said:**
> 
I actually like the templates and they are a very good way of learning the template system. I was just confused by some of the entries in the Python template. To quote myself, "What is the purpose of writing "cmd" to get "#"? *Maybe I am missing a feature*." I take your response to mean that I was not missing a feature. ;) 

Okay, maybe I didn't answer the query right. I actually prefer typing "cmt", than (shift + 3 + space). It is faster and  my brain has been programmed to type "cmt" when I need to comment anything in any source code (Java, C, XML, HTML, etc). So that template was influenced by my own work habit. I realize my work patterns maybe different from yours, and I can understand why you'll find the template redundant, but for me it is bliss. :-D So if you do not like any template or template trigger, feel free to modify it however you wish. Because what makes sense for me, may not for someone else.
> **AgenT said:**
> 
 Thank you for the nice editor! Hopefully this post is more understandable than my previous one. And for all it is worth, think of my previous post as a (rather long) free bump. :rolleyes:

Again, good luck with your work. It looks very promising.

Thanks for the feedback. For the record, I didn't see anything wrong with your previous post. Your post made me realize the frustration a VIM user might experience when trying to use Scribes, which will in one way or another influence how I work on Scribes in the future. Software is about people not machines. So  your feedback is invaluable.

Cheers

---

### Post by AgenT on 2006-11-11
> **Mystilleef said:**
> The point I was trying to get accross was that to do anything meaningful in VIM, you have to spend days/weeks/months configuring it and reading manuals... Any application that requires extensive configuration, unnecessary tampering, time wastage, sacrifice to the Unix gods, and manual reading will be ignored by me. Hence the reason I started Scribes.Correct. And this is one of the appealing things about Scribes. There should not be a need to do anything unnecessary at all. Option toggles are silly if they are just there to give people an option. If there is an option, that may mean that there is some problem that needs to be solved. I took a very similar approach to the application ([Bonager]("http://www.ubuntuforums.org/showthread.php?t=295262")) that I started developing not too long ago. 3 clicks maximum to get anything done. Only 1 real option in the application and a smart dialogue interface that only shows you what you need to know. What's the point of giving the user a choice when the application can be written to be smart enough to know when one option makes no sense and presents the user with the other.

> **Mystilleef said:**
> So if you do not like any template or template trigger, feel free to modify it however you wish. Because what makes sense for me, may not for someone else. Two suggestions:[LIST=1]
[*]Use version numbers for the template pack if you intend to release it multiple times (and you should if you add new keys)
[*]If not done so already (have not tested this), make template importation smart in this way: when I have key name cmt for Python and I import your Python script, your cmt should not overwrite mine. Maybe renaming the new cmt to cmt2 would be a good solution.[/LIST]> **Mystilleef said:**
> Your post made me realize the frustration a VIM user might experience when trying to use ScribesNow *that* was my intention in that first post of mine.

One quick (somewhat irrelevant to Scribus) question: What distribution do you use? And what made you look into Ubuntu(forums)? The large userbase?

And a suggestion: Include user submissions into the template archive file you have available, filename <user>_<language>.xml. Once too many people are submitting their templates to you, create an easy to use repo for user created templates. One where no registration is required and you have 3 fields total: file upload field, language and user(name). Parse the file to make sure it is an xml file and you should be safe (and even tar it immediately for extra security). Then have a page that lists them all for download.

A Scribes suggestion: make it possible to add custom languages in templates.

Again, good luck,
Possible Scribes Convert ;)

---

### Post by Mystilleef on 2006-11-11
> **AgenT said:**
> Correct. And this is one of the appealing things about Scribes. There should not be a need to do anything unnecessary at all. Option toggles are silly if they are just there to give people an option. If there is an option, that may mean that there is some problem that needs to be solved. I took a very similar approach to the application ([Bonager]("http://www.ubuntuforums.org/showthread.php?t=295262")) that I started developing not too long ago. 3 clicks maximum to get anything done. Only 1 real option in the application and a smart dialogue interface that only shows you what you need to know. What's the point of giving the user a choice when the application can be written to be smart enough to know when one option makes no sense and presents the user with the other.

I agree. By the way, Bonager is an interesting project.
> **AgenT said:**
>  
[LIST=1]
[*]Use version numbers for the template pack if you intend to release it multiple times (and you should if you add new keys)[/LIST]Point taken.

> **AgenT said:**
> [LIST=1]
[*]If not done so already (have not tested this), make template importation smart in this way: when I have key name cmt for Python and I import your Python script, your cmt should not overwrite mine. Maybe renaming the new cmt to cmt2 would be a good solution.[/LIST]Yes, this is how it currently works.

> **AgenT said:**
> 
One quick (somewhat irrelevant to Scribus) question: What distribution do you use? 

I use Gentoo. I managed to break my Gentoo box. I cringed at the idea of installing it from Scratch. I decided the best thing to do was to install Ubuntu and then install Gentoo from Ubuntu. That way I could still be productive while Gentoo takes years to install. I installed Ubuntu Edgy Eft and it rocked my world. I was so impressed I decided to stick with for a long while, before eventually returning to Gentoo. Now, I use the Ubuntu partition primarily for testing. 

> **AgenT said:**
> And what made you look into Ubuntu(forums)? The large userbase?

Yes, the large user base and the friendly community. 

> **AgenT said:**
> 
And a suggestion: Include user submissions into the template archive file you have available, filename <user>_<language>.xml. Once too many people are submitting their templates to you, create an easy to use repo for user created templates. One where no registration is required and you have 3 fields total: file upload field, language and user(name). Parse the file to make sure it is an xml file and you should be safe (and even tar it immediately for extra security). Then have a page that lists them all for download.


That's brilliant. People are also free to email me templates for languages that do not have one.

> **AgenT said:**
> 
A Scribes suggestion: make it possible to add custom languages in templates.

Again, good luck,
Possible Scribes Convert ;)

Language support and generation is closely tied to GtkSourceView. So I have little or no control over that. However there is a "General" section where you place templates that don't belong to any particular language.


Cheers

---

### Post by AgenT on 2006-11-11
> **Mystilleef said:**
> Language support and generation is closely tied to GtkSourceView. So I have little or no control over that. However there is a "General" section where you place templates that don't belong to any particular language.Why does Scribes use gconf for its configuration? Why not use ~/.scribes/? Gconf may make things a little easier for some GNOME-only developers, but it makes things frustrating for users. For example, I wanted to test Scribes' problem with loading gconf. I removed Scribes fully and searched recursively for scribes in the ~ directory. Found two entries (under ~/.gconf and /.gnome2) and deleted them. Installed Scribes and found out my settings were saved somehow from the previous install. Annoying!](*,)  Using gconf is not good for the user because it is difficult to track down configuration files and remove them in case something goes wrong. It is very easy to remove ~/.app/ and have everything restart to default. However, I understand if GNOME itself wants to use its own config file method (but Scribes is not a required GNOME application).

---

### Post by AgenT on 2006-11-11
Attached is a quick template for the vBulletin board. Not every tag is supported. Attached with .txt because .xml is not allowed.

SUGGESTION: I just noticed that embedding one template keyword in another does not work. Using vB template (provided in attachment):
[noparse]
_ = cursor placement
vbh\t = [highlight]_[highlight]
vbi\t = *_*

Now try this:
vbh\t, and then vbi\t

The expected result is this:
[highlight]*_*[/highlight]

However, Scribes gives this result:
[highlight]\t_[/highlight]
[/noparse]

SUGGESTION #2:
There should be a "View All" shortcuts option in the help menu or a full list on the website.

UPDATE: fixed bad attachment - xml file only had one entry.

---

### Post by AgenT on 2006-11-11
Attached is the complete shortcut list taken from Scribes menu and converted into an image. PNG file format and made to be printed on one page.

---

### Post by altonbr on 2006-11-11
> **Mystilleef said:**
> 
- This will be provided by the gtksourceview library in the nearest future.


I personally cannot use this software until it supports highlighting JavaScript and CSS inside HTML AND the use of regular expressions.

Your program is coming along create, I just really need these functions as a Web Developer... so sadly, at the moment, I have to use a much MUCH larger text-editor (basically SDK) to do this.

---

### Post by NoWhereMan on 2006-11-11
> **altonbr said:**
> I personally cannot use this software until it supports highlighting JavaScript and CSS inside HTML AND the use of regular expressions.

textmate does not support such a feature too on mac AFAIK, what we really one would need is a quick way to switch from a language to another :) sorry to bug you, Mystilleef :D

bye

---

### Post by altonbr on 2006-11-11
> **Mystilleef said:**
> > RIGHT, so why does Scribes have "Use spaces instead of tabs" enabled by default?It isn't enabled by default. Maybe the GConf schema was not properly installed on your system.

I have the same problem... not that it's really a big deal, really... but maybe you can force it to turn off in the next version???


In addition to my other post and NoWhereMan, I've used Scribes, BlueFish, SCREEM, gEdit, gPhpEdit, jEdit &  Eclipse... and they all just make me miss Notepad++ (from win32). All of them seem to have some good features here, but missing others there. NONE of them have everything I need/want from a text editor. Scribes is close. But gEdit is closer.


A thing I love about Scribes compared to BlueFish is your Syntax Color Editor. It's quite ingenious with it's integration to the color picker library (if there is such a thing). Bluefish makes you type in long RGB code which just doesn't make sense for a smooth work flow (having to open GIMP or a similar App).


Darn, isn't it annoying trying to please everyone?

---

### Post by Mystilleef on 2006-11-11
> **AgenT said:**
> Why does Scribes use gconf for its configuration? Why not use ~/.scribes/? Gconf may make things a little easier for some GNOME-only developers, but it makes things frustrating for users. For example, I wanted to test Scribes' problem with loading gconf. I removed Scribes fully and searched recursively for scribes in the ~ directory. Found two entries (under ~/.gconf and /.gnome2) and deleted them. Installed Scribes and found out my settings were saved somehow from the previous install. Annoying!](*,)  Using gconf is not good for the user because it is difficult to track down configuration files and remove them in case something goes wrong. It is very easy to remove ~/.app/ and have everything restart to default. However, I understand if GNOME itself wants to use its own config file method (but Scribes is not a required GNOME application).

Scribes is GNOME app. All GNOME apps use GConf for storing configuration information.

---

### Post by Mystilleef on 2006-11-11
> **AgenT said:**
> Attached is a quick template for the vBulletin board. Not every tag is supported. Attached with .txt because .xml is not allowed.

SUGGESTION: I just noticed that embedding one template keyword in another does not work. Using vB template (provided in attachment):
[noparse]
_ = cursor placement
vbh\t = [highlight]_[highlight]
vbi\t = *_*

Now try this:
vbh\t, and then vbi\t

The expected result is this:
[highlight]*_*[/highlight]

However, Scribes gives this result:
[highlight]\t_[/highlight]
[/noparse]

SUGGESTION #2:
There should be a "View All" shortcuts option in the help menu or a full list on the website.

UPDATE: fixed bad attachment - xml file only had one entry.

Thanks I'll look at these templates and add them to the templates tarball. The problem with your template is that Scribes is reading all the letters before the template trigger itself. So Scribes can see the template. This is because any character with the exception of space can be a template trigger.

---

### Post by Mystilleef on 2006-11-11
> **AgenT said:**
> Attached is the complete shortcut list taken from Scribes menu and converted into an image. PNG file format and made to be printed on one page.

Thanks, I'll upload this to the website.

---

### Post by Mystilleef on 2006-11-11
> **NoWhereMan said:**
> textmate does not support such a feature too on mac AFAIK, what we really one would need is a quick way to switch from a language to another :) sorry to bug you, Mystilleef :D

bye

I hope to work on this for 0.3.x release.

Cheers

---

### Post by Mystilleef on 2006-11-11
> **AgenT said:**
> Why does Scribes use gconf for its configuration? Why not use ~/.scribes/? Gconf may make things a little easier for some GNOME-only developers, but it makes things frustrating for users. For example, I wanted to test Scribes' problem with loading gconf. I removed Scribes fully and searched recursively for scribes in the ~ directory. Found two entries (under ~/.gconf and /.gnome2) and deleted them. Installed Scribes and found out my settings were saved somehow from the previous install. Annoying!](*,)  Using gconf is not good for the user because it is difficult to track down configuration files and remove them in case something goes wrong. It is very easy to remove ~/.app/ and have everything restart to default. However, I understand if GNOME itself wants to use its own config file method (but Scribes is not a required GNOME application).

Read this on why you should use GConf for your applications. It also goes into details about where configuration information is stored.
 
[http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/)

Cheers

---

### Post by AgenT on 2006-11-11
> **Mystilleef said:**
> Thanks I'll look at these templates and add them to the templates tarball. The problem with your template is that Scribes is reading all the letters before the template trigger itself. So Scribes can see the template. This is because any character with the exception of space can be a template trigger.That makes sense and it should be that way. But is it possible to circumvent this in the template? Or am I stuck with having to always add a space after some character if I wish to activate another trigger?

---

### Post by AgenT on 2006-11-11
> **Mystilleef said:**
> Read this on why you should use GConf for your applications. It also goes into details about where configuration information is stored.
 
[http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/)

CheersThank you for the link.

---

### Post by Mystilleef on 2006-11-12
> **AgenT said:**
> That makes sense and it should be that way. But is it possible to circumvent this in the template? Or am I stuck with having to always add a space after some character if I wish to activate another trigger?

I have not yet found a sane (clean) way to do that yet. I'm reluctant to uglify the syntax. I am thinking about adding an escape character, maybe (`). If you have any ideas, do not hesitate to share them.

Cheers

---

### Post by Mystilleef on 2006-11-12
> **AgenT said:**
> Why does Scribes use gconf for its configuration? Why not use ~/.scribes/? Gconf may make things a little easier for some GNOME-only developers, but it makes things frustrating for users. For example, I wanted to test Scribes' problem with loading gconf. I removed Scribes fully and searched recursively for scribes in the ~ directory. Found two entries (under ~/.gconf and /.gnome2) and deleted them. Installed Scribes and found out my settings were saved somehow from the previous install. Annoying!](*,)  Using gconf is not good for the user because it is difficult to track down configuration files and remove them in case something goes wrong. It is very easy to remove ~/.app/ and have everything restart to default. However, I understand if GNOME itself wants to use its own config file method (but Scribes is not a required GNOME application).

Hello,

Finally found time to investigate the GConf problem. Apparently, I was 
not doing enough checks in case GConf is not properly reloaded after
installation. Thus many default values I thought were initialized 
weren't. The problem has now been fixed. The fix will be in version 
0.3.1. Thanks for the feedback.

Cheers

---

### Post by AgenT on 2006-11-12
> **Mystilleef said:**
> I have not yet found a sane (clean) way to do that yet. I'm reluctant to uglify the syntax. I am thinking about adding an escape character, maybe (`). If you have any ideas, do not hesitate to share them.Would it be possible for Scribes to automatically inherit an "escape" behind the scenes in the document?

Here is what I mean. And do note that this can be done in a variety of ways and I am just presenting one way. Scribes knows when a trigger has been triggered and can escape the next character that will be typed on a ${}. That is to say, a hidden escape would be put automatically to the left of every bracket that belongs to the trigger AFTER a trigger is activated. The removed after the trigger is completed. And this hidden escape would literally be hidden. The user would not see anything happening.

Here is an example from your Python template. The original trigger:
```
for ${item} in ${list}:
    ${cursor}
```Now when I type for and press tab this would happen:
```
for `${item} in `${list}:
    `${cursor}
```But the ` would of course not be visible (not even a blank space).
After I fill in ${item}, ${list} and ${cursor}, Scribes removes all the ` hidden escapes.

The escape would have one function: treat whatever comes directly after it as a separate entry (as if there were a space between what is to the left of ` and what is to the right). 

Therefore, to use another example, a trigger that is triggered by vbi and looks like this: ```
[noparse]*${text}*[/noparse]
``` would actually look like this to Scribes (again, this being hidden from the user):
```
[noparse]*`${text}*[/noparse]
``` and would be treated by Scribes exactly like: ```
[noparse]* ${text}*[/noparse]
``` (notice the space between [noparse][i][/noparse] and ${text}. That would be all that Scribes would need to do because Scribes is already smart enough to understand that if there is a space before the next toggle, then that next toggle is executed.

---

### Post by AgenT on 2006-11-12
Few things that would make Scribes more powerful:[LIST=1]
[*]A way to comment a line and selection. This may be solved (although maybe not to your liking) if using regex (sed) on selection and line is possible. ex. s/^/#/g. The sed way would eliminate Scribes from having to know what comment character to use in a given context. Or, if making this built in (not sed), have a popup or whatnot and ask the user to enter a character to use for comment.
[*]Ability to replace in selection only. When I highlight a selection and hit replace, that text is pre-filled into the find field. This is useful some of the time, but what if I only want to replace x with y in one part of the document?[/LIST]Can you explain to me what incremental search is? I am sure that I already used it with different editors, but I do not understand what that phrase means nor can I figure out what it does.

---

### Post by Patrick K. on 2006-11-12
Totally awesome application! Just the thing I need to help me learn to make some of my own stuff. Thanks bro!

---

### Post by dbbolton on 2006-11-13
> **PriceChild said:**
> Just thought i'd point out [http://scribes.sourceforge.net/demo.htm](http://scribes.sourceforge.net/demo.htm) doesnt' work for me....

I had a problem with flash earlier on youtube... maybe its just me.

Edgy's flash won't reinstall for me....
yeah, didn't go for me either.

---

### Post by Mystilleef on 2006-11-13
> **AgenT said:**
> Would it be possible for Scribes to automatically inherit an "escape" behind the scenes in the document?

Here is what I mean. And do note that this can be done in a variety of ways and I am just presenting one way. Scribes knows when a trigger has been triggered and can escape the next character that will be typed on a ${}. That is to say, a hidden escape would be put automatically to the left of every bracket that belongs to the trigger AFTER a trigger is activated. The removed after the trigger is completed. And this hidden escape would literally be hidden. The user would not see anything happening.

Here is an example from your Python template. The original trigger:
```
for ${item} in ${list}:
    ${cursor}
```Now when I type for and press tab this would happen:
```
for `${item} in `${list}:
    `${cursor}
```But the ` would of course not be visible (not even a blank space).
After I fill in ${item}, ${list} and ${cursor}, Scribes removes all the ` hidden escapes.

The escape would have one function: treat whatever comes directly after it as a separate entry (as if there were a space between what is to the left of ` and what is to the right). 

Therefore, to use another example, a trigger that is triggered by vbi and looks like this: ```
[noparse]*${text}*[/noparse]
``` would actually look like this to Scribes (again, this being hidden from the user):
```
[noparse]*`${text}*[/noparse]
``` and would be treated by Scribes exactly like: ```
[noparse]* ${text}*[/noparse]
``` (notice the space between [noparse][i][/noparse] and ${text}. That would be all that Scribes would need to do because Scribes is already smart enough to understand that if there is a space before the next toggle, then that next toggle is executed.

That's a possible solution. However, the implementation overhead is
expensive. I was thinking of something a little simpler. Like adding
(`) before template triggers. Assuming you have a trigger called "for",
if you want to expand the trigger regardless of where it is found, you
just type "`for". The possible drawback to this is that (`) may not be
used as a trigger or part of one.

---

### Post by AgenT on 2006-11-13
> **dbbolton said:**
> yeah, didn't go for me either.Works fine here (Edgy). Using:
```
 flashplugin-nonfree     7.0.68~ubuntu3
```No other flash plugin is installed. Do note that this was NOT a fresh install.

---

### Post by AgenT on 2006-11-13
> **Mystilleef said:**
> That's a possible solution. However, the implementation overhead is
expensive. I was thinking of something a little simpler. Like adding
(`) before template triggers. Assuming you have a trigger called "for",
if you want to expand the trigger regardless of where it is found, you
just type "`for". The possible drawback to this is that (`) may not be
used as a trigger or part of one.
Or how about hitting the escape key one time instead of `? Or is this, again, a problem with overhead? Actually, the ` idea sounds better as it ends up the same thing and ` is closer while ESC is too far away from home row. As long as the ` is automatically removed (or not even shown).

---

### Post by Mystilleef on 2006-11-13
> **AgenT said:**
> Few things that would make Scribes more powerful:[LIST=1]
[*]A way to comment a line and selection. This may be solved (although maybe not to your liking) if using regex (sed) on selection and line is possible. ex. s/^/#/g. The sed way would eliminate Scribes from having to know what comment character to use in a given context. Or, if making this built in (not sed), have a popup or whatnot and ask the user to enter a character to use for comment.[/LIST]This will be implemented as language plug-ins because how you comment
code is source code dependent.

> **AgenT said:**
> [LIST=1]
[*]Ability to replace in selection only. When I highlight a selection and hit replace, that text is pre-filled into the find field. This is useful some of the time, but what if I only want to replace x with y in one part of the document?[/LIST]You navigate to the part of the document using the "next" button, and
replace the highlighted text using the "replace" button.

> **AgenT said:**
> 
Can you explain to me what incremental search is? I am sure that I already used it with different editors, but I do not understand what that phrase means nor can I figure out what it does.

Incremental searching means text is searched beginning from the cursor
position as opposed to the beginning of the document.

---

### Post by Mystilleef on 2006-11-13
> **dbbolton said:**
> yeah, didn't go for me either.

This is an old GIF demo.

[http://www.minds.may.ie/~dez/images/blog/scribes.html]("http://www.minds.may.ie/%7Edez/images/blog/scribes.html")

I can't find PriceChild's post..

Cheers

---

### Post by Mystilleef on 2006-11-13
> **AgenT said:**
> Or how about hitting the escape key one time instead of `? Or is this, again, a problem with overhead? Actually, the ` idea sounds better as it ends up the same thing and ` is closer while ESC is too far away from home row.

I prefer (`) because ESC is usually used to exit operations in most applications including Scribes. In fact, I believe in earlier versions of Scribes ESC was also used to exit template mode. 

> **AgenT said:**
> 
 As long as the ` is automatically removed (or not even shown).
It will be shown (so as not to confuse users into thinking their keyboard or Scribes is broken) but it will be removed when the trigger is expanded.

Cheers

---

### Post by AgenT on 2006-11-13
> **Mystilleef said:**
> This will be implemented as language plug-ins because how you comment
code is source code dependent.That sounds great.> **Mystilleef said:**
> You navigate to the part of the document using the "next" button, and
replace the highlighted text using the "replace" button.That is possible, but takes a very long time when needing to something multiple times.

For example, let us say that I have a function foo() and I use foo() 40x in the document. I want to replace foo() with foo2() in all but one instance. Now I have to find/replace 39 times. It would be easier just to highlight everything but that 1 instance and replace. In vim this is easy: highlight, shift-;, s/foo/foo2/g. Quick and takes seconds. I actually asked for this feature because I was just in such a situation. And clicking 'replace' like mad to make it go fast is not the answer because you will end up replacing that one instance that you did not want to replace. Replacing this way requires reading, which requires a lot more time.

One way you could implement this is by checking highlighted text length: if it is longer than 100 chars for example, do not pre-fill find field, but enable replace all within highlighted text only. If less than 100, pre-fill and do it the way it's done now.
> **Mystilleef said:**
> 
Incremental searching means text is searched beginning from the cursor
position as opposed to the beginning of the document.Thank you. Definitely not what I had in mind when I read "incremental".

---

### Post by AgenT on 2006-11-13
> **Mystilleef said:**
> It will be shown (so as not to confuse users into thinking their keyboard or Scribes is broken) but it will be removed when the trigger is expanded.Sounds great!

---

### Post by Mystilleef on 2006-11-13
> **AgenT said:**
> 
One way you could implement this is by checking highlighted text length: if it is longer than 100 chars for example, do not pre-fill find field, but enable replace all within highlighted text only. If less than 100, pre-fill and do it the way it's done now.


I like the idea. I'll implement it.

Cheers

---

### Post by crypto178 on 2006-11-13
Scribes is awesome, thanks for your work :)
The help, especially, is well written and useful.

There's only some small things I haven't figured out yet :
How to customize how the date is formatted when using ${date} in a template (it seems to be yyyy:mm:dd by default)?

Another thing I couldn't get to work is the spell checking. Does it work with other languages than English?

Last, the accents seem to be displayed wrong (only in the menus, not in what I actually type), see screenshot : [http://img479.imageshack.us/img479/566/capturepl5.png](http://img479.imageshack.us/img479/566/capturepl5.png)

---

### Post by Mystilleef on 2006-11-13
> **crypto178 said:**
> Scribes is awesome, thanks for your work :)
The help, especially, is well written and useful.

There's only some small things I haven't figured out yet :
How to customize how the date is formatted when using ${date} in a template (it seems to be yyyy:mm:dd by default)?

Another thing I couldn't get to work is the spell checking. Does it work with other languages than English?

Last, the accents seem to be displayed wrong (only in the menus, not in what I actually type), see screenshot : [http://img479.imageshack.us/img479/566/capturepl5.png](http://img479.imageshack.us/img479/566/capturepl5.png)

The date format cannot yet be configured. Users have reported that
spell checking works in other languages. The accent issue is a bug that
will be fixed in the next release.

Cheers

---

### Post by AgenT on 2006-11-13
How-To Change Default Text Editor (to Scribes):

Check if this file exists:
```
~/.local/share/applications/defaults.list
```If so, open it, if not:
```
touch ~/.local/share/applications/defaults.list
```Open ~/.local/share/applications/defaults.list and look for this entry:
```
[Default Applications]
```If it does not exist, add it on top. Next, add the following below "[Default Applications]":
```
text/plain=scribes.desktop
```Your completed entry should look like this:
```
[Default Applications]
text/plain=scribes.desktop
```Now run:
```
pkill nautilus
```It is possible to set any mime type and any program that has a *.desktop entry.

Why is this better than just right-click on file -> Open With? Because with the above, ALL plain text files will be opened by Scribes, not just ones that have a particular extension.

For more details on what programs are used for what mime types, see file:
/usr/share/applications/defaults.list
One easy way to replace a program like gedit would be to get all entries containing gedit, replace them with scribes, and add that list to ~/.local/share/applications/defaults.list.

This quit one-liner does exactly that, except that it posts the results in terminal and you will just have to copy/paste it into your file:
```
 grep gedit /usr/share/applications/defaults.list | sed s/gedit/scribes/g
```

---

### Post by NoWhereMan on 2006-11-14
> **Mystilleef said:**
> I prefer (`) because ESC is usually used to exit operations in most applications including Scribes. In fact, I believe in earlier versions of Scribes ESC was also used to exit template mode. 

on non-English layouts the backtick char may not be easily reachable, or at least whith not as much ease as ESC. On Italian layout for instance it is Alt-gr+'

bye ;)

---

### Post by AgenT on 2006-11-14
> **NoWhereMan said:**
> on non-English layouts the backtick char may not be easily reachable, or at least whith not as much ease as ESC. On Italian layout for instance it is Alt-gr+'
This is a very good point. But I would also try to find a key or combination of keys that are easier to use than ESC. I find ESC key not usable because it is the farthest key from home-row. This is especially true on a lot of laptops that have to squeeze in less used keys on top somewhere. And is very uncomfortable for touch-typists. For example, the X (smallest IBM laptop) series of IBM Thinkpads have an amazingly compact keyboard that yet feels very roomy with keys that are a good size. Because of this, ESC key is NOT within reach because IBM knew that it's almost never used. The same with the volume and other system buttons - rarely used, so the were put on top and are not within reach. I actually find this annoying with Scribes - it does require the use of ESC a lot. One very quick and nice feature that I would like to see in Scribes is the one in vim: ctrl-c being equal to ESC in function. That is, whenever ESC key needs to be pressed, ctrl-c can be used instead.

---

### Post by NoWhereMan on 2006-11-14
> **AgenT said:**
> I would like to see in Scribes is the one in vim: ctrl-c being equal to ESC in function. That is, whenever ESC key needs to be pressed, ctrl-c can be used instead.

That may be an idea; of course not ctrl-c (=> copy)

---

### Post by AgenT on 2006-11-14
> **NoWhereMan said:**
> That may be an idea; of course not ctrl-c (=> copy)Any ideas what key?

Currently, these keys are bound to ctrl in Scribes (this list does not include GNOME defaults, like ctrl-c):
```
b
d
g
i
k
l
o
p
s
t
w
```I propose ctrl-h. h for "huh?" ;) And it's nice because 1) it's a letter 2) it is away from ctrl making touch typing easy 3) h seems to be used in many applications for special functions, like ctrl-h for history in web browsers. ctrl-e sounds good too. e for "escape". e also has advantage #1 and #2.

---

### Post by nephish on 2006-11-21
i dig this a editor a lot, its already taking over for my python work, but would like better highlighting for rhtml files. (if anyone has a .lang file for gtksourceview, i would love to have it )

good work

---

### Post by Mystilleef on 2006-11-21
Disclaimer: For some weird reason, I'm not receiving email updates on
new comments added to this forum.

The problem with assigning new shortcut keys is that you can't please
everyone. But we don't need another shortcut key, we just need a saner
escape character. So far "`" is looking the most enticing to me.

---

### Post by DirtDawg on 2006-12-13
I'm sorry if I'm rehashing but is it safe to assume Scribes is not available for Dapper?

When I try to compile, I get this error:
```
Error: Version 0.70 or better of dbus-python needed.

```
But the most recent version os [dbus-python]("http://packages.ubuntu.com/dapper/python/python2.4-dbus") for Dapper is .60.

I assume this means Scribes is a no-go for Dapper?

---

### Post by nephish on 2006-12-13
i got it running in dapper, i think that its in multiverse.

---

### Post by DirtDawg on 2006-12-13
> **nephish said:**
> i got it running in dapper, i think that its in multiverse.

I'm sorry, do you mean Scribes is in Multiverse, or dbus-python?

EDIT: So is Scribes available in Dapper or not? If so, could someone tell me how? Thanks again.

---

### Post by Zdravko on 2006-12-16
Wow, I think Scribes is a great application! First of all it looks extremely lightweight and simple. Second, it just works! I wonder if it appears as default text editor in Feisty Fawn (the next Ubuntu release)... 

May I know when you plan to release the next version of Scribes? Is there a TODO-list or something of the sort?

---

### Post by AgenT on 2006-12-16
> **DirtDawg said:**
> I'm sorry, do you mean Scribes is in Multiverse, or dbus-python?

EDIT: So is Scribes available in Dapper or not? If so, could someone tell me how? Thanks again.Taken from the official Scribes website:
> Scribes is built upon Python and the Python libraries for GNOME. You need the following software and their dependencies installed on your computer to use Scribes.[LIST]
[*]Yelp 2.12
[*]D-Bus 0.7 (Python bindings)
[*]PyGTK 2.10
[*]GNOME Python Desktop 2.12
[*]GNOME Python Extras 2.12[/LIST]That means you need to install D-Bus 0.7. Check your other dependencies and install newer versions of them (but be prepared for breakage when upgrading to Edgy later). Of course, you can just upgrade to Edgy instead. If you try to have the best of both worlds you will just break your system.

---

### Post by ponsfrilus on 2006-12-19
:KS  Hey, do someone have a link to a scibres PHP template xml file? :-k   Thanks! :)

---

### Post by OffHand on 2006-12-19
You got an eta for a fix for the sudo su issue?

---

### Post by DirtDawg on 2006-12-20
> **AgenT said:**
> Taken from the official Scribes website:
That means you need to install D-Bus 0.7. Check your other dependencies and install newer versions of them (but be prepared for breakage when upgrading to Edgy later). Of course, you can just upgrade to Edgy instead. If you try to have the best of both worlds you will just break your system.

Okay thank you. Edgy doesn't actually work correctly on the machine I was considering and I don't feel comfortable upgrading that dbus package for fear of unintended breakage down the road, so it looks like a no-go for me.

Well Scribes looks cool anyway. Keep it up.

---

### Post by OffHand on 2006-12-20
I wasn't able to post a bug on your sourceforge website so I will do it here. 

Scribes will not offer to save the file if you click on the close button. High priority bug because no one likes to lose his work by accidentally closing the window.

---

### Post by Wolki on 2006-12-20
> **OffHand said:**
> Scribes will not offer to save the file if you click on the close button. High priority bug because no one likes to lose his work by accidentally closing the window.


Scribes aggressively autosaves open documents, so the chance of losing anything is extremely small. In particular, it will always save automatically when closing the window.

---

### Post by BrokeBody on 2006-12-20
> **chaosgeisterchen said:**
> Seems to be VERY cool. But only THAT great for Python? Or does it support all those features for other languages too..

It has support for over 30 languages.

---

### Post by OffHand on 2006-12-20
> **Wolki said:**
> Scribes aggressively autosaves open documents, so the chance of losing anything is extremely small. In particular, it will always save automatically when closing the window.

Aye it does, I just noticed it. Thanks for replying though  :)
I still think a save dialog should be implemented.

---

### Post by Wolki on 2006-12-20
> **OffHand said:**
> 
I still think a save dialog should be implemented.

I cancertainlyunderstand that, having saving explicit makes some use cases explicit easier (eg., if you decide you don't want some changes after all). But Mystilleef feels that autosaving is a core feature of scribes (see for example [1]), and once you get used to it it's ok andoften convenient.

[1] [http://sourceforge.net/forum/forum.php?thread_id=1628869&forum_id=481790](http://sourceforge.net/forum/forum.php?thread_id=1628869&forum_id=481790)

---

### Post by AgenT on 2006-12-20
> **OffHand said:**
> I wasn't able to post a bug on your sourceforge website so I will do it here. 

Scribes will not offer to save the file if you click on the close button. High priority bug because no one likes to lose his work by accidentally closing the window.
You are obsessing with buttons on your toolbar. You can always hit CTRL+S if you need to. Scribes will autosave your work if you quit by pressing the "X" button. It will even save if you force quit it via your WM which is what I do as hitting buttons is a waste of time.

You are just used to having trivial things that require manual intervention. Scribes tries to change that. It's like Windows users asking "how do I defragment GNU/Linux". :rolleyes:

---

### Post by Zdravko on 2006-12-22
I think that Scribes is a much better text editor than gEdit and maybe than Vim!

---

### Post by OffHand on 2006-12-22
> **AgenT said:**
> You are obsessing with buttons on your toolbar. You can always hit CTRL+S if you need to. Scribes will autosave your work if you quit by pressing the "X" button. It will even save if you force quit it via your WM which is what I do as hitting buttons is a waste of time.

You are just used to having trivial things that require manual intervention. Scribes tries to change that. It's like Windows users asking "how do I defragment GNU/Linux". :rolleyes:

I'm not dumb and I will not let someone, or an application for that matter, dictate me how I should use an application. (I know in a way every app tells me how I should use it) 
Autosave isn't enough for me. I like to see the usual options when I press the close button. Like any other application. It is probably even mentioned in the Gnome GUI Guidelines. 
Scribes can try to change that but it will fail... at least on me. 

Nice application but not as ready as Gedit is for every day use.

---

### Post by Zdravko on 2006-12-22
I think you should just accommodate and get used to it - Scribes will dictate the rules for GNOME applications!

---

### Post by NoWhereMan on 2006-12-30
I don't know if you'll like it, btw I had this idea: do not bracket-match if cursor is before a word, i mean (pipe | is the cursor):

> my long text with lots of stuff **|**and so on

let me now add a left bracket
> my long text with lots of stuff **(|**and so on

it will be completed this way
> my long text with lots of stuff **(|)**and so on

now I am right in the middle, but as I'm accustomed to beleive that an added char comes *after* the cursor, I hit backspace (it's abitude... I typed a wrong char, I delete it with backspace). What happens is that scribses deletes the opening bracket, and the closing one, too
> my long text with lots of stuff **|**and so on

I should have used del key, instad, I know... btw I find this sometimes annoyng; I know, it's a matter of getting accustomed to it, but what if scribes were so clever that in this particular case, the bracket are not matched?

you may say, well we could put the closing bracket after the word the cursor is at... yeah, but what if want the bracket to close at the end of line?

no-bracket-matching is this case is cheaper, and maybe less annoying ?

---

another one regarding bracket matching, and curly braces.

> if (something) {**|**}
hit enter:

> if (something) {[b]
|[/b]}

what about auto indenting, here?

```
if (something) {[b]
        |[/b]
}
```

bye, and thanx :)

---

### Post by joflow on 2007-01-04
I'm trying to create a new file with scribes from the commandline is this possible?  I get the following error from running the following:

sudo scribes /path/to/file.py

"Traceback (most recent call last):
  File "/usr/bin/scribes", line 39, in ?
    main(argv[1:])
  File "/usr/lib/python2.4/site-packages/SCRIBES/dbusmain.py", line 53, in main
    from info import dbus_iface
  File "/usr/lib/python2.4/site-packages/SCRIBES/info.py", line 32, in ?
    session_bus = SessionBus()
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 266, in __new__
    return Bus.__new__(cls, Bus.TYPE_SESSION, use_default_mainloop, private)
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 99, in __new__
    bus._connection = dbus_bindings.bus_get(bus_type, private)
  File "dbus_bindings.pyx", line 1692, in dbus_bindings.bus_get
dbus_bindings.DBusException: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

---

### Post by AgenT on 2007-01-04
> **joflow said:**
> I'm trying to create a new file with scribes from the commandline is this possible?  I get the following error from running the following:

sudo scribes /path/to/file.pyPlease use code tags when posting code, and quote tags when quoting.

The error you received is a known bug in Scribes. Do not use sudo with Scribes.

---

### Post by Zdravko on 2007-01-05
May I know when can we expect a new version of Scribes? I am really eager to see it...

---

### Post by ComplexNumber on 2007-01-05
scribes doesn't do anything for me. i had a brief trial of it recently, but it offers me nothing. i prefer to stick with leafpad(for a fast and simple text viewer/editor), gedit(for code programming), and open office writer (for wordprocessing).

---

### Post by roderikk on 2007-01-05
> **ComplexNumber said:**
> scribes doesn't do anything for me. i had a brief trial of it recently, but it offers me nothing. i prefer to stick with leafpad(for a fast and simple text viewer/editor), gedit(for code programming), and open office writer (for wordprocessing).
It does require a bit of a change of mind but I do really fancy it. I don't know in which language you code but be sure to download the extra templates. These I found when reading the faq, they add support for things like java, latex and c++.

On another note, might it be feasible to make scribes embeddable/extendable. When I am writing my octave/matlab or java code I would love to be able to just run it in a terminal underneath the screen with a single shortcut.

Good luck and thanks!

---

### Post by ComplexNumber on 2007-01-05
> **roderikk said:**
> It does require a bit of a change of mind but I do really fancy it. I don't know in which language you code but be sure to download the extra templates. These I found when reading the faq, they add support for things like java, latex and c++.

On another note, might it be feasible to make scribes embeddable/extendable. When I am writing my octave/matlab or java code I would love to be able to just run it in a terminal underneath the screen with a single shortcut.

Good luck and thanks!
yeah, i kinda gathered that it seemed to revolve around a different way of thinking to what 99.9999% of editors require. but i really don't think that the learning curve is anywhere near worth what i would get in return, so i promptly uninstalled it.
9 out of 10 for originality of thought, though.
maybe it would suit someone who is less 'fixed' than me.

scribes comes across as if it is based on the same reasoning that emacs is - ie learn 5 billion shortcut commands, and your workflow when creating letters will increase (ASSUMING THAT ONE HAS TO WRITE AT LEAST 30 LETTERS EVERY DAY). i have no doubt that emacs(or scribes) may well make it easier and quicker to write letters (assume that i have to write lots of letters), but considering that i rarely have to write any letters, something that is readily accessible, fast, simple, and intuitive is much more suited to my needs.

---

### Post by NoWhereMan on 2007-01-05
letters? O.o who would need bracket matching, line numbering, word completion, syntax highlighting to write letters? O.o

---

### Post by ComplexNumber on 2007-01-05
> **NoWhereMan said:**
> letters? O.o who would need bracket matching, line numbering, word completion, syntax highlighting to write letters? O.o
thats for writing code. anyway, who said that one would need bracket matching etc to write letters?

---

### Post by NoWhereMan on 2007-01-05
from what you said it looked like you meant that scribes is meant to increase your workflow when writing letters o.o

---

### Post by ComplexNumber on 2007-01-05
> **NoWhereMan said:**
> from what you said it looked like you meant that scribes is meant to increase your workflow when writing letters o.o
no, i just used that as an example. i meant for all text processing type work (eg wordprocessing, coding,  text editing, etc).

---

### Post by NoWhereMan on 2007-01-05
oh, ok :D

---

### Post by Zdravko on 2007-01-06
Where did you say these templates are? I want to use them! :)

---

### Post by AgenT on 2007-01-06
> **Zdravko said:**
> Where did you say these templates are? I want to use them! :)Before asking a question about a topic relating to a thread it is usually a good idea to read the original post (post #1 or the thread starter, whatever you prefer to call it).

---

### Post by Zdravko on 2007-01-06
There is only template for C, not for C++. Why? It doesn't work for cpp or hpp files. But the template definitions should work nice in C++.

---

### Post by AgenT on 2007-01-06
> **Zdravko said:**
> There is only template for C, not for C++. Why?Why? Because no one has made C++ templates. If you make some (very easy), submit them.

---

### Post by Zdravko on 2007-01-08
Huston, we have a problem! 
I tried with success to write some template definitions for C++. It worked. However the C-templates were totally messed. I previously exported these, just to avoid confusions. Now the export function may have done something wrong... After clicking on the C-templates tab, a strange mixture of the C++ templates appears and some C-templates ](*,)

Besides, where should I post the C++ template, once it is finished? :KS

---

### Post by AgenT on 2007-01-08
> **Zdravko said:**
> Huston, we have a problem! 
I tried with success to write some template definitions for C++. It worked. However the C-templates were totally messed. I previously exported these, just to avoid confusions. Now the export function may have done something wrong... After clicking on the C-templates tab, a strange mixture of the C++ templates appears and some C-templates ](*,)

Besides, where should I post the C++ template, once it is finished? :KSMaybe you exported them to the same file? Maybe you edited them after exporting? The image you provide shows some very odd problems (@46@46) which make no sense. Not sure what the problem could be.

You can attach your working templates here. If you want, I can submit them to Scribes' author or you can do that yourself via the sourceforge website.

---

### Post by hanzomon4 on 2007-01-08
I can't run scribes as root, when I try I get this output ```
gksudo scribes 
  File "/usr/bin/scribes", line 39, in ?
    main(argv[1:])
  File "/usr/lib/python2.4/site-packages/SCRIBES/dbusmain.py", line 53, in main
    from info import dbus_iface
  File "/usr/lib/python2.4/site-packages/SCRIBES/info.py", line 32, in ?
    session_bus = SessionBus()
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 266, in __new__
    return Bus.__new__(cls, Bus.TYPE_SESSION, use_default_mainloop, private)
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 99, in __new__
    bus._connection = dbus_bindings.bus_get(bus_type, private)
  File "dbus_bindings.pyx", line 1692, in dbus_bindings.bus_get
dbus_bindings.DBusException: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken
```

Any ideas?

---

### Post by AgenT on 2007-01-08
> **hanzomon4 said:**
> Any ideas?Yes, just read a few posts above yours for the answer to your question. Your question has been asked and answered a few times already in this thread.

---

### Post by hanzomon4 on 2007-01-09
Found it, it's a d-bus issue and there's no fix at the moment... This being somewhat major, perhaps adding it to the first post would be a good idea

---

### Post by Zdravko on 2007-01-09
> **AgenT said:**
> Maybe you exported them to the same file? Maybe you edited them after exporting? The image you provide shows some very odd problems (@46@46) which make no sense. Not sure what the problem could be.

You can attach your working templates here. If you want, I can submit them to Scribes' author or you can do that yourself via the sourceforge website.

No, I think something is wrong with the create-template part of the software. Is there a way to flush all the templates Scribes uses? I already removed everything. But adding a C++ template again adds some mess in the C templates :(

---

### Post by quinnman on 2007-01-10
Does Scribes support rectangular text selecting and copying or is this feature planned? Does any other simple text editor in GNOME have this feature? Thank you.

---

### Post by Zdravko on 2007-01-10
[quinnman]("http://ubuntuforums.org/member.php?u=43117"), no - only OpenOffice can handle such operations.

---

### Post by AgenT on 2007-01-10
> **quinnman said:**
> Does Scribes support rectangular text selecting and copying or is this feature planned? Does any other simple text editor in GNOME have this feature? Thank you.
Text editors do exactly as their title suggest: edit text files. No text file has rectangular text selection or boxes. A text file has text. ;)

For your needs, try AbiWord, a GNOME-program similar to OpenOffice Writer except slimmer and much faster loading.

---

### Post by quinnman on 2007-01-10
> **AgenT said:**
> Text editors do exactly as their title suggest: edit text files. No text file has rectangular text selection or boxes. A text file has text. ;)

For your needs, try AbiWord, a GNOME-program similar to OpenOffice Writer except slimmer and much faster loading.

I should have expressed myself better before. It needn't to be a simple "text editor", it might  be something like kate in KDE, which has this feature. Do you know about any such editor in GNOME?

---

### Post by NoWhereMan on 2007-01-10
SciTE; I used to like it but it's quite slow with GTK and it is inconsistent with handling newlines. there are always gvim or cream... :/

---

### Post by Zdravko on 2007-01-11
[quinnman]("http://ubuntuforums.org/member.php?u=43117"), here we discuss Scribes, not fancy programs. Ok? If you are searching an application for a specific need - don't be shy to start a new thread about it. 
The developer of Scribes seems to be very busy right now - he never said anything about the templates' bug... :(

---

### Post by AgenT on 2007-01-11
> **Zdravko said:**
> []("http://ubuntuforums.org/member.php?u=43117")The developer of Scribes seems to be very busy right now - he never said anything about the templates' bug... :(It is doubtful that the developer reads this thread because he had problems receiving email notifications. If you found a bug, file a bug report on his bug report page or ask in the forums. Both of these are linked from Scribes' website and are hosted on sourceforge.

---

### Post by Zdravko on 2007-01-13
I just reported the bug here:

[http://sourceforge.net/tracker/index.php?func=detail&aid=1634723&group_id=143967&atid=757280](http://sourceforge.net/tracker/index.php?func=detail&aid=1634723&group_id=143967&atid=757280)


Hope this works! Scribes is the coolest program I've ever seen so far under Ubuntu!

---

### Post by Zdravko on 2007-01-13
And why is this thread in the Cafe' forum? It just doesn't make sense. For example, dee.de's XORG GUI Config application is placed in the Programming forum. I believe that this thread should be moved there, too.

---

### Post by AgenT on 2007-01-13
> **Zdravko said:**
> I just reported the bug here:

[http://sourceforge.net/tracker/index.php?func=detail&aid=1634723&group_id=143967&atid=757280](http://sourceforge.net/tracker/index.php?func=detail&aid=1634723&group_id=143967&atid=757280)


Hope this works! Scribes is the coolest program I've ever seen so far under Ubuntu!
Scribes is a GNU/Linux program, not an Ubuntu one. That it works under Ubuntu is because Ubuntu is a GNU/Linux distribution (based on Debian).

---

### Post by Zdravko on 2007-01-14
[AgenT]("http://ubuntuforums.org/member.php?u=10526"), I can say the same for [http://ubuntuforums.org/showthread.php?t=156243](http://ubuntuforums.org/showthread.php?t=156243) :)


I wonder why this thread is still here - programmers may need it. Not coffee drinkers!

---

### Post by AgenT on 2007-01-14
> **Zdravko said:**
> []("http://ubuntuforums.org/member.php?u=10526")I wonder why this thread is still here - programmers may need it. Not coffee drinkers!I am not sure why you are replying to my post with this. My post had nothing to do with moving this thread.

This thread should not go into Programming because that is reserved for programming questions and answers. The author of this thread does not need help with programming.

The Xorg-Edit thread should probably be in How-To Tips & Tricks. The reason for this is rather complicated but let us say I have experience in this. Notice my project threads are both in HowTo - they were moved there from Cafe. I had conversations about this with the forum Moderators a few months back and we all agreed that How-To was the best place for such threads.

Threads such as these two will probably NOT be moved unless the original author asks for them to be moved.

---

### Post by NoWhereMan on 2007-02-07
new dev package :)

tarball:
[http://sourceforge.net/forum/forum.php?thread_id=1660193&forum_id=481790](http://sourceforge.net/forum/forum.php?thread_id=1660193&forum_id=481790)

deb here:
[http://sourceforge.net/mailarchive/forum.php?thread_id=31557973&forum_id=50620](http://sourceforge.net/mailarchive/forum.php?thread_id=31557973&forum_id=50620)

w00t ! ^^

---

### Post by Choad on 2007-02-07
> **Mystilleef said:**
> Hello,

Apologies if I'm posting in the wrong forum. I need your help testing Scribes before I make a public release. I appreciate any feedback you have.

Flash Demo: [http://scribes.sf.net/demo.htm](http://scribes.sf.net/demo.htm)

website: [http://scribes.sf.net/](http://scribes.sf.net/)

download: [http://scribes.sf.net/download.html](http://scribes.sf.net/download.html)

templates: [http://scribes.sf.net/templates.tar.bz2](http://scribes.sf.net/templates.tar.bz2) 

I'll upload a deb file immediately the maintainer provides one.

Thanks
that is pure awesome!

time to download this badboy

---

### Post by nephish on 2007-02-07
i just did, it is just a fun fun editor to use.
great work on this.

---

### Post by Choad on 2007-02-07
this is the best thing to happen to text documents since text documents were invented. it is that good!

would be good if backspace deleted a whole tab tho. its a drag having to tap tap tap tap tap to get rid of an accidental tab (and due to the nature of this program, there are lots of accidental tabs)

---

### Post by Choad on 2007-02-07
> **Choad said:**
> this is the best thing to happen to text documents since text documents were invented. it is that good!

would be good if backspace deleted a whole tab tho. its a drag having to tap tap tap tap tap to get rid of an accidental tab (and due to the nature of this program, there are lots of accidental tabs)
oh, i take that back. "spaces to tabs" and its all gravy.

:D i am so happy now i have found this

---

### Post by SunnyRabbiera on 2007-02-07
I am giving this a shot as i have been having issues with gedit.

---

### Post by phoenyx on 2007-03-07
Sometimes when I try to edit .adp files (they're an OpenACS thing) with Scribes I get the following error:

The MIME type of the file you are trying to open is not for a text file.
MIME type: application/x-extension-adp

but they'll open in gedit, vim, etc.

Also, I xmodmapped (is that a verb?) my caps lock to escape and vice versa and it has made using Scribes that much nicer :)

---

### Post by Mystilleef on 2007-03-07
> **phoenyx said:**
> Sometimes when I try to edit .adp files (they're an OpenACS thing) with Scribes I get the following error:

The MIME type of the file you are trying to open is not for a text file.
MIME type: application/x-extension-adp

but they'll open in gedit, vim, etc.

Also, I xmodmapped (is that a verb?) my caps lock to escape and vice versa and it has made using Scribes that much nicer :)

Fixed in the latest development release.

[http://scribes.sf.net/devel/scribes-0.3.1-devel-build-9.tar.bz2](http://scribes.sf.net/devel/scribes-0.3.1-devel-build-9.tar.bz2)

Cheers

---

### Post by Mystilleef on 2007-03-07
I'm sorry if I've not responded to queries on this thread. The Forum's software has not been emailing me when comments are made to this thread. I'll try to respond all queries as soon as possible.

---

### Post by Mystilleef on 2007-03-07
> **ponsfrilus said:**
> :KS  Hey, do someone have a link to a scibres PHP template xml file? :-k   Thanks! :)

Yes, [http://scribes.sf.net/templates.tar.bz2](http://scribes.sf.net/templates.tar.bz2)

---

### Post by Mystilleef on 2007-03-07
> **OffHand said:**
> You got an eta for a fix for the sudo su issue?

Unfortunately, there's no fix that I know off, just a workaround.

```

DBUS_SESSION_BUS_ADDRESS= sudo scribes

```

---

### Post by Mystilleef on 2007-03-07
> **NoWhereMan said:**
> I don't know if you'll like it, btw I had this idea: do not bracket-match if cursor is before a word, i mean (pipe | is the cursor):



let me now add a left bracket


it will be completed this way


now I am right in the middle, but as I'm accustomed to beleive that an added char comes *after* the cursor, I hit backspace (it's abitude... I typed a wrong char, I delete it with backspace). What happens is that scribses deletes the opening bracket, and the closing one, too


I should have used del key, instad, I know... btw I find this sometimes annoyng; I know, it's a matter of getting accustomed to it, but what if scribes were so clever that in this particular case, the bracket are not matched?

you may say, well we could put the closing bracket after the word the cursor is at... yeah, but what if want the bracket to close at the end of line?

no-bracket-matching is this case is cheaper, and maybe less annoying ?


I'm not sure I understand the issue well. But you can select the line and press the open bracket and the selection will automatically be enclosed in brackets. That way you don't need to deal with the "annoyances" of bracket completion. Again, I'm not sure if I'm addressing your issue. If I'm not, do not hesitate to ask again.

> **NoWhereMan said:**
> 
what about auto indenting, here?

```
if (something) {[b]
        |[/b]
}
```

bye, and thanx :)

This is language specific and can't be implemented in a generic manner. Also, different projects usually have different coding style with regards to parenthesis placement. It's difficult to cater for all those coding styles. A plugin can now be written for them however.

---

### Post by Mystilleef on 2007-03-07
> **Zdravko said:**
> May I know when can we expect a new version of Scribes? I am really eager to see it...

The next version of Scribes, version 0.3.1, is already feature complete. It just need more testing and internationalization before it is released into the wild. You test the latest development release and provide feedback.

[http://scribes.sf.net/devel/scribes-0.3.1-devel-build-9.tar.bz2](http://scribes.sf.net/devel/scribes-0.3.1-devel-build-9.tar.bz2)

I plan to make a release by the end of this month, but I'm not making any promises.

Cheers

---

### Post by Mystilleef on 2007-03-07
> **quinnman said:**
> Does Scribes support rectangular text selecting and copying or is this feature planned? Does any other simple text editor in GNOME have this feature? Thank you.

No GTK+ text editor has this because GTK+ does not support it. When GTK+ supports it text editors will follow suit.

---

### Post by Mystilleef on 2007-03-07
You are welcome to test the latest development release of Scribes and provide feedback.

Download:
[http://scribes.sf.net/devel/scribes-0.3.1-devel-build-9.tar.bz2](http://scribes.sf.net/devel/scribes-0.3.1-devel-build-9.tar.bz2)

Provide Feedback:
[http://scribes.sourceforge.net/community.html](http://scribes.sourceforge.net/community.html)

Cheers

---

### Post by Mystilleef on 2007-03-17
Hello,

Scribes 0.3.1 has been released.

Release Note:  [http://scribes.sourceforge.net/release-note-0-3-1.html](http://scribes.sourceforge.net/release-note-0-3-1.html)

Flash Demo: [http://scribes.sf.net/demo.htm](http://scribes.sf.net/demo.htm)

website: [http://scribes.sf.net/](http://scribes.sf.net/)

download: [http://scribes.sf.net/download.html](http://scribes.sf.net/download.html)

templates: [http://scribes.sf.net/templates.tar.bz2](http://scribes.sf.net/templates.tar.bz2) 

Thanks

---

### Post by hanzomon4 on 2007-03-17
> **AgenT said:**
> Please use code tags when posting code, and quote tags when quoting.

The error you received is a known bug in Scribes. Do not use sudo with Scribes.

I'm sorry but I asked about this problem a while back and I suggested that someone add this to the first post.

@Mystilleef can you add to your first post that sudo doesn't work "yet", and good job I like scribes.....

---

### Post by Mystilleef on 2007-03-17
> **hanzomon4 said:**
> I'm sorry but I asked about this problem a while back and I suggested that someone add this to the first post.

@Mystilleef can you add to your first post that sudo doesn't work "yet", and good job I like scribes.....

The sudo issue is a problem with D-Bus and it doesn't look like they have any intention of fixing it. They site security reasons. However to use sudo with scribes you have to do the following:

```

DBUS_SESSION_BUS_ADDRESS = sudo scribes
```

---

### Post by NoWhereMan on 2007-03-18
> **Mystilleef said:**
> Hello,

Scribes 0.3.1 has been released.

w00t ! :)

---

### Post by nephish on 2007-04-07
hey, you can get rhtml support for scribes with language files ( as previously noted ) but i made a simple one, you can get it at [bitsbam.com]("http://www.bitsbam.com")
three pretty simple steps to make it work.

---

### Post by Spif on 2007-04-09
Anyone kind enough to make a .deb? :)

---

### Post by Zdravko on 2007-04-19
Yeah, it will be a nice idea for FF :)

---

### Post by edwinw on 2007-04-28
Hi,

I'm just having a problem compiling scribes on Feisty, no errors come up on "./configure --prefix=/usr", but make gives me the following error message:

[FONT="Courier New"]Making all in po
make[1]: Entering directory `/home/edwin/Desktop/scribes-0.3.2.1/po'
file=`echo de | sed 's,.*/,,'`.gmo \
	  && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[1]: *** [de.gmo] Error 127
make[1]: Leaving directory `/home/edwin/Desktop/scribes-0.3.2.1/po'
make: *** [all-recursive] Error 1[/FONT]

I'm just guessing I have set some extra stuff in my Makefile, but have no idea what.  Yeah, I'm way too spoiled with pre-packaged software and just running apt-get.  Anyway, can someone tell me how to make the compile work?  Thanks!

---

### Post by Mystilleef on 2007-04-28
> **edwinw said:**
> Hi,

I'm just having a problem compiling scribes on Feisty, no errors come up on "./configure --prefix=/usr", but make gives me the following error message:

[FONT="Courier New"]Making all in po
make[1]: Entering directory `/home/edwin/Desktop/scribes-0.3.2.1/po'
file=`echo de | sed 's,.*/,,'`.gmo \
	  && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[1]: *** [de.gmo] Error 127
make[1]: Leaving directory `/home/edwin/Desktop/scribes-0.3.2.1/po'
make: *** [all-recursive] Error 1[/FONT]

I'm just guessing I have set some extra stuff in my Makefile, but have no idea what.  Yeah, I'm way too spoiled with pre-packaged software and just running apt-get.  Anyway, can someone tell me how to make the compile work?  Thanks!

I believe you need to install the gettext package.

---

### Post by edwinw on 2007-04-28
Thanks for the quick reply Mystilleef, that was it!  Looking forward to trying out scribes now!

---

### Post by 50words on 2007-04-29
Is there any way to get a .deb for this? I found one for 0.1, but that doesn't do much good. The Readme that comes with the tarball doesn't help much for a newbie like me. I did my best to follow the commands, but didn't get anywhere.

I unpacked the tarball on my desktop and did as it said:

```

root@usr:~# ./configure
bash: ./configure: No such file or directory

```

So there must be a couple of steps or instructions I am missing.

---

### Post by Mystilleef on 2007-04-30
> **50words said:**
> Is there any way to get a .deb for this? I found one for 0.1, but that doesn't do much good. The Readme that comes with the tarball doesn't help much for a newbie like me. I did my best to follow the commands, but didn't get anywhere.

I unpacked the tarball on my desktop and did as it said:

```

root@usr:~# ./configure
bash: ./configure: No such file or directory

```So there must be a couple of steps or instructions I am missing.

You need to "cd" into the unpacked folder

```

cd unpacked_scribes_folder
./configure
make
sudo make install

```

---

### Post by 50words on 2007-04-30
I guess that should be obvious, but it wouldn't be too hard to add to the install guide.

Now I get this:

```

root@me:/home/me/Desktop/scribes-0.3.2.2# make
Making all in po
make[1]: Entering directory `/home/me/Desktop/scribes-0.3.2.2/po'
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[1]: *** [de.gmo] Error 127
make[1]: Leaving directory `/home/me/Desktop/scribes-0.3.2.2/po'
make: *** [all-recursive] Error 1

```

---

### Post by Mystilleef on 2007-04-30
> **50words said:**
> I guess that should be obvious, but it wouldn't be too hard to add to the install guide.

Now I get this:

```

root@me:/home/me/Desktop/scribes-0.3.2.2# make
Making all in po
make[1]: Entering directory `/home/me/Desktop/scribes-0.3.2.2/po'
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[1]: *** [de.gmo] Error 127
make[1]: Leaving directory `/home/me/Desktop/scribes-0.3.2.2/po'
make: *** [all-recursive] Error 1

```

Install the gettext package for ubuntu.

Then try again.

---

### Post by 50words on 2007-04-30
Hot stuff. Thanks!

Edit: Apps like Scribes are why I will not be purchasing Vista. Although I still work primarily in Windows XP, more and more I am finding that I wish I was working in Ubuntu. Maybe it's time to figure out VMWare.

---

### Post by phoenyx on 2007-05-01
For those asking about a .deb for ubuntu I came across this:
[http://revu.tauware.de/details.py?upid=4822](http://revu.tauware.de/details.py?upid=4822)

I just installed from a .deb I found here:
[http://www.getdeb.net/app.php?name=Scribes](http://www.getdeb.net/app.php?name=Scribes)

and it works great.

---

### Post by engla on 2007-05-02
> **phoenyx said:**
> For those asking about a .deb for ubuntu I came across this:
[http://revu.tauware.de/details.py?upid=4822](http://revu.tauware.de/details.py?upid=4822)

I just installed from a .deb I found here:
[http://www.getdeb.net/app.php?name=Scribes](http://www.getdeb.net/app.php?name=Scribes)

and it works great.
yeah it's great with getdeb. I don't get those people though -- scribes is a python app so you don't have to provide 32bit/64bit etc packages. You can make one package for all  architectures (including mine, powerpc). I took the getdeb package and updated it to scribes 0.3.2.2 and built a cross-arch package... (The key is simple, specify Architecture: all (not any) in the debian/control file).

---

### Post by Endolith on 2007-05-03
> **Mystilleef said:**
> Yes, it may well be. But most importantly it is a question of consistency. When a user sees *, the user should automatically know the document has be modified. In the next release I'm going to work of making the state of the document more explicit in the statusbar.

I often make changes to a file that I don't intend to save, and use the undo functionality to get back to the latest stable state by watching for the * to disappear.  Like editing to get it to an intermediate stage which I then copy into another document, or silly things like that.  This may not fit in with your philosophy but it should still be possible to do things like this in a different way, at least.  (When you say it autosaves, you mean it saves each revision of the file separately to prevent data loss, right?  So you can go through the past revisions and see what changes you made?  I can't run it right now to try it out, but it looks promising.)

> I think most people who want to change the name of a file don't care what happens to the old file. Maybe I'm being presumptious.

Of course they do.  It is a quick way to duplicate a file when you want to make a new file based on the other.  You should be explicit when you describe an action like that.  "Rename" is wrong, because it is creating a copy of a file under a different name; not renaming an existing file.

I would sometimes like to actually rename a file, too, to literally give it a new name and destroy the original, but I have never seen an application (besides Google docs ;-)) that can do that.  You always have to save a copy and then delete the original from a file manager.  It's annoying.  Maybe you should have both "Rename" and "Save a copy"?

> **chaosgeisterchen said:**
> I would very much appreciate if, for instance, KDE would use Konqueror as open file dialog, as the open file dialog of KDE is great but it lacks options to perform - for instance copy/pase and file deletion.

Agreed.  Open dialogs and the whole process surrounding them suffer from a horrible lack of imagination and waste of duplicated effort.

> **Spif said:**
> Tabs > All. It is a must have feature, especially when working with multiple modules at once.

According to his philosophy, you should get a tabbing window manager, like Ion.  I'd really like to see a tiling/tabbing interface built into GNOME.  The whole "windows overlapping that you can drag around like paper on a desktop" metaphor is retarded.  Someone needs to create an ingenious window manager that does sane, productive things like tiling the entire screen and tabbing multiple applications, but without the l33tness of the barebones "rebel" WMs that emphasize being "lightweight" as if that's some kind of virtue.  Windows should maximize inside panes, everything should resize dynamically when you change a pane's size or span, multiple incarnations of the same application with different documents should be tabbed by the window manager, etc. etc. etc. etc.

> **NoWhereMan said:**
> I must admit this is sometimes annoying, for instance if you type something in a new document, then decide you want to discard it, you close it, and still a file is saved on your desktop...

You should be able to discard the file from within the application.

> **Mystilleef said:**
> On occassions I've been known to say it does your dishes, cleans up after you and massages your girlfriend.

Uh oh.  I'll keep an eye on those two...

> **ago said:**
> * I do not see why Home does not go to beginning of line (in my setup it goes before to first non-whitespace char), I do not think this is consistent.

Pressing Home should go to the first non-whitespace character.  Pressing it again should go to the beginning of the line.

> In Scribes "ctrl-t" is used exclusively for indentation. "Tab" key does not perform indentation. It only inserts a "\t"(Tab) character into the buffer.

Ew.  The "Tab" key should increase indentation of the selected lines and shift-Tab should decrease indentation.

> I know some editors use the "\t" exclusively for indentation, but I think they are wrong! Maybe I'm being too pedantic here?

There are holy wars about it.  :-)

[http://www.jwz.org/doc/tabs-vs-spaces.html](http://www.jwz.org/doc/tabs-vs-spaces.html)
[http://www.adamspiers.org/computing/why_no_tabs.html](http://www.adamspiers.org/computing/why_no_tabs.html)
[http://www.derkarl.org/why_to_tabs.html](http://www.derkarl.org/why_to_tabs.html)

The entire concept of a tab character is a silly anachronism from typing tables in ASCII, but here is a potential solution that uses them:

[http://nickgravgaard.com/elastictabstops/](http://nickgravgaard.com/elastictabstops/)

> What behavior do you expect when you type the "End" key? Do you expect to be taken to the end of the line, or the end of the last character in a line?

What if the end of the line has whitespace?

> **Mystilleef said:**
> I encourage more
feedback/opinions/suggestions/criticisms/comparisons regardless of how
gentle or acrimonious they may be.  I've stopped trying to gauge
emotions when interacting on the Internet. :-)

I wish you could teach me how to do that...

> **quinnman said:**
> Does Scribes support rectangular text selecting and copying or is this feature planned? Does any other simple text editor in GNOME have this feature? Thank you.

Rectangular text editing is a useful feature.  I believe Notepad++ for Windows uses Alt+highlight.

---

### Post by paziek on 2008-04-30
```
paziek@Lolita:~/src/scribes-0.3.3.3$ make
Making all in po
make[1]: Entering directory `/home/paziek/src/scribes-0.3.3.3/po'
file=`echo de | sed 's,.*/,,'`.gmo \
	  && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[1]: *** [de.gmo] Error 127
make[1]: Leaving directory `/home/paziek/src/scribes-0.3.3.3/po'
make: *** [all-recursive] Error 1

```
And I do have gettext installed :s

---

### Post by JordyD on 2009-07-10
I just thought I'd upload this deb I packaged since the Jaunty scribes version does not work. I'm no packager, so I used [GiftWrap]("http://giftwrap.tuxfamily.org/index.php?"). I don't know how good the package is or if I did it correctly, but it works on my computer, so I'm hoping it will help others.

Unfortunately, the forums say that the deb is too large, and tar.gz does not compress it enough. If anybody has a suggestion on how to get it on here, I would gladly upload it.

---

### Post by WildWillie on 2010-01-27
On the Scribes site, it says that the dev branch is the only thing that is officially supported, so that is where I turned to fix the template import issue. I followed the directions on the install site:

```
root# sudo apt-get install bzr libglib2.0-dev
root# sudo apt-get install gnome-common
root# sudo apt-get install python-gtksourceview2
root# sudo apt-get install python-gnome2
root# sudo apt-get install python-gnome2-desktop
root# sudo apt-get install python-gnome2-extras

```

 but 

```
sudo ./autogen.sh
```

gives me

```
...
Error: pygtksourceview2 was not found.
configure: error: Error: Dependency check failed
```

what gives? I also installed gettext.

---

