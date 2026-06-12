---
title: "file-quit or X out"
date: 2009-09-01
forum: The Cafe
---

### Post by rifak on 2009-09-01
this is a two part post: 1) which is the more thorough way, if there is one, to close a window/app and 2) what do you guys use?

ive been personally using ubuntu full time for a little over a year now and always close windows by either ctrl-q, or file-quit. this is basically due to what i am used to. when i first was introduced to linux (3 years ago in a research lab) i was taught on opensuse and the person who introduced it to me told me that using the X button wasn't a full closing of the program and to always use file-quit or ctrl-q, so it just kind of stuck since then. is this a bunch of garbage or is there some truth to it?

---

### Post by yabbadabbadont on 2009-09-01
If the application you are using was written properly, they are interchangeable.  If it wasn't written properly, you might lose data (depending upon what the app does) if you just hit the close window manager icon.  You are most likely quite safe using the close icon though.

---

### Post by toupeiro on 2009-09-01
how about kill?

---

### Post by yabbadabbadont on 2009-09-01
> **toupeiro said:**
> how about kill?

Same answer as above.

---

### Post by Simian Man on 2009-09-01
The only time it would matter is some programs (like Rhythmbox and Transmission) will minimize to the notification area when you hit the close button.

In general, it doesn't make a difference though.

---

### Post by Xbehave on 2009-09-01
clicking the x tells the window manager to tell the program to quit
file,exit tells the program to quit

99.9..(a lot more 0s)..9% of the time these are the same but:
a program may not be codded to properly deal with the window manager instruction
a window manager may not send the correct instruction (i doubt this ever happens though because if your smart enough to code a WM you are smart enough to code the x button)
if the program does not respond to the signal from the WM quick enough (say its doing a lot of saving or something), the WM may give you an error warning and suggest you kill the program.
> **toupeiro said:**
> how about kill?
AFAIK
kill is bad mkay, it means as stop the program NOW, do the minimum cleanup to let the program work next time but forget about anything else.
kill -9 is even worse its just stop the program NOW

---

### Post by toupeiro on 2009-09-01
> **Xbehave said:**
> clicking the x tells the window manager to tell the program to quit
file,exit tells the program to quit

99.9..(a lot more 0s)..9% of the time these are the same but:
a program may not be codded to properly deal with the window manager instruction
a window manager may not send the correct instruction (i doubt this ever happens though because if your smart enough to code a WM you are smart enough to code the x button)
if the program does not respond to the signal from the WM quick enough (say its doing a lot of saving or something), the WM may give you an error warning and suggest you kill the program.

AFAIK
kill is bad mkay, it means as stop the program NOW, do the minimum cleanup to let the program work next time but forget about anything else.
kill -9 is even worse its just stop the program NOW


kill == that pretty X in your window manager.  If you are not using file contexts to close applications, you are basically killing it unless the application was written to do something else with the X button.

Perhaps I didn't say kill -9 because I already knew better? ;)

---

### Post by FuturePilot on 2009-09-01
Which ever one my mouse happens to be closest to.

---

### Post by Xbehave on 2009-09-01
> **toupeiro said:**
> kill == that pretty X in your window manager.  If you are not using file contexts to close applications, you are basically killing it unless the application was written to do something else with the X button.

Perhaps I didn't say kill -9 because I already knew better? ;)
erm most standard applications are written to do something else, try using the 3 methods in firefox (open,close,open,close,open (twice because session management doesn't show an error on the 1st time))
1)file->close (results in no crash message)
2)click the x (results in no crash message)
3)kill firefox's PID (results in crash message)

kill is a much more "unfriendly" option, in kde if a program doesn't close after pressing X, you are asked if you want to kill $pid_of_window, with a little warning and with dameon+gui programs (or even firefox) using kill gives a lot more problems than clicking the x

---

### Post by magmon on 2009-09-01
I use the x button out of habit.

---

### Post by doorknob60 on 2009-09-01
I usually use the X button or Alt-F4, just because it's quicker.

---

### Post by Eviltechie on 2009-09-02
I use the little dot on the left side of the window.

[IMG]http://img10.imageshack.us/img10/3907/iusethedot.jpg[/IMG]

---

### Post by MaxIBoy on 2009-09-02
Some programs (like transmission and VLC) can go to the systray instead of closing when you click the X, but most such programs have the ability to disable this. Some programs are poorly written and hang instead of closing properly (rare.) Otherwise it closes quite thoroughly.

The X or alt-f4 works just fine in almost all circumstances.

---

### Post by pissedoffdude on 2009-09-02
> **switham said:**
> this is a two part post: 1) which is the more thorough way, if there is one, to close a window/app and 2) what do you guys use?

ive been personally using ubuntu full time for a little over a year now and always close windows by either ctrl-q, or file-quit. this is basically due to what i am used to. when i first was introduced to linux (3 years ago in a research lab) i was taught on opensuse and the person who introduced it to me told me that using the X button wasn't a full closing of the program and to always use file-quit or ctrl-q, so it just kind of stuck since then. is this a bunch of garbage or is there some truth to it?

Both ways should close the program entirely, unless it minimizes to the system tray.  AFAIK, a linux program can close completely just by hitting the x, with a few exceptions.  Maybe you're thinking of mac programs?

---

### Post by SacValleyDweller on 2009-09-02
Normaly I just X out.

If I cant find said button, like happened when I was trying to install Jaunty on my (now relegated to) backup desktop, file close.

If the program appears stuck, which happened not a majority of the time but enough to be a drag on my desktop when it ran XP, Alt F4

---

### Post by toupeiro on 2009-09-02
> **Xbehave said:**
> erm most standard applications are written to do something else, try using the 3 methods in firefox (open,close,open,close,open (twice because session management doesn't show an error on the 1st time))
1)file->close (results in no crash message)
2)click the x (results in no crash message)
3)kill firefox's PID (results in crash message)

kill is a much more "unfriendly" option, in kde if a program doesn't close after pressing X, you are asked if you want to kill $pid_of_window, with a little warning and with dameon+gui programs (or even firefox) using kill gives a lot more problems than clicking the x

For the sake of accuracy, you have to pick another app in your example.  Firefox **!=** most applications.

---

### Post by schauerlich on 2009-09-02
Cmd-Q.

---

### Post by Xbehave on 2009-09-02
> **toupeiro said:**
> For the sake of accuracy, you have to pick another app in your example.  Firefox **!=** most applications.
kwrite
kword
kspread
kpresenter
kolourpaint
i'll stop here and just assume anything using kde

scribus
zenmap
gnumeric
okteta
I don't have any other apps where its easy to tell 

alt+f4 / X button should always either minimize to tray or be the same as clicking , if they do not there is a bug somewhere. Closing via the "file>exit", is better because
[LIST=1]
[*]It makes more sense to tell the program directly
[*]It will always exit instead of minimize to tray
[*]There is less chance of a bug (although tbh if your program is that buggy, you have to wonder if it will get as far as needing closing)
[/LIST]
Closing via alt+f4/x button has the advantage that if the program doesn't shutdown in a timely manner the WM will prompt you to **kill** it, which i hope i have established is a different thing that should be avoided whenever possible

---

### Post by yabbadabbadont on 2009-09-02
Just to be pedantic, Alt-F4 as a close shortcut key is entirely dependent upon which window manager you are using.  (and how you have it configured)  On my machine, Alt-F4 simply switches to the fourth desktop.  ;)

---

### Post by hessiess on 2009-09-02
ctrl+shift+c (DWM equv for alt+f4) or just :q <enter> :). I dont have any `x' buttons, or window bars, waste of presous screen space.

---

### Post by HappyFeet on 2009-09-02
> **futurepilot said:**
> which ever one my mouse happens to be closest to.

+1

---

