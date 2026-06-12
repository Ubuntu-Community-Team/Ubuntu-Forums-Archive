---
title: "Official autokey thread, and call for devs/users"
date: 2008-02-21
forum: The Cafe
---

### Post by peabody on 2008-02-21
Hello, I'm the autokey dev.  In case you're curious what autokey is, here's a video demonstration and download link: [http://autokey.sf.net/](http://autokey.sf.net/).

The good news is I've made a new 0.31.1 release which has a number of niceties:

[LIST]
[*]Can turn voice off by specifying 'voice = no' in the [config] section of the abbr.ini file.
[*]New placeholders, put %% in an expansion to indicate where you would like the cursor placed after expansion
[*]Arguments, use abbrv~arg and place %s in an expansion to have whatever single word is typed after the tilde be inserted
[/LIST]

The BAD news

I can't work on it anymore until the summer.  I hate to abandon whatever users I currently have, but I just flunked a midterm :(.  I love this project but I've been putting off things I have to do for it...so...

This is a shout-out to anyone with some rudimentary Python skills.  I could use a maintainer in my absence who'd be willing to cleanup the code and bring the project closer towards its goals.  Some of the initial goals are:

[LIST]
[*]International Keyboard Support
[*]Example gui front end of somekind.  However, I don't want it implemented in autokey.py.  I would like instead some sort of IPC so autokey.py can communicate to any number of front ends
[*]Possibly a macro recording feature.
[*]Massive code cleanup :), the project's a mess because it was hacked together as a proof-of-concept.  There are functions which take parameters that aren't used anymore, encapsulation of responsibilities among the functions is pretty darn bad.
[/LIST]

If anyone's interested, get in touch with me somehow, either via the thread, or via the sourceforge page.

---

### Post by LOBONCA on 2008-03-09
Hello Peabody,

I am new to Linux and miss AutoHotKey. I downloaded AutoKey but get thisr: 
Error: Dependency is not satisfiable libc6
libc6 is installed on my system.

How can I fix this?

---

### Post by peabody on 2008-03-09
> **LOBONCA said:**
> Hello Peabody,

I am new to Linux and miss AutoHotKey. I downloaded AutoKey but get thisr: 
Error: Dependency is not satisfiable libc6
libc6 is installed on my system.

How can I fix this?

Are you on a 64-bit system perchance?  If so, you'll have to rebuild the deb from the source tarball.  Download the tar, extract ([http://sourceforge.net/project/showfiles.php?group_id=216191#downloads](http://sourceforge.net/project/showfiles.php?group_id=216191#downloads)) and run debuild from the extracted folder.  You may have to install the debian developer tools:

```

sudo apt-get install build-essential devscripts debhelper

```

If everything goes smoothly, a nice x86_64 deb will get built in the parent folder.  You should just be able to dpkg -i that package or double click it to have gdebi install it.

If it's not the case that you're on a 64-bit system then that is indeed a strange error and I wouldn't have a good idea what would cause that :( sorry.

[Edit: just in case you do get a 64-bit package up and running, could you do me a favor and attach the deb to the thread?  I can then post it the sourceforge release page, thanks].

---

### Post by szymon_g on 2008-03-09
hm... sorry for (maybe) dumb question:

will it work with (g)vim :? and, if yes, how to (dynamiclly) turn it on/off :?

---

### Post by peabody on 2008-03-09
Well, gvim already has this feature :).  The scroll lock key toggles expansion on and off, so I take it you'll probably want the program off while you're in gvim.

---

### Post by sonicprogress on 2008-04-30
I love this program already, as writing a piece of software like this is something I came up with as an idea around 6 months ago. Unfortunately, I haven't programmed since the days of BBC Basic!

Is there any chance you could make it so that I can run it without the qwerty/dvorak dialog popping up (perhaps hack this into a commandline option?), and without asking for sudo access?

I'd like to basically autorun it at boot, so I don't have to remember to run it every time...

Also while I understand that its only a proof of concept right now, I have plenty of ideas that I would love to throw into the pot. Let me know if you'd like to here what I envisioned way back when.

It would be desperate shame to see this stop here.

---

### Post by peabody on 2008-05-03
It won't stop here, but I've just been so incredibly busy (it's midterms right now).  I'm hoping over the summer that I'll have a lot of time to spend on this project.

If you need the program to run at login, put an entry in session control panel for 'autokey.py'.

---

### Post by nhasian on 2008-05-07
yes, i'd like to help out as well with the development if i can.  In the TODO list you mentioned having a blacklist for expansion keys.  I propose a whitelist where the expansion is executed ONLY IF a certain string is matched from the title window.  For example I would like to have the same abbreviation but different outputs based on which program or website i'm in.

PS how do you terminate the program from running?  like if i want to modify the ~/.abbr.ini and relaunch it to activate the new changes?

---

### Post by peabody on 2008-05-08
killall autokey.py

Feel free to play with the source code and let me know if you get anywhere.  I'm still swamped, but June is fast approaching...

FYI, the program dynamically reloads .abbr.ini, you don't have to relaunch.

---

### Post by nhasian on 2008-05-08
duh i should have known that.  Hey do you have a bugtracker set up for autohotkey?  I'm finding it very versatile and useful, but i'm running into bugs as well.  for example, i dont think you can use numbers in the abbreviations.  like:

hello1 = hello world
hello2 = hello universe

---

### Post by peabody on 2008-05-08
Feel free to use the bugtracker on the sourceforge page.  However, I have a solution for you:

Find your autokey.py script and search for the line that starts with 'word_chars'.  That's a string of everything that's to be considered a word character.  Just add the numbers you want to use to that string.

In future versions I'm going to make this thing something you can customize via ~/.abbr.ini as I've had several requests to make various characters usable in abbreviations and I figure it's just easiest to let the user customize that.

---

### Post by nhasian on 2008-05-09
thanks!  that did the trick. you know your gonna make me learn python just so i can work on this script right? ^_^

by the way you really use a Dvorak keyboard? how many wpm can you do with that?

---

### Post by peabody on 2008-05-09
I haven't typed much faster than when I used QWERTY.  I find the layout more ergonomic however.

---

### Post by EarloftheWest on 2008-05-22
I just installed Autokey and it's already working out great. Autohotkey was the one application that I really missed when I moved to Ubuntu.

Peabody, thanks so much for taking the time to make it.

Interestingly, I use the Dvorak keyboard layout, too. I've toyed with switching to [Colemak]("http://colemak.com/").

One file that I used on a somewhat regular basis in Windows under AutoHotKey was a spell check program:
[http://www.autohotkey.com/download/AutoCorrect.ahk](http://www.autohotkey.com/download/AutoCorrect.ahk)
It doesn't look too hard to convert it to AutoKey.

---

### Post by bas.janssen on 2008-05-27
Hi there! 

First; ***BIG THUMBS UP*** for you, peabody! 

After finding your autokey program on sourceforge i finally ditched windows xp in favour of ubuntu/linux on my desktop. :)

I work for a small isp and used pc magazine's 'robotype' for most of my daily e-mail correspondence for years now. (people always asking the same ... questions) Saves me a few hours of work on a daily basis.. 

I've been using linux for ages on server systems now, but not having a 'robotype for linux' kept me from doing the desktop switch for years. 

So I would love to contribute to the development of autokey, but I'm a bit of a lousy programmer (only a bit of php/perl coding, no python). 

One of the things I'm thinking about is to create a MySQL 'importer/exporter' for more efficient storage, editing an sharing of the collection. (i.e. grouping of multiple abbreviations in categories, having a shared library, search possibilities, etc etc)    

Maybe there are other things i can do for you. (offer you free hosting space, bug reporting, etc) If so, do send me a P.M.

Thanks again for doing a great job! 

Bas Janssen 
Amsterdam, the Netherlands

---

### Post by Karolis on 2008-06-19
GREAT program! Unfortunately not quite usable yet :(

Why?

Well, two things really:

1. Needs and ability to set the activation button instead of auto-changing the text;

2. If you are non-English speaker and you use more than one keyboard layout, the program uses whatever keyboard you are using instead of set abbreviation. So for example in Lithuanian keyboard = button is Ž. So if I set abbreviation targ = target="_blank" and the keyboard is set to Lithuanian, after typing targ I get targetž"_blank"

I'll be waiting forward for new releases. Until then...

---

### Post by kristian.rekovic@gmail.co on 2008-06-25
[http://www.gnome.org/~parente/pyatspi/doc/](http://www.gnome.org/~parente/pyatspi/doc/)   <---- API Documentation for pyatspi library
[http://live.gnome.org/GAP/PythonATSPI](http://live.gnome.org/GAP/PythonATSPI)        <---- Some code example

Below is a little example of how you can get it to display let's say keyboard hw codes, or the actuall letter of the keys.
hopefully if the code below helps just please add my name to the code, otherwise it's free code. 

Here is a present for you pyatspi it's like api for windows, i put the little code below together, forget the keylogger, atspi has everething you need, as well as more. but here is a usefull example for you below. contact me via email [email]kristian.rekovic@gmail.com[/email]

#/usr/binenv python
#gexpansion.py
#
# requires pyatspi in > synaptic
# eather manually enable atspi keyboard accesability
# or install acerciser in > Applications-add programs-Programming (make sure u enable all repos for this install)
# Run acerciser and it will ask if you want to enable keyboard accesability say yes, log out of gnome and log back in then bang the #script below will work just don't forget to install pyatspi.
#
#Program information: Gnome text expansion utility.
# Author: Kristian Rekovic
# gexpansion - gnome text expansion utility written by Kristian Rekovic.
# Copyright (C) 2008 Kristian Rekovic
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program. If not, see <http://www.gnu.org/licenses/>.

import pyatspi
import os
import string
import sys
import re

def callback(event):

os.system(['clear'][os.name == 'linux']) #Clear linux console
string_event = str(event) #Convert event to string
keystring = string_event[37] #Prints the letter of the string pressed
hwcode = string_event[19]+string_event[20] #hwcode:Hardware code for pressed key <--- i prefer this when dealing with st
print keystring #<----------- keystring of released key
print hwcode #<----------- Hardware code for pressed key.
print event #<----------- Raw data i converted to text in event_string then parsed in keystring and hwcode.
#If you look up pyatspi in google you will se more example code which has a full accesability feature
#It's kind of like api for windows but a hell of a lot better. Enjoy.

reg = pyatspi.Registry
reg.registerKeystrokeListener(callback, mask=pyatspi.allModifiers())
reg.start()

---

### Post by peabody on 2008-06-26
This is really great!  Thanks for pointing this out.  I will definitely use this.  However, I've discovered a caveat: It only works with gnome applications which use assitive technology.  That covers quite a few applications including firefox and openoffice.org.  However, just about any KDE app doesn't work, and other obscure apps which use other toolkits, such as the x11 toolkit version of emacs.  Opera doesn't work either.

Since I'm looking for a method that provides the most general solution, I will probably pursue a hybrid approach.  At the very least, I'll use both methods and allow the user to choose from them.

The good news is that this approach provides somewhat of a fix to the keyboard encoding issue.

---

### Post by cdekter on 2008-06-26
I was using AutoHotKey in Windows and was disappointed when I found there was nothing like it for Linux. Now I'm happy again! :)

I would be glad to help out with development of this excellent utility. I have a decent level of experience programming in Python (been doing it for my day job the last 2 years). I also have experience with wxWidgets so I would be able to work on creating the GUI front end you've mentioned.

---

### Post by peabody on 2008-06-29
Sorry it took me so long to respond, I responded to your email to the effect of "If you get me your sourceforge account, you'll have commit access."  Feel free to play with the code and if you're sure you've added something worthwhile and stable, go ahead and commit.

Before doing anything too dramatic though, let's talk some shop.  I plan to roll in dramatic changes in a few weeks.  In particular I've been playing around with the pyatspi module pointed out to me in a previous post.  Despite its limitations, it's awful snazzy and should prove to be a bit of a Holy Grail for people dealing with internationalization issues.  It still doesn't work too well if you actively swap between input methods, but it "just works" for the default keyboard layout chosen for your x11 install.

I've also allowed the user to specify what characters they consider to be word characters.  You'll have full control over what characters you can use in your abbreviations.

Unfortunately, I'm booked from July 2nd to the 10th and won't be able to work during that time.

---

### Post by kristian.rekovic@gmail.co on 2008-07-11
[http://gexpansion.sourceforge.net/](http://gexpansion.sourceforge.net/)
Linux autotext utility

---

### Post by LOBONCA on 2008-07-20
For those developing AutoKey I strongly suggest you take a look at Phrase Express [http://www.phraseexpress.com](http://www.phraseexpress.com)

It blows the doors off of AutoHotKey in a major way. It is flexible and has great features that would do Linux developers well to take a look at it. I am dying on the vine with no auto typing / app launching program in Linux. Pleeeeaaaaazzzzeee work on this. 

Many thanks.

---

### Post by cdekter on 2008-07-20
> **LOBONCA said:**
> For those developing AutoKey I strongoy suggest you take a look at Phrase Express [http://www.phraseexpress.com](http://www.phraseexpress.com)

It blows the doors off of AutoHotKey in a major way. It is flexible and has great features that would do Linux developers well to take a look at it. I am dying on the vine with no auto typing / app launching program in Linux. Pleeeeaaaaazzzzeee work on this. 

Many thanks.

Thanks for your post. We are currently working on an almost total rewrite of Autokey, including a GUI as well as many new features. In particular, we have implemented almost all the hotstring features that AutoHotKey offers. I have been searching for ideas on additional features, and this is a great help. I will be taking a detailed look at Phrase Express to see what we can implement in Autokey. Watch this space! :)

---

### Post by sonicprogress on 2008-09-03
Is there any progress on this at all? :KS:lolflag:

---

### Post by cdekter on 2008-09-04
Yup, there certainly has. A 0.40 version is basically ready, anyone interested in giving it a try, feel free to PM me for more details.

---

### Post by jfl on 2008-09-05
> **cdekter said:**
> Yup, there certainly has. A 0.40 version is basically ready, anyone interested in giving it a try, feel free to PM me for more details.
Can't wait !!!
Thanks for all your efforts.

---

### Post by cdekter on 2008-09-06
Thank you to those who have posted and pm'ed me over the last few days regarding Autokey 0.40. I will endeavour to package up a release archive in the next day or so and will post the details here. Promise :)

---

### Post by cdekter on 2008-09-07
I've uploaded a new version of Autokey on the Sourceforge project page. Please note, this is a zero point release, meaning there are potential major bugs yet to be uncovered and as yet incomplete functionality. See the release notes on Sourceforge for more information on this. To download, follow this link:

[https://sourceforge.net/project/showfiles.php?group_id=216191]("https://sourceforge.net/project/showfiles.php?group_id=216191")

Please post any requests for help on the project's forums on Sourceforge.

---

### Post by zeltak on 2008-09-23
Hi

Autokey seems an awesome program and after a bit fiddling around i got it to run in kubuntu 8.04, it runs but has very strange behaviours. for one it stops working (even though the program is still running) after a few uses. also when it complete the text it inserts double spaces and mixed characters in example using the example abbr.ini:

btw inputs > byy  the wa

etc...

can you guys help with these issues, i would really love to use it , it seems a killer program!

thx

zeltak

---

### Post by cdekter on 2008-09-23
You've hit on a bit of a hole in our testing there - I'm a GNOME user so I'll have to run up a Kubuntu VM to see if I can reproduce the problems you mention. Will keep you posted.

---

### Post by zeltak on 2008-09-23
Thx for the effort, let me know if you need help testing!

thx

Zeltak

---

### Post by GregMB on 2008-10-02
This is an awesome program, but I have a problem with it, and the fact I use the Dvorak keyboard layout. When I type "btw", nothing happens, but if I type "xy," (where the keys are in QWERTY) it expands to "xf yd. ,af". Any idea how to solve this? I'm using version 0.40.0.

---

### Post by cdekter on 2008-10-04
> **GregMB said:**
> This is an awesome program, but I have a problem with it, and the fact I use the Dvorak keyboard layout. When I type "btw", nothing happens, but if I type "xy," (where the keys are in QWERTY) it expands to "xf yd. ,af". Any idea how to solve this? I'm using version 0.40.0.

Hmm this seems very strange. v0.40 is using xlib to determine the key codes for a given character, essentially the same interface GNOME uses. It should therefore be immune to this sort of problem. Are you using Gnome, and if so what keyboard mapping is configured in the keyboard applet?

---

### Post by GregMB on 2008-10-06
> **cdekter said:**
> Hmm this seems very strange. v0.40 is using xlib to determine the key codes for a given character, essentially the same interface GNOME uses. It should therefore be immune to this sort of problem. Are you using Gnome, and if so what keyboard mapping is configured in the keyboard applet?

I'm using GNOME, but I also have KDE installed, on the off chance that it matters. In System -> Preferences -> Keyboard it's set to USA Dvorak. In the little keyboard thing (SCIM), it's set to Dvorak.

---

### Post by gat0r on 2008-10-08
Guys, i've got 

Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008

I've downloaded autokey 0.40.0 and when i run ./aurokey.sh it gives me:

gat0r@dezcom:~/dl/autokey$ sudo ./autokey.sh 
[sudo] password for gat0r: 
Traceback (most recent call last):
  File "autokey.py", line 23, in <module>
    import expansionservice, iomediator
  File "/home/gat0r/dl/autokey/src/lib/expansionservice.py", line 19, in <module>
    import sys, os, os.path, threading, gamin, string, time, ConfigParser, select, re, subprocess
ImportError: No module named gamin
gat0r@dezcom:~/dl/autokey$

Any suggestions?

---

### Post by GregMB on 2008-10-08
> **gat0r said:**
> Guys, i've got 

Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008

I've downloaded autokey 0.40.0 and when i run ./aurokey.sh it gives me:

gat0r@dezcom:~/dl/autokey$ sudo ./autokey.sh 
[sudo] password for gat0r: 
Traceback (most recent call last):
  File "autokey.py", line 23, in <module>
    import expansionservice, iomediator
  File "/home/gat0r/dl/autokey/src/lib/expansionservice.py", line 19, in <module>
    import sys, os, os.path, threading, gamin, string, time, ConfigParser, select, re, subprocess
ImportError: No module named gamin
gat0r@dezcom:~/dl/autokey$

Any suggestions?

Try ```
sudo apt-get install python-gamin
``` And running the program again. It worked for me. Also, I might be wrong, but I don't think you should run autokey as root.

---

### Post by cdekter on 2008-10-09
> **GregMB said:**
> Try ```
sudo apt-get install python-gamin
``` And running the program again. It worked for me. Also, I might be wrong, but I don't think you should run autokey as root.

Correct - there is no need to use sudo to run it, it can run with normal user privileges.

---

### Post by jfl on 2008-10-21
I have been running "autokey" for over a month now.
**I am delighted**
No bugs ... yet ( except when I goofed !!!)

This was the last link I needed to get rid of Windoze.

[SIZE="6"]THANKS !!![/SIZE]

---

### Post by cdekter on 2008-10-21
> **jfl said:**
> I have been running "autokey" for over a month now.
**I am delighted**
No bugs ... yet ( except when I goofed !!!)

This was the last link I needed to get rid of Windoze.

[SIZE="6"]THANKS !!![/SIZE]

Nice to hear from a satisfied user :) I am actively working on the next version of Autokey, with proper support for alternate keymaps (on Gnome only). Once that is in completed, there is a new version in the works with dramatically expanded GUI and many new features - think no more manual config file editing.

---

### Post by GregMB on 2008-11-06
> **cdekter said:**
> Hmm this seems very strange. v0.40 is using xlib to determine the key codes for a given character, essentially the same interface GNOME uses. It should therefore be immune to this sort of problem. Are you using Gnome, and if so what keyboard mapping is configured in the keyboard applet?

After upgrading to *Buntu 8.10, it works fine. I don't know what happened, but it works now.

---

### Post by cdekter on 2008-11-06
> **GregMB said:**
> After upgrading to *Buntu 8.10, it works fine. I don't know what happened, but it works now.

That's great news, I'd say something in the X configuration changed in the new version of Ubuntu that fixed the problem. You mention *Buntu, have you tried it in Kubuntu? 

Thanks.

---

### Post by BionicSeahorse on 2008-11-07
Thanks a bunch for such a useful app! I've only been using it for a few hours, but I'm already addicted. :)

Here's a shortcut for creating a standard ActionScript private function with parameters:

```
pvf = private function $(echo $(zenity --title='Public Function Name?' --entry)) $(echo \($(zenity --title='Function Parameters?' --entry)\)):%% {
pvf.immediate = true
```

[SIZE="1"][COLOR="Red"]NOTE: The code above needs to be inside the [abbr] section of  the abbreviations file for it to work.[/COLOR] If you code inside Eclipse, this shortcut will be especially useful, since it will indent and close braces automatically too.[/SIZE]

Hope that helps a fellow AS coder! :)

---

### Post by sonicprogress on 2008-11-07
This program is coming on great.I'm using it at work right now.





A few requests though, starting with a bug :

try adding this to the .abbr.ini

loop me = loop me forever

This really shouldn't be allowed as it can totally screw with your pc. Try it and you'll see what I mean.





**1.** I found this out when I wanted to be able to have a string appear

i.e. "tail -f" = "tail -f /var/log/randomlogfile.log"

Please can you make it possible to add strings like this. It would make autokey 100x better!





**2.** Also I have found that some of the corrections that are made in the terminal are just downright annoying.

for eg. If I have i = I added to .abbr.ini and then in terminal I type
cd /home/i/ it renames it to /home/I/ which is really annoying.

Adding strings would help with this too as then I could have "i " = "I" instead.

Ideally I'd like autokey to be able to detect the window that has focus and then activate a set of abbreviations specifically for that process. So, terminal has its own abbreviations independent of gedit for example. This could be set up fairly easily within the .abbr.ini though I am unsure as to how this would be implemented.





**3.** This is a minor thing, but instead of right clicking and clicking on 'Edit abbreviations file' it would be nice if instead a little box came up asking me for an abbreviation to add. If you had per process abbreviations, it could also let you know which software your adding the abbreviation for.

This software is absolutely brilliant by the way.I hope you know that. :KS

---

### Post by cdekter on 2008-11-07
@sonicprogress:

Thanks very much for your bug reports and suggestions. Here's my response:

1. Not quite sure why this is happening - there is some code already in place to prevent it, so I'll have to look into it. 

2. You can already achieve this in the current version of the app. For example, if you only want 'i' replaced with I when it is typed as a word, you can use the following config in abbr.ini:

i = I
i.wordchars = [^ \n]

What this means is that the replacement of 'i' with 'I' will only occur when it is preceded by a line break or a space, as it would be if used in a sentence/document/etc. This way, when you're typing a path in your terminal, it won't be replaced. Try it and see how you go :)

3. The next major upgrade to Autokey will have a full featured GUI for managing abbreviations, which will very much address this suggestion :)

Cheers

---

### Post by sonicprogress on 2008-11-08
> **cdekter said:**
> @sonicprogress:

i = I
i.wordchars = [^ \n]

What this means is that the replacement of 'i' with 'I' will only occur when it is preceded by a line break or a space, as it would be if used in a sentence/document/etc. This way, when you're typing a path in your terminal, it won't be replaced. Try it and see how you go :)


Thanks, this works perfectly. is the wordchars part of that line from python?

Is there any way I can use something similar so that I can have :
```

tail -f = tail -f /var/log/somelog.log
```

I know that I could just create a command as say :

```
readlog = tail -f /var/log/somelog.log
```

However, really what I am seeing is the potential here for not just autocompletion/word correction, but also full sentence prediction. This is really what I envisioned as ideas in my head a few years ago.

I can understand that you don't want to be going down the road of advanced features just yet, but this is something I'm very interested in indeed. I already have plenty of ideas about how to go about it too.

i.e. a piece of software that makes the keyboard obsolete. I see it as the final piece of the puzzle before all the other technologies out there (voice recognition, speech recognition , semantic web search, compiz type desktops, mobile interfaces....) can all begin to merge together.
You guys could well be writing the very piece of software that allows this to happen. Food for thought I think.

> **cdekter said:**
> 
3. The next major upgrade to Autokey will have a full featured GUI for managing abbreviations, which will very much address this suggestion :)
Cheers

Are there any plans to make it so that this gui can be shown/hidden with hotkeys? That way I could get rid of the tray icon all together (I like openbox :D).

---

### Post by wordmagic on 2008-11-15
I just found this thread, is it easy to import a list of mulitlingual autocorrect entries to this program (mainly English and Greek)? Will expansion work OK for Greek too?

---

### Post by cdekter on 2008-11-15
> **wordmagic said:**
> I just found this thread, is it easy to import a list of mulitlingual autocorrect entries to this program (mainly English and Greek)? Will expansion work OK for Greek too?

There is no import feature as such, but the configuration file is plain text so it should be relatively straight forward to get the info in there, depending on where you're importing it from. 

In terms of language support, full Unicode is enabled in Autokey. In theory, it should be able to output any expansion that you could also type on your keyboard, i.e., it can send any characters that are mapped to a key on your keyboard (including ones that are accessed by pressing shift/alt-gr/etc). Alt-gr support is broken in the current version, but a patch will be out soon. I'd be interested in any feedback you can give if you do try Autokey out.

---

### Post by wordmagic on 2008-11-15
Thanks for your reply, yes, I will report back once i test it. "Importing" was the wrong term used, I meant "using" (since I can easily export in two column format from other applications, replace tab with "=" and that would be it as far as I can see).

---

### Post by wordmagic on 2008-11-15
Just installed it and when I try to run it I get:

Waring! Stale lockfile; It looks like hotstring.py is already running, are you sure it isn't already active?

---

### Post by cdekter on 2008-11-15
> **wordmagic said:**
> Just installed it and when I try to run it I get:

Waring! Stale lockfile; It looks like hotstring.py is already running, are you sure it isn't already active?

Something has gone wrong with the sourceforge page and it is presenting the old version for download. I'll try to get it fixed, in the mean time follow this link to download the correct version:

[http://sourceforge.net/project/showfiles.php?group_id=216191&package_id=261010&release_id=624670](http://sourceforge.net/project/showfiles.php?group_id=216191&package_id=261010&release_id=624670)

---

### Post by wordmagic on 2008-11-15
Downloaded and uncompressed. How do I install it? Do I have to uninstal previous version?

---

### Post by cdekter on 2008-11-15
> **wordmagic said:**
> Downloaded and uncompressed. How do I install it? Do I have to uninstal previous version?

Yes, please remove the old version. The new version requires no installation as such, you simply start it using the autokey.sh script provided.

---

### Post by cdekter on 2008-11-15
I have uploaded a new release to the SourceForge page: v0.40.1. The following fixes are included:

- Removed references to incomplete ATSPI interface (this will probably not be implemented, at least at this stage).
- Added experimental fix for keyboard layouts that use right Alt as Alt-Gr
- Fixed startup script so that it can be run from anywhere, e.g. when running it from a GNOME .desktop shortcut.

---

### Post by wordmagic on 2008-11-16
I am not sure where the old version was installed (Not in applications ->Add/Remove / I can see it as an option though in Applications-> Accessories). I can only see an /usr/bin/autokey.py apart from the latest download in my home folder (see files in attachment).

How do I remove it and in which folder do I paste the new one? Sorry for the inane questions...

I tried to run it from Home folder where I downloaded it by double-clicking autokey.sh but nothing happened and when I typed abbreviations none worked. Is there some sort of indication it is running?

---

### Post by cdekter on 2008-11-17
First, to remove the old version:

System -> Administration -> Synaptic

Search for Autokey, and remove any packages found.

Next create an Autokey folder under your /home/username folder, and extract the new version there.

To run it, press Alt+F2 to open the run dialog, and type in:

/home/username/autokey/autokey.sh

A new icon should appear in the system tray - this indicates that Autokey is running.

---

### Post by wordmagic on 2008-11-17
Thank you, I followed exactly your steps. Uninstalled and run:

/home/spiros/autokey-0.40.1/autokey.sh

Still, nothing appeared on the desktop.

By the way, I can still see old version in sourceforge:
[http://sourceforge.net/project/showfiles.php?group_id=216191&package_id=261010&release_id=624670](http://sourceforge.net/project/showfiles.php?group_id=216191&package_id=261010&release_id=624670)
autokey-0.40.0.tar.gz

---

### Post by cdekter on 2008-11-17
> **wordmagic said:**
> Thank you, I followed exactly your steps. Uninstalled and run:

/home/spiros/autokey-0.40.1/autokey.sh

Still, nothing appeared on the desktop.

By the way, I can still see old version in sourceforge:
[http://sourceforge.net/project/showfiles.php?group_id=216191&package_id=261010&release_id=624670](http://sourceforge.net/project/showfiles.php?group_id=216191&package_id=261010&release_id=624670)
autokey-0.40.0.tar.gz

Can you please open a terminal, run the same command there, and post the output.

To get the newer version off SourceForge, please navigate around the site - all versions are available, you just need to go to the right page to get the latest version.

---

### Post by wordmagic on 2008-11-17
File "autokey.py", line 23, in <module>
    import expansionservice, iomediator
  File "/home/spiros/autokey-0.40.1/src/lib/expansionservice.py", line 19, in <module>
    import sys, os, os.path, threading, gamin, string, time, ConfigParser, select, re, subprocess
ImportError: No module named gamin
spiros@spiros-desktop:~$

---

### Post by wordmagic on 2008-11-17
I just ran the gamin command further up this thread and it produced the icon and this:
```

spiros@spiros-desktop:~$ /home/spiros/autokey-0.40.1/autokey.sh
{' ': 65, 'alt_gr': 113, 'ctrl': 37, '\t': 23, 'shift': 50, '\n': 36, 'up': 111, 'capslock': 66, 'backspace': 22, 'alt': 64, 'super': 133, 'left': 113
```}

I tested with btw and it works! Is there a way so that it starts automatically when system boots? 

Now I tested with Greek words but it does not work:

&#960;&#947; = &#960;&#961;&#940;&#947;&#956;&#945;
&#960;&#947;&#964; = &#960;&#961;&#940;&#947;&#956;&#945;&#964;&#945;
` = &#949;&#943;&#957;&#945;&#953;
~ = &#954;&#945;&#953;

Also, when I type Greek characters that correspond to the same keys, Greek characters are expanded:

&#946;&#964;&#962; (the Greek characters from keys btw) becomes &#946;&#965; &#964;&#951;&#949; &#962;&#945;&#965;! This should not happen...

---

### Post by cdekter on 2008-11-17
> **wordmagic said:**
> I just ran the gamin command further up this thread and it produced the icon and this:
```

spiros@spiros-desktop:~$ /home/spiros/autokey-0.40.1/autokey.sh
{' ': 65, 'alt_gr': 113, 'ctrl': 37, '\t': 23, 'shift': 50, '\n': 36, 'up': 111, 'capslock': 66, 'backspace': 22, 'alt': 64, 'super': 133, 'left': 113
```}

I tested with btw and it works! Is there a way so that it starts automatically when system boots? 

Now I tested with Greek words but it does not work:

&#960;&#947; = &#960;&#961;&#940;&#947;&#956;&#945;
&#960;&#947;&#964; = &#960;&#961;&#940;&#947;&#956;&#945;&#964;&#945;
` = &#949;&#943;&#957;&#945;&#953;
~ = &#954;&#945;&#953;

Also, when I type Greek characters that correspond to the same keys, Greek characters are expanded:

&#946;&#964;&#962; (the Greek characters from keys btw) becomes &#946;&#965; &#964;&#951;&#949; &#962;&#945;&#965;! This should not happen...

I'm going to need a lot more information about how your keyboard works before I can help you. Please give me everything you can think of.

---

### Post by wordmagic on 2008-11-17
I am not sure what exactly you need.
This is what a Greek keyboard layout looks like:

[http://en.wikipedia.org/wiki/Keyboard_layout#Greek](http://en.wikipedia.org/wiki/Keyboard_layout#Greek)

It seems that your script is not based on characters, but on **keys**, so this is a major issue for multilingualism.

---

### Post by cdekter on 2008-11-17
> **wordmagic said:**
> I am not sure what exactly you need.
This is what a Greek keyboard layout looks like:

[http://en.wikipedia.org/wiki/Keyboard_layout#Greek](http://en.wikipedia.org/wiki/Keyboard_layout#Greek)

It seems that your script is not based on characters, but on **keys**, so this is a major issue for multilingualism.

That's correct - as I originally told you when you asked me if Greek keyboard layout would work. In order to make Autokey compatible with both GNOME and KDE, it has to communicate directly with the X server with regards to keyboard events. Since the X server knows only about key codes, not characters, Autokey can only send and receive characters that are associated directly with keys on your keyboard.

In your situation it seems to me that your X keyboard layout is not the same as your GNOME layout set in SCIM/keyboard settings. This is only a guess - unfortunately since I don't use an alternate layout myself, I can't offer you much help in troubleshooting.

---

### Post by wordmagic on 2008-11-17
Well, I use Ubuntu 8.0.10.

In my opinion, it should not be based on key events but on characters (or somehow "convert" the key events if alternate keyboard layout is used); but only you know if this is feasible or how hard it is to implement. It seems to me though that it is the only way to make it truly multilingual and benefit loads of people.

---

### Post by cdekter on 2008-11-17
> **wordmagic said:**
> Well, I use Ubuntu 8.0.10.

In my opinion, it should not be based on key events but on characters (or somehow "convert" the key events if alternate keyboard layout is used); but only you know if this is feasible or how hard it is to implement. It seems to me though that it is the only way to make it truly multilingual and benefit loads of people.

You are of course correct - unfortunately the method that Autokey is using is currently the only one that works (at least some of the time), at least until I can find some working code examples for ATSPI.

---

### Post by BionicSeahorse on 2008-11-19
Hey peabody & cdekter,

Could you please explain what the settings inside the [default] section mean (inside the abbr.ini file)?
> 
[defaults]
omittrigger = false
wordchars = [\w~]
matchcase = false
ignorecase = false
backspace = true
immediate = false
triggerinside = false

Thanks again for such a useful app!

---

### Post by cdekter on 2008-11-19
The options do the following:

omittrigger: When replacing the abbreviation, omit the character that triggered replacement, e.g. if you type brb<space>, it will be replace as be right back, and the space will be discarded. This option only has an affect if immediate = false

wordchars: a regular expression telling Autokey which characters to treat as being part of a word. Refer to the Python regular expression documentation for more information on expressions. This option works in conjunction with the triggerinside option.

matchcase: if set to true, will match the case of the replacement with the case of the abbreviation as typed. For example, if you typed Brb, you'd get Be right back. For this to work, ignorecase must be set to true.

ignorecase: if set to false, the case of the abbreviation type must match the case in the configuration file exactly, otherwise the abbreviation will not trigger.

backspace: if set to false, Autokey won't remove the typed abbreviation before sending its replacement. E.g. in the case of brb, you'd end up with "brb be right back".

immediate: if set to true, a non-word character (as defined in the wordchars option) is not required to trigger the abbreviation. 

triggerinside: if set to true, will trigger the abbreviation when it is typed as part of a word (as defined in the wordchars option). E.g. if you typed mebrb, you'd end up with mebe right back.

Each of these options can also be applied to individual abbreviations. For example, if you wanted to set triggerinside to true only for the brb abbreviation, you'd do:

brb.triggerinside = true

Hope this helps.

---

### Post by Sanjay on 2008-11-24
I cannot express how much I *LOVE* this. 

Before this I was using snippits, which is ok but not perfect. 

I'm loving this, first off written in python, which I like better and the source makes a lot of sense to me, also noticeably faster than ruby which is what snippits is written in. 

What I wanted to do was have AutoKey replace mis-spelled words for me on the fly. When I have some time (Have a tonne of work on and preparing for my upcoming exams, i'm sure you know what this is like from reading your posts peabody!) I want to use Gnu-Aspell to implement this. 

BUT! For now, I have a rough and dirty implementation, basically I took this list:

[http://www.autohotkey.com/download/AutoCorrect.ahk](http://www.autohotkey.com/download/AutoCorrect.ahk)

Which is for autohotkey, and ran it through a little bit of python I wrote so that the abbreviation syntax is formatted for AutoKey.

What you get is this: 

[http://pastebin.com/f4eac9450](http://pastebin.com/f4eac9450)

So, take the contents of that pastebin, 

Copy&paste that into your abbr.ini under the [abbr] section.

Be warned that when you hit save your CPU will churn through that massive list for a little while at full tilt while it updates its list.

You now have typo autocorrection! :)

Once it is loaded I was surprised at how fast it actually is, pretty much instant on my very underpowered laptop. To the point where this is actually a very viable solution. 

Right now I am one very happy camper! 

Cheers, Sanjay

---

### Post by cdekter on 2008-11-24
@Sanjay

I'm thrilled that you find Autokey so useful. Thank you for your comments :)

I have previously attempted something similar to what you've done, but using a list of common misspellings in English from Wikipedia. I also hit the issue of long load times. Unfortunately this would make Autokey take many seconds to load each time at boot as well.

With this in mind, I've created a new release of Autokey - 0.40.2. You can download it from SourceForge download page. The configuration file loading speed has been massively increased - it's now about 200 times faster. I added the list of autocorrect entries you created to my config file, and Autokey now starts in much less than a second on my machine. 

I look forward to hearing more from you on implementing autocorrect via Aspell - I can see a few potential problems with it, but in fact the 0.40 series of Autokey is about to be superceded (in a few months anyway), and the new version should enable these issues to be resolved.

---

### Post by Sanjay on 2008-11-25
Awesome going on the optimisation, makes adding correction rules so much less painful! :KS

I've sat and thought a little on the aspell etc front. I have come to the conclusion that perhaps spellchecking EVERY word by default is going to be a poor idea. For example if that kind of behaviour was implemented then what would happen when you typed "facebook" etc? These arent dictionary words but are typed intentionally.

If I were going to implement something like this it would probably use python-enchant, which is a rather lovely little spellchecking library for python. It would add another dependency to AutoKey however.

At the moment I am running snippits AND AutoKey simultaneously, snippits runs on a hotkey activation system. So you type a word, leave the cursor just after the word you want and hit the hotkey. Snippits then looks through your rules, if your word matches a pattern in there it replaces it with its corresponding pattern. But (And here's the part I find REALLY handy) if it cannot find the pattern it runs the word passed to it through a spellchecker (Raspell, ruby bindings for aspell) , if not correctly spelled it replaces it with the most probable suggestion.

I propose: Add a hotkey to AutoKey to implement this feature, so it behaves such that you type a word:

sugestion |

(Pipe indicates position of cursor)

Now I can see that this is spelled wrongly, and this word was not in my abbr.ini for a correction so it remains wrongly spelled, but going back and correcting manually is tedious, so instead I hit my AutoKey hotkey (User defined) AutoKey then takes the word and runs it through python-enchant

suggestionsList = enchant.suggest("sugestion") 

This return a list of suggestions, 
suggestionsList = ['suggestion', 'suggestions', 'digestion', 'question', 'succession', 'suggesting', "suggestion's", 'section', 'suction']

Lists of suggestions returned by enchant are ordered in probability, first most likely, so we grab 

suggestionList[0] 

and write it out replacing the input word. 

suggestion |

I realise this is all MUCH easier said than done, if I had time I would read all the source for AutoKey and start on this myself. However as it stands I have spent much more time on this post than I should. I'm meant to be doing the sleeping-barber concurrency problem in poxy bloody java right now. Ahh well. :lolflag:   

Again, thanks for the optimisation, It makes me happy!

Sanjay.

---

### Post by cdekter on 2008-12-03
For anyone still monitoring this thread - I've just released a new version (0.40.3). It includes the following fixes and improvements:

[LIST]
[*]Added statistic tracking the number of keystroke saved, displayed in the About dialog (thanks to Dan McCombs for this one)
[*]Notify popups are now always shown, even if the tray icon is hidden.
[*]The order of items in the configuration file is now maintained, as well as any comments in the file (thanks to Dan McCombs for this one)
[*]Multiline abbreviations with blank lines are now possible (thanks to Dan McCombs for this one)
[*]Improved accuracy of abbreviation detection for extremely fast typists
[*]Added fix to prevent recursive abbreviations from putting the app in an infinite loop
[/LIST]

This release adds a new dependency - on Debian/Ubuntu/etc the package is called python-configobj. 

Any comments/bugreports/etc welcome :)

---

### Post by nhasian on 2008-12-04
i'm still monitoring this thread.  what is the .a for?  would you like me to make a wiki page for autokey?

---

### Post by cdekter on 2008-12-04
> **nhasian said:**
> i'm still monitoring this thread.  what is the .a for?  would you like me to make a wiki page for autokey?

The .a is because I fixed a small bug after releasing 0.40.3 which didn't really warrant bumping the version number, so I just appended an a to it. This is the version you should download.

Any contributions are welcome - if you like I can give you access to the project's wiki on SourceForge.

---

### Post by sonicprogress on 2008-12-08
> **cdekter said:**
> 
Any contributions are welcome - if you like I can give you access to the project's wiki on SourceForge.

Any chance I could get in on that?

I use autokey all the time now, and I'd like to be able to contribute to the project.

---

### Post by imnotashinobi on 2008-12-08
hello, I'm still monitoring this thread!

I was wondering, are modifier keys and such (shift, ctrl, alt, caps lock, down, right, etc.) yet implemented? And, if so, how do they looks like in the abbr.ini file? I would like to know this for the following reasons:

1. quite oftenly, I accidentally hit 'up' while holding 'shift', resulting in the highlighting of everything before the cursor on a given line. I then proceed to press another character I may want capitalised and end up with just that character and any following characters.
example: 'I'm using Ubuntu!' may be reduced to '!', because I'm accidently holding 'shift'+'up'+'1'.

2. I only find 'caps lock' useful SOME of the times. so I'd like to be able to have a key combination [example: 'alt'+'caps lock' to activate 'caps lock'] control its activation rather than a single button. 'caps lock' may then be turned into an extra 'alt' key or something.

3. automatic capitilization of letters proceeding a period and a space [or two].
example: "...corn. they plant..." -becomes- "...corn. They plant..."

If any of these features may be implemented in future releases, I will be quite happy ^_^!

I'm using 0.40.3.a on intrepid 32-bit. The release before didn't work for me... Y_Y Probably because of some unknown dependency missing.

this project is developing quite nicely.

cheers!

---

### Post by cdekter on 2008-12-08
> **sonicprogress said:**
> Any chance I could get in on that?

I use autokey all the time now, and I'd like to be able to contribute to the project.

Great to hear from you :) I'll give you access the first chance I get.

---

### Post by cdekter on 2008-12-08
> **imnotashinobi said:**
> hello, I'm still monitoring this thread!

I was wondering, are modifier keys and such (shift, ctrl, alt, caps lock, down, right, etc.) yet implemented? And, if so, how do they looks like in the abbr.ini file? I would like to know this for the following reasons:
*snip*

If any of these features may be implemented in future releases, I will be quite happy ^_^!

cheers!

Thanks for your comments. The version of AutoKey you are using (which is the current version) does not support sending modifier keys as part of an expansion. However, the new version due out in a few months will support this (along with many other new features). 

I did not have any plans to implement something like the autocorrect you have suggested, however it would be relatively simple to do, so I'll consider adding it as a feature that may be optionally activated. Thanks for suggesting it :)

Cheers

---

### Post by imnotashinobi on 2008-12-12
Glad I could be of help to this wonderful app. With all the short hand and commonly misspelled words, I'm surprised this thing isnt more popular. I can't wait to see what features will be implemented in future releases.

!!!

---

### Post by cdekter on 2008-12-12
I thought interested people might appreciate a look at the new version. It should be ready for beta in about a month's time.

To start with, here's a screenshot of the new configuration editor:

[[IMG]http://img208.imageshack.us/img208/2943/screenshotautokeyconfigdg3.th.png[/IMG]](http://img208.imageshack.us/my.php?image=screenshotautokeyconfigdg3.png)

It still needs tweaking here and there to get the layout really nice, but all the functionality is there. Some features visible in this screenshot:

[LIST]
[*]Phrases can be collected together in folders (and folders can have sub-folders as well)
[*]You can now have hotkeys as well as abbreviations to trigger a phrase, and a single phrase can have both a hotkey and an abbreviation.
[*]Window filter - you can use a regular expression to filter on the window title to make the phrase available only in certain applications
[*]Phrases, and entire folders of phrases can be made visible in the tray menu, allowing you to select them without having to assign a hotkey or abbreviations.
[*]Predictive mode - phrases can be triggered by typing the first few words (configurable).
[/LIST]

These are just some of the highlights, there are many other enhancements and improvements - stay tuned.

---

### Post by imnotashinobi on 2008-12-14
... Wow... O_O

you, sir, take adding features quite seriously, don't you? lol; this project may very well rival/surpass autohotkey.

---

### Post by Spitphire on 2008-12-14
I'm anxious to try this program, unfortuantely I know zero about python.. I'm getting the following error.  I imagine I'm missing a package.. any help?

```

am@msi:~/Desktop$ ./autokey.sh
Traceback (most recent call last):
  File "autokey.py", line 23, in <module>
    from configobj import ConfigObj
ImportError: No module named configobj

```

---

### Post by Spitphire on 2008-12-14
> **Spitphire said:**
> I'm anxious to try this program, unfortuantely I know zero about python.. I'm getting the following error.  I imagine I'm missing a package.. any help?

```

am@msi:~/Desktop$ ./autokey.sh
Traceback (most recent call last):
  File "autokey.py", line 23, in <module>
    from configobj import ConfigObj
ImportError: No module named configobj

```

Fixed my own problem, for anyone else here's what I did:

```

sudo apt-get install python-ConfigObj python-Xlib

```

-spit

---

### Post by cdekter on 2008-12-14
> **Spitphire said:**
> I'm anxious to try this program, unfortuantely I know zero about python.. I'm getting the following error.  I imagine I'm missing a package.. any help?

```

am@msi:~/Desktop$ ./autokey.sh
Traceback (most recent call last):
  File "autokey.py", line 23, in <module>
    from configobj import ConfigObj
ImportError: No module named configobj

```

You need to install an extra package to resolve this. On Ubuntu/Debian it's called python-configobj.

EDIT: I see you already found the solution. The next version of AutoKey will provide a .deb so dependencies will be automatically installed - problem solved.

---

### Post by sonicprogress on 2008-12-16
A few more thoughts for you!

Please can the abbr.ini included in the install be renamed to abbr_default.ini?

Last time I installed the update my abbr.ini was overwritten with the default.

Ideally, I'd like to see the software search for the file in a specified location (stated through the gui of course!) and if it fails to find the file to revert to the default instead of bombing out.

Also, I am seeing the same issues as some of the other uses where the abbreviations don't seem to always be activated (using wmii window manager here). Reading what you've said it doesn't seem to happen in Gnome - Should the window manager make a difference?

It seems a bit hit and miss for me sometimes, almost as if there is a bit of a lag between recognising the key combinations and the actual rewrite of the abbreviation. Either it works fine, or it doesn't at all.

The last update seemed to alleviate the affects slightly which is why I think it is some kind of performance issue in the code somewhere.

---

### Post by cdekter on 2008-12-16
> **sonicprogress said:**
> A few more thoughts for you!

Please can the abbr.ini included in the install be renamed to abbr_default.ini?

Last time I installed the update my abbr.ini was overwritten with the default.

Ideally, I'd like to see the software search for the file in a specified location (stated through the gui of course!) and if it fails to find the file to revert to the default instead of bombing out.



The abbr.ini file is deprecated in the new version of AutoKey, due out in a few weeks. A binary file will be used to store all settings, and no default file will be included in the release. The first time you run the application, it will create a blank default configuration. So your config will never get overwritten when you upgrade. Also, there will be a function for importing your existing abbreviations from 0.40.x, so that you don't have to recreate them from scratch.

> 

Also, I am seeing the same issues as some of the other uses where the abbreviations don't seem to always be activated (using wmii window manager here). Reading what you've said it doesn't seem to happen in Gnome - Should the window manager make a difference?

It seems a bit hit and miss for me sometimes, almost as if there is a bit of a lag between recognising the key combinations and the actual rewrite of the abbreviation. Either it works fine, or it doesn't at all.

The last update seemed to alleviate the affects slightly which is why I think it is some kind of performance issue in the code somewhere.

The window manager should not make any difference, as AutoKey communicates directly with the X server. If your issue was helped by the latest version, it leads me to suspect that this issue is due to individual typing habits. For example, if you don't cleanly release one key before hitting the next. Since this is a human factor, it's very difficult to debug, as each person is different. 

If you are interested in helping to work on this issue, I can show you how to turn on some debugging output in AutoKey. Also, it would be a good start if you can give me some examples of this issue occurring.

Finally, there are certain actions that will cause AutoKey's input buffer to be cleared. For example, if you type part of an abbreviation, then switch to a different window, then back to the first window, and finish typing the abbreviation, it will not trigger. Any mouse clicks and hot keys (e.g. Ctrl+B) also clear the input buffer.

---

### Post by cdekter on 2008-12-16
If anyone is interested in checking out the new version as it's being developed, you can get it from the SVN repository:

```
svn co https://autokey.svn.sourceforge.net/svnroot/autokey/trunk autokey 
```

One important thing to note is that saving of configuration is not yet implemented (i.e. your settings will be lost when you exit the program). I'll endeavour to put that in tonight.

---

### Post by sonicprogress on 2008-12-18
> **cdekter said:**
> 
The window manager should not make any difference, as AutoKey communicates directly with the X server. If your issue was helped by the latest version, it leads me to suspect that this issue is due to individual typing habits. For example, if you don't cleanly release one key before hitting the next. Since this is a human factor, it's very difficult to debug, as each person is different. 


Aha! This is exactly it. I have the following set up using space bar as the trigger :

h = host
h.wordchars = [^ \n]
w = whois
w.wordchars = [^ \n]

It makes perfect sense that I would hit say the h key and then the space bar in quick succession. I can imagine other people type this way with the space bar too.

I'll download the SVN at some point and see if it goes away.

> **cdekter said:**
> 
If you are interested in helping to work on this issue, I can show you how to turn on some debugging output in AutoKey. Also, it would be a good start if you can give me some examples of this issue occurring.


Sure thing.


Edit :

I have just tried the SVN and I'm getting this...(This is when I carefully type each key)

hosthost 

whoiwhois 

be right bbe right back

---

### Post by cdekter on 2008-12-18
Hmmm... in the latest version (0.40.3a) I put in a fix which in theory should mean you can type as fast as you like and it should not cause any issues. I tested this myself and hitting the two keys as fast as I could after one another, it still worked correctly.

I'll test it using your config and see if I can detect any issues. Mean time, it's possible to get AutoKey to print out the state as its tracking your input - this should give you some clues as to why its not detecting your abbreviations. Just run it from a terminal window (or run it and pipe the output to a file like so: ./autokey.sh > log.out 

After each key press it will print out the current state of input tracking.

---

### Post by sonicprogress on 2008-12-18
> **cdekter said:**
> Hmmm... in the latest version (0.40.3a) I put in a fix which in theory should mean you can type as fast as you like and it should not cause any issues. I tested this myself and hitting the two keys as fast as I could after one another, it still worked correctly.

I'll test it using your config and see if I can detect any issues. Mean time, it's possible to get AutoKey to print out the state as its tracking your input - this should give you some clues as to why its not detecting your abbreviations. Just run it from a terminal window (or run it and pipe the output to a file like so: ./autokey.sh > log.out 

After each key press it will print out the current state of input tracking.

I worked out what it was... I somehow managed to run two instances! There is going to need to be some code added to prevent this - Especially if going down the GUI route.

No further performance issues since using the SVN. I'll keep testing and let you know.

./autokey.sh gives me a permission denied error by the way. I have to run it with sh autokey.sh.

sh autokey.sh > log.out doesn't seem to output to the file.

I must say its a real shame that there is no longer an abbr.ini to edit directly, though I expect once the SVN version saves the changes that I won't be so bothered. :guitar:

---

### Post by cdekter on 2008-12-18
> **sonicprogress said:**
> I worked out what it was... I somehow managed to run two instances! There is going to need to be some code added to prevent this - Especially if going down the GUI route.


Good point - I'll add a TODO for the new version.

> 
./autokey.sh gives me a permission denied error by the way. I have to run it with sh autokey.sh.

sh autokey.sh > log.out doesn't seem to output to the file.



It sounds like you need to add execute permissions to the autokey.sh script. Improved error reporting and logging is on my todo list for the new version as well...

> 
I must say its a real shame that there is no longer an abbr.ini to edit directly, though I expect once the SVN version saves the changes that I won't be so bothered. :guitar:

Indeed... unfortunately the new version with its many different options and ability to organise phrases into folder and subfolders meant that the configuration file would have been far too complex and required really rather a lot of code to parse it. Persisting using serialised objects is the more 'modern' and indeed the more Pythonic approach.

I should have saving finished in the next day or so and I'll post here when I've committed the update to SVN.

---

### Post by cdekter on 2008-12-21
I've committed a new version to SVN which adds the necessary code to save the configuration. Also implemented a check to ensure only one instance of the program can run.

---

### Post by sonicprogress on 2008-12-22
carriage returns (\n) don't appear to work anymore in the svn. Is this yet to be coded back in?

---

### Post by cdekter on 2008-12-22
> **sonicprogress said:**
> carriage returns (\n) don't appear to work anymore in the svn. Is this yet to be coded back in?

Can you please elaborate on what you mean by 'don't work'? As far as I can tell they are working correctly...

---

### Post by sonicprogress on 2008-12-24
> **cdekter said:**
> Can you please elaborate on what you mean by 'don't work'? As far as I can tell they are working correctly...

Taken from my old abbr.ini :

errlog.immediate=true
errlog = chroot /usr/fs\n cd /var/log\ntail -n1000 error_log\n

In the svn, instead of executing several commands (emulating the enter key via \n) this abbreviation now just echo's out the entire line.

i.e. chroot /usr/fs\n cd /var/log\ntail -n1000 error_log\n


More seriously, I have also noticed that the GUI no longer appears when I import my abbreviations, press save, file/quit and then run the autokey again. The abbrevations still run fine despite there being no GUI.

I can restore the GUI by deleting abbr.bin.

---

### Post by cdekter on 2008-12-24
> **sonicprogress said:**
> Taken from my old abbr.ini :

errlog.immediate=true
errlog = chroot /usr/fs\n cd /var/log\ntail -n1000 error_log\n

In the svn, instead of executing several commands (emulating the enter key via \n) this abbreviation now just echo's out the entire line.

i.e. chroot /usr/fs\n cd /var/log\ntail -n1000 error_log\n



This could possibly be a bug in the importer, should be simple to fix. In the mean time, you can work around it by editing the above phrase in the GUI, and replacing the occurrences of \n with actual line breaks (i.e. by pressing enter). AutoKey will send these as Enter presses so it will still work correctly.

> 

More seriously, I have also noticed that the GUI no longer appears when I import my abbreviations, press save, file/quit and then run the autokey again. The abbrevations still run fine despite there being no GUI.

I can restore the GUI by deleting abbr.bin.

That is how it was designed - the configuration window is shown on the first run, thereafter it can be shown by right clicking on the tray icon and selecting Configure. So, if you're running a DE with no tray area, you're kinda stuck for the moment. I am planning to implement a configurable hotkey for showing the configuration window. This way you don't have the window showing each time you boot up if you have AutoKey running on startup.

---

### Post by cdekter on 2009-01-09
Just in case anyone is still monitoring this thread - I'd like to preclude anyone having problems with AutoKey on KDE4 from having to post anything about this... There is currently a bug in QT4 which prevents keyboard events from being processed in the correct order if they are sent at high speed (like AutoKey does) this means that phrases come out garbled.

The details can be found here: 
 
[http://trolltech.com/developer/task-tracker/index_html?method=entry&id=212067](http://trolltech.com/developer/task-tracker/index_html?method=entry&id=212067) 
 
This launchpad bug looks similar: 
 
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/289907](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/289907) 

Hopefully it might be fixed in Jaunty. It would be helpful if I could have an indication of how many people are using AutoKey on KDE4, as I have developed a workaround for this problem. It's not ideal, but it will at least allow you to use AutoKey. Anyone who is interested in this workaround should PM me.

---

### Post by sonicprogress on 2009-02-05
Hi there.

I seem to be stuck on the SVN revision 36.

the latest SVN (version 50) is unuseable for me. When I run it the default or imported abbreviations don't do anything. If I run autokey, sometimes I get this error:


Exception in thread XLibInterface-thread:
Traceback (most recent call last):
  File "/usr/lib/python2.5/threading.py", line 486, in __bootstrap_inner
    self.run()
  File "/home/tjefferies/svn/autokey/src/lib/interface.py", line 201, in run
    self.record_dpy.record_enable_context(self.ctx, self.__processEvent)
  File "/var/lib/python-support/python2.5/Xlib/ext/record.py", line 240, in enable_context
    context = context)
  File "/var/lib/python-support/python2.5/Xlib/ext/record.py", line 217, in __init__
    apply(rq.ReplyRequest.__init__, (self, ) + args, keys)
  File "/var/lib/python-support/python2.5/Xlib/protocol/rq.py", line 1430, in __init__
    self.reply()
  File "/var/lib/python-support/python2.5/Xlib/protocol/rq.py", line 1442, in reply
    self._display.send_and_recv(request = self._serial)
  File "/var/lib/python-support/python2.5/Xlib/protocol/display.py", line 548, in send_and_recv
    gotreq = self.parse_response(request)
  File "/var/lib/python-support/python2.5/Xlib/protocol/display.py", line 635, in parse_response
    gotreq = self.parse_request_response(request) or gotreq
  File "/var/lib/python-support/python2.5/Xlib/protocol/display.py", line 721, in parse_request_response
    req._parse_response(self.data_recv[:self.request_length])
  File "/var/lib/python-support/python2.5/Xlib/ext/record.py", line 221, in _parse_response
    self._callback(r)
  File "/home/tjefferies/svn/autokey/src/lib/interface.py", line 297, in __processEvent
    self.__handleKeyRelease(event.detail)
  File "/home/tjefferies/svn/autokey/src/lib/interface.py", line 312, in __handleKeyRelease
    self.lock.release()
  File "/usr/lib/python2.5/threading.py", line 116, in release
    raise RuntimeError("cannot release un-aquired lock")
RuntimeError: cannot release un-aquired lock


The other thing that I am having problems with is dvorak.

I have been using the following commands to swap keyboard configs:

setxkbmap gb
setxkbmap dvorak

unfortunately though, autokey doesn't detect the change. I have read previously that this is difficult to do. Is there any way I can tell autokey to switch to dvorak (preferably without having to restart it?

Thankyou!

---

### Post by cdekter on 2009-02-05
The locking error is very strange - I've never seen this before. The lock being used there is a re-entrant lock and should by definition be immune to this kind of problem. You haven't made any changes to the code? 

Can you please post the following:

Python version
python-xlib version
Distro and distro version

Also, the latest revision is 52 - please update to it and see if that helps. I can't imagine it will though, as no changes have been made to the interface code.

Regarding the keyboard mapping issue - I will not be able to fix that for some time. AutoKey uses the RECORD X extension to receive events, and as far as I'm aware this extension can't receive the MappingNotify events issued when you run setxkbmap. I am looking at replacing RECORD with a proper X event interface (as some distros have disabled the RECORD extension, e.g. Fedora), which would enable me to fix this problem. This is still a while off however.

---

### Post by cdekter on 2009-02-05
I've committed version 53 to SVN which should fix the RuntimeError you've been experiencing.

---

### Post by cdekter on 2009-02-06
AutoKey v0.51.0 has been uploaded to the SourceForge download page, with many improvements, bug fixes and new features. Refer to the change log on the download page for more info.

[https://sourceforge.net/project/platformdownload.php?group_id=216191&sel_platform=6566](https://sourceforge.net/project/platformdownload.php?group_id=216191&sel_platform=6566)

---

### Post by sonicprogress on 2009-02-06
> **cdekter said:**
> The locking error is very strange - I've never seen this before. The lock being used there is a re-entrant lock and should by definition be immune to this kind of problem. You haven't made any changes to the code? 

Can you please post the following:

Python version
python-xlib version
Distro and distro version

Also, the latest revision is 52 - please update to it and see if that helps. I can't imagine it will though, as no changes have been made to the interface code.

Regarding the keyboard mapping issue - I will not be able to fix that for some time. AutoKey uses the RECORD X extension to receive events, and as far as I'm aware this extension can't receive the MappingNotify events issued when you run setxkbmap. I am looking at replacing RECORD with a proper X event interface (as some distros have disabled the RECORD extension, e.g. Fedora), which would enable me to fix this problem. This is still a while off however.

I removed all the files and reinstalled from the SVN repository.
I'm not seeing that error now, but autokey is behaving very bizarely. Abbrevations work in firefox but not in any of my uxterm terminals!

I tested Terminator - No problem
Gnome terminal - no problem
uxterm - nope!
lxterm - nope!
xterm - nope!

I've decided to make the move to terminator to get round the problem.

Package: python
Version: 2.5.2-1ubuntu1

Package: python-xlib
Version: 0.14-2

Distributor ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid

2.6.27-7-generic

In regards to key mapping, are you saying that even if I was in a gnome desktop and I chose a different locale that autokey won't work with it?
If I could do it this way, then that wouldn't be the end of the world (just the end of my spare resources - lol).

---

### Post by cdekter on 2009-02-06
> **sonicprogress said:**
> I removed all the files and reinstalled from the SVN repository.
I'm not seeing that error now, but autokey is behaving very bizarely. Abbrevations work in firefox but not in any of my uxterm terminals!

I tested Terminator - No problem
Gnome terminal - no problem
uxterm - nope!
lxterm - nope!
xterm - nope!

I've decided to make the move to terminator to get round the problem.

I've tested this on my own system - unfortunately xterm and its variants don't respond to the X events sent by AutoKey. There is probably nothing that can be done to fix this. I suggest using some other terminal emulator (there are many) which will work, e.g. gnome-terminal, konsole, etc.

> **sonicprogress said:**
> 
In regards to key mapping, are you saying that even if I was in a gnome desktop and I chose a different locale that autokey won't work with it?
If I could do it this way, then that wouldn't be the end of the world (just the end of my spare resources - lol).

No I don't think this will help you either. The xlib library used by AutoKey caches the keyboard mapping information on startup. This is one of the side-effects of having a client-server system like X - things have to be cached on the client side and aren't updated in real-time as a result. A future version of AutoKey will likely fix this problem by handling the MappingNotify events I mentioned earlier.

---

### Post by Mehall on 2009-03-06
is this program still under development?

I'm assuming it is since it was last released tail end of january according to SourceForge, but I like to make sure.

I'm using CrunchBang Linux (essentially ubuntu w/ Openbox and very fast) so I'm going to give it a try and report back any issues.

*off to download it*

---

### Post by Mehall on 2009-03-06
How do you change the global trigger key?

As tab is making it not work in firefox pages for me.

Works fine in the address bar, but not here, meebo, or various other forums.

EDIT: It also works okay ish in Thunderbird, but left some of the trigger phrase in when it shouldn't

---

### Post by cdekter on 2009-03-06
> **Mehall said:**
> is this program still under development?

I'm assuming it is since it was last released tail end of january according to SourceForge, but I like to make sure.

I'm using CrunchBang Linux (essentially ubuntu w/ Openbox and very fast) so I'm going to give it a try and report back any issues.

*off to download it*

It's very much still actively being developed. I'm planning to put out a release in the next two weeks with a few small new features and fixes.

---

### Post by cdekter on 2009-03-06
> **Mehall said:**
> How do you change the global trigger key?

As tab is making it not work in firefox pages for me.

Works fine in the address bar, but not here, meebo, or various other forums.

EDIT: It also works okay ish in Thunderbird, but left some of the trigger phrase in when it shouldn't

There is no global setting for the trigger key, however it can be set on a phrase-by-phrase basis using the Word Characters option under Abbreviation settings. You can choose one of the available options (e.g. Space and Enter Only might be a good option in your case) or you can enter your own regex. Any characters that don't match the regex will be treated as trigger characters.

If you give me some more detail as to what characters you'd like as trigger characters, I can come up with the right regex for you.

---

### Post by Mehall on 2009-03-07
> **cdekter said:**
> There is no global setting for the trigger key, however it can be set on a phrase-by-phrase basis using the Word Characters option under Abbreviation settings. You can choose one of the available options (e.g. Space and Enter Only might be a good option in your case) or you can enter your own regex. Any characters that don't match the regex will be treated as trigger characters.

If you give me some more detail as to what characters you'd like as trigger characters, I can come up with the right regex for you.

Can I make a suggestion?

I know it's your app and you can do what you think is best, but something like how [Texter](http://lifehacker.com/software/texter/lifehacker-code-texter-windows-238306.php) works seems a better implementation to me.

You set up the abbreviations, and there is a global key you can press after entering it, and it also supports scripting like you might wish for.

---

### Post by cdekter on 2009-03-07
Thanks for the suggestion. I had a look, and it seems to me like AutoKey can already do everything that Texter can. It's just a matter of knowing how to configure it - on this front the lack of documentation for AutoKey is a bit of an impediment. As I'm working on this project essentially on my own, working on the code has to take a higher priority than writing manuals, hence why it isn't done yet.

---

### Post by Mehall on 2009-03-08
> **cdekter said:**
> Thanks for the suggestion. I had a look, and it seems to me like AutoKey can already do everything that Texter can. It's just a matter of knowing how to configure it - on this front the lack of documentation for AutoKey is a bit of an impediment. As I'm working on this project essentially on my own, working on the code has to take a higher priority than writing manuals, hence why it isn't done yet.

Fair point.

I am highly interested in using AutoKey more, but ease of use is vital to me, especially when we consider I aim to use a program to ease daily habits, rather than make things complicated.

The main thing I wanted to suggest was, as I said, the global hotkey, eg Tab or space, which would tell the program the phrase you entered had to be substituted. (obviously space and enter might not be good if you have reasonably useufl names, lol, but as pointed otu, tab isn't great either, so maybe  arandom character that ahs low chances of being used like, say, ` ? (though ctrl+` ) would probably work well, and I think I know how to do that, but it irks me to ahve to set each one individually)

---

### Post by cdekter on 2009-03-08
The solution might be to have a way to set a global default trigger character (or in the case of AutoKey, a global default word characters regex). I'll look into this for the next release.

---

### Post by Rob-e on 2009-03-10
wow, nice job on this, I remember using this some time ago before it had a gui, and wow, it's really nice now.

Just 1 question, how can I execute commands from it?  like before you could have $(date) and it would put the date (not the string $(date)), i assume the syntax has changed now

---

### Post by Rob-e on 2009-03-10
> **Rob-e said:**
> wow, nice job on this, I remember using this some time ago before it had a gui, and wow, it's really nice now.

Just 1 question, how can I execute commands from it?  like before you could have $(date) and it would put the date (not the string $(date)), i assume the syntax has changed now

found it: File > insert macro :D

---

### Post by Rob-e on 2009-03-10
Ok, sorry for the triple post but I've done something amazing

I made a calculator.

make a new phrase and put this in the contents box:
$(exec output=true&command=python -c "print $(xclip -o)")

then map it to a hotkey (i used alt-c)
then highlight a math problem (like 5+5)
and press the hotkey
BAM! it replaces it with the solution

in case you dont want to dissect the command it just uses xclip to get the highlighted string, then runs the highlighted text in python and prints it out

this could be destructive if you start highlighting python commands though so be careful :D

---

### Post by cdekter on 2009-03-10
> **Rob-e said:**
> Just 1 question, how can I execute commands from it?  like before you could have $(date) and it would put the date (not the string $(date)), i assume the syntax has changed now

You can use the Execute Command macro function. With the appropriate phrase selected, go to File -> Insert Macro -> Execute a command. A dialog then appears asking you for the command to be run.

---

### Post by icheyne on 2009-03-19
Thanks so much for this. I have used a program called [PowerPro]("http://powerpro.webeddie.com/") to do this in Windows for several years. It's so good to see something this this for Linux. I tried to get [Snippits]("http://ben.kudria.net/code/snippits") to work, but failed.

I struggled with the GUI a little to make it do what I wanted, but it works very well now. I like how it requires minimal set up and dependencies.

:D

---

### Post by cdekter on 2009-03-20
> **icheyne said:**
>  I struggled with the GUI a little to make it do what I wanted, but it works very well now. I like how it requires minimal set up and dependencies.

:D

Can you provide any details on where you had troubles with it? I'd be glad for any input to improve the UI.

---

### Post by Kangarooo on 2009-04-16
So if The Gui is ready when this will be in synaptic?:popcorn:

Also make it to be possible to upload seeting file for each user to for example some site or maybe launchpad?
i dont know much about ubuntu but if i understand correctly i can upload some of ubuntu programm automatikaly and with some (dont know yet witch) keywords on clean fresh install i can download my files/programms..
So i could be allways on every computer with same short-cut-keys-setting for this great thing.. :)

Also most used and most usable abbrivations should be detected with survey and put in project as recomended so they are on clean install..

Also there hould be auto word corrector but that shoud be another project..
For exampl it would turn word Heelo to Hello (like google..) wrld to world.
But that auto-corrector should work together with this programm couse if i have abbrivation like "mmo" and i want it to turn to "Mine more ore" but autocorrectr will change it to MMA. So there should be some activator.. CTRL and SHIFT are taken so some new?

Activator must work like this-> on abbrivation programm autokey activator if active then autocorrector not active..

p.s. is there autocorrector programm in linux? all languages? firefox has.. so make firefox work with ubuntu to develop autocorrect?

---

### Post by zeltak on 2009-06-24
hi

any idea when the abbreviation bug in Jaunty will be fixed

thx

Zeltak

---

### Post by cdekter on 2009-06-24
> **zeltak said:**
> hi

any idea when the abbreviation bug in Jaunty will be fixed

thx

Zeltak

I am partway through building a new interface class that will work around the X server problem by using AT-SPI. It is a big job and requires a lot of experimentation (because like a lot of things in Gnome, AT-SPI is poorly documented). I expect it to take another month or two, unless I manage to find someone to help out with it.

---

### Post by zeltak on 2009-06-25
thx cdekter

i dont mind helping in other areas (since i dont know anything about programming at all) such as documentation, simple graphic manipulations, etc...

I am using KDE by the way (kubuntu) will the new system work with kde?

Thx

Zeltak

---

### Post by cdekter on 2009-06-25
It will work with GTK+ apps under KDE (e.g. Firefox). That's about it I'm afraid. There are only a couple of ways in Linux of doing what AutoKey does, and with X Record broken, AT-SPI is the only other way. Unfortunately QT does not currently have AT-SPI support (although I've read that it is in the works).

---

### Post by K_REY_C on 2009-10-14
This is a wonderful tool. Quick question: how do you place the cursor in a script? 

Thanks very much!

---

### Post by cdekter on 2009-10-14
> **K_REY_C said:**
> This is a wonderful tool. Quick question: how do you place the cursor in a script? 

Thanks very much!

At the moment there is no convenience method for doing this, so you can do it yourself using keyboard.send_key("<left>", count). So for example:

```
s1 = "Cursor goes at the end of this fragment ->"
s2 = "Cursor will be before this fragment"
keyboard.send_keys(s1 + s2)
keyboard.send_key("<left>", len(s2))
```

There are still a lot of extensions possible for the scripting engine, it just comes down to when I have time to write them.

---

### Post by cacycleworks on 2009-12-14
@cdekter : Yaaay, I can't believe it - autokeys might let me finally find a replacement for my kubuntu 8.04 (KDE 3.5). See, I have integrated many meta key shortcuts into my workflow for emails to automate text insertion. When they made KDE4, the khotkeys are now non-functional!!

I have begun thinking about how to use Autokey to implement the replace-as-type functionality with some abbreviations that I can make...  And ubuntu/gnome has "keyboard shortcuts" that I use for launching programs (couldn't quite figure out how to make it insert text via simulating keyboard presses). If anyone is interested that program is gnome-keybinding-properties

I used Ubuntu Software Center to install AutoKey 0.54.5 and I have a few questions, if you would please help me:
[LIST]
[*]I see mention of abbr.ini; where is this file? 
[*]Do I treat abbr.ini as a script?
[*]How do I link a script to a meta-key combo?
[/LIST]
I saw your post above about the script... my big question is help with a specific situation: 

I reply to MANY emails and have automated several text insertions. The biggest one is when I reply. I simply type the name of who I am addressing...
cdekter

I leave the cursor right there then I press meta+t and khotkeys will type a , then (home)Hi(space)(down key)(enter)(enter)Thanks for writing!(space)(enter)(enter)Thanks,(enter)Chris(up key)(up key)(end)

And then the cursor is left after the "Thanks for writing!" bit. So then only typing cdekter is converted into:

> Hi cdekter,

Thanks for writing! [cursor]

Thanks,
Chris


This works great for me as custom signatures, etc, are too kludgy to be effective. I can work from a few different gmail type of accounts.

Thank you very much for your efforts! They are enabling me to make the switch from KDE to Ubuntu/gnome.
:) Chris

---

### Post by cacycleworks on 2009-12-14
Oh, I need to add that in the context of my usage of AutoKey 0.54.5, I have a fresh install of Ubuntu desktop 9.10 x86_64.

---

### Post by cacycleworks on 2009-12-14
> **sonicprogress said:**
> This program is coming on great.I'm using it at work right now.

**1.** I found this out when I wanted to be able to have a string appear

i.e. "tail -f" = "tail -f /var/log/randomlogfile.log"

Please can you make it possible to add strings like this. It would make autokey 100x better!


Hi KS,

You probable already know this, but you can add alias in your .bashrc file for when you are typing in the terminal window...
```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# some more ls aliases
alias ll='ls -l'
alias la='ls -A'
alias l='ls -CF'

```

Best,
Chris

---

### Post by cdekter on 2009-12-14
> **cacycleworks said:**
> 
I used Ubuntu Software Center to install AutoKey 0.54.5 and I have a few questions, if you would please help me:
[LIST]
[*]I see mention of abbr.ini; where is this file? 
[*]Do I treat abbr.ini as a script?
[*]How do I link a script to a meta-key combo?
[/LIST]



The abbr.ini was used in an earlier version of AutoKey (0.4x) and is no longer relevant. I would suggest strongly that you consider upgrading AutoKey by adding the PPA to your software sources:

[https://launchpad.net/~cdekter/+archive/ppa](https://launchpad.net/~cdekter/+archive/ppa)

The version in the software store is quite old and the program has moved on a long way since then. I'll be better able to help you if you are running the latest version.

To do the upgrade, after adding the PPA, do:

```
sudo apt-get remove autokey
sudo apt-get install autokey-gtk
```

Secondly, I would suggest joining the users group on Google Groups here:

[http://groups.google.com/group/autokey-users?pli=1](http://groups.google.com/group/autokey-users?pli=1)

You will be more likely to get help from other users of AutoKey if you post there.

> **cacycleworks said:**
> 

I saw your post above about the script... my big question is help with a specific situation: 



What you describe is very easy to do. Everything in AutoKey is done through the GUI and it should be fairly intuitive. Once you have upgraded to the latest version, I would suggest visiting the home page ([http://autokey.googlecode.com](http://autokey.googlecode.com)). There are links there that will take you to the wiki which should set you on the right way.

---

### Post by cacycleworks on 2009-12-15
Thanks Chris, brilliant! The GUI in the new version made everything crystal clear. 

BTW, it took me a long time to go to code.google.com to find the wiki ... it's not linked to from the google group??

The script I wrote to do the Hi , thing is like this:
```
output = "<home>Hi <end>,<enter><enter>Thanks for writing!"
output += "<enter><enter>Thanks,<enter>Chris" 
output += "<up><up><up><end> " 
keyboard.send_keys(output)

```

Rather than use the cursor workaround, I just used the up arrow keys. :)

Thanks!!
Chris

---

### Post by cacycleworks on 2009-12-16
In case there are other KDE3 holdouts like me who have a keyboard full of text insertion macros, I wrote a php script to convert the khotkeysrc to format that will work with autokey-gtk.

Sorry, I don't know python or I'd use python. 

[PHP]<?
$infile="/home/me/.kde/share/config/khotkeysrc";
$lines = file($infile);
$macro=Array();
// Loop through our file array one line at a time
foreach ($lines as $line) {
	$line=trim($line);
	list( $key, $data ) = explode( "=", $line);
	if( strpos( $key, "[" ) == 0 && strpos( $key, "[" ) !== FALSE ) {
		continue;	// skip ini keys ...
	}
	if( $key == "Key" ) {
		$input_key=$data;
		if( ! is_null( $word ) ) {
			$macro[$input_key]= $word;
			$input_key="";
		}
	}
	if( $key=="Input") {
		$word="";
		$data=explode( ":", $data );
		foreach( $data as $letter ) {
			if( strlen( $letter ) > 1 ) {
				if( strpos( $letter, "shift+" ) !== FALSE ) {
					list( $shift, $letter ) = explode( "+", $letter );
					if( ord($letter) >= 97 && ord($letter) <= 122 ){
						$letter = strtoupper($letter);
					} elseif ( $letter == "'" ) {
						$letter='"';	// convert ' to "
					}  elseif (  is_numeric($letter)  ) {
						$letter="<shift>+".$letter;
					}
				} elseif( $letter == "space" ) {
					$letter = " ";
				} elseif( strpos($letter, "return") !== FALSE || strpos($letter, "\n") !== FALSE ) {
					$letter="<enter>";
				} else	{
					if( strpos( $letter, "+" ) !== FALSE ) {
						$letter=explode( "+", $letter );
						$letter=implode( ">+<", $letter);
					}
					$letter="<".$letter.">";
				}
			}
			$word[]=$letter;
		}
		$word = implode( "", $word );
	}
}
print_r( $macro );
?>[/PHP]

---

### Post by mobilediesel on 2009-12-16
First, thanks to cdekter for continuing development on this program!

The only trouble I actually have with it is my lack of experience with writing Python. It would probably be easier if I wasn't also expanding knowledge of BASH and Lua scripting at the same time! That makes the problems my own fault. :D

When my experience catches up with what Autokey is capable of it will be a VERY nice replacement for AutoHotkey that I used to use when I was running Windows.

---

### Post by BionicSeahorse on 2009-12-18
Thanks to cdekter for such an awesome program! I have been using snippits for a good while, but Autokey will most likely take over those duties from now on.

Question: Why doesn't the following script work?

```
output= eval(system.exec_command("xclip -o"))
system.exec_command("kdialog --passivepopup \"The answer is %s\" 5" % output)
```

Mind you, I'm completely new to Python, so bear with me here. :)
TIA

---

### Post by cdekter on 2009-12-19
> **BionicSeahorse said:**
> Thanks to cdekter for such an awesome program! I have been using snippits for a good while, but Autokey will most likely take over those duties from now on.

Question: Why doesn't the following script work?

```
output= eval(system.exec_command("xclip -o"))
system.exec_command("kdialog --passivepopup \"The answer is %s\" 5" % output)
```

Mind you, I'm completely new to Python, so bear with me here. :)
TIA

Have you had a look under the View -> Show Script Error menu option? This will tell you about any errors occurring during execution.

Aside from this, you can replace system.exec_command("xclip -o") with clipboard.get_clipboard()

---

### Post by BionicSeahorse on 2009-12-19
> **cdekter said:**
> Have you had a look under the View -> Show Script Error menu option? This will tell you about any errors occurring during execution.
I did check that before, but there was "no error information available". After further inspection, I noticed that selecting a text containing a math problem like "5+5" was getting truncated to "5+" after passing it through [FONT="Courier New"]system.exec_command("xclip -o")[/FONT].
> Aside from this, you can replace system.exec_command("xclip -o") with clipboard.get_clipboard()
Changing my code to the following made it work perfectly:
```

output= eval(clipboard.get_selection())
system.exec_command("kdialog --passivepopup \"The answer is %s\" 5" % output)

```
I'm noticing a few quirks here and there, but I think I'll be posting those in the google group instead.
Thanks again for such a great timesaver!

---

### Post by sethlbrown on 2011-06-01
Just wondering if autokey is still the best solution for global text expansion and if it works with 11.04. I'm looking to make the move from OSX, and this is a must have for me, along with trackpad gestures, which appear possible now. (No doubt they have been for a long time.)

---

### Post by thaelim on 2011-06-01
> **sethlbrown said:**
> Just wondering if autokey is still the best solution for global text expansion and if it works with 11.04. I'm looking to make the move from OSX, and this is a must have for me, along with trackpad gestures, which appear possible now. (No doubt they have been for a long time.)

It works for a given definition of the word. I am aware of two major issues - the tray icon doesn't work with Unity, and most (if not all) applications that use GTK3 do not respond to the keyboard events generated by AutoKey. The second issue is fairly serious and I don't know when it will be resolved.

---

