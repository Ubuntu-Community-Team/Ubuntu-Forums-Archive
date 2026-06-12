---
title: "[SOLVED] How do I run a key press as a command?"
date: 2008-01-04
forum: The Cafe
---

### Post by urukrama on 2008-01-04
I am **not** looking to assign commands to keyboard keys, but rather the other way round. I am looking for an application that allows me to run the pressing of a key on my keyboard as a command. In other words, that if I run command *xyz* it is the equivalent of pressing key *a*.

I've been looking for it on these and other Linux forums, and on Google, but haven't had much success yet. I hope it is possible, as every key has a unique code that could perhaps be simulated on the command line by a particular application. 

Any suggestions anyone?

---

### Post by scizzo on 2008-01-04
Sounds like you are trying to create a macro on the keyboard. So that for example: Ctrl+Alt+F1 is equivalent to Ctrl+F1

Am I right?

[https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys)

that link might help?

---

### Post by urukrama on 2008-01-04
> **scizzo said:**
> Am I right?

No. :-) I want to use a command for a keypress, not a keypress for another keypress or command.

---

### Post by SoulinEther on 2008-01-04
I am screaming at my keyboard "NO! NO!" when I read scizzo's response.

I am looking for the EXACT same thing!! If you find it, I want to know about it!

Hey, just got a thought.... maybe we should look at the source code for the gnome on screen keyboard....

Edit: Looking at onboard's source... it's not very clear to me... it uses GDK...and some object oriented programming that I don't understand in python yet.

---

### Post by Crashmaxx on 2008-01-04
Why do you need to output key presses? Why not just run the command you want from the command line? Or output the text you want if that is what you are trying to do?

---

### Post by cwej on 2008-01-04
You want to trigger a keypress event, right? What programming language (makes a difference)?  Does this link help? [http://www5.experts-exchange.com/Programming/Languages/Visual_Basic/Q_20460831.html](http://www5.experts-exchange.com/Programming/Languages/Visual_Basic/Q_20460831.html)

---

### Post by yabbadabbadont on 2008-01-04
Is btnx what you are looking for?

---

### Post by Lostincyberspace on 2008-01-05
What are you using it for?

---

### Post by SoulinEther on 2008-01-05
K, well, for me... it's probably best that I don't use it to issue a keyboard command, but I just wanted it as a bandaid solution.

I want to make a new Xfce panel that displays the name of the active window (this part i have not figured out...), and provides functionality to close, minimize, restore, etc the active window.

Xfce's default shortcuts are like Alt+F5 to grow/shrink, Alt+F8 to minimize, etc..... Because I don't want to go through the hell of figuring out how to directly call for the minimizing of the current window, (though i'm sure it's closely related to finding out what the title of the active window is), I wanted this bandaid solution to just press Alt+F5 on launching a script or quick program.

I think it would involve the use of GDK, at least for GTK purposes....

Or does someone know how to make direct X event calls or whatever?
..

(and for that matter, on the side, preferrably in python, could someone help me with how to manipulate an active window ? lol.)

Thanks.

---

### Post by popch on 2008-01-05
In that case I find the cure (simulating key strokes) worse than the ailment (wanting to manipulate a window), because I am sure that there must be an API do to just that.

However, I think there are solutions out there which do simulate keystrokes.

---

### Post by urukrama on 2008-01-05
> **yabbadabbadont said:**
> Is btnx what you are looking for?

No, but thank you. As far as i can tell, btnx can assign any keystroke or command to any button of your mouse, but that is not what I want (though some of the other posters seem to, though).

I want an application that I can use to simulate a key press at the command line. So that *nameoftheapp keycode* (or whatever form the command takes) equals pressing the key that has that keycode.

I was hoping something like that would exist. What if you have a script that needs some sort of confirmation from the command line (done automatically, without you pressing that key)?

I'd like to use this thing  -- once I find it! -- to trigger certain actions of applications that *only* run by pressing a key assigned to it globally.

---

### Post by Gordy on 2008-01-05
Your heading for a mass of problems when you do this.. You will learn soon what I mean...

---

### Post by forrestcupp on 2008-01-05
Why not just make a bash script and echo the letter?  For the letter Y,

```
#!/bin/bash
echo Y
```

Then just save the file as whatever you want and run it like a command.  You could even make a link to it in your panel or something so that if you click that icon, it will echo the letter Y to the terminal.

That's about as simple as it gets.

---

### Post by urukrama on 2008-01-05
Thanks forrestcupp. That looks very simple. :-)  I'll try it out later, but would this work with something like ScrollLock, PrintScreen, Ctrl, Delete, etc.?

---

### Post by napsilan on 2008-01-05
I don't know the exact details but I thought this was done using something like

echo KEY > /dev/keyboard

or I could be imagining things.

---

### Post by ugm6hr on 2008-01-05
I was looking for something that would simulate repeated keystrokes in order to turn off my power saving screen settings when I watch films.

But doesn't echo *display* text, rather than simulating key presses?

---

### Post by ReiKn on 2008-01-05
> **urukrama said:**
> 
I was hoping something like that would exist. What if you have a script that needs some sort of confirmation from the command line (done automatically, without you pressing that key)?


In bash scripts you can do something like this:

```
cat  <<+                                                                        
Input for program "cat" here between the plus-signs.                                                                       
+ 
```

And now it gives automatically the input between plus signs to the program before the <<

This way you can give automatically input to programs which ask for input during use.

---

### Post by Namtabmai on 2008-01-05
Try xkbevd.

E.g.

```
/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]"
```

Will send the Alt+Left key combination.

---

### Post by urukrama on 2008-01-06
> **Namtabmai said:**
> Try xkbevd.

Thank you. This is interesting, but this only works (as far as I can tell) to send text to the focussed windows. That is what the man pages said, and that is how it worked for me. 

But I want to send a (global) key press that triggers a command of an application. Xvkbd doesn't help with that, it seems.

(I had xkbevd installed, but needed to install xvkbd separately, btw)

---

### Post by urukrama on 2008-01-24
Sorry to bring this up again, but I haven't had any luck so far. I have tried all the suggestions, but nothing did what I wanted (I couldn't quite grasp what **ReiKn** and **napsilan** suggested, though).

To clarify why I want to achieve this, I'll give an example of why I want to use a command to simulate a keypress. When running, tilda is only shown when a particular key is pressed (F1) by default. I would like to bind that to a mouse action in Openbox or Pekwm, but I can only bind commands (or Openbox and Pekwm actions) to mouse actions in those window managers. That is why I would like to simulate a keypress.

The keys I am interested in are not the general letters or numbers, but things like F1-F12, Scroll_Lock, Print_Screen, etc.

So, any further suggestions? :-)

---

### Post by urukrama on 2008-01-25
I've found what I was looking for. With [xmacro]("http://xmacro.sourceforge.net/") and following [these]("http://www.wifizabreh.net/thiemel/Linux/X11-keyboard-macro.en.txt") instructions, I first recorded the keypress I wanted to simulate (with xmacrorec), and can now rerun that anytime I want (with xmacroplay).

Problem solved.

---

### Post by ReiKn on 2008-01-25
> **urukrama said:**
> Sorry to bring this up again, but I haven't had any luck so far. I have tried all the suggestions, but nothing did what I wanted (I couldn't quite grasp what **ReiKn** and **napsilan** suggested, though).

To clarify why I want to achieve this, I'll give an example of why I want to use a command to simulate a keypress. When running, tilda is only shown when a particular key is pressed (F1) by default. I would like to bind that to a mouse action in Openbox or Pekwm, but I can only bind commands (or Openbox and Pekwm actions) to mouse actions in those window managers. That is why I would like to simulate a keypress.

The keys I am interested in are not the general letters or numbers, but things like F1-F12, Scroll_Lock, Print_Screen, etc.

So, any further suggestions? :-)

You could try the program called xautomation (sudo apt-get install xautomation) . Then for sending F1 the call is

xte "key F1"

---

### Post by urukrama on 2008-01-26
Thanks, that is a little simpler.

---

### Post by Acglaphotis on 2008-01-26
try xsend, it does what you are looking for.

---

### Post by durand on 2009-12-16
> **Namtabmai said:**
> Try xkbevd.

E.g.

```
/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]"
```

Will send the Alt+Left key combination.

Thanks, that works great for my purposes! (Using spotify as an alarm clock)

---

### Post by lazyr on 2010-06-25
I find the easiest way to use xdotool (it's in the universe repository).

You can just use commands like:

```
xdotool key Ctrl+c
xdotool key Super+a
xdotool key Control+Alt+Right
xdotool key Control+Alt+Left
```

---

### Post by manoj_isi on 2010-08-02
xdotool did my job.. thanx all of you for this wonderful post..  


linux rocks

---

### Post by Zorgoth on 2010-08-02
Yay for xdotool!

---

### Post by bernabap on 2010-10-25
I need help ... I bought a multimedia control ([http://www.dealextreme.com/details.dx/sku.26368](http://www.dealextreme.com/details.dx/sku.26368)) for use with XBMC. This control comes with four shortcut keys already set to "Ctrl Alt A", "Ctrl Alt B", "Ctrl Alt C" and "Ctrl Alt D". I wanted to create a script to simulate the pressure of "i" key, which opens in XBMC the information of the selected movie. So I could create a shortcut to this script that has already set in my control to simulate the pressure of that key.

In Windows xp I could do exactly what I want to creating a VBScript like this:


 Set WshShell = WScript.CreateObject ("WScript.Shell")

WshShell.SendKeys "{i}"
WScript.Sleep 10

After  I created a shortcut to this script with "Ctrl Alt D", goes like every  time I open XBMC and select a movie I can click on the button on my  control that is set to "Ctrl Alt D" and display the Movie information.

Worked perfect in XP but I really want to get it working in Ubuntu!

I've tried to create several scripts and configured to run with the shortcut "Ctrl Alt D", but none of them work in XBMC.

I tried the following ways:

# First using xautomation:
/usr/bin/xte "key i";

# Attempt  2 with xdotool:
xdotool key i

These two options only work running through the terminal, nothing was displayed by the shortcut.

# Third option xkbevd:
/usr/bin/xvkbd-xsendevent-text "\ [i]"

This  method worked using the key for that shortcut in my control displaying  the letter "i" in the terminal, in gedit, within vim, but for some reason  does not work in XBMC. Neither worked in Google search.

Anyone have any ideas?

---

### Post by shafin on 2010-11-10
Thanks a lot.
I just used this to bind firefox 4 panorama to a screen edge

---

### Post by Biopyro on 2013-01-24
xdotool has worked perfectly to allow my media remote to work while also allowing the "home" and "mail" keys on my keyboard to act as media keys. Thanks guys.

I searched for "Ubuntu two keys one function action" and some other variations before I got here.

---

### Post by oldos2er on 2013-01-24
Ancient thread closed.

---

