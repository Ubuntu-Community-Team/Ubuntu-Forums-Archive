---
title: "Ubuntu Cheatsheet"
date: 2008-02-25
forum: The Cafe
---

### Post by thesingularity on 2008-02-25
removed

---

### Post by Dojan5 on 2008-02-26
YEAH, i like this cheatsheet, not least the name.
But for me (as a beginner) It is very useful

===EDIT 1===

:.:.:Off Topic:.:.:
Oh yaa, why dont Canonical include Alt+T as a command for opening the terminal?
I out my settings like that, VERY useful...

>>>EDIT 2<<<
O_O
Why aint UbuntuForums link on the sheet?

---

### Post by mr.propre on 2008-02-26
Well ist not perfect, but a thanks for you.
BTW: you can programm a shortcut to open your terminal, even to program it using a function key (like most keyboard have).

System -> Preferences -> Keyboard Shortcuts.

---

### Post by handy on 2008-02-26
You may find a few additions on [***_this site_***]("http://tldp.org/guides.html").

Keep up the good work, you will learn heaps compiling you Cheatsheet.

---

### Post by machoo02 on 2008-02-26
```
rm -i *path*    delete a file or directory and all its contents
```
The -i flag will cause rm to be interactive, and ask you to confirm before deleting.  It won't allow you do delete a directory that currently has files in it.  For that, you need the -R (recursive) flag to delete a directory AND its contents.

---

### Post by koleoptero on 2008-02-26
Oh this is great! Keep adding things! this would be really helpful to a lot of people (including me). :)

Another no so known (but potentially dangerous) and useful thing is when you want to get root priviledges in the terminal, like the old su command, which is: sudo -i

---

### Post by JurB on 2008-02-26
/boot  holds the **linux kernel**, startup files and grub
/root  is root (administrator) home folder 
ps ax  shows all **[SIZE=-1]processes[/SIZE]**
...

---

### Post by tehet on 2008-02-26
> **koleoptero said:**
> to get root priviledges in the terminal, like the old su command, which is: sudo -i
Yes, that's a proper way to gain root. **sudo su** as stated in the cheat sheet is a big no-no!

---

### Post by afeasfaerw23231233 on 2008-02-26
i am a noob. but i would suggest you to add 
vim filename  -->  i [insert text] --> esc [exit] --> :q! [quit] / :wq! [save and quit]
sudo apt-get install something 
top [see cpu usage, ram usage, uptime..]
free -m [ see ram usage] free -m -s 1 [ update every 1 sec]
df -h [see disk usage]
it may has error, i cannot remember more at the moment
edit: ah...
chmod -fR 777 filename [777 can be replaced by other values]
ctrl + c [terminate the process in the terminal]

---

### Post by koleoptero on 2008-02-26
> **afeasfaerw23231233 said:**
> i am a noob. but i would suggest you to add 
vim filename  --> shift + i [insert text] --> esc [exit] --> :q! [quit] / :wq! [save and quit]


You don't need shift to enter insert mode in vim, just i. And there are so many things about vim that it's a chapter in itself...

---

### Post by Vadi on 2008-02-26
I didn't even know some of this stuff, so thanks!

I think you should add planet.ubuntulinux.com though, it's like a congregation of a bunch of ubuntu-related blogs.

---

### Post by koenn on 2008-02-26
> **koleoptero said:**
> You don't need shift to enter insert mode in vim, just i. And there are so many things about vim that it's a chapter in itself...
yes, but the actions needed to get in to edit mode, edit a text, save and quit, are the absolute minimum you need to edit a file. And it's not uncommon for new users to actually reboot their computer because they can't figure out how lo leave vim, so it's a usefull 'cheat code'

for the record : the [esc] is not really an exit, it means 'leave edit mode, enter command mode' so that the commands (write, quite) actually work in stead of being added as text to the file.

---

### Post by tdrusk on 2008-02-26
This seems more fulfilling...

[http://people.debian.org/~debacle/refcard/refcard-en-a4.pdf](http://people.debian.org/~debacle/refcard/refcard-en-a4.pdf)

---

### Post by AndyCooll on 2008-02-26
In fact here are the ultimate in cheat sheets: [Linux-Unix-Cheat-Sheets]("http://www.scottklarr.com/topic/115/linux-unix-cheat-sheets---the-ultimate-collection/")

:cool:

---

### Post by blithen on 2008-02-27
How did you make the cheat sheet?
EDIT: What program did you use rather.

---

### Post by thesingularity on 2008-02-27
removed

---

### Post by kaens on 2008-02-27
Some more useful terminal things:

`command` - substitute ouput of command, e.g.

```
 
>file `which man`
/usr/bin/man: symbolic link to `../lib/man-db/man'

```

!! - run the previous command
Ctrl-r - search backwards through history for command
^foo^bar - run last command substituting foo for bar


One more thing that I've found particularly useful:

dpkg --contents /var/cache/apt/archives/<packagename>

will return a list of what files were added / modified on your system by <packagename>

---

### Post by afeasfaerw23231233 on 2008-02-27
> **koleoptero said:**
> You don't need shift to enter insert mode in vim, just i. And there are so many things about vim that it's a chapter in itself...

yes, thanks for your suggestion. i only know how to insert, esc, : , q , w and !. i am too lazy to look at the man page

---

### Post by darsu on 2008-02-27
Some important regular expressions tokens that apply everywhere:
^ = start of line
$ = end of line

---

### Post by kevdog on 2008-02-27
Although this might be a bit much for your cheatsheet, I think learning grep, sed, and awk are quite useful, since these in my opinion are really powerful tools to search through files, and filter what you want.

Im no master at any of these tools, however I found a great one-line sed site (I dont understand all the examples, but they are really easy to use):
[http://sed.sourceforge.net/sed1line.txt](http://sed.sourceforge.net/sed1line.txt)

---

### Post by handy on 2008-02-27
> **thesingularity said:**
> Welcome, added Ubuntu Forums to the cheatsheet. :)




Nice thanks for the tip. :)




Whoops! My mistake - fixed. :)




Cool, wow I did not know about the ram usage nor hard disk usage commands. Thanks very much!




Welcome, thanks for the link. I will check it out soon as I currently have a dialup connection.




I created my own web based software that allows anyone to create web based cheatsheets for any project, it is currently used at [hey4.com]("http://hey4.com")

You can see another example of the cheatsheet web application working here: [Ultimate Mathematics Cheat Sheet]("http://hey4.com/ultimate_mathematics_cheat_sheet")

A special thank you to all the people who "thanked" my post. :)

How could I not thank such a post?

Of course you would agree... :-)

---

### Post by Vadi on 2008-02-27
I added the planet on your cheatsheet:

[http://hey4.com/ubuntu_cheat_sheet](http://hey4.com/ubuntu_cheat_sheet)

---

### Post by Xbehave on 2008-02-27
keep it short otherwise people wont read it. too many of the *'better'* alternatives are far too long and most people wont bother reading them

---

### Post by corney91 on 2008-02-27
Just a minor thing - you only need to use 'cd' to get to the home directory, it's essentially the same as 'cd ~' but two characters less :p

Anyway, great cheatsheet!:)

---

### Post by days_of_ruin on 2008-02-29
> **corney91 said:**
> Just a minor thing - you only need to use 'cd' to get to the home directory, it's essentially the same as 'cd ~' but two characters less :p

Anyway, great cheatsheet!:)

Wish I had known that#-o

---

### Post by thesingularity on 2008-03-04
removed

---

### Post by marufaberlin on 2008-03-04
How about some commands you should definitely **not** run (see my signature). You maight want to look at [http://ubuntuforums.org/announcement.php?f=100](http://ubuntuforums.org/announcement.php?f=100).

PS.: Is the Ubuntu CheatSheet available as a PDF Document?

---

### Post by TorqueyPete on 2008-03-17
What a great thread!
 I reckon that a beginners list like this should be part of the introduction every Linux distro.
 After all , the vast majority of the, so far, limited number of folks who actually know what Linux is _but are Windows users by default_, still believe it's for experts and techies only.
 May I suggest altering the "sudo apt-get install package" line to "sudo apt-get install/remove package" and add the info that you use either install or remove, depending on your intentions for the package? Just so that total noobs like me can undo their mistakes, without trawling through tutorials that seem to be so in depth that you get fed up.
 Not everyone, has the ability to concentrate for long enough, like me with severe tinnitus, and some have 'short term memory loss', which is a recognized disability.

 Thanks again for a useful list!

---

