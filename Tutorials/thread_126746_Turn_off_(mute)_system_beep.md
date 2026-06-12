---
title: "Turn off (mute) system beep"
date: 2006-02-07
forum: Tutorials
---

### Post by WolfJay_83 on 2006-02-07
For anyone with a laptop who works in a library or other quiet area, system beeps every time you press the backspace key one too many times, or just using emacs, can be quite disturbing.

To shut them off: 
open an xterm or terminal, and enter the two lines
```

xset b off
xset b 0 0 0

```

Hope this helps.

note: this does not work if run before X.  To have it run as default, you can place it in your .xinitrc before the windowmanager. If you're using Gnome or KDE, it is probably easier to just turn off the "System Bell" or set it to "Visable Only" in your respective settings manager.

---

### Post by zachtib on 2006-02-07
[QUOTE=WolfJay_83]For anyone with a laptop who works in a library or other quiet area, system beeps every time you press the backspace key one too many times, or just using emacs, can be quite disturbing.

To shut them off: 
open an xterm or terminal, and enter the two lines
```

xset b off
xset b 0 0 0

```

Hope this helps.[/QUOTE]

will this disable it permanently, or do i need to run this every time i boot up?

---

### Post by Parkotron on 2006-02-07
I've always just unplugged the internal speaker all together. I guess this solution is a little less drastic.

---

### Post by WolfJay_83 on 2006-02-07
It appears to turn it off temporarily (I've been using it just when in the library).  I suppose if you put it in a script to be run on bootup, you could make it perminent.  I will have to put together instructions when I do that myself.

note: its kindof hard to disconnect the pc speaker in a laptop.  Also, on a PC, if your video or ram gets messed up, you won't know whats going on on bootup without the post beep.

regards

---

### Post by art on 2006-02-07
You can disable system bell if in the Terminal you go to Edit->Current Profile->General and uncheck the Terminal Bell
Or in the Configuration editor go to apps->Gnome-Terminal->Profiles->default check silent Bell.

---

### Post by i3dmaster on 2006-02-07
wouldn't do any good for console beep.

---

### Post by dbw on 2006-02-07
Alternatively, (in gnome) you can change the System>Preferences>Sound>System Bell setting to either off or to a visual alert.  I like the visual alert, which will invert the colors of the application frame briefly.  This is a strong option because:
  it allows beeps pre-Gnome, so I know if anything goes awry
  I don't find the flashing border obnoxious
  The information is still presented, just in case.

This definately changes terminal and emacs beeps.

---

### Post by rfruth on 2006-02-07
Put a strip of tape over the internal speaker, then you get a muted beep :p

---

### Post by llimllib on 2006-03-22
[QUOTE=WolfJay_83]For anyone with a laptop who works in a library or other quiet area, system beeps every time you press the backspace key one too many times, or just using emacs, can be quite disturbing.

To shut them off: 
open an xterm or terminal, and enter the two lines
```

xset b off
xset b 0 0 0

```

Hope this helps.[/QUOTE]

Many thanks! works like a charm.

---

### Post by geofs on 2006-04-15
Do not unplug your internal speaker or make boot scripts ;)

Edit the *.inputrc* file in your home directory (create it if needed) and add the line

```
set bell-style visible
```

this will replace the beep by a flashing screen.  You can replace '*visible*' by '*none*' to get nothing at all.

You can also add (or uncomment) this line in the general /etc/inputrc file to set the bell-style for all users (overriden in ~/.inputrc).

You have to log out to enable this setting.

PS: this also works in xterm/konsole/gnome-terminal

---

### Post by Mr Fat Bat on 2006-05-08
Thanks geofs!

My system bell was driving everyone in the office up the wall!

---

### Post by Peepsalot on 2006-06-01
Well I tried to stop this beeping by adding ```
set bell-style visible
``` to my home directory's .inputrc file.

It looks like it only works for the shell, but programs such as *man* still beep when I reach the end of a page, or if I accidentally press an arrow left or right from *more*.

Is there a  way to completely disable this device on bootup?

---

### Post by zaiyon on 2006-06-04
/etc/inputrc is the readline configuration file afaik, so it turns beeping only off in readline applications (such as bash)

I managed to silence vim by adding this to my .vimrc:
```

set vb t_vb=

```

I don't need any bell, it's just annoying. No visual bell too. Still, I don't want to take my laptop apart to deactivate it.

As the last poster, my only problem now are programs like less and man, who still beep, which could cause a divorce soon if I don't find a way to get rid of it ;)

But only on the vterms, I don't have any beeps in X since I deactivated the bell in gnome as described some posts earlier, and it worked perfectly for all applications run in X.

---

### Post by neuropsychguy on 2006-08-23
Thanks for the help. Now I can finally have that stupid beep not beep!

---

### Post by irsic on 2006-11-16
Hey. I have quite similar question. How do you turn terminal bell on?
I have tried in Terminal->Current Profile and terminal bell is checked but is not working. Any tips? Doesn't one of ASCII's od the trick?

---

### Post by WolfJay_83 on 2006-11-20
stupid question- your sound works everywhere else right?  I think that terminal beep in the gnome terminal is based on the sound system (as aposed to the pc speaker).

I think in gnome's sound configuration, you can change pc speaker settings.  But I'm not sure.

I don't have gnome on this computer, so sorry I'm not much help.  I wrote this post because I use aterm in a window manager instead of gnome, so theres no graphical way to change the sound settings.

If you're having sound issues, or realy want to fix the beep problem, I'd suggest starting a new thread. This one's realy old, so it's unlikely that your going to get the response that you would from a new one for your specific problem.

Good luck, and have fun getting everything working the way you like.
-Jason

---

### Post by irsic on 2006-11-25
thanks. I did open a new one though...no response so far :)

---

### Post by pormogo on 2006-12-05
Anyone have an idea how to do this in an actual terminal and not within X. I run an ubuntu server box at my office that I run without X (it basically just stores and processes logs). Any time I work on it thought I can tell the system bell is slowly driving those around me mad. Does anyone know how to turn off the system bell outside of X. Is there a bash environment variable that I can set?

---

### Post by dragonfixed on 2006-12-05
Or Just sudo vim /etc/modprobe.d/blacklist

and add 

blacklist pcspkr

---

### Post by Peepsalot on 2006-12-05
> **pormogo said:**
> Anyone have an idea how to do this in an actual terminal and not within X. I run an ubuntu server box at my office that I run without X (it basically just stores and processes logs). Any time I work on it thought I can tell the system bell is slowly driving those around me mad. Does anyone know how to turn off the system bell outside of X. Is there a bash environment variable that I can set?
Try putting this line in your .bash_profile
```

echo -e "\\33[10;0]\\33[11;0]"

```

See section 4 for more info:
[http://www.ibiblio.org/pub/Linux/docs/HOWTO/Visual-Bell](http://www.ibiblio.org/pub/Linux/docs/HOWTO/Visual-Bell)

I set mine to:
```

echo -e "\\33[10;1000]\\33[11;5]"
```
Which makes a very subtle clicking noise since the duration is so short.

---

### Post by binaryspiral on 2007-03-21
Great tutorial... I too was annoying the Ayche Eee Double Hockey Sticks out of my cube farm cohorts... what can I say, I do HAVE fat fingers. :)

Thanks again!

---

### Post by shoofy on 2007-03-26
This didn't do anything for me other than print the 33[10:(etc.) on the screen when I log in. I still get the beeps.

---

### Post by Peepsalot on 2007-03-27
> **shoofy said:**
> This didn't do anything for me other than print the 33[10:(etc.) on the screen when I log in. I still get the beeps.

Hmm, the only thing i can think is that you didn't type it exactly right.  Did you try copying and pasting the exact code to avoiding typing errors?

---

### Post by shoofy on 2007-03-27
I did. Didn't change anything. It seems logical that that's what it should be doing, doesn't it? Echo just prints back whatever comes after it...

---

### Post by Peepsalot on 2007-03-27
Well, the -e option in echo enables blackslash escapes, which it seems are interpreted by the shell as commands/configuration options of some sort.

---

### Post by shoofy on 2007-03-27
> **Peepsalot said:**
> Well, the -e option in echo enables blackslash escapes, which it seems are interpreted by the shell as commands/configuration options of some sort.That does not seem to be the case. I tried a few variations on the command in the terminal and they all came back exactly the same: ```
$ echo -e "\\33[10;0]\\33[11;0]"
\33[10;0]\33[11;0]
$ echo "\\33[10;0]\\33[11;0]"
\33[10;0]\33[11;0]
$ echo "\33[10;0]\33[11;0]"
\33[10;0]\33[11;0]
```
I get the sense that we're missing something here. Are you sure that that's the only line you added to .bash_profile?

---

### Post by Peepsalot on 2007-03-29
Are you using something other than the default shell?

What does "echo $SHELL" return?

---

### Post by shoofy on 2007-03-29
```
$ echo $SHELL
/bin/bash
```

---

### Post by Peepsalot on 2007-03-30
well, sorry I have no idea.

---

### Post by WolfJay_83 on 2007-04-02
This only works in X.  You can add those lines to your .xinitrc or .xsession
 (not .bashrc)

Sorry, I should have clarified that orrigionally, but I didn't figure it out untill later.

---

### Post by TechZilla on 2007-06-23
the best solution was from DragonFixed.  He proposed

"Just sudo vim /etc/modprobe.d/blacklist

and add

blacklist pcspkr"

which is MUCH better then disconnecting the device in the case of hardware malfunction pre-kernel.  as well as preventing the pc-speaker pre-xserver.

thank you DragonFixed (except for suggesting i use vim, im far too lazy to learn vim so i use nano, which is so close to the old "edit.exe" that it taked almost 3 min to learn every usefull function)

i suggest nano to anyone irritated with editing files via commandline, i had to learn some vim commands for my linux+ test and at my job my boss always says "vi this or that"
i ask "vi?" he says with a goofy voice "...or nano" heh heh

---

### Post by sixdollarshirt on 2007-07-11
> **art said:**
> You can disable system bell if in the Terminal you go to Edit->Current Profile->General and uncheck the Terminal Bell
Or in the Configuration editor go to apps->Gnome-Terminal->Profiles->default check silent Bell.

Great help to new Ubuntu users.  Thanks very much.

---

### Post by jctweb on 2007-09-12
> **dragonfixed said:**
> Or Just sudo vim /etc/modprobe.d/blacklist

and add 

blacklist pcspkr

Definitely the best solution - especially when using a laptop where you can't disconnect the infernal beeper.

Thanks a ton

Jon

---

### Post by jw5801 on 2007-11-01
If you want it to not beep in console without going to the extreme of blacklisting the module for the speaker add this to /etc/rc.local
```

for i in 1 2 3 4 5 6
do
        setterm -blength 0 > /dev/tty$i
done

```
The other solution I've seen around is to add this to /etc/profile:
```
setterm -bfreq 0
```

---

### Post by schneertz on 2007-11-06
The blacklisting solution *did not work* for me. :(

Gusty, HP Pavilion dv400

---

### Post by jw5801 on 2007-11-06
What happened when you tried it? Blacklist it and then reboot. Then it shouldn't work at all as the OS doesn't have access to the speaker. Try ```
sudo rmmod pcspkr
```which removes the module from the kernel. Blacklisting the module tells the kernel to not load it in the first place. So a reboot should kill your system beep.

---

### Post by schneertz on 2007-11-07
I've rebooted several times, and I still get the beep.

When I do an lsmod, pcspkr doesn't show up in the list. Still, the beep.

I also have System Beep disabled in Sound Preferences.

---

### Post by jw5801 on 2007-11-07
When is the beep happening? Are you sure it's the pc speaker and not something else? Check in your bios and see if you can turn it off there.

---

### Post by nebbe on 2007-11-08
Thx a million for this thread :) 

Found ".inputrc" in my "/etc/inputrc", edited the line with "set bell-style visible", and i also used the "xset b off" &  "xset b 0 0 0" in a terminal.

Nice work my fellow nerds, Cheers!

---

### Post by MozartlovesUbun2 on 2007-11-11
> **dbw said:**
> Alternatively, (in gnome) you can change the System>Preferences>Sound>System Bell setting to either off or to a visual alert.  I like the visual alert, which will invert the colors of the application frame briefly.  This is a strong option because:
  it allows beeps pre-Gnome, so I know if anything goes awry
  I don't find the flashing border obnoxious
  The information is still presented, just in case.

This definately changes terminal and emacs beeps.

yup

that helps a lot

---

### Post by JoeLinux117 on 2008-03-06
Ahhh!  Finally!  Thanks a million to jw5801!

I have Ubuntu Server 7.10 running on a SPARC box, and it obviously (it's a SPARC) doesn't have the pcspkr module, so I've had no way of getting rid of the stupid beep!

```
setterm -bfreq 0
```
worked like a charm.  Thanks again!


--JoeLinux

---

### Post by elnur on 2008-03-19
> **dragonfixed said:**
> Or Just sudo vim /etc/modprobe.d/blacklist

and add 

blacklist pcspkr

Thanks! This helped me.

---

### Post by behnamgolds on 2008-04-03
hello  there ...

i found  an easier  way to do that  , this is a  permanent  and  multipurpose(for terminal and other programs)    solution :)  

just  run  the   gconf-editor    and  go to the        /desktop/gnome/peripherals/keyboard/bell_mode

and  change  the  "bell_mode"  's  value  to  off   ....

---

### Post by jw5801 on 2008-04-03
> **behnamgolds said:**
> hello  there ...

i found  an easier  way to do that  , this is a  permanent  and  multipurpose(for terminal and other programs)    solution :)  

just  run  the   gconf-editor    and  go to the        /desktop/gnome/peripherals/keyboard/bell_mode

and  change  the  "bell_mode"  's  value  to  off   ....

That would only work in Gnome, not in a tty or any other desktop environment. This thread was looking for a more general solution.

---

### Post by wnwek on 2008-04-19
> **jw5801 said:**
> 
The other solution I've seen around is to add this to /etc/profile:

```
setterm -bfreq 0
```



This worked for me!

---

### Post by 3rdalbum on 2008-04-19
I don't want to turn off the beep entirely, so is there a way to set it up to play a sound file instead of beeping the PC speaker? I already have the sox package installed (which has the "play" command).

I especially want to set this up on the Ubuntu computers that I make for other people. I think it sounds more professional to use a sound file rather than the PC speaker.

---

### Post by jw5801 on 2008-04-19
> **3rdalbum said:**
> I don't want to turn off the beep entirely, so is there a way to set it up to play a sound file instead of beeping the PC speaker? I already have the sox package installed (which has the "play" command).

I especially want to set this up on the Ubuntu computers that I make for other people. I think it sounds more professional to use a sound file rather than the PC speaker.

I'm sure there's a setting in Gnome somewhere to do that.
gconf-editor: desktop > gnome > peripherals > keyboard
And set bell_mode to custom, then bell_custom_file to the file you want to play. I'm guessing it probably needs to be a .wav. You probably also want to use one of the other methods of killing it too (ie. blacklist pcspkr) so it doesn't go off in ttys or anything else non-gnome.

---

### Post by drawkcab on 2008-04-20
> **dbw said:**
> Alternatively, (in gnome) you can change the System>Preferences>Sound>System Bell setting to either off or to a visual alert.  I like the visual alert, which will invert the colors of the application frame briefly.  This is a strong option because:
  it allows beeps pre-Gnome, so I know if anything goes awry
  I don't find the flashing border obnoxious
  The information is still presented, just in case.

This definately changes terminal and emacs beeps.

This worked for me...thanks!    :guitar:

---

### Post by Stvnx7 on 2008-06-03
This one worked for me:

xset b off
xset b 0 0 0


What I did was put it in system --> preferences --> sessions. 

xset b off && xset b 0 0 0


That way, it runs the first commmand, waits for it to be done, and runs second command. You can easily disable and re-enable it too.

---

### Post by curran on 2008-07-18
Here's a command which will disable the system beep altogether, the equivalent of unplugging the speaker:

```
sudo sh -c "echo blacklist pcspkr >> /etc/modprobe.d/blacklist"
```

---

### Post by parakeets11 on 2008-09-02
These don't work if you want to run a command to shut off your computer at a certain time like ```
sudo shutdown -P 00:03
```  I still have yet to find a way to do this.  I would be enjoyable to be able to listen to music while I sleep yet not have it beep every minute telling me that it is going to shut off.  Even when I muted them in the sound menu and in the terminal menu. I also tried the commands but it didn't work.

---

### Post by danger89 on 2008-11-23
Check:
[http://ubuntu-snippets.blogspot.com/2008/08/disable-system-beepsound-in-ubuntu.html](http://ubuntu-snippets.blogspot.com/2008/08/disable-system-beepsound-in-ubuntu.html)

> 
To temporarly disable system beep for current session use following command.

sudo rmmod pcspkr

To perminently disable system beep add following line to /etc/modprobe.d/blacklist file.

blacklist pcspkr


Good Luck.

---

### Post by mkgs on 2008-12-30
> **art said:**
> You can disable system bell if in the Terminal you go to Edit->Current Profile->General and uncheck the Terminal Bell
Or in the Configuration editor go to apps->Gnome-Terminal->Profiles->default check silent Bell.

:D Thanks a lot for this tip. The beep was annoying most of the time.

---

### Post by ubername on 2009-01-18
> **WolfJay_83 said:**
> For anyone with a laptop who works in a library or other quiet area, system beeps every time you press the backspace key one too many times, or just using emacs, can be quite disturbing.

To shut them off: 
open an xterm or terminal, and enter the two lines
```

xset b off
xset b 0 0 0

```

Hope this helps.

note: this does not work if run before X.  To have it run as default, you can place it in your .xinitrc before the windowmanager. If you're using Gnome or KDE, it is probably easier to just turn off the "System Bell" or set it to "Visable Only" in your respective settings manager.

Fantastic! Works in Jaunty. Where is .xinitrc? I could only find /etc/X11/xinit/xinitrc. Is that the same (or a generic version for all users?)

My /etc/X11/xinit/xinitrc is:

#!/bin/bash
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession

Where would I put

xset b off
xset b 0 0 0

TIA

---

### Post by ubername on 2009-01-18
In Jaunty, in order to get rid of the system beep so far I have tried:

Using the volume control applet and setting alert sounds to 'disabled'.

Adding 'blacklist pcspkr' to etc/modprobe.d/blacklist.

Adding a session to my 'session' options with the command xset b off && xset b 0 0 0.

Editing /etc/X11/xinit/xinitrc to this:
#!/bin/bash
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

xset b off
xset b 0 0 0

# invoke global X session script
. /etc/X11/Xsession

Going into a GUI terminal window and selecting Edit>Profiles>Default and deselecting the 'Terminal Bell' option.

Going into Applications>System Tools>Configuration Editor, selecting Apps then gnome-terminal then profiles then default and checking the 'silent_bell' option.

And possibly some others which I can't remember right now.

What does work is entering

xset b off
xset b 0 0 0

in a terminal, but I have to do this after each login. I would love to make this persistent, or find a better solution.

Can anyone help?

(and thanks to all the posters who described the other solutions which didn't work for me. I know that you are all trying to help and the fact that they didn't work for me is in no way a dismissal of you help.)

---

### Post by Essar Allen on 2009-04-15
> **geofs said:**
> Do not unplug your internal speaker or make boot scripts ;)

Edit the *.inputrc* file in your home directory (create it if needed) and add the line

```
set bell-style visible
```

this will replace the beep by a flashing screen.  You can replace '*visible*' by '*none*' to get nothing at all.

You can also add (or uncomment) this line in the general /etc/inputrc file to set the bell-style for all users (overriden in ~/.inputrc).

You have to log out to enable this setting.

PS: this also works in xterm/konsole/gnome-terminal

I'm brand new to Linux and was wondering how to get to the home directory. I assume i go through terminal, but have no clue on how to get there. 

Thanks in advance,
Essar

---

### Post by elnur on 2009-04-15
> **Essar Allen said:**
> I'm brand new to Linux and was wondering how to get to the home directory. I assume i go through terminal, but have no clue on how to get there. 

Thanks in advance,
Essar

To edit .inputrc file in your home directory open the terminal and type:
```
nano ~/.inputrc
```
As you can guess ~ is your home directory. ~ corresponds to a directory /home/YOUR_NAME

---

### Post by BubuXP on 2009-04-28
> **ubername said:**
> In Jaunty, in order to get rid of the system beep so far I have tried:
[...]
Adding 'blacklist pcspkr' to etc/modprobe.d/blacklist.
[...]
Can anyone help?

This solution is still valid, the only thing to change is the blacklist filename, that is changed in Jaunty.

To get rid of the beeps, just add
blacklist pcspkr
in /etc/modprobe.d/blacklist.conf

See you all at the next ubuntu release for a new fix :-D

---

### Post by sdunnrocket9 on 2009-05-06
Thanks - the system command worked. And I found the system apps settings, too.

---

### Post by l-x-l on 2009-05-06
> **art said:**
> You can disable system bell if in the Terminal you go to Edit->Current Profile->General and uncheck the Terminal Bell
Or in the Configuration editor go to apps->Gnome-Terminal->Profiles->default check silent Bell.

> **dragonfixed said:**
> Or Just sudo vim /etc/modprobe.d/blacklist

and add 

blacklist pcspkr

Thx for both of these tips. The beeping was driving me crazy in Jaunty.

---

### Post by Spaced on 2009-05-15
Hello everybody,

I tried all the solution proposed in this topic, but none of them worked for me. My problem is that I hear the system beep when I shut down my laptop... the beep more or less overlaps with the "exit" sound.

I disabled alert sounds in System>Preferences>Sound, did the same for the terminal and for some other applications... I also blacklisted "pcspkr" in /etc/modprobe.d/blacklist.conf... all to no avail... I see indeed that every possible beep in the normal running of Ubuntu has disappeared, but the shutdown one has not. 

I've tried to have a look at the Bios, to check if I could disable the system beep from there, but I haven't found that option. I have a Dell Inspiron 1525, maybe some of you can help me. Thanks.

---

### Post by jw5801 on 2009-05-15
> **Spaced said:**
> Hello everybody,

I tried all the solution proposed in this topic, but none of them worked for me. My problem is that I hear the system beep when I shut down my laptop... the beep more or less overlaps with the "exit" sound.

I disabled alert sounds in System>Preferences>Sound, did the same for the terminal and for some other applications... I also blacklisted "pcspkr" in /etc/modprobe.d/blacklist.conf... all to no avail... I see indeed that every possible beep in the normal running of Ubuntu has disappeared, but the shutdown one has not. 

I've tried to have a look at the Bios, to check if I could disable the system beep from there, but I haven't found that option. I have a Dell Inspiron 1525, maybe some of you can help me. Thanks.

Sounds as though the bios insists on beeping when powering off. This is completely separate from the operating system, and if your bios doesn't support changing it, there's not all that much you can do, short of physically disconnecting the speaker inside the case.

---

### Post by Spaced on 2009-05-15
> **jw5801 said:**
> Sounds as though the bios insists on beeping when powering off. This is completely separate from the operating system, and if your bios doesn't support changing it, there's not all that much you can do, short of physically disconnecting the speaker inside the case.

First of all thank you for your reply... then, I have finally discovered that this noise is not produced by the motherboard, it's not the system beep... I was mistaken because the noise is very similar, but when I shut down the laptop with the headphones plugged, the noise comes from them, so it cannot be the system beep.

But this doesn't solve the problem... if possible, it makes it even more weird...

---

### Post by bdoe on 2009-05-31
The sounds you are describing are the fast, high-pitched beeps that *normally* happen when you issue a 'shutdown -r now' or 'shutdown -h now' command from console. However, up until Jaunty, these beeps have never accompanied a shutdown from desktop. I believe that these beeps happening from a desktop shutdown in Jaunty is a bug, and a damned annoying one at that.

On a related note: YOU ACTUALLY GOT THE EXIT SOUND TO PLAY??? I have not had the logout/exit sound play for me ever since I installed Hardy!  Feisty and Gutsy were the last distros where the exit sound worked!

---

### Post by Spaced on 2009-05-31
> **bdoe said:**
> The sounds you are describing are the fast, high-pitched beeps that *normally* happen when you issue a 'shutdown -r now' or 'shutdown -h now' command from console. However, up until Jaunty, these beeps have never accompanied a shutdown from desktop. I believe that these beeps happening from a desktop shutdown in Jaunty is a bug, and a damned annoying one at that.

On a related note: YOU ACTUALLY GOT THE EXIT SOUND TO PLAY??? I have not had the logout/exit sound play for me ever since I installed Hardy!  Feisty and Gutsy were the last distros where the exit sound worked!

After reinstalling the ALSA drivers the noise has disappeared, at least for me.

Anyway, to answer your question, when I had that noise I had also the logout sound. I too didn't have it until I found this solution: [http://forum.ubuntu-it.org/index.php/topic,137529.msg2036628.html#msg2036628](http://forum.ubuntu-it.org/index.php/topic,137529.msg2036628.html#msg2036628)

Put simply, you have to edit the file /etc/gdm/PostSession/Default, adding after the last line ("exit 0") the following:

/usr/bin/canberra-gtk-play --id="desktop-logout"

Reboot and you should have again your beloved logout sound!

---

### Post by lixy on 2009-06-02
> **curran said:**
> Here's a command which will disable the system beep altogether, the equivalent of unplugging the speaker:

```
sudo sh -c "echo blacklist pcspkr >> /etc/modprobe.d/blacklist"
```

Well...you then need to remove the module. On my system (Jaunty), blacklisting pcspkr didn't disable the beep until I threw in a "sudo rmmod pcspkr".

---

### Post by jw5801 on 2009-06-02
> **lixy said:**
> Well...you then need to remove the module. On my system (Jaunty), blacklisting pcspkr didn't disable the beep until I threw in a "sudo rmmod pcspkr".

The blacklist prevents it from being loaded on startup. Otherwise you'd need to remove the module every single time you booted the machine up.

---

### Post by braddock on 2009-07-10
In a cafe now, annoying the hell out of everyone around me because Ubuntu beeps under mute everytime I do a failed Firefox page search.

The blacklist method works for me now, but let me just say it is hardly the expected system "mute" behavior.  And what about when I'm home and WANT beeps?

There is a ticket [https://bugs.launchpad.net/ubuntu/+bug/389542](https://bugs.launchpad.net/ubuntu/+bug/389542)

---

### Post by tiagosales on 2009-09-07
> **braddock said:**
> In a cafe now, annoying the hell out of everyone around me because Ubuntu beeps under mute everytime I do a failed Firefox page search.

The blacklist method works for me now, but let me just say it is hardly the expected system "mute" behavior.  And what about when I'm home and WANT beeps?

There is a ticket [https://bugs.launchpad.net/ubuntu/+bug/389542](https://bugs.launchpad.net/ubuntu/+bug/389542)

To reactivate pcspkr module, only load the module:

```
sudo modprobe pcspkr
```

What do you think?

---

### Post by shivku on 2009-10-08
"blacklist pcspkr" did not turn off the beep for me. I did an lsmod and picked up the module that looked closest to a pc speaker. It was "snd_pcsp". 

Next I did rmmod snd_pcsp and added it to the blacklist and now the beep has gone to hell.

---

### Post by jw5801 on 2009-10-08
> **shivku said:**
> "blacklist pcspkr" did not turn off the beep for me. I did an lsmod and picked up the module that looked closest to a pc speaker. It was "snd_pcsp". 

Next I did rmmod snd_pcsp and added it to the blacklist and now the beep has gone to hell.

Yep, the name of the module changed in kernel 2.6.31. Well, it might have changed in 2.6.30 as well, I'm not sure, I just don't build it into my kernel anymore! :P

---

### Post by zereshk on 2010-07-21
imho, the winning lazy-friendly solution is this:

System > Preferences > Sound 

And just tick 'Mute'.

---

### Post by digitsm on 2011-02-03
> Do not unplug your internal speaker or make boot scripts :wink:

Edit the *.inputrc* file in your home directory (create it if needed) and add the line

     Code:
     set bell-style visible 
this will replace the beep by a flashing screen.  You can replace '*visible*' by '*none*' to get nothing at all.

You can also add (or uncomment) this line in the general /etc/inputrc  file to set the bell-style for all users (overriden in ~/.inputrc).

You have to log out to enable this setting.

PS: this also works in xterm/konsole/gnome-terminal
                                                                                                                   @geofs: The method you've offered didn't work for me.
I'm using LMDE x64 (which is debian-based but very similar to ubuntu) and there was no *.inputrc* file in my home.
I could find */etc/inputrc* but uncommenting the line you mentioned didn't affect anything.

>                                   **Turn off (mute) system beep**             
                                                                For anyone with a  laptop who works in a library or other quiet area, system beeps every  time you press the backspace key one too many times, or just using  emacs, can be quite disturbing.

To shut them off: 
open an xterm or terminal, and enter the two lines
     Code:
     xset b off
xset b 0 0 0 
Hope this helps.

note: this does not work if run before X.  To have it run as default,  you can place it in your .xinitrc before the windowmanager. If you're  using Gnome or KDE, it is probably easier to just turn off the "System  Bell" or set it to "Visable Only" in your respective settings manager.
But the method WolfJay_83 offered worked for me too. Thank you WolfJay_83.

---

### Post by jth on 2011-09-14
None of these methods worked for my Dell Latitude E6510. The shutdown beep was driving me crazy.

It turns out there is a hidden mixer in the volume control called, funnily enough, "Beep." If you make this visible in Volume Control preferences and mute it, the evil beep is gone. You can also probably do the same in alsamixer.

---

