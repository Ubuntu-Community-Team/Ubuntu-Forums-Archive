---
title: "Can't remember the name of this editor"
date: 2011-05-18
forum: The Cafe
---

### Post by jhonan on 2011-05-18
I was using Ubuntu 10.04 last year for some scripting (Bash, SQL, Python, XML editing, modifying CSV files etc), and now I'm back on a fresh install of Ubuntu, minus the apps I was using.

But I can't remember the editor I was using, and I loved it! I'm using Gnome, so pretty sure it would have been GTK-based (i.e. not Qt or Java) :confused:

The main feature I remember (and the one I really miss) was the ability to select a word in a file, and it would automatically find the same word in all other files in a certain location. It made this so easy, and was very helpful for code refactoring (finding field or variable names in a load of files and changing them all at the same time)

So it could have been;

- gedit - but I can't seem to find the plugin
- Wasn't vim or emacs; I don't use these
- geany - Again, I thought it was this, but can't find the word-search plug-in
- Eclipse... perhaps... but I installed this today and can't get it to do the file search thing
- Bluefish... or some other code editor?

Whatever it was, it would have had the simplicity of gedit for editing plain text files, but also things like indents, right-margin line, code colouring etc.

Any suggestions?

---

### Post by el_koraco on 2011-05-18
Kate does this, but she's QT.

---

### Post by jhonan on 2011-05-18
> **el_koraco said:**
> Kate does this, but she's QT.
Yeah, I used to love using Kate when I was on KDE, and leafpad was surprisingly good as well. But for various reasons I'm on Gnome on this particular setup, and I generally tend to stick with same-library apps (GTK for Gnome, Qt for KDE)

It was probably geany or gedit with some obscure plugin...

---

### Post by el_koraco on 2011-05-18
[http://en.wikipedia.org/wiki/SciTE]("http://en.wikipedia.org/wiki/SciTE")

[http://en.wikipedia.org/wiki/JEdit]("http://en.wikipedia.org/wiki/JEdit")

?

---

### Post by jhonan on 2011-05-18
Not Jedit... possibly scite or some derivative. Thanks for your help on this btw, it's been frustrating me all day!

Actually, I just downloaded bluefish and its looking pretty nice - It doesn't have that 'find in files' thing, not that I can see, but there are some other nice features in the latest version.

Incidentally, as I was googling this, I found this very thread as the 4th entry on google!.. I can't believe google is updating its index so quickly - within minutes of making the post google has indexed the page. Impressive.

---

### Post by slooksterpsv on 2011-05-18
Doesn't MonoDevelop do refactoring, was it MonoDevelop?

EDIT: No it doesn't do all those format hmm...

EDIT 2: Tried code::blocks, wasn't it, but I'm hearing lots of good things about NetBeans so I'm trying it. I'll let you know if it works or not.

---

### Post by jhonan on 2011-05-18
I've just remembered something else it could do, that I absolutely loved.

You know in bash when you declare functions {} - Well, what this editor did was list all the functions in a .sh file in a panel on the left, like a method browser - So although you were editing a .sh file, it felt more like c++, you could click on a function name and it would jump to the location in the script.

I'm starting to think it was probably Eclipse....

> **slooksterpsv said:**
> Doesn't MonoDevelop do refactoring, was it MonoDevelop?
It didn't do the refactoring, just made it easier by letting you search files recursively for variable name instances, so you could get rid of unreferenced variables for example.

---

### Post by el_koraco on 2011-05-18
I was gonna suggest bluefish, but jedit and scrite seemed more in tune, because they kinda look like gedit. 

Kate would probably suit you the best, but she seems to want to pull 50 mb worth of dependencies in, even with no install recommends. 

Can't remember when I did some scripting, so I do remove gedit and install leafpad right after I remove brasero and install k3b on any Ubuntu first thing.

---

### Post by oldfred on 2011-05-18
I have this as part of my rsync backup and make sure I have a copy before a clean install. Then I get all my old apps, but also have found tha I am installing old apps I do not want anymore and should houseclean before reinstalling.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

dpkg --get-selections > ~/my-packages
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade

---

### Post by el_koraco on 2011-05-18
> **oldfred said:**
> 
dpkg --get-selections > ~/my-packages
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade

you need to do sudo apt-get update before dselect, but yeah, it's a handy thing.

---

### Post by jhonan on 2011-05-18
Thanks for that dpkg suggestion.

So anyway, I've been trying a few editors and I think what I used was Eclipse + ShellEd plugin.

It's the only combination I can get to display bash functions in an outline panel. And it does the 'references' dialog, which searches the entire project for calls to a function. (i.e. for tracking function dependencies)

---

