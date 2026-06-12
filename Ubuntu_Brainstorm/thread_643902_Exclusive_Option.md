---
title: "Exclusive Option"
date: 2007-12-18
forum: Ubuntu Brainstorm
---

### Post by lexen on 2007-12-18
The idea is that there are many applications that use a lot of system resources and are often the only program running.  If you got rid or everything running that isn't required for that one program, it would speed the system significantly.  Below I have made some fake screen shots to explain how this would look.


This is my traditional desktop and will serve as the starting point.  I used Firefox because it is a very common program, but it wouldn't really benifit from the Exclusive option.
[IMG]http://www.grandhavenmi.org/exclusive/1.png[/IMG]


To activate the exclusive option, you right click the application on the bottom panel you will get the option to "Make Exclusive."  It is a little hard to see in the screen shot below, but it is above "Close."
[IMG]http://www.grandhavenmi.org/exclusive/2.png[/IMG]


When you choose "Make Exclusive" you will get a window that warns that it will close all other applications.  You have the option to "Make Exclusive" to "Cancel" or to view "Options."  For the sake of this demonstration, I will click "Options."
[IMG]http://www.grandhavenmi.org/exclusive/3.png[/IMG]


You have a few things that you can keep running.  You can keep the applications panel running, which will also give you the option to keep the clock running.  There is also the option to run the application in "Safe Graphics Mode" and to turn "Networking / Internet" on or off.  I also figured that there might be a time when you need two applications running to get stuff done.  For that reason, I added the option to run a second program.  I think it should stop at two, because if you run more then two applications it would defeat the purpose.  If people think otherwise, then maybe we should add more application slots.
[IMG]http://www.grandhavenmi.org/exclusive/4.png[/IMG]


This is what it should look like when the program is exclusive.  There will be a loading screen that I would imagine would look something like the start-up screen.
[IMG]http://www.grandhavenmi.org/exclusive/5.png[/IMG]


When you are ready to leave Exclusive Mode, the quick key should be Ctrl-Alt-Esc or something like that.  If you have the applications panel still open, you can right click the program and say "Make Non-Exclusive."  When you do that, it will have to start-up again as if you had shut down the computer.  Maybe there should be an option to start up with an exclusive program, but I don't know how hard that would be to program.

This option would be ideal for video editing / exporting, 3D Games, or anything else that makes the computer sweat.  If anyone has any questions, comments or possible changes, please comment about them.

---

### Post by xelapond on 2007-12-21
That would be really great for developers too!  Maybe we could also add a thing just so if we don't want to go full exclusive we can just set   the nice value of the program, to give some program higher priority then others.

BTW, do those screen shots work?  Or are they just nonfunctional windows?

---

### Post by smartboyathome on 2007-12-21
> **xelapond said:**
> That would be really great for developers too!  Maybe we could also add a thing just so if we don't want to go full exclusive we can just set   the nice value of the program, to give some program higher priority then others.

BTW, do those screen shots work?  Or are they just nonfunctional windows?

They are fake/nonfunctional windows. GNOME doesn't have this option (and I don't think it is available by extention either). It beats my meathod of having to log out and then log back in using failsafe terminal to do this.

---

### Post by lexen on 2007-12-21
smartboyathome was right, those are fake screen shots to show how it _might_ work.  

I am a little surprised on how many people don't like the idea.  It would really speed up a lot of programs:
3D Games
Compiling code
Video work
Audio Work

I would also imagine if you wanted to keep something downloading, it would lower the amount of watts because there is a lot less for the processor to do.

xelapond:  How would that priority thing work?  The idea is to strip the system down until it can only run one program, so I don't know how a priority system would work.  I am not dissing it, I just want to know what you mean.


Thanks,
Lexen

---

### Post by Lster on 2007-12-21
It's a really funky idea! I'm not really sure what I think of it - it really depends on how effective it would be...

---

### Post by wormser on 2007-12-21
> **lexen said:**
>  I am a little surprised on how many people don't like the idea.  It would really speed up a lot of programs:
3D Games
Compiling code
Video work
Audio Work

I think it is a good idea especially for those programs listed.  Ubuntu (*nix) command [nice]("http://en.wikipedia.org/wiki/Nice_(Unix)") does this by setting priority.  I never use it and do not know how much difference it makes, but it probably could be used for this idea.  It would give the application select higher priority and other not need lower priority or kill them.

---

### Post by lexen on 2007-12-22
How do you use "nice?"  Is it like: firefox nice-20?


Thanks,
Lexen

---

### Post by xelapond on 2007-12-24
Quoted from the man page:
> NAME
       nice - run a program with modified scheduling priority

SYNOPSIS
       nice [OPTION] [COMMAND [ARG]...]

DESCRIPTION
       Run  COMMAND  with an adjusted niceness, which affects process sched\
ul&#8208;
       ing.  With no COMMAND, print the current  niceness.   Nicenesses  ra\
nge
       from -20 (most favorable scheduling) to 19 (least favorable).

       -n, --adjustment=N
              add integer N to the niceness (default 10)

       --help display this help and exit


I'm not positive, but I think it would look something like 
```
nice -n -20 firefox
```

To run firefox with full priority though.  I'm not sure, so you would be better off asked a *nix guy.

I forget the name, but there is a program for Mac OS X that does this is a nice Ubuntu like GUI.

Alex

edit:  It turns out that command I posted spawns a new firefox process with a nice of -20.  I don't know if there is a way to modify the nice without spawning a new program though.  But again, ask a *nix guy.

---

### Post by Nekiruhs on 2007-12-24
> **xelapond said:**
> Quoted from the man page:


I'm not positive, but I think it would look something like 
```
nice -n -20 firefox
```

To run firefox with full priority though.  I'm not sure, so you would be better off asked a *nix guy.

I forget the name, but there is a program for Mac OS X that does this is a nice Ubuntu like GUI.

Alex

edit:  It turns out that command I posted spawns a new firefox process with a nice of -20.  I don't know if there is a way to modify the nice without spawning a new program though.  But again, ask a *nix guy.
I'd be careful about that. That allows firefox to trample over the kernel itself for CPU time. Might want to put it a little lower.

---

### Post by xelapond on 2007-12-24
> 
Originally Posted by xelapond  View Post
Quoted from the man page:


I'm not positive, but I think it would look something like
Code:

nice -n -20 firefox

To run firefox with full priority though. I'm not sure, so you would be better off asked a *nix guy.

I forget the name, but there is a program for Mac OS X that does this is a nice Ubuntu like GUI.

Alex

edit: It turns out that command I posted spawns a new firefox process with a nice of -20. I don't know if there is a way to modify the nice without spawning a new program though. But again, ask a *nix guy.
I'd be careful about that. That allows firefox to trample over the kernel itself for CPU time. Might want to put it a little lower.

 

Hmm, that could be a problem:)

Maybe in the GUI(if one is written) limit it to -15 or so, just to prevent that.

---

### Post by lexen on 2008-01-04
I know this discussion has more or less died, but I really think this would make ubuntu more productive and allow people with slower PCs to do more.  Is there any programmer that could tell me about how hard a program like this would be to make so I can get an idea of what it would take to get it up and running?


Thanks,
Lexen

---

### Post by Rufe0 on 2008-01-05
I just don't see a real need for this. Yes sure it would optimise your syste m and it would run better but I can't realy see it being a noticable effect. Im running apache, sql and other programs like that in the background and im seeing only very small amount of system resourses being used. If I went into this mode now I would only notice a 1% difference (I'm guessing) and if I didn't have these things running then I imagine it would be more like 0.1%, so I can't see this being of any use to me. Maybe it's something that should be implemented but not at the epense of somthing more useful.

---

### Post by Samhain13 on 2008-01-05
I voted YES specifically for this reason:

> This option would be ideal for video editing...

because most of the time, when I play with video editing, I'll have at least the GIMP, a file browser and Totem open too. Sometimes, I also have Firefox running as I am often following some kind of tutorial some where. This option will be very useful for me as I can opt-out of it and restore my previously running applications after rendering. :)

---

### Post by xelapond on 2008-01-06
When I am programming(I do work on embedded cores, so no, I can't write the app for you:()  I Have at least 3 data sheets, firefox, terminal(or two), scite, songbird, skype and a few file browsers.  Once I get a JTAG debugger Ill have that open too.

I would love to go exclusive on scite, just so its a little faster(10+ tabs really does slow it down, then add compiler support into that mess)

Alex

---

### Post by lexen on 2008-01-07
I really don't know how much faster this will make a program, but consider video game councils, the Game Cube had like a 300Mhz Processor and it could play games with far better graphics then my 2Ghz computer.  The reason is because all it has to do is play video games, they striped down the operating system until it could do little more then that.  I don't think we could get it that efficient, but if we got it half efficient, it would be like turning your 2Ghz into a 6Ghz.

Does anyone know any other reasons why video games are so much faster then PCs?  Are they written in machine code or something else like that?

I've heard a lot of people talking about how they have like 6 programs running at a time, so it wouldn't work for them.  They're right, it wouldn't work for them, what it would work for would be when they are done doing the manual labor and it will be another 6 hours before it compiles and they leave to do something else.  Theoretically, they could make it exclusive and they would only have to wait 2 hours, but that is assuming it speeds up the computer 3 fold, which is based on making the computer half as efficient as a video game.



Thanks for reading,
Lexen

---

### Post by lexen on 2008-01-25
For those of you that were interested in this idea, there is a half way to do it now, but it isn't very user friendly.  If you log out and click the "select session" option at the bottom left hand corner of the screen and change your session to "failsafe terminal"  you will first get a warning and then you will get just a terminal.  Then you just type in the command to open a program and you will get it moving a lot faster.  When you are done just type "exit" and it will log you out.  When you sign in afterward, you don't have to worry about switching your session back, it does that automatically.

     This won't work for everyone or every program.  For example, it looks like you can't run programs that use multiple windows, at least I couldn't run XawTV but I didn't try GIMP or any other programs like that.

     Does anyone know how hard it would be to switch to failsafe terminal while leaving one program open?  Is there a way to run only a terminal and have two windows open?  What is different between failsafe terminal and regular terminal?


Thanks,
Lexen

---

### Post by Mr. Picklesworth on 2008-01-27
Changing the "nice" of the application has always worked for me. I see the benefit of having a "make exclusive" tool somewhere that calculates an ideal "nice" value to put the program on top there.

Doesn't the window manager give us some kind of automatic "nice" adjustment, too?

---

