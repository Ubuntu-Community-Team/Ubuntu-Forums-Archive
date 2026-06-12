---
title: "Someone should make a macro program"
date: 2007-05-30
forum: The Cafe
---

### Post by Genecks on 2007-05-30
I've been reading up on the availability of a macro program in Linux. It seems there really isn't a decent macro program, which is disappointing. Someone seems to have created one macro program within the duration of a year ago. However, I could see how a macro could help any linux community, which is why I think people should get to work on one right away:

1) Users who face a technical problem can create a macro to replicate how they solved that problem. Afterwards, they can share the macro with other users. No longer would a person have to spend an hour or more trying to solve a problem.

2) It's just a nice feature to have in the first place. WIndows came out with a macro recorder over ten years ago. Yet during that time, Linux did not have one. I find that amazingly surprising. There hasn't been a program to record the axis positions of a mouse, the clicks of it, nor the typing of the keys. I find that mighty surprising, seeing how people have remained optimistic about Linux for over a decade.

WIth a couple of reasons for a macro to be built, I think someone should get to work on building one for Linux. I'm sure if a team of programmers got together, they could have one built within a month.

---

### Post by 23meg on 2007-05-30
> 1) Users who face a technical problem can create a macro to replicate how they solved that problem. Afterwards, they can share the macro with other users. No longer would a person have to spend an hour or more trying to solve a problem.

Heard of shell scripts?

> There hasn't been a program to record the axis positions of a mouse, the clicks of it, nor the typing of the keys.

There's more than one, but I can't remember the names; do a description search in APT / Synaptic.

> WIth a couple of reasons for a macro to be built, I think someone should get to work on building one for Linux. I'm sure if a team of programmers got together, they could have one built within a month.

Here's what to do if you can't find what you're looking for:

[https://wiki.ubuntu.com/FeatureSpecifications](https://wiki.ubuntu.com/FeatureSpecifications)

---

### Post by Tomosaur on 2007-05-30
Yeah, seriously, you should just read up on shell scripts. You'd actually be surprised how many scripts are shared here on the ubuntu forums. In actual fact, any time you see a whole bunch of commands when reading a tutorial, chances are you can just lump all those commands into one script file and execute that.

---

### Post by Tundro Walker on 2007-05-30
Having used the ones in MS Office, I would argue for and against it.

For...

1) it makes it easy for folks who don't want to get too involved with computers to quickly automate stuff. 

Against...

1) The code recorded usually isn't the most efficient

2) The macro program can't fathom all the programs and setups you'll ever have on your machine.  So, if it just records X,Y mouse locations and mouse clicks, you could seriously screw up your machine if you run the macro with the wrong program.  Sometimes the same pop-up shows up on various parts of the screen, too, so  recording a click on it may "miss" the next time the macro is ran (or if it's ran on another person's machine).

3) It'll probably involve the GUI, since that's how the typical user who doesn't want to really get into computers will interact with their computer, and the GUI adds a lot of overhead to otherwise simple tasks.

Do I think it's a good idea?  Yes.  Do I think it's feasable?  Not really...well, not when compared to shell scripting (which isn't GUI-reliant).

Instead, I think someone should make BASH shell that has intellisense dropdowns, highlight & F1 for quick-help on a function's, switch's or keyword's use, etc...let the shell help you write the scripts.  (Of course, in saying that, I bet somebody's already done this, but I have no clue what the project would be.)


PS: 

> ...which is why I think people should get to work on one right away

That sounded rude.  "Everyone!  Attention!  I have a very important idea, and you should stop what you're doing and work on my idea pronto!  Now get to work, slaves!  Chop chop!"

---

### Post by Genecks on 2007-05-30
It's alright for you to provide an antithesis. Sadly, it seems you don't understand the "call to action" part of rhetoric. Sounded rude for you to twist my words and make others think I consider them as slaves. I don't consider others slaves.

Anyway, I keep reading about this shell-script stuff; but it doesn't seem to pertain to the environment. I figured Linux didn't have anything to match a macro recorder, because I looked for a couple hours on google: through groups, this website, and linuxforums. I couldn't come up with any reasonable answers that dated even back to 2002. Most things spoke of shell-scripting. Yet, I haven't come to understand what all of you mean by "shell-scripting."

I figured people were pointing toward bash, yet I didn't see anything relevant to spouting out keyboard commands and taking notice of x-and-y coordinates.

>  There hasn't been a program to record the axis positions of a mouse, the clicks of it, nor the typing of the keys. 
Of course, I meant in relation to recording and then repeating. I've read that there are programs which record this information.

---

### Post by Tomosaur on 2007-05-30
Ah I understand what you mean by a macro now. The recording of mouse clicks and such to speed up tasks.

In Linux, the whole system is maintainable by the command line, which is probably why no macro software has emerged (or at least, I've never seen any). If you can do it in the GUI, you can do it in the command line (that's the general rule of thumb anyway. Obviously, you can't use the GIMP from the command line, but you get the picture). Since everything can be done via command line, most Linux users' natural approach is to write a shell script (a sequence of commands in a plain-text file, which can be executed either manually or by using a scheduler such as cron). Windows doesn't really offer this kind of control (although it does allow SOME degree of control, with scheduling etc etc) which is a possible reason why macro software has become prevelant.

Anyway, there may be macro software available for Linux, I just personally haven't used any. Shell scripting is fairly easy to do, and there are probably GUI scheduling apps available for you to use. There may even be a macro program somewhere in the repositories.

As soon as you understand that pretty much everything you're likely to do with a macro can be done with a command (or a few commands) in the terminal, you'll begin to understand why shell scripting is so powerful and useful. Think of the GUI as an interface to the command line, and it'll all start making sense. If you can do everything without a gui, then what's the point of clicking around? Here's a shell script to gather information about the files located in your home folder:
```

#!/bin/sh
ls -l $HOME > $HOME/home_folder.txt

```

All this does is perform a directory search of your home folder, complete with permissions, ownership etc, and then puts all of this into a text file in your home directory.

The first line ('#!/bin/sh') tells your shell (in Ubuntu, you actually use the Dash shell by default, which is essentially exactly the same as Bash but is more optimised.) which program to use to execute the file - the /bin/sh bit is the path to the shell executable.

'ls -l $HOME' means 'list the contents of my home directory, with metadata'.
'> $HOME/home_folder.txt' means 'put the output of the previous command into this file'.

Easy! You can then schedule this script to run at a designated time using the scheduler of your choice.

---

### Post by 23meg on 2007-05-30
[QUOTE=Genecks]I figured Linux didn't have anything to match a macro recorder, because I looked for a couple hours on google: through groups, this website, and linuxforums.[/QUOTE]

It took me two minutes of searching to find these:

[http://members.home.nl/wijnenjl/Record_Playback_Python_TclTk_INI_Wx_EN_01.html](http://members.home.nl/wijnenjl/Record_Playback_Python_TclTk_INI_Wx_EN_01.html)
[http://xmacro.sourceforge.net/](http://xmacro.sourceforge.net/)

I'm sure there's at least one more, but can't remember the name now.

---

### Post by Genecks on 2007-05-30
Ah, good find. Thank you!

Maybe there is a breakdown in communication, however. For what some people are calling "macros" within BASH, I would call them batch scripts using commands. Listing directories, to me, in a command-line interface is like using dir/p/w in DOS. I don't really see how that's a macro.

---

### Post by 23meg on 2007-05-30
People aren't calling them macros; they're pointing you to the widely accepted way of automating things. Your definition of a macro is strictly something that automates GUI actions, apparently; if that's the case, yes, they're not what you're looking for.

---

### Post by bpill on 2007-10-26
There is an application called Xnee, but it does not seem to install with Ubuntu.

---

### Post by jr.gotti on 2007-10-26
> **Genecks said:**
> Ah, good find. Thank you!

Maybe there is a breakdown in communication, however. For what some people are calling "macros" within BASH, I would call them batch scripts using commands. Listing directories, to me, in a command-line interface is like using dir/p/w in DOS. I don't really see how that's a macro.

Well, Gnome is (basically) a front end for bash. Therefore, anything you can do from the GUI you can do from the terminal. That said, you can make a shell script to do whatever you want, ie. fix a problem, change a setting, install a program. Isn't that exactly what a macro does? Repeat a defined set of actions? 

Shell scripts and the shell in general are what make *nix so powerful.

---

### Post by brianves on 2007-11-06
So how would I in terminal make my mouse cursor click in the middle of the screen?  And how would I add delay to an action?  Also how many times to repeat the action?  And of course typing text?

---

### Post by jr.gotti on 2007-11-06
> **brianves said:**
> So how would I in terminal make my mouse cursor click in the middle of the screen?  And how would I add delay to an action?  Also how many times to repeat the action?  And of course typing text?

The point is that you don't have to worry about a GUI at all. IT's not getting the script to actually click on an icon with the cursor, but getting the shell to skip straight to opening the program.

 As for typing, why would you have a macro type something for you? I'm honestly curious. 

Unless your talking about logging into webpages and such with a macro, then I guess you can't do that with a shell script. 

Eh, whatever works!

---

### Post by crocuta on 2007-11-16
I have been trying with a set of programs called  xmacro  because i don't think i can get away using only shell scripts.   The scenario is this:
There is a web page where i'm required to type in the grades for a number of students,  each grade into a different textbox.   I have all that data in a OpenOffice spreadsheet.

Probably there's a way to export my data into a CSV text file that  i can manipulate with shell scripts, although i have not found a way to send something to the browser, and even less to a specific textbox.

So i wrote a sequence of keys to copy a grade from the spreadsheet, change the window, paste, go to the next textbox, change the window again and go to the next cell.

[FONT="Courier New"]
Delay 1 
KeyStrPress Control_L
KeyStrPress c
Delay 1 
KeyStrRelease c
KeyStrRelease Control_L
KeyStrPress Alt_L
KeyStrPress Tab
KeyStrRelease Tab
KeyStrRelease Alt_L
Delay 1 
KeyStrPress Control_L
KeyStrPress v
Delay 1 
KeyStrRelease v
KeyStrRelease Control_L
KeyStrPress Tab
KeyStrRelease Tab
KeyStrPress Alt_L
KeyStrPress Tab
KeyStrRelease Tab
KeyStrRelease Alt_L
Delay 1 
KeyStrPress Right
KeyStrRelease Right[/FONT]

That is called with xmacroplay, and everything is repeated with a script.  Yeah, it works, but with mixed results. Depending on the speed of the machine, sometimes it skips a cell or it doesn't copy or paste.  So, i'm still looking for an efficient solution,  but maybe this works for you.

---

### Post by wijnenjl on 2007-12-04
Hello All,

JW_Record_Playback is a macro recorder, that you can use to record and playback mouse movements (including mousewheel movements) and key-strokes (as when typing in a terminal window).

You can see how it works in: [http://members.home.nl/wijnenjl/out_plus_sound_02.mpg.html](http://members.home.nl/wijnenjl/out_plus_sound_02.mpg.html)

This film can be found on the JWF website: [http://members.home.nl/wijnenjl/index7o.html](http://members.home.nl/wijnenjl/index7o.html)

You can download the open source package from sourceforge
- for suse (tested in 10,1) here: [http://sourceforge.net/project/downloading.php?group_id=152282&use_mirror=garr&filename=JW_Record_Playback_15_Oct_2006_01a.tar.gz&74125205](http://sourceforge.net/project/downloading.php?group_id=152282&use_mirror=garr&filename=JW_Record_Playback_15_Oct_2006_01a.tar.gz&74125205)
- for ubuntu (tested in feisty fawn 7.04) here:
[http://sourceforge.net/project/downloading.php?group_id=152282&use_mirror=garr&filename=JW_Record_Playback_10_Jun_2007_04a.tar.gz&84148822](http://sourceforge.net/project/downloading.php?group_id=152282&use_mirror=garr&filename=JW_Record_Playback_10_Jun_2007_04a.tar.gz&84148822)

JW_Record_Playback was specifically created to make it possible to edit the recorded macro file with any plain text editor.

James Wayne.

---

### Post by ShadowSystems on 2007-12-17
Thank you for the JW Macro application link. =)
Like the OP, I had been looking for a way to record macros similar to Iolo's MacroMagic for Windows.
The ability to set a keystroke combination (E.G.: Control-Shift-Z) & have that translate into:
----
Open Email
Show Raw Source
Copy All
Close Email
Open New Email
Switch to the TO field
Type in the three addresses it goes to
Switch to the SUBJ field
Type in today's date, time, & my ID#
Switch to the BODY field
Paste
Select "Attach File"
Navigate to the Log dir
Attach the last (newest) file in it
Send the email
----
Is a VERY large thing to try and figure out from scratch.
I've been brainstorming what I need to use TO write a script (bash? perl? vi? emacs? rm -f? Dancing naked around the room with a chicken in each hand & a candle on my head while chanting ancient Cantonese incantations?) and that step alone has taken me the last two weeks of research.

I understand the need for administrative oversight (to make sure than running someone else's script doesn't hose your system), but even creating your OWN macro to run for your own use, there didn't seem to BE a solution other than replies of "learn Bash!"
It felt like we were being told to study brain surgery when all we wanted to know was how to apply a band aid. =J
Once I'm comfortable building small, low-level scripts for things like the email routine I mentioned above, or automating my back-up routine (yes I know I can run it as a cron job, but I want to learn things for myself so I know what's happening "under the hood" so to speak), THEN I'll stick my toe into the waters of the "heavy stuff".
But for right now, all I need is a band aid, not a neural map to my frontal lobe. =)P

---

### Post by Jhongy on 2007-12-17
> **crocuta said:**
> I have been trying with a set of programs called  xmacro  because i don't think i can get away using only shell scripts.   The scenario is this:
There is a web page where i'm required to type in the grades for a number of students,  each grade into a different textbox.   I have all that data in a OpenOffice spreadsheet.

Probably there's a way to export my data into a CSV text file that  i can manipulate with shell scripts, although i have not found a way to send something to the browser, and even less to a specific textbox.

So i wrote a sequence of keys to copy a grade from the spreadsheet, change the window, paste, go to the next textbox, change the window again and go to the next cell.

[FONT="Courier New"]
Delay 1 
KeyStrPress Control_L
KeyStrPress c
Delay 1 
KeyStrRelease c
KeyStrRelease Control_L
KeyStrPress Alt_L
KeyStrPress Tab
KeyStrRelease Tab
KeyStrRelease Alt_L
Delay 1 
KeyStrPress Control_L
KeyStrPress v
Delay 1 
KeyStrRelease v
KeyStrRelease Control_L
KeyStrPress Tab
KeyStrRelease Tab
KeyStrPress Alt_L
KeyStrPress Tab
KeyStrRelease Tab
KeyStrRelease Alt_L
Delay 1 
KeyStrPress Right
KeyStrRelease Right[/FONT]

That is called with xmacroplay, and everything is repeated with a script.  Yeah, it works, but with mixed results. Depending on the speed of the machine, sometimes it skips a cell or it doesn't copy or paste.  So, i'm still looking for an efficient solution,  but maybe this works for you.

The standard (and more reliable) way to script webpage interaction is with cURL. It's in the repos and comes with decent documentation (in the man page). 

You'd write a script (you could use PHP (use php-cli from the repos) or python (already installed)) that crafted a simple cURL request, and sent it to the page. You could use BASH too, but PHP/Python have so many commends to manipulate data (e.g. a list of files in CSV).

It requires a little learning, but there are many, many tutorials for PHP or python (and are probably as easy to learn as GUI macro scripting), and the solution would be much, much more elegant. 

J

---

### Post by VictorWarner on 2008-12-27
I come just across this thread and have been trying to make the JW_Record_Playback macro work (for Ubuntu 7.04). I am using Ubuntu 8.10: 



> **wijnenjl said:**
> Hello All,

JW_Record_Playback is a macro recorder, that you can use to record and playback mouse movements (including mousewheel movements) and key-strokes (as when typing in a terminal window).

You can see how it works in: [http://members.home.nl/wijnenjl/out_plus_sound_02.mpg.html](http://members.home.nl/wijnenjl/out_plus_sound_02.mpg.html)

This film can be found on the JWF website: [http://members.home.nl/wijnenjl/index7o.html](http://members.home.nl/wijnenjl/index7o.html)

You can download the open source package from sourceforge
- for suse (tested in 10,1) here: [http://sourceforge.net/project/downloading.php?group_id=152282&use_mirror=garr&filename=JW_Record_Playback_15_Oct_2006_01a.tar.gz&74125205](http://sourceforge.net/project/downloading.php?group_id=152282&use_mirror=garr&filename=JW_Record_Playback_15_Oct_2006_01a.tar.gz&74125205)
- for ubuntu (tested in feisty fawn 7.04) here:
[http://sourceforge.net/project/downloading.php?group_id=152282&use_mirror=garr&filename=JW_Record_Playback_10_Jun_2007_04a.tar.gz&84148822](http://sourceforge.net/project/downloading.php?group_id=152282&use_mirror=garr&filename=JW_Record_Playback_10_Jun_2007_04a.tar.gz&84148822)

JW_Record_Playback was specifically created to make it possible to edit the recorded macro file with any plain text editor.

James Wayne.


I have followed the instructions and built TkExt-3.6.11 and now wish to run the macro program with the command suggested:

```
export PYTHONPATH=.;cd /home/wijnenjl/Documents/tools/JW_record_Playback;python Rec_Play_03_direct_save_get_04ts.py

```

But I am getting the following error message(s):

```
Traceback (most recent call last):
  File "Rec_Play_03_direct_save_get_04ts.py", line 7, in <module>
    from Main import opj
  File "/home/wijnenjl/Documents/Tools/JW_record_Playback/Main.py", line 1794, in <module>
    import wx.lib.mixins.inspect
ImportError: No module named inspect
```

My knowledge of linux is extremely limited so I would grateful for help in understanding what this message means and how it can be fixed.

Victor Warner.

---

### Post by Bachstelze on 2008-12-27
You need the package [font="monospace"]python-wxgtk2.8[/font].

---

### Post by VictorWarner on 2008-12-27
Thank you for the reply. 

Unfortunately the suggestion does not work, as python-wxgtk2.8 is already installed. 

I would be grateful for any other suggestions.

Victor Warner

---

### Post by Bachstelze on 2008-12-27
The problem is that the program you're trying to use is old, and tries to load the [font="monospace"]inspect[/font] module, which has been renamed to [font="monospace"]inspection[/font] in wxGTK 2.8.3. The best solution would be to find an updated version of the program or, if none exists, replace all occurrences of [font="monospace"]wx.lib.mixins.inspect[/font] in the source with [font="monospace"]wx.lib.mixins.inspection[/font].

Another approach would be to create the [font="monospace"]inspect[/font] module as a link to the [font="monospace"]inspection[/font] one:

```
cd /usr/lib/python2.4/site-packages/wx-2.8-gtk2-unicode/wx/lib/mixins
sudo ln -s inspection.py inspect.py
```

---

