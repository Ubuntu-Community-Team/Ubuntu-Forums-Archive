---
title: "Would *ANYBODY* find this useful?"
date: 2008-01-27
forum: The Cafe
---

### Post by peabody on 2008-01-27
I wrote a hotstring based replacement tool akin to Texter, Textpander and AutoHotKey's hotstrings.  I talked about it [here](http://ubuntuforums.org/showthread.php?t=675751) and [here](http://ubuntuforums.org/showthread.php?t=675753).  Put up a webpage for it at [http://peabody.weeman.org/autokey.html](http://peabody.weeman.org/autokey.html) with a demonstration video...

And I got nothing, zip, zero, zilch, nada!

I wrote this program mostly because from what I could tell from here, it was a badly needed thing in Desktop Linux, [judging](http://ubuntuforums.org/showthread.php?t=467025&highlight=textpander) [by](http://ubuntuforums.org/showthread.php?p=4042879&highlight=texter#post4042879) [posts](http://ubuntuforums.org/showthread.php?t=494889&highlight=texter) [like](http://ubuntuforums.org/showthread.php?t=477214&highlight=texter) [these](http://ubuntuforums.org/showthread.php?t=666493&highlight=autohotkey).  Guess I was wrong, because I have received ZERO response to it and it's been a few days now.

Admittedly, it's buggy, but I thought with some feedback from other programmers I could take it somewhere.  I don't want to abandon it, but truth be told, it's not even something I need.  I'm a programmer by trade and this kind of functionality is built into my editors, although I'll admit it's nice to have this thing be there for you in any program you need it in.

If I don't receive any positive feedback I'll probably shelve the project, which is too bad because I thought I was doing something worthwhile.

---

### Post by jackocleebrown on 2008-01-27
Hey,

This DOES look very cool. Sorry to hear you have not had a massive response. I am not sure what I would use it for right now... would not be surprised if it came in handy at some point. I hope you get some interest - I am sure that there are people out there who will want to use this. presumably you can customize the "dictionary" of abbreviations?

Do you ever get that thing that when you are writing a "how-to" for someone (or for a forum) that whenever you type in an instruction with  terminal command (especially one with paths on it) that you just can't stop yourself from pressing that TAB key! very frustrating. Perhaps you can work out a way to allow tab completion on any text input to easily write paths etc.

Anyhow, good luck,

Jack.

---

### Post by ugm6hr on 2008-01-27
I've just seen the video.  It is cool :)

Although, just like Desktop visual effects, I'm not sure I would use it for very long...  Though that's not a good reason to stop coding it!

---

### Post by peabody on 2008-01-27
> **jackocleebrown said:**
> . presumably you can customize the "dictionary" of abbreviations?

Yep, it's a ini style file that goes in ~/.abbr.ini.  Currently there are two annoying limitations on what can be an abbreviation (case-insensitive and no adjacent duplicate characters, long story, it's a documented known problem in the README).

> 
Do you ever get that thing that when you are writing a "how-to" for someone (or for a forum) that whenever you type in an instruction with  terminal command (especially one with paths on it) that you just can't stop yourself from pressing that TAB key! very frustrating.

Kind of sorta can get part of the functionality.  The text expansions are run through an 'echo' on the shell, so you can run any shell command via $() and capture its output.  Tab is a non-word character, so it would expand the abbreviation if what you typed matched.

---

### Post by conehead77 on 2008-01-27
This looks useful for posting in forums: 
ill -> i´ll 
dont -> don´t
ms -> Microsoft

I dont know if it would be useful in plain text editors, cant you have autocorrection there already? I know MS Word can (and i assume OO too), but i can see uses for extending this to just everywhere on the desktop.

edit: maybe its possible to import the abbreviations list from OO autocorrection then?

---

### Post by peabody on 2008-01-27
> **conehead77 said:**
> 
I dont know if it would be useful in plain text editors, cant you have autocorrection there already?

It's not, in fact it's disruptive if you use something like vim and Emacs and already have your own abbreviations :).  But again, the utility isn't for those audiences.

> 
edit: maybe its possible to import the abbreviations list from OO autocorrection then?

Yeah, would probably be very easy to write a script that could make a huge list of common spelling error abbreviations.  The program's pretty minimal right now because it's mostlly in proof-of-concept form.  I may even start over with the code base if I get enough positive response to really try and turn this into something people would use on a daily basis.

---

### Post by conehead77 on 2008-01-27
> **peabody said:**
> It's not, in fact it's disruptive if you use something like vim and Emacs and already have your own abbreviations :).  But again, the utility isn't for those audiences.

I can see me using it within firefox, plugin comes into mind...

---

### Post by peabody on 2008-01-27
> **conehead77 said:**
> I can see me using it within firefox, plugin comes into mind...

Yeah the first thing I actually thought to do was write either a firefox plugin or greasemonkey script.  Funny thing was, programming this proved easier, ironic as that may seem.  I don't have much extensive experience with javascript and while I could monitor keystrokes I couldn't think of an easy way to just replace the typed abbrv.

Plus my guess was that people really were looking for something you could use in firefox and gaim and xchat, etc, etc.

---

### Post by RebounD11 on 2008-01-27
> **conehead77 said:**
> This looks useful for posting in forums: 
ms -> Microsoft


ms stands for Thank you in my country as far as Instant messaging goes .. :D

Which comes with another idea: get someone to help you ith abbreviation for different languages :)

Great job! Don't stop just because you had no response so far.
> 
First they ignore you...
Then they laugh at you...
Then they fight you...
And then you win!

From a RedHat commercial I liked on Youtube. I think it's a quote from Mohandas Gandhi.
[http://www.youtube.com/watch?v=uBUgEx_91BU](http://www.youtube.com/watch?v=uBUgEx_91BU)

---

### Post by peabody on 2008-01-27
> **RebounD11 said:**
> Which comes with another idea: get someone to help you ith abbreviation for different languages :)

That's why I'm hoping to get some attention.  I'm having keyboard layout issues right now (long story short, /dev/input/* generates the same key sequences regardless of the keyboard layout, so the workaround I have so far is to prompt the user for their keyboard layout...not too great a solution).  I have no clue how keyboards from different countries are laid out.

I would definitely need help to get this program to work for other languages.

---

### Post by Bungo Pony on 2008-01-27
That's really cool! It would be really useful for message forums and IMing.

It would be really nice if you could add your own abbreviations, like your initials and such just by adding them to a conf file. Censors in message forums let you add your own customized words to censor.

---

### Post by peabody on 2008-01-27
> **Bungo Pony said:**
> 
It would be really nice if you could add your own abbreviations, like your initials and such just by adding them to a conf file.

That's exactly how the program operates.  In fact, one of the abbreviations I have launches gedit with the conf file loaded up so you can add abbrevs.  The conf file is constantly being reread, so changes are added immediately.

---

### Post by kevdog on 2008-01-27
Does this program slow down when you add say 1 million entries to the .conf file.  I assume the programs searchs the ini file sequentially, or is there some other type of logic.

---

### Post by peabody on 2008-01-27
> **kevdog said:**
> Does this program slow down when you add say 1 million entries to the .conf file.  I assume the programs searchs the ini file sequentially, or is there some other type of logic.

It definitely would, if it came to that I could try and have an implementation that keeps the dictionary in an on disk hash.  For now it's a proof of concept, I just used Python ConfigParser module.

---

### Post by forrestcupp on 2008-01-27
This looks pretty cool.  

So does it work with any program you type into?  Do you just type the abbreviation and when you press space it changes it?  Are there instructions for use in the download?

---

### Post by peabody on 2008-01-27
> **forrestcupp said:**
> This looks pretty cool.  

So does it work with any program you type into?  Do you just type the abbreviation and when you press space it changes it?  Are there instructions for use in the download?

Yes, yes and yes.

Instructions are in the download in the INSTALL and README files.  The program to run after installation is hotstring.py.  It's good to run it from a terminal initially to make sure everything's working.

---

### Post by kevdog on 2008-01-27
I might try this --

So when I am typing in the ubuntu forums reply section, it would make
dont = don't?  That would be useful

---

### Post by peabody on 2008-01-27
> **kevdog said:**
> I might try this --

So when I am typing in the ubuntu forums reply section, it would make
dont = don't?  That would be useful

Yes, I don't see any reason why that wouldn't work provided you have added that abbreviation to the abbr.ini file.  The line would look like

```
dont = don't
```

I just tried this abbrv and it worked fine.

---

### Post by conehead77 on 2008-01-27
I tried and failed :(

```
~/autokey-0.22 hotstring.py 
Traceback (most recent call last):
  File "/usr/local/bin/hotstring.py", line 22, in <module>
    import Xlib.X as X
ImportError: No module named Xlib.X

```

---

### Post by bobbocanfly on 2008-01-27
Nice idea but it just seems *really* buggy at the moment. I keep getting error messages about "stop_grab(dispal)". Nice idea though, will definately try it out again when it is a bit less buggy.

---

### Post by peabody on 2008-01-27
> **bobbocanfly said:**
> Nice idea but it just seems *really* buggy at the moment. I keep getting error messages about "stop_grab(dispal)". Nice idea though, will definately try it out again when it is a bit less buggy.

sounds like you ran autokey.py instead of hotstring.py.  hotstring.py is the latest program...autokey.py is old and is only around for the utility functions.

Run hotstring.py and let me know if you keep getting the same errors.

---

### Post by peabody on 2008-01-27
> **conehead77 said:**
> I tried and failed :(

```
~/autokey-0.22 hotstring.py 
Traceback (most recent call last):
  File "/usr/local/bin/hotstring.py", line 22, in <module>
    import Xlib.X as X
ImportError: No module named Xlib.X

```

you need to install the python-xlib package as stated in the docs (although I'll admit I could have made that more clear, I will do so now).

sudo apt-get install python-xlib.

---

### Post by peabody on 2008-01-27
Sorry for the triple post, but I found another text expansion program for linux.  This one's written in ruby, and unlike my program, it doesn't actually actively monitor the keyboard for input, but rather relies on you to assign keyboard shortcuts to a shell script that uses the 'ks' command.  I've responded to the following thread with installation details.

[http://ubuntuforums.org/showthread.php?p=4217972#post4217972](http://ubuntuforums.org/showthread.php?p=4217972#post4217972)

I've installed it and it's pretty snazzy.  It's command language is much more straight forward, but you have to go more out of your way to get your expansions to launch (i.e. it's up to you to assign commands to your keyboard through whatever mechanism is available to you on your Linux desktop environment).

Here's a blog post which shows an example of how to assign a shell script to a keyboard shortcut in GNOME.

[http://www.cyberciti.biz/faq/howto-create-keyboard-shortcuts-in-gnome/](http://www.cyberciti.biz/faq/howto-create-keyboard-shortcuts-in-gnome/)

By the way, I would love it if anyone who has tried my program would give me input, critical or otherwise.  I'm completely willing to help you get it working.

---

### Post by forrestcupp on 2008-01-27
Does this program log our credit card numbers and send our sensitive information back to you?

---

### Post by peabody on 2008-01-27
> **forrestcupp said:**
> Does this program log our credit card numbers and send our sensitive information back to you?

Hell it's open source, if you don't trust it, don't use, but if you know enough about code you can look at the source and see if it's doing anything bad.

None of my code does that.  I've looked over the keylogger program I use for the input and it doesn't do anything as far as I can tell.  I modified it somewhat to print keysequences instead of the actual printable characters.

[Edit]
Heck, I'll even show you how to run wireshark so you can see what's running over your network connection just to be safe.

[Edit]
In fact, here's the url to the program I used, if other people with knowledge want to vouch for it:[http://archives.neohapsis.com/archives/sf/linux/2005-q3/0065.html](http://archives.neohapsis.com/archives/sf/linux/2005-q3/0065.html)

---

### Post by Scarath on 2008-01-27
Just wanna say i would find this very useful when using a single handed keyboard with a PDA. Keep it up, cant wait to see the polished product. Maybe show it to the peeps @ maemo?

---

### Post by peabody on 2008-01-27
> **Scarath said:**
> Just wanna say i would find this very useful when using a single handed keyboard with a PDA. Keep it up, cant wait to see the polished product. Maybe show it to the peeps @ maemo?

Thanks, although I've been having an email conversation with the author of [snippits](http://www.youtube.com/watch?v=Mn_-CddjHOA).  I think his program is slightly better written, though it's not as easy to get up and running as mine is.  I've written a howto for his program which should get posted in the tutorial forum as soon as the mods get through it.  I've told him how I'm monitoring X11 input and he's seeing how he can incorporate in his program.

---

### Post by kevdog on 2008-01-27
So which program would you recommend right now? Your's or snippits, or wait until your changes have been incorporated into snippits?

---

### Post by peabody on 2008-01-27
> **kevdog said:**
> So which program would you recommend right now? Your's or snippits, or wait until your changes have been incorporated into snippits?

Aw heck, that depends :).  I think snippits is more difficult to install than mine (mine's just a tar ball, extract, make, sudo make install, cp abbr.ini ~/.abbr.ini, hotstring.py) since it's done through ruby gems which might be confusing if you're not used to it.  His also doesn't monitor all key strokes so the only way to make it work similarly to mine is to assign a keyboard shortcut to a shell command (which you have to look up how to do for your particular desktop environment).  Once there though, it does work nicely, and his expansions have slightly more functionality, in that you can embed ruby code them, and use place holders like {cursor} and use commands like {up} {down} {control}, etc.

However, I think it's much easier to use the output from a shell command in mine (just use subshell syntax: $(zenity --text='hello there!')).

Try both, they don't necessarily conflict and it's easy to turn either off.

---

### Post by forrestcupp on 2008-01-28
> **peabody said:**
> Hell it's open source, if you don't trust it, don't use, but if you know enough about code you can look at the source and see if it's doing anything bad.

Sorry man.  It was kind of a joke.  I should have put a smiley after it or something. :)  I know it's open source and everyone can look at it for themselves.  If you were doing something malicious, it would be stupid to put the source code out there for everyone to see.

I did notice something when looking at the abbr.ini file, though.  I think if someone were using this regularly, that "date" is way too common of a word to expand into a shell command.  It would be irritating if someone were typing in the Cafe about a hot date they went on last night and it kept expanding into a shell command.  I know it's easy to take it out, but maybe that one entry shouldn't be in there by default.

Edit:
Don't give up on this just because you found a similar project.  I think they are both for different audiences, and it seems like your implementation is a little better for what you intended it for.  I think the other one would be good for programmers.  I have used the built in code snippets in Visual Studio.  But your's is for a different purpose.  Keep working on it and polishing it.  It's a great piece of work.

And also, it's all about choice, isn't it?

---

### Post by Vadi on 2008-01-28
The link seems to be down

---

### Post by peabody on 2008-01-28
> **forrestcupp]
Edit:
Don't give up on this just because you found a similar project. I think they are both for different audiences, and it seems like your implementation is a little better for what you intended it for. I think the other one would be good for programmers. I have used the built in code snippets in Visual Studio. But your's is for a different purpose. Keep working on it and polishing it. It's a great piece of work.

And also, it's all about choice, isn't it?
[/quote]

Yes it certainly is, and thanks for the encouragement :).  I definitely want to polish my product, but the wall I'm currently facing is the reliability of the input capture.  Since you've used it, you may have noticed that for whatever reasons it just doesn't get the right input sometimes.  The worst of the problems was that keys were duplicating randomly.  I hacked that problem away by ignoring duplicates, but unfortunately, that has the unpleasant side-effect of requiring abbreviations to have no duplicate adjacent characters.   I don't have a lot of ideas on how to work around that currently.  It might be time for a trip to the LKML to ask about the nature of the /dev/input/* files.

Thanks for the date suggestion, when in doubt, remove a vowel, I'll make it 'dte' from here on out.

[QUOTE=Vadi said:**
> The link seems to be down

Huh?  Just checked, I was able to download it.  Can you post the link you're trying?

---

### Post by Vadi on 2008-01-28
Works now. Btw, if you want to spread it, start by putting a well-worded link in your sig.

---

### Post by PartisanEntity on 2008-01-28
I really like this and am definitely going to try this. I will post feedback of course. System-wide use would be great i.e. text editors, firefox, terminal..

edit: hmm the link to your website in your OP is down. Bandwidth exceeded?

---

### Post by peabody on 2008-01-28
> **PartisanEntity said:**
> I really like this and am definitely going to try this. I will post feedback of course. System-wide use would be great i.e. text editors, firefox, terminal..

edit: hmm the link to your website in your OP is down. Bandwidth exceeded?

Really???  You're the second person to say that the link has gone down recently.  That's it, I'm opening a sourceforge page... should be up by tonight.

Sorry everyone for the inconvenience.

[Edit]:

Oops...guess it takes 1-3 days to get a project approved on sf.net.  Well, I'll let everybody know as soon as it's up.

[Edit]

I've attached the latest version of this project on this thread for the time being.
I provided a .deb file that I made via checkinstall, but I honestly still recommend the source package.  If you absolutely want to use the deb,  **there are 3 caveats about it!**

[LIST=1]
[*]checkinstall wouldn't let me change the requires field.  This package requires the python-xlib package, however, it won't install it by itself, you will have to do that on your own
[*]This package only works for x86 architectures
[*]No example abbr.ini comes with it, go to my website  [http://peabody.weeman.org/autokey.html](http://peabody.weeman.org/autokey.html) and I'll have an example .ini in plain text on the page shortly.
[/LIST]

---

### Post by DjBones on 2008-01-29
looks like a great application!
although i'm not sure if myself in partcular would find it applicable,
with more developement i could only guess that it would get a cult legion going ;)
with some more developement maybe it could even get into the hardy repo's!

---

### Post by peabody on 2008-01-29
> Do you ever get that thing that when you are writing a "how-to" for someone (or for a forum) that whenever you type in an instruction with terminal command (especially one with paths on it) that you just can't stop yourself from pressing that TAB key! very frustrating. Perhaps you can work out a way to allow tab completion on any text input to easily write paths etc.

Found a way...

[http://www.youtube.com/watch?v=va-OnEF80S0](http://www.youtube.com/watch?v=va-OnEF80S0)

:), a bit of a hack and it's not the tab key (although you can use that to expand the shortcut once typed).

Sorry about the quality of the video, but I did zoom in on the text at the end.

abbrv is
```
chfile = $(zenity --file-selection --multiple --separator=" -- ")
```

---

### Post by peabody on 2008-01-31
Okay folks, just wanted to say that the sourceforge project page is finally up.  I've made a few changes to the program as well, so it should be a bit more usable by people.

project page:
[http://sourceforge.net/projects/autokey/](http://sourceforge.net/projects/autokey/)

homepage:
[http://autokey.sourceforge.net/](http://autokey.sourceforge.net/)

Definitely need advice and feedback.  I'm curious if I should announce this somewhere else on the forums.  I don't know where would be most appropriate.

---

### Post by antisocialist on 2008-02-11
do i need to log out for it to work, because it doesnt seem to be working... or do i need to assign a shortcut key for it to run the correction?

---

### Post by peabody on 2008-02-11
> **antisocialist said:**
> do i need to log out for it to work, because it doesnt seem to be working... or do i need to assign a shortcut key for it to run the correction?

Couple of things...

Did you make sure to use the release from sourceforge, and did you make sure to run the hotstring.py program froma a terminal to see if it is able to monitor keystrokes from your /dev/input/eventX file?  Finally, do have a standard US keyboard, or are you using something else?  Unfortunately my program seems to only work on standard keyboards currently.  A way to tell is to run:

```

sudo hotstring_logger /dev/by-path/*kbd

```

And see if, when you type a key, that a double-digit number is echoed to the terminal.

---

### Post by antisocialist on 2008-02-11
perhaps you should change the default abbr.ini to have edt = $(gedit ~/.abbr.ini) rather than edit as that way it will not interrupt posting when editing a post on forums example is below
EDIT 
link and the link would be here if this were real

see how that could be a good change
and for some reason it doesn't seem to be working now

EDIT
nvm i fixed it
lol o.O
be right back 
yay it's working!!!
(just had to save and close it before it would edit my text (suspiciously eyes the terminal window it is running in)

however i think that is a brilliant feature on your part that when you have .abbr.ini open it will not replace text (as this would screw up the abbr.ini file)

---

### Post by antisocialist on 2008-02-11
also good additions to default abbr.ini would be
u = you
i = I
r = are
however if you plan to type the alphabet these wont be particularly helpful
oh also
doesnt = doesn't
wont = won'I
I are you friend
also for bbcode I use "linkage" for links and "imgurl" for the bbcode
imgurl = 
that would be good to add to default config (it of course requires xclip but a simple sudo aptitude install xclip isnt too hard for anyone is it now?
oh another good one
sai = sudo aptitude install
i use that a lot

THANK YOU for this killer app, it is much better than snippet as it allows you to copy+paste things to avoid the edit and has edit as you type
you can be assured that i will use this to save me 2+ hours a day once I get it fully set up for myself
also when I do I will upload it to a post so you can add it (I will mainly use generic things) also I am finding the edit feature (which I have changed to "edt" for reasons in above post) very useful
thanks

---

### Post by peabody on 2008-02-11
Awesome!  I'm really glad the program is useful to you.  In the future, I hope to fix my international keyboard problem.  Thanks for letting me know it works for you!  If you have suggestions for the example abbr.ini, feel free to post them, I will add them as time goes by for future releases.

Ironically enough, you can use snippits with my program, by using a $(snippit name) abbreviation :).

---

### Post by Specter043 on 2008-02-11
I would definitely use this out of beta.  Maybe a customizable dictionary and an on/off option.

---

### Post by peabody on 2008-02-11
> **antisocialist said:**
> 
however i think that is a brilliant feature on your part that when you have .abbr.ini open it will not replace text (as this would screw up the abbr.ini file)

What's funny about this actually, is that it's an unintended consequence that turned out useful.  Subshells block the program, so until you exit, hotstring.py doesn't work.

---

### Post by peabody on 2008-02-11
> **Specter043 said:**
> I would definitely use this out of beta.  Maybe a customizable dictionary and an on/off option.

Cool, although you might be waiting a while ;), I'm neck deep in school currently and probably won't have much time to dedicate to the project until spring break.

I'm willing to help people get the program working however, in the mean time.

---

### Post by Linuxratty on 2008-02-12
Go to Klikit Linux. They might be interested.

---

### Post by SanskritFritz on 2008-02-13
Hey, coming from Windows as an Autohotkey user, I was looking for this kind of utility for some time now. THANK YOU! I will start to use it as soon I get back to my beloved Ubuntu machine (I'm at work now)

---

### Post by peabody on 2008-02-13
> **SanskritFritz said:**
>  THANK YOU! I will start to use it as soon I get back to my beloved Ubuntu machine (I'm at work now)

No problem, although thank me if and only if it works for you ;).

---

### Post by SanskritFritz on 2008-02-15
> **peabody said:**
> No problem, although thank me if and only if it works for you ;).Well, I tried to use it, but you were right, it doesn't work here :-( I tried to experiment with the time.sleep values, but no success. Do you have plans to develop it further? After the exams? Please? Pretty please?

---

### Post by peabody on 2008-02-15
> **SanskritFritz said:**
> Well, I tried to use it, but you were right, it doesn't work here :-( I tried to experiment with the time.sleep values, but no success. Do you have plans to develop it further? After the exams? Please? Pretty please?

I can try and see if we can get it working for you.  Firstly did you install python-xlib?  Did the installation go smoothly?  Second, what does hotstring.py do when run from a terminal?  Lastly, does the follow command print double digits when you press buttons on your keyboard?

```
sudo hotstring_logger /dev/input/by-path/*kbd
```

I had another user with a uk keyboard in which the program printed huge numbers, well into 40,000 range.  I haven't figured out a way to deal with them yet (my international keyboard problem).

If you have more than one keyboard on your machine, you might try and see if there are two keyboard files in /dev/input/by-path/  If that's the  case, you can explicitly set an eventfile abbreviation in abbr.ini to point to it.

---

### Post by SanskritFritz on 2008-02-16
Thanks for your answer!
Install went ok, it prints this in the terminal on run:
```
Input after loop: []
Input after key:  ['f']
Input after loop: ['f']
Input after key:  ['f', '<backspace>']
Input after loop: []
Input after key:  []
Input after loop: []
Input after key:  ['b']
Input after loop: ['b']
Input after key:  ['b']

```and so on. I tried it again now, and sometimes it works, but very rarely. I have to say, the output in the terminal does not correspond to my typing, either i doesnt find anything, or it finds the same key twice or three times or even more. Only at a certain typing speed, very hard to maintain, I get positive results.
PS: yes, the keylogger yields normal ansi characters. I use only Hungarian layout.

---

### Post by peabody on 2008-02-16
Okay, a couple of things...

1) it could be the event file it's finding doesn't correspond directly with your keyboard.  Could you show my what's listed under /dev/input/by-path

2) In hotstring.py you'll notice that I have two variables, dvorak and qwerty which are just python lists where each character is in a position corresponding to the ascii sequence sent from the /dev/input/eventX file.  You could retool either of these to better represent the hungarian layout (this one right?: [http://en.wikipedia.org/wiki/Keyboard_layouts#Hungary](http://en.wikipedia.org/wiki/Keyboard_layouts#Hungary)).  I don't have the time to do it myself, but if you can get it working I'll give you commit access to the project on sourceforge (provided you have a sourceforge login).  I need a way to get international keyboards working and right now, the only approach I can see is to just start filling out my own keyboard layouts (hopefully I'll find a way around that since that information is essentially there for me to access in the X server somehow).

---

### Post by SanskritFritz on 2008-02-16
Well, before I do the mapping (I do have SF acc, thanks for your offer!), I think we have another problem: timing. The hungarian layout is very similar to the qwerty layout, so I think 'brb' for example should work with qwerty mapping as well. Am I right?```
/dev/input/by-path$ ls -l
lrwxrwxrwx 1 root root 9 2008-02-16 22:03 platform-i8042-serio-0-event-kbd -> ../event1
lrwxrwxrwx 1 root root 9 2008-02-16 22:03 platform-i8042-serio-1-event-mouse -> ../event3
lrwxrwxrwx 1 root root 9 2008-02-16 22:03 platform-i8042-serio-1-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2008-02-16 22:03 platform-pcspkr-event-spkr -> ../event2
```/dev/input/by-path$ ls -l

---

### Post by peabody on 2008-02-16
> **SanskritFritz said:**
> Well, before I do the mapping (I do have SF acc, thanks for your offer!), I think we have another problem: timing. The hungarian layout is very similar to the qwerty layout, so I think 'brb' for example should work with qwerty mapping as well. Am I right?

Maybe...the trick is not ascii codes (I said the wrong thing in my last post), the trick is scancodes... the scancodes are actually different than us ascii, for instance, a on my keyboard maps to scancode 
30, while its ascii code is 65 (97 lower case).

Thanks for the device file listing, unfortunately, I'm pretty sure it's finding the right file.  Try running sudo hotstring_logger /dev/input/by-path/*kbd again and try and see what scancodes are being sent for each key on the keyboard.  If you could construct a listing for me, either you or I could set it up to work for your keyboard (hopefully).

I got to be away for a few hours, but I should be back later tonight.

---

### Post by SanskritFritz on 2008-02-16
> **peabody said:**
> Try running sudo hotstring_logger /dev/input/by-path/*kbd again and try and see what scancodes are being sent for each key on the keyboard.  If you could construct a listing for me, either you or I could set it up to work for your keyboard (hopefully).

I got to be away for a few hours, but I should be back later tonight.

sudo hotstring_logger /dev/input/by-path/*kbd yields seemingly good scancodes. the problem is, that I would expect **one** scancode per keypress, but very often nothing is printed when I press a key, sometimes more than one. Here is an example: I press **aaaaa**, and I get this in the terminal:
0
30
30
0
This doesnt seem to correspond to my typing :-(
Well, it is midnight here, so I go to bed. Thanks for your help, I'll be back tomorrow!

---

### Post by peabody on 2008-02-16
Hmm, that's pretty disappointing to hear; I can't be sure what would be causing that.  Five a's only translating to 4 sent scancodes with two of them being incorrect is hard to explain.  What are your hardware specs?  I often have the opposite problem with hotstring_logger, sometimes it sends the same key twice.

Here's an idea, try running the program with a higher priority.  sudo nice -n -20 hotstring_logger /dev/input/by-path/*kbd.  See if you have better luck with that.

[B]Big Important Edit:

Can you do me a huge favor and download subversion trunk?  I think I may have found the problem! (not 100% sure yet).  I made some changes to keylogger.c so recompile and reinstall the program.  I also made it so that you can (optionally) pass a sleep parameter to hotstring.py so you don't have to edit the hotstring.py file anymore to play with what would be the best wait time for sending events.  I recommend starting with something like 0.01 and working your way up to 1.

To checkout the subversion trunk, make sure the subversion package is installed and run the following in a terminal.

edit: had to put a space in the protocol so that vbulletin wouldn't make it a url and truncate it.  be sure to remove it afterwords.

svn co   https: //autokey.svn.sourceforge.net/svnroot/autokey/trunk autokey

Edit: wow, that's extremely strange...a space is getting put between the n and the k.  delete that one too.

[/B]

---

### Post by Martje_001 on 2008-02-17
Beautiful program!
But please see my attachment (.ogg iside)...

---

### Post by peabody on 2008-02-17
> **Martje_001 said:**
> Beautiful program!
But please see my attachment (.ogg iside)...

Pretty sure the latest version of the program shouldn't be doing this.  I just tried this abbreviation and it worked for me.

I'd try the subversion trunk and see if it fixes the problem for you.  If it doesn't, I have some good news.  I've been working on the program today and it's been coming along.  I now have a shortcut key to turn on and off the expansion functionality (scroll lock key).  I use espeak to speak audio cues for when the expansion is turned on and off.  A visual queue would be better, but this was easy to implement :).  I haven't committed this version yet since it makes a bit of a change to the way the program's run (you no longer run hotstring.py but autokey.py now, I merged my old code).  I will probably commit it tomorrow, and if I get enough positive feedback on that version, I'll make a new release.

---

### Post by Martje_001 on 2008-02-17
```
martijn@mydesk:~$ svn co https://autokey.svn.sourceforge.net/svnroot/autokey/trunk autokey
A    autokey/keyreader.py
A    autokey/abbr.ini
A    autokey/TODO
A    autokey/INSTALL
A    autokey/autokey.py
A    autokey/hotstring.py
A    autokey/autokey.desktop
A    autokey/keylogger.c
A    autokey/Makefile
A    autokey/README
Checked out revision 4.
martijn@mydesk:~$ cd autokey
martijn@mydesk:~/autokey$ make
gcc -o hotstring_logger keylogger.c
martijn@mydesk:~/autokey$ sudo make install
[sudo] password for martijn:
cp hotstring_logger *.py /usr/local/bin
cp autokey.desktop /usr/local/share/applications
echo "You should copy the example abbr.ini to ~/.abbr.ini"
You should copy the example abbr.ini to ~/.abbr.ini
```
Went fine eh?

```
martijn@mydesk:~$ autokey.py
Don't run this, run hotstring.py
Traceback (most recent call last):
  File "/usr/local/bin/autokey.py", line 185, in <module>
    if __name__ == '__main__': main()
  File "/usr/local/bin/autokey.py", line 166, in main
    sys.exit(1)
NameError: global name 'sys' is not defined

```
Hmm.. doesn't work, so I run hotstring.py:
```
martijn@mydesk:~$ hotstring.py
Input after loop: []
Input after key:  ['i']
Input after loop: ['i']
Input after key:  ['i', 'd']
Input after loop: ['i', 'd']
Input after key:  ['i', 'd', 'n']
Input after loop: ['i', 'd', 'n']
Input after key:  ['i', 'd', 'n', ' ']
Sending 'I don't know'
```
From the terminal everything seems fine, but I still get '*I don know*'

---

### Post by SanskritFritz on 2008-02-17
> **peabody said:**
> **Can you do me a huge favor and download subversion trunk?  I think I may have found the problem! (not 100% sure yet).**Man, you are great! It works without any flaw now! Thanks! So I will start the Hungarian mapping, dont expect it too soon though, I have too much work to do nowadays... you also be careful with your exams, heheh... nevertheless, waiting for the next version. If you need help, I'm available, the biggest constraint being the free time of course...
Again, thanks!

---

### Post by tribaal on 2008-02-17
Cool little program you have here :)

Works flawlessly for me, I'l like to see this included in GNOME or something, this should be in the default install (having a menu in the keyboard shortcuts config screen or something).

Nice work :)

- Trib'

---

### Post by Vitamin-Carrot on 2008-02-17
Word replacer would be cool to have predictive text aswell.
Do you set up the phrases that are to be replaced?

---

### Post by peabody on 2008-02-17
> Hmm.. doesn't work, so I run hotstring.py:

If you read the INSTALL you would have seen that it told you to run the hotstring.py program :).  Although, for what it's worth, my latest revisions have gone back to using autokey.py (I merged the code).  Sorry for the confusion.  I know nobody likes to read those text files, but especially for my program, I highly HIGHLY encourage it.  It's very much in a huge state of flux right now and will likely have dramatic changes between releases.  In particular, a list of known problems is in the README with ideas for work arounds or calls for help.

As for the 'I don know' expansion, only thing I can think of is that your keyboard requires the shift key to type something like an apostrophe.  I haven't been able to reproduce your problem on my machine unfortunely :(, so I'm not sure where to start looking.}

> Cool little program you have here

Works flawlessly for me, I'l like to see this included in GNOME or something, this should be in the default install (having a menu in the keyboard shortcuts config screen or something).

Nice work

- Trib'

Thanks for the encouragement :)!  I'm guessing I have a long way to go before the code is stable enough for Debian or Ubuntu however.  I certainly won't stop anyone from packaging the program for either distro!

> Word replacer would be cool to have predictive text aswell.
Do you set up the phrases that are to be replaced?

Yes, there's a text file that you copy to your home folder called .abbr.ini.  You place 'word = expaned phrase', one for each line.  The program comes with an example one and shows how you can use shell commands so you can do neat things like paste from the clipboard into the expansions, etc, etc.  One of the main expansions is 'edt' which actually launches a text editor with that file as the contents.  Makes it so you can make quick changes to your abbreviations.

As for predictive replacement (something like OOo's functionality) that would be cool, although it would be very tricky and I'd like to work on getting the program stable and getting it working for all international keyboards before I start letting feature creep get the better of me :).

---

### Post by peabody on 2008-02-17
Sorry to double post, but I just wanted to let everyone know that the latest subversion trunk has been made into release 0.26.  If everyone interested in the program could give this one a go, that would be great!  Links in the sig.  Thanks!

I will be commiting my latest revisions to the subversion trunk later today.  Those revisions are a bit more experimental, but I think most people will agree that the latest subversion will be a nice improvement.  I've inserted audio cues and you can now toggle the expansion functionality on and off with the scroll lock key.  You can download the subversion trunk with:

```
svn co https://autokey.svn.sourceforge.net/svnroot/autokey/trunk autokey
```

I'll post here again later tonight when I've committed the changes.

---

### Post by peabody on 2008-02-18
Okay boys and girls, svn trunk has been updated!  If anybody could be kind enough to test it, that would be truly awesome.  If this version proves useful enough, it's gonna be 0.30.

---

### Post by SanskritFritz on 2008-02-18
> **peabody said:**
> Okay boys and girls, svn trunk has been updated!  If anybody could be kind enough to test it, that would be truly awesome.  If this version proves useful enough, it's gonna be 0.30.Updated my working directory, with the new version! Works great, I'm currently looking into the code to disable the speech ;-)
On the other hand, I will soon start to do the hungarian keyboard mapping. Great work, keep up! Thumbs up!

---

### Post by peabody on 2008-02-19
Just released version 0.30 to the sourceforge page.  I will be adding a .deb shortly.

I realize the audio cues may annoy people, I'll make that an optional feature to turn on in the future.

---

### Post by peabody on 2008-02-19
deb has been posted, it's not the primary download file however.  You can download the deb from this page:

[https://sourceforge.net/project/showfiles.php?group_id=216191](https://sourceforge.net/project/showfiles.php?group_id=216191)

---

### Post by peabody on 2008-02-19
FYI: There was a slight problem with the deb I uploaded.  I fixed the problem, but just in case...if you're getting an error when you try and run autokey.py in the terminal that says that it couldn't import 'test_mod', try downloading the deb from another mirror.  It looks like it can take a while for the files to propagate to the mirrors on sf.

---

### Post by GeBo on 2008-04-04
Hello, Peabody. Thanks for your program.

Actually, I'm not a frequent user of your program, but I'm always interested in such a program, as I am a big fan of AutoHotkey. A few months ago I searched for a equivalent under Linux (specifically Ubuntu) and ran into your little gem. Although it wasn't what I was looking for, I liked the concept and saw some possibilities for practical use.

Today I updated to the latest version (0.31.1) and found that an extra space was added after completing. I can't remember if it did in my previous version. Also I noticed idn gives me: I donqt know (notice the 'q' instead of a quotation mark).

Maybe someone can check this if this also happens with others. By the way, my native language is dutch, but I use a VS international keyboard (which is standardly used in the Netherlands).

Typing the previous sentence, I typed Btw. This was replaced by a lower case b instead of an upper case one. Peabody, maybe you can look into this?

Lasts me only to say: Keep up the good work!


As of what 'AutoHotkey under Linux' concerns: xmacro does that trick for me (it's in the repository). A very basic tutorial can be found [[COLOR="Blue"]here[/COLOR]]("http://ikester.blogspot.com/2007/01/im-huge-fan-of-autohotkey.html").

---

### Post by Tundro Walker on 2008-04-05
This is one of those things where you need to give it some time to catch on ... sort of like conky or the quake-style console drop-downs.

I could easily see this catching on with the IM / texting crowd, so their lame abbreviated speech will finally get auto-parsed into real words.

Unfortunately, the folks that would be most likely to use it (the ones I mentioned), probably fall a little further from the tech-savvy end of the bell curve than you.  So, they probably a) won't install it, or b) won't remember to use it once they do.

If you implemented it like a spell-checker, where someone could type up all their texting / reply stuff, then clicked a button to have it go through and parse out their acronym stuff automatically, it'd probably see more use.

---

### Post by GeBo on 2008-04-05
What I meant with "possibilities for practical use", is like using an abbreviation for e.g. your company name and for a signature underneath every mail you write. If you work for a holding and you have to send mails out of the name of the different companies, this can very much come in handy.

Example:

br1 = Best regards,
 One company
 GeBo

br2 = Best regards,
 other company
 GeBo

That multi-line thing is really powerful. You can even write complete standard text which fills a whole A4 (letter, if you please). So you don't have to copy - paste all the time when creating an e-mail; you just use the abbreviation.

---

### Post by gotix on 2008-07-28
of course it is usefull !
I am a big fan of Autohotkey too, so anything that implements some functionalities of it in Linux is great.
Is it possible to make it a package so I can install it with synaptic?

---

### Post by papsynot on 2008-08-03
> **GeBo said:**
> Today I updated to the latest version (0.31.1) and found that an extra space was added after completing. I can't remember if it did in my previous version.
I have this problem as well.  It happens regularly but not all the time.

---

### Post by toddlohenry on 2008-11-01
> **peabody said:**
> That's why I'm hoping to get some attention.  I'm having keyboard layout issues right now (long story short, /dev/input/* generates the same key sequences regardless of the keyboard layout, so the workaround I have so far is to prompt the user for their keyboard layout...not too great a solution).  I have no clue how keyboards from different countries are laid out.

I would definitely need help to get this program to work for other languages.

I'm a recent convert to Ubuntu. Not being able to find a good text expander is one of the few hangups I have so far. What's the status of your project?

---

### Post by Martje_001 on 2008-12-15
Hey, I wanted to say that I still use your program and it's really useful. However, it still doesn't do some things I want it to. Maby I could take over the project? Or maby move it to Launchpad so that we can file bug reports and upload patches easily?

---

### Post by toddlohenry on 2009-05-21
It's INCREDIBLY useful -- in fact, a good text expander is the only thing that keeps me from fully embracing Ubuntu! In the Windoze space I use asutype and it saves me tons of time. I have your software installed on another computer -- the problem is that I had to have a geek do it for me and even he had problems. If you could improve the installation experience, I'd love to be able to use it...

---

### Post by -grubby on 2009-05-21
Just one suggestion: Move the configuration into ~/.config.

---

### Post by iansane on 2011-07-04
Well it's 2011 now, just started to try and install it from source from google code and lucky I decided to check synaptic first. So much easier to just install it from there now that it's in the repos.

So I'm way late but thanks for getting this program out there. It's going to come in handy for inserting default html and css :-)

---

