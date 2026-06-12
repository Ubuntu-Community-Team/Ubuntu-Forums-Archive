---
title: "errors dont get shown to users except from terminal"
date: 2007-10-29
forum: Ubuntu Brainstorm
---

### Post by sdowney717 on 2007-10-29
like if you run something using wine from the menu, the mouse cursor will go busy for a while then nothing.
This leaves you wondering what happened.
Why should a user have to get to terminal and type the command just to see the error?

---

### Post by smartboyathome on 2007-10-30
> **sdowney717 said:**
> like if you run something using wine from the menu, the mouse cursor will go busy for a while then nothing.
This leaves you wondering what happened.
Why should a user have to get to terminal and type the command just to see the error?

This would be up to the wine developers, not anyone else. Also, if you want the errors, you would pretty much HAVE to type it in terminal, because a GUI would be unreliable. :(

---

### Post by sdowney717 on 2007-10-30
[http://ubuntuforums.org/showthread.php?t=533257&highlight=wine+error+log](http://ubuntuforums.org/showthread.php?t=533257&highlight=wine+error+log)

I did find winefix

what do you think?

---

### Post by AlexThomson_NZ on 2007-10-30
Interesting idea to maybe implement for all apps (rather than Wine)

Maybe when running something from a Launcher in the GUI, have the ability to display any output to stderr in a visible window?  Of course, there are usually logs to go through, but may be a bit more useful for n00bs (so they give more info when asking for help)

---

### Post by jusmurph on 2007-10-31
Terminal is nice for presenting the error in a format that can easily be copy and pasted for others to help with.

Though something of a warning would be nice ofcourse.

---

### Post by kragen on 2007-10-31
A lot of apps post messages to the terminal though - most of it isnt errors either, so there is no way to reliably tell whether or not an app has worked properly or whether you need to post the contents of the terminal up somewhere. (as far as I am aware).

---

### Post by coolen on 2007-10-31
This is up to the developers. Having anything which goes to stderr appear in a box would be daunting: there are some crazy error messages out there, and a lot of them are from separate calls, not one big long one. In a lot of cases, you'd get either one long, cryptic error message, or thirty separate windoews popping up with tiny bits of information which make no sense (not to mention flood your window list).

---

### Post by sdowney717 on 2007-10-31
well, it would still be nice to get some feedback when what you clicked on is just dropped cold and leaves you wondering.
Are these runtime errors trapped by the OS in a log file? 
Then if a user clicked in the gui, if an error showed up in the log, it could perhaps display it somehow in a separate window like terminal even. 

It could even be setup in a drop down box from the panel. Like you would click on the panel button, and the errors would show in a window.

setup an error icon in the panel and just putting all the errors in a running list might be helpful.

---

### Post by AlexThomson_NZ on 2007-10-31
Unless you are running from a terminal, stderr/stdout is lost in the ether.

I suppose it would be nice to get some (subtle) notification that something was logged to stderr- that way some programmers might be more inclined to handle errors properly/log them to a file

---

