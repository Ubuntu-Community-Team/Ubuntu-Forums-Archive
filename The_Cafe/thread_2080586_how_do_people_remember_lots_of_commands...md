---
title: "how do people remember lots of commands..??"
date: 2012-11-04
forum: The Cafe
---

### Post by rushikesh988 on 2012-11-04
hello all ,
I am the ubuntu user since 6.06 but let me tell you . I have always found it very complex task to remember commands of linux.

I have also seen that many users here solving problems only with commands (and yes hats off to the forum staff they just rock with their knowlege base) 
I mean there are hundreds (probably thousands not sure) of commands for linux and with there arguments it becomes the huge list ..


I have tried using 
> man -k  
or 
info
whatis
but its still a complex thing to remember ...
Is there is any special trick  except practicing it ???

---

### Post by coffeecat on 2012-11-04
Not an Ubuntu Testimonials & Experiences sub-forum thread.

*Thread moved to **The Community Cafe**.*

---

### Post by oldos2er on 2012-11-04
> **rushikesh988 said:**
> Is there is any special trick  except practicing it ???

Bash has a wonderful memory; I don't.

---

### Post by MG&amp;TL on 2012-11-04
I just tend to remember how to use stuff I use on a regular basis. Others I just look up.

Bash's history is a lifesaver too, as is the Ctrl-R search.

---

### Post by GrubThemeArtist on 2012-11-04
Bash has a structure to it that once you understand the structure then writing out long commands becomes simple. You still have to learn about more command line tools to use which is like learning vocabulary. Also, some tools have their own structure such as sed or awk. You just learn their structure, and then you combine your understanding of the language to to write out whatever tasks you want to to. It's like learning an actual language, you don't just memorize common phrases, you learn how the language works.

You'll still always have to go to man pages to look up options though, that's always going to happen unless you can memorize every option of every command.

---

### Post by 28c64 on 2012-11-04
> **MG&TL said:**
> ... as is the Ctrl-R search.

I typically have a good memory using commands, but I can't believe I never knew about the search function in bash.

Thanks!

---

### Post by MG&amp;TL on 2012-11-04
> **28c64 said:**
> I typically have a good memory using commands, but I can't believe I never knew about the search function in bash.

Thanks!

Not a problem-neither could I! :lol:

---

### Post by PaulW2U on 2012-11-04
> **rushikesh988 said:**
> I mean there are hundreds (probably thousands not sure) of commands for linux and with there arguments it becomes the huge list ..

Include all the command arguments and there are probably millions of options that might provide the solution that I'm looking for. :)

For me, Google is my friend. Somebody, somewhere at sometime will have posted that all important command and it's arguments that will solve my problem if I simply tell Google what it is. For me one of the joys of using Linux is not memorising hundreds of commands and their options but in searching for solutions that have been posted by people who have had exactly the same problem before me.

---

### Post by bhaskar7x7 on 2012-11-04
No, I don't think it's worth mugging up commands, what I do is keep notes, type in commands or things you learn everyday about Linux in a simple libreoffice document file, export it to PDF and save it onto tablet and your phone. To make this easier, install WebDAV software on your android device or good reader on iPad, single click to start wifi and drop in the PDF to the devices, less than one minute work but keeps the latest notes in sync everywhere.

Over the period of time, I do tend to remember commands I use the most and rest like starting wifi hotspot, connecting to Internet or mounting network shares, I refer my notes.

---

### Post by malspa on 2012-11-04
I don't try to memorize many commands; I use bash history, man pages when I need to, web searches when I need to, and my notes.

---

### Post by mamamia88 on 2012-11-04
xfce notes plugin for often used commands.   most commands i use on a daily basis are easy to remember though.  like cd,mv,cp etc.

---

### Post by drmrgd on 2012-11-04
To me, the best thing to remember is what is possible.  If I know that something can be done with a command (usually because I learned a new one from somewhere), then I don't need to necessarily remember the exact syntax, unless it's very complicated.  For example, I recently learned that you can do case-insensitive recursive searches with grep, and pass the output with a line number:

```
grep -rin <query> <location>
```


Another good example is using bash history with a search and replace (for example if I mistyped something or need to make a small change to a long command:


```
!!:gs/<thing to be replaced>/<thing to replace it>/
```

I've been using that a ton for a project that I've been working on that has a lot of files that pass variables around.  So, I can use that to help me remember where the calls are being made and in which line of which script.  

Late on, if I forget that exact syntax, just that I know it's possible will make me do quick searches in the manpages or through Google to get the syntax correct.  

For longer one-liners that approach script length, but not enough to put a whole script together, I usually keep a txt document with those and what they do for quick reference.

In short, I think just playing around a lot and trying things will lead you to find things that you didn't know you could do before.  Then using this forum, the man pages, and Google to get the syntax exactly correct.

---

### Post by Megaptera on 2012-11-04
I find CLI Companion very useful "CLI Companion is a tool to store and run Terminal commands from a GUI. People unfamiliar with the Terminal will find CLI Companion a useful way to become acquainted with the Terminal and unlock its potential. Experienced users can use CLI Companion to store their extensive list of commands in a searchable list." Here: [https://launchpad.net/clicompanion](https://launchpad.net/clicompanion)

---

### Post by pqwoerituytrueiwoq on 2012-11-04
cat ~/.bash_history | grep "fragment of command"

some things i make a script to run so i just type the script name to run some long command
eg:
```
echo -e '#!/bin/sh\ncat ~/.bash_history | grep "$1"' | sudo tee /usr/local/bin/brain-fart;sudo chmod +x /usr/local/bin/brain-fart
```

never knew about ctrl+r  before now :)

---

### Post by SeijiSensei on 2012-11-04
The "apropos" command can sometimes help.  It will list all the possible man pages that apply to the object of apropos.  For instance, "apropos copy" brings up not only cp and scp, but also rsync and ssh-copy-id.  Each item has a brief description; you can see the full documentation with the man command.

Other than that, it's just a matter of experience.  I've used the command line every day for years, so most commands are just second nature by now.  If I want to do something that I cannot remember the command for, I either try apropos or do a Google search.

---

### Post by Erik1984 on 2012-11-05
There are so many bash tricks I don't know. CTRL+R is a good one. Thanks!

I also like the case insensitive history search. I have just put this in my ~/.bashrc:
```
hgrep() {history | grep -i $@ ;}
```

---

### Post by IWantFroyo on 2012-11-05
> **MG&TL said:**
> I just tend to remember how to use stuff I use on a regular basis. Others I just look up.

Bash's history is a lifesaver too, as is the Ctrl-R search.

> **Bash's history is a lifesaver too, as is the Ctrl-R search.**

My life has been a lie.

---

### Post by PaulW2U on 2012-11-05
> **MG&TL said:**
> Bash's history is a lifesaver too, as is the Ctrl-R search.

How come I've been here for two and a half years and never come across this very useful command? :oops:

Thanks MG&TL, I shall be using that a lot.

---

### Post by rushikesh988 on 2012-11-05
i didn't know that ...thanks man

---

### Post by rushikesh988 on 2012-11-05
Thanks all for the valuable tricks and some tips ...

A beer from me to all community  cafe  users :)

cheers..:guitar:=D>

---

### Post by Uncle Spellbinder on 2012-11-05
For me, it has always been repetition. The more you use any command, the easier it is to remember it

Off the top of my head, I use the following regularly enough that I remember them quite easily...

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install <package name>
sudo apt-get remove --purge <package name>
sudo apt-get install -f
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean

---

### Post by rushikesh988 on 2012-11-05
>  sudo apt-get is the first step towards being advance user in linux ;)

---

### Post by whatthefunk on 2012-11-05
I just learn through regular use.  I started out learning basic navigation (cd, ls, mv, cp etc) then learned commands to acquire system information because my old computer sucked and always had problems.  (Great guide here by the way: [http://www.cyberciti.biz/tips/linux-command-to-gathers-up-information-about-a-linux-system.html](http://www.cyberciti.biz/tips/linux-command-to-gathers-up-information-about-a-linux-system.html))  Then I learned package managing stuff like apt-get, apt-cache, and dpkg.  And so on....  I basically just learn something when the need arises.  Im to the point now where I dont need to look at man pages for most things, and then when I get stumped, I at least know where to start looking.  Just keep using the terminal and Im sure that youll get the hang of it and learn a lot.

---

### Post by rushikesh988 on 2012-11-05
oh nice one sir...

---

### Post by samalex on 2012-11-05
I only remember maybe 10-15 often used commands (ps, ls, cat, man, apt-get, dpkg, grep, and a few others), but once I use a command with some lengthy options I almost always just pull it out of bash_history instead of trying to memorize what I did. I never clear out my history, so I generally have a lengthy history to refer back on.

---

### Post by sffvba[e0rt on 2012-11-05
As long as I have the net available, Google and copy/paste I can use the terminal :)


404

---

### Post by dannyboy79 on 2012-11-05
> **rushikesh988 said:**
> hello all ,
I am the ubuntu user since 6.06 but let me tell you . I have always found it very complex task to remember commands of linux.

I have also seen that many users here solving problems only with commands (and yes hats off to the forum staff they just rock with their knowlege base) 
I mean there are hundreds (probably thousands not sure) of commands for linux and with there arguments it becomes the huge list ..


I have tried using 

but its still a complex thing to remember ...
Is there is any special trick  except practicing it ???simply put, the commands you use and practice frequently you won't ever forget.

---

### Post by Jakin on 2012-11-05
Over time, its like remembering anything else.. Complex commands that i might use are also in history, if for some reason i had command-block that day.

---

### Post by mikodo on 2012-11-06
Wow, thanks!  

```
gedit .bash_history
```

Never new of this. And, I was maintaining a "stupid_file", for myself. Duh!

Another one, I didn't know:

```
Ctrl-R search
```

Like, I could ever get so good to remember something like this:

```
sudo dpkg --get-selections | grep '[[:space:]]install$='| awk '{print $1}' > installedpackages
```

---

### Post by stinkeye on 2012-11-06
On using bash history.
Running these 2 commands...
```
echo "\"\e[5~\": history-search-backward" >> ~/.inputrc
echo "\"\e[6~\": history-search-forward" >> ~/.inputrc
```
Binds pageup to history-search-backward....Binds pagedown to history-search-forward.

So if I enter **sudo dpkg** I can cycle through all the history commands starting with **sudo dpkg**, using pageup and pagedown.

How did I know this? Looked in my 4 years worth of gnotes.

---

### Post by Paqman on 2012-11-06
> **rushikesh988 said:**
> 
I have also seen that many users here solving problems only with commands (and yes hats off to the forum staff they just rock with their knowlege base) 
I mean there are hundreds (probably thousands not sure) of commands for linux and with there arguments it becomes the huge list ..


I have tried using 

but its still a complex thing to remember ...
Is there is any special trick  except practicing it ???

They may well work as sysadmins and such, and are doing this stuff all day every day for a job.

---

### Post by mikodo on 2012-11-06
> **stinkeye said:**
> On using bash history.
Running these 2 commands...
```
echo "\"\e[5~\": history-search-backward" >> ~/.inputrc
echo "\"\e[6~\": history-search-forward" >> ~/.inputrc
```Binds pageup to history-search-backward....Binds pagedown to history-search-forward.

So if I enter **sudo dpkg** I can cycle through all the history commands starting with **sudo dpkg**, using pageup and pagedown.  Nice.

I wanted to read about these. I found and followed the further suggestions in the link below, but stopped at the GREP color features:

[https://wiki.ubuntu.com/Spec/EnhancedBash](https://wiki.ubuntu.com/Spec/EnhancedBash)

---

### Post by rushikesh988 on 2012-11-06
> **Paqman said:**
> They may well work as sysadmins and such, and are doing this stuff all day every day for a job.
ohh  i see

---

### Post by drmrgd on 2012-11-06
> **stinkeye said:**
> On using bash history.
Running these 2 commands...
```
echo "\"\e[5~\": history-search-backward" >> ~/.inputrc
echo "\"\e[6~\": history-search-forward" >> ~/.inputrc
```
Binds pageup to history-search-backward....Binds pagedown to history-search-forward.

So if I enter **sudo dpkg** I can cycle through all the history commands starting with **sudo dpkg**, using pageup and pagedown.

How did I know this? Looked in my 4 years worth of gnotes.

Wow!  Excellent trick.  Didn't know about that, but now it's added to my system.  This is extremely useful!

---

### Post by nothingspecial on 2012-11-06
> **stinkeye said:**
> On using bash history.
Running these 2 commands...
```
echo "\"\e[5~\": history-search-backward" >> ~/.inputrc
echo "\"\e[6~\": history-search-forward" >> ~/.inputrc
```
Binds pageup to history-search-backward....Binds pagedown to history-search-forward.

So if I enter **sudo dpkg** I can cycle through all the history commands starting with **sudo dpkg**, using pageup and pagedown.

How did I know this? Looked in my 4 years worth of gnotes.

Thank you, that's fairly awesome :)

---

### Post by koenn on 2012-11-06
> Like, I could ever get so good to remember something like this:

```
sudo dpkg --get-selections | grep '[[:space:]]install$='| awk '{print $1}' > installedpackages
```

That's the thing - you don't have to **remember** a line like that -- as somebody already mentioned : it's like learning a language

the only thing worth remembering there is that 'dpkg --get-selections' will list software you installed through dpkg. Or remember even less - that dpkg has an option to list installed software (and you can look up which one that was whenever you need it). 

The rest -- pipes, grep, awk, output redirection ... -- is stuff you pick up as you go, and if you understand what they are, you'll figure out a way to combine them and build that command as needed

FWIW, 
```
dpkg --get-selections | grep  'install$' | cut -f1

```
or even 
```
dpkg --get-selections | cut -f1

```
would work just as well

---

### Post by CharlesA on 2012-11-06
> **dannyboy79 said:**
> simply put, the commands you use and practice frequently you won't ever forget.

Pretty much this. I know I've pretty much memorized some of the commands I use often, and if I have a whole load of commands I need to run to accomplish a specific task (such as reinstalling my raid drivers via dkms), I write a script for it.

> **Jakin said:**
> Over time, its like remembering anything else.. Complex commands that i might use are also in history, if for some reason i had command-block that day.

History and scripts are (only) the way to fly. ;)

---

### Post by rushikesh988 on 2012-11-07
> **CharlesA said:**
> 

History and scripts are (only) the way to fly. ;)



 totally agree

---

### Post by Erik1984 on 2012-11-07
> **stinkeye said:**
> On using bash history.
Running these 2 commands...
```
echo "\"\e[5~\": history-search-backward" >> ~/.inputrc
echo "\"\e[6~\": history-search-forward" >> ~/.inputrc
```Binds pageup to history-search-backward....Binds pagedown to history-search-forward.

So if I enter **sudo dpkg** I can cycle through all the history commands starting with **sudo dpkg**, using pageup and pagedown.

How did I know this? Looked in my 4 years worth of gnotes.

Where should those commands go, just enter them once in the terminal?

---

### Post by MG&amp;TL on 2012-11-07
> **Euroman said:**
> Where should those commands go, just enter them once in the terminal?

Yup. All they do is add a new keyboard binding to the configuration file for (bash?) your shell.

---

### Post by Erik1984 on 2012-11-07
> **MG&TL said:**
> Yup. All they do is add a new keyboard binding to the configuration file for (bash?) your shell.

Thanks. I understand them now, they just add a line to the file ~/.inputrc. It seems to work :)

---

### Post by linuxvstheworld on 2012-12-06
I just use necessary commands until they practically stick.

---

