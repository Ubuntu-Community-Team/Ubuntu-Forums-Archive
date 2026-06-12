---
title: "HOWTO : Create a custom keyboard shortcut"
date: 2005-10-20
forum: Tutorials
---

### Post by frodon on 2005-10-20
The goal of this small HOWTO is to create a custom keyboard shortcut to run a software (like xmms, 3ddesk, ...) or what command line you want (xkill, transset 0.5, ...). Personally i use this trick to launch xkill, different values of transset and also alltray.

**[SIZE="3"]A- Using xbindkeys, works for each desktop (KDE, GNOME, XFCE, ...)[/SIZE]**

**[SIZE="2"]1[/SIZE]**- First install xbindkeys : ```
sudo apt-get install xbindkeys
```

**[SIZE="2"]2[/SIZE]**- Install xbindkeys-config, it's a GTK frontend for xbindkeys so it' easy to configure xbindkeys with that. ```
sudo apt-get install xbindkeys-config
```

**[SIZE="2"]3[/SIZE]**- Configuration
Launch xbindkeys : ```
xbindkeys
```Then launch the GUI : ```
xbindkeys-config
```And then enjoy how it's easy to configure shortcuts with this GUI ;)



**[SIZE="3"]B- Using metacity (the default GNOME window manager)[/SIZE]**
In the example i give, i want to start xkill (graphical kill) using "Alt + a" shortcut.
You will see some screenshots from _aysiu _at the bottom of the post.


**[SIZE="3"]1[/SIZE]**- Open GConf editor (Applications -> System Tools -> Configuration Editor), go to apps -> metacity -> keybinding_commands, and now choose a command, for my example I choose command_1. Edit command_1 writing xkill in order to run xkill (or every command you want to launch like in a terminal).

**[SIZE="3"]2[/SIZE]**- In the same directory go to global_keybindings. Edit command_1 (or the command you choose in part 1) with the wanted shortcut like that : <Alt>a (to use the windows key just edit the field with **Super_L**)


**[SIZE="3"]Misc[/SIZE]**
If you are looking for the name a key, the tool **xev** will help you. Just type **xev** in a terminal then you will see an output for each key you hit.
There are some output exemples of xev in this thread.

that's all !

Enjoy  ;-)

---

### Post by Mustard on 2005-10-27
I like this one. :)

---

### Post by No6 on 2005-10-28
Great! :roll:

I've been using xbindkeys... Ah well you learn something new everyday. :-)

---

### Post by bionnaki on 2005-10-28
anyway to make a keyboard shortcut that'll show hidden files in nautilus? I'd like to change from control-H to something easier...

---

### Post by Gandalf on 2005-10-31
Great TIP Thx,
I would like to add that i've added another shortcut <Alt>z to killall xkill in case you changed your mind and want to quit xkill without killing something..
and i have a question, on my laptop Fn + F6 suppose to lock my screen ( lock PC) but it does eject the DVD-ROM, anyone knows how to change this?

Thanks

---

### Post by frodon on 2005-11-01
You can manage that in System > Preferences > keyboard shortcut in the desktop section. There is an eject field and a lock screen field to specify keyboard shortcuts.

Happy to know that you like this small TIP ;)

---

### Post by Chris Tucker on 2005-11-28
how do you add key codes? like my custom volume up is command 'volmute increase' and button code is 0xb0 ..

---

### Post by Chris Tucker on 2005-11-28
nevermind, used another tutorial to add XF86 syms to my keys

---

### Post by frodon on 2005-11-28
nice !

May you put the link here for other users ?

Thanks

---

### Post by Chris Tucker on 2005-11-29
[http://www.djlosch.com/tutorial_debian.php#pcm_volume_link](http://www.djlosch.com/tutorial_debian.php#pcm_volume_link)
[http://ubuntuforums.org/showthread.php?t=27039&highlight=metacity+key+codes](http://ubuntuforums.org/showthread.php?t=27039&highlight=metacity+key+codes)
used those two to fix my problem where volume keys controlled Master (which affected nothing) to change to control PCM.

---

### Post by Hebus95 on 2005-11-29
How to use the key between Ctrl and Alt ?:rolleyes:  You know the key with a flag ?

I would create a win+E shortcut to launch nautilus.

---

### Post by frodon on 2005-11-29
I think you should enter **<Super_L>e**, however run "xev" in a terminal it will tell you the keysim of each key you hit.

---

### Post by Hebus95 on 2005-11-29
<Super_L> doesn't work, but I finally found how to do the trick :

use <Mod4> to create a shortcut with the Windows key.

It would be good to add a table with such equivalents in the wiki.

---

### Post by frodon on 2005-11-29
Happy that you found what you was looking for :)

With my keyboard Super_L works but it might be different for some keyboards.
I don't think a table is needed in the wiki because **xev** is a tool which allow you to know the keysim of each key of the keyboard, then all you have to do to know the keysim (even for multimedie buttons) is to run xev and hit the wanted key.

---

### Post by 0okami on 2005-12-07
[QUOTE=frodon]1- Open GConf editor,....[/QUOTE]

ok, where do i find that GConf editor? 

I checked my applications menu and didnt see that in there. 
Checked:
system->pref, not there.
system->admini...not there.  
applications->system tools... not there. 

even tried running GConf in a terminal... 

is there another name it might go by? 
sorry, still new to this.

---

### Post by frodon on 2005-12-07
It's in Applications -> System Tools -> Configuration Editor.

I will update the howto if it isn'e enough clear.

---

### Post by aysiu on 2005-12-07
The command is actually ```
gconf-editor
```

---

### Post by 0okami on 2005-12-07
Thanks! got it.

---

### Post by frodon on 2005-12-07
Thanks aysiu i will put your screenshot in the HowTo if you're ok ;)

---

### Post by aysiu on 2005-12-07
[QUOTE=frodon]Thanks aysiu i will put your screenshot in the HowTo if you're ok ;)[/QUOTE] Sure thing.

---

### Post by 0okami on 2005-12-07
[QUOTE=Hebus95]<Super_L> doesn't work, but I finally found how to do the trick :

use <Mod4> to create a shortcut with the Windows key.

It would be good to add a table with such equivalents in the wiki.[/QUOTE]

if you dont mind, could you clarify on the <Mod4> ? 

i ran xev and i got: 

```

    KeyRelease event, serial 29, synthetic NO, window 0x3a00001,
    root 0x113, subw 0x0, time 4022236, (565,168), root:(583,316),
    state 0x50, keycode 115 (keysym 0xffeb, [COLOR="Red"]Super_L[/COLOR]), same_screen YES,
    XLookupString gives 0 bytes:

```

Howevr, using <Super_L> does not trigger 3ddesk. 
If i use <alt>F3, it triggers, so im sure my other settings are ok. Just not sure what Might be failing for <Super_L>

I tried putting in <Mod4> to test. No luck either.


[B]
===============edit===============
[/B]
Never mind :D I got it working with Super_L without the <brackets> just plain:
***Super_L***

Thanks.

============end edit===============

---

### Post by Rinzwind on 2005-12-07
Ookami: frodon  has an e behind the <Super_l>

He says "<Super_L>e"?

Nevertheless I didn't get it working with <Super_L>e or <Super_L> :D

---

### Post by frodon on 2005-12-07
Strange, it works without any problems for me.

I will check that tomorow after my job because i'm not in front ubuntu now (in front of red hat at work now lol).
However i will update the HowTo the next week, i think, i will add another way to bind keys which i also use, the tool is called xbindkey.

EDIT : I just see your edit Ookami, glad it works for you too, i will also add that in the guide because many people like to use the windows key.

---

### Post by 0okami on 2005-12-07
[QUOTE=frodon]EDIT : I just see your edit Ookami, glad it works for you too, i will also add that in the guide because many people like to use the windows key.[/QUOTE]

Tell you the truth, i've never used the windows key untill now. Not even in windows ;) 3ddesktop gives me a good reason to use it. :)

---

### Post by Rinzwind on 2005-12-07
This is what I made of it:

[img]http://www.warofemperium.com/pics/snapshot1.png[/img]
[img]http://www.warofemperium.com/pics/snapshot2.png[/img]

But the stupid key doesn't want to open firefox.

And yes you can abuse these pics too ;)

---

### Post by 0okami on 2005-12-07
[QUOTE=Rinzwind]This is what I made of it:
But the stupid key doesn't want to open firefox.
[/QUOTE]

interesting. run[COLOR="Red"]*** xev***[/COLOR] in the terminal, press that windows key and post us what the details say in the terminal.

---

### Post by Rinzwind on 2005-12-07
I get this
> 
KeyPress event, serial 27, synthetic NO, window 0x3200001,
    root 0x46, subw 0x0, time 2399688, (882,-241), root:(885,426),
    state 0x0, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x3200001,
    root 0x46, subw 0x0, time 2399759, (882,-241), root:(885,426),
    state 0x40, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes:


So I'd say I did it correctly.

---

### Post by Hebus95 on 2005-12-07
Ctrl      <=>     <Control>    or     <Ctrl>
Alt       <=>       <Alt>        or   <Mod1>    or     <meta>
Alt Gr   <=>      <Mod5>
Win      <=>     <Mod4>      or    <super>   or     <hyper>
Shift     <=>     <Shift>
Menu    <=>     <menu>

---

### Post by Hebus95 on 2005-12-07
Depending on what you want to do you will use Super_L/Super_R or <Mod4>.
Use <Mod4> if the win key is associated with another key. example : <Mod4>e
You consider here that win is a shift key.
When you use Super_L the win key lost this behaviour. You can use Super_L to popup a menu for exemple.
Only for experimental purpose try : <Mod4>Super_R :smile:

---

### Post by amokoura on 2005-12-08
Pressing the left Winbutton tells me this:
```
KeyPress event, serial 26, synthetic NO, window 0x3a00001,
    root 0x48, subw 0x3a00002, time 83486908, (52,31), root:(766,280),
    state 0x10, keycode 115 (**keysym 0x0, NoSymbol**), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3a00001,
    root 0x48, subw 0x3a00002, time 83487171, (52,31), root:(766,280),
    state 0x10, keycode 115 (**keysym 0x0, NoSymbol**), same_screen YES,
    XLookupString gives 0 bytes:
```

So I guess it's not possible to use it for keyboard shortcuts. The right Winbutton works ok, though..

---

### Post by frodon on 2005-12-14
[COLOR="Sienna"][SIZE="4"]**The HowTo has been updated !**[/SIZE][/COLOR]

---

### Post by Mustard on 2005-12-14
I just thought I would mention that xbindkeys-config 0.1.3-1 is in the universe repository (for warty, hoary, breezy and dapper), so its installable using apt-get.

It comes up as a suggested install when you use apt-get to install xbindkeys.

Is the command to start the gui using this command a typo?

```
xbindkeys_config
``` ?

because after installing using apt-get I used this command to start the gui

```
xbindkeys-config
```

---

### Post by frodon on 2005-12-14
Yep you're right, i wrote it yesterday before going to sleep ;)

I will update the guide.

thanks

EDIT : strange for me the command is really xbindkeys_config but i don't use the ubuntu package

---

### Post by diffuser78 on 2006-01-03
That was good help

> **frodon]The goal of this small HOWTO is to create a custom keyboard shortcut to run a software (like xmms, 3ddesk, ...) or what command line you want (xkill, transset 0.5, ...). Personally i use this trick to launch xkill, different values of transset and also alltray.

**[SIZE="3"]A- Using xbindkeys, works for each desktop (KDE, GNOME, XFCE, ...)[/SIZE]**

**[SIZE="2"]1[/SIZE]**- First install xbindkeys : ```
sudo apt-get install xbindkeys
```

**[SIZE="2"]2[/SIZE]**- Install xbindkeys-config, it's a GTK frontend for xbindkeys so it' easy to configure xbindkeys with that. ```
sudo apt-get install xbindkeys-config
```

**[SIZE="2"]3[/SIZE]**- Configuration
Launch xbindkeys : ```
xbindkeys
```Then launch the GUI : ```
xbindkeys-config
```And then enjoy how it's easy to configure shortcuts with this GUI  said:**
> B- Using metacity (the default GNOME window manager)[/SIZE]**
In the example i give, i want to start xkill (graphical kill) using "Alt + a" shortcut.
You will see some screenshots from _aysiu _at the bottom of the post.


**[SIZE="3"]1[/SIZE]**- Open GConf editor (Applications -> System Tools -> Configuration Editor), go to apps -> metacity -> keybinding_commands, and now choose a command, for my example I choose command_1. Edit command_1 writing xkill in order to run xkill (or every command you want to launch like in a terminal).

**[SIZE="3"]2[/SIZE]**- In the same directory go to global_keybindings. Edit command_1 (or the command you choose in part 1) with the wanted shortcut like that : <Alt>a (to use the windows key just edit the field with **Super_L**)


**[SIZE="3"]Misc[/SIZE]**
If you are looking for the name a key, the tool **xev** will help you. Just type **xev** in a terminal then you will see an output for each key you hit.
There are some output exemples of xev in this thread.

that's all !

Enjoy  ;-)

---

### Post by kuad on 2006-01-14
Is it possible to create a shortcut that will open the Logout dialog (instead of having to click System > Logout) ? I can't figure out what command is executed when you click System > Logout. Thanks

---

### Post by robotgeek on 2006-01-19
[QUOTE=amokoura]Pressing the left Winbutton tells me this:
```
KeyPress event, serial 26, synthetic NO, window 0x3a00001,
    root 0x48, subw 0x3a00002, time 83486908, (52,31), root:(766,280),
    state 0x10, keycode 115 (**keysym 0x0, NoSymbol**), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3a00001,
    root 0x48, subw 0x3a00002, time 83487171, (52,31), root:(766,280),
    state 0x10, keycode 115 (**keysym 0x0, NoSymbol**), same_screen YES,
    XLookupString gives 0 bytes:
```

So I guess it's not possible to use it for keyboard shortcuts. The right Winbutton works ok, though..[/QUOTE]
Try changing your keyboard layout from Preferences -> Keyboard -> Layout Tab

---

### Post by Havoc on 2006-01-26
You think I could map the "Mouse Wheel Up" and "Mouse Wheel Down" Actions to commands?

Here's the output...

```
ButtonPress event, serial 29, synthetic NO, window 0x3800001,
    root 0x132, subw 0x0, time 10908339, (112,177), root:(132,248),
    state 0x0, button 4, same_screen YES

ButtonRelease event, serial 29, synthetic NO, window 0x3800001,
    root 0x132, subw 0x0, time 10908339, (112,177), root:(132,248),
    state 0x800, button 4, same_screen YES

```

...for the mouse wheel up "button".Since this is quite cryptic to me, could someone elaborate for me?
I've tried "button 4" and "<button 4>" but no go.
Please?

Thanks! :cool:

---

### Post by frodon on 2006-01-26
Not sure that Mouse Wheel up/down alone will work good or be a good idea, however i use some shortcuts like Ctrl + Mouse Wheel up to run some commands without any problems using xbindkeys.
Do you really need to use mouse wheel up/down alone, because you might get some conflicts with some apps.

---

### Post by Havoc on 2006-01-26
Yes, I was meaning to use <Ctrl><Shift> and mouse up "button" to invoke the "transset-df --inc 0.1" command and likewise on the Mouse wheel down "button".

So, your answer was, use "xbindkeys"? :confused: 

Thanks for the quick answer.

---

### Post by frodon on 2006-01-26
It's what i did because i found it easier (more fast) to set so i didn't try with metacity but it should work too, follow the part A of the guide it will take you 2 min to get it work. Xbindkeys is really light and powerful and don't depend on any window manager.
Another link if you want to edit the file by hand (but i prefer the GUI ;) ) : [http://gentoo-wiki.com/TIP_Xorg_X11_and_Tranparency#transset-df](http://gentoo-wiki.com/TIP_Xorg_X11_and_Tranparency#transset-df)

---

### Post by Havoc on 2006-01-26
Dammit!

Thanks! Thank you for your quick and informational posts!

Off to eyecandy kingdom! :D

---

### Post by mell0w on 2006-02-02
sorry for the newb question, but what do i enter as a value if i just want to open a directory folder?

---

### Post by OneSeventeen on 2006-02-02
[QUOTE=mell0w]sorry for the newb question, but what do i enter as a value if i just want to open a directory folder?[/QUOTE]
I use:
```

nautilus /path/to/file --browser

```
(--browser is optional, but it makes it more legible to me!)

---

### Post by OneSeventeen on 2006-02-02
[QUOTE=frodon]Not sure that Mouse Wheel up/down alone will work good or be a good idea, however i use some shortcuts like Ctrl + Mouse Wheel up to run some commands without any problems using xbindkeys.
Do you really need to use mouse wheel up/down alone, because you might get some conflicts with some apps.[/QUOTE]
Any tips on how to do this?  When I use "get keys" and hold down control and move the mouse wheel up, it displays the following:
Control + Control_L | m:0x4 + c:37

Then when I apply it, and hold down control and move the mouse wheel up, it does nothing.

If I use get keys to do any other non-mouse related combination, it works just fine.

Is there any other software I need to include to get it working?  (the mouse wheel does work in other apps)

---

### Post by mell0w on 2006-02-02
thanks for your help OneSeventeen :)

one more thing, is it possible to make a shortcut key that slides the panel bar close or open?

---

### Post by frodon on 2006-02-03
[QUOTE=OneSeventeen]Any tips on how to do this?  When I use "get keys" and hold down control and move the mouse wheel up, it displays the following:
Control + Control_L | m:0x4 + c:37

Then when I apply it, and hold down control and move the mouse wheel up, it does nothing.

If I use get keys to do any other non-mouse related combination, it works just fine.

Is there any other software I need to include to get it working?  (the mouse wheel does work in other apps)[/QUOTE]Strange, i have no problem with that, did you tried to restart xbindkeys ?

However if you're ok to edit the xbindkey.rc file to add your shortcuts, this exemple will show you how to edit the file to use Ctrl + mouse wheel but it would have work with "get keys" : 
[http://gentoo-wiki.com/TIP_Xorg_X11_and_Tranparency#transset-df](http://gentoo-wiki.com/TIP_Xorg_X11_and_Tranparency#transset-df)

---

### Post by BitTorrentBuddha on 2006-02-19
when running this command, I get the output ```
W: Couldn't stat source package list ftp://ftp.free.fr breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.free.fr breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
``` is there a way to fix this? (I've already run sudo apt-get update)

Just pressed on and ignored those messages, I would still like to know how to fix it or if it's causing any trouble, because I see it everytime I have to download anything... but now I have xbindkeys-config open, what is the command that opens the gui "run command" prompt? (the one like the "run application" panel addition, not gksuexec)

---

### Post by frodon on 2006-02-20
You get this message because the path to the plf repository you use is perhaps broken, so don't worry plf is just an extra repository which contain mainly proprietary codecs that you shoud have installed already.
So you can ignore these messages.

When you say "the gui run command", do you mean what you get by pressing Alt+F2 ?

---

### Post by BitTorrentBuddha on 2006-02-20
yeah, is there a command for that?
and also is there a way to determine if somethings running, then do ____ (e.g. control+esc = xkill, but  if i press contro+esc again = killall xkill)

---

### Post by frodon on 2006-02-21
I don't remeber the command but it should be gnome-****** i will search this evening.
For you second question i would create a script and make a shortcut to launch the script.
The script would look like that : ```
#!/bin/bash
a=`ps -aef | grep -i xkill| awk ' {if ($8 == "xkill"){printf "2"}} '`
if  [[ $a = "" ]]
then
	xkill &
else
	killall xkill
fi
```Make the scripts executable : ```
sudo chmod +x the_script
```And use the full path of the script as command for the shortcut and the trick is done.

---

### Post by BitTorrentBuddha on 2006-02-21
out of blatent curiosity where would I go about learning shell script?

---

### Post by Super King on 2006-02-24
Awesome HowTo, now my old friend Ctrl-Alt-Delete is back!:mrgreen:

---

### Post by Ancalagon on 2006-03-24
Super King,

Did you figure out a way to make Ctrl-Alt-Delete pull up the logout menu, or do you just have those keys bound to something like:

shutdown -h now

Thanks!

---

### Post by binarysleeper on 2006-03-31
If you are using KDE you can use this command to bring up the logout screen:
dcop kdesktop KDesktopIface logout

HTH

---

### Post by Bubba Ho-Tep on 2006-04-14
Errrr I hope I'm posting in right place for this - I've a problem getting this to work.

I'm trying to get gnome terminal to open with the Windows key - 

when I hit "Get Key" the terminal i opened xbindkeys-config with reports "Operation not permitted". Despite this xbindkeys spawns a window asking me to choose a key. I do this and it captures this: 

Mod4 + Super_R | m:0x40 + c:116   (ie my windows key)

If I hit "Run Action" then sure enough it opens a terminal. But when I save and close xbindkeys-config - it does nothing.

Er my Linux knowledge is pretty small at the mo so my only idea is that it's something to do with permissions on the er thingummy. I looked at .xbindkeysrc - and I'm the owner with read/write permissions so er I dunno...

I also tried mapping opening a terminal to another key but no joy. 

Can anyone help?

BH-T

---

### Post by gmcle454 on 2006-05-15
Thanks, I had no idea what the keystroke value was for the windows key. I could see the <Mod4> but I think <Super_L> / <Super_R> may be an unnecessary tribute to "the other os." :rolleyes: ;) 

Thanks for the help!

---

### Post by searayman on 2006-06-21
installed it and opened it once, but didnt understand it. ANywho i went to open it a second time and got this:

mike@mike-desktop:~$ xbindkeys
Error : /home/mike/.xbindkeysrc not found or reading not allowed.
please, create one with 'xbindkeys --defaults > /home/mike/.xbindkeysrc'.
or, if you want scheme configuration style,
with 'xbindkeys --defaults-guile > /home/mike/.xbindkeysrc.scm'.
mike@mike-desktop:~$


any ideas?

also if we get it workign could u help me make a keybind for the windows key? i want the windows key to run the command: 3ddesk

---

### Post by armandg on 2006-08-21
> **amokoura said:**
> (...)So I guess it's not possible to use it for keyboard shortcuts. The right Winbutton works ok, though..

I'm using norwegian keyboard (with æ, ø and å-keys) and had to set shortcut-key to Select for some reason. try that. ;)
EDIT: this was concerning the left win-button

---

### Post by BramKuijper on 2006-08-29
Instead of xbindkeys, I am trying to use the Keyboard Shortcuts Manager under System > Preferences to make a shortcut. 

As soon as I try to press a key which is anything besides a function key, Alt, Delete, Shift...
GNOME's 'find string' box appears at the lower right end of the list and blocks any further typing, so that I cannot assign anything to K, L, M or combinations of Alt+K, Alt+M, etc...

I assume this is a bug, or totally expected behavior?  ](*,)

---

### Post by malcolm1234 on 2006-12-17
> **Ancalagon said:**
> Super King,

Did you figure out a way to make Ctrl-Alt-Delete pull up the logout menu, or do you just have those keys bound to something like:

shutdown -h now

Thanks!

I'm trying to bind a key to the logout menu. 

I tried System->Preferences->Keyboard Shortcuts and then setting a key for Logout, but the key doesn't respond. Any ideas?

---

### Post by cha0s on 2007-02-15
What key was it, malcolm1234? When I was doing this I accidentally set the wrong key, and it worked (luckily I could cancel :P)

Just wanted to say thanks =) This helps me a Lot.

---

### Post by 403jungle on 2007-10-19
> **gmcle454 said:**
> Thanks, I had no idea what the keystroke value was for the windows key. I could see the <Mod4> but I think <Super_L> / <Super_R> may be an unnecessary tribute to "the other os." :rolleyes: ;) 

Thanks for the help!

I removed the logo on the button. I haven't been able to put a ubuntu logo in place of it yet though.

:)

---

### Post by coelhao on 2007-12-29
hey on gnome how do I bind <Mod4>T to open a terminal window...
i got it to open using xterm but its quite ugly, I want the cute terminal just like when I click Applications->Accessories->Terminal... what is the command?

anyways how do I know what comands the shortcut in the application menu execute?

---

### Post by KrazyPenguin on 2008-02-09
If you wanted to retreive these settings for a fresh install, where might they be stored??

(saves having to tweaks all those commands again)

;-)

---

### Post by dingclancy on 2008-04-17
Hello!

How do yo uninstall xbindkeys?

Thanks!

---

### Post by frodon on 2008-04-18
Like your other programs using synaptic or apt-get directly.
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by Jphenow on 2008-04-28
hey i was trying to do this and found out whenever i do sudo i get this > sudo: unable to resolve host phenow-desktop


any ideas??

thanks guys

---

### Post by kevin66 on 2008-04-30
How do you uninstall?

---

### Post by frodon on 2008-04-30
Scroll up 2 times, post #66

---

### Post by demonzrulaz on 2008-07-12
Hey guys, I'm using a laptop so I only have one windows key. I tried the command xev and pressed the windows key and this is what I got:

state 0x40, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,

I want to be able to use the windows key in combination with other keys, like Win+T = Terminal, Win+R = Gnome-Do, Win+E = Nautilus, etc. I tried <Mod4>T but that doesn't work. <Super>T and <Super_L>T definately doesn't work and Super_L by itself works but I can't use any extra buttons. Can you guys help? Thanks in advance.

---

### Post by airjaw on 2008-09-15
Hey guys.. I set up a shortcut to open up terminal but I actually want the shortcut to open up Konsole.. 

I tried xbindkeys but it won't run for some reason. T his is the error:

airjaw@airjaw-laptop:~$ xbindkeys
Error : /home/airjaw/.xbindkeysrc not found or reading not allowed.
please, create one with 'xbindkeys --defaults > /home/airjaw/.xbindkeysrc'.
or, if you want scheme configuration style,
with 'xbindkeys --defaults-guile > /home/airjaw/.xbindkeysrc.scm'.


Any ideas? Thanks.

---

### Post by Teonline on 2008-10-26
Hello, i am using compiz as window manager so i can't use metacity's bindings. I downloaded xbindkeys and his gui. I tried with the gui and all worked fine until i restart my pc, all my shortcuts deleted (or i suppose so). I tried also gediting the xbindkeysrc file but nothing hppened.
If i digit:
 ```
xbindkeys -s
```
i get this return:
```
Error in alocation of keys
```

Any suggestion? 

Thanks a lot!:)

---

### Post by steve101101 on 2008-11-30
worked great to get the brightness changed on my sony vaio. thanks.

---

### Post by lukjad on 2008-11-30
will have to try it.

---

### Post by jastonas on 2008-12-11
i think gconf editor is just fine compared to messy xbindkeys :)
xkill rulz!

---

### Post by Johnpeter on 2008-12-24
What is the keyboard shortcut in Microsoft Word 2007 for highlighting text with a color?I found a way to do it using older versions of Word, but nothing for 2007. Can anyone help? Or tell me how to add custom keyboard shortcuts?

---

### Post by gabrielshier on 2009-05-14
Extremely helpful!
Thanks alot! :p

---

### Post by toejamfootball on 2009-06-08
Thanks :)

---

### Post by unimatrix on 2009-06-22
Can I do something like this with xbindkeys:
```
  m:0x10 + b:10 + b:14
```
Well, obviously this doesn't work or I wouldn't be asking, but how do I do it?
I want to bind a combination of two mouse buttons to trigger something.

---

### Post by unimatrix on 2009-06-22
Ok I've found one hacky way to do this.

```

# Toggle mouse modifier:
"echo 1 > ~/.mymousemod"
  m:0x10 + b:10

# Untoggle mouse modifier:
"echo 0 > ~/.mymousemod"
  m:0x10 + b:10 + Release

# Volume Up:
"if [ "`cat ~/.mymousemod`" -eq "1" ]; then aumix -v+5 ; fi"
  m:0x10 + b:14

# Volume Down:
"if [ "`cat ~/.mymousemod`" -eq "1" ]; then aumix -v-5 ; fi"
  m:0x10 + b:13

```

This will make a virtual modifier key. The state will be written in ~/.mymousemod as 1 or 0. 1 meaning the modifier is pressed, and 0 that it is not. Before executing the command on another mouse button, just check whether the 'modifier' is pressed.


Here's a new problem though. Binding any key with xbindkeys will override its main function. Is there any way to bind it to something and still let it do what it originally does?

---

### Post by Trogdole on 2009-07-31
[FONT=Times New Roman][SIZE=2]Gonna sound like a total noob right now, but how do I know what to put for the action? Are these terminal commands or what? I'm new to Ubuntu, but this would be beyond me in Windows too. For instance, I want a global shortcut to pause/play Songbird. But I have no idea what that action is, or how to find it. Any help? Point me in the right direction? Tell me I'm in over my head? Thanks.[/SIZE][/FONT]

---

### Post by unimatrix on 2009-08-01
> **Trogdole said:**
> [FONT=Times New Roman][SIZE=2]Gonna sound like a total noob right now, but how do I know what to put for the action? Are these terminal commands or what? I'm new to Ubuntu, but this would be beyond me in Windows too. For instance, I want a global shortcut to pause/play Songbird. But I have no idea what that action is, or how to find it. Any help? Point me in the right direction? Tell me I'm in over my head? Thanks.[/SIZE][/FONT]

Yes, they are commands that you would normally type into the terminal. By default you cannot control Songbird from terminal (no play/pause/... parameters), however I've found an addon that makes it possible: [http://addons.songbirdnest.com/addon/1381](http://addons.songbirdnest.com/addon/1381)

With this addon you get songbird parameters such as play, stop, previous...
You can test them by typing them into the terminal this way:
```
songbird --pause
```
This is also the command you would put into your .xbindkeysrc file.
If by some reason it doesn't work, you can also try using the full path to songbird:
```
/usr/bin/songbird --pause
```
Of course, instead of pause you can use other parameters too. They are listed on the addon site I've posted.

---

### Post by celem on 2009-11-10
frodon - thank you so much. The keybindings were so arcane. Now I have concurred my keyboard!

---

### Post by WannabeFantasma on 2010-02-02
Cool I found this :D

might test this out!

---

### Post by wmhunter96 on 2010-04-19
Great job thanks a video would be nice 2 :lolflag:

---

### Post by schmendrick on 2010-11-28
just wanted to say thanks, xbindkeys solved all my problems!

---

### Post by DarkSideKlyde on 2011-03-10
Thanks for the tip about xkeybinds. I couldn't figure out how to use the program at first. When I pressed the 'Get Key' button, the program closed. I Googled it and got this:

[FONT=Verdana, Arial, Helvetica][SIZE=2][Before you do anything else you must create a default configuration file with this command:  [/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica][SIZE=2]$ **xbindkeys --defaults > $HOME/.xbindkeysrc**
[/SIZE][/FONT]     [FONT=Verdana, Arial, Helvetica][SIZE=2]xbindkeys[/SIZE][/FONT][FONT=Verdana, Arial, Helvetica][SIZE=2] won't work without this.][/SIZE][/FONT]

from this page : [http://www.linuxplanet.com/linuxplanet/tutorials/6401/2/](http://www.linuxplanet.com/linuxplanet/tutorials/6401/2/)

After I created the configuration file as stated above and the program worked as it should. Hope this helps somebody.

---

### Post by swajime on 2011-12-23
I've got a dell inspiron n5510.  It has 3 buttons to the top right of the keyboard that I've been trying unsuccessfully to set up.  The xev is not responding to them.

The left button opens the DASH home window.
The middle button adds "atkbd serio: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0). atkbd serio0: Use 'setkeycodes e6e <keycode>' to make it known." to kern.log and syslog.  The right button does nothing.

They should be Settings, Support, & Display On/Off.

Thanks,


John

---

