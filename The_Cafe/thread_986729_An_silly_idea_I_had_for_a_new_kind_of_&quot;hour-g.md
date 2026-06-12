---
title: "An silly idea I had for a new kind of &quot;hour-glass&quot; icon (came to me while sleeping)"
date: 2008-11-18
forum: The Cafe
---

### Post by diablo75 on 2008-11-18
I didn't mention this in that other dream thread because it wasn't weird enough to post there.

Don't ask me for details about the dream, because I don't remember any.  What I do remember was seeing a very cool cursor on a computer screen that I've never seen anywhere else.

Okay, so!

You have an ordinary busy cursor:  In Windows when you click on an application shortcut, the cursor will change to either an hour-glass, or a semi-hour glass with the smaller cursor next to it.  At the moment, I can't remember if anything like this occurs within Ubuntu after clicking on something that takes a few seconds to load...but that doesn't matter.  Irrespective of OS, lets just say we have a cursor that turns into an hourglass when the computer is busy loading a program or something else.

So, here's what I saw in my dream.

When you click on something, instead of an hour glass, you see a ring (picture a doughnut with one line through it on one side) encircle the cursor and it's purpose is to act as an animated countdown to the point where whatever you just clicked on is fully loaded.  The biggest difference between it and the hour glass is that the hour glass didn't give you any kind of visual countdown at all.

Using my HORRIBLE Gimp skills, I made some drawings to show you a mockup of this idea.  The "full" is what a person would see right after clicking on something, and then it would increment down until gone.  Of course there would be more than just 4 frames of animation.  I wish I had the patience and known-how to easily create an animation that has a more granular countdown.

Here's where the embarrassment comes in:  I have no idea what these countdowns could possibly be based on.  How might the OS know how long it is going to take for any given application to load to the point of being on screen?  Maybe someone else can tackle that or rule out the idea entirely.  But it was worth a shot.  :)

Again, please excuse my horrible drawings.  I'm sure there are those of you out there who would be able to create something more professional looking.

---

### Post by Dr Small on 2008-11-18
Somehow, that looks familar.

---

### Post by Capt. Mac on 2008-11-18
I genuinely like the idea, but I'm not really sure about the feasibility of using it as a progress bar.

Also, what would it do if two programs/objects/whatever are loading as opposed to one?

---

### Post by damis648 on 2008-11-18
> **Dr Small said:**
> Somehow, that looks familar.

+1, thats kinda like the vista loading icon. I don't really like it, no offense, but I think this would kind-of ruin the user experience because they know that once the ring is gone, the program will load. You add more anticipation and a pointless GUI addon. It is very hard to explain, so that probably doesn't make sense, but I know I just would not feel comfortable seeing a countdown timer everything I try to open something. What does anybody else think?

---

### Post by diablo75 on 2008-11-18
> **Capt. Mac said:**
> Also, what would it do if two programs/objects/whatever are loading as opposed to one?

I think it would add an additional right outside any others that are already present, and give it a different color.  If any rings finish, the unfinished ones collapse in towards the center until they too are gone.

If I were to redraw the pictures, I wouldn't have made the ring so fat looking.  It could be much skinnier.

Edit:  I've resized the original pictures to something more "actual size" because otherwise it looks kind of obnoxious.

---

### Post by Dr Small on 2008-11-18
> **Capt. Mac said:**
> I genuinely like the idea, but I'm not really sure about the feasibility of using it as a progress bar.

Also, what would it do if two programs/objects/whatever are loading as opposed to one?
It would undoubtedly conflict or show the last one. Personally, I wouldn't use it. I'm not into GUI stuff. I click something from a menu, and it loads presto. Hardly any waiting time.

---

### Post by Changturkey on 2008-11-18
> **Dr Small said:**
> Somehow, that looks familar.

It's the Xbox 360 Controller thing.

---

### Post by Rokurosv on 2008-11-18
Looks vistaish, but you could make a cursor theme to try it out.

And it does look like 360 controler ring

---

### Post by diablo75 on 2008-11-18
> **Changturkey said:**
> It's the Xbox 360 Controller thing.
This is why I wish I had the time to create a 100 frame gif instead of 4 frames with 25% increments.  (sigh)

---

### Post by AliTabuger7 on 2008-11-18
> **diablo75 said:**
> This is why I wish I had the time to create a 100 frame gif instead of 4 frames with 25% increments.  (sigh)

Why not 3 instead of 4?

Look at the Ubuntu logo in the top left of this page.

---

### Post by diablo75 on 2008-11-18
> **AliTabuger7 said:**
> Why not 3 instead of 4?

Look at the Ubuntu logo in the top left of this page.

I didn't want 4 or 3.  I wanted about 100 (one frame for each percentage point in time left to full process load).  I wanted this to be a more granular animation, not a blocky 4 frame animation.

Edit:  So I made a more granular animation to show you what I'm trying to say.

---

### Post by pp. on 2008-11-19
A very similar concept does indeed exist, as others have pointed out. I think I have seen that in quicktime or some other Apple product. What's new is the double duty as "busy" cursor and progress indicator. However, if the progress is kind of slow you won't notice that the segment of the circle is growing while you wait.

---

### Post by Giant Speck on 2008-11-19
Vista has this.

[IMG]http://img170.imageshack.us/img170/6282/aerobusylargebv7.gif[/IMG]

Or at least something very, very similar.

---

### Post by diablo75 on 2008-11-19
> **Giant Speck said:**
> Vista has this.

[IMG]http://img170.imageshack.us/img170/6282/aerobusylargebv7.gif[/IMG]

Or at least something very, very similar.

Right, but it's nothing more than an hourglass with a new look.  It's not a progress bar that gives you any sort of visual ETA.

---

### Post by Asday on 2009-01-05
> **Dr Small said:**
> Somehow, that looks familar.

The EVE-online module countdowns.

To be honest, I like this idea.  I'm guessing it'd be fairly hard to do, 'cause application programmers'd have to put something in their code to say "10% ready!" or whatever, so it'd take a while for it to be universal.

Well, I'm guessing at the method here.  (^-^ )

---

### Post by Tomosaur on 2009-01-05
Not all software gives any indication of its 'init' progress (in fact, very few do). While I think it'd be a good idea, I don't think it's one that is likely to be implemented any time soon.

However, there are ways it could be accomplished in a 'pseudo-accurate' way: simply measure the average time it takes for the application to launch normally (there are already applications which do this - I use one as my bootup screen to give a smooth progress bar rather than one which jumps - I think Mac uses something along those lines). Of course, if your computer is using more resources than it usually does, the timing would be off.

---

### Post by Asday on 2009-01-07
That was the workaround I thought would happen.  Maybe also include current system resource usage in the calculations to improve accuracy?

Actually, I'm getting quite interested in this, reckon we could make it in Python?

---

### Post by 3rdalbum on 2009-01-07
I think it should be reasonably easy to implement at application-level. Most programs don't seem to print anything to stdout (the controlling terminal) while loading unless there's an error. Why not print some sort of universal progress message like this:

```
chris@chris-desktop:$ gimp
[startup] 10%
[startup] 22%
[startup] 40%
Font cache loaded
[startup] 60%
[startup] 87%
Creating GUI...    done
[startup] 100%
```

Whenever the program accomplishes a particular task on startup, it can just print an update to stdout. This way it will work a lot like the Ubuntu startup progress bar. I guess the program developers could also use "[startup] indeterminate" if they're not sure how long the initial stages of the startup process will take.

KDE's little bouncing icon sometimes stops bouncing before the program finishes starting up, or continues bouncing even though the program has crashed. If KDE keeps an eye on the terminal output, it could test for the words "Segmentation fault" or "[startup] aborted" and remove its bouncing icon. Your progress wheel could do exactly the same thing.

In short: Cool idea, let's see someone take up this ball and convince program developers to put [startup] x% messages in their programs!

---

### Post by dannybuntu on 2009-01-07
I would prefer the circle go the other way around like - clockwise

---

### Post by rick08 on 2009-01-07
I have seen something very similar to this in a them I once used.  I'll have to find it and post the theme name.

---

### Post by Asday on 2009-01-07
> **3rdalbum said:**
> I think it should be reasonably easy to implement at application-level. <snip>

Yeah, but no.  Think how many programs there are around.  Yes, I know, you could release boilerplate code for every language around, (have fun with the brainf*ck one) but what percentage of people will implement it?

I think, if it's going to be made (as I said, I'm very happy to help, if it's in Python...) the releases in order should be something like:

[LIST=1][*]Basic functionality, the guessing, based on previous load time, and system resource usage, etc.
[*]Mild integration, checking if the program already has percent loaded, etc.
[*]Then release boilerplate code
[*]????
[*]Don't profit.  Feel smug.  Brag.  Up to you.
[/LIST]

---

