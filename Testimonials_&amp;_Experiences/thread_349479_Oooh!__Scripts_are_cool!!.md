---
title: "Oooh!  Scripts are cool!!"
date: 2007-01-30
forum: Testimonials &amp; Experiences
---

### Post by whitefort on 2007-01-30
First, as a newbie Windows migrant, I have to confess that I'm one of those people who (until yesterday) whined horribly about having to use a terminal to do ***anything. *** But I think my whining days may be over...

What follows will be totally old hat ho-hum stuff for people who know Linux, but for a non-techie newbie like, it blew my socks off.

Yesterday I discovered that I could download something called Xplanet, then make a simple little text file to use it.  The upshot is that every time the text file is run, my wallpaper changes to a picture of planet Earth, centred on my home location, and showing the areas that are currently in light and darkness.

Even better, it seems there's an easy way to make Linux run this script every 30 minutes or so, so that I have a constantly updated Planet Earth light/dark wallpaper. (I haven't quite figured that bit out yet, but it's my next project).

I think I've just become a convert.  Suddenly I see the fun (and power) of typing stuff in, instead of just expecting to be able to do everything with a mouse click.

I just wanted to share this, in case it helps any other newbies who moan and groan every time the word 'terminal' is used!

I also used to whine that Windows was for people who just wanted to ***use ***a PC, and Linux was for people who liked to ***tinker ***with PCs.  Now I'm beginning to suspect that maybe Linux is so wonderful that it seduces/encourages people to start tinkering!

---

### Post by taurus on 2007-01-30
Move to Testimonials.

---

### Post by jvc26 on 2007-01-30
lol, very true, I used to do a lot of messing about customising my XP - so much so that it hardly looked like XP any more. Then I discovered Ubuntu and my same inquisitive altering of things began. I havent needed to customise the looks and the like as I like the way it looks, in terms of terminal work and stuff though, it doesnt take long before you'd almost rather use the terminal for things rather than a GUI - Synaptic package manager, creating root directories using terminal than a gksudo nautilus. Terminal holds so many more things I havent yet got round to trying out, but i really is an excellent tool.
Il

---

### Post by aktiwers on 2007-01-30
Same here.
I used to customise Windows all the time..  I suddenly found out, I had tons of programs running, using another shell and all my programs was opensource. Then I thought..  hmmm who am I kidden?? I moved to Linux and now I can customize everything, even without tons of programs sucking up my machine!

---

### Post by seijuro on 2007-01-30
> **whitefort said:**
> Now I'm beginning to suspect that maybe Linux is so wonderful that it seduces/encourages people to start tinkering!

Indeed it does. My wife is more experienced with tweaking Linux and tinkering with things than she did in the entire time she was saddled with windows.

---

### Post by whitefort on 2007-01-31
Thanks for the replies, guys.  I'm continuing to be amazed at what Ubuntu can do, and am in danger of becoming (gulp) somone who tinkers with computers!

Which means I'll probably break something very soon, so I'd better get a backup strategy sorted out.

Just as a quick PS... now that I've got my Xplanet wallpaper script up and running, would some kind person point me in the right direction, towards details of how I can get Linux to auto-run it every half-hour?  I've totally forgotten the name of the program I need!

---

### Post by weresheep on 2007-01-31
Hello,

The way you get Ubuntu to start a task automatically is using 'cron' system daemon. You use a program called 'crontab' to edit a user table that lists the programs and their times and dates that cron should run.

The format of the crontab table is a bit compicated but no doubt a few googles should get you a few examples. Type 'man cron' and 'man crontab' in order to view the relavent manual pages.

Oh, and welcome to the world on Unix! :D 

-weresheep

---

### Post by whitefort on 2007-01-31
Thanks, Weresheep.

Cron!  That's the one.  Somehow I'd gotten 'Chron' into my head.  I'm off now to do some googling.

Thanks again!

---

### Post by TheSqueak on 2007-01-31
There's also a really nice little script to get xplanet to overlay an automatically updated satellite image of the cloud cover over the rendering of the globe. I'm not sure where to get it any more, but i'll have a look if I get a chance this afternoon.

---

### Post by darrenm on 2007-01-31
```
crontab -e
0/30 * * * * /path/to/xplanet

```

:)

---

### Post by whitefort on 2007-01-31
Thanks, you guys are the best!

My new-fangled wallpaper changer is up and running.  I can still hardly believe you can do something like that with just a few lines of typing!

I think my next crontab project will be to (try to!) set different desktop themes for morning, afternoon, and evening...  :D 

Thanks again!

---

### Post by 3rdalbum on 2007-02-01
There's also a program called gCronTab, which is a graphical editor for the crontab. I've not used it myself, but it looks pretty good.

---

### Post by Wolki on 2007-02-01
> **whitefort said:**
> I think my next crontab project will be to (try to!) set different desktop themes for morning, afternoon, and evening...  :D 


In case you didn't figure it out already, here are some pointers:

Various theme type things (and lots of other stuff) in Ubuntu's default desktop environment (GNOME) are stored in an xml configuration structure called gconf. You can take a look at it and change settings graphically with a tool called gconf-editor that unfortunately is hidden from the menus, but you can enable it again by editing the menus or just start it with the run dialog/terminal.

For example, take a look at the keys /desktop/gnome/interface/gtk_theme and /desktop/gnome/interface/icon_theme.

And one last hint: you can do various things (like setting keys)  from a script by using a program called gconftool-2; documentation for this can be displayed by executing "man gconftool-2" in a terminal.

---

### Post by pgilmon on 2007-02-16
Whitefort, [this thread]("http://www.ubuntuforums.org/showthread.php?t=351341") might be of your interest. It contains a script that updates the wallpaper every 30 minutes without the need to set cron up. The script itself goes to sleep for 30 min, then wakes up, refreshes the wallpaper and goes to sleep again.

---

### Post by whitefort on 2007-02-16
> **pgilmon said:**
> Whitefort, [this thread]("http://www.ubuntuforums.org/showthread.php?t=351341") might be of your interest.

Thanks for that - I've had my cron up and running for a while now, but this seems like a more elegant solution somehow!

---

