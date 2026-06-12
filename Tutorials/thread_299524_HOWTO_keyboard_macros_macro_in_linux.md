---
title: "HOWTO keyboard macros macro in linux"
date: 2006-11-14
forum: Tutorials
---

### Post by grizzly on 2006-11-14
Yup, its indeed possible to have system-wide application independent macros in unix! thanks to xmacros and whoever who wrote a guide somehere i don't remember.

Step 1. Install the app 
> aptitude install xmacro  
Step 2. Record the macro: > xmacrorec -d 1400 > ~/quote wait...  
Step 3.  xmacro isn't perfect so open ~/quote for editing, as many lines are repeated and need to be removed.   
Step 4. Replay the macro > cat ~/quote | xmacroplay ":0.0" 

Basically  xmacroplay plays the commands from a text file.The text file can be written manually or by the above recording method. Reading the examplbelow should make it all very easy.
  **EXAMPLE** 
>          Delay 1  # Always add this!!
KeyStrPress bracketleft
KeyStrRelease bracketleft
String quote
KeyStrPress bracketright
KeyStrRelease bracketright
KeyStrPress bracketleft
KeyStrRelease bracketleft
KeyStrPress slash
KeyStrRelease slash
String quote
KeyStrPress bracketright
KeyStrRelease bracketright
Delay 1           #delay
KeyStrRelease Left
KeyStrPress Left
KeyStrRelease Left
KeyStrPress Left
KeyStrRelease Left
KeyStrPress Left
KeyStrRelease Left
KeyStrPress Left
KeyStrRelease Left
KeyStrPress Left
KeyStrRelease Left
KeyStrPress Left
KeyStrRelease Left
KeyStrPress Left
KeyStrRelease Left
KeyStrPress Lef
  The above types [ q u o t e ] [ / q u o t e ] followed by 8 'left arrow' keys so that the cursor is between [qote] & [/quote] priceless..  

**Example 2** 
Delay 1           #delay
Sending a hotkey - Ctrl + g 
> KeyStrPress Control_R 
KeyStrPress g KeyStrRelease g 
KeyStrRelease Control_R  
 
=== Problems? 
1. Read the last 4 topics on [http://xmacro.sourceforge.net/](http://xmacro.sourceforge.net/) for a better understanfing of the macro file. its simple btw 
2. try adding a lil delay (look in above example for how)
3. How to play the macro?? You can use xbindkeys/khotkeys(kdeonly) to assign a shortcut for the macro.

---

### Post by David Valentine on 2006-12-01
There's a new GUI alternative I would love to see in the repos:  [JW_Record_Playback]("http://members.home.nl/wijnenjl/Record_Playback_Python_TclTk_INI_Wx_EN_01.html").  How do we request such things, since it's apparently not appropriate for the backports/repository forum?

---

### Post by mike_m on 2007-09-02
thanks for the example, but how do you stop the macrorec?

```
xmacrorec -d 1400 > ~/quote
```
I see "-d 1400" is delay rec by 1.4 sec 
and "> ~/quote" is save macro file to quote

but don't we need a quit rec key?
I can't find this anywhere, thanks.

PS I did get xmacroplay to replay my hand typed script into an open doc:
```
Delay 1 # Always add this!!
String mikemason.org
KeyStrPress Return
KeyStrRelease Return
String my web address
```

Not much, but a test

---

### Post by James7 on 2007-09-04
Would this program be useful if you wanted to have quick keyboard shortcuts to enter a string of text or character not on your keyboard?

For example, could I use [COLOR="Red"]CTL-ALT-a[/COLOR] to put a "à" into any text field in any open program? And say, [COLOR="Red"]CTL-ALT-SHIFT-A[/COLOR] to put a "À" into any text field in any open program?

Any help much appreciated ! :)

---

### Post by mike_m on 2007-09-05
Not from what i see, I tried to set hotkeys (keyboard shortcuts) but they would not run the command lines needed ie: (cat testing.macro | xmacroplay -d 100 :0)

So I have to Alt+F2 then type "cat testing.macro | xmacroplay -d 100 :0"

---

### Post by James7 on 2007-09-06
Thanks, mate, this looks a bit beyond me. I was looking for a way to do what [KeyText]("http://www.keytext.com/") does in Windows. Perhaps there is another program out there....

---

### Post by newsun on 2007-09-07
This definately looks promising and I will definately try it out when I get my system76 laptop or my macmini back up. In the meantime, I am curious about doing dynamic thing in the macros like having a date print out for dating a note.

i.e.

This is a note

type key shortcut and the date is filled in at cursor.

2007-09-07 - This is a note

---

### Post by mike_m on 2007-09-08
I don't think xmacro can do that.

---

### Post by billynomates on 2008-09-14
This is awesome!

[Here is a page of all the keys to help you write your own.]("http://www.openmash.org/lxr/source/xlib/X11/keysymdef.h?c=tk8.3) Just take off the "XK_" before each one.

In Compiz Settings, if  you go to General Options, and then to the commands tab, you can fire off events on keyboard short cuts. 
For example, I have set it so that I can write my email address super-fast (for forms and stuff). So in one of the Command boxes I have written 

```
cat ~/path/to/macro | xmacroplay ":0.0"
```

and then in the corresponding Key Bindings box, I have "<super> apostrophe", so now when I press Super+' it'll type my email address.

The possibilities are endless!

---

### Post by roystonlodge on 2010-03-20
Oh man, I am finally gonna pwn at Armagetron...

---

### Post by edc80 on 2011-12-05
I found a much friendlier way to do these.  Try installing Autokey-gtk using the Synaptic Package Manager.  The keyboard macros work and the graphic user interface makes it easy for novices like me to set these up.

I found this tutorial article to be especially helpful:

[http://saravananthirumuruganathan.wordpress.com/2010/04/14/autokey-linux-utility-for-text-substitution-hotkeys-and-desktop-automation/]("http://saravananthirumuruganathan.wordpress.com/2010/04/14/autokey-linux-utility-for-text-substitution-hotkeys-and-desktop-automation/")

TJTM,
-Ed.

---

