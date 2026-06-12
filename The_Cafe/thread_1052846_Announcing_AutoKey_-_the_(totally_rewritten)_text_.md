---
title: "Announcing AutoKey - the (totally rewritten) text expansion and hotkey utility"
date: 2009-01-28
forum: The Cafe
---

### Post by cdekter on 2009-01-28
AutoKey is a text replacement and hotkey utility. It allows you to manage collection of phrases or other text, and assign abbreviations and hotkeys to these phrases allowing you to insert them on demand into whatever program you are using. This is the most basic functionality, and is similar to a well-known Windows utility called AutoHotkey.

[[IMG]http://img516.imageshack.us/img516/4950/configwindowxz3.th.png[/IMG]](http://img516.imageshack.us/my.php?image=configwindowxz3.png)

[[IMG]http://img516.imageshack.us/img516/3091/advancedvw0.th.png[/IMG]](http://img516.imageshack.us/my.php?image=advancedvw0.png)

AutoKey works by sending and receiving keyboard events via the X server. As such it is compatible with any version of Linux running an X server that has the RECORD extension available/enabled. Full unicode support is provided and it should in theory work with any keyboard layout.

This new version has been totally rewritten, along with having many new features, including a full-featured GUI for managing the configuration.

In depth:
[LIST]
[*]Phrases can be collected into folders.
[*]Folders can also be assigned abbreviations and hotkeys, allowing you choose a phrase from the folder on entering the abbreviation/hotkey
[*]Regular expressions can be used to filter windows by their title, to excludes hotkeys/abbreviations from triggering in certain applications
[*]Phrases or folders can be attached to the tray icon menu, allowing you to select them without assigning a hotkey or abbreviation
[*]A predictive mode can be enabled on a phrase-by-phrase basis. AutoKey will then suggest matching phrase(s) as you type a configurable number of characters from the beginning of the phrase (see screenshot below)
[*]AutoKey can track your usage patterns and present the most frequently used items at the top of the phrase menu
[*]A plugin framework provides the ability to extend AutoKey
[*]An import facility allows users of AutoKey 0.40.x to import their existing abbreviations
[/LIST]

[[IMG]http://img516.imageshack.us/img516/7686/suggestld0.th.png[/IMG]](http://img516.imageshack.us/my.php?image=suggestld0.png)

This release is essentially a beta, but it is thoroughly unit-tested and should be trouble free. We are also looking for someone with experience in Debian packaging to package the application, which is released under GPL v3 (naturally).

Visit the [SourceForge.net download page]("https://sourceforge.net/project/platformdownload.php?group_id=216191&sel_platform=6566") to download the source code, which is written entirely in Python and can be run as is (by running the autokey.sh shell script). Ensure that you have the required packages installed as listed on the release notes page.

Potential future features:
[LIST]
[*]Autocorrect and spell checking as-you-type (in ANY application)
[*]Automatic recognition and storage of frequently-typed sentences (using the Python Natural Language Toolkit)
[/LIST]

Any comments/criticism/patches welcomed :)

---

### Post by cdekter on 2009-01-31
An update has been released today to fix a few minor UI issues.

---

### Post by cdekter on 2009-02-21
Version 0.52.0 has just been released. The changelog details fixes/improvements, but the following are the major highlights:

[LIST]
[*]A popup similar to Tracker, where you can enter an abbreviation and have it autocompleted for you. Can be activated using a configurable hotkey or by clicking on the tray icon.
[*]In GTK-based applications, AutoKey can now type any character, even if it is not defined in the user's keyboard mapping.
[/LIST]

[Download it from here]("https://sourceforge.net/project/platformdownload.php?group_id=216191&sel_platform=6566")

---

### Post by marshag63 on 2009-02-27
Hi!  I have a fresh install of Mint 6.  I downloaded the zipped autokey file and unzipped it to my home directory.  I downloaded python-configobj and python-xlib -- I noticed that python-xlib0 was already installed.  Anyhow, I cannot get autokey to run.  Do you think that having python-xlib and python-xlib0 is causing the problem?

I can't wait to try this new version out!  :)

Any advice greatly appreciated.

Thanks!

MarshaG

---

### Post by marshag63 on 2009-02-27
I answered my own questions - DO NOT REMOVE PYTHON-XLIB0 from Linux Mint 6 Felicia - BAD BAD BAD!!!!

MarshaG.

---

### Post by cdekter on 2009-03-02
> **marshag63 said:**
> I answered my own questions - DO NOT REMOVE PYTHON-XLIB0 from Linux Mint 6 Felicia - BAD BAD BAD!!!!

MarshaG.

Glad you worked it out - hope you find AutoKey useful.

---

### Post by marshag63 on 2009-03-02
cdekter, unfortunately I am unable to use it.  Linux Mint 6 needs python-xlib0, or the install is "borked".  Even though I downloaded python-xlib and installed it, I could not get Autokey to run.  :(  

Any chance Autokey will move to python-xlib0?

MarshaG

---

### Post by cdekter on 2009-03-02
I'm not sure why mint has two different versions of the package. They must fundamentally be the same thing. Can you please post the terminal output that prints when you start AutoKey so I can try and determine the cause of the problem.

---

### Post by marshag63 on 2009-03-03
First a little background on my install:
P4 Gateway, 512 MB Ram, Linux Mint 6 (Felicia) - fresh install.

I used Synaptic to download python-configobj and python-xlib.  Then I went to the autokey webpage and downloaded the latest autokey zipped file to my desktop.  I double clicked on the zip file and the archive program opened up.  I extracted the contents of the zip file to /home/username.  I then opened a terminal and type "autokey.sh" with the following results:

bash: autokey.sh: command not found


MarshaG.

---

### Post by cdekter on 2009-03-03
You need to set the autokey.sh script to be executable, then run it using

./autokey.sh

---

### Post by marshag63 on 2009-03-03
YAY!.  I used "chmod +x autokey.sh" and now it runs when I type ./autokey.sh.  Is it normal that one would have to make the file executable like that?  How would I get it to run without having to type "./autokey.sh" everytime?

It looks great!  Just need to figure out how to use it.  :)

MarshaG.

---

### Post by marshag63 on 2009-03-04
I have a couple quick questions.

What is the difference between a "positioning" phrase and a "tray" phrase?

Can phrases be added via keyboard shortcuts like MS Word Autotext where I would highlight the phrase and press Alt + F3 and then all I have to do is tell it what abbreviation to use?

Kinda fuzzy on how this works.

Thanks for any help  :)

MarshaG

---

### Post by cdekter on 2009-03-04
Those are just some examples to show you what is possible.

The positioning phrase is an example of using the Cursor Position macro to position the cursor after the phrase is executed.

The tray phrase is an example of a phrase that is shown in the tray menu, when you right-click the tray icon

The shortcut for adding phrases is a nice idea, I may include it in the next release.

---

### Post by marshag63 on 2009-03-04
Hi!  I have another quick question.  

Can Autokey import from a source other than previous versions of autokey, i.e., like a tab separated text file or something?


Can I use a clipboard program to paste text into the Autokey dialog box?

Are there are new videos of this version?

Thanks again for a great program - looking forward to exploring what it can do more.

MarshaG.

---

### Post by cdekter on 2009-03-04
> **marshag63 said:**
> Hi!  I have another quick question.  

Can Autokey import from a source other than previous versions of autokey, i.e., like a tab separated text file or something?



Not it can't however the config file format from the previous version is very straight forward:

```

[abbr]
idts = I don't think so
ymmv = your mileage may vary
linux = Linux
otoh = On the other hand
ftw = for the win
ianal = I am not a lawyer
idn = I don't know

[defaults]
omittrigger = false
wordchars = [\w]
matchcase = false
ignorecase = false
backspace = true
immediate = false
triggerinside = false

```

> **marshag63 said:**
> 

Can I use a clipboard program to paste text into the Autokey dialog box?



I don't see why not...

> **marshag63 said:**
> 

Are there are new videos of this version?



Not yet no.

---

### Post by marshag63 on 2009-03-08
What's the name of the file that hold's these configurations?


BTW, I'd be glad to help out with a manual or documentation - that way I can learn how to use Autokey. 

MarshaG

---

### Post by marshag63 on 2009-03-08
Just downloaded Autokey 0.52.2, extracted it to my /home/user directory where it created a Folder named "Autokey".  In a terminal, I changed directory to the Autokey directory and I made the file executable with "chmod +x autokey.sh)  When I type "./autokey.sh" to start autokey, I got an error box with the following message:

Fatal error starting AutoKey.
[Errno 2] No such file or directory: '../../config/autokey.bin'

Did I do something wrong?

Thanks so much for any help.

MarshaG.

---

### Post by cdekter on 2009-03-08
Oops... That would be a bug. I'll put out a fix later today.

---

### Post by marshag63 on 2009-03-08
Thanks! I downloaded 0.52.1 and installed it until the next updated version.

MarshaG.

---

### Post by cdekter on 2009-03-13
Version 0.52.2 has just been released. It fixes all the bugs reported since the 0.52.1 release. It also adds the ability to manipulate phrases and folders by cut/copy/paste, and a few other minor new features.

---

### Post by marshag63 on 2009-03-14
That's great news - downloading it now.

Could I ask a favor of everyone helping develop this?  I would like to write a tutorial for installing and using Autokey for abbreviation expansion primarily, i.e., the users who will be using this tutorial already are used to having a defined set of abbreviations for words and phrases.  

SSOLVED:  It is "./autokey.sh"
If anyone would care to explain step-by-step (and the CLI way too) on how you install Autokey so that it starts with typing "autokey.sh" and not "./autokey.sh", that would be a great first step.

SOLVED!  See Post #24
I would also like to be able to add/import a big list of abbreviations already compiled (using the abc = anything before coming), but need to know which file to add the abbreviations to.

I'd be interested in knowing about the "macro" function - is it macro as in recorded keystrokes or macro as in write the code (bash?) to perform an action?

All help greatly appreciated!  :)

MarshaG.

---

### Post by ice60 on 2009-03-14
i might try it when i eventually install a supported distro, i'm still using suse 10.2 lol. i bookmarked the thread.

---

### Post by marshag63 on 2009-03-14
I've been playing with Autokey for a few minutes now and noticed a couple of things:

PARTIALLY SOLVED:  Works in Openoffice (part of the time), works first time in Gedit then no more.  
Unable to set keyboard command to toggle configuration window to open.
I used default Control K - in Gedit it worked once and then would bring up the "look" box.  

SOLVED:  Abbreviations with options "Match phrase case to typed abbreviation" and "Ignore case of typed abbreviation" will expand the abbreviation according to how the abbreviation was typed, no matter how the abbreviation was entered.  NICE!  :)

Conflict with Configuration window options to expand abbreviation to match case.
When I toggle on "match case to typed case" it automatically puts a check mark in the "ignore case" option"

Can the Configuration window be set to remember the last phrase folder that was edited or be set to a default folder?

I noticed when I right click on the tray icon to go into the configuration window the focus is on the "folders and phrases" button - its cool that it sorts the folders alphabetically in ascending or descending order

Autokey is very much on the right track!  YAY!

MarshaG

---

### Post by marshag63 on 2009-03-14
I wrote a short tutorial on how to add a group of abbreviations.

Autokey 0.52.2 - March 14, 2009


_How To Import Abbreviations In a Group:_

Since there is no longer an abbr.ini file, you have no file to edit and directly add abbreviations.  However, you can import from a file name "abbr.ini."  See example below - be sure to include the "config" and "defaults" sections, and do not have any duplicate abbreviations as this will cause import to fail. 

In the [abbr] section the format is:  abbreviation = text as you want it to appear.
___________________________________________________________________________________________________________________________
[config] 
voice = no 
method = XLib 
editor = gedit 
 
[abbr] 
# Comments are now possible in the config file to make your config more manageable 
afaik = As far as I know 
idts = I don't think so 
ymmv = your mileage may vary 
linux = Linux 
otoh = On the other hand 
sk = We all know that %s sucks 
escapechars = You can also write multiline abbreviations by using the \\n character like this:\n\nThis is two lines down. 
ftw = for the win 
ianal = I am not a lawyer 
emacs = Emacs 
fwiw = For what it's worth 
idn = I don't know 
 
[defaults] 
omittrigger = false 
wordchars = [\w] 
matchcase = true
ignorecase = false 
backspace = true 
immediate = false 
triggerinside = false 
____________________________________________________________________________________________________________________________

Once you have added your abbreviations, save the file and make sure the name is "abbr.ini"

With autokey running, bring up the "Autokey Configuration" window or right click on the tray icon and then on "Configure."  Then click on "File" and choose "Import Settings."  From the "Import Autokey Settings from 4.0" diaglog box, navigate to the directory where you stored your "abbr.ini" file, left click on the "abbr.ini" file and then click on the "Okay" button and this will add a folder titled "Imported Abbreviations."  Your abbreviations are now ready to use.

**VERY IMPORTANT:  Be sure to exit the Autokey program by clicking on the system tray icon and choosing "Quit" or any new changes will be lost!**

---

### Post by marshag63 on 2009-03-24
How to Install Autokey-0.52.2.1:

Make sure you have installed python-xlib and python-configobj - either through Synaptic or via command line:

(sudo apt-get python-xlib python-configobj)

Download zipped file from Sourceforge to Desktop.

[https://sourceforge.net/project/showfiles.p...ckage_id=261010](https://sourceforge.net/project/showfiles.p...ckage_id=261010) (Autokey-0.52.2.1.tar.gz)

Double left click on zipped file on Desktop to start extraction process, extract to /home/username directory (i.e., users /home directory, where it creates an "Autokey" directory.

Open a terminal and change to the Autokey directory - "cd Autokey" and press Enter.

Now we must change permissions of the autokey.sh file.
Type "chmod +x autokey.sh"

Now to run autokey, you must be in the Autokey directory and type
"./autokey.sh" (without quotes). 

Make a desktop launcher  - right click on panel, Add to Panel, double click Custom Application Launcher, Autokey in name box, /home/username/Autokey/autokey.sh in command box.

MarshaG.

---

### Post by guraknugen on 2009-04-12
I'm not sure if this is the right place to write, but I didn't find a better one:

I just downloaded the latest version, Autokey-0.52.2-1.tar.gz. I unpacked it, added run permissions to the autokey.sh and finally, from a Gnome terminal, entered ./autokey.sh.

The result of this was the following:
```
y$ ./autokey.sh 
Traceback (most recent call last):
  File "autokey.py", line 23, in <module>
    import expansionservice, ui
  File "/home/me/Autokey/src/lib/expansionservice.py", line 20, in <module>
    import iomediator, configurationmanager, ui
  File "/home/me/Autokey/src/lib/iomediator.py", line 71, in <module>
    from interface import *
  File "/home/me/Autokey/src/lib/interface.py", line 22, in <module>
    from configurationmanager import *
  File "/home/me/Autokey/src/lib/configurationmanager.py", line 18, in <module>
    import os.path, shutil, configobj, gtk
ImportError: No module named configobj
$

```
I guess this means that something needs to be installed. I found, in another thread, a similar problem and that person was recommended to install python-gamin.
I installed it (I can see in Synaptic that it's installed), but the same problem still persists.

I tried Autokey a year ago and it worked OK, but it lacked UTF-8 support, so the Swedish characters åäöÅÄÖ couldn't be used, which made it useless to me, but now I read that this seems to be fixed, so I'm very excited to try this new version. When I was on Windows, before summer 2007, I used something called AllChars for the same thing. Some of the AllChars features, like the compose key feature, seems to be default in any Linux system, but I missed the text expansion feature.

A don't know much about Python, so any kind of help would be appreciated.
I am running Ubuntu 8.10 on a 1.6 GHz 2.0 GiB laptop, by the way.

---

### Post by cdekter on 2009-04-12
You need to install the package python-configobj

---

### Post by guraknugen on 2009-04-12
> **cdekter said:**
> You need to install the package python-configobj

Thanks. I installed it and tried again and got more error messages, this time about Xlib, but I found a package called python-Xlib and I installed it and after that it started.

Thanks!

---

### Post by guraknugen on 2009-04-12
> **guraknugen said:**
> Thanks. I installed it and tried again and got more error messages, this time about Xlib, but I found a package called python-Xlib and I installed it and after that it started.

Thanks!

Are there any instructions for how to use it?
The dialogue that appeared the first time I started the autokey.sh was accidently closed, and now I don't know how to get it back. Autokey seems to be running in the background so I guess I should press some key combination or something to get the dialogue window back, right?

I tried logging out and then in again, but all that happens is that autokey.sh runs in the background. There has to be a way to define abbreviations and things like that, right?

Or am I missing something here? Or maybe I'm just being plain stupid&#8230;

---

### Post by Shaun32 on 2009-04-14
I tried to open AutoKey today, and I haven't been able to open it yet.  A dialog box came up with "Fatal error starting AutoKey.
Couldn't recognize the image file format for file '../../config/autokeyicon.svg'"

I thought this was fixed in the most recent version.  Is there any quick fix for this bug?  I'm pretty sure I have the most recent version.  I have 0.52.2-1.

I would absolutely love this program if I could get it to work, because I type the same messages all day for work.

Oh yeah, I'm running Kubuntu 8.04 - don't know if that makes a difference.

Thanks in advance!

---

### Post by cdekter on 2009-04-14
> **guraknugen said:**
> Are there any instructions for how to use it?
The dialogue that appeared the first time I started the autokey.sh was accidently closed, and now I don't know how to get it back. Autokey seems to be running in the background so I guess I should press some key combination or something to get the dialogue window back, right?

I tried logging out and then in again, but all that happens is that autokey.sh runs in the background. There has to be a way to define abbreviations and things like that, right?

Or am I missing something here? Or maybe I'm just being plain stupid…

There is a key combination, but there is also a tray icon that you can right click :)

---

### Post by cdekter on 2009-04-14
> **Shaun32 said:**
> I tried to open AutoKey today, and I haven't been able to open it yet.  A dialog box came up with "Fatal error starting AutoKey.
Couldn't recognize the image file format for file '../../config/autokeyicon.svg'"

I thought this was fixed in the most recent version.  Is there any quick fix for this bug?  I'm pretty sure I have the most recent version.  I have 0.52.2-1.

I would absolutely love this program if I could get it to work, because I type the same messages all day for work.

Oh yeah, I'm running Kubuntu 8.04 - don't know if that makes a difference.

Thanks in advance!

This is not a bug - in Kubuntu you will need to install some Gnome/GTK packages to get it to run. The easiest way to achieve this is to install some Gnome app through Synaptic/apt, which will then pull in all the necessary packages. A nice simple one might for example be gedit

---

### Post by Shaun32 on 2009-04-14
> **cdekter said:**
> This is not a bug - in Kubuntu you will need to install some Gnome/GTK packages to get it to run. The easiest way to achieve this is to install some Gnome app through Synaptic/apt, which will then pull in all the necessary packages. A nice simple one might for example be gedit

Oh!  Ok, cool, well I'll just do that, then.  Obviously I'm not very knowledgeable about the way GNOME works vs. KDE.  Will that limit Autokey to only be able to be used in GNOME programs, then?  I'm looking to use it in Firefox.

---

### Post by Shaun32 on 2009-04-14
OK, sorry for being an uber-noob here, but I took your advice and installed gedit to try to get those GNOME libraries installed.  Gedit works fine, but Autokey still comes up with the same error, so I tried to do some googling and installed some GNOME and GTK libraries, and Autokey still comes up with the same message.  I have not rebooted, but I have logged in and logged out.  What are some specific packages that I should make sure I have installed?  I'm pretty clueless on which ones I need and which ones I don't need.

---

### Post by cdekter on 2009-04-14
> **Shaun32 said:**
> Oh!  Ok, cool, well I'll just do that, then.  Obviously I'm not very knowledgeable about the way GNOME works vs. KDE.  Will that limit Autokey to only be able to be used in GNOME programs, then?  I'm looking to use it in Firefox.

AutoKey will work in any X application, whether it be KDE, GNOME or otherwise.

To specifically fix the problem you've been having, install the package librsvg2-common

---

### Post by guraknugen on 2009-04-14
> **cdekter said:**
> There is a key combination, but there is also a tray icon that you can right click :)

Ooops&#8230; didn't see that, but yes, you're right!
I wonder why I didn't look for one&#8230;
Thanks!

Finally I will try this thing out!:guitar:

---

### Post by mc4100 on 2009-04-14
FYI, the main window will have the buttons and search at the button cut-off on a 1024x600 display (read your netbook), so you'll have to untick "constrain Y" in compiz and use the Alt key till it's fixed.

---

### Post by guraknugen on 2009-04-14
I am testing this thing right now and I think it works better than AllChars, that I used when I had Windows a few years ago. I have a few questions though:

In the date format selection dialogue, where is the ISO-8601 format? Can I add my own date formats? (Today's date is 2009-04-14, written in the ISO-8601 format, which is the same as the Swedish standard format as well as the standard format for many other countries)

For some strange reason my abbreviations suddenly stopped working. &#8221;Enable expansions&#8221; is checked. I know I did a lot in the settings dialogue, maybe I selected or unselected something that I shouldn't. Any suggestions? A few minutes ago my abbreviations were replaced by the appropriate phrase right after I hit Enter or Space or something like that, but now it doesn't. I can bring my phrases using the right click of the AutoKey icon, so&#8230; well, I don't know&#8230;

OK, I closed AutoKey and started it again and now it works&#8230; Strange anyway. Maybe a bug of some kind&#8230; 

And yes, åäöÅÄÖ works, which is nice!

And about positioning phrases: What's the idea about the space in &#8221;$(cursor )&#8221;? It didn't work without it&#8230;

Okay, apart from some minor issues, I have to say that I like this very much. Thanks!

I was planning to do something similar (but more simple) in C++, and maybe I will some day, but this seems to work well enough for me.

---

### Post by Shaun32 on 2009-04-14
> **cdekter said:**
> AutoKey will work in any X application, whether it be KDE, GNOME or otherwise.

To specifically fix the problem you've been having, install the package librsvg2-common

That worked!  The GUI popped up, at least.  I have yet to test it, but I'm assuming it works.  Thanks for sticking with me there!  Work may actually be fun tomorrow LOL because this is gonna make it a lot more efficient.

I'll be sure to post back if I have questions.

*Update* I have all my main aliases in there now.  Wow is that a cool program!  It will serve my needs very well.  I love the GUI.  Very helpful and much better than editing a config file.  Did some of you help develop it?  If so, nice work!

---

### Post by guraknugen on 2009-04-15
I ran into a strange problem:
When I use &#8221;[&#8221; and &#8221;]&#8221; in my phrases, they are replaced by &#8221;(&#8221; and &#8221;)&#8221; respectively. Why is that? Is there a workaround?

Example:
[MyXMLTag]$(cursor )[/MyXMLTag] &#8680; (MyXMLTag)(/MyXMLTag)
{MyXMLTag}$(cursor ){/MyXMLTag} &#8680; /MyXMLTag=//MyXMLTag=

Can it be that my keyboard layout isn't the standard US layout? Actually I have my own layout. It's like the standard Swedish layout with a lot of changes&#8230; I made my layout by editing the different **evdev** files. Maybe AutoKey doesn't care about **evdev**?

Well, I guess an ugly workaround would be to just find out what to write to make it write what I want&#8230;

Anyway, it looks to me, by studying the behaviour of this program, that it translate keystrokes rather than characters, is that correct?

---

### Post by guraknugen on 2009-04-15
> **guraknugen said:**
> 
Well, I guess an ugly workaround would be to just find out what to write to make it write what I want&#8230;

I entered every character I have on my keyboard (most keys have four different characters) into AutoKey, but when AutoKey printed them out there was no {[]} anywhere. Seems like a bug, doesn't it?

I also tried with the standard Swedish layout and it was worse. Numbers wasn't printed at all and {[]} became 7890 (that's the keys where they are located).

Hint: Swedish (and many other) keyboards' right Alt key is called "AltGr" and is used to bring out some extra characters, like &#8364;, £, $ and @. I have heard that standard US keyboards doesn't have this key and it seems to me that AutoKey doesn't detect that key at all. That explains why &#8221;[&#8221; was &#8221;(&#8221;, because my own kayboard layout has no numbers on the first line (I only have numbers on the num pad - why have them at two different places&#8230;?)

I don't know if I only complicated things now, hopefully not&#8230;

---

### Post by guraknugen on 2009-04-16
I have another question:
Can someone please explain how &#8221;Substitute preceding word&#8221; is supposed to work? It doesn't make any sense to me, but I am sure that's because I don't understand how to use it.

My first (and so far only) guess was that it could substitute the word before the command with something, like this:

Let's say that our abbreviation &#8221;a&#8221; will be substituted by &#8221;this is a test&#8221;. Then I thought I could create a new abbreviation &#8221;b&#8221;, that looks like this:
&#8221;My brother said that a$(sub )&#8221;, and when I type &#8221;b &#8221; in, for example, my text editor, it would be replaced by &#8221;My brother said that this is a test&#8221;

This, however, didn't work at all. I also tried to put a space right after &#8221;a&#8221;, but no luck.

Maybe I misunderstood it all, so please tell me more about the $(sub ) thing.

---

### Post by cdekter on 2009-04-20
> **guraknugen said:**
> I ran into a strange problem:
When I use ”[” and ”]” in my phrases, they are replaced by ”(” and ”)” respectively. Why is that? Is there a workaround?

Example:
[MyXMLTag]$(cursor )[/MyXMLTag] &#8680; (MyXMLTag)(/MyXMLTag)
{MyXMLTag}$(cursor ){/MyXMLTag} &#8680; /MyXMLTag=//MyXMLTag=

Can it be that my keyboard layout isn't the standard US layout? Actually I have my own layout. It's like the standard Swedish layout with a lot of changes… I made my layout by editing the different **evdev** files. Maybe AutoKey doesn't care about **evdev**?

Well, I guess an ugly workaround would be to just find out what to write to make it write what I want…

Anyway, it looks to me, by studying the behaviour of this program, that it translate keystrokes rather than characters, is that correct?

You are correct - Autokey receives keyboard codes as events and then queries the X server to determine what the keycode means. If you've used some non-standard way to set up a keyboard layout, it will not work correctly. You must set up your keyboard using the standard tools available in Gnome or KDE (or other DE of your choice) or using the setxkbmap command line tool.

---

### Post by cdekter on 2009-04-20
> **guraknugen said:**
> I have another question:
Can someone please explain how ”Substitute preceding word” is supposed to work? It doesn't make any sense to me, but I am sure that's because I don't understand how to use it.

My first (and so far only) guess was that it could substitute the word before the command with something, like this:

Let's say that our abbreviation ”a” will be substituted by ”this is a test”. Then I thought I could create a new abbreviation ”b”, that looks like this:
”My brother said that a$(sub )”, and when I type ”b ” in, for example, my text editor, it would be replaced by ”My brother said that this is a test”

This, however, didn't work at all. I also tried to put a space right after ”a”, but no luck.

Maybe I misunderstood it all, so please tell me more about the $(sub ) thing.

The $(sub ) token will be replaced by the word preceding the abbreviation, separated by a tilde (~). So if you set up a phrase like so:

This is a test phrase for $(sub )

then give it the abbreviation subs, if you type the following:

substitution~subs 

it will yield: This is a test for substitution

Note that only one preceding word will be substituted, and it must be separated from the abbreviation by a tilde. You can't substitute more than one word, as the cutoff occurs at the first space encountered before the tilde.

---

### Post by cdekter on 2009-04-20
> **guraknugen said:**
> I am testing this thing right now and I think it works better than AllChars, that I used when I had Windows a few years ago. I have a few questions though:

In the date format selection dialogue, where is the ISO-8601 format? Can I add my own date formats? (Today's date is 2009-04-14, written in the ISO-8601 format, which is the same as the Swedish standard format as well as the standard format for many other countries)



After the macro is inserted into the phrase, you can edit the value after the 'format=' parameter - this determines the format of the date that will be inserted.

> **guraknugen said:**
> For some strange reason my abbreviations suddenly stopped working. ”Enable expansions” is checked. I know I did a lot in the settings dialogue, maybe I selected or unselected something that I shouldn't. Any suggestions? A few minutes ago my abbreviations were replaced by the appropriate phrase right after I hit Enter or Space or something like that, but now it doesn't. I can bring my phrases using the right click of the AutoKey icon, so… well, I don't know…

OK, I closed AutoKey and started it again and now it works… Strange anyway. Maybe a bug of some kind… 



This is probably a bug. If you run Autokey from the terminal, it should print a stack trace in the terminal, if this ever happens again. If you could record this stack trace I could attempt to fix it.

> **guraknugen said:**
> And about positioning phrases: What's the idea about the space in ”$(cursor )”? It didn't work without it…


It's just the way the token parsing code is written, since some tokens can include parameters e.g. the date token. The space is needed to distinguish the name of the token from the parameter list.

---

### Post by guraknugen on 2009-04-22
> **cdekter said:**
> You are correct - Autokey receives keyboard codes as events and then queries the X server to determine what the keycode means. If you've used some non-standard way to set up a keyboard layout, it will not work correctly. You must set up your keyboard using the standard tools available in Gnome or KDE (or other DE of your choice) or using the setxkbmap command line tool.

I was told that Ubuntu doesn't use xkbmap anymore or that it's on its way out or something. I just make changes in the evdev files, but I wish there was a way doing it by adding something locally, maybe user setting files in a folder called ~/.evdev or something like that, that should add to the system defaults. That would make it easier to use custom settings, but okay, that's very OT here&#8230;

Anyway, still it seems like the right Alt key (called AltGr on Swedish keyboards) isn't recognized in some way by Autokey. Somehow the system have to know that I have to press AltGr+( to get a &#8221;[&#8221; on my keyboard using my personal layout, otherwise I wouldn't be able to type those chartacters at all, would I?

This AltGr has to be used on any Swedish keyboard to type £, $, @, &#8364;, {, [, ], }, \ and | (unless you prefer to use the Compose key or Ctrl+Shift+u Unicode) by default.

Is there a workaround for this problem? For example, can I use unicode numbers instead? Like u+005b for &#8221;[&#8221; or something that kind of force AutoKey to output the right character or key combination?

---

### Post by cdekter on 2009-04-22
> **guraknugen said:**
> Anyway, still it seems like the right Alt key (called AltGr on Swedish keyboards) isn't recognized in some way by Autokey. Somehow the system have to know that I have to press AltGr+( to get a ”[” on my keyboard using my personal layout, otherwise I wouldn't be able to type those chartacters at all, would I?

This AltGr has to be used on any Swedish keyboard to type £, $, @, €, {, [, ], }, \ and | (unless you prefer to use the Compose key or Ctrl+Shift+u Unicode) by default.

Is there a workaround for this problem? For example, can I use unicode numbers instead? Like u+005b for ”[” or something that kind of force AutoKey to output the right character or key combination?

Autokey does in fact know about AltGr and all other possible modifiers that X supports (there are six). Again, if the characters are not being output correctly, the problem is in your X keyboard map. Autokey will automatically use the Ctrl+Shift+u method to enter characters that are not found within your X keyboard map, so it seems to me that in your case the characters are mapped within X but the output is being altered somewhere else along the event chain.

---

### Post by guraknugen on 2009-04-23
> **cdekter said:**
> Autokey does in fact know about AltGr and all other possible modifiers that X supports (there are six). Again, if the characters are not being output correctly, the problem is in your X keyboard map. Autokey will automatically use the Ctrl+Shift+u method to enter characters that are not found within your X keyboard map, so it seems to me that in your case the characters are mapped within X but the output is being altered somewhere else along the event chain.

Is the fact that I defined my layout using Evdev a problem here? My first thought was to do it with xkbmap, but I was advised not to, since it was &#8221;the old way&#8221; to do it and on its way out, kind of. Or maybe I just misunderstand everything here.
Sorry for being so incredibly stupid.

---

### Post by cdekter on 2009-04-23
> **guraknugen said:**
> Is the fact that I defined my layout using Evdev a problem here? My first thought was to do it with xkbmap, but I was advised not to, since it was &#8221;the old way&#8221; to do it and on its way out, kind of. Or maybe I just misunderstand everything here.
Sorry for being so incredibly stupid.

I do think that using EVDEV is the cause of your problems here. I don't see how xkbmap is old or being replaced, I haven't seen anything to indicate that in all the documentation I've read about keyboard mappings in X. Aside from that, I'm puzzled why you've had to do such low-level customisations. Surely your keyboard would be supported by one of the standard mappings?

---

### Post by guraknugen on 2009-04-25
> **cdekter said:**
> I do think that using EVDEV is the cause of your problems here. I don't see how xkbmap is old or being replaced, I haven't seen anything to indicate that in all the documentation I've read about keyboard mappings in X. Aside from that, I'm puzzled why you've had to do such low-level customisations. Surely your keyboard would be supported by one of the standard mappings?

Okay, so explain this:
I created a new abbreviation, called &#8221;Kyoto Bojo&#8221; which is supposed to type &#8221;[{&#20140;&#37117;&#24917;&#24773;}]&#8221; when I type &#8221;kyotobojo&#8221;. The funny thing is that it prints out the japanese characters fine, but not [{}]. I don't have any Japanese characters (or symbols) included in my keyboard layout at all.

Another funny thing is that sometimes the &#8221;}&#8221; and &#8221;]&#8221; is typed too early. And a third funny thing is that when I use it here at this forum, the result is this:
> (/=[ U ]4eac
[ U ]90fd
[ U ]6155
[ U ]60c5
) [ /U ][ /U ][ /U ][ /U ]

Seems like the &#8221;}&#8221; (&#8221;=&#8221; with my keyboard layout as we discussed earlier) was typed VERY early this time. I'll try again:
> (/[ U ]4eac
[ U ]90fd
[ U ]6155
[ U ]60c5
=)
[ /U ][ /U ][ /U ][ /U ]

I added spaces inside the &#8221;[]&#8221; only to prevent underlining here in this forum.

A funny thing is also that the > [/U] things, which I guess means &#8221;End of Unicode special characters&#8221;, are all typed at the end, not after eaxh character.

Well, I guess we'll never know&#8230;
At least this keeps me wanting to do a similar program in C++&#8230; too bad I am such a crappy programmer though&#8230;

Oh,m and I just tested this on my Eee PC 900 (Swedish edition with Swedish keyboard layout). It's not an Ubuntu machine, I installed Mandriva Linux Free 2009.0 on it instead. However, I never touched the keyboard layout on that one, it's the standard Swedish layout just like it was when I installed Mandriva on its empty SSD. No customization there what so ever. Here's the result of > [ b ]$(cursor )[ /b ] on my Eee PC 900:
b/b
The cursor (which you can't see here) is placed BEFORE the string, which maybe is natural since four characters are omitted here, and AutoKey probably steps a number of positions backwards, as if the &#8221;[][]&#8221; were there.

I don't think that Mandriva use Evdev, but I'm not sure, since I don't know much about Mandriva at all. I just wanted to test it since Ubuntu Eee was so slow on that machine. Fortunately Mandriva was a lot faster and that's the only reason that I kept it so far. Even the cube runs smootly&#8230; if I tweak the settings a bit.

---

### Post by cdekter on 2009-04-25
> **guraknugen said:**
> Okay, so explain this:
I created a new abbreviation, called ”Kyoto Bojo” which is supposed to type ”[{&#20140;&#37117;&#24917;&#24773;}]” when I type ”kyotobojo”. The funny thing is that it prints out the japanese characters fine, but not [{}]. I don't have any Japanese characters (or symbols) included in my keyboard layout at all.


The reason the Japanese characters work is because they are not detected in your keyboard layout and are then entered using the standard GNOME Unicode method (ctrl+shift+u followed by the entity code). This doesn't work in Firefox because it doesn't support this entry method.

At this point I don't know why [{}] doesn't work for you. How are these characters entered on your keyboard normally? Shift? AltGr? No modifier? All of these should in theory work. 

> **guraknugen said:**
> 

Well, I guess we'll never know…
At least this keeps me wanting to do a similar program in C++… too bad I am such a crappy programmer though…



That would not solve this problem - you'd be using the same libraries, solving the same problems and encountering the same issues.

---

### Post by guraknugen on 2009-04-26
> **cdekter said:**
> The reason the Japanese characters work is because they are not detected in your keyboard layout and are then entered using the standard GNOME Unicode method (ctrl+shift+u followed by the entity code). This doesn't work in Firefox because it doesn't support this entry method.

At this point I don't know why [{}] doesn't work for you. How are these characters entered on your keyboard normally? Shift? AltGr? No modifier? All of these should in theory work.

As I said I have my own keyboard layout but these particular characters I didn't change, so they are like on a standard Swedish keyboard as follows:
```
AltGr+7 &#8594; {
AltGr+8 &#8594; [
AltGr+9 &#8594; ]
AltGr+0 &#8594; }
```

For example I have |, &#8240;, ¤ on Shift+7, +5 and +4 respectively, and they work fine, so it seems like the problem is related to the AltGr key.

Maybe this can be some kind of clue: I tried some Shift+AltGr combinations and those worked fine, BUT they worked like those Japanese characters, that Ctrl+Shift+u thing that doesn't work with Firefox (and obviously not with Opera either, since that's the web browser of my choice and it doesn't seem to work here&#8230;)

I have a standard 105 key keyboard.

Here is my suggestion for an &#8221;ugly fix&#8221;:
Add a check box somewhere that, if checked force AutoKey to use that Unicode method for every character that isn't included in the keyboard layout AND characters that need AltGr. If such a thing is not possible, then use the Unicode thing for ALL characters&#8230;

Here's another suggestion:
Add a feature that force AutoKey to use that Unicode method whenever the user wants, like a character combination of some kind. Maybe a &#8221;u&#8221; plus some other character that's not used a lot, or why not the famous &#8221;\&#8221; character&#8230; So if I want the "[" character I just type "\[" instead, and "\\" for the "\" character&#8230; That would not make it possible to achieve the "\" character the normal way so maybe "\\\" should mean "\ with Unicode method" and "\\" should mean "\"&#8230; Well, maybe too complicated, but maybe a check box for activating this feature would solve that problem&#8230; And it's still an ugly fix.

So in my example, I would have to input this in the Phrase Contents box to achieve [ b ]$(cursor )[ /b ]:
```
\[b\]$(cursor )\[/b\]
```

This would work for me until someone finds out why it doesn't work already.

> **cdekter said:**
> That would not solve this problem - you'd be using the same libraries, solving the same problems and encountering the same issues.

You are probably right, unfortunately&#8230; But it might take care of some speed problems, I would guess.

---

### Post by bas.janssen on 2009-04-28
I just installed 0.52.2-1, and no problem starting autokey.. 
but 'replace as you type' (as it walways did in previous versions..) doesn't seem to work annymore... 

I can only click the icon for a popup in wich i can type a abbreviation.... 

Am i missing something here ? 

There also seems to be a bug in the import function, 

The import hangs on newlines (new lines starting with a space char in the old abbr.ini) i.e. for a 3 line signature abbrr.  

reg = Regards, 
 Bas Janssen 
 Sales and Support 

I would really downgrade to 0.40.0 again, but this one stopped working after my ubuntu 8.1 - 9.4 dist-upgrade....  (any idea what caused this?)

---

### Post by cdekter on 2009-04-28
> **bas.janssen said:**
> I just installed 0.52.2-1, and no problem starting autokey.. 
but 'replace as you type' (as it walways did in previous versions..) doesn't seem to work annymore... 

I can only click the icon for a popup in wich i can type a abbreviation.... 

Am i missing something here ? 



Please note: due to breakage in the new version of X related to events and the 'Record' extension (used by Autokey to receive keyboard and mouse events), the replace-as-you-type feature will not work at all on Jaunty, until this bug in the X server is fixed. See here for more details:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/315456](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/315456)

> **bas.janssen said:**
> 

There also seems to be a bug in the import function, 

The import hangs on newlines (new lines starting with a space char in the old abbr.ini) i.e. for a 3 line signature abbrr.  

reg = Regards, 
 Bas Janssen 
 Sales and Support 


Haven't heard of this happening - please file a bug on the SourceForge tracker and I'll look into it.

---

### Post by bas.janssen on 2009-04-29
Thanks for your quick reply! 

OWh.. that's a real bummer... I use autokey a *lot*! Esp. for answering the same questions at our e-mail helpdesk (small isp) over and over again... 

The availability of autokey made me finally switch over to desktop-linux here in the first place.... Can't do my daily job without autokey in fact ;-)

I tested your latest release in a intrepid ibex virtual machine, and all things seem to work fine... 

If I look at the xserver bug it states: 

[https://bugs.freedesktop.org/show_bug.cgi?id=20500](https://bugs.freedesktop.org/show_bug.cgi?id=20500)
"RECORD is heavily broken at the moment and in desperate need of love. The
whole event delivery changed under it. How quickly that'll get fixed, I don't
know." 

So i guess this problem wil stand for a while?.... 

I also noticed that none of the shortcut key bindings seem to work in autokey on jaunty... The 'press key' button in the preferences also doesn't get keyboard events.. Same problem here?? 

This sadly means that autokey is un-usable on the newest ubuntu distributrion..... 

2 questions though: 

-- Is it possible to continue running jaunty, but to downgrade only the X server?? (and how should that be done?)

-- Do older versions of autokey use 'xrecord'? Might they work?  (tested 0.40, but no..)

Gues I'll be looking at a complete system re-install to get back on intrepid then ..... :-(

Thanks anyway, you guys make a *great* product!

---

### Post by cdekter on 2009-04-29
> **bas.janssen said:**
> Thanks for your quick reply! 

OWh.. that's a real bummer... I use autokey a *lot*! Esp. for answering the same questions at our e-mail helpdesk (small isp) over and over again... 

The availability of autokey made me finally switch over to desktop-linux here in the first place.... Can't do my daily job without autokey in fact ;-)



Glad to hear you found it useful :)

> **bas.janssen said:**
> 

[https://bugs.freedesktop.org/show_bug.cgi?id=20500](https://bugs.freedesktop.org/show_bug.cgi?id=20500)
"RECORD is heavily broken at the moment and in desperate need of love. The
whole event delivery changed under it. How quickly that'll get fixed, I don't
know." 

So i guess this problem wil stand for a while?.... 



Unfortunately yes. I am looking at other ways around this problem, but it will take some time.

> **bas.janssen said:**
> 

I also noticed that none of the shortcut key bindings seem to work in autokey on jaunty... The 'press key' button in the preferences also doesn't get keyboard events.. Same problem here?? 



Yes, that problem is caused by the same underlying issue.

> **bas.janssen said:**
> 

2 questions though: 

-- Is it possible to continue running jaunty, but to downgrade only the X server?? (and how should that be done?)

-- Do older versions of autokey use 'xrecord'? Might they work?  (tested 0.40, but no..)



I'm not sure what it would take to downgrade the X server but I imagine it would be a lot of work as you'd have to obtain display drivers for that X server version (the latest drivers wouldn't work due to ABI changes in the X server). It's a real pity as there have been many great improvements in Jaunty. 

The 0.30 series of Autokey used a really basic keylogger that watched the keyboard event device under /dev, however it is missing most of the features added in 0.40 so I don't know how much use it will be to you, or whether it will even work at all.

---

### Post by bas.janssen on 2009-05-04
> **cdekter said:**
> 
The 0.30 series of Autokey used a really basic keylogger that watched the keyboard event device under /dev, however it is missing most of the features added in 0.40 so I don't know how much use it will be to you, or whether it will even work at all.

Yes! you are a hero!! ;-) 

0.31.1 Works just fine in Ubuntu Jaunty :P No problem for me to go back a few versions while the X problems are sorted out. (have been using autokey since the first release)

Thanks again, bas

---

### Post by cdekter on 2009-05-08
I've just uploaded the new version to the SourceForge download page - version 0.53.0. It fixes several bugs that have been reported in the last 2 months, and also adds a proper installation script. AutoKey can now be installed for all users and each user can have their own configuration.

[Download here]("https://sourceforge.net/project/showfiles.php?group_id=216191&package_id=261010&release_id=681400")

Alternatively, add my [PPA]("https://launchpad.net/~cdekter/+archive/ppa") and follow the instructions on the PPA home page to install it via Synaptic/apt.

To migrate your existing configuration to the new version, install the new version, run it once and exit, then copy your existing autokey.bin to ~/.config/autokey

The home page has also been updated (it hadn't been changed since v0.31!). Note that the new version still will not work on Ubuntu 9.04, or any distribution using X server >= v1.5.2

---

### Post by urlwolf on 2009-06-09
One thing that I love from autohotkey and couldn't find in autokey is that one can map say right Alt key or right shift key.

Is this possible in autokey?

Using an ERPL a lot wears out my hands, and using my thumbs to send selection (right alt) is a godsent.

---

### Post by cdekter on 2009-06-10
> **urlwolf said:**
> One thing that I love from autohotkey and couldn't find in autokey is that one can map say right Alt key or right shift key.

Is this possible in autokey?

Using an ERPL a lot wears out my hands, and using my thumbs to send selection (right alt) is a godsent.

Can you give a more detailed description of what you're trying to achieve? Right Alt is available as <alt_gr> in AutoKey, but aside from that I don't really understand what you're trying to achieve.

---

### Post by urlwolf on 2009-06-13
> **cdekter said:**
> Can you give a more detailed description of what you're trying to achieve? Right Alt is available as <alt_gr> in AutoKey, but aside from that I don't really understand what you're trying to achieve.

great.
I just wanted to translate to linux something like this in autohotkey:

```
#WinActivateForce
	F4::
	IfWinExist, Console
	{
		Send ^c                    ; copy selection to clipboard
		WinActivate ; R Console
				save = %clipboard%
				sendinput, {Raw}%save%
				sendinput,{enter}
				Sleep 1000
				WinActivate, ahk_class Vim
	}

	; Ralt::
	; IfWinExist, Console
	{
		Send ^c                    ; copy selection to clipboard
		WinActivate ; R Console
				save = %clipboard%
				sendinput, {Raw}%save%
				sendinput,{enter}
				Sleep 1000
				WinActivate, ahk_class Vim
	}

```

---

### Post by cdekter on 2009-07-04
Good news - after months of dead ends and frustration, AutoKey now works on Ubuntu 9.04. I've just uploaded v0.54.0 to the SourceForge site and PPA. 

This new version no longer uses XRecord to receive events, so it will work on Jaunty and indeed on other distributions that don't have XRecord at all (e.g. Fedora). It also includes one or two minor bug fixes (see the change log).

Work will now move to focus on v0.60. This will be a major upgrade for AutoKey, as we will be adding the ability to write scripts for AutoKey in Python. This is intended to replace the current macro functionality, and in the long run will allow us to make AutoKey as powerful as AutoHotKey is on windows.

---

### Post by cdekter on 2009-07-06
Version 0.54.3 has just been released. All the bugs with the new keystroke interface should now be resolved. A big thank you to everyone who helped by testing the new version.

---

### Post by Sanjay on 2009-07-10
> we will be adding the ability to write scripts for AutoKey in Python.

OH

Hell yes.

---

### Post by manishmahabir on 2009-07-11
how soon can we have a version for karmic?
I am doing alpha testing....

---

### Post by mobilediesel on 2009-07-11
I wish I'd found this sooner! I've been missing AutoHotKey since leaving Windows XP behind. Autokey can't quite do everything AutoHotKey can but with Python scripting already mentioned for future release Autokey will definitely be ahead!

I am having one minor problem.
```
<a href='$(sub )'>$(cursor )</a>
```
It works fine if I typed the address that goes into the anchor tag. If I copy and paste the address nothing shows up where "$(sub )" points to. Since most of the links I would type into a web page are small this isn't a big deal but thought you'd like to know.

Now, hopefully I'll have learned enough Python to make it worth upgrading when you add that scripting to Autokey! :)

---

### Post by cdekter on 2009-07-11
> **manishmahabir said:**
> how soon can we have a version for karmic?
I am doing alpha testing....

I'm planning to do a release in the next few days - when I upload to the PPA I'll add a Karmic build.

---

### Post by cdekter on 2009-07-11
> **mobilediesel said:**
> It works fine if I typed the address that goes into the anchor tag. If I copy and paste the address nothing shows up where "$(sub )" points to. Since most of the links I would type into a web page are small this isn't a big deal but thought you'd like to know.

Yup, that's because AutoKey knows nothing about the clipboard/selection. It only records things you physically type. Having said that, it will be quite easy to do what you want using a script in the new version ;)

---

### Post by Nevon on 2009-07-11
May I ask how you're doing global hotkeys? I haven't tried the application yet, but I'm assuming you don't require the application window to have focus just for the hotkeys to work. 

I'm asking because I'm one of the authors of an application called Caffeine. It's an application that sits in your system tray and allows you to easily temporarily disable the screensaver and power saving mode. One of the features that we're looking to implement is a global hotkey to toggle the activation of the application, but it seems to be harder than you'd think. 

How did you solve it?

---

### Post by mobilediesel on 2009-07-11
> **cdekter said:**
> Yup, that's because AutoKey knows nothing about the clipboard/selection. It only records things you physically type. Having said that, it will be quite easy to do what you want using a script in the new version ;)

That will, of course, force me to study python. Would it just be Python or would it support other languages?

Either way, once it supports scripting of ANY kind I'll have all the power that AutoHotKey had and MORE! I can hardly wait!

---

### Post by cdekter on 2009-07-11
> **Nevon said:**
> May I ask how you're doing global hotkeys? I haven't tried the application yet, but I'm assuming you don't require the application window to have focus just for the hotkeys to work. 

I'm asking because I'm one of the authors of an application called Caffeine. It's an application that sits in your system tray and allows you to easily temporarily disable the screensaver and power saving mode. One of the features that we're looking to implement is a global hotkey to toggle the activation of the application, but it seems to be harder than you'd think. 

How did you solve it?

Simply put, by capturing every keypress via one of several methods. I also track the state of the modifier keys (Control, Alt, etc.). Then, a hotkey is simply any key pressed while a modifier is active. 

AutoKey is highly modularised, so it would be quite easy to build the necessary modules into your application. The particular modules used for the keyboard monitoring have quite a simple API. However, this is probably overkill for your purposes.

I would suggest having a look at how Gnome-Do registers its global hotkey. It believe it does this by adding an entry into GConf. Obviously this only works under Gnome but I'm sure KDE would have something similar.

---

### Post by cdekter on 2009-07-11
> **mobilediesel said:**
> That will, of course, force me to study python. Would it just be Python or would it support other languages?

Either way, once it supports scripting of ANY kind I'll have all the power that AutoHotKey had and MORE! I can hardly wait!

No, just Python for now.

Actually if you install a program called XClip, you could use a macro as follows:

```

<a href='$(exec output=true&command=xclip -o)'>$(cursor )</a>

```

When you run this, the 'exec' part of the phrase will be replaced with the contents of the clipboard.

---

### Post by Nevon on 2009-07-11
> **cdekter said:**
> Simply put, by capturing every keypress via one of several methods. I also track the state of the modifier keys (Control, Alt, etc.). Then, a hotkey is simply any key pressed while a modifier is active. 

AutoKey is highly modularised, so it would be quite easy to build the necessary modules into your application. The particular modules used for the keyboard monitoring have quite a simple API. However, this is probably overkill for your purposes.

I would suggest having a look at how Gnome-Do registers its global hotkey. It believe it does this by adding an entry into GConf. Obviously this only works under Gnome but I'm sure KDE would have something similar.

I've check into the Gconf-solution, but as our application should support as many different desktop environments as possible - it's not a viable solution for us. 

Could you perhaps point me to what modules in AutoKey are handling the hotkeys, so I can study them and perhaps find a way to adapt it to our needs?

---

### Post by cdekter on 2009-07-11
> **Nevon said:**
> Could you perhaps point me to what modules in AutoKey are handling the hotkeys, so I can study them and perhaps find a way to adapt it to our needs?

Certainly - take a look at iomediator.py and interface.py. Everything you'll need is contained in these two modules. Your application would hook into the IoMediator class to be notified of hotkeys.

---

### Post by mobilediesel on 2009-07-11
> **cdekter said:**
> No, just Python for now.

Actually if you install a program called XClip, you could use a macro as follows:

```

<a href='$(exec output=true&command=xclip -o)'>$(cursor )</a>

```

When you run this, the 'exec' part of the phrase will be replaced with the contents of the clipboard.

I'd heard of Xclip before, totally didn't think about it for this! Works perfect so far! I forgot about the $(exec ) feature. I'll have to play with that some more. This is damn-near a replacement for all of AutoHotKey now!

---

### Post by cdekter on 2009-07-12
A new version is out - 0.54.4. With any luck, this version will fix any remaining problems with handling of keymaps that use Alt-Grid (e.g. German, Canadian). It also includes many other bug fixes and improvements, and there is now also a Karmic package in the PPA.

---

### Post by rrfx on 2009-07-13
Thanks cdekter, this is the exact program i've been looking for on Ubuntu for several years! Was just looking through your python source... nice coding. Almost reported a bug in the datetime formatting, but yesterdays update fixed it! :) Thanks.

Since it's not in the manual yet the values valid for the datetime plugin are (from the bottom of [http://docs.python.org/library/datetime.html]("http://docs.python.org/library/datetime.html")):

```
Directive 	Meaning 	Notes
%a 	Locale’s abbreviated weekday name. 	 
%A 	Locale’s full weekday name. 	 
%b 	Locale’s abbreviated month name. 	 
%B 	Locale’s full month name. 	 
%c 	Locale’s appropriate date and time representation. 	 
%d 	Day of the month as a decimal number [01,31]. 	 
%f 	Microsecond as a decimal number [0,999999], zero-padded
%H 	Hour (24-hour clock) as a decimal number [00,23]. 	 
%I 	Hour (12-hour clock) as a decimal number [01,12]. 	 
%j 	Day of the year as a decimal number [001,366]. 	 
%m 	Month as a decimal number [01,12]. 	 
%M 	Minute as a decimal number [00,59]. 	 
%p 	Locale’s equivalent of either AM or PM
%S 	Second as a decimal number [00,61]. 	
%U 	Week number of the year (Sunday as the first day of the week)
%w 	Weekday as a decimal number [0(Sunday),6]. 	 
%W 	Week number of the year (Monday as the first day of the week)
%x 	Locale’s appropriate date representation. 	 
%X 	Locale’s appropriate time representation. 	 
%y 	Year without century as a decimal number [00,99]. 	 
%Y 	Year with century as a decimal number. 	 
%z 	UTC offset in the form +HHMM or -HHMM 
%Z 	Time zone name (empty string if the object is naive). 	 
%% 	A literal '%' character.
```

---

### Post by cdekter on 2009-07-13
Thanks for the reminder... added it to the FAQ page. :)

---

### Post by rrfx on 2009-07-13
> **cdekter said:**
> Thanks for the reminder... added it to the FAQ page. :)

No worries mate ;) I discovered last night that Python's timezone support is quite average. The datetime.now() function gives a "naive" object and as such the %z %Z format specifiers wont work.

---

### Post by guraknugen on 2009-07-14
I installed the new 0.54.4 version from the Intrepid repository and I noticed the following:

åäö doesn't work at all. So doesn't Japanese characters, for instance &#8221;&#20140;&#37117;&#24917;&#24773;&#8221; shows up as &#8221;äº¬é&#402;½æ&#8230;&#8226;æ&#402;&#8230;&#8221;.

I imported all my phrases from an older version, I think it was 0.52.something, by copying the autokey.bin file like described a few pages back in this thread.

Also expansions doesn't seem to work anymore.

I'm running Ubuntu 8.10.

Oh, by the way, {[]} now work for me (I posted here a few pages ago about that this didn't work on my system with a Swedish keyboard for any characters that requires the AltGr key, for example those i just mentioned plus $£@&#8364;).

---

### Post by cdekter on 2009-07-14
Have you checked the Troubleshooting page? 

[http://autokey.wiki.sourceforge.net/Troubleshooting](http://autokey.wiki.sourceforge.net/Troubleshooting)

There is a section on keyboard maps. If you are still having problems, you can raise a bug detailing what keyboard maps(s) you are using, how you are switching between them (if at all), how the problem keys are normally produced, etc.

---

### Post by guraknugen on 2009-07-15
> **cdekter said:**
> Have you checked the Troubleshooting page? 

[http://autokey.wiki.sourceforge.net/Troubleshooting](http://autokey.wiki.sourceforge.net/Troubleshooting)

There is a section on keyboard maps. If you are still having problems, you can raise a bug detailing what keyboard maps(s) you are using, how you are switching between them (if at all), how the problem keys are normally produced, etc.

Thanks!
&#8221;X Record: Will work in any distribution using X.org server prior to version 1.6. E.g. Ubuntu Jaunty upgrades the server to v1.6, and as a result XRecord will not work.
X EvDev: Should work in most cases, except if you are using 'exotic' hardware such as Bluetooth keyboards (or any keyboard device that does not use the EvDev X driver).
AT-SPI: Only works when the active window is a GTK-based application (including Firefox 3). Also requires certain configuration items in your Gnome environment to be enabled (see below).&#8221;

It was set to X EvDev. I changed to X Record and then restarted AutoKey.
Now not only expansions work, but also åäöÅÄÖ, Japanese characters and such.

I wonder why X EvDev doesn't work, however, since I know I use EvDev as long as it has been the default in Ubuntu (since 8.04 I think). I actually created my own keyboard layout by editing the evdev files.

I just tested AutoKey on one of my Wifes Ubuntu 9.04 computers and it worked fine with the X EvDev setting, and it didn't work with the X Record setting, just as we would expect.

Thanks!
Finally I just might upgrade to Ubuntu 9.04!

On my second laptop (an Eee PC with Mandriva Linux Free 2009.1) I also noticed that the 0.52 version no longer works (it worked with Mandriva Linux Free 2009.0), so I guess that Mandriva Linux Free 2009.1 also includes X server 1.6 and that Mandriva Linux Free 2009.0 includes the 1.5 version.

---

### Post by cdekter on 2009-07-15
> **guraknugen said:**
> 
I actually created my own keyboard layout by editing the evdev files.


This is probably why some of the characters were not output correctly. You might find this problem will resurface if you upgrade to 9.04 and start using the EvDev interface again. I would advise you to test it using a live-CD on your actual hardware, as some devices seem to simply not work using the EvDev interface (for example, the touchpad on my laptop is not recognised).

---

### Post by guraknugen on 2009-07-16
> **cdekter said:**
> This is probably why some of the characters were not output correctly. You might find this problem will resurface if you upgrade to 9.04 and start using the EvDev interface again. I would advise you to test it using a live-CD on your actual hardware, as some devices seem to simply not work using the EvDev interface (for example, the touchpad on my laptop is not recognised).

Why does everyone say that? It feels like everyone thinks that I'm an idiot or something.

Creating your own layout is actually very easy and there are not much that could go wrong at all. There are three files to edit and it's all very simple and it works 100% of the time. To be sure that I don't misspell anyuthing I copy and paste a lot and then, all I have to do is just to fill in what characters to be assigned to which keys. What could possibly go wrong? Nothing, nothing and nothing.

Besides I also tested everything with the original Swedish layout and that didn't work either.

However, now when following your instructions, everything works with AutoKey and Ubuntu 8.10 as well as with Ubuntu 9.04 on my wife's computer. Even Japanese characters that are NOT included in my keyboard layout works perfectly in most applications on my Ubuntu 8.10 system. The AltGr characters also works now, and I didn't change anything to make that happen, so obviously AutoKey has been changed, not my keyboard layout.

I also tested everything on another computer with Mandriva Linux Free 2009.0 a couple of months ago, and I never created a keyboard layout on that one, I always used the standard Swedish layout, and I had exactly the same problems as with Ubuntu on this computer.

Another problem I have sometimes, is that when I type fast and abbreviations are included in the text, one or two characters sometimes are placed at the wrong place. I will actually test this right now:

One of my abbreviations are &#8221;mandf&#8221;, and it is supposed to output &#8221;Mandriva Linux Free 2009.1&#8221;. Look now what happens when I type the following:
&#8221;I have mandf installed on my Eee PC.&#8221;

The result is different all the time, but here is a sample:

&#8221;I have mandfMandrivla Linux Free l2009.1 ed on my Eee PC.&#8221;

As you can see some characters are actually missing, so what I need to do to prevent this is to wait for the expansion, which sometimes makes autocorrections fail:

&#8221;I have Mandriva Linux Free 2009.1 installed on my Eee PC.&#8221;

Maybe this is impossible to correct and not a bug, and maybe the user just have to &#8221;take it or leave it&#8221;, I don't know.

It would also be nice if an option was added in the preferences that makes AutoKey startup automatically at start up. Yes, I know how to do that manually, but it would be convenient to achieve the same thing by just checking a check box.

Finally I want to add that I use AutoKey all the time and I'm glad that someone took the time to develop this.

---

### Post by smonk on 2009-07-18
Thank you, **cdekter**, for creating and maintaining AutoKey!

I recently switched to Ubuntu 9.04 from Windows and was glad to find AutoKey to replace ShortKeys on Windows. AutoKey (0.54.4) works great, but for some reason it won't expand text after the system has been suspended. (I've set Ubuntu to suspend the system when I close the lid of my Dell Inspiron 15n laptop and wake up when I reopen it.) Disabling and then re-enabling expansions makes no difference. Quitting and restarting AutoKeys gives this error message:
[INDENT] Error starting interface. Keyboard monitoring will be disabled.
Check your system/configuration.
Unable to connect to EvDev daemon:
[Errno 111] Connection refused
[/INDENT]Changing the Device Interface setting from X EvDev to AT-SPI makes no difference either. The only way I can get it to work again is to restart the whole system.

Any ideas for this linux newbie?

---

### Post by cdekter on 2009-07-18
I am aware of this bug, and working on a fix. In the meantime, you can restart the daemon without rebooting your PC. After resume, exit AutoKey, then run this from the terminal:

sudo invoke-rc.d autokey restart

Then start AutoKey again.

---

### Post by smonk on 2009-07-18
Thanks, it works! When I run the command from the terminal I get this message:

"pidfile /tmp/autokey-daemon.pid does not exist. Daemon not running?"

But there doesn't seem to be a problem as AutoKey works perfectly when I restart it.

The only problem is that I need AutoKey to memorize the command that recovers AutoKey. :) I suggest you build in this function and put a "Restart AutoKey" menu item in AutoKey's system tray right-click menu.

For now, I created a special profile in Terminal that automatically runs the command and then exits the terminal. I named the profile "autokeyreset", then I created a launcher (right-click on the system panel, select "Add to Panel", then "Custom Application Launcher") and entered this command:

gnome-terminal --window-with-profile=autokeyreset

I also created a launcher for AutoKey itself, so I've got it down to three clicks: quit, reset, start. There's probably a better way, but it's only temporary, right? In other words... Thanks in advance for fixing that bug! :)
[B]
July 22 UPDATE:[/B] Just upgraded to version 0.54.5 and AutoKey now seems to be working perfectly after waking the system from sleep. Well done!

---

### Post by guraknugen on 2009-07-19
Here's another problem that I run into now and then, and this happened with all the versions I tested so far since 0.5 or so:

First I make sure that AutoKey starts every time I log in to my computer, by adding AutoKey in System &#8594; Settings &#8594; Sessions.

This works perfectly almost every time, but some times when I start my computer I get an error message reading something like &#8221;AutoKey is already running (pid 6667)&#8221;. The Pid is of course not the same every time, but today when I checked, and it was 6667, that pid wasn't AutoKey, it was gnome-screensaver.

When I try to start it manually I get the same error message. If I kill the gnome-screensaver process and then try to start AutoKey manually, AutoKey is starting correctly.

I don't know if it's allways the gnome-screensaver that gets in its way, but next time it happens I will check for that.

---

### Post by cdekter on 2009-07-19
Thanks, I'll include a fix in the next release.

---

### Post by guraknugen on 2009-07-21
> **cdekter said:**
> Thanks, I'll include a fix in the next release.

I just tried to install the next release via the repository (for Intrepid, since I still use Intrepid) using the update manager:

```
E: /var/cache/apt/archives/autokey_0.54.5-0~intrepid_all.deb: subprocess new pre-removal-script caused error code 1
```

There are the exact error messages:
```
Preparing to replace autokey 0.54,4-0-intrepid (with &#8230;/autokey_0.54.5-intrepid_all.deb) &#8230;
[Errno 3] The process doesn't exist
invoke-rc.d: initscript autokey, action "stop" failed.
dpkg: Warning - old pre-removal-script returned error status 1
dpkg - trying script from the new package instead &#8230;
[Errno 3] The process doesn't exist
invoke-rc.d: initscript autokey, action "stop" failed.
dpkg: Error when managing /var/cache/apt/archives/autokey_0.54.5-0-intrepid_all.deb (--unpack):
sub process new pre-removal-script caused error code 1
pidfile /tmp/autokey-daemon.pid already exist. Daemon already running?
invoke-rc.d: initscript autokey, action "start" failed.
```
&#8230;and so on&#8230; (I couldn't copy and paste it so I just typed it manually).

First time I tried I had autokey running, second time I cancelled it before trying to update.

---

### Post by guraknugen on 2009-07-21
> **guraknugen said:**
> I just tried to install the next release via the repository (for Intrepid, since I still use Intrepid) using the update manager:

```
E: /var/cache/apt/archives/autokey_0.54.5-0~intrepid_all.deb: subprocess new pre-removal-script caused error code 1
```

Now I logged out, switched to British English (instead of Swedish), logged in and opened a console, then typing &#8221;sudo apt-get install autokey&#8221;. All this to be able to copy and paste all the error message in English instead of translating them from Swedish. However, when I did this, the installation worked perfectly without any errors&#8230;

So something is obviously wrong and it seems to be related to language setting or something like that, and since I guess I'm the only non-English speaking user around I guess this won't be fixed, ever. Am I right? Of course I am. But that doesn't matter much. At least I know now how to get around the problem.

---

### Post by cdekter on 2009-07-21
Try this:

```
sudo rm /tmp/autokey-daemon.pid
sudo apt-get upgrade
```

---

### Post by guraknugen on 2009-07-22
> **cdekter said:**
> Try this:

```
sudo rm /tmp/autokey-daemon.pid
sudo apt-get upgrade
```

Well, I guess I can't now, since the update was successful when I switched to British English, can I? I'll try that for the next update if it fails again.

---

### Post by guraknugen on 2009-08-01
How can I make a cursor abbreviation to work without having to confirm with a mouse click?

For example, I have this simple phrase:

```
<b>$(cursor )</b>
```

The abbreviation for it is:
```
ft
```

Now, I type:
```
ft&#8629;
```

What happens now is that a small button appears near the mouse pointer, containing the name of the phrase (&#8221;Fetstil&#8221; in this case), that I have to click to execute the thing. I really hate that, so how can I skip that button thing?

---

### Post by cdekter on 2009-08-01
The default behaviour is to not show that popup. Have  you by any chance enabled the "Always prompt before pasting this phrase" option.

---

### Post by guraknugen on 2009-08-01
> **cdekter said:**
> The default behaviour is to not show that popup. Have  you by any chance enabled the "Always prompt before pasting this phrase" option.

He he&#8230; yes&#8230;:o
I didn't even realize that there was such a setting. I don't know why I didn't see that until now.

Sorry.

---

### Post by cdekter on 2009-08-03
Work is 90% complete on version 0.60.0, and I would like to invite anyone who is interested (and prepared to put up with some bugs) to test it. 

20,000 foot overview:
[LIST]
[*]About three quarters of the code has been completely rewritten/refactored. 
[*]The UI has been completely rebuilt using PyKDE4/PyQT4, and redesigned for better interaction (e.g. drag-n-drop on the tree widget is now possible).
[*]The Python scripting feature is largely finished. It includes a built-in code editor using Scintilla, complete with API autocomplete and calltips. 
[*]Macros are no longer supported, as the same effect can be achieved using scripts.
[/LIST]

I've only tested it on Jaunty thus far, but it should run on Intrepid. Hardy is not supported any more as the KDE APIs from KDE4.0 were fairly incomplete at that stage.

Some screenshots:

[[IMG]http://i847.photobucket.com/albums/ab37/cdekter/th_configwindow_new.jpg[/IMG]](http://s847.photobucket.com/albums/ab37/cdekter/?action=view&current=configwindow_new.jpg)

[[IMG]http://i847.photobucket.com/albums/ab37/cdekter/th_settings_new.jpg[/IMG]](http://s847.photobucket.com/albums/ab37/cdekter/?action=view&current=settings_new.jpg)

To install it, download the appropriate deb:
[Intrepid]("http://autokey.sourceforge.net/downloads/autokey_0.60.0-0~intrepid_all.deb")
[Jaunty]("http://autokey.sourceforge.net/downloads/autokey_0.60.0-0~jaunty_all.deb")

---

### Post by mobilediesel on 2009-08-03
> **cdekter said:**
> I've only tested it on Jaunty thus far, but it should run on Intrepid. Hardy is not supported any more as the KDE APIs from KDE4.0 were fairly incomplete at that stage.

Awww. I was ready to test until "Hardy is not supported any more"

At least the "exec" feature still lets me have some scripting. Although now I'm considering upgrading instead of waiting for the next LTS version of Xubuntu.

---

### Post by urlwolf on 2009-08-10
Just a quick note to say that I love this project.
It was sorely needed. Autohotkey is a neat invention, and now you have done it with a proper language (python! ahk doesn't even have arrays).

I can imagine this project to steal a lot of attention in the linux world.

---

### Post by mfseeker on 2009-08-15
Chris,

I have been using AutoKey and happily following and submitting to the help forum for many weeks. Suddenly, I have lost access to that forum. When I follow links such as 
[https://sourceforge.net/forum/message.php?msg_id=7552813](https://sourceforge.net/forum/message.php?msg_id=7552813), I get this message: 
[B]Permission Denied 
 Access to this page is restricted (either to project members or to project administrators) and you do not meet the requirements to access this page. Please contact the administrator of this project for further assistance. [/B]

I also no longer receive the email notifications for the forum.

I have spent some hours trying to figure this out and fix it, as I would like to continue reading and posting.

And, yes, I would like to be part of your beta test group.

Stan Armstrong (mfseeker)

---

### Post by cdekter on 2009-08-15
The reason for the error is that the forum is disabled because we have moved to Google Code project hosting. Instead of the forum there is now an autokey-users group on Google Groups. Follow the link from the AutoKey home page ([http://autokey.sourceforge.net](http://autokey.sourceforge.net), then click on Users Group).

---

### Post by guraknugen on 2009-08-18
The new 0.60 version just appeared in the Ubuntu update manager on both my machines (8.10 and 9.04) and I tried to update on both computers. Both failed, just like last time there was an update.

Here are the error messages on the 8.10 machine, I think they are pretty much the same on the 9.04 as well:

```
Compiling /usr/lib/python2.5/site-packages/autokey/ui/configwindow.py ...
  File "/usr/lib/python2.5/site-packages/autokey/ui/configwindow.py", line 37
    from .. configmanager import *
SyntaxError: 'import *' not allowed with 'from .'

Compiling /usr/lib/python2.5/site-packages/autokey/ui/notifier.py ...
  File "/usr/lib/python2.5/site-packages/autokey/ui/notifier.py", line 24
    from .. configmanager import *
SyntaxError: 'import *' not allowed with 'from .'

Compiling /usr/lib/python2.5/site-packages/autokey/ui/popupmenu.py ...
  File "/usr/lib/python2.5/site-packages/autokey/ui/popupmenu.py", line 26
    from .. configmanager import *
SyntaxError: 'import *' not allowed with 'from .'

Compiling /usr/lib/python2.5/site-packages/autokey/ui/settingsdialog.py ...
  File "/usr/lib/python2.5/site-packages/autokey/ui/settingsdialog.py", line 24
    from .. configmanager import *
SyntaxError: 'import *' not allowed with 'from .'

pycentral: pycentral pkginstall: error byte-compiling files (33)
pycentral pkginstall: error byte-compiling files (33)
dpkg: fel vid hantering av autokey (--configure):
 underprocess post-installation script gav felkod 1
Fel uppstod vid hantering:
 autokey
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
:confused:

Do I miss some packages? Isn't the update manager supposed to take care of that?

Suggestions?
Thanks.

---

### Post by cdekter on 2009-08-18
Hmm... well to be honest I haven't tested in 8.10 - I don't have a machine running that any more. Looks like Python 2.6 added some new features to the relative import capability that 2.5 can't cope with. I'll have to ditch the relative imports. 

I find it hard to believe that you had the same failure on 9.04 though - I've tested it thoroughly there. It would help if you could post the actual errors. Also, Ubuntu Forums Community Cafe is not the right place for support requests - please use our group at Google Groups: [http://groups.google.com/group/autokey-users](http://groups.google.com/group/autokey-users)

---

### Post by guraknugen on 2009-08-19
> **cdekter said:**
> Hmm... well to be honest I haven't tested in 8.10 - I don't have a machine running that any more. Looks like Python 2.6 added some new features to the relative import capability that 2.5 can't cope with. I'll have to ditch the relative imports. 

I find it hard to believe that you had the same failure on 9.04 though - I've tested it thoroughly there. It would help if you could post the actual errors. Also, Ubuntu Forums Community Cafe is not the right place for support requests - please use our group at Google Groups: [http://groups.google.com/group/autokey-users](http://groups.google.com/group/autokey-users)

Thanks. I didn't know about that group.

I just tried it again on my wife's computer (the one with Ubuntu 9.04) and this time, after closing Autokey and typing the commands below, it installed without problems.

```
sudo rm /tmp/autokey-daemon.pid
sudo apt-get upgrade

```

However, the program didn't work as good as the previous version, but I saw that someone already wrote about that at that group so I just contributed with a post there.

---

### Post by guraknugen on 2009-08-19
I installed Python 3 from the Ubuntu 8.10 repos and then tried to update AutoKey again. It worked. Thanks.

---

### Post by smonk on 2009-08-19
The new version 0.60.x doesn't work for me and I want to downgrade to version 0.54.5, which worked perfectly. After backing up the config (data) files, I completely removed version 0.60.x in Synaptic. I downloaded autokey_0.54.5.tar.gz, but I'm a Linux newbie and don't know how to install it manually. Can someone tell me how?

My system is Ubuntu 9.04

Thanks!

---

### Post by guraknugen on 2009-08-19
> **smonk said:**
> The new version 0.60.x doesn't work for me and I want to downgrade to version 0.54.5, which worked perfectly. After backing up the config (data) files, I completely removed version 0.60.x in Synaptic. I downloaded autokey_0.54.5.tar.gz, but I'm a Linux newbie and don't know how to install it manually. Can someone tell me how?

My system is Ubuntu 9.04

Thanks!

There is a file in that archive called INSTALL which contains install instructions. I tried to follow them but two of the system requirements was not fulfilled. One of them was that Python &#10878;2.6 is required, but I just installed 3.0 so I don't know why it complains on that one. Maybe because I also have Python 2.5 installed?

So I guess that I just have to wait patiently until there is a new version that meet my needs, or run the old 0.52.2 which doesn't need an installation at all.

---

### Post by dustigroove on 2009-10-01
Just as a note, autokey-gtk can be found in the PPA repository for those having issues with using the original KDE version.

---

### Post by haciendadad on 2009-11-14
I am trying to set this up for my wife's business and I an fairly comfortable with Ubuntu (9.10), but after I downloaded this and extracted this to my Desktop a folder called "build" was put on the Desktop.  I didn't know what to do next, the INSTALL instructions were pretty sparse so I am stuck.

I did run this command that I found on some blog:
sudo apt-get install python-xlib python-gamin python-notify python-configobj

I've read about something called AutoKey.sh but I only see a AutoKey file.  I made it executable, but that didn't do anything.

I must be an idiot to be the only one who just doesn't get it.

Please tell me what I need to do next to get it to run.

Thanks.

---

### Post by dustigroove on 2009-11-14
> **haciendadad said:**
> I am trying to set this up for my wife's business and I an fairly comfortable with Ubuntu (9.10), but after I downloaded this and extracted this to my Desktop a folder called "build" was put on the Desktop...

No need to build or compile, just add the PPA repository. You can do this from within the Synaptic package manager or by manually adding the lines to your sources.list file.

Instructions to add can be found on Chris's Launchpad page:
[https://launchpad.net/~cdekter/+archive/ppa](https://launchpad.net/~cdekter/+archive/ppa)

Then just install through Synaptic or 'sudo apt-get install autokey-gtk' in a terminal.

Cheers

---

### Post by mobilediesel on 2009-11-14
I've finally updated to AutoKey (GTK UI) 0.60.7a. Now the only problem I have is that I can't find anywhere that lists the replacement for the old **$(cursor )** function. That kinda breaks a couple of my replacement texts.

Am I just missing it in the wiki on google code?

---

### Post by haciendadad on 2009-11-14
> 
No need to build or compile, just add the PPA repository. You can do this from within the Synaptic package manager or by manually adding the lines to your sources.list file.

Instructions to add can be found on Chris's Launchpad page:
[https://launchpad.net/~cdekter/+archive/ppa](https://launchpad.net/~cdekter/+archive/ppa)

Then just install through Synaptic or 'sudo apt-get install autokey-gtk' in a terminal.


Sheesh that was easy!  Thanks!!!!!!

---

### Post by cdekter on 2009-11-14
> **mobilediesel said:**
> I've finally updated to AutoKey (GTK UI) 0.60.7a. Now the only problem I have is that I can't find anywhere that lists the replacement for the old **$(cursor )** function. That kinda breaks a couple of my replacement texts.

Am I just missing it in the wiki on google code?

The macros from the earlier versions won't work in v0.6x. You can achieve the same effect with a script:

```

firstPart = "First part of the text. Cursor ->"
secondPart = "<- second part"
keyboard.send_keys(firstPart + secondPart)
keyboard.send_key("<left>", len(secondPart))

```

---

### Post by mobilediesel on 2009-11-15
> **cdekter said:**
> The macros from the earlier versions won't work in v0.6x. You can achieve the same effect with a script:

```

firstPart = "First part of the text. Cursor ->"
secondPart = "<- second part"
keyboard.send_keys(firstPart + secondPart)
keyboard.send_key("<left>", len(secondPart))

```

Exactly what I was looking for! Thanks!

I've been messing with Python a bit lately anyway so this gives me another reason to learn.

I was really missing AutoHotkey from Windows but this looks like it will now be FAR more powerful!

---

### Post by urlwolf on 2009-11-15
I've looked at the docs, but not sure this is possible...
Can I remap right click to middle click *just when FF is the active window*?

Thanks

---

### Post by mobilediesel on 2009-11-15
I have a small script that changes selected text to lower case that pretty much works
```
text = clipboard.get_selection()
keyboard.send_keys("<delete>")
keyboard.send_keys(text.lower())
```
except for setting a hotkey for it. It works fine from the tray menu but when I set a hotkey for it, it doesn't trigger with the hotkey. I've tried nearly every key on the keyboard with nearly every combination of CTRL, ALT, SHIFT and SUPER.

I just wonder if it's yet something else I'm missing. :)

This small script allowed me to uninstall an addon in firefox so I'm already quite happy with it so far!

---

### Post by GeBo on 2009-12-26
I've been trying all evening to get this script to work, but I can't...

```
regels = int(dialog.input_dialog(title="Aantal verzen", message="Geef het aantal verzen", default="")) + 1

for t in range(2, regels):
    keyboard.send_keys("<ctrl>+f")
    time.sleep(0.3)
    keyboard.send_keys("%s" % t)
    keyboard.send_keys("<enter>")
    keyboard.send_keys("<escape>")
    time.sleep(0.2)
    keyboard.send_keys("<left>")
    keyboard.send_keys("<right>")
    keyboard.send_keys("<enter>")

```

If I put an actual value in the for loop, like range(2, 25) it does work, but with a variable it doesn't. I can't figure this one out...

Any suggestions?

---

### Post by cdekter on 2009-12-26
It doesn't work because dialog.input_dialog() actually returns 2 values - the return code of the dialog process and the value entered. This is so you can handle the situation where cancel is clicked in the dialog, instead of a value being entered. This should work:

```

result, regels = dialog.input_dialog(title="Aantal verzen", message="Geef het aantal verzen")

if result == 0:
    for t in range(2, int(regels)):
        keyboard.send_keys("<ctrl>+f")
        time.sleep(0.3)
        keyboard.send_keys("%s" % t)
        keyboard.send_keys("<enter>")
        keyboard.send_keys("<escape>")
        time.sleep(0.2)
        keyboard.send_keys("<left>")
        keyboard.send_keys("<right>")
        keyboard.send_keys("<enter>")
```

Also, you can combine several keys together for keyboard.send_keys() rather than having each key as a separate method call.

---

### Post by GeBo on 2009-12-27
Great! This works indeed. Like a charm!

Thank you so much.

---

### Post by kaspin on 2010-01-31
[SIZE="3"][SIZE="3"][FONT="Comic Sans MS"][COLOR="Navy"]I can get autokey (loaded into ubuntu 9.10 with synaptic) to send simple text using abbreviations under 'phrases'. However, I want to sign into email accounts and was wondering if it possible to send, e.g. 
"myaddress@hotmail.com"
 <tab>
 "password"
 <enter>
using just one abbreviation (as I could do in Autohotkey).
If so, I would be very grateful if someone could explain how, in a language that geriatric simpletons such as myself could understand. Or if there's a tutorial covering this sort of thing, a reference to it would be appreciated.
Thanks a bunch.........kaspin [/COLOR][/FONT][/SIZE][/SIZE][SIZE="3"][/SIZE][SIZE="2"][/SIZE][SIZE="3"][/SIZE]

---

### Post by cdekter on 2010-01-31
Have you tried simply putting the text you want into a phrase like so?

[email]myaddress@hotmail.com[/email]<tab>password<enter>

That should work.

There are plenty of examples in the various wiki pages accessible from the [project page]("http://autokey.googlecode.com"). There is also a [Google Group]("http://groups.google.com/group/autokey-users") where you should post questions like this (and many of them are already answered if you search the group's history).

---

### Post by kaspin on 2010-02-02
[FONT=Comic Sans MS][SIZE=2][COLOR=Navy]Hi cdekter,
Works a treat....so simple! Thanks a lot.
Will check out those links you mentioned as I have another problem on my other machine - I selected the option to run autokey in the background, but can't remember assigning a special hotkey to reinstate the config window, so I'm stuck without a tray icon - even deleting and reinstalling autokey doesn't solve it. Happy days..................
kaspin[/COLOR][/SIZE][/FONT]

---

### Post by kaspin on 2010-02-02
[FONT="Comic Sans MS"][SIZE="2"][COLOR="Navy"]Hi again cdekter,
It's a good evening - looked in the links you gave and got back the tray icon by typing in the terminal:
$ killall autokey
$ autokey -c
Merci   kaspin[/COLOR][/SIZE][/FONT]

---

### Post by kaspin on 2010-02-24
[FONT="Comic Sans MS"][SIZE="2"][COLOR="Navy"]Hello again,
I've now installed Autokey (version 0.61.2 - KDE 4.3.2) on my PC and 2 laptops, all running Ubuntu 9.10, and I'm glad to say that I can do everything in Autokey that I used to do with Autohotkey under Windoze. However, on my PC the keyboard is French (the laptops are QWERTY), yet Autokey treats it as QWERTY. Is there a way around this, please?
kaspin[/COLOR][/SIZE][/FONT]

---

### Post by cdekter on 2010-02-24
> **kaspin said:**
> [FONT="Comic Sans MS"][SIZE="2"][COLOR="Navy"]Hello again,
I've now installed Autokey (version 0.61.2 - KDE 4.3.2) on my PC and 2 laptops, all running Ubuntu 9.10, and I'm glad to say that I can do everything in Autokey that I used to do with Autohotkey under Windoze. However, on my PC the keyboard is French (the laptops are QWERTY), yet Autokey treats it as QWERTY. Is there a way around this, please?
kaspin[/COLOR][/SIZE][/FONT]

AutoKey determines your keyboard layout by asking X for it. You need to configure your layout using xkbmap (which I believe KDE does do if you enable keyboard maps in the Control Panel thingo). You might need to play around with the settings a bit to get it working.

---

### Post by kaspin on 2010-02-25
[FONT="Comic Sans MS"][SIZE="2"][COLOR="Navy"]Hi cdekter,
You're right - it was an Ubuntu problem. I deleted all possible keyboard configurations under System/Preferences and now Autokey works perfectly.
Thanks again for your help,  kaspin [/COLOR][/SIZE][/FONT]

---

### Post by mobilediesel on 2010-04-11
I just received an update to version 0.70.0. After figuring out that **python-json** had to be installed, I get the following message on startup:
```
Error starting interface. Keyboard monitoring will be disabled.
Check your system/configuration.
```

I tried restarting autokey and now I get:

```
Fatal error starting AutoKey.
'module' object has no attribute 'load'
```

Then in the terminal it spits out:

```
Traceback (most recent call last):
  File "/usr/bin/autokey-gtk", line 7, in <module>
    a = Application()
  File "/usr/lib/python2.5/site-packages/autokey/gtkapp.py", line 82, in __init__
    self.show_error_dialog(_("Fatal error starting AutoKey.\n") + str(e))
  File "/usr/lib/python2.5/site-packages/autokey/gtkapp.py", line 247, in show_error_dialog
    dlg.run()
KeyboardInterrupt

```

---

### Post by cdekter on 2010-04-11
Aaargh... I'm really regretting putting out that build for Hardy now. I'll look into this but I can't guarantee that I'm going to have time to fix it as I don't have any machines lying around still running that version (virtual or otherwise). My advice would be to try and use apt-get to roll back to the previous version (hopefully the packages are still in your cache).

---

### Post by pakki on 2010-04-13
using autokey 0.70.0 launched via accessories>Autokey (qt) or autokey (gtk)

I hav two icons dont knw why??

However whichever i run following occurs & i am saddened:(
[IMG]http://i41.tinypic.com/4q3a4k.jpg[/IMG]

---

### Post by cdekter on 2010-04-13
If you are on gnome:

sudo apt-get remove autokey autokey-qt

If you are on KDE:

sudo apt-get remove autokey autokey-gtk

A new version was released 12 hours ago, please upgrade and check again

---

### Post by mobilediesel on 2010-04-13
After today's update I get:
[ATTACH]153185[/ATTACH]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=153185&d=1271196684[/IMG]

If anyone has a copy of the previous version, that would be great until the new one works with Hardy.

---

### Post by cdekter on 2010-04-13
The new version works fine on Hardy. See here on how to post useful debugging information.

[http://code.google.com/p/autokey/wiki/Troubleshooting](http://code.google.com/p/autokey/wiki/Troubleshooting)

---

### Post by mobilediesel on 2010-04-14
> **cdekter said:**
> The new version works fine on Hardy. See here on how to post useful debugging information.

[http://code.google.com/p/autokey/wiki/Troubleshooting](http://code.google.com/p/autokey/wiki/Troubleshooting)

I finally found what was causing the problem. I've been using **xmodmap -e 'remove lock = Caps_Lock'** to disable the caps lock key. AutoKey doesn't seem to like that. Is it possible to disable the caps lock key in any way that would be compatible with AutoKey?

I'm using OpenBox so maybe there's a way to kill caps lock with the rc.xml that won't disable AutoKey's keyboard monitoring.

---

### Post by cdekter on 2010-04-14
> **mobilediesel said:**
> I finally found what was causing the problem. I've been using **xmodmap -e 'remove lock = Caps_Lock'** to disable the caps lock key. AutoKey doesn't seem to like that. Is it possible to disable the caps lock key in any way that would be compatible with AutoKey?

Somebody else had a similar problem - I've already got a fix for it. Will be in the next release.

---

### Post by mobilediesel on 2010-04-14
> **cdekter said:**
> Somebody else had a similar problem - I've already got a fix for it. Will be in the next release.

Nice!

Try getting Microsoft to work on stuff so quickly.

I also noticed the SysTray icon looks different again. It's better than the basic black "A" since my desktop wallpaper is dark and the taskbar/systray are transparent!

---

### Post by DAE_JA_VOO on 2010-04-17
Hey cdekter!

I need your help please :D  I've been a Windows user for some time now, and I just moved over to Ubuntu, and Autohotkey is the one app I absolutely can't live without. Seriously, I would drop Ubuntu and go back to Windows just for Autohotkey. So your app is my saving grace! only problem is that I don't know a thing about scripting. What I did in AHK was make certain keystrokes send others. For example, pressting Alt+D would actually send Ctrl+W, which would close the tab in my browser. Pressing Caps lock+Q would open a link, etc. Here's the script file I used in AHK. Please help me to port this to your app. Thanks man!

```
SetCapsLockState, AlwaysOff


LAlt & w::
      	       Send,^c ^t ^k ^v {Enter}
return

LAlt & q::
               Send,^{PgUp}
return

LAlt & s::
               Send,^{PgDn}
return

LAlt & d::
               Send,^w
return




;Web Links:



CapsLock & q::
               Send,^t http://forums.pcformat.co.za/index.php {Enter}
return

CapsLock & w::
               Send,^t http://www.systemshock.co.za/forums/index.php?act=idx {Enter}
return

CapsLock & e::
               Send,^t http://forums.prophecy.co.za/ {Enter}
return

CapsLock & r::
               Send,^t http://www.xbox-360.co.za/forum/ {Enter}
return

CapsLock & t::
               Send,^t http://www.pcbuyersguide.co.za/forum.php {Enter}
return

CapsLock & s::
               Send,^t http://www.speedsolving.com/index.php {Enter}
return

CapsLock & 1::
               Send,^t http://www.facebook.com/home.php? {Enter}
return

CapsLock & 2::
               Send,^t http://www.facebook.com/?sk=messages&ref=mb{Enter}
return

CapsLock & c::
               Send,^t http://cubemania.org/puzzles/2/times {Enter}
return

CapsLock & b::
               Send,^t http://forums.bit-tech.net/{Enter}
return
```

---

### Post by cdekter on 2010-04-17
I can tell you right off the bat that your shortcuts with Capslock aren't possible with AutoKey. Most of the others would be possible AFAICT. However, could I suggest that you repost your question on the [AutoKey Users group]("http://groups.google.com/group/autokey-users") and I'll answer it in full there, so that others may benefit and it becomes part of the searchable history on the group.

---

### Post by afbase on 2010-04-21
I try opening autokey and i get 
```
$ autokey-gtk -l
INFO - root - Initialising application
INFO - config-manager - Loading config from existing file: /home/user/.config/autokey/autokey.json
ERROR - config-manager - Error while loading configuration. Cannot recover.


```
fatal error starting autokey.No JSON object could be decoded

Checking the log file I got this:
```

INFO - root - Initialising application
INFO - config-manager - Loading config from existing file: /home/clinton/.config/autokey/autokey.json
ERROR - config-manager - Error while loading configuration. Cannot recover.
ERROR - root - Fatal error starting AutoKey: No JSON object could be decoded
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/autokey/qtapp.py", line 91, in __init__
    self.initialise(args.isSet("configure"))
  File "/usr/lib/python2.6/dist-packages/autokey/qtapp.py", line 128, in initialise
    self.configManager = get_config_manager(self)
  File "/usr/lib/python2.6/dist-packages/autokey/configmanager.py", line 113, in get_config_manager
    configData = json.load(pFile)
  File "/usr/lib/python2.6/json/__init__.py", line 267, in load
    parse_constant=parse_constant, **kw)
  File "/usr/lib/python2.6/json/__init__.py", line 307, in loads
    return _default_decoder.decode(s)
  File "/usr/lib/python2.6/json/decoder.py", line 319, in decode
    obj, end = self.raw_decode(s, idx=_w(s, 0).end())
  File "/usr/lib/python2.6/json/decoder.py", line 338, in raw_decode
    raise ValueError("No JSON object could be decoded")
ValueError: No JSON object could be decoded

```

---

### Post by cdekter on 2010-04-21
Questions and issues like this one need to be posted to the Google group for AutoKey:

[http://groups.google.com/group/autokey-users/](http://groups.google.com/group/autokey-users/)

Mods, please close this thread.

---

### Post by mobilediesel on 2010-04-21
> **afbase said:**
> I try opening autokey and i get 
```
$ autokey-gtk -l
INFO - root - Initialising application
INFO - config-manager - Loading config from existing file: /home/user/.config/autokey/autokey.json
ERROR - config-manager - Error while loading configuration. Cannot recover.


```
fatal error starting autokey.No JSON object could be decoded

Checking the log file I got this:
```

INFO - root - Initialising application
INFO - config-manager - Loading config from existing file: /home/clinton/.config/autokey/autokey.json
ERROR - config-manager - Error while loading configuration. Cannot recover.
ERROR - root - Fatal error starting AutoKey: No JSON object could be decoded
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/autokey/qtapp.py", line 91, in __init__
    self.initialise(args.isSet("configure"))
  File "/usr/lib/python2.6/dist-packages/autokey/qtapp.py", line 128, in initialise
    self.configManager = get_config_manager(self)
  File "/usr/lib/python2.6/dist-packages/autokey/configmanager.py", line 113, in get_config_manager
    configData = json.load(pFile)
  File "/usr/lib/python2.6/json/__init__.py", line 267, in load
    parse_constant=parse_constant, **kw)
  File "/usr/lib/python2.6/json/__init__.py", line 307, in loads
    return _default_decoder.decode(s)
  File "/usr/lib/python2.6/json/decoder.py", line 319, in decode
    obj, end = self.raw_decode(s, idx=_w(s, 0).end())
  File "/usr/lib/python2.6/json/decoder.py", line 338, in raw_decode
    raise ValueError("No JSON object could be decoded")
ValueError: No JSON object could be decoded

```

look for autokey.json in ~/.config/autokey
if it's zero length:
```
~/.config/autokey $ ls -l
-rw-r--r-- 1 mobilediesel mobilediesel    0 04-20-2010 17:21 autokey.json
```
close autokey and delete that file and re-run autokey. It should re-create the .json file from your autokey.bin file.

At least that worked for me.

---

### Post by mobilediesel on 2010-04-21
> **cdekter said:**
> Questions and issues like this one need to be posted to the Google group for AutoKey:

[http://groups.google.com/group/autokey-users/](http://groups.google.com/group/autokey-users/)

Mods, please close this thread.

^^ What he said.

---

### Post by afbase on 2010-04-21
> **mobilediesel said:**
> look for autokey.json in ~/.config/autokey
if it's zero length:
```
~/.config/autokey $ ls -l
-rw-r--r-- 1 mobilediesel mobilediesel    0 04-20-2010 17:21 autokey.json
```
close autokey and delete that file and re-run autokey. It should re-create the .json file from your autokey.bin file.

At least that worked for me.

Thank you!! now i can do my homework.:popcorn:

---

### Post by kaspin on 2010-05-12
[FONT="Comic Sans MS"][SIZE="2"][COLOR="RoyalBlue"]G'Day CDekter,
I have a new AZERTY keyboard problem, which crept in recently. The "@" key seems to change the French keyboard layout to QWERTY. For example my text "amq@amq" is output by Autokey as "amqq;a" (the @ does not appear in the output). I have only the AZERTY layout configured on my PC, and have tried updating from 0.61.7 to the latest version from your ppa and even reinstalling a fresh 10.04, but to no avail.
Not sure if I'm in the right place to post this - if not please tell me where to go (politely...).
Thanks in advance,
kaspin[/COLOR][/SIZE][/FONT]

---

### Post by cdekter on 2010-05-12
[AutoKey Users]("http://groups.google.com/group/autokey-users") on Google Groups is the right place... start a thread there and we'll try to debug this.

---

### Post by kaspin on 2010-05-12
[FONT="Comic Sans MS"][COLOR="RoyalBlue"][SIZE="2"]OK - thanks.
kaspin[/SIZE][/COLOR][/FONT]

---

### Post by wordmagic on 2012-10-30
I am trying to use it with Ubuntu 12.04 and Greek text (version 0.90). But it does not trigger the expansion. Latin text and abbreviation works ok. When the abbreviation is latin, and the text is Greek, it comes out in strange characters. When the abbreviation is Greek, and the text is Greek, nothing happens.

Does that mean it is not unicode-ready or that I have missed something?

Moreover, I see a number of different versions (qt, gde, common), I am not quite sure which I should be using.

---

### Post by nainainai on 2013-01-01
there's any plugin or way for me to add syntax highlighting for HTML, CSS, Bash, PHP, Ruby (and maybe others)?

if there isn't, is it too hard to implement it? if someone just tell me how to do it I can do the heavy lifting, but I don't really know sh* about python

there's several ways to add syntax highlight, maybe GtkSourceview?

---

