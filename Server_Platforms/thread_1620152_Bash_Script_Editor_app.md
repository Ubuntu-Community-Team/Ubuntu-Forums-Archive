---
title: "Bash Script Editor app?"
date: 2010-11-12
forum: Server Platforms
---

### Post by samosamo on 2010-11-12
Hey everyone, is there a good GUI app for bash scripts?  Currently I write them in vim, but as they get more complicated I would really like some formatting and highlighting.

---

### Post by kerry_s on 2010-11-12
gedit?

---

### Post by DaithiF on 2010-11-12
well you could use gedit, but I suspect you're not using vim to its full potential -- syntax highlighting, auto indenting, folding, etc ...

---

### Post by kjurkic on 2010-11-15
> **samosamo said:**
> Hey everyone, is there a good GUI app for bash scripts?  Currently I write them in vim, but as they get more complicated I would really like some formatting and highlighting.

Hi

Pay no attention to the Übergeek snobs and don't bother with the masochist's playthings like vim or (shudder:roll:) emacs. Remember, misery loves company.

UltraEdit will do what you want without needing an advanced CommpSci degree and months of your life reading the man pages.:P

So will Bluefish for that matter, as long as you save your file with the .sh extension

regards
Ken

---

### Post by samosamo on 2010-12-16
Thanks kjurkic!  I like both of your suggestions.  They both do Bash highlighting and autoindenting, but neither seem to have error checking or other types of functions to clean up the code.

---

### Post by CharlesA on 2010-12-16
I didn't know there was a program that automatically checks your code for errors.

I always test my bash scripts on a VM before trying them on a production machine.

See here: [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_02_03.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_02_03.html)

---

### Post by samosamo on 2010-12-16
I just found this.  It is a ruby script that corrects your file for indents, makes it easier to find errors that are caused by incomplete starts/closings to if/else and things like that.

[http://www.arachnoid.com/linux/beautify_bash/](http://www.arachnoid.com/linux/beautify_bash/)

---

### Post by CharlesA on 2010-12-16
Thanks for the link. :)

---

### Post by SeijiSensei on 2010-12-16
I use [jed]("http://www.jedsoft.org/jed/"), a lightweight version of emacs.  It has syntax checking as well.  It's especially good at finding mismatched parentheses and braces.  It also has a number of built-in customizations for common file types including shell scripts and programming languages like C and PHP.  In these cases keywords and commands are also color-coded and highlighted.

jed is available from the repos via "sudo apt-get install jed".  However it uses a lot of control-key sequences like emacs.  For someone who learned emacs some years (decades, actually) ago, it was an easy transition to jed.  For others, it would be a bit of work, though there are drop-down menus for most common commands as well as the keyboard shortcuts.

I've also opened scripts with KDE's kate text editor.  It has syntax highlighting; don't know whether it actually checks the syntax like jed does, though.

---

